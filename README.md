# MSP430 `.z1` / `.sky` / `ARM M4F(CC1352R)` / `cooja-native` Platformları için Üretilmiş Firmware’ler Üzerinde Yapılabilecek Analiz Türleri Kontrol Listesi

---
İnceleme için Contiki-NG ortamında derlenmiş iki farklı platforma ait dosyalar (nullnet-unicast.z1 ve nullnet-unicast.sky) kullanılmıştır.
Çıktıların olduğu dosyalar eklenecek.
---

# 1. Binary Kimlik Analizi

MSP430 Mimari Tipi
- Her iki dosya için de msp430-readelf -h çıktısının Class satırından dosyanın ELF32 sınıfında olduğu ve msp430-objdump -f çıktısından elf32-msp430 dosya formatında olduğu görülmüştür. 
- z1 platformu msp430:430X mimarisini kullanmaktayken sky platformu daha eski olan msp430:430 mimarisini kullanmaktadır.

ELF Format Bilgisi
- msp430-readelf -h çıktısındaki Type satırından dosyaların EXEC yani çalıştırılabilir kodlar olduğu görülmüştür.

Endianness Bilgisi
- Çok byte’dan oluşan verilerin bellekte hangi sırayla saklanacağını belirler. Little Endian, LSB’den MSB’ye bir sıralama belirtirken; Big Endian, MSB’den LSB’ye bir sıra belirtir.
- msp430-readelf -h çıktısının Data satırından her iki dosyanın da 2's complement ve little endian veri yapısını kullandığı gözlenmiştir. 
- 2’s complement, pozitif sayılar standart binary formatta saklanırken negatif sayıların 2’nin tümleyeni şeklinde saklandığını belirtir.

Entry Point Adresi
- msp430-readelf -h çıktısındaki ‘Entry point address’ satırları incelendiğinde donanımların bellek haritaları farklı olduğundan sisteme enerji geldiğinde işlemcinin ilk okuyacağı adreslerin z1 için 0x3100, sky için 0x4000 olduğu görülmüştür

ABI Bilgisi
- Derlenmiş kod parçalarının birbiriyle nasıl iletişim kuracağını belirler. Interrupt çağırma düzeni, stack yapısı, register kullanımı, veri tiplerinin boyutları gibi kuralları tanımlar.
- msp430-readelf -h çıktısının OS/ABI satırından dosyaların Standalone App olduğu gözlemlenir yani doğrudan donanım üzerinde çalışabilecek şekilde kurgulanmıştır. 
- ABI Version değerlerinin 0 olması ise özel bir ABI sürümü belirtilmediğini gösterir.

Compiler İzi
- msp430-readelf -p .comment komutu ile ELF dosyasının metadata bölümü incelendiğinde, her iki imajda da açıkça GCC: (GNU) imzası bulunmuştur.

Toolchain Versiyonu
- msp430-readelf -p .comment komutunun çıktısından derleyicinin versiyonu 4.7.2 20120920 (mspgcc dev 20120911) olarak bulunur. Bu bilgi MSP430 mimarisi için özelleştirilmiş olan mspgcc araç zincirinin 4.7.2 numaralı sürümünün kullanıldığına işaret eder.

Optimizasyon Level Tahmini 
- msp430-readelf -S ile incelenen Section Headers tablosunda hata ayıklama verilerini tutan .debug_info, .debug_line, .debug_frame gibi bölümlerin imaj içerisinde çok büyük yer kapladığı görülmüştür. Bu durum derleme işlemi sırasında kod boyutunu küçültecek yüksek optimizasyonların kapalı olduğuna işaret eder.

Debug Symbol Analizi
- msp430-objdump -f çıktısındaki HAS_SYMS bayrağı ve msp430-readelf -S tablosundaki .symtab bölümünün varlığı derleyicinin fonksiyon ve değişken isimlerini silmediğini göstermektedir.

---

# 2. Bellek Kullanım Analizi

Flash, RAM, Stack, Heap Anlamları
- Flash: Kalıcı bellektir. Enerji kesildiğinde veriler silinmez. İşletim sistemi kodları, fonksiyonlar ve sabit veriler burada tutulur.
- RAM: Geçici bellektir. Cihaz çalıştığı sürece global değişkenlerin, sensör verilerinin ve bufferların değerlerini anlık olarak tutar. Enerji kesilince silinir.
- Stack: Fonksiyonların içindeki yerel değişkenlerin ve interrupt geldiğinde dönüş adreslerinin geçici olarak tutulduğu, LIFO mantığıyla çalışan dinamik RAM alanıdır.
- Heap: Çalışma zamanında boyutları belli olmayan değişkenler için malloc() gibi fonksiyonlarla rastgele ayrılan dinamik bellek alanıdır.

Flash Kullanım Miktarı
- Cihaza enerji verildiğinde ilk değerleri olan değişkenler çalışmak için RAM'e kopyalanır, ancak enerji yokken bu ilk değerlerin Flash bellekte kalıcı olarak saklanması gerekir. Bu yüzden Flash boyutu hesaplanırken text + data formülü kullanılır.
- msp430-size komutunun çıktısındaki text ve data bölümlerinin toplamı yani flash boyutu z1 dosyası için 28097 + 2488 = 30585, sky dosyası için 29171 + 4426 = 33597 bulunur.

RAM Kullanım Miktarı
- RAM içinde ilk değeri atanmış global değişkenler ve ilk değeri atanmamış/sıfır olarak başlatılan değişkenler bulunur. RAM boyutu hesabında data + bss formülü kullanılır.
- Bu değer msp430-size komutunun çıktısından z1 dosyası için 2488 + 2632 = 5120, sky dosyası için 4426 + 3086 = 7512 bulunur.
- Sky platformunun Z1'e kıyasla RAM üzerinde yaklaşık 2.4 KB daha fazla alan rezerve ettiği gözlemlenmiştir. 

.text, .data, .bss Boyutu
- msp430-size çıktısından z1 dosyası için text 28097 byte, data 2488 byte, bss 2632 byte; sky dosyası için text 29171 byte, data 4426 byte, bss 3086 byte bulunmuştur.

Stack Kullanım Tahmini
- Stack boyutu komutla ölçülemez, statik değişkenlerden (.data + .bss) arta kalan boş RAM alanı, fonksiyon çağrıları sırasında Stack tarafından dinamik olarak tüketilecektir.

Heap Varlığı Analizi
- msp430-nm çıktısı incelendiğinde malloc izine rastlanmamıştır. Contiki-NG işletim sisteminin buframmem_memb_mem gibi statik hafıza blokları kullandığı ve Heap kullanmadığı tespit edilmiştir.

Section Dağılımı
- msp430-readelf -S çıktılarındaki bölüm başlıkları tablosu incelendiğinde, işletim sistemi ve uygulamaya ait derlenmiş dosyaların mantıksal olarak belirli bölgelere ayrıldığı görülmüştür.
- Çalıştırılabilir makine kodları .text bölümünde, sadece okunabilir sabitler .rodata bölümünde ve donanım kesme vektörleri .vectors bölümünde toplanmıştır.
- Çalışma zamanında değişebilecek global ve statik değişkenler ilk değer ataması olanlar için .data, ilk değeri olmayanlar için .bss bölümlerine dağıtılmıştır.
- Ayrıca imajların içinde cihaz belleğine yüklenmeyen ancak Cooja üzerinde hata ayıklama için kullanılan çok sayıda .debug_* bölümü bulunmaktadır.

Memory Map Analizi
- msp430-readelf -S çıktısının Addr bölümünden görülebileceği üzere .text z1 için 00003100 adresinden, sky için 00004000 adresinden başlamaktadır.
- Her iki platformda da RAM 0x1100 fiziksel adresinden başlamakta olup, .data ve .bss bölümleri bu bölgeye yerleşmektedir.
- Flash (ROM) adreslemelerinde .z1 platformunda kodların çalıştığı .text bölümü Flash bellekte 0x3100 adresinden başlarken, daha eski bir mimari olan .sky platformunda bu alan 0x4000 adresinden başlamaktadır.
- İşlemcinin kesmelere (interrupt) yanıt verirken baktığı .vectors tablosunun, her iki cihazda da hafıza haritasının en sonuna yani .z1 için 0xFFC0, .sky için 0xFFE0 adreslerine konumlandırıldığı gözlemlenmiştir.

Büyük Veri Yapılarının Tespiti
- msp430-nm —-size-sort çıktısından sistemde en çok yer kaplayan semboller incelenmiştir. Küçükten büyüğe bir sıralama yapıldığı için en alttaki yapılar en büyük yapılardır.
- En çok yer kaplayan fonksiyon, her iki platformda da bir kayan nokta matematik işlemi olan __ieee754_powf fonksiyonudur, T sembolü ile .text bölümünde olduğunu anlarız.
- En büyük veri yapıları anchor_nodes, D sembolü ile .data bölümünde ve buframmem_memb_mem, b sembolü ile .bss bölümündedir.

---

# 3. Symbol / Function Analizi

Fonksiyon İsimleri
- Sisteme ait temel fonksiyonlar .text belleğine yerleşir.
- msp430-nm çıktısının üçüncü satırındaki T (global text) ve t (static text) harfleri o satırdaki ismin bir çalıştırılabilir makine kodu, yani fonksiyon olduğunu gösterir.

Global Değişkenler
- İlk değeri atanmış global değişkenler .data bölümünde yer alırken, ilk değeri olmayan global değişkenler .bss bölümünde bulunur.
- msp430-nm çıktısının üçüncü satırındaki D harfi ilk değeri olan global değişkenleri, B harfi ise ilk değeri atanmamış global değişkenleri belirtir.

Static Değişkenler
- msp430-nm çıktısının üçüncü satırındaki d ve b harfleri, bu değişkenlerin static olduğunu ve kapsamlarının o dosyayla sınırlandırıldığını gösterir.

ISR Interrupt Fonksiyonları
- Donanım kesmelerini yöneten ISR rutinleri fonksiyon formunda .text alanında yer almaktadır.
- msp430-nm çıktısında ismi interrupt olan veya isr ile biten, solunda T veya t yazan semboller interrupt fonksiyonlarıdır.

Contiki Process Entryleri
- Contiki-NG’de process'ler çalıştırılabilir bir kod değil, bir veri yapısıdır. Bu yüzden msp430-nm çıktısında isimleri _process ile biten ve .data bölgesinde tutulan sembollere bakarız.

Radio Driver Fonksiyonları
- Her iki platformun da haberleşme için TI CC2420 çipini kullandığı sembol tablosundan okunabilmektedir. msp430-nm çıktısında cc2420_ ön eki ile başlayan ve fonksiyon olduklarını belirten, T ve t harfine sahip satırlar aranır.

Timer Callbackleri
- Sistemin zamanlayıcı mimarisini kullanan geri çağırma ve zaman aşımı fonksiyonları tespit edilmiştir.
msp430-nm çıktısında ismi timer_ ile biten veya _expired anahtar kelimesini barındıran fonksiyonlar (T ve t) incelenir.

Networking Callbackleri
- msp430-nm listesinde _callback kelimesiyle biten fonksiyonlar aranır ve bunların ağ yığınına ait oldukları isimlerinden çözümlenir.

Sensor Handlerları
- msp430-nm çıktısında mp102, accm_ ve button gibi sensör isimleri aratılarak bulunur.

Kullanılan Kütüphaneler
- Derlenmiş imaja düşük seviyeli C standart kütüphanelerinin bağlandığı tespit edilmiştir.
- Bellek işlemleri için memcpy, memset; string işlemleri için sprintf, printf çağrıları mevcuttur.
- En çok yer kaplayan kütüphaneler z1 ve sky cihazlarında donanımsal kayan nokta işlemcisi bulunmadığı için derleyicinin eklemek zorunda kaldığı __ieee754_powf, __addsf3, __divsf3 gibi yazılımsal kayan nokta matematik kütüphaneleridir.
- msp430-nm çıktısının en altında başı çift alt tire ile başlayan sembollere bakılır. Bunlar GCC'nin otomatik bağladığı matematik kütüphaneleridir. Ayrıca memcpy gibi standart C fonksiyonlarını T olarak tespit ettik.

Kullanılmayan Fonksiyonlar
- z1 ve sky imajlarının içinde kullanılmayan fonksiyon bulunmadığı tespit edilmiştir.
- Bunun mimari sebebi, GNU Toolchain bağlayıcısının derleme aşamasında --gc-sections kullanmasıdır. Linker, kod içinden hiçbir çağrı almayan ölü fonksiyonları tespit edip bellekten tamamen siler. Dolayısıyla msp430-nm sembol tablosunda gördüğümüz tüm fonksiyonlar, sistemde aktif olarak çağrılan canlı fonksiyonlardır.

Function Address Mapping
- msp430-nm, fonksiyonların Flash bellekte tam olarak hangi fiziksel adrese yazıldığını göstermektedir. Örnek olarak main fonksiyonunun bellek haritasındaki yeri incelendiğinde; mimari farklılıklardan ötürü bu fonksiyon z1 imajında 0x0000313e adresine yerleşirken, sky imajında 0x0000403e adresine yerleşmiştir.
- msp430-nm çıktısındaki 1. sütun fonksiyonun HEX adresini, 4. sütun ise fonksiyonun adını verir.

---

# 4. String ve Metadata Analizi

Debug Mesajları
- msp430-strings çıktısı incelendiğinde, işletim sisteminin çalışma zamanındaki hataları yakalamak için kullandığı Check in inconsistent state: %ld vs. %ld ve Check failed: %ld vs. %ld gibi stack kontrolü debug mesajları her iki imajda da bulunmuştur.
- Ayrıca sky imajında loglama seviyelerini belirten Errors, Warnings, Info, Debug metinleri görülmektedir.

printf Logları
- msp430-strings çıktısına bakılırsa, içindeki %d (integer), %u (unsigned integer), %llu (long long unsigned) ve %s (string) gibi C diline ait format belirteçlerinin varlığı, bu metinlerin ekrana bir değişken değeri yazdırmak için (printf) kullanıldığını gösterir.

IPv6 Adresleri
- msp430-strings çıktısında IP adresi formatında hiçbir şey yoktur. Doğrudan nullnet stringlerini göründüğü için, IP katmanı yerine doğrudan MAC katmanı üzerinden haberleşen bir mimari olduğu anlaşılır.
- Ancak sky imajının tablosunda ipv6 ve tcpip modüllerinin isimlerinin bulunduğu görülmüştür.

MAC Adresleri
- Kod içine gömülmüş statik bir MAC adresi bulunmamaktadır. Cihazlar kendi donanımsal MAC adreslerini çalışma zamanında EEPROM'dan okuyup ekrana basmaktadır. Bunun kanıtı olarak imajda bulunan Link-layer address: ve LL-%04x format dizgileri tespit edilmiştir.

Network Node ID’leri
- Düğümlerin ağ üzerindeki kimliklerini belirtmek için Node ID: %u ve ağ üzerinden paket geldiğinde kaynağı loglamak için Received %u , node_id %d from stringleri her iki cihazın çıktısında da gözlemlenmiştir.

Sensor İsimleri
- Sensörlerin ticari/model isimleri çıktıda aranır.
Örneğin z1 imajında ADXL345 sensor, TMP102 sensor ve Button dizgileri yer alırken, bu donanımlara sahip olmayan sky platformunda bu dizgiler bulunmamaktadır.

Process İsimleri
- Contiki-NG süreçlerinin başlangıcında ekrana bilgi vermek veya süreçleri isimlendirmek için yazılmış Accelerometer process, Ctimer process, Event timer ve Stack check stringleri gözlemlenmiştir.

Routing Protokol İsimleri
- Ağ katmanında karmaşık bir routing protokolü yerine, doğrudan nullrouting dizgisinin bulunduğu görülmüştür.
- Bu durum düğümler arası yönlendirmenin yapılmadığını, doğrudan komşular arası basit bir haberleşme kurulduğunu gösterir.

TSCH/6LoWPAN/RPL stringleri
- Uygulama nullnet tabanlı olduğu için RPL stringleri bulunmamaktadır.

Hidden Diagnostic Mesajlar
- Normal çalışmada ekranda görünmeyen, ancak bazı durumlarda tetiklenen gizli teşhis mesajları tespit edilmiştir. Örnek olarak not for us : dizgisi verilebilir.

Hardcoded Config Değerleri
- Ağın donanım yapılandırma bilgilerini basan CC2420 CCA threshold %i ve açılışta kullanılan Contiki versiyonunun değerini barındıran Starting Contiki-NG-release/v4.8-625-g8518cbaff-dirty dizgileri, uygulamanın konfigürasyon yapısına dair bilgiler vermektedir.

---

# 5. Assembly / Instruction Analizi

Bu bölümde msp430-objdump -d çıktıları üzerinden değerlendirmeler yapılmıştır.

Instruction Sequence Analizi
- z1 platformu MSP430X mimarisine sahip olduğu için calla, pushm.a gibi 20-bit komut dizilimini kullanırken; sky platformu standart call, push gibi 16-bit komut dizilimi kullanmıştır.

Function Prologue/Epilogue
- Standart C fonksiyonlarında prologue ve epilogue işlemleri bulunur. Ancak main fonksiyonunun sonunda bir epilogue bloğu yoktur; fonksiyon bir sonsuz döngü ile bitmektedir.
- Diğer standart fonksiyonlarda ise prologue aşamasında z1 için pushm.a, sky için push komutları ile yazmaçların yığına kaydedildiği ve epilogue aşamasında z1 için reta, sky için ret komutu ile fonksiyondan çıkıldığı gözlemlenmiştir.

Register kullanımı
- Fonksiyon çağrılarında, parametrelerin aktarımı için r15, r14 ve r13 yazmaçları aktif olarak kullanılmaktadır.
- r1 yığın işlemlerini yönetirken, r2 bayrak durumlarını tutmaktadır. 
- Fonksiyon içerisinde değiştirilmemesi gereken veriler ise yedeği alınan r10 ve r11 gibi yazmaçlarda tutulmaktadır.

Stack Frame Yapısı
Stack Frame, derleyici tarafından lokal değişken boyutlarına göre ayarlanmıştır. Derin fonksiyon çağrılarında, stack çok daha yoğun kullanılmaktadır. r1 yazmacının kullanıldığı kısımlarda verilen değerlere bakılarak bu sonuca ulaşılabilir.

ISR Akışı
- Kesme servis rutinlerinin (ISR) akışı standart fonksiyonlardan tamamen farklı donanımsal mekanizmalara sahiptir.
- Örneğin timera1ISR çıktısı incelendiğinde, donanım kesmesi oluştuğunda bloğun en başında pushm.a #4, r15 komutu ile yazmaçların yığına eklendiği görülmüştür. Kesme görevi bittiğinde ise yığından yazmaçlar popm.a ile geri çekilmekte ve standart ret komutu yerine, donanımsal SR ve PC’yi yığından eş zamanlı geri yükleyen reti komutu kullanılmaktadır.

Loop Yapıları
- İmaj dosyasının genelinde döngü yapılarının kurulması, test (tst) ve koşullu geriye dallanma (jz, jnz, …)opkodlarının kombinasyonuyla sağlanmaktadır.

Branch Analizi
- Program akışındaki dallanma, cmp veya tst komutlarının durum yazmacı (r2) üzerindeki zero (Z) ve negative (N) bayraklarını tetiklemesi ve ardından gelen durumsal zıplama opkodları (jl gibi) ile yönetilmektedir.

Jump Table Analizi
- Bellekten adres okuyup doğrudan Program Counter'a ekleme yapan klasik bir Jump Table yapısı derleyici tarafından tercih edilmemiştir. Bunun yerine, ardışık if-else if tabanlı karşılaştırma zincirleri kullanılmıştır.

Function Call Graph
- Opkodlar içerisindeki call ve calla komutlarının hedef adresleri takip edilerek sistemin Fonksiyon Çağrı Grafiği çıkarılabilmektedir.

Inline Function Tespiti
- Kod boyutu son derece küçük olan ve tek bir temel amaca hizmet eden bazı kritik fonksiyonların, inline edilmeyerek bağımsız birer alt rutin olarak hafızada bırakıldığı tespit edilmiştir.

Compiler Optimization Davranışı
- Derleyicinin optimizasyon davranışı incelendiğinde, bellek erişim verimliliğinin ve yazmaç tahsisatının oldukça düşük tutulduğu görülmektedir.
- Değişkenlerin CPU çekirdek yazmaçlarında (r4-r11) lokal olarak önbelleğe alınmaması, derleyicinin hız veya kod boyutu optimizasyonu gütmeden, kaynak kodu satır satır makine diline doğrudan çevirdiğini ortaya koymaktadır.

Delay Loop Analizi
- İşletim sistemi çekirdek fonksiyonlarında, işlemci saat çevrimlerini harcayarak zaman gecikmesi yaratmayı amaçlayan, bir yazmacı döngü içinde sıfıra kadar eksilten klasik yazılımsal gecikme döngüleri bulunmamaktadır.
- Sistem, zamanlama ihtiyaçlarını işlemciyi kilitleyen yazılımsal döngülerle çözmek yerine donanımsal timer kesmeleri ve olay kuyrukları üzerinden asenkron olarak yürütmektedir.

Busy-wait Yapıları
- Firmware’in olay yönetim katmanında, belirli bir donanım veya yazılım bayrağının durum değiştirmesini bekleyen busy-wait mekanizmaları tespit edilmiştir. z1 platformuna ait main scheduler fonksiyonunun son bloğu buna bir örnektir.

Context Switching
- Gerçek zamanlı işletim sistemlerinde görülen donanımsal preemptive context switching mekanizmasının bu yapıda bulunmadığı gözlemlenmiştir.
- Bunun yerine Contiki-NG, cooperative bir görev geçiş modeli uygulamaktadır. call_process fonksiyonundaki geçiş mekanizması incelendiğinde, komple bir yazmaç matrisi yedeklemesi yerine sadece aktif süreç işaretçisinin değiştirilip fonksiyonun tetiklenmesi, sistemin hafif bağlam değişimi karakterini ortaya koymaktadır.

Scheduler Davranışı
- İşletim sisteminin scheduler stratejisi, olay kuyruğunun durumuna göre CPU'yu uyku modlarına sokup çıkaran bir güç yönetim algoritması olarak gözlenmiştir.

---

# 6. Source-Level Mapping Analizi

(Debug build varsa)

* Address → source line eşleme
* Function → source file eşleme
* ISR → source mapping
* Crash address çözümleme
* Optimization sonrası source mapping
* Inline edilmiş kodların tespiti

Araçlar:

* `msp430-addr2line`
* `msp430-objdump -S`
* `Ve üstteki araçların ARM versiyonları...`

---

# 7. ELF Yapısı Analizi

Bu bölümde msp430-radelf çıktıları üzerinden değerlendirmeler yapılmıştır.

ELF Header
- Class, Data, OS/ABI ve Type satırlarında yazan değerlere göre incelenen her iki imaj da 32-bitlik ELF32 sınıfında olup, verileri en düşük anlamlı bayt en düşük adrese gelecek şekilde (Little Endian) organize etmektedir. İşletim sistemi ABI alanı Standalone App olarak geçmektedir ve dosyalar yürütülebilir (EXEC) formattadır.

Section Header
- z1 imajında toplam 20, sky imajında ise 19 adet bölüm başlığı bulunmaktadır.
- Tabloda çalıştırılabilir makine kodları AX (Alloc, Execute) bayrağıyla, çalışma zamanında değişebilen RAM değişkenleri ise WA (Write, Alloc) bayrağıyla işaretlenmiştir.

Program Header
- Number of program headers alanındaki değerlere bakılır.
- Buna göre z1 imajında belleğe yüklenecek 5 adet program başlığı, sky imajında ise 4 adet program başlığı mevcuttur.

Symbol Table
- Tablonun alt kısımlarına doğru [18] .symtab isimli bölümün ve SYMTAB tipinin varlığını gözlemleyebiliriz.
- İmajlar strip edilmemiş olduğu için .symtab isimli özel bir bölüm tutulmaktadır. Bu tablo sayesinde hangi fonksiyonun veya değişkenin hangi HEX adresinde olduğu okunabilmektedir.

Relocation Entries
- Bölüm listesinde adı .rel ön ekiyle başlayan hiçbir satır olmamasından ve Type kısmının REL değil EXEC olmasından dolayı relokasyon tabloları bulunmamaktadır.

Debug Sections
- Geliştirme ortamında makine kodu yerine kaynak kod seviyesinde hata ayıklama yapabilmek için dosyanın içine yüksek boyutta debug verisi gömülmüştür.
- Bu bölümler Flash belleğe yüklenmez ancak ELF dosyası üzerinde büyük bir alan kaplar.
- Bölüm tablosundaki [8] numaralı satırdan [15] numaralı satıra kadar devam eden .debug_aranges, .debug_info, .debug_locgibi gibi bölümlerin varlığı bunu gösterir.

DWARF Info
- Hata ayıklama verilerinin .debug_line ve .debug_info şeklinde spesifik olarak adlandırılması, açık kaynaklı GCC araç zincirinin varsayılan olarak kullandığı DWARF standardının mimari kalıplarıdır.

Linker-Generated Metadata
- Linker, derleme işlemi esnasında kendi metadatalarını imajın içine gömmüştür.
- Bölüm isimlerinin saklandığı .shstrtab tablosu ve araç zinciri versiyonunu tutan .comment bölümü her iki imajda da mevcuttur.
- Ek olarak sadece z1 imajında Linker tarafından üretilmiş .gnu.attributes tablosu bulunmaktadır.

Startup Section
- Entry point address satırından, donanımların ROM bellek eşleme farklılıklarından dolayı z1 imajının başlatma noktası 0x3100 adresi olarak, sky imajının başlatma noktası ise 0x4000 adresi olarak bulunmuştur.

Vector Table
- İşlemciye bir donanım kesmesi geldiğinde işlemcinin hangi adrese dallanacağını gösteren donanımsal Kesme Vektör Tablosu, Flash belleğin fiziksel olarak en son bölgesine konumlandırılmıştır.
- Bölüm listesindeki [6] .vectors isimli satırın Addr sütununda yazan değerlere bakılırsa, z1 platformunda 0xffc0 adresinden, sky platformunda ise 0xffe0 adresinden başlanmaktadır.

Initialization Routines
- İşletim sistemi main fonksiyonuna girmeden önce ELF dosyasının bellek mimarisini donanımda hazırlayan C Runtime başlatma rutinleri devreye girmektedir.
- Entry Point adresinden uyanan kod öncelikle .rodata içerisindeki ilk değerleri statik .data bölümüne kopyalamakta, ardından ilk değeri olmayan değişkenleri içeren .bss bölümünü donanımsal olarak tamamen sıfırlamakta ve son olarak main bloğuna çağrı yapmaktadır.

---

# 8. Interrupt ve Donanım Analizi

Bu bölümde msp430-radelf, msp430-nm ve msp430-objdump çıktıları üzerinden değerlendirmeler yapılmıştır.

Interrupt Vector Table
- msp430-readelf -S tablosu üzerinden yapılan bellek haritası analizinde, donanım kesmelerini ilgili ISR fonksiyonlarına yönlendiren donanımsal Kesme Vektör Tablosu (.vectors) tespit edilmiştir.
- Bu tablo Flash belleğin en sonlarına doğru konumlandırılmıştır.
- Tablo z1 platformunda 0xffc0 adresinden, sky platformunda ise 0xffe0 adresinden başlamaktadır. İşlemci bir kesme aldığında doğrudan bu adrese giderek çalıştırılacak kodun yerini bulur.

GPIO Access Pattern
- Cihazların dış dünyayla olan pin bağlantıları donanım kesmeleri ile yönetilmektedir.
- Derlenmiş imajda dış donanımlardan gelen sinyalleri yakalamak üzere port1_isr ve irq_p2 fonksiyonları kullanılmıştır.

Timer Interrupt Kullanımı
- İşletim sisteminin scheduling işlevi doğrudan donanımsal timer kesmeleri ile sağlanmaktadır.
- msp430-objdump -d çıktılarında timera0 ve timera1 ISR fonksiyonları analiz edilmiştir.

UART ISR
- Sensör ağlarında terminal loglaması veya bilgisayar haberleşmesi için kullanılan donanımsal seri port (UART) asenkron kesmelerle çalışmaktadır.
- Platform farklılıklarından dolayı z1 cihazı uart0_rx_interrupt rutini ile veri alırken, sky platformunun UART kesmeleri için uart1_input_handler yapısını kullandığı görülmektedir.

Radio Interrupt Handler
- Kablosuz sensör ağkarının kullandığı IEEE 802.15.4 haberleşmesi interrupt-driven çalışır.
- Her iki cihazda da CC2420 kullanıldığı için, havadaki paket antene düşüp CRC kontrolünden geçtiğinde işlemciyi uyarmak için cc2420_interrupt ve cc2420_port1_interrupt rutinleri tetiklenmektedir.

ADC Access
- Yapılan sembol analizi sonucunda, her iki firmware imajında da işlemcinin dahili ADC donanımını tetikleyen herhangi bir kesme (ADC12_ISR gibi) veya ADC sürücü kodu bulunmamaktadır.

Sensor Polling
- Contiki-NG işletim sisteminin sensör mimarisinde polling ve interrupt tabanlı olmak üzere karma bir donanım erişim düzeni görülmektedir.
- Sensör süreçlerini periyodik olarak kontrol eden sensors_process yapısı mevcutken, ivmeölçer gibi anlık tepki gereken donanımların accm_int1_cb fonksiyonlarıyla doğrudan kesmeye bağlandığı tespit edilmiştir.

Low-Power Mode Geçişleri
- Gömülü sistemlerde r2 yazmacı uykuyu yönetir, bit set etmek (bis) uyutur, bit temizlemek (bic) uyandırır.Bu komutlar takip edilerek geçişler bulunur.

Clock Configuration
- Cihaz açılırken temel saati ayarlamak için clock_init tetiklenmekte, MSP430'un DCO donanımını kalibre etmek için ise msp430_init_dco ve msp430_sync_dco rutinleri kullanılmaktadır.

MSP430 Register Erişimleri
Çıktılar incelendiğinde RAM'deki değişkenler yerine doğrudan donanım yazmaçlarına yazıldığı tespit edilmiştir.

---

# 9. Networking Analizi

* Unicast kullanım tespiti
* Broadcast kullanım tespiti
* Multicast tespiti
* IPv6 stack kullanımı
* RPL routing analizi
* TSCH scheduler çağrıları
* MAC layer interaction
* Packet buffer kullanımı
* Neighbor table erişimi
* Radio transmission akışı
* Retransmission logic
* ACK mekanizmaları
* CSMA/TSCH farkları
* Contiki network API kullanımı

Araçlar:

* `msp430-nm`
* `msp430-objdump`
* `msp430-strings`
* `Ve üstteki araçların ARM versiyonları...`

---

# 10. Wireless / TSCH Analizi

* TSCH slot operation
* Channel hopping logic
* ASN handling
* Radio timing loops
* Synchronization routines
* Schedule management
* Packet timing
* MAC timing critical path
* Drift compensation
* Low-power radio behavior

Araçlar:

* `msp430-objdump`
* `msp430-nm`
* `Ve üstteki araçların ARM versiyonları...`

---

# 11. Sensor ve Peripheral Analizi

* Button handler
* LED driver
* UART usage
* SPI access
* I2C access
* ADC routines
* Sensor polling interval
* Interrupt-driven sensor logic
* GPIO toggle behavior
* Peripheral initialization sequence

Araçlar:

* `msp430-objdump`
* `msp430-nm`
* `Ve üstteki araçların ARM versiyonları...`

---

# 12. Algoritma Koşma / DSP / Matematiksel Analiz

* Floating-point kullanımı
* Fixed-point kullanımı
* Trigonometric computation
* Multiply/divide routines
* Software floating-point emulation
* DSP benzeri loop’lar
* Matrix operation izleri
* Signal processing pattern’leri
* Computational hotspot’lar
* Numerical optimization

Araçlar:

* `msp430-objdump`
* `msp430-gprof`
* `msp430-nm`
* `Ve üstteki araçların ARM versiyonları...`

---

# 13. Güç ve Performans Analizi

* Low-power mode geçişleri
* CPU-intensive function’lar
* Busy-wait detection
* Sleep/wakeup flow
* Timer usage intensity
* Radio duty cycle tahmini
* ISR yoğunluğu
* Function execution cost
* Flash/RAM efficiency
* Energy-heavy computation bölgeleri

Araçlar:

* `msp430-gprof`
* `msp430-objdump`
* `msp430-size`
* `Ve üstteki araçların ARM versiyonları...`

---

# 14. Coverage ve Profiling Analizi

* Function call frequency
* Execution hotspot
* Unused branch’ler
* Rarely executed path’ler
* Test coverage
* Critical execution path
* Runtime bottleneck’ler

Araçlar:

* `msp430-gcov`
* `msp430-gprof`
* `Ve üstteki araçların ARM versiyonları...`

---

# 15. Reverse Engineering Analizi

* Firmware behavior recovery
* Unknown firmware classification
* Feature inference
* Protocol inference
* ISR purpose discovery
* Hardware interaction recovery
* State machine extraction
* Scheduler reconstruction
* Event-flow reconstruction
* Network role inference

Araçlar:

* `msp430-objdump`
* `msp430-nm`
* `msp430-readelf`
* `msp430-strings`
* `Ve üstteki araçların ARM versiyonları...`

---

# 16. Compiler ve Optimization Analizi

* `-O0/-O2/-Os` farkları
* Inlining behavior
* Dead code elimination
* Constant folding
* Loop optimization
* Register allocation
* Tail-call optimization
* Branch optimization
* Macro expansion
* Preprocessor etkileri

Araçlar:

* `msp430-gcc`
* `msp430-cpp`
* `msp430-objdump`
* `Ve üstteki araçların ARM versiyonları...`

---

# 17. Linker ve Build Sistemi Analizi

* Section placement
* Link order
* Static library linkage
* Startup code
* Linker script behavior
* Vector placement
* Symbol resolution
* Relocation behavior

Araçlar:

* `msp430-ld`
* `msp430-ar`
* `msp430-ranlib`
* `msp430-readelf`
* `Ve üstteki araçların ARM versiyonları...`

---

# 18. Binary Transformation Analizi

* ELF → HEX conversion
* ELF → binary conversion
* Section extraction
* Symbol stripping
* Debug removal
* Firmware minimization
* Binary patch preparation

Araçlar:

* `msp430-objcopy`
* `msp430-strip`
* `Ve üstteki araçların ARM versiyonları...`

---

# 19. Library ve Archive Analizi

* Static library içeriği
* Object file extraction
* Archive symbol table
* Linked module analizi

Araçlar:

* `msp430-ar`
* `msp430-gcc-ar`
* `msp430-ranlib`
* `Ve üstteki araçların ARM versiyonları...`

---

# 20. Contiki-NG Özel Analizler

* PROCESS_THREAD recovery
* Protothread expansion
* Event-driven scheduler analizi
* etimer/ctimer usage
* PROCESS_BEGIN/END expansion
* PROCESS_YIELD flow
* NETSTACK interaction
* Packetbuf lifecycle
* uIP callback chain
* Rime stack usage

Araçlar:

* `msp430-cpp`
* `msp430-objdump`
* `msp430-nm`
* `Ve üstteki araçların ARM versiyonları...`

---

# 21. Güvenlik ve Robustness Analizi

* Hardcoded credential arama
* Debug backdoor izleri
* Buffer handling
* Unsafe memory access
* Stack-heavy routines
* Potential overflow bölgeleri
* Assert/debug remnants
* Information leakage string’leri

Araçlar:

* `msp430-strings`
* `msp430-objdump`
* `msp430-readelf`
* `Ve üstteki araçların ARM versiyonları...`

---

# 22. Karşılaştırmalı Firmware Analizi

Bu bölümde nullnet-unicast.z1 ve nullnet-unicast.sky dosyaları karşılaştırılarak açıklamalar yapılmıştır.

Code Size Farkı
- ROM boyutları karşılaştırıldığında sky platformunun kod boyutunun daha büyük olduğu tespit edilmiştir.
- İşletim sistemi ve uygulama kodlarının Flash bellekte kapladığı alan (.text + .data) hesaplandığında z1 firmware'i 30.585 byte, sky firmware'i ise 33.597 byte yer kaplamaktadır.

RAM Farkı
- Statik RAM alanları hesaplandığında z1 platformu 5.120 byte, sky platformu ise 7.512 byte hafıza kullanmıştır.

Function Count Farkı
- z1 platformu üzerinde gelişmiş donanımsal sensörler barındırdığı için I2C haberleşmesine ait ek fonksiyonlar (i2c_rx_interrupt, i2c_enable gibi) içerir. - Ancak sky platformunda bu sensör kodları bulunmaz, bunun yerine dairesel tampon (ringbuf_) ve ds2411 ID okuyucu gibi kendine özgü fonksiyonlar bulunur. Bu nedenle imajların fonksiyon sayıları ve çeşitlilikleri donanıma bağlı olarak farklılık göstermektedir.

ISR Yoğunluğu
- ISR yoğunluğu bakımından z1 platformu daha kalabalıktır.
- Her iki platform da zamanlayıcı ve radyo kesmelerini ortak kullanmaktadır ancak z1 platformunda donanımsal I2C sensörleri bulunduğu için i2c_rx_interrupt ve i2c_tx_interrupt gibi ek donanım kesmeleri tespit edilmiştir.

Networking Complexity
- Uygulama kodu NullNet tabanlı, basit ve IP'siz olmasına rağmen, derleyici ağ karmaşıklığı bakımından sky platformuna çok daha ağır bir networking katmanı bağlamıştır.
- z1 imajında sadece nullnet kalıntıları varken, sky imajının içinde ipv6, tcpip, 6lowpan, 6top, coap ve snmp gibi çok daha karmaşık IoT ağ protokollerinin izlerine rastlanmıştır.

---

# 23. Eğitimsel Reverse Engineering Görevleri

* Bir firmware’in ne yaptığını bulma
* hangi protokolü kullandığını çıkarma
* button/LED mapping bulma
* ISR’leri tanıma
* network role çıkarımı
* Kullandığı algoritmik blok tespiti
* energy-heavy bölgeleri bulma
* stripped firmware çözümleme


---
