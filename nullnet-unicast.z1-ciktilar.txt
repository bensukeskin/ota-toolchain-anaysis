msp430-readelf -h

user@409f9b5f2321:/work$ msp430-readelf -h nullnet-unicast.z1

ELF Header:
  Magic:   7f 45 4c 46 01 01 01 ff 00 00 00 00 00 00 00 00 
  Class:                             ELF32
  Data:                              2's complement, little endian
  Version:                           1 (current)
  OS/ABI:                            Standalone App
  ABI Version:                       0
  Type:                              EXEC (Executable file)
  Machine:                           Texas Instruments msp430 microcontroller
  Version:                           0x1
  Entry point address:               0x3100
  Start of program headers:          52 (bytes into file)
  Start of section headers:          93488 (bytes into file)
  Flags:                             0x10000001
  Size of this header:               52 (bytes)
  Size of program headers:           32 (bytes)
  Number of program headers:         5
  Size of section headers:           40 (bytes)
  Number of section headers:         20
  Section header string table index: 17


msp430-readelf -S

user@409f9b5f2321:/work$ msp430-readelf -S nullnet-unicast.z1

There are 20 section headers, starting at offset 0x16d30:

Section Headers:
  [Nr] Name              Type            Addr     Off    Size   ES Flg Lk Inf Al
  [ 0]                   NULL            00000000 000000 000000 00      0   0  0
  [ 1] .text             PROGBITS        00003100 0000d4 00676e 00  AX  0   0  2
  [ 2] .rodata           PROGBITS        00009870 006844 000613 00   A  0   0  4
  [ 3] .data             PROGBITS        00001100 006e58 0009b8 00  WA  0   0  2
  [ 4] .bss              NOBITS          00001ab8 007810 000a46 00  WA  0   0  2
  [ 5] .noinit           NOBITS          000024fe 007810 000002 00  WA  0   0  2
  [ 6] .vectors          PROGBITS        0000ffc0 007810 000040 00  AX  0   0  1
  [ 7] .comment          PROGBITS        00000000 007850 000030 01  MS  0   0  1
  [ 8] .debug_aranges    PROGBITS        00000000 007880 000588 00      0   0  8
  [ 9] .debug_info       PROGBITS        00000000 007e08 0052c2 00      0   0  1
  [10] .debug_abbrev     PROGBITS        00000000 00d0ca 0026b3 00      0   0  1
  [11] .debug_line       PROGBITS        00000000 00f77d 001d41 00      0   0  1
  [12] .debug_frame      PROGBITS        00000000 0114c0 0006a4 00      0   0  4
  [13] .debug_str        PROGBITS        00000000 011b64 0008e8 01  MS  0   0  1
  [14] .debug_loc        PROGBITS        00000000 01244c 004424 00      0   0  1
  [15] .debug_ranges     PROGBITS        00000000 016870 0003e8 00      0   0  1
  [16] .gnu.attributes   LOOS+ffffff5    00000000 016c58 000011 00      0   0  1
  [17] .shstrtab         STRTAB          00000000 016c69 0000c4 00      0   0  1
  [18] .symtab           SYMTAB          00000000 017050 0035f0 10     19 271  4
  [19] .strtab           STRTAB          00000000 01a640 0028c6 00      0   0  1
Key to Flags:
  W (write), A (alloc), X (execute), M (merge), S (strings)
  I (info), L (link order), G (group), T (TLS), E (exclude), x (unknown)
  O (extra OS processing required) o (OS specific), p (processor specific)
msp430-readelf -p .comment

user@409f9b5f2321:/work$ msp430-readelf -p .comment nullnet-unicast.z1

String dump of section '.comment':
  [     0]  GCC: (GNU) 4.7.2 20120920 (mspgcc dev 20120911)



msp430-size

user@409f9b5f2321:/work$ msp430-size nullnet-unicast.z1
   text	   data	    bss	    dec	    hex	filename
  28097	   2488	   2632	  33217	   81c1	nullnet-unicast.z1msp430-strings

user@409f9b5f2321:/work$ msp430-strings nullnet-unicast.z1

ADXL345 sensor
Accelerometer process
Button
CC2420 driver
Main
INFO
[%-4s: %-10s] 
Starting Contiki-NG-release/v4.8-625-g8518cbaff-dirty
- Routing: %s
- Net: %s
- MAC: %s
- 802.15.4 PANID: 0x%04x
- 802.15.4 Default channel: %u
Node ID: %u
Link-layer address: 
not for us : 
CSMA
Ctimer process
Event timer
(NULL LL addr)
%02x
INFO
[%-4s: %-10s] 
linkaddr_node_addr iss 
count.1 %d, remain: %d
Sending from node_id :%d, to linkaddr_node_addr :
Sending done from :%d
%d-)%d  
Received %u , node_id %d from 
 RSSI is : %d
distance is: %llu wcl: %llu - wcwcl: %llu 
okaf weights: %s
%llu %llu %llu %llu %llu %llu %llu %llu %d
kf: %s
NullNet unicast example
nullnet
nullrouting
INFO
[%-4s: %-10s] 
CC2420 CCA threshold %i
Sensors
Stack
[%-4s: %-10s] 
Check in inconsistent state: %ld vs. %ld
Check failed: %ld vs. %ld
Stack check
TMP102 sensor
(null)msp430-nm —-size-sort -S

user@409f9b5f2321:/work$ msp430-nm --size-sort -S nullnet-unicast.z1

00002414 00000001 B cc2420_last_correlation
00002410 00000001 B cc2420_last_rssi
00002418 00000001 B cc2420_sfd_counter
000023d2 00000001 b enabled
00002406 00000001 b enabled
000023f3 00000001 b fevent
000023f0 00000001 b hdrlen
000023eb 00000001 b initialized
000023f2 00000001 b lastevent
000023d6 00000001 b lock_off
000023d5 00000001 b lock_on
000023d4 00000001 b locked
000023ef 00000001 b mac_dsn
000023f4 00000001 b nevents
00002405 00000001 b num_sensors
000023d3 00000001 b poll_mode
000023f1 00000001 b poll_requested
00001a53 00000001 D prescale_lsb
000023ee 00000001 B prescale_msb
000024f8 00000001 B process_maxevents
00002424 00000001 B receive_data
000023d7 00000001 b receive_on
0000241d 00000001 B rx_byte_ctr
000023ed 00000001 b rx_byte_tot
00001a52 00000001 d send_on_cca
000024f9 00000001 B sensors_event
0000241c 00000001 B transmit_data1
00002427 00000001 B transmit_data2
00002407 00000001 b transmitting
00002420 00000001 B tx_byte_ctr
000023ec 00000001 b tx_byte_tot
000023d8 00000001 b was_on
00009b50 00000002 r CSWTCH.16
000024fe 00000002 B __wdt_clear_value
0000114e 00000002 D anchor_count
000023d0 00000002 b available_
00001d96 00000002 b buflen
00001d94 00000002 b bufptr
00002416 00000002 B cc2420_authority_level_of_sender
0000241a 00000002 B cc2420_sfd_end_time
00002412 00000002 B cc2420_sfd_start_time
00001ada 00000002 b channel
00001d80 00000002 b count.3283
00001d8e 00000002 b count4Edges.3284
000023cc 00000002 b counter
00001ba4 00000002 b ctimer_list_list
0000114c 00000002 d cur_break
0000114a 00000002 D curr_log_level_main
000023ce 00000002 b destination_
000061e2 00000002 t drop_route
00004ac4 00000002 T energest_flush
00004ac2 00000002 T energest_init
000023b8 00000002 b events.2068
000061c6 00000002 t global_repair
00002422 00000002 B i
000023b6 00000002 b i.2067
000061a8 00000002 t init
00001ab8 00000002 b int1_mask
00001aba 00000002 b int2_mask
00001ad4 00000002 b last_packet_timestamp
00001adc 00000002 b last_tar
000061bc 00000002 t leave_network
000061de 00000002 t link_callback
000061c8 00000002 t local_repair
00001148 00000002 d mac_pan_id
00002432 00000002 B msp430_dco_required
00001ae6 00000002 b neighbor_list_list
000023d9 00000002 b neighbor_memb_memb_used
000061e0 00000002 t neighbor_state_changed
000023b4 00000002 b next_rtimer
00001c8c 00000002 B node_id
000024c4 00000002 B nullnet_buf
000024c6 00000002 B nullnet_len
00001ad8 00000002 b prev_DACTST
00001ad6 00000002 b prev_MDMCTRL1
00001e20 00000002 B process_current
00001e22 00000002 B process_list
000061aa 00000002 t root_set_prefix
00002425 00000002 B rx_buf
00002428 00000002 B rx_buf_ptr
000023ba 00000002 b stack_top.2107
00001ba6 00000002 b timerlist
0000241e 00000002 B tx_buf_ptr
00002498 00000004 B Xwcl
000024c0 00000004 B Xwcwcl
000024ac 00000004 B Ywcl
00002478 00000004 B Ywcwcl
0000240c 00000004 B accm_int1_cb
00002408 00000004 B accm_int2_cb
00009986 00000004 R autostart_processes
00001ade 00000004 b count
00001d90 00000004 b current_callback
000061d2 00000004 t ext_header_hbh_update
000061ca 00000004 t ext_header_remove
000061da 00000004 t ext_header_srh_get_next_hop
000061d6 00000004 t ext_header_srh_update
000061ce 00000004 t ext_header_update
000039fc 00000004 t get_object
000061b4 00000004 t get_root_ipaddr
000061b8 00000004 t get_sr_node_ipaddr
000061e4 00000004 t is_in_leaf_mode
0000559e 00000004 T list_head
00001a38 00000004 d next
00001ba8 00000004 b next_expiration
000061be 00000004 t node_has_joined
000061c2 00000004 t node_is_reachable
000061b0 00000004 t node_is_root
00002444 00000004 B payXwcl_d
000024b0 00000004 B payYwcl_d
00002494 00000004 B payda_wcl
000024b4 00000004 B payda_wcwcl
000061ac 00000004 t root_start
00001ae2 00000004 b seconds
000024fa 00000004 B sensors_flags
00003a00 00000004 t set_object
000023c8 00000004 b uart0_input_handler
000048b8 00000006 T csma_security_parse_frame
00004cd6 00000006 T frame802154_get_pan_id
00005548 00000006 T leds_init
00005598 00000006 T list_init
000061a2 00000006 T nullnet_set_input_callback
000048c4 00000006 t off
000048be 00000006 t on
0000620e 00000006 T packetbuf_datalen
00006208 00000006 T packetbuf_hdrptr
00006202 00000006 T packetbuf_set_datalen
00007ab4 00000006 T powf
0000687e 00000006 T random_init
00006884 00000006 T random_rand
000068a6 00000006 T rtimer_arch_schedule
000068ac 00000006 T rtimer_init
00004902 00000006 t send_packet
00006cc8 00000006 t value
000036e4 00000006 T watchdog_interrupt
00009a10 00000008 R __thenan_sf
0000248c 00000008 B averageX
000024b8 00000008 B averageY
000099f8 00000008 r bp
00001a10 00000008 d bufmem
000023fd 00000008 b bufmem_memb_used
00001a08 00000008 d buframmem
000023f5 00000008 b buframmem_memb_used
000053d4 00000008 t create
00002470 00000008 B currentXwcl
00002468 00000008 B currentXwcwcl
00002450 00000008 B currentYwcl
000024a4 00000008 B currentYwcwcl
00001acc 00000008 b debouncetimer
00009a08 00000008 r dp_h
00009a00 00000008 r dp_l
000053dc 00000008 t hdr_length
00006124 00000008 t init
00005572 00000008 T linkaddr_copy
0000242a 00000008 B linkaddr_node_addr
0000997e 00000008 R linkaddr_null
00001128 00000008 d metadata_memb
000023e3 00000008 b metadata_memb_memb_used
00001e18 00000008 b mgt_timer
00001118 00000008 d neighbor_memb
000024f0 00000008 B node_mac
00001120 00000008 d packet_memb
000023db 00000008 b packet_memb_memb_used
00002448 00000008 B payXwcl
0000243c 00000008 B payXwcwcl
00002484 00000008 B payYwcl
00002434 00000008 B payYwcwcl
00001a30 00000008 D sensors
00002458 00000008 B sumX
00002460 00000008 B sumXwcwcl
0000247c 00000008 B sumY
0000249c 00000008 B sumYwcwcl
00001abc 00000008 b suppressTimer1
00001ac4 00000008 b suppressTimer2
00003b8a 0000000a t cc2420_receiving_packet
00004b36 0000000a T etimer_request_poll
00005488 0000000a T i2c_busy
0000566a 0000000a T mac_sequence_init
00006362 0000000a T packetbuf_attr
00006214 0000000a T packetbuf_hdrlen
00003b94 0000000a t pending_packet
0000588c 0000000a T splhigh_
000096f4 0000000a T srand
00006be2 0000000a T tmp102_stop
00001100 0000000c D accmeter_process
0000110c 0000000c D cc2420_process
0000446e 0000000c T clock_delay
00001130 0000000c D ctimer_process
000023bc 0000000c b et.2129
00004c76 0000000c T etimer_pending
0000113c 0000000c D etimer_process
00009972 0000000c R framer_802154
0000449e 0000000c T init_platform
0000558c 0000000c T linkaddr_set_node_addr
0000561e 0000000c T list_item_next
00001150 0000000c D nullnet_example_process
0000621e 0000000c T packetbuf_dataptr
00006356 0000000c T packetbuf_set_attr
00006264 0000000c T packetbuf_totlen
00001d82 0000000c b periodic_timer.3282
00001a18 0000000c D sensors_process
00001a24 0000000c D stack_check_process
000098f4 0000000e R adxl345
00009902 0000000e R button_sensor
00004c68 0000000e T etimer_expired
000054c8 0000000e T leds_arch_init
00005932 0000000e T netstack_init
0000998a 0000000e R nullnet_driver
00006380 0000000e T packetbuf_addr
0000638e 0000000e T packetbuf_holds_broadcast
00006642 0000000e T process_alloc_event
000066f8 0000000e T process_nevents
0000688a 0000000e T rtimer_arch_init
00006898 0000000e T rtimer_arch_now
000099ea 0000000e R tmp102
00006cde 0000000e T uart0_active
000023a4 00000010 b bufmem_memb_mem
000048a8 00000010 T csma_security_create_frame
00004a8a 00000010 T ctimer_set
0000560e 00000010 T list_length
00009948 00000010 r output_power
000024c8 00000010 B packetbuf_addrs
00008d68 00000010 T printf
00006cce 00000010 T putchar
00003df0 00000012 t cc2420_send
00004c56 00000012 T etimer_reset
00004c44 00000012 T etimer_set
00005560 00000012 T leds_off
0000554e 00000012 T leds_on
0000557a 00000012 T linkaddr_cmp
000055a2 00000012 T list_tail
000062d4 00000012 T packetbuf_clear
0000639c 00000012 T platform_init_stage_one
00006750 00000012 T process_post_synch
000067b0 00000012 T queuebuf_init
00006810 00000012 T queuebuf_update_attr_from_packetbuf
000036ea 00000012 t status
00006bac 00000012 t status
00006d8c 00000012 T watchdog_init
00006d64 00000012 T watchdog_periodic
00003684 00000014 T i2c_rx_interrupt
000054b4 00000014 T i2c_transmit_n
00005780 00000014 T mac_call_sent_callback
0000598c 00000014 T node_id_init
0000636c 00000014 T packetbuf_set_addr
00006d50 00000014 T watchdog_start
00001a3c 00000016 d adxl345_default_settings
00003946 00000016 T autostart_start
0000401c 00000016 T cc2420_interrupt
000041e2 00000016 T cc2420_set_cca_threshold
00004c82 00000016 T etimer_next_expiration_time
00006cec 00000016 T uart0_writeb
00006d76 00000016 T watchdog_stop
00004a28 00000018 T ctimer_init
00005674 00000018 T mac_sequence_set_dsn
000024d8 00000018 B packetbuf_attrs
00006798 00000018 T process_poll
0000395c 00000018 t status
000039e2 0000001a T cc2420_arch_init
0000442c 0000001a T clock_time
00009958 0000001a R csma_driver
0000488e 0000001a T csma_output_init
00003c30 0000001a t flushrx
00003b70 0000001a t on
000061e8 0000001a T packetbuf_hdrreduce
00008dd0 0000001a T sprintf
00003a04 0000001a t strobe
00006650 0000001c T process_init
00006b90 0000001c T timer_reset
00006b4a 0000001c T timer_set
0000405e 0000001e T cc2420_get_txpower
00003b52 0000001e t get_status
00003858 0000001e t value
00006de4 0000001e T xmem_init
00004968 00000020 t init
00003974 00000020 t value
00008d78 00000022 t append
00003d68 00000022 T cc2420_on
00005492 00000022 T i2c_enable
00006310 00000022 T packetbuf_attr_copyto
00003698 00000022 T timera0
00003b9e 00000022 t wait_for_transmission
0000447a 00000024 T clock_wait
00006332 00000024 T packetbuf_attr_copyfrom
00006bbe 00000024 T tmp102_init
00003bc0 00000024 t wait_for_status
0000350a 00000026 T cc2420_timerb1_interrupt
00003920 00000026 t configure
00006bec 00000026 t configure
000055e8 00000026 T list_add
000096ce 00000026 T rand
000068b2 00000026 T rtimer_run_next
00003c72 00000028 t RELEASE_LOCK
00004446 00000028 T clock_init
00004a9a 00000028 T ctimer_stop
00004e64 00000028 T frame802154_is_broadcast_addr
00005864 00000028 T msp430_init_dco
00003c4a 00000028 t off
000062ac 00000028 T packetbuf_attr_clear
0000372a 0000002a t accm_write_stream
0000583a 0000002a T memb_inmemb
000062e6 0000002a T packetbuf_copyfrom
00006822 0000002a T queuebuf_free
0000699a 0000002a T sensors_changed
00006b66 0000002a T timer_expired
000036ba 0000002a T uart0_rx_interrupt
00004032 0000002c T cc2420_set_txpower
000096fe 0000002c T memcmp
000096a2 0000002c T puts
00003cfa 0000002c t set_poll_mode
000036fc 0000002e t accm_write_reg
00005904 0000002e T msp430_cpu_init
000069f6 0000002e T stack_check_init
00003e02 00000030 T cc2420_off
00006612 00000030 t do_poll
00001e24 00000030 b events
0000541a 00000030 T i2c_transmitinit
00001b34 00000030 b packet_memb_memb_mem
00003cca 00000030 t set_auto_ack
00003c9a 00000030 t set_frame_filtering
000038ee 00000032 T accm_stop
00004e8c 00000032 T frame802154_hdrlen
00005808 00000032 T memb_free
0000684c 00000032 T queuebuf_to_packetbuf
000069c4 00000032 T spi_init
0000616e 00000034 t input
000054d6 00000034 T leds_arch_get
000055b4 00000034 T list_remove
00008d9a 00000036 t call_vuprintf
000053e4 00000036 T i2c_receiveinit
00005794 00000036 T memb_init
00006762 00000036 T process_start
00009910 00000038 R cc2420_driver
000048ca 00000038 t max_payload
00003b1a 00000038 t write_fifo_buf
00003f96 0000003a T cc2420_set_channel
0000622a 0000003a T packetbuf_copyto
000088de 0000003c T __fixunssfsi
000034ce 0000003c T irq_p2
00006270 0000003c T packetbuf_hdralloc
00004c98 0000003e T etimer_stop
0000544a 0000003e T i2c_receive_n
0000550a 0000003e T leds_arch_set
000057ca 0000003e T memb_alloc
0000ffc0 00000040 T __ivtbl_32
00004c04 00000040 t add_timer
0000654a 00000040 t call_process
0000562a 00000040 T log_lladdr
00001b64 00000040 b metadata_memb_memb_mem
00003d26 00000042 t cc2420_prepare
0000612c 00000042 t output
00003a64 00000044 t setreg
00003a1e 00000046 t getreg
00006d9e 00000046 t wait_ready
0000407c 00000048 T cc2420_rssi
00004a40 0000004a T ctimer_set_with_process
00006706 0000004a T process_post
00008226 0000004c T __addsf3
00003fd0 0000004c T cc2420_set_pan_addr
00003be4 0000004c t getrxdata
00001ae8 0000004c b neighbor_memb_memb_mem
00005940 0000004c T node_id_z1_restore
00008c8e 0000004e T __gesf2
00008602 0000004e T __gtsf2
0000869e 0000004e T __lesf2
00008650 0000004e T __ltsf2
00003994 0000004e t configure
000067c2 0000004e T queuebuf_new_from_packetbuf
00006d02 0000004e T uart0_init
00008272 00000050 T __subsf3
00009998 00000052 R nullrouting_driver
00003754 00000054 t accm_read_reg
00003e32 00000054 t cc2420_cca
000064f6 00000054 T platform_idle
00006a24 00000054 T stack_check_get_usage
000037a8 00000056 t process_thread_accmeter_process
00003f40 00000056 t process_thread_cc2420_process
00006c70 00000058 T tmp102_read_temp_x100
000037fe 0000005a t accm_read_axis.part.0
00009812 0000005c T memset
00006c12 0000005e T tmp102_read_reg
00004908 00000060 t input_packet
00001a54 00000064 D percentage10
00003d8a 00000066 t cc2420_transmit
000044aa 00000066 t schedule_transmission
00008874 0000006a T __clzsi2
00004ebe 0000006e T frame802154_create_fcf
0000568c 0000006e T mac_sequence_is_duplicate
00005896 0000006e T msp430_sync_dco
00004ac6 00000070 t update_time
00006484 00000072 T platform_init_stage_three
00003aa8 00000072 t write_ram
00003876 00000078 T accm_init
00001d98 00000080 b packetbuf_aligned
00003600 00000084 T i2c_tx_interrupt
0000344a 00000084 T port1_isr
000056fa 00000086 T mac_sequence_register_seqno
00004510 00000086 t tx_done
0000658a 00000088 t exit_process
00006e02 00000088 T xmem_pread
00008cdc 0000008c T __fixsfsi
00005000 0000008c T frame802154_parse_fcf
0000666c 0000008c T process_run
00005336 0000009e t create_frame
000051e8 0000009e t parse
00004988 000000a0 t process_thread_ctimer_process
000086ec 000000a4 T __floatsisf
00008bea 000000a4 T __fpcmp_parts_f
00004dbc 000000a8 t field_len
00005286 000000b0 T framer_802154_setup_params
00003e86 000000ba t cc2420_read
000068d8 000000c2 t process_thread_sensors_process
00004b40 000000c4 t process_thread_etimer_process
00003530 000000d0 T timera1
00006a78 000000d2 t process_thread_stack_check_process
00004f2c 000000d4 T frame802154_create
000063ae 000000d6 T platform_init_stage_two
00004cdc 000000e0 T frame802154_has_panid
00001bac 000000e0 b received_seqnos
00008790 000000e4 T __floatunsisf
0000972a 000000e8 T memcpy
00004342 000000ea T cc2420_init
00001c8e 000000f2 B rssiList
00009d7c 00000100 R __clz_tab
00008ade 0000010c T __unpack_f
000040c4 0000011e t get_value
00007d78 00000120 T __fixunssfdi
00007e98 00000124 T __floatundisf
000084c0 00000142 T __divsf3
00004746 00000148 T csma_output_packet
000041f8 0000014a t set_value
00007c22 00000156 T __ieee754_sqrtf
0000508c 0000015c T frame802154_parse
00007aba 00000168 T scalbnf
00008dea 00000176 t print_field
000059a0 00000194 t process_thread_nullnet_example_process
00004596 000001b0 t transmit_from_queue
0000891a 000001c4 T __pack_f
0000313e 000001c4 T main
000082c2 000001fe T __mulsf3
00007fbc 0000026a t _fpadd_parts
00001620 000003e8 D node_positions
0000115c 000004c4 D anchor_nodes
00001e54 00000550 b buframmem_memb_mem
00005b34 000005f0 T input_callback
00008f60 00000742 T vuprintf
00006e8a 00000c2a T __ieee754_powf






msp430-objdump -f

user@409f9b5f2321:/work$ msp430-objdump -f nullnet-unicast.z1

nullnet-unicast.z1:     file format elf32-msp430
architecture: msp430:430X, flags 0x00000112:
EXEC_P, HAS_SYMS, D_PAGED
start address 0x00003100
msp430-objdump -d

user@113c3d69a7ba:/work$ msp430-objdump -d nullnet-unicast.z1


nullnet-unicast.z1:     file format elf32-msp430


Disassembly of section .text:

00003100 <__watchdog_support>:
    3100:	55 42 20 01 	mov.b	&0x0120,r5	
    3104:	35 d0 08 5a 	bis	#23048,	r5	;#0x5a08
    3108:	82 45 fe 24 	mov	r5,	&0x24fe	

0000310c <__init_stack>:
    310c:	31 40 00 31 	mov	#12544,	r1	;#0x3100

00003110 <__do_copy_data>:
    3110:	3f 40 b8 09 	mov	#2488,	r15	;#0x09b8
    3114:	0f 93       	tst	r15		
    3116:	08 24       	jz	$+18     	;abs 0x3128
    3118:	92 42 fe 24 	mov	&0x24fe,&0x0120	
    311c:	20 01 
    311e:	2f 83       	decd	r15		
    3120:	9f 4f 84 9e 	mov	-24956(r15),4352(r15);0x9e84(r15), 0x1100(r15)
    3124:	00 11 
    3126:	f8 23       	jnz	$-14     	;abs 0x3118

00003128 <__do_clear_bss>:
    3128:	3f 40 46 0a 	mov	#2630,	r15	;#0x0a46
    312c:	0f 93       	tst	r15		
    312e:	07 24       	jz	$+16     	;abs 0x313e
    3130:	92 42 fe 24 	mov	&0x24fe,&0x0120	
    3134:	20 01 
    3136:	1f 83       	dec	r15		
    3138:	cf 43 b8 1a 	mov.b	#0,	6840(r15);r3 As==00, 0x1ab8(r15)
    313c:	f9 23       	jnz	$-12     	;abs 0x3130

0000313e <main>:
    313e:	b0 13 9c 63 	calla	#0x0639c	
    3142:	b0 13 46 44 	calla	#0x04446	
    3146:	b0 13 ac 68 	calla	#0x068ac	
    314a:	b0 13 50 66 	calla	#0x06650	
    314e:	0e 43       	clr	r14		
    3150:	3f 40 3c 11 	mov	#4412,	r15	;#0x113c
    3154:	b0 13 62 67 	calla	#0x06762	
    3158:	b0 13 28 4a 	calla	#0x04a28	
    315c:	b0 13 8c 6d 	calla	#0x06d8c	
    3160:	b0 13 c2 4a 	calla	#0x04ac2	
    3164:	b0 13 f6 69 	calla	#0x069f6	
    3168:	b0 13 ae 63 	calla	#0x063ae	
    316c:	b0 13 b0 67 	calla	#0x067b0	
    3170:	b0 13 32 59 	calla	#0x05932	
    3174:	b0 13 8c 59 	calla	#0x0598c	
    3178:	b2 90 03 00 	cmp	#3,	&0x114a	;#0x0003
    317c:	4a 11 
    317e:	0e 38       	jl	$+30     	;abs 0x319c
    3180:	30 12 52 9a 	push	#-26030	;#0x9a52
    3184:	30 12 57 9a 	push	#-26025	;#0x9a57
    3188:	30 12 5c 9a 	push	#-26020	;#0x9a5c
    318c:	b0 13 68 8d 	calla	#0x08d68	
    3190:	31 50 06 00 	add	#6,	r1	;#0x0006
    3194:	3f 40 6b 9a 	mov	#-26005,r15	;#0x9a6b
    3198:	b0 13 a2 96 	calla	#0x096a2	
    319c:	b2 90 03 00 	cmp	#3,	&0x114a	;#0x0003
    31a0:	4a 11 
    31a2:	11 38       	jl	$+36     	;abs 0x31c6
    31a4:	30 12 52 9a 	push	#-26030	;#0x9a52
    31a8:	30 12 57 9a 	push	#-26025	;#0x9a57
    31ac:	30 12 5c 9a 	push	#-26020	;#0x9a5c
    31b0:	b0 13 68 8d 	calla	#0x08d68	
    31b4:	31 50 06 00 	add	#6,	r1	;#0x0006
    31b8:	12 12 98 99 	push	&0x9998	
    31bc:	30 12 a1 9a 	push	#-25951	;#0x9aa1
    31c0:	b0 13 68 8d 	calla	#0x08d68	
    31c4:	21 52       	add	#4,	r1	;r2 As==10
    31c6:	b2 90 03 00 	cmp	#3,	&0x114a	;#0x0003
    31ca:	4a 11 
    31cc:	11 38       	jl	$+36     	;abs 0x31f0
    31ce:	30 12 52 9a 	push	#-26030	;#0x9a52
    31d2:	30 12 57 9a 	push	#-26025	;#0x9a57
    31d6:	30 12 5c 9a 	push	#-26020	;#0x9a5c
    31da:	b0 13 68 8d 	calla	#0x08d68	
    31de:	31 50 06 00 	add	#6,	r1	;#0x0006
    31e2:	12 12 8a 99 	push	&0x998a	
    31e6:	30 12 b0 9a 	push	#-25936	;#0x9ab0
    31ea:	b0 13 68 8d 	calla	#0x08d68	
    31ee:	21 52       	add	#4,	r1	;r2 As==10
    31f0:	b2 90 03 00 	cmp	#3,	&0x114a	;#0x0003
    31f4:	4a 11 
    31f6:	11 38       	jl	$+36     	;abs 0x321a
    31f8:	30 12 52 9a 	push	#-26030	;#0x9a52
    31fc:	30 12 57 9a 	push	#-26025	;#0x9a57
    3200:	30 12 5c 9a 	push	#-26020	;#0x9a5c
    3204:	b0 13 68 8d 	calla	#0x08d68	
    3208:	31 50 06 00 	add	#6,	r1	;#0x0006
    320c:	12 12 58 99 	push	&0x9958	
    3210:	30 12 bb 9a 	push	#-25925	;#0x9abb
    3214:	b0 13 68 8d 	calla	#0x08d68	
    3218:	21 52       	add	#4,	r1	;r2 As==10
    321a:	b2 90 03 00 	cmp	#3,	&0x114a	;#0x0003
    321e:	4a 11 
    3220:	11 38       	jl	$+36     	;abs 0x3244
    3222:	30 12 52 9a 	push	#-26030	;#0x9a52
    3226:	30 12 57 9a 	push	#-26025	;#0x9a57
    322a:	30 12 5c 9a 	push	#-26020	;#0x9a5c
    322e:	b0 13 68 8d 	calla	#0x08d68	
    3232:	31 50 06 00 	add	#6,	r1	;#0x0006
    3236:	30 12 cd ab 	push	#-21555	;#0xabcd
    323a:	30 12 c6 9a 	push	#-25914	;#0x9ac6
    323e:	b0 13 68 8d 	calla	#0x08d68	
    3242:	21 52       	add	#4,	r1	;r2 As==10
    3244:	b2 90 03 00 	cmp	#3,	&0x114a	;#0x0003
    3248:	4a 11 
    324a:	11 38       	jl	$+36     	;abs 0x326e
    324c:	30 12 52 9a 	push	#-26030	;#0x9a52
    3250:	30 12 57 9a 	push	#-26025	;#0x9a57
    3254:	30 12 5c 9a 	push	#-26020	;#0x9a5c
    3258:	b0 13 68 8d 	calla	#0x08d68	
    325c:	31 50 06 00 	add	#6,	r1	;#0x0006
    3260:	30 12 1a 00 	push	#26		;#0x001a
    3264:	30 12 e0 9a 	push	#-25888	;#0x9ae0
    3268:	b0 13 68 8d 	calla	#0x08d68	
    326c:	21 52       	add	#4,	r1	;r2 As==10
    326e:	b2 90 03 00 	cmp	#3,	&0x114a	;#0x0003
    3272:	4a 11 
    3274:	11 38       	jl	$+36     	;abs 0x3298
    3276:	30 12 52 9a 	push	#-26030	;#0x9a52
    327a:	30 12 57 9a 	push	#-26025	;#0x9a57
    327e:	30 12 5c 9a 	push	#-26020	;#0x9a5c
    3282:	b0 13 68 8d 	calla	#0x08d68	
    3286:	31 50 06 00 	add	#6,	r1	;#0x0006
    328a:	12 12 8c 1c 	push	&0x1c8c	
    328e:	30 12 00 9b 	push	#-25856	;#0x9b00
    3292:	b0 13 68 8d 	calla	#0x08d68	
    3296:	21 52       	add	#4,	r1	;r2 As==10
    3298:	b2 90 03 00 	cmp	#3,	&0x114a	;#0x0003
    329c:	4a 11 
    329e:	0f 38       	jl	$+32     	;abs 0x32be
    32a0:	30 12 52 9a 	push	#-26030	;#0x9a52
    32a4:	30 12 57 9a 	push	#-26025	;#0x9a57
    32a8:	30 12 5c 9a 	push	#-26020	;#0x9a5c
    32ac:	b0 13 68 8d 	calla	#0x08d68	
    32b0:	31 50 06 00 	add	#6,	r1	;#0x0006
    32b4:	30 12 0d 9b 	push	#-25843	;#0x9b0d
    32b8:	b0 13 68 8d 	calla	#0x08d68	
    32bc:	21 53       	incd	r1		
    32be:	b2 90 03 00 	cmp	#3,	&0x114a	;#0x0003
    32c2:	4a 11 
    32c4:	04 38       	jl	$+10     	;abs 0x32ce
    32c6:	3f 40 2a 24 	mov	#9258,	r15	;#0x242a
    32ca:	b0 13 2a 56 	calla	#0x0562a	
    32ce:	b2 90 03 00 	cmp	#3,	&0x114a	;#0x0003
    32d2:	4a 11 
    32d4:	04 38       	jl	$+10     	;abs 0x32de
    32d6:	3f 40 0a 00 	mov	#10,	r15	;#0x000a
    32da:	b0 13 ce 6c 	calla	#0x06cce	
    32de:	b0 13 84 64 	calla	#0x06484	
    32e2:	3f 40 86 99 	mov	#-26234,r15	;#0x9986
    32e6:	b0 13 46 39 	calla	#0x03946	
    32ea:	b0 13 50 6d 	calla	#0x06d50	
    32ee:	b0 13 6c 66 	calla	#0x0666c	
    32f2:	0b 4f       	mov	r15,	r11	
    32f4:	b0 13 64 6d 	calla	#0x06d64	
    32f8:	4b 93       	tst.b	r11		
    32fa:	f9 23       	jnz	$-12     	;abs 0x32ee
    32fc:	b0 13 f6 64 	calla	#0x064f6	
    3300:	f6 3f       	jmp	$-18     	;abs 0x32ee

00003302 <__stop_progExec__>:
    3302:	32 d0 f0 00 	bis	#240,	r2	;#0x00f0
    3306:	fd 3f       	jmp	$-4      	;abs 0x3302

00003308 <__ctors_end>:
    3308:	30 40 0c 33 	br	#0x330c	

0000330c <_unexpected_>:
    330c:	00 13       	reti			

0000330e <__mulsi3>:
    330e:	1b 14       	pushm.a	#2,	r11	
    3310:	0b 43       	clr	r11		
    3312:	0a 43       	clr	r10		
    3314:	07 3c       	jmp	$+16     	;abs 0x3324
    3316:	5d 03       	rrum	#1,	r13	
    3318:	0c 10       	rrc	r12		
    331a:	02 28       	jnc	$+6      	;abs 0x3320
    331c:	0a 5e       	add	r14,	r10	
    331e:	0b 6f       	addc	r15,	r11	
    3320:	0e 5e       	rla	r14		
    3322:	0f 6f       	rlc	r15		
    3324:	0c 93       	tst	r12		
    3326:	f7 23       	jnz	$-16     	;abs 0x3316
    3328:	0d 93       	tst	r13		
    332a:	f5 23       	jnz	$-20     	;abs 0x3316
    332c:	0e 4a       	mov	r10,	r14	
    332e:	0f 4b       	mov	r11,	r15	
    3330:	1a 16       	popm.a	#2,	r11	
    3332:	10 01       	reta			

00003334 <__udivhi3>:
    3334:	7c 40 10 00 	mov.b	#16,	r12	;#0x0010
    3338:	0d 4e       	mov	r14,	r13	
    333a:	0e 43       	clr	r14		
    333c:	0f 5f       	rla	r15		
    333e:	0e 6e       	rlc	r14		
    3340:	0e 9d       	cmp	r13,	r14	
    3342:	02 28       	jnc	$+6      	;abs 0x3348
    3344:	0e 8d       	sub	r13,	r14	
    3346:	1f d3       	bis	#1,	r15	;r3 As==01
    3348:	1c 83       	dec	r12		
    334a:	f8 23       	jnz	$-14     	;abs 0x333c
    334c:	10 01       	reta			

0000334e <__umodhi3>:
    334e:	b0 13 34 33 	calla	#0x03334	
    3352:	0f 4e       	mov	r14,	r15	
    3354:	10 01       	reta			

00003356 <__udivsi3>:
    3356:	2b 14       	pushm.a	#3,	r11	
    3358:	79 40 20 00 	mov.b	#32,	r9	;#0x0020
    335c:	0a 4c       	mov	r12,	r10	
    335e:	0b 4d       	mov	r13,	r11	
    3360:	0c 43       	clr	r12		
    3362:	0d 43       	clr	r13		
    3364:	0e 5e       	rla	r14		
    3366:	0f 6f       	rlc	r15		
    3368:	0c 6c       	rlc	r12		
    336a:	0d 6d       	rlc	r13		
    336c:	0d 9b       	cmp	r11,	r13	
    336e:	06 28       	jnc	$+14     	;abs 0x337c
    3370:	02 20       	jnz	$+6      	;abs 0x3376
    3372:	0c 9a       	cmp	r10,	r12	
    3374:	03 28       	jnc	$+8      	;abs 0x337c
    3376:	0c 8a       	sub	r10,	r12	
    3378:	0d 7b       	subc	r11,	r13	
    337a:	1e d3       	bis	#1,	r14	;r3 As==01
    337c:	19 83       	dec	r9		
    337e:	f2 23       	jnz	$-26     	;abs 0x3364
    3380:	29 16       	popm.a	#3,	r11	
    3382:	10 01       	reta			

00003384 <__umodsi3>:
    3384:	b0 13 56 33 	calla	#0x03356	
    3388:	0e 4c       	mov	r12,	r14	
    338a:	0f 4d       	mov	r13,	r15	
    338c:	10 01       	reta			

0000338e <__xabi_udivmod64>:
    338e:	37 14       	pushm.a	#4,	r7	
    3390:	30 12 40 00 	push	#64		;#0x0040
    3394:	04 48       	mov	r8,	r4	
    3396:	05 49       	mov	r9,	r5	
    3398:	06 4a       	mov	r10,	r6	
    339a:	07 4b       	mov	r11,	r7	
    339c:	08 43       	clr	r8		
    339e:	09 43       	clr	r9		
    33a0:	0a 43       	clr	r10		
    33a2:	0b 43       	clr	r11		
    33a4:	0c 5c       	rla	r12		
    33a6:	0d 6d       	rlc	r13		
    33a8:	0e 6e       	rlc	r14		
    33aa:	0f 6f       	rlc	r15		
    33ac:	08 68       	rlc	r8		
    33ae:	09 69       	rlc	r9		
    33b0:	0a 6a       	rlc	r10		
    33b2:	0b 6b       	rlc	r11		
    33b4:	0b 97       	cmp	r7,	r11	
    33b6:	0e 28       	jnc	$+30     	;abs 0x33d4
    33b8:	08 20       	jnz	$+18     	;abs 0x33ca
    33ba:	0a 96       	cmp	r6,	r10	
    33bc:	0b 28       	jnc	$+24     	;abs 0x33d4
    33be:	05 20       	jnz	$+12     	;abs 0x33ca
    33c0:	09 95       	cmp	r5,	r9	
    33c2:	08 28       	jnc	$+18     	;abs 0x33d4
    33c4:	02 20       	jnz	$+6      	;abs 0x33ca
    33c6:	08 94       	cmp	r4,	r8	
    33c8:	05 28       	jnc	$+12     	;abs 0x33d4
    33ca:	08 84       	sub	r4,	r8	
    33cc:	09 75       	subc	r5,	r9	
    33ce:	0a 76       	subc	r6,	r10	
    33d0:	0b 77       	subc	r7,	r11	
    33d2:	1c d3       	bis	#1,	r12	;r3 As==01
    33d4:	91 83 00 00 	dec	0(r1)		;0x0000(r1)
    33d8:	e5 23       	jnz	$-52     	;abs 0x33a4
    33da:	21 53       	incd	r1		
    33dc:	34 16       	popm.a	#4,	r7	
    33de:	10 01       	reta			

000033e0 <__udivdi3>:
    33e0:	3b 14       	pushm.a	#4,	r11	
    33e2:	18 41 14 00 	mov	20(r1),	r8	;0x0014(r1)
    33e6:	19 41 16 00 	mov	22(r1),	r9	;0x0016(r1)
    33ea:	1a 41 18 00 	mov	24(r1),	r10	;0x0018(r1)
    33ee:	1b 41 1a 00 	mov	26(r1),	r11	;0x001a(r1)
    33f2:	b0 13 8e 33 	calla	#0x0338e	
    33f6:	38 16       	popm.a	#4,	r11	
    33f8:	10 01       	reta			

000033fa <__umoddi3>:
    33fa:	3b 14       	pushm.a	#4,	r11	
    33fc:	18 41 14 00 	mov	20(r1),	r8	;0x0014(r1)
    3400:	19 41 16 00 	mov	22(r1),	r9	;0x0016(r1)
    3404:	1a 41 18 00 	mov	24(r1),	r10	;0x0018(r1)
    3408:	1b 41 1a 00 	mov	26(r1),	r11	;0x001a(r1)
    340c:	b0 13 8e 33 	calla	#0x0338e	
    3410:	0c 48       	mov	r8,	r12	
    3412:	0d 49       	mov	r9,	r13	
    3414:	0e 4a       	mov	r10,	r14	
    3416:	0f 4b       	mov	r11,	r15	
    3418:	38 16       	popm.a	#4,	r11	
    341a:	10 01       	reta			

0000341c <__udivmoddi4>:
    341c:	4b 14       	pushm.a	#5,	r11	
    341e:	18 41 18 00 	mov	24(r1),	r8	;0x0018(r1)
    3422:	19 41 1a 00 	mov	26(r1),	r9	;0x001a(r1)
    3426:	1a 41 1c 00 	mov	28(r1),	r10	;0x001c(r1)
    342a:	1b 41 1e 00 	mov	30(r1),	r11	;0x001e(r1)
    342e:	b0 13 8e 33 	calla	#0x0338e	
    3432:	17 41 20 00 	mov	32(r1),	r7	;0x0020(r1)
    3436:	87 48 00 00 	mov	r8,	0(r7)	;0x0000(r7)
    343a:	87 49 02 00 	mov	r9,	2(r7)	;0x0002(r7)
    343e:	87 4a 04 00 	mov	r10,	4(r7)	;0x0004(r7)
    3442:	87 4b 06 00 	mov	r11,	6(r7)	;0x0006(r7)
    3446:	47 16       	popm.a	#5,	r11	
    3448:	10 01       	reta			

0000344a <port1_isr>:
    344a:	3f 14       	pushm.a	#4,	r15	
    344c:	f2 b0 40 00 	bit.b	#64,	&0x0023	;#0x0040
    3450:	23 00 
    3452:	15 24       	jz	$+44     	;abs 0x347e
    3454:	e2 b2 23 00 	bit.b	#4,	&0x0023	;r2 As==10
    3458:	12 20       	jnz	$+38     	;abs 0x347e
    345a:	3f 40 bc 1a 	mov	#6844,	r15	;#0x1abc
    345e:	b0 13 66 6b 	calla	#0x06b66	
    3462:	0f 93       	tst	r15		
    3464:	32 24       	jz	$+102    	;abs 0x34ca
    3466:	3d 40 20 00 	mov	#32,	r13	;#0x0020
    346a:	0e 43       	clr	r14		
    346c:	3f 40 bc 1a 	mov	#6844,	r15	;#0x1abc
    3470:	b0 13 4a 6b 	calla	#0x06b4a	
    3474:	5f 42 23 00 	mov.b	&0x0023,r15	
    3478:	7f f0 bf ff 	and.b	#-65,	r15	;#0xffbf
    347c:	18 3c       	jmp	$+50     	;abs 0x34ae
    347e:	5f 42 23 00 	mov.b	&0x0023,r15	
    3482:	4f 93       	tst.b	r15		
    3484:	1b 34       	jge	$+56     	;abs 0x34bc
    3486:	e2 b2 23 00 	bit.b	#4,	&0x0023	;r2 As==10
    348a:	18 20       	jnz	$+50     	;abs 0x34bc
    348c:	3f 40 c4 1a 	mov	#6852,	r15	;#0x1ac4
    3490:	b0 13 66 6b 	calla	#0x06b66	
    3494:	0f 93       	tst	r15		
    3496:	19 24       	jz	$+52     	;abs 0x34ca
    3498:	3d 40 20 00 	mov	#32,	r13	;#0x0020
    349c:	0e 43       	clr	r14		
    349e:	3f 40 c4 1a 	mov	#6852,	r15	;#0x1ac4
    34a2:	b0 13 4a 6b 	calla	#0x06b4a	
    34a6:	5f 42 23 00 	mov.b	&0x0023,r15	
    34aa:	7f f0 7f 00 	and.b	#127,	r15	;#0x007f
    34ae:	c2 4f 23 00 	mov.b	r15,	&0x0023	
    34b2:	3f 40 00 11 	mov	#4352,	r15	;#0x1100
    34b6:	b0 13 98 67 	calla	#0x06798	
    34ba:	04 3c       	jmp	$+10     	;abs 0x34c4
    34bc:	b0 13 1c 40 	calla	#0x0401c	
    34c0:	0f 93       	tst	r15		
    34c2:	03 24       	jz	$+8      	;abs 0x34ca
    34c4:	b1 c0 f0 00 	bic	#240,	16(r1)	;#0x00f0, 0x0010(r1)
    34c8:	10 00 
    34ca:	3c 16       	popm.a	#4,	r15	
    34cc:	00 13       	reti			

000034ce <irq_p2>:
    34ce:	3f 14       	pushm.a	#4,	r15	
    34d0:	5f 42 2b 00 	mov.b	&0x002b,r15	
    34d4:	7f f0 20 00 	and.b	#32,	r15	;#0x0020
    34d8:	14 24       	jz	$+42     	;abs 0x3502
    34da:	3f 40 cc 1a 	mov	#6860,	r15	;#0x1acc
    34de:	b0 13 66 6b 	calla	#0x06b66	
    34e2:	0f 93       	tst	r15		
    34e4:	0e 24       	jz	$+30     	;abs 0x3502
    34e6:	3d 40 20 00 	mov	#32,	r13	;#0x0020
    34ea:	0e 43       	clr	r14		
    34ec:	3f 40 cc 1a 	mov	#6860,	r15	;#0x1acc
    34f0:	b0 13 4a 6b 	calla	#0x06b4a	
    34f4:	3f 40 02 99 	mov	#-26366,r15	;#0x9902
    34f8:	b0 13 9a 69 	calla	#0x0699a	
    34fc:	b1 c0 f0 00 	bic	#240,	16(r1)	;#0x00f0, 0x0010(r1)
    3500:	10 00 
    3502:	c2 43 2b 00 	mov.b	#0,	&0x002b	;r3 As==00
    3506:	3c 16       	popm.a	#4,	r15	
    3508:	00 13       	reti			

0000350a <cc2420_timerb1_interrupt>:
    350a:	0f 14       	pushm.a	#1,	r15	
    350c:	1f 42 1e 01 	mov	&0x011e,r15	
    3510:	e2 b3 1c 00 	bit.b	#2,	&0x001c	;r3 As==10
    3514:	06 24       	jz	$+14     	;abs 0x3522
    3516:	d2 53 18 24 	inc.b	&0x2418	
    351a:	92 42 94 01 	mov	&0x0194,&0x2412	
    351e:	12 24 
    3520:	05 3c       	jmp	$+12     	;abs 0x352c
    3522:	c2 43 18 24 	mov.b	#0,	&0x2418	;r3 As==00
    3526:	92 42 94 01 	mov	&0x0194,&0x241a	
    352a:	1a 24 
    352c:	0f 16       	popm.a	#1,	r15	
    352e:	00 13       	reti			

00003530 <timera1>:
    3530:	3f 14       	pushm.a	#4,	r15	
    3532:	b0 13 50 6d 	calla	#0x06d50	
    3536:	1f 42 2e 01 	mov	&0x012e,r15	
    353a:	2f 93       	cmp	#2,	r15	;r3 As==10
    353c:	5d 20       	jnz	$+188    	;abs 0x35f8
    353e:	b2 b0 20 00 	bit	#32,	&0x0160	;#0x0020
    3542:	60 01 
    3544:	0b 24       	jz	$+24     	;abs 0x355c
    3546:	1e 42 74 01 	mov	&0x0174,r14	
    354a:	1f 42 70 01 	mov	&0x0170,r15	
    354e:	1d 42 70 01 	mov	&0x0170,r13	
    3552:	0f 9d       	cmp	r13,	r15	
    3554:	fa 23       	jnz	$-10     	;abs 0x354a
    3556:	0e 8f       	sub	r15,	r14	
    3558:	1e 93       	cmp	#1,	r14	;r3 As==01
    355a:	f1 27       	jz	$-28     	;abs 0x353e
    355c:	1f 42 70 01 	mov	&0x0170,r15	
    3560:	1e 42 70 01 	mov	&0x0170,r14	
    3564:	0f 9e       	cmp	r14,	r15	
    3566:	fa 23       	jnz	$-10     	;abs 0x355c
    3568:	2a 3c       	jmp	$+86     	;abs 0x35be
    356a:	b2 50 00 01 	add	#256,	&0x0174	;#0x0100
    356e:	74 01 
    3570:	1e 42 de 1a 	mov	&0x1ade,r14	
    3574:	1f 42 e0 1a 	mov	&0x1ae0,r15	
    3578:	1e 53       	inc	r14		
    357a:	0f 63       	adc	r15		
    357c:	82 4e de 1a 	mov	r14,	&0x1ade	
    3580:	82 4f e0 1a 	mov	r15,	&0x1ae0	
    3584:	1e 42 de 1a 	mov	&0x1ade,r14	
    3588:	1f 42 e0 1a 	mov	&0x1ae0,r15	
    358c:	3e f0 7f 00 	and	#127,	r14	;#0x007f
    3590:	0f f3       	and	#0,	r15	;r3 As==00
    3592:	0e 93       	tst	r14		
    3594:	0e 20       	jnz	$+30     	;abs 0x35b2
    3596:	0f 93       	tst	r15		
    3598:	0c 20       	jnz	$+26     	;abs 0x35b2
    359a:	1e 42 e2 1a 	mov	&0x1ae2,r14	
    359e:	1f 42 e4 1a 	mov	&0x1ae4,r15	
    35a2:	1e 53       	inc	r14		
    35a4:	0f 63       	adc	r15		
    35a6:	82 4e e2 1a 	mov	r14,	&0x1ae2	
    35aa:	82 4f e4 1a 	mov	r15,	&0x1ae4	
    35ae:	b0 13 c4 4a 	calla	#0x04ac4	
    35b2:	1f 42 70 01 	mov	&0x0170,r15	
    35b6:	1e 42 70 01 	mov	&0x0170,r14	
    35ba:	0f 9e       	cmp	r14,	r15	
    35bc:	fa 23       	jnz	$-10     	;abs 0x35b2
    35be:	82 4f dc 1a 	mov	r15,	&0x1adc	
    35c2:	1f 42 dc 1a 	mov	&0x1adc,r15	
    35c6:	1f 82 74 01 	sub	&0x0174,r15	
    35ca:	0f 93       	tst	r15		
    35cc:	ce 37       	jge	$-98     	;abs 0x356a
    35ce:	b0 13 76 4c 	calla	#0x04c76	
    35d2:	0f 93       	tst	r15		
    35d4:	11 24       	jz	$+36     	;abs 0x35f8
    35d6:	b0 13 82 4c 	calla	#0x04c82	
    35da:	1c 42 de 1a 	mov	&0x1ade,r12	
    35de:	1d 42 e0 1a 	mov	&0x1ae0,r13	
    35e2:	3c e3       	inv	r12		
    35e4:	3d e3       	inv	r13		
    35e6:	0c 5e       	add	r14,	r12	
    35e8:	0d 6f       	addc	r15,	r13	
    35ea:	0d 93       	tst	r13		
    35ec:	05 34       	jge	$+12     	;abs 0x35f8
    35ee:	b0 13 36 4b 	calla	#0x04b36	
    35f2:	b1 c0 f0 00 	bic	#240,	16(r1)	;#0x00f0, 0x0010(r1)
    35f6:	10 00 
    35f8:	b0 13 76 6d 	calla	#0x06d76	
    35fc:	3c 16       	popm.a	#4,	r15	
    35fe:	00 13       	reti			

00003600 <i2c_tx_interrupt>:
    3600:	2f 14       	pushm.a	#3,	r15	
    3602:	f2 b2 07 00 	bit.b	#8,	&0x0007	;r2 As==11
    3606:	19 24       	jz	$+52     	;abs 0x363a
    3608:	5e 42 20 24 	mov.b	&0x2420,r14	
    360c:	4e 93       	tst.b	r14		
    360e:	06 20       	jnz	$+14     	;abs 0x361c
    3610:	e2 d2 d9 00 	bis.b	#4,	&0x00d9	;r2 As==10
    3614:	5f 42 07 00 	mov.b	&0x0007,r15	
    3618:	7f c2       	bic.b	#8,	r15	;r2 As==11
    361a:	30 3c       	jmp	$+98     	;abs 0x367c
    361c:	5f 42 ec 23 	mov.b	&0x23ec,r15	
    3620:	4f 4f       	mov.b	r15,	r15	
    3622:	4d 4e       	mov.b	r14,	r13	
    3624:	8d 11       	sxt	r13		
    3626:	0f 8d       	sub	r13,	r15	
    3628:	1f 52 1e 24 	add	&0x241e,r15	
    362c:	6f 4f       	mov.b	@r15,	r15	
    362e:	c2 4f df 00 	mov.b	r15,	&0x00df	
    3632:	7e 53       	add.b	#-1,	r14	;r3 As==11
    3634:	c2 4e 20 24 	mov.b	r14,	&0x2420	
    3638:	23 3c       	jmp	$+72     	;abs 0x3680
    363a:	5f 42 07 00 	mov.b	&0x0007,r15	
    363e:	6f f2       	and.b	#4,	r15	;r2 As==10
    3640:	1f 24       	jz	$+64     	;abs 0x3680
    3642:	5f 42 ed 23 	mov.b	&0x23ed,r15	
    3646:	5d 42 de 00 	mov.b	&0x00de,r13	
    364a:	4f 4f       	mov.b	r15,	r15	
    364c:	5e 42 1d 24 	mov.b	&0x241d,r14	
    3650:	8e 11       	sxt	r14		
    3652:	0f 8e       	sub	r14,	r15	
    3654:	1f 52 28 24 	add	&0x2428,r15	
    3658:	cf 4d 00 00 	mov.b	r13,	0(r15)	;0x0000(r15)
    365c:	5f 42 1d 24 	mov.b	&0x241d,r15	
    3660:	7f 53       	add.b	#-1,	r15	;r3 As==11
    3662:	c2 4f 1d 24 	mov.b	r15,	&0x241d	
    3666:	5f 93       	cmp.b	#1,	r15	;r3 As==01
    3668:	0b 20       	jnz	$+24     	;abs 0x3680
    366a:	5f 42 ed 23 	mov.b	&0x23ed,r15	
    366e:	5f 93       	cmp.b	#1,	r15	;r3 As==01
    3670:	02 24       	jz	$+6      	;abs 0x3676
    3672:	e2 d2 d9 00 	bis.b	#4,	&0x00d9	;r2 As==10
    3676:	5f 42 07 00 	mov.b	&0x0007,r15	
    367a:	6f c2       	bic.b	#4,	r15	;r2 As==10
    367c:	c2 4f 07 00 	mov.b	r15,	&0x0007	
    3680:	2d 16       	popm.a	#3,	r15	
    3682:	00 13       	reti			

00003684 <i2c_rx_interrupt>:
    3684:	0f 14       	pushm.a	#1,	r15	
    3686:	f2 b2 dd 00 	bit.b	#8,	&0x00dd	;r2 As==11
    368a:	04 24       	jz	$+10     	;abs 0x3694
    368c:	e2 d2 d9 00 	bis.b	#4,	&0x00d9	;r2 As==10
    3690:	f2 c2 dd 00 	bic.b	#8,	&0x00dd	;r2 As==11
    3694:	0f 16       	popm.a	#1,	r15	
    3696:	00 13       	reti			

00003698 <timera0>:
    3698:	3f 14       	pushm.a	#4,	r15	
    369a:	b0 13 50 6d 	calla	#0x06d50	
    369e:	b0 13 b2 68 	calla	#0x068b2	
    36a2:	b0 13 f8 66 	calla	#0x066f8	
    36a6:	0f 93       	tst	r15		
    36a8:	04 24       	jz	$+10     	;abs 0x36b2
    36aa:	03 38       	jl	$+8      	;abs 0x36b2
    36ac:	b1 c0 f0 00 	bic	#240,	16(r1)	;#0x00f0, 0x0010(r1)
    36b0:	10 00 
    36b2:	b0 13 76 6d 	calla	#0x06d76	
    36b6:	3c 16       	popm.a	#4,	r15	
    36b8:	00 13       	reti			

000036ba <uart0_rx_interrupt>:
    36ba:	3f 14       	pushm.a	#4,	r15	
    36bc:	e2 b2 65 00 	bit.b	#4,	&0x0065	;r2 As==10
    36c0:	03 24       	jz	$+8      	;abs 0x36c8
    36c2:	5f 42 66 00 	mov.b	&0x0066,r15	
    36c6:	0c 3c       	jmp	$+26     	;abs 0x36e0
    36c8:	5f 42 66 00 	mov.b	&0x0066,r15	
    36cc:	2e 00 c8 23 	mova	&0x023c8,r14	
    36d0:	de 03       	tsta	r14		
    36d2:	06 24       	jz	$+14     	;abs 0x36e0
    36d4:	4e 13       	calla	r14		
    36d6:	0f 93       	tst	r15		
    36d8:	03 24       	jz	$+8      	;abs 0x36e0
    36da:	b1 c0 f0 00 	bic	#240,	16(r1)	;#0x00f0, 0x0010(r1)
    36de:	10 00 
    36e0:	3c 16       	popm.a	#4,	r15	
    36e2:	00 13       	reti			

000036e4 <watchdog_interrupt>:
    36e4:	82 43 20 01 	mov	#0,	&0x0120	;r3 As==00
    36e8:	00 13       	reti			

000036ea <status>:
    36ea:	3f 50 7f ff 	add	#-129,	r15	;#0xff7f
    36ee:	2f 93       	cmp	#2,	r15	;r3 As==10
    36f0:	03 2c       	jc	$+8      	;abs 0x36f8
    36f2:	5f 42 d2 23 	mov.b	&0x23d2,r15	
    36f6:	10 01       	reta			
    36f8:	0f 43       	clr	r15		
    36fa:	10 01       	reta			

000036fc <accm_write_reg>:
    36fc:	21 83       	decd	r1		
    36fe:	c1 4f 00 00 	mov.b	r15,	0(r1)	;0x0000(r1)
    3702:	c1 4e 01 00 	mov.b	r14,	1(r1)	;0x0001(r1)
    3706:	7f 40 53 00 	mov.b	#83,	r15	;#0x0053
    370a:	b0 13 1a 54 	calla	#0x0541a	
    370e:	b0 13 88 54 	calla	#0x05488	
    3712:	4f 93       	tst.b	r15		
    3714:	fc 23       	jnz	$-6      	;abs 0x370e
    3716:	0e 41       	mov	r1,	r14	
    3718:	6f 43       	mov.b	#2,	r15	;r3 As==10
    371a:	b0 13 b4 54 	calla	#0x054b4	
    371e:	b0 13 88 54 	calla	#0x05488	
    3722:	4f 93       	tst.b	r15		
    3724:	fc 23       	jnz	$-6      	;abs 0x371e
    3726:	21 53       	incd	r1		
    3728:	10 01       	reta			

0000372a <accm_write_stream>:
    372a:	1b 14       	pushm.a	#2,	r11	
    372c:	4b 4f       	mov.b	r15,	r11	
    372e:	0a 4e       	mov	r14,	r10	
    3730:	7f 40 53 00 	mov.b	#83,	r15	;#0x0053
    3734:	b0 13 1a 54 	calla	#0x0541a	
    3738:	b0 13 88 54 	calla	#0x05488	
    373c:	4f 93       	tst.b	r15		
    373e:	fc 23       	jnz	$-6      	;abs 0x3738
    3740:	0e 4a       	mov	r10,	r14	
    3742:	4f 4b       	mov.b	r11,	r15	
    3744:	b0 13 b4 54 	calla	#0x054b4	
    3748:	b0 13 88 54 	calla	#0x05488	
    374c:	4f 93       	tst.b	r15		
    374e:	fc 23       	jnz	$-6      	;abs 0x3748
    3750:	1a 16       	popm.a	#2,	r11	
    3752:	10 01       	reta			

00003754 <accm_read_reg>:
    3754:	21 83       	decd	r1		
    3756:	c1 43 01 00 	mov.b	#0,	1(r1)	;r3 As==00, 0x0001(r1)
    375a:	c1 4f 00 00 	mov.b	r15,	0(r1)	;0x0000(r1)
    375e:	7f 40 53 00 	mov.b	#83,	r15	;#0x0053
    3762:	b0 13 1a 54 	calla	#0x0541a	
    3766:	b0 13 88 54 	calla	#0x05488	
    376a:	4f 93       	tst.b	r15		
    376c:	fc 23       	jnz	$-6      	;abs 0x3766
    376e:	0e 41       	mov	r1,	r14	
    3770:	5f 43       	mov.b	#1,	r15	;r3 As==01
    3772:	b0 13 b4 54 	calla	#0x054b4	
    3776:	b0 13 88 54 	calla	#0x05488	
    377a:	4f 93       	tst.b	r15		
    377c:	fc 23       	jnz	$-6      	;abs 0x3776
    377e:	7f 40 53 00 	mov.b	#83,	r15	;#0x0053
    3782:	b0 13 e4 53 	calla	#0x053e4	
    3786:	b0 13 88 54 	calla	#0x05488	
    378a:	4f 93       	tst.b	r15		
    378c:	fc 23       	jnz	$-6      	;abs 0x3786
    378e:	0e 41       	mov	r1,	r14	
    3790:	1e 53       	inc	r14		
    3792:	5f 43       	mov.b	#1,	r15	;r3 As==01
    3794:	b0 13 4a 54 	calla	#0x0544a	
    3798:	b0 13 88 54 	calla	#0x05488	
    379c:	4f 93       	tst.b	r15		
    379e:	fc 23       	jnz	$-6      	;abs 0x3798
    37a0:	5f 41 01 00 	mov.b	1(r1),	r15	;0x0001(r1)
    37a4:	21 53       	incd	r1		
    37a6:	10 01       	reta			

000037a8 <process_thread_accmeter_process>:
    37a8:	0b 14       	pushm.a	#1,	r11	
    37aa:	0b 4f       	mov	r15,	r11	
    37ac:	7e 90 82 ff 	cmp.b	#-126,	r14	;#0xff82
    37b0:	13 20       	jnz	$+40     	;abs 0x37d8
    37b2:	7f 40 30 00 	mov.b	#48,	r15	;#0x0030
    37b6:	b0 13 54 37 	calla	#0x03754	
    37ba:	4e 4f       	mov.b	r15,	r14	
    37bc:	1e b2 b8 1a 	bit	&0x1ab8,r14	
    37c0:	03 24       	jz	$+8      	;abs 0x37c8
    37c2:	2e 00 0c 24 	mova	&0x0240c,r14	
    37c6:	05 3c       	jmp	$+12     	;abs 0x37d2
    37c8:	1e b2 ba 1a 	bit	&0x1aba,r14	
    37cc:	05 24       	jz	$+12     	;abs 0x37d8
    37ce:	2e 00 08 24 	mova	&0x02408,r14	
    37d2:	de 03       	tsta	r14		
    37d4:	01 24       	jz	$+4      	;abs 0x37d8
    37d6:	4e 13       	calla	r14		
    37d8:	2f 4b       	mov	@r11,	r15	
    37da:	0f 93       	tst	r15		
    37dc:	04 24       	jz	$+10     	;abs 0x37e6
    37de:	3f 90 3f 01 	cmp	#319,	r15	;#0x013f
    37e2:	05 20       	jnz	$+12     	;abs 0x37ee
    37e4:	09 3c       	jmp	$+20     	;abs 0x37f8
    37e6:	bb 40 3f 01 	mov	#319,	0(r11)	;#0x013f, 0x0000(r11)
    37ea:	00 00 
    37ec:	05 3c       	jmp	$+12     	;abs 0x37f8
    37ee:	8b 43 00 00 	mov	#0,	0(r11)	;r3 As==00, 0x0000(r11)
    37f2:	7f 40 03 00 	mov.b	#3,	r15	;#0x0003
    37f6:	01 3c       	jmp	$+4      	;abs 0x37fa
    37f8:	5f 43       	mov.b	#1,	r15	;r3 As==01
    37fa:	0b 16       	popm.a	#1,	r11	
    37fc:	10 01       	reta			

000037fe <accm_read_axis.part.0>:
    37fe:	21 82       	sub	#4,	r1	;r2 As==10
    3800:	7f 50 32 00 	add.b	#50,	r15	;#0x0032
    3804:	c1 4f 02 00 	mov.b	r15,	2(r1)	;0x0002(r1)
    3808:	7f 40 53 00 	mov.b	#83,	r15	;#0x0053
    380c:	b0 13 1a 54 	calla	#0x0541a	
    3810:	b0 13 88 54 	calla	#0x05488	
    3814:	4f 93       	tst.b	r15		
    3816:	fc 23       	jnz	$-6      	;abs 0x3810
    3818:	0e 41       	mov	r1,	r14	
    381a:	2e 53       	incd	r14		
    381c:	5f 43       	mov.b	#1,	r15	;r3 As==01
    381e:	b0 13 b4 54 	calla	#0x054b4	
    3822:	b0 13 88 54 	calla	#0x05488	
    3826:	4f 93       	tst.b	r15		
    3828:	fc 23       	jnz	$-6      	;abs 0x3822
    382a:	7f 40 53 00 	mov.b	#83,	r15	;#0x0053
    382e:	b0 13 e4 53 	calla	#0x053e4	
    3832:	b0 13 88 54 	calla	#0x05488	
    3836:	4f 93       	tst.b	r15		
    3838:	fc 23       	jnz	$-6      	;abs 0x3832
    383a:	0e 41       	mov	r1,	r14	
    383c:	6f 43       	mov.b	#2,	r15	;r3 As==10
    383e:	b0 13 4a 54 	calla	#0x0544a	
    3842:	b0 13 88 54 	calla	#0x05488	
    3846:	4f 93       	tst.b	r15		
    3848:	fc 23       	jnz	$-6      	;abs 0x3842
    384a:	5f 41 01 00 	mov.b	1(r1),	r15	;0x0001(r1)
    384e:	8f 10       	swpb	r15		
    3850:	6e 41       	mov.b	@r1,	r14	
    3852:	0f de       	bis	r14,	r15	
    3854:	21 52       	add	#4,	r1	;r2 As==10
    3856:	10 01       	reta			

00003858 <value>:
    3858:	c2 93 d2 23 	tst.b	&0x23d2	
    385c:	0a 24       	jz	$+22     	;abs 0x3872
    385e:	0f 93       	tst	r15		
    3860:	05 24       	jz	$+12     	;abs 0x386c
    3862:	2f 93       	cmp	#2,	r15	;r3 As==10
    3864:	03 24       	jz	$+8      	;abs 0x386c
    3866:	2f 92       	cmp	#4,	r15	;r2 As==10
    3868:	01 24       	jz	$+4      	;abs 0x386c
    386a:	03 3c       	jmp	$+8      	;abs 0x3872
    386c:	b0 13 fe 37 	calla	#0x037fe	
    3870:	10 01       	reta			
    3872:	3f 43       	mov	#-1,	r15	;r3 As==11
    3874:	10 01       	reta			

00003876 <accm_init>:
    3876:	0b 14       	pushm.a	#1,	r11	
    3878:	cf 03       	clra	r15		
    387a:	60 0f 0c 24 	mova	r15,	&0x0240c
    387e:	60 0f 08 24 	mova	r15,	&0x02408
    3882:	f2 f0 3f 00 	and.b	#63,	&0x0022	;#0x003f
    3886:	22 00 
    3888:	f2 f0 3f 00 	and.b	#63,	&0x0026	;#0x003f
    388c:	26 00 
    388e:	f2 f0 3f 00 	and.b	#63,	&0x0041	;#0x003f
    3892:	41 00 
    3894:	b0 13 92 54 	calla	#0x05492	
    3898:	3e 40 3c 1a 	mov	#6716,	r14	;#0x1a3c
    389c:	7f 40 0f 00 	mov.b	#15,	r15	;#0x000f
    38a0:	b0 13 2a 37 	calla	#0x0372a	
    38a4:	3b 40 4b 1a 	mov	#6731,	r11	;#0x1a4b
    38a8:	0e 4b       	mov	r11,	r14	
    38aa:	7f 40 05 00 	mov.b	#5,	r15	;#0x0005
    38ae:	b0 13 2a 37 	calla	#0x0372a	
    38b2:	5e 4b 05 00 	mov.b	5(r11),	r14	;0x0005(r11)
    38b6:	7f 40 31 00 	mov.b	#49,	r15	;#0x0031
    38ba:	b0 13 fc 36 	calla	#0x036fc	
    38be:	5e 4b 06 00 	mov.b	6(r11),	r14	;0x0006(r11)
    38c2:	7f 40 38 00 	mov.b	#56,	r15	;#0x0038
    38c6:	b0 13 fc 36 	calla	#0x036fc	
    38ca:	0e 43       	clr	r14		
    38cc:	3f 40 00 11 	mov	#4352,	r15	;#0x1100
    38d0:	b0 13 62 67 	calla	#0x06762	
    38d4:	32 c2       	dint			
    38d6:	03 43       	nop			
    38d8:	f2 f0 3f 00 	and.b	#63,	&0x0024	;#0x003f
    38dc:	24 00 
    38de:	f2 d0 c0 ff 	bis.b	#-64,	&0x0025	;#0xffc0
    38e2:	25 00 
    38e4:	32 d2       	eint			
    38e6:	d2 43 d2 23 	mov.b	#1,	&0x23d2	;r3 As==01
    38ea:	0b 16       	popm.a	#1,	r11	
    38ec:	10 01       	reta			

000038ee <accm_stop>:
    38ee:	32 c2       	dint			
    38f0:	03 43       	nop			
    38f2:	f2 f0 3f 00 	and.b	#63,	&0x0025	;#0x003f
    38f6:	25 00 
    38f8:	5e 42 ba 1a 	mov.b	&0x1aba,r14	
    38fc:	5e d2 b8 1a 	bis.b	&0x1ab8,r14	
    3900:	7e e3       	xor.b	#-1,	r14	;r3 As==11
    3902:	7f 40 2e 00 	mov.b	#46,	r15	;#0x002e
    3906:	b0 13 fc 36 	calla	#0x036fc	
    390a:	5e 42 ba 1a 	mov.b	&0x1aba,r14	
    390e:	7e e3       	xor.b	#-1,	r14	;r3 As==11
    3910:	7f 40 2f 00 	mov.b	#47,	r15	;#0x002f
    3914:	b0 13 fc 36 	calla	#0x036fc	
    3918:	32 d2       	eint			
    391a:	c2 43 d2 23 	mov.b	#0,	&0x23d2	;r3 As==00
    391e:	10 01       	reta			

00003920 <configure>:
    3920:	0b 14       	pushm.a	#1,	r11	
    3922:	0b 4e       	mov	r14,	r11	
    3924:	3f 90 81 00 	cmp	#129,	r15	;#0x0081
    3928:	0b 20       	jnz	$+24     	;abs 0x3940
    392a:	0e 93       	tst	r14		
    392c:	03 24       	jz	$+8      	;abs 0x3934
    392e:	b0 13 76 38 	calla	#0x03876	
    3932:	02 3c       	jmp	$+6      	;abs 0x3938
    3934:	b0 13 ee 38 	calla	#0x038ee	
    3938:	c2 4b d2 23 	mov.b	r11,	&0x23d2	
    393c:	0f 43       	clr	r15		
    393e:	01 3c       	jmp	$+4      	;abs 0x3942
    3940:	3f 43       	mov	#-1,	r15	;r3 As==11
    3942:	0b 16       	popm.a	#1,	r11	
    3944:	10 01       	reta			

00003946 <autostart_start>:
    3946:	0b 14       	pushm.a	#1,	r11	
    3948:	0b 4f       	mov	r15,	r11	
    394a:	03 3c       	jmp	$+8      	;abs 0x3952
    394c:	0e 43       	clr	r14		
    394e:	b0 13 62 67 	calla	#0x06762	
    3952:	3f 4b       	mov	@r11+,	r15	
    3954:	0f 93       	tst	r15		
    3956:	fa 23       	jnz	$-10     	;abs 0x394c
    3958:	0b 16       	popm.a	#1,	r11	
    395a:	10 01       	reta			

0000395c <status>:
    395c:	3f 50 7f ff 	add	#-129,	r15	;#0xff7f
    3960:	2f 93       	cmp	#2,	r15	;r3 As==10
    3962:	06 2c       	jc	$+14     	;abs 0x3970
    3964:	5f 42 2d 00 	mov.b	&0x002d,r15	
    3968:	7f f0 20 00 	and.b	#32,	r15	;#0x0020
    396c:	4f 4f       	mov.b	r15,	r15	
    396e:	10 01       	reta			
    3970:	0f 43       	clr	r15		
    3972:	10 01       	reta			

00003974 <value>:
    3974:	f2 b0 20 00 	bit.b	#32,	&0x0028	;#0x0020
    3978:	28 00 
    397a:	0a 20       	jnz	$+22     	;abs 0x3990
    397c:	3f 40 cc 1a 	mov	#6860,	r15	;#0x1acc
    3980:	b0 13 66 6b 	calla	#0x06b66	
    3984:	1e 43       	mov	#1,	r14	;r3 As==01
    3986:	0f 93       	tst	r15		
    3988:	01 24       	jz	$+4      	;abs 0x398c
    398a:	0e 43       	clr	r14		
    398c:	0f 4e       	mov	r14,	r15	
    398e:	10 01       	reta			
    3990:	1f 43       	mov	#1,	r15	;r3 As==01
    3992:	10 01       	reta			

00003994 <configure>:
    3994:	3f 90 81 00 	cmp	#129,	r15	;#0x0081
    3998:	20 20       	jnz	$+66     	;abs 0x39da
    399a:	5f 42 2d 00 	mov.b	&0x002d,r15	
    399e:	0e 93       	tst	r14		
    39a0:	17 24       	jz	$+48     	;abs 0x39d0
    39a2:	7f f0 20 00 	and.b	#32,	r15	;#0x0020
    39a6:	1b 20       	jnz	$+56     	;abs 0x39de
    39a8:	0d 43       	clr	r13		
    39aa:	0e 43       	clr	r14		
    39ac:	3f 40 cc 1a 	mov	#6860,	r15	;#0x1acc
    39b0:	b0 13 4a 6b 	calla	#0x06b4a	
    39b4:	f2 d0 20 00 	bis.b	#32,	&0x002c	;#0x0020
    39b8:	2c 00 
    39ba:	f2 f0 df ff 	and.b	#-33,	&0x002e	;#0xffdf
    39be:	2e 00 
    39c0:	f2 f0 df ff 	and.b	#-33,	&0x002a	;#0xffdf
    39c4:	2a 00 
    39c6:	5f 42 2d 00 	mov.b	&0x002d,r15	
    39ca:	7f d0 20 00 	bis.b	#32,	r15	;#0x0020
    39ce:	02 3c       	jmp	$+6      	;abs 0x39d4
    39d0:	7f f0 df ff 	and.b	#-33,	r15	;#0xffdf
    39d4:	c2 4f 2d 00 	mov.b	r15,	&0x002d	
    39d8:	02 3c       	jmp	$+6      	;abs 0x39de
    39da:	0f 43       	clr	r15		
    39dc:	10 01       	reta			
    39de:	1f 43       	mov	#1,	r15	;r3 As==01
    39e0:	10 01       	reta			

000039e2 <cc2420_arch_init>:
    39e2:	b0 13 c4 69 	calla	#0x069c4	
    39e6:	d2 d3 1a 00 	bis.b	#1,	&0x001a	;r3 As==01
    39ea:	f2 d0 20 00 	bis.b	#32,	&0x001e	;#0x0020
    39ee:	1e 00 
    39f0:	f2 d0 40 00 	bis.b	#64,	&0x001e	;#0x0040
    39f4:	1e 00 
    39f6:	d2 d3 19 00 	bis.b	#1,	&0x0019	;r3 As==01
    39fa:	10 01       	reta			

000039fc <get_object>:
    39fc:	1f 43       	mov	#1,	r15	;r3 As==01
    39fe:	10 01       	reta			

00003a00 <set_object>:
    3a00:	1f 43       	mov	#1,	r15	;r3 As==01
    3a02:	10 01       	reta			

00003a04 <strobe>:
    3a04:	d2 c3 19 00 	bic.b	#1,	&0x0019	;r3 As==01
    3a08:	f2 b2 03 00 	bit.b	#8,	&0x0003	;r2 As==11
    3a0c:	fd 27       	jz	$-4      	;abs 0x3a08
    3a0e:	c2 4f 6f 00 	mov.b	r15,	&0x006f	
    3a12:	d2 b3 6d 00 	bit.b	#1,	&0x006d	;r3 As==01
    3a16:	fd 23       	jnz	$-4      	;abs 0x3a12
    3a18:	d2 d3 19 00 	bis.b	#1,	&0x0019	;r3 As==01
    3a1c:	10 01       	reta			

00003a1e <getreg>:
    3a1e:	d2 c3 19 00 	bic.b	#1,	&0x0019	;r3 As==01
    3a22:	f2 b2 03 00 	bit.b	#8,	&0x0003	;r2 As==11
    3a26:	fd 27       	jz	$-4      	;abs 0x3a22
    3a28:	3f d0 40 00 	bis	#64,	r15	;#0x0040
    3a2c:	c2 4f 6f 00 	mov.b	r15,	&0x006f	
    3a30:	d2 b3 6d 00 	bit.b	#1,	&0x006d	;r3 As==01
    3a34:	fd 23       	jnz	$-4      	;abs 0x3a30
    3a36:	5f 42 6e 00 	mov.b	&0x006e,r15	
    3a3a:	c2 43 6f 00 	mov.b	#0,	&0x006f	;r3 As==00
    3a3e:	e2 b2 03 00 	bit.b	#4,	&0x0003	;r2 As==10
    3a42:	fd 27       	jz	$-4      	;abs 0x3a3e
    3a44:	5e 42 6e 00 	mov.b	&0x006e,r14	
    3a48:	4e 4e       	mov.b	r14,	r14	
    3a4a:	8e 10       	swpb	r14		
    3a4c:	c2 43 6f 00 	mov.b	#0,	&0x006f	;r3 As==00
    3a50:	e2 b2 03 00 	bit.b	#4,	&0x0003	;r2 As==10
    3a54:	fd 27       	jz	$-4      	;abs 0x3a50
    3a56:	5f 42 6e 00 	mov.b	&0x006e,r15	
    3a5a:	d2 d3 19 00 	bis.b	#1,	&0x0019	;r3 As==01
    3a5e:	4f 4f       	mov.b	r15,	r15	
    3a60:	0f de       	bis	r14,	r15	
    3a62:	10 01       	reta			

00003a64 <setreg>:
    3a64:	d2 c3 19 00 	bic.b	#1,	&0x0019	;r3 As==01
    3a68:	f2 b2 03 00 	bit.b	#8,	&0x0003	;r2 As==11
    3a6c:	fd 27       	jz	$-4      	;abs 0x3a68
    3a6e:	c2 4f 6f 00 	mov.b	r15,	&0x006f	
    3a72:	f2 b2 03 00 	bit.b	#8,	&0x0003	;r2 As==11
    3a76:	fd 27       	jz	$-4      	;abs 0x3a72
    3a78:	0f 4e       	mov	r14,	r15	
    3a7a:	8f 10       	swpb	r15		
    3a7c:	4f 4f       	mov.b	r15,	r15	
    3a7e:	c2 4f 6f 00 	mov.b	r15,	&0x006f	
    3a82:	f2 b2 03 00 	bit.b	#8,	&0x0003	;r2 As==11
    3a86:	fd 27       	jz	$-4      	;abs 0x3a82
    3a88:	c2 4e 6f 00 	mov.b	r14,	&0x006f	
    3a8c:	d2 b3 6d 00 	bit.b	#1,	&0x006d	;r3 As==01
    3a90:	fd 23       	jnz	$-4      	;abs 0x3a8c
    3a92:	f2 b2 03 00 	bit.b	#8,	&0x0003	;r2 As==11
    3a96:	fd 27       	jz	$-4      	;abs 0x3a92
    3a98:	c2 43 6f 00 	mov.b	#0,	&0x006f	;r3 As==00
    3a9c:	d2 b3 6d 00 	bit.b	#1,	&0x006d	;r3 As==01
    3aa0:	fd 23       	jnz	$-4      	;abs 0x3a9c
    3aa2:	d2 d3 19 00 	bis.b	#1,	&0x0019	;r3 As==01
    3aa6:	10 01       	reta			

00003aa8 <write_ram>:
    3aa8:	0b 14       	pushm.a	#1,	r11	
    3aaa:	d2 c3 19 00 	bic.b	#1,	&0x0019	;r3 As==01
    3aae:	f2 b2 03 00 	bit.b	#8,	&0x0003	;r2 As==11
    3ab2:	fd 27       	jz	$-4      	;abs 0x3aae
    3ab4:	0b 4e       	mov	r14,	r11	
    3ab6:	3b d0 80 00 	bis	#128,	r11	;#0x0080
    3aba:	c2 4b 6f 00 	mov.b	r11,	&0x006f	
    3abe:	f2 b2 03 00 	bit.b	#8,	&0x0003	;r2 As==11
    3ac2:	fd 27       	jz	$-4      	;abs 0x3abe
    3ac4:	5e 03       	rrum	#1,	r14	
    3ac6:	3e f0 c0 00 	and	#192,	r14	;#0x00c0
    3aca:	c2 4e 6f 00 	mov.b	r14,	&0x006f	
    3ace:	0c 93       	tst	r12		
    3ad0:	09 24       	jz	$+20     	;abs 0x3ae4
    3ad2:	0d 3c       	jmp	$+28     	;abs 0x3aee
    3ad4:	f2 b2 03 00 	bit.b	#8,	&0x0003	;r2 As==11
    3ad8:	fd 27       	jz	$-4      	;abs 0x3ad4
    3ada:	0b 5f       	add	r15,	r11	
    3adc:	e2 4b 6f 00 	mov.b	@r11,	&0x006f	
    3ae0:	5e 53       	inc.b	r14		
    3ae2:	01 3c       	jmp	$+4      	;abs 0x3ae6
    3ae4:	4e 43       	clr.b	r14		
    3ae6:	4b 4e       	mov.b	r14,	r11	
    3ae8:	0b 9d       	cmp	r13,	r11	
    3aea:	f4 2b       	jnc	$-22     	;abs 0x3ad4
    3aec:	0f 3c       	jmp	$+32     	;abs 0x3b0c
    3aee:	4d 4d       	mov.b	r13,	r13	
    3af0:	0e 43       	clr	r14		
    3af2:	09 3c       	jmp	$+20     	;abs 0x3b06
    3af4:	f2 b2 03 00 	bit.b	#8,	&0x0003	;r2 As==11
    3af8:	fd 27       	jz	$-4      	;abs 0x3af4
    3afa:	4c 4c       	mov.b	r12,	r12	
    3afc:	0c 5f       	add	r15,	r12	
    3afe:	d2 4c ff ff 	mov.b	-1(r12),&0x006f	;0xffff(r12)
    3b02:	6f 00 
    3b04:	1e 53       	inc	r14		
    3b06:	4c 4d       	mov.b	r13,	r12	
    3b08:	4c 8e       	sub.b	r14,	r12	
    3b0a:	f4 23       	jnz	$-22     	;abs 0x3af4
    3b0c:	d2 b3 6d 00 	bit.b	#1,	&0x006d	;r3 As==01
    3b10:	fd 23       	jnz	$-4      	;abs 0x3b0c
    3b12:	d2 d3 19 00 	bis.b	#1,	&0x0019	;r3 As==01
    3b16:	0b 16       	popm.a	#1,	r11	
    3b18:	10 01       	reta			

00003b1a <write_fifo_buf>:
    3b1a:	0b 14       	pushm.a	#1,	r11	
    3b1c:	d2 c3 19 00 	bic.b	#1,	&0x0019	;r3 As==01
    3b20:	f2 b2 03 00 	bit.b	#8,	&0x0003	;r2 As==11
    3b24:	fd 27       	jz	$-4      	;abs 0x3b20
    3b26:	f2 40 3e 00 	mov.b	#62,	&0x006f	;#0x003e
    3b2a:	6f 00 
    3b2c:	4d 43       	clr.b	r13		
    3b2e:	07 3c       	jmp	$+16     	;abs 0x3b3e
    3b30:	f2 b2 03 00 	bit.b	#8,	&0x0003	;r2 As==11
    3b34:	fd 27       	jz	$-4      	;abs 0x3b30
    3b36:	0b 5f       	add	r15,	r11	
    3b38:	e2 4b 6f 00 	mov.b	@r11,	&0x006f	
    3b3c:	5d 53       	inc.b	r13		
    3b3e:	4b 4d       	mov.b	r13,	r11	
    3b40:	0b 9e       	cmp	r14,	r11	
    3b42:	f6 2b       	jnc	$-18     	;abs 0x3b30
    3b44:	d2 b3 6d 00 	bit.b	#1,	&0x006d	;r3 As==01
    3b48:	fd 23       	jnz	$-4      	;abs 0x3b44
    3b4a:	d2 d3 19 00 	bis.b	#1,	&0x0019	;r3 As==01
    3b4e:	0b 16       	popm.a	#1,	r11	
    3b50:	10 01       	reta			

00003b52 <get_status>:
    3b52:	d2 c3 19 00 	bic.b	#1,	&0x0019	;r3 As==01
    3b56:	f2 b2 03 00 	bit.b	#8,	&0x0003	;r2 As==11
    3b5a:	fd 27       	jz	$-4      	;abs 0x3b56
    3b5c:	c2 43 6f 00 	mov.b	#0,	&0x006f	;r3 As==00
    3b60:	d2 b3 6d 00 	bit.b	#1,	&0x006d	;r3 As==01
    3b64:	fd 23       	jnz	$-4      	;abs 0x3b60
    3b66:	5f 42 6e 00 	mov.b	&0x006e,r15	
    3b6a:	d2 d3 19 00 	bis.b	#1,	&0x0019	;r3 As==01
    3b6e:	10 01       	reta			

00003b70 <on>:
    3b70:	5f 42 d3 23 	mov.b	&0x23d3,r15	
    3b74:	4f 93       	tst.b	r15		
    3b76:	02 20       	jnz	$+6      	;abs 0x3b7c
    3b78:	e2 d2 25 00 	bis.b	#4,	&0x0025	;r2 As==10
    3b7c:	3f 40 03 00 	mov	#3,	r15	;#0x0003
    3b80:	b0 13 04 3a 	calla	#0x03a04	
    3b84:	d2 43 d7 23 	mov.b	#1,	&0x23d7	;r3 As==01
    3b88:	10 01       	reta			

00003b8a <cc2420_receiving_packet>:
    3b8a:	5f 42 1c 00 	mov.b	&0x001c,r15	
    3b8e:	5f 03       	rrum	#1,	r15	
    3b90:	1f f3       	and	#1,	r15	;r3 As==01
    3b92:	10 01       	reta			

00003b94 <pending_packet>:
    3b94:	5f 42 20 00 	mov.b	&0x0020,r15	
    3b98:	5f 07       	rrum	#2,	r15	
    3b9a:	1f f3       	and	#1,	r15	;r3 As==01
    3b9c:	10 01       	reta			

00003b9e <wait_for_transmission>:
    3b9e:	0b 14       	pushm.a	#1,	r11	
    3ba0:	b0 13 98 68 	calla	#0x06898	
    3ba4:	3b 40 34 f3 	mov	#-3276,	r11	;#0xf334
    3ba8:	0b 8f       	sub	r15,	r11	
    3baa:	b0 13 52 3b 	calla	#0x03b52	
    3bae:	7f f2       	and.b	#8,	r15	;r2 As==11
    3bb0:	05 24       	jz	$+12     	;abs 0x3bbc
    3bb2:	b0 13 98 68 	calla	#0x06898	
    3bb6:	0f 5b       	add	r11,	r15	
    3bb8:	0f 93       	tst	r15		
    3bba:	f7 3b       	jl	$-16     	;abs 0x3baa
    3bbc:	0b 16       	popm.a	#1,	r11	
    3bbe:	10 01       	reta			

00003bc0 <wait_for_status>:
    3bc0:	1b 14       	pushm.a	#2,	r11	
    3bc2:	4a 4f       	mov.b	r15,	r10	
    3bc4:	b0 13 98 68 	calla	#0x06898	
    3bc8:	3b 40 34 f3 	mov	#-3276,	r11	;#0xf334
    3bcc:	0b 8f       	sub	r15,	r11	
    3bce:	b0 13 52 3b 	calla	#0x03b52	
    3bd2:	4f ba       	bit.b	r10,	r15	
    3bd4:	05 20       	jnz	$+12     	;abs 0x3be0
    3bd6:	b0 13 98 68 	calla	#0x06898	
    3bda:	0f 5b       	add	r11,	r15	
    3bdc:	0f 93       	tst	r15		
    3bde:	f7 3b       	jl	$-16     	;abs 0x3bce
    3be0:	1a 16       	popm.a	#2,	r11	
    3be2:	10 01       	reta			

00003be4 <getrxdata>:
    3be4:	0b 14       	pushm.a	#1,	r11	
    3be6:	d2 c3 19 00 	bic.b	#1,	&0x0019	;r3 As==01
    3bea:	f2 b2 03 00 	bit.b	#8,	&0x0003	;r2 As==11
    3bee:	fd 27       	jz	$-4      	;abs 0x3bea
    3bf0:	f2 40 7f 00 	mov.b	#127,	&0x006f	;#0x007f
    3bf4:	6f 00 
    3bf6:	d2 b3 6d 00 	bit.b	#1,	&0x006d	;r3 As==01
    3bfa:	fd 23       	jnz	$-4      	;abs 0x3bf6
    3bfc:	5d 42 6e 00 	mov.b	&0x006e,r13	
    3c00:	4d 43       	clr.b	r13		
    3c02:	0c 3c       	jmp	$+26     	;abs 0x3c1c
    3c04:	c2 43 6f 00 	mov.b	#0,	&0x006f	;r3 As==00
    3c08:	e2 b2 03 00 	bit.b	#4,	&0x0003	;r2 As==10
    3c0c:	fd 27       	jz	$-4      	;abs 0x3c08
    3c0e:	5b 42 6e 00 	mov.b	&0x006e,r11	
    3c12:	4c 4d       	mov.b	r13,	r12	
    3c14:	0c 5f       	add	r15,	r12	
    3c16:	cc 4b 00 00 	mov.b	r11,	0(r12)	;0x0000(r12)
    3c1a:	5d 53       	inc.b	r13		
    3c1c:	4c 4d       	mov.b	r13,	r12	
    3c1e:	0c 9e       	cmp	r14,	r12	
    3c20:	f1 3b       	jl	$-28     	;abs 0x3c04
    3c22:	1f 43       	mov	#1,	r15	;r3 As==01
    3c24:	b0 13 6e 44 	calla	#0x0446e	
    3c28:	d2 d3 19 00 	bis.b	#1,	&0x0019	;r3 As==01
    3c2c:	0b 16       	popm.a	#1,	r11	
    3c2e:	10 01       	reta			

00003c30 <flushrx>:
    3c30:	21 83       	decd	r1		
    3c32:	1e 43       	mov	#1,	r14	;r3 As==01
    3c34:	0f 41       	mov	r1,	r15	
    3c36:	b0 13 e4 3b 	calla	#0x03be4	
    3c3a:	3f 42       	mov	#8,	r15	;r2 As==11
    3c3c:	b0 13 04 3a 	calla	#0x03a04	
    3c40:	3f 42       	mov	#8,	r15	;r2 As==11
    3c42:	b0 13 04 3a 	calla	#0x03a04	
    3c46:	21 53       	incd	r1		
    3c48:	10 01       	reta			

00003c4a <off>:
    3c4a:	c2 43 d7 23 	mov.b	#0,	&0x23d7	;r3 As==00
    3c4e:	b0 13 9e 3b 	calla	#0x03b9e	
    3c52:	3f 40 06 00 	mov	#6,	r15	;#0x0006
    3c56:	b0 13 04 3a 	calla	#0x03a04	
    3c5a:	5f 42 d3 23 	mov.b	&0x23d3,r15	
    3c5e:	4f 93       	tst.b	r15		
    3c60:	02 20       	jnz	$+6      	;abs 0x3c66
    3c62:	e2 c2 25 00 	bic.b	#4,	&0x0025	;r2 As==10
    3c66:	e2 b2 20 00 	bit.b	#4,	&0x0020	;r2 As==10
    3c6a:	02 20       	jnz	$+6      	;abs 0x3c70
    3c6c:	b0 13 30 3c 	calla	#0x03c30	
    3c70:	10 01       	reta			

00003c72 <RELEASE_LOCK>:
    3c72:	d2 93 d4 23 	cmp.b	#1,	&0x23d4	;r3 As==01
    3c76:	0e 20       	jnz	$+30     	;abs 0x3c94
    3c78:	c2 93 d5 23 	tst.b	&0x23d5	
    3c7c:	04 24       	jz	$+10     	;abs 0x3c86
    3c7e:	b0 13 70 3b 	calla	#0x03b70	
    3c82:	c2 43 d5 23 	mov.b	#0,	&0x23d5	;r3 As==00
    3c86:	c2 93 d6 23 	tst.b	&0x23d6	
    3c8a:	04 24       	jz	$+10     	;abs 0x3c94
    3c8c:	b0 13 4a 3c 	calla	#0x03c4a	
    3c90:	c2 43 d6 23 	mov.b	#0,	&0x23d6	;r3 As==00
    3c94:	f2 53 d4 23 	add.b	#-1,	&0x23d4	;r3 As==11
    3c98:	10 01       	reta			

00003c9a <set_frame_filtering>:
    3c9a:	0b 14       	pushm.a	#1,	r11	
    3c9c:	4b 4f       	mov.b	r15,	r11	
    3c9e:	d2 53 d4 23 	inc.b	&0x23d4	
    3ca2:	3f 40 11 00 	mov	#17,	r15	;#0x0011
    3ca6:	b0 13 1e 3a 	calla	#0x03a1e	
    3caa:	0e 4f       	mov	r15,	r14	
    3cac:	4b 93       	tst.b	r11		
    3cae:	03 24       	jz	$+8      	;abs 0x3cb6
    3cb0:	3e d0 00 08 	bis	#2048,	r14	;#0x0800
    3cb4:	02 3c       	jmp	$+6      	;abs 0x3cba
    3cb6:	3e f0 ff f7 	and	#-2049,	r14	;#0xf7ff
    3cba:	3f 40 11 00 	mov	#17,	r15	;#0x0011
    3cbe:	b0 13 64 3a 	calla	#0x03a64	
    3cc2:	b0 13 72 3c 	calla	#0x03c72	
    3cc6:	0b 16       	popm.a	#1,	r11	
    3cc8:	10 01       	reta			

00003cca <set_auto_ack>:
    3cca:	0b 14       	pushm.a	#1,	r11	
    3ccc:	4b 4f       	mov.b	r15,	r11	
    3cce:	d2 53 d4 23 	inc.b	&0x23d4	
    3cd2:	3f 40 11 00 	mov	#17,	r15	;#0x0011
    3cd6:	b0 13 1e 3a 	calla	#0x03a1e	
    3cda:	0e 4f       	mov	r15,	r14	
    3cdc:	4b 93       	tst.b	r11		
    3cde:	03 24       	jz	$+8      	;abs 0x3ce6
    3ce0:	3e d0 10 00 	bis	#16,	r14	;#0x0010
    3ce4:	02 3c       	jmp	$+6      	;abs 0x3cea
    3ce6:	3e f0 ef ff 	and	#-17,	r14	;#0xffef
    3cea:	3f 40 11 00 	mov	#17,	r15	;#0x0011
    3cee:	b0 13 64 3a 	calla	#0x03a64	
    3cf2:	b0 13 72 3c 	calla	#0x03c72	
    3cf6:	0b 16       	popm.a	#1,	r11	
    3cf8:	10 01       	reta			

00003cfa <set_poll_mode>:
    3cfa:	d2 53 d4 23 	inc.b	&0x23d4	
    3cfe:	c2 4f d3 23 	mov.b	r15,	&0x23d3	
    3d02:	4f 93       	tst.b	r15		
    3d04:	05 24       	jz	$+12     	;abs 0x3d10
    3d06:	e2 c2 23 00 	bic.b	#4,	&0x0023	;r2 As==10
    3d0a:	e2 c2 25 00 	bic.b	#4,	&0x0025	;r2 As==10
    3d0e:	08 3c       	jmp	$+18     	;abs 0x3d20
    3d10:	e2 c2 24 00 	bic.b	#4,	&0x0024	;r2 As==10
    3d14:	e2 c2 23 00 	bic.b	#4,	&0x0023	;r2 As==10
    3d18:	e2 d2 25 00 	bis.b	#4,	&0x0025	;r2 As==10
    3d1c:	e2 c2 23 00 	bic.b	#4,	&0x0023	;r2 As==10
    3d20:	b0 13 72 3c 	calla	#0x03c72	
    3d24:	10 01       	reta			

00003d26 <cc2420_prepare>:
    3d26:	1b 14       	pushm.a	#2,	r11	
    3d28:	21 83       	decd	r1		
    3d2a:	0a 4f       	mov	r15,	r10	
    3d2c:	0b 4e       	mov	r14,	r11	
    3d2e:	3e 90 7e 00 	cmp	#126,	r14	;#0x007e
    3d32:	16 2c       	jc	$+46     	;abs 0x3d60
    3d34:	d2 53 d4 23 	inc.b	&0x23d4	
    3d38:	3f 40 09 00 	mov	#9,	r15	;#0x0009
    3d3c:	b0 13 04 3a 	calla	#0x03a04	
    3d40:	4f 4b       	mov.b	r11,	r15	
    3d42:	6f 53       	incd.b	r15		
    3d44:	c1 4f 00 00 	mov.b	r15,	0(r1)	;0x0000(r1)
    3d48:	1e 43       	mov	#1,	r14	;r3 As==01
    3d4a:	0f 41       	mov	r1,	r15	
    3d4c:	b0 13 1a 3b 	calla	#0x03b1a	
    3d50:	0e 4b       	mov	r11,	r14	
    3d52:	0f 4a       	mov	r10,	r15	
    3d54:	b0 13 1a 3b 	calla	#0x03b1a	
    3d58:	b0 13 72 3c 	calla	#0x03c72	
    3d5c:	0f 43       	clr	r15		
    3d5e:	01 3c       	jmp	$+4      	;abs 0x3d62
    3d60:	1f 43       	mov	#1,	r15	;r3 As==01
    3d62:	21 53       	incd	r1		
    3d64:	1a 16       	popm.a	#2,	r11	
    3d66:	10 01       	reta			

00003d68 <cc2420_on>:
    3d68:	c2 93 d7 23 	tst.b	&0x23d7	
    3d6c:	0c 20       	jnz	$+26     	;abs 0x3d86
    3d6e:	c2 93 d4 23 	tst.b	&0x23d4	
    3d72:	03 24       	jz	$+8      	;abs 0x3d7a
    3d74:	d2 43 d5 23 	mov.b	#1,	&0x23d5	;r3 As==01
    3d78:	06 3c       	jmp	$+14     	;abs 0x3d86
    3d7a:	d2 43 d4 23 	mov.b	#1,	&0x23d4	;r3 As==01
    3d7e:	b0 13 70 3b 	calla	#0x03b70	
    3d82:	b0 13 72 3c 	calla	#0x03c72	
    3d86:	1f 43       	mov	#1,	r15	;r3 As==01
    3d88:	10 01       	reta			

00003d8a <cc2420_transmit>:
    3d8a:	3f 90 7d 00 	cmp	#125,	r15	;#0x007d
    3d8e:	01 24       	jz	$+4      	;abs 0x3d92
    3d90:	2d 2c       	jc	$+92     	;abs 0x3dec
    3d92:	d2 53 d4 23 	inc.b	&0x23d4	
    3d96:	c2 93 52 1a 	tst.b	&0x1a52	
    3d9a:	0a 24       	jz	$+22     	;abs 0x3db0
    3d9c:	3f 40 03 00 	mov	#3,	r15	;#0x0003
    3da0:	b0 13 04 3a 	calla	#0x03a04	
    3da4:	6f 43       	mov.b	#2,	r15	;r3 As==10
    3da6:	b0 13 c0 3b 	calla	#0x03bc0	
    3daa:	3f 40 05 00 	mov	#5,	r15	;#0x0005
    3dae:	01 3c       	jmp	$+4      	;abs 0x3db2
    3db0:	2f 42       	mov	#4,	r15	;r2 As==10
    3db2:	b0 13 04 3a 	calla	#0x03a04	
    3db6:	3f 40 16 05 	mov	#1302,	r15	;#0x0516
    3dba:	e2 b3 1c 00 	bit.b	#2,	&0x001c	;r3 As==10
    3dbe:	13 24       	jz	$+40     	;abs 0x3de6
    3dc0:	b0 13 52 3b 	calla	#0x03b52	
    3dc4:	7f f2       	and.b	#8,	r15	;r2 As==11
    3dc6:	04 20       	jnz	$+10     	;abs 0x3dd0
    3dc8:	b0 13 72 3c 	calla	#0x03c72	
    3dcc:	2f 43       	mov	#2,	r15	;r3 As==10
    3dce:	10 01       	reta			
    3dd0:	b0 13 9e 3b 	calla	#0x03b9e	
    3dd4:	c2 93 d7 23 	tst.b	&0x23d7	
    3dd8:	02 20       	jnz	$+6      	;abs 0x3dde
    3dda:	b0 13 4a 3c 	calla	#0x03c4a	
    3dde:	b0 13 72 3c 	calla	#0x03c72	
    3de2:	0f 43       	clr	r15		
    3de4:	10 01       	reta			
    3de6:	3f 53       	add	#-1,	r15	;r3 As==11
    3de8:	e8 23       	jnz	$-46     	;abs 0x3dba
    3dea:	ee 3f       	jmp	$-34     	;abs 0x3dc8
    3dec:	1f 43       	mov	#1,	r15	;r3 As==01
    3dee:	10 01       	reta			

00003df0 <cc2420_send>:
    3df0:	0b 14       	pushm.a	#1,	r11	
    3df2:	0b 4e       	mov	r14,	r11	
    3df4:	b0 13 26 3d 	calla	#0x03d26	
    3df8:	0f 4b       	mov	r11,	r15	
    3dfa:	b0 13 8a 3d 	calla	#0x03d8a	
    3dfe:	0b 16       	popm.a	#1,	r11	
    3e00:	10 01       	reta			

00003e02 <cc2420_off>:
    3e02:	c2 93 d7 23 	tst.b	&0x23d7	
    3e06:	13 24       	jz	$+40     	;abs 0x3e2e
    3e08:	c2 93 d4 23 	tst.b	&0x23d4	
    3e0c:	03 24       	jz	$+8      	;abs 0x3e14
    3e0e:	d2 43 d6 23 	mov.b	#1,	&0x23d6	;r3 As==01
    3e12:	0d 3c       	jmp	$+28     	;abs 0x3e2e
    3e14:	d2 43 d4 23 	mov.b	#1,	&0x23d4	;r3 As==01
    3e18:	b0 13 52 3b 	calla	#0x03b52	
    3e1c:	7f f2       	and.b	#8,	r15	;r2 As==11
    3e1e:	03 24       	jz	$+8      	;abs 0x3e26
    3e20:	d2 43 d6 23 	mov.b	#1,	&0x23d6	;r3 As==01
    3e24:	02 3c       	jmp	$+6      	;abs 0x3e2a
    3e26:	b0 13 4a 3c 	calla	#0x03c4a	
    3e2a:	b0 13 72 3c 	calla	#0x03c72	
    3e2e:	1f 43       	mov	#1,	r15	;r3 As==01
    3e30:	10 01       	reta			

00003e32 <cc2420_cca>:
    3e32:	1b 14       	pushm.a	#2,	r11	
    3e34:	c2 93 d4 23 	tst.b	&0x23d4	
    3e38:	01 24       	jz	$+4      	;abs 0x3e3c
    3e3a:	13 3c       	jmp	$+40     	;abs 0x3e62
    3e3c:	d2 43 d4 23 	mov.b	#1,	&0x23d4	;r3 As==01
    3e40:	c2 93 d7 23 	tst.b	&0x23d7	
    3e44:	04 20       	jnz	$+10     	;abs 0x3e4e
    3e46:	b0 13 68 3d 	calla	#0x03d68	
    3e4a:	1a 43       	mov	#1,	r10	;r3 As==01
    3e4c:	01 3c       	jmp	$+4      	;abs 0x3e50
    3e4e:	0a 43       	clr	r10		
    3e50:	c2 93 d7 23 	tst.b	&0x23d7	
    3e54:	08 20       	jnz	$+18     	;abs 0x3e66
    3e56:	b0 13 72 3c 	calla	#0x03c72	
    3e5a:	0a 93       	tst	r10		
    3e5c:	02 24       	jz	$+6      	;abs 0x3e62
    3e5e:	b0 13 02 3e 	calla	#0x03e02	
    3e62:	1b 43       	mov	#1,	r11	;r3 As==01
    3e64:	0d 3c       	jmp	$+28     	;abs 0x3e80
    3e66:	6f 43       	mov.b	#2,	r15	;r3 As==10
    3e68:	b0 13 c0 3b 	calla	#0x03bc0	
    3e6c:	5b 42 20 00 	mov.b	&0x0020,r11	
    3e70:	5b 0f       	rrum	#4,	r11	
    3e72:	1b f3       	and	#1,	r11	;r3 As==01
    3e74:	0a 93       	tst	r10		
    3e76:	02 24       	jz	$+6      	;abs 0x3e7c
    3e78:	b0 13 02 3e 	calla	#0x03e02	
    3e7c:	b0 13 72 3c 	calla	#0x03c72	
    3e80:	0f 4b       	mov	r11,	r15	
    3e82:	1a 16       	popm.a	#2,	r11	
    3e84:	10 01       	reta			

00003e86 <cc2420_read>:
    3e86:	1b 14       	pushm.a	#2,	r11	
    3e88:	21 82       	sub	#4,	r1	;r2 As==10
    3e8a:	0b 4f       	mov	r15,	r11	
    3e8c:	0a 4e       	mov	r14,	r10	
    3e8e:	e2 b2 20 00 	bit.b	#4,	&0x0020	;r2 As==10
    3e92:	52 24       	jz	$+166    	;abs 0x3f38
    3e94:	d2 53 d4 23 	inc.b	&0x23d4	
    3e98:	1e 43       	mov	#1,	r14	;r3 As==01
    3e9a:	0f 41       	mov	r1,	r15	
    3e9c:	2f 53       	incd	r15		
    3e9e:	b0 13 e4 3b 	calla	#0x03be4	
    3ea2:	5d 41 02 00 	mov.b	2(r1),	r13	;0x0002(r1)
    3ea6:	4d 93       	tst.b	r13		
    3ea8:	43 38       	jl	$+136    	;abs 0x3f30
    3eaa:	7d 90 03 00 	cmp.b	#3,	r13	;#0x0003
    3eae:	40 28       	jnc	$+130    	;abs 0x3f30
    3eb0:	4e 4d       	mov.b	r13,	r14	
    3eb2:	2e 83       	decd	r14		
    3eb4:	0a 9e       	cmp	r14,	r10	
    3eb6:	3c 28       	jnc	$+122    	;abs 0x3f30
    3eb8:	0f 4b       	mov	r11,	r15	
    3eba:	b0 13 e4 3b 	calla	#0x03be4	
    3ebe:	2e 43       	mov	#2,	r14	;r3 As==10
    3ec0:	0f 41       	mov	r1,	r15	
    3ec2:	b0 13 e4 3b 	calla	#0x03be4	
    3ec6:	5f 41 01 00 	mov.b	1(r1),	r15	;0x0001(r1)
    3eca:	4f 93       	tst.b	r15		
    3ecc:	18 34       	jge	$+50     	;abs 0x3efe
    3ece:	6e 41       	mov.b	@r1,	r14	
    3ed0:	7e 50 d3 ff 	add.b	#-45,	r14	;#0xffd3
    3ed4:	c2 4e 10 24 	mov.b	r14,	&0x2410	
    3ed8:	7f f0 7f 00 	and.b	#127,	r15	;#0x007f
    3edc:	c2 4f 14 24 	mov.b	r15,	&0x2414	
    3ee0:	5f 42 d3 23 	mov.b	&0x23d3,r15	
    3ee4:	4f 93       	tst.b	r15		
    3ee6:	0d 20       	jnz	$+28     	;abs 0x3f02
    3ee8:	8e 11       	sxt	r14		
    3eea:	6f 42       	mov.b	#4,	r15	;r2 As==10
    3eec:	b0 13 56 63 	calla	#0x06356	
    3ef0:	5e 42 14 24 	mov.b	&0x2414,r14	
    3ef4:	7f 40 03 00 	mov.b	#3,	r15	;#0x0003
    3ef8:	b0 13 56 63 	calla	#0x06356	
    3efc:	02 3c       	jmp	$+6      	;abs 0x3f02
    3efe:	e1 43 02 00 	mov.b	#2,	2(r1)	;r3 As==10, 0x0002(r1)
    3f02:	5f 42 d3 23 	mov.b	&0x23d3,r15	
    3f06:	4f 93       	tst.b	r15		
    3f08:	0d 20       	jnz	$+28     	;abs 0x3f24
    3f0a:	e2 b2 20 00 	bit.b	#4,	&0x0020	;r2 As==10
    3f0e:	0a 24       	jz	$+22     	;abs 0x3f24
    3f10:	f2 b2 20 00 	bit.b	#8,	&0x0020	;r2 As==11
    3f14:	03 20       	jnz	$+8      	;abs 0x3f1c
    3f16:	b0 13 30 3c 	calla	#0x03c30	
    3f1a:	04 3c       	jmp	$+10     	;abs 0x3f24
    3f1c:	3f 40 0c 11 	mov	#4364,	r15	;#0x110c
    3f20:	b0 13 98 67 	calla	#0x06798	
    3f24:	b0 13 72 3c 	calla	#0x03c72	
    3f28:	5f 41 02 00 	mov.b	2(r1),	r15	;0x0002(r1)
    3f2c:	2f 83       	decd	r15		
    3f2e:	05 3c       	jmp	$+12     	;abs 0x3f3a
    3f30:	b0 13 30 3c 	calla	#0x03c30	
    3f34:	b0 13 72 3c 	calla	#0x03c72	
    3f38:	0f 43       	clr	r15		
    3f3a:	21 52       	add	#4,	r1	;r2 As==10
    3f3c:	1a 16       	popm.a	#2,	r11	
    3f3e:	10 01       	reta			

00003f40 <process_thread_cc2420_process>:
    3f40:	0b 14       	pushm.a	#1,	r11	
    3f42:	0b 4f       	mov	r15,	r11	
    3f44:	2f 4f       	mov	@r15,	r15	
    3f46:	0f 93       	tst	r15		
    3f48:	04 24       	jz	$+10     	;abs 0x3f52
    3f4a:	3f 90 81 03 	cmp	#897,	r15	;#0x0381
    3f4e:	15 20       	jnz	$+44     	;abs 0x3f7a
    3f50:	1b 3c       	jmp	$+56     	;abs 0x3f88
    3f52:	bb 40 81 03 	mov	#897,	0(r11)	;#0x0381, 0x0000(r11)
    3f56:	00 00 
    3f58:	15 3c       	jmp	$+44     	;abs 0x3f84
    3f5a:	7e 90 82 ff 	cmp.b	#-126,	r14	;#0xff82
    3f5e:	12 20       	jnz	$+38     	;abs 0x3f84
    3f60:	b0 13 d4 62 	calla	#0x062d4	
    3f64:	b0 13 1e 62 	calla	#0x0621e	
    3f68:	3e 40 80 00 	mov	#128,	r14	;#0x0080
    3f6c:	b0 13 86 3e 	calla	#0x03e86	
    3f70:	b0 13 02 62 	calla	#0x06202	
    3f74:	80 13 62 99 	calla	&0x09962	
    3f78:	ec 3f       	jmp	$-38     	;abs 0x3f52
    3f7a:	8b 43 00 00 	mov	#0,	0(r11)	;r3 As==00, 0x0000(r11)
    3f7e:	7f 40 03 00 	mov.b	#3,	r15	;#0x0003
    3f82:	07 3c       	jmp	$+16     	;abs 0x3f92
    3f84:	5f 43       	mov.b	#1,	r15	;r3 As==01
    3f86:	05 3c       	jmp	$+12     	;abs 0x3f92
    3f88:	5f 42 d3 23 	mov.b	&0x23d3,r15	
    3f8c:	4f 93       	tst.b	r15		
    3f8e:	e5 27       	jz	$-52     	;abs 0x3f5a
    3f90:	f9 3f       	jmp	$-12     	;abs 0x3f84
    3f92:	0b 16       	popm.a	#1,	r11	
    3f94:	10 01       	reta			

00003f96 <cc2420_set_channel>:
    3f96:	0b 14       	pushm.a	#1,	r11	
    3f98:	0b 4f       	mov	r15,	r11	
    3f9a:	d2 53 d4 23 	inc.b	&0x23d4	
    3f9e:	82 4f da 1a 	mov	r15,	&0x1ada	
    3fa2:	b0 13 9e 3b 	calla	#0x03b9e	
    3fa6:	0e 4b       	mov	r11,	r14	
    3fa8:	5e 06       	rlam	#2,	r14	
    3faa:	0e 5b       	add	r11,	r14	
    3fac:	3e 50 2e 41 	add	#16686,	r14	;#0x412e
    3fb0:	3f 40 18 00 	mov	#24,	r15	;#0x0018
    3fb4:	b0 13 64 3a 	calla	#0x03a64	
    3fb8:	c2 93 d7 23 	tst.b	&0x23d7	
    3fbc:	04 24       	jz	$+10     	;abs 0x3fc6
    3fbe:	3f 40 03 00 	mov	#3,	r15	;#0x0003
    3fc2:	b0 13 04 3a 	calla	#0x03a04	
    3fc6:	b0 13 72 3c 	calla	#0x03c72	
    3fca:	1f 43       	mov	#1,	r15	;r3 As==01
    3fcc:	0b 16       	popm.a	#1,	r11	
    3fce:	10 01       	reta			

00003fd0 <cc2420_set_pan_addr>:
    3fd0:	0b 14       	pushm.a	#1,	r11	
    3fd2:	21 82       	sub	#4,	r1	;r2 As==10
    3fd4:	81 4f 00 00 	mov	r15,	0(r1)	;0x0000(r1)
    3fd8:	81 4e 02 00 	mov	r14,	2(r1)	;0x0002(r1)
    3fdc:	0b 4d       	mov	r13,	r11	
    3fde:	d2 53 d4 23 	inc.b	&0x23d4	
    3fe2:	0c 43       	clr	r12		
    3fe4:	2d 43       	mov	#2,	r13	;r3 As==10
    3fe6:	3e 40 68 01 	mov	#360,	r14	;#0x0168
    3fea:	0f 41       	mov	r1,	r15	
    3fec:	b0 13 a8 3a 	calla	#0x03aa8	
    3ff0:	0c 43       	clr	r12		
    3ff2:	2d 43       	mov	#2,	r13	;r3 As==10
    3ff4:	3e 40 6a 01 	mov	#362,	r14	;#0x016a
    3ff8:	0f 41       	mov	r1,	r15	
    3ffa:	2f 53       	incd	r15		
    3ffc:	b0 13 a8 3a 	calla	#0x03aa8	
    4000:	0b 93       	tst	r11		
    4002:	07 24       	jz	$+16     	;abs 0x4012
    4004:	1c 43       	mov	#1,	r12	;r3 As==01
    4006:	3d 42       	mov	#8,	r13	;r2 As==11
    4008:	3e 40 60 01 	mov	#352,	r14	;#0x0160
    400c:	0f 4b       	mov	r11,	r15	
    400e:	b0 13 a8 3a 	calla	#0x03aa8	
    4012:	b0 13 72 3c 	calla	#0x03c72	
    4016:	21 52       	add	#4,	r1	;r2 As==10
    4018:	0b 16       	popm.a	#1,	r11	
    401a:	10 01       	reta			

0000401c <cc2420_interrupt>:
    401c:	e2 c2 23 00 	bic.b	#4,	&0x0023	;r2 As==10
    4020:	3f 40 0c 11 	mov	#4364,	r15	;#0x110c
    4024:	b0 13 98 67 	calla	#0x06798	
    4028:	92 42 12 24 	mov	&0x2412,&0x1ad4	
    402c:	d4 1a 
    402e:	1f 43       	mov	#1,	r15	;r3 As==01
    4030:	10 01       	reta			

00004032 <cc2420_set_txpower>:
    4032:	0b 14       	pushm.a	#1,	r11	
    4034:	4b 4f       	mov.b	r15,	r11	
    4036:	d2 53 d4 23 	inc.b	&0x23d4	
    403a:	3f 40 15 00 	mov	#21,	r15	;#0x0015
    403e:	b0 13 1e 3a 	calla	#0x03a1e	
    4042:	3f f0 e0 ff 	and	#-32,	r15	;#0xffe0
    4046:	0e 4b       	mov	r11,	r14	
    4048:	3e f0 1f 00 	and	#31,	r14	;#0x001f
    404c:	0e df       	bis	r15,	r14	
    404e:	3f 40 15 00 	mov	#21,	r15	;#0x0015
    4052:	b0 13 64 3a 	calla	#0x03a64	
    4056:	b0 13 72 3c 	calla	#0x03c72	
    405a:	0b 16       	popm.a	#1,	r11	
    405c:	10 01       	reta			

0000405e <cc2420_get_txpower>:
    405e:	0b 14       	pushm.a	#1,	r11	
    4060:	d2 53 d4 23 	inc.b	&0x23d4	
    4064:	3f 40 15 00 	mov	#21,	r15	;#0x0015
    4068:	b0 13 1e 3a 	calla	#0x03a1e	
    406c:	0b 4f       	mov	r15,	r11	
    406e:	b0 13 72 3c 	calla	#0x03c72	
    4072:	0f 4b       	mov	r11,	r15	
    4074:	3f f0 1f 00 	and	#31,	r15	;#0x001f
    4078:	0b 16       	popm.a	#1,	r11	
    407a:	10 01       	reta			

0000407c <cc2420_rssi>:
    407c:	1b 14       	pushm.a	#2,	r11	
    407e:	c2 93 d4 23 	tst.b	&0x23d4	
    4082:	1c 20       	jnz	$+58     	;abs 0x40bc
    4084:	d2 43 d4 23 	mov.b	#1,	&0x23d4	;r3 As==01
    4088:	c2 93 d7 23 	tst.b	&0x23d7	
    408c:	04 20       	jnz	$+10     	;abs 0x4096
    408e:	b0 13 68 3d 	calla	#0x03d68	
    4092:	1a 43       	mov	#1,	r10	;r3 As==01
    4094:	01 3c       	jmp	$+4      	;abs 0x4098
    4096:	0a 43       	clr	r10		
    4098:	6f 43       	mov.b	#2,	r15	;r3 As==10
    409a:	b0 13 c0 3b 	calla	#0x03bc0	
    409e:	3f 40 13 00 	mov	#19,	r15	;#0x0013
    40a2:	b0 13 1e 3a 	calla	#0x03a1e	
    40a6:	8f 11       	sxt	r15		
    40a8:	0b 4f       	mov	r15,	r11	
    40aa:	3b 50 d3 ff 	add	#-45,	r11	;#0xffd3
    40ae:	0a 93       	tst	r10		
    40b0:	02 24       	jz	$+6      	;abs 0x40b6
    40b2:	b0 13 02 3e 	calla	#0x03e02	
    40b6:	b0 13 72 3c 	calla	#0x03c72	
    40ba:	01 3c       	jmp	$+4      	;abs 0x40be
    40bc:	0b 43       	clr	r11		
    40be:	0f 4b       	mov	r11,	r15	
    40c0:	1a 16       	popm.a	#2,	r11	
    40c2:	10 01       	reta			

000040c4 <get_value>:
    40c4:	1b 14       	pushm.a	#2,	r11	
    40c6:	0b 4e       	mov	r14,	r11	
    40c8:	0e 93       	tst	r14		
    40ca:	86 24       	jz	$+270    	;abs 0x41d8
    40cc:	3f 90 19 00 	cmp	#25,	r15	;#0x0019
    40d0:	85 2c       	jc	$+268    	;abs 0x41dc
    40d2:	5f 06       	rlam	#2,	r15	
    40d4:	00 18 5f 4f 	movx.a	39024(r15),r15	;0x09870(r15)
    40d8:	70 98 
    40da:	c0 0f       	bra	r15		
    40dc:	3f 40 12 00 	mov	#18,	r15	;#0x0012
    40e0:	b0 13 1e 3a 	calla	#0x03a1e	
    40e4:	3f f2       	and	#8,	r15	;r2 As==11
    40e6:	03 24       	jz	$+8      	;abs 0x40ee
    40e8:	ab 43 00 00 	mov	#2,	0(r11)	;r3 As==10, 0x0000(r11)
    40ec:	07 3c       	jmp	$+16     	;abs 0x40fc
    40ee:	1f 43       	mov	#1,	r15	;r3 As==01
    40f0:	c2 93 d7 23 	tst.b	&0x23d7	
    40f4:	01 20       	jnz	$+4      	;abs 0x40f8
    40f6:	0f 43       	clr	r15		
    40f8:	8b 4f 00 00 	mov	r15,	0(r11)	;0x0000(r11)
    40fc:	0f 43       	clr	r15		
    40fe:	6f 3c       	jmp	$+224    	;abs 0x41de
    4100:	9e 42 da 1a 	mov	&0x1ada,0(r14)	;0x0000(r14)
    4104:	00 00 
    4106:	fa 3f       	jmp	$-10     	;abs 0x40fc
    4108:	8e 43 00 00 	mov	#0,	0(r14)	;r3 As==00, 0x0000(r14)
    410c:	3f 40 11 00 	mov	#17,	r15	;#0x0011
    4110:	b0 13 1e 3a 	calla	#0x03a1e	
    4114:	3f b0 00 08 	bit	#2048,	r15	;#0x0800
    4118:	02 24       	jz	$+6      	;abs 0x411e
    411a:	9b d3 00 00 	bis	#1,	0(r11)	;r3 As==01, 0x0000(r11)
    411e:	3f 40 11 00 	mov	#17,	r15	;#0x0011
    4122:	b0 13 1e 3a 	calla	#0x03a1e	
    4126:	3f f0 10 00 	and	#16,	r15	;#0x0010
    412a:	02 24       	jz	$+6      	;abs 0x4130
    412c:	ab d3 00 00 	bis	#2,	0(r11)	;r3 As==10, 0x0000(r11)
    4130:	5f 42 d3 23 	mov.b	&0x23d3,r15	
    4134:	4f 93       	tst.b	r15		
    4136:	01 20       	jnz	$+4      	;abs 0x413a
    4138:	e1 3f       	jmp	$-60     	;abs 0x40fc
    413a:	ab d2 00 00 	bis	#4,	0(r11)	;r2 As==10, 0x0000(r11)
    413e:	de 3f       	jmp	$-66     	;abs 0x40fc
    4140:	8e 43 00 00 	mov	#0,	0(r14)	;r3 As==00, 0x0000(r14)
    4144:	c2 93 52 1a 	tst.b	&0x1a52	
    4148:	d9 27       	jz	$-76     	;abs 0x40fc
    414a:	9e 43 00 00 	mov	#1,	0(r14)	;r3 As==01, 0x0000(r14)
    414e:	d6 3f       	jmp	$-82     	;abs 0x40fc
    4150:	b0 13 5e 40 	calla	#0x0405e	
    4154:	bb 40 e7 ff 	mov	#-25,	0(r11)	;#0xffe7, 0x0000(r11)
    4158:	00 00 
    415a:	0e 43       	clr	r14		
    415c:	0d 4e       	mov	r14,	r13	
    415e:	5d 02       	rlam	#1,	r13	
    4160:	5c 4d 49 99 	mov.b	-26295(r13),r12	;0x9949(r13)
    4164:	0f 9c       	cmp	r12,	r15	
    4166:	04 38       	jl	$+10     	;abs 0x4170
    4168:	db 4d 48 99 	mov.b	-26296(r13),0(r11)	;0x9948(r13), 0x0000(r11)
    416c:	00 00 
    416e:	19 3c       	jmp	$+52     	;abs 0x41a2
    4170:	1e 53       	inc	r14		
    4172:	3e 92       	cmp	#8,	r14	;r2 As==11
    4174:	f3 23       	jnz	$-24     	;abs 0x415c
    4176:	c2 3f       	jmp	$-122    	;abs 0x40fc
    4178:	d2 53 d4 23 	inc.b	&0x23d4	
    417c:	3f 40 13 00 	mov	#19,	r15	;#0x0013
    4180:	b0 13 1e 3a 	calla	#0x03a1e	
    4184:	0a 4f       	mov	r15,	r10	
    4186:	b0 13 72 3c 	calla	#0x03c72	
    418a:	0f 4a       	mov	r10,	r15	
    418c:	8f 10       	swpb	r15		
    418e:	8f 11       	sxt	r15		
    4190:	3f 50 d3 ff 	add	#-45,	r15	;#0xffd3
    4194:	b1 3f       	jmp	$-156    	;abs 0x40f8
    4196:	b0 13 7c 40 	calla	#0x0407c	
    419a:	ae 3f       	jmp	$-162    	;abs 0x40f8
    419c:	de 42 10 24 	mov.b	&0x2410,0(r14)	;0x0000(r14)
    41a0:	00 00 
    41a2:	ab 11       	sxt	@r11		
    41a4:	ab 3f       	jmp	$-168    	;abs 0x40fc
    41a6:	de 42 14 24 	mov.b	&0x2414,0(r14)	;0x0000(r14)
    41aa:	00 00 
    41ac:	ce 43 01 00 	mov.b	#0,	1(r14)	;r3 As==00, 0x0001(r14)
    41b0:	a5 3f       	jmp	$-180    	;abs 0x40fc
    41b2:	be 40 0b 00 	mov	#11,	0(r14)	;#0x000b, 0x0000(r14)
    41b6:	00 00 
    41b8:	a1 3f       	jmp	$-188    	;abs 0x40fc
    41ba:	be 40 1a 00 	mov	#26,	0(r14)	;#0x001a, 0x0000(r14)
    41be:	00 00 
    41c0:	9d 3f       	jmp	$-196    	;abs 0x40fc
    41c2:	be 40 e7 ff 	mov	#-25,	0(r14)	;#0xffe7, 0x0000(r14)
    41c6:	00 00 
    41c8:	99 3f       	jmp	$-204    	;abs 0x40fc
    41ca:	8e 43 00 00 	mov	#0,	0(r14)	;r3 As==00, 0x0000(r14)
    41ce:	96 3f       	jmp	$-210    	;abs 0x40fc
    41d0:	be 40 7d 00 	mov	#125,	0(r14)	;#0x007d, 0x0000(r14)
    41d4:	00 00 
    41d6:	92 3f       	jmp	$-218    	;abs 0x40fc
    41d8:	2f 43       	mov	#2,	r15	;r3 As==10
    41da:	01 3c       	jmp	$+4      	;abs 0x41de
    41dc:	1f 43       	mov	#1,	r15	;r3 As==01
    41de:	1a 16       	popm.a	#2,	r11	
    41e0:	10 01       	reta			

000041e2 <cc2420_set_cca_threshold>:
    41e2:	d2 53 d4 23 	inc.b	&0x23d4	
    41e6:	4e 4f       	mov.b	r15,	r14	
    41e8:	8e 10       	swpb	r14		
    41ea:	3f 40 13 00 	mov	#19,	r15	;#0x0013
    41ee:	b0 13 64 3a 	calla	#0x03a64	
    41f2:	b0 13 72 3c 	calla	#0x03c72	
    41f6:	10 01       	reta			

000041f8 <set_value>:
    41f8:	0b 14       	pushm.a	#1,	r11	
    41fa:	21 83       	decd	r1		
    41fc:	0b 4e       	mov	r14,	r11	
    41fe:	3f 92       	cmp	#8,	r15	;r2 As==11
    4200:	9a 2c       	jc	$+310    	;abs 0x4336
    4202:	5f 06       	rlam	#2,	r15	
    4204:	00 18 5f 4f 	movx.a	39124(r15),r15	;0x098d4(r15)
    4208:	d4 98 
    420a:	c0 0f       	bra	r15		
    420c:	1e 93       	cmp	#1,	r14	;r3 As==01
    420e:	03 20       	jnz	$+8      	;abs 0x4216
    4210:	b0 13 68 3d 	calla	#0x03d68	
    4214:	8e 3c       	jmp	$+286    	;abs 0x4332
    4216:	0e 93       	tst	r14		
    4218:	03 20       	jnz	$+8      	;abs 0x4220
    421a:	b0 13 02 3e 	calla	#0x03e02	
    421e:	89 3c       	jmp	$+276    	;abs 0x4332
    4220:	0f 4e       	mov	r14,	r15	
    4222:	2f 83       	decd	r15		
    4224:	2f 93       	cmp	#2,	r15	;r3 As==10
    4226:	89 2c       	jc	$+276    	;abs 0x433a
    4228:	0e 41       	mov	r1,	r14	
    422a:	0f 43       	clr	r15		
    422c:	b0 13 c4 40 	calla	#0x040c4	
    4230:	2b 93       	cmp	#2,	r11	;r3 As==10
    4232:	27 20       	jnz	$+80     	;abs 0x4282
    4234:	2e 41       	mov	@r1,	r14	
    4236:	2e 93       	cmp	#2,	r14	;r3 As==10
    4238:	7c 24       	jz	$+250    	;abs 0x4332
    423a:	5f 43       	mov.b	#1,	r15	;r3 As==01
    423c:	1e 93       	cmp	#1,	r14	;r3 As==01
    423e:	01 24       	jz	$+4      	;abs 0x4242
    4240:	4f 43       	clr.b	r15		
    4242:	c2 4f d8 23 	mov.b	r15,	&0x23d8	
    4246:	b0 13 4a 3c 	calla	#0x03c4a	
    424a:	3f 40 12 00 	mov	#18,	r15	;#0x0012
    424e:	b0 13 1e 3a 	calla	#0x03a1e	
    4252:	82 4f d6 1a 	mov	r15,	&0x1ad6	
    4256:	3e 40 0c 05 	mov	#1292,	r14	;#0x050c
    425a:	3f 40 12 00 	mov	#18,	r15	;#0x0012
    425e:	b0 13 64 3a 	calla	#0x03a64	
    4262:	3f 40 2e 00 	mov	#46,	r15	;#0x002e
    4266:	b0 13 1e 3a 	calla	#0x03a1e	
    426a:	82 4f d8 1a 	mov	r15,	&0x1ad8	
    426e:	3e 40 00 18 	mov	#6144,	r14	;#0x1800
    4272:	3f 40 2e 00 	mov	#46,	r15	;#0x002e
    4276:	b0 13 64 3a 	calla	#0x03a64	
    427a:	2f 42       	mov	#4,	r15	;r2 As==10
    427c:	b0 13 04 3a 	calla	#0x03a04	
    4280:	58 3c       	jmp	$+178    	;abs 0x4332
    4282:	a1 93 00 00 	cmp	#2,	0(r1)	;r3 As==10, 0x0000(r1)
    4286:	55 20       	jnz	$+172    	;abs 0x4332
    4288:	3f 40 06 00 	mov	#6,	r15	;#0x0006
    428c:	b0 13 04 3a 	calla	#0x03a04	
    4290:	1e 42 d8 1a 	mov	&0x1ad8,r14	
    4294:	3f 40 2e 00 	mov	#46,	r15	;#0x002e
    4298:	b0 13 64 3a 	calla	#0x03a64	
    429c:	1e 42 d6 1a 	mov	&0x1ad6,r14	
    42a0:	3f 40 12 00 	mov	#18,	r15	;#0x0012
    42a4:	b0 13 64 3a 	calla	#0x03a64	
    42a8:	c2 93 d8 23 	tst.b	&0x23d8	
    42ac:	42 24       	jz	$+134    	;abs 0x4332
    42ae:	b0 13 70 3b 	calla	#0x03b70	
    42b2:	3f 3c       	jmp	$+128    	;abs 0x4332
    42b4:	0f 4e       	mov	r14,	r15	
    42b6:	3f 50 f5 ff 	add	#-11,	r15	;#0xfff5
    42ba:	3f 90 10 00 	cmp	#16,	r15	;#0x0010
    42be:	3d 2c       	jc	$+124    	;abs 0x433a
    42c0:	0f 4e       	mov	r14,	r15	
    42c2:	b0 13 96 3f 	calla	#0x03f96	
    42c6:	35 3c       	jmp	$+108    	;abs 0x4332
    42c8:	3e b0 f8 ff 	bit	#-8,	r14	;#0xfff8
    42cc:	36 20       	jnz	$+110    	;abs 0x433a
    42ce:	4f 4e       	mov.b	r14,	r15	
    42d0:	5f f3       	and.b	#1,	r15	;r3 As==01
    42d2:	b0 13 9a 3c 	calla	#0x03c9a	
    42d6:	0f 4b       	mov	r11,	r15	
    42d8:	5f 03       	rrum	#1,	r15	
    42da:	5f f3       	and.b	#1,	r15	;r3 As==01
    42dc:	b0 13 ca 3c 	calla	#0x03cca	
    42e0:	0f 4b       	mov	r11,	r15	
    42e2:	5f 07       	rrum	#2,	r15	
    42e4:	5f f3       	and.b	#1,	r15	;r3 As==01
    42e6:	b0 13 fa 3c 	calla	#0x03cfa	
    42ea:	23 3c       	jmp	$+72     	;abs 0x4332
    42ec:	3e b0 fe ff 	bit	#-2,	r14	;#0xfffe
    42f0:	24 20       	jnz	$+74     	;abs 0x433a
    42f2:	5b f3       	and.b	#1,	r11	;r3 As==01
    42f4:	c2 4b 52 1a 	mov.b	r11,	&0x1a52	
    42f8:	1c 3c       	jmp	$+58     	;abs 0x4332
    42fa:	0f 4e       	mov	r14,	r15	
    42fc:	3f 50 19 00 	add	#25,	r15	;#0x0019
    4300:	3f 90 1a 00 	cmp	#26,	r15	;#0x001a
    4304:	1a 2c       	jc	$+54     	;abs 0x433a
    4306:	1f 43       	mov	#1,	r15	;r3 As==01
    4308:	0e 4f       	mov	r15,	r14	
    430a:	5e 02       	rlam	#1,	r14	
    430c:	5e 4e 48 99 	mov.b	-26296(r14),r14	;0x9948(r14)
    4310:	8e 11       	sxt	r14		
    4312:	0e 9b       	cmp	r11,	r14	
    4314:	03 38       	jl	$+8      	;abs 0x431c
    4316:	1f 53       	inc	r15		
    4318:	3f 92       	cmp	#8,	r15	;r2 As==11
    431a:	f6 23       	jnz	$-18     	;abs 0x4308
    431c:	5f 02       	rlam	#1,	r15	
    431e:	5f 4f 47 99 	mov.b	-26297(r15),r15	;0x9947(r15)
    4322:	b0 13 32 40 	calla	#0x04032	
    4326:	05 3c       	jmp	$+12     	;abs 0x4332
    4328:	0f 4e       	mov	r14,	r15	
    432a:	3f 50 2d 00 	add	#45,	r15	;#0x002d
    432e:	b0 13 e2 41 	calla	#0x041e2	
    4332:	0f 43       	clr	r15		
    4334:	03 3c       	jmp	$+8      	;abs 0x433c
    4336:	1f 43       	mov	#1,	r15	;r3 As==01
    4338:	01 3c       	jmp	$+4      	;abs 0x433c
    433a:	2f 43       	mov	#2,	r15	;r3 As==10
    433c:	21 53       	incd	r1		
    433e:	0b 16       	popm.a	#1,	r11	
    4340:	10 01       	reta			

00004342 <cc2420_init>:
    4342:	0b 14       	pushm.a	#1,	r11	
    4344:	b0 13 8c 58 	calla	#0x0588c	
    4348:	0b 4f       	mov	r15,	r11	
    434a:	b0 13 e2 39 	calla	#0x039e2	
    434e:	e2 c2 25 00 	bic.b	#4,	&0x0025	;r2 As==10
    4352:	e2 c2 24 00 	bic.b	#4,	&0x0024	;r2 As==10
    4356:	e2 c2 23 00 	bic.b	#4,	&0x0023	;r2 As==10
    435a:	02 db       	bis	r11,	r2	
    435c:	f2 d0 20 00 	bis.b	#32,	&0x001d	;#0x0020
    4360:	1d 00 
    4362:	3f 40 fa 00 	mov	#250,	r15	;#0x00fa
    4366:	b0 13 6e 44 	calla	#0x0446e	
    436a:	f2 f0 bf ff 	and.b	#-65,	&0x001d	;#0xffbf
    436e:	1d 00 
    4370:	3f 40 7f 00 	mov	#127,	r15	;#0x007f
    4374:	b0 13 6e 44 	calla	#0x0446e	
    4378:	f2 d0 40 00 	bis.b	#64,	&0x001d	;#0x0040
    437c:	1d 00 
    437e:	3f 40 7d 00 	mov	#125,	r15	;#0x007d
    4382:	b0 13 6e 44 	calla	#0x0446e	
    4386:	1f 43       	mov	#1,	r15	;r3 As==01
    4388:	b0 13 04 3a 	calla	#0x03a04	
    438c:	7f 40 40 00 	mov.b	#64,	r15	;#0x0040
    4390:	b0 13 c0 3b 	calla	#0x03bc0	
    4394:	5f 43       	mov.b	#1,	r15	;r3 As==01
    4396:	b0 13 ca 3c 	calla	#0x03cca	
    439a:	5f 43       	mov.b	#1,	r15	;r3 As==01
    439c:	b0 13 9a 3c 	calla	#0x03c9a	
    43a0:	3f 40 11 00 	mov	#17,	r15	;#0x0011
    43a4:	b0 13 1e 3a 	calla	#0x03a1e	
    43a8:	0e 4f       	mov	r15,	r14	
    43aa:	3e d0 20 00 	bis	#32,	r14	;#0x0020
    43ae:	3f 40 11 00 	mov	#17,	r15	;#0x0011
    43b2:	b0 13 64 3a 	calla	#0x03a64	
    43b6:	3e 40 00 05 	mov	#1280,	r14	;#0x0500
    43ba:	3f 40 12 00 	mov	#18,	r15	;#0x0012
    43be:	b0 13 64 3a 	calla	#0x03a64	
    43c2:	3f 40 17 00 	mov	#23,	r15	;#0x0017
    43c6:	b0 13 1e 3a 	calla	#0x03a1e	
    43ca:	0e 4f       	mov	r15,	r14	
    43cc:	3e d0 00 20 	bis	#8192,	r14	;#0x2000
    43d0:	3f 40 17 00 	mov	#23,	r15	;#0x0017
    43d4:	b0 13 64 3a 	calla	#0x03a64	
    43d8:	3e 40 7f 00 	mov	#127,	r14	;#0x007f
    43dc:	3f 40 1c 00 	mov	#28,	r15	;#0x001c
    43e0:	b0 13 64 3a 	calla	#0x03a64	
    43e4:	0e 43       	clr	r14		
    43e6:	3f 40 19 00 	mov	#25,	r15	;#0x0019
    43ea:	b0 13 64 3a 	calla	#0x03a64	
    43ee:	0e 43       	clr	r14		
    43f0:	3f 40 1a 00 	mov	#26,	r15	;#0x001a
    43f4:	b0 13 64 3a 	calla	#0x03a64	
    43f8:	0d 43       	clr	r13		
    43fa:	0e 43       	clr	r14		
    43fc:	3f 43       	mov	#-1,	r15	;r3 As==11
    43fe:	b0 13 d0 3f 	calla	#0x03fd0	
    4402:	3f 40 1a 00 	mov	#26,	r15	;#0x001a
    4406:	b0 13 96 3f 	calla	#0x03f96	
    440a:	3f 40 d3 ff 	mov	#-45,	r15	;#0xffd3
    440e:	b0 13 e2 41 	calla	#0x041e2	
    4412:	b0 13 30 3c 	calla	#0x03c30	
    4416:	4f 43       	clr.b	r15		
    4418:	b0 13 fa 3c 	calla	#0x03cfa	
    441c:	0e 43       	clr	r14		
    441e:	3f 40 0c 11 	mov	#4364,	r15	;#0x110c
    4422:	b0 13 62 67 	calla	#0x06762	
    4426:	1f 43       	mov	#1,	r15	;r3 As==01
    4428:	0b 16       	popm.a	#1,	r11	
    442a:	10 01       	reta			

0000442c <clock_time>:
    442c:	1e 42 de 1a 	mov	&0x1ade,r14	
    4430:	1f 42 e0 1a 	mov	&0x1ae0,r15	
    4434:	1c 42 de 1a 	mov	&0x1ade,r12	
    4438:	1d 42 e0 1a 	mov	&0x1ae0,r13	
    443c:	0e 9c       	cmp	r12,	r14	
    443e:	f6 23       	jnz	$-18     	;abs 0x442c
    4440:	0f 9d       	cmp	r13,	r15	
    4442:	f4 23       	jnz	$-22     	;abs 0x442c
    4444:	10 01       	reta			

00004446 <clock_init>:
    4446:	32 c2       	dint			
    4448:	03 43       	nop			
    444a:	b2 40 04 01 	mov	#260,	&0x0160	;#0x0104
    444e:	60 01 
    4450:	b2 40 10 00 	mov	#16,	&0x0164	;#0x0010
    4454:	64 01 
    4456:	b2 40 00 01 	mov	#256,	&0x0174	;#0x0100
    445a:	74 01 
    445c:	b2 d0 20 00 	bis	#32,	&0x0160	;#0x0020
    4460:	60 01 
    4462:	82 43 de 1a 	mov	#0,	&0x1ade	;r3 As==00
    4466:	82 43 e0 1a 	mov	#0,	&0x1ae0	;r3 As==00
    446a:	32 d2       	eint			
    446c:	10 01       	reta			

0000446e <clock_delay>:
    446e:	02 3c       	jmp	$+6      	;abs 0x4474
    4470:	03 43       	nop			
    4472:	3f 53       	add	#-1,	r15	;r3 As==11
    4474:	0f 93       	tst	r15		
    4476:	fc 23       	jnz	$-6      	;abs 0x4470
    4478:	10 01       	reta			

0000447a <clock_wait>:
    447a:	3b 14       	pushm.a	#4,	r11	
    447c:	08 4e       	mov	r14,	r8	
    447e:	09 4f       	mov	r15,	r9	
    4480:	b0 13 2c 44 	calla	#0x0442c	
    4484:	0a 4e       	mov	r14,	r10	
    4486:	0b 4f       	mov	r15,	r11	
    4488:	b0 13 2c 44 	calla	#0x0442c	
    448c:	0e 8a       	sub	r10,	r14	
    448e:	0f 7b       	subc	r11,	r15	
    4490:	0f 99       	cmp	r9,	r15	
    4492:	fa 2b       	jnc	$-10     	;abs 0x4488
    4494:	02 20       	jnz	$+6      	;abs 0x449a
    4496:	0e 98       	cmp	r8,	r14	
    4498:	f7 2b       	jnc	$-16     	;abs 0x4488
    449a:	38 16       	popm.a	#4,	r11	
    449c:	10 01       	reta			

0000449e <init_platform>:
    449e:	0e 43       	clr	r14		
    44a0:	3f 40 18 1a 	mov	#6680,	r15	;#0x1a18
    44a4:	b0 13 62 67 	calla	#0x06762	
    44a8:	10 01       	reta			

000044aa <schedule_transmission>:
    44aa:	2b 14       	pushm.a	#3,	r11	
    44ac:	09 4f       	mov	r15,	r9	
    44ae:	5e 4f 21 00 	mov.b	33(r15),r14	;0x0021(r15)
    44b2:	2e 93       	cmp	#2,	r14	;r3 As==10
    44b4:	03 34       	jge	$+8      	;abs 0x44bc
    44b6:	3e 50 03 00 	add	#3,	r14	;#0x0003
    44ba:	02 3c       	jmp	$+6      	;abs 0x44c0
    44bc:	3e 40 05 00 	mov	#5,	r14	;#0x0005
    44c0:	7e f0 0f 00 	and.b	#15,	r14	;#0x000f
    44c4:	1a 43       	mov	#1,	r10	;r3 As==01
    44c6:	03 24       	jz	$+8      	;abs 0x44ce
    44c8:	7e 53       	add.b	#-1,	r14	;r3 As==11
    44ca:	ce 18 0a 5a 	.rpt	r14
				addx	r10,	r10	
    44ce:	3a 53       	add	#-1,	r10	;r3 As==11
    44d0:	0b 4a       	mov	r10,	r11	
    44d2:	8b 10       	swpb	r11		
    44d4:	8b 11       	sxt	r11		
    44d6:	8b 10       	swpb	r11		
    44d8:	8b 11       	sxt	r11		
    44da:	0e 4b       	mov	r11,	r14	
    44dc:	0a 93       	tst	r10		
    44de:	02 20       	jnz	$+6      	;abs 0x44e4
    44e0:	0b 93       	tst	r11		
    44e2:	0a 24       	jz	$+22     	;abs 0x44f8
    44e4:	b0 13 84 68 	calla	#0x06884	
    44e8:	0c 4a       	mov	r10,	r12	
    44ea:	0d 4b       	mov	r11,	r13	
    44ec:	0e 4f       	mov	r15,	r14	
    44ee:	0f 43       	clr	r15		
    44f0:	b0 13 84 33 	calla	#0x03384	
    44f4:	0a 4e       	mov	r14,	r10	
    44f6:	0e 4f       	mov	r15,	r14	
    44f8:	09 12       	push	r9		
    44fa:	8c 00 96 45 	mova	#0x04596,r12	
    44fe:	0d 4a       	mov	r10,	r13	
    4500:	0f 49       	mov	r9,	r15	
    4502:	3f 50 0a 00 	add	#10,	r15	;#0x000a
    4506:	b0 13 8a 4a 	calla	#0x04a8a	
    450a:	21 53       	incd	r1		
    450c:	29 16       	popm.a	#3,	r11	
    450e:	10 01       	reta			

00004510 <tx_done>:
    4510:	5b 14       	pushm.a	#6,	r11	
    4512:	07 4f       	mov	r15,	r7	
    4514:	0a 4e       	mov	r14,	r10	
    4516:	0b 4d       	mov	r13,	r11	
    4518:	1c 4e 04 00 	mov	4(r14),	r12	;0x0004(r14)
    451c:	09 0c       	mova	@r12,	r9	
    451e:	18 4c 04 00 	mov	4(r12),	r8	;0x0004(r12)
    4522:	56 4d 20 00 	mov.b	32(r13),r6	;0x0020(r13)
    4526:	1f 4d 24 00 	mov	36(r13),r15	;0x0024(r13)
    452a:	b0 13 b4 55 	calla	#0x055b4	
    452e:	1f 4a 02 00 	mov	2(r10),	r15	;0x0002(r10)
    4532:	b0 13 22 68 	calla	#0x06822	
    4536:	1e 4a 04 00 	mov	4(r10),	r14	;0x0004(r10)
    453a:	3f 40 28 11 	mov	#4392,	r15	;#0x1128
    453e:	b0 13 08 58 	calla	#0x05808	
    4542:	0e 4a       	mov	r10,	r14	
    4544:	3f 40 20 11 	mov	#4384,	r15	;#0x1120
    4548:	b0 13 08 58 	calla	#0x05808	
    454c:	1f 4b 24 00 	mov	36(r11),r15	;0x0024(r11)
    4550:	b0 13 9e 55 	calla	#0x0559e	
    4554:	0f 93       	tst	r15		
    4556:	08 24       	jz	$+18     	;abs 0x4568
    4558:	cb 43 20 00 	mov.b	#0,	32(r11)	;r3 As==00, 0x0020(r11)
    455c:	cb 43 21 00 	mov.b	#0,	33(r11)	;r3 As==00, 0x0021(r11)
    4560:	0f 4b       	mov	r11,	r15	
    4562:	b0 13 aa 44 	calla	#0x044aa	
    4566:	0f 3c       	jmp	$+32     	;abs 0x4586
    4568:	0f 4b       	mov	r11,	r15	
    456a:	3f 50 0a 00 	add	#10,	r15	;#0x000a
    456e:	b0 13 9a 4a 	calla	#0x04a9a	
    4572:	0e 4b       	mov	r11,	r14	
    4574:	3f 40 e6 1a 	mov	#6886,	r15	;#0x1ae6
    4578:	b0 13 b4 55 	calla	#0x055b4	
    457c:	0e 4b       	mov	r11,	r14	
    457e:	3f 40 18 11 	mov	#4376,	r15	;#0x1118
    4582:	b0 13 08 58 	calla	#0x05808	
    4586:	4c 46       	mov.b	r6,	r12	
    4588:	0d 47       	mov	r7,	r13	
    458a:	0e 48       	mov	r8,	r14	
    458c:	cf 09       	mova	r9,	r15	
    458e:	b0 13 80 57 	calla	#0x05780	
    4592:	56 16       	popm.a	#6,	r11	
    4594:	10 01       	reta			

00004596 <transmit_from_queue>:
    4596:	5b 14       	pushm.a	#6,	r11	
    4598:	21 82       	sub	#4,	r1	;r2 As==10
    459a:	0b 4f       	mov	r15,	r11	
    459c:	0f 93       	tst	r15		
    459e:	d0 24       	jz	$+418    	;abs 0x4740
    45a0:	1f 4f 24 00 	mov	36(r15),r15	;0x0024(r15)
    45a4:	b0 13 9e 55 	calla	#0x0559e	
    45a8:	0a 4f       	mov	r15,	r10	
    45aa:	0f 93       	tst	r15		
    45ac:	c9 24       	jz	$+404    	;abs 0x4740
    45ae:	1f 4f 02 00 	mov	2(r15),	r15	;0x0002(r15)
    45b2:	b0 13 4c 68 	calla	#0x0684c	
    45b6:	3e 40 2a 24 	mov	#9258,	r14	;#0x242a
    45ba:	7f 40 0c 00 	mov.b	#12,	r15	;#0x000c
    45be:	b0 13 6c 63 	calla	#0x0636c	
    45c2:	1e 43       	mov	#1,	r14	;r3 As==01
    45c4:	7f 40 07 00 	mov.b	#7,	r15	;#0x0007
    45c8:	b0 13 56 63 	calla	#0x06356	
    45cc:	b0 13 a8 48 	calla	#0x048a8	
    45d0:	0f 93       	tst	r15		
    45d2:	b1 38       	jl	$+356    	;abs 0x4736
    45d4:	b0 13 08 62 	calla	#0x06208	
    45d8:	56 4f 02 00 	mov.b	2(r15),	r6	;0x0002(r15)
    45dc:	b0 13 64 62 	calla	#0x06264	
    45e0:	09 4f       	mov	r15,	r9	
    45e2:	b0 13 08 62 	calla	#0x06208	
    45e6:	0e 49       	mov	r9,	r14	
    45e8:	80 13 14 99 	calla	&0x09914	
    45ec:	b0 13 8e 63 	calla	#0x0638e	
    45f0:	49 4f       	mov.b	r15,	r9	
    45f2:	27 00 28 99 	mova	&0x09928,r7	
    45f6:	47 13       	calla	r7		
    45f8:	0f 93       	tst	r15		
    45fa:	01 24       	jz	$+4      	;abs 0x45fe
    45fc:	50 3c       	jmp	$+162    	;abs 0x469e
    45fe:	49 49       	mov.b	r9,	r9	
    4600:	09 93       	tst	r9		
    4602:	09 24       	jz	$+20     	;abs 0x4616
    4604:	b0 13 64 62 	calla	#0x06264	
    4608:	80 13 18 99 	calla	&0x09918	
    460c:	0f 93       	tst	r15		
    460e:	08 24       	jz	$+18     	;abs 0x4620
    4610:	2f 93       	cmp	#2,	r15	;r3 As==10
    4612:	94 20       	jnz	$+298    	;abs 0x473c
    4614:	44 3c       	jmp	$+138    	;abs 0x469e
    4616:	80 13 2c 99 	calla	&0x0992c	
    461a:	0f 93       	tst	r15		
    461c:	40 20       	jnz	$+130    	;abs 0x469e
    461e:	f2 3f       	jmp	$-26     	;abs 0x4604
    4620:	09 93       	tst	r9		
    4622:	3f 20       	jnz	$+128    	;abs 0x46a2
    4624:	b0 13 98 68 	calla	#0x06898	
    4628:	29 00 2c 99 	mova	&0x0992c,r9	
    462c:	38 40 f3 ff 	mov	#-13,	r8	;#0xfff3
    4630:	08 8f       	sub	r15,	r8	
    4632:	49 13       	calla	r9		
    4634:	0f 93       	tst	r15		
    4636:	04 24       	jz	$+10     	;abs 0x4640
    4638:	47 13       	calla	r7		
    463a:	0f 93       	tst	r15		
    463c:	07 20       	jnz	$+16     	;abs 0x464c
    463e:	0c 3c       	jmp	$+26     	;abs 0x4658
    4640:	b0 13 98 68 	calla	#0x06898	
    4644:	0f 58       	add	r8,	r15	
    4646:	0f 93       	tst	r15		
    4648:	f4 3b       	jl	$-22     	;abs 0x4632
    464a:	f6 3f       	jmp	$-18     	;abs 0x4638
    464c:	b0 13 98 68 	calla	#0x06898	
    4650:	38 40 eb ff 	mov	#-21,	r8	;#0xffeb
    4654:	08 8f       	sub	r15,	r8	
    4656:	08 3c       	jmp	$+18     	;abs 0x4668
    4658:	49 13       	calla	r9		
    465a:	0f 93       	tst	r15		
    465c:	f7 23       	jnz	$-16     	;abs 0x464c
    465e:	80 13 24 99 	calla	&0x09924	
    4662:	0f 93       	tst	r15		
    4664:	f3 27       	jz	$-24     	;abs 0x464c
    4666:	06 3c       	jmp	$+14     	;abs 0x4674
    4668:	49 13       	calla	r9		
    466a:	0f 93       	tst	r15		
    466c:	05 24       	jz	$+12     	;abs 0x4678
    466e:	49 13       	calla	r9		
    4670:	0f 93       	tst	r15		
    4672:	08 20       	jnz	$+18     	;abs 0x4684
    4674:	2f 43       	mov	#2,	r15	;r3 As==10
    4676:	16 3c       	jmp	$+46     	;abs 0x46a4
    4678:	b0 13 98 68 	calla	#0x06898	
    467c:	0f 58       	add	r8,	r15	
    467e:	0f 93       	tst	r15		
    4680:	f3 3b       	jl	$-24     	;abs 0x4668
    4682:	f5 3f       	jmp	$-20     	;abs 0x466e
    4684:	3e 40 03 00 	mov	#3,	r14	;#0x0003
    4688:	0f 41       	mov	r1,	r15	
    468a:	80 13 20 99 	calla	&0x09920	
    468e:	3f 90 03 00 	cmp	#3,	r15	;#0x0003
    4692:	05 20       	jnz	$+12     	;abs 0x469e
    4694:	1f 43       	mov	#1,	r15	;r3 As==01
    4696:	c1 96 02 00 	cmp.b	r6,	2(r1)	;0x0002(r1)
    469a:	04 20       	jnz	$+10     	;abs 0x46a4
    469c:	02 3c       	jmp	$+6      	;abs 0x46a2
    469e:	1f 43       	mov	#1,	r15	;r3 As==01
    46a0:	01 3c       	jmp	$+4      	;abs 0x46a4
    46a2:	0f 43       	clr	r15		
    46a4:	1e 4a 04 00 	mov	4(r10),	r14	;0x0004(r10)
    46a8:	0e 93       	tst	r14		
    46aa:	4a 24       	jz	$+150    	;abs 0x4740
    46ac:	1f 93       	cmp	#1,	r15	;r3 As==01
    46ae:	21 24       	jz	$+68     	;abs 0x46f2
    46b0:	2f 93       	cmp	#2,	r15	;r3 As==10
    46b2:	03 34       	jge	$+8      	;abs 0x46ba
    46b4:	0f 93       	tst	r15		
    46b6:	07 24       	jz	$+16     	;abs 0x46c6
    46b8:	39 3c       	jmp	$+116    	;abs 0x472c
    46ba:	2f 93       	cmp	#2,	r15	;r3 As==10
    46bc:	0c 24       	jz	$+26     	;abs 0x46d6
    46be:	3f 90 03 00 	cmp	#3,	r15	;#0x0003
    46c2:	34 20       	jnz	$+106    	;abs 0x472c
    46c4:	3d 3c       	jmp	$+124    	;abs 0x4740
    46c6:	cb 43 21 00 	mov.b	#0,	33(r11)	;r3 As==00, 0x0021(r11)
    46ca:	db 53 20 00 	inc.b	32(r11)	;0x0020(r11)
    46ce:	0d 4b       	mov	r11,	r13	
    46d0:	0e 4a       	mov	r10,	r14	
    46d2:	0f 43       	clr	r15		
    46d4:	2d 3c       	jmp	$+92     	;abs 0x4730
    46d6:	cb 43 21 00 	mov.b	#0,	33(r11)	;r3 As==00, 0x0021(r11)
    46da:	5f 4b 20 00 	mov.b	32(r11),r15	;0x0020(r11)
    46de:	5f 53       	inc.b	r15		
    46e0:	cb 4f 20 00 	mov.b	r15,	32(r11)	;0x0020(r11)
    46e4:	5f 9e 06 00 	cmp.b	6(r14),	r15	;0x0006(r14)
    46e8:	19 28       	jnc	$+52     	;abs 0x471c
    46ea:	0d 4b       	mov	r11,	r13	
    46ec:	0e 4a       	mov	r10,	r14	
    46ee:	2f 43       	mov	#2,	r15	;r3 As==10
    46f0:	1f 3c       	jmp	$+64     	;abs 0x4730
    46f2:	5f 4b 21 00 	mov.b	33(r11),r15	;0x0021(r11)
    46f6:	5f 53       	inc.b	r15		
    46f8:	7f 90 06 00 	cmp.b	#6,	r15	;#0x0006
    46fc:	03 2c       	jc	$+8      	;abs 0x4704
    46fe:	cb 4f 21 00 	mov.b	r15,	33(r11)	;0x0021(r11)
    4702:	04 3c       	jmp	$+10     	;abs 0x470c
    4704:	cb 43 21 00 	mov.b	#0,	33(r11)	;r3 As==00, 0x0021(r11)
    4708:	db 53 20 00 	inc.b	32(r11)	;0x0020(r11)
    470c:	db 9e 06 00 	cmp.b	6(r14),	32(r11)	;0x0006(r14), 0x0020(r11)
    4710:	20 00 
    4712:	04 28       	jnc	$+10     	;abs 0x471c
    4714:	0d 4b       	mov	r11,	r13	
    4716:	0e 4a       	mov	r10,	r14	
    4718:	1f 43       	mov	#1,	r15	;r3 As==01
    471a:	0a 3c       	jmp	$+22     	;abs 0x4730
    471c:	0f 4b       	mov	r11,	r15	
    471e:	b0 13 aa 44 	calla	#0x044aa	
    4722:	1f 4a 02 00 	mov	2(r10),	r15	;0x0002(r10)
    4726:	b0 13 10 68 	calla	#0x06810	
    472a:	0a 3c       	jmp	$+22     	;abs 0x4740
    472c:	0d 4b       	mov	r11,	r13	
    472e:	0e 4a       	mov	r10,	r14	
    4730:	b0 13 10 45 	calla	#0x04510	
    4734:	05 3c       	jmp	$+12     	;abs 0x4740
    4736:	3f 40 05 00 	mov	#5,	r15	;#0x0005
    473a:	b4 3f       	jmp	$-150    	;abs 0x46a4
    473c:	2f 42       	mov	#4,	r15	;r2 As==10
    473e:	b2 3f       	jmp	$-154    	;abs 0x46a4
    4740:	21 52       	add	#4,	r1	;r2 As==10
    4742:	56 16       	popm.a	#6,	r11	
    4744:	10 01       	reta			

00004746 <csma_output_packet>:
    4746:	4b 14       	pushm.a	#5,	r11	
    4748:	c8 0f       	mova	r15,	r8	
    474a:	07 4e       	mov	r14,	r7	
    474c:	7f 40 0d 00 	mov.b	#13,	r15	;#0x000d
    4750:	b0 13 80 63 	calla	#0x06380	
    4754:	0a 4f       	mov	r15,	r10	
    4756:	b0 13 74 56 	calla	#0x05674	
    475a:	1e 43       	mov	#1,	r14	;r3 As==01
    475c:	7f 40 0b 00 	mov.b	#11,	r15	;#0x000b
    4760:	b0 13 56 63 	calla	#0x06356	
    4764:	3f 40 e6 1a 	mov	#6886,	r15	;#0x1ae6
    4768:	b0 13 9e 55 	calla	#0x0559e	
    476c:	0a 3c       	jmp	$+22     	;abs 0x4782
    476e:	0e 4a       	mov	r10,	r14	
    4770:	0f 4b       	mov	r11,	r15	
    4772:	2f 53       	incd	r15		
    4774:	b0 13 7a 55 	calla	#0x0557a	
    4778:	4f 93       	tst.b	r15		
    477a:	76 20       	jnz	$+238    	;abs 0x4868
    477c:	0f 4b       	mov	r11,	r15	
    477e:	b0 13 1e 56 	calla	#0x0561e	
    4782:	0b 4f       	mov	r15,	r11	
    4784:	0f 93       	tst	r15		
    4786:	f3 23       	jnz	$-24     	;abs 0x476e
    4788:	78 3c       	jmp	$+242    	;abs 0x487a
    478a:	0e 4a       	mov	r10,	r14	
    478c:	0f 4b       	mov	r11,	r15	
    478e:	2f 53       	incd	r15		
    4790:	b0 13 72 55 	calla	#0x05572	
    4794:	cb 43 20 00 	mov.b	#0,	32(r11)	;r3 As==00, 0x0020(r11)
    4798:	cb 43 21 00 	mov.b	#0,	33(r11)	;r3 As==00, 0x0021(r11)
    479c:	0f 4b       	mov	r11,	r15	
    479e:	3f 50 22 00 	add	#34,	r15	;#0x0022
    47a2:	8b 4f 24 00 	mov	r15,	36(r11)	;0x0024(r11)
    47a6:	8b 43 22 00 	mov	#0,	34(r11)	;r3 As==00, 0x0022(r11)
    47aa:	b0 13 98 55 	calla	#0x05598	
    47ae:	0e 4b       	mov	r11,	r14	
    47b0:	3f 40 e6 1a 	mov	#6886,	r15	;#0x1ae6
    47b4:	b0 13 e8 55 	calla	#0x055e8	
    47b8:	57 3c       	jmp	$+176    	;abs 0x4868
    47ba:	3f 40 20 11 	mov	#4384,	r15	;#0x1120
    47be:	b0 13 ca 57 	calla	#0x057ca	
    47c2:	0a 4f       	mov	r15,	r10	
    47c4:	0f 93       	tst	r15		
    47c6:	38 24       	jz	$+114    	;abs 0x4838
    47c8:	3f 40 28 11 	mov	#4392,	r15	;#0x1128
    47cc:	b0 13 ca 57 	calla	#0x057ca	
    47d0:	8a 4f 04 00 	mov	r15,	4(r10)	;0x0004(r10)
    47d4:	0f 93       	tst	r15		
    47d6:	2b 24       	jz	$+88     	;abs 0x482e
    47d8:	b0 13 c2 67 	calla	#0x067c2	
    47dc:	8a 4f 02 00 	mov	r15,	2(r10)	;0x0002(r10)
    47e0:	19 4a 04 00 	mov	4(r10),	r9	;0x0004(r10)
    47e4:	0f 93       	tst	r15		
    47e6:	1e 24       	jz	$+62     	;abs 0x4824
    47e8:	7f 40 05 00 	mov.b	#5,	r15	;#0x0005
    47ec:	b0 13 62 63 	calla	#0x06362	
    47f0:	4f 93       	tst.b	r15		
    47f2:	03 24       	jz	$+8      	;abs 0x47fa
    47f4:	c9 4f 06 00 	mov.b	r15,	6(r9)	;0x0006(r9)
    47f8:	02 3c       	jmp	$+6      	;abs 0x47fe
    47fa:	f9 42 06 00 	mov.b	#8,	6(r9)	;r2 As==11, 0x0006(r9)
    47fe:	79 08 00 00 	mova	r8,	0(r9)	;0x0000(r9)
    4802:	89 47 04 00 	mov	r7,	4(r9)	;0x0004(r9)
    4806:	0e 4a       	mov	r10,	r14	
    4808:	1f 4b 24 00 	mov	36(r11),r15	;0x0024(r11)
    480c:	b0 13 e8 55 	calla	#0x055e8	
    4810:	1f 4b 24 00 	mov	36(r11),r15	;0x0024(r11)
    4814:	b0 13 9e 55 	calla	#0x0559e	
    4818:	0a 9f       	cmp	r15,	r10	
    481a:	37 20       	jnz	$+112    	;abs 0x488a
    481c:	0f 4b       	mov	r11,	r15	
    481e:	b0 13 aa 44 	calla	#0x044aa	
    4822:	33 3c       	jmp	$+104    	;abs 0x488a
    4824:	0e 49       	mov	r9,	r14	
    4826:	3f 40 28 11 	mov	#4392,	r15	;#0x1128
    482a:	b0 13 08 58 	calla	#0x05808	
    482e:	0e 4a       	mov	r10,	r14	
    4830:	3f 40 20 11 	mov	#4384,	r15	;#0x1120
    4834:	b0 13 08 58 	calla	#0x05808	
    4838:	1f 4b 24 00 	mov	36(r11),r15	;0x0024(r11)
    483c:	b0 13 0e 56 	calla	#0x0560e	
    4840:	0f 93       	tst	r15		
    4842:	0a 20       	jnz	$+22     	;abs 0x4858
    4844:	0e 4b       	mov	r11,	r14	
    4846:	3f 40 e6 1a 	mov	#6886,	r15	;#0x1ae6
    484a:	b0 13 b4 55 	calla	#0x055b4	
    484e:	0e 4b       	mov	r11,	r14	
    4850:	3f 40 18 11 	mov	#4376,	r15	;#0x1118
    4854:	b0 13 08 58 	calla	#0x05808	
    4858:	1c 43       	mov	#1,	r12	;r3 As==01
    485a:	3d 40 06 00 	mov	#6,	r13	;#0x0006
    485e:	0e 47       	mov	r7,	r14	
    4860:	cf 08       	mova	r8,	r15	
    4862:	b0 13 80 57 	calla	#0x05780	
    4866:	11 3c       	jmp	$+36     	;abs 0x488a
    4868:	1f 4b 24 00 	mov	36(r11),r15	;0x0024(r11)
    486c:	b0 13 0e 56 	calla	#0x0560e	
    4870:	3f 90 07 00 	cmp	#7,	r15	;#0x0007
    4874:	01 24       	jz	$+4      	;abs 0x4878
    4876:	f0 37       	jge	$-30     	;abs 0x4858
    4878:	a0 3f       	jmp	$-190    	;abs 0x47ba
    487a:	3f 40 18 11 	mov	#4376,	r15	;#0x1118
    487e:	b0 13 ca 57 	calla	#0x057ca	
    4882:	0b 4f       	mov	r15,	r11	
    4884:	0f 93       	tst	r15		
    4886:	81 23       	jnz	$-252    	;abs 0x478a
    4888:	e7 3f       	jmp	$-48     	;abs 0x4858
    488a:	47 16       	popm.a	#5,	r11	
    488c:	10 01       	reta			

0000488e <csma_output_init>:
    488e:	3f 40 20 11 	mov	#4384,	r15	;#0x1120
    4892:	b0 13 94 57 	calla	#0x05794	
    4896:	3f 40 28 11 	mov	#4392,	r15	;#0x1128
    489a:	b0 13 94 57 	calla	#0x05794	
    489e:	3f 40 18 11 	mov	#4376,	r15	;#0x1118
    48a2:	b0 13 94 57 	calla	#0x05794	
    48a6:	10 01       	reta			

000048a8 <csma_security_create_frame>:
    48a8:	1e 43       	mov	#1,	r14	;r3 As==01
    48aa:	7f 40 0b 00 	mov.b	#11,	r15	;#0x000b
    48ae:	b0 13 56 63 	calla	#0x06356	
    48b2:	80 13 76 99 	calla	&0x09976	
    48b6:	10 01       	reta			

000048b8 <csma_security_parse_frame>:
    48b8:	80 13 7a 99 	calla	&0x0997a	
    48bc:	10 01       	reta			

000048be <on>:
    48be:	80 13 30 99 	calla	&0x09930	
    48c2:	10 01       	reta			

000048c4 <off>:
    48c4:	80 13 34 99 	calla	&0x09934	
    48c8:	10 01       	reta			

000048ca <max_payload>:
    48ca:	0b 14       	pushm.a	#1,	r11	
    48cc:	21 83       	decd	r1		
    48ce:	80 13 72 99 	calla	&0x09972	
    48d2:	0b 4f       	mov	r15,	r11	
    48d4:	0e 41       	mov	r1,	r14	
    48d6:	3f 40 18 00 	mov	#24,	r15	;#0x0018
    48da:	80 13 38 99 	calla	&0x09938	
    48de:	1f 93       	cmp	#1,	r15	;r3 As==01
    48e0:	0c 24       	jz	$+26     	;abs 0x48fa
    48e2:	0b 93       	tst	r11		
    48e4:	02 34       	jge	$+6      	;abs 0x48ea
    48e6:	3b 40 15 00 	mov	#21,	r11	;#0x0015
    48ea:	2f 41       	mov	@r1,	r15	
    48ec:	3f 90 81 00 	cmp	#129,	r15	;#0x0081
    48f0:	02 38       	jl	$+6      	;abs 0x48f6
    48f2:	3f 40 80 00 	mov	#128,	r15	;#0x0080
    48f6:	0f 8b       	sub	r11,	r15	
    48f8:	01 3c       	jmp	$+4      	;abs 0x48fc
    48fa:	0f 43       	clr	r15		
    48fc:	21 53       	incd	r1		
    48fe:	0b 16       	popm.a	#1,	r11	
    4900:	10 01       	reta			

00004902 <send_packet>:
    4902:	b0 13 46 47 	calla	#0x04746	
    4906:	10 01       	reta			

00004908 <input_packet>:
    4908:	b0 13 0e 62 	calla	#0x0620e	
    490c:	3f 90 03 00 	cmp	#3,	r15	;#0x0003
    4910:	2a 24       	jz	$+86     	;abs 0x4966
    4912:	b0 13 b8 48 	calla	#0x048b8	
    4916:	0f 93       	tst	r15		
    4918:	26 38       	jl	$+78     	;abs 0x4966
    491a:	7f 40 0d 00 	mov.b	#13,	r15	;#0x000d
    491e:	b0 13 80 63 	calla	#0x06380	
    4922:	3e 40 2a 24 	mov	#9258,	r14	;#0x242a
    4926:	b0 13 7a 55 	calla	#0x0557a	
    492a:	4f 93       	tst.b	r15		
    492c:	0a 20       	jnz	$+22     	;abs 0x4942
    492e:	b0 13 8e 63 	calla	#0x0638e	
    4932:	4f 93       	tst.b	r15		
    4934:	06 20       	jnz	$+14     	;abs 0x4942
    4936:	30 12 22 9b 	push	#-25822	;#0x9b22
    493a:	b0 13 68 8d 	calla	#0x08d68	
    493e:	21 53       	incd	r1		
    4940:	10 01       	reta			
    4942:	7f 40 0c 00 	mov.b	#12,	r15	;#0x000c
    4946:	b0 13 80 63 	calla	#0x06380	
    494a:	3e 40 2a 24 	mov	#9258,	r14	;#0x242a
    494e:	b0 13 7a 55 	calla	#0x0557a	
    4952:	4f 93       	tst.b	r15		
    4954:	08 20       	jnz	$+18     	;abs 0x4966
    4956:	b0 13 8c 56 	calla	#0x0568c	
    495a:	0f 93       	tst	r15		
    495c:	04 20       	jnz	$+10     	;abs 0x4966
    495e:	b0 13 fa 56 	calla	#0x056fa	
    4962:	80 13 90 99 	calla	&0x09990	
    4966:	10 01       	reta			

00004968 <init>:
    4968:	21 83       	decd	r1		
    496a:	0e 41       	mov	r1,	r14	
    496c:	3f 40 18 00 	mov	#24,	r15	;#0x0018
    4970:	80 13 38 99 	calla	&0x09938	
    4974:	0f 93       	tst	r15		
    4976:	06 20       	jnz	$+14     	;abs 0x4984
    4978:	b0 13 6a 56 	calla	#0x0566a	
    497c:	b0 13 8e 48 	calla	#0x0488e	
    4980:	b0 13 be 48 	calla	#0x048be	
    4984:	21 53       	incd	r1		
    4986:	10 01       	reta			

00004988 <process_thread_ctimer_process>:
    4988:	2b 14       	pushm.a	#3,	r11	
    498a:	0a 4f       	mov	r15,	r10	
    498c:	09 4d       	mov	r13,	r9	
    498e:	2f 4f       	mov	@r15,	r15	
    4990:	0f 93       	tst	r15		
    4992:	04 24       	jz	$+10     	;abs 0x499c
    4994:	3f 90 4a 00 	cmp	#74,	r15	;#0x004a
    4998:	3a 20       	jnz	$+118    	;abs 0x4a0e
    499a:	40 3c       	jmp	$+130    	;abs 0x4a1c
    499c:	3f 40 a4 1b 	mov	#7076,	r15	;#0x1ba4
    49a0:	b0 13 9e 55 	calla	#0x0559e	
    49a4:	0b 4f       	mov	r15,	r11	
    49a6:	09 3c       	jmp	$+20     	;abs 0x49ba
    49a8:	1d 4b 06 00 	mov	6(r11),	r13	;0x0006(r11)
    49ac:	1e 4b 08 00 	mov	8(r11),	r14	;0x0008(r11)
    49b0:	0f 4b       	mov	r11,	r15	
    49b2:	2f 53       	incd	r15		
    49b4:	b0 13 44 4c 	calla	#0x04c44	
    49b8:	2b 4b       	mov	@r11,	r11	
    49ba:	0b 93       	tst	r11		
    49bc:	f5 23       	jnz	$-20     	;abs 0x49a8
    49be:	d2 43 eb 23 	mov.b	#1,	&0x23eb	;r3 As==01
    49c2:	ba 40 4a 00 	mov	#74,	0(r10)	;#0x004a, 0x0000(r10)
    49c6:	00 00 
    49c8:	27 3c       	jmp	$+80     	;abs 0x4a18
    49ca:	3f 40 a4 1b 	mov	#7076,	r15	;#0x1ba4
    49ce:	b0 13 9e 55 	calla	#0x0559e	
    49d2:	0b 4f       	mov	r15,	r11	
    49d4:	19 3c       	jmp	$+52     	;abs 0x4a08
    49d6:	0f 4b       	mov	r11,	r15	
    49d8:	2f 53       	incd	r15		
    49da:	09 9f       	cmp	r15,	r9	
    49dc:	14 20       	jnz	$+42     	;abs 0x4a06
    49de:	0e 4b       	mov	r11,	r14	
    49e0:	3f 40 a4 1b 	mov	#7076,	r15	;#0x1ba4
    49e4:	b0 13 b4 55 	calla	#0x055b4	
    49e8:	19 42 20 1e 	mov	&0x1e20,r9	
    49ec:	92 4b 0e 00 	mov	14(r11),&0x1e20	;0x000e(r11)
    49f0:	20 1e 
    49f2:	3e 0b 10 00 	mova	16(r11),r14	;0x0010(r11)
    49f6:	de 03       	tsta	r14		
    49f8:	03 24       	jz	$+8      	;abs 0x4a00
    49fa:	1f 4b 14 00 	mov	20(r11),r15	;0x0014(r11)
    49fe:	4e 13       	calla	r14		
    4a00:	82 49 20 1e 	mov	r9,	&0x1e20	
    4a04:	de 3f       	jmp	$-66     	;abs 0x49c2
    4a06:	2b 4b       	mov	@r11,	r11	
    4a08:	0b 93       	tst	r11		
    4a0a:	e5 23       	jnz	$-52     	;abs 0x49d6
    4a0c:	da 3f       	jmp	$-74     	;abs 0x49c2
    4a0e:	8a 43 00 00 	mov	#0,	0(r10)	;r3 As==00, 0x0000(r10)
    4a12:	7f 40 03 00 	mov.b	#3,	r15	;#0x0003
    4a16:	06 3c       	jmp	$+14     	;abs 0x4a24
    4a18:	5f 43       	mov.b	#1,	r15	;r3 As==01
    4a1a:	04 3c       	jmp	$+10     	;abs 0x4a24
    4a1c:	7e 90 88 ff 	cmp.b	#-120,	r14	;#0xff88
    4a20:	fb 23       	jnz	$-8      	;abs 0x4a18
    4a22:	d3 3f       	jmp	$-88     	;abs 0x49ca
    4a24:	29 16       	popm.a	#3,	r11	
    4a26:	10 01       	reta			

00004a28 <ctimer_init>:
    4a28:	c2 43 eb 23 	mov.b	#0,	&0x23eb	;r3 As==00
    4a2c:	3f 40 a4 1b 	mov	#7076,	r15	;#0x1ba4
    4a30:	b0 13 98 55 	calla	#0x05598	
    4a34:	0e 43       	clr	r14		
    4a36:	3f 40 30 11 	mov	#4400,	r15	;#0x1130
    4a3a:	b0 13 62 67 	calla	#0x06762	
    4a3e:	10 01       	reta			

00004a40 <ctimer_set_with_process>:
    4a40:	2b 14       	pushm.a	#3,	r11	
    4a42:	09 4f       	mov	r15,	r9	
    4a44:	0a 4d       	mov	r13,	r10	
    4a46:	0b 4e       	mov	r14,	r11	
    4a48:	9f 41 12 00 	mov	18(r1),	14(r15)	;0x0012(r1), 0x000e(r15)
    4a4c:	0e 00 
    4a4e:	7f 0c 10 00 	mova	r12,	16(r15)	;0x0010(r15)
    4a52:	9f 41 10 00 	mov	16(r1),	20(r15)	;0x0010(r1), 0x0014(r15)
    4a56:	14 00 
    4a58:	c2 93 eb 23 	tst.b	&0x23eb	
    4a5c:	0b 24       	jz	$+24     	;abs 0x4a74
    4a5e:	1b 42 20 1e 	mov	&0x1e20,r11	
    4a62:	b2 40 30 11 	mov	#4400,	&0x1e20	;#0x1130
    4a66:	20 1e 
    4a68:	2f 53       	incd	r15		
    4a6a:	b0 13 44 4c 	calla	#0x04c44	
    4a6e:	82 4b 20 1e 	mov	r11,	&0x1e20	
    4a72:	04 3c       	jmp	$+10     	;abs 0x4a7c
    4a74:	89 4d 06 00 	mov	r13,	6(r9)	;0x0006(r9)
    4a78:	89 4e 08 00 	mov	r14,	8(r9)	;0x0008(r9)
    4a7c:	0e 49       	mov	r9,	r14	
    4a7e:	3f 40 a4 1b 	mov	#7076,	r15	;#0x1ba4
    4a82:	b0 13 e8 55 	calla	#0x055e8	
    4a86:	29 16       	popm.a	#3,	r11	
    4a88:	10 01       	reta			

00004a8a <ctimer_set>:
    4a8a:	12 12 20 1e 	push	&0x1e20	
    4a8e:	11 12 08 00 	push	8(r1)		;0x0008(r1)
    4a92:	b0 13 40 4a 	calla	#0x04a40	
    4a96:	21 52       	add	#4,	r1	;r2 As==10
    4a98:	10 01       	reta			

00004a9a <ctimer_stop>:
    4a9a:	0b 14       	pushm.a	#1,	r11	
    4a9c:	0b 4f       	mov	r15,	r11	
    4a9e:	c2 93 eb 23 	tst.b	&0x23eb	
    4aa2:	04 24       	jz	$+10     	;abs 0x4aac
    4aa4:	2f 53       	incd	r15		
    4aa6:	b0 13 98 4c 	calla	#0x04c98	
    4aaa:	04 3c       	jmp	$+10     	;abs 0x4ab4
    4aac:	8f 43 0a 00 	mov	#0,	10(r15)	;r3 As==00, 0x000a(r15)
    4ab0:	8f 43 0c 00 	mov	#0,	12(r15)	;r3 As==00, 0x000c(r15)
    4ab4:	0e 4b       	mov	r11,	r14	
    4ab6:	3f 40 a4 1b 	mov	#7076,	r15	;#0x1ba4
    4aba:	b0 13 b4 55 	calla	#0x055b4	
    4abe:	0b 16       	popm.a	#1,	r11	
    4ac0:	10 01       	reta			

00004ac2 <energest_init>:
    4ac2:	10 01       	reta			

00004ac4 <energest_flush>:
    4ac4:	10 01       	reta			

00004ac6 <update_time>:
    4ac6:	2b 14       	pushm.a	#3,	r11	
    4ac8:	82 93 a6 1b 	tst	&0x1ba6	
    4acc:	05 20       	jnz	$+12     	;abs 0x4ad8
    4ace:	82 43 a8 1b 	mov	#0,	&0x1ba8	;r3 As==00
    4ad2:	82 43 aa 1b 	mov	#0,	&0x1baa	;r3 As==00
    4ad6:	2d 3c       	jmp	$+92     	;abs 0x4b32
    4ad8:	b0 13 2c 44 	calla	#0x0442c	
    4adc:	1b 42 a6 1b 	mov	&0x1ba6,r11	
    4ae0:	1c 4b 04 00 	mov	4(r11),	r12	;0x0004(r11)
    4ae4:	1d 4b 06 00 	mov	6(r11),	r13	;0x0006(r11)
    4ae8:	2c 5b       	add	@r11,	r12	
    4aea:	1d 6b 02 00 	addc	2(r11),	r13	;0x0002(r11)
    4aee:	0c 8e       	sub	r14,	r12	
    4af0:	0d 7f       	subc	r15,	r13	
    4af2:	19 4b 08 00 	mov	8(r11),	r9	;0x0008(r11)
    4af6:	13 3c       	jmp	$+40     	;abs 0x4b1e
    4af8:	1a 49 04 00 	mov	4(r9),	r10	;0x0004(r9)
    4afc:	1b 49 06 00 	mov	6(r9),	r11	;0x0006(r9)
    4b00:	2a 59       	add	@r9,	r10	
    4b02:	1b 69 02 00 	addc	2(r9),	r11	;0x0002(r9)
    4b06:	0a 8e       	sub	r14,	r10	
    4b08:	0b 7f       	subc	r15,	r11	
    4b0a:	0b 9d       	cmp	r13,	r11	
    4b0c:	04 28       	jnc	$+10     	;abs 0x4b16
    4b0e:	0d 9b       	cmp	r11,	r13	
    4b10:	04 28       	jnc	$+10     	;abs 0x4b1a
    4b12:	0a 9c       	cmp	r12,	r10	
    4b14:	02 2c       	jc	$+6      	;abs 0x4b1a
    4b16:	0c 4a       	mov	r10,	r12	
    4b18:	0d 4b       	mov	r11,	r13	
    4b1a:	19 49 08 00 	mov	8(r9),	r9	;0x0008(r9)
    4b1e:	09 93       	tst	r9		
    4b20:	eb 23       	jnz	$-40     	;abs 0x4af8
    4b22:	0a 4c       	mov	r12,	r10	
    4b24:	0b 4d       	mov	r13,	r11	
    4b26:	0a 5e       	add	r14,	r10	
    4b28:	0b 6f       	addc	r15,	r11	
    4b2a:	82 4a a8 1b 	mov	r10,	&0x1ba8	
    4b2e:	82 4b aa 1b 	mov	r11,	&0x1baa	
    4b32:	29 16       	popm.a	#3,	r11	
    4b34:	10 01       	reta			

00004b36 <etimer_request_poll>:
    4b36:	3f 40 3c 11 	mov	#4412,	r15	;#0x113c
    4b3a:	b0 13 98 67 	calla	#0x06798	
    4b3e:	10 01       	reta			

00004b40 <process_thread_etimer_process>:
    4b40:	2b 14       	pushm.a	#3,	r11	
    4b42:	0a 4f       	mov	r15,	r10	
    4b44:	2f 4f       	mov	@r15,	r15	
    4b46:	0f 93       	tst	r15		
    4b48:	04 24       	jz	$+10     	;abs 0x4b52
    4b4a:	3f 90 59 00 	cmp	#89,	r15	;#0x0059
    4b4e:	4d 20       	jnz	$+156    	;abs 0x4bea
    4b50:	51 3c       	jmp	$+164    	;abs 0x4bf4
    4b52:	82 43 a6 1b 	mov	#0,	&0x1ba6	;r3 As==00
    4b56:	ba 40 59 00 	mov	#89,	0(r10)	;#0x0059, 0x0000(r10)
    4b5a:	00 00 
    4b5c:	5f 43       	mov.b	#1,	r15	;r3 As==01
    4b5e:	50 3c       	jmp	$+162    	;abs 0x4c00
    4b60:	1e 4e 08 00 	mov	8(r14),	r14	;0x0008(r14)
    4b64:	0e 93       	tst	r14		
    4b66:	01 20       	jnz	$+4      	;abs 0x4b6a
    4b68:	f4 3f       	jmp	$-22     	;abs 0x4b52
    4b6a:	8e 9d 0a 00 	cmp	r13,	10(r14)	;0x000a(r14)
    4b6e:	f8 27       	jz	$-14     	;abs 0x4b60
    4b70:	82 4e a6 1b 	mov	r14,	&0x1ba6	
    4b74:	08 3c       	jmp	$+18     	;abs 0x4b86
    4b76:	8c 9d 0a 00 	cmp	r13,	10(r12)	;0x000a(r12)
    4b7a:	04 20       	jnz	$+10     	;abs 0x4b84
    4b7c:	9e 4c 08 00 	mov	8(r12),	8(r14)	;0x0008(r12), 0x0008(r14)
    4b80:	08 00 
    4b82:	01 3c       	jmp	$+4      	;abs 0x4b86
    4b84:	0e 4c       	mov	r12,	r14	
    4b86:	1c 4e 08 00 	mov	8(r14),	r12	;0x0008(r14)
    4b8a:	0c 93       	tst	r12		
    4b8c:	f4 23       	jnz	$-22     	;abs 0x4b76
    4b8e:	e3 3f       	jmp	$-56     	;abs 0x4b56
    4b90:	7e 90 82 ff 	cmp.b	#-126,	r14	;#0xff82
    4b94:	e0 23       	jnz	$-62     	;abs 0x4b56
    4b96:	1b 42 a6 1b 	mov	&0x1ba6,r11	
    4b9a:	09 43       	clr	r9		
    4b9c:	23 3c       	jmp	$+72     	;abs 0x4be4
    4b9e:	0f 4b       	mov	r11,	r15	
    4ba0:	b0 13 66 6b 	calla	#0x06b66	
    4ba4:	0f 93       	tst	r15		
    4ba6:	1b 24       	jz	$+56     	;abs 0x4bde
    4ba8:	0d 4b       	mov	r11,	r13	
    4baa:	7e 40 88 ff 	mov.b	#-120,	r14	;#0xff88
    4bae:	1f 4b 0a 00 	mov	10(r11),r15	;0x000a(r11)
    4bb2:	b0 13 06 67 	calla	#0x06706	
    4bb6:	0f 93       	tst	r15		
    4bb8:	10 20       	jnz	$+34     	;abs 0x4bda
    4bba:	8b 43 0a 00 	mov	#0,	10(r11)	;r3 As==00, 0x000a(r11)
    4bbe:	09 93       	tst	r9		
    4bc0:	04 24       	jz	$+10     	;abs 0x4bca
    4bc2:	99 4b 08 00 	mov	8(r11),	8(r9)	;0x0008(r11), 0x0008(r9)
    4bc6:	08 00 
    4bc8:	03 3c       	jmp	$+8      	;abs 0x4bd0
    4bca:	92 4b 08 00 	mov	8(r11),	&0x1ba6	;0x0008(r11)
    4bce:	a6 1b 
    4bd0:	8b 43 08 00 	mov	#0,	8(r11)	;r3 As==00, 0x0008(r11)
    4bd4:	b0 13 c6 4a 	calla	#0x04ac6	
    4bd8:	de 3f       	jmp	$-66     	;abs 0x4b96
    4bda:	b0 13 36 4b 	calla	#0x04b36	
    4bde:	09 4b       	mov	r11,	r9	
    4be0:	1b 4b 08 00 	mov	8(r11),	r11	;0x0008(r11)
    4be4:	0b 93       	tst	r11		
    4be6:	db 23       	jnz	$-72     	;abs 0x4b9e
    4be8:	b6 3f       	jmp	$-146    	;abs 0x4b56
    4bea:	8a 43 00 00 	mov	#0,	0(r10)	;r3 As==00, 0x0000(r10)
    4bee:	7f 40 03 00 	mov.b	#3,	r15	;#0x0003
    4bf2:	06 3c       	jmp	$+14     	;abs 0x4c00
    4bf4:	7e 90 87 ff 	cmp.b	#-121,	r14	;#0xff87
    4bf8:	cb 23       	jnz	$-104    	;abs 0x4b90
    4bfa:	1e 42 a6 1b 	mov	&0x1ba6,r14	
    4bfe:	b2 3f       	jmp	$-154    	;abs 0x4b64
    4c00:	29 16       	popm.a	#3,	r11	
    4c02:	10 01       	reta			

00004c04 <add_timer>:
    4c04:	0b 14       	pushm.a	#1,	r11	
    4c06:	0b 4f       	mov	r15,	r11	
    4c08:	b0 13 36 4b 	calla	#0x04b36	
    4c0c:	8b 93 0a 00 	tst	10(r11)	;0x000a(r11)
    4c10:	0d 24       	jz	$+28     	;abs 0x4c2c
    4c12:	1f 42 a6 1b 	mov	&0x1ba6,r15	
    4c16:	08 3c       	jmp	$+18     	;abs 0x4c28
    4c18:	0f 9b       	cmp	r11,	r15	
    4c1a:	04 20       	jnz	$+10     	;abs 0x4c24
    4c1c:	9f 42 20 1e 	mov	&0x1e20,10(r15)	;0x000a(r15)
    4c20:	0a 00 
    4c22:	0c 3c       	jmp	$+26     	;abs 0x4c3c
    4c24:	1f 4f 08 00 	mov	8(r15),	r15	;0x0008(r15)
    4c28:	0f 93       	tst	r15		
    4c2a:	f6 23       	jnz	$-18     	;abs 0x4c18
    4c2c:	9b 42 20 1e 	mov	&0x1e20,10(r11)	;0x000a(r11)
    4c30:	0a 00 
    4c32:	9b 42 a6 1b 	mov	&0x1ba6,8(r11)	;0x0008(r11)
    4c36:	08 00 
    4c38:	82 4b a6 1b 	mov	r11,	&0x1ba6	
    4c3c:	b0 13 c6 4a 	calla	#0x04ac6	
    4c40:	0b 16       	popm.a	#1,	r11	
    4c42:	10 01       	reta			

00004c44 <etimer_set>:
    4c44:	0b 14       	pushm.a	#1,	r11	
    4c46:	0b 4f       	mov	r15,	r11	
    4c48:	b0 13 4a 6b 	calla	#0x06b4a	
    4c4c:	0f 4b       	mov	r11,	r15	
    4c4e:	b0 13 04 4c 	calla	#0x04c04	
    4c52:	0b 16       	popm.a	#1,	r11	
    4c54:	10 01       	reta			

00004c56 <etimer_reset>:
    4c56:	0b 14       	pushm.a	#1,	r11	
    4c58:	0b 4f       	mov	r15,	r11	
    4c5a:	b0 13 90 6b 	calla	#0x06b90	
    4c5e:	0f 4b       	mov	r11,	r15	
    4c60:	b0 13 04 4c 	calla	#0x04c04	
    4c64:	0b 16       	popm.a	#1,	r11	
    4c66:	10 01       	reta			

00004c68 <etimer_expired>:
    4c68:	1e 43       	mov	#1,	r14	;r3 As==01
    4c6a:	8f 93 0a 00 	tst	10(r15)	;0x000a(r15)
    4c6e:	01 24       	jz	$+4      	;abs 0x4c72
    4c70:	0e 43       	clr	r14		
    4c72:	0f 4e       	mov	r14,	r15	
    4c74:	10 01       	reta			

00004c76 <etimer_pending>:
    4c76:	1f 43       	mov	#1,	r15	;r3 As==01
    4c78:	82 93 a6 1b 	tst	&0x1ba6	
    4c7c:	01 20       	jnz	$+4      	;abs 0x4c80
    4c7e:	0f 43       	clr	r15		
    4c80:	10 01       	reta			

00004c82 <etimer_next_expiration_time>:
    4c82:	82 93 a6 1b 	tst	&0x1ba6	
    4c86:	05 24       	jz	$+12     	;abs 0x4c92
    4c88:	1e 42 a8 1b 	mov	&0x1ba8,r14	
    4c8c:	1f 42 aa 1b 	mov	&0x1baa,r15	
    4c90:	10 01       	reta			
    4c92:	0e 43       	clr	r14		
    4c94:	0f 43       	clr	r15		
    4c96:	10 01       	reta			

00004c98 <etimer_stop>:
    4c98:	0b 14       	pushm.a	#1,	r11	
    4c9a:	0b 4f       	mov	r15,	r11	
    4c9c:	1f 42 a6 1b 	mov	&0x1ba6,r15	
    4ca0:	0b 9f       	cmp	r15,	r11	
    4ca2:	05 20       	jnz	$+12     	;abs 0x4cae
    4ca4:	92 4b 08 00 	mov	8(r11),	&0x1ba6	;0x0008(r11)
    4ca8:	a6 1b 
    4caa:	10 3c       	jmp	$+34     	;abs 0x4ccc
    4cac:	0f 4e       	mov	r14,	r15	
    4cae:	0f 93       	tst	r15		
    4cb0:	05 24       	jz	$+12     	;abs 0x4cbc
    4cb2:	1e 4f 08 00 	mov	8(r15),	r14	;0x0008(r15)
    4cb6:	0e 9b       	cmp	r11,	r14	
    4cb8:	f9 23       	jnz	$-12     	;abs 0x4cac
    4cba:	05 3c       	jmp	$+12     	;abs 0x4cc6
    4cbc:	8b 43 08 00 	mov	#0,	8(r11)	;r3 As==00, 0x0008(r11)
    4cc0:	8b 43 0a 00 	mov	#0,	10(r11)	;r3 As==00, 0x000a(r11)
    4cc4:	06 3c       	jmp	$+14     	;abs 0x4cd2
    4cc6:	9f 4b 08 00 	mov	8(r11),	8(r15)	;0x0008(r11), 0x0008(r15)
    4cca:	08 00 
    4ccc:	b0 13 c6 4a 	calla	#0x04ac6	
    4cd0:	f5 3f       	jmp	$-20     	;abs 0x4cbc
    4cd2:	0b 16       	popm.a	#1,	r11	
    4cd4:	10 01       	reta			

00004cd6 <frame802154_get_pan_id>:
    4cd6:	1f 42 48 11 	mov	&0x1148,r15	
    4cda:	10 01       	reta			

00004cdc <frame802154_has_panid>:
    4cdc:	0b 14       	pushm.a	#1,	r11	
    4cde:	0f 93       	tst	r15		
    4ce0:	6b 24       	jz	$+216    	;abs 0x4db8
    4ce2:	ef 93 08 00 	cmp.b	#2,	8(r15)	;r3 As==10, 0x0008(r15)
    4ce6:	42 20       	jnz	$+134    	;abs 0x4d6c
    4ce8:	5c 4f 07 00 	mov.b	7(r15),	r12	;0x0007(r15)
    4cec:	4c 93       	tst.b	r12		
    4cee:	07 20       	jnz	$+16     	;abs 0x4cfe
    4cf0:	cf 93 09 00 	tst.b	9(r15)		;0x0009(r15)
    4cf4:	1a 20       	jnz	$+54     	;abs 0x4d2a
    4cf6:	df 93 04 00 	cmp.b	#1,	4(r15)	;r3 As==01, 0x0004(r15)
    4cfa:	17 20       	jnz	$+48     	;abs 0x4d2a
    4cfc:	1a 3c       	jmp	$+54     	;abs 0x4d32
    4cfe:	5b 4f 09 00 	mov.b	9(r15),	r11	;0x0009(r15)
    4d02:	4b 93       	tst.b	r11		
    4d04:	04 20       	jnz	$+10     	;abs 0x4d0e
    4d06:	cf 93 04 00 	tst.b	4(r15)		;0x0004(r15)
    4d0a:	13 24       	jz	$+40     	;abs 0x4d32
    4d0c:	51 3c       	jmp	$+164    	;abs 0x4db0
    4d0e:	7c 90 03 00 	cmp.b	#3,	r12	;#0x0003
    4d12:	07 20       	jnz	$+16     	;abs 0x4d22
    4d14:	7b 90 03 00 	cmp.b	#3,	r11	;#0x0003
    4d18:	0a 20       	jnz	$+22     	;abs 0x4d2e
    4d1a:	cf 93 04 00 	tst.b	4(r15)		;0x0004(r15)
    4d1e:	09 24       	jz	$+20     	;abs 0x4d32
    4d20:	04 3c       	jmp	$+10     	;abs 0x4d2a
    4d22:	6c 93       	cmp.b	#2,	r12	;r3 As==10
    4d24:	04 20       	jnz	$+10     	;abs 0x4d2e
    4d26:	4b 93       	tst.b	r11		
    4d28:	04 20       	jnz	$+10     	;abs 0x4d32
    4d2a:	0b 43       	clr	r11		
    4d2c:	03 3c       	jmp	$+8      	;abs 0x4d34
    4d2e:	6b 93       	cmp.b	#2,	r11	;r3 As==10
    4d30:	fc 23       	jnz	$-6      	;abs 0x4d2a
    4d32:	1b 43       	mov	#1,	r11	;r3 As==01
    4d34:	cf 93 04 00 	tst.b	4(r15)		;0x0004(r15)
    4d38:	2f 20       	jnz	$+96     	;abs 0x4d98
    4d3a:	4c 93       	tst.b	r12		
    4d3c:	06 20       	jnz	$+14     	;abs 0x4d4a
    4d3e:	5f 4f 09 00 	mov.b	9(r15),	r15	;0x0009(r15)
    4d42:	6f 83       	decd.b	r15		
    4d44:	6f 93       	cmp.b	#2,	r15	;r3 As==10
    4d46:	25 28       	jnc	$+76     	;abs 0x4d92
    4d48:	27 3c       	jmp	$+80     	;abs 0x4d98
    4d4a:	6c 93       	cmp.b	#2,	r12	;r3 As==10
    4d4c:	08 20       	jnz	$+18     	;abs 0x4d5e
    4d4e:	5f 4f 09 00 	mov.b	9(r15),	r15	;0x0009(r15)
    4d52:	6f 93       	cmp.b	#2,	r15	;r3 As==10
    4d54:	1e 24       	jz	$+62     	;abs 0x4d92
    4d56:	7f 90 03 00 	cmp.b	#3,	r15	;#0x0003
    4d5a:	1b 24       	jz	$+56     	;abs 0x4d92
    4d5c:	1d 3c       	jmp	$+60     	;abs 0x4d98
    4d5e:	7c 90 03 00 	cmp.b	#3,	r12	;#0x0003
    4d62:	1a 20       	jnz	$+54     	;abs 0x4d98
    4d64:	ef 93 09 00 	cmp.b	#2,	9(r15)	;r3 As==10, 0x0009(r15)
    4d68:	14 24       	jz	$+42     	;abs 0x4d92
    4d6a:	16 3c       	jmp	$+46     	;abs 0x4d98
    4d6c:	ef 93 00 00 	cmp.b	#2,	0(r15)	;r3 As==10, 0x0000(r15)
    4d70:	12 24       	jz	$+38     	;abs 0x4d96
    4d72:	cf 93 04 00 	tst.b	4(r15)		;0x0004(r15)
    4d76:	06 20       	jnz	$+14     	;abs 0x4d84
    4d78:	5b 4f 09 00 	mov.b	9(r15),	r11	;0x0009(r15)
    4d7c:	7b f0 03 00 	and.b	#3,	r11	;#0x0003
    4d80:	1c 43       	mov	#1,	r12	;r3 As==01
    4d82:	01 20       	jnz	$+4      	;abs 0x4d86
    4d84:	0c 43       	clr	r12		
    4d86:	ff b0 03 00 	bit.b	#3,	7(r15)	;#0x0003, 0x0007(r15)
    4d8a:	07 00 
    4d8c:	07 20       	jnz	$+16     	;abs 0x4d9c
    4d8e:	0b 43       	clr	r11		
    4d90:	06 3c       	jmp	$+14     	;abs 0x4d9e
    4d92:	1c 43       	mov	#1,	r12	;r3 As==01
    4d94:	04 3c       	jmp	$+10     	;abs 0x4d9e
    4d96:	0b 43       	clr	r11		
    4d98:	0c 43       	clr	r12		
    4d9a:	01 3c       	jmp	$+4      	;abs 0x4d9e
    4d9c:	1b 43       	mov	#1,	r11	;r3 As==01
    4d9e:	0e 93       	tst	r14		
    4da0:	02 24       	jz	$+6      	;abs 0x4da6
    4da2:	8e 4c 00 00 	mov	r12,	0(r14)	;0x0000(r14)
    4da6:	0d 93       	tst	r13		
    4da8:	07 24       	jz	$+16     	;abs 0x4db8
    4daa:	8d 4b 00 00 	mov	r11,	0(r13)	;0x0000(r13)
    4dae:	04 3c       	jmp	$+10     	;abs 0x4db8
    4db0:	7c 90 03 00 	cmp.b	#3,	r12	;#0x0003
    4db4:	ba 27       	jz	$-138    	;abs 0x4d2a
    4db6:	b5 3f       	jmp	$-148    	;abs 0x4d22
    4db8:	0b 16       	popm.a	#1,	r11	
    4dba:	10 01       	reta			

00004dbc <field_len>:
    4dbc:	1b 14       	pushm.a	#2,	r11	
    4dbe:	21 82       	sub	#4,	r1	;r2 As==10
    4dc0:	0b 4f       	mov	r15,	r11	
    4dc2:	0a 4e       	mov	r14,	r10	
    4dc4:	3d 40 06 00 	mov	#6,	r13	;#0x0006
    4dc8:	0e 43       	clr	r14		
    4dca:	0f 4a       	mov	r10,	r15	
    4dcc:	b0 13 12 98 	calla	#0x09812	
    4dd0:	db b3 15 00 	bit.b	#1,	21(r11)	;r3 As==01, 0x0015(r11)
    4dd4:	02 20       	jnz	$+6      	;abs 0x4dda
    4dd6:	da 43 00 00 	mov.b	#1,	0(r10)	;r3 As==01, 0x0000(r10)
    4dda:	eb 93 18 00 	cmp.b	#2,	24(r11)	;r3 As==10, 0x0018(r11)
    4dde:	11 2c       	jc	$+36     	;abs 0x4e02
    4de0:	fb b0 03 00 	bit.b	#3,	23(r11)	;#0x0003, 0x0017(r11)
    4de4:	17 00 
    4de6:	0b 24       	jz	$+24     	;abs 0x4dfe
    4de8:	fb b0 03 00 	bit.b	#3,	25(r11)	;#0x0003, 0x0019(r11)
    4dec:	19 00 
    4dee:	07 24       	jz	$+16     	;abs 0x4dfe
    4df0:	9b 9b 1c 00 	cmp	28(r11),30(r11)	;0x001c(r11), 0x001e(r11)
    4df4:	1e 00 
    4df6:	03 20       	jnz	$+8      	;abs 0x4dfe
    4df8:	db 43 14 00 	mov.b	#1,	20(r11)	;r3 As==01, 0x0014(r11)
    4dfc:	02 3c       	jmp	$+6      	;abs 0x4e02
    4dfe:	cb 43 14 00 	mov.b	#0,	20(r11)	;r3 As==00, 0x0014(r11)
    4e02:	0d 41       	mov	r1,	r13	
    4e04:	0e 41       	mov	r1,	r14	
    4e06:	2e 53       	incd	r14		
    4e08:	0f 4b       	mov	r11,	r15	
    4e0a:	3f 50 10 00 	add	#16,	r15	;#0x0010
    4e0e:	b0 13 dc 4c 	calla	#0x04cdc	
    4e12:	81 93 02 00 	tst	2(r1)		;0x0002(r1)
    4e16:	02 24       	jz	$+6      	;abs 0x4e1c
    4e18:	ea 43 03 00 	mov.b	#2,	3(r10)	;r3 As==10, 0x0003(r10)
    4e1c:	81 93 00 00 	tst	0(r1)		;0x0000(r1)
    4e20:	02 24       	jz	$+6      	;abs 0x4e26
    4e22:	ea 43 01 00 	mov.b	#2,	1(r10)	;r3 As==10, 0x0001(r10)
    4e26:	5f 4b 17 00 	mov.b	23(r11),r15	;0x0017(r11)
    4e2a:	7f f0 03 00 	and.b	#3,	r15	;#0x0003
    4e2e:	6f 83       	decd.b	r15		
    4e30:	6f 93       	cmp.b	#2,	r15	;r3 As==10
    4e32:	04 2c       	jc	$+10     	;abs 0x4e3c
    4e34:	4f 4f       	mov.b	r15,	r15	
    4e36:	5f 4f 50 9b 	mov.b	-25776(r15),r15	;0x9b50(r15)
    4e3a:	01 3c       	jmp	$+4      	;abs 0x4e3e
    4e3c:	4f 43       	clr.b	r15		
    4e3e:	ca 4f 02 00 	mov.b	r15,	2(r10)	;0x0002(r10)
    4e42:	5f 4b 19 00 	mov.b	25(r11),r15	;0x0019(r11)
    4e46:	7f f0 03 00 	and.b	#3,	r15	;#0x0003
    4e4a:	6f 83       	decd.b	r15		
    4e4c:	6f 93       	cmp.b	#2,	r15	;r3 As==10
    4e4e:	04 2c       	jc	$+10     	;abs 0x4e58
    4e50:	4f 4f       	mov.b	r15,	r15	
    4e52:	5f 4f 50 9b 	mov.b	-25776(r15),r15	;0x9b50(r15)
    4e56:	01 3c       	jmp	$+4      	;abs 0x4e5a
    4e58:	4f 43       	clr.b	r15		
    4e5a:	ca 4f 04 00 	mov.b	r15,	4(r10)	;0x0004(r10)
    4e5e:	21 52       	add	#4,	r1	;r2 As==10
    4e60:	1a 16       	popm.a	#2,	r11	
    4e62:	10 01       	reta			

00004e64 <frame802154_is_broadcast_addr>:
    4e64:	6f 93       	cmp.b	#2,	r15	;r3 As==10
    4e66:	08 24       	jz	$+18     	;abs 0x4e78
    4e68:	3f 42       	mov	#8,	r15	;r2 As==11
    4e6a:	07 3c       	jmp	$+16     	;abs 0x4e7a
    4e6c:	0d 4e       	mov	r14,	r13	
    4e6e:	0d 5f       	add	r15,	r13	
    4e70:	fd 93 00 00 	cmp.b	#-1,	0(r13)	;r3 As==11, 0x0000(r13)
    4e74:	02 24       	jz	$+6      	;abs 0x4e7a
    4e76:	08 3c       	jmp	$+18     	;abs 0x4e88
    4e78:	2f 43       	mov	#2,	r15	;r3 As==10
    4e7a:	3f 53       	add	#-1,	r15	;r3 As==11
    4e7c:	0d 4f       	mov	r15,	r13	
    4e7e:	1d 53       	inc	r13		
    4e80:	1d 93       	cmp	#1,	r13	;r3 As==01
    4e82:	f4 37       	jge	$-22     	;abs 0x4e6c
    4e84:	5f 43       	mov.b	#1,	r15	;r3 As==01
    4e86:	10 01       	reta			
    4e88:	4f 43       	clr.b	r15		
    4e8a:	10 01       	reta			

00004e8c <frame802154_hdrlen>:
    4e8c:	31 50 fa ff 	add	#-6,	r1	;#0xfffa
    4e90:	0e 41       	mov	r1,	r14	
    4e92:	b0 13 bc 4d 	calla	#0x04dbc	
    4e96:	6f 41       	mov.b	@r1,	r15	
    4e98:	2f 53       	incd	r15		
    4e9a:	5e 41 01 00 	mov.b	1(r1),	r14	;0x0001(r1)
    4e9e:	0f 5e       	add	r14,	r15	
    4ea0:	5e 41 02 00 	mov.b	2(r1),	r14	;0x0002(r1)
    4ea4:	0f 5e       	add	r14,	r15	
    4ea6:	5e 41 03 00 	mov.b	3(r1),	r14	;0x0003(r1)
    4eaa:	0f 5e       	add	r14,	r15	
    4eac:	5e 41 04 00 	mov.b	4(r1),	r14	;0x0004(r1)
    4eb0:	0f 5e       	add	r14,	r15	
    4eb2:	5e 41 05 00 	mov.b	5(r1),	r14	;0x0005(r1)
    4eb6:	0f 5e       	add	r14,	r15	
    4eb8:	31 50 06 00 	add	#6,	r1	;#0x0006
    4ebc:	10 01       	reta			

00004ebe <frame802154_create_fcf>:
    4ebe:	5c 4f 01 00 	mov.b	1(r15),	r12	;0x0001(r15)
    4ec2:	1c f3       	and	#1,	r12	;r3 As==01
    4ec4:	5c 0a       	rlam	#3,	r12	
    4ec6:	5d 4f 02 00 	mov.b	2(r15),	r13	;0x0002(r15)
    4eca:	1d f3       	and	#1,	r13	;r3 As==01
    4ecc:	5d 0e       	rlam	#4,	r13	
    4ece:	4c dd       	bis.b	r13,	r12	
    4ed0:	6d 4f       	mov.b	@r15,	r13	
    4ed2:	7d f0 07 00 	and.b	#7,	r13	;#0x0007
    4ed6:	4c dd       	bis.b	r13,	r12	
    4ed8:	5d 4f 03 00 	mov.b	3(r15),	r13	;0x0003(r15)
    4edc:	1d f3       	and	#1,	r13	;r3 As==01
    4ede:	5d 0e       	rlam	#4,	r13	
    4ee0:	5d 02       	rlam	#1,	r13	
    4ee2:	4c dd       	bis.b	r13,	r12	
    4ee4:	5d 4f 04 00 	mov.b	4(r15),	r13	;0x0004(r15)
    4ee8:	1d f3       	and	#1,	r13	;r3 As==01
    4eea:	5d 0e       	rlam	#4,	r13	
    4eec:	5d 06       	rlam	#2,	r13	
    4eee:	4c dd       	bis.b	r13,	r12	
    4ef0:	ce 4c 00 00 	mov.b	r12,	0(r14)	;0x0000(r14)
    4ef4:	5c 4f 09 00 	mov.b	9(r15),	r12	;0x0009(r15)
    4ef8:	5c 0e       	rlam	#4,	r12	
    4efa:	5c 06       	rlam	#2,	r12	
    4efc:	5d 4f 05 00 	mov.b	5(r15),	r13	;0x0005(r15)
    4f00:	5d f3       	and.b	#1,	r13	;r3 As==01
    4f02:	4d dc       	bis.b	r12,	r13	
    4f04:	5c 4f 06 00 	mov.b	6(r15),	r12	;0x0006(r15)
    4f08:	1c f3       	and	#1,	r12	;r3 As==01
    4f0a:	5c 02       	rlam	#1,	r12	
    4f0c:	4d dc       	bis.b	r12,	r13	
    4f0e:	5c 4f 07 00 	mov.b	7(r15),	r12	;0x0007(r15)
    4f12:	3c f0 03 00 	and	#3,	r12	;#0x0003
    4f16:	5c 06       	rlam	#2,	r12	
    4f18:	4d dc       	bis.b	r12,	r13	
    4f1a:	5f 4f 08 00 	mov.b	8(r15),	r15	;0x0008(r15)
    4f1e:	3f f0 03 00 	and	#3,	r15	;#0x0003
    4f22:	5f 0e       	rlam	#4,	r15	
    4f24:	4d df       	bis.b	r15,	r13	
    4f26:	ce 4d 01 00 	mov.b	r13,	1(r14)	;0x0001(r14)
    4f2a:	10 01       	reta			

00004f2c <frame802154_create>:
    4f2c:	4b 14       	pushm.a	#5,	r11	
    4f2e:	31 50 fa ff 	add	#-6,	r1	;#0xfffa
    4f32:	0a 4f       	mov	r15,	r10	
    4f34:	0b 4e       	mov	r14,	r11	
    4f36:	0e 41       	mov	r1,	r14	
    4f38:	b0 13 bc 4d 	calla	#0x04dbc	
    4f3c:	0e 4b       	mov	r11,	r14	
    4f3e:	0f 4a       	mov	r10,	r15	
    4f40:	3f 50 10 00 	add	#16,	r15	;#0x0010
    4f44:	b0 13 be 4e 	calla	#0x04ebe	
    4f48:	d1 93 00 00 	cmp.b	#1,	0(r1)	;r3 As==01, 0x0000(r1)
    4f4c:	06 20       	jnz	$+14     	;abs 0x4f5a
    4f4e:	db 4a 1a 00 	mov.b	26(r10),2(r11)	;0x001a(r10), 0x0002(r11)
    4f52:	02 00 
    4f54:	7f 40 03 00 	mov.b	#3,	r15	;#0x0003
    4f58:	01 3c       	jmp	$+4      	;abs 0x4f5c
    4f5a:	6f 43       	mov.b	#2,	r15	;r3 As==10
    4f5c:	e1 93 01 00 	cmp.b	#2,	1(r1)	;r3 As==10, 0x0001(r1)
    4f60:	0f 20       	jnz	$+32     	;abs 0x4f80
    4f62:	4e 4f       	mov.b	r15,	r14	
    4f64:	0e 5b       	add	r11,	r14	
    4f66:	de 4a 1c 00 	mov.b	28(r10),0(r14)	;0x001c(r10), 0x0000(r14)
    4f6a:	00 00 
    4f6c:	4e 4f       	mov.b	r15,	r14	
    4f6e:	5e 53       	inc.b	r14		
    4f70:	4e 4e       	mov.b	r14,	r14	
    4f72:	0e 5b       	add	r11,	r14	
    4f74:	1d 4a 1c 00 	mov	28(r10),r13	;0x001c(r10)
    4f78:	8d 10       	swpb	r13		
    4f7a:	ce 4d 00 00 	mov.b	r13,	0(r14)	;0x0000(r14)
    4f7e:	6f 53       	incd.b	r15		
    4f80:	58 41 02 00 	mov.b	2(r1),	r8	;0x0002(r1)
    4f84:	4e 43       	clr.b	r14		
    4f86:	0d 43       	clr	r13		
    4f88:	4c 48       	mov.b	r8,	r12	
    4f8a:	0c 5a       	add	r10,	r12	
    4f8c:	07 3c       	jmp	$+16     	;abs 0x4f9c
    4f8e:	07 4c       	mov	r12,	r7	
    4f90:	07 5d       	add	r13,	r7	
    4f92:	49 49       	mov.b	r9,	r9	
    4f94:	09 5b       	add	r11,	r9	
    4f96:	e9 47 00 00 	mov.b	@r7,	0(r9)	;0x0000(r9)
    4f9a:	5e 53       	inc.b	r14		
    4f9c:	49 4f       	mov.b	r15,	r9	
    4f9e:	49 8d       	sub.b	r13,	r9	
    4fa0:	3d 53       	add	#-1,	r13	;r3 As==11
    4fa2:	4e 98       	cmp.b	r8,	r14	
    4fa4:	f4 23       	jnz	$-22     	;abs 0x4f8e
    4fa6:	4f 5e       	add.b	r14,	r15	
    4fa8:	e1 93 03 00 	cmp.b	#2,	3(r1)	;r3 As==10, 0x0003(r1)
    4fac:	0f 20       	jnz	$+32     	;abs 0x4fcc
    4fae:	4e 4f       	mov.b	r15,	r14	
    4fb0:	0e 5b       	add	r11,	r14	
    4fb2:	de 4a 1e 00 	mov.b	30(r10),0(r14)	;0x001e(r10), 0x0000(r14)
    4fb6:	00 00 
    4fb8:	4e 4f       	mov.b	r15,	r14	
    4fba:	5e 53       	inc.b	r14		
    4fbc:	4e 4e       	mov.b	r14,	r14	
    4fbe:	0e 5b       	add	r11,	r14	
    4fc0:	1d 4a 1e 00 	mov	30(r10),r13	;0x001e(r10)
    4fc4:	8d 10       	swpb	r13		
    4fc6:	ce 4d 00 00 	mov.b	r13,	0(r14)	;0x0000(r14)
    4fca:	6f 53       	incd.b	r15		
    4fcc:	59 41 04 00 	mov.b	4(r1),	r9	;0x0004(r1)
    4fd0:	4e 43       	clr.b	r14		
    4fd2:	0d 43       	clr	r13		
    4fd4:	4c 49       	mov.b	r9,	r12	
    4fd6:	0c 5a       	add	r10,	r12	
    4fd8:	08 3c       	jmp	$+18     	;abs 0x4fea
    4fda:	08 4c       	mov	r12,	r8	
    4fdc:	08 5d       	add	r13,	r8	
    4fde:	4a 4a       	mov.b	r10,	r10	
    4fe0:	0a 5b       	add	r11,	r10	
    4fe2:	da 48 08 00 	mov.b	8(r8),	0(r10)	;0x0008(r8), 0x0000(r10)
    4fe6:	00 00 
    4fe8:	5e 53       	inc.b	r14		
    4fea:	4a 4f       	mov.b	r15,	r10	
    4fec:	4a 8d       	sub.b	r13,	r10	
    4fee:	3d 53       	add	#-1,	r13	;r3 As==11
    4ff0:	4e 99       	cmp.b	r9,	r14	
    4ff2:	f3 23       	jnz	$-24     	;abs 0x4fda
    4ff4:	4f 5e       	add.b	r14,	r15	
    4ff6:	4f 4f       	mov.b	r15,	r15	
    4ff8:	31 50 06 00 	add	#6,	r1	;#0x0006
    4ffc:	47 16       	popm.a	#5,	r11	
    4ffe:	10 01       	reta			

00005000 <frame802154_parse_fcf>:
    5000:	0b 14       	pushm.a	#1,	r11	
    5002:	31 50 f6 ff 	add	#-10,	r1	;#0xfff6
    5006:	0b 4e       	mov	r14,	r11	
    5008:	6d 4f       	mov.b	@r15,	r13	
    500a:	4e 4d       	mov.b	r13,	r14	
    500c:	7e f0 07 00 	and.b	#7,	r14	;#0x0007
    5010:	c1 4e 00 00 	mov.b	r14,	0(r1)	;0x0000(r1)
    5014:	4e 4d       	mov.b	r13,	r14	
    5016:	5e 0b       	rrum	#3,	r14	
    5018:	5e f3       	and.b	#1,	r14	;r3 As==01
    501a:	c1 4e 01 00 	mov.b	r14,	1(r1)	;0x0001(r1)
    501e:	4e 4d       	mov.b	r13,	r14	
    5020:	5e 0f       	rrum	#4,	r14	
    5022:	5e f3       	and.b	#1,	r14	;r3 As==01
    5024:	c1 4e 02 00 	mov.b	r14,	2(r1)	;0x0002(r1)
    5028:	4c 4d       	mov.b	r13,	r12	
    502a:	5c 0f       	rrum	#4,	r12	
    502c:	5c 03       	rrum	#1,	r12	
    502e:	5c f3       	and.b	#1,	r12	;r3 As==01
    5030:	c1 4c 03 00 	mov.b	r12,	3(r1)	;0x0003(r1)
    5034:	4d 4d       	mov.b	r13,	r13	
    5036:	5d 0f       	rrum	#4,	r13	
    5038:	5d 07       	rrum	#2,	r13	
    503a:	5d f3       	and.b	#1,	r13	;r3 As==01
    503c:	c1 4d 04 00 	mov.b	r13,	4(r1)	;0x0004(r1)
    5040:	5d 4f 01 00 	mov.b	1(r15),	r13	;0x0001(r15)
    5044:	4f 4d       	mov.b	r13,	r15	
    5046:	5f f3       	and.b	#1,	r15	;r3 As==01
    5048:	c1 4f 05 00 	mov.b	r15,	5(r1)	;0x0005(r1)
    504c:	4f 4d       	mov.b	r13,	r15	
    504e:	5f 03       	rrum	#1,	r15	
    5050:	5f f3       	and.b	#1,	r15	;r3 As==01
    5052:	c1 4f 06 00 	mov.b	r15,	6(r1)	;0x0006(r1)
    5056:	4f 4d       	mov.b	r13,	r15	
    5058:	5f 07       	rrum	#2,	r15	
    505a:	7f f0 03 00 	and.b	#3,	r15	;#0x0003
    505e:	c1 4f 07 00 	mov.b	r15,	7(r1)	;0x0007(r1)
    5062:	4f 4d       	mov.b	r13,	r15	
    5064:	5f 0f       	rrum	#4,	r15	
    5066:	7f f0 03 00 	and.b	#3,	r15	;#0x0003
    506a:	c1 4f 08 00 	mov.b	r15,	8(r1)	;0x0008(r1)
    506e:	4d 4d       	mov.b	r13,	r13	
    5070:	5d 0f       	rrum	#4,	r13	
    5072:	5d 07       	rrum	#2,	r13	
    5074:	c1 4d 09 00 	mov.b	r13,	9(r1)	;0x0009(r1)
    5078:	3d 40 0a 00 	mov	#10,	r13	;#0x000a
    507c:	0e 41       	mov	r1,	r14	
    507e:	0f 4b       	mov	r11,	r15	
    5080:	b0 13 2a 97 	calla	#0x0972a	
    5084:	31 50 0a 00 	add	#10,	r1	;#0x000a
    5088:	0b 16       	popm.a	#1,	r11	
    508a:	10 01       	reta			

0000508c <frame802154_parse>:
    508c:	3b 14       	pushm.a	#4,	r11	
    508e:	31 50 f2 ff 	add	#-14,	r1	;#0xfff2
    5092:	09 4f       	mov	r15,	r9	
    5094:	08 4e       	mov	r14,	r8	
    5096:	0a 4d       	mov	r13,	r10	
    5098:	2e 93       	cmp	#2,	r14	;r3 As==10
    509a:	a1 38       	jl	$+324    	;abs 0x51de
    509c:	0e 41       	mov	r1,	r14	
    509e:	b0 13 00 50 	calla	#0x05000	
    50a2:	3d 40 0a 00 	mov	#10,	r13	;#0x000a
    50a6:	0e 41       	mov	r1,	r14	
    50a8:	0f 4a       	mov	r10,	r15	
    50aa:	3f 50 10 00 	add	#16,	r15	;#0x0010
    50ae:	b0 13 2a 97 	calla	#0x0972a	
    50b2:	c1 93 05 00 	tst.b	5(r1)		;0x0005(r1)
    50b6:	03 24       	jz	$+8      	;abs 0x50be
    50b8:	0b 49       	mov	r9,	r11	
    50ba:	2b 53       	incd	r11		
    50bc:	06 3c       	jmp	$+14     	;abs 0x50ca
    50be:	da 49 02 00 	mov.b	2(r9),	26(r10)	;0x0002(r9), 0x001a(r10)
    50c2:	1a 00 
    50c4:	0b 49       	mov	r9,	r11	
    50c6:	3b 50 03 00 	add	#3,	r11	;#0x0003
    50ca:	0d 41       	mov	r1,	r13	
    50cc:	3d 50 0a 00 	add	#10,	r13	;#0x000a
    50d0:	0e 41       	mov	r1,	r14	
    50d2:	3e 50 0c 00 	add	#12,	r14	;#0x000c
    50d6:	0f 41       	mov	r1,	r15	
    50d8:	b0 13 dc 4c 	calla	#0x04cdc	
    50dc:	5f 41 07 00 	mov.b	7(r1),	r15	;0x0007(r1)
    50e0:	4f 93       	tst.b	r15		
    50e2:	2d 24       	jz	$+92     	;abs 0x513e
    50e4:	81 93 0a 00 	tst	10(r1)		;0x000a(r1)
    50e8:	09 24       	jz	$+20     	;abs 0x50fc
    50ea:	6d 4b       	mov.b	@r11,	r13	
    50ec:	5e 4b 01 00 	mov.b	1(r11),	r14	;0x0001(r11)
    50f0:	8e 10       	swpb	r14		
    50f2:	0d 5e       	add	r14,	r13	
    50f4:	8a 4d 1c 00 	mov	r13,	28(r10)	;0x001c(r10)
    50f8:	2b 53       	incd	r11		
    50fa:	02 3c       	jmp	$+6      	;abs 0x5100
    50fc:	8a 43 1c 00 	mov	#0,	28(r10)	;r3 As==00, 0x001c(r10)
    5100:	6f 93       	cmp.b	#2,	r15	;r3 As==10
    5102:	0c 20       	jnz	$+26     	;abs 0x511c
    5104:	3e 40 7e 99 	mov	#-26242,r14	;#0x997e
    5108:	0f 4a       	mov	r10,	r15	
    510a:	b0 13 72 55 	calla	#0x05572	
    510e:	da 4b 01 00 	mov.b	1(r11),	0(r10)	;0x0001(r11), 0x0000(r10)
    5112:	00 00 
    5114:	ea 4b 01 00 	mov.b	@r11,	1(r10)	;0x0001(r10)
    5118:	2b 53       	incd	r11		
    511a:	18 3c       	jmp	$+50     	;abs 0x514c
    511c:	7f 90 03 00 	cmp.b	#3,	r15	;#0x0003
    5120:	15 20       	jnz	$+44     	;abs 0x514c
    5122:	0e 4b       	mov	r11,	r14	
    5124:	3e 50 07 00 	add	#7,	r14	;#0x0007
    5128:	0f 43       	clr	r15		
    512a:	0d 4a       	mov	r10,	r13	
    512c:	0d 5f       	add	r15,	r13	
    512e:	ed 4e 00 00 	mov.b	@r14,	0(r13)	;0x0000(r13)
    5132:	1f 53       	inc	r15		
    5134:	3e 53       	add	#-1,	r14	;r3 As==11
    5136:	3f 92       	cmp	#8,	r15	;r2 As==11
    5138:	f8 23       	jnz	$-14     	;abs 0x512a
    513a:	3b 52       	add	#8,	r11	;r2 As==11
    513c:	07 3c       	jmp	$+16     	;abs 0x514c
    513e:	3e 40 7e 99 	mov	#-26242,r14	;#0x997e
    5142:	0f 4a       	mov	r10,	r15	
    5144:	b0 13 72 55 	calla	#0x05572	
    5148:	8a 43 1c 00 	mov	#0,	28(r10)	;r3 As==00, 0x001c(r10)
    514c:	5e 41 09 00 	mov.b	9(r1),	r14	;0x0009(r1)
    5150:	4e 93       	tst.b	r14		
    5152:	33 24       	jz	$+104    	;abs 0x51ba
    5154:	81 93 0c 00 	tst	12(r1)		;0x000c(r1)
    5158:	0e 24       	jz	$+30     	;abs 0x5176
    515a:	6f 4b       	mov.b	@r11,	r15	
    515c:	5d 4b 01 00 	mov.b	1(r11),	r13	;0x0001(r11)
    5160:	8d 10       	swpb	r13		
    5162:	0f 5d       	add	r13,	r15	
    5164:	8a 4f 1e 00 	mov	r15,	30(r10)	;0x001e(r10)
    5168:	2b 53       	incd	r11		
    516a:	81 93 0a 00 	tst	10(r1)		;0x000a(r1)
    516e:	06 20       	jnz	$+14     	;abs 0x517c
    5170:	8a 4f 1c 00 	mov	r15,	28(r10)	;0x001c(r10)
    5174:	03 3c       	jmp	$+8      	;abs 0x517c
    5176:	9a 4a 1c 00 	mov	28(r10),30(r10)	;0x001c(r10), 0x001e(r10)
    517a:	1e 00 
    517c:	6e 93       	cmp.b	#2,	r14	;r3 As==10
    517e:	0d 20       	jnz	$+28     	;abs 0x519a
    5180:	3e 40 7e 99 	mov	#-26242,r14	;#0x997e
    5184:	0f 4a       	mov	r10,	r15	
    5186:	3f 52       	add	#8,	r15	;r2 As==11
    5188:	b0 13 72 55 	calla	#0x05572	
    518c:	da 4b 01 00 	mov.b	1(r11),	8(r10)	;0x0001(r11), 0x0008(r10)
    5190:	08 00 
    5192:	ea 4b 09 00 	mov.b	@r11,	9(r10)	;0x0009(r10)
    5196:	2b 53       	incd	r11		
    5198:	18 3c       	jmp	$+50     	;abs 0x51ca
    519a:	7e 90 03 00 	cmp.b	#3,	r14	;#0x0003
    519e:	15 20       	jnz	$+44     	;abs 0x51ca
    51a0:	0e 4a       	mov	r10,	r14	
    51a2:	3f 40 07 00 	mov	#7,	r15	;#0x0007
    51a6:	0d 4b       	mov	r11,	r13	
    51a8:	0d 5f       	add	r15,	r13	
    51aa:	ee 4d 08 00 	mov.b	@r13,	8(r14)	;0x0008(r14)
    51ae:	3f 53       	add	#-1,	r15	;r3 As==11
    51b0:	1e 53       	inc	r14		
    51b2:	3f 93       	cmp	#-1,	r15	;r3 As==11
    51b4:	f8 23       	jnz	$-14     	;abs 0x51a6
    51b6:	3b 52       	add	#8,	r11	;r2 As==11
    51b8:	08 3c       	jmp	$+18     	;abs 0x51ca
    51ba:	3e 40 7e 99 	mov	#-26242,r14	;#0x997e
    51be:	0f 4a       	mov	r10,	r15	
    51c0:	3f 52       	add	#8,	r15	;r2 As==11
    51c2:	b0 13 72 55 	calla	#0x05572	
    51c6:	8a 43 1e 00 	mov	#0,	30(r10)	;r3 As==00, 0x001e(r10)
    51ca:	0f 4b       	mov	r11,	r15	
    51cc:	0f 89       	sub	r9,	r15	
    51ce:	0e 48       	mov	r8,	r14	
    51d0:	0e 8f       	sub	r15,	r14	
    51d2:	8a 4e 36 00 	mov	r14,	54(r10)	;0x0036(r10)
    51d6:	8a 4b 34 00 	mov	r11,	52(r10)	;0x0034(r10)
    51da:	08 9f       	cmp	r15,	r8	
    51dc:	01 34       	jge	$+4      	;abs 0x51e0
    51de:	0f 43       	clr	r15		
    51e0:	31 50 0e 00 	add	#14,	r1	;#0x000e
    51e4:	38 16       	popm.a	#4,	r11	
    51e6:	10 01       	reta			

000051e8 <parse>:
    51e8:	1b 14       	pushm.a	#2,	r11	
    51ea:	31 50 c8 ff 	add	#-56,	r1	;#0xffc8
    51ee:	b0 13 0e 62 	calla	#0x0620e	
    51f2:	0b 4f       	mov	r15,	r11	
    51f4:	b0 13 1e 62 	calla	#0x0621e	
    51f8:	0d 41       	mov	r1,	r13	
    51fa:	0e 4b       	mov	r11,	r14	
    51fc:	b0 13 8c 50 	calla	#0x0508c	
    5200:	0b 4f       	mov	r15,	r11	
    5202:	0f 93       	tst	r15		
    5204:	02 20       	jnz	$+6      	;abs 0x520a
    5206:	3b 43       	mov	#-1,	r11	;r3 As==11
    5208:	39 3c       	jmp	$+116    	;abs 0x527c
    520a:	b0 13 e8 61 	calla	#0x061e8	
    520e:	0f 93       	tst	r15		
    5210:	fa 27       	jz	$-10     	;abs 0x5206
    5212:	5e 41 10 00 	mov.b	16(r1),	r14	;0x0010(r1)
    5216:	7f 40 0b 00 	mov.b	#11,	r15	;#0x000b
    521a:	b0 13 56 63 	calla	#0x06356	
    521e:	5e 41 13 00 	mov.b	19(r1),	r14	;0x0013(r1)
    5222:	7f 40 07 00 	mov.b	#7,	r15	;#0x0007
    5226:	b0 13 56 63 	calla	#0x06356	
    522a:	c1 93 17 00 	tst.b	23(r1)		;0x0017(r1)
    522e:	15 24       	jz	$+44     	;abs 0x525a
    5230:	1a 41 1c 00 	mov	28(r1),	r10	;0x001c(r1)
    5234:	b0 13 d6 4c 	calla	#0x04cd6	
    5238:	0a 9f       	cmp	r15,	r10	
    523a:	03 24       	jz	$+8      	;abs 0x5242
    523c:	b1 93 1c 00 	cmp	#-1,	28(r1)	;r3 As==11, 0x001c(r1)
    5240:	e2 23       	jnz	$-58     	;abs 0x5206
    5242:	0e 41       	mov	r1,	r14	
    5244:	5f 41 17 00 	mov.b	23(r1),	r15	;0x0017(r1)
    5248:	b0 13 64 4e 	calla	#0x04e64	
    524c:	4f 93       	tst.b	r15		
    524e:	05 20       	jnz	$+12     	;abs 0x525a
    5250:	0e 41       	mov	r1,	r14	
    5252:	7f 40 0d 00 	mov.b	#13,	r15	;#0x000d
    5256:	b0 13 6c 63 	calla	#0x0636c	
    525a:	0e 41       	mov	r1,	r14	
    525c:	3e 52       	add	#8,	r14	;r2 As==11
    525e:	7f 40 0c 00 	mov.b	#12,	r15	;#0x000c
    5262:	b0 13 6c 63 	calla	#0x0636c	
    5266:	c1 93 15 00 	tst.b	21(r1)		;0x0015(r1)
    526a:	03 20       	jnz	$+8      	;abs 0x5272
    526c:	5e 41 1a 00 	mov.b	26(r1),	r14	;0x001a(r1)
    5270:	01 3c       	jmp	$+4      	;abs 0x5274
    5272:	3e 43       	mov	#-1,	r14	;r3 As==11
    5274:	7f 40 06 00 	mov.b	#6,	r15	;#0x0006
    5278:	b0 13 56 63 	calla	#0x06356	
    527c:	0f 4b       	mov	r11,	r15	
    527e:	31 50 38 00 	add	#56,	r1	;#0x0038
    5282:	1a 16       	popm.a	#2,	r11	
    5284:	10 01       	reta			

00005286 <framer_802154_setup_params>:
    5286:	2b 14       	pushm.a	#3,	r11	
    5288:	ca 0f       	mova	r15,	r10	
    528a:	49 4e       	mov.b	r14,	r9	
    528c:	0b 4d       	mov	r13,	r11	
    528e:	df 03       	tsta	r15		
    5290:	50 24       	jz	$+162    	;abs 0x5332
    5292:	0d 93       	tst	r13		
    5294:	4e 24       	jz	$+158    	;abs 0x5332
    5296:	7f 40 0b 00 	mov.b	#11,	r15	;#0x000b
    529a:	4a 13       	calla	r10		
    529c:	cb 4f 10 00 	mov.b	r15,	16(r11)	;0x0010(r11)
    52a0:	cb 43 12 00 	mov.b	#0,	18(r11)	;r3 As==00, 0x0012(r11)
    52a4:	49 93       	tst.b	r9		
    52a6:	03 24       	jz	$+8      	;abs 0x52ae
    52a8:	cb 43 13 00 	mov.b	#0,	19(r11)	;r3 As==00, 0x0013(r11)
    52ac:	05 3c       	jmp	$+12     	;abs 0x52b8
    52ae:	7f 40 07 00 	mov.b	#7,	r15	;#0x0007
    52b2:	4a 13       	calla	r10		
    52b4:	cb 4f 13 00 	mov.b	r15,	19(r11)	;0x0013(r11)
    52b8:	cb 43 15 00 	mov.b	#0,	21(r11)	;r3 As==00, 0x0015(r11)
    52bc:	7f 42       	mov.b	#8,	r15	;r2 As==11
    52be:	4a 13       	calla	r10		
    52c0:	cb 4f 16 00 	mov.b	r15,	22(r11)	;0x0016(r11)
    52c4:	db 43 18 00 	mov.b	#1,	24(r11)	;r3 As==01, 0x0018(r11)
    52c8:	cb 43 11 00 	mov.b	#0,	17(r11)	;r3 As==00, 0x0011(r11)
    52cc:	7f 40 06 00 	mov.b	#6,	r15	;#0x0006
    52d0:	4a 13       	calla	r10		
    52d2:	cb 4f 1a 00 	mov.b	r15,	26(r11)	;0x001a(r11)
    52d6:	b0 13 d6 4c 	calla	#0x04cd6	
    52da:	8b 4f 1e 00 	mov	r15,	30(r11)	;0x001e(r11)
    52de:	7f 40 09 00 	mov.b	#9,	r15	;#0x0009
    52e2:	4a 13       	calla	r10		
    52e4:	1f 93       	cmp	#1,	r15	;r3 As==01
    52e6:	03 20       	jnz	$+8      	;abs 0x52ee
    52e8:	cb 43 19 00 	mov.b	#0,	25(r11)	;r3 As==00, 0x0019(r11)
    52ec:	03 3c       	jmp	$+8      	;abs 0x52f4
    52ee:	fb 40 03 00 	mov.b	#3,	25(r11)	;#0x0003, 0x0019(r11)
    52f2:	19 00 
    52f4:	b0 13 d6 4c 	calla	#0x04cd6	
    52f8:	8b 4f 1c 00 	mov	r15,	28(r11)	;0x001c(r11)
    52fc:	7f 40 0a 00 	mov.b	#10,	r15	;#0x000a
    5300:	4a 13       	calla	r10		
    5302:	1f 93       	cmp	#1,	r15	;r3 As==01
    5304:	03 20       	jnz	$+8      	;abs 0x530c
    5306:	cb 43 17 00 	mov.b	#0,	23(r11)	;r3 As==00, 0x0017(r11)
    530a:	08 3c       	jmp	$+18     	;abs 0x531c
    530c:	49 93       	tst.b	r9		
    530e:	03 24       	jz	$+8      	;abs 0x5316
    5310:	eb 43 17 00 	mov.b	#2,	23(r11)	;r3 As==10, 0x0017(r11)
    5314:	03 3c       	jmp	$+8      	;abs 0x531c
    5316:	fb 40 03 00 	mov.b	#3,	23(r11)	;#0x0003, 0x0017(r11)
    531a:	17 00 
    531c:	eb 93 19 00 	cmp.b	#2,	25(r11)	;r3 As==10, 0x0019(r11)
    5320:	03 24       	jz	$+8      	;abs 0x5328
    5322:	eb 93 17 00 	cmp.b	#2,	23(r11)	;r3 As==10, 0x0017(r11)
    5326:	03 20       	jnz	$+8      	;abs 0x532e
    5328:	db 43 14 00 	mov.b	#1,	20(r11)	;r3 As==01, 0x0014(r11)
    532c:	02 3c       	jmp	$+6      	;abs 0x5332
    532e:	cb 43 14 00 	mov.b	#0,	20(r11)	;r3 As==00, 0x0014(r11)
    5332:	29 16       	popm.a	#3,	r11	
    5334:	10 01       	reta			

00005336 <create_frame>:
    5336:	1b 14       	pushm.a	#2,	r11	
    5338:	31 50 c8 ff 	add	#-56,	r1	;#0xffc8
    533c:	0a 4f       	mov	r15,	r10	
    533e:	b0 13 d6 4c 	calla	#0x04cd6	
    5342:	3f 93       	cmp	#-1,	r15	;r3 As==11
    5344:	02 20       	jnz	$+6      	;abs 0x534a
    5346:	3b 43       	mov	#-1,	r11	;r3 As==11
    5348:	40 3c       	jmp	$+130    	;abs 0x53ca
    534a:	3d 40 38 00 	mov	#56,	r13	;#0x0038
    534e:	0e 43       	clr	r14		
    5350:	0f 41       	mov	r1,	r15	
    5352:	b0 13 12 98 	calla	#0x09812	
    5356:	b0 13 8e 63 	calla	#0x0638e	
    535a:	0d 41       	mov	r1,	r13	
    535c:	4e 4f       	mov.b	r15,	r14	
    535e:	8f 00 62 63 	mova	#0x06362,r15	
    5362:	b0 13 86 52 	calla	#0x05286	
    5366:	b0 13 8e 63 	calla	#0x0638e	
    536a:	4f 93       	tst.b	r15		
    536c:	05 24       	jz	$+12     	;abs 0x5378
    536e:	f1 43 00 00 	mov.b	#-1,	0(r1)	;r3 As==11, 0x0000(r1)
    5372:	f1 43 01 00 	mov.b	#-1,	1(r1)	;r3 As==11, 0x0001(r1)
    5376:	08 3c       	jmp	$+18     	;abs 0x5388
    5378:	7f 40 0d 00 	mov.b	#13,	r15	;#0x000d
    537c:	b0 13 80 63 	calla	#0x06380	
    5380:	0e 4f       	mov	r15,	r14	
    5382:	0f 41       	mov	r1,	r15	
    5384:	b0 13 72 55 	calla	#0x05572	
    5388:	7f 40 0c 00 	mov.b	#12,	r15	;#0x000c
    538c:	b0 13 80 63 	calla	#0x06380	
    5390:	0e 4f       	mov	r15,	r14	
    5392:	0f 41       	mov	r1,	r15	
    5394:	3f 52       	add	#8,	r15	;r2 As==11
    5396:	b0 13 72 55 	calla	#0x05572	
    539a:	b0 13 1e 62 	calla	#0x0621e	
    539e:	81 4f 34 00 	mov	r15,	52(r1)	;0x0034(r1)
    53a2:	b0 13 0e 62 	calla	#0x0620e	
    53a6:	81 4f 36 00 	mov	r15,	54(r1)	;0x0036(r1)
    53aa:	0f 41       	mov	r1,	r15	
    53ac:	b0 13 8c 4e 	calla	#0x04e8c	
    53b0:	0b 4f       	mov	r15,	r11	
    53b2:	0a 93       	tst	r10		
    53b4:	0a 24       	jz	$+22     	;abs 0x53ca
    53b6:	b0 13 70 62 	calla	#0x06270	
    53ba:	0f 93       	tst	r15		
    53bc:	c4 27       	jz	$-118    	;abs 0x5346
    53be:	b0 13 08 62 	calla	#0x06208	
    53c2:	0e 4f       	mov	r15,	r14	
    53c4:	0f 41       	mov	r1,	r15	
    53c6:	b0 13 2c 4f 	calla	#0x04f2c	
    53ca:	0f 4b       	mov	r11,	r15	
    53cc:	31 50 38 00 	add	#56,	r1	;#0x0038
    53d0:	1a 16       	popm.a	#2,	r11	
    53d2:	10 01       	reta			

000053d4 <create>:
    53d4:	1f 43       	mov	#1,	r15	;r3 As==01
    53d6:	b0 13 36 53 	calla	#0x05336	
    53da:	10 01       	reta			

000053dc <hdr_length>:
    53dc:	0f 43       	clr	r15		
    53de:	b0 13 36 53 	calla	#0x05336	
    53e2:	10 01       	reta			

000053e4 <i2c_receiveinit>:
    53e4:	d2 43 d9 00 	mov.b	#1,	&0x00d9	;r3 As==01
    53e8:	f2 40 0f 00 	mov.b	#15,	&0x00d8	;#0x000f
    53ec:	d8 00 
    53ee:	f2 40 81 ff 	mov.b	#-127,	&0x00d9	;#0xff81
    53f2:	d9 00 
    53f4:	d2 42 53 1a 	mov.b	&0x1a53,&0x00da	
    53f8:	da 00 
    53fa:	d2 42 ee 23 	mov.b	&0x23ee,&0x00db	
    53fe:	db 00 
    5400:	4f 4f       	mov.b	r15,	r15	
    5402:	82 4f 7e 01 	mov	r15,	&0x017e	
    5406:	f2 f0 ef ff 	and.b	#-17,	&0x00d9	;#0xffef
    540a:	d9 00 
    540c:	d2 c3 d9 00 	bic.b	#1,	&0x00d9	;r3 As==01
    5410:	f2 42 dc 00 	mov.b	#8,	&0x00dc	;r2 As==11
    5414:	e2 42 06 00 	mov.b	#4,	&0x0006	;r2 As==10
    5418:	10 01       	reta			

0000541a <i2c_transmitinit>:
    541a:	d2 d3 d9 00 	bis.b	#1,	&0x00d9	;r3 As==01
    541e:	f2 d0 0f 00 	bis.b	#15,	&0x00d8	;#0x000f
    5422:	d8 00 
    5424:	f2 40 81 ff 	mov.b	#-127,	&0x00d9	;#0xff81
    5428:	d9 00 
    542a:	d2 42 53 1a 	mov.b	&0x1a53,&0x00da	
    542e:	da 00 
    5430:	d2 42 ee 23 	mov.b	&0x23ee,&0x00db	
    5434:	db 00 
    5436:	4f 4f       	mov.b	r15,	r15	
    5438:	82 4f 7e 01 	mov	r15,	&0x017e	
    543c:	d2 c3 d9 00 	bic.b	#1,	&0x00d9	;r3 As==01
    5440:	f2 42 dc 00 	mov.b	#8,	&0x00dc	;r2 As==11
    5444:	f2 42 06 00 	mov.b	#8,	&0x0006	;r2 As==11
    5448:	10 01       	reta			

0000544a <i2c_receive_n>:
    544a:	c2 4f ed 23 	mov.b	r15,	&0x23ed	
    544e:	c2 4f 1d 24 	mov.b	r15,	&0x241d	
    5452:	82 4e 28 24 	mov	r14,	&0x2428	
    5456:	e2 b3 d9 00 	bit.b	#2,	&0x00d9	;r3 As==10
    545a:	fd 23       	jnz	$-4      	;abs 0x5456
    545c:	f2 b2 dd 00 	bit.b	#8,	&0x00dd	;r2 As==11
    5460:	fa 23       	jnz	$-10     	;abs 0x5456
    5462:	5f 42 ed 23 	mov.b	&0x23ed,r15	
    5466:	5f 93       	cmp.b	#1,	r15	;r3 As==01
    5468:	0b 20       	jnz	$+24     	;abs 0x5480
    546a:	32 c2       	dint			
    546c:	03 43       	nop			
    546e:	e2 d3 d9 00 	bis.b	#2,	&0x00d9	;r3 As==10
    5472:	e2 b3 d9 00 	bit.b	#2,	&0x00d9	;r3 As==10
    5476:	fd 23       	jnz	$-4      	;abs 0x5472
    5478:	e2 d2 d9 00 	bis.b	#4,	&0x00d9	;r2 As==10
    547c:	32 d2       	eint			
    547e:	02 3c       	jmp	$+6      	;abs 0x5484
    5480:	e2 d3 d9 00 	bis.b	#2,	&0x00d9	;r3 As==10
    5484:	4f 43       	clr.b	r15		
    5486:	10 01       	reta			

00005488 <i2c_busy>:
    5488:	5f 42 dd 00 	mov.b	&0x00dd,r15	
    548c:	7f f0 10 00 	and.b	#16,	r15	;#0x0010
    5490:	10 01       	reta			

00005492 <i2c_enable>:
    5492:	f2 d0 06 00 	bis.b	#6,	&0x0033	;#0x0006
    5496:	33 00 
    5498:	f2 d0 06 00 	bis.b	#6,	&0x0045	;#0x0006
    549c:	45 00 
    549e:	e2 d2 32 00 	bis.b	#4,	&0x0032	;r2 As==10
    54a2:	e2 c3 32 00 	bic.b	#2,	&0x0032	;r3 As==10
    54a6:	f2 d0 06 00 	bis.b	#6,	&0x0012	;#0x0006
    54aa:	12 00 
    54ac:	f2 d0 06 00 	bis.b	#6,	&0x0031	;#0x0006
    54b0:	31 00 
    54b2:	10 01       	reta			

000054b4 <i2c_transmit_n>:
    54b4:	c2 4f ec 23 	mov.b	r15,	&0x23ec	
    54b8:	c2 4f 20 24 	mov.b	r15,	&0x2420	
    54bc:	82 4e 1e 24 	mov	r14,	&0x241e	
    54c0:	f2 d0 12 00 	bis.b	#18,	&0x00d9	;#0x0012
    54c4:	d9 00 
    54c6:	10 01       	reta			

000054c8 <leds_arch_init>:
    54c8:	f2 d0 70 00 	bis.b	#112,	&0x0032	;#0x0070
    54cc:	32 00 
    54ce:	f2 d0 70 00 	bis.b	#112,	&0x0031	;#0x0070
    54d2:	31 00 
    54d4:	10 01       	reta			

000054d6 <leds_arch_get>:
    54d6:	5e 42 31 00 	mov.b	&0x0031,r14	
    54da:	7e b0 10 00 	bit.b	#16,	r14	;#0x0010
    54de:	02 24       	jz	$+6      	;abs 0x54e4
    54e0:	4f 43       	clr.b	r15		
    54e2:	02 3c       	jmp	$+6      	;abs 0x54e8
    54e4:	7f 40 10 00 	mov.b	#16,	r15	;#0x0010
    54e8:	7e b0 40 00 	bit.b	#64,	r14	;#0x0040
    54ec:	02 24       	jz	$+6      	;abs 0x54f2
    54ee:	4d 43       	clr.b	r13		
    54f0:	02 3c       	jmp	$+6      	;abs 0x54f6
    54f2:	7d 40 40 00 	mov.b	#64,	r13	;#0x0040
    54f6:	4f dd       	bis.b	r13,	r15	
    54f8:	7e f0 20 00 	and.b	#32,	r14	;#0x0020
    54fc:	02 24       	jz	$+6      	;abs 0x5502
    54fe:	4e 43       	clr.b	r14		
    5500:	02 3c       	jmp	$+6      	;abs 0x5506
    5502:	7e 40 20 00 	mov.b	#32,	r14	;#0x0020
    5506:	4f de       	bis.b	r14,	r15	
    5508:	10 01       	reta			

0000550a <leds_arch_set>:
    550a:	5e 42 31 00 	mov.b	&0x0031,r14	
    550e:	7e f0 8f ff 	and.b	#-113,	r14	;#0xff8f
    5512:	7f b0 10 00 	bit.b	#16,	r15	;#0x0010
    5516:	02 24       	jz	$+6      	;abs 0x551c
    5518:	4d 43       	clr.b	r13		
    551a:	02 3c       	jmp	$+6      	;abs 0x5520
    551c:	7d 40 10 00 	mov.b	#16,	r13	;#0x0010
    5520:	4e dd       	bis.b	r13,	r14	
    5522:	7f b0 40 00 	bit.b	#64,	r15	;#0x0040
    5526:	02 24       	jz	$+6      	;abs 0x552c
    5528:	4d 43       	clr.b	r13		
    552a:	02 3c       	jmp	$+6      	;abs 0x5530
    552c:	7d 40 40 00 	mov.b	#64,	r13	;#0x0040
    5530:	4d de       	bis.b	r14,	r13	
    5532:	7f f0 20 00 	and.b	#32,	r15	;#0x0020
    5536:	02 24       	jz	$+6      	;abs 0x553c
    5538:	4f 43       	clr.b	r15		
    553a:	02 3c       	jmp	$+6      	;abs 0x5540
    553c:	7f 40 20 00 	mov.b	#32,	r15	;#0x0020
    5540:	4f dd       	bis.b	r13,	r15	
    5542:	c2 4f 31 00 	mov.b	r15,	&0x0031	
    5546:	10 01       	reta			

00005548 <leds_init>:
    5548:	b0 13 c8 54 	calla	#0x054c8	
    554c:	10 01       	reta			

0000554e <leds_on>:
    554e:	0b 14       	pushm.a	#1,	r11	
    5550:	4b 4f       	mov.b	r15,	r11	
    5552:	b0 13 d6 54 	calla	#0x054d6	
    5556:	4f db       	bis.b	r11,	r15	
    5558:	b0 13 0a 55 	calla	#0x0550a	
    555c:	0b 16       	popm.a	#1,	r11	
    555e:	10 01       	reta			

00005560 <leds_off>:
    5560:	0b 14       	pushm.a	#1,	r11	
    5562:	4b 4f       	mov.b	r15,	r11	
    5564:	b0 13 d6 54 	calla	#0x054d6	
    5568:	4f cb       	bic.b	r11,	r15	
    556a:	b0 13 0a 55 	calla	#0x0550a	
    556e:	0b 16       	popm.a	#1,	r11	
    5570:	10 01       	reta			

00005572 <linkaddr_copy>:
    5572:	3d 42       	mov	#8,	r13	;r2 As==11
    5574:	b0 13 2a 97 	calla	#0x0972a	
    5578:	10 01       	reta			

0000557a <linkaddr_cmp>:
    557a:	3d 42       	mov	#8,	r13	;r2 As==11
    557c:	b0 13 fe 96 	calla	#0x096fe	
    5580:	5e 43       	mov.b	#1,	r14	;r3 As==01
    5582:	0f 93       	tst	r15		
    5584:	01 24       	jz	$+4      	;abs 0x5588
    5586:	4e 43       	clr.b	r14		
    5588:	4f 4e       	mov.b	r14,	r15	
    558a:	10 01       	reta			

0000558c <linkaddr_set_node_addr>:
    558c:	0e 4f       	mov	r15,	r14	
    558e:	3f 40 2a 24 	mov	#9258,	r15	;#0x242a
    5592:	b0 13 72 55 	calla	#0x05572	
    5596:	10 01       	reta			

00005598 <list_init>:
    5598:	8f 43 00 00 	mov	#0,	0(r15)	;r3 As==00, 0x0000(r15)
    559c:	10 01       	reta			

0000559e <list_head>:
    559e:	2f 4f       	mov	@r15,	r15	
    55a0:	10 01       	reta			

000055a2 <list_tail>:
    55a2:	2f 4f       	mov	@r15,	r15	
    55a4:	0f 93       	tst	r15		
    55a6:	02 20       	jnz	$+6      	;abs 0x55ac
    55a8:	10 01       	reta			
    55aa:	0f 4e       	mov	r14,	r15	
    55ac:	2e 4f       	mov	@r15,	r14	
    55ae:	0e 93       	tst	r14		
    55b0:	fc 23       	jnz	$-6      	;abs 0x55aa
    55b2:	10 01       	reta			

000055b4 <list_remove>:
    55b4:	0b 14       	pushm.a	#1,	r11	
    55b6:	2d 4f       	mov	@r15,	r13	
    55b8:	0d 93       	tst	r13		
    55ba:	14 24       	jz	$+42     	;abs 0x55e4
    55bc:	0c 43       	clr	r12		
    55be:	01 3c       	jmp	$+4      	;abs 0x55c2
    55c0:	0d 4b       	mov	r11,	r13	
    55c2:	0d 9e       	cmp	r14,	r13	
    55c4:	0b 20       	jnz	$+24     	;abs 0x55dc
    55c6:	2e 4d       	mov	@r13,	r14	
    55c8:	0c 93       	tst	r12		
    55ca:	03 20       	jnz	$+8      	;abs 0x55d2
    55cc:	8f 4e 00 00 	mov	r14,	0(r15)	;0x0000(r15)
    55d0:	02 3c       	jmp	$+6      	;abs 0x55d6
    55d2:	8c 4e 00 00 	mov	r14,	0(r12)	;0x0000(r12)
    55d6:	8d 43 00 00 	mov	#0,	0(r13)	;r3 As==00, 0x0000(r13)
    55da:	04 3c       	jmp	$+10     	;abs 0x55e4
    55dc:	2b 4d       	mov	@r13,	r11	
    55de:	0c 4d       	mov	r13,	r12	
    55e0:	0b 93       	tst	r11		
    55e2:	ee 23       	jnz	$-34     	;abs 0x55c0
    55e4:	0b 16       	popm.a	#1,	r11	
    55e6:	10 01       	reta			

000055e8 <list_add>:
    55e8:	1b 14       	pushm.a	#2,	r11	
    55ea:	0a 4f       	mov	r15,	r10	
    55ec:	0b 4e       	mov	r14,	r11	
    55ee:	b0 13 b4 55 	calla	#0x055b4	
    55f2:	8b 43 00 00 	mov	#0,	0(r11)	;r3 As==00, 0x0000(r11)
    55f6:	0f 4a       	mov	r10,	r15	
    55f8:	b0 13 a2 55 	calla	#0x055a2	
    55fc:	0f 93       	tst	r15		
    55fe:	03 20       	jnz	$+8      	;abs 0x5606
    5600:	8a 4b 00 00 	mov	r11,	0(r10)	;0x0000(r10)
    5604:	02 3c       	jmp	$+6      	;abs 0x560a
    5606:	8f 4b 00 00 	mov	r11,	0(r15)	;0x0000(r15)
    560a:	1a 16       	popm.a	#2,	r11	
    560c:	10 01       	reta			

0000560e <list_length>:
    560e:	2e 4f       	mov	@r15,	r14	
    5610:	0f 43       	clr	r15		
    5612:	02 3c       	jmp	$+6      	;abs 0x5618
    5614:	1f 53       	inc	r15		
    5616:	2e 4e       	mov	@r14,	r14	
    5618:	0e 93       	tst	r14		
    561a:	fc 23       	jnz	$-6      	;abs 0x5614
    561c:	10 01       	reta			

0000561e <list_item_next>:
    561e:	0f 93       	tst	r15		
    5620:	02 24       	jz	$+6      	;abs 0x5626
    5622:	2f 4f       	mov	@r15,	r15	
    5624:	10 01       	reta			
    5626:	0f 43       	clr	r15		
    5628:	10 01       	reta			

0000562a <log_lladdr>:
    562a:	1b 14       	pushm.a	#2,	r11	
    562c:	0a 4f       	mov	r15,	r10	
    562e:	0f 93       	tst	r15		
    5630:	0d 20       	jnz	$+28     	;abs 0x564c
    5632:	30 12 52 9b 	push	#-25774	;#0x9b52
    5636:	b0 13 68 8d 	calla	#0x08d68	
    563a:	21 53       	incd	r1		
    563c:	14 3c       	jmp	$+42     	;abs 0x5666
    563e:	1b b3       	bit	#1,	r11	;r3 As==01
    5640:	06 20       	jnz	$+14     	;abs 0x564e
    5642:	3f 40 2e 00 	mov	#46,	r15	;#0x002e
    5646:	b0 13 ce 6c 	calla	#0x06cce	
    564a:	01 3c       	jmp	$+4      	;abs 0x564e
    564c:	0b 43       	clr	r11		
    564e:	0f 4a       	mov	r10,	r15	
    5650:	0f 5b       	add	r11,	r15	
    5652:	6f 4f       	mov.b	@r15,	r15	
    5654:	0f 12       	push	r15		
    5656:	30 12 61 9b 	push	#-25759	;#0x9b61
    565a:	b0 13 68 8d 	calla	#0x08d68	
    565e:	21 52       	add	#4,	r1	;r2 As==10
    5660:	1b 53       	inc	r11		
    5662:	3b 92       	cmp	#8,	r11	;r2 As==11
    5664:	ec 23       	jnz	$-38     	;abs 0x563e
    5666:	1a 16       	popm.a	#2,	r11	
    5668:	10 01       	reta			

0000566a <mac_sequence_init>:
    566a:	b0 13 84 68 	calla	#0x06884	
    566e:	c2 4f ef 23 	mov.b	r15,	&0x23ef	
    5672:	10 01       	reta			

00005674 <mac_sequence_set_dsn>:
    5674:	5e 42 ef 23 	mov.b	&0x23ef,r14	
    5678:	4f 4e       	mov.b	r14,	r15	
    567a:	5f 53       	inc.b	r15		
    567c:	c2 4f ef 23 	mov.b	r15,	&0x23ef	
    5680:	4e 4e       	mov.b	r14,	r14	
    5682:	7f 40 06 00 	mov.b	#6,	r15	;#0x0006
    5686:	b0 13 56 63 	calla	#0x06356	
    568a:	10 01       	reta			

0000568c <mac_sequence_is_duplicate>:
    568c:	4b 14       	pushm.a	#5,	r11	
    568e:	b0 13 2c 44 	calla	#0x0442c	
    5692:	0a 4e       	mov	r14,	r10	
    5694:	0b 4f       	mov	r15,	r11	
    5696:	09 43       	clr	r9		
    5698:	7f 40 0c 00 	mov.b	#12,	r15	;#0x000c
    569c:	b0 13 80 63 	calla	#0x06380	
    56a0:	0e 49       	mov	r9,	r14	
    56a2:	5e 02       	rlam	#1,	r14	
    56a4:	08 49       	mov	r9,	r8	
    56a6:	58 0e       	rlam	#4,	r8	
    56a8:	08 8e       	sub	r14,	r8	
    56aa:	07 48       	mov	r8,	r7	
    56ac:	37 50 ac 1b 	add	#7084,	r7	;#0x1bac
    56b0:	0e 47       	mov	r7,	r14	
    56b2:	b0 13 7a 55 	calla	#0x0557a	
    56b6:	4f 93       	tst.b	r15		
    56b8:	19 24       	jz	$+52     	;abs 0x56ec
    56ba:	7f 40 06 00 	mov.b	#6,	r15	;#0x0006
    56be:	b0 13 62 63 	calla	#0x06362	
    56c2:	5e 48 b8 1b 	mov.b	7096(r8),r14	;0x1bb8(r8)
    56c6:	0f 9e       	cmp	r14,	r15	
    56c8:	02 24       	jz	$+6      	;abs 0x56ce
    56ca:	0f 43       	clr	r15		
    56cc:	14 3c       	jmp	$+42     	;abs 0x56f6
    56ce:	0e 4a       	mov	r10,	r14	
    56d0:	0f 4b       	mov	r11,	r15	
    56d2:	1e 87 08 00 	sub	8(r7),	r14	;0x0008(r7)
    56d6:	1f 77 0a 00 	subc	10(r7),	r15	;0x000a(r7)
    56da:	1d 43       	mov	#1,	r13	;r3 As==01
    56dc:	0f 93       	tst	r15		
    56de:	03 20       	jnz	$+8      	;abs 0x56e6
    56e0:	3e 90 01 0a 	cmp	#2561,	r14	;#0x0a01
    56e4:	01 28       	jnc	$+4      	;abs 0x56e8
    56e6:	0d 43       	clr	r13		
    56e8:	0f 4d       	mov	r13,	r15	
    56ea:	05 3c       	jmp	$+12     	;abs 0x56f6
    56ec:	19 53       	inc	r9		
    56ee:	39 90 10 00 	cmp	#16,	r9	;#0x0010
    56f2:	d2 23       	jnz	$-90     	;abs 0x5698
    56f4:	ea 3f       	jmp	$-42     	;abs 0x56ca
    56f6:	47 16       	popm.a	#5,	r11	
    56f8:	10 01       	reta			

000056fa <mac_sequence_register_seqno>:
    56fa:	1b 14       	pushm.a	#2,	r11	
    56fc:	0a 43       	clr	r10		
    56fe:	7f 40 0c 00 	mov.b	#12,	r15	;#0x000c
    5702:	b0 13 80 63 	calla	#0x06380	
    5706:	0d 4a       	mov	r10,	r13	
    5708:	5d 02       	rlam	#1,	r13	
    570a:	0e 4a       	mov	r10,	r14	
    570c:	5e 0e       	rlam	#4,	r14	
    570e:	0e 8d       	sub	r13,	r14	
    5710:	3e 50 ac 1b 	add	#7084,	r14	;#0x1bac
    5714:	b0 13 7a 55 	calla	#0x0557a	
    5718:	0b 4a       	mov	r10,	r11	
    571a:	1b 53       	inc	r11		
    571c:	4f 93       	tst.b	r15		
    571e:	04 20       	jnz	$+10     	;abs 0x5728
    5720:	0a 4b       	mov	r11,	r10	
    5722:	3b 90 10 00 	cmp	#16,	r11	;#0x0010
    5726:	eb 23       	jnz	$-40     	;abs 0x56fe
    5728:	2b 83       	decd	r11		
    572a:	0f 4b       	mov	r11,	r15	
    572c:	5f 02       	rlam	#1,	r15	
    572e:	5b 0e       	rlam	#4,	r11	
    5730:	0b 8f       	sub	r15,	r11	
    5732:	3b 50 ac 1b 	add	#7084,	r11	;#0x1bac
    5736:	0a 3c       	jmp	$+22     	;abs 0x574c
    5738:	3d 40 0e 00 	mov	#14,	r13	;#0x000e
    573c:	0e 4b       	mov	r11,	r14	
    573e:	0f 4b       	mov	r11,	r15	
    5740:	3f 50 0e 00 	add	#14,	r15	;#0x000e
    5744:	b0 13 2a 97 	calla	#0x0972a	
    5748:	3b 50 f2 ff 	add	#-14,	r11	;#0xfff2
    574c:	3b 90 9e 1b 	cmp	#7070,	r11	;#0x1b9e
    5750:	f3 23       	jnz	$-24     	;abs 0x5738
    5752:	7f 40 06 00 	mov.b	#6,	r15	;#0x0006
    5756:	b0 13 62 63 	calla	#0x06362	
    575a:	c2 4f b8 1b 	mov.b	r15,	&0x1bb8	
    575e:	b0 13 2c 44 	calla	#0x0442c	
    5762:	82 4e b4 1b 	mov	r14,	&0x1bb4	
    5766:	82 4f b6 1b 	mov	r15,	&0x1bb6	
    576a:	7f 40 0c 00 	mov.b	#12,	r15	;#0x000c
    576e:	b0 13 80 63 	calla	#0x06380	
    5772:	0e 4f       	mov	r15,	r14	
    5774:	3f 40 ac 1b 	mov	#7084,	r15	;#0x1bac
    5778:	b0 13 72 55 	calla	#0x05572	
    577c:	1a 16       	popm.a	#2,	r11	
    577e:	10 01       	reta			

00005780 <mac_call_sent_callback>:
    5780:	0b 14       	pushm.a	#1,	r11	
    5782:	cb 0f       	mova	r15,	r11	
    5784:	0f 4e       	mov	r14,	r15	
    5786:	0e 4d       	mov	r13,	r14	
    5788:	0d 4c       	mov	r12,	r13	
    578a:	db 03       	tsta	r11		
    578c:	01 24       	jz	$+4      	;abs 0x5790
    578e:	4b 13       	calla	r11		
    5790:	0b 16       	popm.a	#1,	r11	
    5792:	10 01       	reta			

00005794 <memb_init>:
    5794:	0b 14       	pushm.a	#1,	r11	
    5796:	0b 4f       	mov	r15,	r11	
    5798:	1d 4f 02 00 	mov	2(r15),	r13	;0x0002(r15)
    579c:	0e 43       	clr	r14		
    579e:	1f 4f 04 00 	mov	4(r15),	r15	;0x0004(r15)
    57a2:	b0 13 12 98 	calla	#0x09812	
    57a6:	02 12       	push	r2		
    57a8:	32 c2       	dint			
    57aa:	03 43       	nop			
    57ac:	92 4b 02 00 	mov	2(r11),	&0x0132	;0x0002(r11)
    57b0:	32 01 
    57b2:	a2 4b 38 01 	mov	@r11,	&0x0138	
    57b6:	1d 42 3a 01 	mov	&0x013a,r13	
    57ba:	32 41       	pop	r2		
    57bc:	0e 43       	clr	r14		
    57be:	1f 4b 06 00 	mov	6(r11),	r15	;0x0006(r11)
    57c2:	b0 13 12 98 	calla	#0x09812	
    57c6:	0b 16       	popm.a	#1,	r11	
    57c8:	10 01       	reta			

000057ca <memb_alloc>:
    57ca:	0d 4f       	mov	r15,	r13	
    57cc:	1c 4f 02 00 	mov	2(r15),	r12	;0x0002(r15)
    57d0:	0e 43       	clr	r14		
    57d2:	16 3c       	jmp	$+46     	;abs 0x5800
    57d4:	1f 4d 04 00 	mov	4(r13),	r15	;0x0004(r13)
    57d8:	0f 5e       	add	r14,	r15	
    57da:	cf 93 00 00 	tst.b	0(r15)		;0x0000(r15)
    57de:	0f 20       	jnz	$+32     	;abs 0x57fe
    57e0:	df 43 00 00 	mov.b	#1,	0(r15)	;r3 As==01, 0x0000(r15)
    57e4:	02 12       	push	r2		
    57e6:	32 c2       	dint			
    57e8:	03 43       	nop			
    57ea:	82 4e 32 01 	mov	r14,	&0x0132	
    57ee:	a2 4d 38 01 	mov	@r13,	&0x0138	
    57f2:	1f 42 3a 01 	mov	&0x013a,r15	
    57f6:	32 41       	pop	r2		
    57f8:	1f 5d 06 00 	add	6(r13),	r15	;0x0006(r13)
    57fc:	10 01       	reta			
    57fe:	1e 53       	inc	r14		
    5800:	0e 9c       	cmp	r12,	r14	
    5802:	e8 23       	jnz	$-46     	;abs 0x57d4
    5804:	0f 43       	clr	r15		
    5806:	10 01       	reta			

00005808 <memb_free>:
    5808:	0b 14       	pushm.a	#1,	r11	
    580a:	1c 4f 06 00 	mov	6(r15),	r12	;0x0006(r15)
    580e:	1b 4f 02 00 	mov	2(r15),	r11	;0x0002(r15)
    5812:	0d 43       	clr	r13		
    5814:	0d 3c       	jmp	$+28     	;abs 0x5830
    5816:	0c 9e       	cmp	r14,	r12	
    5818:	09 20       	jnz	$+20     	;abs 0x582c
    581a:	1d 5f 04 00 	add	4(r15),	r13	;0x0004(r15)
    581e:	cd 93 00 00 	tst.b	0(r13)		;0x0000(r13)
    5822:	08 24       	jz	$+18     	;abs 0x5834
    5824:	cd 43 00 00 	mov.b	#0,	0(r13)	;r3 As==00, 0x0000(r13)
    5828:	0f 43       	clr	r15		
    582a:	05 3c       	jmp	$+12     	;abs 0x5836
    582c:	2c 5f       	add	@r15,	r12	
    582e:	1d 53       	inc	r13		
    5830:	0d 9b       	cmp	r11,	r13	
    5832:	f1 23       	jnz	$-28     	;abs 0x5816
    5834:	3f 43       	mov	#-1,	r15	;r3 As==11
    5836:	0b 16       	popm.a	#1,	r11	
    5838:	10 01       	reta			

0000583a <memb_inmemb>:
    583a:	1c 4f 06 00 	mov	6(r15),	r12	;0x0006(r15)
    583e:	0e 9c       	cmp	r12,	r14	
    5840:	0f 28       	jnc	$+32     	;abs 0x5860
    5842:	02 12       	push	r2		
    5844:	32 c2       	dint			
    5846:	03 43       	nop			
    5848:	a2 4f 32 01 	mov	@r15,	&0x0132	
    584c:	92 4f 02 00 	mov	2(r15),	&0x0138	;0x0002(r15)
    5850:	38 01 
    5852:	1d 42 3a 01 	mov	&0x013a,r13	
    5856:	32 41       	pop	r2		
    5858:	0d 5c       	add	r12,	r13	
    585a:	1f 43       	mov	#1,	r15	;r3 As==01
    585c:	0e 9d       	cmp	r13,	r14	
    585e:	01 28       	jnc	$+4      	;abs 0x5862
    5860:	0f 43       	clr	r15		
    5862:	10 01       	reta			

00005864 <msp430_init_dco>:
    5864:	5f 42 fd 10 	mov.b	&0x10fd,r15	
    5868:	c2 43 56 00 	mov.b	#0,	&0x0056	;r3 As==00
    586c:	7f 93       	cmp.b	#-1,	r15	;r3 As==11
    586e:	07 24       	jz	$+16     	;abs 0x587e
    5870:	d2 42 fd 10 	mov.b	&0x10fd,&0x0057	
    5874:	57 00 
    5876:	d2 42 fc 10 	mov.b	&0x10fc,&0x0056	
    587a:	56 00 
    587c:	10 01       	reta			
    587e:	f2 40 8d ff 	mov.b	#-115,	&0x0057	;#0xff8d
    5882:	57 00 
    5884:	f2 40 88 ff 	mov.b	#-120,	&0x0056	;#0xff88
    5888:	56 00 
    588a:	10 01       	reta			

0000588c <splhigh_>:
    588c:	0f 42       	mov	r2,	r15	
    588e:	32 c2       	dint			
    5890:	03 43       	nop			
    5892:	3f f2       	and	#8,	r15	;r2 As==11
    5894:	10 01       	reta			

00005896 <msp430_sync_dco>:
    5896:	b2 40 04 02 	mov	#516,	&0x0180	;#0x0204
    589a:	80 01 
    589c:	b2 40 00 51 	mov	#20736,	&0x018e	;#0x5100
    58a0:	8e 01 
    58a2:	b2 d0 20 00 	bis	#32,	&0x0180	;#0x0020
    58a6:	80 01 
    58a8:	92 c3 8e 01 	bic	#1,	&0x018e	;r3 As==01
    58ac:	92 b3 8e 01 	bit	#1,	&0x018e	;r3 As==01
    58b0:	fd 27       	jz	$-4      	;abs 0x58ac
    58b2:	1e 42 9e 01 	mov	&0x019e,r14	
    58b6:	92 c3 8e 01 	bic	#1,	&0x018e	;r3 As==01
    58ba:	92 b3 8e 01 	bit	#1,	&0x018e	;r3 As==01
    58be:	fd 27       	jz	$-4      	;abs 0x58ba
    58c0:	1f 42 9e 01 	mov	&0x019e,r15	
    58c4:	0f 8e       	sub	r14,	r15	
    58c6:	3f 90 f4 00 	cmp	#244,	r15	;#0x00f4
    58ca:	19 24       	jz	$+52     	;abs 0x58fe
    58cc:	3f 90 f5 00 	cmp	#245,	r15	;#0x00f5
    58d0:	0a 28       	jnc	$+22     	;abs 0x58e6
    58d2:	f2 53 56 00 	add.b	#-1,	&0x0056	;r3 As==11
    58d6:	5f 42 56 00 	mov.b	&0x0056,r15	
    58da:	7f 93       	cmp.b	#-1,	r15	;r3 As==11
    58dc:	e5 23       	jnz	$-52     	;abs 0x58a8
    58de:	5f 42 57 00 	mov.b	&0x0057,r15	
    58e2:	7f 53       	add.b	#-1,	r15	;r3 As==11
    58e4:	09 3c       	jmp	$+20     	;abs 0x58f8
    58e6:	d2 53 56 00 	inc.b	&0x0056	
    58ea:	5f 42 56 00 	mov.b	&0x0056,r15	
    58ee:	4f 93       	tst.b	r15		
    58f0:	db 23       	jnz	$-72     	;abs 0x58a8
    58f2:	5f 42 57 00 	mov.b	&0x0057,r15	
    58f6:	5f 53       	inc.b	r15		
    58f8:	c2 4f 57 00 	mov.b	r15,	&0x0057	
    58fc:	d5 3f       	jmp	$-84     	;abs 0x58a8
    58fe:	82 43 80 01 	mov	#0,	&0x0180	;r3 As==00
    5902:	10 01       	reta			

00005904 <msp430_cpu_init>:
    5904:	32 c2       	dint			
    5906:	03 43       	nop			
    5908:	b0 13 8c 6d 	calla	#0x06d8c	
    590c:	c2 43 25 00 	mov.b	#0,	&0x0025	;r3 As==00
    5910:	c2 43 2d 00 	mov.b	#0,	&0x002d	;r3 As==00
    5914:	b0 13 64 58 	calla	#0x05864	
    5918:	b0 13 96 58 	calla	#0x05896	
    591c:	32 d2       	eint			
    591e:	1f 42 4c 11 	mov	&0x114c,r15	
    5922:	1f b3       	bit	#1,	r15	;r3 As==01
    5924:	03 24       	jz	$+8      	;abs 0x592c
    5926:	1f 53       	inc	r15		
    5928:	82 4f 4c 11 	mov	r15,	&0x114c	
    592c:	82 43 32 24 	mov	#0,	&0x2432	;r3 As==00
    5930:	10 01       	reta			

00005932 <netstack_init>:
    5932:	80 13 10 99 	calla	&0x09910	
    5936:	80 13 5a 99 	calla	&0x0995a	
    593a:	80 13 8c 99 	calla	&0x0998c	
    593e:	10 01       	reta			

00005940 <node_id_z1_restore>:
    5940:	31 50 f4 ff 	add	#-12,	r1	;#0xfff4
    5944:	0c 43       	clr	r12		
    5946:	0d 43       	clr	r13		
    5948:	3e 40 0c 00 	mov	#12,	r14	;#0x000c
    594c:	0f 41       	mov	r1,	r15	
    594e:	b0 13 02 6e 	calla	#0x06e02	
    5952:	f1 90 ad ff 	cmp.b	#-83,	0(r1)	;#0xffad, 0x0000(r1)
    5956:	00 00 
    5958:	14 20       	jnz	$+42     	;abs 0x5982
    595a:	f1 90 de ff 	cmp.b	#-34,	1(r1)	;#0xffde, 0x0001(r1)
    595e:	01 00 
    5960:	10 20       	jnz	$+34     	;abs 0x5982
    5962:	5f 41 02 00 	mov.b	2(r1),	r15	;0x0002(r1)
    5966:	8f 10       	swpb	r15		
    5968:	5e 41 03 00 	mov.b	3(r1),	r14	;0x0003(r1)
    596c:	0f de       	bis	r14,	r15	
    596e:	82 4f 8c 1c 	mov	r15,	&0x1c8c	
    5972:	3d 42       	mov	#8,	r13	;r2 As==11
    5974:	0e 41       	mov	r1,	r14	
    5976:	2e 52       	add	#4,	r14	;r2 As==10
    5978:	3f 40 f0 24 	mov	#9456,	r15	;#0x24f0
    597c:	b0 13 2a 97 	calla	#0x0972a	
    5980:	02 3c       	jmp	$+6      	;abs 0x5986
    5982:	82 43 8c 1c 	mov	#0,	&0x1c8c	;r3 As==00
    5986:	31 50 0c 00 	add	#12,	r1	;#0x000c
    598a:	10 01       	reta			

0000598c <node_id_init>:
    598c:	3f 40 31 24 	mov	#9265,	r15	;#0x2431
    5990:	6e 4f       	mov.b	@r15,	r14	
    5992:	5f 4f ff ff 	mov.b	-1(r15),r15	;0xffff(r15)
    5996:	8f 10       	swpb	r15		
    5998:	0e 5f       	add	r15,	r14	
    599a:	82 4e 8c 1c 	mov	r14,	&0x1c8c	
    599e:	10 01       	reta			

000059a0 <process_thread_nullnet_example_process>:
    59a0:	1b 14       	pushm.a	#2,	r11	
    59a2:	0b 4f       	mov	r15,	r11	
    59a4:	2f 4f       	mov	@r15,	r15	
    59a6:	0f 93       	tst	r15		
    59a8:	04 24       	jz	$+10     	;abs 0x59b2
    59aa:	3f 90 dd 02 	cmp	#733,	r15	;#0x02dd
    59ae:	b2 20       	jnz	$+358    	;abs 0x5b14
    59b0:	b8 3c       	jmp	$+370    	;abs 0x5b22
    59b2:	b2 40 8c 1c 	mov	#7308,	&0x24c4	;#0x1c8c
    59b6:	c4 24 
    59b8:	a2 43 c6 24 	mov	#2,	&0x24c6	;r3 As==10
    59bc:	8f 00 34 5b 	mova	#0x05b34,r15	
    59c0:	b0 13 a2 61 	calla	#0x061a2	
    59c4:	30 12 66 9b 	push	#-25754	;#0x9b66
    59c8:	30 12 6a 9b 	push	#-25750	;#0x9b6a
    59cc:	30 12 6f 9b 	push	#-25745	;#0x9b6f
    59d0:	b0 13 68 8d 	calla	#0x08d68	
    59d4:	31 50 06 00 	add	#6,	r1	;#0x0006
    59d8:	30 12 7e 9b 	push	#-25730	;#0x9b7e
    59dc:	b0 13 68 8d 	calla	#0x08d68	
    59e0:	21 53       	incd	r1		
    59e2:	3f 40 2a 24 	mov	#9258,	r15	;#0x242a
    59e6:	b0 13 2a 56 	calla	#0x0562a	
    59ea:	30 12 66 9b 	push	#-25754	;#0x9b66
    59ee:	30 12 6a 9b 	push	#-25750	;#0x9b6a
    59f2:	30 12 6f 9b 	push	#-25745	;#0x9b6f
    59f6:	b0 13 68 8d 	calla	#0x08d68	
    59fa:	31 50 06 00 	add	#6,	r1	;#0x0006
    59fe:	3f 40 0a 00 	mov	#10,	r15	;#0x000a
    5a02:	b0 13 ce 6c 	calla	#0x06cce	
    5a06:	1a 42 8c 1c 	mov	&0x1c8c,r10	
    5a0a:	82 4a 80 1d 	mov	r10,	&0x1d80	
    5a0e:	3e 40 64 00 	mov	#100,	r14	;#0x0064
    5a12:	0f 4a       	mov	r10,	r15	
    5a14:	b0 13 4e 33 	calla	#0x0334e	
    5a18:	0f 12       	push	r15		
    5a1a:	0a 12       	push	r10		
    5a1c:	30 12 96 9b 	push	#-25706	;#0x9b96
    5a20:	b0 13 68 8d 	calla	#0x08d68	
    5a24:	31 50 06 00 	add	#6,	r1	;#0x0006
    5a28:	1f 42 8c 1c 	mov	&0x1c8c,r15	
    5a2c:	3f 50 54 1a 	add	#6740,	r15	;#0x1a54
    5a30:	cf 93 ff ff 	tst.b	-1(r15)	;0xffff(r15)
    5a34:	6f 24       	jz	$+224    	;abs 0x5b14
    5a36:	3d 40 40 00 	mov	#64,	r13	;#0x0040
    5a3a:	0e 43       	clr	r14		
    5a3c:	3f 40 82 1d 	mov	#7554,	r15	;#0x1d82
    5a40:	b0 13 44 4c 	calla	#0x04c44	
    5a44:	4d 3c       	jmp	$+156    	;abs 0x5ae0
    5a46:	bb 40 dd 02 	mov	#733,	0(r11)	;#0x02dd, 0x0000(r11)
    5a4a:	00 00 
    5a4c:	68 3c       	jmp	$+210    	;abs 0x5b1e
    5a4e:	1f 42 80 1d 	mov	&0x1d80,r15	
    5a52:	1f 53       	inc	r15		
    5a54:	82 4f 80 1d 	mov	r15,	&0x1d80	
    5a58:	3e 40 64 00 	mov	#100,	r14	;#0x0064
    5a5c:	b0 13 4e 33 	calla	#0x0334e	
    5a60:	cf 93 54 1a 	tst.b	6740(r15)	;0x1a54(r15)
    5a64:	37 20       	jnz	$+112    	;abs 0x5ad4
    5a66:	30 12 66 9b 	push	#-25754	;#0x9b66
    5a6a:	30 12 6a 9b 	push	#-25750	;#0x9b6a
    5a6e:	30 12 6f 9b 	push	#-25745	;#0x9b6f
    5a72:	b0 13 68 8d 	calla	#0x08d68	
    5a76:	31 50 06 00 	add	#6,	r1	;#0x0006
    5a7a:	12 12 8c 1c 	push	&0x1c8c	
    5a7e:	30 12 af 9b 	push	#-25681	;#0x9baf
    5a82:	b0 13 68 8d 	calla	#0x08d68	
    5a86:	21 52       	add	#4,	r1	;r2 As==10
    5a88:	3e 40 64 00 	mov	#100,	r14	;#0x0064
    5a8c:	1f 42 80 1d 	mov	&0x1d80,r15	
    5a90:	b0 13 4e 33 	calla	#0x0334e	
    5a94:	3f 53       	add	#-1,	r15	;r3 As==11
    5a96:	0e 4f       	mov	r15,	r14	
    5a98:	5e 02       	rlam	#1,	r14	
    5a9a:	5f 0a       	rlam	#3,	r15	
    5a9c:	0e 5f       	add	r15,	r14	
    5a9e:	2e 53       	incd	r14		
    5aa0:	0f 4e       	mov	r14,	r15	
    5aa2:	3f 50 5c 11 	add	#4444,	r15	;#0x115c
    5aa6:	b0 13 2a 56 	calla	#0x0562a	
    5aaa:	3f 40 0a 00 	mov	#10,	r15	;#0x000a
    5aae:	b0 13 ce 6c 	calla	#0x06cce	
    5ab2:	3e 40 64 00 	mov	#100,	r14	;#0x0064
    5ab6:	1f 42 80 1d 	mov	&0x1d80,r15	
    5aba:	b0 13 4e 33 	calla	#0x0334e	
    5abe:	3f 53       	add	#-1,	r15	;r3 As==11
    5ac0:	0e 4f       	mov	r15,	r14	
    5ac2:	5e 02       	rlam	#1,	r14	
    5ac4:	5f 0a       	rlam	#3,	r15	
    5ac6:	0e 5f       	add	r15,	r14	
    5ac8:	2e 53       	incd	r14		
    5aca:	0f 4e       	mov	r14,	r15	
    5acc:	3f 50 5c 11 	add	#4444,	r15	;#0x115c
    5ad0:	80 13 94 99 	calla	&0x09994	
    5ad4:	3f 40 82 1d 	mov	#7554,	r15	;#0x1d82
    5ad8:	b0 13 56 4c 	calla	#0x04c56	
    5adc:	92 53 8e 1d 	inc	&0x1d8e	
    5ae0:	3f 40 64 00 	mov	#100,	r15	;#0x0064
    5ae4:	1f 82 4e 11 	sub	&0x114e,r15	
    5ae8:	1f 92 8e 1d 	cmp	&0x1d8e,r15	
    5aec:	ac 2f       	jc	$-166    	;abs 0x5a46
    5aee:	30 12 66 9b 	push	#-25754	;#0x9b66
    5af2:	30 12 6a 9b 	push	#-25750	;#0x9b6a
    5af6:	30 12 6f 9b 	push	#-25745	;#0x9b6f
    5afa:	b0 13 68 8d 	calla	#0x08d68	
    5afe:	31 50 06 00 	add	#6,	r1	;#0x0006
    5b02:	12 12 8c 1c 	push	&0x1c8c	
    5b06:	30 12 e1 9b 	push	#-25631	;#0x9be1
    5b0a:	b0 13 68 8d 	calla	#0x08d68	
    5b0e:	21 52       	add	#4,	r1	;r2 As==10
    5b10:	80 13 6a 99 	calla	&0x0996a	
    5b14:	8b 43 00 00 	mov	#0,	0(r11)	;r3 As==00, 0x0000(r11)
    5b18:	7f 40 03 00 	mov.b	#3,	r15	;#0x0003
    5b1c:	09 3c       	jmp	$+20     	;abs 0x5b30
    5b1e:	5f 43       	mov.b	#1,	r15	;r3 As==01
    5b20:	07 3c       	jmp	$+16     	;abs 0x5b30
    5b22:	3f 40 82 1d 	mov	#7554,	r15	;#0x1d82
    5b26:	b0 13 68 4c 	calla	#0x04c68	
    5b2a:	0f 93       	tst	r15		
    5b2c:	90 23       	jnz	$-222    	;abs 0x5a4e
    5b2e:	f7 3f       	jmp	$-16     	;abs 0x5b1e
    5b30:	1a 16       	popm.a	#2,	r11	
    5b32:	10 01       	reta			

00005b34 <input_callback>:
    5b34:	7b 14       	pushm.a	#8,	r11	
    5b36:	04 41       	mov	r1,	r4	
    5b38:	34 50 20 00 	add	#32,	r4	;#0x0020
    5b3c:	31 50 74 ff 	add	#-140,	r1	;#0xff74
    5b40:	0a 4f       	mov	r15,	r10	
    5b42:	09 4d       	mov	r13,	r9	
    5b44:	1f 42 8c 1c 	mov	&0x1c8c,r15	
    5b48:	3f 50 54 1a 	add	#6740,	r15	;#0x1a54
    5b4c:	cf 93 ff ff 	tst.b	-1(r15)	;0xffff(r15)
    5b50:	02 24       	jz	$+6      	;abs 0x5b56
    5b52:	80 00 1c 61 	bra	#0x0611c	
    5b56:	0b 43       	clr	r11		
    5b58:	0f 4b       	mov	r11,	r15	
    5b5a:	5f 02       	rlam	#1,	r15	
    5b5c:	1f 12 8e 1c 	push	7310(r15)	;0x1c8e(r15)
    5b60:	0b 12       	push	r11		
    5b62:	30 12 f7 9b 	push	#-25609	;#0x9bf7
    5b66:	b0 13 68 8d 	calla	#0x08d68	
    5b6a:	31 50 06 00 	add	#6,	r1	;#0x0006
    5b6e:	1b 53       	inc	r11		
    5b70:	3b 90 64 00 	cmp	#100,	r11	;#0x0064
    5b74:	f1 23       	jnz	$-28     	;abs 0x5b58
    5b76:	e4 4a b8 ff 	mov.b	@r10,	-72(r4)	;0xffb8(r4)
    5b7a:	d4 4a 01 00 	mov.b	1(r10),	-71(r4)	;0x0001(r10), 0xffb9(r4)
    5b7e:	b9 ff 
    5b80:	30 12 66 9b 	push	#-25754	;#0x9b66
    5b84:	30 12 6a 9b 	push	#-25750	;#0x9b6a
    5b88:	30 12 6f 9b 	push	#-25745	;#0x9b6f
    5b8c:	b0 13 68 8d 	calla	#0x08d68	
    5b90:	31 50 06 00 	add	#6,	r1	;#0x0006
    5b94:	17 44 b8 ff 	mov	-72(r4),r7	;0xffb8(r4)
    5b98:	12 12 8c 1c 	push	&0x1c8c	
    5b9c:	07 12       	push	r7		
    5b9e:	30 12 00 9c 	push	#-25600	;#0x9c00
    5ba2:	b0 13 68 8d 	calla	#0x08d68	
    5ba6:	31 50 06 00 	add	#6,	r1	;#0x0006
    5baa:	0f 49       	mov	r9,	r15	
    5bac:	b0 13 2a 56 	calla	#0x0562a	
    5bb0:	30 12 66 9b 	push	#-25754	;#0x9b66
    5bb4:	30 12 6a 9b 	push	#-25750	;#0x9b6a
    5bb8:	30 12 6f 9b 	push	#-25745	;#0x9b6f
    5bbc:	b0 13 68 8d 	calla	#0x08d68	
    5bc0:	31 50 06 00 	add	#6,	r1	;#0x0006
    5bc4:	6f 42       	mov.b	#4,	r15	;r2 As==10
    5bc6:	b0 13 62 63 	calla	#0x06362	
    5bca:	0f 12       	push	r15		
    5bcc:	30 12 20 9c 	push	#-25568	;#0x9c20
    5bd0:	b0 13 68 8d 	calla	#0x08d68	
    5bd4:	21 52       	add	#4,	r1	;r2 As==10
    5bd6:	3f 40 0a 00 	mov	#10,	r15	;#0x000a
    5bda:	b0 13 ce 6c 	calla	#0x06cce	
    5bde:	37 53       	add	#-1,	r7	;r3 As==11
    5be0:	6f 42       	mov.b	#4,	r15	;r2 As==10
    5be2:	b0 13 62 63 	calla	#0x06362	
    5be6:	08 4f       	mov	r15,	r8	
    5be8:	0f 47       	mov	r7,	r15	
    5bea:	5f 02       	rlam	#1,	r15	
    5bec:	8f 48 8e 1c 	mov	r8,	7310(r15);0x1c8e(r15)
    5bf0:	0f 43       	clr	r15		
    5bf2:	05 43       	clr	r5		
    5bf4:	8f 93 8e 1c 	tst	7310(r15)	;0x1c8e(r15)
    5bf8:	01 24       	jz	$+4      	;abs 0x5bfc
    5bfa:	15 53       	inc	r5		
    5bfc:	2f 53       	incd	r15		
    5bfe:	3f 90 c8 00 	cmp	#200,	r15	;#0x00c8
    5c02:	f8 23       	jnz	$-14     	;abs 0x5bf4
    5c04:	08 93       	tst	r8		
    5c06:	02 20       	jnz	$+6      	;abs 0x5c0c
    5c08:	80 00 d4 5e 	bra	#0x05ed4	
    5c0c:	1c 42 58 24 	mov	&0x2458,r12	
    5c10:	1d 42 5a 24 	mov	&0x245a,r13	
    5c14:	1e 42 5c 24 	mov	&0x245c,r14	
    5c18:	1f 42 5e 24 	mov	&0x245e,r15	
    5c1c:	b0 13 98 7e 	calla	#0x07e98	
    5c20:	0a 4e       	mov	r14,	r10	
    5c22:	0b 4f       	mov	r15,	r11	
    5c24:	09 47       	mov	r7,	r9	
    5c26:	59 02       	rlam	#1,	r9	
    5c28:	57 0a       	rlam	#3,	r7	
    5c2a:	09 57       	add	r7,	r9	
    5c2c:	39 50 20 16 	add	#5664,	r9	;#0x1620
    5c30:	07 49       	mov	r9,	r7	
    5c32:	27 53       	incd	r7		
    5c34:	84 47 c0 ff 	mov	r7,	-64(r4)	;0xffc0(r4)
    5c38:	3c 40 00 24 	mov	#9216,	r12	;#0x2400
    5c3c:	3d 40 74 49 	mov	#18804,	r13	;#0x4974
    5c40:	2e 47       	mov	@r7,	r14	
    5c42:	1f 47 02 00 	mov	2(r7),	r15	;0x0002(r7)
    5c46:	b0 13 c2 82 	calla	#0x082c2	
    5c4a:	0c 4e       	mov	r14,	r12	
    5c4c:	0d 4f       	mov	r15,	r13	
    5c4e:	0e 4a       	mov	r10,	r14	
    5c50:	0f 4b       	mov	r11,	r15	
    5c52:	b0 13 26 82 	calla	#0x08226	
    5c56:	b0 13 78 7d 	calla	#0x07d78	
    5c5a:	84 4c c8 ff 	mov	r12,	-56(r4)	;0xffc8(r4)
    5c5e:	84 4d ca ff 	mov	r13,	-54(r4)	;0xffca(r4)
    5c62:	84 4e cc ff 	mov	r14,	-52(r4)	;0xffcc(r4)
    5c66:	84 4f ce ff 	mov	r15,	-50(r4)	;0xffce(r4)
    5c6a:	82 4c 58 24 	mov	r12,	&0x2458	
    5c6e:	82 4d 5a 24 	mov	r13,	&0x245a	
    5c72:	82 4e 5c 24 	mov	r14,	&0x245c	
    5c76:	82 4f 5e 24 	mov	r15,	&0x245e	
    5c7a:	1c 42 7c 24 	mov	&0x247c,r12	
    5c7e:	1d 42 7e 24 	mov	&0x247e,r13	
    5c82:	1e 42 80 24 	mov	&0x2480,r14	
    5c86:	1f 42 82 24 	mov	&0x2482,r15	
    5c8a:	b0 13 98 7e 	calla	#0x07e98	
    5c8e:	0a 4e       	mov	r14,	r10	
    5c90:	0b 4f       	mov	r15,	r11	
    5c92:	39 50 06 00 	add	#6,	r9	;#0x0006
    5c96:	84 49 ba ff 	mov	r9,	-70(r4)	;0xffba(r4)
    5c9a:	3c 40 00 24 	mov	#9216,	r12	;#0x2400
    5c9e:	3d 40 74 49 	mov	#18804,	r13	;#0x4974
    5ca2:	2e 49       	mov	@r9,	r14	
    5ca4:	1f 49 02 00 	mov	2(r9),	r15	;0x0002(r9)
    5ca8:	b0 13 c2 82 	calla	#0x082c2	
    5cac:	0c 4e       	mov	r14,	r12	
    5cae:	0d 4f       	mov	r15,	r13	
    5cb0:	0e 4a       	mov	r10,	r14	
    5cb2:	0f 4b       	mov	r11,	r15	
    5cb4:	b0 13 26 82 	calla	#0x08226	
    5cb8:	b0 13 78 7d 	calla	#0x07d78	
    5cbc:	82 4c 7c 24 	mov	r12,	&0x247c	
    5cc0:	82 4d 7e 24 	mov	r13,	&0x247e	
    5cc4:	82 4e 80 24 	mov	r14,	&0x2480	
    5cc8:	82 4f 82 24 	mov	r15,	&0x2482	
    5ccc:	92 44 c8 ff 	mov	-56(r4),&0x248c	;0xffc8(r4)
    5cd0:	8c 24 
    5cd2:	92 44 ca ff 	mov	-54(r4),&0x248e	;0xffca(r4)
    5cd6:	8e 24 
    5cd8:	92 44 cc ff 	mov	-52(r4),&0x2490	;0xffcc(r4)
    5cdc:	90 24 
    5cde:	92 44 ce ff 	mov	-50(r4),&0x2492	;0xffce(r4)
    5ce2:	92 24 
    5ce4:	82 4c b8 24 	mov	r12,	&0x24b8	
    5ce8:	82 4d ba 24 	mov	r13,	&0x24ba	
    5cec:	82 4e bc 24 	mov	r14,	&0x24bc	
    5cf0:	82 4f be 24 	mov	r15,	&0x24be	
    5cf4:	0f 48       	mov	r8,	r15	
    5cf6:	8f 10       	swpb	r15		
    5cf8:	8f 11       	sxt	r15		
    5cfa:	8f 10       	swpb	r15		
    5cfc:	8f 11       	sxt	r15		
    5cfe:	0e 48       	mov	r8,	r14	
    5d00:	b0 13 ec 86 	calla	#0x086ec	
    5d04:	3c 40 49 d1 	mov	#-11959,r12	;#0xd149
    5d08:	3d 40 ad 42 	mov	#17069,	r13	;#0x42ad
    5d0c:	b0 13 26 82 	calla	#0x08226	
    5d10:	3c 40 b8 40 	mov	#16568,	r12	;#0x40b8
    5d14:	3d 40 bb 42 	mov	#17083,	r13	;#0x42bb
    5d18:	b0 13 c0 84 	calla	#0x084c0	
    5d1c:	0c 4e       	mov	r14,	r12	
    5d1e:	0d 4f       	mov	r15,	r13	
    5d20:	3e 40 d9 77 	mov	#30681,	r14	;#0x77d9
    5d24:	3f 40 d9 3f 	mov	#16345,	r15	;#0x3fd9
    5d28:	b0 13 72 82 	calla	#0x08272	
    5d2c:	0c 4e       	mov	r14,	r12	
    5d2e:	0d 4f       	mov	r15,	r13	
    5d30:	0e 43       	clr	r14		
    5d32:	3f 40 20 41 	mov	#16672,	r15	;#0x4120
    5d36:	b0 13 b4 7a 	calla	#0x07ab4	
    5d3a:	08 4e       	mov	r14,	r8	
    5d3c:	09 4f       	mov	r15,	r9	
    5d3e:	0c 4e       	mov	r14,	r12	
    5d40:	0d 4f       	mov	r15,	r13	
    5d42:	0e 43       	clr	r14		
    5d44:	3f 40 80 3f 	mov	#16256,	r15	;#0x3f80
    5d48:	b0 13 c0 84 	calla	#0x084c0	
    5d4c:	0a 4e       	mov	r14,	r10	
    5d4e:	0b 4f       	mov	r15,	r11	
    5d50:	0c 48       	mov	r8,	r12	
    5d52:	0d 49       	mov	r9,	r13	
    5d54:	0e 43       	clr	r14		
    5d56:	3f 40 00 40 	mov	#16384,	r15	;#0x4000
    5d5a:	b0 13 c0 84 	calla	#0x084c0	
    5d5e:	06 4e       	mov	r14,	r6	
    5d60:	07 4f       	mov	r15,	r7	
    5d62:	1e 42 4e 11 	mov	&0x114e,r14	
    5d66:	0f 4e       	mov	r14,	r15	
    5d68:	8f 10       	swpb	r15		
    5d6a:	8f 11       	sxt	r15		
    5d6c:	8f 10       	swpb	r15		
    5d6e:	8f 11       	sxt	r15		
    5d70:	b0 13 ec 86 	calla	#0x086ec	
    5d74:	0c 46       	mov	r6,	r12	
    5d76:	0d 47       	mov	r7,	r13	
    5d78:	b0 13 b4 7a 	calla	#0x07ab4	
    5d7c:	0c 4e       	mov	r14,	r12	
    5d7e:	0d 4f       	mov	r15,	r13	
    5d80:	0e 4a       	mov	r10,	r14	
    5d82:	0f 4b       	mov	r11,	r15	
    5d84:	b0 13 c2 82 	calla	#0x082c2	
    5d88:	84 4e c8 ff 	mov	r14,	-56(r4)	;0xffc8(r4)
    5d8c:	84 4f ca ff 	mov	r15,	-54(r4)	;0xffca(r4)
    5d90:	3c 40 00 24 	mov	#9216,	r12	;#0x2400
    5d94:	3d 40 74 49 	mov	#18804,	r13	;#0x4974
    5d98:	b0 13 c2 82 	calla	#0x082c2	
    5d9c:	b0 13 78 7d 	calla	#0x07d78	
    5da0:	3f 15       	pushm	#4,	r15	
    5da2:	3c 40 00 24 	mov	#9216,	r12	;#0x2400
    5da6:	3d 40 74 49 	mov	#18804,	r13	;#0x4974
    5daa:	0e 4a       	mov	r10,	r14	
    5dac:	0f 4b       	mov	r11,	r15	
    5dae:	b0 13 c2 82 	calla	#0x082c2	
    5db2:	b0 13 78 7d 	calla	#0x07d78	
    5db6:	3f 15       	pushm	#4,	r15	
    5db8:	3c 40 00 24 	mov	#9216,	r12	;#0x2400
    5dbc:	3d 40 74 49 	mov	#18804,	r13	;#0x4974
    5dc0:	0e 48       	mov	r8,	r14	
    5dc2:	0f 49       	mov	r9,	r15	
    5dc4:	b0 13 c2 82 	calla	#0x082c2	
    5dc8:	b0 13 78 7d 	calla	#0x07d78	
    5dcc:	3f 15       	pushm	#4,	r15	
    5dce:	30 12 2e 9c 	push	#-25554	;#0x9c2e
    5dd2:	3c 40 54 ff 	mov	#-172,	r12	;#0xff54
    5dd6:	0c 54       	add	r4,	r12	
    5dd8:	0c 12       	push	r12		
    5dda:	b0 13 d0 8d 	calla	#0x08dd0	
    5dde:	31 50 1c 00 	add	#28,	r1	;#0x001c
    5de2:	3d 40 54 ff 	mov	#-172,	r13	;#0xff54
    5de6:	0d 54       	add	r4,	r13	
    5de8:	0d 12       	push	r13		
    5dea:	30 12 59 9c 	push	#-25511	;#0x9c59
    5dee:	b0 13 68 8d 	calla	#0x08d68	
    5df2:	21 52       	add	#4,	r1	;r2 As==10
    5df4:	0c 4a       	mov	r10,	r12	
    5df6:	0d 4b       	mov	r11,	r13	
    5df8:	1e 42 94 24 	mov	&0x2494,r14	
    5dfc:	1f 42 96 24 	mov	&0x2496,r15	
    5e00:	b0 13 26 82 	calla	#0x08226	
    5e04:	82 4e 94 24 	mov	r14,	&0x2494	
    5e08:	82 4f 96 24 	mov	r15,	&0x2496	
    5e0c:	1c 44 c8 ff 	mov	-56(r4),r12	;0xffc8(r4)
    5e10:	1d 44 ca ff 	mov	-54(r4),r13	;0xffca(r4)
    5e14:	1e 42 b4 24 	mov	&0x24b4,r14	
    5e18:	1f 42 b6 24 	mov	&0x24b6,r15	
    5e1c:	b0 13 26 82 	calla	#0x08226	
    5e20:	82 4e b4 24 	mov	r14,	&0x24b4	
    5e24:	82 4f b6 24 	mov	r15,	&0x24b6	
    5e28:	19 44 c0 ff 	mov	-64(r4),r9	;0xffc0(r4)
    5e2c:	26 49       	mov	@r9,	r6	
    5e2e:	17 49 02 00 	mov	2(r9),	r7	;0x0002(r9)
    5e32:	0c 46       	mov	r6,	r12	
    5e34:	0d 47       	mov	r7,	r13	
    5e36:	0e 4a       	mov	r10,	r14	
    5e38:	0f 4b       	mov	r11,	r15	
    5e3a:	b0 13 c2 82 	calla	#0x082c2	
    5e3e:	0c 4e       	mov	r14,	r12	
    5e40:	0d 4f       	mov	r15,	r13	
    5e42:	1e 42 98 24 	mov	&0x2498,r14	
    5e46:	1f 42 9a 24 	mov	&0x249a,r15	
    5e4a:	b0 13 26 82 	calla	#0x08226	
    5e4e:	82 4e 98 24 	mov	r14,	&0x2498	
    5e52:	82 4f 9a 24 	mov	r15,	&0x249a	
    5e56:	1c 44 ba ff 	mov	-70(r4),r12	;0xffba(r4)
    5e5a:	28 4c       	mov	@r12,	r8	
    5e5c:	19 4c 02 00 	mov	2(r12),	r9	;0x0002(r12)
    5e60:	0c 48       	mov	r8,	r12	
    5e62:	0d 49       	mov	r9,	r13	
    5e64:	0e 4a       	mov	r10,	r14	
    5e66:	0f 4b       	mov	r11,	r15	
    5e68:	b0 13 c2 82 	calla	#0x082c2	
    5e6c:	0c 4e       	mov	r14,	r12	
    5e6e:	0d 4f       	mov	r15,	r13	
    5e70:	1e 42 ac 24 	mov	&0x24ac,r14	
    5e74:	1f 42 ae 24 	mov	&0x24ae,r15	
    5e78:	b0 13 26 82 	calla	#0x08226	
    5e7c:	82 4e ac 24 	mov	r14,	&0x24ac	
    5e80:	82 4f ae 24 	mov	r15,	&0x24ae	
    5e84:	0c 46       	mov	r6,	r12	
    5e86:	0d 47       	mov	r7,	r13	
    5e88:	1e 44 c8 ff 	mov	-56(r4),r14	;0xffc8(r4)
    5e8c:	1f 44 ca ff 	mov	-54(r4),r15	;0xffca(r4)
    5e90:	b0 13 c2 82 	calla	#0x082c2	
    5e94:	0c 4e       	mov	r14,	r12	
    5e96:	0d 4f       	mov	r15,	r13	
    5e98:	1e 42 c0 24 	mov	&0x24c0,r14	
    5e9c:	1f 42 c2 24 	mov	&0x24c2,r15	
    5ea0:	b0 13 26 82 	calla	#0x08226	
    5ea4:	82 4e c0 24 	mov	r14,	&0x24c0	
    5ea8:	82 4f c2 24 	mov	r15,	&0x24c2	
    5eac:	0c 48       	mov	r8,	r12	
    5eae:	0d 49       	mov	r9,	r13	
    5eb0:	1e 44 c8 ff 	mov	-56(r4),r14	;0xffc8(r4)
    5eb4:	1f 44 ca ff 	mov	-54(r4),r15	;0xffca(r4)
    5eb8:	b0 13 c2 82 	calla	#0x082c2	
    5ebc:	0c 4e       	mov	r14,	r12	
    5ebe:	0d 4f       	mov	r15,	r13	
    5ec0:	1e 42 78 24 	mov	&0x2478,r14	
    5ec4:	1f 42 7a 24 	mov	&0x247a,r15	
    5ec8:	b0 13 26 82 	calla	#0x08226	
    5ecc:	82 4e 78 24 	mov	r14,	&0x2478	
    5ed0:	82 4f 7a 24 	mov	r15,	&0x247a	
    5ed4:	05 93       	tst	r5		
    5ed6:	01 20       	jnz	$+4      	;abs 0x5eda
    5ed8:	15 43       	mov	#1,	r5	;r3 As==01
    5eda:	08 45       	mov	r5,	r8	
    5edc:	0f 45       	mov	r5,	r15	
    5ede:	8f 10       	swpb	r15		
    5ee0:	8f 11       	sxt	r15		
    5ee2:	8f 10       	swpb	r15		
    5ee4:	8f 11       	sxt	r15		
    5ee6:	09 4f       	mov	r15,	r9	
    5ee8:	0a 4f       	mov	r15,	r10	
    5eea:	0b 4f       	mov	r15,	r11	
    5eec:	3b 15       	pushm	#4,	r11	
    5eee:	1c 42 58 24 	mov	&0x2458,r12	
    5ef2:	1d 42 5a 24 	mov	&0x245a,r13	
    5ef6:	1e 42 5c 24 	mov	&0x245c,r14	
    5efa:	1f 42 5e 24 	mov	&0x245e,r15	
    5efe:	b0 13 e0 33 	calla	#0x033e0	
    5f02:	84 4c c8 ff 	mov	r12,	-56(r4)	;0xffc8(r4)
    5f06:	84 4d ca ff 	mov	r13,	-54(r4)	;0xffca(r4)
    5f0a:	84 4e cc ff 	mov	r14,	-52(r4)	;0xffcc(r4)
    5f0e:	84 4f ce ff 	mov	r15,	-50(r4)	;0xffce(r4)
    5f12:	82 4c 8c 24 	mov	r12,	&0x248c	
    5f16:	82 4d 8e 24 	mov	r13,	&0x248e	
    5f1a:	82 4e 90 24 	mov	r14,	&0x2490	
    5f1e:	82 4f 92 24 	mov	r15,	&0x2492	
    5f22:	81 48 00 00 	mov	r8,	0(r1)	;0x0000(r1)
    5f26:	81 49 02 00 	mov	r9,	2(r1)	;0x0002(r1)
    5f2a:	81 4a 04 00 	mov	r10,	4(r1)	;0x0004(r1)
    5f2e:	81 4b 06 00 	mov	r11,	6(r1)	;0x0006(r1)
    5f32:	1c 42 7c 24 	mov	&0x247c,r12	
    5f36:	1d 42 7e 24 	mov	&0x247e,r13	
    5f3a:	1e 42 80 24 	mov	&0x2480,r14	
    5f3e:	1f 42 82 24 	mov	&0x2482,r15	
    5f42:	b0 13 e0 33 	calla	#0x033e0	
    5f46:	31 52       	add	#8,	r1	;r2 As==11
    5f48:	84 4c d0 ff 	mov	r12,	-48(r4)	;0xffd0(r4)
    5f4c:	84 4d d2 ff 	mov	r13,	-46(r4)	;0xffd2(r4)
    5f50:	84 4e d4 ff 	mov	r14,	-44(r4)	;0xffd4(r4)
    5f54:	84 4f d6 ff 	mov	r15,	-42(r4)	;0xffd6(r4)
    5f58:	82 4c b8 24 	mov	r12,	&0x24b8	
    5f5c:	82 4d ba 24 	mov	r13,	&0x24ba	
    5f60:	82 4e bc 24 	mov	r14,	&0x24bc	
    5f64:	82 4f be 24 	mov	r15,	&0x24be	
    5f68:	1a 42 94 24 	mov	&0x2494,r10	
    5f6c:	1b 42 96 24 	mov	&0x2496,r11	
    5f70:	0c 4a       	mov	r10,	r12	
    5f72:	0d 4b       	mov	r11,	r13	
    5f74:	1e 42 98 24 	mov	&0x2498,r14	
    5f78:	1f 42 9a 24 	mov	&0x249a,r15	
    5f7c:	b0 13 c0 84 	calla	#0x084c0	
    5f80:	3c 40 00 24 	mov	#9216,	r12	;#0x2400
    5f84:	3d 40 74 49 	mov	#18804,	r13	;#0x4974
    5f88:	b0 13 c2 82 	calla	#0x082c2	
    5f8c:	b0 13 78 7d 	calla	#0x07d78	
    5f90:	84 4c c0 ff 	mov	r12,	-64(r4)	;0xffc0(r4)
    5f94:	84 4d c2 ff 	mov	r13,	-62(r4)	;0xffc2(r4)
    5f98:	84 4e c4 ff 	mov	r14,	-60(r4)	;0xffc4(r4)
    5f9c:	84 4f c6 ff 	mov	r15,	-58(r4)	;0xffc6(r4)
    5fa0:	82 4c 70 24 	mov	r12,	&0x2470	
    5fa4:	82 4d 72 24 	mov	r13,	&0x2472	
    5fa8:	82 4e 74 24 	mov	r14,	&0x2474	
    5fac:	82 4f 76 24 	mov	r15,	&0x2476	
    5fb0:	0c 4a       	mov	r10,	r12	
    5fb2:	0d 4b       	mov	r11,	r13	
    5fb4:	1e 42 ac 24 	mov	&0x24ac,r14	
    5fb8:	1f 42 ae 24 	mov	&0x24ae,r15	
    5fbc:	b0 13 c0 84 	calla	#0x084c0	
    5fc0:	3c 40 00 24 	mov	#9216,	r12	;#0x2400
    5fc4:	3d 40 74 49 	mov	#18804,	r13	;#0x4974
    5fc8:	b0 13 c2 82 	calla	#0x082c2	
    5fcc:	b0 13 78 7d 	calla	#0x07d78	
    5fd0:	08 4c       	mov	r12,	r8	
    5fd2:	09 4d       	mov	r13,	r9	
    5fd4:	0a 4e       	mov	r14,	r10	
    5fd6:	0b 4f       	mov	r15,	r11	
    5fd8:	82 4c 50 24 	mov	r12,	&0x2450	
    5fdc:	82 4d 52 24 	mov	r13,	&0x2452	
    5fe0:	82 4e 54 24 	mov	r14,	&0x2454	
    5fe4:	82 4f 56 24 	mov	r15,	&0x2456	
    5fe8:	16 42 b4 24 	mov	&0x24b4,r6	
    5fec:	17 42 b6 24 	mov	&0x24b6,r7	
    5ff0:	0c 46       	mov	r6,	r12	
    5ff2:	0d 47       	mov	r7,	r13	
    5ff4:	1e 42 c0 24 	mov	&0x24c0,r14	
    5ff8:	1f 42 c2 24 	mov	&0x24c2,r15	
    5ffc:	b0 13 c0 84 	calla	#0x084c0	
    6000:	3c 40 00 24 	mov	#9216,	r12	;#0x2400
    6004:	3d 40 74 49 	mov	#18804,	r13	;#0x4974
    6008:	b0 13 c2 82 	calla	#0x082c2	
    600c:	b0 13 78 7d 	calla	#0x07d78	
    6010:	84 4c d8 ff 	mov	r12,	-40(r4)	;0xffd8(r4)
    6014:	84 4d da ff 	mov	r13,	-38(r4)	;0xffda(r4)
    6018:	84 4e dc ff 	mov	r14,	-36(r4)	;0xffdc(r4)
    601c:	84 4f de ff 	mov	r15,	-34(r4)	;0xffde(r4)
    6020:	82 4c 68 24 	mov	r12,	&0x2468	
    6024:	82 4d 6a 24 	mov	r13,	&0x246a	
    6028:	82 4e 6c 24 	mov	r14,	&0x246c	
    602c:	82 4f 6e 24 	mov	r15,	&0x246e	
    6030:	0c 46       	mov	r6,	r12	
    6032:	0d 47       	mov	r7,	r13	
    6034:	1e 42 78 24 	mov	&0x2478,r14	
    6038:	1f 42 7a 24 	mov	&0x247a,r15	
    603c:	b0 13 c0 84 	calla	#0x084c0	
    6040:	3c 40 00 24 	mov	#9216,	r12	;#0x2400
    6044:	3d 40 74 49 	mov	#18804,	r13	;#0x4974
    6048:	b0 13 c2 82 	calla	#0x082c2	
    604c:	b0 13 78 7d 	calla	#0x07d78	
    6050:	82 4c a4 24 	mov	r12,	&0x24a4	
    6054:	82 4d a6 24 	mov	r13,	&0x24a6	
    6058:	82 4e a8 24 	mov	r14,	&0x24a8	
    605c:	82 4f aa 24 	mov	r15,	&0x24aa	
    6060:	16 42 8c 1c 	mov	&0x1c8c,r6	
    6064:	36 53       	add	#-1,	r6	;r3 As==11
    6066:	05 12       	push	r5		
    6068:	3f 15       	pushm	#4,	r15	
    606a:	1c 44 d8 ff 	mov	-40(r4),r12	;0xffd8(r4)
    606e:	1d 44 da ff 	mov	-38(r4),r13	;0xffda(r4)
    6072:	1e 44 dc ff 	mov	-36(r4),r14	;0xffdc(r4)
    6076:	1f 44 de ff 	mov	-34(r4),r15	;0xffde(r4)
    607a:	3f 15       	pushm	#4,	r15	
    607c:	3b 15       	pushm	#4,	r11	
    607e:	1c 44 c0 ff 	mov	-64(r4),r12	;0xffc0(r4)
    6082:	1d 44 c2 ff 	mov	-62(r4),r13	;0xffc2(r4)
    6086:	1e 44 c4 ff 	mov	-60(r4),r14	;0xffc4(r4)
    608a:	1f 44 c6 ff 	mov	-58(r4),r15	;0xffc6(r4)
    608e:	3f 15       	pushm	#4,	r15	
    6090:	1c 44 d0 ff 	mov	-48(r4),r12	;0xffd0(r4)
    6094:	1d 44 d2 ff 	mov	-46(r4),r13	;0xffd2(r4)
    6098:	1e 44 d4 ff 	mov	-44(r4),r14	;0xffd4(r4)
    609c:	1f 44 d6 ff 	mov	-42(r4),r15	;0xffd6(r4)
    60a0:	3f 15       	pushm	#4,	r15	
    60a2:	1c 44 c8 ff 	mov	-56(r4),r12	;0xffc8(r4)
    60a6:	1d 44 ca ff 	mov	-54(r4),r13	;0xffca(r4)
    60aa:	1e 44 cc ff 	mov	-52(r4),r14	;0xffcc(r4)
    60ae:	1f 44 ce ff 	mov	-50(r4),r15	;0xffce(r4)
    60b2:	3f 15       	pushm	#4,	r15	
    60b4:	0a 46       	mov	r6,	r10	
    60b6:	5a 02       	rlam	#1,	r10	
    60b8:	0b 46       	mov	r6,	r11	
    60ba:	5b 0a       	rlam	#3,	r11	
    60bc:	0a 5b       	add	r11,	r10	
    60be:	3a 50 20 16 	add	#5664,	r10	;#0x1620
    60c2:	3c 40 00 24 	mov	#9216,	r12	;#0x2400
    60c6:	3d 40 74 49 	mov	#18804,	r13	;#0x4974
    60ca:	1e 4a 06 00 	mov	6(r10),	r14	;0x0006(r10)
    60ce:	1f 4a 08 00 	mov	8(r10),	r15	;0x0008(r10)
    60d2:	b0 13 c2 82 	calla	#0x082c2	
    60d6:	b0 13 78 7d 	calla	#0x07d78	
    60da:	3f 15       	pushm	#4,	r15	
    60dc:	3c 40 00 24 	mov	#9216,	r12	;#0x2400
    60e0:	3d 40 74 49 	mov	#18804,	r13	;#0x4974
    60e4:	1e 4a 02 00 	mov	2(r10),	r14	;0x0002(r10)
    60e8:	1f 4a 04 00 	mov	4(r10),	r15	;0x0004(r10)
    60ec:	b0 13 c2 82 	calla	#0x082c2	
    60f0:	b0 13 78 7d 	calla	#0x07d78	
    60f4:	3f 15       	pushm	#4,	r15	
    60f6:	30 12 6c 9c 	push	#-25492	;#0x9c6c
    60fa:	3d 40 54 ff 	mov	#-172,	r13	;#0xff54
    60fe:	0d 54       	add	r4,	r13	
    6100:	0d 12       	push	r13		
    6102:	b0 13 d0 8d 	calla	#0x08dd0	
    6106:	31 50 46 00 	add	#70,	r1	;#0x0046
    610a:	3e 40 54 ff 	mov	#-172,	r14	;#0xff54
    610e:	0e 54       	add	r4,	r14	
    6110:	0e 12       	push	r14		
    6112:	30 12 97 9c 	push	#-25449	;#0x9c97
    6116:	b0 13 68 8d 	calla	#0x08d68	
    611a:	21 52       	add	#4,	r1	;r2 As==10
    611c:	31 50 8c 00 	add	#140,	r1	;#0x008c
    6120:	74 16       	popm.a	#8,	r11	
    6122:	10 01       	reta			

00006124 <init>:
    6124:	cf 03       	clra	r15		
    6126:	60 0f 90 1d 	mova	r15,	&0x01d90
    612a:	10 01       	reta			

0000612c <output>:
    612c:	0b 14       	pushm.a	#1,	r11	
    612e:	0b 4f       	mov	r15,	r11	
    6130:	b0 13 d4 62 	calla	#0x062d4	
    6134:	1e 42 c6 24 	mov	&0x24c6,r14	
    6138:	1f 42 c4 24 	mov	&0x24c4,r15	
    613c:	b0 13 e6 62 	calla	#0x062e6	
    6140:	0b 93       	tst	r11		
    6142:	02 24       	jz	$+6      	;abs 0x6148
    6144:	0e 4b       	mov	r11,	r14	
    6146:	02 3c       	jmp	$+6      	;abs 0x614c
    6148:	3e 40 7e 99 	mov	#-26242,r14	;#0x997e
    614c:	7f 40 0d 00 	mov.b	#13,	r15	;#0x000d
    6150:	b0 13 6c 63 	calla	#0x0636c	
    6154:	3e 40 2a 24 	mov	#9258,	r14	;#0x242a
    6158:	7f 40 0c 00 	mov.b	#12,	r15	;#0x000c
    615c:	b0 13 6c 63 	calla	#0x0636c	
    6160:	0e 43       	clr	r14		
    6162:	cf 03       	clra	r15		
    6164:	80 13 5e 99 	calla	&0x0995e	
    6168:	5f 43       	mov.b	#1,	r15	;r3 As==01
    616a:	0b 16       	popm.a	#1,	r11	
    616c:	10 01       	reta			

0000616e <input>:
    616e:	3b 14       	pushm.a	#4,	r11	
    6170:	2b 00 90 1d 	mova	&0x01d90,r11	
    6174:	db 03       	tsta	r11		
    6176:	13 24       	jz	$+40     	;abs 0x619e
    6178:	7f 40 0d 00 	mov.b	#13,	r15	;#0x000d
    617c:	b0 13 80 63 	calla	#0x06380	
    6180:	08 4f       	mov	r15,	r8	
    6182:	7f 40 0c 00 	mov.b	#12,	r15	;#0x000c
    6186:	b0 13 80 63 	calla	#0x06380	
    618a:	09 4f       	mov	r15,	r9	
    618c:	b0 13 0e 62 	calla	#0x0620e	
    6190:	0a 4f       	mov	r15,	r10	
    6192:	b0 13 1e 62 	calla	#0x0621e	
    6196:	0c 48       	mov	r8,	r12	
    6198:	0d 49       	mov	r9,	r13	
    619a:	0e 4a       	mov	r10,	r14	
    619c:	4b 13       	calla	r11		
    619e:	38 16       	popm.a	#4,	r11	
    61a0:	10 01       	reta			

000061a2 <nullnet_set_input_callback>:
    61a2:	60 0f 90 1d 	mova	r15,	&0x01d90
    61a6:	10 01       	reta			

000061a8 <init>:
    61a8:	10 01       	reta			

000061aa <root_set_prefix>:
    61aa:	10 01       	reta			

000061ac <root_start>:
    61ac:	0f 43       	clr	r15		
    61ae:	10 01       	reta			

000061b0 <node_is_root>:
    61b0:	0f 43       	clr	r15		
    61b2:	10 01       	reta			

000061b4 <get_root_ipaddr>:
    61b4:	0f 43       	clr	r15		
    61b6:	10 01       	reta			

000061b8 <get_sr_node_ipaddr>:
    61b8:	0f 43       	clr	r15		
    61ba:	10 01       	reta			

000061bc <leave_network>:
    61bc:	10 01       	reta			

000061be <node_has_joined>:
    61be:	1f 43       	mov	#1,	r15	;r3 As==01
    61c0:	10 01       	reta			

000061c2 <node_is_reachable>:
    61c2:	1f 43       	mov	#1,	r15	;r3 As==01
    61c4:	10 01       	reta			

000061c6 <global_repair>:
    61c6:	10 01       	reta			

000061c8 <local_repair>:
    61c8:	10 01       	reta			

000061ca <ext_header_remove>:
    61ca:	5f 43       	mov.b	#1,	r15	;r3 As==01
    61cc:	10 01       	reta			

000061ce <ext_header_update>:
    61ce:	1f 43       	mov	#1,	r15	;r3 As==01
    61d0:	10 01       	reta			

000061d2 <ext_header_hbh_update>:
    61d2:	1f 43       	mov	#1,	r15	;r3 As==01
    61d4:	10 01       	reta			

000061d6 <ext_header_srh_update>:
    61d6:	0f 43       	clr	r15		
    61d8:	10 01       	reta			

000061da <ext_header_srh_get_next_hop>:
    61da:	0f 43       	clr	r15		
    61dc:	10 01       	reta			

000061de <link_callback>:
    61de:	10 01       	reta			

000061e0 <neighbor_state_changed>:
    61e0:	10 01       	reta			

000061e2 <drop_route>:
    61e2:	10 01       	reta			

000061e4 <is_in_leaf_mode>:
    61e4:	4f 43       	clr.b	r15		
    61e6:	10 01       	reta			

000061e8 <packetbuf_hdrreduce>:
    61e8:	1e 42 96 1d 	mov	&0x1d96,r14	
    61ec:	0e 9f       	cmp	r15,	r14	
    61ee:	07 28       	jnc	$+16     	;abs 0x61fe
    61f0:	82 5f 94 1d 	add	r15,	&0x1d94	
    61f4:	0e 8f       	sub	r15,	r14	
    61f6:	82 4e 96 1d 	mov	r14,	&0x1d96	
    61fa:	1f 43       	mov	#1,	r15	;r3 As==01
    61fc:	10 01       	reta			
    61fe:	0f 43       	clr	r15		
    6200:	10 01       	reta			

00006202 <packetbuf_set_datalen>:
    6202:	82 4f 96 1d 	mov	r15,	&0x1d96	
    6206:	10 01       	reta			

00006208 <packetbuf_hdrptr>:
    6208:	3f 40 98 1d 	mov	#7576,	r15	;#0x1d98
    620c:	10 01       	reta			

0000620e <packetbuf_datalen>:
    620e:	1f 42 96 1d 	mov	&0x1d96,r15	
    6212:	10 01       	reta			

00006214 <packetbuf_hdrlen>:
    6214:	5f 42 f0 23 	mov.b	&0x23f0,r15	
    6218:	5f 52 94 1d 	add.b	&0x1d94,r15	
    621c:	10 01       	reta			

0000621e <packetbuf_dataptr>:
    621e:	b0 13 14 62 	calla	#0x06214	
    6222:	4f 4f       	mov.b	r15,	r15	
    6224:	3f 50 98 1d 	add	#7576,	r15	;#0x1d98
    6228:	10 01       	reta			

0000622a <packetbuf_copyto>:
    622a:	3b 14       	pushm.a	#4,	r11	
    622c:	08 4f       	mov	r15,	r8	
    622e:	5b 42 f0 23 	mov.b	&0x23f0,r11	
    6232:	19 42 96 1d 	mov	&0x1d96,r9	
    6236:	0a 4b       	mov	r11,	r10	
    6238:	0a 59       	add	r9,	r10	
    623a:	3a 90 81 00 	cmp	#129,	r10	;#0x0081
    623e:	0f 2c       	jc	$+32     	;abs 0x625e
    6240:	0d 4b       	mov	r11,	r13	
    6242:	3e 40 98 1d 	mov	#7576,	r14	;#0x1d98
    6246:	b0 13 2a 97 	calla	#0x0972a	
    624a:	b0 13 1e 62 	calla	#0x0621e	
    624e:	0d 49       	mov	r9,	r13	
    6250:	0e 4f       	mov	r15,	r14	
    6252:	0f 48       	mov	r8,	r15	
    6254:	0f 5b       	add	r11,	r15	
    6256:	b0 13 2a 97 	calla	#0x0972a	
    625a:	0f 4a       	mov	r10,	r15	
    625c:	01 3c       	jmp	$+4      	;abs 0x6260
    625e:	0f 43       	clr	r15		
    6260:	38 16       	popm.a	#4,	r11	
    6262:	10 01       	reta			

00006264 <packetbuf_totlen>:
    6264:	b0 13 14 62 	calla	#0x06214	
    6268:	4f 4f       	mov.b	r15,	r15	
    626a:	1f 52 96 1d 	add	&0x1d96,r15	
    626e:	10 01       	reta			

00006270 <packetbuf_hdralloc>:
    6270:	0b 14       	pushm.a	#1,	r11	
    6272:	0b 4f       	mov	r15,	r11	
    6274:	b0 13 64 62 	calla	#0x06264	
    6278:	0e 4f       	mov	r15,	r14	
    627a:	0e 5b       	add	r11,	r14	
    627c:	3e 90 81 00 	cmp	#129,	r14	;#0x0081
    6280:	12 2c       	jc	$+38     	;abs 0x62a6
    6282:	0e 4f       	mov	r15,	r14	
    6284:	3e 53       	add	#-1,	r14	;r3 As==11
    6286:	0f 4b       	mov	r11,	r15	
    6288:	3f 50 98 1d 	add	#7576,	r15	;#0x1d98
    628c:	06 3c       	jmp	$+14     	;abs 0x629a
    628e:	0d 4f       	mov	r15,	r13	
    6290:	0d 5e       	add	r14,	r13	
    6292:	dd 4e 98 1d 	mov.b	7576(r14),0(r13)	;0x1d98(r14), 0x0000(r13)
    6296:	00 00 
    6298:	3e 53       	add	#-1,	r14	;r3 As==11
    629a:	0e 93       	tst	r14		
    629c:	f8 37       	jge	$-14     	;abs 0x628e
    629e:	c2 5b f0 23 	add.b	r11,	&0x23f0	
    62a2:	1f 43       	mov	#1,	r15	;r3 As==01
    62a4:	01 3c       	jmp	$+4      	;abs 0x62a8
    62a6:	0f 43       	clr	r15		
    62a8:	0b 16       	popm.a	#1,	r11	
    62aa:	10 01       	reta			

000062ac <packetbuf_attr_clear>:
    62ac:	3d 40 18 00 	mov	#24,	r13	;#0x0018
    62b0:	0e 43       	clr	r14		
    62b2:	3f 40 d8 24 	mov	#9432,	r15	;#0x24d8
    62b6:	b0 13 12 98 	calla	#0x09812	
    62ba:	3e 40 7e 99 	mov	#-26242,r14	;#0x997e
    62be:	3f 40 c8 24 	mov	#9416,	r15	;#0x24c8
    62c2:	b0 13 72 55 	calla	#0x05572	
    62c6:	3e 40 7e 99 	mov	#-26242,r14	;#0x997e
    62ca:	3f 40 d0 24 	mov	#9424,	r15	;#0x24d0
    62ce:	b0 13 72 55 	calla	#0x05572	
    62d2:	10 01       	reta			

000062d4 <packetbuf_clear>:
    62d4:	82 43 94 1d 	mov	#0,	&0x1d94	;r3 As==00
    62d8:	82 43 96 1d 	mov	#0,	&0x1d96	;r3 As==00
    62dc:	c2 43 f0 23 	mov.b	#0,	&0x23f0	;r3 As==00
    62e0:	b0 13 ac 62 	calla	#0x062ac	
    62e4:	10 01       	reta			

000062e6 <packetbuf_copyfrom>:
    62e6:	1b 14       	pushm.a	#2,	r11	
    62e8:	0a 4f       	mov	r15,	r10	
    62ea:	0b 4e       	mov	r14,	r11	
    62ec:	b0 13 d4 62 	calla	#0x062d4	
    62f0:	3b 90 81 00 	cmp	#129,	r11	;#0x0081
    62f4:	02 28       	jnc	$+6      	;abs 0x62fa
    62f6:	3b 40 80 00 	mov	#128,	r11	;#0x0080
    62fa:	0d 4b       	mov	r11,	r13	
    62fc:	0e 4a       	mov	r10,	r14	
    62fe:	3f 40 98 1d 	mov	#7576,	r15	;#0x1d98
    6302:	b0 13 2a 97 	calla	#0x0972a	
    6306:	82 4b 96 1d 	mov	r11,	&0x1d96	
    630a:	0f 4b       	mov	r11,	r15	
    630c:	1a 16       	popm.a	#2,	r11	
    630e:	10 01       	reta			

00006310 <packetbuf_attr_copyto>:
    6310:	0b 14       	pushm.a	#1,	r11	
    6312:	0b 4e       	mov	r14,	r11	
    6314:	3d 40 18 00 	mov	#24,	r13	;#0x0018
    6318:	3e 40 d8 24 	mov	#9432,	r14	;#0x24d8
    631c:	b0 13 2a 97 	calla	#0x0972a	
    6320:	3d 40 10 00 	mov	#16,	r13	;#0x0010
    6324:	3e 40 c8 24 	mov	#9416,	r14	;#0x24c8
    6328:	0f 4b       	mov	r11,	r15	
    632a:	b0 13 2a 97 	calla	#0x0972a	
    632e:	0b 16       	popm.a	#1,	r11	
    6330:	10 01       	reta			

00006332 <packetbuf_attr_copyfrom>:
    6332:	0b 14       	pushm.a	#1,	r11	
    6334:	0b 4e       	mov	r14,	r11	
    6336:	3d 40 18 00 	mov	#24,	r13	;#0x0018
    633a:	0e 4f       	mov	r15,	r14	
    633c:	3f 40 d8 24 	mov	#9432,	r15	;#0x24d8
    6340:	b0 13 2a 97 	calla	#0x0972a	
    6344:	3d 40 10 00 	mov	#16,	r13	;#0x0010
    6348:	0e 4b       	mov	r11,	r14	
    634a:	3f 40 c8 24 	mov	#9416,	r15	;#0x24c8
    634e:	b0 13 2a 97 	calla	#0x0972a	
    6352:	0b 16       	popm.a	#1,	r11	
    6354:	10 01       	reta			

00006356 <packetbuf_set_attr>:
    6356:	4f 4f       	mov.b	r15,	r15	
    6358:	5f 02       	rlam	#1,	r15	
    635a:	8f 4e d8 24 	mov	r14,	9432(r15);0x24d8(r15)
    635e:	1f 43       	mov	#1,	r15	;r3 As==01
    6360:	10 01       	reta			

00006362 <packetbuf_attr>:
    6362:	4f 4f       	mov.b	r15,	r15	
    6364:	5f 02       	rlam	#1,	r15	
    6366:	1f 4f d8 24 	mov	9432(r15),r15	;0x24d8(r15)
    636a:	10 01       	reta			

0000636c <packetbuf_set_addr>:
    636c:	4f 4f       	mov.b	r15,	r15	
    636e:	3f 50 f4 ff 	add	#-12,	r15	;#0xfff4
    6372:	5f 0a       	rlam	#3,	r15	
    6374:	3f 50 c8 24 	add	#9416,	r15	;#0x24c8
    6378:	b0 13 72 55 	calla	#0x05572	
    637c:	1f 43       	mov	#1,	r15	;r3 As==01
    637e:	10 01       	reta			

00006380 <packetbuf_addr>:
    6380:	4f 4f       	mov.b	r15,	r15	
    6382:	3f 50 f4 ff 	add	#-12,	r15	;#0xfff4
    6386:	5f 0a       	rlam	#3,	r15	
    6388:	3f 50 c8 24 	add	#9416,	r15	;#0x24c8
    638c:	10 01       	reta			

0000638e <packetbuf_holds_broadcast>:
    638e:	3e 40 7e 99 	mov	#-26242,r14	;#0x997e
    6392:	3f 40 d0 24 	mov	#9424,	r15	;#0x24d0
    6396:	b0 13 7a 55 	calla	#0x0557a	
    639a:	10 01       	reta			

0000639c <platform_init_stage_one>:
    639c:	b0 13 04 59 	calla	#0x05904	
    63a0:	b0 13 48 55 	calla	#0x05548	
    63a4:	7f 40 10 00 	mov.b	#16,	r15	;#0x0010
    63a8:	b0 13 4e 55 	calla	#0x0554e	
    63ac:	10 01       	reta			

000063ae <platform_init_stage_two>:
    63ae:	31 82       	sub	#8,	r1	;r2 As==11
    63b0:	3e 40 64 00 	mov	#100,	r14	;#0x0064
    63b4:	0f 43       	clr	r15		
    63b6:	b0 13 7a 44 	calla	#0x0447a	
    63ba:	3e 40 45 00 	mov	#69,	r14	;#0x0045
    63be:	0f 43       	clr	r15		
    63c0:	b0 13 02 6d 	calla	#0x06d02	
    63c4:	b0 13 e4 6d 	calla	#0x06de4	
    63c8:	7f 40 10 00 	mov.b	#16,	r15	;#0x0010
    63cc:	b0 13 60 55 	calla	#0x05560	
    63d0:	b0 13 40 59 	calla	#0x05940	
    63d4:	5f 42 f1 24 	mov.b	&0x24f1,r15	
    63d8:	5f d2 f0 24 	bis.b	&0x24f0,r15	
    63dc:	5f d2 f2 24 	bis.b	&0x24f2,r15	
    63e0:	5f d2 f3 24 	bis.b	&0x24f3,r15	
    63e4:	5f d2 f4 24 	bis.b	&0x24f4,r15	
    63e8:	5f d2 f5 24 	bis.b	&0x24f5,r15	
    63ec:	5f d2 f6 24 	bis.b	&0x24f6,r15	
    63f0:	5f d2 f7 24 	bis.b	&0x24f7,r15	
    63f4:	4f 93       	tst.b	r15		
    63f6:	16 20       	jnz	$+46     	;abs 0x6424
    63f8:	f2 40 c1 ff 	mov.b	#-63,	&0x24f0	;#0xffc1
    63fc:	f0 24 
    63fe:	f2 40 0c 00 	mov.b	#12,	&0x24f1	;#0x000c
    6402:	f1 24 
    6404:	c2 43 f2 24 	mov.b	#0,	&0x24f2	;r3 As==00
    6408:	c2 43 f3 24 	mov.b	#0,	&0x24f3	;r3 As==00
    640c:	c2 43 f4 24 	mov.b	#0,	&0x24f4	;r3 As==00
    6410:	c2 43 f5 24 	mov.b	#0,	&0x24f5	;r3 As==00
    6414:	1f 42 8c 1c 	mov	&0x1c8c,r15	
    6418:	0e 4f       	mov	r15,	r14	
    641a:	8e 10       	swpb	r14		
    641c:	c2 4e f6 24 	mov.b	r14,	&0x24f6	
    6420:	c2 4f f7 24 	mov.b	r15,	&0x24f7	
    6424:	5e 42 f6 24 	mov.b	&0x24f6,r14	
    6428:	5f 42 f7 24 	mov.b	&0x24f7,r15	
    642c:	0f 5e       	add	r14,	r15	
    642e:	b0 13 7e 68 	calla	#0x0687e	
    6432:	3d 42       	mov	#8,	r13	;r2 As==11
    6434:	0e 43       	clr	r14		
    6436:	0f 41       	mov	r1,	r15	
    6438:	b0 13 12 98 	calla	#0x09812	
    643c:	1f 42 8c 1c 	mov	&0x1c8c,r15	
    6440:	0f 93       	tst	r15		
    6442:	0b 20       	jnz	$+24     	;abs 0x645a
    6444:	0e 41       	mov	r1,	r14	
    6446:	3f 42       	mov	#8,	r15	;r2 As==11
    6448:	04 3c       	jmp	$+10     	;abs 0x6452
    644a:	de 4f f0 24 	mov.b	9456(r15),0(r14)	;0x24f0(r15), 0x0000(r14)
    644e:	00 00 
    6450:	1e 53       	inc	r14		
    6452:	3f 53       	add	#-1,	r15	;r3 As==11
    6454:	3f 93       	cmp	#-1,	r15	;r3 As==11
    6456:	f9 23       	jnz	$-12     	;abs 0x644a
    6458:	05 3c       	jmp	$+12     	;abs 0x6464
    645a:	c1 4f 00 00 	mov.b	r15,	0(r1)	;0x0000(r1)
    645e:	8f 10       	swpb	r15		
    6460:	c1 4f 01 00 	mov.b	r15,	1(r1)	;0x0001(r1)
    6464:	0f 41       	mov	r1,	r15	
    6466:	b0 13 8c 55 	calla	#0x0558c	
    646a:	b0 13 42 43 	calla	#0x04342	
    646e:	1e 43       	mov	#1,	r14	;r3 As==01
    6470:	3f 40 81 00 	mov	#129,	r15	;#0x0081
    6474:	80 13 fa 98 	calla	&0x098fa	
    6478:	7f 40 70 00 	mov.b	#112,	r15	;#0x0070
    647c:	b0 13 60 55 	calla	#0x05560	
    6480:	31 52       	add	#8,	r1	;r2 As==11
    6482:	10 01       	reta			

00006484 <platform_init_stage_three>:
    6484:	0b 14       	pushm.a	#1,	r11	
    6486:	31 82       	sub	#8,	r1	;r2 As==11
    6488:	b0 13 9e 44 	calla	#0x0449e	
    648c:	5b 42 2a 24 	mov.b	&0x242a,r11	
    6490:	8b 10       	swpb	r11		
    6492:	5f 42 2b 24 	mov.b	&0x242b,r15	
    6496:	0b 5f       	add	r15,	r11	
    6498:	3d 42       	mov	#8,	r13	;r2 As==11
    649a:	0e 43       	clr	r14		
    649c:	0f 41       	mov	r1,	r15	
    649e:	b0 13 12 98 	calla	#0x09812	
    64a2:	3e 40 2a 24 	mov	#9258,	r14	;#0x242a
    64a6:	0f 41       	mov	r1,	r15	
    64a8:	b0 13 72 55 	calla	#0x05572	
    64ac:	0d 41       	mov	r1,	r13	
    64ae:	0e 4b       	mov	r11,	r14	
    64b0:	3f 40 cd ab 	mov	#-21555,r15	;#0xabcd
    64b4:	b0 13 d0 3f 	calla	#0x03fd0	
    64b8:	b2 90 03 00 	cmp	#3,	&0x114a	;#0x0003
    64bc:	4a 11 
    64be:	11 38       	jl	$+36     	;abs 0x64e2
    64c0:	30 12 cc 9c 	push	#-25396	;#0x9ccc
    64c4:	30 12 cf 9c 	push	#-25393	;#0x9ccf
    64c8:	30 12 d4 9c 	push	#-25388	;#0x9cd4
    64cc:	b0 13 68 8d 	calla	#0x08d68	
    64d0:	31 50 06 00 	add	#6,	r1	;#0x0006
    64d4:	30 12 d3 ff 	push	#-45		;#0xffd3
    64d8:	30 12 e3 9c 	push	#-25373	;#0x9ce3
    64dc:	b0 13 68 8d 	calla	#0x08d68	
    64e0:	21 52       	add	#4,	r1	;r2 As==10
    64e2:	3d 40 00 0f 	mov	#3840,	r13	;#0x0f00
    64e6:	0e 43       	clr	r14		
    64e8:	3f 40 18 1e 	mov	#7704,	r15	;#0x1e18
    64ec:	b0 13 4a 6b 	calla	#0x06b4a	
    64f0:	31 52       	add	#8,	r1	;r2 As==11
    64f2:	0b 16       	popm.a	#1,	r11	
    64f4:	10 01       	reta			

000064f6 <platform_idle>:
    64f6:	0b 14       	pushm.a	#1,	r11	
    64f8:	b0 13 8c 58 	calla	#0x0588c	
    64fc:	0b 4f       	mov	r15,	r11	
    64fe:	b0 13 f8 66 	calla	#0x066f8	
    6502:	0f 93       	tst	r15		
    6504:	02 24       	jz	$+6      	;abs 0x650a
    6506:	02 db       	bis	r11,	r2	
    6508:	1e 3c       	jmp	$+62     	;abs 0x6546
    650a:	b0 13 de 6c 	calla	#0x06cde	
    650e:	4f 93       	tst.b	r15		
    6510:	fa 23       	jnz	$-10     	;abs 0x6506
    6512:	3f 40 18 1e 	mov	#7704,	r15	;#0x1e18
    6516:	b0 13 66 6b 	calla	#0x06b66	
    651a:	0f 93       	tst	r15		
    651c:	08 24       	jz	$+18     	;abs 0x652e
    651e:	b0 13 64 6d 	calla	#0x06d64	
    6522:	3f 40 18 1e 	mov	#7704,	r15	;#0x1e18
    6526:	b0 13 90 6b 	calla	#0x06b90	
    652a:	b0 13 96 58 	calla	#0x05896	
    652e:	b0 13 76 6d 	calla	#0x06d76	
    6532:	82 93 32 24 	tst	&0x2432	
    6536:	03 24       	jz	$+8      	;abs 0x653e
    6538:	32 d0 18 00 	bis	#24,	r2	;#0x0018
    653c:	02 3c       	jmp	$+6      	;abs 0x6542
    653e:	32 d0 d8 00 	bis	#216,	r2	;#0x00d8
    6542:	b0 13 50 6d 	calla	#0x06d50	
    6546:	0b 16       	popm.a	#1,	r11	
    6548:	10 01       	reta			

0000654a <call_process>:
    654a:	1b 14       	pushm.a	#2,	r11	
    654c:	0b 4f       	mov	r15,	r11	
    654e:	4a 4e       	mov.b	r14,	r10	
    6550:	df b3 0a 00 	bit.b	#1,	10(r15)	;r3 As==01, 0x000a(r15)
    6554:	18 24       	jz	$+50     	;abs 0x6586
    6556:	3c 0f 04 00 	mova	4(r15),	r12	;0x0004(r15)
    655a:	dc 03       	tsta	r12		
    655c:	14 24       	jz	$+42     	;abs 0x6586
    655e:	82 4f 20 1e 	mov	r15,	&0x1e20	
    6562:	ef 43 0a 00 	mov.b	#2,	10(r15)	;r3 As==10, 0x000a(r15)
    6566:	3f 52       	add	#8,	r15	;r2 As==11
    6568:	4c 13       	calla	r12		
    656a:	8f 11       	sxt	r15		
    656c:	2f 83       	decd	r15		
    656e:	2f 93       	cmp	#2,	r15	;r3 As==10
    6570:	03 28       	jnc	$+8      	;abs 0x6578
    6572:	7a 90 83 ff 	cmp.b	#-125,	r10	;#0xff83
    6576:	05 20       	jnz	$+12     	;abs 0x6582
    6578:	0e 4b       	mov	r11,	r14	
    657a:	0f 4b       	mov	r11,	r15	
    657c:	b0 13 8a 65 	calla	#0x0658a	
    6580:	02 3c       	jmp	$+6      	;abs 0x6586
    6582:	db 43 0a 00 	mov.b	#1,	10(r11)	;r3 As==01, 0x000a(r11)
    6586:	1a 16       	popm.a	#2,	r11	
    6588:	10 01       	reta			

0000658a <exit_process>:
    658a:	3b 14       	pushm.a	#4,	r11	
    658c:	0b 4f       	mov	r15,	r11	
    658e:	08 4e       	mov	r14,	r8	
    6590:	19 42 20 1e 	mov	&0x1e20,r9	
    6594:	1a 42 22 1e 	mov	&0x1e22,r10	
    6598:	0f 4a       	mov	r10,	r15	
    659a:	01 3c       	jmp	$+4      	;abs 0x659e
    659c:	2f 4f       	mov	@r15,	r15	
    659e:	0f 9b       	cmp	r11,	r15	
    65a0:	03 24       	jz	$+8      	;abs 0x65a8
    65a2:	0f 93       	tst	r15		
    65a4:	fb 23       	jnz	$-8      	;abs 0x659c
    65a6:	33 3c       	jmp	$+104    	;abs 0x660e
    65a8:	0b 93       	tst	r11		
    65aa:	31 24       	jz	$+100    	;abs 0x660e
    65ac:	cb 93 0a 00 	tst.b	10(r11)	;0x000a(r11)
    65b0:	1c 24       	jz	$+58     	;abs 0x65ea
    65b2:	cb 43 0a 00 	mov.b	#0,	10(r11)	;r3 As==00, 0x000a(r11)
    65b6:	09 3c       	jmp	$+20     	;abs 0x65ca
    65b8:	0b 9a       	cmp	r10,	r11	
    65ba:	06 24       	jz	$+14     	;abs 0x65c8
    65bc:	0d 4b       	mov	r11,	r13	
    65be:	7e 40 87 ff 	mov.b	#-121,	r14	;#0xff87
    65c2:	0f 4a       	mov	r10,	r15	
    65c4:	b0 13 4a 65 	calla	#0x0654a	
    65c8:	2a 4a       	mov	@r10,	r10	
    65ca:	0a 93       	tst	r10		
    65cc:	f5 23       	jnz	$-20     	;abs 0x65b8
    65ce:	3c 0b 04 00 	mova	4(r11),	r12	;0x0004(r11)
    65d2:	dc 03       	tsta	r12		
    65d4:	0a 24       	jz	$+22     	;abs 0x65ea
    65d6:	0b 98       	cmp	r8,	r11	
    65d8:	08 24       	jz	$+18     	;abs 0x65ea
    65da:	82 4b 20 1e 	mov	r11,	&0x1e20	
    65de:	0d 43       	clr	r13		
    65e0:	7e 40 83 ff 	mov.b	#-125,	r14	;#0xff83
    65e4:	0f 4b       	mov	r11,	r15	
    65e6:	3f 52       	add	#8,	r15	;r2 As==11
    65e8:	4c 13       	calla	r12		
    65ea:	1f 42 22 1e 	mov	&0x1e22,r15	
    65ee:	0b 9f       	cmp	r15,	r11	
    65f0:	0a 20       	jnz	$+22     	;abs 0x6606
    65f2:	a2 4b 22 1e 	mov	@r11,	&0x1e22	
    65f6:	09 3c       	jmp	$+20     	;abs 0x660a
    65f8:	2e 4f       	mov	@r15,	r14	
    65fa:	0e 9b       	cmp	r11,	r14	
    65fc:	03 20       	jnz	$+8      	;abs 0x6604
    65fe:	af 4b 00 00 	mov	@r11,	0(r15)	;0x0000(r15)
    6602:	03 3c       	jmp	$+8      	;abs 0x660a
    6604:	0f 4e       	mov	r14,	r15	
    6606:	0f 93       	tst	r15		
    6608:	f7 23       	jnz	$-16     	;abs 0x65f8
    660a:	82 49 20 1e 	mov	r9,	&0x1e20	
    660e:	38 16       	popm.a	#4,	r11	
    6610:	10 01       	reta			

00006612 <do_poll>:
    6612:	0b 14       	pushm.a	#1,	r11	
    6614:	c2 43 f1 23 	mov.b	#0,	&0x23f1	;r3 As==00
    6618:	1b 42 22 1e 	mov	&0x1e22,r11	
    661c:	0e 3c       	jmp	$+30     	;abs 0x663a
    661e:	cb 93 0b 00 	tst.b	11(r11)	;0x000b(r11)
    6622:	0a 24       	jz	$+22     	;abs 0x6638
    6624:	db 43 0a 00 	mov.b	#1,	10(r11)	;r3 As==01, 0x000a(r11)
    6628:	cb 43 0b 00 	mov.b	#0,	11(r11)	;r3 As==00, 0x000b(r11)
    662c:	0d 43       	clr	r13		
    662e:	7e 40 82 ff 	mov.b	#-126,	r14	;#0xff82
    6632:	0f 4b       	mov	r11,	r15	
    6634:	b0 13 4a 65 	calla	#0x0654a	
    6638:	2b 4b       	mov	@r11,	r11	
    663a:	0b 93       	tst	r11		
    663c:	f0 23       	jnz	$-30     	;abs 0x661e
    663e:	0b 16       	popm.a	#1,	r11	
    6640:	10 01       	reta			

00006642 <process_alloc_event>:
    6642:	5f 42 f2 23 	mov.b	&0x23f2,r15	
    6646:	4e 4f       	mov.b	r15,	r14	
    6648:	5e 53       	inc.b	r14		
    664a:	c2 4e f2 23 	mov.b	r14,	&0x23f2	
    664e:	10 01       	reta			

00006650 <process_init>:
    6650:	f2 40 8a ff 	mov.b	#-118,	&0x23f2	;#0xff8a
    6654:	f2 23 
    6656:	c2 43 f3 23 	mov.b	#0,	&0x23f3	;r3 As==00
    665a:	c2 43 f4 23 	mov.b	#0,	&0x23f4	;r3 As==00
    665e:	c2 43 f8 24 	mov.b	#0,	&0x24f8	;r3 As==00
    6662:	82 43 22 1e 	mov	#0,	&0x1e22	;r3 As==00
    6666:	82 43 20 1e 	mov	#0,	&0x1e20	;r3 As==00
    666a:	10 01       	reta			

0000666c <process_run>:
    666c:	2b 14       	pushm.a	#3,	r11	
    666e:	5f 42 f1 23 	mov.b	&0x23f1,r15	
    6672:	4f 93       	tst.b	r15		
    6674:	02 24       	jz	$+6      	;abs 0x667a
    6676:	b0 13 12 66 	calla	#0x06612	
    667a:	5d 42 f4 23 	mov.b	&0x23f4,r13	
    667e:	4d 93       	tst.b	r13		
    6680:	33 24       	jz	$+104    	;abs 0x66e8
    6682:	5e 42 f3 23 	mov.b	&0x23f3,r14	
    6686:	0c 4e       	mov	r14,	r12	
    6688:	5c 02       	rlam	#1,	r12	
    668a:	0f 4e       	mov	r14,	r15	
    668c:	5f 0a       	rlam	#3,	r15	
    668e:	0f 8c       	sub	r12,	r15	
    6690:	3f 50 24 1e 	add	#7716,	r15	;#0x1e24
    6694:	6a 4f       	mov.b	@r15,	r10	
    6696:	19 4f 02 00 	mov	2(r15),	r9	;0x0002(r15)
    669a:	1f 4f 04 00 	mov	4(r15),	r15	;0x0004(r15)
    669e:	1e 53       	inc	r14		
    66a0:	7e f0 07 00 	and.b	#7,	r14	;#0x0007
    66a4:	c2 4e f3 23 	mov.b	r14,	&0x23f3	
    66a8:	7d 53       	add.b	#-1,	r13	;r3 As==11
    66aa:	c2 4d f4 23 	mov.b	r13,	&0x23f4	
    66ae:	0f 93       	tst	r15		
    66b0:	12 20       	jnz	$+38     	;abs 0x66d6
    66b2:	1b 42 22 1e 	mov	&0x1e22,r11	
    66b6:	0c 3c       	jmp	$+26     	;abs 0x66d0
    66b8:	5f 42 f1 23 	mov.b	&0x23f1,r15	
    66bc:	4f 93       	tst.b	r15		
    66be:	02 24       	jz	$+6      	;abs 0x66c4
    66c0:	b0 13 12 66 	calla	#0x06612	
    66c4:	0d 49       	mov	r9,	r13	
    66c6:	4e 4a       	mov.b	r10,	r14	
    66c8:	0f 4b       	mov	r11,	r15	
    66ca:	b0 13 4a 65 	calla	#0x0654a	
    66ce:	2b 4b       	mov	@r11,	r11	
    66d0:	0b 93       	tst	r11		
    66d2:	f2 23       	jnz	$-26     	;abs 0x66b8
    66d4:	09 3c       	jmp	$+20     	;abs 0x66e8
    66d6:	7a 90 81 ff 	cmp.b	#-127,	r10	;#0xff81
    66da:	02 20       	jnz	$+6      	;abs 0x66e0
    66dc:	df 43 0a 00 	mov.b	#1,	10(r15)	;r3 As==01, 0x000a(r15)
    66e0:	0d 49       	mov	r9,	r13	
    66e2:	4e 4a       	mov.b	r10,	r14	
    66e4:	b0 13 4a 65 	calla	#0x0654a	
    66e8:	5f 42 f1 23 	mov.b	&0x23f1,r15	
    66ec:	5e 42 f4 23 	mov.b	&0x23f4,r14	
    66f0:	4f 4f       	mov.b	r15,	r15	
    66f2:	0f 5e       	add	r14,	r15	
    66f4:	29 16       	popm.a	#3,	r11	
    66f6:	10 01       	reta			

000066f8 <process_nevents>:
    66f8:	5f 42 f1 23 	mov.b	&0x23f1,r15	
    66fc:	5e 42 f4 23 	mov.b	&0x23f4,r14	
    6700:	4f 4f       	mov.b	r15,	r15	
    6702:	0f 5e       	add	r14,	r15	
    6704:	10 01       	reta			

00006706 <process_post>:
    6706:	1b 14       	pushm.a	#2,	r11	
    6708:	5b 42 f4 23 	mov.b	&0x23f4,r11	
    670c:	7b 92       	cmp.b	#8,	r11	;r2 As==11
    670e:	1b 24       	jz	$+56     	;abs 0x6746
    6710:	4c 4b       	mov.b	r11,	r12	
    6712:	5c 52 f3 23 	add.b	&0x23f3,r12	
    6716:	3c f0 07 00 	and	#7,	r12	;#0x0007
    671a:	0a 4c       	mov	r12,	r10	
    671c:	5a 02       	rlam	#1,	r10	
    671e:	5c 0a       	rlam	#3,	r12	
    6720:	0c 8a       	sub	r10,	r12	
    6722:	3c 50 24 1e 	add	#7716,	r12	;#0x1e24
    6726:	cc 4e 00 00 	mov.b	r14,	0(r12)	;0x0000(r12)
    672a:	8c 4d 02 00 	mov	r13,	2(r12)	;0x0002(r12)
    672e:	8c 4f 04 00 	mov	r15,	4(r12)	;0x0004(r12)
    6732:	4f 4b       	mov.b	r11,	r15	
    6734:	5f 53       	inc.b	r15		
    6736:	c2 4f f4 23 	mov.b	r15,	&0x23f4	
    673a:	c2 9f f8 24 	cmp.b	r15,	&0x24f8	
    673e:	05 2c       	jc	$+12     	;abs 0x674a
    6740:	c2 4f f8 24 	mov.b	r15,	&0x24f8	
    6744:	02 3c       	jmp	$+6      	;abs 0x674a
    6746:	1f 43       	mov	#1,	r15	;r3 As==01
    6748:	01 3c       	jmp	$+4      	;abs 0x674c
    674a:	0f 43       	clr	r15		
    674c:	1a 16       	popm.a	#2,	r11	
    674e:	10 01       	reta			

00006750 <process_post_synch>:
    6750:	0b 14       	pushm.a	#1,	r11	
    6752:	1b 42 20 1e 	mov	&0x1e20,r11	
    6756:	b0 13 4a 65 	calla	#0x0654a	
    675a:	82 4b 20 1e 	mov	r11,	&0x1e20	
    675e:	0b 16       	popm.a	#1,	r11	
    6760:	10 01       	reta			

00006762 <process_start>:
    6762:	0b 14       	pushm.a	#1,	r11	
    6764:	1b 42 22 1e 	mov	&0x1e22,r11	
    6768:	0c 4b       	mov	r11,	r12	
    676a:	01 3c       	jmp	$+4      	;abs 0x676e
    676c:	2c 4c       	mov	@r12,	r12	
    676e:	0c 9f       	cmp	r15,	r12	
    6770:	11 24       	jz	$+36     	;abs 0x6794
    6772:	0c 93       	tst	r12		
    6774:	fb 23       	jnz	$-8      	;abs 0x676c
    6776:	0f 93       	tst	r15		
    6778:	0d 24       	jz	$+28     	;abs 0x6794
    677a:	8f 4b 00 00 	mov	r11,	0(r15)	;0x0000(r15)
    677e:	82 4f 22 1e 	mov	r15,	&0x1e22	
    6782:	df 43 0a 00 	mov.b	#1,	10(r15)	;r3 As==01, 0x000a(r15)
    6786:	8f 43 08 00 	mov	#0,	8(r15)	;r3 As==00, 0x0008(r15)
    678a:	0d 4e       	mov	r14,	r13	
    678c:	7e 40 81 ff 	mov.b	#-127,	r14	;#0xff81
    6790:	b0 13 50 67 	calla	#0x06750	
    6794:	0b 16       	popm.a	#1,	r11	
    6796:	10 01       	reta			

00006798 <process_poll>:
    6798:	0f 93       	tst	r15		
    679a:	09 24       	jz	$+20     	;abs 0x67ae
    679c:	5e 4f 0a 00 	mov.b	10(r15),r14	;0x000a(r15)
    67a0:	7e 53       	add.b	#-1,	r14	;r3 As==11
    67a2:	6e 93       	cmp.b	#2,	r14	;r3 As==10
    67a4:	04 2c       	jc	$+10     	;abs 0x67ae
    67a6:	df 43 0b 00 	mov.b	#1,	11(r15)	;r3 As==01, 0x000b(r15)
    67aa:	d2 43 f1 23 	mov.b	#1,	&0x23f1	;r3 As==01
    67ae:	10 01       	reta			

000067b0 <queuebuf_init>:
    67b0:	3f 40 08 1a 	mov	#6664,	r15	;#0x1a08
    67b4:	b0 13 94 57 	calla	#0x05794	
    67b8:	3f 40 10 1a 	mov	#6672,	r15	;#0x1a10
    67bc:	b0 13 94 57 	calla	#0x05794	
    67c0:	10 01       	reta			

000067c2 <queuebuf_new_from_packetbuf>:
    67c2:	1b 14       	pushm.a	#2,	r11	
    67c4:	3f 40 10 1a 	mov	#6672,	r15	;#0x1a10
    67c8:	b0 13 ca 57 	calla	#0x057ca	
    67cc:	0b 4f       	mov	r15,	r11	
    67ce:	0f 93       	tst	r15		
    67d0:	1c 24       	jz	$+58     	;abs 0x680a
    67d2:	3f 40 08 1a 	mov	#6664,	r15	;#0x1a08
    67d6:	b0 13 ca 57 	calla	#0x057ca	
    67da:	0a 4f       	mov	r15,	r10	
    67dc:	8b 4f 00 00 	mov	r15,	0(r11)	;0x0000(r11)
    67e0:	0f 93       	tst	r15		
    67e2:	07 20       	jnz	$+16     	;abs 0x67f2
    67e4:	0e 4b       	mov	r11,	r14	
    67e6:	3f 40 10 1a 	mov	#6672,	r15	;#0x1a10
    67ea:	b0 13 08 58 	calla	#0x05808	
    67ee:	0b 43       	clr	r11		
    67f0:	0c 3c       	jmp	$+26     	;abs 0x680a
    67f2:	b0 13 2a 62 	calla	#0x0622a	
    67f6:	8a 4f 80 00 	mov	r15,	128(r10);0x0080(r10)
    67fa:	0e 4a       	mov	r10,	r14	
    67fc:	3e 50 9a 00 	add	#154,	r14	;#0x009a
    6800:	0f 4a       	mov	r10,	r15	
    6802:	3f 50 82 00 	add	#130,	r15	;#0x0082
    6806:	b0 13 10 63 	calla	#0x06310	
    680a:	0f 4b       	mov	r11,	r15	
    680c:	1a 16       	popm.a	#2,	r11	
    680e:	10 01       	reta			

00006810 <queuebuf_update_attr_from_packetbuf>:
    6810:	2f 4f       	mov	@r15,	r15	
    6812:	0e 4f       	mov	r15,	r14	
    6814:	3e 50 9a 00 	add	#154,	r14	;#0x009a
    6818:	3f 50 82 00 	add	#130,	r15	;#0x0082
    681c:	b0 13 10 63 	calla	#0x06310	
    6820:	10 01       	reta			

00006822 <queuebuf_free>:
    6822:	0b 14       	pushm.a	#1,	r11	
    6824:	0b 4f       	mov	r15,	r11	
    6826:	0e 4f       	mov	r15,	r14	
    6828:	3f 40 10 1a 	mov	#6672,	r15	;#0x1a10
    682c:	b0 13 3a 58 	calla	#0x0583a	
    6830:	0f 93       	tst	r15		
    6832:	0a 24       	jz	$+22     	;abs 0x6848
    6834:	2e 4b       	mov	@r11,	r14	
    6836:	3f 40 08 1a 	mov	#6664,	r15	;#0x1a08
    683a:	b0 13 08 58 	calla	#0x05808	
    683e:	0e 4b       	mov	r11,	r14	
    6840:	3f 40 10 1a 	mov	#6672,	r15	;#0x1a10
    6844:	b0 13 08 58 	calla	#0x05808	
    6848:	0b 16       	popm.a	#1,	r11	
    684a:	10 01       	reta			

0000684c <queuebuf_to_packetbuf>:
    684c:	0b 14       	pushm.a	#1,	r11	
    684e:	0b 4f       	mov	r15,	r11	
    6850:	0e 4f       	mov	r15,	r14	
    6852:	3f 40 10 1a 	mov	#6672,	r15	;#0x1a10
    6856:	b0 13 3a 58 	calla	#0x0583a	
    685a:	0f 93       	tst	r15		
    685c:	0e 24       	jz	$+30     	;abs 0x687a
    685e:	2b 4b       	mov	@r11,	r11	
    6860:	1e 4b 80 00 	mov	128(r11),r14	;0x0080(r11)
    6864:	0f 4b       	mov	r11,	r15	
    6866:	b0 13 e6 62 	calla	#0x062e6	
    686a:	0e 4b       	mov	r11,	r14	
    686c:	3e 50 9a 00 	add	#154,	r14	;#0x009a
    6870:	0f 4b       	mov	r11,	r15	
    6872:	3f 50 82 00 	add	#130,	r15	;#0x0082
    6876:	b0 13 32 63 	calla	#0x06332	
    687a:	0b 16       	popm.a	#1,	r11	
    687c:	10 01       	reta			

0000687e <random_init>:
    687e:	b0 13 f4 96 	calla	#0x096f4	
    6882:	10 01       	reta			

00006884 <random_rand>:
    6884:	b0 13 ce 96 	calla	#0x096ce	
    6888:	10 01       	reta			

0000688a <rtimer_arch_init>:
    688a:	32 c2       	dint			
    688c:	03 43       	nop			
    688e:	b2 40 10 00 	mov	#16,	&0x0162	;#0x0010
    6892:	62 01 
    6894:	32 d2       	eint			
    6896:	10 01       	reta			

00006898 <rtimer_arch_now>:
    6898:	1f 42 70 01 	mov	&0x0170,r15	
    689c:	1e 42 70 01 	mov	&0x0170,r14	
    68a0:	0f 9e       	cmp	r14,	r15	
    68a2:	fa 23       	jnz	$-10     	;abs 0x6898
    68a4:	10 01       	reta			

000068a6 <rtimer_arch_schedule>:
    68a6:	82 4f 72 01 	mov	r15,	&0x0172	
    68aa:	10 01       	reta			

000068ac <rtimer_init>:
    68ac:	b0 13 8a 68 	calla	#0x0688a	
    68b0:	10 01       	reta			

000068b2 <rtimer_run_next>:
    68b2:	1d 42 b4 23 	mov	&0x23b4,r13	
    68b6:	0d 93       	tst	r13		
    68b8:	0e 24       	jz	$+30     	;abs 0x68d6
    68ba:	82 43 b4 23 	mov	#0,	&0x23b4	;r3 As==00
    68be:	1e 4d 06 00 	mov	6(r13),	r14	;0x0006(r13)
    68c2:	0f 4d       	mov	r13,	r15	
    68c4:	5d 13 02 00 	calla	2(r13)		;0x0002(r13)
    68c8:	1f 42 b4 23 	mov	&0x23b4,r15	
    68cc:	0f 93       	tst	r15		
    68ce:	03 24       	jz	$+8      	;abs 0x68d6
    68d0:	2f 4f       	mov	@r15,	r15	
    68d2:	b0 13 a6 68 	calla	#0x068a6	
    68d6:	10 01       	reta			

000068d8 <process_thread_sensors_process>:
    68d8:	0b 14       	pushm.a	#1,	r11	
    68da:	0b 4f       	mov	r15,	r11	
    68dc:	2f 4f       	mov	@r15,	r15	
    68de:	3f 90 75 00 	cmp	#117,	r15	;#0x0075
    68e2:	23 24       	jz	$+72     	;abs 0x692a
    68e4:	3f 90 7c 00 	cmp	#124,	r15	;#0x007c
    68e8:	52 24       	jz	$+166    	;abs 0x698e
    68ea:	0f 93       	tst	r15		
    68ec:	49 20       	jnz	$+148    	;abs 0x6980
    68ee:	b0 13 42 66 	calla	#0x06642	
    68f2:	c2 4f f9 24 	mov.b	r15,	&0x24f9	
    68f6:	82 43 b6 23 	mov	#0,	&0x23b6	;r3 As==00
    68fa:	09 3c       	jmp	$+20     	;abs 0x690e
    68fc:	cf 43 fa 24 	mov.b	#0,	9466(r15);r3 As==00, 0x24fa(r15)
    6900:	0e 43       	clr	r14		
    6902:	3f 40 80 00 	mov	#128,	r15	;#0x0080
    6906:	5d 13 06 00 	calla	6(r13)		;0x0006(r13)
    690a:	92 53 b6 23 	inc	&0x23b6	
    690e:	1f 42 b6 23 	mov	&0x23b6,r15	
    6912:	0e 4f       	mov	r15,	r14	
    6914:	5e 02       	rlam	#1,	r14	
    6916:	1d 4e 30 1a 	mov	6704(r14),r13	;0x1a30(r14)
    691a:	0d 93       	tst	r13		
    691c:	ef 23       	jnz	$-32     	;abs 0x68fc
    691e:	c2 4f 05 24 	mov.b	r15,	&0x2405	
    6922:	bb 40 75 00 	mov	#117,	0(r11)	;#0x0075, 0x0000(r11)
    6926:	00 00 
    6928:	30 3c       	jmp	$+98     	;abs 0x698a
    692a:	82 43 b8 23 	mov	#0,	&0x23b8	;r3 As==00
    692e:	82 43 b6 23 	mov	#0,	&0x23b6	;r3 As==00
    6932:	1c 3c       	jmp	$+58     	;abs 0x696c
    6934:	cf 93 fa 24 	tst.b	9466(r15)	;0x24fa(r15)
    6938:	17 34       	jge	$+48     	;abs 0x6968
    693a:	5f 02       	rlam	#1,	r15	
    693c:	1d 4f 30 1a 	mov	6704(r15),r13	;0x1a30(r15)
    6940:	5e 42 f9 24 	mov.b	&0x24f9,r14	
    6944:	0f 43       	clr	r15		
    6946:	b0 13 06 67 	calla	#0x06706	
    694a:	0f 93       	tst	r15		
    694c:	04 20       	jnz	$+10     	;abs 0x6956
    694e:	bb 40 7c 00 	mov	#124,	0(r11)	;#0x007c, 0x0000(r11)
    6952:	00 00 
    6954:	1a 3c       	jmp	$+54     	;abs 0x698a
    6956:	1f 42 b6 23 	mov	&0x23b6,r15	
    695a:	3f 50 fa 24 	add	#9466,	r15	;#0x24fa
    695e:	ff f0 7f 00 	and.b	#127,	0(r15)	;#0x007f, 0x0000(r15)
    6962:	00 00 
    6964:	92 53 b8 23 	inc	&0x23b8	
    6968:	92 53 b6 23 	inc	&0x23b6	
    696c:	1f 42 b6 23 	mov	&0x23b6,r15	
    6970:	5e 42 05 24 	mov.b	&0x2405,r14	
    6974:	0f 9e       	cmp	r14,	r15	
    6976:	de 3b       	jl	$-66     	;abs 0x6934
    6978:	82 93 b8 23 	tst	&0x23b8	
    697c:	d6 23       	jnz	$-82     	;abs 0x692a
    697e:	d1 3f       	jmp	$-92     	;abs 0x6922
    6980:	8b 43 00 00 	mov	#0,	0(r11)	;r3 As==00, 0x0000(r11)
    6984:	7f 40 03 00 	mov.b	#3,	r15	;#0x0003
    6988:	06 3c       	jmp	$+14     	;abs 0x6996
    698a:	5f 43       	mov.b	#1,	r15	;r3 As==01
    698c:	04 3c       	jmp	$+10     	;abs 0x6996
    698e:	5e 92 f9 24 	cmp.b	&0x24f9,r14	
    6992:	fb 23       	jnz	$-8      	;abs 0x698a
    6994:	e0 3f       	jmp	$-62     	;abs 0x6956
    6996:	0b 16       	popm.a	#1,	r11	
    6998:	10 01       	reta			

0000699a <sensors_changed>:
    699a:	5d 42 05 24 	mov.b	&0x2405,r13	
    699e:	0e 43       	clr	r14		
    69a0:	0e 3c       	jmp	$+30     	;abs 0x69be
    69a2:	0c 4e       	mov	r14,	r12	
    69a4:	5c 02       	rlam	#1,	r12	
    69a6:	8c 9f 30 1a 	cmp	r15,	6704(r12);0x1a30(r12)
    69aa:	08 20       	jnz	$+18     	;abs 0x69bc
    69ac:	fe d0 80 ff 	bis.b	#-128,	9466(r14);#0xff80, 0x24fa(r14)
    69b0:	fa 24 
    69b2:	3f 40 18 1a 	mov	#6680,	r15	;#0x1a18
    69b6:	b0 13 98 67 	calla	#0x06798	
    69ba:	10 01       	reta			
    69bc:	1e 53       	inc	r14		
    69be:	0e 9d       	cmp	r13,	r14	
    69c0:	f0 3b       	jl	$-30     	;abs 0x69a2
    69c2:	f4 3f       	jmp	$-22     	;abs 0x69ac

000069c4 <spi_init>:
    69c4:	d2 d3 69 00 	bis.b	#1,	&0x0069	;r3 As==01
    69c8:	f2 d0 80 ff 	bis.b	#-128,	&0x0069	;#0xff80
    69cc:	69 00 
    69ce:	f2 40 69 00 	mov.b	#105,	&0x0068	;#0x0069
    69d2:	68 00 
    69d4:	c2 43 6b 00 	mov.b	#0,	&0x006b	;r3 As==00
    69d8:	e2 43 6a 00 	mov.b	#2,	&0x006a	;r3 As==10
    69dc:	f2 d0 0e 00 	bis.b	#14,	&0x001b	;#0x000e
    69e0:	1b 00 
    69e2:	f2 d0 0c 00 	bis.b	#12,	&0x001a	;#0x000c
    69e6:	1a 00 
    69e8:	e2 c2 03 00 	bic.b	#4,	&0x0003	;r2 As==10
    69ec:	f2 c2 03 00 	bic.b	#8,	&0x0003	;r2 As==11
    69f0:	d2 c3 69 00 	bic.b	#1,	&0x0069	;r3 As==01
    69f4:	10 01       	reta			

000069f6 <stack_check_init>:
    69f6:	21 83       	decd	r1		
    69f8:	82 41 ba 23 	mov	r1,	&0x23ba	
    69fc:	b1 40 00 25 	mov	#9472,	0(r1)	;#0x2500, 0x0000(r1)
    6a00:	00 00 
    6a02:	06 3c       	jmp	$+14     	;abs 0x6a10
    6a04:	ff 40 cd ff 	mov.b	#-51,	0(r15)	;#0xffcd, 0x0000(r15)
    6a08:	00 00 
    6a0a:	1f 53       	inc	r15		
    6a0c:	81 4f 00 00 	mov	r15,	0(r1)	;0x0000(r1)
    6a10:	2f 41       	mov	@r1,	r15	
    6a12:	0f 91       	cmp	r1,	r15	
    6a14:	f7 2b       	jnc	$-16     	;abs 0x6a04
    6a16:	0e 43       	clr	r14		
    6a18:	3f 40 24 1a 	mov	#6692,	r15	;#0x1a24
    6a1c:	b0 13 62 67 	calla	#0x06762	
    6a20:	21 53       	incd	r1		
    6a22:	10 01       	reta			

00006a24 <stack_check_get_usage>:
    6a24:	0b 14       	pushm.a	#1,	r11	
    6a26:	b0 13 64 6d 	calla	#0x06d64	
    6a2a:	3b 40 00 25 	mov	#9472,	r11	;#0x2500
    6a2e:	01 3c       	jmp	$+4      	;abs 0x6a32
    6a30:	1b 53       	inc	r11		
    6a32:	fb 90 cd ff 	cmp.b	#-51,	0(r11)	;#0xffcd, 0x0000(r11)
    6a36:	00 00 
    6a38:	05 24       	jz	$+12     	;abs 0x6a44
    6a3a:	3b 90 00 31 	cmp	#12544,	r11	;#0x3100
    6a3e:	f8 2b       	jnc	$-14     	;abs 0x6a30
    6a40:	01 3c       	jmp	$+4      	;abs 0x6a44
    6a42:	1b 53       	inc	r11		
    6a44:	fb 90 cd ff 	cmp.b	#-51,	0(r11)	;#0xffcd, 0x0000(r11)
    6a48:	00 00 
    6a4a:	03 20       	jnz	$+8      	;abs 0x6a52
    6a4c:	3b 90 00 31 	cmp	#12544,	r11	;#0x3100
    6a50:	f8 2b       	jnc	$-14     	;abs 0x6a42
    6a52:	b0 13 64 6d 	calla	#0x06d64	
    6a56:	3b 90 00 31 	cmp	#12544,	r11	;#0x3100
    6a5a:	0a 2c       	jc	$+22     	;abs 0x6a70
    6a5c:	3d 40 00 31 	mov	#12544,	r13	;#0x3100
    6a60:	0d 8b       	sub	r11,	r13	
    6a62:	0e 4d       	mov	r13,	r14	
    6a64:	8d 10       	swpb	r13		
    6a66:	8d 11       	sxt	r13		
    6a68:	8d 10       	swpb	r13		
    6a6a:	8d 11       	sxt	r13		
    6a6c:	0f 4d       	mov	r13,	r15	
    6a6e:	02 3c       	jmp	$+6      	;abs 0x6a74
    6a70:	3e 43       	mov	#-1,	r14	;r3 As==11
    6a72:	3f 43       	mov	#-1,	r15	;r3 As==11
    6a74:	0b 16       	popm.a	#1,	r11	
    6a76:	10 01       	reta			

00006a78 <process_thread_stack_check_process>:
    6a78:	4b 14       	pushm.a	#5,	r11	
    6a7a:	07 4f       	mov	r15,	r7	
    6a7c:	2f 4f       	mov	@r15,	r15	
    6a7e:	0f 93       	tst	r15		
    6a80:	04 24       	jz	$+10     	;abs 0x6a8a
    6a82:	3f 90 92 00 	cmp	#146,	r15	;#0x0092
    6a86:	51 20       	jnz	$+164    	;abs 0x6b2a
    6a88:	57 3c       	jmp	$+176    	;abs 0x6b38
    6a8a:	3d 40 00 05 	mov	#1280,	r13	;#0x0500
    6a8e:	0e 43       	clr	r14		
    6a90:	3f 40 bc 23 	mov	#9148,	r15	;#0x23bc
    6a94:	b0 13 44 4c 	calla	#0x04c44	
    6a98:	b7 40 92 00 	mov	#146,	0(r7)	;#0x0092, 0x0000(r7)
    6a9c:	00 00 
    6a9e:	4a 3c       	jmp	$+150    	;abs 0x6b34
    6aa0:	b0 13 24 6a 	calla	#0x06a24	
    6aa4:	08 4e       	mov	r14,	r8	
    6aa6:	09 4f       	mov	r15,	r9	
    6aa8:	3e 40 00 31 	mov	#12544,	r14	;#0x3100
    6aac:	3e 80 00 25 	sub	#9472,	r14	;#0x2500
    6ab0:	0a 4e       	mov	r14,	r10	
    6ab2:	8e 10       	swpb	r14		
    6ab4:	8e 11       	sxt	r14		
    6ab6:	8e 10       	swpb	r14		
    6ab8:	8e 11       	sxt	r14		
    6aba:	0b 4e       	mov	r14,	r11	
    6abc:	09 93       	tst	r9		
    6abe:	05 38       	jl	$+12     	;abs 0x6aca
    6ac0:	0e 93       	tst	r14		
    6ac2:	03 38       	jl	$+8      	;abs 0x6aca
    6ac4:	0e 99       	cmp	r9,	r14	
    6ac6:	17 38       	jl	$+48     	;abs 0x6af6
    6ac8:	12 3c       	jmp	$+38     	;abs 0x6aee
    6aca:	92 93 4a 11 	cmp	#1,	&0x114a	;r3 As==01
    6ace:	28 38       	jl	$+82     	;abs 0x6b20
    6ad0:	30 12 04 9d 	push	#-25340	;#0x9d04
    6ad4:	30 12 0a 9d 	push	#-25334	;#0x9d0a
    6ad8:	30 12 0e 9d 	push	#-25330	;#0x9d0e
    6adc:	b0 13 68 8d 	calla	#0x08d68	
    6ae0:	31 50 06 00 	add	#6,	r1	;#0x0006
    6ae4:	1b 15       	pushm	#2,	r11	
    6ae6:	19 15       	pushm	#2,	r9	
    6ae8:	30 12 1d 9d 	push	#-25315	;#0x9d1d
    6aec:	15 3c       	jmp	$+44     	;abs 0x6b18
    6aee:	09 9e       	cmp	r14,	r9	
    6af0:	17 38       	jl	$+48     	;abs 0x6b20
    6af2:	0a 98       	cmp	r8,	r10	
    6af4:	15 2c       	jc	$+44     	;abs 0x6b20
    6af6:	92 93 4a 11 	cmp	#1,	&0x114a	;r3 As==01
    6afa:	12 38       	jl	$+38     	;abs 0x6b20
    6afc:	30 12 04 9d 	push	#-25340	;#0x9d04
    6b00:	30 12 0a 9d 	push	#-25334	;#0x9d0a
    6b04:	30 12 0e 9d 	push	#-25330	;#0x9d0e
    6b08:	b0 13 68 8d 	calla	#0x08d68	
    6b0c:	31 50 06 00 	add	#6,	r1	;#0x0006
    6b10:	1b 15       	pushm	#2,	r11	
    6b12:	19 15       	pushm	#2,	r9	
    6b14:	30 12 47 9d 	push	#-25273	;#0x9d47
    6b18:	b0 13 68 8d 	calla	#0x08d68	
    6b1c:	31 50 0a 00 	add	#10,	r1	;#0x000a
    6b20:	3f 40 bc 23 	mov	#9148,	r15	;#0x23bc
    6b24:	b0 13 56 4c 	calla	#0x04c56	
    6b28:	b7 3f       	jmp	$-144    	;abs 0x6a98
    6b2a:	87 43 00 00 	mov	#0,	0(r7)	;r3 As==00, 0x0000(r7)
    6b2e:	7f 40 03 00 	mov.b	#3,	r15	;#0x0003
    6b32:	09 3c       	jmp	$+20     	;abs 0x6b46
    6b34:	5f 43       	mov.b	#1,	r15	;r3 As==01
    6b36:	07 3c       	jmp	$+16     	;abs 0x6b46
    6b38:	3f 40 bc 23 	mov	#9148,	r15	;#0x23bc
    6b3c:	b0 13 68 4c 	calla	#0x04c68	
    6b40:	0f 93       	tst	r15		
    6b42:	f8 27       	jz	$-14     	;abs 0x6b34
    6b44:	ad 3f       	jmp	$-164    	;abs 0x6aa0
    6b46:	47 16       	popm.a	#5,	r11	
    6b48:	10 01       	reta			

00006b4a <timer_set>:
    6b4a:	0b 14       	pushm.a	#1,	r11	
    6b4c:	0b 4f       	mov	r15,	r11	
    6b4e:	8f 4d 04 00 	mov	r13,	4(r15)	;0x0004(r15)
    6b52:	8f 4e 06 00 	mov	r14,	6(r15)	;0x0006(r15)
    6b56:	b0 13 2c 44 	calla	#0x0442c	
    6b5a:	8b 4e 00 00 	mov	r14,	0(r11)	;0x0000(r11)
    6b5e:	8b 4f 02 00 	mov	r15,	2(r11)	;0x0002(r11)
    6b62:	0b 16       	popm.a	#1,	r11	
    6b64:	10 01       	reta			

00006b66 <timer_expired>:
    6b66:	0b 14       	pushm.a	#1,	r11	
    6b68:	0b 4f       	mov	r15,	r11	
    6b6a:	b0 13 2c 44 	calla	#0x0442c	
    6b6e:	2e 8b       	sub	@r11,	r14	
    6b70:	1f 7b 02 00 	subc	2(r11),	r15	;0x0002(r11)
    6b74:	1e 53       	inc	r14		
    6b76:	0f 63       	adc	r15		
    6b78:	1d 43       	mov	#1,	r13	;r3 As==01
    6b7a:	8b 9f 06 00 	cmp	r15,	6(r11)	;0x0006(r11)
    6b7e:	05 28       	jnc	$+12     	;abs 0x6b8a
    6b80:	03 20       	jnz	$+8      	;abs 0x6b88
    6b82:	8b 9e 04 00 	cmp	r14,	4(r11)	;0x0004(r11)
    6b86:	01 28       	jnc	$+4      	;abs 0x6b8a
    6b88:	0d 43       	clr	r13		
    6b8a:	0f 4d       	mov	r13,	r15	
    6b8c:	0b 16       	popm.a	#1,	r11	
    6b8e:	10 01       	reta			

00006b90 <timer_reset>:
    6b90:	0b 14       	pushm.a	#1,	r11	
    6b92:	0b 4f       	mov	r15,	r11	
    6b94:	b0 13 66 6b 	calla	#0x06b66	
    6b98:	0f 93       	tst	r15		
    6b9a:	06 24       	jz	$+14     	;abs 0x6ba8
    6b9c:	9b 5b 04 00 	add	4(r11),	0(r11)	;0x0004(r11), 0x0000(r11)
    6ba0:	00 00 
    6ba2:	9b 6b 06 00 	addc	6(r11),	2(r11)	;0x0006(r11), 0x0002(r11)
    6ba6:	02 00 
    6ba8:	0b 16       	popm.a	#1,	r11	
    6baa:	10 01       	reta			

00006bac <status>:
    6bac:	3f 50 7f ff 	add	#-129,	r15	;#0xff7f
    6bb0:	2f 93       	cmp	#2,	r15	;r3 As==10
    6bb2:	03 2c       	jc	$+8      	;abs 0x6bba
    6bb4:	5f 42 06 24 	mov.b	&0x2406,r15	
    6bb8:	10 01       	reta			
    6bba:	0f 43       	clr	r15		
    6bbc:	10 01       	reta			

00006bbe <tmp102_init>:
    6bbe:	d2 d3 32 00 	bis.b	#1,	&0x0032	;r3 As==01
    6bc2:	d2 c2 33 00 	bic.b	&0x0033,&0x0033	
    6bc6:	33 00 
    6bc8:	d2 c2 33 00 	bic.b	&0x0033,&0x0045	
    6bcc:	45 00 
    6bce:	d2 c2 33 00 	bic.b	&0x0033,&0x0012	
    6bd2:	12 00 
    6bd4:	d2 d3 31 00 	bis.b	#1,	&0x0031	;r3 As==01
    6bd8:	b0 13 92 54 	calla	#0x05492	
    6bdc:	d2 43 06 24 	mov.b	#1,	&0x2406	;r3 As==01
    6be0:	10 01       	reta			

00006be2 <tmp102_stop>:
    6be2:	d2 c3 31 00 	bic.b	#1,	&0x0031	;r3 As==01
    6be6:	c2 43 06 24 	mov.b	#0,	&0x2406	;r3 As==00
    6bea:	10 01       	reta			

00006bec <configure>:
    6bec:	0b 14       	pushm.a	#1,	r11	
    6bee:	0b 4e       	mov	r14,	r11	
    6bf0:	3f 90 81 00 	cmp	#129,	r15	;#0x0081
    6bf4:	0b 20       	jnz	$+24     	;abs 0x6c0c
    6bf6:	0e 93       	tst	r14		
    6bf8:	03 24       	jz	$+8      	;abs 0x6c00
    6bfa:	b0 13 be 6b 	calla	#0x06bbe	
    6bfe:	02 3c       	jmp	$+6      	;abs 0x6c04
    6c00:	b0 13 e2 6b 	calla	#0x06be2	
    6c04:	c2 4b 06 24 	mov.b	r11,	&0x2406	
    6c08:	0f 43       	clr	r15		
    6c0a:	01 3c       	jmp	$+4      	;abs 0x6c0e
    6c0c:	3f 43       	mov	#-1,	r15	;r3 As==11
    6c0e:	0b 16       	popm.a	#1,	r11	
    6c10:	10 01       	reta			

00006c12 <tmp102_read_reg>:
    6c12:	21 82       	sub	#4,	r1	;r2 As==10
    6c14:	c1 43 00 00 	mov.b	#0,	0(r1)	;r3 As==00, 0x0000(r1)
    6c18:	c1 43 01 00 	mov.b	#0,	1(r1)	;r3 As==00, 0x0001(r1)
    6c1c:	c1 4f 02 00 	mov.b	r15,	2(r1)	;0x0002(r1)
    6c20:	7f 40 48 00 	mov.b	#72,	r15	;#0x0048
    6c24:	b0 13 1a 54 	calla	#0x0541a	
    6c28:	b0 13 88 54 	calla	#0x05488	
    6c2c:	4f 93       	tst.b	r15		
    6c2e:	fc 23       	jnz	$-6      	;abs 0x6c28
    6c30:	0e 41       	mov	r1,	r14	
    6c32:	2e 53       	incd	r14		
    6c34:	5f 43       	mov.b	#1,	r15	;r3 As==01
    6c36:	b0 13 b4 54 	calla	#0x054b4	
    6c3a:	b0 13 88 54 	calla	#0x05488	
    6c3e:	4f 93       	tst.b	r15		
    6c40:	fc 23       	jnz	$-6      	;abs 0x6c3a
    6c42:	7f 40 48 00 	mov.b	#72,	r15	;#0x0048
    6c46:	b0 13 e4 53 	calla	#0x053e4	
    6c4a:	b0 13 88 54 	calla	#0x05488	
    6c4e:	4f 93       	tst.b	r15		
    6c50:	fc 23       	jnz	$-6      	;abs 0x6c4a
    6c52:	0e 41       	mov	r1,	r14	
    6c54:	6f 43       	mov.b	#2,	r15	;r3 As==10
    6c56:	b0 13 4a 54 	calla	#0x0544a	
    6c5a:	b0 13 88 54 	calla	#0x05488	
    6c5e:	4f 93       	tst.b	r15		
    6c60:	fc 23       	jnz	$-6      	;abs 0x6c5a
    6c62:	6f 41       	mov.b	@r1,	r15	
    6c64:	8f 10       	swpb	r15		
    6c66:	5e 41 01 00 	mov.b	1(r1),	r14	;0x0001(r1)
    6c6a:	0f de       	bis	r14,	r15	
    6c6c:	21 52       	add	#4,	r1	;r2 As==10
    6c6e:	10 01       	reta			

00006c70 <tmp102_read_temp_x100>:
    6c70:	4f 43       	clr.b	r15		
    6c72:	b0 13 12 6c 	calla	#0x06c12	
    6c76:	0e 4f       	mov	r15,	r14	
    6c78:	0f 93       	tst	r15		
    6c7a:	04 34       	jge	$+10     	;abs 0x6c84
    6c7c:	3e e3       	inv	r14		
    6c7e:	1e 53       	inc	r14		
    6c80:	3d 43       	mov	#-1,	r13	;r3 As==11
    6c82:	01 3c       	jmp	$+4      	;abs 0x6c86
    6c84:	1d 43       	mov	#1,	r13	;r3 As==01
    6c86:	0f 4e       	mov	r14,	r15	
    6c88:	8f 10       	swpb	r15		
    6c8a:	8f 11       	sxt	r15		
    6c8c:	02 12       	push	r2		
    6c8e:	32 c2       	dint			
    6c90:	03 43       	nop			
    6c92:	82 4f 32 01 	mov	r15,	&0x0132	
    6c96:	82 4d 38 01 	mov	r13,	&0x0138	
    6c9a:	1f 42 3a 01 	mov	&0x013a,r15	
    6c9e:	32 41       	pop	r2		
    6ca0:	0d 4f       	mov	r15,	r13	
    6ca2:	5d 06       	rlam	#2,	r13	
    6ca4:	5f 0e       	rlam	#4,	r15	
    6ca6:	0d 5f       	add	r15,	r13	
    6ca8:	0c 4d       	mov	r13,	r12	
    6caa:	5c 06       	rlam	#2,	r12	
    6cac:	0c 5d       	add	r13,	r12	
    6cae:	3e f0 ff 00 	and	#255,	r14	;#0x00ff
    6cb2:	0d 4e       	mov	r14,	r13	
    6cb4:	5d 06       	rlam	#2,	r13	
    6cb6:	5e 0e       	rlam	#4,	r14	
    6cb8:	0d 5e       	add	r14,	r13	
    6cba:	0f 4d       	mov	r13,	r15	
    6cbc:	5f 06       	rlam	#2,	r15	
    6cbe:	0f 5d       	add	r13,	r15	
    6cc0:	8f 10       	swpb	r15		
    6cc2:	8f 11       	sxt	r15		
    6cc4:	0f 5c       	add	r12,	r15	
    6cc6:	10 01       	reta			

00006cc8 <value>:
    6cc8:	b0 13 70 6c 	calla	#0x06c70	
    6ccc:	10 01       	reta			

00006cce <putchar>:
    6cce:	0b 14       	pushm.a	#1,	r11	
    6cd0:	0b 4f       	mov	r15,	r11	
    6cd2:	4f 4f       	mov.b	r15,	r15	
    6cd4:	b0 13 ec 6c 	calla	#0x06cec	
    6cd8:	0f 4b       	mov	r11,	r15	
    6cda:	0b 16       	popm.a	#1,	r11	
    6cdc:	10 01       	reta			

00006cde <uart0_active>:
    6cde:	5f 42 65 00 	mov.b	&0x0065,r15	
    6ce2:	5e 42 07 24 	mov.b	&0x2407,r14	
    6ce6:	5f f3       	and.b	#1,	r15	;r3 As==01
    6ce8:	4f de       	bis.b	r14,	r15	
    6cea:	10 01       	reta			

00006cec <uart0_writeb>:
    6cec:	0b 14       	pushm.a	#1,	r11	
    6cee:	4b 4f       	mov.b	r15,	r11	
    6cf0:	b0 13 64 6d 	calla	#0x06d64	
    6cf4:	d2 b3 65 00 	bit.b	#1,	&0x0065	;r3 As==01
    6cf8:	fd 23       	jnz	$-4      	;abs 0x6cf4
    6cfa:	c2 4b 67 00 	mov.b	r11,	&0x0067	
    6cfe:	0b 16       	popm.a	#1,	r11	
    6d00:	10 01       	reta			

00006d02 <uart0_init>:
    6d02:	21 82       	sub	#4,	r1	;r2 As==10
    6d04:	81 4e 00 00 	mov	r14,	0(r1)	;0x0000(r1)
    6d08:	81 4f 02 00 	mov	r15,	2(r1)	;0x0002(r1)
    6d0c:	d2 d3 61 00 	bis.b	#1,	&0x0061	;r3 As==01
    6d10:	f2 d0 80 ff 	bis.b	#-128,	&0x0061	;#0xff80
    6d14:	61 00 
    6d16:	e2 41 62 00 	mov.b	@r1,	&0x0062	
    6d1a:	d2 41 01 00 	mov.b	1(r1),	&0x0063	;0x0001(r1)
    6d1e:	63 00 
    6d20:	f2 40 06 00 	mov.b	#6,	&0x0064	;#0x0006
    6d24:	64 00 
    6d26:	f2 f0 df ff 	and.b	#-33,	&0x001a	;#0xffdf
    6d2a:	1a 00 
    6d2c:	f2 d0 10 00 	bis.b	#16,	&0x001a	;#0x0010
    6d30:	1a 00 
    6d32:	f2 d0 30 00 	bis.b	#48,	&0x001b	;#0x0030
    6d36:	1b 00 
    6d38:	c2 43 07 24 	mov.b	#0,	&0x2407	;r3 As==00
    6d3c:	d2 c3 03 00 	bic.b	#1,	&0x0003	;r3 As==01
    6d40:	e2 c3 03 00 	bic.b	#2,	&0x0003	;r3 As==10
    6d44:	d2 c3 61 00 	bic.b	#1,	&0x0061	;r3 As==01
    6d48:	d2 d3 01 00 	bis.b	#1,	&0x0001	;r3 As==01
    6d4c:	21 52       	add	#4,	r1	;r2 As==10
    6d4e:	10 01       	reta			

00006d50 <watchdog_start>:
    6d50:	1f 42 cc 23 	mov	&0x23cc,r15	
    6d54:	3f 53       	add	#-1,	r15	;r3 As==11
    6d56:	82 4f cc 23 	mov	r15,	&0x23cc	
    6d5a:	03 20       	jnz	$+8      	;abs 0x6d62
    6d5c:	b2 40 1c 5a 	mov	#23068,	&0x0120	;#0x5a1c
    6d60:	20 01 
    6d62:	10 01       	reta			

00006d64 <watchdog_periodic>:
    6d64:	1f 42 20 01 	mov	&0x0120,r15	
    6d68:	3f f0 ff 00 	and	#255,	r15	;#0x00ff
    6d6c:	3f d0 18 5a 	bis	#23064,	r15	;#0x5a18
    6d70:	82 4f 20 01 	mov	r15,	&0x0120	
    6d74:	10 01       	reta			

00006d76 <watchdog_stop>:
    6d76:	1f 42 cc 23 	mov	&0x23cc,r15	
    6d7a:	1f 53       	inc	r15		
    6d7c:	82 4f cc 23 	mov	r15,	&0x23cc	
    6d80:	1f 93       	cmp	#1,	r15	;r3 As==01
    6d82:	03 20       	jnz	$+8      	;abs 0x6d8a
    6d84:	b2 40 80 5a 	mov	#23168,	&0x0120	;#0x5a80
    6d88:	20 01 
    6d8a:	10 01       	reta			

00006d8c <watchdog_init>:
    6d8c:	82 43 cc 23 	mov	#0,	&0x23cc	;r3 As==00
    6d90:	b0 13 76 6d 	calla	#0x06d76	
    6d94:	d2 c3 02 00 	bic.b	#1,	&0x0002	;r3 As==01
    6d98:	d2 d3 00 00 	bis.b	#1,	&0x0000	;r3 As==01
    6d9c:	10 01       	reta			

00006d9e <wait_ready>:
    6d9e:	0b 14       	pushm.a	#1,	r11	
    6da0:	b0 13 8c 58 	calla	#0x0588c	
    6da4:	f2 f0 ef ff 	and.b	#-17,	&0x001d	;#0xffef
    6da8:	1d 00 
    6daa:	f2 b2 03 00 	bit.b	#8,	&0x0003	;r2 As==11
    6dae:	fd 27       	jz	$-4      	;abs 0x6daa
    6db0:	f2 40 05 00 	mov.b	#5,	&0x006f	;#0x0005
    6db4:	6f 00 
    6db6:	d2 b3 6d 00 	bit.b	#1,	&0x006d	;r3 As==01
    6dba:	fd 23       	jnz	$-4      	;abs 0x6db6
    6dbc:	5e 42 6e 00 	mov.b	&0x006e,r14	
    6dc0:	c2 43 6f 00 	mov.b	#0,	&0x006f	;r3 As==00
    6dc4:	e2 b2 03 00 	bit.b	#4,	&0x0003	;r2 As==10
    6dc8:	fd 27       	jz	$-4      	;abs 0x6dc4
    6dca:	5b 42 6e 00 	mov.b	&0x006e,r11	
    6dce:	f2 d0 10 00 	bis.b	#16,	&0x001d	;#0x0010
    6dd2:	1d 00 
    6dd4:	02 df       	bis	r15,	r2	
    6dd6:	b0 13 64 6d 	calla	#0x06d64	
    6dda:	5b b3       	bit.b	#1,	r11	;r3 As==01
    6ddc:	e1 23       	jnz	$-60     	;abs 0x6da0
    6dde:	4f 4b       	mov.b	r11,	r15	
    6de0:	0b 16       	popm.a	#1,	r11	
    6de2:	10 01       	reta			

00006de4 <xmem_init>:
    6de4:	b0 13 c4 69 	calla	#0x069c4	
    6de8:	f2 d0 10 00 	bis.b	#16,	&0x001e	;#0x0010
    6dec:	1e 00 
    6dee:	f2 d0 80 ff 	bis.b	#-128,	&0x0032	;#0xff80
    6df2:	32 00 
    6df4:	f2 d0 10 00 	bis.b	#16,	&0x001d	;#0x0010
    6df8:	1d 00 
    6dfa:	f2 d0 80 ff 	bis.b	#-128,	&0x0031	;#0xff80
    6dfe:	31 00 
    6e00:	10 01       	reta			

00006e02 <xmem_pread>:
    6e02:	5b 14       	pushm.a	#6,	r11	
    6e04:	07 4f       	mov	r15,	r7	
    6e06:	09 4e       	mov	r14,	r9	
    6e08:	06 4c       	mov	r12,	r6	
    6e0a:	0a 4d       	mov	r13,	r10	
    6e0c:	08 4f       	mov	r15,	r8	
    6e0e:	08 5e       	add	r14,	r8	
    6e10:	b0 13 9e 6d 	calla	#0x06d9e	
    6e14:	b0 13 8c 58 	calla	#0x0588c	
    6e18:	f2 f0 ef ff 	and.b	#-17,	&0x001d	;#0xffef
    6e1c:	1d 00 
    6e1e:	f2 b2 03 00 	bit.b	#8,	&0x0003	;r2 As==11
    6e22:	fd 27       	jz	$-4      	;abs 0x6e1e
    6e24:	f2 40 03 00 	mov.b	#3,	&0x006f	;#0x0003
    6e28:	6f 00 
    6e2a:	f2 b2 03 00 	bit.b	#8,	&0x0003	;r2 As==11
    6e2e:	fd 27       	jz	$-4      	;abs 0x6e2a
    6e30:	c2 4a 6f 00 	mov.b	r10,	&0x006f	
    6e34:	f2 b2 03 00 	bit.b	#8,	&0x0003	;r2 As==11
    6e38:	fd 27       	jz	$-4      	;abs 0x6e34
    6e3a:	0b 46       	mov	r6,	r11	
    6e3c:	8b 10       	swpb	r11		
    6e3e:	8a 10       	swpb	r10		
    6e40:	4b ea       	xor.b	r10,	r11	
    6e42:	0b ea       	xor	r10,	r11	
    6e44:	c2 4b 6f 00 	mov.b	r11,	&0x006f	
    6e48:	5b 42 03 00 	mov.b	&0x0003,r11	
    6e4c:	7b f2       	and.b	#8,	r11	;r2 As==11
    6e4e:	fc 27       	jz	$-6      	;abs 0x6e48
    6e50:	c2 46 6f 00 	mov.b	r6,	&0x006f	
    6e54:	d2 b3 6d 00 	bit.b	#1,	&0x006d	;r3 As==01
    6e58:	fd 23       	jnz	$-4      	;abs 0x6e54
    6e5a:	5e 42 6e 00 	mov.b	&0x006e,r14	
    6e5e:	0d 47       	mov	r7,	r13	
    6e60:	0b 3c       	jmp	$+24     	;abs 0x6e78
    6e62:	c2 43 6f 00 	mov.b	#0,	&0x006f	;r3 As==00
    6e66:	e2 b2 03 00 	bit.b	#4,	&0x0003	;r2 As==10
    6e6a:	fd 27       	jz	$-4      	;abs 0x6e66
    6e6c:	5e 42 6e 00 	mov.b	&0x006e,r14	
    6e70:	7e e3       	xor.b	#-1,	r14	;r3 As==11
    6e72:	cd 4e 00 00 	mov.b	r14,	0(r13)	;0x0000(r13)
    6e76:	1d 53       	inc	r13		
    6e78:	0d 98       	cmp	r8,	r13	
    6e7a:	f3 2b       	jnc	$-24     	;abs 0x6e62
    6e7c:	f2 d0 10 00 	bis.b	#16,	&0x001d	;#0x0010
    6e80:	1d 00 
    6e82:	02 df       	bis	r15,	r2	
    6e84:	0f 49       	mov	r9,	r15	
    6e86:	56 16       	popm.a	#6,	r11	
    6e88:	10 01       	reta			

00006e8a <__ieee754_powf>:
    6e8a:	7b 14       	pushm.a	#8,	r11	
    6e8c:	31 50 dc ff 	add	#-36,	r1	;#0xffdc
    6e90:	04 4c       	mov	r12,	r4	
    6e92:	05 4d       	mov	r13,	r5	
    6e94:	81 4c 14 00 	mov	r12,	20(r1)	;0x0014(r1)
    6e98:	81 4d 16 00 	mov	r13,	22(r1)	;0x0016(r1)
    6e9c:	0a 4c       	mov	r12,	r10	
    6e9e:	0b 4d       	mov	r13,	r11	
    6ea0:	3a f3       	and	#-1,	r10	;r3 As==11
    6ea2:	3b f0 ff 7f 	and	#32767,	r11	;#0x7fff
    6ea6:	81 4a 00 00 	mov	r10,	0(r1)	;0x0000(r1)
    6eaa:	81 4b 02 00 	mov	r11,	2(r1)	;0x0002(r1)
    6eae:	0a 93       	tst	r10		
    6eb0:	04 20       	jnz	$+10     	;abs 0x6eba
    6eb2:	0b 93       	tst	r11		
    6eb4:	02 20       	jnz	$+6      	;abs 0x6eba
    6eb6:	80 00 94 7a 	bra	#0x07a94	
    6eba:	81 4e 08 00 	mov	r14,	8(r1)	;0x0008(r1)
    6ebe:	81 4f 0a 00 	mov	r15,	10(r1)	;0x000a(r1)
    6ec2:	06 4e       	mov	r14,	r6	
    6ec4:	07 4f       	mov	r15,	r7	
    6ec6:	36 f3       	and	#-1,	r6	;r3 As==11
    6ec8:	37 f0 ff 7f 	and	#32767,	r7	;#0x7fff
    6ecc:	37 90 80 7f 	cmp	#32640,	r7	;#0x7f80
    6ed0:	05 38       	jl	$+12     	;abs 0x6edc
    6ed2:	37 90 81 7f 	cmp	#32641,	r7	;#0x7f81
    6ed6:	0a 34       	jge	$+22     	;abs 0x6eec
    6ed8:	16 93       	cmp	#1,	r6	;r3 As==01
    6eda:	08 2c       	jc	$+18     	;abs 0x6eec
    6edc:	b1 90 80 7f 	cmp	#32640,	2(r1)	;#0x7f80, 0x0002(r1)
    6ee0:	02 00 
    6ee2:	0c 38       	jl	$+26     	;abs 0x6efc
    6ee4:	03 20       	jnz	$+8      	;abs 0x6eec
    6ee6:	91 93 00 00 	cmp	#1,	0(r1)	;r3 As==01, 0x0000(r1)
    6eea:	08 28       	jnc	$+18     	;abs 0x6efc
    6eec:	0c 4e       	mov	r14,	r12	
    6eee:	0d 4f       	mov	r15,	r13	
    6ef0:	0e 44       	mov	r4,	r14	
    6ef2:	0f 45       	mov	r5,	r15	
    6ef4:	b0 13 26 82 	calla	#0x08226	
    6ef8:	80 00 8e 7a 	bra	#0x07a8e	
    6efc:	91 41 0a 00 	mov	10(r1),	16(r1)	;0x000a(r1), 0x0010(r1)
    6f00:	10 00 
    6f02:	91 41 14 00 	mov	20(r1),	12(r1)	;0x0014(r1), 0x000c(r1)
    6f06:	0c 00 
    6f08:	19 41 16 00 	mov	22(r1),	r9	;0x0016(r1)
    6f0c:	81 93 10 00 	tst	16(r1)		;0x0010(r1)
    6f10:	05 38       	jl	$+12     	;abs 0x6f1c
    6f12:	81 43 04 00 	mov	#0,	4(r1)	;r3 As==00, 0x0004(r1)
    6f16:	81 43 06 00 	mov	#0,	6(r1)	;r3 As==00, 0x0006(r1)
    6f1a:	49 3c       	jmp	$+148    	;abs 0x6fae
    6f1c:	b1 90 80 4b 	cmp	#19328,	2(r1)	;#0x4b80, 0x0002(r1)
    6f20:	02 00 
    6f22:	05 38       	jl	$+12     	;abs 0x6f2e
    6f24:	a1 43 04 00 	mov	#2,	4(r1)	;r3 As==10, 0x0004(r1)
    6f28:	81 43 06 00 	mov	#0,	6(r1)	;r3 As==00, 0x0006(r1)
    6f2c:	40 3c       	jmp	$+130    	;abs 0x6fae
    6f2e:	b1 90 80 3f 	cmp	#16256,	2(r1)	;#0x3f80, 0x0002(r1)
    6f32:	02 00 
    6f34:	02 34       	jge	$+6      	;abs 0x6f3a
    6f36:	80 00 9c 7a 	bra	#0x07a9c	
    6f3a:	1c 41 02 00 	mov	2(r1),	r12	;0x0002(r1)
    6f3e:	0d 4c       	mov	r12,	r13	
    6f40:	8d 10       	swpb	r13		
    6f42:	8d 11       	sxt	r13		
    6f44:	8d 10       	swpb	r13		
    6f46:	8d 11       	sxt	r13		
    6f48:	7b 40 07 00 	mov.b	#7,	r11	;#0x0007
    6f4c:	0d 11       	rra	r13		
    6f4e:	0c 10       	rrc	r12		
    6f50:	7b 53       	add.b	#-1,	r11	;r3 As==11
    6f52:	fc 23       	jnz	$-6      	;abs 0x6f4c
    6f54:	38 40 96 00 	mov	#150,	r8	;#0x0096
    6f58:	08 8c       	sub	r12,	r8	
    6f5a:	4b 48       	mov.b	r8,	r11	
    6f5c:	7b f0 1f 00 	and.b	#31,	r11	;#0x001f
    6f60:	2c 41       	mov	@r1,	r12	
    6f62:	1d 41 02 00 	mov	2(r1),	r13	;0x0002(r1)
    6f66:	4b 93       	tst.b	r11		
    6f68:	04 24       	jz	$+10     	;abs 0x6f72
    6f6a:	0d 11       	rra	r13		
    6f6c:	0c 10       	rrc	r12		
    6f6e:	7b 53       	add.b	#-1,	r11	;r3 As==11
    6f70:	fa 3f       	jmp	$-10     	;abs 0x6f66
    6f72:	78 f0 1f 00 	and.b	#31,	r8	;#0x001f
    6f76:	0a 4c       	mov	r12,	r10	
    6f78:	0b 4d       	mov	r13,	r11	
    6f7a:	48 93       	tst.b	r8		
    6f7c:	04 24       	jz	$+10     	;abs 0x6f86
    6f7e:	0a 5a       	rla	r10		
    6f80:	0b 6b       	rlc	r11		
    6f82:	78 53       	add.b	#-1,	r8	;r3 As==11
    6f84:	fa 3f       	jmp	$-10     	;abs 0x6f7a
    6f86:	2a 91       	cmp	@r1,	r10	
    6f88:	02 24       	jz	$+6      	;abs 0x6f8e
    6f8a:	80 00 9c 7a 	bra	#0x07a9c	
    6f8e:	1b 91 02 00 	cmp	2(r1),	r11	;0x0002(r1)
    6f92:	02 24       	jz	$+6      	;abs 0x6f98
    6f94:	80 00 9c 7a 	bra	#0x07a9c	
    6f98:	1c f3       	and	#1,	r12	;r3 As==01
    6f9a:	0d f3       	and	#0,	r13	;r3 As==00
    6f9c:	a1 43 04 00 	mov	#2,	4(r1)	;r3 As==10, 0x0004(r1)
    6fa0:	81 43 06 00 	mov	#0,	6(r1)	;r3 As==00, 0x0006(r1)
    6fa4:	81 8c 04 00 	sub	r12,	4(r1)	;0x0004(r1)
    6fa8:	81 7d 06 00 	subc	r13,	6(r1)	;0x0006(r1)
    6fac:	25 3c       	jmp	$+76     	;abs 0x6ff8
    6fae:	81 93 00 00 	tst	0(r1)		;0x0000(r1)
    6fb2:	22 20       	jnz	$+70     	;abs 0x6ff8
    6fb4:	b1 90 80 7f 	cmp	#32640,	2(r1)	;#0x7f80, 0x0002(r1)
    6fb8:	02 00 
    6fba:	1e 20       	jnz	$+62     	;abs 0x6ff8
    6fbc:	06 93       	tst	r6		
    6fbe:	0b 20       	jnz	$+24     	;abs 0x6fd6
    6fc0:	37 90 80 3f 	cmp	#16256,	r7	;#0x3f80
    6fc4:	08 20       	jnz	$+18     	;abs 0x6fd6
    6fc6:	0c 44       	mov	r4,	r12	
    6fc8:	0d 45       	mov	r5,	r13	
    6fca:	0e 44       	mov	r4,	r14	
    6fcc:	0f 45       	mov	r5,	r15	
    6fce:	b0 13 72 82 	calla	#0x08272	
    6fd2:	80 00 8e 7a 	bra	#0x07a8e	
    6fd6:	37 90 80 3f 	cmp	#16256,	r7	;#0x3f80
    6fda:	0b 38       	jl	$+24     	;abs 0x6ff2
    6fdc:	02 20       	jnz	$+6      	;abs 0x6fe2
    6fde:	16 93       	cmp	#1,	r6	;r3 As==01
    6fe0:	08 28       	jnc	$+18     	;abs 0x6ff2
    6fe2:	09 93       	tst	r9		
    6fe4:	02 38       	jl	$+6      	;abs 0x6fea
    6fe6:	80 00 a8 7a 	bra	#0x07aa8	
    6fea:	04 43       	clr	r4		
    6fec:	05 43       	clr	r5		
    6fee:	80 00 a8 7a 	bra	#0x07aa8	
    6ff2:	09 93       	tst	r9		
    6ff4:	fa 37       	jge	$-10     	;abs 0x6fea
    6ff6:	5f 3c       	jmp	$+192    	;abs 0x70b6
    6ff8:	81 93 00 00 	tst	0(r1)		;0x0000(r1)
    6ffc:	0e 20       	jnz	$+30     	;abs 0x701a
    6ffe:	b1 90 80 3f 	cmp	#16256,	2(r1)	;#0x3f80, 0x0002(r1)
    7002:	02 00 
    7004:	0a 20       	jnz	$+22     	;abs 0x701a
    7006:	09 93       	tst	r9		
    7008:	02 38       	jl	$+6      	;abs 0x700e
    700a:	80 00 8e 7a 	bra	#0x07a8e	
    700e:	0c 4e       	mov	r14,	r12	
    7010:	0d 4f       	mov	r15,	r13	
    7012:	0e 43       	clr	r14		
    7014:	3f 40 80 3f 	mov	#16256,	r15	;#0x3f80
    7018:	77 3c       	jmp	$+240    	;abs 0x7108
    701a:	81 93 0c 00 	tst	12(r1)		;0x000c(r1)
    701e:	10 20       	jnz	$+34     	;abs 0x7040
    7020:	39 90 00 40 	cmp	#16384,	r9	;#0x4000
    7024:	03 20       	jnz	$+8      	;abs 0x702c
    7026:	0c 4e       	mov	r14,	r12	
    7028:	0d 4f       	mov	r15,	r13	
    702a:	89 3c       	jmp	$+276    	;abs 0x713e
    702c:	39 90 00 3f 	cmp	#16128,	r9	;#0x3f00
    7030:	07 20       	jnz	$+16     	;abs 0x7040
    7032:	81 93 10 00 	tst	16(r1)		;0x0010(r1)
    7036:	04 38       	jl	$+10     	;abs 0x7040
    7038:	b0 13 22 7c 	calla	#0x07c22	
    703c:	80 00 8e 7a 	bra	#0x07a8e	
    7040:	0a 4e       	mov	r14,	r10	
    7042:	0b 4f       	mov	r15,	r11	
    7044:	3b f0 ff 7f 	and	#32767,	r11	;#0x7fff
    7048:	06 93       	tst	r6		
    704a:	03 20       	jnz	$+8      	;abs 0x7052
    704c:	37 90 80 7f 	cmp	#32640,	r7	;#0x7f80
    7050:	09 24       	jz	$+20     	;abs 0x7064
    7052:	06 93       	tst	r6		
    7054:	02 20       	jnz	$+6      	;abs 0x705a
    7056:	07 93       	tst	r7		
    7058:	05 24       	jz	$+12     	;abs 0x7064
    705a:	06 93       	tst	r6		
    705c:	30 20       	jnz	$+98     	;abs 0x70be
    705e:	37 90 80 3f 	cmp	#16256,	r7	;#0x3f80
    7062:	2d 20       	jnz	$+92     	;abs 0x70be
    7064:	09 93       	tst	r9		
    7066:	03 38       	jl	$+8      	;abs 0x706e
    7068:	0e 4a       	mov	r10,	r14	
    706a:	0f 4b       	mov	r11,	r15	
    706c:	07 3c       	jmp	$+16     	;abs 0x707c
    706e:	0c 4a       	mov	r10,	r12	
    7070:	0d 4b       	mov	r11,	r13	
    7072:	0e 43       	clr	r14		
    7074:	3f 40 80 3f 	mov	#16256,	r15	;#0x3f80
    7078:	b0 13 c0 84 	calla	#0x084c0	
    707c:	81 93 10 00 	tst	16(r1)		;0x0010(r1)
    7080:	02 38       	jl	$+6      	;abs 0x7086
    7082:	80 00 8e 7a 	bra	#0x07a8e	
    7086:	06 53       	add	#0,	r6	;r3 As==00
    7088:	37 60 80 c0 	addc	#-16256,r7	;#0xc080
    708c:	16 d1 04 00 	bis	4(r1),	r6	;0x0004(r1)
    7090:	17 d1 06 00 	bis	6(r1),	r7	;0x0006(r1)
    7094:	06 93       	tst	r6		
    7096:	03 20       	jnz	$+8      	;abs 0x709e
    7098:	07 93       	tst	r7		
    709a:	01 20       	jnz	$+4      	;abs 0x709e
    709c:	2f 3c       	jmp	$+96     	;abs 0x70fc
    709e:	04 4e       	mov	r14,	r4	
    70a0:	05 4f       	mov	r15,	r5	
    70a2:	91 93 04 00 	cmp	#1,	4(r1)	;r3 As==01, 0x0004(r1)
    70a6:	02 24       	jz	$+6      	;abs 0x70ac
    70a8:	80 00 a8 7a 	bra	#0x07aa8	
    70ac:	81 93 06 00 	tst	6(r1)		;0x0006(r1)
    70b0:	02 24       	jz	$+6      	;abs 0x70b6
    70b2:	80 00 a8 7a 	bra	#0x07aa8	
    70b6:	35 e0 00 80 	xor	#-32768,r5	;#0x8000
    70ba:	80 00 a8 7a 	bra	#0x07aa8	
    70be:	18 41 0a 00 	mov	10(r1),	r8	;0x000a(r1)
    70c2:	08 58       	rla	r8		
    70c4:	08 43       	clr	r8		
    70c6:	08 68       	rlc	r8		
    70c8:	81 48 08 00 	mov	r8,	8(r1)	;0x0008(r1)
    70cc:	81 43 0a 00 	mov	#0,	10(r1)	;r3 As==00, 0x000a(r1)
    70d0:	1c 41 08 00 	mov	8(r1),	r12	;0x0008(r1)
    70d4:	1d 41 0a 00 	mov	10(r1),	r13	;0x000a(r1)
    70d8:	3c 53       	add	#-1,	r12	;r3 As==11
    70da:	3d 63       	addc	#-1,	r13	;r3 As==11
    70dc:	81 4c 1c 00 	mov	r12,	28(r1)	;0x001c(r1)
    70e0:	81 4d 1e 00 	mov	r13,	30(r1)	;0x001e(r1)
    70e4:	1c 41 04 00 	mov	4(r1),	r12	;0x0004(r1)
    70e8:	1d 41 06 00 	mov	6(r1),	r13	;0x0006(r1)
    70ec:	1c d1 1c 00 	bis	28(r1),	r12	;0x001c(r1)
    70f0:	1d d1 1e 00 	bis	30(r1),	r13	;0x001e(r1)
    70f4:	0c 93       	tst	r12		
    70f6:	0c 20       	jnz	$+26     	;abs 0x7110
    70f8:	0d 93       	tst	r13		
    70fa:	0a 20       	jnz	$+22     	;abs 0x7110
    70fc:	0c 4e       	mov	r14,	r12	
    70fe:	0d 4f       	mov	r15,	r13	
    7100:	b0 13 72 82 	calla	#0x08272	
    7104:	0c 4e       	mov	r14,	r12	
    7106:	0d 4f       	mov	r15,	r13	
    7108:	b0 13 c0 84 	calla	#0x084c0	
    710c:	80 00 8e 7a 	bra	#0x07a8e	
    7110:	b1 90 00 4d 	cmp	#19712,	2(r1)	;#0x4d00, 0x0002(r1)
    7114:	02 00 
    7116:	90 38       	jl	$+290    	;abs 0x7238
    7118:	03 20       	jnz	$+8      	;abs 0x7120
    711a:	91 93 00 00 	cmp	#1,	0(r1)	;r3 As==01, 0x0000(r1)
    711e:	8c 28       	jnc	$+282    	;abs 0x7238
    7120:	37 90 7f 3f 	cmp	#16255,	r7	;#0x3f7f
    7124:	06 38       	jl	$+14     	;abs 0x7132
    7126:	37 90 80 3f 	cmp	#16256,	r7	;#0x3f80
    712a:	0d 34       	jge	$+28     	;abs 0x7146
    712c:	36 90 f8 ff 	cmp	#-8,	r6	;#0xfff8
    7130:	0a 2c       	jc	$+22     	;abs 0x7146
    7132:	09 93       	tst	r9		
    7134:	5a 37       	jge	$-330    	;abs 0x6fea
    7136:	3c 40 ca f2 	mov	#-3382,	r12	;#0xf2ca
    713a:	3d 40 49 71 	mov	#29001,	r13	;#0x7149
    713e:	0e 4c       	mov	r12,	r14	
    7140:	0f 4d       	mov	r13,	r15	
    7142:	80 00 8a 7a 	bra	#0x07a8a	
    7146:	37 90 80 3f 	cmp	#16256,	r7	;#0x3f80
    714a:	0b 38       	jl	$+24     	;abs 0x7162
    714c:	02 20       	jnz	$+6      	;abs 0x7152
    714e:	36 92       	cmp	#8,	r6	;r2 As==11
    7150:	08 28       	jnc	$+18     	;abs 0x7162
    7152:	09 93       	tst	r9		
    7154:	4a 3b       	jl	$-362    	;abs 0x6fea
    7156:	19 93       	cmp	#1,	r9	;r3 As==01
    7158:	ee 37       	jge	$-34     	;abs 0x7136
    715a:	91 93 0c 00 	cmp	#1,	12(r1)	;r3 As==01, 0x000c(r1)
    715e:	eb 2f       	jc	$-40     	;abs 0x7136
    7160:	44 3f       	jmp	$-374    	;abs 0x6fea
    7162:	0c 43       	clr	r12		
    7164:	3d 40 80 3f 	mov	#16256,	r13	;#0x3f80
    7168:	b0 13 72 82 	calla	#0x08272	
    716c:	0a 4e       	mov	r14,	r10	
    716e:	0b 4f       	mov	r15,	r11	
    7170:	3c 40 00 aa 	mov	#-22016,r12	;#0xaa00
    7174:	3d 40 b8 3f 	mov	#16312,	r13	;#0x3fb8
    7178:	b0 13 c2 82 	calla	#0x082c2	
    717c:	08 4e       	mov	r14,	r8	
    717e:	09 4f       	mov	r15,	r9	
    7180:	3c 40 70 a5 	mov	#-23184,r12	;#0xa570
    7184:	3d 40 ec 36 	mov	#14060,	r13	;#0x36ec
    7188:	0e 4a       	mov	r10,	r14	
    718a:	0f 4b       	mov	r11,	r15	
    718c:	b0 13 c2 82 	calla	#0x082c2	
    7190:	81 4e 00 00 	mov	r14,	0(r1)	;0x0000(r1)
    7194:	81 4f 02 00 	mov	r15,	2(r1)	;0x0002(r1)
    7198:	0c 4a       	mov	r10,	r12	
    719a:	0d 4b       	mov	r11,	r13	
    719c:	0e 4a       	mov	r10,	r14	
    719e:	0f 4b       	mov	r11,	r15	
    71a0:	b0 13 c2 82 	calla	#0x082c2	
    71a4:	06 4e       	mov	r14,	r6	
    71a6:	07 4f       	mov	r15,	r7	
    71a8:	0c 43       	clr	r12		
    71aa:	3d 40 80 3e 	mov	#16000,	r13	;#0x3e80
    71ae:	0e 4a       	mov	r10,	r14	
    71b0:	0f 4b       	mov	r11,	r15	
    71b2:	b0 13 c2 82 	calla	#0x082c2	
    71b6:	0c 4e       	mov	r14,	r12	
    71b8:	0d 4f       	mov	r15,	r13	
    71ba:	3e 40 ab aa 	mov	#-21845,r14	;#0xaaab
    71be:	3f 40 aa 3e 	mov	#16042,	r15	;#0x3eaa
    71c2:	b0 13 72 82 	calla	#0x08272	
    71c6:	0c 4e       	mov	r14,	r12	
    71c8:	0d 4f       	mov	r15,	r13	
    71ca:	0e 4a       	mov	r10,	r14	
    71cc:	0f 4b       	mov	r11,	r15	
    71ce:	b0 13 c2 82 	calla	#0x082c2	
    71d2:	0c 4e       	mov	r14,	r12	
    71d4:	0d 4f       	mov	r15,	r13	
    71d6:	0e 43       	clr	r14		
    71d8:	3f 40 00 3f 	mov	#16128,	r15	;#0x3f00
    71dc:	b0 13 72 82 	calla	#0x08272	
    71e0:	0c 4e       	mov	r14,	r12	
    71e2:	0d 4f       	mov	r15,	r13	
    71e4:	0e 46       	mov	r6,	r14	
    71e6:	0f 47       	mov	r7,	r15	
    71e8:	b0 13 c2 82 	calla	#0x082c2	
    71ec:	3c 40 3b aa 	mov	#-21957,r12	;#0xaa3b
    71f0:	3d 40 b8 3f 	mov	#16312,	r13	;#0x3fb8
    71f4:	b0 13 c2 82 	calla	#0x082c2	
    71f8:	0c 4e       	mov	r14,	r12	
    71fa:	0d 4f       	mov	r15,	r13	
    71fc:	2e 41       	mov	@r1,	r14	
    71fe:	1f 41 02 00 	mov	2(r1),	r15	;0x0002(r1)
    7202:	b0 13 72 82 	calla	#0x08272	
    7206:	0a 4e       	mov	r14,	r10	
    7208:	0b 4f       	mov	r15,	r11	
    720a:	0c 4e       	mov	r14,	r12	
    720c:	0d 4f       	mov	r15,	r13	
    720e:	0e 48       	mov	r8,	r14	
    7210:	0f 49       	mov	r9,	r15	
    7212:	b0 13 26 82 	calla	#0x08226	
    7216:	3e f0 00 f0 	and	#-4096,	r14	;#0xf000
    721a:	3f f3       	and	#-1,	r15	;r3 As==11
    721c:	81 4e 08 00 	mov	r14,	8(r1)	;0x0008(r1)
    7220:	81 4f 0a 00 	mov	r15,	10(r1)	;0x000a(r1)
    7224:	0c 48       	mov	r8,	r12	
    7226:	0d 49       	mov	r9,	r13	
    7228:	b0 13 72 82 	calla	#0x08272	
    722c:	0c 4e       	mov	r14,	r12	
    722e:	0d 4f       	mov	r15,	r13	
    7230:	0e 4a       	mov	r10,	r14	
    7232:	0f 4b       	mov	r11,	r15	
    7234:	80 00 40 76 	bra	#0x07640	
    7238:	37 90 80 00 	cmp	#128,	r7	;#0x0080
    723c:	03 38       	jl	$+8      	;abs 0x7244
    723e:	0e 43       	clr	r14		
    7240:	0f 43       	clr	r15		
    7242:	0c 3c       	jmp	$+26     	;abs 0x725c
    7244:	0c 43       	clr	r12		
    7246:	3d 40 80 4b 	mov	#19328,	r13	;#0x4b80
    724a:	0e 4a       	mov	r10,	r14	
    724c:	0f 4b       	mov	r11,	r15	
    724e:	b0 13 c2 82 	calla	#0x082c2	
    7252:	06 4e       	mov	r14,	r6	
    7254:	07 4f       	mov	r15,	r7	
    7256:	3e 40 e8 ff 	mov	#-24,	r14	;#0xffe8
    725a:	3f 43       	mov	#-1,	r15	;r3 As==11
    725c:	0c 47       	mov	r7,	r12	
    725e:	0d 47       	mov	r7,	r13	
    7260:	8d 10       	swpb	r13		
    7262:	8d 11       	sxt	r13		
    7264:	8d 10       	swpb	r13		
    7266:	8d 11       	sxt	r13		
    7268:	7b 40 07 00 	mov.b	#7,	r11	;#0x0007
    726c:	0d 11       	rra	r13		
    726e:	0c 10       	rrc	r12		
    7270:	7b 53       	add.b	#-1,	r11	;r3 As==11
    7272:	fc 23       	jnz	$-6      	;abs 0x726c
    7274:	0a 4c       	mov	r12,	r10	
    7276:	0b 4d       	mov	r13,	r11	
    7278:	3a 50 81 ff 	add	#-127,	r10	;#0xff81
    727c:	3b 63       	addc	#-1,	r11	;r3 As==11
    727e:	0a 5e       	add	r14,	r10	
    7280:	0b 6f       	addc	r15,	r11	
    7282:	81 4a 10 00 	mov	r10,	16(r1)	;0x0010(r1)
    7286:	81 4b 12 00 	mov	r11,	18(r1)	;0x0012(r1)
    728a:	36 f3       	and	#-1,	r6	;r3 As==11
    728c:	37 f0 7f 00 	and	#127,	r7	;#0x007f
    7290:	0a 46       	mov	r6,	r10	
    7292:	0b 47       	mov	r7,	r11	
    7294:	0a d3       	bis	#0,	r10	;r3 As==00
    7296:	3b d0 80 3f 	bis	#16256,	r11	;#0x3f80
    729a:	37 90 1c 00 	cmp	#28,	r7	;#0x001c
    729e:	12 38       	jl	$+38     	;abs 0x72c4
    72a0:	03 20       	jnz	$+8      	;abs 0x72a8
    72a2:	36 90 72 c4 	cmp	#-15246,r6	;#0xc472
    72a6:	0e 28       	jnc	$+30     	;abs 0x72c4
    72a8:	37 90 5d 00 	cmp	#93,	r7	;#0x005d
    72ac:	10 38       	jl	$+34     	;abs 0x72ce
    72ae:	03 20       	jnz	$+8      	;abs 0x72b6
    72b0:	36 90 d7 b3 	cmp	#-19497,r6	;#0xb3d7
    72b4:	0c 28       	jnc	$+26     	;abs 0x72ce
    72b6:	91 53 10 00 	inc	16(r1)		;0x0010(r1)
    72ba:	81 63 12 00 	adc	18(r1)		;0x0012(r1)
    72be:	0a 53       	add	#0,	r10	;r3 As==00
    72c0:	3b 60 80 ff 	addc	#-128,	r11	;#0xff80
    72c4:	81 43 08 00 	mov	#0,	8(r1)	;r3 As==00, 0x0008(r1)
    72c8:	81 43 0a 00 	mov	#0,	10(r1)	;r3 As==00, 0x000a(r1)
    72cc:	04 3c       	jmp	$+10     	;abs 0x72d6
    72ce:	91 43 08 00 	mov	#1,	8(r1)	;r3 As==01, 0x0008(r1)
    72d2:	81 43 0a 00 	mov	#0,	10(r1)	;r3 As==00, 0x000a(r1)
    72d6:	81 4a 20 00 	mov	r10,	32(r1)	;0x0020(r1)
    72da:	81 4b 22 00 	mov	r11,	34(r1)	;0x0022(r1)
    72de:	1f 41 08 00 	mov	8(r1),	r15	;0x0008(r1)
    72e2:	5f 06       	rlam	#2,	r15	
    72e4:	18 4f f8 99 	mov	-26120(r15),r8	;0x99f8(r15)
    72e8:	19 4f fa 99 	mov	-26118(r15),r9	;0x99fa(r15)
    72ec:	0c 48       	mov	r8,	r12	
    72ee:	0d 49       	mov	r9,	r13	
    72f0:	0e 4a       	mov	r10,	r14	
    72f2:	0f 4b       	mov	r11,	r15	
    72f4:	b0 13 72 82 	calla	#0x08272	
    72f8:	06 4e       	mov	r14,	r6	
    72fa:	07 4f       	mov	r15,	r7	
    72fc:	0c 48       	mov	r8,	r12	
    72fe:	0d 49       	mov	r9,	r13	
    7300:	0e 4a       	mov	r10,	r14	
    7302:	0f 4b       	mov	r11,	r15	
    7304:	b0 13 26 82 	calla	#0x08226	
    7308:	0c 4e       	mov	r14,	r12	
    730a:	0d 4f       	mov	r15,	r13	
    730c:	0e 43       	clr	r14		
    730e:	3f 40 80 3f 	mov	#16256,	r15	;#0x3f80
    7312:	b0 13 c0 84 	calla	#0x084c0	
    7316:	81 4e 18 00 	mov	r14,	24(r1)	;0x0018(r1)
    731a:	81 4f 1a 00 	mov	r15,	26(r1)	;0x001a(r1)
    731e:	0c 4e       	mov	r14,	r12	
    7320:	0d 4f       	mov	r15,	r13	
    7322:	0e 46       	mov	r6,	r14	
    7324:	0f 47       	mov	r7,	r15	
    7326:	b0 13 c2 82 	calla	#0x082c2	
    732a:	81 4e 0c 00 	mov	r14,	12(r1)	;0x000c(r1)
    732e:	81 4f 0e 00 	mov	r15,	14(r1)	;0x000e(r1)
    7332:	1e 41 0c 00 	mov	12(r1),	r14	;0x000c(r1)
    7336:	1f 41 0e 00 	mov	14(r1),	r15	;0x000e(r1)
    733a:	3e f0 00 f0 	and	#-4096,	r14	;#0xf000
    733e:	3f f3       	and	#-1,	r15	;r3 As==11
    7340:	81 4e 00 00 	mov	r14,	0(r1)	;0x0000(r1)
    7344:	81 4f 02 00 	mov	r15,	2(r1)	;0x0002(r1)
    7348:	0b 11       	rra	r11		
    734a:	0a 10       	rrc	r10		
    734c:	0a d3       	bis	#0,	r10	;r3 As==00
    734e:	3b d0 00 20 	bis	#8192,	r11	;#0x2000
    7352:	0a 53       	add	#0,	r10	;r3 As==00
    7354:	2b 62       	addc	#4,	r11	;r2 As==10
    7356:	0e 43       	clr	r14		
    7358:	0f 43       	clr	r15		
    735a:	1f 41 08 00 	mov	8(r1),	r15	;0x0008(r1)
    735e:	7d 40 05 00 	mov.b	#5,	r13	;#0x0005
    7362:	0e 5e       	rla	r14		
    7364:	0f 6f       	rlc	r15		
    7366:	7d 53       	add.b	#-1,	r13	;r3 As==11
    7368:	fc 23       	jnz	$-6      	;abs 0x7362
    736a:	0a 5e       	add	r14,	r10	
    736c:	0b 6f       	addc	r15,	r11	
    736e:	0c 4a       	mov	r10,	r12	
    7370:	0d 4b       	mov	r11,	r13	
    7372:	2e 41       	mov	@r1,	r14	
    7374:	1f 41 02 00 	mov	2(r1),	r15	;0x0002(r1)
    7378:	b0 13 c2 82 	calla	#0x082c2	
    737c:	0c 4e       	mov	r14,	r12	
    737e:	0d 4f       	mov	r15,	r13	
    7380:	0e 46       	mov	r6,	r14	
    7382:	0f 47       	mov	r7,	r15	
    7384:	b0 13 72 82 	calla	#0x08272	
    7388:	06 4e       	mov	r14,	r6	
    738a:	07 4f       	mov	r15,	r7	
    738c:	0c 48       	mov	r8,	r12	
    738e:	0d 49       	mov	r9,	r13	
    7390:	0e 4a       	mov	r10,	r14	
    7392:	0f 4b       	mov	r11,	r15	
    7394:	b0 13 72 82 	calla	#0x08272	
    7398:	0c 4e       	mov	r14,	r12	
    739a:	0d 4f       	mov	r15,	r13	
    739c:	1e 41 20 00 	mov	32(r1),	r14	;0x0020(r1)
    73a0:	1f 41 22 00 	mov	34(r1),	r15	;0x0022(r1)
    73a4:	b0 13 72 82 	calla	#0x08272	
    73a8:	0c 4e       	mov	r14,	r12	
    73aa:	0d 4f       	mov	r15,	r13	
    73ac:	2e 41       	mov	@r1,	r14	
    73ae:	1f 41 02 00 	mov	2(r1),	r15	;0x0002(r1)
    73b2:	b0 13 c2 82 	calla	#0x082c2	
    73b6:	0c 4e       	mov	r14,	r12	
    73b8:	0d 4f       	mov	r15,	r13	
    73ba:	0e 46       	mov	r6,	r14	
    73bc:	0f 47       	mov	r7,	r15	
    73be:	b0 13 72 82 	calla	#0x08272	
    73c2:	0c 4e       	mov	r14,	r12	
    73c4:	0d 4f       	mov	r15,	r13	
    73c6:	1e 41 18 00 	mov	24(r1),	r14	;0x0018(r1)
    73ca:	1f 41 1a 00 	mov	26(r1),	r15	;0x001a(r1)
    73ce:	b0 13 c2 82 	calla	#0x082c2	
    73d2:	06 4e       	mov	r14,	r6	
    73d4:	07 4f       	mov	r15,	r7	
    73d6:	1c 41 0c 00 	mov	12(r1),	r12	;0x000c(r1)
    73da:	1d 41 0e 00 	mov	14(r1),	r13	;0x000e(r1)
    73de:	0e 4c       	mov	r12,	r14	
    73e0:	0f 4d       	mov	r13,	r15	
    73e2:	b0 13 c2 82 	calla	#0x082c2	
    73e6:	0a 4e       	mov	r14,	r10	
    73e8:	0b 4f       	mov	r15,	r11	
    73ea:	0c 4e       	mov	r14,	r12	
    73ec:	0d 4f       	mov	r15,	r13	
    73ee:	b0 13 c2 82 	calla	#0x082c2	
    73f2:	08 4e       	mov	r14,	r8	
    73f4:	09 4f       	mov	r15,	r9	
    73f6:	3c 40 42 f1 	mov	#-3774,	r12	;#0xf142
    73fa:	3d 40 53 3e 	mov	#15955,	r13	;#0x3e53
    73fe:	0e 4a       	mov	r10,	r14	
    7400:	0f 4b       	mov	r11,	r15	
    7402:	b0 13 c2 82 	calla	#0x082c2	
    7406:	3c 40 55 32 	mov	#12885,	r12	;#0x3255
    740a:	3d 40 6c 3e 	mov	#15980,	r13	;#0x3e6c
    740e:	b0 13 26 82 	calla	#0x08226	
    7412:	0c 4e       	mov	r14,	r12	
    7414:	0d 4f       	mov	r15,	r13	
    7416:	0e 4a       	mov	r10,	r14	
    7418:	0f 4b       	mov	r11,	r15	
    741a:	b0 13 c2 82 	calla	#0x082c2	
    741e:	3c 40 05 a3 	mov	#-23803,r12	;#0xa305
    7422:	3d 40 8b 3e 	mov	#16011,	r13	;#0x3e8b
    7426:	b0 13 26 82 	calla	#0x08226	
    742a:	0c 4e       	mov	r14,	r12	
    742c:	0d 4f       	mov	r15,	r13	
    742e:	0e 4a       	mov	r10,	r14	
    7430:	0f 4b       	mov	r11,	r15	
    7432:	b0 13 c2 82 	calla	#0x082c2	
    7436:	3c 40 ab aa 	mov	#-21845,r12	;#0xaaab
    743a:	3d 40 aa 3e 	mov	#16042,	r13	;#0x3eaa
    743e:	b0 13 26 82 	calla	#0x08226	
    7442:	0c 4e       	mov	r14,	r12	
    7444:	0d 4f       	mov	r15,	r13	
    7446:	0e 4a       	mov	r10,	r14	
    7448:	0f 4b       	mov	r11,	r15	
    744a:	b0 13 c2 82 	calla	#0x082c2	
    744e:	3c 40 b7 6d 	mov	#28087,	r12	;#0x6db7
    7452:	3d 40 db 3e 	mov	#16091,	r13	;#0x3edb
    7456:	b0 13 26 82 	calla	#0x08226	
    745a:	0c 4e       	mov	r14,	r12	
    745c:	0d 4f       	mov	r15,	r13	
    745e:	0e 4a       	mov	r10,	r14	
    7460:	0f 4b       	mov	r11,	r15	
    7462:	b0 13 c2 82 	calla	#0x082c2	
    7466:	3c 40 9a 99 	mov	#-26214,r12	;#0x999a
    746a:	3d 40 19 3f 	mov	#16153,	r13	;#0x3f19
    746e:	b0 13 26 82 	calla	#0x08226	
    7472:	0c 4e       	mov	r14,	r12	
    7474:	0d 4f       	mov	r15,	r13	
    7476:	0e 48       	mov	r8,	r14	
    7478:	0f 49       	mov	r9,	r15	
    747a:	b0 13 c2 82 	calla	#0x082c2	
    747e:	0a 4e       	mov	r14,	r10	
    7480:	0b 4f       	mov	r15,	r11	
    7482:	1c 41 0c 00 	mov	12(r1),	r12	;0x000c(r1)
    7486:	1d 41 0e 00 	mov	14(r1),	r13	;0x000e(r1)
    748a:	2e 41       	mov	@r1,	r14	
    748c:	1f 41 02 00 	mov	2(r1),	r15	;0x0002(r1)
    7490:	b0 13 26 82 	calla	#0x08226	
    7494:	0c 4e       	mov	r14,	r12	
    7496:	0d 4f       	mov	r15,	r13	
    7498:	0e 46       	mov	r6,	r14	
    749a:	0f 47       	mov	r7,	r15	
    749c:	b0 13 c2 82 	calla	#0x082c2	
    74a0:	0c 4e       	mov	r14,	r12	
    74a2:	0d 4f       	mov	r15,	r13	
    74a4:	0e 4a       	mov	r10,	r14	
    74a6:	0f 4b       	mov	r11,	r15	
    74a8:	b0 13 26 82 	calla	#0x08226	
    74ac:	08 4e       	mov	r14,	r8	
    74ae:	09 4f       	mov	r15,	r9	
    74b0:	2c 41       	mov	@r1,	r12	
    74b2:	1d 41 02 00 	mov	2(r1),	r13	;0x0002(r1)
    74b6:	0e 4c       	mov	r12,	r14	
    74b8:	0f 4d       	mov	r13,	r15	
    74ba:	b0 13 c2 82 	calla	#0x082c2	
    74be:	81 4e 18 00 	mov	r14,	24(r1)	;0x0018(r1)
    74c2:	81 4f 1a 00 	mov	r15,	26(r1)	;0x001a(r1)
    74c6:	0c 43       	clr	r12		
    74c8:	3d 40 40 40 	mov	#16448,	r13	;#0x4040
    74cc:	b0 13 26 82 	calla	#0x08226	
    74d0:	0c 48       	mov	r8,	r12	
    74d2:	0d 49       	mov	r9,	r13	
    74d4:	b0 13 26 82 	calla	#0x08226	
    74d8:	0a 4e       	mov	r14,	r10	
    74da:	0b 4f       	mov	r15,	r11	
    74dc:	3a f0 00 f0 	and	#-4096,	r10	;#0xf000
    74e0:	3b f3       	and	#-1,	r11	;r3 As==11
    74e2:	0c 4a       	mov	r10,	r12	
    74e4:	0d 4b       	mov	r11,	r13	
    74e6:	2e 41       	mov	@r1,	r14	
    74e8:	1f 41 02 00 	mov	2(r1),	r15	;0x0002(r1)
    74ec:	b0 13 c2 82 	calla	#0x082c2	
    74f0:	81 4e 00 00 	mov	r14,	0(r1)	;0x0000(r1)
    74f4:	81 4f 02 00 	mov	r15,	2(r1)	;0x0002(r1)
    74f8:	0c 4a       	mov	r10,	r12	
    74fa:	0d 4b       	mov	r11,	r13	
    74fc:	0e 46       	mov	r6,	r14	
    74fe:	0f 47       	mov	r7,	r15	
    7500:	b0 13 c2 82 	calla	#0x082c2	
    7504:	06 4e       	mov	r14,	r6	
    7506:	07 4f       	mov	r15,	r7	
    7508:	0c 43       	clr	r12		
    750a:	3d 40 40 40 	mov	#16448,	r13	;#0x4040
    750e:	0e 4a       	mov	r10,	r14	
    7510:	0f 4b       	mov	r11,	r15	
    7512:	b0 13 72 82 	calla	#0x08272	
    7516:	1c 41 18 00 	mov	24(r1),	r12	;0x0018(r1)
    751a:	1d 41 1a 00 	mov	26(r1),	r13	;0x001a(r1)
    751e:	b0 13 72 82 	calla	#0x08272	
    7522:	0c 4e       	mov	r14,	r12	
    7524:	0d 4f       	mov	r15,	r13	
    7526:	0e 48       	mov	r8,	r14	
    7528:	0f 49       	mov	r9,	r15	
    752a:	b0 13 72 82 	calla	#0x08272	
    752e:	1c 41 0c 00 	mov	12(r1),	r12	;0x000c(r1)
    7532:	1d 41 0e 00 	mov	14(r1),	r13	;0x000e(r1)
    7536:	b0 13 c2 82 	calla	#0x082c2	
    753a:	0c 4e       	mov	r14,	r12	
    753c:	0d 4f       	mov	r15,	r13	
    753e:	0e 46       	mov	r6,	r14	
    7540:	0f 47       	mov	r7,	r15	
    7542:	b0 13 26 82 	calla	#0x08226	
    7546:	08 4e       	mov	r14,	r8	
    7548:	09 4f       	mov	r15,	r9	
    754a:	0c 4e       	mov	r14,	r12	
    754c:	0d 4f       	mov	r15,	r13	
    754e:	2e 41       	mov	@r1,	r14	
    7550:	1f 41 02 00 	mov	2(r1),	r15	;0x0002(r1)
    7554:	b0 13 26 82 	calla	#0x08226	
    7558:	0a 4e       	mov	r14,	r10	
    755a:	0b 4f       	mov	r15,	r11	
    755c:	3a f0 00 f0 	and	#-4096,	r10	;#0xf000
    7560:	3b f3       	and	#-1,	r11	;r3 As==11
    7562:	3c 40 00 38 	mov	#14336,	r12	;#0x3800
    7566:	3d 40 76 3f 	mov	#16246,	r13	;#0x3f76
    756a:	0e 4a       	mov	r10,	r14	
    756c:	0f 4b       	mov	r11,	r15	
    756e:	b0 13 c2 82 	calla	#0x082c2	
    7572:	81 4e 0c 00 	mov	r14,	12(r1)	;0x000c(r1)
    7576:	81 4f 0e 00 	mov	r15,	14(r1)	;0x000e(r1)
    757a:	3c 40 a0 c3 	mov	#-15456,r12	;#0xc3a0
    757e:	3d 40 9d 36 	mov	#13981,	r13	;#0x369d
    7582:	0e 4a       	mov	r10,	r14	
    7584:	0f 4b       	mov	r11,	r15	
    7586:	b0 13 c2 82 	calla	#0x082c2	
    758a:	06 4e       	mov	r14,	r6	
    758c:	07 4f       	mov	r15,	r7	
    758e:	2c 41       	mov	@r1,	r12	
    7590:	1d 41 02 00 	mov	2(r1),	r13	;0x0002(r1)
    7594:	0e 4a       	mov	r10,	r14	
    7596:	0f 4b       	mov	r11,	r15	
    7598:	b0 13 72 82 	calla	#0x08272	
    759c:	0c 4e       	mov	r14,	r12	
    759e:	0d 4f       	mov	r15,	r13	
    75a0:	0e 48       	mov	r8,	r14	
    75a2:	0f 49       	mov	r9,	r15	
    75a4:	b0 13 72 82 	calla	#0x08272	
    75a8:	3c 40 4f 38 	mov	#14415,	r12	;#0x384f
    75ac:	3d 40 76 3f 	mov	#16246,	r13	;#0x3f76
    75b0:	b0 13 c2 82 	calla	#0x082c2	
    75b4:	0c 4e       	mov	r14,	r12	
    75b6:	0d 4f       	mov	r15,	r13	
    75b8:	0e 46       	mov	r6,	r14	
    75ba:	0f 47       	mov	r7,	r15	
    75bc:	b0 13 26 82 	calla	#0x08226	
    75c0:	1b 41 08 00 	mov	8(r1),	r11	;0x0008(r1)
    75c4:	5b 06       	rlam	#2,	r11	
    75c6:	1c 4b 00 9a 	mov	-26112(r11),r12	;0x9a00(r11)
    75ca:	1d 4b 02 9a 	mov	-26110(r11),r13	;0x9a02(r11)
    75ce:	b0 13 26 82 	calla	#0x08226	
    75d2:	06 4e       	mov	r14,	r6	
    75d4:	07 4f       	mov	r15,	r7	
    75d6:	1e 41 10 00 	mov	16(r1),	r14	;0x0010(r1)
    75da:	1f 41 12 00 	mov	18(r1),	r15	;0x0012(r1)
    75de:	b0 13 ec 86 	calla	#0x086ec	
    75e2:	08 4e       	mov	r14,	r8	
    75e4:	09 4f       	mov	r15,	r9	
    75e6:	1a 4b 08 9a 	mov	-26104(r11),r10	;0x9a08(r11)
    75ea:	1b 4b 0a 9a 	mov	-26102(r11),r11	;0x9a0a(r11)
    75ee:	0c 46       	mov	r6,	r12	
    75f0:	0d 47       	mov	r7,	r13	
    75f2:	1e 41 0c 00 	mov	12(r1),	r14	;0x000c(r1)
    75f6:	1f 41 0e 00 	mov	14(r1),	r15	;0x000e(r1)
    75fa:	b0 13 26 82 	calla	#0x08226	
    75fe:	0c 4a       	mov	r10,	r12	
    7600:	0d 4b       	mov	r11,	r13	
    7602:	b0 13 26 82 	calla	#0x08226	
    7606:	0c 48       	mov	r8,	r12	
    7608:	0d 49       	mov	r9,	r13	
    760a:	b0 13 26 82 	calla	#0x08226	
    760e:	3e f0 00 f0 	and	#-4096,	r14	;#0xf000
    7612:	3f f3       	and	#-1,	r15	;r3 As==11
    7614:	81 4e 08 00 	mov	r14,	8(r1)	;0x0008(r1)
    7618:	81 4f 0a 00 	mov	r15,	10(r1)	;0x000a(r1)
    761c:	0c 48       	mov	r8,	r12	
    761e:	0d 49       	mov	r9,	r13	
    7620:	b0 13 72 82 	calla	#0x08272	
    7624:	0c 4a       	mov	r10,	r12	
    7626:	0d 4b       	mov	r11,	r13	
    7628:	b0 13 72 82 	calla	#0x08272	
    762c:	1c 41 0c 00 	mov	12(r1),	r12	;0x000c(r1)
    7630:	1d 41 0e 00 	mov	14(r1),	r13	;0x000e(r1)
    7634:	b0 13 72 82 	calla	#0x08272	
    7638:	0c 4e       	mov	r14,	r12	
    763a:	0d 4f       	mov	r15,	r13	
    763c:	0e 46       	mov	r6,	r14	
    763e:	0f 47       	mov	r7,	r15	
    7640:	b0 13 72 82 	calla	#0x08272	
    7644:	08 4e       	mov	r14,	r8	
    7646:	09 4f       	mov	r15,	r9	
    7648:	1e 41 04 00 	mov	4(r1),	r14	;0x0004(r1)
    764c:	1f 41 06 00 	mov	6(r1),	r15	;0x0006(r1)
    7650:	3e 53       	add	#-1,	r14	;r3 As==11
    7652:	3f 63       	addc	#-1,	r15	;r3 As==11
    7654:	1e d1 1c 00 	bis	28(r1),	r14	;0x001c(r1)
    7658:	1f d1 1e 00 	bis	30(r1),	r15	;0x001e(r1)
    765c:	0e 93       	tst	r14		
    765e:	08 20       	jnz	$+18     	;abs 0x7670
    7660:	0f 93       	tst	r15		
    7662:	06 20       	jnz	$+14     	;abs 0x7670
    7664:	81 43 00 00 	mov	#0,	0(r1)	;r3 As==00, 0x0000(r1)
    7668:	b1 40 80 bf 	mov	#-16512,2(r1)	;#0xbf80, 0x0002(r1)
    766c:	02 00 
    766e:	05 3c       	jmp	$+12     	;abs 0x767a
    7670:	81 43 00 00 	mov	#0,	0(r1)	;r3 As==00, 0x0000(r1)
    7674:	b1 40 80 3f 	mov	#16256,	2(r1)	;#0x3f80, 0x0002(r1)
    7678:	02 00 
    767a:	1a 41 14 00 	mov	20(r1),	r10	;0x0014(r1)
    767e:	1b 41 16 00 	mov	22(r1),	r11	;0x0016(r1)
    7682:	3a f0 00 f0 	and	#-4096,	r10	;#0xf000
    7686:	3b f3       	and	#-1,	r11	;r3 As==11
    7688:	0c 4a       	mov	r10,	r12	
    768a:	0d 4b       	mov	r11,	r13	
    768c:	0e 44       	mov	r4,	r14	
    768e:	0f 45       	mov	r5,	r15	
    7690:	b0 13 72 82 	calla	#0x08272	
    7694:	1c 41 08 00 	mov	8(r1),	r12	;0x0008(r1)
    7698:	1d 41 0a 00 	mov	10(r1),	r13	;0x000a(r1)
    769c:	b0 13 c2 82 	calla	#0x082c2	
    76a0:	06 4e       	mov	r14,	r6	
    76a2:	07 4f       	mov	r15,	r7	
    76a4:	0c 48       	mov	r8,	r12	
    76a6:	0d 49       	mov	r9,	r13	
    76a8:	0e 44       	mov	r4,	r14	
    76aa:	0f 45       	mov	r5,	r15	
    76ac:	b0 13 c2 82 	calla	#0x082c2	
    76b0:	0c 4e       	mov	r14,	r12	
    76b2:	0d 4f       	mov	r15,	r13	
    76b4:	0e 46       	mov	r6,	r14	
    76b6:	0f 47       	mov	r7,	r15	
    76b8:	b0 13 26 82 	calla	#0x08226	
    76bc:	81 4e 04 00 	mov	r14,	4(r1)	;0x0004(r1)
    76c0:	81 4f 06 00 	mov	r15,	6(r1)	;0x0006(r1)
    76c4:	1c 41 08 00 	mov	8(r1),	r12	;0x0008(r1)
    76c8:	1d 41 0a 00 	mov	10(r1),	r13	;0x000a(r1)
    76cc:	0e 4a       	mov	r10,	r14	
    76ce:	0f 4b       	mov	r11,	r15	
    76d0:	b0 13 c2 82 	calla	#0x082c2	
    76d4:	06 4e       	mov	r14,	r6	
    76d6:	07 4f       	mov	r15,	r7	
    76d8:	0c 4e       	mov	r14,	r12	
    76da:	0d 4f       	mov	r15,	r13	
    76dc:	1e 41 04 00 	mov	4(r1),	r14	;0x0004(r1)
    76e0:	1f 41 06 00 	mov	6(r1),	r15	;0x0006(r1)
    76e4:	b0 13 26 82 	calla	#0x08226	
    76e8:	04 4e       	mov	r14,	r4	
    76ea:	05 4f       	mov	r15,	r5	
    76ec:	08 4e       	mov	r14,	r8	
    76ee:	09 4f       	mov	r15,	r9	
    76f0:	0a 4e       	mov	r14,	r10	
    76f2:	0b 4f       	mov	r15,	r11	
    76f4:	3a f3       	and	#-1,	r10	;r3 As==11
    76f6:	3b f0 ff 7f 	and	#32767,	r11	;#0x7fff
    76fa:	09 93       	tst	r9		
    76fc:	3d 38       	jl	$+124    	;abs 0x7778
    76fe:	02 20       	jnz	$+6      	;abs 0x7704
    7700:	1e 93       	cmp	#1,	r14	;r3 As==01
    7702:	3a 28       	jnc	$+118    	;abs 0x7778
    7704:	3b 90 00 43 	cmp	#17152,	r11	;#0x4300
    7708:	04 38       	jl	$+10     	;abs 0x7712
    770a:	27 20       	jnz	$+80     	;abs 0x775a
    770c:	1a 93       	cmp	#1,	r10	;r3 As==01
    770e:	01 28       	jnc	$+4      	;abs 0x7712
    7710:	24 3c       	jmp	$+74     	;abs 0x775a
    7712:	0a 93       	tst	r10		
    7714:	5d 20       	jnz	$+188    	;abs 0x77d0
    7716:	3b 90 00 43 	cmp	#17152,	r11	;#0x4300
    771a:	5a 20       	jnz	$+182    	;abs 0x77d0
    771c:	3c 40 3c aa 	mov	#-21956,r12	;#0xaa3c
    7720:	3d 40 38 33 	mov	#13112,	r13	;#0x3338
    7724:	1e 41 04 00 	mov	4(r1),	r14	;0x0004(r1)
    7728:	1f 41 06 00 	mov	6(r1),	r15	;0x0006(r1)
    772c:	b0 13 26 82 	calla	#0x08226	
    7730:	81 4e 08 00 	mov	r14,	8(r1)	;0x0008(r1)
    7734:	81 4f 0a 00 	mov	r15,	10(r1)	;0x000a(r1)
    7738:	0c 46       	mov	r6,	r12	
    773a:	0d 47       	mov	r7,	r13	
    773c:	0e 44       	mov	r4,	r14	
    773e:	0f 45       	mov	r5,	r15	
    7740:	b0 13 72 82 	calla	#0x08272	
    7744:	0c 4e       	mov	r14,	r12	
    7746:	0d 4f       	mov	r15,	r13	
    7748:	1e 41 08 00 	mov	8(r1),	r14	;0x0008(r1)
    774c:	1f 41 0a 00 	mov	10(r1),	r15	;0x000a(r1)
    7750:	b0 13 02 86 	calla	#0x08602	
    7754:	0f 93       	tst	r15		
    7756:	42 24       	jz	$+134    	;abs 0x77dc
    7758:	41 38       	jl	$+132    	;abs 0x77dc
    775a:	3c 40 ca f2 	mov	#-3382,	r12	;#0xf2ca
    775e:	3d 40 49 71 	mov	#29001,	r13	;#0x7149
    7762:	2e 41       	mov	@r1,	r14	
    7764:	1f 41 02 00 	mov	2(r1),	r15	;0x0002(r1)
    7768:	b0 13 c2 82 	calla	#0x082c2	
    776c:	3c 40 ca f2 	mov	#-3382,	r12	;#0xf2ca
    7770:	3d 40 49 71 	mov	#29001,	r13	;#0x7149
    7774:	80 00 8a 7a 	bra	#0x07a8a	
    7778:	3b 90 16 43 	cmp	#17174,	r11	;#0x4316
    777c:	04 38       	jl	$+10     	;abs 0x7786
    777e:	19 20       	jnz	$+52     	;abs 0x77b2
    7780:	1a 93       	cmp	#1,	r10	;r3 As==01
    7782:	01 28       	jnc	$+4      	;abs 0x7786
    7784:	16 3c       	jmp	$+46     	;abs 0x77b2
    7786:	0a 93       	tst	r10		
    7788:	23 20       	jnz	$+72     	;abs 0x77d0
    778a:	3b 90 16 43 	cmp	#17174,	r11	;#0x4316
    778e:	20 20       	jnz	$+66     	;abs 0x77d0
    7790:	0c 46       	mov	r6,	r12	
    7792:	0d 47       	mov	r7,	r13	
    7794:	0e 44       	mov	r4,	r14	
    7796:	0f 45       	mov	r5,	r15	
    7798:	b0 13 72 82 	calla	#0x08272	
    779c:	0c 4e       	mov	r14,	r12	
    779e:	0d 4f       	mov	r15,	r13	
    77a0:	1e 41 04 00 	mov	4(r1),	r14	;0x0004(r1)
    77a4:	1f 41 06 00 	mov	6(r1),	r15	;0x0006(r1)
    77a8:	b0 13 9e 86 	calla	#0x0869e	
    77ac:	0f 93       	tst	r15		
    77ae:	01 24       	jz	$+4      	;abs 0x77b2
    77b0:	15 34       	jge	$+44     	;abs 0x77dc
    77b2:	3c 40 60 42 	mov	#16992,	r12	;#0x4260
    77b6:	3d 40 a2 0d 	mov	#3490,	r13	;#0x0da2
    77ba:	2e 41       	mov	@r1,	r14	
    77bc:	1f 41 02 00 	mov	2(r1),	r15	;0x0002(r1)
    77c0:	b0 13 c2 82 	calla	#0x082c2	
    77c4:	3c 40 60 42 	mov	#16992,	r12	;#0x4260
    77c8:	3d 40 a2 0d 	mov	#3490,	r13	;#0x0da2
    77cc:	80 00 8a 7a 	bra	#0x07a8a	
    77d0:	3b 90 00 3f 	cmp	#16128,	r11	;#0x3f00
    77d4:	62 38       	jl	$+198    	;abs 0x789a
    77d6:	02 20       	jnz	$+6      	;abs 0x77dc
    77d8:	1a 93       	cmp	#1,	r10	;r3 As==01
    77da:	5f 28       	jnc	$+192    	;abs 0x789a
    77dc:	0e 4b       	mov	r11,	r14	
    77de:	0f 4b       	mov	r11,	r15	
    77e0:	8f 10       	swpb	r15		
    77e2:	8f 11       	sxt	r15		
    77e4:	8f 10       	swpb	r15		
    77e6:	8f 11       	sxt	r15		
    77e8:	7d 40 07 00 	mov.b	#7,	r13	;#0x0007
    77ec:	0f 11       	rra	r15		
    77ee:	0e 10       	rrc	r14		
    77f0:	7d 53       	add.b	#-1,	r13	;r3 As==11
    77f2:	fc 23       	jnz	$-6      	;abs 0x77ec
    77f4:	7e 50 82 ff 	add.b	#-126,	r14	;#0xff82
    77f8:	7e f0 1f 00 	and.b	#31,	r14	;#0x001f
    77fc:	04 43       	clr	r4		
    77fe:	35 40 80 00 	mov	#128,	r5	;#0x0080
    7802:	4e 93       	tst.b	r14		
    7804:	04 24       	jz	$+10     	;abs 0x780e
    7806:	05 11       	rra	r5		
    7808:	04 10       	rrc	r4		
    780a:	7e 53       	add.b	#-1,	r14	;r3 As==11
    780c:	fa 3f       	jmp	$-10     	;abs 0x7802
    780e:	04 58       	add	r8,	r4	
    7810:	05 69       	addc	r9,	r5	
    7812:	0c 44       	mov	r4,	r12	
    7814:	0d 45       	mov	r5,	r13	
    7816:	3c f3       	and	#-1,	r12	;r3 As==11
    7818:	3d f0 ff 7f 	and	#32767,	r13	;#0x7fff
    781c:	0e 4d       	mov	r13,	r14	
    781e:	0f 4d       	mov	r13,	r15	
    7820:	8f 10       	swpb	r15		
    7822:	8f 11       	sxt	r15		
    7824:	8f 10       	swpb	r15		
    7826:	8f 11       	sxt	r15		
    7828:	7d 40 07 00 	mov.b	#7,	r13	;#0x0007
    782c:	0f 11       	rra	r15		
    782e:	0e 10       	rrc	r14		
    7830:	7d 53       	add.b	#-1,	r13	;r3 As==11
    7832:	fc 23       	jnz	$-6      	;abs 0x782c
    7834:	0a 4e       	mov	r14,	r10	
    7836:	0b 4f       	mov	r15,	r11	
    7838:	3a 50 81 ff 	add	#-127,	r10	;#0xff81
    783c:	3b 63       	addc	#-1,	r11	;r3 As==11
    783e:	4d 4a       	mov.b	r10,	r13	
    7840:	7d f0 1f 00 	and.b	#31,	r13	;#0x001f
    7844:	3e 43       	mov	#-1,	r14	;r3 As==11
    7846:	3f 40 7f 00 	mov	#127,	r15	;#0x007f
    784a:	4d 93       	tst.b	r13		
    784c:	04 24       	jz	$+10     	;abs 0x7856
    784e:	0f 11       	rra	r15		
    7850:	0e 10       	rrc	r14		
    7852:	7d 53       	add.b	#-1,	r13	;r3 As==11
    7854:	fa 3f       	jmp	$-10     	;abs 0x784a
    7856:	0c 44       	mov	r4,	r12	
    7858:	0d 45       	mov	r5,	r13	
    785a:	0c ce       	bic	r14,	r12	
    785c:	0d cf       	bic	r15,	r13	
    785e:	34 f3       	and	#-1,	r4	;r3 As==11
    7860:	35 f0 7f 00 	and	#127,	r5	;#0x007f
    7864:	3f 40 17 00 	mov	#23,	r15	;#0x0017
    7868:	4f 8a       	sub.b	r10,	r15	
    786a:	7f f0 1f 00 	and.b	#31,	r15	;#0x001f
    786e:	04 d3       	bis	#0,	r4	;r3 As==00
    7870:	35 d0 80 00 	bis	#128,	r5	;#0x0080
    7874:	4f 93       	tst.b	r15		
    7876:	04 24       	jz	$+10     	;abs 0x7880
    7878:	05 11       	rra	r5		
    787a:	04 10       	rrc	r4		
    787c:	7f 53       	add.b	#-1,	r15	;r3 As==11
    787e:	fa 3f       	jmp	$-10     	;abs 0x7874
    7880:	09 93       	tst	r9		
    7882:	04 34       	jge	$+10     	;abs 0x788c
    7884:	34 e3       	inv	r4		
    7886:	35 e3       	inv	r5		
    7888:	14 53       	inc	r4		
    788a:	05 63       	adc	r5		
    788c:	0e 46       	mov	r6,	r14	
    788e:	0f 47       	mov	r7,	r15	
    7890:	b0 13 72 82 	calla	#0x08272	
    7894:	06 4e       	mov	r14,	r6	
    7896:	07 4f       	mov	r15,	r7	
    7898:	02 3c       	jmp	$+6      	;abs 0x789e
    789a:	04 43       	clr	r4		
    789c:	05 43       	clr	r5		
    789e:	0c 46       	mov	r6,	r12	
    78a0:	0d 47       	mov	r7,	r13	
    78a2:	1e 41 04 00 	mov	4(r1),	r14	;0x0004(r1)
    78a6:	1f 41 06 00 	mov	6(r1),	r15	;0x0006(r1)
    78aa:	b0 13 26 82 	calla	#0x08226	
    78ae:	0a 4e       	mov	r14,	r10	
    78b0:	0b 4f       	mov	r15,	r11	
    78b2:	3a f0 00 f0 	and	#-4096,	r10	;#0xf000
    78b6:	3b f3       	and	#-1,	r11	;r3 As==11
    78b8:	3c 40 00 72 	mov	#29184,	r12	;#0x7200
    78bc:	3d 40 31 3f 	mov	#16177,	r13	;#0x3f31
    78c0:	0e 4a       	mov	r10,	r14	
    78c2:	0f 4b       	mov	r11,	r15	
    78c4:	b0 13 c2 82 	calla	#0x082c2	
    78c8:	08 4e       	mov	r14,	r8	
    78ca:	09 4f       	mov	r15,	r9	
    78cc:	0c 46       	mov	r6,	r12	
    78ce:	0d 47       	mov	r7,	r13	
    78d0:	0e 4a       	mov	r10,	r14	
    78d2:	0f 4b       	mov	r11,	r15	
    78d4:	b0 13 72 82 	calla	#0x08272	
    78d8:	0c 4e       	mov	r14,	r12	
    78da:	0d 4f       	mov	r15,	r13	
    78dc:	1e 41 04 00 	mov	4(r1),	r14	;0x0004(r1)
    78e0:	1f 41 06 00 	mov	6(r1),	r15	;0x0006(r1)
    78e4:	b0 13 72 82 	calla	#0x08272	
    78e8:	3c 40 18 72 	mov	#29208,	r12	;#0x7218
    78ec:	3d 40 31 3f 	mov	#16177,	r13	;#0x3f31
    78f0:	b0 13 c2 82 	calla	#0x082c2	
    78f4:	06 4e       	mov	r14,	r6	
    78f6:	07 4f       	mov	r15,	r7	
    78f8:	3c 40 8c be 	mov	#-16756,r12	;#0xbe8c
    78fc:	3d 40 bf 35 	mov	#13759,	r13	;#0x35bf
    7900:	0e 4a       	mov	r10,	r14	
    7902:	0f 4b       	mov	r11,	r15	
    7904:	b0 13 c2 82 	calla	#0x082c2	
    7908:	0c 4e       	mov	r14,	r12	
    790a:	0d 4f       	mov	r15,	r13	
    790c:	0e 46       	mov	r6,	r14	
    790e:	0f 47       	mov	r7,	r15	
    7910:	b0 13 26 82 	calla	#0x08226	
    7914:	06 4e       	mov	r14,	r6	
    7916:	07 4f       	mov	r15,	r7	
    7918:	0c 4e       	mov	r14,	r12	
    791a:	0d 4f       	mov	r15,	r13	
    791c:	0e 48       	mov	r8,	r14	
    791e:	0f 49       	mov	r9,	r15	
    7920:	b0 13 26 82 	calla	#0x08226	
    7924:	0a 4e       	mov	r14,	r10	
    7926:	0b 4f       	mov	r15,	r11	
    7928:	0c 48       	mov	r8,	r12	
    792a:	0d 49       	mov	r9,	r13	
    792c:	b0 13 72 82 	calla	#0x08272	
    7930:	0c 4e       	mov	r14,	r12	
    7932:	0d 4f       	mov	r15,	r13	
    7934:	0e 46       	mov	r6,	r14	
    7936:	0f 47       	mov	r7,	r15	
    7938:	b0 13 72 82 	calla	#0x08272	
    793c:	06 4e       	mov	r14,	r6	
    793e:	07 4f       	mov	r15,	r7	
    7940:	0c 4a       	mov	r10,	r12	
    7942:	0d 4b       	mov	r11,	r13	
    7944:	0e 4a       	mov	r10,	r14	
    7946:	0f 4b       	mov	r11,	r15	
    7948:	b0 13 c2 82 	calla	#0x082c2	
    794c:	08 4e       	mov	r14,	r8	
    794e:	09 4f       	mov	r15,	r9	
    7950:	3c 40 4c bb 	mov	#-17588,r12	;#0xbb4c
    7954:	3d 40 31 33 	mov	#13105,	r13	;#0x3331
    7958:	b0 13 c2 82 	calla	#0x082c2	
    795c:	3c 40 0e ea 	mov	#-5618,	r12	;#0xea0e
    7960:	3d 40 dd 35 	mov	#13789,	r13	;#0x35dd
    7964:	b0 13 72 82 	calla	#0x08272	
    7968:	0c 4e       	mov	r14,	r12	
    796a:	0d 4f       	mov	r15,	r13	
    796c:	0e 48       	mov	r8,	r14	
    796e:	0f 49       	mov	r9,	r15	
    7970:	b0 13 c2 82 	calla	#0x082c2	
    7974:	3c 40 55 b3 	mov	#-19627,r12	;#0xb355
    7978:	3d 40 8a 38 	mov	#14474,	r13	;#0x388a
    797c:	b0 13 26 82 	calla	#0x08226	
    7980:	0c 4e       	mov	r14,	r12	
    7982:	0d 4f       	mov	r15,	r13	
    7984:	0e 48       	mov	r8,	r14	
    7986:	0f 49       	mov	r9,	r15	
    7988:	b0 13 c2 82 	calla	#0x082c2	
    798c:	3c 40 61 0b 	mov	#2913,	r12	;#0x0b61
    7990:	3d 40 36 3b 	mov	#15158,	r13	;#0x3b36
    7994:	b0 13 72 82 	calla	#0x08272	
    7998:	0c 4e       	mov	r14,	r12	
    799a:	0d 4f       	mov	r15,	r13	
    799c:	0e 48       	mov	r8,	r14	
    799e:	0f 49       	mov	r9,	r15	
    79a0:	b0 13 c2 82 	calla	#0x082c2	
    79a4:	3c 40 ab aa 	mov	#-21845,r12	;#0xaaab
    79a8:	3d 40 2a 3e 	mov	#15914,	r13	;#0x3e2a
    79ac:	b0 13 26 82 	calla	#0x08226	
    79b0:	0c 4e       	mov	r14,	r12	
    79b2:	0d 4f       	mov	r15,	r13	
    79b4:	0e 48       	mov	r8,	r14	
    79b6:	0f 49       	mov	r9,	r15	
    79b8:	b0 13 c2 82 	calla	#0x082c2	
    79bc:	0c 4e       	mov	r14,	r12	
    79be:	0d 4f       	mov	r15,	r13	
    79c0:	0e 4a       	mov	r10,	r14	
    79c2:	0f 4b       	mov	r11,	r15	
    79c4:	b0 13 72 82 	calla	#0x08272	
    79c8:	08 4e       	mov	r14,	r8	
    79ca:	09 4f       	mov	r15,	r9	
    79cc:	0c 4e       	mov	r14,	r12	
    79ce:	0d 4f       	mov	r15,	r13	
    79d0:	0e 4a       	mov	r10,	r14	
    79d2:	0f 4b       	mov	r11,	r15	
    79d4:	b0 13 c2 82 	calla	#0x082c2	
    79d8:	81 4e 04 00 	mov	r14,	4(r1)	;0x0004(r1)
    79dc:	81 4f 06 00 	mov	r15,	6(r1)	;0x0006(r1)
    79e0:	0c 43       	clr	r12		
    79e2:	3d 40 00 40 	mov	#16384,	r13	;#0x4000
    79e6:	0e 48       	mov	r8,	r14	
    79e8:	0f 49       	mov	r9,	r15	
    79ea:	b0 13 72 82 	calla	#0x08272	
    79ee:	0c 4e       	mov	r14,	r12	
    79f0:	0d 4f       	mov	r15,	r13	
    79f2:	1e 41 04 00 	mov	4(r1),	r14	;0x0004(r1)
    79f6:	1f 41 06 00 	mov	6(r1),	r15	;0x0006(r1)
    79fa:	b0 13 c0 84 	calla	#0x084c0	
    79fe:	08 4e       	mov	r14,	r8	
    7a00:	09 4f       	mov	r15,	r9	
    7a02:	0c 46       	mov	r6,	r12	
    7a04:	0d 47       	mov	r7,	r13	
    7a06:	0e 4a       	mov	r10,	r14	
    7a08:	0f 4b       	mov	r11,	r15	
    7a0a:	b0 13 c2 82 	calla	#0x082c2	
    7a0e:	0c 4e       	mov	r14,	r12	
    7a10:	0d 4f       	mov	r15,	r13	
    7a12:	0e 46       	mov	r6,	r14	
    7a14:	0f 47       	mov	r7,	r15	
    7a16:	b0 13 26 82 	calla	#0x08226	
    7a1a:	0c 4e       	mov	r14,	r12	
    7a1c:	0d 4f       	mov	r15,	r13	
    7a1e:	0e 48       	mov	r8,	r14	
    7a20:	0f 49       	mov	r9,	r15	
    7a22:	b0 13 72 82 	calla	#0x08272	
    7a26:	0c 4a       	mov	r10,	r12	
    7a28:	0d 4b       	mov	r11,	r13	
    7a2a:	b0 13 72 82 	calla	#0x08272	
    7a2e:	0c 4e       	mov	r14,	r12	
    7a30:	0d 4f       	mov	r15,	r13	
    7a32:	0e 43       	clr	r14		
    7a34:	3f 40 80 3f 	mov	#16256,	r15	;#0x3f80
    7a38:	b0 13 72 82 	calla	#0x08272	
    7a3c:	0a 4e       	mov	r14,	r10	
    7a3e:	0b 4f       	mov	r15,	r11	
    7a40:	0c 43       	clr	r12		
    7a42:	0d 43       	clr	r13		
    7a44:	0d 44       	mov	r4,	r13	
    7a46:	79 40 07 00 	mov.b	#7,	r9	;#0x0007
    7a4a:	0c 5c       	rla	r12		
    7a4c:	0d 6d       	rlc	r13		
    7a4e:	79 53       	add.b	#-1,	r9	;r3 As==11
    7a50:	fc 23       	jnz	$-6      	;abs 0x7a4a
    7a52:	0c 5a       	add	r10,	r12	
    7a54:	0d 6b       	addc	r11,	r13	
    7a56:	0a 4d       	mov	r13,	r10	
    7a58:	0b 4d       	mov	r13,	r11	
    7a5a:	8b 10       	swpb	r11		
    7a5c:	8b 11       	sxt	r11		
    7a5e:	8b 10       	swpb	r11		
    7a60:	8b 11       	sxt	r11		
    7a62:	79 40 07 00 	mov.b	#7,	r9	;#0x0007
    7a66:	0b 11       	rra	r11		
    7a68:	0a 10       	rrc	r10		
    7a6a:	79 53       	add.b	#-1,	r9	;r3 As==11
    7a6c:	fc 23       	jnz	$-6      	;abs 0x7a66
    7a6e:	0b 93       	tst	r11		
    7a70:	04 38       	jl	$+10     	;abs 0x7a7a
    7a72:	1b 93       	cmp	#1,	r11	;r3 As==01
    7a74:	07 34       	jge	$+16     	;abs 0x7a84
    7a76:	1a 93       	cmp	#1,	r10	;r3 As==01
    7a78:	05 2c       	jc	$+12     	;abs 0x7a84
    7a7a:	0d 44       	mov	r4,	r13	
    7a7c:	b0 13 ba 7a 	calla	#0x07aba	
    7a80:	0c 4e       	mov	r14,	r12	
    7a82:	0d 4f       	mov	r15,	r13	
    7a84:	2e 41       	mov	@r1,	r14	
    7a86:	1f 41 02 00 	mov	2(r1),	r15	;0x0002(r1)
    7a8a:	b0 13 c2 82 	calla	#0x082c2	
    7a8e:	04 4e       	mov	r14,	r4	
    7a90:	05 4f       	mov	r15,	r5	
    7a92:	0a 3c       	jmp	$+22     	;abs 0x7aa8
    7a94:	04 43       	clr	r4		
    7a96:	35 40 80 3f 	mov	#16256,	r5	;#0x3f80
    7a9a:	06 3c       	jmp	$+14     	;abs 0x7aa8
    7a9c:	81 43 04 00 	mov	#0,	4(r1)	;r3 As==00, 0x0004(r1)
    7aa0:	81 43 06 00 	mov	#0,	6(r1)	;r3 As==00, 0x0006(r1)
    7aa4:	80 00 f8 6f 	bra	#0x06ff8	
    7aa8:	0e 44       	mov	r4,	r14	
    7aaa:	0f 45       	mov	r5,	r15	
    7aac:	31 50 24 00 	add	#36,	r1	;#0x0024
    7ab0:	74 16       	popm.a	#8,	r11	
    7ab2:	10 01       	reta			

00007ab4 <powf>:
    7ab4:	b0 13 8a 6e 	calla	#0x06e8a	
    7ab8:	10 01       	reta			

00007aba <scalbnf>:
    7aba:	4b 14       	pushm.a	#5,	r11	
    7abc:	0a 4f       	mov	r15,	r10	
    7abe:	0b 4d       	mov	r13,	r11	
    7ac0:	08 4e       	mov	r14,	r8	
    7ac2:	09 4f       	mov	r15,	r9	
    7ac4:	0c 48       	mov	r8,	r12	
    7ac6:	0d 49       	mov	r9,	r13	
    7ac8:	3c f3       	and	#-1,	r12	;r3 As==11
    7aca:	3d f0 ff 7f 	and	#32767,	r13	;#0x7fff
    7ace:	0c 93       	tst	r12		
    7ad0:	02 20       	jnz	$+6      	;abs 0x7ad6
    7ad2:	0d 93       	tst	r13		
    7ad4:	a3 24       	jz	$+328    	;abs 0x7c1c
    7ad6:	3d 90 80 7f 	cmp	#32640,	r13	;#0x7f80
    7ada:	08 28       	jnc	$+18     	;abs 0x7aec
    7adc:	0f 4a       	mov	r10,	r15	
    7ade:	0c 4e       	mov	r14,	r12	
    7ae0:	0d 4a       	mov	r10,	r13	
    7ae2:	09 4e       	mov	r14,	r9	
    7ae4:	0b 4a       	mov	r10,	r11	
    7ae6:	b0 13 26 82 	calla	#0x08226	
    7aea:	97 3c       	jmp	$+304    	;abs 0x7c1a
    7aec:	3d 90 80 00 	cmp	#128,	r13	;#0x0080
    7af0:	0c 28       	jnc	$+26     	;abs 0x7b0a
    7af2:	0e 48       	mov	r8,	r14	
    7af4:	0f 49       	mov	r9,	r15	
    7af6:	0c 4d       	mov	r13,	r12	
    7af8:	0d 43       	clr	r13		
    7afa:	79 40 07 00 	mov.b	#7,	r9	;#0x0007
    7afe:	12 c3       	clrc			
    7b00:	0d 10       	rrc	r13		
    7b02:	0c 10       	rrc	r12		
    7b04:	79 53       	add.b	#-1,	r9	;r3 As==11
    7b06:	fb 23       	jnz	$-8      	;abs 0x7afe
    7b08:	1b 3c       	jmp	$+56     	;abs 0x7b40
    7b0a:	0c 43       	clr	r12		
    7b0c:	3d 40 00 4c 	mov	#19456,	r13	;#0x4c00
    7b10:	0f 4a       	mov	r10,	r15	
    7b12:	b0 13 c2 82 	calla	#0x082c2	
    7b16:	0a 4f       	mov	r15,	r10	
    7b18:	08 4e       	mov	r14,	r8	
    7b1a:	09 4f       	mov	r15,	r9	
    7b1c:	08 f3       	and	#0,	r8	;r3 As==00
    7b1e:	39 f0 80 7f 	and	#32640,	r9	;#0x7f80
    7b22:	0c 49       	mov	r9,	r12	
    7b24:	0d 49       	mov	r9,	r13	
    7b26:	8d 10       	swpb	r13		
    7b28:	8d 11       	sxt	r13		
    7b2a:	8d 10       	swpb	r13		
    7b2c:	8d 11       	sxt	r13		
    7b2e:	79 40 07 00 	mov.b	#7,	r9	;#0x0007
    7b32:	0d 11       	rra	r13		
    7b34:	0c 10       	rrc	r12		
    7b36:	79 53       	add.b	#-1,	r9	;r3 As==11
    7b38:	fc 23       	jnz	$-6      	;abs 0x7b32
    7b3a:	3c 50 e7 ff 	add	#-25,	r12	;#0xffe7
    7b3e:	3d 63       	addc	#-1,	r13	;r3 As==11
    7b40:	08 4b       	mov	r11,	r8	
    7b42:	07 4b       	mov	r11,	r7	
    7b44:	87 10       	swpb	r7		
    7b46:	87 11       	sxt	r7		
    7b48:	87 10       	swpb	r7		
    7b4a:	87 11       	sxt	r7		
    7b4c:	09 47       	mov	r7,	r9	
    7b4e:	0c 58       	add	r8,	r12	
    7b50:	0d 69       	addc	r9,	r13	
    7b52:	0d 93       	tst	r13		
    7b54:	0b 38       	jl	$+24     	;abs 0x7b6c
    7b56:	03 20       	jnz	$+8      	;abs 0x7b5e
    7b58:	3c 90 ff 00 	cmp	#255,	r12	;#0x00ff
    7b5c:	07 28       	jnc	$+16     	;abs 0x7b6c
    7b5e:	3e 40 ca f2 	mov	#-3382,	r14	;#0xf2ca
    7b62:	3f 40 49 71 	mov	#29001,	r15	;#0x7149
    7b66:	0a 93       	tst	r10		
    7b68:	2f 34       	jge	$+96     	;abs 0x7bc8
    7b6a:	2a 3c       	jmp	$+86     	;abs 0x7bc0
    7b6c:	0d 93       	tst	r13		
    7b6e:	16 38       	jl	$+46     	;abs 0x7b9c
    7b70:	02 20       	jnz	$+6      	;abs 0x7b76
    7b72:	1c 93       	cmp	#1,	r12	;r3 As==01
    7b74:	13 28       	jnc	$+40     	;abs 0x7b9c
    7b76:	0a 43       	clr	r10		
    7b78:	0b 43       	clr	r11		
    7b7a:	0b 4c       	mov	r12,	r11	
    7b7c:	7d 40 07 00 	mov.b	#7,	r13	;#0x0007
    7b80:	0a 5a       	rla	r10		
    7b82:	0b 6b       	rlc	r11		
    7b84:	7d 53       	add.b	#-1,	r13	;r3 As==11
    7b86:	fc 23       	jnz	$-6      	;abs 0x7b80
    7b88:	0c 4e       	mov	r14,	r12	
    7b8a:	0d 4f       	mov	r15,	r13	
    7b8c:	3c f3       	and	#-1,	r12	;r3 As==11
    7b8e:	3d f0 7f 80 	and	#-32641,r13	;#0x807f
    7b92:	0c da       	bis	r10,	r12	
    7b94:	0d db       	bis	r11,	r13	
    7b96:	0e 4c       	mov	r12,	r14	
    7b98:	0a 4d       	mov	r13,	r10	
    7b9a:	40 3c       	jmp	$+130    	;abs 0x7c1c
    7b9c:	3d 93       	cmp	#-1,	r13	;r3 As==11
    7b9e:	05 38       	jl	$+12     	;abs 0x7baa
    7ba0:	0d 93       	tst	r13		
    7ba2:	26 34       	jge	$+78     	;abs 0x7bf0
    7ba4:	3c 90 ea ff 	cmp	#-22,	r12	;#0xffea
    7ba8:	23 2c       	jc	$+72     	;abs 0x7bf0
    7baa:	3a f0 00 80 	and	#-32768,r10	;#0x8000
    7bae:	3b 90 31 75 	cmp	#30001,	r11	;#0x7531
    7bb2:	0f 38       	jl	$+32     	;abs 0x7bd2
    7bb4:	3e 40 ca f2 	mov	#-3382,	r14	;#0xf2ca
    7bb8:	3f 40 49 71 	mov	#29001,	r15	;#0x7149
    7bbc:	0a 93       	tst	r10		
    7bbe:	04 24       	jz	$+10     	;abs 0x7bc8
    7bc0:	3e 40 ca f2 	mov	#-3382,	r14	;#0xf2ca
    7bc4:	3f 40 49 f1 	mov	#-3767,	r15	;#0xf149
    7bc8:	3c 40 ca f2 	mov	#-3382,	r12	;#0xf2ca
    7bcc:	3d 40 49 71 	mov	#29001,	r13	;#0x7149
    7bd0:	22 3c       	jmp	$+70     	;abs 0x7c16
    7bd2:	3e 40 60 42 	mov	#16992,	r14	;#0x4260
    7bd6:	3f 40 a2 0d 	mov	#3490,	r15	;#0x0da2
    7bda:	0a 93       	tst	r10		
    7bdc:	04 24       	jz	$+10     	;abs 0x7be6
    7bde:	3e 40 60 42 	mov	#16992,	r14	;#0x4260
    7be2:	3f 40 a2 8d 	mov	#-29278,r15	;#0x8da2
    7be6:	3c 40 60 42 	mov	#16992,	r12	;#0x4260
    7bea:	3d 40 a2 0d 	mov	#3490,	r13	;#0x0da2
    7bee:	13 3c       	jmp	$+40     	;abs 0x7c16
    7bf0:	0a 43       	clr	r10		
    7bf2:	0b 43       	clr	r11		
    7bf4:	0b 4c       	mov	r12,	r11	
    7bf6:	3b 50 19 00 	add	#25,	r11	;#0x0019
    7bfa:	7d 40 07 00 	mov.b	#7,	r13	;#0x0007
    7bfe:	0a 5a       	rla	r10		
    7c00:	0b 6b       	rlc	r11		
    7c02:	7d 53       	add.b	#-1,	r13	;r3 As==11
    7c04:	fc 23       	jnz	$-6      	;abs 0x7bfe
    7c06:	3e f3       	and	#-1,	r14	;r3 As==11
    7c08:	3f f0 7f 80 	and	#-32641,r15	;#0x807f
    7c0c:	0e da       	bis	r10,	r14	
    7c0e:	0f db       	bis	r11,	r15	
    7c10:	0c 43       	clr	r12		
    7c12:	3d 40 00 33 	mov	#13056,	r13	;#0x3300
    7c16:	b0 13 c2 82 	calla	#0x082c2	
    7c1a:	0a 4f       	mov	r15,	r10	
    7c1c:	0f 4a       	mov	r10,	r15	
    7c1e:	47 16       	popm.a	#5,	r11	
    7c20:	10 01       	reta			

00007c22 <__ieee754_sqrtf>:
    7c22:	7b 14       	pushm.a	#8,	r11	
    7c24:	21 83       	decd	r1		
    7c26:	0a 4e       	mov	r14,	r10	
    7c28:	0b 4f       	mov	r15,	r11	
    7c2a:	0c 4e       	mov	r14,	r12	
    7c2c:	0d 4f       	mov	r15,	r13	
    7c2e:	06 4e       	mov	r14,	r6	
    7c30:	07 4f       	mov	r15,	r7	
    7c32:	36 f3       	and	#-1,	r6	;r3 As==11
    7c34:	37 f0 ff 7f 	and	#32767,	r7	;#0x7fff
    7c38:	37 90 80 7f 	cmp	#32640,	r7	;#0x7f80
    7c3c:	0b 28       	jnc	$+24     	;abs 0x7c54
    7c3e:	0c 4e       	mov	r14,	r12	
    7c40:	0d 4f       	mov	r15,	r13	
    7c42:	b0 13 c2 82 	calla	#0x082c2	
    7c46:	0c 4e       	mov	r14,	r12	
    7c48:	0d 4f       	mov	r15,	r13	
    7c4a:	0e 4a       	mov	r10,	r14	
    7c4c:	0f 4b       	mov	r11,	r15	
    7c4e:	b0 13 26 82 	calla	#0x08226	
    7c52:	19 3c       	jmp	$+52     	;abs 0x7c86
    7c54:	06 93       	tst	r6		
    7c56:	02 20       	jnz	$+6      	;abs 0x7c5c
    7c58:	07 93       	tst	r7		
    7c5a:	89 24       	jz	$+276    	;abs 0x7d6e
    7c5c:	0d 93       	tst	r13		
    7c5e:	09 38       	jl	$+20     	;abs 0x7c72
    7c60:	08 4d       	mov	r13,	r8	
    7c62:	09 4d       	mov	r13,	r9	
    7c64:	89 10       	swpb	r9		
    7c66:	89 11       	sxt	r9		
    7c68:	89 10       	swpb	r9		
    7c6a:	89 11       	sxt	r9		
    7c6c:	7f 40 07 00 	mov.b	#7,	r15	;#0x0007
    7c70:	0d 3c       	jmp	$+28     	;abs 0x7c8c
    7c72:	0c 4a       	mov	r10,	r12	
    7c74:	0d 4b       	mov	r11,	r13	
    7c76:	0e 4a       	mov	r10,	r14	
    7c78:	0f 4b       	mov	r11,	r15	
    7c7a:	b0 13 72 82 	calla	#0x08272	
    7c7e:	0c 4e       	mov	r14,	r12	
    7c80:	0d 4f       	mov	r15,	r13	
    7c82:	b0 13 c0 84 	calla	#0x084c0	
    7c86:	0a 4e       	mov	r14,	r10	
    7c88:	0b 4f       	mov	r15,	r11	
    7c8a:	71 3c       	jmp	$+228    	;abs 0x7d6e
    7c8c:	09 11       	rra	r9		
    7c8e:	08 10       	rrc	r8		
    7c90:	7f 53       	add.b	#-1,	r15	;r3 As==11
    7c92:	fc 23       	jnz	$-6      	;abs 0x7c8c
    7c94:	37 90 80 00 	cmp	#128,	r7	;#0x0080
    7c98:	14 2c       	jc	$+42     	;abs 0x7cc2
    7c9a:	0e 43       	clr	r14		
    7c9c:	0f 43       	clr	r15		
    7c9e:	04 3c       	jmp	$+10     	;abs 0x7ca8
    7ca0:	0c 5c       	rla	r12		
    7ca2:	0d 6d       	rlc	r13		
    7ca4:	1e 53       	inc	r14		
    7ca6:	0f 63       	adc	r15		
    7ca8:	0a 4c       	mov	r12,	r10	
    7caa:	0b 4d       	mov	r13,	r11	
    7cac:	0a f3       	and	#0,	r10	;r3 As==00
    7cae:	3b f0 80 00 	and	#128,	r11	;#0x0080
    7cb2:	0a 93       	tst	r10		
    7cb4:	02 20       	jnz	$+6      	;abs 0x7cba
    7cb6:	0b 93       	tst	r11		
    7cb8:	f3 27       	jz	$-24     	;abs 0x7ca0
    7cba:	08 8e       	sub	r14,	r8	
    7cbc:	09 7f       	subc	r15,	r9	
    7cbe:	18 53       	inc	r8		
    7cc0:	09 63       	adc	r9		
    7cc2:	38 50 81 ff 	add	#-127,	r8	;#0xff81
    7cc6:	39 63       	addc	#-1,	r9	;r3 As==11
    7cc8:	3c f3       	and	#-1,	r12	;r3 As==11
    7cca:	3d f0 7f 00 	and	#127,	r13	;#0x007f
    7cce:	0c d3       	bis	#0,	r12	;r3 As==00
    7cd0:	3d d0 80 00 	bis	#128,	r13	;#0x0080
    7cd4:	0e 48       	mov	r8,	r14	
    7cd6:	0f 49       	mov	r9,	r15	
    7cd8:	1e f3       	and	#1,	r14	;r3 As==01
    7cda:	0f f3       	and	#0,	r15	;r3 As==00
    7cdc:	0e 93       	tst	r14		
    7cde:	02 20       	jnz	$+6      	;abs 0x7ce4
    7ce0:	0f 93       	tst	r15		
    7ce2:	02 24       	jz	$+6      	;abs 0x7ce8
    7ce4:	0c 5c       	rla	r12		
    7ce6:	0d 6d       	rlc	r13		
    7ce8:	09 11       	rra	r9		
    7cea:	08 10       	rrc	r8		
    7cec:	0c 5c       	rla	r12		
    7cee:	0d 6d       	rlc	r13		
    7cf0:	b1 40 19 00 	mov	#25,	0(r1)	;#0x0019, 0x0000(r1)
    7cf4:	00 00 
    7cf6:	0e 43       	clr	r14		
    7cf8:	0f 43       	clr	r15		
    7cfa:	04 43       	clr	r4		
    7cfc:	05 43       	clr	r5		
    7cfe:	0a 43       	clr	r10		
    7d00:	3b 40 00 01 	mov	#256,	r11	;#0x0100
    7d04:	06 44       	mov	r4,	r6	
    7d06:	07 45       	mov	r5,	r7	
    7d08:	06 5a       	add	r10,	r6	
    7d0a:	07 6b       	addc	r11,	r7	
    7d0c:	0d 97       	cmp	r7,	r13	
    7d0e:	0b 38       	jl	$+24     	;abs 0x7d26
    7d10:	02 20       	jnz	$+6      	;abs 0x7d16
    7d12:	0c 96       	cmp	r6,	r12	
    7d14:	08 28       	jnc	$+18     	;abs 0x7d26
    7d16:	04 46       	mov	r6,	r4	
    7d18:	05 47       	mov	r7,	r5	
    7d1a:	04 5a       	add	r10,	r4	
    7d1c:	05 6b       	addc	r11,	r5	
    7d1e:	0c 86       	sub	r6,	r12	
    7d20:	0d 77       	subc	r7,	r13	
    7d22:	0e 5a       	add	r10,	r14	
    7d24:	0f 6b       	addc	r11,	r15	
    7d26:	0c 5c       	rla	r12		
    7d28:	0d 6d       	rlc	r13		
    7d2a:	12 c3       	clrc			
    7d2c:	0b 10       	rrc	r11		
    7d2e:	0a 10       	rrc	r10		
    7d30:	b1 53 00 00 	add	#-1,	0(r1)	;r3 As==11, 0x0000(r1)
    7d34:	e7 23       	jnz	$-48     	;abs 0x7d04
    7d36:	0c 93       	tst	r12		
    7d38:	02 20       	jnz	$+6      	;abs 0x7d3e
    7d3a:	0d 93       	tst	r13		
    7d3c:	06 24       	jz	$+14     	;abs 0x7d4a
    7d3e:	0c 4e       	mov	r14,	r12	
    7d40:	0d 4f       	mov	r15,	r13	
    7d42:	1c f3       	and	#1,	r12	;r3 As==01
    7d44:	0d f3       	and	#0,	r13	;r3 As==00
    7d46:	0e 5c       	add	r12,	r14	
    7d48:	0f 6d       	addc	r13,	r15	
    7d4a:	0f 11       	rra	r15		
    7d4c:	0e 10       	rrc	r14		
    7d4e:	0e 53       	add	#0,	r14	;r3 As==00
    7d50:	3f 60 00 3f 	addc	#16128,	r15	;#0x3f00
    7d54:	0c 43       	clr	r12		
    7d56:	0d 43       	clr	r13		
    7d58:	0d 48       	mov	r8,	r13	
    7d5a:	7b 40 07 00 	mov.b	#7,	r11	;#0x0007
    7d5e:	0c 5c       	rla	r12		
    7d60:	0d 6d       	rlc	r13		
    7d62:	7b 53       	add.b	#-1,	r11	;r3 As==11
    7d64:	fc 23       	jnz	$-6      	;abs 0x7d5e
    7d66:	0a 4e       	mov	r14,	r10	
    7d68:	0b 4f       	mov	r15,	r11	
    7d6a:	0a 5c       	add	r12,	r10	
    7d6c:	0b 6d       	addc	r13,	r11	
    7d6e:	0e 4a       	mov	r10,	r14	
    7d70:	0f 4b       	mov	r11,	r15	
    7d72:	21 53       	incd	r1		
    7d74:	74 16       	popm.a	#8,	r11	
    7d76:	10 01       	reta			

00007d78 <__fixunssfdi>:
    7d78:	7b 14       	pushm.a	#8,	r11	
    7d7a:	21 83       	decd	r1		
    7d7c:	0a 4e       	mov	r14,	r10	
    7d7e:	0b 4f       	mov	r15,	r11	
    7d80:	0c 43       	clr	r12		
    7d82:	3d 40 80 3f 	mov	#16256,	r13	;#0x3f80
    7d86:	b0 13 50 86 	calla	#0x08650	
    7d8a:	0f 93       	tst	r15		
    7d8c:	2c 38       	jl	$+90     	;abs 0x7de6
    7d8e:	0c 43       	clr	r12		
    7d90:	3d 40 80 4f 	mov	#20352,	r13	;#0x4f80
    7d94:	0e 4a       	mov	r10,	r14	
    7d96:	0f 4b       	mov	r11,	r15	
    7d98:	b0 13 50 86 	calla	#0x08650	
    7d9c:	0f 93       	tst	r15		
    7d9e:	14 38       	jl	$+42     	;abs 0x7dc8
    7da0:	0c 43       	clr	r12		
    7da2:	3d 40 80 5f 	mov	#24448,	r13	;#0x5f80
    7da6:	0e 4a       	mov	r10,	r14	
    7da8:	0f 4b       	mov	r11,	r15	
    7daa:	b0 13 50 86 	calla	#0x08650	
    7dae:	0f 93       	tst	r15		
    7db0:	25 38       	jl	$+76     	;abs 0x7dfc
    7db2:	38 43       	mov	#-1,	r8	;r3 As==11
    7db4:	39 43       	mov	#-1,	r9	;r3 As==11
    7db6:	3a 43       	mov	#-1,	r10	;r3 As==11
    7db8:	3b 43       	mov	#-1,	r11	;r3 As==11
    7dba:	0c 48       	mov	r8,	r12	
    7dbc:	0d 49       	mov	r9,	r13	
    7dbe:	0e 4a       	mov	r10,	r14	
    7dc0:	0f 4b       	mov	r11,	r15	
    7dc2:	21 53       	incd	r1		
    7dc4:	74 16       	popm.a	#8,	r11	
    7dc6:	10 01       	reta			
    7dc8:	0e 4a       	mov	r10,	r14	
    7dca:	0f 4b       	mov	r11,	r15	
    7dcc:	b0 13 de 88 	calla	#0x088de	
    7dd0:	08 4e       	mov	r14,	r8	
    7dd2:	09 4f       	mov	r15,	r9	
    7dd4:	0a 43       	clr	r10		
    7dd6:	0b 43       	clr	r11		
    7dd8:	0c 48       	mov	r8,	r12	
    7dda:	0d 49       	mov	r9,	r13	
    7ddc:	0e 4a       	mov	r10,	r14	
    7dde:	0f 4b       	mov	r11,	r15	
    7de0:	21 53       	incd	r1		
    7de2:	74 16       	popm.a	#8,	r11	
    7de4:	10 01       	reta			
    7de6:	08 43       	clr	r8		
    7de8:	09 43       	clr	r9		
    7dea:	0a 43       	clr	r10		
    7dec:	0b 43       	clr	r11		
    7dee:	0c 48       	mov	r8,	r12	
    7df0:	0d 49       	mov	r9,	r13	
    7df2:	0e 4a       	mov	r10,	r14	
    7df4:	0f 4b       	mov	r11,	r15	
    7df6:	21 53       	incd	r1		
    7df8:	74 16       	popm.a	#8,	r11	
    7dfa:	10 01       	reta			
    7dfc:	0c 43       	clr	r12		
    7dfe:	3d 40 80 2f 	mov	#12160,	r13	;#0x2f80
    7e02:	0e 4a       	mov	r10,	r14	
    7e04:	0f 4b       	mov	r11,	r15	
    7e06:	b0 13 c2 82 	calla	#0x082c2	
    7e0a:	08 4e       	mov	r14,	r8	
    7e0c:	09 4f       	mov	r15,	r9	
    7e0e:	b1 40 05 00 	mov	#5,	0(r1)	;#0x0005, 0x0000(r1)
    7e12:	00 00 
    7e14:	3a 40 10 00 	mov	#16,	r10	;#0x0010
    7e18:	0b 43       	clr	r11		
    7e1a:	04 43       	clr	r4		
    7e1c:	05 43       	clr	r5		
    7e1e:	4d 4a       	mov.b	r10,	r13	
    7e20:	7d f0 1f 00 	and.b	#31,	r13	;#0x001f
    7e24:	1e 43       	mov	#1,	r14	;r3 As==01
    7e26:	0f 43       	clr	r15		
    7e28:	04 24       	jz	$+10     	;abs 0x7e32
    7e2a:	0e 5e       	rla	r14		
    7e2c:	0f 6f       	rlc	r15		
    7e2e:	7d 53       	add.b	#-1,	r13	;r3 As==11
    7e30:	fc 23       	jnz	$-6      	;abs 0x7e2a
    7e32:	b0 13 90 87 	calla	#0x08790	
    7e36:	06 4e       	mov	r14,	r6	
    7e38:	07 4f       	mov	r15,	r7	
    7e3a:	0c 48       	mov	r8,	r12	
    7e3c:	0d 49       	mov	r9,	r13	
    7e3e:	b0 13 9e 86 	calla	#0x0869e	
    7e42:	0f 93       	tst	r15		
    7e44:	01 24       	jz	$+4      	;abs 0x7e48
    7e46:	0a 34       	jge	$+22     	;abs 0x7e5c
    7e48:	04 da       	bis	r10,	r4	
    7e4a:	05 db       	bis	r11,	r5	
    7e4c:	0c 46       	mov	r6,	r12	
    7e4e:	0d 47       	mov	r7,	r13	
    7e50:	0e 48       	mov	r8,	r14	
    7e52:	0f 49       	mov	r9,	r15	
    7e54:	b0 13 c0 84 	calla	#0x084c0	
    7e58:	08 4e       	mov	r14,	r8	
    7e5a:	09 4f       	mov	r15,	r9	
    7e5c:	12 c3       	clrc			
    7e5e:	0b 10       	rrc	r11		
    7e60:	0a 10       	rrc	r10		
    7e62:	b1 53 00 00 	add	#-1,	0(r1)	;r3 As==11, 0x0000(r1)
    7e66:	db 23       	jnz	$-72     	;abs 0x7e1e
    7e68:	0c 43       	clr	r12		
    7e6a:	3d 40 80 4f 	mov	#20352,	r13	;#0x4f80
    7e6e:	0e 48       	mov	r8,	r14	
    7e70:	0f 49       	mov	r9,	r15	
    7e72:	b0 13 c2 82 	calla	#0x082c2	
    7e76:	b0 13 de 88 	calla	#0x088de	
    7e7a:	4d 44       	mov.b	r4,	r13	
    7e7c:	7d f0 3f 00 	and.b	#63,	r13	;#0x003f
    7e80:	08 4e       	mov	r14,	r8	
    7e82:	09 4f       	mov	r15,	r9	
    7e84:	0a 43       	clr	r10		
    7e86:	0b 43       	clr	r11		
    7e88:	98 27       	jz	$-206    	;abs 0x7dba
    7e8a:	08 58       	rla	r8		
    7e8c:	09 69       	rlc	r9		
    7e8e:	0a 6a       	rlc	r10		
    7e90:	0b 6b       	rlc	r11		
    7e92:	7d 53       	add.b	#-1,	r13	;r3 As==11
    7e94:	fa 23       	jnz	$-10     	;abs 0x7e8a
    7e96:	91 3f       	jmp	$-220    	;abs 0x7dba

00007e98 <__floatundisf>:
    7e98:	7b 14       	pushm.a	#8,	r11	
    7e9a:	04 4c       	mov	r12,	r4	
    7e9c:	05 4d       	mov	r13,	r5	
    7e9e:	06 4e       	mov	r14,	r6	
    7ea0:	07 4f       	mov	r15,	r7	
    7ea2:	3c f3       	and	#-1,	r12	;r3 As==11
    7ea4:	3d f3       	and	#-1,	r13	;r3 As==11
    7ea6:	0e f3       	and	#0,	r14	;r3 As==00
    7ea8:	0f f3       	and	#0,	r15	;r3 As==00
    7eaa:	0c 94       	cmp	r4,	r12	
    7eac:	5b 24       	jz	$+184    	;abs 0x7f64
    7eae:	0c 47       	mov	r7,	r12	
    7eb0:	0b 46       	mov	r6,	r11	
    7eb2:	17 93       	cmp	#1,	r7	;r3 As==01
    7eb4:	6f 28       	jnc	$+224    	;abs 0x7f94
    7eb6:	37 90 00 01 	cmp	#256,	r7	;#0x0100
    7eba:	66 2c       	jc	$+206    	;abs 0x7f88
    7ebc:	3d 40 10 00 	mov	#16,	r13	;#0x0010
    7ec0:	38 40 10 00 	mov	#16,	r8	;#0x0010
    7ec4:	09 43       	clr	r9		
    7ec6:	4d 4d       	mov.b	r13,	r13	
    7ec8:	0e 4b       	mov	r11,	r14	
    7eca:	0f 4c       	mov	r12,	r15	
    7ecc:	4d 93       	tst.b	r13		
    7ece:	05 24       	jz	$+12     	;abs 0x7eda
    7ed0:	12 c3       	clrc			
    7ed2:	0f 10       	rrc	r15		
    7ed4:	0e 10       	rrc	r14		
    7ed6:	7d 53       	add.b	#-1,	r13	;r3 As==11
    7ed8:	fb 23       	jnz	$-8      	;abs 0x7ed0
    7eda:	3e 50 7c 9d 	add	#-25220,r14	;#0x9d7c
    7ede:	6a 4e       	mov.b	@r14,	r10	
    7ee0:	0b 43       	clr	r11		
    7ee2:	0a 58       	add	r8,	r10	
    7ee4:	0b 69       	addc	r9,	r11	
    7ee6:	08 4a       	mov	r10,	r8	
    7ee8:	49 4a       	mov.b	r10,	r9	
    7eea:	79 f0 3f 00 	and.b	#63,	r9	;#0x003f
    7eee:	0c 44       	mov	r4,	r12	
    7ef0:	0d 45       	mov	r5,	r13	
    7ef2:	0e 46       	mov	r6,	r14	
    7ef4:	0f 47       	mov	r7,	r15	
    7ef6:	07 24       	jz	$+16     	;abs 0x7f06
    7ef8:	12 c3       	clrc			
    7efa:	0f 10       	rrc	r15		
    7efc:	0e 10       	rrc	r14		
    7efe:	0d 10       	rrc	r13		
    7f00:	0c 10       	rrc	r12		
    7f02:	79 53       	add.b	#-1,	r9	;r3 As==11
    7f04:	f9 23       	jnz	$-12     	;abs 0x7ef8
    7f06:	39 40 20 00 	mov	#32,	r9	;#0x0020
    7f0a:	49 8a       	sub.b	r10,	r9	
    7f0c:	79 f0 1f 00 	and.b	#31,	r9	;#0x001f
    7f10:	04 24       	jz	$+10     	;abs 0x7f1a
    7f12:	04 54       	rla	r4		
    7f14:	05 65       	rlc	r5		
    7f16:	79 53       	add.b	#-1,	r9	;r3 As==11
    7f18:	fc 23       	jnz	$-6      	;abs 0x7f12
    7f1a:	04 93       	tst	r4		
    7f1c:	42 24       	jz	$+134    	;abs 0x7fa2
    7f1e:	1c d3       	bis	#1,	r12	;r3 As==01
    7f20:	0d d3       	bis	#0,	r13	;r3 As==00
    7f22:	0e d3       	bis	#0,	r14	;r3 As==00
    7f24:	0f d3       	bis	#0,	r15	;r3 As==00
    7f26:	0e 4c       	mov	r12,	r14	
    7f28:	0f 4d       	mov	r13,	r15	
    7f2a:	b0 13 90 87 	calla	#0x08790	
    7f2e:	06 4e       	mov	r14,	r6	
    7f30:	07 4f       	mov	r15,	r7	
    7f32:	3a 90 20 00 	cmp	#32,	r10	;#0x0020
    7f36:	22 24       	jz	$+70     	;abs 0x7f7c
    7f38:	3a 90 1f 00 	cmp	#31,	r10	;#0x001f
    7f3c:	39 24       	jz	$+116    	;abs 0x7fb0
    7f3e:	78 f0 1f 00 	and.b	#31,	r8	;#0x001f
    7f42:	1e 43       	mov	#1,	r14	;r3 As==01
    7f44:	0f 43       	clr	r15		
    7f46:	04 24       	jz	$+10     	;abs 0x7f50
    7f48:	0e 5e       	rla	r14		
    7f4a:	0f 6f       	rlc	r15		
    7f4c:	78 53       	add.b	#-1,	r8	;r3 As==11
    7f4e:	fc 23       	jnz	$-6      	;abs 0x7f48
    7f50:	b0 13 ec 86 	calla	#0x086ec	
    7f54:	0c 4e       	mov	r14,	r12	
    7f56:	0d 4f       	mov	r15,	r13	
    7f58:	0e 46       	mov	r6,	r14	
    7f5a:	0f 47       	mov	r7,	r15	
    7f5c:	b0 13 c2 82 	calla	#0x082c2	
    7f60:	74 16       	popm.a	#8,	r11	
    7f62:	10 01       	reta			
    7f64:	0d 95       	cmp	r5,	r13	
    7f66:	a3 23       	jnz	$-184    	;abs 0x7eae
    7f68:	0e 96       	cmp	r6,	r14	
    7f6a:	a1 23       	jnz	$-188    	;abs 0x7eae
    7f6c:	0f 97       	cmp	r7,	r15	
    7f6e:	9f 23       	jnz	$-192    	;abs 0x7eae
    7f70:	0e 4c       	mov	r12,	r14	
    7f72:	0f 4d       	mov	r13,	r15	
    7f74:	b0 13 90 87 	calla	#0x08790	
    7f78:	74 16       	popm.a	#8,	r11	
    7f7a:	10 01       	reta			
    7f7c:	0b 93       	tst	r11		
    7f7e:	dc 23       	jnz	$-70     	;abs 0x7f38
    7f80:	0c 43       	clr	r12		
    7f82:	3d 40 80 4f 	mov	#20352,	r13	;#0x4f80
    7f86:	e8 3f       	jmp	$-46     	;abs 0x7f58
    7f88:	3d 40 18 00 	mov	#24,	r13	;#0x0018
    7f8c:	38 40 18 00 	mov	#24,	r8	;#0x0018
    7f90:	09 43       	clr	r9		
    7f92:	99 3f       	jmp	$-204    	;abs 0x7ec6
    7f94:	36 90 00 01 	cmp	#256,	r6	;#0x0100
    7f98:	07 2c       	jc	$+16     	;abs 0x7fa8
    7f9a:	0d 43       	clr	r13		
    7f9c:	08 43       	clr	r8		
    7f9e:	09 43       	clr	r9		
    7fa0:	92 3f       	jmp	$-218    	;abs 0x7ec6
    7fa2:	05 93       	tst	r5		
    7fa4:	bc 23       	jnz	$-134    	;abs 0x7f1e
    7fa6:	bf 3f       	jmp	$-128    	;abs 0x7f26
    7fa8:	3d 42       	mov	#8,	r13	;r2 As==11
    7faa:	38 42       	mov	#8,	r8	;r2 As==11
    7fac:	09 43       	clr	r9		
    7fae:	8b 3f       	jmp	$-232    	;abs 0x7ec6
    7fb0:	0b 93       	tst	r11		
    7fb2:	c5 23       	jnz	$-116    	;abs 0x7f3e
    7fb4:	0c 43       	clr	r12		
    7fb6:	3d 40 00 4f 	mov	#20224,	r13	;#0x4f00
    7fba:	ce 3f       	jmp	$-98     	;abs 0x7f58

00007fbc <_fpadd_parts>:
    7fbc:	7b 14       	pushm.a	#8,	r11	
    7fbe:	21 82       	sub	#4,	r1	;r2 As==10
    7fc0:	09 4d       	mov	r13,	r9	
    7fc2:	6c 4f       	mov.b	@r15,	r12	
    7fc4:	6c 93       	cmp.b	#2,	r12	;r3 As==10
    7fc6:	64 28       	jnc	$+202    	;abs 0x8090
    7fc8:	6d 4e       	mov.b	@r14,	r13	
    7fca:	6d 93       	cmp.b	#2,	r13	;r3 As==10
    7fcc:	dd 28       	jnc	$+444    	;abs 0x8188
    7fce:	6c 92       	cmp.b	#4,	r12	;r2 As==10
    7fd0:	02 20       	jnz	$+6      	;abs 0x7fd6
    7fd2:	80 00 14 82 	bra	#0x08214	
    7fd6:	6d 92       	cmp.b	#4,	r13	;r2 As==10
    7fd8:	d7 24       	jz	$+432    	;abs 0x8188
    7fda:	6d 93       	cmp.b	#2,	r13	;r3 As==10
    7fdc:	ad 24       	jz	$+348    	;abs 0x8138
    7fde:	6c 93       	cmp.b	#2,	r12	;r3 As==10
    7fe0:	d3 24       	jz	$+424    	;abs 0x8188
    7fe2:	18 4f 02 00 	mov	2(r15),	r8	;0x0002(r15)
    7fe6:	1c 4e 02 00 	mov	2(r14),	r12	;0x0002(r14)
    7fea:	14 4f 04 00 	mov	4(r15),	r4	;0x0004(r15)
    7fee:	15 4f 06 00 	mov	6(r15),	r5	;0x0006(r15)
    7ff2:	16 4e 04 00 	mov	4(r14),	r6	;0x0004(r14)
    7ff6:	17 4e 06 00 	mov	6(r14),	r7	;0x0006(r14)
    7ffa:	0d 48       	mov	r8,	r13	
    7ffc:	0d 8c       	sub	r12,	r13	
    7ffe:	0b 4d       	mov	r13,	r11	
    8000:	0d 93       	tst	r13		
    8002:	b2 38       	jl	$+358    	;abs 0x8168
    8004:	3b 90 20 00 	cmp	#32,	r11	;#0x0020
    8008:	46 34       	jge	$+142    	;abs 0x8096
    800a:	1d 93       	cmp	#1,	r13	;r3 As==01
    800c:	ce 38       	jl	$+414    	;abs 0x81aa
    800e:	4d 4b       	mov.b	r11,	r13	
    8010:	7d f0 1f 00 	and.b	#31,	r13	;#0x001f
    8014:	81 46 00 00 	mov	r6,	0(r1)	;0x0000(r1)
    8018:	81 47 02 00 	mov	r7,	2(r1)	;0x0002(r1)
    801c:	0c 24       	jz	$+26     	;abs 0x8036
    801e:	4a 4d       	mov.b	r13,	r10	
    8020:	0c 46       	mov	r6,	r12	
    8022:	0d 47       	mov	r7,	r13	
    8024:	12 c3       	clrc			
    8026:	0d 10       	rrc	r13		
    8028:	0c 10       	rrc	r12		
    802a:	7a 53       	add.b	#-1,	r10	;r3 As==11
    802c:	fb 23       	jnz	$-8      	;abs 0x8024
    802e:	81 4c 00 00 	mov	r12,	0(r1)	;0x0000(r1)
    8032:	81 4d 02 00 	mov	r13,	2(r1)	;0x0002(r1)
    8036:	7b f0 1f 00 	and.b	#31,	r11	;#0x001f
    803a:	1c 43       	mov	#1,	r12	;r3 As==01
    803c:	0d 43       	clr	r13		
    803e:	04 24       	jz	$+10     	;abs 0x8048
    8040:	0c 5c       	rla	r12		
    8042:	0d 6d       	rlc	r13		
    8044:	7b 53       	add.b	#-1,	r11	;r3 As==11
    8046:	fc 23       	jnz	$-6      	;abs 0x8040
    8048:	3c 53       	add	#-1,	r12	;r3 As==11
    804a:	3d 63       	addc	#-1,	r13	;r3 As==11
    804c:	0c f6       	and	r6,	r12	
    804e:	0d f7       	and	r7,	r13	
    8050:	1a 43       	mov	#1,	r10	;r3 As==01
    8052:	0b 43       	clr	r11		
    8054:	0c 93       	tst	r12		
    8056:	02 20       	jnz	$+6      	;abs 0x805c
    8058:	0d 93       	tst	r13		
    805a:	d9 24       	jz	$+436    	;abs 0x820e
    805c:	26 41       	mov	@r1,	r6	
    805e:	17 41 02 00 	mov	2(r1),	r7	;0x0002(r1)
    8062:	06 da       	bis	r10,	r6	
    8064:	07 db       	bis	r11,	r7	
    8066:	5f 4f 01 00 	mov.b	1(r15),	r15	;0x0001(r15)
    806a:	5f 9e 01 00 	cmp.b	1(r14),	r15	;0x0001(r14)
    806e:	1d 20       	jnz	$+60     	;abs 0x80aa
    8070:	c9 4f 01 00 	mov.b	r15,	1(r9)	;0x0001(r9)
    8074:	89 48 02 00 	mov	r8,	2(r9)	;0x0002(r9)
    8078:	06 54       	add	r4,	r6	
    807a:	07 65       	addc	r5,	r7	
    807c:	89 46 04 00 	mov	r6,	4(r9)	;0x0004(r9)
    8080:	89 47 06 00 	mov	r7,	6(r9)	;0x0006(r9)
    8084:	f9 40 03 00 	mov.b	#3,	0(r9)	;#0x0003, 0x0000(r9)
    8088:	00 00 
    808a:	07 93       	tst	r7		
    808c:	42 38       	jl	$+134    	;abs 0x8112
    808e:	0f 49       	mov	r9,	r15	
    8090:	21 52       	add	#4,	r1	;r2 As==10
    8092:	74 16       	popm.a	#8,	r11	
    8094:	10 01       	reta			
    8096:	0c 98       	cmp	r8,	r12	
    8098:	64 38       	jl	$+202    	;abs 0x8162
    809a:	08 4c       	mov	r12,	r8	
    809c:	04 43       	clr	r4		
    809e:	05 43       	clr	r5		
    80a0:	5f 4f 01 00 	mov.b	1(r15),	r15	;0x0001(r15)
    80a4:	5f 9e 01 00 	cmp.b	1(r14),	r15	;0x0001(r14)
    80a8:	e3 27       	jz	$-56     	;abs 0x8070
    80aa:	4f 93       	tst.b	r15		
    80ac:	66 24       	jz	$+206    	;abs 0x817a
    80ae:	06 84       	sub	r4,	r6	
    80b0:	07 75       	subc	r5,	r7	
    80b2:	07 93       	tst	r7		
    80b4:	6d 38       	jl	$+220    	;abs 0x8190
    80b6:	c9 43 01 00 	mov.b	#0,	1(r9)	;r3 As==00, 0x0001(r9)
    80ba:	89 48 02 00 	mov	r8,	2(r9)	;0x0002(r9)
    80be:	89 46 04 00 	mov	r6,	4(r9)	;0x0004(r9)
    80c2:	89 47 06 00 	mov	r7,	6(r9)	;0x0006(r9)
    80c6:	0e 46       	mov	r6,	r14	
    80c8:	0f 47       	mov	r7,	r15	
    80ca:	3e 53       	add	#-1,	r14	;r3 As==11
    80cc:	3f 63       	addc	#-1,	r15	;r3 As==11
    80ce:	3f 90 ff 3f 	cmp	#16383,	r15	;#0x3fff
    80d2:	05 28       	jnc	$+12     	;abs 0x80de
    80d4:	3f 90 00 40 	cmp	#16384,	r15	;#0x4000
    80d8:	17 2c       	jc	$+48     	;abs 0x8108
    80da:	3e 93       	cmp	#-1,	r14	;r3 As==11
    80dc:	15 2c       	jc	$+44     	;abs 0x8108
    80de:	1d 49 02 00 	mov	2(r9),	r13	;0x0002(r9)
    80e2:	3d 53       	add	#-1,	r13	;r3 As==11
    80e4:	06 56       	rla	r6		
    80e6:	07 67       	rlc	r7		
    80e8:	0c 4d       	mov	r13,	r12	
    80ea:	3d 53       	add	#-1,	r13	;r3 As==11
    80ec:	0e 46       	mov	r6,	r14	
    80ee:	0f 47       	mov	r7,	r15	
    80f0:	3e 53       	add	#-1,	r14	;r3 As==11
    80f2:	3f 63       	addc	#-1,	r15	;r3 As==11
    80f4:	3f 90 ff 3f 	cmp	#16383,	r15	;#0x3fff
    80f8:	f5 2b       	jnc	$-20     	;abs 0x80e4
    80fa:	3c 24       	jz	$+122    	;abs 0x8174
    80fc:	89 46 04 00 	mov	r6,	4(r9)	;0x0004(r9)
    8100:	89 47 06 00 	mov	r7,	6(r9)	;0x0006(r9)
    8104:	89 4c 02 00 	mov	r12,	2(r9)	;0x0002(r9)
    8108:	f9 40 03 00 	mov.b	#3,	0(r9)	;#0x0003, 0x0000(r9)
    810c:	00 00 
    810e:	07 93       	tst	r7		
    8110:	be 37       	jge	$-130    	;abs 0x808e
    8112:	0e 46       	mov	r6,	r14	
    8114:	0f 47       	mov	r7,	r15	
    8116:	1e f3       	and	#1,	r14	;r3 As==01
    8118:	0f f3       	and	#0,	r15	;r3 As==00
    811a:	12 c3       	clrc			
    811c:	07 10       	rrc	r7		
    811e:	06 10       	rrc	r6		
    8120:	0c 4e       	mov	r14,	r12	
    8122:	0d 4f       	mov	r15,	r13	
    8124:	0c d6       	bis	r6,	r12	
    8126:	0d d7       	bis	r7,	r13	
    8128:	89 4c 04 00 	mov	r12,	4(r9)	;0x0004(r9)
    812c:	89 4d 06 00 	mov	r13,	6(r9)	;0x0006(r9)
    8130:	99 53 02 00 	inc	2(r9)		;0x0002(r9)
    8134:	0f 49       	mov	r9,	r15	
    8136:	ac 3f       	jmp	$-166    	;abs 0x8090
    8138:	6c 93       	cmp.b	#2,	r12	;r3 As==10
    813a:	aa 23       	jnz	$-170    	;abs 0x8090
    813c:	a9 4f 00 00 	mov	@r15,	0(r9)	;0x0000(r9)
    8140:	99 4f 02 00 	mov	2(r15),	2(r9)	;0x0002(r15), 0x0002(r9)
    8144:	02 00 
    8146:	99 4f 04 00 	mov	4(r15),	4(r9)	;0x0004(r15), 0x0004(r9)
    814a:	04 00 
    814c:	99 4f 06 00 	mov	6(r15),	6(r9)	;0x0006(r15), 0x0006(r9)
    8150:	06 00 
    8152:	5e 4e 01 00 	mov.b	1(r14),	r14	;0x0001(r14)
    8156:	5e ff 01 00 	and.b	1(r15),	r14	;0x0001(r15)
    815a:	c9 4e 01 00 	mov.b	r14,	1(r9)	;0x0001(r9)
    815e:	0f 49       	mov	r9,	r15	
    8160:	97 3f       	jmp	$-208    	;abs 0x8090
    8162:	06 43       	clr	r6		
    8164:	07 43       	clr	r7		
    8166:	9c 3f       	jmp	$-198    	;abs 0x80a0
    8168:	3b e3       	inv	r11		
    816a:	1b 53       	inc	r11		
    816c:	3b 90 20 00 	cmp	#32,	r11	;#0x0020
    8170:	92 37       	jge	$-218    	;abs 0x8096
    8172:	4b 3f       	jmp	$-360    	;abs 0x800a
    8174:	3e 93       	cmp	#-1,	r14	;r3 As==11
    8176:	b6 2b       	jnc	$-146    	;abs 0x80e4
    8178:	c1 3f       	jmp	$-124    	;abs 0x80fc
    817a:	0c 44       	mov	r4,	r12	
    817c:	0d 45       	mov	r5,	r13	
    817e:	0c 86       	sub	r6,	r12	
    8180:	0d 77       	subc	r7,	r13	
    8182:	06 4c       	mov	r12,	r6	
    8184:	07 4d       	mov	r13,	r7	
    8186:	95 3f       	jmp	$-212    	;abs 0x80b2
    8188:	0f 4e       	mov	r14,	r15	
    818a:	21 52       	add	#4,	r1	;r2 As==10
    818c:	74 16       	popm.a	#8,	r11	
    818e:	10 01       	reta			
    8190:	d9 43 01 00 	mov.b	#1,	1(r9)	;r3 As==01, 0x0001(r9)
    8194:	89 48 02 00 	mov	r8,	2(r9)	;0x0002(r9)
    8198:	36 e3       	inv	r6		
    819a:	37 e3       	inv	r7		
    819c:	16 53       	inc	r6		
    819e:	07 63       	adc	r7		
    81a0:	89 46 04 00 	mov	r6,	4(r9)	;0x0004(r9)
    81a4:	89 47 06 00 	mov	r7,	6(r9)	;0x0006(r9)
    81a8:	8e 3f       	jmp	$-226    	;abs 0x80c6
    81aa:	0d 93       	tst	r13		
    81ac:	79 27       	jz	$-268    	;abs 0x80a0
    81ae:	08 5b       	add	r11,	r8	
    81b0:	4d 4b       	mov.b	r11,	r13	
    81b2:	7d f0 1f 00 	and.b	#31,	r13	;#0x001f
    81b6:	81 44 00 00 	mov	r4,	0(r1)	;0x0000(r1)
    81ba:	81 45 02 00 	mov	r5,	2(r1)	;0x0002(r1)
    81be:	0c 24       	jz	$+26     	;abs 0x81d8
    81c0:	4a 4d       	mov.b	r13,	r10	
    81c2:	0c 44       	mov	r4,	r12	
    81c4:	0d 45       	mov	r5,	r13	
    81c6:	12 c3       	clrc			
    81c8:	0d 10       	rrc	r13		
    81ca:	0c 10       	rrc	r12		
    81cc:	7a 53       	add.b	#-1,	r10	;r3 As==11
    81ce:	fb 23       	jnz	$-8      	;abs 0x81c6
    81d0:	81 4c 00 00 	mov	r12,	0(r1)	;0x0000(r1)
    81d4:	81 4d 02 00 	mov	r13,	2(r1)	;0x0002(r1)
    81d8:	7b f0 1f 00 	and.b	#31,	r11	;#0x001f
    81dc:	1c 43       	mov	#1,	r12	;r3 As==01
    81de:	0d 43       	clr	r13		
    81e0:	04 24       	jz	$+10     	;abs 0x81ea
    81e2:	0c 5c       	rla	r12		
    81e4:	0d 6d       	rlc	r13		
    81e6:	7b 53       	add.b	#-1,	r11	;r3 As==11
    81e8:	fc 23       	jnz	$-6      	;abs 0x81e2
    81ea:	3c 53       	add	#-1,	r12	;r3 As==11
    81ec:	3d 63       	addc	#-1,	r13	;r3 As==11
    81ee:	0c f4       	and	r4,	r12	
    81f0:	0d f5       	and	r5,	r13	
    81f2:	1a 43       	mov	#1,	r10	;r3 As==01
    81f4:	0b 43       	clr	r11		
    81f6:	0c 93       	tst	r12		
    81f8:	04 20       	jnz	$+10     	;abs 0x8202
    81fa:	0d 93       	tst	r13		
    81fc:	02 20       	jnz	$+6      	;abs 0x8202
    81fe:	0a 43       	clr	r10		
    8200:	0b 43       	clr	r11		
    8202:	24 41       	mov	@r1,	r4	
    8204:	15 41 02 00 	mov	2(r1),	r5	;0x0002(r1)
    8208:	04 da       	bis	r10,	r4	
    820a:	05 db       	bis	r11,	r5	
    820c:	49 3f       	jmp	$-364    	;abs 0x80a0
    820e:	0a 43       	clr	r10		
    8210:	0b 43       	clr	r11		
    8212:	24 3f       	jmp	$-438    	;abs 0x805c
    8214:	6d 92       	cmp.b	#4,	r13	;r2 As==10
    8216:	3c 23       	jnz	$-390    	;abs 0x8090
    8218:	df 9e 01 00 	cmp.b	1(r14),	1(r15)	;0x0001(r14), 0x0001(r15)
    821c:	01 00 
    821e:	38 27       	jz	$-398    	;abs 0x8090
    8220:	3f 40 10 9a 	mov	#-26096,r15	;#0x9a10
    8224:	35 3f       	jmp	$-404    	;abs 0x8090

00008226 <__addsf3>:
    8226:	31 50 e0 ff 	add	#-32,	r1	;#0xffe0
    822a:	81 4e 1c 00 	mov	r14,	28(r1)	;0x001c(r1)
    822e:	81 4f 1e 00 	mov	r15,	30(r1)	;0x001e(r1)
    8232:	81 4c 18 00 	mov	r12,	24(r1)	;0x0018(r1)
    8236:	81 4d 1a 00 	mov	r13,	26(r1)	;0x001a(r1)
    823a:	0e 41       	mov	r1,	r14	
    823c:	3e 50 10 00 	add	#16,	r14	;#0x0010
    8240:	0f 41       	mov	r1,	r15	
    8242:	3f 50 1c 00 	add	#28,	r15	;#0x001c
    8246:	b0 13 de 8a 	calla	#0x08ade	
    824a:	0e 41       	mov	r1,	r14	
    824c:	3e 52       	add	#8,	r14	;r2 As==11
    824e:	0f 41       	mov	r1,	r15	
    8250:	3f 50 18 00 	add	#24,	r15	;#0x0018
    8254:	b0 13 de 8a 	calla	#0x08ade	
    8258:	0d 41       	mov	r1,	r13	
    825a:	0e 41       	mov	r1,	r14	
    825c:	3e 52       	add	#8,	r14	;r2 As==11
    825e:	0f 41       	mov	r1,	r15	
    8260:	3f 50 10 00 	add	#16,	r15	;#0x0010
    8264:	b0 13 bc 7f 	calla	#0x07fbc	
    8268:	b0 13 1a 89 	calla	#0x0891a	
    826c:	31 50 20 00 	add	#32,	r1	;#0x0020
    8270:	10 01       	reta			

00008272 <__subsf3>:
    8272:	31 50 e0 ff 	add	#-32,	r1	;#0xffe0
    8276:	81 4e 1c 00 	mov	r14,	28(r1)	;0x001c(r1)
    827a:	81 4f 1e 00 	mov	r15,	30(r1)	;0x001e(r1)
    827e:	81 4c 18 00 	mov	r12,	24(r1)	;0x0018(r1)
    8282:	81 4d 1a 00 	mov	r13,	26(r1)	;0x001a(r1)
    8286:	0e 41       	mov	r1,	r14	
    8288:	3e 50 10 00 	add	#16,	r14	;#0x0010
    828c:	0f 41       	mov	r1,	r15	
    828e:	3f 50 1c 00 	add	#28,	r15	;#0x001c
    8292:	b0 13 de 8a 	calla	#0x08ade	
    8296:	0e 41       	mov	r1,	r14	
    8298:	3e 52       	add	#8,	r14	;r2 As==11
    829a:	0f 41       	mov	r1,	r15	
    829c:	3f 50 18 00 	add	#24,	r15	;#0x0018
    82a0:	b0 13 de 8a 	calla	#0x08ade	
    82a4:	d1 e3 09 00 	xor.b	#1,	9(r1)	;r3 As==01, 0x0009(r1)
    82a8:	0d 41       	mov	r1,	r13	
    82aa:	0e 41       	mov	r1,	r14	
    82ac:	3e 52       	add	#8,	r14	;r2 As==11
    82ae:	0f 41       	mov	r1,	r15	
    82b0:	3f 50 10 00 	add	#16,	r15	;#0x0010
    82b4:	b0 13 bc 7f 	calla	#0x07fbc	
    82b8:	b0 13 1a 89 	calla	#0x0891a	
    82bc:	31 50 20 00 	add	#32,	r1	;#0x0020
    82c0:	10 01       	reta			

000082c2 <__mulsf3>:
    82c2:	7b 14       	pushm.a	#8,	r11	
    82c4:	31 50 de ff 	add	#-34,	r1	;#0xffde
    82c8:	81 4e 1c 00 	mov	r14,	28(r1)	;0x001c(r1)
    82cc:	81 4f 1e 00 	mov	r15,	30(r1)	;0x001e(r1)
    82d0:	81 4c 18 00 	mov	r12,	24(r1)	;0x0018(r1)
    82d4:	81 4d 1a 00 	mov	r13,	26(r1)	;0x001a(r1)
    82d8:	0e 41       	mov	r1,	r14	
    82da:	3e 50 10 00 	add	#16,	r14	;#0x0010
    82de:	0f 41       	mov	r1,	r15	
    82e0:	3f 50 1c 00 	add	#28,	r15	;#0x001c
    82e4:	b0 13 de 8a 	calla	#0x08ade	
    82e8:	0e 41       	mov	r1,	r14	
    82ea:	3e 52       	add	#8,	r14	;r2 As==11
    82ec:	0f 41       	mov	r1,	r15	
    82ee:	3f 50 18 00 	add	#24,	r15	;#0x0018
    82f2:	b0 13 de 8a 	calla	#0x08ade	
    82f6:	5f 41 10 00 	mov.b	16(r1),	r15	;0x0010(r1)
    82fa:	6f 93       	cmp.b	#2,	r15	;r3 As==10
    82fc:	10 2c       	jc	$+34     	;abs 0x831e
    82fe:	5f 43       	mov.b	#1,	r15	;r3 As==01
    8300:	d1 91 09 00 	cmp.b	9(r1),	17(r1)	;0x0009(r1), 0x0011(r1)
    8304:	11 00 
    8306:	1e 24       	jz	$+62     	;abs 0x8344
    8308:	c1 4f 11 00 	mov.b	r15,	17(r1)	;0x0011(r1)
    830c:	0f 41       	mov	r1,	r15	
    830e:	3f 50 10 00 	add	#16,	r15	;#0x0010
    8312:	b0 13 1a 89 	calla	#0x0891a	
    8316:	31 50 22 00 	add	#34,	r1	;#0x0022
    831a:	74 16       	popm.a	#8,	r11	
    831c:	10 01       	reta			
    831e:	5e 41 08 00 	mov.b	8(r1),	r14	;0x0008(r1)
    8322:	6e 93       	cmp.b	#2,	r14	;r3 As==10
    8324:	13 2c       	jc	$+40     	;abs 0x834c
    8326:	5f 43       	mov.b	#1,	r15	;r3 As==01
    8328:	d1 91 09 00 	cmp.b	9(r1),	17(r1)	;0x0009(r1), 0x0011(r1)
    832c:	11 00 
    832e:	0c 24       	jz	$+26     	;abs 0x8348
    8330:	c1 4f 09 00 	mov.b	r15,	9(r1)	;0x0009(r1)
    8334:	0f 41       	mov	r1,	r15	
    8336:	3f 52       	add	#8,	r15	;r2 As==11
    8338:	b0 13 1a 89 	calla	#0x0891a	
    833c:	31 50 22 00 	add	#34,	r1	;#0x0022
    8340:	74 16       	popm.a	#8,	r11	
    8342:	10 01       	reta			
    8344:	4f 43       	clr.b	r15		
    8346:	e0 3f       	jmp	$-62     	;abs 0x8308
    8348:	4f 43       	clr.b	r15		
    834a:	f2 3f       	jmp	$-26     	;abs 0x8330
    834c:	6f 92       	cmp.b	#4,	r15	;r2 As==10
    834e:	05 20       	jnz	$+12     	;abs 0x835a
    8350:	6e 93       	cmp.b	#2,	r14	;r3 As==10
    8352:	d5 23       	jnz	$-84     	;abs 0x82fe
    8354:	3f 40 10 9a 	mov	#-26096,r15	;#0x9a10
    8358:	dc 3f       	jmp	$-70     	;abs 0x8312
    835a:	6e 92       	cmp.b	#4,	r14	;r2 As==10
    835c:	03 20       	jnz	$+8      	;abs 0x8364
    835e:	6f 93       	cmp.b	#2,	r15	;r3 As==10
    8360:	f9 27       	jz	$-12     	;abs 0x8354
    8362:	e1 3f       	jmp	$-60     	;abs 0x8326
    8364:	6f 93       	cmp.b	#2,	r15	;r3 As==10
    8366:	cb 27       	jz	$-104    	;abs 0x82fe
    8368:	6e 93       	cmp.b	#2,	r14	;r3 As==10
    836a:	dd 27       	jz	$-68     	;abs 0x8326
    836c:	16 41 14 00 	mov	20(r1),	r6	;0x0014(r1)
    8370:	17 41 16 00 	mov	22(r1),	r7	;0x0016(r1)
    8374:	1e 41 0c 00 	mov	12(r1),	r14	;0x000c(r1)
    8378:	1f 41 0e 00 	mov	14(r1),	r15	;0x000e(r1)
    837c:	b1 40 20 00 	mov	#32,	32(r1)	;#0x0020, 0x0020(r1)
    8380:	20 00 
    8382:	0c 43       	clr	r12		
    8384:	0d 43       	clr	r13		
    8386:	0a 43       	clr	r10		
    8388:	0b 43       	clr	r11		
    838a:	04 43       	clr	r4		
    838c:	05 43       	clr	r5		
    838e:	08 4c       	mov	r12,	r8	
    8390:	09 4d       	mov	r13,	r9	
    8392:	08 3c       	jmp	$+18     	;abs 0x83a4
    8394:	0e 5e       	rla	r14		
    8396:	0f 6f       	rlc	r15		
    8398:	12 c3       	clrc			
    839a:	07 10       	rrc	r7		
    839c:	06 10       	rrc	r6		
    839e:	b1 53 20 00 	add	#-1,	32(r1)	;r3 As==11, 0x0020(r1)
    83a2:	21 24       	jz	$+68     	;abs 0x83e6
    83a4:	0c 46       	mov	r6,	r12	
    83a6:	0d 47       	mov	r7,	r13	
    83a8:	1c f3       	and	#1,	r12	;r3 As==01
    83aa:	0d f3       	and	#0,	r13	;r3 As==00
    83ac:	0c 93       	tst	r12		
    83ae:	02 20       	jnz	$+6      	;abs 0x83b4
    83b0:	0d 93       	tst	r13		
    83b2:	0f 24       	jz	$+32     	;abs 0x83d2
    83b4:	04 5e       	add	r14,	r4	
    83b6:	05 6f       	addc	r15,	r5	
    83b8:	0c 48       	mov	r8,	r12	
    83ba:	0d 49       	mov	r9,	r13	
    83bc:	0c 5a       	add	r10,	r12	
    83be:	0d 6b       	addc	r11,	r13	
    83c0:	18 43       	mov	#1,	r8	;r3 As==01
    83c2:	09 43       	clr	r9		
    83c4:	05 9f       	cmp	r15,	r5	
    83c6:	03 28       	jnc	$+8      	;abs 0x83ce
    83c8:	0b 24       	jz	$+24     	;abs 0x83e0
    83ca:	08 43       	clr	r8		
    83cc:	09 43       	clr	r9		
    83ce:	08 5c       	add	r12,	r8	
    83d0:	09 6d       	addc	r13,	r9	
    83d2:	0a 5a       	rla	r10		
    83d4:	0b 6b       	rlc	r11		
    83d6:	0f 93       	tst	r15		
    83d8:	dd 37       	jge	$-68     	;abs 0x8394
    83da:	1a d3       	bis	#1,	r10	;r3 As==01
    83dc:	0b d3       	bis	#0,	r11	;r3 As==00
    83de:	da 3f       	jmp	$-74     	;abs 0x8394
    83e0:	04 9e       	cmp	r14,	r4	
    83e2:	f5 2b       	jnc	$-20     	;abs 0x83ce
    83e4:	f2 3f       	jmp	$-26     	;abs 0x83ca
    83e6:	0c 48       	mov	r8,	r12	
    83e8:	0d 49       	mov	r9,	r13	
    83ea:	0e 4d       	mov	r13,	r14	
    83ec:	1b 41 12 00 	mov	18(r1),	r11	;0x0012(r1)
    83f0:	1b 51 0a 00 	add	10(r1),	r11	;0x000a(r1)
    83f4:	0f 4b       	mov	r11,	r15	
    83f6:	2f 53       	incd	r15		
    83f8:	81 4f 02 00 	mov	r15,	2(r1)	;0x0002(r1)
    83fc:	5f 43       	mov.b	#1,	r15	;r3 As==01
    83fe:	d1 91 09 00 	cmp.b	9(r1),	17(r1)	;0x0009(r1), 0x0011(r1)
    8402:	11 00 
    8404:	45 24       	jz	$+140    	;abs 0x8490
    8406:	c1 4f 01 00 	mov.b	r15,	1(r1)	;0x0001(r1)
    840a:	0e 93       	tst	r14		
    840c:	27 38       	jl	$+80     	;abs 0x845c
    840e:	3d 90 00 40 	cmp	#16384,	r13	;#0x4000
    8412:	10 2c       	jc	$+34     	;abs 0x8434
    8414:	1f 41 02 00 	mov	2(r1),	r15	;0x0002(r1)
    8418:	3f 53       	add	#-1,	r15	;r3 As==11
    841a:	0e 4f       	mov	r15,	r14	
    841c:	0c 5c       	rla	r12		
    841e:	0d 6d       	rlc	r13		
    8420:	05 93       	tst	r5		
    8422:	19 38       	jl	$+52     	;abs 0x8456
    8424:	04 54       	rla	r4		
    8426:	05 65       	rlc	r5		
    8428:	3f 53       	add	#-1,	r15	;r3 As==11
    842a:	3d 90 00 40 	cmp	#16384,	r13	;#0x4000
    842e:	f5 2b       	jnc	$-20     	;abs 0x841a
    8430:	81 4e 02 00 	mov	r14,	2(r1)	;0x0002(r1)
    8434:	0e 4c       	mov	r12,	r14	
    8436:	0f 4d       	mov	r13,	r15	
    8438:	3e f0 7f 00 	and	#127,	r14	;#0x007f
    843c:	0f f3       	and	#0,	r15	;r3 As==00
    843e:	3e 90 40 00 	cmp	#64,	r14	;#0x0040
    8442:	28 24       	jz	$+82     	;abs 0x8494
    8444:	81 4c 04 00 	mov	r12,	4(r1)	;0x0004(r1)
    8448:	81 4d 06 00 	mov	r13,	6(r1)	;0x0006(r1)
    844c:	f1 40 03 00 	mov.b	#3,	0(r1)	;#0x0003, 0x0000(r1)
    8450:	00 00 
    8452:	0f 41       	mov	r1,	r15	
    8454:	5e 3f       	jmp	$-322    	;abs 0x8312
    8456:	1c d3       	bis	#1,	r12	;r3 As==01
    8458:	0d d3       	bis	#0,	r13	;r3 As==00
    845a:	e4 3f       	jmp	$-54     	;abs 0x8424
    845c:	3b 50 03 00 	add	#3,	r11	;#0x0003
    8460:	0a 4b       	mov	r11,	r10	
    8462:	0e 4c       	mov	r12,	r14	
    8464:	0f 4d       	mov	r13,	r15	
    8466:	1e f3       	and	#1,	r14	;r3 As==01
    8468:	0f f3       	and	#0,	r15	;r3 As==00
    846a:	0e 93       	tst	r14		
    846c:	02 20       	jnz	$+6      	;abs 0x8472
    846e:	0f 93       	tst	r15		
    8470:	06 24       	jz	$+14     	;abs 0x847e
    8472:	12 c3       	clrc			
    8474:	05 10       	rrc	r5		
    8476:	04 10       	rrc	r4		
    8478:	04 d3       	bis	#0,	r4	;r3 As==00
    847a:	35 d0 00 80 	bis	#-32768,r5	;#0x8000
    847e:	12 c3       	clrc			
    8480:	0d 10       	rrc	r13		
    8482:	0c 10       	rrc	r12		
    8484:	1b 53       	inc	r11		
    8486:	0d 93       	tst	r13		
    8488:	eb 3b       	jl	$-40     	;abs 0x8460
    848a:	81 4a 02 00 	mov	r10,	2(r1)	;0x0002(r1)
    848e:	bf 3f       	jmp	$-128    	;abs 0x840e
    8490:	4f 43       	clr.b	r15		
    8492:	b9 3f       	jmp	$-140    	;abs 0x8406
    8494:	0f 93       	tst	r15		
    8496:	d6 23       	jnz	$-82     	;abs 0x8444
    8498:	0e 4c       	mov	r12,	r14	
    849a:	0f 4d       	mov	r13,	r15	
    849c:	3e f0 80 00 	and	#128,	r14	;#0x0080
    84a0:	0f f3       	and	#0,	r15	;r3 As==00
    84a2:	0e 93       	tst	r14		
    84a4:	cf 23       	jnz	$-96     	;abs 0x8444
    84a6:	0f 93       	tst	r15		
    84a8:	cd 23       	jnz	$-100    	;abs 0x8444
    84aa:	04 93       	tst	r4		
    84ac:	02 20       	jnz	$+6      	;abs 0x84b2
    84ae:	05 93       	tst	r5		
    84b0:	c9 27       	jz	$-108    	;abs 0x8444
    84b2:	3c 50 40 00 	add	#64,	r12	;#0x0040
    84b6:	0d 63       	adc	r13		
    84b8:	3c f0 80 ff 	and	#-128,	r12	;#0xff80
    84bc:	3d f3       	and	#-1,	r13	;r3 As==11
    84be:	c2 3f       	jmp	$-122    	;abs 0x8444

000084c0 <__divsf3>:
    84c0:	4b 14       	pushm.a	#5,	r11	
    84c2:	31 50 e8 ff 	add	#-24,	r1	;#0xffe8
    84c6:	81 4e 14 00 	mov	r14,	20(r1)	;0x0014(r1)
    84ca:	81 4f 16 00 	mov	r15,	22(r1)	;0x0016(r1)
    84ce:	81 4c 10 00 	mov	r12,	16(r1)	;0x0010(r1)
    84d2:	81 4d 12 00 	mov	r13,	18(r1)	;0x0012(r1)
    84d6:	0e 41       	mov	r1,	r14	
    84d8:	3e 52       	add	#8,	r14	;r2 As==11
    84da:	0f 41       	mov	r1,	r15	
    84dc:	3f 50 14 00 	add	#20,	r15	;#0x0014
    84e0:	b0 13 de 8a 	calla	#0x08ade	
    84e4:	0e 41       	mov	r1,	r14	
    84e6:	0f 41       	mov	r1,	r15	
    84e8:	3f 50 10 00 	add	#16,	r15	;#0x0010
    84ec:	b0 13 de 8a 	calla	#0x08ade	
    84f0:	5f 41 08 00 	mov.b	8(r1),	r15	;0x0008(r1)
    84f4:	6f 93       	cmp.b	#2,	r15	;r3 As==10
    84f6:	08 2c       	jc	$+18     	;abs 0x8508
    84f8:	0f 41       	mov	r1,	r15	
    84fa:	3f 52       	add	#8,	r15	;r2 As==11
    84fc:	b0 13 1a 89 	calla	#0x0891a	
    8500:	31 50 18 00 	add	#24,	r1	;#0x0018
    8504:	47 16       	popm.a	#5,	r11	
    8506:	10 01       	reta			
    8508:	6e 41       	mov.b	@r1,	r14	
    850a:	6e 93       	cmp.b	#2,	r14	;r3 As==10
    850c:	07 2c       	jc	$+16     	;abs 0x851c
    850e:	0f 41       	mov	r1,	r15	
    8510:	b0 13 1a 89 	calla	#0x0891a	
    8514:	31 50 18 00 	add	#24,	r1	;#0x0018
    8518:	47 16       	popm.a	#5,	r11	
    851a:	10 01       	reta			
    851c:	d1 e1 01 00 	xor.b	1(r1),	9(r1)	;0x0001(r1), 0x0009(r1)
    8520:	09 00 
    8522:	6f 92       	cmp.b	#4,	r15	;r2 As==10
    8524:	02 24       	jz	$+6      	;abs 0x852a
    8526:	6f 93       	cmp.b	#2,	r15	;r3 As==10
    8528:	05 20       	jnz	$+12     	;abs 0x8534
    852a:	4f 9e       	cmp.b	r14,	r15	
    852c:	e5 23       	jnz	$-52     	;abs 0x84f8
    852e:	3f 40 10 9a 	mov	#-26096,r15	;#0x9a10
    8532:	e4 3f       	jmp	$-54     	;abs 0x84fc
    8534:	6e 92       	cmp.b	#4,	r14	;r2 As==10
    8536:	34 24       	jz	$+106    	;abs 0x85a0
    8538:	6e 93       	cmp.b	#2,	r14	;r3 As==10
    853a:	48 24       	jz	$+146    	;abs 0x85cc
    853c:	1d 41 0a 00 	mov	10(r1),	r13	;0x000a(r1)
    8540:	1d 81 02 00 	sub	2(r1),	r13	;0x0002(r1)
    8544:	81 4d 0a 00 	mov	r13,	10(r1)	;0x000a(r1)
    8548:	1e 41 0c 00 	mov	12(r1),	r14	;0x000c(r1)
    854c:	1f 41 0e 00 	mov	14(r1),	r15	;0x000e(r1)
    8550:	1a 41 04 00 	mov	4(r1),	r10	;0x0004(r1)
    8554:	1b 41 06 00 	mov	6(r1),	r11	;0x0006(r1)
    8558:	0f 9b       	cmp	r11,	r15	
    855a:	04 28       	jnc	$+10     	;abs 0x8564
    855c:	0b 9f       	cmp	r15,	r11	
    855e:	07 28       	jnc	$+16     	;abs 0x856e
    8560:	0e 9a       	cmp	r10,	r14	
    8562:	05 2c       	jc	$+12     	;abs 0x856e
    8564:	0e 5e       	rla	r14		
    8566:	0f 6f       	rlc	r15		
    8568:	3d 53       	add	#-1,	r13	;r3 As==11
    856a:	81 4d 0a 00 	mov	r13,	10(r1)	;0x000a(r1)
    856e:	37 40 1f 00 	mov	#31,	r7	;#0x001f
    8572:	0c 43       	clr	r12		
    8574:	3d 40 00 40 	mov	#16384,	r13	;#0x4000
    8578:	08 43       	clr	r8		
    857a:	09 43       	clr	r9		
    857c:	0b 3c       	jmp	$+24     	;abs 0x8594
    857e:	08 dc       	bis	r12,	r8	
    8580:	09 dd       	bis	r13,	r9	
    8582:	0e 8a       	sub	r10,	r14	
    8584:	0f 7b       	subc	r11,	r15	
    8586:	12 c3       	clrc			
    8588:	0d 10       	rrc	r13		
    858a:	0c 10       	rrc	r12		
    858c:	0e 5e       	rla	r14		
    858e:	0f 6f       	rlc	r15		
    8590:	37 53       	add	#-1,	r7	;r3 As==11
    8592:	0f 24       	jz	$+32     	;abs 0x85b2
    8594:	0f 9b       	cmp	r11,	r15	
    8596:	f7 2b       	jnc	$-16     	;abs 0x8586
    8598:	f2 23       	jnz	$-26     	;abs 0x857e
    859a:	0e 9a       	cmp	r10,	r14	
    859c:	f4 2b       	jnc	$-22     	;abs 0x8586
    859e:	ef 3f       	jmp	$-32     	;abs 0x857e
    85a0:	81 43 0c 00 	mov	#0,	12(r1)	;r3 As==00, 0x000c(r1)
    85a4:	81 43 0e 00 	mov	#0,	14(r1)	;r3 As==00, 0x000e(r1)
    85a8:	81 43 0a 00 	mov	#0,	10(r1)	;r3 As==00, 0x000a(r1)
    85ac:	0f 41       	mov	r1,	r15	
    85ae:	3f 52       	add	#8,	r15	;r2 As==11
    85b0:	a5 3f       	jmp	$-180    	;abs 0x84fc
    85b2:	0c 48       	mov	r8,	r12	
    85b4:	0d 49       	mov	r9,	r13	
    85b6:	3c f0 7f 00 	and	#127,	r12	;#0x007f
    85ba:	0d f3       	and	#0,	r13	;r3 As==00
    85bc:	3c 90 40 00 	cmp	#64,	r12	;#0x0040
    85c0:	0a 24       	jz	$+22     	;abs 0x85d6
    85c2:	81 48 0c 00 	mov	r8,	12(r1)	;0x000c(r1)
    85c6:	81 49 0e 00 	mov	r9,	14(r1)	;0x000e(r1)
    85ca:	96 3f       	jmp	$-210    	;abs 0x84f8
    85cc:	e1 42 08 00 	mov.b	#4,	8(r1)	;r2 As==10, 0x0008(r1)
    85d0:	0f 41       	mov	r1,	r15	
    85d2:	3f 52       	add	#8,	r15	;r2 As==11
    85d4:	93 3f       	jmp	$-216    	;abs 0x84fc
    85d6:	0d 93       	tst	r13		
    85d8:	f4 23       	jnz	$-22     	;abs 0x85c2
    85da:	0c 48       	mov	r8,	r12	
    85dc:	0d 49       	mov	r9,	r13	
    85de:	3c f0 80 00 	and	#128,	r12	;#0x0080
    85e2:	0d f3       	and	#0,	r13	;r3 As==00
    85e4:	0c 93       	tst	r12		
    85e6:	ed 23       	jnz	$-36     	;abs 0x85c2
    85e8:	0d 93       	tst	r13		
    85ea:	eb 23       	jnz	$-40     	;abs 0x85c2
    85ec:	0e 93       	tst	r14		
    85ee:	02 20       	jnz	$+6      	;abs 0x85f4
    85f0:	0f 93       	tst	r15		
    85f2:	e7 27       	jz	$-48     	;abs 0x85c2
    85f4:	38 50 40 00 	add	#64,	r8	;#0x0040
    85f8:	09 63       	adc	r9		
    85fa:	38 f0 80 ff 	and	#-128,	r8	;#0xff80
    85fe:	39 f3       	and	#-1,	r9	;r3 As==11
    8600:	e0 3f       	jmp	$-62     	;abs 0x85c2

00008602 <__gtsf2>:
    8602:	31 50 e8 ff 	add	#-24,	r1	;#0xffe8
    8606:	81 4e 14 00 	mov	r14,	20(r1)	;0x0014(r1)
    860a:	81 4f 16 00 	mov	r15,	22(r1)	;0x0016(r1)
    860e:	81 4c 10 00 	mov	r12,	16(r1)	;0x0010(r1)
    8612:	81 4d 12 00 	mov	r13,	18(r1)	;0x0012(r1)
    8616:	0e 41       	mov	r1,	r14	
    8618:	3e 52       	add	#8,	r14	;r2 As==11
    861a:	0f 41       	mov	r1,	r15	
    861c:	3f 50 14 00 	add	#20,	r15	;#0x0014
    8620:	b0 13 de 8a 	calla	#0x08ade	
    8624:	0e 41       	mov	r1,	r14	
    8626:	0f 41       	mov	r1,	r15	
    8628:	3f 50 10 00 	add	#16,	r15	;#0x0010
    862c:	b0 13 de 8a 	calla	#0x08ade	
    8630:	e1 93 08 00 	cmp.b	#2,	8(r1)	;r3 As==10, 0x0008(r1)
    8634:	0b 28       	jnc	$+24     	;abs 0x864c
    8636:	e1 93 00 00 	cmp.b	#2,	0(r1)	;r3 As==10, 0x0000(r1)
    863a:	08 28       	jnc	$+18     	;abs 0x864c
    863c:	0e 41       	mov	r1,	r14	
    863e:	0f 41       	mov	r1,	r15	
    8640:	3f 52       	add	#8,	r15	;r2 As==11
    8642:	b0 13 ea 8b 	calla	#0x08bea	
    8646:	31 50 18 00 	add	#24,	r1	;#0x0018
    864a:	10 01       	reta			
    864c:	3f 43       	mov	#-1,	r15	;r3 As==11
    864e:	fb 3f       	jmp	$-8      	;abs 0x8646

00008650 <__ltsf2>:
    8650:	31 50 e8 ff 	add	#-24,	r1	;#0xffe8
    8654:	81 4e 14 00 	mov	r14,	20(r1)	;0x0014(r1)
    8658:	81 4f 16 00 	mov	r15,	22(r1)	;0x0016(r1)
    865c:	81 4c 10 00 	mov	r12,	16(r1)	;0x0010(r1)
    8660:	81 4d 12 00 	mov	r13,	18(r1)	;0x0012(r1)
    8664:	0e 41       	mov	r1,	r14	
    8666:	3e 52       	add	#8,	r14	;r2 As==11
    8668:	0f 41       	mov	r1,	r15	
    866a:	3f 50 14 00 	add	#20,	r15	;#0x0014
    866e:	b0 13 de 8a 	calla	#0x08ade	
    8672:	0e 41       	mov	r1,	r14	
    8674:	0f 41       	mov	r1,	r15	
    8676:	3f 50 10 00 	add	#16,	r15	;#0x0010
    867a:	b0 13 de 8a 	calla	#0x08ade	
    867e:	e1 93 08 00 	cmp.b	#2,	8(r1)	;r3 As==10, 0x0008(r1)
    8682:	0b 28       	jnc	$+24     	;abs 0x869a
    8684:	e1 93 00 00 	cmp.b	#2,	0(r1)	;r3 As==10, 0x0000(r1)
    8688:	08 28       	jnc	$+18     	;abs 0x869a
    868a:	0e 41       	mov	r1,	r14	
    868c:	0f 41       	mov	r1,	r15	
    868e:	3f 52       	add	#8,	r15	;r2 As==11
    8690:	b0 13 ea 8b 	calla	#0x08bea	
    8694:	31 50 18 00 	add	#24,	r1	;#0x0018
    8698:	10 01       	reta			
    869a:	1f 43       	mov	#1,	r15	;r3 As==01
    869c:	fb 3f       	jmp	$-8      	;abs 0x8694

0000869e <__lesf2>:
    869e:	31 50 e8 ff 	add	#-24,	r1	;#0xffe8
    86a2:	81 4e 14 00 	mov	r14,	20(r1)	;0x0014(r1)
    86a6:	81 4f 16 00 	mov	r15,	22(r1)	;0x0016(r1)
    86aa:	81 4c 10 00 	mov	r12,	16(r1)	;0x0010(r1)
    86ae:	81 4d 12 00 	mov	r13,	18(r1)	;0x0012(r1)
    86b2:	0e 41       	mov	r1,	r14	
    86b4:	3e 52       	add	#8,	r14	;r2 As==11
    86b6:	0f 41       	mov	r1,	r15	
    86b8:	3f 50 14 00 	add	#20,	r15	;#0x0014
    86bc:	b0 13 de 8a 	calla	#0x08ade	
    86c0:	0e 41       	mov	r1,	r14	
    86c2:	0f 41       	mov	r1,	r15	
    86c4:	3f 50 10 00 	add	#16,	r15	;#0x0010
    86c8:	b0 13 de 8a 	calla	#0x08ade	
    86cc:	e1 93 08 00 	cmp.b	#2,	8(r1)	;r3 As==10, 0x0008(r1)
    86d0:	0b 28       	jnc	$+24     	;abs 0x86e8
    86d2:	e1 93 00 00 	cmp.b	#2,	0(r1)	;r3 As==10, 0x0000(r1)
    86d6:	08 28       	jnc	$+18     	;abs 0x86e8
    86d8:	0e 41       	mov	r1,	r14	
    86da:	0f 41       	mov	r1,	r15	
    86dc:	3f 52       	add	#8,	r15	;r2 As==11
    86de:	b0 13 ea 8b 	calla	#0x08bea	
    86e2:	31 50 18 00 	add	#24,	r1	;#0x0018
    86e6:	10 01       	reta			
    86e8:	1f 43       	mov	#1,	r15	;r3 As==01
    86ea:	fb 3f       	jmp	$-8      	;abs 0x86e2

000086ec <__floatsisf>:
    86ec:	1b 14       	pushm.a	#2,	r11	
    86ee:	31 82       	sub	#8,	r1	;r2 As==11
    86f0:	f1 40 03 00 	mov.b	#3,	0(r1)	;#0x0003, 0x0000(r1)
    86f4:	00 00 
    86f6:	0d 4f       	mov	r15,	r13	
    86f8:	0d 5d       	rla	r13		
    86fa:	0d 43       	clr	r13		
    86fc:	0d 6d       	rlc	r13		
    86fe:	4c 4d       	mov.b	r13,	r12	
    8700:	c1 4d 01 00 	mov.b	r13,	1(r1)	;0x0001(r1)
    8704:	0e 93       	tst	r14		
    8706:	0a 20       	jnz	$+22     	;abs 0x871c
    8708:	0f 93       	tst	r15		
    870a:	08 20       	jnz	$+18     	;abs 0x871c
    870c:	e1 43 00 00 	mov.b	#2,	0(r1)	;r3 As==10, 0x0000(r1)
    8710:	0f 41       	mov	r1,	r15	
    8712:	b0 13 1a 89 	calla	#0x0891a	
    8716:	31 52       	add	#8,	r1	;r2 As==11
    8718:	1a 16       	popm.a	#2,	r11	
    871a:	10 01       	reta			
    871c:	b1 40 1e 00 	mov	#30,	2(r1)	;#0x001e, 0x0002(r1)
    8720:	02 00 
    8722:	4c 93       	tst.b	r12		
    8724:	17 20       	jnz	$+48     	;abs 0x8754
    8726:	0a 4e       	mov	r14,	r10	
    8728:	0b 4f       	mov	r15,	r11	
    872a:	0e 4a       	mov	r10,	r14	
    872c:	0f 4b       	mov	r11,	r15	
    872e:	b0 13 74 88 	calla	#0x08874	
    8732:	3f 53       	add	#-1,	r15	;r3 As==11
    8734:	1f 93       	cmp	#1,	r15	;r3 As==01
    8736:	27 38       	jl	$+80     	;abs 0x8786
    8738:	4e 4f       	mov.b	r15,	r14	
    873a:	7e f0 1f 00 	and.b	#31,	r14	;#0x001f
    873e:	81 4a 04 00 	mov	r10,	4(r1)	;0x0004(r1)
    8742:	81 4b 06 00 	mov	r11,	6(r1)	;0x0006(r1)
    8746:	0f 20       	jnz	$+32     	;abs 0x8766
    8748:	3e 40 1e 00 	mov	#30,	r14	;#0x001e
    874c:	0e 8f       	sub	r15,	r14	
    874e:	81 4e 02 00 	mov	r14,	2(r1)	;0x0002(r1)
    8752:	de 3f       	jmp	$-66     	;abs 0x8710
    8754:	0e 93       	tst	r14		
    8756:	10 24       	jz	$+34     	;abs 0x8778
    8758:	0a 4e       	mov	r14,	r10	
    875a:	0b 4f       	mov	r15,	r11	
    875c:	3a e3       	inv	r10		
    875e:	3b e3       	inv	r11		
    8760:	1a 53       	inc	r10		
    8762:	0b 63       	adc	r11		
    8764:	e2 3f       	jmp	$-58     	;abs 0x872a
    8766:	91 51 04 00 	rla	4(r1)		;0x0004(r1)
    876a:	04 00 
    876c:	91 61 06 00 	rlc	6(r1)		;0x0006(r1)
    8770:	06 00 
    8772:	7e 53       	add.b	#-1,	r14	;r3 As==11
    8774:	f8 23       	jnz	$-14     	;abs 0x8766
    8776:	e8 3f       	jmp	$-46     	;abs 0x8748
    8778:	3f 90 00 80 	cmp	#-32768,r15	;#0x8000
    877c:	ed 23       	jnz	$-36     	;abs 0x8758
    877e:	0e 43       	clr	r14		
    8780:	3f 40 00 cf 	mov	#-12544,r15	;#0xcf00
    8784:	c8 3f       	jmp	$-110    	;abs 0x8716
    8786:	81 4a 04 00 	mov	r10,	4(r1)	;0x0004(r1)
    878a:	81 4b 06 00 	mov	r11,	6(r1)	;0x0006(r1)
    878e:	c0 3f       	jmp	$-126    	;abs 0x8710

00008790 <__floatunsisf>:
    8790:	3b 14       	pushm.a	#4,	r11	
    8792:	31 82       	sub	#8,	r1	;r2 As==11
    8794:	0a 4e       	mov	r14,	r10	
    8796:	0b 4f       	mov	r15,	r11	
    8798:	c1 43 01 00 	mov.b	#0,	1(r1)	;r3 As==00, 0x0001(r1)
    879c:	0e 93       	tst	r14		
    879e:	0a 20       	jnz	$+22     	;abs 0x87b4
    87a0:	0b 93       	tst	r11		
    87a2:	08 20       	jnz	$+18     	;abs 0x87b4
    87a4:	e1 43 00 00 	mov.b	#2,	0(r1)	;r3 As==10, 0x0000(r1)
    87a8:	0f 41       	mov	r1,	r15	
    87aa:	b0 13 1a 89 	calla	#0x0891a	
    87ae:	31 52       	add	#8,	r1	;r2 As==11
    87b0:	38 16       	popm.a	#4,	r11	
    87b2:	10 01       	reta			
    87b4:	f1 40 03 00 	mov.b	#3,	0(r1)	;#0x0003, 0x0000(r1)
    87b8:	00 00 
    87ba:	b1 40 1e 00 	mov	#30,	2(r1)	;#0x001e, 0x0002(r1)
    87be:	02 00 
    87c0:	0e 4a       	mov	r10,	r14	
    87c2:	0f 4b       	mov	r11,	r15	
    87c4:	b0 13 74 88 	calla	#0x08874	
    87c8:	09 4f       	mov	r15,	r9	
    87ca:	39 53       	add	#-1,	r9	;r3 As==11
    87cc:	09 93       	tst	r9		
    87ce:	1d 38       	jl	$+60     	;abs 0x880a
    87d0:	46 24       	jz	$+142    	;abs 0x885e
    87d2:	4f 49       	mov.b	r9,	r15	
    87d4:	7f f0 1f 00 	and.b	#31,	r15	;#0x001f
    87d8:	81 4a 04 00 	mov	r10,	4(r1)	;0x0004(r1)
    87dc:	81 4b 06 00 	mov	r11,	6(r1)	;0x0006(r1)
    87e0:	0b 20       	jnz	$+24     	;abs 0x87f8
    87e2:	3f 40 1e 00 	mov	#30,	r15	;#0x001e
    87e6:	0f 89       	sub	r9,	r15	
    87e8:	81 4f 02 00 	mov	r15,	2(r1)	;0x0002(r1)
    87ec:	0f 41       	mov	r1,	r15	
    87ee:	b0 13 1a 89 	calla	#0x0891a	
    87f2:	31 52       	add	#8,	r1	;r2 As==11
    87f4:	38 16       	popm.a	#4,	r11	
    87f6:	10 01       	reta			
    87f8:	91 51 04 00 	rla	4(r1)		;0x0004(r1)
    87fc:	04 00 
    87fe:	91 61 06 00 	rlc	6(r1)		;0x0006(r1)
    8802:	06 00 
    8804:	7f 53       	add.b	#-1,	r15	;r3 As==11
    8806:	f8 23       	jnz	$-14     	;abs 0x87f8
    8808:	ec 3f       	jmp	$-38     	;abs 0x87e2
    880a:	08 49       	mov	r9,	r8	
    880c:	38 e3       	inv	r8		
    880e:	18 53       	inc	r8		
    8810:	4d 48       	mov.b	r8,	r13	
    8812:	7d f0 1f 00 	and.b	#31,	r13	;#0x001f
    8816:	1e 43       	mov	#1,	r14	;r3 As==01
    8818:	0f 43       	clr	r15		
    881a:	04 24       	jz	$+10     	;abs 0x8824
    881c:	0e 5e       	rla	r14		
    881e:	0f 6f       	rlc	r15		
    8820:	7d 53       	add.b	#-1,	r13	;r3 As==11
    8822:	fc 23       	jnz	$-6      	;abs 0x881c
    8824:	3e 53       	add	#-1,	r14	;r3 As==11
    8826:	3f 63       	addc	#-1,	r15	;r3 As==11
    8828:	0e fa       	and	r10,	r14	
    882a:	0f fb       	and	r11,	r15	
    882c:	1c 43       	mov	#1,	r12	;r3 As==01
    882e:	0d 43       	clr	r13		
    8830:	0e 93       	tst	r14		
    8832:	04 20       	jnz	$+10     	;abs 0x883c
    8834:	0f 93       	tst	r15		
    8836:	02 20       	jnz	$+6      	;abs 0x883c
    8838:	0c 43       	clr	r12		
    883a:	0d 43       	clr	r13		
    883c:	78 f0 1f 00 	and.b	#31,	r8	;#0x001f
    8840:	13 20       	jnz	$+40     	;abs 0x8868
    8842:	0e 4c       	mov	r12,	r14	
    8844:	0f 4d       	mov	r13,	r15	
    8846:	0e da       	bis	r10,	r14	
    8848:	0f db       	bis	r11,	r15	
    884a:	81 4e 04 00 	mov	r14,	4(r1)	;0x0004(r1)
    884e:	81 4f 06 00 	mov	r15,	6(r1)	;0x0006(r1)
    8852:	3f 40 1e 00 	mov	#30,	r15	;#0x001e
    8856:	0f 89       	sub	r9,	r15	
    8858:	81 4f 02 00 	mov	r15,	2(r1)	;0x0002(r1)
    885c:	a5 3f       	jmp	$-180    	;abs 0x87a8
    885e:	81 4a 04 00 	mov	r10,	4(r1)	;0x0004(r1)
    8862:	81 4b 06 00 	mov	r11,	6(r1)	;0x0006(r1)
    8866:	a0 3f       	jmp	$-190    	;abs 0x87a8
    8868:	12 c3       	clrc			
    886a:	0b 10       	rrc	r11		
    886c:	0a 10       	rrc	r10		
    886e:	78 53       	add.b	#-1,	r8	;r3 As==11
    8870:	fb 23       	jnz	$-8      	;abs 0x8868
    8872:	e7 3f       	jmp	$-48     	;abs 0x8842

00008874 <__clzsi2>:
    8874:	2b 14       	pushm.a	#3,	r11	
    8876:	1f 93       	cmp	#1,	r15	;r3 As==01
    8878:	15 2c       	jc	$+44     	;abs 0x88a4
    887a:	3e 90 00 01 	cmp	#256,	r14	;#0x0100
    887e:	2a 28       	jnc	$+86     	;abs 0x88d4
    8880:	3a 40 18 00 	mov	#24,	r10	;#0x0018
    8884:	0b 43       	clr	r11		
    8886:	39 42       	mov	#8,	r9	;r2 As==11
    8888:	49 49       	mov.b	r9,	r9	
    888a:	0c 4e       	mov	r14,	r12	
    888c:	0d 4f       	mov	r15,	r13	
    888e:	49 93       	tst.b	r9		
    8890:	15 20       	jnz	$+44     	;abs 0x88bc
    8892:	3c 50 7c 9d 	add	#-25220,r12	;#0x9d7c
    8896:	6e 4c       	mov.b	@r12,	r14	
    8898:	0f 43       	clr	r15		
    889a:	0a 8e       	sub	r14,	r10	
    889c:	0b 7f       	subc	r15,	r11	
    889e:	0f 4a       	mov	r10,	r15	
    88a0:	29 16       	popm.a	#3,	r11	
    88a2:	10 01       	reta			
    88a4:	3f 90 00 01 	cmp	#256,	r15	;#0x0100
    88a8:	0f 28       	jnc	$+32     	;abs 0x88c8
    88aa:	3a 42       	mov	#8,	r10	;r2 As==11
    88ac:	0b 43       	clr	r11		
    88ae:	39 40 18 00 	mov	#24,	r9	;#0x0018
    88b2:	49 49       	mov.b	r9,	r9	
    88b4:	0c 4e       	mov	r14,	r12	
    88b6:	0d 4f       	mov	r15,	r13	
    88b8:	49 93       	tst.b	r9		
    88ba:	eb 27       	jz	$-40     	;abs 0x8892
    88bc:	12 c3       	clrc			
    88be:	0d 10       	rrc	r13		
    88c0:	0c 10       	rrc	r12		
    88c2:	79 53       	add.b	#-1,	r9	;r3 As==11
    88c4:	fb 23       	jnz	$-8      	;abs 0x88bc
    88c6:	e5 3f       	jmp	$-52     	;abs 0x8892
    88c8:	3a 40 10 00 	mov	#16,	r10	;#0x0010
    88cc:	0b 43       	clr	r11		
    88ce:	39 40 10 00 	mov	#16,	r9	;#0x0010
    88d2:	ef 3f       	jmp	$-32     	;abs 0x88b2
    88d4:	3a 40 20 00 	mov	#32,	r10	;#0x0020
    88d8:	0b 43       	clr	r11		
    88da:	09 43       	clr	r9		
    88dc:	ea 3f       	jmp	$-42     	;abs 0x88b2

000088de <__fixunssfsi>:
    88de:	1b 14       	pushm.a	#2,	r11	
    88e0:	0a 4e       	mov	r14,	r10	
    88e2:	0b 4f       	mov	r15,	r11	
    88e4:	0c 43       	clr	r12		
    88e6:	3d 40 00 4f 	mov	#20224,	r13	;#0x4f00
    88ea:	b0 13 8e 8c 	calla	#0x08c8e	
    88ee:	0f 93       	tst	r15		
    88f0:	06 34       	jge	$+14     	;abs 0x88fe
    88f2:	0e 4a       	mov	r10,	r14	
    88f4:	0f 4b       	mov	r11,	r15	
    88f6:	b0 13 dc 8c 	calla	#0x08cdc	
    88fa:	1a 16       	popm.a	#2,	r11	
    88fc:	10 01       	reta			
    88fe:	0c 43       	clr	r12		
    8900:	3d 40 00 4f 	mov	#20224,	r13	;#0x4f00
    8904:	0e 4a       	mov	r10,	r14	
    8906:	0f 4b       	mov	r11,	r15	
    8908:	b0 13 72 82 	calla	#0x08272	
    890c:	b0 13 dc 8c 	calla	#0x08cdc	
    8910:	0e 53       	add	#0,	r14	;r3 As==00
    8912:	3f 60 00 80 	addc	#-32768,r15	;#0x8000
    8916:	1a 16       	popm.a	#2,	r11	
    8918:	10 01       	reta			

0000891a <__pack_f>:
    891a:	3b 14       	pushm.a	#4,	r11	
    891c:	0d 4f       	mov	r15,	r13	
    891e:	1e 4f 04 00 	mov	4(r15),	r14	;0x0004(r15)
    8922:	1f 4f 06 00 	mov	6(r15),	r15	;0x0006(r15)
    8926:	5b 4d 01 00 	mov.b	1(r13),	r11	;0x0001(r13)
    892a:	6c 4d       	mov.b	@r13,	r12	
    892c:	6c 93       	cmp.b	#2,	r12	;r3 As==10
    892e:	66 28       	jnc	$+206    	;abs 0x89fc
    8930:	6c 92       	cmp.b	#4,	r12	;r2 As==10
    8932:	60 24       	jz	$+194    	;abs 0x89f4
    8934:	6c 93       	cmp.b	#2,	r12	;r3 As==10
    8936:	36 24       	jz	$+110    	;abs 0x89a4
    8938:	0e 93       	tst	r14		
    893a:	32 24       	jz	$+102    	;abs 0x89a0
    893c:	19 4d 02 00 	mov	2(r13),	r9	;0x0002(r13)
    8940:	39 90 82 ff 	cmp	#-126,	r9	;#0xff82
    8944:	63 38       	jl	$+200    	;abs 0x8a0c
    8946:	39 90 80 00 	cmp	#128,	r9	;#0x0080
    894a:	54 34       	jge	$+170    	;abs 0x89f4
    894c:	0c 4e       	mov	r14,	r12	
    894e:	0d 4f       	mov	r15,	r13	
    8950:	3c f0 7f 00 	and	#127,	r12	;#0x007f
    8954:	0d f3       	and	#0,	r13	;r3 As==00
    8956:	3c 90 40 00 	cmp	#64,	r12	;#0x0040
    895a:	36 24       	jz	$+110    	;abs 0x89c8
    895c:	3e 50 3f 00 	add	#63,	r14	;#0x003f
    8960:	0f 63       	adc	r15		
    8962:	0f 93       	tst	r15		
    8964:	40 38       	jl	$+130    	;abs 0x89e6
    8966:	0c 49       	mov	r9,	r12	
    8968:	3c 50 7f 00 	add	#127,	r12	;#0x007f
    896c:	12 c3       	clrc			
    896e:	0f 10       	rrc	r15		
    8970:	0e 10       	rrc	r14		
    8972:	12 c3       	clrc			
    8974:	0f 10       	rrc	r15		
    8976:	0e 10       	rrc	r14		
    8978:	12 c3       	clrc			
    897a:	0f 10       	rrc	r15		
    897c:	0e 10       	rrc	r14		
    897e:	12 c3       	clrc			
    8980:	0f 10       	rrc	r15		
    8982:	0e 10       	rrc	r14		
    8984:	12 c3       	clrc			
    8986:	0f 10       	rrc	r15		
    8988:	0e 10       	rrc	r14		
    898a:	12 c3       	clrc			
    898c:	0f 10       	rrc	r15		
    898e:	0e 10       	rrc	r14		
    8990:	12 c3       	clrc			
    8992:	0f 10       	rrc	r15		
    8994:	0e 10       	rrc	r14		
    8996:	3e f3       	and	#-1,	r14	;r3 As==11
    8998:	3f f0 7f 00 	and	#127,	r15	;#0x007f
    899c:	4c 4c       	mov.b	r12,	r12	
    899e:	05 3c       	jmp	$+12     	;abs 0x89aa
    89a0:	0f 93       	tst	r15		
    89a2:	cc 23       	jnz	$-102    	;abs 0x893c
    89a4:	4c 43       	clr.b	r12		
    89a6:	0e 43       	clr	r14		
    89a8:	0f 43       	clr	r15		
    89aa:	4d 4c       	mov.b	r12,	r13	
    89ac:	5d 0e       	rlam	#4,	r13	
    89ae:	5d 0a       	rlam	#3,	r13	
    89b0:	3f f0 7f 00 	and	#127,	r15	;#0x007f
    89b4:	0f dd       	bis	r13,	r15	
    89b6:	4b 4b       	mov.b	r11,	r11	
    89b8:	0b 11       	rra	r11		
    89ba:	0b 43       	clr	r11		
    89bc:	0b 10       	rrc	r11		
    89be:	0d 4f       	mov	r15,	r13	
    89c0:	0d db       	bis	r11,	r13	
    89c2:	0f 4d       	mov	r13,	r15	
    89c4:	38 16       	popm.a	#4,	r11	
    89c6:	10 01       	reta			
    89c8:	0d 93       	tst	r13		
    89ca:	c8 23       	jnz	$-110    	;abs 0x895c
    89cc:	0c 4e       	mov	r14,	r12	
    89ce:	0d 4f       	mov	r15,	r13	
    89d0:	3c f0 80 00 	and	#128,	r12	;#0x0080
    89d4:	0d f3       	and	#0,	r13	;r3 As==00
    89d6:	0c 93       	tst	r12		
    89d8:	02 20       	jnz	$+6      	;abs 0x89de
    89da:	0d 93       	tst	r13		
    89dc:	c2 27       	jz	$-122    	;abs 0x8962
    89de:	3e 50 40 00 	add	#64,	r14	;#0x0040
    89e2:	0f 63       	adc	r15		
    89e4:	be 3f       	jmp	$-130    	;abs 0x8962
    89e6:	12 c3       	clrc			
    89e8:	0f 10       	rrc	r15		
    89ea:	0e 10       	rrc	r14		
    89ec:	0c 49       	mov	r9,	r12	
    89ee:	3c 50 80 00 	add	#128,	r12	;#0x0080
    89f2:	bc 3f       	jmp	$-134    	;abs 0x896c
    89f4:	7c 43       	mov.b	#-1,	r12	;r3 As==11
    89f6:	0e 43       	clr	r14		
    89f8:	0f 43       	clr	r15		
    89fa:	d7 3f       	jmp	$-80     	;abs 0x89aa
    89fc:	0e d3       	bis	#0,	r14	;r3 As==00
    89fe:	3f d0 10 00 	bis	#16,	r15	;#0x0010
    8a02:	3e f3       	and	#-1,	r14	;r3 As==11
    8a04:	3f f0 7f 00 	and	#127,	r15	;#0x007f
    8a08:	7c 43       	mov.b	#-1,	r12	;r3 As==11
    8a0a:	cf 3f       	jmp	$-96     	;abs 0x89aa
    8a0c:	3d 40 82 ff 	mov	#-126,	r13	;#0xff82
    8a10:	0d 89       	sub	r9,	r13	
    8a12:	3d 90 1a 00 	cmp	#26,	r13	;#0x001a
    8a16:	50 34       	jge	$+162    	;abs 0x8ab8
    8a18:	4c 4d       	mov.b	r13,	r12	
    8a1a:	7c f0 1f 00 	and.b	#31,	r12	;#0x001f
    8a1e:	08 4e       	mov	r14,	r8	
    8a20:	09 4f       	mov	r15,	r9	
    8a22:	05 24       	jz	$+12     	;abs 0x8a2e
    8a24:	12 c3       	clrc			
    8a26:	09 10       	rrc	r9		
    8a28:	08 10       	rrc	r8		
    8a2a:	7c 53       	add.b	#-1,	r12	;r3 As==11
    8a2c:	fb 23       	jnz	$-8      	;abs 0x8a24
    8a2e:	4a 4d       	mov.b	r13,	r10	
    8a30:	7a f0 1f 00 	and.b	#31,	r10	;#0x001f
    8a34:	1c 43       	mov	#1,	r12	;r3 As==01
    8a36:	0d 43       	clr	r13		
    8a38:	04 24       	jz	$+10     	;abs 0x8a42
    8a3a:	0c 5c       	rla	r12		
    8a3c:	0d 6d       	rlc	r13		
    8a3e:	7a 53       	add.b	#-1,	r10	;r3 As==11
    8a40:	fc 23       	jnz	$-6      	;abs 0x8a3a
    8a42:	3c 53       	add	#-1,	r12	;r3 As==11
    8a44:	3d 63       	addc	#-1,	r13	;r3 As==11
    8a46:	0c fe       	and	r14,	r12	
    8a48:	0d ff       	and	r15,	r13	
    8a4a:	1e 43       	mov	#1,	r14	;r3 As==01
    8a4c:	0f 43       	clr	r15		
    8a4e:	0c 93       	tst	r12		
    8a50:	04 20       	jnz	$+10     	;abs 0x8a5a
    8a52:	0d 93       	tst	r13		
    8a54:	02 20       	jnz	$+6      	;abs 0x8a5a
    8a56:	0e 43       	clr	r14		
    8a58:	0f 43       	clr	r15		
    8a5a:	0c 4e       	mov	r14,	r12	
    8a5c:	0d 4f       	mov	r15,	r13	
    8a5e:	0c d8       	bis	r8,	r12	
    8a60:	0d d9       	bis	r9,	r13	
    8a62:	0e 4c       	mov	r12,	r14	
    8a64:	0f 4d       	mov	r13,	r15	
    8a66:	3e f0 7f 00 	and	#127,	r14	;#0x007f
    8a6a:	0f f3       	and	#0,	r15	;r3 As==00
    8a6c:	3e 90 40 00 	cmp	#64,	r14	;#0x0040
    8a70:	26 24       	jz	$+78     	;abs 0x8abe
    8a72:	3c 50 3f 00 	add	#63,	r12	;#0x003f
    8a76:	0d 63       	adc	r13		
    8a78:	0e 4c       	mov	r12,	r14	
    8a7a:	0f 4d       	mov	r13,	r15	
    8a7c:	12 c3       	clrc			
    8a7e:	0f 10       	rrc	r15		
    8a80:	0e 10       	rrc	r14		
    8a82:	12 c3       	clrc			
    8a84:	0f 10       	rrc	r15		
    8a86:	0e 10       	rrc	r14		
    8a88:	12 c3       	clrc			
    8a8a:	0f 10       	rrc	r15		
    8a8c:	0e 10       	rrc	r14		
    8a8e:	12 c3       	clrc			
    8a90:	0f 10       	rrc	r15		
    8a92:	0e 10       	rrc	r14		
    8a94:	12 c3       	clrc			
    8a96:	0f 10       	rrc	r15		
    8a98:	0e 10       	rrc	r14		
    8a9a:	12 c3       	clrc			
    8a9c:	0f 10       	rrc	r15		
    8a9e:	0e 10       	rrc	r14		
    8aa0:	12 c3       	clrc			
    8aa2:	0f 10       	rrc	r15		
    8aa4:	0e 10       	rrc	r14		
    8aa6:	3e f3       	and	#-1,	r14	;r3 As==11
    8aa8:	3f f0 7f 00 	and	#127,	r15	;#0x007f
    8aac:	5c 43       	mov.b	#1,	r12	;r3 As==01
    8aae:	3d 90 00 40 	cmp	#16384,	r13	;#0x4000
    8ab2:	7b 2f       	jc	$-264    	;abs 0x89aa
    8ab4:	4c 43       	clr.b	r12		
    8ab6:	79 3f       	jmp	$-268    	;abs 0x89aa
    8ab8:	0c 43       	clr	r12		
    8aba:	0d 43       	clr	r13		
    8abc:	da 3f       	jmp	$-74     	;abs 0x8a72
    8abe:	0f 93       	tst	r15		
    8ac0:	d8 23       	jnz	$-78     	;abs 0x8a72
    8ac2:	0e 4c       	mov	r12,	r14	
    8ac4:	0f 4d       	mov	r13,	r15	
    8ac6:	3e f0 80 00 	and	#128,	r14	;#0x0080
    8aca:	0f f3       	and	#0,	r15	;r3 As==00
    8acc:	0e 93       	tst	r14		
    8ace:	04 24       	jz	$+10     	;abs 0x8ad8
    8ad0:	3c 50 40 00 	add	#64,	r12	;#0x0040
    8ad4:	0d 63       	adc	r13		
    8ad6:	d0 3f       	jmp	$-94     	;abs 0x8a78
    8ad8:	0f 93       	tst	r15		
    8ada:	ce 27       	jz	$-98     	;abs 0x8a78
    8adc:	f9 3f       	jmp	$-12     	;abs 0x8ad0

00008ade <__unpack_f>:
    8ade:	3b 14       	pushm.a	#4,	r11	
    8ae0:	2a 4f       	mov	@r15,	r10	
    8ae2:	59 4f 02 00 	mov.b	2(r15),	r9	;0x0002(r15)
    8ae6:	0b 49       	mov	r9,	r11	
    8ae8:	3b f0 7f 00 	and	#127,	r11	;#0x007f
    8aec:	08 4a       	mov	r10,	r8	
    8aee:	09 4b       	mov	r11,	r9	
    8af0:	1d 4f 02 00 	mov	2(r15),	r13	;0x0002(r15)
    8af4:	5d 0f       	rrum	#4,	r13	
    8af6:	5d 0b       	rrum	#3,	r13	
    8af8:	4d 4d       	mov.b	r13,	r13	
    8afa:	5f 4f 03 00 	mov.b	3(r15),	r15	;0x0003(r15)
    8afe:	4f 5f       	rla.b	r15		
    8b00:	0f 43       	clr	r15		
    8b02:	0f 6f       	rlc	r15		
    8b04:	ce 4f 01 00 	mov.b	r15,	1(r14)	;0x0001(r14)
    8b08:	0d 93       	tst	r13		
    8b0a:	2c 20       	jnz	$+90     	;abs 0x8b64
    8b0c:	0a 93       	tst	r10		
    8b0e:	4f 24       	jz	$+160    	;abs 0x8bae
    8b10:	be 40 82 ff 	mov	#-126,	2(r14)	;#0xff82, 0x0002(r14)
    8b14:	02 00 
    8b16:	0c 48       	mov	r8,	r12	
    8b18:	0d 49       	mov	r9,	r13	
    8b1a:	0c 5c       	rla	r12		
    8b1c:	0d 6d       	rlc	r13		
    8b1e:	0c 5c       	rla	r12		
    8b20:	0d 6d       	rlc	r13		
    8b22:	0c 5c       	rla	r12		
    8b24:	0d 6d       	rlc	r13		
    8b26:	0c 5c       	rla	r12		
    8b28:	0d 6d       	rlc	r13		
    8b2a:	0c 5c       	rla	r12		
    8b2c:	0d 6d       	rlc	r13		
    8b2e:	0c 5c       	rla	r12		
    8b30:	0d 6d       	rlc	r13		
    8b32:	0c 5c       	rla	r12		
    8b34:	0d 6d       	rlc	r13		
    8b36:	fe 40 03 00 	mov.b	#3,	0(r14)	;#0x0003, 0x0000(r14)
    8b3a:	00 00 
    8b3c:	3d 90 00 40 	cmp	#16384,	r13	;#0x4000
    8b40:	0b 2c       	jc	$+24     	;abs 0x8b58
    8b42:	3f 40 81 ff 	mov	#-127,	r15	;#0xff81
    8b46:	0c 5c       	rla	r12		
    8b48:	0d 6d       	rlc	r13		
    8b4a:	0b 4f       	mov	r15,	r11	
    8b4c:	3f 53       	add	#-1,	r15	;r3 As==11
    8b4e:	3d 90 00 40 	cmp	#16384,	r13	;#0x4000
    8b52:	f9 2b       	jnc	$-12     	;abs 0x8b46
    8b54:	8e 4b 02 00 	mov	r11,	2(r14)	;0x0002(r14)
    8b58:	8e 4c 04 00 	mov	r12,	4(r14)	;0x0004(r14)
    8b5c:	8e 4d 06 00 	mov	r13,	6(r14)	;0x0006(r14)
    8b60:	38 16       	popm.a	#4,	r11	
    8b62:	10 01       	reta			
    8b64:	3d 90 ff 00 	cmp	#255,	r13	;#0x00ff
    8b68:	28 24       	jz	$+82     	;abs 0x8bba
    8b6a:	3d 50 81 ff 	add	#-127,	r13	;#0xff81
    8b6e:	8e 4d 02 00 	mov	r13,	2(r14)	;0x0002(r14)
    8b72:	fe 40 03 00 	mov.b	#3,	0(r14)	;#0x0003, 0x0000(r14)
    8b76:	00 00 
    8b78:	0c 4a       	mov	r10,	r12	
    8b7a:	0d 4b       	mov	r11,	r13	
    8b7c:	0c 5c       	rla	r12		
    8b7e:	0d 6d       	rlc	r13		
    8b80:	0c 5c       	rla	r12		
    8b82:	0d 6d       	rlc	r13		
    8b84:	0c 5c       	rla	r12		
    8b86:	0d 6d       	rlc	r13		
    8b88:	0c 5c       	rla	r12		
    8b8a:	0d 6d       	rlc	r13		
    8b8c:	0c 5c       	rla	r12		
    8b8e:	0d 6d       	rlc	r13		
    8b90:	0c 5c       	rla	r12		
    8b92:	0d 6d       	rlc	r13		
    8b94:	0c 5c       	rla	r12		
    8b96:	0d 6d       	rlc	r13		
    8b98:	0a 4c       	mov	r12,	r10	
    8b9a:	0b 4d       	mov	r13,	r11	
    8b9c:	0a d3       	bis	#0,	r10	;r3 As==00
    8b9e:	3b d0 00 40 	bis	#16384,	r11	;#0x4000
    8ba2:	8e 4a 04 00 	mov	r10,	4(r14)	;0x0004(r14)
    8ba6:	8e 4b 06 00 	mov	r11,	6(r14)	;0x0006(r14)
    8baa:	38 16       	popm.a	#4,	r11	
    8bac:	10 01       	reta			
    8bae:	0b 93       	tst	r11		
    8bb0:	af 23       	jnz	$-160    	;abs 0x8b10
    8bb2:	ee 43 00 00 	mov.b	#2,	0(r14)	;r3 As==10, 0x0000(r14)
    8bb6:	38 16       	popm.a	#4,	r11	
    8bb8:	10 01       	reta			
    8bba:	0a 93       	tst	r10		
    8bbc:	0e 24       	jz	$+30     	;abs 0x8bda
    8bbe:	0a f3       	and	#0,	r10	;r3 As==00
    8bc0:	3b f0 10 00 	and	#16,	r11	;#0x0010
    8bc4:	0a 93       	tst	r10		
    8bc6:	02 20       	jnz	$+6      	;abs 0x8bcc
    8bc8:	0b 93       	tst	r11		
    8bca:	0c 24       	jz	$+26     	;abs 0x8be4
    8bcc:	de 43 00 00 	mov.b	#1,	0(r14)	;r3 As==01, 0x0000(r14)
    8bd0:	8e 48 04 00 	mov	r8,	4(r14)	;0x0004(r14)
    8bd4:	8e 49 06 00 	mov	r9,	6(r14)	;0x0006(r14)
    8bd8:	e8 3f       	jmp	$-46     	;abs 0x8baa
    8bda:	0b 93       	tst	r11		
    8bdc:	f0 23       	jnz	$-30     	;abs 0x8bbe
    8bde:	ee 42 00 00 	mov.b	#4,	0(r14)	;r2 As==10, 0x0000(r14)
    8be2:	e3 3f       	jmp	$-56     	;abs 0x8baa
    8be4:	ce 43 00 00 	mov.b	#0,	0(r14)	;r3 As==00, 0x0000(r14)
    8be8:	f3 3f       	jmp	$-24     	;abs 0x8bd0

00008bea <__fpcmp_parts_f>:
    8bea:	0b 14       	pushm.a	#1,	r11	
    8bec:	6d 4f       	mov.b	@r15,	r13	
    8bee:	6d 93       	cmp.b	#2,	r13	;r3 As==10
    8bf0:	12 28       	jnc	$+38     	;abs 0x8c16
    8bf2:	6c 4e       	mov.b	@r14,	r12	
    8bf4:	6c 93       	cmp.b	#2,	r12	;r3 As==10
    8bf6:	0f 28       	jnc	$+32     	;abs 0x8c16
    8bf8:	6d 92       	cmp.b	#4,	r13	;r2 As==10
    8bfa:	41 24       	jz	$+132    	;abs 0x8c7e
    8bfc:	6c 92       	cmp.b	#4,	r12	;r2 As==10
    8bfe:	11 24       	jz	$+36     	;abs 0x8c22
    8c00:	6d 93       	cmp.b	#2,	r13	;r3 As==10
    8c02:	0d 24       	jz	$+28     	;abs 0x8c1e
    8c04:	6c 93       	cmp.b	#2,	r12	;r3 As==10
    8c06:	14 24       	jz	$+42     	;abs 0x8c30
    8c08:	5d 4f 01 00 	mov.b	1(r15),	r13	;0x0001(r15)
    8c0c:	5d 9e 01 00 	cmp.b	1(r14),	r13	;0x0001(r14)
    8c10:	14 24       	jz	$+42     	;abs 0x8c3a
    8c12:	4d 93       	tst.b	r13		
    8c14:	09 20       	jnz	$+20     	;abs 0x8c28
    8c16:	1e 43       	mov	#1,	r14	;r3 As==01
    8c18:	0f 4e       	mov	r14,	r15	
    8c1a:	0b 16       	popm.a	#1,	r11	
    8c1c:	10 01       	reta			
    8c1e:	6c 93       	cmp.b	#2,	r12	;r3 As==10
    8c20:	28 24       	jz	$+82     	;abs 0x8c72
    8c22:	ce 93 01 00 	tst.b	1(r14)		;0x0001(r14)
    8c26:	f7 23       	jnz	$-16     	;abs 0x8c16
    8c28:	3e 43       	mov	#-1,	r14	;r3 As==11
    8c2a:	0f 4e       	mov	r14,	r15	
    8c2c:	0b 16       	popm.a	#1,	r11	
    8c2e:	10 01       	reta			
    8c30:	cf 93 01 00 	tst.b	1(r15)		;0x0001(r15)
    8c34:	f0 27       	jz	$-30     	;abs 0x8c16
    8c36:	3e 43       	mov	#-1,	r14	;r3 As==11
    8c38:	f8 3f       	jmp	$-14     	;abs 0x8c2a
    8c3a:	1b 4f 02 00 	mov	2(r15),	r11	;0x0002(r15)
    8c3e:	1c 4e 02 00 	mov	2(r14),	r12	;0x0002(r14)
    8c42:	0c 9b       	cmp	r11,	r12	
    8c44:	e6 3b       	jl	$-50     	;abs 0x8c12
    8c46:	0b 9c       	cmp	r12,	r11	
    8c48:	16 38       	jl	$+46     	;abs 0x8c76
    8c4a:	1b 4f 04 00 	mov	4(r15),	r11	;0x0004(r15)
    8c4e:	1f 4f 06 00 	mov	6(r15),	r15	;0x0006(r15)
    8c52:	1c 4e 04 00 	mov	4(r14),	r12	;0x0004(r14)
    8c56:	1e 4e 06 00 	mov	6(r14),	r14	;0x0006(r14)
    8c5a:	0e 9f       	cmp	r15,	r14	
    8c5c:	da 2b       	jnc	$-74     	;abs 0x8c12
    8c5e:	0f 9e       	cmp	r14,	r15	
    8c60:	02 28       	jnc	$+6      	;abs 0x8c66
    8c62:	0c 9b       	cmp	r11,	r12	
    8c64:	d6 2b       	jnc	$-82     	;abs 0x8c12
    8c66:	0f 9e       	cmp	r14,	r15	
    8c68:	06 28       	jnc	$+14     	;abs 0x8c76
    8c6a:	0e 9f       	cmp	r15,	r14	
    8c6c:	02 28       	jnc	$+6      	;abs 0x8c72
    8c6e:	0b 9c       	cmp	r12,	r11	
    8c70:	02 28       	jnc	$+6      	;abs 0x8c76
    8c72:	0e 43       	clr	r14		
    8c74:	d1 3f       	jmp	$-92     	;abs 0x8c18
    8c76:	4d 93       	tst.b	r13		
    8c78:	ce 23       	jnz	$-98     	;abs 0x8c16
    8c7a:	3e 43       	mov	#-1,	r14	;r3 As==11
    8c7c:	d6 3f       	jmp	$-82     	;abs 0x8c2a
    8c7e:	6c 92       	cmp.b	#4,	r12	;r2 As==10
    8c80:	d7 23       	jnz	$-80     	;abs 0x8c30
    8c82:	5e 4e 01 00 	mov.b	1(r14),	r14	;0x0001(r14)
    8c86:	5f 4f 01 00 	mov.b	1(r15),	r15	;0x0001(r15)
    8c8a:	0e 8f       	sub	r15,	r14	
    8c8c:	c5 3f       	jmp	$-116    	;abs 0x8c18

00008c8e <__gesf2>:
    8c8e:	31 50 e8 ff 	add	#-24,	r1	;#0xffe8
    8c92:	81 4e 14 00 	mov	r14,	20(r1)	;0x0014(r1)
    8c96:	81 4f 16 00 	mov	r15,	22(r1)	;0x0016(r1)
    8c9a:	81 4c 10 00 	mov	r12,	16(r1)	;0x0010(r1)
    8c9e:	81 4d 12 00 	mov	r13,	18(r1)	;0x0012(r1)
    8ca2:	0e 41       	mov	r1,	r14	
    8ca4:	3e 52       	add	#8,	r14	;r2 As==11
    8ca6:	0f 41       	mov	r1,	r15	
    8ca8:	3f 50 14 00 	add	#20,	r15	;#0x0014
    8cac:	b0 13 de 8a 	calla	#0x08ade	
    8cb0:	0e 41       	mov	r1,	r14	
    8cb2:	0f 41       	mov	r1,	r15	
    8cb4:	3f 50 10 00 	add	#16,	r15	;#0x0010
    8cb8:	b0 13 de 8a 	calla	#0x08ade	
    8cbc:	e1 93 08 00 	cmp.b	#2,	8(r1)	;r3 As==10, 0x0008(r1)
    8cc0:	0b 28       	jnc	$+24     	;abs 0x8cd8
    8cc2:	e1 93 00 00 	cmp.b	#2,	0(r1)	;r3 As==10, 0x0000(r1)
    8cc6:	08 28       	jnc	$+18     	;abs 0x8cd8
    8cc8:	0e 41       	mov	r1,	r14	
    8cca:	0f 41       	mov	r1,	r15	
    8ccc:	3f 52       	add	#8,	r15	;r2 As==11
    8cce:	b0 13 ea 8b 	calla	#0x08bea	
    8cd2:	31 50 18 00 	add	#24,	r1	;#0x0018
    8cd6:	10 01       	reta			
    8cd8:	3f 43       	mov	#-1,	r15	;r3 As==11
    8cda:	fb 3f       	jmp	$-8      	;abs 0x8cd2

00008cdc <__fixsfsi>:
    8cdc:	31 50 f4 ff 	add	#-12,	r1	;#0xfff4
    8ce0:	81 4e 08 00 	mov	r14,	8(r1)	;0x0008(r1)
    8ce4:	81 4f 0a 00 	mov	r15,	10(r1)	;0x000a(r1)
    8ce8:	0e 41       	mov	r1,	r14	
    8cea:	0f 41       	mov	r1,	r15	
    8cec:	3f 52       	add	#8,	r15	;r2 As==11
    8cee:	b0 13 de 8a 	calla	#0x08ade	
    8cf2:	6f 41       	mov.b	@r1,	r15	
    8cf4:	6f 93       	cmp.b	#2,	r15	;r3 As==10
    8cf6:	27 24       	jz	$+80     	;abs 0x8d46
    8cf8:	26 28       	jnc	$+78     	;abs 0x8d46
    8cfa:	6f 92       	cmp.b	#4,	r15	;r2 As==10
    8cfc:	07 24       	jz	$+16     	;abs 0x8d0c
    8cfe:	1f 41 02 00 	mov	2(r1),	r15	;0x0002(r1)
    8d02:	0f 93       	tst	r15		
    8d04:	20 38       	jl	$+66     	;abs 0x8d46
    8d06:	3f 90 1f 00 	cmp	#31,	r15	;#0x001f
    8d0a:	09 38       	jl	$+20     	;abs 0x8d1e
    8d0c:	c1 93 01 00 	tst.b	1(r1)		;0x0001(r1)
    8d10:	25 20       	jnz	$+76     	;abs 0x8d5c
    8d12:	3e 43       	mov	#-1,	r14	;r3 As==11
    8d14:	3f 40 ff 7f 	mov	#32767,	r15	;#0x7fff
    8d18:	31 50 0c 00 	add	#12,	r1	;#0x000c
    8d1c:	10 01       	reta			
    8d1e:	3d 40 1e 00 	mov	#30,	r13	;#0x001e
    8d22:	4d 8f       	sub.b	r15,	r13	
    8d24:	7d f0 1f 00 	and.b	#31,	r13	;#0x001f
    8d28:	1e 41 04 00 	mov	4(r1),	r14	;0x0004(r1)
    8d2c:	1f 41 06 00 	mov	6(r1),	r15	;0x0006(r1)
    8d30:	0f 20       	jnz	$+32     	;abs 0x8d50
    8d32:	c1 93 01 00 	tst.b	1(r1)		;0x0001(r1)
    8d36:	f0 27       	jz	$-30     	;abs 0x8d18
    8d38:	3e e3       	inv	r14		
    8d3a:	3f e3       	inv	r15		
    8d3c:	1e 53       	inc	r14		
    8d3e:	0f 63       	adc	r15		
    8d40:	31 50 0c 00 	add	#12,	r1	;#0x000c
    8d44:	10 01       	reta			
    8d46:	0e 43       	clr	r14		
    8d48:	0f 43       	clr	r15		
    8d4a:	31 50 0c 00 	add	#12,	r1	;#0x000c
    8d4e:	10 01       	reta			
    8d50:	12 c3       	clrc			
    8d52:	0f 10       	rrc	r15		
    8d54:	0e 10       	rrc	r14		
    8d56:	7d 53       	add.b	#-1,	r13	;r3 As==11
    8d58:	fb 23       	jnz	$-8      	;abs 0x8d50
    8d5a:	eb 3f       	jmp	$-40     	;abs 0x8d32
    8d5c:	0e 43       	clr	r14		
    8d5e:	3f 40 00 80 	mov	#-32768,r15	;#0x8000
    8d62:	31 50 0c 00 	add	#12,	r1	;#0x000c
    8d66:	10 01       	reta			

00008d68 <printf>:
    8d68:	0d 41       	mov	r1,	r13	
    8d6a:	2d 52       	add	#4,	r13	;r2 As==10
    8d6c:	3e 4d       	mov	@r13+,	r14	
    8d6e:	8f 00 ce 6c 	mova	#0x06cce,r15	
    8d72:	b0 13 60 8f 	calla	#0x08f60	
    8d76:	10 01       	reta			

00008d78 <append>:
    8d78:	1e 42 d0 23 	mov	&0x23d0,r14	
    8d7c:	1e 93       	cmp	#1,	r14	;r3 As==01
    8d7e:	0b 38       	jl	$+24     	;abs 0x8d96
    8d80:	1d 42 ce 23 	mov	&0x23ce,r13	
    8d84:	cd 4f 00 00 	mov.b	r15,	0(r13)	;0x0000(r13)
    8d88:	1d 53       	inc	r13		
    8d8a:	82 4d ce 23 	mov	r13,	&0x23ce	
    8d8e:	3e 53       	add	#-1,	r14	;r3 As==11
    8d90:	82 4e d0 23 	mov	r14,	&0x23d0	
    8d94:	10 01       	reta			
    8d96:	3f 43       	mov	#-1,	r15	;r3 As==11
    8d98:	10 01       	reta			

00008d9a <call_vuprintf>:
    8d9a:	1b 14       	pushm.a	#2,	r11	
    8d9c:	21 83       	decd	r1		
    8d9e:	81 4e 00 00 	mov	r14,	0(r1)	;0x0000(r1)
    8da2:	1a 42 ce 23 	mov	&0x23ce,r10	
    8da6:	1b 42 d0 23 	mov	&0x23d0,r11	
    8daa:	0d 4e       	mov	r14,	r13	
    8dac:	0e 4f       	mov	r15,	r14	
    8dae:	8f 00 78 8d 	mova	#0x08d78,r15	
    8db2:	b0 13 60 8f 	calla	#0x08f60	
    8db6:	0f 9b       	cmp	r11,	r15	
    8db8:	04 38       	jl	$+10     	;abs 0x8dc2
    8dba:	0b 5a       	add	r10,	r11	
    8dbc:	cb 43 ff ff 	mov.b	#0,	-1(r11)	;r3 As==00, 0xffff(r11)
    8dc0:	04 3c       	jmp	$+10     	;abs 0x8dca
    8dc2:	1e 42 ce 23 	mov	&0x23ce,r14	
    8dc6:	ce 43 00 00 	mov.b	#0,	0(r14)	;r3 As==00, 0x0000(r14)
    8dca:	21 53       	incd	r1		
    8dcc:	1a 16       	popm.a	#2,	r11	
    8dce:	10 01       	reta			

00008dd0 <sprintf>:
    8dd0:	92 41 04 00 	mov	4(r1),	&0x23ce	;0x0004(r1)
    8dd4:	ce 23 
    8dd6:	b2 40 ff 7f 	mov	#32767,	&0x23d0	;#0x7fff
    8dda:	d0 23 
    8ddc:	0e 41       	mov	r1,	r14	
    8dde:	3e 52       	add	#8,	r14	;r2 As==11
    8de0:	1f 41 06 00 	mov	6(r1),	r15	;0x0006(r1)
    8de4:	b0 13 9a 8d 	calla	#0x08d9a	
    8de8:	10 01       	reta			

00008dea <print_field>:
    8dea:	7b 14       	pushm.a	#8,	r11	
    8dec:	31 82       	sub	#8,	r1	;r2 As==11
    8dee:	c9 0f       	mova	r15,	r9	
    8df0:	05 4e       	mov	r14,	r5	
    8df2:	0b 4d       	mov	r13,	r11	
    8df4:	17 41 2c 00 	mov	44(r1),	r7	;0x002c(r1)
    8df8:	1d 41 2e 00 	mov	46(r1),	r13	;0x002e(r1)
    8dfc:	06 4d       	mov	r13,	r6	
    8dfe:	86 10       	swpb	r6		
    8e00:	4f 46       	mov.b	r6,	r15	
    8e02:	4c 4d       	mov.b	r13,	r12	
    8e04:	4e 47       	mov.b	r7,	r14	
    8e06:	4e 93       	tst.b	r14		
    8e08:	11 34       	jge	$+36     	;abs 0x8e2c
    8e0a:	f1 40 30 00 	mov.b	#48,	0(r1)	;#0x0030, 0x0000(r1)
    8e0e:	00 00 
    8e10:	0d 47       	mov	r7,	r13	
    8e12:	8d 10       	swpb	r13		
    8e14:	6d f3       	and.b	#2,	r13	;r3 As==10
    8e16:	03 24       	jz	$+8      	;abs 0x8e1e
    8e18:	7d 40 58 00 	mov.b	#88,	r13	;#0x0058
    8e1c:	02 3c       	jmp	$+6      	;abs 0x8e22
    8e1e:	7d 40 78 00 	mov.b	#120,	r13	;#0x0078
    8e22:	c1 4d 01 00 	mov.b	r13,	1(r1)	;0x0001(r1)
    8e26:	0a 41       	mov	r1,	r10	
    8e28:	2a 53       	incd	r10		
    8e2a:	0f 3c       	jmp	$+32     	;abs 0x8e4a
    8e2c:	7e b0 40 00 	bit.b	#64,	r14	;#0x0040
    8e30:	04 24       	jz	$+10     	;abs 0x8e3a
    8e32:	f1 40 30 00 	mov.b	#48,	0(r1)	;#0x0030, 0x0000(r1)
    8e36:	00 00 
    8e38:	04 3c       	jmp	$+10     	;abs 0x8e42
    8e3a:	4c 93       	tst.b	r12		
    8e3c:	05 24       	jz	$+12     	;abs 0x8e48
    8e3e:	c1 4d 00 00 	mov.b	r13,	0(r1)	;0x0000(r1)
    8e42:	0a 41       	mov	r1,	r10	
    8e44:	1a 53       	inc	r10		
    8e46:	01 3c       	jmp	$+4      	;abs 0x8e4a
    8e48:	0a 41       	mov	r1,	r10	
    8e4a:	0a 81       	sub	r1,	r10	
    8e4c:	87 10       	swpb	r7		
    8e4e:	77 b2       	bit.b	#8,	r7	;r2 As==11
    8e50:	02 24       	jz	$+6      	;abs 0x8e56
    8e52:	08 4f       	mov	r15,	r8	
    8e54:	01 3c       	jmp	$+4      	;abs 0x8e58
    8e56:	38 43       	mov	#-1,	r8	;r3 As==11
    8e58:	7e f0 20 00 	and.b	#32,	r14	;#0x0020
    8e5c:	47 20       	jnz	$+144    	;abs 0x8eec
    8e5e:	0c 45       	mov	r5,	r12	
    8e60:	3c 53       	add	#-1,	r12	;r3 As==11
    8e62:	1c 53       	inc	r12		
    8e64:	cc 93 00 00 	tst.b	0(r12)		;0x0000(r12)
    8e68:	fc 23       	jnz	$-6      	;abs 0x8e62
    8e6a:	0c 85       	sub	r5,	r12	
    8e6c:	0b 9a       	cmp	r10,	r11	
    8e6e:	02 28       	jnc	$+6      	;abs 0x8e74
    8e70:	0b 8a       	sub	r10,	r11	
    8e72:	01 3c       	jmp	$+4      	;abs 0x8e76
    8e74:	0b 43       	clr	r11		
    8e76:	67 b2       	bit.b	#4,	r7	;r2 As==10
    8e78:	05 24       	jz	$+12     	;abs 0x8e84
    8e7a:	0b 9f       	cmp	r15,	r11	
    8e7c:	02 28       	jnc	$+6      	;abs 0x8e82
    8e7e:	0b 8f       	sub	r15,	r11	
    8e80:	01 3c       	jmp	$+4      	;abs 0x8e84
    8e82:	0b 43       	clr	r11		
    8e84:	08 9c       	cmp	r12,	r8	
    8e86:	01 2c       	jc	$+4      	;abs 0x8e8a
    8e88:	0c 48       	mov	r8,	r12	
    8e8a:	57 b3       	bit.b	#1,	r7	;r3 As==01
    8e8c:	11 20       	jnz	$+36     	;abs 0x8eb0
    8e8e:	f1 40 20 00 	mov.b	#32,	2(r1)	;#0x0020, 0x0002(r1)
    8e92:	02 00 
    8e94:	04 43       	clr	r4		
    8e96:	0d 43       	clr	r13		
    8e98:	16 3c       	jmp	$+46     	;abs 0x8ec6
    8e9a:	0f 41       	mov	r1,	r15	
    8e9c:	0f 54       	add	r4,	r15	
    8e9e:	6f 4f       	mov.b	@r15,	r15	
    8ea0:	8f 11       	sxt	r15		
    8ea2:	14 53       	inc	r4		
    8ea4:	81 4c 06 00 	mov	r12,	6(r1)	;0x0006(r1)
    8ea8:	49 13       	calla	r9		
    8eaa:	1c 41 06 00 	mov	6(r1),	r12	;0x0006(r1)
    8eae:	01 3c       	jmp	$+4      	;abs 0x8eb2
    8eb0:	04 43       	clr	r4		
    8eb2:	04 9a       	cmp	r10,	r4	
    8eb4:	f2 3b       	jl	$-26     	;abs 0x8e9a
    8eb6:	04 4a       	mov	r10,	r4	
    8eb8:	0a 93       	tst	r10		
    8eba:	01 34       	jge	$+4      	;abs 0x8ebe
    8ebc:	04 43       	clr	r4		
    8ebe:	0d 4a       	mov	r10,	r13	
    8ec0:	f1 40 30 00 	mov.b	#48,	2(r1)	;#0x0030, 0x0002(r1)
    8ec4:	02 00 
    8ec6:	0c 8d       	sub	r13,	r12	
    8ec8:	81 4c 04 00 	mov	r12,	4(r1)	;0x0004(r1)
    8ecc:	09 3c       	jmp	$+20     	;abs 0x8ee0
    8ece:	5f 41 02 00 	mov.b	2(r1),	r15	;0x0002(r1)
    8ed2:	8f 11       	sxt	r15		
    8ed4:	81 4d 06 00 	mov	r13,	6(r1)	;0x0006(r1)
    8ed8:	49 13       	calla	r9		
    8eda:	1d 41 06 00 	mov	6(r1),	r13	;0x0006(r1)
    8ede:	1d 53       	inc	r13		
    8ee0:	1f 41 04 00 	mov	4(r1),	r15	;0x0004(r1)
    8ee4:	0f 5d       	add	r13,	r15	
    8ee6:	0f 9b       	cmp	r11,	r15	
    8ee8:	f2 2b       	jnc	$-26     	;abs 0x8ece
    8eea:	02 3c       	jmp	$+6      	;abs 0x8ef0
    8eec:	04 43       	clr	r4		
    8eee:	0d 43       	clr	r13		
    8ef0:	0d 84       	sub	r4,	r13	
    8ef2:	81 4d 04 00 	mov	r13,	4(r1)	;0x0004(r1)
    8ef6:	05 3c       	jmp	$+12     	;abs 0x8f02
    8ef8:	14 53       	inc	r4		
    8efa:	0d 51       	add	r1,	r13	
    8efc:	6f 4d       	mov.b	@r13,	r15	
    8efe:	8f 11       	sxt	r15		
    8f00:	49 13       	calla	r9		
    8f02:	0d 44       	mov	r4,	r13	
    8f04:	1f 41 04 00 	mov	4(r1),	r15	;0x0004(r1)
    8f08:	0f 54       	add	r4,	r15	
    8f0a:	81 4f 02 00 	mov	r15,	2(r1)	;0x0002(r1)
    8f0e:	04 9a       	cmp	r10,	r4	
    8f10:	f3 3b       	jl	$-24     	;abs 0x8ef8
    8f12:	67 f2       	and.b	#4,	r7	;r2 As==10
    8f14:	05 24       	jz	$+12     	;abs 0x8f20
    8f16:	4a 46       	mov.b	r6,	r10	
    8f18:	0a 3c       	jmp	$+22     	;abs 0x8f2e
    8f1a:	4f 46       	mov.b	r6,	r15	
    8f1c:	1f 51 02 00 	add	2(r1),	r15	;0x0002(r1)
    8f20:	08 5f       	add	r15,	r8	
    8f22:	0a 4f       	mov	r15,	r10	
    8f24:	05 8f       	sub	r15,	r5	
    8f26:	0a 3c       	jmp	$+22     	;abs 0x8f3c
    8f28:	3f 40 30 00 	mov	#48,	r15	;#0x0030
    8f2c:	49 13       	calla	r9		
    8f2e:	7a 53       	add.b	#-1,	r10	;r3 As==11
    8f30:	7a 93       	cmp.b	#-1,	r10	;r3 As==11
    8f32:	fa 23       	jnz	$-10     	;abs 0x8f28
    8f34:	f2 3f       	jmp	$-26     	;abs 0x8f1a
    8f36:	8f 11       	sxt	r15		
    8f38:	49 13       	calla	r9		
    8f3a:	1a 53       	inc	r10		
    8f3c:	0f 45       	mov	r5,	r15	
    8f3e:	0f 5a       	add	r10,	r15	
    8f40:	6f 4f       	mov.b	@r15,	r15	
    8f42:	4f 93       	tst.b	r15		
    8f44:	07 24       	jz	$+16     	;abs 0x8f54
    8f46:	0a 98       	cmp	r8,	r10	
    8f48:	f6 23       	jnz	$-18     	;abs 0x8f36
    8f4a:	04 3c       	jmp	$+10     	;abs 0x8f54
    8f4c:	3f 40 20 00 	mov	#32,	r15	;#0x0020
    8f50:	49 13       	calla	r9		
    8f52:	1a 53       	inc	r10		
    8f54:	0a 9b       	cmp	r11,	r10	
    8f56:	fa 2b       	jnc	$-10     	;abs 0x8f4c
    8f58:	0f 4a       	mov	r10,	r15	
    8f5a:	31 52       	add	#8,	r1	;r2 As==11
    8f5c:	74 16       	popm.a	#8,	r11	
    8f5e:	10 01       	reta			

00008f60 <vuprintf>:
    8f60:	7b 14       	pushm.a	#8,	r11	
    8f62:	31 50 be ff 	add	#-66,	r1	;#0xffbe
    8f66:	71 0f 3c 00 	mova	r15,	60(r1)	;0x003c(r1)
    8f6a:	0b 4d       	mov	r13,	r11	
    8f6c:	81 4e 40 00 	mov	r14,	64(r1)	;0x0040(r1)
    8f70:	c1 43 2b 00 	mov.b	#0,	43(r1)	;r3 As==00, 0x002b(r1)
    8f74:	c1 43 26 00 	mov.b	#0,	38(r1)	;r3 As==00, 0x0026(r1)
    8f78:	c1 43 2a 00 	mov.b	#0,	42(r1)	;r3 As==00, 0x002a(r1)
    8f7c:	c1 43 27 00 	mov.b	#0,	39(r1)	;r3 As==00, 0x0027(r1)
    8f80:	81 43 30 00 	mov	#0,	48(r1)	;r3 As==00, 0x0030(r1)
    8f84:	04 43       	clr	r4		
    8f86:	0d 43       	clr	r13		
    8f88:	81 43 28 00 	mov	#0,	40(r1)	;r3 As==00, 0x0028(r1)
    8f8c:	08 41       	mov	r1,	r8	
    8f8e:	38 50 18 00 	add	#24,	r8	;#0x0018
    8f92:	81 48 1c 00 	mov	r8,	28(r1)	;0x001c(r1)
    8f96:	80 00 82 96 	bra	#0x09682	
    8f9a:	0d 93       	tst	r13		
    8f9c:	1d 20       	jnz	$+60     	;abs 0x8fd8
    8f9e:	7f 90 25 00 	cmp.b	#37,	r15	;#0x0025
    8fa2:	13 20       	jnz	$+40     	;abs 0x8fca
    8fa4:	81 43 18 00 	mov	#0,	24(r1)	;r3 As==00, 0x0018(r1)
    8fa8:	81 43 1a 00 	mov	#0,	26(r1)	;r3 As==00, 0x001a(r1)
    8fac:	81 4e 40 00 	mov	r14,	64(r1)	;0x0040(r1)
    8fb0:	c1 43 2b 00 	mov.b	#0,	43(r1)	;r3 As==00, 0x002b(r1)
    8fb4:	c1 43 26 00 	mov.b	#0,	38(r1)	;r3 As==00, 0x0026(r1)
    8fb8:	c1 43 2a 00 	mov.b	#0,	42(r1)	;r3 As==00, 0x002a(r1)
    8fbc:	c1 43 27 00 	mov.b	#0,	39(r1)	;r3 As==00, 0x0027(r1)
    8fc0:	81 43 30 00 	mov	#0,	48(r1)	;r3 As==00, 0x0030(r1)
    8fc4:	80 00 7a 96 	bra	#0x0967a	
    8fc8:	0b 4a       	mov	r10,	r11	
    8fca:	8f 11       	sxt	r15		
    8fcc:	51 13 3e 00 	calla	62(r1)		;0x003e(r1)
    8fd0:	91 53 28 00 	inc	40(r1)		;0x0028(r1)
    8fd4:	80 00 62 96 	bra	#0x09662	
    8fd8:	7f 90 3a 00 	cmp.b	#58,	r15	;#0x003a
    8fdc:	2b 34       	jge	$+88     	;abs 0x9034
    8fde:	7f 90 31 00 	cmp.b	#49,	r15	;#0x0031
    8fe2:	ba 34       	jge	$+374    	;abs 0x9158
    8fe4:	7f 90 2a 00 	cmp.b	#42,	r15	;#0x002a
    8fe8:	8d 24       	jz	$+284    	;abs 0x9104
    8fea:	7f 90 2b 00 	cmp.b	#43,	r15	;#0x002b
    8fee:	11 34       	jge	$+36     	;abs 0x9012
    8ff0:	7f 90 20 00 	cmp.b	#32,	r15	;#0x0020
    8ff4:	73 24       	jz	$+232    	;abs 0x90dc
    8ff6:	7f 90 21 00 	cmp.b	#33,	r15	;#0x0021
    8ffa:	04 34       	jge	$+10     	;abs 0x9004
    8ffc:	7f 90 8a ff 	cmp.b	#-118,	r15	;#0xff8a
    9000:	43 20       	jnz	$+136    	;abs 0x9088
    9002:	50 3c       	jmp	$+162    	;abs 0x90a4
    9004:	7f 90 23 00 	cmp.b	#35,	r15	;#0x0023
    9008:	48 24       	jz	$+146    	;abs 0x909a
    900a:	7f 90 25 00 	cmp.b	#37,	r15	;#0x0025
    900e:	3c 20       	jnz	$+122    	;abs 0x9088
    9010:	dc 3f       	jmp	$-70     	;abs 0x8fca
    9012:	7f 90 2d 00 	cmp.b	#45,	r15	;#0x002d
    9016:	58 24       	jz	$+178    	;abs 0x90c8
    9018:	7f 90 2e 00 	cmp.b	#46,	r15	;#0x002e
    901c:	04 34       	jge	$+10     	;abs 0x9026
    901e:	7f 90 2b 00 	cmp.b	#43,	r15	;#0x002b
    9022:	32 20       	jnz	$+102    	;abs 0x9088
    9024:	56 3c       	jmp	$+174    	;abs 0x90d2
    9026:	7f 90 2e 00 	cmp.b	#46,	r15	;#0x002e
    902a:	63 24       	jz	$+200    	;abs 0x90f2
    902c:	7f 90 30 00 	cmp.b	#48,	r15	;#0x0030
    9030:	2b 20       	jnz	$+88     	;abs 0x9088
    9032:	7f 3c       	jmp	$+256    	;abs 0x9132
    9034:	7f 90 6c 00 	cmp.b	#108,	r15	;#0x006c
    9038:	39 24       	jz	$+116    	;abs 0x90ac
    903a:	7f 90 6d 00 	cmp.b	#109,	r15	;#0x006d
    903e:	11 34       	jge	$+36     	;abs 0x9062
    9040:	7f 90 63 00 	cmp.b	#99,	r15	;#0x0063
    9044:	92 24       	jz	$+294    	;abs 0x916a
    9046:	7f 90 64 00 	cmp.b	#100,	r15	;#0x0064
    904a:	04 34       	jge	$+10     	;abs 0x9054
    904c:	7f 90 58 00 	cmp.b	#88,	r15	;#0x0058
    9050:	1b 20       	jnz	$+56     	;abs 0x9088
    9052:	d4 3c       	jmp	$+426    	;abs 0x91fc
    9054:	7f 90 64 00 	cmp.b	#100,	r15	;#0x0064
    9058:	d4 24       	jz	$+426    	;abs 0x9202
    905a:	7f 90 69 00 	cmp.b	#105,	r15	;#0x0069
    905e:	14 20       	jnz	$+42     	;abs 0x9088
    9060:	d0 3c       	jmp	$+418    	;abs 0x9202
    9062:	7f 90 73 00 	cmp.b	#115,	r15	;#0x0073
    9066:	90 24       	jz	$+290    	;abs 0x9188
    9068:	7f 90 74 00 	cmp.b	#116,	r15	;#0x0074
    906c:	07 34       	jge	$+16     	;abs 0x907c
    906e:	7f 90 6f 00 	cmp.b	#111,	r15	;#0x006f
    9072:	11 24       	jz	$+36     	;abs 0x9096
    9074:	7f 90 70 00 	cmp.b	#112,	r15	;#0x0070
    9078:	07 20       	jnz	$+16     	;abs 0x9088
    907a:	aa 3c       	jmp	$+342    	;abs 0x91d0
    907c:	7f 90 75 00 	cmp.b	#117,	r15	;#0x0075
    9080:	c2 24       	jz	$+390    	;abs 0x9206
    9082:	7f 90 78 00 	cmp.b	#120,	r15	;#0x0078
    9086:	c2 24       	jz	$+390    	;abs 0x920c
    9088:	19 41 40 00 	mov	64(r1),	r9	;0x0040(r1)
    908c:	1a 41 28 00 	mov	40(r1),	r10	;0x0028(r1)
    9090:	0a 89       	sub	r9,	r10	
    9092:	80 00 50 96 	bra	#0x09650	
    9096:	3a 42       	mov	#8,	r10	;r2 As==11
    9098:	bb 3c       	jmp	$+376    	;abs 0x9210
    909a:	f1 d0 10 00 	bis.b	#16,	24(r1)	;#0x0010, 0x0018(r1)
    909e:	18 00 
    90a0:	80 00 7c 96 	bra	#0x0967c	
    90a4:	d1 d3 18 00 	bis.b	#1,	24(r1)	;r3 As==01, 0x0018(r1)
    90a8:	80 00 7c 96 	bra	#0x0967c	
    90ac:	5e 41 18 00 	mov.b	24(r1),	r14	;0x0018(r1)
    90b0:	6e f3       	and.b	#2,	r14	;r3 As==10
    90b2:	5f 41 18 00 	mov.b	24(r1),	r15	;0x0018(r1)
    90b6:	03 24       	jz	$+8      	;abs 0x90be
    90b8:	6f c3       	bic.b	#2,	r15	;r3 As==10
    90ba:	6f d2       	bis.b	#4,	r15	;r2 As==10
    90bc:	01 3c       	jmp	$+4      	;abs 0x90c0
    90be:	6f d3       	bis.b	#2,	r15	;r3 As==10
    90c0:	c1 4f 18 00 	mov.b	r15,	24(r1)	;0x0018(r1)
    90c4:	80 00 7c 96 	bra	#0x0967c	
    90c8:	f1 d0 20 00 	bis.b	#32,	24(r1)	;#0x0020, 0x0018(r1)
    90cc:	18 00 
    90ce:	80 00 7c 96 	bra	#0x0967c	
    90d2:	f1 40 2b 00 	mov.b	#43,	26(r1)	;#0x002b, 0x001a(r1)
    90d6:	1a 00 
    90d8:	80 00 7c 96 	bra	#0x0967c	
    90dc:	f1 90 2b 00 	cmp.b	#43,	26(r1)	;#0x002b, 0x001a(r1)
    90e0:	1a 00 
    90e2:	02 20       	jnz	$+6      	;abs 0x90e8
    90e4:	80 00 7c 96 	bra	#0x0967c	
    90e8:	f1 40 20 00 	mov.b	#32,	26(r1)	;#0x0020, 0x001a(r1)
    90ec:	1a 00 
    90ee:	80 00 7c 96 	bra	#0x0967c	
    90f2:	c1 93 27 00 	tst.b	39(r1)		;0x0027(r1)
    90f6:	02 24       	jz	$+6      	;abs 0x90fc
    90f8:	80 00 66 96 	bra	#0x09666	
    90fc:	d1 43 2a 00 	mov.b	#1,	42(r1)	;r3 As==01, 0x002a(r1)
    9100:	80 00 7c 96 	bra	#0x0967c	
    9104:	0f 4b       	mov	r11,	r15	
    9106:	2f 53       	incd	r15		
    9108:	2e 4b       	mov	@r11,	r14	
    910a:	0e 93       	tst	r14		
    910c:	02 38       	jl	$+6      	;abs 0x9112
    910e:	04 4e       	mov	r14,	r4	
    9110:	0b 3c       	jmp	$+24     	;abs 0x9128
    9112:	c1 93 2a 00 	tst.b	42(r1)		;0x002a(r1)
    9116:	02 24       	jz	$+6      	;abs 0x911c
    9118:	80 00 74 96 	bra	#0x09674	
    911c:	f1 d0 20 00 	bis.b	#32,	24(r1)	;#0x0020, 0x0018(r1)
    9120:	18 00 
    9122:	04 4e       	mov	r14,	r4	
    9124:	34 e3       	inv	r4		
    9126:	14 53       	inc	r4		
    9128:	0b 4f       	mov	r15,	r11	
    912a:	d1 43 27 00 	mov.b	#1,	39(r1)	;r3 As==01, 0x0027(r1)
    912e:	80 00 7c 96 	bra	#0x0967c	
    9132:	04 93       	tst	r4		
    9134:	11 20       	jnz	$+36     	;abs 0x9158
    9136:	c1 93 2a 00 	tst.b	42(r1)		;0x002a(r1)
    913a:	0e 20       	jnz	$+30     	;abs 0x9158
    913c:	5f 41 18 00 	mov.b	24(r1),	r15	;0x0018(r1)
    9140:	5f 0f       	rrum	#4,	r15	
    9142:	5f 03       	rrum	#1,	r15	
    9144:	59 43       	mov.b	#1,	r9	;r3 As==01
    9146:	49 cf       	bic.b	r15,	r9	
    9148:	5e 41 19 00 	mov.b	25(r1),	r14	;0x0019(r1)
    914c:	5e c3       	bic.b	#1,	r14	;r3 As==01
    914e:	4e d9       	bis.b	r9,	r14	
    9150:	c1 4e 19 00 	mov.b	r14,	25(r1)	;0x0019(r1)
    9154:	80 00 7c 96 	bra	#0x0967c	
    9158:	0e 44       	mov	r4,	r14	
    915a:	5e 02       	rlam	#1,	r14	
    915c:	54 0a       	rlam	#3,	r4	
    915e:	04 5e       	add	r14,	r4	
    9160:	34 50 d0 ff 	add	#-48,	r4	;#0xffd0
    9164:	8f 11       	sxt	r15		
    9166:	04 5f       	add	r15,	r4	
    9168:	e0 3f       	jmp	$-62     	;abs 0x912a
    916a:	0a 4b       	mov	r11,	r10	
    916c:	2a 53       	incd	r10		
    916e:	6f 4b       	mov.b	@r11,	r15	
    9170:	c1 93 2a 00 	tst.b	42(r1)		;0x002a(r1)
    9174:	03 20       	jnz	$+8      	;abs 0x917c
    9176:	c1 93 27 00 	tst.b	39(r1)		;0x0027(r1)
    917a:	26 27       	jz	$-434    	;abs 0x8fc8
    917c:	c1 4f 00 00 	mov.b	r15,	0(r1)	;0x0000(r1)
    9180:	c1 43 01 00 	mov.b	#0,	1(r1)	;r3 As==00, 0x0001(r1)
    9184:	0e 41       	mov	r1,	r14	
    9186:	03 3c       	jmp	$+8      	;abs 0x918e
    9188:	0a 4b       	mov	r11,	r10	
    918a:	2a 53       	incd	r10		
    918c:	2e 4b       	mov	@r11,	r14	
    918e:	c1 93 2a 00 	tst.b	42(r1)		;0x002a(r1)
    9192:	05 24       	jz	$+12     	;abs 0x919e
    9194:	f1 d2 19 00 	bis.b	#8,	25(r1)	;r2 As==11, 0x0019(r1)
    9198:	c1 44 1b 00 	mov.b	r4,	27(r1)	;0x001b(r1)
    919c:	05 3c       	jmp	$+12     	;abs 0x91a8
    919e:	c1 93 27 00 	tst.b	39(r1)		;0x0027(r1)
    91a2:	02 24       	jz	$+6      	;abs 0x91a8
    91a4:	81 44 30 00 	mov	r4,	48(r1)	;0x0030(r1)
    91a8:	0e 93       	tst	r14		
    91aa:	02 20       	jnz	$+6      	;abs 0x91b0
    91ac:	3e 40 7c 9e 	mov	#-24964,r14	;#0x9e7c
    91b0:	11 12 1c 00 	push	28(r1)		;0x001c(r1)
    91b4:	11 12 1c 00 	push	28(r1)		;0x001c(r1)
    91b8:	1d 41 34 00 	mov	52(r1),	r13	;0x0034(r1)
    91bc:	3f 01 40 00 	mova	64(r1),	r15	;0x0040(r1)
    91c0:	b0 13 ea 8d 	calla	#0x08dea	
    91c4:	21 52       	add	#4,	r1	;r2 As==10
    91c6:	81 5f 28 00 	add	r15,	40(r1)	;0x0028(r1)
    91ca:	0b 4a       	mov	r10,	r11	
    91cc:	80 00 62 96 	bra	#0x09662	
    91d0:	0d 4b       	mov	r11,	r13	
    91d2:	2d 53       	incd	r13		
    91d4:	2e 4b       	mov	@r11,	r14	
    91d6:	81 4e 1e 00 	mov	r14,	30(r1)	;0x001e(r1)
    91da:	5f 43       	mov.b	#1,	r15	;r3 As==01
    91dc:	0e 93       	tst	r14		
    91de:	01 20       	jnz	$+4      	;abs 0x91e2
    91e0:	4f 43       	clr.b	r15		
    91e2:	1f f3       	and	#1,	r15	;r3 As==01
    91e4:	5f 0e       	rlam	#4,	r15	
    91e6:	5e 41 18 00 	mov.b	24(r1),	r14	;0x0018(r1)
    91ea:	7e f0 ef ff 	and.b	#-17,	r14	;#0xffef
    91ee:	4e df       	bis.b	r15,	r14	
    91f0:	c1 4e 18 00 	mov.b	r14,	24(r1)	;0x0018(r1)
    91f4:	0b 4d       	mov	r13,	r11	
    91f6:	3a 40 10 00 	mov	#16,	r10	;#0x0010
    91fa:	70 3c       	jmp	$+226    	;abs 0x92dc
    91fc:	e1 d3 19 00 	bis.b	#2,	25(r1)	;r3 As==10, 0x0019(r1)
    9200:	05 3c       	jmp	$+12     	;abs 0x920c
    9202:	f1 d2 18 00 	bis.b	#8,	24(r1)	;r2 As==11, 0x0018(r1)
    9206:	3a 40 0a 00 	mov	#10,	r10	;#0x000a
    920a:	02 3c       	jmp	$+6      	;abs 0x9210
    920c:	3a 40 10 00 	mov	#16,	r10	;#0x0010
    9210:	5f 41 18 00 	mov.b	24(r1),	r15	;0x0018(r1)
    9214:	6f b2       	bit.b	#4,	r15	;r2 As==10
    9216:	24 24       	jz	$+74     	;abs 0x9260
    9218:	0c 4b       	mov	r11,	r12	
    921a:	3c 52       	add	#8,	r12	;r2 As==11
    921c:	2d 4b       	mov	@r11,	r13	
    921e:	1e 4b 02 00 	mov	2(r11),	r14	;0x0002(r11)
    9222:	1f 4b 04 00 	mov	4(r11),	r15	;0x0004(r11)
    9226:	1b 4b 06 00 	mov	6(r11),	r11	;0x0006(r11)
    922a:	81 4d 1e 00 	mov	r13,	30(r1)	;0x001e(r1)
    922e:	81 4e 20 00 	mov	r14,	32(r1)	;0x0020(r1)
    9232:	81 4f 22 00 	mov	r15,	34(r1)	;0x0022(r1)
    9236:	81 4b 24 00 	mov	r11,	36(r1)	;0x0024(r1)
    923a:	d1 43 26 00 	mov.b	#1,	38(r1)	;r3 As==01, 0x0026(r1)
    923e:	0d 93       	tst	r13		
    9240:	06 20       	jnz	$+14     	;abs 0x924e
    9242:	0e 93       	tst	r14		
    9244:	04 20       	jnz	$+10     	;abs 0x924e
    9246:	0f 93       	tst	r15		
    9248:	02 20       	jnz	$+6      	;abs 0x924e
    924a:	0b 93       	tst	r11		
    924c:	02 24       	jz	$+6      	;abs 0x9252
    924e:	c1 43 26 00 	mov.b	#0,	38(r1)	;r3 As==00, 0x0026(r1)
    9252:	0b 5b       	rla	r11		
    9254:	0b 43       	clr	r11		
    9256:	0b 6b       	rlc	r11		
    9258:	c1 4b 2b 00 	mov.b	r11,	43(r1)	;0x002b(r1)
    925c:	0b 4c       	mov	r12,	r11	
    925e:	3e 3c       	jmp	$+126    	;abs 0x92dc
    9260:	6f b3       	bit.b	#2,	r15	;r3 As==10
    9262:	18 24       	jz	$+50     	;abs 0x9294
    9264:	0d 4b       	mov	r11,	r13	
    9266:	2d 52       	add	#4,	r13	;r2 As==10
    9268:	2e 4b       	mov	@r11,	r14	
    926a:	1f 4b 02 00 	mov	2(r11),	r15	;0x0002(r11)
    926e:	81 4e 1e 00 	mov	r14,	30(r1)	;0x001e(r1)
    9272:	81 4f 20 00 	mov	r15,	32(r1)	;0x0020(r1)
    9276:	d1 43 26 00 	mov.b	#1,	38(r1)	;r3 As==01, 0x0026(r1)
    927a:	0e 93       	tst	r14		
    927c:	02 20       	jnz	$+6      	;abs 0x9282
    927e:	0f 93       	tst	r15		
    9280:	02 24       	jz	$+6      	;abs 0x9286
    9282:	c1 43 26 00 	mov.b	#0,	38(r1)	;r3 As==00, 0x0026(r1)
    9286:	0f 5f       	rla	r15		
    9288:	0f 43       	clr	r15		
    928a:	0f 6f       	rlc	r15		
    928c:	c1 4f 2b 00 	mov.b	r15,	43(r1)	;0x002b(r1)
    9290:	0b 4d       	mov	r13,	r11	
    9292:	24 3c       	jmp	$+74     	;abs 0x92dc
    9294:	5f f3       	and.b	#1,	r15	;r3 As==01
    9296:	0e 4b       	mov	r11,	r14	
    9298:	11 24       	jz	$+36     	;abs 0x92bc
    929a:	2e 52       	add	#4,	r14	;r2 As==10
    929c:	0f 0b       	mova	@r11,	r15	
    929e:	71 0f 1e 00 	mova	r15,	30(r1)	;0x001e(r1)
    92a2:	d1 43 26 00 	mov.b	#1,	38(r1)	;r3 As==01, 0x0026(r1)
    92a6:	df 03       	tsta	r15		
    92a8:	02 24       	jz	$+6      	;abs 0x92ae
    92aa:	c1 43 26 00 	mov.b	#0,	38(r1)	;r3 As==00, 0x0026(r1)
    92ae:	d1 43 2b 00 	mov.b	#1,	43(r1)	;r3 As==01, 0x002b(r1)
    92b2:	df 03       	tsta	r15		
    92b4:	12 38       	jl	$+38     	;abs 0x92da
    92b6:	c1 43 2b 00 	mov.b	#0,	43(r1)	;r3 As==00, 0x002b(r1)
    92ba:	0f 3c       	jmp	$+32     	;abs 0x92da
    92bc:	2e 53       	incd	r14		
    92be:	2f 4b       	mov	@r11,	r15	
    92c0:	81 4f 1e 00 	mov	r15,	30(r1)	;0x001e(r1)
    92c4:	d1 43 26 00 	mov.b	#1,	38(r1)	;r3 As==01, 0x0026(r1)
    92c8:	0f 93       	tst	r15		
    92ca:	02 24       	jz	$+6      	;abs 0x92d0
    92cc:	c1 43 26 00 	mov.b	#0,	38(r1)	;r3 As==00, 0x0026(r1)
    92d0:	0f 5f       	rla	r15		
    92d2:	0f 43       	clr	r15		
    92d4:	0f 6f       	rlc	r15		
    92d6:	c1 4f 2b 00 	mov.b	r15,	43(r1)	;0x002b(r1)
    92da:	0b 4e       	mov	r14,	r11	
    92dc:	f1 b0 10 00 	bit.b	#16,	24(r1)	;#0x0010, 0x0018(r1)
    92e0:	18 00 
    92e2:	11 24       	jz	$+36     	;abs 0x9306
    92e4:	c1 93 26 00 	tst.b	38(r1)		;0x0026(r1)
    92e8:	0e 20       	jnz	$+30     	;abs 0x9306
    92ea:	5f 41 18 00 	mov.b	24(r1),	r15	;0x0018(r1)
    92ee:	3a 90 10 00 	cmp	#16,	r10	;#0x0010
    92f2:	03 20       	jnz	$+8      	;abs 0x92fa
    92f4:	7f d0 80 ff 	bis.b	#-128,	r15	;#0xff80
    92f8:	04 3c       	jmp	$+10     	;abs 0x9302
    92fa:	3a 92       	cmp	#8,	r10	;r2 As==11
    92fc:	04 20       	jnz	$+10     	;abs 0x9306
    92fe:	7f d0 40 00 	bis.b	#64,	r15	;#0x0040
    9302:	c1 4f 18 00 	mov.b	r15,	24(r1)	;0x0018(r1)
    9306:	5d 41 18 00 	mov.b	24(r1),	r13	;0x0018(r1)
    930a:	7d b2       	bit.b	#8,	r13	;r2 As==11
    930c:	45 24       	jz	$+140    	;abs 0x9398
    930e:	c1 93 2b 00 	tst.b	43(r1)		;0x002b(r1)
    9312:	42 24       	jz	$+134    	;abs 0x9398
    9314:	f1 40 2d 00 	mov.b	#45,	26(r1)	;#0x002d, 0x001a(r1)
    9318:	1a 00 
    931a:	6d b2       	bit.b	#4,	r13	;r2 As==10
    931c:	11 24       	jz	$+36     	;abs 0x9340
    931e:	b1 e3 1e 00 	xor	#-1,	30(r1)	;r3 As==11, 0x001e(r1)
    9322:	b1 e3 20 00 	xor	#-1,	32(r1)	;r3 As==11, 0x0020(r1)
    9326:	b1 e3 22 00 	xor	#-1,	34(r1)	;r3 As==11, 0x0022(r1)
    932a:	b1 e3 24 00 	xor	#-1,	36(r1)	;r3 As==11, 0x0024(r1)
    932e:	91 53 1e 00 	inc	30(r1)		;0x001e(r1)
    9332:	81 63 20 00 	adc	32(r1)		;0x0020(r1)
    9336:	81 63 22 00 	adc	34(r1)		;0x0022(r1)
    933a:	81 63 24 00 	adc	36(r1)		;0x0024(r1)
    933e:	2c 3c       	jmp	$+90     	;abs 0x9398
    9340:	6d b3       	bit.b	#2,	r13	;r3 As==10
    9342:	0f 24       	jz	$+32     	;abs 0x9362
    9344:	1e 41 1e 00 	mov	30(r1),	r14	;0x001e(r1)
    9348:	1f 41 20 00 	mov	32(r1),	r15	;0x0020(r1)
    934c:	3e e3       	inv	r14		
    934e:	3f e3       	inv	r15		
    9350:	08 4e       	mov	r14,	r8	
    9352:	09 4f       	mov	r15,	r9	
    9354:	18 53       	inc	r8		
    9356:	09 63       	adc	r9		
    9358:	81 48 1e 00 	mov	r8,	30(r1)	;0x001e(r1)
    935c:	81 49 20 00 	mov	r9,	32(r1)	;0x0020(r1)
    9360:	1b 3c       	jmp	$+56     	;abs 0x9398
    9362:	5d b3       	bit.b	#1,	r13	;r3 As==01
    9364:	13 24       	jz	$+40     	;abs 0x938c
    9366:	18 41 1e 00 	mov	30(r1),	r8	;0x001e(r1)
    936a:	19 41 20 00 	mov	32(r1),	r9	;0x0020(r1)
    936e:	0f 49       	mov	r9,	r15	
    9370:	3f f0 0f 00 	and	#15,	r15	;#0x000f
    9374:	12 c3       	clrc			
    9376:	04 18 4f 10 	.rpt	#5
				rrcx.a	r15		
    937a:	00 18 4f d8 	bisx.a	r8,	r15	
    937e:	00 18 7f e3 	invx.a	r15		
    9382:	af 00 01 00 	adda	#0x00001,r15	
    9386:	71 0f 1e 00 	mova	r15,	30(r1)	;0x001e(r1)
    938a:	06 3c       	jmp	$+14     	;abs 0x9398
    938c:	1f 41 1e 00 	mov	30(r1),	r15	;0x001e(r1)
    9390:	3f e3       	inv	r15		
    9392:	1f 53       	inc	r15		
    9394:	81 4f 1e 00 	mov	r15,	30(r1)	;0x001e(r1)
    9398:	c1 43 17 00 	mov.b	#0,	23(r1)	;r3 As==00, 0x0017(r1)
    939c:	6d b2       	bit.b	#4,	r13	;r2 As==10
    939e:	68 24       	jz	$+210    	;abs 0x9470
    93a0:	16 41 1e 00 	mov	30(r1),	r6	;0x001e(r1)
    93a4:	15 41 20 00 	mov	32(r1),	r5	;0x0020(r1)
    93a8:	91 41 22 00 	mov	34(r1),	44(r1)	;0x0022(r1), 0x002c(r1)
    93ac:	2c 00 
    93ae:	17 41 24 00 	mov	36(r1),	r7	;0x0024(r1)
    93b2:	08 41       	mov	r1,	r8	
    93b4:	38 50 15 00 	add	#21,	r8	;#0x0015
    93b8:	81 4a 32 00 	mov	r10,	50(r1)	;0x0032(r1)
    93bc:	0f 4a       	mov	r10,	r15	
    93be:	8f 10       	swpb	r15		
    93c0:	8f 11       	sxt	r15		
    93c2:	8f 10       	swpb	r15		
    93c4:	8f 11       	sxt	r15		
    93c6:	81 4f 34 00 	mov	r15,	52(r1)	;0x0034(r1)
    93ca:	81 4f 36 00 	mov	r15,	54(r1)	;0x0036(r1)
    93ce:	81 4f 38 00 	mov	r15,	56(r1)	;0x0038(r1)
    93d2:	1c 41 32 00 	mov	50(r1),	r12	;0x0032(r1)
    93d6:	1d 41 34 00 	mov	52(r1),	r13	;0x0034(r1)
    93da:	1e 41 36 00 	mov	54(r1),	r14	;0x0036(r1)
    93de:	1f 41 38 00 	mov	56(r1),	r15	;0x0038(r1)
    93e2:	3f 15       	pushm	#4,	r15	
    93e4:	0c 46       	mov	r6,	r12	
    93e6:	0d 45       	mov	r5,	r13	
    93e8:	1e 41 34 00 	mov	52(r1),	r14	;0x0034(r1)
    93ec:	0f 47       	mov	r7,	r15	
    93ee:	b0 13 fa 33 	calla	#0x033fa	
    93f2:	31 52       	add	#8,	r1	;r2 As==11
    93f4:	3c 90 0a 00 	cmp	#10,	r12	;#0x000a
    93f8:	06 34       	jge	$+14     	;abs 0x9406
    93fa:	09 48       	mov	r8,	r9	
    93fc:	7c 50 30 00 	add.b	#48,	r12	;#0x0030
    9400:	c8 4c 01 00 	mov.b	r12,	1(r8)	;0x0001(r8)
    9404:	0d 3c       	jmp	$+28     	;abs 0x9420
    9406:	4c 4c       	mov.b	r12,	r12	
    9408:	e1 b3 19 00 	bit.b	#2,	25(r1)	;r3 As==10, 0x0019(r1)
    940c:	03 24       	jz	$+8      	;abs 0x9414
    940e:	7f 40 37 00 	mov.b	#55,	r15	;#0x0037
    9412:	02 3c       	jmp	$+6      	;abs 0x9418
    9414:	7f 40 57 00 	mov.b	#87,	r15	;#0x0057
    9418:	09 48       	mov	r8,	r9	
    941a:	4f 5c       	add.b	r12,	r15	
    941c:	c8 4f 01 00 	mov.b	r15,	1(r8)	;0x0001(r8)
    9420:	1c 41 32 00 	mov	50(r1),	r12	;0x0032(r1)
    9424:	1d 41 34 00 	mov	52(r1),	r13	;0x0034(r1)
    9428:	1e 41 36 00 	mov	54(r1),	r14	;0x0036(r1)
    942c:	1f 41 38 00 	mov	56(r1),	r15	;0x0038(r1)
    9430:	3f 15       	pushm	#4,	r15	
    9432:	0c 46       	mov	r6,	r12	
    9434:	0d 45       	mov	r5,	r13	
    9436:	1e 41 34 00 	mov	52(r1),	r14	;0x0034(r1)
    943a:	0f 47       	mov	r7,	r15	
    943c:	b0 13 e0 33 	calla	#0x033e0	
    9440:	31 52       	add	#8,	r1	;r2 As==11
    9442:	06 4c       	mov	r12,	r6	
    9444:	05 4d       	mov	r13,	r5	
    9446:	81 4e 2c 00 	mov	r14,	44(r1)	;0x002c(r1)
    944a:	07 4f       	mov	r15,	r7	
    944c:	38 53       	add	#-1,	r8	;r3 As==11
    944e:	0c 93       	tst	r12		
    9450:	b3 23       	jnz	$-152    	;abs 0x93b8
    9452:	0d 93       	tst	r13		
    9454:	b1 23       	jnz	$-156    	;abs 0x93b8
    9456:	0e 93       	tst	r14		
    9458:	af 23       	jnz	$-160    	;abs 0x93b8
    945a:	0f 93       	tst	r15		
    945c:	ad 23       	jnz	$-164    	;abs 0x93b8
    945e:	81 43 1e 00 	mov	#0,	30(r1)	;r3 As==00, 0x001e(r1)
    9462:	81 43 20 00 	mov	#0,	32(r1)	;r3 As==00, 0x0020(r1)
    9466:	81 43 22 00 	mov	#0,	34(r1)	;r3 As==00, 0x0022(r1)
    946a:	81 43 24 00 	mov	#0,	36(r1)	;r3 As==00, 0x0024(r1)
    946e:	c2 3c       	jmp	$+390    	;abs 0x95f4
    9470:	6d b3       	bit.b	#2,	r13	;r3 As==10
    9472:	3a 24       	jz	$+118    	;abs 0x94e8
    9474:	15 41 1e 00 	mov	30(r1),	r5	;0x001e(r1)
    9478:	16 41 20 00 	mov	32(r1),	r6	;0x0020(r1)
    947c:	07 41       	mov	r1,	r7	
    947e:	37 50 15 00 	add	#21,	r7	;#0x0015
    9482:	08 4a       	mov	r10,	r8	
    9484:	88 10       	swpb	r8		
    9486:	88 11       	sxt	r8		
    9488:	88 10       	swpb	r8		
    948a:	88 11       	sxt	r8		
    948c:	0c 4a       	mov	r10,	r12	
    948e:	0d 48       	mov	r8,	r13	
    9490:	0e 45       	mov	r5,	r14	
    9492:	0f 46       	mov	r6,	r15	
    9494:	b0 13 84 33 	calla	#0x03384	
    9498:	3e 90 0a 00 	cmp	#10,	r14	;#0x000a
    949c:	06 34       	jge	$+14     	;abs 0x94aa
    949e:	09 47       	mov	r7,	r9	
    94a0:	7e 50 30 00 	add.b	#48,	r14	;#0x0030
    94a4:	c7 4e 01 00 	mov.b	r14,	1(r7)	;0x0001(r7)
    94a8:	0d 3c       	jmp	$+28     	;abs 0x94c4
    94aa:	4e 4e       	mov.b	r14,	r14	
    94ac:	e1 b3 19 00 	bit.b	#2,	25(r1)	;r3 As==10, 0x0019(r1)
    94b0:	03 24       	jz	$+8      	;abs 0x94b8
    94b2:	7f 40 37 00 	mov.b	#55,	r15	;#0x0037
    94b6:	02 3c       	jmp	$+6      	;abs 0x94bc
    94b8:	7f 40 57 00 	mov.b	#87,	r15	;#0x0057
    94bc:	09 47       	mov	r7,	r9	
    94be:	4f 5e       	add.b	r14,	r15	
    94c0:	c7 4f 01 00 	mov.b	r15,	1(r7)	;0x0001(r7)
    94c4:	0c 4a       	mov	r10,	r12	
    94c6:	0d 48       	mov	r8,	r13	
    94c8:	0e 45       	mov	r5,	r14	
    94ca:	0f 46       	mov	r6,	r15	
    94cc:	b0 13 56 33 	calla	#0x03356	
    94d0:	05 4e       	mov	r14,	r5	
    94d2:	06 4f       	mov	r15,	r6	
    94d4:	37 53       	add	#-1,	r7	;r3 As==11
    94d6:	0e 93       	tst	r14		
    94d8:	d4 23       	jnz	$-86     	;abs 0x9482
    94da:	0f 93       	tst	r15		
    94dc:	d2 23       	jnz	$-90     	;abs 0x9482
    94de:	81 43 1e 00 	mov	#0,	30(r1)	;r3 As==00, 0x001e(r1)
    94e2:	81 43 20 00 	mov	#0,	32(r1)	;r3 As==00, 0x0020(r1)
    94e6:	86 3c       	jmp	$+270    	;abs 0x95f4
    94e8:	5d f3       	and.b	#1,	r13	;r3 As==01
    94ea:	5b 24       	jz	$+184    	;abs 0x95a2
    94ec:	1d 41 1e 00 	mov	30(r1),	r13	;0x001e(r1)
    94f0:	1e 41 20 00 	mov	32(r1),	r14	;0x0020(r1)
    94f4:	06 4e       	mov	r14,	r6	
    94f6:	36 f0 0f 00 	and	#15,	r6	;#0x000f
    94fa:	12 c3       	clrc			
    94fc:	04 18 46 10 	.rpt	#5
				rrcx.a	r6		
    9500:	00 18 46 dd 	bisx.a	r13,	r6	
    9504:	07 41       	mov	r1,	r7	
    9506:	37 50 15 00 	add	#21,	r7	;#0x0015
    950a:	08 4a       	mov	r10,	r8	
    950c:	0a 93       	tst	r10		
    950e:	03 34       	jge	$+8      	;abs 0x9516
    9510:	80 1f 78 d0 	bisx.a	#-65536,r8	;#0xf0000
    9514:	00 00 
    9516:	c5 06       	mova	r6,	r5	
    9518:	04 18 45 65 	.rpt	#5
				addcx.a	r5,	r5	
    951c:	cd 08       	mova	r8,	r13	
    951e:	04 18 4d 6d 	.rpt	#5
				addcx.a	r13,	r13	
    9522:	0c 48       	mov	r8,	r12	
    9524:	3d f0 0f 00 	and	#15,	r13	;#0x000f
    9528:	0e 46       	mov	r6,	r14	
    952a:	c9 05       	mova	r5,	r9	
    952c:	39 f0 0f 00 	and	#15,	r9	;#0x000f
    9530:	0f 49       	mov	r9,	r15	
    9532:	b0 13 84 33 	calla	#0x03384	
    9536:	81 4e 2c 00 	mov	r14,	44(r1)	;0x002c(r1)
    953a:	81 4f 2e 00 	mov	r15,	46(r1)	;0x002e(r1)
    953e:	3f 01 2c 00 	mova	44(r1),	r15	;0x002c(r1)
    9542:	3f 90 0a 00 	cmp	#10,	r15	;#0x000a
    9546:	06 34       	jge	$+14     	;abs 0x9554
    9548:	09 47       	mov	r7,	r9	
    954a:	7f 50 30 00 	add.b	#48,	r15	;#0x0030
    954e:	c7 4f 01 00 	mov.b	r15,	1(r7)	;0x0001(r7)
    9552:	0d 3c       	jmp	$+28     	;abs 0x956e
    9554:	4f 4f       	mov.b	r15,	r15	
    9556:	e1 b3 19 00 	bit.b	#2,	25(r1)	;r3 As==10, 0x0019(r1)
    955a:	03 24       	jz	$+8      	;abs 0x9562
    955c:	7e 40 37 00 	mov.b	#55,	r14	;#0x0037
    9560:	02 3c       	jmp	$+6      	;abs 0x9566
    9562:	7e 40 57 00 	mov.b	#87,	r14	;#0x0057
    9566:	09 47       	mov	r7,	r9	
    9568:	4e 5f       	add.b	r15,	r14	
    956a:	c7 4e 01 00 	mov.b	r14,	1(r7)	;0x0001(r7)
    956e:	cd 08       	mova	r8,	r13	
    9570:	04 18 4d 6d 	.rpt	#5
				addcx.a	r13,	r13	
    9574:	0c 48       	mov	r8,	r12	
    9576:	3d f0 0f 00 	and	#15,	r13	;#0x000f
    957a:	0e 46       	mov	r6,	r14	
    957c:	c8 05       	mova	r5,	r8	
    957e:	38 f0 0f 00 	and	#15,	r8	;#0x000f
    9582:	0f 48       	mov	r8,	r15	
    9584:	b0 13 56 33 	calla	#0x03356	
    9588:	81 4e 2c 00 	mov	r14,	44(r1)	;0x002c(r1)
    958c:	81 4f 2e 00 	mov	r15,	46(r1)	;0x002e(r1)
    9590:	36 01 2c 00 	mova	44(r1),	r6	;0x002c(r1)
    9594:	37 53       	add	#-1,	r7	;r3 As==11
    9596:	d6 03       	tsta	r6		
    9598:	b8 23       	jnz	$-142    	;abs 0x950a
    959a:	cc 03       	clra	r12		
    959c:	71 0c 1e 00 	mova	r12,	30(r1)	;0x001e(r1)
    95a0:	29 3c       	jmp	$+84     	;abs 0x95f4
    95a2:	17 41 1e 00 	mov	30(r1),	r7	;0x001e(r1)
    95a6:	08 41       	mov	r1,	r8	
    95a8:	38 50 15 00 	add	#21,	r8	;#0x0015
    95ac:	0e 4a       	mov	r10,	r14	
    95ae:	0f 47       	mov	r7,	r15	
    95b0:	b0 13 4e 33 	calla	#0x0334e	
    95b4:	3f 90 0a 00 	cmp	#10,	r15	;#0x000a
    95b8:	06 34       	jge	$+14     	;abs 0x95c6
    95ba:	09 48       	mov	r8,	r9	
    95bc:	7f 50 30 00 	add.b	#48,	r15	;#0x0030
    95c0:	c8 4f 01 00 	mov.b	r15,	1(r8)	;0x0001(r8)
    95c4:	0d 3c       	jmp	$+28     	;abs 0x95e0
    95c6:	4f 4f       	mov.b	r15,	r15	
    95c8:	e1 b3 19 00 	bit.b	#2,	25(r1)	;r3 As==10, 0x0019(r1)
    95cc:	03 24       	jz	$+8      	;abs 0x95d4
    95ce:	7e 40 37 00 	mov.b	#55,	r14	;#0x0037
    95d2:	02 3c       	jmp	$+6      	;abs 0x95d8
    95d4:	7e 40 57 00 	mov.b	#87,	r14	;#0x0057
    95d8:	09 48       	mov	r8,	r9	
    95da:	4e 5f       	add.b	r15,	r14	
    95dc:	c8 4e 01 00 	mov.b	r14,	1(r8)	;0x0001(r8)
    95e0:	0e 4a       	mov	r10,	r14	
    95e2:	0f 47       	mov	r7,	r15	
    95e4:	b0 13 34 33 	calla	#0x03334	
    95e8:	07 4f       	mov	r15,	r7	
    95ea:	38 53       	add	#-1,	r8	;r3 As==11
    95ec:	0f 93       	tst	r15		
    95ee:	de 23       	jnz	$-66     	;abs 0x95ac
    95f0:	81 43 1e 00 	mov	#0,	30(r1)	;r3 As==00, 0x001e(r1)
    95f4:	3a 90 0a 00 	cmp	#10,	r10	;#0x000a
    95f8:	02 24       	jz	$+6      	;abs 0x95fe
    95fa:	c1 43 1a 00 	mov.b	#0,	26(r1)	;r3 As==00, 0x001a(r1)
    95fe:	c1 93 2a 00 	tst.b	42(r1)		;0x002a(r1)
    9602:	0d 24       	jz	$+28     	;abs 0x961e
    9604:	1f 41 1c 00 	mov	28(r1),	r15	;0x001c(r1)
    9608:	0f 89       	sub	r9,	r15	
    960a:	2f 83       	decd	r15		
    960c:	0f 94       	cmp	r4,	r15	
    960e:	0c 2c       	jc	$+26     	;abs 0x9628
    9610:	e1 d2 19 00 	bis.b	#4,	25(r1)	;r2 As==10, 0x0019(r1)
    9614:	4d 44       	mov.b	r4,	r13	
    9616:	4d 8f       	sub.b	r15,	r13	
    9618:	c1 4d 1b 00 	mov.b	r13,	27(r1)	;0x001b(r1)
    961c:	05 3c       	jmp	$+12     	;abs 0x9628
    961e:	c1 93 27 00 	tst.b	39(r1)		;0x0027(r1)
    9622:	02 24       	jz	$+6      	;abs 0x9628
    9624:	81 44 30 00 	mov	r4,	48(r1)	;0x0030(r1)
    9628:	11 12 1c 00 	push	28(r1)		;0x001c(r1)
    962c:	11 12 1c 00 	push	28(r1)		;0x001c(r1)
    9630:	1d 41 34 00 	mov	52(r1),	r13	;0x0034(r1)
    9634:	0e 49       	mov	r9,	r14	
    9636:	1e 53       	inc	r14		
    9638:	3f 01 40 00 	mova	64(r1),	r15	;0x0040(r1)
    963c:	b0 13 ea 8d 	calla	#0x08dea	
    9640:	21 52       	add	#4,	r1	;r2 As==10
    9642:	81 5f 28 00 	add	r15,	40(r1)	;0x0028(r1)
    9646:	0d 3c       	jmp	$+28     	;abs 0x9662
    9648:	7f 49       	mov.b	@r9+,	r15	
    964a:	8f 11       	sxt	r15		
    964c:	51 13 3e 00 	calla	62(r1)		;0x003e(r1)
    9650:	0f 49       	mov	r9,	r15	
    9652:	0f 5a       	add	r10,	r15	
    9654:	19 91 3a 00 	cmp	58(r1),	r9	;0x003a(r1)
    9658:	f7 2b       	jnc	$-16     	;abs 0x9648
    965a:	81 49 40 00 	mov	r9,	64(r1)	;0x0040(r1)
    965e:	81 4f 28 00 	mov	r15,	40(r1)	;0x0028(r1)
    9662:	0d 43       	clr	r13		
    9664:	0c 3c       	jmp	$+26     	;abs 0x967e
    9666:	81 44 30 00 	mov	r4,	48(r1)	;0x0030(r1)
    966a:	d1 43 2a 00 	mov.b	#1,	42(r1)	;r3 As==01, 0x002a(r1)
    966e:	c1 43 27 00 	mov.b	#0,	39(r1)	;r3 As==00, 0x0027(r1)
    9672:	03 3c       	jmp	$+8      	;abs 0x967a
    9674:	0b 4f       	mov	r15,	r11	
    9676:	d1 43 27 00 	mov.b	#1,	39(r1)	;r3 As==01, 0x0027(r1)
    967a:	04 43       	clr	r4		
    967c:	1d 43       	mov	#1,	r13	;r3 As==01
    967e:	1e 41 3a 00 	mov	58(r1),	r14	;0x003a(r1)
    9682:	81 4e 3a 00 	mov	r14,	58(r1)	;0x003a(r1)
    9686:	08 4e       	mov	r14,	r8	
    9688:	91 53 3a 00 	inc	58(r1)		;0x003a(r1)
    968c:	7f 48       	mov.b	@r8+,	r15	
    968e:	4f 93       	tst.b	r15		
    9690:	02 24       	jz	$+6      	;abs 0x9696
    9692:	80 00 9a 8f 	bra	#0x08f9a	
    9696:	1f 41 28 00 	mov	40(r1),	r15	;0x0028(r1)
    969a:	31 50 42 00 	add	#66,	r1	;#0x0042
    969e:	74 16       	popm.a	#8,	r11	
    96a0:	10 01       	reta			

000096a2 <puts>:
    96a2:	0b 14       	pushm.a	#1,	r11	
    96a4:	0b 4f       	mov	r15,	r11	
    96a6:	6f 4b       	mov.b	@r11,	r15	
    96a8:	4f 93       	tst.b	r15		
    96aa:	06 24       	jz	$+14     	;abs 0x96b8
    96ac:	1b 53       	inc	r11		
    96ae:	8f 11       	sxt	r15		
    96b0:	b0 13 ce 6c 	calla	#0x06cce	
    96b4:	0f 93       	tst	r15		
    96b6:	f7 37       	jge	$-16     	;abs 0x96a6
    96b8:	cb 93 00 00 	tst.b	0(r11)		;0x0000(r11)
    96bc:	05 20       	jnz	$+12     	;abs 0x96c8
    96be:	3f 40 0a 00 	mov	#10,	r15	;#0x000a
    96c2:	b0 13 ce 6c 	calla	#0x06cce	
    96c6:	01 3c       	jmp	$+4      	;abs 0x96ca
    96c8:	3f 43       	mov	#-1,	r15	;r3 As==11
    96ca:	0b 16       	popm.a	#1,	r11	
    96cc:	10 01       	reta			

000096ce <rand>:
    96ce:	3c 40 6d 4e 	mov	#20077,	r12	;#0x4e6d
    96d2:	3d 40 c6 41 	mov	#16838,	r13	;#0x41c6
    96d6:	1e 42 38 1a 	mov	&0x1a38,r14	
    96da:	1f 42 3a 1a 	mov	&0x1a3a,r15	
    96de:	b0 13 0e 33 	calla	#0x0330e	
    96e2:	3e 50 39 30 	add	#12345,	r14	;#0x3039
    96e6:	0f 63       	adc	r15		
    96e8:	82 4e 38 1a 	mov	r14,	&0x1a38	
    96ec:	82 4f 3a 1a 	mov	r15,	&0x1a3a	
    96f0:	0f 4e       	mov	r14,	r15	
    96f2:	10 01       	reta			

000096f4 <srand>:
    96f4:	82 4f 38 1a 	mov	r15,	&0x1a38	
    96f8:	82 43 3a 1a 	mov	#0,	&0x1a3a	;r3 As==00
    96fc:	10 01       	reta			

000096fe <memcmp>:
    96fe:	1b 14       	pushm.a	#2,	r11	
    9700:	0d 93       	tst	r13		
    9702:	10 24       	jz	$+34     	;abs 0x9724
    9704:	0c 43       	clr	r12		
    9706:	0b 4f       	mov	r15,	r11	
    9708:	0b 5c       	add	r12,	r11	
    970a:	6a 4b       	mov.b	@r11,	r10	
    970c:	0b 4e       	mov	r14,	r11	
    970e:	0b 5c       	add	r12,	r11	
    9710:	6b 4b       	mov.b	@r11,	r11	
    9712:	4a 9b       	cmp.b	r11,	r10	
    9714:	04 24       	jz	$+10     	;abs 0x971e
    9716:	4f 4a       	mov.b	r10,	r15	
    9718:	4b 4b       	mov.b	r11,	r11	
    971a:	0f 8b       	sub	r11,	r15	
    971c:	04 3c       	jmp	$+10     	;abs 0x9726
    971e:	1c 53       	inc	r12		
    9720:	0d 9c       	cmp	r12,	r13	
    9722:	f1 23       	jnz	$-28     	;abs 0x9706
    9724:	0f 43       	clr	r15		
    9726:	1a 16       	popm.a	#2,	r11	
    9728:	10 01       	reta			

0000972a <memcpy>:
    972a:	3b 14       	pushm.a	#4,	r11	
    972c:	0d 93       	tst	r13		
    972e:	6f 24       	jz	$+224    	;abs 0x980e
    9730:	0f 9e       	cmp	r14,	r15	
    9732:	6d 24       	jz	$+220    	;abs 0x980e
    9734:	35 2c       	jc	$+108    	;abs 0x97a0
    9736:	0c 4e       	mov	r14,	r12	
    9738:	0c df       	bis	r15,	r12	
    973a:	1c f3       	and	#1,	r12	;r3 As==01
    973c:	1d 24       	jz	$+60     	;abs 0x9778
    973e:	0c 4e       	mov	r14,	r12	
    9740:	0c ef       	xor	r15,	r12	
    9742:	1c f3       	and	#1,	r12	;r3 As==01
    9744:	07 20       	jnz	$+16     	;abs 0x9754
    9746:	2d 93       	cmp	#2,	r13	;r3 As==10
    9748:	07 28       	jnc	$+16     	;abs 0x9758
    974a:	0c 4e       	mov	r14,	r12	
    974c:	1c f3       	and	#1,	r12	;r3 As==01
    974e:	2b 43       	mov	#2,	r11	;r3 As==10
    9750:	0b 8c       	sub	r12,	r11	
    9752:	03 3c       	jmp	$+8      	;abs 0x975a
    9754:	0b 4d       	mov	r13,	r11	
    9756:	01 3c       	jmp	$+4      	;abs 0x975a
    9758:	1b 43       	mov	#1,	r11	;r3 As==01
    975a:	0d 8b       	sub	r11,	r13	
    975c:	0c 43       	clr	r12		
    975e:	09 4e       	mov	r14,	r9	
    9760:	09 5c       	add	r12,	r9	
    9762:	0a 4f       	mov	r15,	r10	
    9764:	0a 5c       	add	r12,	r10	
    9766:	ea 49 00 00 	mov.b	@r9,	0(r10)	;0x0000(r10)
    976a:	1c 53       	inc	r12		
    976c:	0c 9b       	cmp	r11,	r12	
    976e:	f7 23       	jnz	$-16     	;abs 0x975e
    9770:	0b 4f       	mov	r15,	r11	
    9772:	0b 5c       	add	r12,	r11	
    9774:	0e 5c       	add	r12,	r14	
    9776:	01 3c       	jmp	$+4      	;abs 0x977a
    9778:	0b 4f       	mov	r15,	r11	
    977a:	0c 4d       	mov	r13,	r12	
    977c:	5c 03       	rrum	#1,	r12	
    977e:	0b 24       	jz	$+24     	;abs 0x9796
    9780:	0a 4c       	mov	r12,	r10	
    9782:	08 4e       	mov	r14,	r8	
    9784:	09 4b       	mov	r11,	r9	
    9786:	b9 48 00 00 	mov	@r8+,	0(r9)	;0x0000(r9)
    978a:	29 53       	incd	r9		
    978c:	3a 53       	add	#-1,	r10	;r3 As==11
    978e:	fb 23       	jnz	$-8      	;abs 0x9786
    9790:	5c 02       	rlam	#1,	r12	
    9792:	0e 5c       	add	r12,	r14	
    9794:	0b 5c       	add	r12,	r11	
    9796:	1d f3       	and	#1,	r13	;r3 As==01
    9798:	3a 24       	jz	$+118    	;abs 0x980e
    979a:	eb 4e 00 00 	mov.b	@r14,	0(r11)	;0x0000(r11)
    979e:	37 3c       	jmp	$+112    	;abs 0x980e
    97a0:	0e 5d       	add	r13,	r14	
    97a2:	0c 4f       	mov	r15,	r12	
    97a4:	0c 5d       	add	r13,	r12	
    97a6:	0b 4c       	mov	r12,	r11	
    97a8:	0b de       	bis	r14,	r11	
    97aa:	1b f3       	and	#1,	r11	;r3 As==01
    97ac:	1b 24       	jz	$+56     	;abs 0x97e4
    97ae:	0b 4c       	mov	r12,	r11	
    97b0:	0b ee       	xor	r14,	r11	
    97b2:	1b f3       	and	#1,	r11	;r3 As==01
    97b4:	06 20       	jnz	$+14     	;abs 0x97c2
    97b6:	3d 90 03 00 	cmp	#3,	r13	;#0x0003
    97ba:	03 28       	jnc	$+8      	;abs 0x97c2
    97bc:	0a 4e       	mov	r14,	r10	
    97be:	1a f3       	and	#1,	r10	;r3 As==01
    97c0:	01 3c       	jmp	$+4      	;abs 0x97c4
    97c2:	0a 4d       	mov	r13,	r10	
    97c4:	0d 8a       	sub	r10,	r13	
    97c6:	0b 4a       	mov	r10,	r11	
    97c8:	3b 53       	add	#-1,	r11	;r3 As==11
    97ca:	3a e3       	inv	r10		
    97cc:	1a 53       	inc	r10		
    97ce:	0e 5a       	add	r10,	r14	
    97d0:	0c 5a       	add	r10,	r12	
    97d2:	09 4e       	mov	r14,	r9	
    97d4:	09 5b       	add	r11,	r9	
    97d6:	0a 4c       	mov	r12,	r10	
    97d8:	0a 5b       	add	r11,	r10	
    97da:	ea 49 00 00 	mov.b	@r9,	0(r10)	;0x0000(r10)
    97de:	3b 53       	add	#-1,	r11	;r3 As==11
    97e0:	3b 93       	cmp	#-1,	r11	;r3 As==11
    97e2:	f7 23       	jnz	$-16     	;abs 0x97d2
    97e4:	0a 4d       	mov	r13,	r10	
    97e6:	5a 03       	rrum	#1,	r10	
    97e8:	0d 24       	jz	$+28     	;abs 0x9804
    97ea:	0b 4a       	mov	r10,	r11	
    97ec:	08 4e       	mov	r14,	r8	
    97ee:	09 4c       	mov	r12,	r9	
    97f0:	28 83       	decd	r8		
    97f2:	29 83       	decd	r9		
    97f4:	a9 48 00 00 	mov	@r8,	0(r9)	;0x0000(r9)
    97f8:	3b 53       	add	#-1,	r11	;r3 As==11
    97fa:	fa 23       	jnz	$-10     	;abs 0x97f0
    97fc:	0b 8a       	sub	r10,	r11	
    97fe:	5b 02       	rlam	#1,	r11	
    9800:	0e 5b       	add	r11,	r14	
    9802:	0c 5b       	add	r11,	r12	
    9804:	1d f3       	and	#1,	r13	;r3 As==01
    9806:	03 24       	jz	$+8      	;abs 0x980e
    9808:	dc 4e ff ff 	mov.b	-1(r14),-1(r12)	;0xffff(r14), 0xffff(r12)
    980c:	ff ff 
    980e:	38 16       	popm.a	#4,	r11	
    9810:	10 01       	reta			

00009812 <memset>:
    9812:	3b 14       	pushm.a	#4,	r11	
    9814:	3d 90 06 00 	cmp	#6,	r13	;#0x0006
    9818:	09 2c       	jc	$+20     	;abs 0x982c
    981a:	0d 5f       	add	r15,	r13	
    981c:	0c 4f       	mov	r15,	r12	
    981e:	03 3c       	jmp	$+8      	;abs 0x9826
    9820:	cc 4e 00 00 	mov.b	r14,	0(r12)	;0x0000(r12)
    9824:	1c 53       	inc	r12		
    9826:	0c 9d       	cmp	r13,	r12	
    9828:	fb 23       	jnz	$-8      	;abs 0x9820
    982a:	1f 3c       	jmp	$+64     	;abs 0x986a
    982c:	0b 4e       	mov	r14,	r11	
    982e:	3b f0 ff 00 	and	#255,	r11	;#0x00ff
    9832:	03 24       	jz	$+8      	;abs 0x983a
    9834:	0c 4b       	mov	r11,	r12	
    9836:	8c 10       	swpb	r12		
    9838:	0b dc       	bis	r12,	r11	
    983a:	1f b3       	bit	#1,	r15	;r3 As==01
    983c:	06 24       	jz	$+14     	;abs 0x984a
    983e:	3d 53       	add	#-1,	r13	;r3 As==11
    9840:	cf 4e 00 00 	mov.b	r14,	0(r15)	;0x0000(r15)
    9844:	0a 4f       	mov	r15,	r10	
    9846:	1a 53       	inc	r10		
    9848:	01 3c       	jmp	$+4      	;abs 0x984c
    984a:	0a 4f       	mov	r15,	r10	
    984c:	0c 4d       	mov	r13,	r12	
    984e:	5c 03       	rrum	#1,	r12	
    9850:	08 4a       	mov	r10,	r8	
    9852:	09 4c       	mov	r12,	r9	
    9854:	88 4b 00 00 	mov	r11,	0(r8)	;0x0000(r8)
    9858:	28 53       	incd	r8		
    985a:	39 53       	add	#-1,	r9	;r3 As==11
    985c:	fb 23       	jnz	$-8      	;abs 0x9854
    985e:	5c 02       	rlam	#1,	r12	
    9860:	0c 5a       	add	r10,	r12	
    9862:	1d f3       	and	#1,	r13	;r3 As==01
    9864:	02 24       	jz	$+6      	;abs 0x986a
    9866:	cc 4e 00 00 	mov.b	r14,	0(r12)	;0x0000(r12)
    986a:	38 16       	popm.a	#4,	r11	
    986c:	10 01       	reta			

Disassembly of section .vectors:

0000ffc0 <__ivtbl_32>:
    ffc0:	08 33 08 33 08 33 08 33 08 33 08 33 08 33 08 33     .3.3.3.3.3.3.3.3
    ffd0:	08 33 08 33 08 33 08 33 08 33 08 33 08 33 08 33     .3.3.3.3.3.3.3.3
    ffe0:	00 36 84 36 4a 34 ce 34 08 33 08 33 08 33 ba 36     .6.6J4.4.3.3.3.6
    fff0:	30 35 98 36 e4 36 08 33 0a 35 08 33 08 33 00 31     05.6.6.3.5.3.3.1

msp430-objdump -x

user@409f9b5f2321:/work$ msp430-objdump -x nullnet-unicast.z1

nullnet-unicast.z1:     file format elf32-msp430
nullnet-unicast.z1
architecture: msp430:430X, flags 0x00000112:
EXEC_P, HAS_SYMS, D_PAGED
start address 0x00003100

Program Header:
    LOAD off    0x00000000 vaddr 0x0000302c paddr 0x0000302c align 2**0
         filesz 0x00006842 memsz 0x00006842 flags r-x
    LOAD off    0x00006844 vaddr 0x00009870 paddr 0x00009870 align 2**0
         filesz 0x00000613 memsz 0x00000613 flags r--
    LOAD off    0x00006e58 vaddr 0x00001100 paddr 0x00009e84 align 2**0
         filesz 0x000009b8 memsz 0x000013fe flags rw-
    LOAD off    0x00007810 vaddr 0x000024fe paddr 0x0000a83c align 2**0
         filesz 0x00000000 memsz 0x00000002 flags rw-
    LOAD off    0x00007810 vaddr 0x0000ffc0 paddr 0x0000ffc0 align 2**0
         filesz 0x00000040 memsz 0x00000040 flags r-x

Sections:
Idx Name          Size      VMA       LMA       File off  Algn
  0 .text         0000676e  00003100  00003100  000000d4  2**1
                  CONTENTS, ALLOC, LOAD, READONLY, CODE
  1 .rodata       00000613  00009870  00009870  00006844  2**2
                  CONTENTS, ALLOC, LOAD, READONLY, DATA
  2 .data         000009b8  00001100  00009e84  00006e58  2**1
                  CONTENTS, ALLOC, LOAD, DATA
  3 .bss          00000a46  00001ab8  0000a83c  00007810  2**1
                  ALLOC
  4 .noinit       00000002  000024fe  0000a83c  00007810  2**1
                  ALLOC
  5 .vectors      00000040  0000ffc0  0000ffc0  00007810  2**0
                  CONTENTS, ALLOC, LOAD, READONLY, CODE
  6 .comment      00000030  00000000  00000000  00007850  2**0
                  CONTENTS, READONLY
  7 .debug_aranges 00000588  00000000  00000000  00007880  2**3
                  CONTENTS, READONLY, DEBUGGING
  8 .debug_info   000052c2  00000000  00000000  00007e08  2**0
                  CONTENTS, READONLY, DEBUGGING
  9 .debug_abbrev 000026b3  00000000  00000000  0000d0ca  2**0
                  CONTENTS, READONLY, DEBUGGING
 10 .debug_line   00001d41  00000000  00000000  0000f77d  2**0
                  CONTENTS, READONLY, DEBUGGING
 11 .debug_frame  000006a4  00000000  00000000  000114c0  2**2
                  CONTENTS, READONLY, DEBUGGING
 12 .debug_str    000008e8  00000000  00000000  00011b64  2**0
                  CONTENTS, READONLY, DEBUGGING
 13 .debug_loc    00004424  00000000  00000000  0001244c  2**0
                  CONTENTS, READONLY, DEBUGGING
 14 .debug_ranges 000003e8  00000000  00000000  00016870  2**0
                  CONTENTS, READONLY, DEBUGGING
 15 .gnu.attributes 00000011  00000000  00000000  00016c58  2**0
                  CONTENTS, READONLY
SYMBOL TABLE:
00003100 l    d  .text	00000000 .text
00009870 l    d  .rodata	00000000 .rodata
00001100 l    d  .data	00000000 .data
00001ab8 l    d  .bss	00000000 .bss
000024fe l    d  .noinit	00000000 .noinit
0000ffc0 l    d  .vectors	00000000 .vectors
00000000 l    d  .comment	00000000 .comment
00000000 l    d  .debug_aranges	00000000 .debug_aranges
00000000 l    d  .debug_info	00000000 .debug_info
00000000 l    d  .debug_abbrev	00000000 .debug_abbrev
00000000 l    d  .debug_line	00000000 .debug_line
00000000 l    d  .debug_frame	00000000 .debug_frame
00000000 l    d  .debug_str	00000000 .debug_str
00000000 l    d  .debug_loc	00000000 .debug_loc
00000000 l    d  .debug_ranges	00000000 .debug_ranges
00000000 l    d  .gnu.attributes	00000000 .gnu.attributes
00000000 l    df *ABS*	00000000 contiki-main.c
00003308 l       .text	00000000 __br_unexpected_
00000000 l    df *ABS*	00000000 adxl345.c
000036ea l     F .text	00000012 status
000023d2 l     O .bss	00000001 enabled
000036fc l     F .text	0000002e accm_write_reg
0000372a l     F .text	0000002a accm_write_stream
00003754 l     F .text	00000054 accm_read_reg
000037a8 l     F .text	00000056 process_thread_accmeter_process
00001ab8 l     O .bss	00000002 int1_mask
00001aba l     O .bss	00000002 int2_mask
000037fe l     F .text	0000005a accm_read_axis.part.0
00003858 l     F .text	0000001e value
00001a3c l     O .data	00000016 adxl345_default_settings
00003920 l     F .text	00000026 configure
00001abc l     O .bss	00000008 suppressTimer1
00001ac4 l     O .bss	00000008 suppressTimer2
00000000 l    df *ABS*	00000000 button-sensor.c
0000395c l     F .text	00000018 status
00003974 l     F .text	00000020 value
00001acc l     O .bss	00000008 debouncetimer
00003994 l     F .text	0000004e configure
00000000 l    df *ABS*	00000000 cc2420-arch-sfd.c
00000000 l    df *ABS*	00000000 clock.c
00001ade l     O .bss	00000004 count
00001ae2 l     O .bss	00000004 seconds
00001adc l     O .bss	00000002 last_tar
00000000 l    df *ABS*	00000000 i2cmaster.c
000023ed l     O .bss	00000001 rx_byte_tot
000023ec l     O .bss	00000001 tx_byte_tot
00000000 l    df *ABS*	00000000 rtimer-arch.c
00000000 l    df *ABS*	00000000 uart0.c
00002407 l     O .bss	00000001 transmitting
000023c8 l     O .bss	00000004 uart0_input_handler
00000000 l    df *ABS*	00000000 watchdog.c
000023cc l     O .bss	00000002 counter
00000000 l    df *ABS*	00000000 autostart.c
00000000 l    df *ABS*	00000000 cc2420-arch.c
00000000 l    df *ABS*	00000000 cc2420.c
000039fc l     F .text	00000004 get_object
00003a00 l     F .text	00000004 set_object
00003a04 l     F .text	0000001a strobe
00003a1e l     F .text	00000046 getreg
00003a64 l     F .text	00000044 setreg
00003aa8 l     F .text	00000072 write_ram
00003b1a l     F .text	00000038 write_fifo_buf
00003b52 l     F .text	0000001e get_status
00003b70 l     F .text	0000001a on
000023d3 l     O .bss	00000001 poll_mode
000023d7 l     O .bss	00000001 receive_on
00003b8a l     F .text	0000000a cc2420_receiving_packet
00003b94 l     F .text	0000000a pending_packet
00003b9e l     F .text	00000022 wait_for_transmission
00003bc0 l     F .text	00000024 wait_for_status
00003be4 l     F .text	0000004c getrxdata
00003c30 l     F .text	0000001a flushrx
00003c4a l     F .text	00000028 off
00003c72 l     F .text	00000028 RELEASE_LOCK
000023d4 l     O .bss	00000001 locked
000023d5 l     O .bss	00000001 lock_on
000023d6 l     O .bss	00000001 lock_off
00003c9a l     F .text	00000030 set_frame_filtering
00003cca l     F .text	00000030 set_auto_ack
00003cfa l     F .text	0000002c set_poll_mode
00003d26 l     F .text	00000042 cc2420_prepare
00003d8a l     F .text	00000066 cc2420_transmit
00001a52 l     O .data	00000001 send_on_cca
00003df0 l     F .text	00000012 cc2420_send
00003e32 l     F .text	00000054 cc2420_cca
00003e86 l     F .text	000000ba cc2420_read
00003f40 l     F .text	00000056 process_thread_cc2420_process
00001ada l     O .bss	00000002 channel
00001ad4 l     O .bss	00000002 last_packet_timestamp
000040c4 l     F .text	0000011e get_value
00009948 l     O .rodata	00000010 output_power
000041f8 l     F .text	0000014a set_value
000023d8 l     O .bss	00000001 was_on
00001ad6 l     O .bss	00000002 prev_MDMCTRL1
00001ad8 l     O .bss	00000002 prev_DACTST
00000000 l    df *ABS*	00000000 contiki-z1-platform.c
00000000 l    df *ABS*	00000000 csma-output.c
000044aa l     F .text	00000066 schedule_transmission
00004596 l     F .text	000001b0 transmit_from_queue
00004510 l     F .text	00000086 tx_done
00001128 l     O .data	00000008 metadata_memb
00001120 l     O .data	00000008 packet_memb
00001ae6 l     O .bss	00000002 neighbor_list_list
00001118 l     O .data	00000008 neighbor_memb
000023d9 l     O .bss	00000002 neighbor_memb_memb_used
00001ae8 l     O .bss	0000004c neighbor_memb_memb_mem
000023db l     O .bss	00000008 packet_memb_memb_used
00001b34 l     O .bss	00000030 packet_memb_memb_mem
000023e3 l     O .bss	00000008 metadata_memb_memb_used
00001b64 l     O .bss	00000040 metadata_memb_memb_mem
00000000 l    df *ABS*	00000000 csma-security.c
00000000 l    df *ABS*	00000000 csma.c
000048be l     F .text	00000006 on
000048c4 l     F .text	00000006 off
000048ca l     F .text	00000038 max_payload
00004902 l     F .text	00000006 send_packet
00004908 l     F .text	00000060 input_packet
00004968 l     F .text	00000020 init
00000000 l    df *ABS*	00000000 ctimer.c
00004988 l     F .text	000000a0 process_thread_ctimer_process
00001ba4 l     O .bss	00000002 ctimer_list_list
000023eb l     O .bss	00000001 initialized
00000000 l    df *ABS*	00000000 energest.c
00000000 l    df *ABS*	00000000 etimer.c
00004ac6 l     F .text	00000070 update_time
00001ba6 l     O .bss	00000002 timerlist
00001ba8 l     O .bss	00000004 next_expiration
00004b40 l     F .text	000000c4 process_thread_etimer_process
00004c04 l     F .text	00000040 add_timer
00000000 l    df *ABS*	00000000 frame802154.c
00001148 l     O .data	00000002 mac_pan_id
00004dbc l     F .text	000000a8 field_len
00009b50 l     O .rodata	00000002 CSWTCH.16
00000000 l    df *ABS*	00000000 framer-802154.c
000051e8 l     F .text	0000009e parse
00005336 l     F .text	0000009e create_frame
000053d4 l     F .text	00000008 create
000053dc l     F .text	00000008 hdr_length
00000000 l    df *ABS*	00000000 leds-arch.c
00000000 l    df *ABS*	00000000 leds.c
00000000 l    df *ABS*	00000000 linkaddr.c
00000000 l    df *ABS*	00000000 list.c
00000000 l    df *ABS*	00000000 log.c
00000000 l    df *ABS*	00000000 mac-sequence.c
000023ef l     O .bss	00000001 mac_dsn
00001bac l     O .bss	000000e0 received_seqnos
00000000 l    df *ABS*	00000000 mac.c
00000000 l    df *ABS*	00000000 memb.c
00000000 l    df *ABS*	00000000 msp430.c
0000114c l     O .data	00000002 cur_break
00000000 l    df *ABS*	00000000 netstack.c
00000000 l    df *ABS*	00000000 node-id-z1.c
00000000 l    df *ABS*	00000000 node-id.c
00000000 l    df *ABS*	00000000 nullnet-unicast.c
000059a0 l     F .text	00000194 process_thread_nullnet_example_process
00001d80 l     O .bss	00000002 count.3283
00001d82 l     O .bss	0000000c periodic_timer.3282
00001d8e l     O .bss	00000002 count4Edges.3284
00000000 l    df *ABS*	00000000 nullnet.c
00006124 l     F .text	00000008 init
00001d90 l     O .bss	00000004 current_callback
0000612c l     F .text	00000042 output
0000616e l     F .text	00000034 input
00000000 l    df *ABS*	00000000 nullrouting.c
000061a8 l     F .text	00000002 init
000061aa l     F .text	00000002 root_set_prefix
000061ac l     F .text	00000004 root_start
000061b0 l     F .text	00000004 node_is_root
000061b4 l     F .text	00000004 get_root_ipaddr
000061b8 l     F .text	00000004 get_sr_node_ipaddr
000061bc l     F .text	00000002 leave_network
000061be l     F .text	00000004 node_has_joined
000061c2 l     F .text	00000004 node_is_reachable
000061c6 l     F .text	00000002 global_repair
000061c8 l     F .text	00000002 local_repair
000061ca l     F .text	00000004 ext_header_remove
000061ce l     F .text	00000004 ext_header_update
000061d2 l     F .text	00000004 ext_header_hbh_update
000061d6 l     F .text	00000004 ext_header_srh_update
000061da l     F .text	00000004 ext_header_srh_get_next_hop
000061de l     F .text	00000002 link_callback
000061e0 l     F .text	00000002 neighbor_state_changed
000061e2 l     F .text	00000002 drop_route
000061e4 l     F .text	00000004 is_in_leaf_mode
00000000 l    df *ABS*	00000000 packetbuf.c
00001d96 l     O .bss	00000002 buflen
00001d94 l     O .bss	00000002 bufptr
00001d98 l     O .bss	00000080 packetbuf_aligned
000023f0 l     O .bss	00000001 hdrlen
00000000 l    df *ABS*	00000000 platform.c
00001e18 l     O .bss	00000008 mgt_timer
00000000 l    df *ABS*	00000000 process.c
0000654a l     F .text	00000040 call_process
0000658a l     F .text	00000088 exit_process
00006612 l     F .text	00000030 do_poll
000023f1 l     O .bss	00000001 poll_requested
000023f2 l     O .bss	00000001 lastevent
000023f3 l     O .bss	00000001 fevent
000023f4 l     O .bss	00000001 nevents
00001e24 l     O .bss	00000030 events
00000000 l    df *ABS*	00000000 queuebuf.c
00001a08 l     O .data	00000008 buframmem
00001a10 l     O .data	00000008 bufmem
000023f5 l     O .bss	00000008 buframmem_memb_used
00001e54 l     O .bss	00000550 buframmem_memb_mem
000023fd l     O .bss	00000008 bufmem_memb_used
000023a4 l     O .bss	00000010 bufmem_memb_mem
00000000 l    df *ABS*	00000000 random.c
00000000 l    df *ABS*	00000000 rtimer.c
000023b4 l     O .bss	00000002 next_rtimer
00000000 l    df *ABS*	00000000 sensors.c
000068d8 l     F .text	000000c2 process_thread_sensors_process
000023b6 l     O .bss	00000002 i.2067
00002405 l     O .bss	00000001 num_sensors
000023b8 l     O .bss	00000002 events.2068
00000000 l    df *ABS*	00000000 spi-legacy.c
00000000 l    df *ABS*	00000000 stack-check.c
000023ba l     O .bss	00000002 stack_top.2107
00006a78 l     F .text	000000d2 process_thread_stack_check_process
000023bc l     O .bss	0000000c et.2129
00000000 l    df *ABS*	00000000 timer.c
00000000 l    df *ABS*	00000000 tmp102.c
00006bac l     F .text	00000012 status
00002406 l     O .bss	00000001 enabled
00006bec l     F .text	00000026 configure
00006cc8 l     F .text	00000006 value
00000000 l    df *ABS*	00000000 uart0-putchar.c
00000000 l    df *ABS*	00000000 xmem.c
00006d9e l     F .text	00000046 wait_ready
00000000 l    df *ABS*	00000000 ef_pow.c
000099f8 l     O .rodata	00000008 bp
00009a00 l     O .rodata	00000008 dp_l
00009a08 l     O .rodata	00000008 dp_h
00000000 l    df *ABS*	00000000 sf_scalbn.c
00000000 l    df *ABS*	00000000 ef_sqrt.c
00000000 l    df *ABS*	00000000 libgcc2.c
00000000 l    df *ABS*	00000000 libgcc2.c
00000000 l    df *ABS*	00000000 fp-bit.c
00007fbc l     F .text	0000026a _fpadd_parts
00000000 l    df *ABS*	00000000 fp-bit.c
00000000 l    df *ABS*	00000000 fp-bit.c
00000000 l    df *ABS*	00000000 fp-bit.c
00000000 l    df *ABS*	00000000 fp-bit.c
00000000 l    df *ABS*	00000000 fp-bit.c
00000000 l    df *ABS*	00000000 fp-bit.c
00000000 l    df *ABS*	00000000 fp-bit.c
00000000 l    df *ABS*	00000000 libgcc2.c
00000000 l    df *ABS*	00000000 libgcc2.c
00000000 l    df *ABS*	00000000 fp-bit.c
00000000 l    df *ABS*	00000000 fp-bit.c
00000000 l    df *ABS*	00000000 fp-bit.c
00000000 l    df *ABS*	00000000 fp-bit.c
00000000 l    df *ABS*	00000000 fp-bit.c
00000000 l    df *ABS*	00000000 printf.c
00000000 l    df *ABS*	00000000 sprintf.c
00008d78 l     F .text	00000022 append
000023d0 l     O .bss	00000002 available_
000023ce l     O .bss	00000002 destination_
00008d9a l     F .text	00000036 call_vuprintf
00000000 l    df *ABS*	00000000 vuprintf.c
00008dea l     F .text	00000176 print_field
00000000 l    df *ABS*	00000000 puts.c
00000000 l    df *ABS*	00000000 rand.c
00001a38 l     O .data	00000004 next
00000000 l    df *ABS*	00000000 memcmp.c
00000000 l    df *ABS*	00000000 memcpy.c
00000000 l    df *ABS*	00000000 memset.c
00000000 l    df *ABS*	00000000 fp-bit.c
00000000 l    df *ABS*	00000000 libgcc2.c
00000000 l    df *ABS*	00000000 z1-sensors.c
00006cce g     F .text	00000010 putchar
00000057 g       *ABS*	00000000 __BCSCTL1
0000005a g       *ABS*	00000000 __CACTL2
00000174 g       *ABS*	00000000 __TACCR1
00000000         *UND*	00000000 gpio_hal_arch_port_pin_set_input
00002434 g     O .bss	00000008 payYwcwcl
00000000 g       *ABS*	00000000 _far_end
000001d6 g       *ABS*	00000000 __DMA0DAL
00006884 g     F .text	00000006 random_rand
000024c4 g     O .bss	00000002 nullnet_buf
00004342 g     F .text	000000ea cc2420_init
00000084 g       *ABS*	00000000 __ADC12MCTL4
00006898 g     F .text	0000000e rtimer_arch_now
000009b8 g       *ABS*	00000000 __data_size
0000015a g       *ABS*	00000000 __ADC12MEM13
00003308  w      .text	00000000 __isr_14
00000128 g       *ABS*	00000000 __FCTL1
000000d8 g       *ABS*	00000000 __UCB1CTL0
000000d6 g       *ABS*	00000000 __UCA1RXBUF
00006cec g     F .text	00000016 uart0_writeb
000054c8 g     F .text	0000000e leds_arch_init
00000024 g       *ABS*	00000000 __P1IES
0000243c g     O .bss	00000008 payXwcwcl
0000622a g     F .text	0000003a packetbuf_copyto
00000000 g       .vectors	00000000 _efardata
00002410 g     O .bss	00000001 cc2420_last_rssi
000001f2 g       *ABS*	00000000 __DMA2SZ
00002408 g     O .bss	00000004 accm_int2_cb
00008d68 g     F .text	00000010 printf
00000069 g       *ABS*	00000000 __UCB0CTL1
000038ee g     F .text	00000032 accm_stop
00003530 g       .text	00000000 __isr_24
00002444 g     O .bss	00000004 payXwcl_d
00000000         *UND*	00000000 gpio_hal_arch_port_write_pin
00003308  w      .text	00000000 __isr_4
00000002 g       *ABS*	00000000 __IFG1
00006310 g     F .text	00000022 packetbuf_attr_copyto
000001e2 g       *ABS*	00000000 __DMA1DAL
000064f6 g     F .text	00000054 platform_idle
00004c76 g     F .text	0000000c etimer_pending
00005286 g     F .text	000000b0 framer_802154_setup_params
00000060 g       *ABS*	00000000 __UCA0CTL0
00000138 g       *ABS*	00000000 __OP2
000054d6 g     F .text	00000034 leds_arch_get
000084c0 g     F .text	00000142 __divsf3
000000df g       *ABS*	00000000 __UCB1TXBUF
00003fd0 g     F .text	0000004c cc2420_set_pan_addr
000001a4 g       *ABS*	00000000 __ADC12IFG
00006e02 g     F .text	00000088 xmem_pread
000062e6 g     F .text	0000002a packetbuf_copyfrom
0000568c g     F .text	0000006e mac_sequence_is_duplicate
0000012e g       *ABS*	00000000 __TAIV
00007ab4 g     F .text	00000006 powf
00005674 g     F .text	00000018 mac_sequence_set_dsn
00000000         *UND*	00000000 gpio_hal_arch_port_pin_cfg_set
00006706 g     F .text	0000004a process_post
00008cdc g     F .text	0000008c __fixsfsi
000001da g       *ABS*	00000000 __DMA0SZ
00010000 g       *ABS*	00000000 _efartext
0000113c g     O .data	0000000c etimer_process
00003334 g     F .text	00000000 __udivhi3
00000130 g       *ABS*	00000000 __MPY
00000001 g       *ABS*	00000000 __IE2
00002412 g     O .bss	00000002 cc2420_sfd_start_time
00009910 g     O .rodata	00000038 cc2420_driver
0000013a g       *ABS*	00000000 __RESLO
00000136 g       *ABS*	00000000 __MACS
000034ce g     F .text	0000003c irq_p2
00000087 g       *ABS*	00000000 __ADC12MCTL7
00004a8a g     F .text	00000010 ctimer_set
0000002b g       *ABS*	00000000 __P2IFG
00004ebe g     F .text	0000006e frame802154_create_fcf
0000001a g       *ABS*	00000000 __P3DIR
000001be g       *ABS*	00000000 __FCTL4
00006362 g     F .text	0000000a packetbuf_attr
0000998a g     O .rodata	0000000e nullnet_driver
000068b2 g     F .text	00000026 rtimer_run_next
00009e84 g       *ABS*	00000000 _etext
00000190 g       *ABS*	00000000 __TBR
00004c56 g     F .text	00000012 etimer_reset
0000401c g     F .text	00000016 cc2420_interrupt
000010f8 g       *ABS*	00000000 __CALDCO_16MHZ
000000d2 g       *ABS*	00000000 __UCA1BR0
00000000         *UND*	00000000 button_hal_button_count
00008272 g     F .text	00000050 __subsf3
0000001d g       *ABS*	00000000 __P4OUT
00000000         *UND*	00000000 gpio_hal_arch_port_read_pin
000066f8 g     F .text	0000000e process_nevents
00001a54 g     O .data	00000064 percentage10
000055e8 g     F .text	00000026 list_add
00003684 g     F .text	00000014 i2c_rx_interrupt
000001ee g       *ABS*	00000000 __DMA2DA
000034ce g       .text	00000000 __isr_19
00000a46 g       *ABS*	00000000 __bss_size
00000081 g       *ABS*	00000000 __ADC12MCTL1
0000017e g       *ABS*	00000000 __UCB1I2CSA
00000152 g       *ABS*	00000000 __ADC12MEM9
00003308  w      .text	00000000 __isr_29
00003f96 g     F .text	0000003a cc2420_set_channel
000010fd g       *ABS*	00000000 __CALBC1_8MHZ
000036ba g       .text	00000000 __isr_23
00003100  w      .text	00000000 __watchdog_support
00003302  w      .text	00000000 __stop_progExec__
00001e22 g     O .bss	00000002 process_list
0000972a g     F .text	000000e8 memcpy
000000d5 g       *ABS*	00000000 __UCA1STAT
00001150 g     O .data	0000000c nullnet_example_process
00002448 g     O .bss	00000008 payXwcl
0000002d g       *ABS*	00000000 __P2IE
00002450 g     O .bss	00000008 currentYwcl
00004032 g     F .text	0000002c cc2420_set_txpower
000000dc g       *ABS*	00000000 __UCB1I2CIE
000001ee g       *ABS*	00000000 __DMA2DAL
00006c70 g     F .text	00000058 tmp102_read_temp_x100
00000012 g       *ABS*	00000000 __P5REN
000001d6 g       *ABS*	00000000 __DMA0DA
00004f2c g     F .text	000000d4 frame802154_create
00006202 g     F .text	00000006 packetbuf_set_datalen
00000000         *UND*	00000000 slip_input_byte
0000003e g       *ABS*	00000000 __PASEL
000000cf g       *ABS*	00000000 __UCA1IRRCTL
000096a2 g     F .text	0000002c puts
0000449e g     F .text	0000000c init_platform
0000110c g     O .data	0000000c cc2420_process
0000620e g     F .text	00000006 packetbuf_datalen
000024c8 g     O .bss	00000010 packetbuf_addrs
0000560e g     F .text	00000010 list_length
00006484 g     F .text	00000072 platform_init_stage_three
00000192 g       *ABS*	00000000 __TBCCR0
00004e64 g     F .text	00000028 frame802154_is_broadcast_addr
00009958 g     O .rodata	0000001a csma_driver
00003308  w      .text	00000000 __isr_11
0000115c g     O .data	000004c4 anchor_nodes
00000186 g       *ABS*	00000000 __TBCCTL2
0000003a g       *ABS*	00000000 __P7OUT
00003356 g     F .text	00000000 __udivsi3
00000038 g       *ABS*	00000000 __PAIN
00000025 g       *ABS*	00000000 __P1IE
0000006b g       *ABS*	00000000 __UCB0BR1
00006332 g     F .text	00000024 packetbuf_attr_copyfrom
000069c4 g     F .text	00000032 spi_init
000024f8 g     O .bss	00000001 process_maxevents
000000d4 g       *ABS*	00000000 __UCA1MCTL
000000dd g       *ABS*	00000000 __UCB1STAT
000001a0 g       *ABS*	00000000 __ADC12CTL0
00002458 g     O .bss	00000008 sumX
00006762 g     F .text	00000036 process_start
00006d64 g     F .text	00000012 watchdog_periodic
0000869e g     F .text	0000004e __lesf2
0000588c g     F .text	0000000a splhigh_
000048b8 g     F .text	00000006 csma_security_parse_frame
00006750 g     F .text	00000012 process_post_synch
00000000         *UND*	00000000 gpio_hal_arch_port_write_pins
00005896 g     F .text	0000006e msp430_sync_dco
00000066 g       *ABS*	00000000 __UCA0RXBUF
000055a2 g     F .text	00000012 list_tail
0000350a g     F .text	00000026 cc2420_timerb1_interrupt
00006cde g     F .text	0000000e uart0_active
00000082 g       *ABS*	00000000 __ADC12MCTL2
0000019c g       *ABS*	00000000 __TBCCR5
00000061 g       *ABS*	00000000 __UCA0CTL1
00003600 g       .text	00000000 __isr_16
00006d50 g     F .text	00000014 watchdog_start
0000341c g       .text	00000000 __udivmoddi4
00002460 g     O .bss	00000008 sumXwcwcl
00006be2 g     F .text	0000000a tmp102_stop
00000038 g       *ABS*	00000000 __P7IN
0000114a g     O .data	00000002 curr_log_level_main
00004c44 g     F .text	00000012 etimer_set
000000cd g       *ABS*	00000000 __UCA1ABCTL
0000405e g     F .text	0000001e cc2420_get_txpower
00000035 g       *ABS*	00000000 __P6OUT
0000241c g     O .bss	00000001 transmit_data1
00000034 g       *ABS*	00000000 __P6IN
000001c8 g       *ABS*	00000000 __DAC12_0DAT
00000182 g       *ABS*	00000000 __TBCCTL0
000036e4 g       .text	00000000 __isr_26
0000997e g     O .rodata	00000008 linkaddr_null
00000000         *UND*	00000000 gpio_hal_arch_init
0000558c g     F .text	0000000c linkaddr_set_node_addr
0000550a g     F .text	0000003e leds_arch_set
0000006d g       *ABS*	00000000 __UCB0STAT
000069f6 g     F .text	0000002e stack_check_init
0000019e g       *ABS*	00000000 __TBCCR6
00003308  w      .text	00000000 __isr_5
00000013 g       *ABS*	00000000 __P6REN
0000241d g     O .bss	00000001 rx_byte_ctr
0000003b g       *ABS*	00000000 __P8OUT
00000063 g       *ABS*	00000000 __UCA0BR1
00000000         *UND*	00000000 uip_aligned_buf
000033fa g     F .text	00000000 __umoddi3
00009e84 g       *ABS*	00000000 __data_load_start
0000554e g     F .text	00000012 leds_on
00003308 g       .text	00000000 __dtors_end
00004cd6 g     F .text	00000006 frame802154_get_pan_id
0000344a g     F .text	00000084 port1_isr
0000003c g       *ABS*	00000000 __P7DIR
00000053 g       *ABS*	00000000 __BCSCTL3
00006798 g     F .text	00000018 process_poll
00006822 g     F .text	0000002a queuebuf_free
00000039 g       *ABS*	00000000 __P8IN
000001de g       *ABS*	00000000 __DMA1SA
000024fe g       .bss	00000000 __bss_end
00000088 g       *ABS*	00000000 __ADC12MCTL8
00000166 g       *ABS*	00000000 __TACCTL2
000067b0 g     F .text	00000012 queuebuf_init
000033e0 g     F .text	00000000 __udivdi3
000001e8 g       *ABS*	00000000 __DMA2CTL
00000065 g       *ABS*	00000000 __UCA0STAT
00001c8c g     O .bss	00000002 node_id
000001d2 g       *ABS*	00000000 __DMA0SAL
000098f4 g     O .rodata	0000000e adxl345
00001620 g     O .data	000003e8 node_positions
0000562a g     F .text	00000040 log_lladdr
00003308  w      .text	00000000 __isr_2
00000156 g       *ABS*	00000000 __ADC12MEM11
0000559e g     F .text	00000004 list_head
00006bbe g     F .text	00000024 tmp102_init
00000160 g       *ABS*	00000000 __TACTL
00000158 g       *ABS*	00000000 __ADC12MEM12
0000012c g       *ABS*	00000000 __FCTL3
00001c8e g     O .bss	000000f2 rssiList
00005572 g     F .text	00000008 linkaddr_copy
00003308  w      .text	00000000 __isr_10
00006642 g     F .text	0000000e process_alloc_event
0000241e g     O .bss	00000002 tx_buf_ptr
00000148 g       *ABS*	00000000 __ADC12MEM4
00002420 g     O .bss	00000001 tx_byte_ctr
00006c12 g     F .text	0000005e tmp102_read_reg
0000003e g       *ABS*	00000000 __P7SEL
0000002e g       *ABS*	00000000 __P2SEL
00005904 g     F .text	0000002e msp430_cpu_init
00000180 g       *ABS*	00000000 __TBCTL
000010f9 g       *ABS*	00000000 __CALBC1_16MHZ
00000126 g       *ABS*	00000000 __DMAIV
0000008d g       *ABS*	00000000 __ADC12MCTL13
00002414 g     O .bss	00000001 cc2420_last_correlation
0000242a g     O .bss	00000008 linkaddr_node_addr
0000014c g       *ABS*	00000000 __ADC12MEM6
00000023 g       *ABS*	00000000 __P1IFG
000010fb g       *ABS*	00000000 __CALBC1_12MHZ
00008ade g     F .text	0000010c __unpack_f
00004a40 g     F .text	0000004a ctimer_set_with_process
00002468 g     O .bss	00000008 currentXwcwcl
0000013c g       *ABS*	00000000 __RESHI
0000011a g       *ABS*	00000000 __UCB0I2CSA
000000ce g       *ABS*	00000000 __UCA1IRTCTL
00000172 g       *ABS*	00000000 __TACCR0
00005560 g     F .text	00000012 leds_off
00005488 g     F .text	0000000a i2c_busy
00000056 g       *ABS*	00000000 __DCOCTL
00000085 g       *ABS*	00000000 __ADC12MCTL5
00000003 g       *ABS*	00000000 __IFG2
000024fe g     O .noinit	00000002 __wdt_clear_value
00001100 g     O .data	0000000c accmeter_process
00000000 g       *ABS*	00000000 __far_data_size
00004a28 g     F .text	00000018 ctimer_init
000053e4 g     F .text	00000036 i2c_receiveinit
000010da g       *ABS*	00000000 __TLV_ADC12_1_TAG
0000240c g     O .bss	00000004 accm_int1_cb
00004cdc g     F .text	000000e0 frame802154_has_panid
0000001b g       *ABS*	00000000 __P3SEL
000001d0 g       *ABS*	00000000 __DMA0CTL
00000045 g       *ABS*	00000000 __P5SEL2
00008602 g     F .text	0000004e __gtsf2
00003308  w      .text	00000000 __isr_7
00002416 g     O .bss	00000002 cc2420_authority_level_of_sender
000041e2 g     F .text	00000016 cc2420_set_cca_threshold
00003698 g       .text	00000000 __isr_25
000010f7 g       *ABS*	00000000 __TLV_DCO_30_LEN
0000006c g       *ABS*	00000000 __UCB0I2CIE
0000006a g       *ABS*	00000000 __UCB0BR0
00004446 g     F .text	00000028 clock_init
0000447a g     F .text	00000024 clock_wait
00003384 g     F .text	00000000 __umodsi3
00006356 g     F .text	0000000c packetbuf_set_attr
00000028 g       *ABS*	00000000 __P2IN
00006b66 g     F .text	0000002a timer_expired
00006264 g     F .text	0000000c packetbuf_totlen
0000014e g       *ABS*	00000000 __ADC12MEM7
0000891a g     F .text	000001c4 __pack_f
00000118 g       *ABS*	00000000 __UCB0I2COA
00000184 g       *ABS*	00000000 __TBCCTL1
000000de g       *ABS*	00000000 __UCB1RXBUF
0000005b g       *ABS*	00000000 __CAPD
0000334e g     F .text	00000000 __umodhi3
0000688a g     F .text	0000000e rtimer_arch_init
00003308  w      .text	00000000 __isr_0
00002470 g     O .bss	00000008 currentXwcl
00002422 g     O .bss	00000002 i
000024d8 g     O .bss	00000018 packetbuf_attrs
00000029 g       *ABS*	00000000 __P2OUT
0000566a g     F .text	0000000a mac_sequence_init
00008874 g     F .text	0000006a __clzsi2
0000012a g       *ABS*	00000000 __FCTL2
00000064 g       *ABS*	00000000 __UCA0MCTL
00002432 g     O .bss	00000002 msp430_dco_required
00003600 g     F .text	00000084 i2c_tx_interrupt
00005932 g     F .text	0000000e netstack_init
00003128  w      .text	00000000 __do_clear_bss
000023ee g     O .bss	00000001 prescale_msb
00000014 g       *ABS*	00000000 __PAREN
0000008f g       *ABS*	00000000 __ADC12MCTL15
00003d68 g     F .text	00000022 cc2420_on
000067c2 g     F .text	0000004e queuebuf_new_from_packetbuf
00000007 g       *ABS*	00000000 __UC1IFG
00000021 g       *ABS*	00000000 __P1OUT
000068a6 g     F .text	00000006 rtimer_arch_schedule
000036e4 g     F .text	00000006 watchdog_interrupt
0000002c g       *ABS*	00000000 __P2IES
0000015c g       *ABS*	00000000 __ADC12MEM14
00000026 g       *ABS*	00000000 __P1SEL
00002478 g     O .bss	00000004 Ywcwcl
00006d02 g     F .text	0000004e uart0_init
0000557a g     F .text	00000012 linkaddr_cmp
00006d76 g     F .text	00000016 watchdog_stop
00000198 g       *ABS*	00000000 __TBCCR3
0000003d g       *ABS*	00000000 __P8DIR
00000080 g       *ABS*	00000000 __ADC12MCTL0
000096ce g     F .text	00000026 rand
0000541a g     F .text	00000030 i2c_transmitinit
0000350a g       .text	00000000 __isr_28
00001a18 g     O .data	0000000c sensors_process
00000140 g       *ABS*	00000000 __ADC12MEM0
00006810 g     F .text	00000012 queuebuf_update_attr_from_packetbuf
000086ec g     F .text	000000a4 __floatsisf
00002424 g     O .bss	00000001 receive_data
00002418 g     O .bss	00000001 cc2420_sfd_counter
00000000         *UND*	00000000 button_hal_buttons
00003356 g       .text	00000000 __ext_udivmod32
00000000         *UND*	00000000 gpio_hal_arch_port_interrupt_enable
00000027 g       *ABS*	00000000 __P1REN
0000330e g       .text	00000000 __mulsi3
00009998 g     O .rodata	00000052 nullrouting_driver
000010c0 g       *ABS*	00000000 __TLV_CHECKSUM
0000114e g     O .data	00000002 anchor_count
0000330c  w      .text	00000000 _unexpected_
00003308  w      .text	00000000 __isr_8
000010db g       *ABS*	00000000 __TLV_ADC12_1_LEN
0000014a g       *ABS*	00000000 __ADC12MEM5
00004c82 g     F .text	00000016 etimer_next_expiration_time
0000018a g       *ABS*	00000000 __TBCCTL4
00003308  w      .text	00000000 __isr_20
00006270 g     F .text	0000003c packetbuf_hdralloc
0000008e g       *ABS*	00000000 __ADC12MCTL14
00003308  w      .text	00000000 __isr_3
000001a6 g       *ABS*	00000000 __ADC12IE
00008f60 g     F .text	00000742 vuprintf
00004b36 g     F .text	0000000a etimer_request_poll
000096fe g     F .text	0000002c memcmp
00000144 g       *ABS*	00000000 __ADC12MEM2
00007e98 g     F .text	00000124 __floatundisf
000001ea g       *ABS*	00000000 __DMA2SAL
000001e6 g       *ABS*	00000000 __DMA1SZ
000010fc g       *ABS*	00000000 __CALDCO_8MHZ
00000033 g       *ABS*	00000000 __P5SEL
0000ffc0 g       .vectors	00000000 __vectors_start
00003334 g       .text	00000000 __ext_udivmod16
00003530 g     F .text	000000d0 timera1
000000da g       *ABS*	00000000 __UCB1BR0
0000636c g     F .text	00000014 packetbuf_set_addr
0000344a g       .text	00000000 __isr_18
00000030 g       *ABS*	00000000 __P5IN
00003100  w      .text	00000000 _reset_vector__
00003308 g       .text	00000000 __ctors_start
0000338e g       .text	00000000 __xabi_udivmod64
00003308  w      .text	00000000 __isr_12
00006e8a g     F .text	00000c2a __ieee754_powf
00000036 g       *ABS*	00000000 __P6DIR
00001130 g     O .data	0000000c ctimer_process
000010fa g       *ABS*	00000000 __CALDCO_12MHZ
00009a10 g     O .rodata	00000008 __thenan_sf
0000003f g       *ABS*	00000000 __P8SEL
000000d0 g       *ABS*	00000000 __UCA1CTL0
0000446e g     F .text	0000000c clock_delay
00000018 g       *ABS*	00000000 __P3IN
00003110  w      .text	00000000 __do_copy_data
00007aba g     F .text	00000168 scalbnf
000024c6 g     O .bss	00000002 nullnet_len
0000247c g     O .bss	00000008 sumY
00006214 g     F .text	0000000a packetbuf_hdrlen
00000150 g       *ABS*	00000000 __ADC12MEM8
00002425 g     O .bss	00000002 rx_buf
00000142 g       *ABS*	00000000 __ADC12MEM1
000000d7 g       *ABS*	00000000 __UCA1TXBUF
00001ab8 g       .bss	00000000 __bss_start
00000014 g       *ABS*	00000000 __P7REN
00006650 g     F .text	0000001c process_init
00009812 g     F .text	0000005c memset
00007c22 g     F .text	00000156 __ieee754_sqrtf
0000313e g     F .text	000001c4 main
00000176 g       *ABS*	00000000 __TACCR2
00006380 g     F .text	0000000e packetbuf_addr
0000019a g       *ABS*	00000000 __TBCCR4
00006de4 g     F .text	0000001e xmem_init
0000638e g     F .text	0000000e packetbuf_holds_broadcast
000096f4 g     F .text	0000000a srand
00003308  w      .text	00000000 __isr_13
00008650 g     F .text	0000004e __ltsf2
00002484 g     O .bss	00000008 payYwcl
00000000         *UND*	00000000 gpio_hal_arch_port_clear_pin
0000248c g     O .bss	00000008 averageX
000001d2 g       *ABS*	00000000 __DMA0SA
00000170 g       *ABS*	00000000 __TAR
00000124 g       *ABS*	00000000 __DMACTL1
0000001e g       *ABS*	00000000 __P4DIR
0000561e g     F .text	0000000c list_item_next
000057ca g     F .text	0000003e memb_alloc
00003308  w      .text	00000000 __isr_27
00002494 g     O .bss	00000004 payda_wcl
00005940 g     F .text	0000004c node_id_z1_restore
0000544a g     F .text	0000003e i2c_receive_n
00007d78 g     F .text	00000120 __fixunssfdi
00000162 g       *ABS*	00000000 __TACCTL0
00010000 g       .vectors	00000000 _vectors_end
00000154 g       *ABS*	00000000 __ADC12MEM10
000082c2 g     F .text	000001fe __mulsf3
00001a24 g     O .data	0000000c stack_check_process
00002498 g     O .bss	00000004 Xwcl
0000488e g     F .text	0000001a csma_output_init
000024f0 g     O .bss	00000008 node_mac
000001ea g       *ABS*	00000000 __DMA2SA
00006208 g     F .text	00000006 packetbuf_hdrptr
0000002a g       *ABS*	00000000 __P2DIR
00005808 g     F .text	00000032 memb_free
0000249c g     O .bss	00000008 sumYwcwcl
00000089 g       *ABS*	00000000 __ADC12MCTL9
0000017c g       *ABS*	00000000 __UCB1I2COA
0000008a g       *ABS*	00000000 __ADC12MCTL10
000000db g       *ABS*	00000000 __UCB1BR1
00004c98 g     F .text	0000003e etimer_stop
00005598 g     F .text	00000006 list_init
000036ba g     F .text	0000002a uart0_rx_interrupt
0000598c g     F .text	00000014 node_id_init
00000068 g       *ABS*	00000000 __UCB0CTL0
0000002f g       *ABS*	00000000 __P2REN
00000032 g       *ABS*	00000000 __P5DIR
000039e2 g     F .text	0000001a cc2420_arch_init
00008dd0 g     F .text	0000001a sprintf
00009d7c g     O .rodata	00000100 __clz_tab
000001c2 g       *ABS*	00000000 __DAC12_1CTL
00004ac4 g     F .text	00000002 energest_flush
0000003a g       *ABS*	00000000 __PAOUT
000001a2 g       *ABS*	00000000 __ADC12CTL1
0000003c g       *ABS*	00000000 __PADIR
0000684c g     F .text	00000032 queuebuf_to_packetbuf
00008c8e g     F .text	0000004e __gesf2
0000006e g       *ABS*	00000000 __UCB0RXBUF
0000687e g     F .text	00000006 random_init
00000000 g       .vectors	00000000 __far_bss_start
000001a8 g       *ABS*	00000000 __ADC12IV
000001dc g       *ABS*	00000000 __DMA1CTL
000024fe g       .noinit	00000000 __noinit_start
00005794 g     F .text	00000036 memb_init
000061a2 g     F .text	00000006 nullnet_set_input_callback
00005b34 g     F .text	000005f0 input_callback
0000583a g     F .text	0000002a memb_inmemb
00003308  w      .text	00000000 __isr_9
0000005e g       *ABS*	00000000 __UCA0IRTCTL
00000000         *UND*	00000000 gpio_hal_arch_port_set_pin
000048a8 g     F .text	00000010 csma_security_create_frame
00009e84 g       *ABS*	00000000 __data_start_rom
00000015 g       *ABS*	00000000 __P8REN
00002500 g       .noinit	00000000 __noinit_end
000010fe g       *ABS*	00000000 __CALDCO_1MHZ
00000067 g       *ABS*	00000000 __UCA0TXBUF
0000018c g       *ABS*	00000000 __TBCCTL5
000001de g       *ABS*	00000000 __DMA1SAL
00000000         *UND*	00000000 spi_arch_has_lock
00003876 g     F .text	00000078 accm_init
00000000 g       .vectors	00000000 __far_bss_end
0000310c  w      .text	00000000 __init_stack
000056fa g     F .text	00000086 mac_sequence_register_seqno
0000005d g       *ABS*	00000000 __UCA0ABCTL
00000086 g       *ABS*	00000000 __ADC12MCTL6
00004ac2 g     F .text	00000002 energest_init
00004a9a g     F .text	00000028 ctimer_stop
00006b4a g     F .text	0000001c timer_set
00000188 g       *ABS*	00000000 __TBCCTL3
00006a24 g     F .text	00000054 stack_check_get_usage
00003e02 g     F .text	00000030 cc2420_off
00000019 g       *ABS*	00000000 __P3OUT
00006b90 g     F .text	0000001c timer_reset
00003308  w      .text	00000000 __isr_30
000001ca g       *ABS*	00000000 __DAC12_1DAT
0000ffc0 g     O .vectors	00000040 __ivtbl_32
0000508c g     F .text	0000015c frame802154_parse
00003308 g       .text	00000000 __dtors_start
00003308  w      .text	00000000 __isr_6
00003308 g       .text	00000000 __ctors_end
00000132 g       *ABS*	00000000 __MPYS
00000062 g       *ABS*	00000000 __UCA0BR0
000024a4 g     O .bss	00000008 currentYwcwcl
00003308  w      .text	00000000 __isr_22
00004e8c g     F .text	00000032 frame802154_hdrlen
000024ac g     O .bss	00000004 Ywcl
00003100 g       *ABS*	00000000 __stack
0000699a g     F .text	0000002a sensors_changed
00002427 g     O .bss	00000001 transmit_data2
00000037 g       *ABS*	00000000 __P6SEL
00003308  w      .text	00000000 __isr_1
0000666c g     F .text	0000008c process_run
0000008c g       *ABS*	00000000 __ADC12MCTL12
00005000 g     F .text	0000008c frame802154_parse_fcf
00009972 g     O .rodata	0000000c framer_802154
00000000 g       .vectors	00000000 __far_data_start
00001ab8 g       .data	00000000 _edata
00001e20 g     O .bss	00000002 process_current
00002500 g       *ABS*	00000000 _end
00000006 g       *ABS*	00000000 __UC1IE
00002428 g     O .bss	00000002 rx_buf_ptr
000054b4 g     F .text	00000014 i2c_transmit_n
00000000         *UND*	00000000 gpio_hal_arch_port_read_pins
00003698 g     F .text	00000022 timera0
00004c68 g     F .text	0000000e etimer_expired
00004746 g     F .text	00000148 csma_output_packet
00000194 g       *ABS*	00000000 __TBCCR1
000024fa g     O .bss	00000004 sensors_flags
00009986 g     O .rodata	00000004 autostart_processes
0000407c g     F .text	00000048 cc2420_rssi
0000011e g       *ABS*	00000000 __TBIV
000061e8 g     F .text	0000001a packetbuf_hdrreduce
000001c0 g       *ABS*	00000000 __DAC12_0CTL
00010000 g       *ABS*	00000000 __far_data_load_start
000099ea g     O .rodata	0000000e tmp102
00008790 g     F .text	000000e4 __floatunsisf
0000015e g       *ABS*	00000000 __ADC12MEM15
0000a83c g       *ABS*	00000000 __data_end_rom
0000621e g     F .text	0000000c packetbuf_dataptr
00000134 g       *ABS*	00000000 __MAC
00000058 g       *ABS*	00000000 __BCSCTL2
00003302  w      .text	00000000 _endless_loop__
00000122 g       *ABS*	00000000 __DMACTL0
0000001f g       *ABS*	00000000 __P4SEL
00000196 g       *ABS*	00000000 __TBCCR2
00000041 g       *ABS*	00000000 __P1SEL2
00003308  w      .text	00000000 __isr_15
00000022 g       *ABS*	00000000 __P1DIR
00000146 g       *ABS*	00000000 __ADC12MEM3
00001a53 g     O .data	00000001 prescale_lsb
000088de g     F .text	0000003c __fixunssfsi
00008bea g     F .text	000000a4 __fpcmp_parts_f
000024b0 g     O .bss	00000004 payYwcl_d
0000442c g     F .text	0000001a clock_time
0000005f g       *ABS*	00000000 __UCA0IRRCTL
00000010 g       *ABS*	00000000 __P3REN
00005492 g     F .text	00000022 i2c_enable
00000164 g       *ABS*	00000000 __TACCTL1
000063ae g     F .text	000000d6 platform_init_stage_two
0000241a g     O .bss	00000002 cc2420_sfd_end_time
000000d3 g       *ABS*	00000000 __UCA1BR1
00000000 g       *ABS*	00000000 __far_bss_size
0000006f g       *ABS*	00000000 __UCB0TXBUF
000024b4 g     O .bss	00000004 payda_wcwcl
000010ff g       *ABS*	00000000 __CALBC1_1MHZ
00000055 g       *ABS*	00000000 __SVSCTL
00002500 g       *ABS*	00000000 _stack
00003110  w      .text	00000000 __low_level_init
000062d4 g     F .text	00000012 packetbuf_clear
00003684 g       .text	00000000 __isr_17
000024f9 g     O .bss	00000001 sensors_event
00000011 g       *ABS*	00000000 __P4REN
000068ac g     F .text	00000006 rtimer_init
00001100 g       .data	00000000 __data_start
000000d1 g       *ABS*	00000000 __UCA1CTL1
0000018e g       *ABS*	00000000 __TBCCTL6
00003308  w      .text	00000000 __isr_21
00009902 g     O .rodata	0000000e button_sensor
00005864 g     F .text	00000028 msp430_init_dco
00006d8c g     F .text	00000012 watchdog_init
000024b8 g     O .bss	00000008 averageY
000001e2 g       *ABS*	00000000 __DMA1DA
00000120 g       *ABS*	00000000 __WDTCTL
00003946 g     F .text	00000016 autostart_start
00000083 g       *ABS*	00000000 __ADC12MCTL3
00000000 g       *ABS*	00000000 __IE1
000055b4 g     F .text	00000034 list_remove
000000d9 g       *ABS*	00000000 __UCB1CTL1
00001a30 g     O .data	00000008 sensors
000024c0 g     O .bss	00000004 Xwcwcl
00000059 g       *ABS*	00000000 __CACTL1
000010f6 g       *ABS*	00000000 __TLV_DCO_30_TAG
00000020 g       *ABS*	00000000 __P1IN
0000001c g       *ABS*	00000000 __P4IN
000062ac g     F .text	00000028 packetbuf_attr_clear
0000008b g       *ABS*	00000000 __ADC12MCTL11
00008226 g     F .text	0000004c __addsf3
0000013e g       *ABS*	00000000 __SUMEXT
00000031 g       *ABS*	00000000 __P5OUT
00005780 g     F .text	00000014 mac_call_sent_callback
00005548 g     F .text	00000006 leds_init
0000639c g     F .text	00000012 platform_init_stage_one































