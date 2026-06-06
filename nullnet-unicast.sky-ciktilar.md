msp430-readelf -h



user@409f9b5f2321:/work$ msp430-readelf -h nullnet-unicast.sky

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
  Entry point address:               0x4000
  Start of program headers:          52 (bytes into file)
  Start of section headers:          89448 (bytes into file)
  Flags:                             0x10000000
  Size of this header:               52 (bytes)
  Size of program headers:           32 (bytes)
  Number of program headers:         4
  Size of section headers:           40 (bytes)
  Number of section headers:         19
  Section header string table index: 16msp430-readelf -S

user@409f9b5f2321:/work$ msp430-readelf -S nullnet-unicast.sky

There are 19 section headers, starting at offset 0x15d68:

Section Headers:
  [Nr] Name              Type            Addr     Off    Size   ES Flg Lk Inf Al
  [ 0]                   NULL            00000000 000000 000000 00      0   0  0
  [ 1] .text             PROGBITS        00004000 0000b4 006b0c 00  AX  0   0  2
  [ 2] .rodata           PROGBITS        0000ab0c 006bc0 0006c7 00   A  0   0  4
  [ 3] .data             PROGBITS        00001100 007288 00114a 00  WA  0   0  2
  [ 4] .bss              NOBITS          0000224a 0083d2 000c0c 00  WA  0   0  2
  [ 5] .noinit           NOBITS          00002e56 0083d2 000002 00  WA  0   0  2
  [ 6] .vectors          PROGBITS        0000ffe0 0083d2 000020 00  AX  0   0  1
  [ 7] .comment          PROGBITS        00000000 0083f2 000030 01  MS  0   0  1
  [ 8] .debug_aranges    PROGBITS        00000000 008424 000374 00      0   0  4
  [ 9] .debug_info       PROGBITS        00000000 008798 004e6a 00      0   0  1
  [10] .debug_abbrev     PROGBITS        00000000 00d602 002684 00      0   0  1
  [11] .debug_line       PROGBITS        00000000 00fc86 001c0d 00      0   0  1
  [12] .debug_frame      PROGBITS        00000000 011894 000682 00      0   0  2
  [13] .debug_str        PROGBITS        00000000 011f16 00089d 01  MS  0   0  1
  [14] .debug_loc        PROGBITS        00000000 0127b3 0033b8 00      0   0  1
  [15] .debug_ranges     PROGBITS        00000000 015b6b 000148 00      0   0  1
  [16] .shstrtab         STRTAB          00000000 015cb3 0000b4 00      0   0  1
  [17] .symtab           SYMTAB          00000000 016060 003140 10     18 262  4
  [18] .strtab           STRTAB          00000000 0191a0 0026a9 00      0   0  1
Key to Flags:
  W (write), A (alloc), X (execute), M (merge), S (strings)
  I (info), L (link order), G (group), T (TLS), E (exclude), x (unknown)
  O (extra OS processing required) o (OS specific), p (processor specific)
msp430-readelf -p .comment

user@409f9b5f2321:/work$ msp430-readelf -p .comment nullnet-unicast.sky

String dump of section '.comment':
  [     0]  GCC: (GNU) 4.7.2 20120920 (mspgcc dev 20120911)


msp430-size

user@409f9b5f2321:/work$ msp430-size nullnet-unicast.sky
   text	   data	    bss	    dec	    hex	filename
  29171	   4426	   3086	  36683	   8f4b	nullnet-unicast.skymsp430-strings

user@409f9b5f2321:/work$ msp430-strings nullnet-unicast.sky

J2LLCPCCC2420 driver
not for us : 
CSMA
T8T>T
TVaNaR_
(NULL LL addr)
%02x
LL-NULL
LL-%04x
tcpip
ipv6
6lowpan
nullnet
framer
6top
coap
snmp
lwm2m
main
None
Errors
Warnings
Info
Debug
INFO
[%-4s: %-10s] 
linkaddr_node_addr iss 
count.1 %d, remain: %d
CLOCK_SECOND %lu
Broadcast from %d, to all. %llu %llu 
Sending done from :%d
num_signal_received_anchors() - start: %d ticks
%d-)%d  
Received %u , node_id %d from 
 RSSI is : %d
zx:%llu zy:%llu zdis:%llu rssi:%d rssiList[count-1]:%d 
zeros: %s
num_signal_received_anchors: %d
 A[0][0]:%llu A[0][1]:%llu A[1][0]:%llu A[1][1]:%llu det:%llu num_anchors: %d
AQ%d: %s
 b0:%llu b1:%llu num_anchors: %d
bzs: %s
det %lluinv_det %llu num: %d
det: %s
 %llu %llu num: %d
mlt: %s
NullNet unicast example
V:BsV)Bnullnet
pnullrouting
HqJqLqPqTqXq\q^qbqfqhqjqnqrqvqzq~q
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
Ctimer process
Event timer
INFO
[%-4s: %-10s] 
CC2420 CCA threshold %i
Sensors
Serial driver
Stack
[%-4s: %-10s] 
Check in inconsistent state: %ld vs. %ld
Check failed: %ld vs. %ld
Stack check
(null)msp430-nm —-size-sort -S

user@409f9b5f2321:/work$ msp430-nm --size-sort -S nullnet-unicast.sky

00002de2 00000001 B cc2420_last_correlation
00002dde 00000001 B cc2420_last_rssi
00002de6 00000001 B cc2420_sfd_counter
000025ec 00000001 b fevent
0000255c 00000001 b hdrlen
00002328 00000001 b initialized
000025eb 00000001 b lastevent
00002258 00000001 b lock_off
00002257 00000001 b lock_on
00002256 00000001 b locked
00002348 00000001 b mac_dsn
000025ed 00000001 b nevents
00002c20 00000001 b num_sensors
00002c26 00000001 b overflow.1985
00002252 00000001 b poll_mode
000025ea 00000001 b poll_requested
00002259 00000001 b receive_on
00002d3f 00000001 b rx_in_progress
0000110a 00000001 d send_on_cca
00002e54 00000001 B sensors_event
00002e55 00000001 B serial_line_event_message
00002d3e 00000001 b transmitting
0000225a 00000001 b was_on
0000b019 00000002 r CSWTCH.16
00002e56 00000002 B __wdt_clear_value
00001190 00000002 D anchor_count
00002ddc 00000002 b available_
0000255a 00000002 b buflen
00002558 00000002 b bufptr
00002de4 00000002 B cc2420_authority_level_of_sender
00002de8 00000002 B cc2420_sfd_end_time
00002de0 00000002 B cc2420_sfd_start_time
00002260 00000002 b channel
00002546 00000002 b count.3214
00002554 00000002 b count4Edges.3215
00002dd8 00000002 b counter
0000232a 00000002 b ctimer_list_list
0000118e 00000002 d cur_break
00002340 00000002 B curr_log_level_6lowpan
00002338 00000002 B curr_log_level_6top
00002336 00000002 B curr_log_level_coap
0000233a 00000002 B curr_log_level_framer
00002342 00000002 B curr_log_level_ipv6
00002332 00000002 B curr_log_level_lwm2m
0000233c 00000002 B curr_log_level_mac
0000118c 00000002 D curr_log_level_main
0000233e 00000002 B curr_log_level_nullnet
00002346 00000002 B curr_log_level_rpl
00002334 00000002 B curr_log_level_snmp
00002344 00000002 B curr_log_level_tcpip
00002556 00000002 b current_callback
00002dda 00000002 b destination_
00007182 00000002 t drop_route
000057a6 00000002 T energest_flush
000057a4 00000002 T energest_init
00002c24 00000002 b events.2008
00007166 00000002 t global_repair
00002c22 00000002 b i.2007
00007148 00000002 t init
00002254 00000002 b last_packet_timestamp
00002dd6 00000002 b last_size
00002262 00000002 b last_tar
0000715c 00000002 t leave_network
0000717e 00000002 t link_callback
00007168 00000002 t local_repair
0000113c 00000002 d mac_pan_id
00002df2 00000002 B msp430_dco_required
0000226c 00000002 b neighbor_list_list
0000226e 00000002 b neighbor_memb_memb_used
00007180 00000002 t neighbor_state_changed
00002c1e 00000002 b next_rtimer
0000242a 00000002 B node_id
00002e1e 00000002 B nullnet_buf
00002e20 00000002 B nullnet_len
00002e18 00000002 B num_signal_received_anchors
0000225e 00000002 b prev_DACTST
0000225c 00000002 b prev_MDMCTRL1
000025e6 00000002 B process_current
000025e8 00000002 B process_list
00002c2e 00000002 b ptr.1992
0000714a 00000002 t root_set_prefix
00002e4a 00000002 B sensors_flags
00002d30 00000002 b stack_top.2047
0000232c 00000002 b timerlist
00002d54 00000002 b uart1_input_handler
00002e08 00000004 B anchors_zero_x
00002e14 00000004 B anchors_zero_y
0000aec4 00000004 R anchorx1
0000aeb4 00000004 R anchorx17
0000aebc 00000004 R anchorx4
0000aec0 00000004 R anchory1
0000aeb0 00000004 R anchory17
0000aeb8 00000004 R anchory4
0000ae94 00000004 R autostart_processes
0000ab60 00000004 R cc2420_aes_128_driver
00002264 00000004 b count
00002df8 00000004 B d_diff
00002df4 00000004 B distance_zero
00007172 00000004 t ext_header_hbh_update
0000716a 00000004 t ext_header_remove
0000717a 00000004 t ext_header_srh_get_next_hop
00007176 00000004 t ext_header_srh_update
0000716e 00000004 t ext_header_update
0000434c 00000004 t get_object
00007154 00000004 t get_root_ipaddr
00007158 00000004 t get_sr_node_ipaddr
00007184 00000004 t is_in_leaf_mode
00006234 00000004 T list_head
00002246 00000004 d next
0000232e 00000004 b next_expiration
0000715e 00000004 t node_has_joined
00007162 00000004 t node_is_reachable
00007150 00000004 t node_is_root
0000714c 00000004 t root_start
00002268 00000004 b seconds
0000110c 00000004 D sensors
00004350 00000004 t set_object
00002e1a 00000004 B x_diff
00002dfc 00000004 B y_diff
000053ee 00000006 T csma_security_parse_frame
000059c8 00000006 T frame802154_get_pan_id
0000abc0 00000006 R framer_802154
000070ba 00000006 t init
000061de 00000006 T leds_init
0000622e 00000006 T list_init
00007142 00000006 T nullnet_set_input_callback
000053fa 00000006 t off
000053f4 00000006 t on
000071ae 00000006 T packetbuf_datalen
000071a8 00000006 T packetbuf_hdrptr
000071a2 00000006 T packetbuf_set_datalen
00008b48 00000006 T powf
000077ee 00000006 T random_init
000077f4 00000006 T random_rand
000078c2 00000006 T rtimer_arch_schedule
000078c8 00000006 T rtimer_init
00002c28 00000006 b rxbuf
00005438 00000006 t send_packet
00007e6e 00000006 T watchdog_interrupt
0000af26 00000008 R __thenan_sf
0000242c 00000008 B b
0000af0e 00000008 r bp
00002220 00000008 d bufmem
00002c06 00000008 b bufmem_memb_used
00002218 00000008 d buframmem
000026ae 00000008 b buframmem_memb_used
0000ab58 00000008 R button_sensor
0000614e 00000008 t create
0000224a 00000008 b debouncetimer
0000af1e 00000008 r dp_h
0000af16 00000008 r dp_l
00002e4c 00000008 B ds2411_id
00002e00 00000008 B estimated_position_x
00002e0c 00000008 B estimated_position_y
00006156 00000008 t hdr_length
00006208 00000008 T linkaddr_copy
00002dea 00000008 B linkaddr_node_addr
0000abc6 00000008 R linkaddr_null
00001120 00000008 d metadata_memb
000022f0 00000008 b metadata_memb_memb_used
000025de 00000008 b mgt_timer
00001110 00000008 d neighbor_memb
0000aed0 00000008 R nullnet_driver
00001118 00000008 d packet_memb
000022b8 00000008 b packet_memb_memb_used
00004506 00000008 t pending_packet
0000ac5e 0000000a r CSWTCH.8
00001100 0000000a D cc2420_process
00001128 0000000a D ctimer_process
00001132 0000000a D etimer_process
00005820 0000000a T etimer_request_poll
00006308 0000000a T mac_sequence_init
00001192 0000000a D nullnet_example_process
00007312 0000000a T packetbuf_attr
000071b4 0000000a T packetbuf_hdrlen
00002228 0000000a D sensors_process
00002232 0000000a D serial_line_process
000065da 0000000a T splhigh_
0000a778 0000000a T srand
0000223c 0000000a D stack_check_process
000044fa 0000000c t cc2420_receiving_packet
00004f8a 0000000c T clock_delay
00002d32 0000000c b et.2069
00005968 0000000c T etimer_pending
00004f96 0000000c T init_platform
00006222 0000000c T linkaddr_set_node_addr
000062b8 0000000c T list_item_next
000065a4 0000000c T msp430_add_lpm_req
000071be 0000000c T packetbuf_dataptr
00007306 0000000c T packetbuf_set_attr
00007210 0000000c T packetbuf_totlen
00002548 0000000c b periodic_timer.3213
0000abb2 0000000e R csma_driver
0000595a 0000000e T etimer_expired
0000615e 0000000e T leds_arch_init
00006650 0000000e T netstack_init
00007346 0000000e T packetbuf_holds_broadcast
000075b4 0000000e T process_alloc_event
0000766c 0000000e T process_nevents
000078a6 0000000e T rtimer_arch_init
000078b4 0000000e T rtimer_arch_now
00002c0e 00000010 b bufmem_memb_mem
000053de 00000010 T csma_security_create_frame
000055cc 00000010 T ctimer_set
000062a8 00000010 T list_length
0000ab8e 00000010 r output_power
00002e22 00000010 B packetbuf_addrs
00009ecc 00000010 T printf
00007ce0 00000010 T putchar
00004784 00000012 t cc2420_send
00005948 00000012 T etimer_reset
00005936 00000012 T etimer_set
000061f6 00000012 T leds_off
000061e4 00000012 T leds_on
00006210 00000012 T linkaddr_cmp
00006238 00000012 T list_tail
00007334 00000012 T packetbuf_addr
00007280 00000012 T packetbuf_clear
00007354 00000012 T platform_init_stage_one
000076bc 00000012 T process_post_synch
0000771c 00000012 T queuebuf_init
00007780 00000012 T queuebuf_update_attr_from_packetbuf
00007eb0 00000012 T watchdog_init
00007e88 00000012 T watchdog_periodic
0000643e 00000014 T mac_call_sent_callback
0000665e 00000014 T node_id_init
000077fa 00000014 T ringbuf_init
00002d40 00000014 b rxdma_timer
00007e74 00000014 T watchdog_start
0000420c 00000016 T autostart_start
00004a52 00000016 T cc2420_interrupt
00004c1c 00000016 T cc2420_set_cca_threshold
00005974 00000016 T etimer_next_expiration_time
00007e9a 00000016 T watchdog_stop
00005566 00000018 T ctimer_init
00006312 00000018 T mac_sequence_set_dsn
00002e32 00000018 B packetbuf_attrs
0000731c 00000018 T packetbuf_set_addr
000075c2 00000018 T process_init
00007704 00000018 T process_poll
00004612 00000018 t set_key
00004222 00000018 t status
00007d2a 00000018 T uart1_active
00007d62 00000018 T uart1_writeb
00004332 0000001a T cc2420_arch_init
00004f48 0000001a T clock_time
000053c4 0000001a T csma_output_init
000045a8 0000001a t flushrx
000044e0 0000001a t on
00007188 0000001a T packetbuf_hdrreduce
0000ab64 0000001c R cc2420_driver
00007ac6 0000001c T serial_line_init
00009f38 0000001c T sprintf
00004354 0000001c t strobe
00007cc4 0000001c T timer_reset
00007c7e 0000001c T timer_set
00004a94 0000001e T cc2420_get_txpower
00002434 00000020 B A
0000ffe0 00000020 T __ivtbl_16
00004312 00000020 T cc2420_port1_interrupt
000044c0 00000020 t get_status
0000549e 00000020 t init
00007d42 00000020 T uart1_set_input
0000423a 00000020 t value
00009edc 00000022 t append
000046fc 00000022 T cc2420_on
000072c0 00000022 T packetbuf_attr_copyto
0000450e 00000022 t wait_for_transmission
000072e2 00000024 T packetbuf_attr_copyfrom
000042ec 00000026 T cc2420_timerb1_interrupt
0000a752 00000026 T rand
000078ce 00000026 T rtimer_run_next
000045ea 00000028 t RELEASE_LOCK
00004f62 00000028 T clock_init
0000560c 00000028 T ctimer_stop
00005b5a 00000028 T frame802154_is_broadcast_addr
000045c2 00000028 t off
00007258 00000028 T packetbuf_attr_clear
00004530 00000028 t wait_for_status
0000627e 0000002a T list_add
000064f8 0000002a T memb_inmemb
000065b0 0000002a T msp430_cpu_init
0000aee4 0000002a R nullrouting_driver
00007792 0000002a T queuebuf_free
000079b6 0000002a T sensors_changed
00007c9a 0000002a T timer_expired
00004a68 0000002c T cc2420_set_txpower
0000a726 0000002c T puts
0000468a 0000002c t set_poll_mode
00007292 0000002e T packetbuf_copyfrom
00007b12 0000002e T stack_check_init
00007878 0000002e T timera0
00004796 00000030 T cc2420_off
000055dc 00000030 T ctimer_reset
00007584 00000030 t do_poll
0000a782 00000030 T memcmp
000022f8 00000030 b metadata_memb_memb_mem
000022c0 00000030 b packet_memb_memb_mem
0000465a 00000030 t set_auto_ack
0000462a 00000030 t set_frame_filtering
00007ae2 00000030 T spi_init
00005b82 00000032 T frame802154_hdrlen
000064c6 00000032 T memb_free
000077bc 00000032 T queuebuf_to_packetbuf
00007846 00000032 T ringbuf_get
0000616c 00000034 T leds_arch_get
0000624a 00000034 T list_remove
00006452 00000036 T memb_init
000076ce 00000036 T process_start
00005400 00000038 t max_payload
0000780e 00000038 T ringbuf_put
00009efe 0000003a t call_vuprintf
00007cf0 0000003a t handle_rxdma_timer
000049ca 0000003c T cc2420_set_channel
0000721c 0000003c T packetbuf_hdralloc
00004484 0000003c t write_fifo_buf
00007ec2 0000003c T xmem_init
0000598a 0000003e T etimer_stop
000061a0 0000003e T leds_arch_set
00006488 0000003e T memb_alloc
000058f6 00000040 t add_timer
00007102 00000040 t input
00008e34 00000042 T __fixunssfsi
000070c0 00000042 t output
0000767a 00000042 T process_post
00007a84 00000042 T serial_line_input_byte
000062c4 00000044 T log_lladdr
000074a8 00000046 t call_process
000046b6 00000046 t cc2420_prepare
000042a6 00000046 T irq_p2
000071ca 00000046 T packetbuf_copyto
00002270 00000048 b neighbor_memb_memb_mem
0000935a 0000004c T __addsf3
00004ab2 0000004c T cc2420_rssi
00004a06 0000004c T cc2420_set_pan_addr
0000425a 0000004c t configure
00004370 0000004c t getreg
000043bc 0000004c t setreg
0000979c 0000004e T __gesf2
0000974e 0000004e T __gtsf2
00009838 0000004e T __lesf2
000097ea 0000004e T __ltsf2
0000113e 0000004e D all_modules
0000557e 0000004e T ctimer_set_with_process
000093a6 00000050 T __subsf3
00004558 00000050 t getrxdata
00005634 00000050 t owreadb
0000772e 00000052 T queuebuf_new_from_packetbuf
00007454 00000054 T platform_idle
00007b40 00000054 T stack_check_get_usage
000048ec 00000056 t process_thread_cc2420_process
0000543e 00000060 t input_packet
000014bc 00000064 D isAnchor10Percent
00001458 00000064 D isAnchor20Percent
000013f4 00000064 D isAnchor30Percent
00001390 00000064 D isAnchor40Percent
0000132c 00000064 D isAnchor50Percent
000012c8 00000064 D isAnchor60Percent
00001264 00000064 D isAnchor70Percent
00001200 00000064 D isAnchor80Percent
0000119c 00000064 D isAnchor90Percent
000021b4 00000064 D percentage10
00002150 00000064 D percentage20
000020ec 00000064 D percentage30
00002088 00000064 D percentage40
00002024 00000064 D percentage50
00001fc0 00000064 D percentage60
00001f5c 00000064 D percentage70
00001ef8 00000064 D percentage80
00001e94 00000064 D percentage90
0000471e 00000066 t cc2420_transmit
000047c6 00000068 t cc2420_cca
00007366 00000068 T platform_init_stage_two
0000a8ac 0000006a T memset
000065e4 0000006c T msp430_sync_dco
00004fa2 00000070 t schedule_transmission
00009aa0 00000072 T __clzsi2
000057a8 00000078 t update_time
00004408 0000007c t write_ram
00002c30 00000080 b buf.1991
0000255e 00000080 b packetbuf_aligned
00002d56 00000080 b rxbuf
00002cb0 00000080 b rxbuf_data
00006522 00000082 T msp430_init_dco
0000632a 00000084 T mac_sequence_is_duplicate
000073ce 00000086 T platform_init_stage_three
00004942 00000088 t encrypt
0000992e 0000008c T __fixsfsi
000063ae 00000090 T mac_sequence_register_seqno
000075da 00000092 T process_run
000074ee 00000096 t exit_process
00005bb4 00000096 T frame802154_create_fcf
00005012 0000009a t tx_done
000060ac 000000a2 t create_frame
00005f52 000000a2 t parse
00009e28 000000a4 T __fpcmp_parts_f
000079e0 000000a4 t process_thread_serial_line_process
00009886 000000a8 T __floatsisf
000054be 000000a8 t process_thread_ctimer_process
00005aae 000000ac t field_len
00005ff4 000000b8 T framer_802154_setup_params
00005d2e 000000bc T frame802154_parse_fcf
0000482e 000000be t cc2420_read
000025ee 000000c0 b events
000078f4 000000c2 t process_thread_sensors_process
00001dcc 000000c8 D AnchorIndexes
0000582a 000000cc t process_thread_etimer_process
00004e6c 000000dc T timera1
000059ce 000000e0 T frame802154_has_panid
0000234a 000000e0 b received_seqnos
00005c4a 000000e4 T frame802154_create
000099ba 000000e6 T __floatunsisf
00004d82 000000ea T cc2420_init
00007b94 000000ea t process_thread_stack_check_process
00002454 000000f2 B rssiList
00007d7a 000000f4 T uart1_init
0000a7b2 000000fa T memcpy
0000b0cc 00000100 R __clz_tab
00004afe 0000011e t get_value
00005684 00000120 T ds2411_init
00008e76 00000124 T __fixunssfdi
00009cec 0000013c T __unpack_f
00008f9a 0000013e T __floatundisf
00009606 00000148 T __divsf3
00004c32 00000150 t set_value
0000526c 00000158 T csma_output_packet
00005dea 00000168 T frame802154_parse
00008cc2 00000172 T __ieee754_sqrtf
00008b4e 00000174 T scalbnf
00009f54 00000194 t print_field
000050ac 000001c0 t transmit_from_queue
0000403e 000001c4 T main
00009b12 000001da T __pack_f
00006672 000001e4 t process_thread_nullnet_example_process
000093f6 00000210 T __mulsf3
000090d8 00000282 t _fpadd_parts
000019e4 000003e8 D node_positions
00001520 000004c4 D anchor_nodes
000026b6 00000550 b buframmem_memb_mem
0000a0e8 0000063e T vuprintf
00006856 00000864 T input_callback
00007efe 00000c4a T __ieee754_powfmsp430-objdump -f

user@409f9b5f2321:/work$ msp430-objdump -f nullnet-unicast.sky

nullnet-unicast.sky:     file format elf32-msp430
architecture: msp430:430, flags 0x00000112:
EXEC_P, HAS_SYMS, D_PAGED
start address 0x00004000msp430-objdump -d

user@113c3d69a7ba:/work$ msp430-objdump -d nullnet-unicast.sky


nullnet-unicast.sky:     file format elf32-msp430


Disassembly of section .text:

00004000 <__watchdog_support>:
    4000:	55 42 20 01 	mov.b	&0x0120,r5	
    4004:	35 d0 08 5a 	bis	#23048,	r5	;#0x5a08
    4008:	82 45 56 2e 	mov	r5,	&0x2e56	

0000400c <__init_stack>:
    400c:	31 40 00 39 	mov	#14592,	r1	;#0x3900

00004010 <__do_copy_data>:
    4010:	3f 40 4a 11 	mov	#4426,	r15	;#0x114a
    4014:	0f 93       	tst	r15		
    4016:	08 24       	jz	$+18     	;abs 0x4028
    4018:	92 42 56 2e 	mov	&0x2e56,&0x0120	
    401c:	20 01 
    401e:	2f 83       	decd	r15		
    4020:	9f 4f d4 b1 	mov	-20012(r15),4352(r15);0xb1d4(r15), 0x1100(r15)
    4024:	00 11 
    4026:	f8 23       	jnz	$-14     	;abs 0x4018

00004028 <__do_clear_bss>:
    4028:	3f 40 0c 0c 	mov	#3084,	r15	;#0x0c0c
    402c:	0f 93       	tst	r15		
    402e:	07 24       	jz	$+16     	;abs 0x403e
    4030:	92 42 56 2e 	mov	&0x2e56,&0x0120	
    4034:	20 01 
    4036:	1f 83       	dec	r15		
    4038:	cf 43 4a 22 	mov.b	#0,	8778(r15);r3 As==00, 0x224a(r15)
    403c:	f9 23       	jnz	$-12     	;abs 0x4030

0000403e <main>:
    403e:	b0 12 54 73 	call	#0x7354	
    4042:	b0 12 62 4f 	call	#0x4f62	
    4046:	b0 12 c8 78 	call	#0x78c8	
    404a:	b0 12 c2 75 	call	#0x75c2	
    404e:	0e 43       	clr	r14		
    4050:	3f 40 32 11 	mov	#4402,	r15	;#0x1132
    4054:	b0 12 ce 76 	call	#0x76ce	
    4058:	b0 12 66 55 	call	#0x5566	
    405c:	b0 12 b0 7e 	call	#0x7eb0	
    4060:	b0 12 a4 57 	call	#0x57a4	
    4064:	b0 12 12 7b 	call	#0x7b12	
    4068:	b0 12 66 73 	call	#0x7366	
    406c:	b0 12 1c 77 	call	#0x771c	
    4070:	b0 12 50 66 	call	#0x6650	
    4074:	b0 12 5e 66 	call	#0x665e	
    4078:	b2 90 03 00 	cmp	#3,	&0x118c	;#0x0003
    407c:	8c 11 
    407e:	0e 38       	jl	$+30     	;abs 0x409c
    4080:	30 12 2e af 	push	#-20690	;#0xaf2e
    4084:	30 12 33 af 	push	#-20685	;#0xaf33
    4088:	30 12 38 af 	push	#-20680	;#0xaf38
    408c:	b0 12 cc 9e 	call	#0x9ecc	
    4090:	31 50 06 00 	add	#6,	r1	;#0x0006
    4094:	3f 40 47 af 	mov	#-20665,r15	;#0xaf47
    4098:	b0 12 26 a7 	call	#0xa726	
    409c:	b2 90 03 00 	cmp	#3,	&0x118c	;#0x0003
    40a0:	8c 11 
    40a2:	11 38       	jl	$+36     	;abs 0x40c6
    40a4:	30 12 2e af 	push	#-20690	;#0xaf2e
    40a8:	30 12 33 af 	push	#-20685	;#0xaf33
    40ac:	30 12 38 af 	push	#-20680	;#0xaf38
    40b0:	b0 12 cc 9e 	call	#0x9ecc	
    40b4:	31 50 06 00 	add	#6,	r1	;#0x0006
    40b8:	12 12 e4 ae 	push	&0xaee4	
    40bc:	30 12 7d af 	push	#-20611	;#0xaf7d
    40c0:	b0 12 cc 9e 	call	#0x9ecc	
    40c4:	21 52       	add	#4,	r1	;r2 As==10
    40c6:	b2 90 03 00 	cmp	#3,	&0x118c	;#0x0003
    40ca:	8c 11 
    40cc:	11 38       	jl	$+36     	;abs 0x40f0
    40ce:	30 12 2e af 	push	#-20690	;#0xaf2e
    40d2:	30 12 33 af 	push	#-20685	;#0xaf33
    40d6:	30 12 38 af 	push	#-20680	;#0xaf38
    40da:	b0 12 cc 9e 	call	#0x9ecc	
    40de:	31 50 06 00 	add	#6,	r1	;#0x0006
    40e2:	12 12 d0 ae 	push	&0xaed0	
    40e6:	30 12 8c af 	push	#-20596	;#0xaf8c
    40ea:	b0 12 cc 9e 	call	#0x9ecc	
    40ee:	21 52       	add	#4,	r1	;r2 As==10
    40f0:	b2 90 03 00 	cmp	#3,	&0x118c	;#0x0003
    40f4:	8c 11 
    40f6:	11 38       	jl	$+36     	;abs 0x411a
    40f8:	30 12 2e af 	push	#-20690	;#0xaf2e
    40fc:	30 12 33 af 	push	#-20685	;#0xaf33
    4100:	30 12 38 af 	push	#-20680	;#0xaf38
    4104:	b0 12 cc 9e 	call	#0x9ecc	
    4108:	31 50 06 00 	add	#6,	r1	;#0x0006
    410c:	12 12 b2 ab 	push	&0xabb2	
    4110:	30 12 97 af 	push	#-20585	;#0xaf97
    4114:	b0 12 cc 9e 	call	#0x9ecc	
    4118:	21 52       	add	#4,	r1	;r2 As==10
    411a:	b2 90 03 00 	cmp	#3,	&0x118c	;#0x0003
    411e:	8c 11 
    4120:	11 38       	jl	$+36     	;abs 0x4144
    4122:	30 12 2e af 	push	#-20690	;#0xaf2e
    4126:	30 12 33 af 	push	#-20685	;#0xaf33
    412a:	30 12 38 af 	push	#-20680	;#0xaf38
    412e:	b0 12 cc 9e 	call	#0x9ecc	
    4132:	31 50 06 00 	add	#6,	r1	;#0x0006
    4136:	30 12 cd ab 	push	#-21555	;#0xabcd
    413a:	30 12 a2 af 	push	#-20574	;#0xafa2
    413e:	b0 12 cc 9e 	call	#0x9ecc	
    4142:	21 52       	add	#4,	r1	;r2 As==10
    4144:	b2 90 03 00 	cmp	#3,	&0x118c	;#0x0003
    4148:	8c 11 
    414a:	11 38       	jl	$+36     	;abs 0x416e
    414c:	30 12 2e af 	push	#-20690	;#0xaf2e
    4150:	30 12 33 af 	push	#-20685	;#0xaf33
    4154:	30 12 38 af 	push	#-20680	;#0xaf38
    4158:	b0 12 cc 9e 	call	#0x9ecc	
    415c:	31 50 06 00 	add	#6,	r1	;#0x0006
    4160:	30 12 1a 00 	push	#26		;#0x001a
    4164:	30 12 bc af 	push	#-20548	;#0xafbc
    4168:	b0 12 cc 9e 	call	#0x9ecc	
    416c:	21 52       	add	#4,	r1	;r2 As==10
    416e:	b2 90 03 00 	cmp	#3,	&0x118c	;#0x0003
    4172:	8c 11 
    4174:	11 38       	jl	$+36     	;abs 0x4198
    4176:	30 12 2e af 	push	#-20690	;#0xaf2e
    417a:	30 12 33 af 	push	#-20685	;#0xaf33
    417e:	30 12 38 af 	push	#-20680	;#0xaf38
    4182:	b0 12 cc 9e 	call	#0x9ecc	
    4186:	31 50 06 00 	add	#6,	r1	;#0x0006
    418a:	12 12 2a 24 	push	&0x242a	
    418e:	30 12 dc af 	push	#-20516	;#0xafdc
    4192:	b0 12 cc 9e 	call	#0x9ecc	
    4196:	21 52       	add	#4,	r1	;r2 As==10
    4198:	b2 90 03 00 	cmp	#3,	&0x118c	;#0x0003
    419c:	8c 11 
    419e:	0f 38       	jl	$+32     	;abs 0x41be
    41a0:	30 12 2e af 	push	#-20690	;#0xaf2e
    41a4:	30 12 33 af 	push	#-20685	;#0xaf33
    41a8:	30 12 38 af 	push	#-20680	;#0xaf38
    41ac:	b0 12 cc 9e 	call	#0x9ecc	
    41b0:	31 50 06 00 	add	#6,	r1	;#0x0006
    41b4:	30 12 e9 af 	push	#-20503	;#0xafe9
    41b8:	b0 12 cc 9e 	call	#0x9ecc	
    41bc:	21 53       	incd	r1		
    41be:	b2 90 03 00 	cmp	#3,	&0x118c	;#0x0003
    41c2:	8c 11 
    41c4:	04 38       	jl	$+10     	;abs 0x41ce
    41c6:	3f 40 ea 2d 	mov	#11754,	r15	;#0x2dea
    41ca:	b0 12 c4 62 	call	#0x62c4	
    41ce:	b2 90 03 00 	cmp	#3,	&0x118c	;#0x0003
    41d2:	8c 11 
    41d4:	04 38       	jl	$+10     	;abs 0x41de
    41d6:	3f 40 0a 00 	mov	#10,	r15	;#0x000a
    41da:	b0 12 e0 7c 	call	#0x7ce0	
    41de:	b0 12 ce 73 	call	#0x73ce	
    41e2:	3f 40 94 ae 	mov	#-20844,r15	;#0xae94
    41e6:	b0 12 0c 42 	call	#0x420c	
    41ea:	b0 12 74 7e 	call	#0x7e74	
    41ee:	b0 12 da 75 	call	#0x75da	
    41f2:	0b 4f       	mov	r15,	r11	
    41f4:	b0 12 88 7e 	call	#0x7e88	
    41f8:	4b 93       	tst.b	r11		
    41fa:	f9 23       	jnz	$-12     	;abs 0x41ee
    41fc:	b0 12 54 74 	call	#0x7454	
    4200:	f6 3f       	jmp	$-18     	;abs 0x41ee

00004202 <__stop_progExec__>:
    4202:	32 d0 f0 00 	bis	#240,	r2	;#0x00f0
    4206:	fd 3f       	jmp	$-4      	;abs 0x4202

00004208 <__ctors_end>:
    4208:	30 40 16 a9 	br	#0xa916	

0000420c <autostart_start>:
    420c:	0b 12       	push	r11		
    420e:	0b 4f       	mov	r15,	r11	
    4210:	03 3c       	jmp	$+8      	;abs 0x4218
    4212:	0e 43       	clr	r14		
    4214:	b0 12 ce 76 	call	#0x76ce	
    4218:	3f 4b       	mov	@r11+,	r15	
    421a:	0f 93       	tst	r15		
    421c:	fa 23       	jnz	$-10     	;abs 0x4212
    421e:	3b 41       	pop	r11		
    4220:	30 41       	ret			

00004222 <status>:
    4222:	3f 50 7f ff 	add	#-129,	r15	;#0xff7f
    4226:	2f 93       	cmp	#2,	r15	;r3 As==10
    4228:	06 2c       	jc	$+14     	;abs 0x4236
    422a:	5f 42 2d 00 	mov.b	&0x002d,r15	
    422e:	7f f0 80 ff 	and.b	#-128,	r15	;#0xff80
    4232:	4f 4f       	mov.b	r15,	r15	
    4234:	30 41       	ret			
    4236:	0f 43       	clr	r15		
    4238:	30 41       	ret			

0000423a <value>:
    423a:	5f 42 28 00 	mov.b	&0x0028,r15	
    423e:	4f 93       	tst.b	r15		
    4240:	0a 38       	jl	$+22     	;abs 0x4256
    4242:	3f 40 4a 22 	mov	#8778,	r15	;#0x224a
    4246:	b0 12 9a 7c 	call	#0x7c9a	
    424a:	1e 43       	mov	#1,	r14	;r3 As==01
    424c:	0f 93       	tst	r15		
    424e:	01 24       	jz	$+4      	;abs 0x4252
    4250:	0e 43       	clr	r14		
    4252:	0f 4e       	mov	r14,	r15	
    4254:	30 41       	ret			
    4256:	1f 43       	mov	#1,	r15	;r3 As==01
    4258:	30 41       	ret			

0000425a <configure>:
    425a:	3f 90 81 00 	cmp	#129,	r15	;#0x0081
    425e:	1f 20       	jnz	$+64     	;abs 0x429e
    4260:	5f 42 2d 00 	mov.b	&0x002d,r15	
    4264:	0e 93       	tst	r14		
    4266:	16 24       	jz	$+46     	;abs 0x4294
    4268:	4f 93       	tst.b	r15		
    426a:	1b 38       	jl	$+56     	;abs 0x42a2
    426c:	0d 43       	clr	r13		
    426e:	0e 43       	clr	r14		
    4270:	3f 40 4a 22 	mov	#8778,	r15	;#0x224a
    4274:	b0 12 7e 7c 	call	#0x7c7e	
    4278:	f2 d0 80 ff 	bis.b	#-128,	&0x002c	;#0xff80
    427c:	2c 00 
    427e:	f2 f0 7f 00 	and.b	#127,	&0x002e	;#0x007f
    4282:	2e 00 
    4284:	f2 f0 7f 00 	and.b	#127,	&0x002a	;#0x007f
    4288:	2a 00 
    428a:	5f 42 2d 00 	mov.b	&0x002d,r15	
    428e:	7f d0 80 ff 	bis.b	#-128,	r15	;#0xff80
    4292:	02 3c       	jmp	$+6      	;abs 0x4298
    4294:	7f f0 7f 00 	and.b	#127,	r15	;#0x007f
    4298:	c2 4f 2d 00 	mov.b	r15,	&0x002d	
    429c:	02 3c       	jmp	$+6      	;abs 0x42a2
    429e:	0f 43       	clr	r15		
    42a0:	30 41       	ret			
    42a2:	1f 43       	mov	#1,	r15	;r3 As==01
    42a4:	30 41       	ret			

000042a6 <irq_p2>:
    42a6:	0f 12       	push	r15		
    42a8:	0e 12       	push	r14		
    42aa:	0d 12       	push	r13		
    42ac:	0c 12       	push	r12		
    42ae:	5f 42 2b 00 	mov.b	&0x002b,r15	
    42b2:	4f 93       	tst.b	r15		
    42b4:	14 34       	jge	$+42     	;abs 0x42de
    42b6:	3f 40 4a 22 	mov	#8778,	r15	;#0x224a
    42ba:	b0 12 9a 7c 	call	#0x7c9a	
    42be:	0f 93       	tst	r15		
    42c0:	0e 24       	jz	$+30     	;abs 0x42de
    42c2:	3d 40 20 00 	mov	#32,	r13	;#0x0020
    42c6:	0e 43       	clr	r14		
    42c8:	3f 40 4a 22 	mov	#8778,	r15	;#0x224a
    42cc:	b0 12 7e 7c 	call	#0x7c7e	
    42d0:	3f 40 58 ab 	mov	#-21672,r15	;#0xab58
    42d4:	b0 12 b6 79 	call	#0x79b6	
    42d8:	b1 c0 f0 00 	bic	#240,	8(r1)	;#0x00f0, 0x0008(r1)
    42dc:	08 00 
    42de:	c2 43 2b 00 	mov.b	#0,	&0x002b	;r3 As==00
    42e2:	3c 41       	pop	r12		
    42e4:	3d 41       	pop	r13		
    42e6:	3e 41       	pop	r14		
    42e8:	3f 41       	pop	r15		
    42ea:	00 13       	reti			

000042ec <cc2420_timerb1_interrupt>:
    42ec:	0f 12       	push	r15		
    42ee:	1f 42 1e 01 	mov	&0x011e,r15	
    42f2:	e2 b3 1c 00 	bit.b	#2,	&0x001c	;r3 As==10
    42f6:	06 24       	jz	$+14     	;abs 0x4304
    42f8:	d2 53 e6 2d 	inc.b	&0x2de6	
    42fc:	92 42 94 01 	mov	&0x0194,&0x2de0	
    4300:	e0 2d 
    4302:	05 3c       	jmp	$+12     	;abs 0x430e
    4304:	c2 43 e6 2d 	mov.b	#0,	&0x2de6	;r3 As==00
    4308:	92 42 94 01 	mov	&0x0194,&0x2de8	
    430c:	e8 2d 
    430e:	3f 41       	pop	r15		
    4310:	00 13       	reti			

00004312 <cc2420_port1_interrupt>:
    4312:	0f 12       	push	r15		
    4314:	0e 12       	push	r14		
    4316:	0d 12       	push	r13		
    4318:	0c 12       	push	r12		
    431a:	b0 12 52 4a 	call	#0x4a52	
    431e:	0f 93       	tst	r15		
    4320:	03 24       	jz	$+8      	;abs 0x4328
    4322:	b1 c0 f0 00 	bic	#240,	8(r1)	;#0x00f0, 0x0008(r1)
    4326:	08 00 
    4328:	3c 41       	pop	r12		
    432a:	3d 41       	pop	r13		
    432c:	3e 41       	pop	r14		
    432e:	3f 41       	pop	r15		
    4330:	00 13       	reti			

00004332 <cc2420_arch_init>:
    4332:	b0 12 e2 7a 	call	#0x7ae2	
    4336:	e2 d2 1e 00 	bis.b	#4,	&0x001e	;r2 As==10
    433a:	f2 d0 20 00 	bis.b	#32,	&0x001e	;#0x0020
    433e:	1e 00 
    4340:	f2 d0 40 00 	bis.b	#64,	&0x001e	;#0x0040
    4344:	1e 00 
    4346:	e2 d2 1d 00 	bis.b	#4,	&0x001d	;r2 As==10
    434a:	30 41       	ret			

0000434c <get_object>:
    434c:	1f 43       	mov	#1,	r15	;r3 As==01
    434e:	30 41       	ret			

00004350 <set_object>:
    4350:	1f 43       	mov	#1,	r15	;r3 As==01
    4352:	30 41       	ret			

00004354 <strobe>:
    4354:	e2 c2 1d 00 	bic.b	#4,	&0x001d	;r2 As==10
    4358:	5e 42 02 00 	mov.b	&0x0002,r14	
    435c:	4e 93       	tst.b	r14		
    435e:	fc 37       	jge	$-6      	;abs 0x4358
    4360:	c2 4f 77 00 	mov.b	r15,	&0x0077	
    4364:	d2 b3 71 00 	bit.b	#1,	&0x0071	;r3 As==01
    4368:	fd 27       	jz	$-4      	;abs 0x4364
    436a:	e2 d2 1d 00 	bis.b	#4,	&0x001d	;r2 As==10
    436e:	30 41       	ret			

00004370 <getreg>:
    4370:	e2 c2 1d 00 	bic.b	#4,	&0x001d	;r2 As==10
    4374:	5e 42 02 00 	mov.b	&0x0002,r14	
    4378:	4e 93       	tst.b	r14		
    437a:	fc 37       	jge	$-6      	;abs 0x4374
    437c:	3f d0 40 00 	bis	#64,	r15	;#0x0040
    4380:	c2 4f 77 00 	mov.b	r15,	&0x0077	
    4384:	d2 b3 71 00 	bit.b	#1,	&0x0071	;r3 As==01
    4388:	fd 27       	jz	$-4      	;abs 0x4384
    438a:	5f 42 76 00 	mov.b	&0x0076,r15	
    438e:	c2 43 77 00 	mov.b	#0,	&0x0077	;r3 As==00
    4392:	f2 b0 40 00 	bit.b	#64,	&0x0002	;#0x0040
    4396:	02 00 
    4398:	fc 27       	jz	$-6      	;abs 0x4392
    439a:	5e 42 76 00 	mov.b	&0x0076,r14	
    439e:	4e 4e       	mov.b	r14,	r14	
    43a0:	8e 10       	swpb	r14		
    43a2:	c2 43 77 00 	mov.b	#0,	&0x0077	;r3 As==00
    43a6:	f2 b0 40 00 	bit.b	#64,	&0x0002	;#0x0040
    43aa:	02 00 
    43ac:	fc 27       	jz	$-6      	;abs 0x43a6
    43ae:	5f 42 76 00 	mov.b	&0x0076,r15	
    43b2:	e2 d2 1d 00 	bis.b	#4,	&0x001d	;r2 As==10
    43b6:	4f 4f       	mov.b	r15,	r15	
    43b8:	0f de       	bis	r14,	r15	
    43ba:	30 41       	ret			

000043bc <setreg>:
    43bc:	e2 c2 1d 00 	bic.b	#4,	&0x001d	;r2 As==10
    43c0:	5d 42 02 00 	mov.b	&0x0002,r13	
    43c4:	4d 93       	tst.b	r13		
    43c6:	fc 37       	jge	$-6      	;abs 0x43c0
    43c8:	c2 4f 77 00 	mov.b	r15,	&0x0077	
    43cc:	5f 42 02 00 	mov.b	&0x0002,r15	
    43d0:	4f 93       	tst.b	r15		
    43d2:	fc 37       	jge	$-6      	;abs 0x43cc
    43d4:	0f 4e       	mov	r14,	r15	
    43d6:	8f 10       	swpb	r15		
    43d8:	4f 4f       	mov.b	r15,	r15	
    43da:	c2 4f 77 00 	mov.b	r15,	&0x0077	
    43de:	5f 42 02 00 	mov.b	&0x0002,r15	
    43e2:	4f 93       	tst.b	r15		
    43e4:	fc 37       	jge	$-6      	;abs 0x43de
    43e6:	c2 4e 77 00 	mov.b	r14,	&0x0077	
    43ea:	d2 b3 71 00 	bit.b	#1,	&0x0071	;r3 As==01
    43ee:	fd 27       	jz	$-4      	;abs 0x43ea
    43f0:	5f 42 02 00 	mov.b	&0x0002,r15	
    43f4:	4f 93       	tst.b	r15		
    43f6:	fc 37       	jge	$-6      	;abs 0x43f0
    43f8:	c2 43 77 00 	mov.b	#0,	&0x0077	;r3 As==00
    43fc:	d2 b3 71 00 	bit.b	#1,	&0x0071	;r3 As==01
    4400:	fd 27       	jz	$-4      	;abs 0x43fc
    4402:	e2 d2 1d 00 	bis.b	#4,	&0x001d	;r2 As==10
    4406:	30 41       	ret			

00004408 <write_ram>:
    4408:	0b 12       	push	r11		
    440a:	e2 c2 1d 00 	bic.b	#4,	&0x001d	;r2 As==10
    440e:	5b 42 02 00 	mov.b	&0x0002,r11	
    4412:	4b 93       	tst.b	r11		
    4414:	fc 37       	jge	$-6      	;abs 0x440e
    4416:	0b 4e       	mov	r14,	r11	
    4418:	3b d0 80 00 	bis	#128,	r11	;#0x0080
    441c:	c2 4b 77 00 	mov.b	r11,	&0x0077	
    4420:	5b 42 02 00 	mov.b	&0x0002,r11	
    4424:	4b 93       	tst.b	r11		
    4426:	fc 37       	jge	$-6      	;abs 0x4420
    4428:	12 c3       	clrc			
    442a:	0e 10       	rrc	r14		
    442c:	3e f0 c0 00 	and	#192,	r14	;#0x00c0
    4430:	c2 4e 77 00 	mov.b	r14,	&0x0077	
    4434:	0c 93       	tst	r12		
    4436:	0a 24       	jz	$+22     	;abs 0x444c
    4438:	0e 3c       	jmp	$+30     	;abs 0x4456
    443a:	5b 42 02 00 	mov.b	&0x0002,r11	
    443e:	4b 93       	tst.b	r11		
    4440:	fc 37       	jge	$-6      	;abs 0x443a
    4442:	0c 5f       	add	r15,	r12	
    4444:	e2 4c 77 00 	mov.b	@r12,	&0x0077	
    4448:	5e 53       	inc.b	r14		
    444a:	01 3c       	jmp	$+4      	;abs 0x444e
    444c:	4e 43       	clr.b	r14		
    444e:	4c 4e       	mov.b	r14,	r12	
    4450:	0c 9d       	cmp	r13,	r12	
    4452:	f3 2b       	jnc	$-24     	;abs 0x443a
    4454:	10 3c       	jmp	$+34     	;abs 0x4476
    4456:	4d 4d       	mov.b	r13,	r13	
    4458:	0e 43       	clr	r14		
    445a:	0a 3c       	jmp	$+22     	;abs 0x4470
    445c:	5b 42 02 00 	mov.b	&0x0002,r11	
    4460:	4b 93       	tst.b	r11		
    4462:	fc 37       	jge	$-6      	;abs 0x445c
    4464:	4c 4c       	mov.b	r12,	r12	
    4466:	0c 5f       	add	r15,	r12	
    4468:	d2 4c ff ff 	mov.b	-1(r12),&0x0077	;0xffff(r12)
    446c:	77 00 
    446e:	1e 53       	inc	r14		
    4470:	4c 4d       	mov.b	r13,	r12	
    4472:	4c 8e       	sub.b	r14,	r12	
    4474:	f3 23       	jnz	$-24     	;abs 0x445c
    4476:	d2 b3 71 00 	bit.b	#1,	&0x0071	;r3 As==01
    447a:	fd 27       	jz	$-4      	;abs 0x4476
    447c:	e2 d2 1d 00 	bis.b	#4,	&0x001d	;r2 As==10
    4480:	3b 41       	pop	r11		
    4482:	30 41       	ret			

00004484 <write_fifo_buf>:
    4484:	0b 12       	push	r11		
    4486:	e2 c2 1d 00 	bic.b	#4,	&0x001d	;r2 As==10
    448a:	5d 42 02 00 	mov.b	&0x0002,r13	
    448e:	4d 93       	tst.b	r13		
    4490:	fc 37       	jge	$-6      	;abs 0x448a
    4492:	f2 40 3e 00 	mov.b	#62,	&0x0077	;#0x003e
    4496:	77 00 
    4498:	4d 43       	clr.b	r13		
    449a:	08 3c       	jmp	$+18     	;abs 0x44ac
    449c:	5b 42 02 00 	mov.b	&0x0002,r11	
    44a0:	4b 93       	tst.b	r11		
    44a2:	fc 37       	jge	$-6      	;abs 0x449c
    44a4:	0c 5f       	add	r15,	r12	
    44a6:	e2 4c 77 00 	mov.b	@r12,	&0x0077	
    44aa:	5d 53       	inc.b	r13		
    44ac:	4c 4d       	mov.b	r13,	r12	
    44ae:	0c 9e       	cmp	r14,	r12	
    44b0:	f5 2b       	jnc	$-20     	;abs 0x449c
    44b2:	d2 b3 71 00 	bit.b	#1,	&0x0071	;r3 As==01
    44b6:	fd 27       	jz	$-4      	;abs 0x44b2
    44b8:	e2 d2 1d 00 	bis.b	#4,	&0x001d	;r2 As==10
    44bc:	3b 41       	pop	r11		
    44be:	30 41       	ret			

000044c0 <get_status>:
    44c0:	e2 c2 1d 00 	bic.b	#4,	&0x001d	;r2 As==10
    44c4:	5f 42 02 00 	mov.b	&0x0002,r15	
    44c8:	4f 93       	tst.b	r15		
    44ca:	fc 37       	jge	$-6      	;abs 0x44c4
    44cc:	c2 43 77 00 	mov.b	#0,	&0x0077	;r3 As==00
    44d0:	d2 b3 71 00 	bit.b	#1,	&0x0071	;r3 As==01
    44d4:	fd 27       	jz	$-4      	;abs 0x44d0
    44d6:	5f 42 76 00 	mov.b	&0x0076,r15	
    44da:	e2 d2 1d 00 	bis.b	#4,	&0x001d	;r2 As==10
    44de:	30 41       	ret			

000044e0 <on>:
    44e0:	5f 42 52 22 	mov.b	&0x2252,r15	
    44e4:	4f 93       	tst.b	r15		
    44e6:	02 20       	jnz	$+6      	;abs 0x44ec
    44e8:	d2 d3 25 00 	bis.b	#1,	&0x0025	;r3 As==01
    44ec:	3f 40 03 00 	mov	#3,	r15	;#0x0003
    44f0:	b0 12 54 43 	call	#0x4354	
    44f4:	d2 43 59 22 	mov.b	#1,	&0x2259	;r3 As==01
    44f8:	30 41       	ret			

000044fa <cc2420_receiving_packet>:
    44fa:	5f 42 1c 00 	mov.b	&0x001c,r15	
    44fe:	12 c3       	clrc			
    4500:	4f 10       	rrc.b	r15		
    4502:	1f f3       	and	#1,	r15	;r3 As==01
    4504:	30 41       	ret			

00004506 <pending_packet>:
    4506:	5f 42 20 00 	mov.b	&0x0020,r15	
    450a:	1f f3       	and	#1,	r15	;r3 As==01
    450c:	30 41       	ret			

0000450e <wait_for_transmission>:
    450e:	0b 12       	push	r11		
    4510:	b0 12 b4 78 	call	#0x78b4	
    4514:	3b 40 34 f3 	mov	#-3276,	r11	;#0xf334
    4518:	0b 8f       	sub	r15,	r11	
    451a:	b0 12 c0 44 	call	#0x44c0	
    451e:	7f f2       	and.b	#8,	r15	;r2 As==11
    4520:	05 24       	jz	$+12     	;abs 0x452c
    4522:	b0 12 b4 78 	call	#0x78b4	
    4526:	0f 5b       	add	r11,	r15	
    4528:	0f 93       	tst	r15		
    452a:	f7 3b       	jl	$-16     	;abs 0x451a
    452c:	3b 41       	pop	r11		
    452e:	30 41       	ret			

00004530 <wait_for_status>:
    4530:	0b 12       	push	r11		
    4532:	0a 12       	push	r10		
    4534:	4a 4f       	mov.b	r15,	r10	
    4536:	b0 12 b4 78 	call	#0x78b4	
    453a:	3b 40 34 f3 	mov	#-3276,	r11	;#0xf334
    453e:	0b 8f       	sub	r15,	r11	
    4540:	b0 12 c0 44 	call	#0x44c0	
    4544:	4f ba       	bit.b	r10,	r15	
    4546:	05 20       	jnz	$+12     	;abs 0x4552
    4548:	b0 12 b4 78 	call	#0x78b4	
    454c:	0f 5b       	add	r11,	r15	
    454e:	0f 93       	tst	r15		
    4550:	f7 3b       	jl	$-16     	;abs 0x4540
    4552:	3a 41       	pop	r10		
    4554:	3b 41       	pop	r11		
    4556:	30 41       	ret			

00004558 <getrxdata>:
    4558:	0b 12       	push	r11		
    455a:	e2 c2 1d 00 	bic.b	#4,	&0x001d	;r2 As==10
    455e:	5d 42 02 00 	mov.b	&0x0002,r13	
    4562:	4d 93       	tst.b	r13		
    4564:	fc 37       	jge	$-6      	;abs 0x455e
    4566:	f2 40 7f 00 	mov.b	#127,	&0x0077	;#0x007f
    456a:	77 00 
    456c:	d2 b3 71 00 	bit.b	#1,	&0x0071	;r3 As==01
    4570:	fd 27       	jz	$-4      	;abs 0x456c
    4572:	5d 42 76 00 	mov.b	&0x0076,r13	
    4576:	4d 43       	clr.b	r13		
    4578:	0d 3c       	jmp	$+28     	;abs 0x4594
    457a:	c2 43 77 00 	mov.b	#0,	&0x0077	;r3 As==00
    457e:	f2 b0 40 00 	bit.b	#64,	&0x0002	;#0x0040
    4582:	02 00 
    4584:	fc 27       	jz	$-6      	;abs 0x457e
    4586:	5b 42 76 00 	mov.b	&0x0076,r11	
    458a:	4c 4d       	mov.b	r13,	r12	
    458c:	0c 5f       	add	r15,	r12	
    458e:	cc 4b 00 00 	mov.b	r11,	0(r12)	;0x0000(r12)
    4592:	5d 53       	inc.b	r13		
    4594:	4c 4d       	mov.b	r13,	r12	
    4596:	0c 9e       	cmp	r14,	r12	
    4598:	f0 3b       	jl	$-30     	;abs 0x457a
    459a:	1f 43       	mov	#1,	r15	;r3 As==01
    459c:	b0 12 8a 4f 	call	#0x4f8a	
    45a0:	e2 d2 1d 00 	bis.b	#4,	&0x001d	;r2 As==10
    45a4:	3b 41       	pop	r11		
    45a6:	30 41       	ret			

000045a8 <flushrx>:
    45a8:	21 83       	decd	r1		
    45aa:	1e 43       	mov	#1,	r14	;r3 As==01
    45ac:	0f 41       	mov	r1,	r15	
    45ae:	b0 12 58 45 	call	#0x4558	
    45b2:	3f 42       	mov	#8,	r15	;r2 As==11
    45b4:	b0 12 54 43 	call	#0x4354	
    45b8:	3f 42       	mov	#8,	r15	;r2 As==11
    45ba:	b0 12 54 43 	call	#0x4354	
    45be:	21 53       	incd	r1		
    45c0:	30 41       	ret			

000045c2 <off>:
    45c2:	c2 43 59 22 	mov.b	#0,	&0x2259	;r3 As==00
    45c6:	b0 12 0e 45 	call	#0x450e	
    45ca:	3f 40 06 00 	mov	#6,	r15	;#0x0006
    45ce:	b0 12 54 43 	call	#0x4354	
    45d2:	5f 42 52 22 	mov.b	&0x2252,r15	
    45d6:	4f 93       	tst.b	r15		
    45d8:	02 20       	jnz	$+6      	;abs 0x45de
    45da:	d2 c3 25 00 	bic.b	#1,	&0x0025	;r3 As==01
    45de:	d2 b3 20 00 	bit.b	#1,	&0x0020	;r3 As==01
    45e2:	02 20       	jnz	$+6      	;abs 0x45e8
    45e4:	b0 12 a8 45 	call	#0x45a8	
    45e8:	30 41       	ret			

000045ea <RELEASE_LOCK>:
    45ea:	d2 93 56 22 	cmp.b	#1,	&0x2256	;r3 As==01
    45ee:	0e 20       	jnz	$+30     	;abs 0x460c
    45f0:	c2 93 57 22 	tst.b	&0x2257	
    45f4:	04 24       	jz	$+10     	;abs 0x45fe
    45f6:	b0 12 e0 44 	call	#0x44e0	
    45fa:	c2 43 57 22 	mov.b	#0,	&0x2257	;r3 As==00
    45fe:	c2 93 58 22 	tst.b	&0x2258	
    4602:	04 24       	jz	$+10     	;abs 0x460c
    4604:	b0 12 c2 45 	call	#0x45c2	
    4608:	c2 43 58 22 	mov.b	#0,	&0x2258	;r3 As==00
    460c:	f2 53 56 22 	add.b	#-1,	&0x2256	;r3 As==11
    4610:	30 41       	ret			

00004612 <set_key>:
    4612:	d2 53 56 22 	inc.b	&0x2256	
    4616:	1c 43       	mov	#1,	r12	;r3 As==01
    4618:	3d 40 10 00 	mov	#16,	r13	;#0x0010
    461c:	3e 40 00 01 	mov	#256,	r14	;#0x0100
    4620:	b0 12 08 44 	call	#0x4408	
    4624:	b0 12 ea 45 	call	#0x45ea	
    4628:	30 41       	ret			

0000462a <set_frame_filtering>:
    462a:	0b 12       	push	r11		
    462c:	4b 4f       	mov.b	r15,	r11	
    462e:	d2 53 56 22 	inc.b	&0x2256	
    4632:	3f 40 11 00 	mov	#17,	r15	;#0x0011
    4636:	b0 12 70 43 	call	#0x4370	
    463a:	0e 4f       	mov	r15,	r14	
    463c:	4b 93       	tst.b	r11		
    463e:	03 24       	jz	$+8      	;abs 0x4646
    4640:	3e d0 00 08 	bis	#2048,	r14	;#0x0800
    4644:	02 3c       	jmp	$+6      	;abs 0x464a
    4646:	3e f0 ff f7 	and	#-2049,	r14	;#0xf7ff
    464a:	3f 40 11 00 	mov	#17,	r15	;#0x0011
    464e:	b0 12 bc 43 	call	#0x43bc	
    4652:	b0 12 ea 45 	call	#0x45ea	
    4656:	3b 41       	pop	r11		
    4658:	30 41       	ret			

0000465a <set_auto_ack>:
    465a:	0b 12       	push	r11		
    465c:	4b 4f       	mov.b	r15,	r11	
    465e:	d2 53 56 22 	inc.b	&0x2256	
    4662:	3f 40 11 00 	mov	#17,	r15	;#0x0011
    4666:	b0 12 70 43 	call	#0x4370	
    466a:	0e 4f       	mov	r15,	r14	
    466c:	4b 93       	tst.b	r11		
    466e:	03 24       	jz	$+8      	;abs 0x4676
    4670:	3e d0 10 00 	bis	#16,	r14	;#0x0010
    4674:	02 3c       	jmp	$+6      	;abs 0x467a
    4676:	3e f0 ef ff 	and	#-17,	r14	;#0xffef
    467a:	3f 40 11 00 	mov	#17,	r15	;#0x0011
    467e:	b0 12 bc 43 	call	#0x43bc	
    4682:	b0 12 ea 45 	call	#0x45ea	
    4686:	3b 41       	pop	r11		
    4688:	30 41       	ret			

0000468a <set_poll_mode>:
    468a:	d2 53 56 22 	inc.b	&0x2256	
    468e:	c2 4f 52 22 	mov.b	r15,	&0x2252	
    4692:	4f 93       	tst.b	r15		
    4694:	05 24       	jz	$+12     	;abs 0x46a0
    4696:	d2 c3 23 00 	bic.b	#1,	&0x0023	;r3 As==01
    469a:	d2 c3 25 00 	bic.b	#1,	&0x0025	;r3 As==01
    469e:	08 3c       	jmp	$+18     	;abs 0x46b0
    46a0:	d2 c3 24 00 	bic.b	#1,	&0x0024	;r3 As==01
    46a4:	d2 c3 23 00 	bic.b	#1,	&0x0023	;r3 As==01
    46a8:	d2 d3 25 00 	bis.b	#1,	&0x0025	;r3 As==01
    46ac:	d2 c3 23 00 	bic.b	#1,	&0x0023	;r3 As==01
    46b0:	b0 12 ea 45 	call	#0x45ea	
    46b4:	30 41       	ret			

000046b6 <cc2420_prepare>:
    46b6:	0b 12       	push	r11		
    46b8:	0a 12       	push	r10		
    46ba:	21 83       	decd	r1		
    46bc:	0a 4f       	mov	r15,	r10	
    46be:	0b 4e       	mov	r14,	r11	
    46c0:	3e 90 7e 00 	cmp	#126,	r14	;#0x007e
    46c4:	16 2c       	jc	$+46     	;abs 0x46f2
    46c6:	d2 53 56 22 	inc.b	&0x2256	
    46ca:	3f 40 09 00 	mov	#9,	r15	;#0x0009
    46ce:	b0 12 54 43 	call	#0x4354	
    46d2:	4f 4b       	mov.b	r11,	r15	
    46d4:	6f 53       	incd.b	r15		
    46d6:	c1 4f 00 00 	mov.b	r15,	0(r1)	;0x0000(r1)
    46da:	1e 43       	mov	#1,	r14	;r3 As==01
    46dc:	0f 41       	mov	r1,	r15	
    46de:	b0 12 84 44 	call	#0x4484	
    46e2:	0e 4b       	mov	r11,	r14	
    46e4:	0f 4a       	mov	r10,	r15	
    46e6:	b0 12 84 44 	call	#0x4484	
    46ea:	b0 12 ea 45 	call	#0x45ea	
    46ee:	0f 43       	clr	r15		
    46f0:	01 3c       	jmp	$+4      	;abs 0x46f4
    46f2:	1f 43       	mov	#1,	r15	;r3 As==01
    46f4:	21 53       	incd	r1		
    46f6:	3a 41       	pop	r10		
    46f8:	3b 41       	pop	r11		
    46fa:	30 41       	ret			

000046fc <cc2420_on>:
    46fc:	c2 93 59 22 	tst.b	&0x2259	
    4700:	0c 20       	jnz	$+26     	;abs 0x471a
    4702:	c2 93 56 22 	tst.b	&0x2256	
    4706:	03 24       	jz	$+8      	;abs 0x470e
    4708:	d2 43 57 22 	mov.b	#1,	&0x2257	;r3 As==01
    470c:	06 3c       	jmp	$+14     	;abs 0x471a
    470e:	d2 43 56 22 	mov.b	#1,	&0x2256	;r3 As==01
    4712:	b0 12 e0 44 	call	#0x44e0	
    4716:	b0 12 ea 45 	call	#0x45ea	
    471a:	1f 43       	mov	#1,	r15	;r3 As==01
    471c:	30 41       	ret			

0000471e <cc2420_transmit>:
    471e:	3f 90 7d 00 	cmp	#125,	r15	;#0x007d
    4722:	01 24       	jz	$+4      	;abs 0x4726
    4724:	2d 2c       	jc	$+92     	;abs 0x4780
    4726:	d2 53 56 22 	inc.b	&0x2256	
    472a:	c2 93 0a 11 	tst.b	&0x110a	
    472e:	0a 24       	jz	$+22     	;abs 0x4744
    4730:	3f 40 03 00 	mov	#3,	r15	;#0x0003
    4734:	b0 12 54 43 	call	#0x4354	
    4738:	6f 43       	mov.b	#2,	r15	;r3 As==10
    473a:	b0 12 30 45 	call	#0x4530	
    473e:	3f 40 05 00 	mov	#5,	r15	;#0x0005
    4742:	01 3c       	jmp	$+4      	;abs 0x4746
    4744:	2f 42       	mov	#4,	r15	;r2 As==10
    4746:	b0 12 54 43 	call	#0x4354	
    474a:	3f 40 20 03 	mov	#800,	r15	;#0x0320
    474e:	e2 b3 1c 00 	bit.b	#2,	&0x001c	;r3 As==10
    4752:	13 24       	jz	$+40     	;abs 0x477a
    4754:	b0 12 c0 44 	call	#0x44c0	
    4758:	7f f2       	and.b	#8,	r15	;r2 As==11
    475a:	04 20       	jnz	$+10     	;abs 0x4764
    475c:	b0 12 ea 45 	call	#0x45ea	
    4760:	2f 43       	mov	#2,	r15	;r3 As==10
    4762:	30 41       	ret			
    4764:	b0 12 0e 45 	call	#0x450e	
    4768:	c2 93 59 22 	tst.b	&0x2259	
    476c:	02 20       	jnz	$+6      	;abs 0x4772
    476e:	b0 12 c2 45 	call	#0x45c2	
    4772:	b0 12 ea 45 	call	#0x45ea	
    4776:	0f 43       	clr	r15		
    4778:	30 41       	ret			
    477a:	3f 53       	add	#-1,	r15	;r3 As==11
    477c:	e8 23       	jnz	$-46     	;abs 0x474e
    477e:	ee 3f       	jmp	$-34     	;abs 0x475c
    4780:	1f 43       	mov	#1,	r15	;r3 As==01
    4782:	30 41       	ret			

00004784 <cc2420_send>:
    4784:	0b 12       	push	r11		
    4786:	0b 4e       	mov	r14,	r11	
    4788:	b0 12 b6 46 	call	#0x46b6	
    478c:	0f 4b       	mov	r11,	r15	
    478e:	b0 12 1e 47 	call	#0x471e	
    4792:	3b 41       	pop	r11		
    4794:	30 41       	ret			

00004796 <cc2420_off>:
    4796:	c2 93 59 22 	tst.b	&0x2259	
    479a:	13 24       	jz	$+40     	;abs 0x47c2
    479c:	c2 93 56 22 	tst.b	&0x2256	
    47a0:	03 24       	jz	$+8      	;abs 0x47a8
    47a2:	d2 43 58 22 	mov.b	#1,	&0x2258	;r3 As==01
    47a6:	0d 3c       	jmp	$+28     	;abs 0x47c2
    47a8:	d2 43 56 22 	mov.b	#1,	&0x2256	;r3 As==01
    47ac:	b0 12 c0 44 	call	#0x44c0	
    47b0:	7f f2       	and.b	#8,	r15	;r2 As==11
    47b2:	03 24       	jz	$+8      	;abs 0x47ba
    47b4:	d2 43 58 22 	mov.b	#1,	&0x2258	;r3 As==01
    47b8:	02 3c       	jmp	$+6      	;abs 0x47be
    47ba:	b0 12 c2 45 	call	#0x45c2	
    47be:	b0 12 ea 45 	call	#0x45ea	
    47c2:	1f 43       	mov	#1,	r15	;r3 As==01
    47c4:	30 41       	ret			

000047c6 <cc2420_cca>:
    47c6:	0b 12       	push	r11		
    47c8:	0a 12       	push	r10		
    47ca:	c2 93 56 22 	tst.b	&0x2256	
    47ce:	01 24       	jz	$+4      	;abs 0x47d2
    47d0:	13 3c       	jmp	$+40     	;abs 0x47f8
    47d2:	d2 43 56 22 	mov.b	#1,	&0x2256	;r3 As==01
    47d6:	c2 93 59 22 	tst.b	&0x2259	
    47da:	04 20       	jnz	$+10     	;abs 0x47e4
    47dc:	b0 12 fc 46 	call	#0x46fc	
    47e0:	1a 43       	mov	#1,	r10	;r3 As==01
    47e2:	01 3c       	jmp	$+4      	;abs 0x47e6
    47e4:	0a 43       	clr	r10		
    47e6:	c2 93 59 22 	tst.b	&0x2259	
    47ea:	08 20       	jnz	$+18     	;abs 0x47fc
    47ec:	b0 12 ea 45 	call	#0x45ea	
    47f0:	0a 93       	tst	r10		
    47f2:	02 24       	jz	$+6      	;abs 0x47f8
    47f4:	b0 12 96 47 	call	#0x4796	
    47f8:	1b 43       	mov	#1,	r11	;r3 As==01
    47fa:	15 3c       	jmp	$+44     	;abs 0x4826
    47fc:	6f 43       	mov.b	#2,	r15	;r3 As==10
    47fe:	b0 12 30 45 	call	#0x4530	
    4802:	5f 42 20 00 	mov.b	&0x0020,r15	
    4806:	12 c3       	clrc			
    4808:	4f 10       	rrc.b	r15		
    480a:	12 c3       	clrc			
    480c:	4f 10       	rrc.b	r15		
    480e:	12 c3       	clrc			
    4810:	4f 10       	rrc.b	r15		
    4812:	12 c3       	clrc			
    4814:	4f 10       	rrc.b	r15		
    4816:	0b 4f       	mov	r15,	r11	
    4818:	1b f3       	and	#1,	r11	;r3 As==01
    481a:	0a 93       	tst	r10		
    481c:	02 24       	jz	$+6      	;abs 0x4822
    481e:	b0 12 96 47 	call	#0x4796	
    4822:	b0 12 ea 45 	call	#0x45ea	
    4826:	0f 4b       	mov	r11,	r15	
    4828:	3a 41       	pop	r10		
    482a:	3b 41       	pop	r11		
    482c:	30 41       	ret			

0000482e <cc2420_read>:
    482e:	0b 12       	push	r11		
    4830:	0a 12       	push	r10		
    4832:	21 82       	sub	#4,	r1	;r2 As==10
    4834:	0b 4f       	mov	r15,	r11	
    4836:	0a 4e       	mov	r14,	r10	
    4838:	d2 b3 20 00 	bit.b	#1,	&0x0020	;r3 As==01
    483c:	52 24       	jz	$+166    	;abs 0x48e2
    483e:	d2 53 56 22 	inc.b	&0x2256	
    4842:	1e 43       	mov	#1,	r14	;r3 As==01
    4844:	0f 41       	mov	r1,	r15	
    4846:	2f 53       	incd	r15		
    4848:	b0 12 58 45 	call	#0x4558	
    484c:	5d 41 02 00 	mov.b	2(r1),	r13	;0x0002(r1)
    4850:	4d 93       	tst.b	r13		
    4852:	43 38       	jl	$+136    	;abs 0x48da
    4854:	7d 90 03 00 	cmp.b	#3,	r13	;#0x0003
    4858:	40 28       	jnc	$+130    	;abs 0x48da
    485a:	4e 4d       	mov.b	r13,	r14	
    485c:	2e 83       	decd	r14		
    485e:	0a 9e       	cmp	r14,	r10	
    4860:	3c 28       	jnc	$+122    	;abs 0x48da
    4862:	0f 4b       	mov	r11,	r15	
    4864:	b0 12 58 45 	call	#0x4558	
    4868:	2e 43       	mov	#2,	r14	;r3 As==10
    486a:	0f 41       	mov	r1,	r15	
    486c:	b0 12 58 45 	call	#0x4558	
    4870:	5f 41 01 00 	mov.b	1(r1),	r15	;0x0001(r1)
    4874:	4f 93       	tst.b	r15		
    4876:	18 34       	jge	$+50     	;abs 0x48a8
    4878:	6e 41       	mov.b	@r1,	r14	
    487a:	7e 50 d3 ff 	add.b	#-45,	r14	;#0xffd3
    487e:	c2 4e de 2d 	mov.b	r14,	&0x2dde	
    4882:	7f f0 7f 00 	and.b	#127,	r15	;#0x007f
    4886:	c2 4f e2 2d 	mov.b	r15,	&0x2de2	
    488a:	5f 42 52 22 	mov.b	&0x2252,r15	
    488e:	4f 93       	tst.b	r15		
    4890:	0d 20       	jnz	$+28     	;abs 0x48ac
    4892:	8e 11       	sxt	r14		
    4894:	6f 42       	mov.b	#4,	r15	;r2 As==10
    4896:	b0 12 06 73 	call	#0x7306	
    489a:	5e 42 e2 2d 	mov.b	&0x2de2,r14	
    489e:	7f 40 03 00 	mov.b	#3,	r15	;#0x0003
    48a2:	b0 12 06 73 	call	#0x7306	
    48a6:	02 3c       	jmp	$+6      	;abs 0x48ac
    48a8:	e1 43 02 00 	mov.b	#2,	2(r1)	;r3 As==10, 0x0002(r1)
    48ac:	5f 42 52 22 	mov.b	&0x2252,r15	
    48b0:	4f 93       	tst.b	r15		
    48b2:	0d 20       	jnz	$+28     	;abs 0x48ce
    48b4:	d2 b3 20 00 	bit.b	#1,	&0x0020	;r3 As==01
    48b8:	0a 24       	jz	$+22     	;abs 0x48ce
    48ba:	f2 b2 20 00 	bit.b	#8,	&0x0020	;r2 As==11
    48be:	03 20       	jnz	$+8      	;abs 0x48c6
    48c0:	b0 12 a8 45 	call	#0x45a8	
    48c4:	04 3c       	jmp	$+10     	;abs 0x48ce
    48c6:	3f 40 00 11 	mov	#4352,	r15	;#0x1100
    48ca:	b0 12 04 77 	call	#0x7704	
    48ce:	b0 12 ea 45 	call	#0x45ea	
    48d2:	5f 41 02 00 	mov.b	2(r1),	r15	;0x0002(r1)
    48d6:	2f 83       	decd	r15		
    48d8:	05 3c       	jmp	$+12     	;abs 0x48e4
    48da:	b0 12 a8 45 	call	#0x45a8	
    48de:	b0 12 ea 45 	call	#0x45ea	
    48e2:	0f 43       	clr	r15		
    48e4:	21 52       	add	#4,	r1	;r2 As==10
    48e6:	3a 41       	pop	r10		
    48e8:	3b 41       	pop	r11		
    48ea:	30 41       	ret			

000048ec <process_thread_cc2420_process>:
    48ec:	0b 12       	push	r11		
    48ee:	0b 4f       	mov	r15,	r11	
    48f0:	2f 4f       	mov	@r15,	r15	
    48f2:	0f 93       	tst	r15		
    48f4:	04 24       	jz	$+10     	;abs 0x48fe
    48f6:	3f 90 81 03 	cmp	#897,	r15	;#0x0381
    48fa:	15 20       	jnz	$+44     	;abs 0x4926
    48fc:	1b 3c       	jmp	$+56     	;abs 0x4934
    48fe:	bb 40 81 03 	mov	#897,	0(r11)	;#0x0381, 0x0000(r11)
    4902:	00 00 
    4904:	15 3c       	jmp	$+44     	;abs 0x4930
    4906:	7e 90 82 ff 	cmp.b	#-126,	r14	;#0xff82
    490a:	12 20       	jnz	$+38     	;abs 0x4930
    490c:	b0 12 80 72 	call	#0x7280	
    4910:	b0 12 be 71 	call	#0x71be	
    4914:	3e 40 80 00 	mov	#128,	r14	;#0x0080
    4918:	b0 12 2e 48 	call	#0x482e	
    491c:	b0 12 a2 71 	call	#0x71a2	
    4920:	92 12 b8 ab 	call	&0xabb8	
    4924:	ec 3f       	jmp	$-38     	;abs 0x48fe
    4926:	8b 43 00 00 	mov	#0,	0(r11)	;r3 As==00, 0x0000(r11)
    492a:	7f 40 03 00 	mov.b	#3,	r15	;#0x0003
    492e:	07 3c       	jmp	$+16     	;abs 0x493e
    4930:	5f 43       	mov.b	#1,	r15	;r3 As==01
    4932:	05 3c       	jmp	$+12     	;abs 0x493e
    4934:	5f 42 52 22 	mov.b	&0x2252,r15	
    4938:	4f 93       	tst.b	r15		
    493a:	e5 27       	jz	$-52     	;abs 0x4906
    493c:	f9 3f       	jmp	$-12     	;abs 0x4930
    493e:	3b 41       	pop	r11		
    4940:	30 41       	ret			

00004942 <encrypt>:
    4942:	0b 12       	push	r11		
    4944:	0b 4f       	mov	r15,	r11	
    4946:	d2 53 56 22 	inc.b	&0x2256	
    494a:	0c 43       	clr	r12		
    494c:	3d 40 10 00 	mov	#16,	r13	;#0x0010
    4950:	3e 40 20 01 	mov	#288,	r14	;#0x0120
    4954:	b0 12 08 44 	call	#0x4408	
    4958:	3f 40 0e 00 	mov	#14,	r15	;#0x000e
    495c:	b0 12 54 43 	call	#0x4354	
    4960:	b0 12 c0 44 	call	#0x44c0	
    4964:	7f f0 10 00 	and.b	#16,	r15	;#0x0010
    4968:	fb 23       	jnz	$-8      	;abs 0x4960
    496a:	e2 c2 1d 00 	bic.b	#4,	&0x001d	;r2 As==10
    496e:	5f 42 02 00 	mov.b	&0x0002,r15	
    4972:	4f 93       	tst.b	r15		
    4974:	fc 37       	jge	$-6      	;abs 0x496e
    4976:	f2 40 a0 ff 	mov.b	#-96,	&0x0077	;#0xffa0
    497a:	77 00 
    497c:	d2 b3 71 00 	bit.b	#1,	&0x0071	;r3 As==01
    4980:	fd 27       	jz	$-4      	;abs 0x497c
    4982:	5f 42 02 00 	mov.b	&0x0002,r15	
    4986:	4f 93       	tst.b	r15		
    4988:	fc 37       	jge	$-6      	;abs 0x4982
    498a:	f2 40 a0 ff 	mov.b	#-96,	&0x0077	;#0xffa0
    498e:	77 00 
    4990:	d2 b3 71 00 	bit.b	#1,	&0x0071	;r3 As==01
    4994:	fd 27       	jz	$-4      	;abs 0x4990
    4996:	5f 42 76 00 	mov.b	&0x0076,r15	
    499a:	4e 43       	clr.b	r14		
    499c:	0c 3c       	jmp	$+26     	;abs 0x49b6
    499e:	c2 43 77 00 	mov.b	#0,	&0x0077	;r3 As==00
    49a2:	f2 b0 40 00 	bit.b	#64,	&0x0002	;#0x0040
    49a6:	02 00 
    49a8:	fc 27       	jz	$-6      	;abs 0x49a2
    49aa:	5d 42 76 00 	mov.b	&0x0076,r13	
    49ae:	0f 5b       	add	r11,	r15	
    49b0:	cf 4d 00 00 	mov.b	r13,	0(r15)	;0x0000(r15)
    49b4:	5e 53       	inc.b	r14		
    49b6:	4f 4e       	mov.b	r14,	r15	
    49b8:	7e 90 10 00 	cmp.b	#16,	r14	;#0x0010
    49bc:	f0 23       	jnz	$-30     	;abs 0x499e
    49be:	e2 d2 1d 00 	bis.b	#4,	&0x001d	;r2 As==10
    49c2:	b0 12 ea 45 	call	#0x45ea	
    49c6:	3b 41       	pop	r11		
    49c8:	30 41       	ret			

000049ca <cc2420_set_channel>:
    49ca:	0b 12       	push	r11		
    49cc:	0b 4f       	mov	r15,	r11	
    49ce:	d2 53 56 22 	inc.b	&0x2256	
    49d2:	82 4f 60 22 	mov	r15,	&0x2260	
    49d6:	b0 12 0e 45 	call	#0x450e	
    49da:	0e 4b       	mov	r11,	r14	
    49dc:	0e 5e       	rla	r14		
    49de:	0e 5e       	rla	r14		
    49e0:	0e 5b       	add	r11,	r14	
    49e2:	3e 50 2e 41 	add	#16686,	r14	;#0x412e
    49e6:	3f 40 18 00 	mov	#24,	r15	;#0x0018
    49ea:	b0 12 bc 43 	call	#0x43bc	
    49ee:	c2 93 59 22 	tst.b	&0x2259	
    49f2:	04 24       	jz	$+10     	;abs 0x49fc
    49f4:	3f 40 03 00 	mov	#3,	r15	;#0x0003
    49f8:	b0 12 54 43 	call	#0x4354	
    49fc:	b0 12 ea 45 	call	#0x45ea	
    4a00:	1f 43       	mov	#1,	r15	;r3 As==01
    4a02:	3b 41       	pop	r11		
    4a04:	30 41       	ret			

00004a06 <cc2420_set_pan_addr>:
    4a06:	0b 12       	push	r11		
    4a08:	21 82       	sub	#4,	r1	;r2 As==10
    4a0a:	81 4f 00 00 	mov	r15,	0(r1)	;0x0000(r1)
    4a0e:	81 4e 02 00 	mov	r14,	2(r1)	;0x0002(r1)
    4a12:	0b 4d       	mov	r13,	r11	
    4a14:	d2 53 56 22 	inc.b	&0x2256	
    4a18:	0c 43       	clr	r12		
    4a1a:	2d 43       	mov	#2,	r13	;r3 As==10
    4a1c:	3e 40 68 01 	mov	#360,	r14	;#0x0168
    4a20:	0f 41       	mov	r1,	r15	
    4a22:	b0 12 08 44 	call	#0x4408	
    4a26:	0c 43       	clr	r12		
    4a28:	2d 43       	mov	#2,	r13	;r3 As==10
    4a2a:	3e 40 6a 01 	mov	#362,	r14	;#0x016a
    4a2e:	0f 41       	mov	r1,	r15	
    4a30:	2f 53       	incd	r15		
    4a32:	b0 12 08 44 	call	#0x4408	
    4a36:	0b 93       	tst	r11		
    4a38:	07 24       	jz	$+16     	;abs 0x4a48
    4a3a:	1c 43       	mov	#1,	r12	;r3 As==01
    4a3c:	3d 42       	mov	#8,	r13	;r2 As==11
    4a3e:	3e 40 60 01 	mov	#352,	r14	;#0x0160
    4a42:	0f 4b       	mov	r11,	r15	
    4a44:	b0 12 08 44 	call	#0x4408	
    4a48:	b0 12 ea 45 	call	#0x45ea	
    4a4c:	21 52       	add	#4,	r1	;r2 As==10
    4a4e:	3b 41       	pop	r11		
    4a50:	30 41       	ret			

00004a52 <cc2420_interrupt>:
    4a52:	d2 c3 23 00 	bic.b	#1,	&0x0023	;r3 As==01
    4a56:	3f 40 00 11 	mov	#4352,	r15	;#0x1100
    4a5a:	b0 12 04 77 	call	#0x7704	
    4a5e:	92 42 e0 2d 	mov	&0x2de0,&0x2254	
    4a62:	54 22 
    4a64:	1f 43       	mov	#1,	r15	;r3 As==01
    4a66:	30 41       	ret			

00004a68 <cc2420_set_txpower>:
    4a68:	0b 12       	push	r11		
    4a6a:	4b 4f       	mov.b	r15,	r11	
    4a6c:	d2 53 56 22 	inc.b	&0x2256	
    4a70:	3f 40 15 00 	mov	#21,	r15	;#0x0015
    4a74:	b0 12 70 43 	call	#0x4370	
    4a78:	3f f0 e0 ff 	and	#-32,	r15	;#0xffe0
    4a7c:	0e 4b       	mov	r11,	r14	
    4a7e:	3e f0 1f 00 	and	#31,	r14	;#0x001f
    4a82:	0e df       	bis	r15,	r14	
    4a84:	3f 40 15 00 	mov	#21,	r15	;#0x0015
    4a88:	b0 12 bc 43 	call	#0x43bc	
    4a8c:	b0 12 ea 45 	call	#0x45ea	
    4a90:	3b 41       	pop	r11		
    4a92:	30 41       	ret			

00004a94 <cc2420_get_txpower>:
    4a94:	0b 12       	push	r11		
    4a96:	d2 53 56 22 	inc.b	&0x2256	
    4a9a:	3f 40 15 00 	mov	#21,	r15	;#0x0015
    4a9e:	b0 12 70 43 	call	#0x4370	
    4aa2:	0b 4f       	mov	r15,	r11	
    4aa4:	b0 12 ea 45 	call	#0x45ea	
    4aa8:	0f 4b       	mov	r11,	r15	
    4aaa:	3f f0 1f 00 	and	#31,	r15	;#0x001f
    4aae:	3b 41       	pop	r11		
    4ab0:	30 41       	ret			

00004ab2 <cc2420_rssi>:
    4ab2:	0b 12       	push	r11		
    4ab4:	0a 12       	push	r10		
    4ab6:	c2 93 56 22 	tst.b	&0x2256	
    4aba:	1c 20       	jnz	$+58     	;abs 0x4af4
    4abc:	d2 43 56 22 	mov.b	#1,	&0x2256	;r3 As==01
    4ac0:	c2 93 59 22 	tst.b	&0x2259	
    4ac4:	04 20       	jnz	$+10     	;abs 0x4ace
    4ac6:	b0 12 fc 46 	call	#0x46fc	
    4aca:	1a 43       	mov	#1,	r10	;r3 As==01
    4acc:	01 3c       	jmp	$+4      	;abs 0x4ad0
    4ace:	0a 43       	clr	r10		
    4ad0:	6f 43       	mov.b	#2,	r15	;r3 As==10
    4ad2:	b0 12 30 45 	call	#0x4530	
    4ad6:	3f 40 13 00 	mov	#19,	r15	;#0x0013
    4ada:	b0 12 70 43 	call	#0x4370	
    4ade:	8f 11       	sxt	r15		
    4ae0:	0b 4f       	mov	r15,	r11	
    4ae2:	3b 50 d3 ff 	add	#-45,	r11	;#0xffd3
    4ae6:	0a 93       	tst	r10		
    4ae8:	02 24       	jz	$+6      	;abs 0x4aee
    4aea:	b0 12 96 47 	call	#0x4796	
    4aee:	b0 12 ea 45 	call	#0x45ea	
    4af2:	01 3c       	jmp	$+4      	;abs 0x4af6
    4af4:	0b 43       	clr	r11		
    4af6:	0f 4b       	mov	r11,	r15	
    4af8:	3a 41       	pop	r10		
    4afa:	3b 41       	pop	r11		
    4afc:	30 41       	ret			

00004afe <get_value>:
    4afe:	0b 12       	push	r11		
    4b00:	0a 12       	push	r10		
    4b02:	0b 4e       	mov	r14,	r11	
    4b04:	0e 93       	tst	r14		
    4b06:	84 24       	jz	$+266    	;abs 0x4c10
    4b08:	3f 90 19 00 	cmp	#25,	r15	;#0x0019
    4b0c:	83 2c       	jc	$+264    	;abs 0x4c14
    4b0e:	0f 5f       	rla	r15		
    4b10:	10 4f 0c ab 	br	-21748(r15)	;0xab0c(r15)
    4b14:	3f 40 12 00 	mov	#18,	r15	;#0x0012
    4b18:	b0 12 70 43 	call	#0x4370	
    4b1c:	3f f2       	and	#8,	r15	;r2 As==11
    4b1e:	03 24       	jz	$+8      	;abs 0x4b26
    4b20:	ab 43 00 00 	mov	#2,	0(r11)	;r3 As==10, 0x0000(r11)
    4b24:	07 3c       	jmp	$+16     	;abs 0x4b34
    4b26:	1f 43       	mov	#1,	r15	;r3 As==01
    4b28:	c2 93 59 22 	tst.b	&0x2259	
    4b2c:	01 20       	jnz	$+4      	;abs 0x4b30
    4b2e:	0f 43       	clr	r15		
    4b30:	8b 4f 00 00 	mov	r15,	0(r11)	;0x0000(r11)
    4b34:	0f 43       	clr	r15		
    4b36:	6f 3c       	jmp	$+224    	;abs 0x4c16
    4b38:	9e 42 60 22 	mov	&0x2260,0(r14)	;0x0000(r14)
    4b3c:	00 00 
    4b3e:	fa 3f       	jmp	$-10     	;abs 0x4b34
    4b40:	8e 43 00 00 	mov	#0,	0(r14)	;r3 As==00, 0x0000(r14)
    4b44:	3f 40 11 00 	mov	#17,	r15	;#0x0011
    4b48:	b0 12 70 43 	call	#0x4370	
    4b4c:	3f b0 00 08 	bit	#2048,	r15	;#0x0800
    4b50:	02 24       	jz	$+6      	;abs 0x4b56
    4b52:	9b d3 00 00 	bis	#1,	0(r11)	;r3 As==01, 0x0000(r11)
    4b56:	3f 40 11 00 	mov	#17,	r15	;#0x0011
    4b5a:	b0 12 70 43 	call	#0x4370	
    4b5e:	3f f0 10 00 	and	#16,	r15	;#0x0010
    4b62:	02 24       	jz	$+6      	;abs 0x4b68
    4b64:	ab d3 00 00 	bis	#2,	0(r11)	;r3 As==10, 0x0000(r11)
    4b68:	5f 42 52 22 	mov.b	&0x2252,r15	
    4b6c:	4f 93       	tst.b	r15		
    4b6e:	01 20       	jnz	$+4      	;abs 0x4b72
    4b70:	e1 3f       	jmp	$-60     	;abs 0x4b34
    4b72:	ab d2 00 00 	bis	#4,	0(r11)	;r2 As==10, 0x0000(r11)
    4b76:	de 3f       	jmp	$-66     	;abs 0x4b34
    4b78:	8e 43 00 00 	mov	#0,	0(r14)	;r3 As==00, 0x0000(r14)
    4b7c:	c2 93 0a 11 	tst.b	&0x110a	
    4b80:	d9 27       	jz	$-76     	;abs 0x4b34
    4b82:	9e 43 00 00 	mov	#1,	0(r14)	;r3 As==01, 0x0000(r14)
    4b86:	d6 3f       	jmp	$-82     	;abs 0x4b34
    4b88:	b0 12 94 4a 	call	#0x4a94	
    4b8c:	bb 40 e7 ff 	mov	#-25,	0(r11)	;#0xffe7, 0x0000(r11)
    4b90:	00 00 
    4b92:	0e 43       	clr	r14		
    4b94:	0d 4e       	mov	r14,	r13	
    4b96:	0d 5d       	rla	r13		
    4b98:	5c 4d 8f ab 	mov.b	-21617(r13),r12	;0xab8f(r13)
    4b9c:	0f 9c       	cmp	r12,	r15	
    4b9e:	04 38       	jl	$+10     	;abs 0x4ba8
    4ba0:	db 4d 8e ab 	mov.b	-21618(r13),0(r11)	;0xab8e(r13), 0x0000(r11)
    4ba4:	00 00 
    4ba6:	19 3c       	jmp	$+52     	;abs 0x4bda
    4ba8:	1e 53       	inc	r14		
    4baa:	3e 92       	cmp	#8,	r14	;r2 As==11
    4bac:	f3 23       	jnz	$-24     	;abs 0x4b94
    4bae:	c2 3f       	jmp	$-122    	;abs 0x4b34
    4bb0:	d2 53 56 22 	inc.b	&0x2256	
    4bb4:	3f 40 13 00 	mov	#19,	r15	;#0x0013
    4bb8:	b0 12 70 43 	call	#0x4370	
    4bbc:	0a 4f       	mov	r15,	r10	
    4bbe:	b0 12 ea 45 	call	#0x45ea	
    4bc2:	0f 4a       	mov	r10,	r15	
    4bc4:	8f 10       	swpb	r15		
    4bc6:	8f 11       	sxt	r15		
    4bc8:	3f 50 d3 ff 	add	#-45,	r15	;#0xffd3
    4bcc:	b1 3f       	jmp	$-156    	;abs 0x4b30
    4bce:	b0 12 b2 4a 	call	#0x4ab2	
    4bd2:	ae 3f       	jmp	$-162    	;abs 0x4b30
    4bd4:	de 42 de 2d 	mov.b	&0x2dde,0(r14)	;0x0000(r14)
    4bd8:	00 00 
    4bda:	ab 11       	sxt	@r11		
    4bdc:	ab 3f       	jmp	$-168    	;abs 0x4b34
    4bde:	de 42 e2 2d 	mov.b	&0x2de2,0(r14)	;0x0000(r14)
    4be2:	00 00 
    4be4:	ce 43 01 00 	mov.b	#0,	1(r14)	;r3 As==00, 0x0001(r14)
    4be8:	a5 3f       	jmp	$-180    	;abs 0x4b34
    4bea:	be 40 0b 00 	mov	#11,	0(r14)	;#0x000b, 0x0000(r14)
    4bee:	00 00 
    4bf0:	a1 3f       	jmp	$-188    	;abs 0x4b34
    4bf2:	be 40 1a 00 	mov	#26,	0(r14)	;#0x001a, 0x0000(r14)
    4bf6:	00 00 
    4bf8:	9d 3f       	jmp	$-196    	;abs 0x4b34
    4bfa:	be 40 e7 ff 	mov	#-25,	0(r14)	;#0xffe7, 0x0000(r14)
    4bfe:	00 00 
    4c00:	99 3f       	jmp	$-204    	;abs 0x4b34
    4c02:	8e 43 00 00 	mov	#0,	0(r14)	;r3 As==00, 0x0000(r14)
    4c06:	96 3f       	jmp	$-210    	;abs 0x4b34
    4c08:	be 40 7d 00 	mov	#125,	0(r14)	;#0x007d, 0x0000(r14)
    4c0c:	00 00 
    4c0e:	92 3f       	jmp	$-218    	;abs 0x4b34
    4c10:	2f 43       	mov	#2,	r15	;r3 As==10
    4c12:	01 3c       	jmp	$+4      	;abs 0x4c16
    4c14:	1f 43       	mov	#1,	r15	;r3 As==01
    4c16:	3a 41       	pop	r10		
    4c18:	3b 41       	pop	r11		
    4c1a:	30 41       	ret			

00004c1c <cc2420_set_cca_threshold>:
    4c1c:	d2 53 56 22 	inc.b	&0x2256	
    4c20:	4e 4f       	mov.b	r15,	r14	
    4c22:	8e 10       	swpb	r14		
    4c24:	3f 40 13 00 	mov	#19,	r15	;#0x0013
    4c28:	b0 12 bc 43 	call	#0x43bc	
    4c2c:	b0 12 ea 45 	call	#0x45ea	
    4c30:	30 41       	ret			

00004c32 <set_value>:
    4c32:	0b 12       	push	r11		
    4c34:	21 83       	decd	r1		
    4c36:	0b 4e       	mov	r14,	r11	
    4c38:	3f 92       	cmp	#8,	r15	;r2 As==11
    4c3a:	9d 2c       	jc	$+316    	;abs 0x4d76
    4c3c:	0f 5f       	rla	r15		
    4c3e:	10 4f 40 ab 	br	-21696(r15)	;0xab40(r15)
    4c42:	1e 93       	cmp	#1,	r14	;r3 As==01
    4c44:	03 20       	jnz	$+8      	;abs 0x4c4c
    4c46:	b0 12 fc 46 	call	#0x46fc	
    4c4a:	93 3c       	jmp	$+296    	;abs 0x4d72
    4c4c:	0e 93       	tst	r14		
    4c4e:	03 20       	jnz	$+8      	;abs 0x4c56
    4c50:	b0 12 96 47 	call	#0x4796	
    4c54:	8e 3c       	jmp	$+286    	;abs 0x4d72
    4c56:	0f 4e       	mov	r14,	r15	
    4c58:	2f 83       	decd	r15		
    4c5a:	2f 93       	cmp	#2,	r15	;r3 As==10
    4c5c:	8e 2c       	jc	$+286    	;abs 0x4d7a
    4c5e:	0e 41       	mov	r1,	r14	
    4c60:	0f 43       	clr	r15		
    4c62:	b0 12 fe 4a 	call	#0x4afe	
    4c66:	2b 93       	cmp	#2,	r11	;r3 As==10
    4c68:	27 20       	jnz	$+80     	;abs 0x4cb8
    4c6a:	2e 41       	mov	@r1,	r14	
    4c6c:	2e 93       	cmp	#2,	r14	;r3 As==10
    4c6e:	81 24       	jz	$+260    	;abs 0x4d72
    4c70:	5f 43       	mov.b	#1,	r15	;r3 As==01
    4c72:	1e 93       	cmp	#1,	r14	;r3 As==01
    4c74:	01 24       	jz	$+4      	;abs 0x4c78
    4c76:	4f 43       	clr.b	r15		
    4c78:	c2 4f 5a 22 	mov.b	r15,	&0x225a	
    4c7c:	b0 12 c2 45 	call	#0x45c2	
    4c80:	3f 40 12 00 	mov	#18,	r15	;#0x0012
    4c84:	b0 12 70 43 	call	#0x4370	
    4c88:	82 4f 5c 22 	mov	r15,	&0x225c	
    4c8c:	3e 40 0c 05 	mov	#1292,	r14	;#0x050c
    4c90:	3f 40 12 00 	mov	#18,	r15	;#0x0012
    4c94:	b0 12 bc 43 	call	#0x43bc	
    4c98:	3f 40 2e 00 	mov	#46,	r15	;#0x002e
    4c9c:	b0 12 70 43 	call	#0x4370	
    4ca0:	82 4f 5e 22 	mov	r15,	&0x225e	
    4ca4:	3e 40 00 18 	mov	#6144,	r14	;#0x1800
    4ca8:	3f 40 2e 00 	mov	#46,	r15	;#0x002e
    4cac:	b0 12 bc 43 	call	#0x43bc	
    4cb0:	2f 42       	mov	#4,	r15	;r2 As==10
    4cb2:	b0 12 54 43 	call	#0x4354	
    4cb6:	5d 3c       	jmp	$+188    	;abs 0x4d72
    4cb8:	a1 93 00 00 	cmp	#2,	0(r1)	;r3 As==10, 0x0000(r1)
    4cbc:	5a 20       	jnz	$+182    	;abs 0x4d72
    4cbe:	3f 40 06 00 	mov	#6,	r15	;#0x0006
    4cc2:	b0 12 54 43 	call	#0x4354	
    4cc6:	1e 42 5e 22 	mov	&0x225e,r14	
    4cca:	3f 40 2e 00 	mov	#46,	r15	;#0x002e
    4cce:	b0 12 bc 43 	call	#0x43bc	
    4cd2:	1e 42 5c 22 	mov	&0x225c,r14	
    4cd6:	3f 40 12 00 	mov	#18,	r15	;#0x0012
    4cda:	b0 12 bc 43 	call	#0x43bc	
    4cde:	c2 93 5a 22 	tst.b	&0x225a	
    4ce2:	47 24       	jz	$+144    	;abs 0x4d72
    4ce4:	b0 12 e0 44 	call	#0x44e0	
    4ce8:	44 3c       	jmp	$+138    	;abs 0x4d72
    4cea:	0f 4e       	mov	r14,	r15	
    4cec:	3f 50 f5 ff 	add	#-11,	r15	;#0xfff5
    4cf0:	3f 90 10 00 	cmp	#16,	r15	;#0x0010
    4cf4:	42 2c       	jc	$+134    	;abs 0x4d7a
    4cf6:	0f 4e       	mov	r14,	r15	
    4cf8:	b0 12 ca 49 	call	#0x49ca	
    4cfc:	3a 3c       	jmp	$+118    	;abs 0x4d72
    4cfe:	3e b0 f8 ff 	bit	#-8,	r14	;#0xfff8
    4d02:	3b 20       	jnz	$+120    	;abs 0x4d7a
    4d04:	4f 4e       	mov.b	r14,	r15	
    4d06:	5f f3       	and.b	#1,	r15	;r3 As==01
    4d08:	b0 12 2a 46 	call	#0x462a	
    4d0c:	12 c3       	clrc			
    4d0e:	0b 10       	rrc	r11		
    4d10:	4f 4b       	mov.b	r11,	r15	
    4d12:	5f f3       	and.b	#1,	r15	;r3 As==01
    4d14:	b0 12 5a 46 	call	#0x465a	
    4d18:	0f 4b       	mov	r11,	r15	
    4d1a:	12 c3       	clrc			
    4d1c:	0f 10       	rrc	r15		
    4d1e:	5f f3       	and.b	#1,	r15	;r3 As==01
    4d20:	b0 12 8a 46 	call	#0x468a	
    4d24:	26 3c       	jmp	$+78     	;abs 0x4d72
    4d26:	3e b0 fe ff 	bit	#-2,	r14	;#0xfffe
    4d2a:	27 20       	jnz	$+80     	;abs 0x4d7a
    4d2c:	5b f3       	and.b	#1,	r11	;r3 As==01
    4d2e:	c2 4b 0a 11 	mov.b	r11,	&0x110a	
    4d32:	1f 3c       	jmp	$+64     	;abs 0x4d72
    4d34:	0f 4e       	mov	r14,	r15	
    4d36:	3f 50 19 00 	add	#25,	r15	;#0x0019
    4d3a:	3f 90 1a 00 	cmp	#26,	r15	;#0x001a
    4d3e:	1d 2c       	jc	$+60     	;abs 0x4d7a
    4d40:	1f 43       	mov	#1,	r15	;r3 As==01
    4d42:	0e 4f       	mov	r15,	r14	
    4d44:	0e 5e       	rla	r14		
    4d46:	5e 4e 8e ab 	mov.b	-21618(r14),r14	;0xab8e(r14)
    4d4a:	8e 11       	sxt	r14		
    4d4c:	0e 9b       	cmp	r11,	r14	
    4d4e:	03 38       	jl	$+8      	;abs 0x4d56
    4d50:	1f 53       	inc	r15		
    4d52:	3f 92       	cmp	#8,	r15	;r2 As==11
    4d54:	f6 23       	jnz	$-18     	;abs 0x4d42
    4d56:	3f 53       	add	#-1,	r15	;r3 As==11
    4d58:	0f 5f       	rla	r15		
    4d5a:	3f 50 8e ab 	add	#-21618,r15	;#0xab8e
    4d5e:	5f 4f 01 00 	mov.b	1(r15),	r15	;0x0001(r15)
    4d62:	b0 12 68 4a 	call	#0x4a68	
    4d66:	05 3c       	jmp	$+12     	;abs 0x4d72
    4d68:	0f 4e       	mov	r14,	r15	
    4d6a:	3f 50 2d 00 	add	#45,	r15	;#0x002d
    4d6e:	b0 12 1c 4c 	call	#0x4c1c	
    4d72:	0f 43       	clr	r15		
    4d74:	03 3c       	jmp	$+8      	;abs 0x4d7c
    4d76:	1f 43       	mov	#1,	r15	;r3 As==01
    4d78:	01 3c       	jmp	$+4      	;abs 0x4d7c
    4d7a:	2f 43       	mov	#2,	r15	;r3 As==10
    4d7c:	21 53       	incd	r1		
    4d7e:	3b 41       	pop	r11		
    4d80:	30 41       	ret			

00004d82 <cc2420_init>:
    4d82:	0b 12       	push	r11		
    4d84:	b0 12 da 65 	call	#0x65da	
    4d88:	0b 4f       	mov	r15,	r11	
    4d8a:	b0 12 32 43 	call	#0x4332	
    4d8e:	d2 c3 25 00 	bic.b	#1,	&0x0025	;r3 As==01
    4d92:	d2 c3 24 00 	bic.b	#1,	&0x0024	;r3 As==01
    4d96:	d2 c3 23 00 	bic.b	#1,	&0x0023	;r3 As==01
    4d9a:	02 db       	bis	r11,	r2	
    4d9c:	f2 d0 20 00 	bis.b	#32,	&0x001d	;#0x0020
    4da0:	1d 00 
    4da2:	3f 40 fa 00 	mov	#250,	r15	;#0x00fa
    4da6:	b0 12 8a 4f 	call	#0x4f8a	
    4daa:	f2 f0 bf ff 	and.b	#-65,	&0x001d	;#0xffbf
    4dae:	1d 00 
    4db0:	3f 40 7f 00 	mov	#127,	r15	;#0x007f
    4db4:	b0 12 8a 4f 	call	#0x4f8a	
    4db8:	f2 d0 40 00 	bis.b	#64,	&0x001d	;#0x0040
    4dbc:	1d 00 
    4dbe:	3f 40 7d 00 	mov	#125,	r15	;#0x007d
    4dc2:	b0 12 8a 4f 	call	#0x4f8a	
    4dc6:	1f 43       	mov	#1,	r15	;r3 As==01
    4dc8:	b0 12 54 43 	call	#0x4354	
    4dcc:	7f 40 40 00 	mov.b	#64,	r15	;#0x0040
    4dd0:	b0 12 30 45 	call	#0x4530	
    4dd4:	5f 43       	mov.b	#1,	r15	;r3 As==01
    4dd6:	b0 12 5a 46 	call	#0x465a	
    4dda:	5f 43       	mov.b	#1,	r15	;r3 As==01
    4ddc:	b0 12 2a 46 	call	#0x462a	
    4de0:	3f 40 11 00 	mov	#17,	r15	;#0x0011
    4de4:	b0 12 70 43 	call	#0x4370	
    4de8:	0e 4f       	mov	r15,	r14	
    4dea:	3e d0 20 00 	bis	#32,	r14	;#0x0020
    4dee:	3f 40 11 00 	mov	#17,	r15	;#0x0011
    4df2:	b0 12 bc 43 	call	#0x43bc	
    4df6:	3e 40 00 05 	mov	#1280,	r14	;#0x0500
    4dfa:	3f 40 12 00 	mov	#18,	r15	;#0x0012
    4dfe:	b0 12 bc 43 	call	#0x43bc	
    4e02:	3f 40 17 00 	mov	#23,	r15	;#0x0017
    4e06:	b0 12 70 43 	call	#0x4370	
    4e0a:	0e 4f       	mov	r15,	r14	
    4e0c:	3e d0 00 20 	bis	#8192,	r14	;#0x2000
    4e10:	3f 40 17 00 	mov	#23,	r15	;#0x0017
    4e14:	b0 12 bc 43 	call	#0x43bc	
    4e18:	3e 40 7f 00 	mov	#127,	r14	;#0x007f
    4e1c:	3f 40 1c 00 	mov	#28,	r15	;#0x001c
    4e20:	b0 12 bc 43 	call	#0x43bc	
    4e24:	0e 43       	clr	r14		
    4e26:	3f 40 19 00 	mov	#25,	r15	;#0x0019
    4e2a:	b0 12 bc 43 	call	#0x43bc	
    4e2e:	0e 43       	clr	r14		
    4e30:	3f 40 1a 00 	mov	#26,	r15	;#0x001a
    4e34:	b0 12 bc 43 	call	#0x43bc	
    4e38:	0d 43       	clr	r13		
    4e3a:	0e 43       	clr	r14		
    4e3c:	3f 43       	mov	#-1,	r15	;r3 As==11
    4e3e:	b0 12 06 4a 	call	#0x4a06	
    4e42:	3f 40 1a 00 	mov	#26,	r15	;#0x001a
    4e46:	b0 12 ca 49 	call	#0x49ca	
    4e4a:	3f 40 d3 ff 	mov	#-45,	r15	;#0xffd3
    4e4e:	b0 12 1c 4c 	call	#0x4c1c	
    4e52:	b0 12 a8 45 	call	#0x45a8	
    4e56:	4f 43       	clr.b	r15		
    4e58:	b0 12 8a 46 	call	#0x468a	
    4e5c:	0e 43       	clr	r14		
    4e5e:	3f 40 00 11 	mov	#4352,	r15	;#0x1100
    4e62:	b0 12 ce 76 	call	#0x76ce	
    4e66:	1f 43       	mov	#1,	r15	;r3 As==01
    4e68:	3b 41       	pop	r11		
    4e6a:	30 41       	ret			

00004e6c <timera1>:
    4e6c:	0f 12       	push	r15		
    4e6e:	0e 12       	push	r14		
    4e70:	0d 12       	push	r13		
    4e72:	0c 12       	push	r12		
    4e74:	b0 12 74 7e 	call	#0x7e74	
    4e78:	1f 42 2e 01 	mov	&0x012e,r15	
    4e7c:	2f 93       	cmp	#2,	r15	;r3 As==10
    4e7e:	5d 20       	jnz	$+188    	;abs 0x4f3a
    4e80:	b2 b0 20 00 	bit	#32,	&0x0160	;#0x0020
    4e84:	60 01 
    4e86:	0b 24       	jz	$+24     	;abs 0x4e9e
    4e88:	1e 42 74 01 	mov	&0x0174,r14	
    4e8c:	1f 42 70 01 	mov	&0x0170,r15	
    4e90:	1d 42 70 01 	mov	&0x0170,r13	
    4e94:	0f 9d       	cmp	r13,	r15	
    4e96:	fa 23       	jnz	$-10     	;abs 0x4e8c
    4e98:	0e 8f       	sub	r15,	r14	
    4e9a:	1e 93       	cmp	#1,	r14	;r3 As==01
    4e9c:	f1 27       	jz	$-28     	;abs 0x4e80
    4e9e:	1f 42 70 01 	mov	&0x0170,r15	
    4ea2:	1e 42 70 01 	mov	&0x0170,r14	
    4ea6:	0f 9e       	cmp	r14,	r15	
    4ea8:	fa 23       	jnz	$-10     	;abs 0x4e9e
    4eaa:	2a 3c       	jmp	$+86     	;abs 0x4f00
    4eac:	b2 50 00 01 	add	#256,	&0x0174	;#0x0100
    4eb0:	74 01 
    4eb2:	1e 42 64 22 	mov	&0x2264,r14	
    4eb6:	1f 42 66 22 	mov	&0x2266,r15	
    4eba:	1e 53       	inc	r14		
    4ebc:	0f 63       	adc	r15		
    4ebe:	82 4e 64 22 	mov	r14,	&0x2264	
    4ec2:	82 4f 66 22 	mov	r15,	&0x2266	
    4ec6:	1e 42 64 22 	mov	&0x2264,r14	
    4eca:	1f 42 66 22 	mov	&0x2266,r15	
    4ece:	3e f0 7f 00 	and	#127,	r14	;#0x007f
    4ed2:	0f f3       	and	#0,	r15	;r3 As==00
    4ed4:	0e 93       	tst	r14		
    4ed6:	0e 20       	jnz	$+30     	;abs 0x4ef4
    4ed8:	0f 93       	tst	r15		
    4eda:	0c 20       	jnz	$+26     	;abs 0x4ef4
    4edc:	1e 42 68 22 	mov	&0x2268,r14	
    4ee0:	1f 42 6a 22 	mov	&0x226a,r15	
    4ee4:	1e 53       	inc	r14		
    4ee6:	0f 63       	adc	r15		
    4ee8:	82 4e 68 22 	mov	r14,	&0x2268	
    4eec:	82 4f 6a 22 	mov	r15,	&0x226a	
    4ef0:	b0 12 a6 57 	call	#0x57a6	
    4ef4:	1f 42 70 01 	mov	&0x0170,r15	
    4ef8:	1e 42 70 01 	mov	&0x0170,r14	
    4efc:	0f 9e       	cmp	r14,	r15	
    4efe:	fa 23       	jnz	$-10     	;abs 0x4ef4
    4f00:	82 4f 62 22 	mov	r15,	&0x2262	
    4f04:	1f 42 62 22 	mov	&0x2262,r15	
    4f08:	1f 82 74 01 	sub	&0x0174,r15	
    4f0c:	0f 93       	tst	r15		
    4f0e:	ce 37       	jge	$-98     	;abs 0x4eac
    4f10:	b0 12 68 59 	call	#0x5968	
    4f14:	0f 93       	tst	r15		
    4f16:	11 24       	jz	$+36     	;abs 0x4f3a
    4f18:	b0 12 74 59 	call	#0x5974	
    4f1c:	1c 42 64 22 	mov	&0x2264,r12	
    4f20:	1d 42 66 22 	mov	&0x2266,r13	
    4f24:	3c e3       	inv	r12		
    4f26:	3d e3       	inv	r13		
    4f28:	0c 5e       	add	r14,	r12	
    4f2a:	0d 6f       	addc	r15,	r13	
    4f2c:	0d 93       	tst	r13		
    4f2e:	05 34       	jge	$+12     	;abs 0x4f3a
    4f30:	b0 12 20 58 	call	#0x5820	
    4f34:	b1 c0 f0 00 	bic	#240,	8(r1)	;#0x00f0, 0x0008(r1)
    4f38:	08 00 
    4f3a:	b0 12 9a 7e 	call	#0x7e9a	
    4f3e:	3c 41       	pop	r12		
    4f40:	3d 41       	pop	r13		
    4f42:	3e 41       	pop	r14		
    4f44:	3f 41       	pop	r15		
    4f46:	00 13       	reti			

00004f48 <clock_time>:
    4f48:	1e 42 64 22 	mov	&0x2264,r14	
    4f4c:	1f 42 66 22 	mov	&0x2266,r15	
    4f50:	1c 42 64 22 	mov	&0x2264,r12	
    4f54:	1d 42 66 22 	mov	&0x2266,r13	
    4f58:	0e 9c       	cmp	r12,	r14	
    4f5a:	f6 23       	jnz	$-18     	;abs 0x4f48
    4f5c:	0f 9d       	cmp	r13,	r15	
    4f5e:	f4 23       	jnz	$-22     	;abs 0x4f48
    4f60:	30 41       	ret			

00004f62 <clock_init>:
    4f62:	32 c2       	dint			
    4f64:	03 43       	nop			
    4f66:	b2 40 04 01 	mov	#260,	&0x0160	;#0x0104
    4f6a:	60 01 
    4f6c:	b2 40 10 00 	mov	#16,	&0x0164	;#0x0010
    4f70:	64 01 
    4f72:	b2 40 00 01 	mov	#256,	&0x0174	;#0x0100
    4f76:	74 01 
    4f78:	b2 d0 20 00 	bis	#32,	&0x0160	;#0x0020
    4f7c:	60 01 
    4f7e:	82 43 64 22 	mov	#0,	&0x2264	;r3 As==00
    4f82:	82 43 66 22 	mov	#0,	&0x2266	;r3 As==00
    4f86:	32 d2       	eint			
    4f88:	30 41       	ret			

00004f8a <clock_delay>:
    4f8a:	02 3c       	jmp	$+6      	;abs 0x4f90
    4f8c:	03 43       	nop			
    4f8e:	3f 53       	add	#-1,	r15	;r3 As==11
    4f90:	0f 93       	tst	r15		
    4f92:	fc 23       	jnz	$-6      	;abs 0x4f8c
    4f94:	30 41       	ret			

00004f96 <init_platform>:
    4f96:	0e 43       	clr	r14		
    4f98:	3f 40 28 22 	mov	#8744,	r15	;#0x2228
    4f9c:	b0 12 ce 76 	call	#0x76ce	
    4fa0:	30 41       	ret			

00004fa2 <schedule_transmission>:
    4fa2:	0b 12       	push	r11		
    4fa4:	0a 12       	push	r10		
    4fa6:	09 12       	push	r9		
    4fa8:	09 4f       	mov	r15,	r9	
    4faa:	5e 4f 1f 00 	mov.b	31(r15),r14	;0x001f(r15)
    4fae:	2e 93       	cmp	#2,	r14	;r3 As==10
    4fb0:	03 34       	jge	$+8      	;abs 0x4fb8
    4fb2:	3e 50 03 00 	add	#3,	r14	;#0x0003
    4fb6:	02 3c       	jmp	$+6      	;abs 0x4fbc
    4fb8:	3e 40 05 00 	mov	#5,	r14	;#0x0005
    4fbc:	7e f0 0f 00 	and.b	#15,	r14	;#0x000f
    4fc0:	1a 43       	mov	#1,	r10	;r3 As==01
    4fc2:	4e 93       	tst.b	r14		
    4fc4:	03 24       	jz	$+8      	;abs 0x4fcc
    4fc6:	0a 5a       	rla	r10		
    4fc8:	7e 53       	add.b	#-1,	r14	;r3 As==11
    4fca:	fb 3f       	jmp	$-8      	;abs 0x4fc2
    4fcc:	3a 53       	add	#-1,	r10	;r3 As==11
    4fce:	0b 4a       	mov	r10,	r11	
    4fd0:	8b 10       	swpb	r11		
    4fd2:	8b 11       	sxt	r11		
    4fd4:	8b 10       	swpb	r11		
    4fd6:	8b 11       	sxt	r11		
    4fd8:	0e 4b       	mov	r11,	r14	
    4fda:	0a 93       	tst	r10		
    4fdc:	02 20       	jnz	$+6      	;abs 0x4fe2
    4fde:	0b 93       	tst	r11		
    4fe0:	0a 24       	jz	$+22     	;abs 0x4ff6
    4fe2:	b0 12 f4 77 	call	#0x77f4	
    4fe6:	0c 4a       	mov	r10,	r12	
    4fe8:	0d 4b       	mov	r11,	r13	
    4fea:	0e 4f       	mov	r15,	r14	
    4fec:	0f 43       	clr	r15		
    4fee:	b0 12 12 aa 	call	#0xaa12	
    4ff2:	0a 4e       	mov	r14,	r10	
    4ff4:	0e 4f       	mov	r15,	r14	
    4ff6:	09 12       	push	r9		
    4ff8:	3c 40 ac 50 	mov	#20652,	r12	;#0x50ac
    4ffc:	0d 4a       	mov	r10,	r13	
    4ffe:	0f 49       	mov	r9,	r15	
    5000:	3f 50 0a 00 	add	#10,	r15	;#0x000a
    5004:	b0 12 cc 55 	call	#0x55cc	
    5008:	21 53       	incd	r1		
    500a:	39 41       	pop	r9		
    500c:	3a 41       	pop	r10		
    500e:	3b 41       	pop	r11		
    5010:	30 41       	ret			

00005012 <tx_done>:
    5012:	0b 12       	push	r11		
    5014:	0a 12       	push	r10		
    5016:	09 12       	push	r9		
    5018:	08 12       	push	r8		
    501a:	07 12       	push	r7		
    501c:	06 12       	push	r6		
    501e:	07 4f       	mov	r15,	r7	
    5020:	0a 4e       	mov	r14,	r10	
    5022:	0b 4d       	mov	r13,	r11	
    5024:	1c 4e 04 00 	mov	4(r14),	r12	;0x0004(r14)
    5028:	29 4c       	mov	@r12,	r9	
    502a:	18 4c 02 00 	mov	2(r12),	r8	;0x0002(r12)
    502e:	56 4d 1e 00 	mov.b	30(r13),r6	;0x001e(r13)
    5032:	1f 4d 22 00 	mov	34(r13),r15	;0x0022(r13)
    5036:	b0 12 4a 62 	call	#0x624a	
    503a:	1f 4a 02 00 	mov	2(r10),	r15	;0x0002(r10)
    503e:	b0 12 92 77 	call	#0x7792	
    5042:	1e 4a 04 00 	mov	4(r10),	r14	;0x0004(r10)
    5046:	3f 40 20 11 	mov	#4384,	r15	;#0x1120
    504a:	b0 12 c6 64 	call	#0x64c6	
    504e:	0e 4a       	mov	r10,	r14	
    5050:	3f 40 18 11 	mov	#4376,	r15	;#0x1118
    5054:	b0 12 c6 64 	call	#0x64c6	
    5058:	1f 4b 22 00 	mov	34(r11),r15	;0x0022(r11)
    505c:	b0 12 34 62 	call	#0x6234	
    5060:	0f 93       	tst	r15		
    5062:	08 24       	jz	$+18     	;abs 0x5074
    5064:	cb 43 1e 00 	mov.b	#0,	30(r11)	;r3 As==00, 0x001e(r11)
    5068:	cb 43 1f 00 	mov.b	#0,	31(r11)	;r3 As==00, 0x001f(r11)
    506c:	0f 4b       	mov	r11,	r15	
    506e:	b0 12 a2 4f 	call	#0x4fa2	
    5072:	0f 3c       	jmp	$+32     	;abs 0x5092
    5074:	0f 4b       	mov	r11,	r15	
    5076:	3f 50 0a 00 	add	#10,	r15	;#0x000a
    507a:	b0 12 0c 56 	call	#0x560c	
    507e:	0e 4b       	mov	r11,	r14	
    5080:	3f 40 6c 22 	mov	#8812,	r15	;#0x226c
    5084:	b0 12 4a 62 	call	#0x624a	
    5088:	0e 4b       	mov	r11,	r14	
    508a:	3f 40 10 11 	mov	#4368,	r15	;#0x1110
    508e:	b0 12 c6 64 	call	#0x64c6	
    5092:	4c 46       	mov.b	r6,	r12	
    5094:	0d 47       	mov	r7,	r13	
    5096:	0e 48       	mov	r8,	r14	
    5098:	0f 49       	mov	r9,	r15	
    509a:	b0 12 3e 64 	call	#0x643e	
    509e:	36 41       	pop	r6		
    50a0:	37 41       	pop	r7		
    50a2:	38 41       	pop	r8		
    50a4:	39 41       	pop	r9		
    50a6:	3a 41       	pop	r10		
    50a8:	3b 41       	pop	r11		
    50aa:	30 41       	ret			

000050ac <transmit_from_queue>:
    50ac:	0b 12       	push	r11		
    50ae:	0a 12       	push	r10		
    50b0:	09 12       	push	r9		
    50b2:	08 12       	push	r8		
    50b4:	07 12       	push	r7		
    50b6:	21 82       	sub	#4,	r1	;r2 As==10
    50b8:	0b 4f       	mov	r15,	r11	
    50ba:	0f 93       	tst	r15		
    50bc:	d0 24       	jz	$+418    	;abs 0x525e
    50be:	1f 4f 22 00 	mov	34(r15),r15	;0x0022(r15)
    50c2:	b0 12 34 62 	call	#0x6234	
    50c6:	0a 4f       	mov	r15,	r10	
    50c8:	0f 93       	tst	r15		
    50ca:	c9 24       	jz	$+404    	;abs 0x525e
    50cc:	1f 4f 02 00 	mov	2(r15),	r15	;0x0002(r15)
    50d0:	b0 12 bc 77 	call	#0x77bc	
    50d4:	3e 40 ea 2d 	mov	#11754,	r14	;#0x2dea
    50d8:	7f 40 0c 00 	mov.b	#12,	r15	;#0x000c
    50dc:	b0 12 1c 73 	call	#0x731c	
    50e0:	1e 43       	mov	#1,	r14	;r3 As==01
    50e2:	7f 40 07 00 	mov.b	#7,	r15	;#0x0007
    50e6:	b0 12 06 73 	call	#0x7306	
    50ea:	b0 12 de 53 	call	#0x53de	
    50ee:	0f 93       	tst	r15		
    50f0:	b1 38       	jl	$+356    	;abs 0x5254
    50f2:	b0 12 a8 71 	call	#0x71a8	
    50f6:	57 4f 02 00 	mov.b	2(r15),	r7	;0x0002(r15)
    50fa:	b0 12 10 72 	call	#0x7210	
    50fe:	09 4f       	mov	r15,	r9	
    5100:	b0 12 a8 71 	call	#0x71a8	
    5104:	0e 49       	mov	r9,	r14	
    5106:	92 12 66 ab 	call	&0xab66	
    510a:	b0 12 46 73 	call	#0x7346	
    510e:	49 4f       	mov.b	r15,	r9	
    5110:	92 12 70 ab 	call	&0xab70	
    5114:	0f 93       	tst	r15		
    5116:	01 24       	jz	$+4      	;abs 0x511a
    5118:	51 3c       	jmp	$+164    	;abs 0x51bc
    511a:	49 49       	mov.b	r9,	r9	
    511c:	09 93       	tst	r9		
    511e:	09 24       	jz	$+20     	;abs 0x5132
    5120:	b0 12 10 72 	call	#0x7210	
    5124:	92 12 68 ab 	call	&0xab68	
    5128:	0f 93       	tst	r15		
    512a:	08 24       	jz	$+18     	;abs 0x513c
    512c:	2f 93       	cmp	#2,	r15	;r3 As==10
    512e:	95 20       	jnz	$+300    	;abs 0x525a
    5130:	45 3c       	jmp	$+140    	;abs 0x51bc
    5132:	92 12 72 ab 	call	&0xab72	
    5136:	0f 93       	tst	r15		
    5138:	41 20       	jnz	$+132    	;abs 0x51bc
    513a:	f2 3f       	jmp	$-26     	;abs 0x5120
    513c:	09 93       	tst	r9		
    513e:	40 20       	jnz	$+130    	;abs 0x51c0
    5140:	b0 12 b4 78 	call	#0x78b4	
    5144:	19 42 72 ab 	mov	&0xab72,r9	
    5148:	38 40 f3 ff 	mov	#-13,	r8	;#0xfff3
    514c:	08 8f       	sub	r15,	r8	
    514e:	89 12       	call	r9		
    5150:	0f 93       	tst	r15		
    5152:	05 24       	jz	$+12     	;abs 0x515e
    5154:	92 12 70 ab 	call	&0xab70	
    5158:	0f 93       	tst	r15		
    515a:	07 20       	jnz	$+16     	;abs 0x516a
    515c:	0c 3c       	jmp	$+26     	;abs 0x5176
    515e:	b0 12 b4 78 	call	#0x78b4	
    5162:	0f 58       	add	r8,	r15	
    5164:	0f 93       	tst	r15		
    5166:	f3 3b       	jl	$-24     	;abs 0x514e
    5168:	f5 3f       	jmp	$-20     	;abs 0x5154
    516a:	b0 12 b4 78 	call	#0x78b4	
    516e:	38 40 eb ff 	mov	#-21,	r8	;#0xffeb
    5172:	08 8f       	sub	r15,	r8	
    5174:	08 3c       	jmp	$+18     	;abs 0x5186
    5176:	89 12       	call	r9		
    5178:	0f 93       	tst	r15		
    517a:	f7 23       	jnz	$-16     	;abs 0x516a
    517c:	92 12 6e ab 	call	&0xab6e	
    5180:	0f 93       	tst	r15		
    5182:	f3 27       	jz	$-24     	;abs 0x516a
    5184:	06 3c       	jmp	$+14     	;abs 0x5192
    5186:	89 12       	call	r9		
    5188:	0f 93       	tst	r15		
    518a:	05 24       	jz	$+12     	;abs 0x5196
    518c:	89 12       	call	r9		
    518e:	0f 93       	tst	r15		
    5190:	08 20       	jnz	$+18     	;abs 0x51a2
    5192:	2f 43       	mov	#2,	r15	;r3 As==10
    5194:	16 3c       	jmp	$+46     	;abs 0x51c2
    5196:	b0 12 b4 78 	call	#0x78b4	
    519a:	0f 58       	add	r8,	r15	
    519c:	0f 93       	tst	r15		
    519e:	f3 3b       	jl	$-24     	;abs 0x5186
    51a0:	f5 3f       	jmp	$-20     	;abs 0x518c
    51a2:	3e 40 03 00 	mov	#3,	r14	;#0x0003
    51a6:	0f 41       	mov	r1,	r15	
    51a8:	92 12 6c ab 	call	&0xab6c	
    51ac:	3f 90 03 00 	cmp	#3,	r15	;#0x0003
    51b0:	05 20       	jnz	$+12     	;abs 0x51bc
    51b2:	1f 43       	mov	#1,	r15	;r3 As==01
    51b4:	c1 97 02 00 	cmp.b	r7,	2(r1)	;0x0002(r1)
    51b8:	04 20       	jnz	$+10     	;abs 0x51c2
    51ba:	02 3c       	jmp	$+6      	;abs 0x51c0
    51bc:	1f 43       	mov	#1,	r15	;r3 As==01
    51be:	01 3c       	jmp	$+4      	;abs 0x51c2
    51c0:	0f 43       	clr	r15		
    51c2:	1e 4a 04 00 	mov	4(r10),	r14	;0x0004(r10)
    51c6:	0e 93       	tst	r14		
    51c8:	4a 24       	jz	$+150    	;abs 0x525e
    51ca:	1f 93       	cmp	#1,	r15	;r3 As==01
    51cc:	21 24       	jz	$+68     	;abs 0x5210
    51ce:	2f 93       	cmp	#2,	r15	;r3 As==10
    51d0:	03 34       	jge	$+8      	;abs 0x51d8
    51d2:	0f 93       	tst	r15		
    51d4:	07 24       	jz	$+16     	;abs 0x51e4
    51d6:	39 3c       	jmp	$+116    	;abs 0x524a
    51d8:	2f 93       	cmp	#2,	r15	;r3 As==10
    51da:	0c 24       	jz	$+26     	;abs 0x51f4
    51dc:	3f 90 03 00 	cmp	#3,	r15	;#0x0003
    51e0:	34 20       	jnz	$+106    	;abs 0x524a
    51e2:	3d 3c       	jmp	$+124    	;abs 0x525e
    51e4:	cb 43 1f 00 	mov.b	#0,	31(r11)	;r3 As==00, 0x001f(r11)
    51e8:	db 53 1e 00 	inc.b	30(r11)	;0x001e(r11)
    51ec:	0d 4b       	mov	r11,	r13	
    51ee:	0e 4a       	mov	r10,	r14	
    51f0:	0f 43       	clr	r15		
    51f2:	2d 3c       	jmp	$+92     	;abs 0x524e
    51f4:	cb 43 1f 00 	mov.b	#0,	31(r11)	;r3 As==00, 0x001f(r11)
    51f8:	5f 4b 1e 00 	mov.b	30(r11),r15	;0x001e(r11)
    51fc:	5f 53       	inc.b	r15		
    51fe:	cb 4f 1e 00 	mov.b	r15,	30(r11)	;0x001e(r11)
    5202:	5f 9e 04 00 	cmp.b	4(r14),	r15	;0x0004(r14)
    5206:	19 28       	jnc	$+52     	;abs 0x523a
    5208:	0d 4b       	mov	r11,	r13	
    520a:	0e 4a       	mov	r10,	r14	
    520c:	2f 43       	mov	#2,	r15	;r3 As==10
    520e:	1f 3c       	jmp	$+64     	;abs 0x524e
    5210:	5f 4b 1f 00 	mov.b	31(r11),r15	;0x001f(r11)
    5214:	5f 53       	inc.b	r15		
    5216:	7f 90 06 00 	cmp.b	#6,	r15	;#0x0006
    521a:	03 2c       	jc	$+8      	;abs 0x5222
    521c:	cb 4f 1f 00 	mov.b	r15,	31(r11)	;0x001f(r11)
    5220:	04 3c       	jmp	$+10     	;abs 0x522a
    5222:	cb 43 1f 00 	mov.b	#0,	31(r11)	;r3 As==00, 0x001f(r11)
    5226:	db 53 1e 00 	inc.b	30(r11)	;0x001e(r11)
    522a:	db 9e 04 00 	cmp.b	4(r14),	30(r11)	;0x0004(r14), 0x001e(r11)
    522e:	1e 00 
    5230:	04 28       	jnc	$+10     	;abs 0x523a
    5232:	0d 4b       	mov	r11,	r13	
    5234:	0e 4a       	mov	r10,	r14	
    5236:	1f 43       	mov	#1,	r15	;r3 As==01
    5238:	0a 3c       	jmp	$+22     	;abs 0x524e
    523a:	0f 4b       	mov	r11,	r15	
    523c:	b0 12 a2 4f 	call	#0x4fa2	
    5240:	1f 4a 02 00 	mov	2(r10),	r15	;0x0002(r10)
    5244:	b0 12 80 77 	call	#0x7780	
    5248:	0a 3c       	jmp	$+22     	;abs 0x525e
    524a:	0d 4b       	mov	r11,	r13	
    524c:	0e 4a       	mov	r10,	r14	
    524e:	b0 12 12 50 	call	#0x5012	
    5252:	05 3c       	jmp	$+12     	;abs 0x525e
    5254:	3f 40 05 00 	mov	#5,	r15	;#0x0005
    5258:	b4 3f       	jmp	$-150    	;abs 0x51c2
    525a:	2f 42       	mov	#4,	r15	;r2 As==10
    525c:	b2 3f       	jmp	$-154    	;abs 0x51c2
    525e:	21 52       	add	#4,	r1	;r2 As==10
    5260:	37 41       	pop	r7		
    5262:	38 41       	pop	r8		
    5264:	39 41       	pop	r9		
    5266:	3a 41       	pop	r10		
    5268:	3b 41       	pop	r11		
    526a:	30 41       	ret			

0000526c <csma_output_packet>:
    526c:	0b 12       	push	r11		
    526e:	0a 12       	push	r10		
    5270:	09 12       	push	r9		
    5272:	08 12       	push	r8		
    5274:	07 12       	push	r7		
    5276:	08 4f       	mov	r15,	r8	
    5278:	07 4e       	mov	r14,	r7	
    527a:	7f 40 0d 00 	mov.b	#13,	r15	;#0x000d
    527e:	b0 12 34 73 	call	#0x7334	
    5282:	0a 4f       	mov	r15,	r10	
    5284:	b0 12 12 63 	call	#0x6312	
    5288:	1e 43       	mov	#1,	r14	;r3 As==01
    528a:	7f 40 0b 00 	mov.b	#11,	r15	;#0x000b
    528e:	b0 12 06 73 	call	#0x7306	
    5292:	3f 40 6c 22 	mov	#8812,	r15	;#0x226c
    5296:	b0 12 34 62 	call	#0x6234	
    529a:	0a 3c       	jmp	$+22     	;abs 0x52b0
    529c:	0e 4a       	mov	r10,	r14	
    529e:	0f 4b       	mov	r11,	r15	
    52a0:	2f 53       	incd	r15		
    52a2:	b0 12 10 62 	call	#0x6210	
    52a6:	4f 93       	tst.b	r15		
    52a8:	76 20       	jnz	$+238    	;abs 0x5396
    52aa:	0f 4b       	mov	r11,	r15	
    52ac:	b0 12 b8 62 	call	#0x62b8	
    52b0:	0b 4f       	mov	r15,	r11	
    52b2:	0f 93       	tst	r15		
    52b4:	f3 23       	jnz	$-24     	;abs 0x529c
    52b6:	78 3c       	jmp	$+242    	;abs 0x53a8
    52b8:	0e 4a       	mov	r10,	r14	
    52ba:	0f 4b       	mov	r11,	r15	
    52bc:	2f 53       	incd	r15		
    52be:	b0 12 08 62 	call	#0x6208	
    52c2:	cb 43 1e 00 	mov.b	#0,	30(r11)	;r3 As==00, 0x001e(r11)
    52c6:	cb 43 1f 00 	mov.b	#0,	31(r11)	;r3 As==00, 0x001f(r11)
    52ca:	0f 4b       	mov	r11,	r15	
    52cc:	3f 50 20 00 	add	#32,	r15	;#0x0020
    52d0:	8b 4f 22 00 	mov	r15,	34(r11)	;0x0022(r11)
    52d4:	8b 43 20 00 	mov	#0,	32(r11)	;r3 As==00, 0x0020(r11)
    52d8:	b0 12 2e 62 	call	#0x622e	
    52dc:	0e 4b       	mov	r11,	r14	
    52de:	3f 40 6c 22 	mov	#8812,	r15	;#0x226c
    52e2:	b0 12 7e 62 	call	#0x627e	
    52e6:	57 3c       	jmp	$+176    	;abs 0x5396
    52e8:	3f 40 18 11 	mov	#4376,	r15	;#0x1118
    52ec:	b0 12 88 64 	call	#0x6488	
    52f0:	0a 4f       	mov	r15,	r10	
    52f2:	0f 93       	tst	r15		
    52f4:	38 24       	jz	$+114    	;abs 0x5366
    52f6:	3f 40 20 11 	mov	#4384,	r15	;#0x1120
    52fa:	b0 12 88 64 	call	#0x6488	
    52fe:	8a 4f 04 00 	mov	r15,	4(r10)	;0x0004(r10)
    5302:	0f 93       	tst	r15		
    5304:	2b 24       	jz	$+88     	;abs 0x535c
    5306:	b0 12 2e 77 	call	#0x772e	
    530a:	8a 4f 02 00 	mov	r15,	2(r10)	;0x0002(r10)
    530e:	19 4a 04 00 	mov	4(r10),	r9	;0x0004(r10)
    5312:	0f 93       	tst	r15		
    5314:	1e 24       	jz	$+62     	;abs 0x5352
    5316:	7f 40 05 00 	mov.b	#5,	r15	;#0x0005
    531a:	b0 12 12 73 	call	#0x7312	
    531e:	4f 93       	tst.b	r15		
    5320:	03 24       	jz	$+8      	;abs 0x5328
    5322:	c9 4f 04 00 	mov.b	r15,	4(r9)	;0x0004(r9)
    5326:	02 3c       	jmp	$+6      	;abs 0x532c
    5328:	f9 42 04 00 	mov.b	#8,	4(r9)	;r2 As==11, 0x0004(r9)
    532c:	89 48 00 00 	mov	r8,	0(r9)	;0x0000(r9)
    5330:	89 47 02 00 	mov	r7,	2(r9)	;0x0002(r9)
    5334:	0e 4a       	mov	r10,	r14	
    5336:	1f 4b 22 00 	mov	34(r11),r15	;0x0022(r11)
    533a:	b0 12 7e 62 	call	#0x627e	
    533e:	1f 4b 22 00 	mov	34(r11),r15	;0x0022(r11)
    5342:	b0 12 34 62 	call	#0x6234	
    5346:	0a 9f       	cmp	r15,	r10	
    5348:	37 20       	jnz	$+112    	;abs 0x53b8
    534a:	0f 4b       	mov	r11,	r15	
    534c:	b0 12 a2 4f 	call	#0x4fa2	
    5350:	33 3c       	jmp	$+104    	;abs 0x53b8
    5352:	0e 49       	mov	r9,	r14	
    5354:	3f 40 20 11 	mov	#4384,	r15	;#0x1120
    5358:	b0 12 c6 64 	call	#0x64c6	
    535c:	0e 4a       	mov	r10,	r14	
    535e:	3f 40 18 11 	mov	#4376,	r15	;#0x1118
    5362:	b0 12 c6 64 	call	#0x64c6	
    5366:	1f 4b 22 00 	mov	34(r11),r15	;0x0022(r11)
    536a:	b0 12 a8 62 	call	#0x62a8	
    536e:	0f 93       	tst	r15		
    5370:	0a 20       	jnz	$+22     	;abs 0x5386
    5372:	0e 4b       	mov	r11,	r14	
    5374:	3f 40 6c 22 	mov	#8812,	r15	;#0x226c
    5378:	b0 12 4a 62 	call	#0x624a	
    537c:	0e 4b       	mov	r11,	r14	
    537e:	3f 40 10 11 	mov	#4368,	r15	;#0x1110
    5382:	b0 12 c6 64 	call	#0x64c6	
    5386:	1c 43       	mov	#1,	r12	;r3 As==01
    5388:	3d 40 06 00 	mov	#6,	r13	;#0x0006
    538c:	0e 47       	mov	r7,	r14	
    538e:	0f 48       	mov	r8,	r15	
    5390:	b0 12 3e 64 	call	#0x643e	
    5394:	11 3c       	jmp	$+36     	;abs 0x53b8
    5396:	1f 4b 22 00 	mov	34(r11),r15	;0x0022(r11)
    539a:	b0 12 a8 62 	call	#0x62a8	
    539e:	3f 90 07 00 	cmp	#7,	r15	;#0x0007
    53a2:	01 24       	jz	$+4      	;abs 0x53a6
    53a4:	f0 37       	jge	$-30     	;abs 0x5386
    53a6:	a0 3f       	jmp	$-190    	;abs 0x52e8
    53a8:	3f 40 10 11 	mov	#4368,	r15	;#0x1110
    53ac:	b0 12 88 64 	call	#0x6488	
    53b0:	0b 4f       	mov	r15,	r11	
    53b2:	0f 93       	tst	r15		
    53b4:	81 23       	jnz	$-252    	;abs 0x52b8
    53b6:	e7 3f       	jmp	$-48     	;abs 0x5386
    53b8:	37 41       	pop	r7		
    53ba:	38 41       	pop	r8		
    53bc:	39 41       	pop	r9		
    53be:	3a 41       	pop	r10		
    53c0:	3b 41       	pop	r11		
    53c2:	30 41       	ret			

000053c4 <csma_output_init>:
    53c4:	3f 40 18 11 	mov	#4376,	r15	;#0x1118
    53c8:	b0 12 52 64 	call	#0x6452	
    53cc:	3f 40 20 11 	mov	#4384,	r15	;#0x1120
    53d0:	b0 12 52 64 	call	#0x6452	
    53d4:	3f 40 10 11 	mov	#4368,	r15	;#0x1110
    53d8:	b0 12 52 64 	call	#0x6452	
    53dc:	30 41       	ret			

000053de <csma_security_create_frame>:
    53de:	1e 43       	mov	#1,	r14	;r3 As==01
    53e0:	7f 40 0b 00 	mov.b	#11,	r15	;#0x000b
    53e4:	b0 12 06 73 	call	#0x7306	
    53e8:	92 12 c2 ab 	call	&0xabc2	
    53ec:	30 41       	ret			

000053ee <csma_security_parse_frame>:
    53ee:	92 12 c4 ab 	call	&0xabc4	
    53f2:	30 41       	ret			

000053f4 <on>:
    53f4:	92 12 74 ab 	call	&0xab74	
    53f8:	30 41       	ret			

000053fa <off>:
    53fa:	92 12 76 ab 	call	&0xab76	
    53fe:	30 41       	ret			

00005400 <max_payload>:
    5400:	0b 12       	push	r11		
    5402:	21 83       	decd	r1		
    5404:	92 12 c0 ab 	call	&0xabc0	
    5408:	0b 4f       	mov	r15,	r11	
    540a:	0e 41       	mov	r1,	r14	
    540c:	3f 40 18 00 	mov	#24,	r15	;#0x0018
    5410:	92 12 78 ab 	call	&0xab78	
    5414:	1f 93       	cmp	#1,	r15	;r3 As==01
    5416:	0c 24       	jz	$+26     	;abs 0x5430
    5418:	0b 93       	tst	r11		
    541a:	02 34       	jge	$+6      	;abs 0x5420
    541c:	3b 40 15 00 	mov	#21,	r11	;#0x0015
    5420:	2f 41       	mov	@r1,	r15	
    5422:	3f 90 81 00 	cmp	#129,	r15	;#0x0081
    5426:	02 38       	jl	$+6      	;abs 0x542c
    5428:	3f 40 80 00 	mov	#128,	r15	;#0x0080
    542c:	0f 8b       	sub	r11,	r15	
    542e:	01 3c       	jmp	$+4      	;abs 0x5432
    5430:	0f 43       	clr	r15		
    5432:	21 53       	incd	r1		
    5434:	3b 41       	pop	r11		
    5436:	30 41       	ret			

00005438 <send_packet>:
    5438:	b0 12 6c 52 	call	#0x526c	
    543c:	30 41       	ret			

0000543e <input_packet>:
    543e:	b0 12 ae 71 	call	#0x71ae	
    5442:	3f 90 03 00 	cmp	#3,	r15	;#0x0003
    5446:	2a 24       	jz	$+86     	;abs 0x549c
    5448:	b0 12 ee 53 	call	#0x53ee	
    544c:	0f 93       	tst	r15		
    544e:	26 38       	jl	$+78     	;abs 0x549c
    5450:	7f 40 0d 00 	mov.b	#13,	r15	;#0x000d
    5454:	b0 12 34 73 	call	#0x7334	
    5458:	3e 40 ea 2d 	mov	#11754,	r14	;#0x2dea
    545c:	b0 12 10 62 	call	#0x6210	
    5460:	4f 93       	tst.b	r15		
    5462:	0a 20       	jnz	$+22     	;abs 0x5478
    5464:	b0 12 46 73 	call	#0x7346	
    5468:	4f 93       	tst.b	r15		
    546a:	06 20       	jnz	$+14     	;abs 0x5478
    546c:	30 12 9e ab 	push	#-21602	;#0xab9e
    5470:	b0 12 cc 9e 	call	#0x9ecc	
    5474:	21 53       	incd	r1		
    5476:	30 41       	ret			
    5478:	7f 40 0c 00 	mov.b	#12,	r15	;#0x000c
    547c:	b0 12 34 73 	call	#0x7334	
    5480:	3e 40 ea 2d 	mov	#11754,	r14	;#0x2dea
    5484:	b0 12 10 62 	call	#0x6210	
    5488:	4f 93       	tst.b	r15		
    548a:	08 20       	jnz	$+18     	;abs 0x549c
    548c:	b0 12 2a 63 	call	#0x632a	
    5490:	0f 93       	tst	r15		
    5492:	04 20       	jnz	$+10     	;abs 0x549c
    5494:	b0 12 ae 63 	call	#0x63ae	
    5498:	92 12 d4 ae 	call	&0xaed4	
    549c:	30 41       	ret			

0000549e <init>:
    549e:	21 83       	decd	r1		
    54a0:	0e 41       	mov	r1,	r14	
    54a2:	3f 40 18 00 	mov	#24,	r15	;#0x0018
    54a6:	92 12 78 ab 	call	&0xab78	
    54aa:	0f 93       	tst	r15		
    54ac:	06 20       	jnz	$+14     	;abs 0x54ba
    54ae:	b0 12 08 63 	call	#0x6308	
    54b2:	b0 12 c4 53 	call	#0x53c4	
    54b6:	b0 12 f4 53 	call	#0x53f4	
    54ba:	21 53       	incd	r1		
    54bc:	30 41       	ret			

000054be <process_thread_ctimer_process>:
    54be:	0b 12       	push	r11		
    54c0:	0a 12       	push	r10		
    54c2:	09 12       	push	r9		
    54c4:	0a 4f       	mov	r15,	r10	
    54c6:	09 4d       	mov	r13,	r9	
    54c8:	2f 4f       	mov	@r15,	r15	
    54ca:	0f 93       	tst	r15		
    54cc:	04 24       	jz	$+10     	;abs 0x54d6
    54ce:	3f 90 4a 00 	cmp	#74,	r15	;#0x004a
    54d2:	3a 20       	jnz	$+118    	;abs 0x5548
    54d4:	40 3c       	jmp	$+130    	;abs 0x5556
    54d6:	3f 40 2a 23 	mov	#9002,	r15	;#0x232a
    54da:	b0 12 34 62 	call	#0x6234	
    54de:	0b 4f       	mov	r15,	r11	
    54e0:	09 3c       	jmp	$+20     	;abs 0x54f4
    54e2:	1d 4b 06 00 	mov	6(r11),	r13	;0x0006(r11)
    54e6:	1e 4b 08 00 	mov	8(r11),	r14	;0x0008(r11)
    54ea:	0f 4b       	mov	r11,	r15	
    54ec:	2f 53       	incd	r15		
    54ee:	b0 12 36 59 	call	#0x5936	
    54f2:	2b 4b       	mov	@r11,	r11	
    54f4:	0b 93       	tst	r11		
    54f6:	f5 23       	jnz	$-20     	;abs 0x54e2
    54f8:	d2 43 28 23 	mov.b	#1,	&0x2328	;r3 As==01
    54fc:	ba 40 4a 00 	mov	#74,	0(r10)	;#0x004a, 0x0000(r10)
    5500:	00 00 
    5502:	27 3c       	jmp	$+80     	;abs 0x5552
    5504:	3f 40 2a 23 	mov	#9002,	r15	;#0x232a
    5508:	b0 12 34 62 	call	#0x6234	
    550c:	0b 4f       	mov	r15,	r11	
    550e:	19 3c       	jmp	$+52     	;abs 0x5542
    5510:	0f 4b       	mov	r11,	r15	
    5512:	2f 53       	incd	r15		
    5514:	09 9f       	cmp	r15,	r9	
    5516:	14 20       	jnz	$+42     	;abs 0x5540
    5518:	0e 4b       	mov	r11,	r14	
    551a:	3f 40 2a 23 	mov	#9002,	r15	;#0x232a
    551e:	b0 12 4a 62 	call	#0x624a	
    5522:	19 42 e6 25 	mov	&0x25e6,r9	
    5526:	92 4b 0e 00 	mov	14(r11),&0x25e6	;0x000e(r11)
    552a:	e6 25 
    552c:	1e 4b 10 00 	mov	16(r11),r14	;0x0010(r11)
    5530:	0e 93       	tst	r14		
    5532:	03 24       	jz	$+8      	;abs 0x553a
    5534:	1f 4b 12 00 	mov	18(r11),r15	;0x0012(r11)
    5538:	8e 12       	call	r14		
    553a:	82 49 e6 25 	mov	r9,	&0x25e6	
    553e:	de 3f       	jmp	$-66     	;abs 0x54fc
    5540:	2b 4b       	mov	@r11,	r11	
    5542:	0b 93       	tst	r11		
    5544:	e5 23       	jnz	$-52     	;abs 0x5510
    5546:	da 3f       	jmp	$-74     	;abs 0x54fc
    5548:	8a 43 00 00 	mov	#0,	0(r10)	;r3 As==00, 0x0000(r10)
    554c:	7f 40 03 00 	mov.b	#3,	r15	;#0x0003
    5550:	06 3c       	jmp	$+14     	;abs 0x555e
    5552:	5f 43       	mov.b	#1,	r15	;r3 As==01
    5554:	04 3c       	jmp	$+10     	;abs 0x555e
    5556:	7e 90 88 ff 	cmp.b	#-120,	r14	;#0xff88
    555a:	fb 23       	jnz	$-8      	;abs 0x5552
    555c:	d3 3f       	jmp	$-88     	;abs 0x5504
    555e:	39 41       	pop	r9		
    5560:	3a 41       	pop	r10		
    5562:	3b 41       	pop	r11		
    5564:	30 41       	ret			

00005566 <ctimer_init>:
    5566:	c2 43 28 23 	mov.b	#0,	&0x2328	;r3 As==00
    556a:	3f 40 2a 23 	mov	#9002,	r15	;#0x232a
    556e:	b0 12 2e 62 	call	#0x622e	
    5572:	0e 43       	clr	r14		
    5574:	3f 40 28 11 	mov	#4392,	r15	;#0x1128
    5578:	b0 12 ce 76 	call	#0x76ce	
    557c:	30 41       	ret			

0000557e <ctimer_set_with_process>:
    557e:	0b 12       	push	r11		
    5580:	0a 12       	push	r10		
    5582:	09 12       	push	r9		
    5584:	09 4f       	mov	r15,	r9	
    5586:	9f 41 0a 00 	mov	10(r1),	14(r15)	;0x000a(r1), 0x000e(r15)
    558a:	0e 00 
    558c:	8f 4c 10 00 	mov	r12,	16(r15)	;0x0010(r15)
    5590:	9f 41 08 00 	mov	8(r1),	18(r15)	;0x0008(r1), 0x0012(r15)
    5594:	12 00 
    5596:	c2 93 28 23 	tst.b	&0x2328	
    559a:	0b 24       	jz	$+24     	;abs 0x55b2
    559c:	1b 42 e6 25 	mov	&0x25e6,r11	
    55a0:	b2 40 28 11 	mov	#4392,	&0x25e6	;#0x1128
    55a4:	e6 25 
    55a6:	2f 53       	incd	r15		
    55a8:	b0 12 36 59 	call	#0x5936	
    55ac:	82 4b e6 25 	mov	r11,	&0x25e6	
    55b0:	04 3c       	jmp	$+10     	;abs 0x55ba
    55b2:	89 4d 06 00 	mov	r13,	6(r9)	;0x0006(r9)
    55b6:	89 4e 08 00 	mov	r14,	8(r9)	;0x0008(r9)
    55ba:	0e 49       	mov	r9,	r14	
    55bc:	3f 40 2a 23 	mov	#9002,	r15	;#0x232a
    55c0:	b0 12 7e 62 	call	#0x627e	
    55c4:	39 41       	pop	r9		
    55c6:	3a 41       	pop	r10		
    55c8:	3b 41       	pop	r11		
    55ca:	30 41       	ret			

000055cc <ctimer_set>:
    55cc:	12 12 e6 25 	push	&0x25e6	
    55d0:	11 12 06 00 	push	6(r1)		;0x0006(r1)
    55d4:	b0 12 7e 55 	call	#0x557e	
    55d8:	21 52       	add	#4,	r1	;r2 As==10
    55da:	30 41       	ret			

000055dc <ctimer_reset>:
    55dc:	0b 12       	push	r11		
    55de:	0a 12       	push	r10		
    55e0:	0b 4f       	mov	r15,	r11	
    55e2:	c2 93 28 23 	tst.b	&0x2328	
    55e6:	0a 24       	jz	$+22     	;abs 0x55fc
    55e8:	1a 42 e6 25 	mov	&0x25e6,r10	
    55ec:	b2 40 28 11 	mov	#4392,	&0x25e6	;#0x1128
    55f0:	e6 25 
    55f2:	2f 53       	incd	r15		
    55f4:	b0 12 48 59 	call	#0x5948	
    55f8:	82 4a e6 25 	mov	r10,	&0x25e6	
    55fc:	0e 4b       	mov	r11,	r14	
    55fe:	3f 40 2a 23 	mov	#9002,	r15	;#0x232a
    5602:	b0 12 7e 62 	call	#0x627e	
    5606:	3a 41       	pop	r10		
    5608:	3b 41       	pop	r11		
    560a:	30 41       	ret			

0000560c <ctimer_stop>:
    560c:	0b 12       	push	r11		
    560e:	0b 4f       	mov	r15,	r11	
    5610:	c2 93 28 23 	tst.b	&0x2328	
    5614:	04 24       	jz	$+10     	;abs 0x561e
    5616:	2f 53       	incd	r15		
    5618:	b0 12 8a 59 	call	#0x598a	
    561c:	04 3c       	jmp	$+10     	;abs 0x5626
    561e:	8f 43 0a 00 	mov	#0,	10(r15)	;r3 As==00, 0x000a(r15)
    5622:	8f 43 0c 00 	mov	#0,	12(r15)	;r3 As==00, 0x000c(r15)
    5626:	0e 4b       	mov	r11,	r14	
    5628:	3f 40 2a 23 	mov	#9002,	r15	;#0x232a
    562c:	b0 12 4a 62 	call	#0x624a	
    5630:	3b 41       	pop	r11		
    5632:	30 41       	ret			

00005634 <owreadb>:
    5634:	0b 12       	push	r11		
    5636:	0a 12       	push	r10		
    5638:	3a 42       	mov	#8,	r10	;r2 As==11
    563a:	0b 43       	clr	r11		
    563c:	f2 d0 10 00 	bis.b	#16,	&0x002a	;#0x0010
    5640:	2a 00 
    5642:	03 43       	nop			
    5644:	03 43       	nop			
    5646:	03 43       	nop			
    5648:	03 43       	nop			
    564a:	03 43       	nop			
    564c:	03 43       	nop			
    564e:	03 43       	nop			
    5650:	f2 f0 ef ff 	and.b	#-17,	&0x002a	;#0xffef
    5654:	2a 00 
    5656:	3f 40 09 00 	mov	#9,	r15	;#0x0009
    565a:	b0 12 8a 4f 	call	#0x4f8a	
    565e:	f2 b0 10 00 	bit.b	#16,	&0x0028	;#0x0010
    5662:	28 00 
    5664:	02 24       	jz	$+6      	;abs 0x566a
    5666:	3b d0 80 00 	bis	#128,	r11	;#0x0080
    566a:	3f 40 47 00 	mov	#71,	r15	;#0x0047
    566e:	b0 12 8a 4f 	call	#0x4f8a	
    5672:	3a 53       	add	#-1,	r10	;r3 As==11
    5674:	03 24       	jz	$+8      	;abs 0x567c
    5676:	12 c3       	clrc			
    5678:	0b 10       	rrc	r11		
    567a:	e0 3f       	jmp	$-62     	;abs 0x563c
    567c:	0f 4b       	mov	r11,	r15	
    567e:	3a 41       	pop	r10		
    5680:	3b 41       	pop	r11		
    5682:	30 41       	ret			

00005684 <ds2411_init>:
    5684:	0b 12       	push	r11		
    5686:	0a 12       	push	r10		
    5688:	09 12       	push	r9		
    568a:	f2 f0 ef ff 	and.b	#-17,	&0x002a	;#0xffef
    568e:	2a 00 
    5690:	f2 f0 ef ff 	and.b	#-17,	&0x0029	;#0xffef
    5694:	29 00 
    5696:	f2 d0 10 00 	bis.b	#16,	&0x002a	;#0x0010
    569a:	2a 00 
    569c:	3f 40 7d 02 	mov	#637,	r15	;#0x027d
    56a0:	b0 12 8a 4f 	call	#0x4f8a	
    56a4:	f2 f0 ef ff 	and.b	#-17,	&0x002a	;#0xffef
    56a8:	2a 00 
    56aa:	3f 40 5b 00 	mov	#91,	r15	;#0x005b
    56ae:	b0 12 8a 4f 	call	#0x4f8a	
    56b2:	5b 42 28 00 	mov.b	&0x0028,r11	
    56b6:	3f 40 20 02 	mov	#544,	r15	;#0x0220
    56ba:	b0 12 8a 4f 	call	#0x4f8a	
    56be:	7b f0 10 00 	and.b	#16,	r11	;#0x0010
    56c2:	65 20       	jnz	$+204    	;abs 0x578e
    56c4:	b0 12 da 65 	call	#0x65da	
    56c8:	09 4f       	mov	r15,	r9	
    56ca:	3b 42       	mov	#8,	r11	;r2 As==11
    56cc:	3a 40 33 00 	mov	#51,	r10	;#0x0033
    56d0:	0f 4a       	mov	r10,	r15	
    56d2:	1f f3       	and	#1,	r15	;r3 As==01
    56d4:	f2 d0 10 00 	bis.b	#16,	&0x002a	;#0x0010
    56d8:	2a 00 
    56da:	0d 24       	jz	$+28     	;abs 0x56f6
    56dc:	03 43       	nop			
    56de:	03 43       	nop			
    56e0:	03 43       	nop			
    56e2:	03 43       	nop			
    56e4:	03 43       	nop			
    56e6:	03 43       	nop			
    56e8:	03 43       	nop			
    56ea:	f2 f0 ef ff 	and.b	#-17,	&0x002a	;#0xffef
    56ee:	2a 00 
    56f0:	3f 40 53 00 	mov	#83,	r15	;#0x0053
    56f4:	09 3c       	jmp	$+20     	;abs 0x5708
    56f6:	3f 40 4d 00 	mov	#77,	r15	;#0x004d
    56fa:	b0 12 8a 4f 	call	#0x4f8a	
    56fe:	f2 f0 ef ff 	and.b	#-17,	&0x002a	;#0xffef
    5702:	2a 00 
    5704:	3f 40 0b 00 	mov	#11,	r15	;#0x000b
    5708:	b0 12 8a 4f 	call	#0x4f8a	
    570c:	3b 53       	add	#-1,	r11	;r3 As==11
    570e:	03 24       	jz	$+8      	;abs 0x5716
    5710:	12 c3       	clrc			
    5712:	0a 10       	rrc	r10		
    5714:	dd 3f       	jmp	$-68     	;abs 0x56d0
    5716:	b0 12 34 56 	call	#0x5634	
    571a:	0a 4f       	mov	r15,	r10	
    571c:	3b 40 07 00 	mov	#7,	r11	;#0x0007
    5720:	b0 12 34 56 	call	#0x5634	
    5724:	cb 4f 4c 2e 	mov.b	r15,	11852(r11);0x2e4c(r11)
    5728:	3b 53       	add	#-1,	r11	;r3 As==11
    572a:	1b 93       	cmp	#1,	r11	;r3 As==01
    572c:	f9 23       	jnz	$-12     	;abs 0x5720
    572e:	b0 12 34 56 	call	#0x5634	
    5732:	02 d9       	bis	r9,	r2	
    5734:	1a 93       	cmp	#1,	r10	;r3 As==01
    5736:	2b 20       	jnz	$+88     	;abs 0x578e
    5738:	3d 42       	mov	#8,	r13	;r2 As==11
    573a:	1e 43       	mov	#1,	r14	;r3 As==01
    573c:	0c 4e       	mov	r14,	r12	
    573e:	1c f3       	and	#1,	r12	;r3 As==01
    5740:	12 c3       	clrc			
    5742:	0e 10       	rrc	r14		
    5744:	0c 93       	tst	r12		
    5746:	02 24       	jz	$+6      	;abs 0x574c
    5748:	3e e0 8c 00 	xor	#140,	r14	;#0x008c
    574c:	3d 53       	add	#-1,	r13	;r3 As==11
    574e:	f6 23       	jnz	$-18     	;abs 0x573c
    5750:	3d 40 07 00 	mov	#7,	r13	;#0x0007
    5754:	5c 4d 4c 2e 	mov.b	11852(r13),r12	;0x2e4c(r13)
    5758:	0e ec       	xor	r12,	r14	
    575a:	3c 42       	mov	#8,	r12	;r2 As==11
    575c:	0b 4e       	mov	r14,	r11	
    575e:	1b f3       	and	#1,	r11	;r3 As==01
    5760:	12 c3       	clrc			
    5762:	0e 10       	rrc	r14		
    5764:	0b 93       	tst	r11		
    5766:	02 24       	jz	$+6      	;abs 0x576c
    5768:	3e e0 8c 00 	xor	#140,	r14	;#0x008c
    576c:	3c 53       	add	#-1,	r12	;r3 As==11
    576e:	f6 23       	jnz	$-18     	;abs 0x575c
    5770:	3d 53       	add	#-1,	r13	;r3 As==11
    5772:	1d 93       	cmp	#1,	r13	;r3 As==01
    5774:	ef 23       	jnz	$-32     	;abs 0x5754
    5776:	0e 9f       	cmp	r15,	r14	
    5778:	0a 20       	jnz	$+22     	;abs 0x578e
    577a:	c2 43 4c 2e 	mov.b	#0,	&0x2e4c	;r3 As==00
    577e:	f2 40 12 00 	mov.b	#18,	&0x2e4d	;#0x0012
    5782:	4d 2e 
    5784:	f2 40 75 00 	mov.b	#117,	&0x2e4e	;#0x0075
    5788:	4e 2e 
    578a:	1f 43       	mov	#1,	r15	;r3 As==01
    578c:	07 3c       	jmp	$+16     	;abs 0x579c
    578e:	3d 42       	mov	#8,	r13	;r2 As==11
    5790:	0e 43       	clr	r14		
    5792:	3f 40 4c 2e 	mov	#11852,	r15	;#0x2e4c
    5796:	b0 12 ac a8 	call	#0xa8ac	
    579a:	0f 43       	clr	r15		
    579c:	39 41       	pop	r9		
    579e:	3a 41       	pop	r10		
    57a0:	3b 41       	pop	r11		
    57a2:	30 41       	ret			

000057a4 <energest_init>:
    57a4:	30 41       	ret			

000057a6 <energest_flush>:
    57a6:	30 41       	ret			

000057a8 <update_time>:
    57a8:	0b 12       	push	r11		
    57aa:	0a 12       	push	r10		
    57ac:	09 12       	push	r9		
    57ae:	82 93 2c 23 	tst	&0x232c	
    57b2:	05 20       	jnz	$+12     	;abs 0x57be
    57b4:	82 43 2e 23 	mov	#0,	&0x232e	;r3 As==00
    57b8:	82 43 30 23 	mov	#0,	&0x2330	;r3 As==00
    57bc:	2d 3c       	jmp	$+92     	;abs 0x5818
    57be:	b0 12 48 4f 	call	#0x4f48	
    57c2:	1b 42 2c 23 	mov	&0x232c,r11	
    57c6:	1c 4b 04 00 	mov	4(r11),	r12	;0x0004(r11)
    57ca:	1d 4b 06 00 	mov	6(r11),	r13	;0x0006(r11)
    57ce:	2c 5b       	add	@r11,	r12	
    57d0:	1d 6b 02 00 	addc	2(r11),	r13	;0x0002(r11)
    57d4:	0c 8e       	sub	r14,	r12	
    57d6:	0d 7f       	subc	r15,	r13	
    57d8:	19 4b 08 00 	mov	8(r11),	r9	;0x0008(r11)
    57dc:	13 3c       	jmp	$+40     	;abs 0x5804
    57de:	1a 49 04 00 	mov	4(r9),	r10	;0x0004(r9)
    57e2:	1b 49 06 00 	mov	6(r9),	r11	;0x0006(r9)
    57e6:	2a 59       	add	@r9,	r10	
    57e8:	1b 69 02 00 	addc	2(r9),	r11	;0x0002(r9)
    57ec:	0a 8e       	sub	r14,	r10	
    57ee:	0b 7f       	subc	r15,	r11	
    57f0:	0b 9d       	cmp	r13,	r11	
    57f2:	04 28       	jnc	$+10     	;abs 0x57fc
    57f4:	0d 9b       	cmp	r11,	r13	
    57f6:	04 28       	jnc	$+10     	;abs 0x5800
    57f8:	0a 9c       	cmp	r12,	r10	
    57fa:	02 2c       	jc	$+6      	;abs 0x5800
    57fc:	0c 4a       	mov	r10,	r12	
    57fe:	0d 4b       	mov	r11,	r13	
    5800:	19 49 08 00 	mov	8(r9),	r9	;0x0008(r9)
    5804:	09 93       	tst	r9		
    5806:	eb 23       	jnz	$-40     	;abs 0x57de
    5808:	0a 4c       	mov	r12,	r10	
    580a:	0b 4d       	mov	r13,	r11	
    580c:	0a 5e       	add	r14,	r10	
    580e:	0b 6f       	addc	r15,	r11	
    5810:	82 4a 2e 23 	mov	r10,	&0x232e	
    5814:	82 4b 30 23 	mov	r11,	&0x2330	
    5818:	39 41       	pop	r9		
    581a:	3a 41       	pop	r10		
    581c:	3b 41       	pop	r11		
    581e:	30 41       	ret			

00005820 <etimer_request_poll>:
    5820:	3f 40 32 11 	mov	#4402,	r15	;#0x1132
    5824:	b0 12 04 77 	call	#0x7704	
    5828:	30 41       	ret			

0000582a <process_thread_etimer_process>:
    582a:	0b 12       	push	r11		
    582c:	0a 12       	push	r10		
    582e:	09 12       	push	r9		
    5830:	0a 4f       	mov	r15,	r10	
    5832:	2f 4f       	mov	@r15,	r15	
    5834:	0f 93       	tst	r15		
    5836:	04 24       	jz	$+10     	;abs 0x5840
    5838:	3f 90 59 00 	cmp	#89,	r15	;#0x0059
    583c:	4d 20       	jnz	$+156    	;abs 0x58d8
    583e:	51 3c       	jmp	$+164    	;abs 0x58e2
    5840:	82 43 2c 23 	mov	#0,	&0x232c	;r3 As==00
    5844:	ba 40 59 00 	mov	#89,	0(r10)	;#0x0059, 0x0000(r10)
    5848:	00 00 
    584a:	5f 43       	mov.b	#1,	r15	;r3 As==01
    584c:	50 3c       	jmp	$+162    	;abs 0x58ee
    584e:	1e 4e 08 00 	mov	8(r14),	r14	;0x0008(r14)
    5852:	0e 93       	tst	r14		
    5854:	01 20       	jnz	$+4      	;abs 0x5858
    5856:	f4 3f       	jmp	$-22     	;abs 0x5840
    5858:	8e 9d 0a 00 	cmp	r13,	10(r14)	;0x000a(r14)
    585c:	f8 27       	jz	$-14     	;abs 0x584e
    585e:	82 4e 2c 23 	mov	r14,	&0x232c	
    5862:	08 3c       	jmp	$+18     	;abs 0x5874
    5864:	8c 9d 0a 00 	cmp	r13,	10(r12)	;0x000a(r12)
    5868:	04 20       	jnz	$+10     	;abs 0x5872
    586a:	9e 4c 08 00 	mov	8(r12),	8(r14)	;0x0008(r12), 0x0008(r14)
    586e:	08 00 
    5870:	01 3c       	jmp	$+4      	;abs 0x5874
    5872:	0e 4c       	mov	r12,	r14	
    5874:	1c 4e 08 00 	mov	8(r14),	r12	;0x0008(r14)
    5878:	0c 93       	tst	r12		
    587a:	f4 23       	jnz	$-22     	;abs 0x5864
    587c:	e3 3f       	jmp	$-56     	;abs 0x5844
    587e:	7e 90 82 ff 	cmp.b	#-126,	r14	;#0xff82
    5882:	e0 23       	jnz	$-62     	;abs 0x5844
    5884:	1b 42 2c 23 	mov	&0x232c,r11	
    5888:	09 43       	clr	r9		
    588a:	23 3c       	jmp	$+72     	;abs 0x58d2
    588c:	0f 4b       	mov	r11,	r15	
    588e:	b0 12 9a 7c 	call	#0x7c9a	
    5892:	0f 93       	tst	r15		
    5894:	1b 24       	jz	$+56     	;abs 0x58cc
    5896:	0d 4b       	mov	r11,	r13	
    5898:	7e 40 88 ff 	mov.b	#-120,	r14	;#0xff88
    589c:	1f 4b 0a 00 	mov	10(r11),r15	;0x000a(r11)
    58a0:	b0 12 7a 76 	call	#0x767a	
    58a4:	0f 93       	tst	r15		
    58a6:	10 20       	jnz	$+34     	;abs 0x58c8
    58a8:	8b 43 0a 00 	mov	#0,	10(r11)	;r3 As==00, 0x000a(r11)
    58ac:	09 93       	tst	r9		
    58ae:	04 24       	jz	$+10     	;abs 0x58b8
    58b0:	99 4b 08 00 	mov	8(r11),	8(r9)	;0x0008(r11), 0x0008(r9)
    58b4:	08 00 
    58b6:	03 3c       	jmp	$+8      	;abs 0x58be
    58b8:	92 4b 08 00 	mov	8(r11),	&0x232c	;0x0008(r11)
    58bc:	2c 23 
    58be:	8b 43 08 00 	mov	#0,	8(r11)	;r3 As==00, 0x0008(r11)
    58c2:	b0 12 a8 57 	call	#0x57a8	
    58c6:	de 3f       	jmp	$-66     	;abs 0x5884
    58c8:	b0 12 20 58 	call	#0x5820	
    58cc:	09 4b       	mov	r11,	r9	
    58ce:	1b 4b 08 00 	mov	8(r11),	r11	;0x0008(r11)
    58d2:	0b 93       	tst	r11		
    58d4:	db 23       	jnz	$-72     	;abs 0x588c
    58d6:	b6 3f       	jmp	$-146    	;abs 0x5844
    58d8:	8a 43 00 00 	mov	#0,	0(r10)	;r3 As==00, 0x0000(r10)
    58dc:	7f 40 03 00 	mov.b	#3,	r15	;#0x0003
    58e0:	06 3c       	jmp	$+14     	;abs 0x58ee
    58e2:	7e 90 87 ff 	cmp.b	#-121,	r14	;#0xff87
    58e6:	cb 23       	jnz	$-104    	;abs 0x587e
    58e8:	1e 42 2c 23 	mov	&0x232c,r14	
    58ec:	b2 3f       	jmp	$-154    	;abs 0x5852
    58ee:	39 41       	pop	r9		
    58f0:	3a 41       	pop	r10		
    58f2:	3b 41       	pop	r11		
    58f4:	30 41       	ret			

000058f6 <add_timer>:
    58f6:	0b 12       	push	r11		
    58f8:	0b 4f       	mov	r15,	r11	
    58fa:	b0 12 20 58 	call	#0x5820	
    58fe:	8b 93 0a 00 	tst	10(r11)	;0x000a(r11)
    5902:	0d 24       	jz	$+28     	;abs 0x591e
    5904:	1f 42 2c 23 	mov	&0x232c,r15	
    5908:	08 3c       	jmp	$+18     	;abs 0x591a
    590a:	0f 9b       	cmp	r11,	r15	
    590c:	04 20       	jnz	$+10     	;abs 0x5916
    590e:	9f 42 e6 25 	mov	&0x25e6,10(r15)	;0x000a(r15)
    5912:	0a 00 
    5914:	0c 3c       	jmp	$+26     	;abs 0x592e
    5916:	1f 4f 08 00 	mov	8(r15),	r15	;0x0008(r15)
    591a:	0f 93       	tst	r15		
    591c:	f6 23       	jnz	$-18     	;abs 0x590a
    591e:	9b 42 e6 25 	mov	&0x25e6,10(r11)	;0x000a(r11)
    5922:	0a 00 
    5924:	9b 42 2c 23 	mov	&0x232c,8(r11)	;0x0008(r11)
    5928:	08 00 
    592a:	82 4b 2c 23 	mov	r11,	&0x232c	
    592e:	b0 12 a8 57 	call	#0x57a8	
    5932:	3b 41       	pop	r11		
    5934:	30 41       	ret			

00005936 <etimer_set>:
    5936:	0b 12       	push	r11		
    5938:	0b 4f       	mov	r15,	r11	
    593a:	b0 12 7e 7c 	call	#0x7c7e	
    593e:	0f 4b       	mov	r11,	r15	
    5940:	b0 12 f6 58 	call	#0x58f6	
    5944:	3b 41       	pop	r11		
    5946:	30 41       	ret			

00005948 <etimer_reset>:
    5948:	0b 12       	push	r11		
    594a:	0b 4f       	mov	r15,	r11	
    594c:	b0 12 c4 7c 	call	#0x7cc4	
    5950:	0f 4b       	mov	r11,	r15	
    5952:	b0 12 f6 58 	call	#0x58f6	
    5956:	3b 41       	pop	r11		
    5958:	30 41       	ret			

0000595a <etimer_expired>:
    595a:	1e 43       	mov	#1,	r14	;r3 As==01
    595c:	8f 93 0a 00 	tst	10(r15)	;0x000a(r15)
    5960:	01 24       	jz	$+4      	;abs 0x5964
    5962:	0e 43       	clr	r14		
    5964:	0f 4e       	mov	r14,	r15	
    5966:	30 41       	ret			

00005968 <etimer_pending>:
    5968:	1f 43       	mov	#1,	r15	;r3 As==01
    596a:	82 93 2c 23 	tst	&0x232c	
    596e:	01 20       	jnz	$+4      	;abs 0x5972
    5970:	0f 43       	clr	r15		
    5972:	30 41       	ret			

00005974 <etimer_next_expiration_time>:
    5974:	82 93 2c 23 	tst	&0x232c	
    5978:	05 24       	jz	$+12     	;abs 0x5984
    597a:	1e 42 2e 23 	mov	&0x232e,r14	
    597e:	1f 42 30 23 	mov	&0x2330,r15	
    5982:	30 41       	ret			
    5984:	0e 43       	clr	r14		
    5986:	0f 43       	clr	r15		
    5988:	30 41       	ret			

0000598a <etimer_stop>:
    598a:	0b 12       	push	r11		
    598c:	0b 4f       	mov	r15,	r11	
    598e:	1f 42 2c 23 	mov	&0x232c,r15	
    5992:	0b 9f       	cmp	r15,	r11	
    5994:	05 20       	jnz	$+12     	;abs 0x59a0
    5996:	92 4b 08 00 	mov	8(r11),	&0x232c	;0x0008(r11)
    599a:	2c 23 
    599c:	10 3c       	jmp	$+34     	;abs 0x59be
    599e:	0f 4e       	mov	r14,	r15	
    59a0:	0f 93       	tst	r15		
    59a2:	05 24       	jz	$+12     	;abs 0x59ae
    59a4:	1e 4f 08 00 	mov	8(r15),	r14	;0x0008(r15)
    59a8:	0e 9b       	cmp	r11,	r14	
    59aa:	f9 23       	jnz	$-12     	;abs 0x599e
    59ac:	05 3c       	jmp	$+12     	;abs 0x59b8
    59ae:	8b 43 08 00 	mov	#0,	8(r11)	;r3 As==00, 0x0008(r11)
    59b2:	8b 43 0a 00 	mov	#0,	10(r11)	;r3 As==00, 0x000a(r11)
    59b6:	06 3c       	jmp	$+14     	;abs 0x59c4
    59b8:	9f 4b 08 00 	mov	8(r11),	8(r15)	;0x0008(r11), 0x0008(r15)
    59bc:	08 00 
    59be:	b0 12 a8 57 	call	#0x57a8	
    59c2:	f5 3f       	jmp	$-20     	;abs 0x59ae
    59c4:	3b 41       	pop	r11		
    59c6:	30 41       	ret			

000059c8 <frame802154_get_pan_id>:
    59c8:	1f 42 3c 11 	mov	&0x113c,r15	
    59cc:	30 41       	ret			

000059ce <frame802154_has_panid>:
    59ce:	0b 12       	push	r11		
    59d0:	0f 93       	tst	r15		
    59d2:	6b 24       	jz	$+216    	;abs 0x5aaa
    59d4:	ef 93 08 00 	cmp.b	#2,	8(r15)	;r3 As==10, 0x0008(r15)
    59d8:	42 20       	jnz	$+134    	;abs 0x5a5e
    59da:	5c 4f 07 00 	mov.b	7(r15),	r12	;0x0007(r15)
    59de:	4c 93       	tst.b	r12		
    59e0:	07 20       	jnz	$+16     	;abs 0x59f0
    59e2:	cf 93 09 00 	tst.b	9(r15)		;0x0009(r15)
    59e6:	1a 20       	jnz	$+54     	;abs 0x5a1c
    59e8:	df 93 04 00 	cmp.b	#1,	4(r15)	;r3 As==01, 0x0004(r15)
    59ec:	17 20       	jnz	$+48     	;abs 0x5a1c
    59ee:	1a 3c       	jmp	$+54     	;abs 0x5a24
    59f0:	5b 4f 09 00 	mov.b	9(r15),	r11	;0x0009(r15)
    59f4:	4b 93       	tst.b	r11		
    59f6:	04 20       	jnz	$+10     	;abs 0x5a00
    59f8:	cf 93 04 00 	tst.b	4(r15)		;0x0004(r15)
    59fc:	13 24       	jz	$+40     	;abs 0x5a24
    59fe:	51 3c       	jmp	$+164    	;abs 0x5aa2
    5a00:	7c 90 03 00 	cmp.b	#3,	r12	;#0x0003
    5a04:	07 20       	jnz	$+16     	;abs 0x5a14
    5a06:	7b 90 03 00 	cmp.b	#3,	r11	;#0x0003
    5a0a:	0a 20       	jnz	$+22     	;abs 0x5a20
    5a0c:	cf 93 04 00 	tst.b	4(r15)		;0x0004(r15)
    5a10:	09 24       	jz	$+20     	;abs 0x5a24
    5a12:	04 3c       	jmp	$+10     	;abs 0x5a1c
    5a14:	6c 93       	cmp.b	#2,	r12	;r3 As==10
    5a16:	04 20       	jnz	$+10     	;abs 0x5a20
    5a18:	4b 93       	tst.b	r11		
    5a1a:	04 20       	jnz	$+10     	;abs 0x5a24
    5a1c:	0b 43       	clr	r11		
    5a1e:	03 3c       	jmp	$+8      	;abs 0x5a26
    5a20:	6b 93       	cmp.b	#2,	r11	;r3 As==10
    5a22:	fc 23       	jnz	$-6      	;abs 0x5a1c
    5a24:	1b 43       	mov	#1,	r11	;r3 As==01
    5a26:	cf 93 04 00 	tst.b	4(r15)		;0x0004(r15)
    5a2a:	2f 20       	jnz	$+96     	;abs 0x5a8a
    5a2c:	4c 93       	tst.b	r12		
    5a2e:	06 20       	jnz	$+14     	;abs 0x5a3c
    5a30:	5f 4f 09 00 	mov.b	9(r15),	r15	;0x0009(r15)
    5a34:	6f 83       	decd.b	r15		
    5a36:	6f 93       	cmp.b	#2,	r15	;r3 As==10
    5a38:	25 28       	jnc	$+76     	;abs 0x5a84
    5a3a:	27 3c       	jmp	$+80     	;abs 0x5a8a
    5a3c:	6c 93       	cmp.b	#2,	r12	;r3 As==10
    5a3e:	08 20       	jnz	$+18     	;abs 0x5a50
    5a40:	5f 4f 09 00 	mov.b	9(r15),	r15	;0x0009(r15)
    5a44:	6f 93       	cmp.b	#2,	r15	;r3 As==10
    5a46:	1e 24       	jz	$+62     	;abs 0x5a84
    5a48:	7f 90 03 00 	cmp.b	#3,	r15	;#0x0003
    5a4c:	1b 24       	jz	$+56     	;abs 0x5a84
    5a4e:	1d 3c       	jmp	$+60     	;abs 0x5a8a
    5a50:	7c 90 03 00 	cmp.b	#3,	r12	;#0x0003
    5a54:	1a 20       	jnz	$+54     	;abs 0x5a8a
    5a56:	ef 93 09 00 	cmp.b	#2,	9(r15)	;r3 As==10, 0x0009(r15)
    5a5a:	14 24       	jz	$+42     	;abs 0x5a84
    5a5c:	16 3c       	jmp	$+46     	;abs 0x5a8a
    5a5e:	ef 93 00 00 	cmp.b	#2,	0(r15)	;r3 As==10, 0x0000(r15)
    5a62:	12 24       	jz	$+38     	;abs 0x5a88
    5a64:	cf 93 04 00 	tst.b	4(r15)		;0x0004(r15)
    5a68:	06 20       	jnz	$+14     	;abs 0x5a76
    5a6a:	5b 4f 09 00 	mov.b	9(r15),	r11	;0x0009(r15)
    5a6e:	7b f0 03 00 	and.b	#3,	r11	;#0x0003
    5a72:	1c 43       	mov	#1,	r12	;r3 As==01
    5a74:	01 20       	jnz	$+4      	;abs 0x5a78
    5a76:	0c 43       	clr	r12		
    5a78:	ff b0 03 00 	bit.b	#3,	7(r15)	;#0x0003, 0x0007(r15)
    5a7c:	07 00 
    5a7e:	07 20       	jnz	$+16     	;abs 0x5a8e
    5a80:	0b 43       	clr	r11		
    5a82:	06 3c       	jmp	$+14     	;abs 0x5a90
    5a84:	1c 43       	mov	#1,	r12	;r3 As==01
    5a86:	04 3c       	jmp	$+10     	;abs 0x5a90
    5a88:	0b 43       	clr	r11		
    5a8a:	0c 43       	clr	r12		
    5a8c:	01 3c       	jmp	$+4      	;abs 0x5a90
    5a8e:	1b 43       	mov	#1,	r11	;r3 As==01
    5a90:	0e 93       	tst	r14		
    5a92:	02 24       	jz	$+6      	;abs 0x5a98
    5a94:	8e 4c 00 00 	mov	r12,	0(r14)	;0x0000(r14)
    5a98:	0d 93       	tst	r13		
    5a9a:	07 24       	jz	$+16     	;abs 0x5aaa
    5a9c:	8d 4b 00 00 	mov	r11,	0(r13)	;0x0000(r13)
    5aa0:	04 3c       	jmp	$+10     	;abs 0x5aaa
    5aa2:	7c 90 03 00 	cmp.b	#3,	r12	;#0x0003
    5aa6:	ba 27       	jz	$-138    	;abs 0x5a1c
    5aa8:	b5 3f       	jmp	$-148    	;abs 0x5a14
    5aaa:	3b 41       	pop	r11		
    5aac:	30 41       	ret			

00005aae <field_len>:
    5aae:	0b 12       	push	r11		
    5ab0:	0a 12       	push	r10		
    5ab2:	21 82       	sub	#4,	r1	;r2 As==10
    5ab4:	0b 4f       	mov	r15,	r11	
    5ab6:	0a 4e       	mov	r14,	r10	
    5ab8:	3d 40 06 00 	mov	#6,	r13	;#0x0006
    5abc:	0e 43       	clr	r14		
    5abe:	0f 4a       	mov	r10,	r15	
    5ac0:	b0 12 ac a8 	call	#0xa8ac	
    5ac4:	db b3 15 00 	bit.b	#1,	21(r11)	;r3 As==01, 0x0015(r11)
    5ac8:	02 20       	jnz	$+6      	;abs 0x5ace
    5aca:	da 43 00 00 	mov.b	#1,	0(r10)	;r3 As==01, 0x0000(r10)
    5ace:	eb 93 18 00 	cmp.b	#2,	24(r11)	;r3 As==10, 0x0018(r11)
    5ad2:	11 2c       	jc	$+36     	;abs 0x5af6
    5ad4:	fb b0 03 00 	bit.b	#3,	23(r11)	;#0x0003, 0x0017(r11)
    5ad8:	17 00 
    5ada:	0b 24       	jz	$+24     	;abs 0x5af2
    5adc:	fb b0 03 00 	bit.b	#3,	25(r11)	;#0x0003, 0x0019(r11)
    5ae0:	19 00 
    5ae2:	07 24       	jz	$+16     	;abs 0x5af2
    5ae4:	9b 9b 1c 00 	cmp	28(r11),30(r11)	;0x001c(r11), 0x001e(r11)
    5ae8:	1e 00 
    5aea:	03 20       	jnz	$+8      	;abs 0x5af2
    5aec:	db 43 14 00 	mov.b	#1,	20(r11)	;r3 As==01, 0x0014(r11)
    5af0:	02 3c       	jmp	$+6      	;abs 0x5af6
    5af2:	cb 43 14 00 	mov.b	#0,	20(r11)	;r3 As==00, 0x0014(r11)
    5af6:	0d 41       	mov	r1,	r13	
    5af8:	0e 41       	mov	r1,	r14	
    5afa:	2e 53       	incd	r14		
    5afc:	0f 4b       	mov	r11,	r15	
    5afe:	3f 50 10 00 	add	#16,	r15	;#0x0010
    5b02:	b0 12 ce 59 	call	#0x59ce	
    5b06:	81 93 02 00 	tst	2(r1)		;0x0002(r1)
    5b0a:	02 24       	jz	$+6      	;abs 0x5b10
    5b0c:	ea 43 03 00 	mov.b	#2,	3(r10)	;r3 As==10, 0x0003(r10)
    5b10:	81 93 00 00 	tst	0(r1)		;0x0000(r1)
    5b14:	02 24       	jz	$+6      	;abs 0x5b1a
    5b16:	ea 43 01 00 	mov.b	#2,	1(r10)	;r3 As==10, 0x0001(r10)
    5b1a:	5f 4b 17 00 	mov.b	23(r11),r15	;0x0017(r11)
    5b1e:	7f f0 03 00 	and.b	#3,	r15	;#0x0003
    5b22:	6f 83       	decd.b	r15		
    5b24:	6f 93       	cmp.b	#2,	r15	;r3 As==10
    5b26:	04 2c       	jc	$+10     	;abs 0x5b30
    5b28:	4f 4f       	mov.b	r15,	r15	
    5b2a:	5f 4f 19 b0 	mov.b	-20455(r15),r15	;0xb019(r15)
    5b2e:	01 3c       	jmp	$+4      	;abs 0x5b32
    5b30:	4f 43       	clr.b	r15		
    5b32:	ca 4f 02 00 	mov.b	r15,	2(r10)	;0x0002(r10)
    5b36:	5f 4b 19 00 	mov.b	25(r11),r15	;0x0019(r11)
    5b3a:	7f f0 03 00 	and.b	#3,	r15	;#0x0003
    5b3e:	6f 83       	decd.b	r15		
    5b40:	6f 93       	cmp.b	#2,	r15	;r3 As==10
    5b42:	04 2c       	jc	$+10     	;abs 0x5b4c
    5b44:	4f 4f       	mov.b	r15,	r15	
    5b46:	5f 4f 19 b0 	mov.b	-20455(r15),r15	;0xb019(r15)
    5b4a:	01 3c       	jmp	$+4      	;abs 0x5b4e
    5b4c:	4f 43       	clr.b	r15		
    5b4e:	ca 4f 04 00 	mov.b	r15,	4(r10)	;0x0004(r10)
    5b52:	21 52       	add	#4,	r1	;r2 As==10
    5b54:	3a 41       	pop	r10		
    5b56:	3b 41       	pop	r11		
    5b58:	30 41       	ret			

00005b5a <frame802154_is_broadcast_addr>:
    5b5a:	6f 93       	cmp.b	#2,	r15	;r3 As==10
    5b5c:	08 24       	jz	$+18     	;abs 0x5b6e
    5b5e:	3f 42       	mov	#8,	r15	;r2 As==11
    5b60:	07 3c       	jmp	$+16     	;abs 0x5b70
    5b62:	0d 4e       	mov	r14,	r13	
    5b64:	0d 5f       	add	r15,	r13	
    5b66:	fd 93 00 00 	cmp.b	#-1,	0(r13)	;r3 As==11, 0x0000(r13)
    5b6a:	02 24       	jz	$+6      	;abs 0x5b70
    5b6c:	08 3c       	jmp	$+18     	;abs 0x5b7e
    5b6e:	2f 43       	mov	#2,	r15	;r3 As==10
    5b70:	3f 53       	add	#-1,	r15	;r3 As==11
    5b72:	0d 4f       	mov	r15,	r13	
    5b74:	1d 53       	inc	r13		
    5b76:	1d 93       	cmp	#1,	r13	;r3 As==01
    5b78:	f4 37       	jge	$-22     	;abs 0x5b62
    5b7a:	5f 43       	mov.b	#1,	r15	;r3 As==01
    5b7c:	30 41       	ret			
    5b7e:	4f 43       	clr.b	r15		
    5b80:	30 41       	ret			

00005b82 <frame802154_hdrlen>:
    5b82:	31 50 fa ff 	add	#-6,	r1	;#0xfffa
    5b86:	0e 41       	mov	r1,	r14	
    5b88:	b0 12 ae 5a 	call	#0x5aae	
    5b8c:	6f 41       	mov.b	@r1,	r15	
    5b8e:	2f 53       	incd	r15		
    5b90:	5e 41 01 00 	mov.b	1(r1),	r14	;0x0001(r1)
    5b94:	0f 5e       	add	r14,	r15	
    5b96:	5e 41 02 00 	mov.b	2(r1),	r14	;0x0002(r1)
    5b9a:	0f 5e       	add	r14,	r15	
    5b9c:	5e 41 03 00 	mov.b	3(r1),	r14	;0x0003(r1)
    5ba0:	0f 5e       	add	r14,	r15	
    5ba2:	5e 41 04 00 	mov.b	4(r1),	r14	;0x0004(r1)
    5ba6:	0f 5e       	add	r14,	r15	
    5ba8:	5e 41 05 00 	mov.b	5(r1),	r14	;0x0005(r1)
    5bac:	0f 5e       	add	r14,	r15	
    5bae:	31 50 06 00 	add	#6,	r1	;#0x0006
    5bb2:	30 41       	ret			

00005bb4 <frame802154_create_fcf>:
    5bb4:	0b 12       	push	r11		
    5bb6:	5c 4f 01 00 	mov.b	1(r15),	r12	;0x0001(r15)
    5bba:	1c f3       	and	#1,	r12	;r3 As==01
    5bbc:	0c 5c       	rla	r12		
    5bbe:	0c 5c       	rla	r12		
    5bc0:	0c 5c       	rla	r12		
    5bc2:	5d 4f 02 00 	mov.b	2(r15),	r13	;0x0002(r15)
    5bc6:	1d f3       	and	#1,	r13	;r3 As==01
    5bc8:	0d 5d       	rla	r13		
    5bca:	0d 5d       	rla	r13		
    5bcc:	0d 5d       	rla	r13		
    5bce:	0d 5d       	rla	r13		
    5bd0:	4c dd       	bis.b	r13,	r12	
    5bd2:	6d 4f       	mov.b	@r15,	r13	
    5bd4:	7d f0 07 00 	and.b	#7,	r13	;#0x0007
    5bd8:	4c dd       	bis.b	r13,	r12	
    5bda:	5d 4f 03 00 	mov.b	3(r15),	r13	;0x0003(r15)
    5bde:	1d f3       	and	#1,	r13	;r3 As==01
    5be0:	0d 5d       	rla	r13		
    5be2:	0d 5d       	rla	r13		
    5be4:	0d 5d       	rla	r13		
    5be6:	0d 5d       	rla	r13		
    5be8:	0d 5d       	rla	r13		
    5bea:	4c dd       	bis.b	r13,	r12	
    5bec:	5d 4f 04 00 	mov.b	4(r15),	r13	;0x0004(r15)
    5bf0:	1d f3       	and	#1,	r13	;r3 As==01
    5bf2:	7b 40 06 00 	mov.b	#6,	r11	;#0x0006
    5bf6:	0d 5d       	rla	r13		
    5bf8:	7b 53       	add.b	#-1,	r11	;r3 As==11
    5bfa:	fd 23       	jnz	$-4      	;abs 0x5bf6
    5bfc:	4c dd       	bis.b	r13,	r12	
    5bfe:	ce 4c 00 00 	mov.b	r12,	0(r14)	;0x0000(r14)
    5c02:	5c 4f 09 00 	mov.b	9(r15),	r12	;0x0009(r15)
    5c06:	7d 40 06 00 	mov.b	#6,	r13	;#0x0006
    5c0a:	0c 5c       	rla	r12		
    5c0c:	7d 53       	add.b	#-1,	r13	;r3 As==11
    5c0e:	fd 23       	jnz	$-4      	;abs 0x5c0a
    5c10:	5d 4f 05 00 	mov.b	5(r15),	r13	;0x0005(r15)
    5c14:	5d f3       	and.b	#1,	r13	;r3 As==01
    5c16:	4d dc       	bis.b	r12,	r13	
    5c18:	5c 4f 06 00 	mov.b	6(r15),	r12	;0x0006(r15)
    5c1c:	1c f3       	and	#1,	r12	;r3 As==01
    5c1e:	0c 5c       	rla	r12		
    5c20:	4d dc       	bis.b	r12,	r13	
    5c22:	5c 4f 07 00 	mov.b	7(r15),	r12	;0x0007(r15)
    5c26:	3c f0 03 00 	and	#3,	r12	;#0x0003
    5c2a:	0c 5c       	rla	r12		
    5c2c:	0c 5c       	rla	r12		
    5c2e:	4d dc       	bis.b	r12,	r13	
    5c30:	5f 4f 08 00 	mov.b	8(r15),	r15	;0x0008(r15)
    5c34:	3f f0 03 00 	and	#3,	r15	;#0x0003
    5c38:	0f 5f       	rla	r15		
    5c3a:	0f 5f       	rla	r15		
    5c3c:	0f 5f       	rla	r15		
    5c3e:	0f 5f       	rla	r15		
    5c40:	4d df       	bis.b	r15,	r13	
    5c42:	ce 4d 01 00 	mov.b	r13,	1(r14)	;0x0001(r14)
    5c46:	3b 41       	pop	r11		
    5c48:	30 41       	ret			

00005c4a <frame802154_create>:
    5c4a:	0b 12       	push	r11		
    5c4c:	0a 12       	push	r10		
    5c4e:	09 12       	push	r9		
    5c50:	08 12       	push	r8		
    5c52:	07 12       	push	r7		
    5c54:	31 50 fa ff 	add	#-6,	r1	;#0xfffa
    5c58:	0a 4f       	mov	r15,	r10	
    5c5a:	0b 4e       	mov	r14,	r11	
    5c5c:	0e 41       	mov	r1,	r14	
    5c5e:	b0 12 ae 5a 	call	#0x5aae	
    5c62:	0e 4b       	mov	r11,	r14	
    5c64:	0f 4a       	mov	r10,	r15	
    5c66:	3f 50 10 00 	add	#16,	r15	;#0x0010
    5c6a:	b0 12 b4 5b 	call	#0x5bb4	
    5c6e:	d1 93 00 00 	cmp.b	#1,	0(r1)	;r3 As==01, 0x0000(r1)
    5c72:	06 20       	jnz	$+14     	;abs 0x5c80
    5c74:	db 4a 1a 00 	mov.b	26(r10),2(r11)	;0x001a(r10), 0x0002(r11)
    5c78:	02 00 
    5c7a:	7f 40 03 00 	mov.b	#3,	r15	;#0x0003
    5c7e:	01 3c       	jmp	$+4      	;abs 0x5c82
    5c80:	6f 43       	mov.b	#2,	r15	;r3 As==10
    5c82:	e1 93 01 00 	cmp.b	#2,	1(r1)	;r3 As==10, 0x0001(r1)
    5c86:	0f 20       	jnz	$+32     	;abs 0x5ca6
    5c88:	4e 4f       	mov.b	r15,	r14	
    5c8a:	0e 5b       	add	r11,	r14	
    5c8c:	de 4a 1c 00 	mov.b	28(r10),0(r14)	;0x001c(r10), 0x0000(r14)
    5c90:	00 00 
    5c92:	4e 4f       	mov.b	r15,	r14	
    5c94:	5e 53       	inc.b	r14		
    5c96:	4e 4e       	mov.b	r14,	r14	
    5c98:	0e 5b       	add	r11,	r14	
    5c9a:	1d 4a 1c 00 	mov	28(r10),r13	;0x001c(r10)
    5c9e:	8d 10       	swpb	r13		
    5ca0:	ce 4d 00 00 	mov.b	r13,	0(r14)	;0x0000(r14)
    5ca4:	6f 53       	incd.b	r15		
    5ca6:	58 41 02 00 	mov.b	2(r1),	r8	;0x0002(r1)
    5caa:	4e 43       	clr.b	r14		
    5cac:	0d 43       	clr	r13		
    5cae:	4c 48       	mov.b	r8,	r12	
    5cb0:	0c 5a       	add	r10,	r12	
    5cb2:	07 3c       	jmp	$+16     	;abs 0x5cc2
    5cb4:	07 4c       	mov	r12,	r7	
    5cb6:	07 5d       	add	r13,	r7	
    5cb8:	49 49       	mov.b	r9,	r9	
    5cba:	09 5b       	add	r11,	r9	
    5cbc:	e9 47 00 00 	mov.b	@r7,	0(r9)	;0x0000(r9)
    5cc0:	5e 53       	inc.b	r14		
    5cc2:	49 4f       	mov.b	r15,	r9	
    5cc4:	49 8d       	sub.b	r13,	r9	
    5cc6:	3d 53       	add	#-1,	r13	;r3 As==11
    5cc8:	4e 98       	cmp.b	r8,	r14	
    5cca:	f4 23       	jnz	$-22     	;abs 0x5cb4
    5ccc:	4f 5e       	add.b	r14,	r15	
    5cce:	e1 93 03 00 	cmp.b	#2,	3(r1)	;r3 As==10, 0x0003(r1)
    5cd2:	0f 20       	jnz	$+32     	;abs 0x5cf2
    5cd4:	4e 4f       	mov.b	r15,	r14	
    5cd6:	0e 5b       	add	r11,	r14	
    5cd8:	de 4a 1e 00 	mov.b	30(r10),0(r14)	;0x001e(r10), 0x0000(r14)
    5cdc:	00 00 
    5cde:	4e 4f       	mov.b	r15,	r14	
    5ce0:	5e 53       	inc.b	r14		
    5ce2:	4e 4e       	mov.b	r14,	r14	
    5ce4:	0e 5b       	add	r11,	r14	
    5ce6:	1d 4a 1e 00 	mov	30(r10),r13	;0x001e(r10)
    5cea:	8d 10       	swpb	r13		
    5cec:	ce 4d 00 00 	mov.b	r13,	0(r14)	;0x0000(r14)
    5cf0:	6f 53       	incd.b	r15		
    5cf2:	59 41 04 00 	mov.b	4(r1),	r9	;0x0004(r1)
    5cf6:	4e 43       	clr.b	r14		
    5cf8:	0d 43       	clr	r13		
    5cfa:	4c 49       	mov.b	r9,	r12	
    5cfc:	0c 5a       	add	r10,	r12	
    5cfe:	08 3c       	jmp	$+18     	;abs 0x5d10
    5d00:	08 4c       	mov	r12,	r8	
    5d02:	08 5d       	add	r13,	r8	
    5d04:	4a 4a       	mov.b	r10,	r10	
    5d06:	0a 5b       	add	r11,	r10	
    5d08:	da 48 08 00 	mov.b	8(r8),	0(r10)	;0x0008(r8), 0x0000(r10)
    5d0c:	00 00 
    5d0e:	5e 53       	inc.b	r14		
    5d10:	4a 4f       	mov.b	r15,	r10	
    5d12:	4a 8d       	sub.b	r13,	r10	
    5d14:	3d 53       	add	#-1,	r13	;r3 As==11
    5d16:	4e 99       	cmp.b	r9,	r14	
    5d18:	f3 23       	jnz	$-24     	;abs 0x5d00
    5d1a:	4f 5e       	add.b	r14,	r15	
    5d1c:	4f 4f       	mov.b	r15,	r15	
    5d1e:	31 50 06 00 	add	#6,	r1	;#0x0006
    5d22:	37 41       	pop	r7		
    5d24:	38 41       	pop	r8		
    5d26:	39 41       	pop	r9		
    5d28:	3a 41       	pop	r10		
    5d2a:	3b 41       	pop	r11		
    5d2c:	30 41       	ret			

00005d2e <frame802154_parse_fcf>:
    5d2e:	0b 12       	push	r11		
    5d30:	31 50 f6 ff 	add	#-10,	r1	;#0xfff6
    5d34:	0b 4f       	mov	r15,	r11	
    5d36:	0f 4e       	mov	r14,	r15	
    5d38:	6c 4b       	mov.b	@r11,	r12	
    5d3a:	4e 4c       	mov.b	r12,	r14	
    5d3c:	7e f0 07 00 	and.b	#7,	r14	;#0x0007
    5d40:	c1 4e 00 00 	mov.b	r14,	0(r1)	;0x0000(r1)
    5d44:	4d 4c       	mov.b	r12,	r13	
    5d46:	12 c3       	clrc			
    5d48:	4d 10       	rrc.b	r13		
    5d4a:	12 c3       	clrc			
    5d4c:	4d 10       	rrc.b	r13		
    5d4e:	12 c3       	clrc			
    5d50:	4d 10       	rrc.b	r13		
    5d52:	5d f3       	and.b	#1,	r13	;r3 As==01
    5d54:	c1 4d 01 00 	mov.b	r13,	1(r1)	;0x0001(r1)
    5d58:	4d 4c       	mov.b	r12,	r13	
    5d5a:	12 c3       	clrc			
    5d5c:	4d 10       	rrc.b	r13		
    5d5e:	12 c3       	clrc			
    5d60:	4d 10       	rrc.b	r13		
    5d62:	12 c3       	clrc			
    5d64:	4d 10       	rrc.b	r13		
    5d66:	12 c3       	clrc			
    5d68:	4d 10       	rrc.b	r13		
    5d6a:	4e 4d       	mov.b	r13,	r14	
    5d6c:	5e f3       	and.b	#1,	r14	;r3 As==01
    5d6e:	c1 4e 02 00 	mov.b	r14,	2(r1)	;0x0002(r1)
    5d72:	12 c3       	clrc			
    5d74:	4d 10       	rrc.b	r13		
    5d76:	5d f3       	and.b	#1,	r13	;r3 As==01
    5d78:	c1 4d 03 00 	mov.b	r13,	3(r1)	;0x0003(r1)
    5d7c:	7e 40 06 00 	mov.b	#6,	r14	;#0x0006
    5d80:	12 c3       	clrc			
    5d82:	4c 10       	rrc.b	r12		
    5d84:	7e 53       	add.b	#-1,	r14	;r3 As==11
    5d86:	fc 23       	jnz	$-6      	;abs 0x5d80
    5d88:	5c f3       	and.b	#1,	r12	;r3 As==01
    5d8a:	c1 4c 04 00 	mov.b	r12,	4(r1)	;0x0004(r1)
    5d8e:	5c 4b 01 00 	mov.b	1(r11),	r12	;0x0001(r11)
    5d92:	4e 4c       	mov.b	r12,	r14	
    5d94:	5e f3       	and.b	#1,	r14	;r3 As==01
    5d96:	c1 4e 05 00 	mov.b	r14,	5(r1)	;0x0005(r1)
    5d9a:	4d 4c       	mov.b	r12,	r13	
    5d9c:	12 c3       	clrc			
    5d9e:	4d 10       	rrc.b	r13		
    5da0:	4e 4d       	mov.b	r13,	r14	
    5da2:	5e f3       	and.b	#1,	r14	;r3 As==01
    5da4:	c1 4e 06 00 	mov.b	r14,	6(r1)	;0x0006(r1)
    5da8:	12 c3       	clrc			
    5daa:	4d 10       	rrc.b	r13		
    5dac:	4e 4d       	mov.b	r13,	r14	
    5dae:	7e f0 03 00 	and.b	#3,	r14	;#0x0003
    5db2:	c1 4e 07 00 	mov.b	r14,	7(r1)	;0x0007(r1)
    5db6:	12 c3       	clrc			
    5db8:	4d 10       	rrc.b	r13		
    5dba:	12 c3       	clrc			
    5dbc:	4d 10       	rrc.b	r13		
    5dbe:	7d f0 03 00 	and.b	#3,	r13	;#0x0003
    5dc2:	c1 4d 08 00 	mov.b	r13,	8(r1)	;0x0008(r1)
    5dc6:	c1 4c 09 00 	mov.b	r12,	9(r1)	;0x0009(r1)
    5dca:	7d 40 06 00 	mov.b	#6,	r13	;#0x0006
    5dce:	12 c3       	clrc			
    5dd0:	51 10 09 00 	rrc.b	9(r1)		;0x0009(r1)
    5dd4:	7d 53       	add.b	#-1,	r13	;r3 As==11
    5dd6:	fb 23       	jnz	$-8      	;abs 0x5dce
    5dd8:	3d 40 0a 00 	mov	#10,	r13	;#0x000a
    5ddc:	0e 41       	mov	r1,	r14	
    5dde:	b0 12 b2 a7 	call	#0xa7b2	
    5de2:	31 50 0a 00 	add	#10,	r1	;#0x000a
    5de6:	3b 41       	pop	r11		
    5de8:	30 41       	ret			

00005dea <frame802154_parse>:
    5dea:	0b 12       	push	r11		
    5dec:	0a 12       	push	r10		
    5dee:	09 12       	push	r9		
    5df0:	08 12       	push	r8		
    5df2:	31 50 f2 ff 	add	#-14,	r1	;#0xfff2
    5df6:	09 4f       	mov	r15,	r9	
    5df8:	08 4e       	mov	r14,	r8	
    5dfa:	0a 4d       	mov	r13,	r10	
    5dfc:	2e 93       	cmp	#2,	r14	;r3 As==10
    5dfe:	a1 38       	jl	$+324    	;abs 0x5f42
    5e00:	0e 41       	mov	r1,	r14	
    5e02:	b0 12 2e 5d 	call	#0x5d2e	
    5e06:	3d 40 0a 00 	mov	#10,	r13	;#0x000a
    5e0a:	0e 41       	mov	r1,	r14	
    5e0c:	0f 4a       	mov	r10,	r15	
    5e0e:	3f 50 10 00 	add	#16,	r15	;#0x0010
    5e12:	b0 12 b2 a7 	call	#0xa7b2	
    5e16:	c1 93 05 00 	tst.b	5(r1)		;0x0005(r1)
    5e1a:	03 24       	jz	$+8      	;abs 0x5e22
    5e1c:	0b 49       	mov	r9,	r11	
    5e1e:	2b 53       	incd	r11		
    5e20:	06 3c       	jmp	$+14     	;abs 0x5e2e
    5e22:	da 49 02 00 	mov.b	2(r9),	26(r10)	;0x0002(r9), 0x001a(r10)
    5e26:	1a 00 
    5e28:	0b 49       	mov	r9,	r11	
    5e2a:	3b 50 03 00 	add	#3,	r11	;#0x0003
    5e2e:	0d 41       	mov	r1,	r13	
    5e30:	3d 50 0a 00 	add	#10,	r13	;#0x000a
    5e34:	0e 41       	mov	r1,	r14	
    5e36:	3e 50 0c 00 	add	#12,	r14	;#0x000c
    5e3a:	0f 41       	mov	r1,	r15	
    5e3c:	b0 12 ce 59 	call	#0x59ce	
    5e40:	5f 41 07 00 	mov.b	7(r1),	r15	;0x0007(r1)
    5e44:	4f 93       	tst.b	r15		
    5e46:	2d 24       	jz	$+92     	;abs 0x5ea2
    5e48:	81 93 0a 00 	tst	10(r1)		;0x000a(r1)
    5e4c:	09 24       	jz	$+20     	;abs 0x5e60
    5e4e:	6d 4b       	mov.b	@r11,	r13	
    5e50:	5e 4b 01 00 	mov.b	1(r11),	r14	;0x0001(r11)
    5e54:	8e 10       	swpb	r14		
    5e56:	0d 5e       	add	r14,	r13	
    5e58:	8a 4d 1c 00 	mov	r13,	28(r10)	;0x001c(r10)
    5e5c:	2b 53       	incd	r11		
    5e5e:	02 3c       	jmp	$+6      	;abs 0x5e64
    5e60:	8a 43 1c 00 	mov	#0,	28(r10)	;r3 As==00, 0x001c(r10)
    5e64:	6f 93       	cmp.b	#2,	r15	;r3 As==10
    5e66:	0c 20       	jnz	$+26     	;abs 0x5e80
    5e68:	3e 40 c6 ab 	mov	#-21562,r14	;#0xabc6
    5e6c:	0f 4a       	mov	r10,	r15	
    5e6e:	b0 12 08 62 	call	#0x6208	
    5e72:	da 4b 01 00 	mov.b	1(r11),	0(r10)	;0x0001(r11), 0x0000(r10)
    5e76:	00 00 
    5e78:	ea 4b 01 00 	mov.b	@r11,	1(r10)	;0x0001(r10)
    5e7c:	2b 53       	incd	r11		
    5e7e:	18 3c       	jmp	$+50     	;abs 0x5eb0
    5e80:	7f 90 03 00 	cmp.b	#3,	r15	;#0x0003
    5e84:	15 20       	jnz	$+44     	;abs 0x5eb0
    5e86:	0e 4b       	mov	r11,	r14	
    5e88:	3e 50 07 00 	add	#7,	r14	;#0x0007
    5e8c:	0f 43       	clr	r15		
    5e8e:	0d 4a       	mov	r10,	r13	
    5e90:	0d 5f       	add	r15,	r13	
    5e92:	ed 4e 00 00 	mov.b	@r14,	0(r13)	;0x0000(r13)
    5e96:	1f 53       	inc	r15		
    5e98:	3e 53       	add	#-1,	r14	;r3 As==11
    5e9a:	3f 92       	cmp	#8,	r15	;r2 As==11
    5e9c:	f8 23       	jnz	$-14     	;abs 0x5e8e
    5e9e:	3b 52       	add	#8,	r11	;r2 As==11
    5ea0:	07 3c       	jmp	$+16     	;abs 0x5eb0
    5ea2:	3e 40 c6 ab 	mov	#-21562,r14	;#0xabc6
    5ea6:	0f 4a       	mov	r10,	r15	
    5ea8:	b0 12 08 62 	call	#0x6208	
    5eac:	8a 43 1c 00 	mov	#0,	28(r10)	;r3 As==00, 0x001c(r10)
    5eb0:	5e 41 09 00 	mov.b	9(r1),	r14	;0x0009(r1)
    5eb4:	4e 93       	tst.b	r14		
    5eb6:	33 24       	jz	$+104    	;abs 0x5f1e
    5eb8:	81 93 0c 00 	tst	12(r1)		;0x000c(r1)
    5ebc:	0e 24       	jz	$+30     	;abs 0x5eda
    5ebe:	6f 4b       	mov.b	@r11,	r15	
    5ec0:	5d 4b 01 00 	mov.b	1(r11),	r13	;0x0001(r11)
    5ec4:	8d 10       	swpb	r13		
    5ec6:	0f 5d       	add	r13,	r15	
    5ec8:	8a 4f 1e 00 	mov	r15,	30(r10)	;0x001e(r10)
    5ecc:	2b 53       	incd	r11		
    5ece:	81 93 0a 00 	tst	10(r1)		;0x000a(r1)
    5ed2:	06 20       	jnz	$+14     	;abs 0x5ee0
    5ed4:	8a 4f 1c 00 	mov	r15,	28(r10)	;0x001c(r10)
    5ed8:	03 3c       	jmp	$+8      	;abs 0x5ee0
    5eda:	9a 4a 1c 00 	mov	28(r10),30(r10)	;0x001c(r10), 0x001e(r10)
    5ede:	1e 00 
    5ee0:	6e 93       	cmp.b	#2,	r14	;r3 As==10
    5ee2:	0d 20       	jnz	$+28     	;abs 0x5efe
    5ee4:	3e 40 c6 ab 	mov	#-21562,r14	;#0xabc6
    5ee8:	0f 4a       	mov	r10,	r15	
    5eea:	3f 52       	add	#8,	r15	;r2 As==11
    5eec:	b0 12 08 62 	call	#0x6208	
    5ef0:	da 4b 01 00 	mov.b	1(r11),	8(r10)	;0x0001(r11), 0x0008(r10)
    5ef4:	08 00 
    5ef6:	ea 4b 09 00 	mov.b	@r11,	9(r10)	;0x0009(r10)
    5efa:	2b 53       	incd	r11		
    5efc:	18 3c       	jmp	$+50     	;abs 0x5f2e
    5efe:	7e 90 03 00 	cmp.b	#3,	r14	;#0x0003
    5f02:	15 20       	jnz	$+44     	;abs 0x5f2e
    5f04:	0e 4a       	mov	r10,	r14	
    5f06:	3f 40 07 00 	mov	#7,	r15	;#0x0007
    5f0a:	0d 4b       	mov	r11,	r13	
    5f0c:	0d 5f       	add	r15,	r13	
    5f0e:	ee 4d 08 00 	mov.b	@r13,	8(r14)	;0x0008(r14)
    5f12:	3f 53       	add	#-1,	r15	;r3 As==11
    5f14:	1e 53       	inc	r14		
    5f16:	3f 93       	cmp	#-1,	r15	;r3 As==11
    5f18:	f8 23       	jnz	$-14     	;abs 0x5f0a
    5f1a:	3b 52       	add	#8,	r11	;r2 As==11
    5f1c:	08 3c       	jmp	$+18     	;abs 0x5f2e
    5f1e:	3e 40 c6 ab 	mov	#-21562,r14	;#0xabc6
    5f22:	0f 4a       	mov	r10,	r15	
    5f24:	3f 52       	add	#8,	r15	;r2 As==11
    5f26:	b0 12 08 62 	call	#0x6208	
    5f2a:	8a 43 1e 00 	mov	#0,	30(r10)	;r3 As==00, 0x001e(r10)
    5f2e:	0f 4b       	mov	r11,	r15	
    5f30:	0f 89       	sub	r9,	r15	
    5f32:	0e 48       	mov	r8,	r14	
    5f34:	0e 8f       	sub	r15,	r14	
    5f36:	8a 4e 36 00 	mov	r14,	54(r10)	;0x0036(r10)
    5f3a:	8a 4b 34 00 	mov	r11,	52(r10)	;0x0034(r10)
    5f3e:	08 9f       	cmp	r15,	r8	
    5f40:	01 34       	jge	$+4      	;abs 0x5f44
    5f42:	0f 43       	clr	r15		
    5f44:	31 50 0e 00 	add	#14,	r1	;#0x000e
    5f48:	38 41       	pop	r8		
    5f4a:	39 41       	pop	r9		
    5f4c:	3a 41       	pop	r10		
    5f4e:	3b 41       	pop	r11		
    5f50:	30 41       	ret			

00005f52 <parse>:
    5f52:	0b 12       	push	r11		
    5f54:	0a 12       	push	r10		
    5f56:	31 50 c8 ff 	add	#-56,	r1	;#0xffc8
    5f5a:	b0 12 ae 71 	call	#0x71ae	
    5f5e:	0b 4f       	mov	r15,	r11	
    5f60:	b0 12 be 71 	call	#0x71be	
    5f64:	0d 41       	mov	r1,	r13	
    5f66:	0e 4b       	mov	r11,	r14	
    5f68:	b0 12 ea 5d 	call	#0x5dea	
    5f6c:	0b 4f       	mov	r15,	r11	
    5f6e:	0f 93       	tst	r15		
    5f70:	02 20       	jnz	$+6      	;abs 0x5f76
    5f72:	3b 43       	mov	#-1,	r11	;r3 As==11
    5f74:	39 3c       	jmp	$+116    	;abs 0x5fe8
    5f76:	b0 12 88 71 	call	#0x7188	
    5f7a:	0f 93       	tst	r15		
    5f7c:	fa 27       	jz	$-10     	;abs 0x5f72
    5f7e:	5e 41 10 00 	mov.b	16(r1),	r14	;0x0010(r1)
    5f82:	7f 40 0b 00 	mov.b	#11,	r15	;#0x000b
    5f86:	b0 12 06 73 	call	#0x7306	
    5f8a:	5e 41 13 00 	mov.b	19(r1),	r14	;0x0013(r1)
    5f8e:	7f 40 07 00 	mov.b	#7,	r15	;#0x0007
    5f92:	b0 12 06 73 	call	#0x7306	
    5f96:	c1 93 17 00 	tst.b	23(r1)		;0x0017(r1)
    5f9a:	15 24       	jz	$+44     	;abs 0x5fc6
    5f9c:	1a 41 1c 00 	mov	28(r1),	r10	;0x001c(r1)
    5fa0:	b0 12 c8 59 	call	#0x59c8	
    5fa4:	0a 9f       	cmp	r15,	r10	
    5fa6:	03 24       	jz	$+8      	;abs 0x5fae
    5fa8:	b1 93 1c 00 	cmp	#-1,	28(r1)	;r3 As==11, 0x001c(r1)
    5fac:	e2 23       	jnz	$-58     	;abs 0x5f72
    5fae:	0e 41       	mov	r1,	r14	
    5fb0:	5f 41 17 00 	mov.b	23(r1),	r15	;0x0017(r1)
    5fb4:	b0 12 5a 5b 	call	#0x5b5a	
    5fb8:	4f 93       	tst.b	r15		
    5fba:	05 20       	jnz	$+12     	;abs 0x5fc6
    5fbc:	0e 41       	mov	r1,	r14	
    5fbe:	7f 40 0d 00 	mov.b	#13,	r15	;#0x000d
    5fc2:	b0 12 1c 73 	call	#0x731c	
    5fc6:	0e 41       	mov	r1,	r14	
    5fc8:	3e 52       	add	#8,	r14	;r2 As==11
    5fca:	7f 40 0c 00 	mov.b	#12,	r15	;#0x000c
    5fce:	b0 12 1c 73 	call	#0x731c	
    5fd2:	c1 93 15 00 	tst.b	21(r1)		;0x0015(r1)
    5fd6:	03 20       	jnz	$+8      	;abs 0x5fde
    5fd8:	5e 41 1a 00 	mov.b	26(r1),	r14	;0x001a(r1)
    5fdc:	01 3c       	jmp	$+4      	;abs 0x5fe0
    5fde:	3e 43       	mov	#-1,	r14	;r3 As==11
    5fe0:	7f 40 06 00 	mov.b	#6,	r15	;#0x0006
    5fe4:	b0 12 06 73 	call	#0x7306	
    5fe8:	0f 4b       	mov	r11,	r15	
    5fea:	31 50 38 00 	add	#56,	r1	;#0x0038
    5fee:	3a 41       	pop	r10		
    5ff0:	3b 41       	pop	r11		
    5ff2:	30 41       	ret			

00005ff4 <framer_802154_setup_params>:
    5ff4:	0b 12       	push	r11		
    5ff6:	0a 12       	push	r10		
    5ff8:	09 12       	push	r9		
    5ffa:	0a 4f       	mov	r15,	r10	
    5ffc:	49 4e       	mov.b	r14,	r9	
    5ffe:	0b 4d       	mov	r13,	r11	
    6000:	0f 93       	tst	r15		
    6002:	50 24       	jz	$+162    	;abs 0x60a4
    6004:	0d 93       	tst	r13		
    6006:	4e 24       	jz	$+158    	;abs 0x60a4
    6008:	7f 40 0b 00 	mov.b	#11,	r15	;#0x000b
    600c:	8a 12       	call	r10		
    600e:	cb 4f 10 00 	mov.b	r15,	16(r11)	;0x0010(r11)
    6012:	cb 43 12 00 	mov.b	#0,	18(r11)	;r3 As==00, 0x0012(r11)
    6016:	49 93       	tst.b	r9		
    6018:	03 24       	jz	$+8      	;abs 0x6020
    601a:	cb 43 13 00 	mov.b	#0,	19(r11)	;r3 As==00, 0x0013(r11)
    601e:	05 3c       	jmp	$+12     	;abs 0x602a
    6020:	7f 40 07 00 	mov.b	#7,	r15	;#0x0007
    6024:	8a 12       	call	r10		
    6026:	cb 4f 13 00 	mov.b	r15,	19(r11)	;0x0013(r11)
    602a:	cb 43 15 00 	mov.b	#0,	21(r11)	;r3 As==00, 0x0015(r11)
    602e:	7f 42       	mov.b	#8,	r15	;r2 As==11
    6030:	8a 12       	call	r10		
    6032:	cb 4f 16 00 	mov.b	r15,	22(r11)	;0x0016(r11)
    6036:	db 43 18 00 	mov.b	#1,	24(r11)	;r3 As==01, 0x0018(r11)
    603a:	cb 43 11 00 	mov.b	#0,	17(r11)	;r3 As==00, 0x0011(r11)
    603e:	7f 40 06 00 	mov.b	#6,	r15	;#0x0006
    6042:	8a 12       	call	r10		
    6044:	cb 4f 1a 00 	mov.b	r15,	26(r11)	;0x001a(r11)
    6048:	b0 12 c8 59 	call	#0x59c8	
    604c:	8b 4f 1e 00 	mov	r15,	30(r11)	;0x001e(r11)
    6050:	7f 40 09 00 	mov.b	#9,	r15	;#0x0009
    6054:	8a 12       	call	r10		
    6056:	1f 93       	cmp	#1,	r15	;r3 As==01
    6058:	03 20       	jnz	$+8      	;abs 0x6060
    605a:	cb 43 19 00 	mov.b	#0,	25(r11)	;r3 As==00, 0x0019(r11)
    605e:	03 3c       	jmp	$+8      	;abs 0x6066
    6060:	fb 40 03 00 	mov.b	#3,	25(r11)	;#0x0003, 0x0019(r11)
    6064:	19 00 
    6066:	b0 12 c8 59 	call	#0x59c8	
    606a:	8b 4f 1c 00 	mov	r15,	28(r11)	;0x001c(r11)
    606e:	7f 40 0a 00 	mov.b	#10,	r15	;#0x000a
    6072:	8a 12       	call	r10		
    6074:	1f 93       	cmp	#1,	r15	;r3 As==01
    6076:	03 20       	jnz	$+8      	;abs 0x607e
    6078:	cb 43 17 00 	mov.b	#0,	23(r11)	;r3 As==00, 0x0017(r11)
    607c:	08 3c       	jmp	$+18     	;abs 0x608e
    607e:	49 93       	tst.b	r9		
    6080:	03 24       	jz	$+8      	;abs 0x6088
    6082:	eb 43 17 00 	mov.b	#2,	23(r11)	;r3 As==10, 0x0017(r11)
    6086:	03 3c       	jmp	$+8      	;abs 0x608e
    6088:	fb 40 03 00 	mov.b	#3,	23(r11)	;#0x0003, 0x0017(r11)
    608c:	17 00 
    608e:	eb 93 19 00 	cmp.b	#2,	25(r11)	;r3 As==10, 0x0019(r11)
    6092:	03 24       	jz	$+8      	;abs 0x609a
    6094:	eb 93 17 00 	cmp.b	#2,	23(r11)	;r3 As==10, 0x0017(r11)
    6098:	03 20       	jnz	$+8      	;abs 0x60a0
    609a:	db 43 14 00 	mov.b	#1,	20(r11)	;r3 As==01, 0x0014(r11)
    609e:	02 3c       	jmp	$+6      	;abs 0x60a4
    60a0:	cb 43 14 00 	mov.b	#0,	20(r11)	;r3 As==00, 0x0014(r11)
    60a4:	39 41       	pop	r9		
    60a6:	3a 41       	pop	r10		
    60a8:	3b 41       	pop	r11		
    60aa:	30 41       	ret			

000060ac <create_frame>:
    60ac:	0b 12       	push	r11		
    60ae:	0a 12       	push	r10		
    60b0:	31 50 c8 ff 	add	#-56,	r1	;#0xffc8
    60b4:	0a 4f       	mov	r15,	r10	
    60b6:	b0 12 c8 59 	call	#0x59c8	
    60ba:	3f 93       	cmp	#-1,	r15	;r3 As==11
    60bc:	02 20       	jnz	$+6      	;abs 0x60c2
    60be:	3b 43       	mov	#-1,	r11	;r3 As==11
    60c0:	40 3c       	jmp	$+130    	;abs 0x6142
    60c2:	3d 40 38 00 	mov	#56,	r13	;#0x0038
    60c6:	0e 43       	clr	r14		
    60c8:	0f 41       	mov	r1,	r15	
    60ca:	b0 12 ac a8 	call	#0xa8ac	
    60ce:	b0 12 46 73 	call	#0x7346	
    60d2:	0d 41       	mov	r1,	r13	
    60d4:	4e 4f       	mov.b	r15,	r14	
    60d6:	3f 40 12 73 	mov	#29458,	r15	;#0x7312
    60da:	b0 12 f4 5f 	call	#0x5ff4	
    60de:	b0 12 46 73 	call	#0x7346	
    60e2:	4f 93       	tst.b	r15		
    60e4:	05 24       	jz	$+12     	;abs 0x60f0
    60e6:	f1 43 00 00 	mov.b	#-1,	0(r1)	;r3 As==11, 0x0000(r1)
    60ea:	f1 43 01 00 	mov.b	#-1,	1(r1)	;r3 As==11, 0x0001(r1)
    60ee:	08 3c       	jmp	$+18     	;abs 0x6100
    60f0:	7f 40 0d 00 	mov.b	#13,	r15	;#0x000d
    60f4:	b0 12 34 73 	call	#0x7334	
    60f8:	0e 4f       	mov	r15,	r14	
    60fa:	0f 41       	mov	r1,	r15	
    60fc:	b0 12 08 62 	call	#0x6208	
    6100:	7f 40 0c 00 	mov.b	#12,	r15	;#0x000c
    6104:	b0 12 34 73 	call	#0x7334	
    6108:	0e 4f       	mov	r15,	r14	
    610a:	0f 41       	mov	r1,	r15	
    610c:	3f 52       	add	#8,	r15	;r2 As==11
    610e:	b0 12 08 62 	call	#0x6208	
    6112:	b0 12 be 71 	call	#0x71be	
    6116:	81 4f 34 00 	mov	r15,	52(r1)	;0x0034(r1)
    611a:	b0 12 ae 71 	call	#0x71ae	
    611e:	81 4f 36 00 	mov	r15,	54(r1)	;0x0036(r1)
    6122:	0f 41       	mov	r1,	r15	
    6124:	b0 12 82 5b 	call	#0x5b82	
    6128:	0b 4f       	mov	r15,	r11	
    612a:	0a 93       	tst	r10		
    612c:	0a 24       	jz	$+22     	;abs 0x6142
    612e:	b0 12 1c 72 	call	#0x721c	
    6132:	0f 93       	tst	r15		
    6134:	c4 27       	jz	$-118    	;abs 0x60be
    6136:	b0 12 a8 71 	call	#0x71a8	
    613a:	0e 4f       	mov	r15,	r14	
    613c:	0f 41       	mov	r1,	r15	
    613e:	b0 12 4a 5c 	call	#0x5c4a	
    6142:	0f 4b       	mov	r11,	r15	
    6144:	31 50 38 00 	add	#56,	r1	;#0x0038
    6148:	3a 41       	pop	r10		
    614a:	3b 41       	pop	r11		
    614c:	30 41       	ret			

0000614e <create>:
    614e:	1f 43       	mov	#1,	r15	;r3 As==01
    6150:	b0 12 ac 60 	call	#0x60ac	
    6154:	30 41       	ret			

00006156 <hdr_length>:
    6156:	0f 43       	clr	r15		
    6158:	b0 12 ac 60 	call	#0x60ac	
    615c:	30 41       	ret			

0000615e <leds_arch_init>:
    615e:	f2 d0 70 00 	bis.b	#112,	&0x0032	;#0x0070
    6162:	32 00 
    6164:	f2 d0 70 00 	bis.b	#112,	&0x0031	;#0x0070
    6168:	31 00 
    616a:	30 41       	ret			

0000616c <leds_arch_get>:
    616c:	5e 42 31 00 	mov.b	&0x0031,r14	
    6170:	7e b0 10 00 	bit.b	#16,	r14	;#0x0010
    6174:	02 24       	jz	$+6      	;abs 0x617a
    6176:	4f 43       	clr.b	r15		
    6178:	02 3c       	jmp	$+6      	;abs 0x617e
    617a:	7f 40 10 00 	mov.b	#16,	r15	;#0x0010
    617e:	7e b0 20 00 	bit.b	#32,	r14	;#0x0020
    6182:	02 24       	jz	$+6      	;abs 0x6188
    6184:	4d 43       	clr.b	r13		
    6186:	02 3c       	jmp	$+6      	;abs 0x618c
    6188:	7d 40 20 00 	mov.b	#32,	r13	;#0x0020
    618c:	4f dd       	bis.b	r13,	r15	
    618e:	7e f0 40 00 	and.b	#64,	r14	;#0x0040
    6192:	02 24       	jz	$+6      	;abs 0x6198
    6194:	4e 43       	clr.b	r14		
    6196:	02 3c       	jmp	$+6      	;abs 0x619c
    6198:	7e 40 40 00 	mov.b	#64,	r14	;#0x0040
    619c:	4f de       	bis.b	r14,	r15	
    619e:	30 41       	ret			

000061a0 <leds_arch_set>:
    61a0:	5e 42 31 00 	mov.b	&0x0031,r14	
    61a4:	7e f0 8f ff 	and.b	#-113,	r14	;#0xff8f
    61a8:	7f b0 10 00 	bit.b	#16,	r15	;#0x0010
    61ac:	02 24       	jz	$+6      	;abs 0x61b2
    61ae:	4d 43       	clr.b	r13		
    61b0:	02 3c       	jmp	$+6      	;abs 0x61b6
    61b2:	7d 40 10 00 	mov.b	#16,	r13	;#0x0010
    61b6:	4e dd       	bis.b	r13,	r14	
    61b8:	7f b0 20 00 	bit.b	#32,	r15	;#0x0020
    61bc:	02 24       	jz	$+6      	;abs 0x61c2
    61be:	4d 43       	clr.b	r13		
    61c0:	02 3c       	jmp	$+6      	;abs 0x61c6
    61c2:	7d 40 20 00 	mov.b	#32,	r13	;#0x0020
    61c6:	4d de       	bis.b	r14,	r13	
    61c8:	7f f0 40 00 	and.b	#64,	r15	;#0x0040
    61cc:	02 24       	jz	$+6      	;abs 0x61d2
    61ce:	4f 43       	clr.b	r15		
    61d0:	02 3c       	jmp	$+6      	;abs 0x61d6
    61d2:	7f 40 40 00 	mov.b	#64,	r15	;#0x0040
    61d6:	4f dd       	bis.b	r13,	r15	
    61d8:	c2 4f 31 00 	mov.b	r15,	&0x0031	
    61dc:	30 41       	ret			

000061de <leds_init>:
    61de:	b0 12 5e 61 	call	#0x615e	
    61e2:	30 41       	ret			

000061e4 <leds_on>:
    61e4:	0b 12       	push	r11		
    61e6:	4b 4f       	mov.b	r15,	r11	
    61e8:	b0 12 6c 61 	call	#0x616c	
    61ec:	4f db       	bis.b	r11,	r15	
    61ee:	b0 12 a0 61 	call	#0x61a0	
    61f2:	3b 41       	pop	r11		
    61f4:	30 41       	ret			

000061f6 <leds_off>:
    61f6:	0b 12       	push	r11		
    61f8:	4b 4f       	mov.b	r15,	r11	
    61fa:	b0 12 6c 61 	call	#0x616c	
    61fe:	4f cb       	bic.b	r11,	r15	
    6200:	b0 12 a0 61 	call	#0x61a0	
    6204:	3b 41       	pop	r11		
    6206:	30 41       	ret			

00006208 <linkaddr_copy>:
    6208:	3d 42       	mov	#8,	r13	;r2 As==11
    620a:	b0 12 b2 a7 	call	#0xa7b2	
    620e:	30 41       	ret			

00006210 <linkaddr_cmp>:
    6210:	3d 42       	mov	#8,	r13	;r2 As==11
    6212:	b0 12 82 a7 	call	#0xa782	
    6216:	5e 43       	mov.b	#1,	r14	;r3 As==01
    6218:	0f 93       	tst	r15		
    621a:	01 24       	jz	$+4      	;abs 0x621e
    621c:	4e 43       	clr.b	r14		
    621e:	4f 4e       	mov.b	r14,	r15	
    6220:	30 41       	ret			

00006222 <linkaddr_set_node_addr>:
    6222:	0e 4f       	mov	r15,	r14	
    6224:	3f 40 ea 2d 	mov	#11754,	r15	;#0x2dea
    6228:	b0 12 08 62 	call	#0x6208	
    622c:	30 41       	ret			

0000622e <list_init>:
    622e:	8f 43 00 00 	mov	#0,	0(r15)	;r3 As==00, 0x0000(r15)
    6232:	30 41       	ret			

00006234 <list_head>:
    6234:	2f 4f       	mov	@r15,	r15	
    6236:	30 41       	ret			

00006238 <list_tail>:
    6238:	2f 4f       	mov	@r15,	r15	
    623a:	0f 93       	tst	r15		
    623c:	02 20       	jnz	$+6      	;abs 0x6242
    623e:	30 41       	ret			
    6240:	0f 4e       	mov	r14,	r15	
    6242:	2e 4f       	mov	@r15,	r14	
    6244:	0e 93       	tst	r14		
    6246:	fc 23       	jnz	$-6      	;abs 0x6240
    6248:	30 41       	ret			

0000624a <list_remove>:
    624a:	0b 12       	push	r11		
    624c:	2d 4f       	mov	@r15,	r13	
    624e:	0d 93       	tst	r13		
    6250:	14 24       	jz	$+42     	;abs 0x627a
    6252:	0c 43       	clr	r12		
    6254:	01 3c       	jmp	$+4      	;abs 0x6258
    6256:	0d 4b       	mov	r11,	r13	
    6258:	0d 9e       	cmp	r14,	r13	
    625a:	0b 20       	jnz	$+24     	;abs 0x6272
   625c:	2e 4d       	mov	@r13,	r14	
    625e:	0c 93       	tst	r12		
    6260:	03 20       	jnz	$+8      	;abs 0x6268
    6262:	8f 4e 00 00 	mov	r14,	0(r15)	;0x0000(r15)
    6266:	02 3c       	jmp	$+6      	;abs 0x626c
    6268:	8c 4e 00 00 	mov	r14,	0(r12)	;0x0000(r12)
    626c:	8d 43 00 00 	mov	#0,	0(r13)	;r3 As==00, 0x0000(r13)
    6270:	04 3c       	jmp	$+10     	;abs 0x627a
    6272:	2b 4d       	mov	@r13,	r11	
    6274:	0c 4d       	mov	r13,	r12	
    6276:	0b 93       	tst	r11		
    6278:	ee 23       	jnz	$-34     	;abs 0x6256
    627a:	3b 41       	pop	r11		
    627c:	30 41       	ret			

0000627e <list_add>:
    627e:	0b 12       	push	r11		
    6280:	0a 12       	push	r10		
    6282:	0a 4f       	mov	r15,	r10	
    6284:	0b 4e       	mov	r14,	r11	
    6286:	b0 12 4a 62 	call	#0x624a	
    628a:	8b 43 00 00 	mov	#0,	0(r11)	;r3 As==00, 0x0000(r11)
    628e:	0f 4a       	mov	r10,	r15	
    6290:	b0 12 38 62 	call	#0x6238	
    6294:	0f 93       	tst	r15		
    6296:	03 20       	jnz	$+8      	;abs 0x629e
    6298:	8a 4b 00 00 	mov	r11,	0(r10)	;0x0000(r10)
    629c:	02 3c       	jmp	$+6      	;abs 0x62a2
    629e:	8f 4b 00 00 	mov	r11,	0(r15)	;0x0000(r15)
    62a2:	3a 41       	pop	r10		
    62a4:	3b 41       	pop	r11		
    62a6:	30 41       	ret			

000062a8 <list_length>:
    62a8:	2e 4f       	mov	@r15,	r14	
    62aa:	0f 43       	clr	r15		
    62ac:	02 3c       	jmp	$+6      	;abs 0x62b2
    62ae:	1f 53       	inc	r15		
    62b0:	2e 4e       	mov	@r14,	r14	
    62b2:	0e 93       	tst	r14		
    62b4:	fc 23       	jnz	$-6      	;abs 0x62ae
    62b6:	30 41       	ret			

000062b8 <list_item_next>:
    62b8:	0f 93       	tst	r15		
    62ba:	02 24       	jz	$+6      	;abs 0x62c0
    62bc:	2f 4f       	mov	@r15,	r15	
    62be:	30 41       	ret			
    62c0:	0f 43       	clr	r15		
    62c2:	30 41       	ret			

000062c4 <log_lladdr>:
    62c4:	0b 12       	push	r11		
    62c6:	0a 12       	push	r10		
    62c8:	0a 4f       	mov	r15,	r10	
    62ca:	0f 93       	tst	r15		
    62cc:	0d 20       	jnz	$+28     	;abs 0x62e8
    62ce:	30 12 ce ab 	push	#-21554	;#0xabce
    62d2:	b0 12 cc 9e 	call	#0x9ecc	
    62d6:	21 53       	incd	r1		
    62d8:	14 3c       	jmp	$+42     	;abs 0x6302
    62da:	1b b3       	bit	#1,	r11	;r3 As==01
    62dc:	06 20       	jnz	$+14     	;abs 0x62ea
    62de:	3f 40 2e 00 	mov	#46,	r15	;#0x002e
    62e2:	b0 12 e0 7c 	call	#0x7ce0	
    62e6:	01 3c       	jmp	$+4      	;abs 0x62ea
    62e8:	0b 43       	clr	r11		
    62ea:	0f 4a       	mov	r10,	r15	
    62ec:	0f 5b       	add	r11,	r15	
    62ee:	6f 4f       	mov.b	@r15,	r15	
    62f0:	0f 12       	push	r15		
    62f2:	30 12 dd ab 	push	#-21539	;#0xabdd
    62f6:	b0 12 cc 9e 	call	#0x9ecc	
    62fa:	21 52       	add	#4,	r1	;r2 As==10
    62fc:	1b 53       	inc	r11		
    62fe:	3b 92       	cmp	#8,	r11	;r2 As==11
    6300:	ec 23       	jnz	$-38     	;abs 0x62da
    6302:	3a 41       	pop	r10		
    6304:	3b 41       	pop	r11		
    6306:	30 41       	ret			

00006308 <mac_sequence_init>:
    6308:	b0 12 f4 77 	call	#0x77f4	
    630c:	c2 4f 48 23 	mov.b	r15,	&0x2348	
    6310:	30 41       	ret			

00006312 <mac_sequence_set_dsn>:
    6312:	5e 42 48 23 	mov.b	&0x2348,r14	
    6316:	4f 4e       	mov.b	r14,	r15	
    6318:	5f 53       	inc.b	r15		
    631a:	c2 4f 48 23 	mov.b	r15,	&0x2348	
    631e:	4e 4e       	mov.b	r14,	r14	
    6320:	7f 40 06 00 	mov.b	#6,	r15	;#0x0006
    6324:	b0 12 06 73 	call	#0x7306	
    6328:	30 41       	ret			

0000632a <mac_sequence_is_duplicate>:
    632a:	0b 12       	push	r11		
    632c:	0a 12       	push	r10		
    632e:	09 12       	push	r9		
    6330:	08 12       	push	r8		
    6332:	07 12       	push	r7		
    6334:	b0 12 48 4f 	call	#0x4f48	
    6338:	0a 4e       	mov	r14,	r10	
    633a:	0b 4f       	mov	r15,	r11	
    633c:	09 43       	clr	r9		
    633e:	7f 40 0c 00 	mov.b	#12,	r15	;#0x000c
    6342:	b0 12 34 73 	call	#0x7334	
    6346:	0d 49       	mov	r9,	r13	
    6348:	0d 5d       	rla	r13		
    634a:	0e 4d       	mov	r13,	r14	
    634c:	0e 5e       	rla	r14		
    634e:	0e 5e       	rla	r14		
    6350:	0e 5e       	rla	r14		
    6352:	07 4e       	mov	r14,	r7	
    6354:	07 8d       	sub	r13,	r7	
    6356:	08 47       	mov	r7,	r8	
    6358:	38 50 4a 23 	add	#9034,	r8	;#0x234a
    635c:	0e 48       	mov	r8,	r14	
    635e:	b0 12 10 62 	call	#0x6210	
    6362:	4f 93       	tst.b	r15		
    6364:	19 24       	jz	$+52     	;abs 0x6398
    6366:	7f 40 06 00 	mov.b	#6,	r15	;#0x0006
    636a:	b0 12 12 73 	call	#0x7312	
    636e:	5e 47 56 23 	mov.b	9046(r7),r14	;0x2356(r7)
    6372:	0f 9e       	cmp	r14,	r15	
    6374:	02 24       	jz	$+6      	;abs 0x637a
    6376:	0f 43       	clr	r15		
    6378:	14 3c       	jmp	$+42     	;abs 0x63a2
    637a:	0e 4a       	mov	r10,	r14	
    637c:	0f 4b       	mov	r11,	r15	
    637e:	1e 88 08 00 	sub	8(r8),	r14	;0x0008(r8)
    6382:	1f 78 0a 00 	subc	10(r8),	r15	;0x000a(r8)
    6386:	1d 43       	mov	#1,	r13	;r3 As==01
    6388:	0f 93       	tst	r15		
    638a:	03 20       	jnz	$+8      	;abs 0x6392
    638c:	3e 90 01 0a 	cmp	#2561,	r14	;#0x0a01
    6390:	01 28       	jnc	$+4      	;abs 0x6394
    6392:	0d 43       	clr	r13		
    6394:	0f 4d       	mov	r13,	r15	
    6396:	05 3c       	jmp	$+12     	;abs 0x63a2
    6398:	19 53       	inc	r9		
    639a:	39 90 10 00 	cmp	#16,	r9	;#0x0010
    639e:	cf 23       	jnz	$-96     	;abs 0x633e
    63a0:	ea 3f       	jmp	$-42     	;abs 0x6376
    63a2:	37 41       	pop	r7		
    63a4:	38 41       	pop	r8		
    63a6:	39 41       	pop	r9		
    63a8:	3a 41       	pop	r10		
    63aa:	3b 41       	pop	r11		
    63ac:	30 41       	ret			

000063ae <mac_sequence_register_seqno>:
    63ae:	0b 12       	push	r11		
    63b0:	0b 43       	clr	r11		
    63b2:	7f 40 0c 00 	mov.b	#12,	r15	;#0x000c
    63b6:	b0 12 34 73 	call	#0x7334	
    63ba:	0d 4b       	mov	r11,	r13	
    63bc:	0d 5d       	rla	r13		
    63be:	0e 4d       	mov	r13,	r14	
    63c0:	0e 5e       	rla	r14		
    63c2:	0e 5e       	rla	r14		
    63c4:	0e 5e       	rla	r14		
    63c6:	0e 8d       	sub	r13,	r14	
    63c8:	3e 50 4a 23 	add	#9034,	r14	;#0x234a
    63cc:	b0 12 10 62 	call	#0x6210	
    63d0:	0e 4b       	mov	r11,	r14	
    63d2:	1e 53       	inc	r14		
    63d4:	4f 93       	tst.b	r15		
    63d6:	04 20       	jnz	$+10     	;abs 0x63e0
    63d8:	0b 4e       	mov	r14,	r11	
    63da:	3e 90 10 00 	cmp	#16,	r14	;#0x0010
    63de:	e9 23       	jnz	$-44     	;abs 0x63b2
    63e0:	0f 4e       	mov	r14,	r15	
    63e2:	2f 83       	decd	r15		
    63e4:	0f 5f       	rla	r15		
    63e6:	0b 4f       	mov	r15,	r11	
    63e8:	0b 5b       	rla	r11		
    63ea:	0b 5b       	rla	r11		
    63ec:	0b 5b       	rla	r11		
    63ee:	0b 8f       	sub	r15,	r11	
    63f0:	3b 50 4a 23 	add	#9034,	r11	;#0x234a
    63f4:	0a 3c       	jmp	$+22     	;abs 0x640a
    63f6:	3d 40 0e 00 	mov	#14,	r13	;#0x000e
    63fa:	0e 4b       	mov	r11,	r14	
    63fc:	0f 4b       	mov	r11,	r15	
    63fe:	3f 50 0e 00 	add	#14,	r15	;#0x000e
    6402:	b0 12 b2 a7 	call	#0xa7b2	
    6406:	3b 50 f2 ff 	add	#-14,	r11	;#0xfff2
    640a:	3b 90 3c 23 	cmp	#9020,	r11	;#0x233c
    640e:	f3 23       	jnz	$-24     	;abs 0x63f6
    6410:	7f 40 06 00 	mov.b	#6,	r15	;#0x0006
    6414:	b0 12 12 73 	call	#0x7312	
    6418:	c2 4f 56 23 	mov.b	r15,	&0x2356	
    641c:	b0 12 48 4f 	call	#0x4f48	
    6420:	82 4e 52 23 	mov	r14,	&0x2352	
    6424:	82 4f 54 23 	mov	r15,	&0x2354	
    6428:	7f 40 0c 00 	mov.b	#12,	r15	;#0x000c
    642c:	b0 12 34 73 	call	#0x7334	
    6430:	0e 4f       	mov	r15,	r14	
    6432:	3f 40 4a 23 	mov	#9034,	r15	;#0x234a
    6436:	b0 12 08 62 	call	#0x6208	
    643a:	3b 41       	pop	r11		
    643c:	30 41       	ret			

0000643e <mac_call_sent_callback>:
    643e:	0b 12       	push	r11		
    6440:	0b 4f       	mov	r15,	r11	
    6442:	0f 4e       	mov	r14,	r15	
    6444:	0e 4d       	mov	r13,	r14	
    6446:	0d 4c       	mov	r12,	r13	
    6448:	0b 93       	tst	r11		
    644a:	01 24       	jz	$+4      	;abs 0x644e
    644c:	8b 12       	call	r11		
    644e:	3b 41       	pop	r11		
    6450:	30 41       	ret			

00006452 <memb_init>:
    6452:	0b 12       	push	r11		
    6454:	0b 4f       	mov	r15,	r11	
    6456:	1d 4f 02 00 	mov	2(r15),	r13	;0x0002(r15)
    645a:	0e 43       	clr	r14		
    645c:	1f 4f 04 00 	mov	4(r15),	r15	;0x0004(r15)
    6460:	b0 12 ac a8 	call	#0xa8ac	
    6464:	02 12       	push	r2		
    6466:	32 c2       	dint			
    6468:	03 43       	nop			
    646a:	92 4b 02 00 	mov	2(r11),	&0x0132	;0x0002(r11)
    646e:	32 01 
    6470:	a2 4b 38 01 	mov	@r11,	&0x0138	
    6474:	1d 42 3a 01 	mov	&0x013a,r13	
    6478:	32 41       	pop	r2		
    647a:	0e 43       	clr	r14		
    647c:	1f 4b 06 00 	mov	6(r11),	r15	;0x0006(r11)
    6480:	b0 12 ac a8 	call	#0xa8ac	
    6484:	3b 41       	pop	r11		
    6486:	30 41       	ret			

00006488 <memb_alloc>:
    6488:	0d 4f       	mov	r15,	r13	
    648a:	1c 4f 02 00 	mov	2(r15),	r12	;0x0002(r15)
    648e:	0e 43       	clr	r14		
    6490:	16 3c       	jmp	$+46     	;abs 0x64be
    6492:	1f 4d 04 00 	mov	4(r13),	r15	;0x0004(r13)
    6496:	0f 5e       	add	r14,	r15	
    6498:	cf 93 00 00 	tst.b	0(r15)		;0x0000(r15)
    649c:	0f 20       	jnz	$+32     	;abs 0x64bc
    649e:	df 43 00 00 	mov.b	#1,	0(r15)	;r3 As==01, 0x0000(r15)
    64a2:	02 12       	push	r2		
    64a4:	32 c2       	dint			
    64a6:	03 43       	nop			
    64a8:	82 4e 32 01 	mov	r14,	&0x0132	
    64ac:	a2 4d 38 01 	mov	@r13,	&0x0138	
    64b0:	1f 42 3a 01 	mov	&0x013a,r15	
    64b4:	32 41       	pop	r2		
    64b6:	1f 5d 06 00 	add	6(r13),	r15	;0x0006(r13)
    64ba:	30 41       	ret			
    64bc:	1e 53       	inc	r14		
    64be:	0e 9c       	cmp	r12,	r14	
    64c0:	e8 23       	jnz	$-46     	;abs 0x6492
    64c2:	0f 43       	clr	r15		
    64c4:	30 41       	ret			

000064c6 <memb_free>:
    64c6:	0b 12       	push	r11		
    64c8:	1c 4f 06 00 	mov	6(r15),	r12	;0x0006(r15)
    64cc:	1b 4f 02 00 	mov	2(r15),	r11	;0x0002(r15)
    64d0:	0d 43       	clr	r13		
    64d2:	0d 3c       	jmp	$+28     	;abs 0x64ee
    64d4:	0c 9e       	cmp	r14,	r12	
    64d6:	09 20       	jnz	$+20     	;abs 0x64ea
    64d8:	1d 5f 04 00 	add	4(r15),	r13	;0x0004(r15)
    64dc:	cd 93 00 00 	tst.b	0(r13)		;0x0000(r13)
    64e0:	08 24       	jz	$+18     	;abs 0x64f2
    64e2:	cd 43 00 00 	mov.b	#0,	0(r13)	;r3 As==00, 0x0000(r13)
    64e6:	0f 43       	clr	r15		
    64e8:	05 3c       	jmp	$+12     	;abs 0x64f4
    64ea:	2c 5f       	add	@r15,	r12	
    64ec:	1d 53       	inc	r13		
    64ee:	0d 9b       	cmp	r11,	r13	
    64f0:	f1 23       	jnz	$-28     	;abs 0x64d4
    64f2:	3f 43       	mov	#-1,	r15	;r3 As==11
    64f4:	3b 41       	pop	r11		
    64f6:	30 41       	ret			

000064f8 <memb_inmemb>:
    64f8:	1c 4f 06 00 	mov	6(r15),	r12	;0x0006(r15)
    64fc:	0e 9c       	cmp	r12,	r14	
    64fe:	0f 28       	jnc	$+32     	;abs 0x651e
    6500:	02 12       	push	r2		
    6502:	32 c2       	dint			
    6504:	03 43       	nop			
    6506:	a2 4f 32 01 	mov	@r15,	&0x0132	
    650a:	92 4f 02 00 	mov	2(r15),	&0x0138	;0x0002(r15)
    650e:	38 01 
    6510:	1d 42 3a 01 	mov	&0x013a,r13	
    6514:	32 41       	pop	r2		
    6516:	0d 5c       	add	r12,	r13	
    6518:	1f 43       	mov	#1,	r15	;r3 As==01
    651a:	0e 9d       	cmp	r13,	r14	
    651c:	01 28       	jnc	$+4      	;abs 0x6520
    651e:	0f 43       	clr	r15		
    6520:	30 41       	ret			

00006522 <msp430_init_dco>:
    6522:	f2 40 a4 ff 	mov.b	#-92,	&0x0057	;#0xffa4
    6526:	57 00 
    6528:	c2 43 58 00 	mov.b	#0,	&0x0058	;r3 As==00
    652c:	f2 d0 30 00 	bis.b	#48,	&0x0057	;#0x0030
    6530:	57 00 
    6532:	3f 43       	mov	#-1,	r15	;r3 As==11
    6534:	03 43       	nop			
    6536:	3f 53       	add	#-1,	r15	;r3 As==11
    6538:	fd 23       	jnz	$-4      	;abs 0x6534
    653a:	b2 40 00 51 	mov	#20736,	&0x0166	;#0x5100
    653e:	66 01 
    6540:	b2 40 24 02 	mov	#548,	&0x0160	;#0x0224
    6544:	60 01 
    6546:	0e 43       	clr	r14		
    6548:	92 b3 66 01 	bit	#1,	&0x0166	;r3 As==01
    654c:	fd 27       	jz	$-4      	;abs 0x6548
    654e:	92 c3 66 01 	bic	#1,	&0x0166	;r3 As==01
    6552:	1f 42 76 01 	mov	&0x0176,r15	
    6556:	0f 8e       	sub	r14,	r15	
    6558:	1e 42 76 01 	mov	&0x0176,r14	
    655c:	3f 90 b8 03 	cmp	#952,	r15	;#0x03b8
    6560:	19 24       	jz	$+52     	;abs 0x6594
    6562:	3f 90 b9 03 	cmp	#953,	r15	;#0x03b9
    6566:	0a 28       	jnc	$+22     	;abs 0x657c
    6568:	f2 53 56 00 	add.b	#-1,	&0x0056	;r3 As==11
    656c:	5f 42 56 00 	mov.b	&0x0056,r15	
    6570:	7f 93       	cmp.b	#-1,	r15	;r3 As==11
    6572:	ea 23       	jnz	$-42     	;abs 0x6548
    6574:	5f 42 57 00 	mov.b	&0x0057,r15	
    6578:	7f 53       	add.b	#-1,	r15	;r3 As==11
    657a:	09 3c       	jmp	$+20     	;abs 0x658e
    657c:	d2 53 56 00 	inc.b	&0x0056	
    6580:	5f 42 56 00 	mov.b	&0x0056,r15	
    6584:	4f 93       	tst.b	r15		
    6586:	e0 23       	jnz	$-62     	;abs 0x6548
    6588:	5f 42 57 00 	mov.b	&0x0057,r15	
    658c:	5f 53       	inc.b	r15		
    658e:	c2 4f 57 00 	mov.b	r15,	&0x0057	
    6592:	da 3f       	jmp	$-74     	;abs 0x6548
    6594:	82 43 66 01 	mov	#0,	&0x0166	;r3 As==00
    6598:	82 43 60 01 	mov	#0,	&0x0160	;r3 As==00
    659c:	f2 f0 cf ff 	and.b	#-49,	&0x0057	;#0xffcf
    65a0:	57 00 
    65a2:	30 41       	ret			

000065a4 <msp430_add_lpm_req>:
    65a4:	1f 93       	cmp	#1,	r15	;r3 As==01
    65a6:	01 24       	jz	$+4      	;abs 0x65aa
    65a8:	02 34       	jge	$+6      	;abs 0x65ae
    65aa:	92 53 f2 2d 	inc	&0x2df2	
    65ae:	30 41       	ret			

000065b0 <msp430_cpu_init>:
    65b0:	32 c2       	dint			
    65b2:	03 43       	nop			
    65b4:	b0 12 b0 7e 	call	#0x7eb0	
    65b8:	c2 43 25 00 	mov.b	#0,	&0x0025	;r3 As==00
    65bc:	c2 43 2d 00 	mov.b	#0,	&0x002d	;r3 As==00
    65c0:	b0 12 22 65 	call	#0x6522	
    65c4:	32 d2       	eint			
    65c6:	1f 42 8e 11 	mov	&0x118e,r15	
    65ca:	1f b3       	bit	#1,	r15	;r3 As==01
    65cc:	03 24       	jz	$+8      	;abs 0x65d4
    65ce:	1f 53       	inc	r15		
    65d0:	82 4f 8e 11 	mov	r15,	&0x118e	
    65d4:	82 43 f2 2d 	mov	#0,	&0x2df2	;r3 As==00
    65d8:	30 41       	ret			

000065da <splhigh_>:
    65da:	0f 42       	mov	r2,	r15	
    65dc:	32 c2       	dint			
    65de:	03 43       	nop			
    65e0:	3f f2       	and	#8,	r15	;r2 As==11
    65e2:	30 41       	ret			

000065e4 <msp430_sync_dco>:
    65e4:	b2 40 04 02 	mov	#516,	&0x0180	;#0x0204
    65e8:	80 01 
    65ea:	b2 40 00 51 	mov	#20736,	&0x018e	;#0x5100
    65ee:	8e 01 
    65f0:	b2 d0 20 00 	bis	#32,	&0x0180	;#0x0020
    65f4:	80 01 
    65f6:	92 c3 8e 01 	bic	#1,	&0x018e	;r3 As==01
    65fa:	92 b3 8e 01 	bit	#1,	&0x018e	;r3 As==01
    65fe:	fd 27       	jz	$-4      	;abs 0x65fa
    6600:	1e 42 9e 01 	mov	&0x019e,r14	
    6604:	92 c3 8e 01 	bic	#1,	&0x018e	;r3 As==01
    6608:	92 b3 8e 01 	bit	#1,	&0x018e	;r3 As==01
    660c:	fd 27       	jz	$-4      	;abs 0x6608
    660e:	1f 42 9e 01 	mov	&0x019e,r15	
    6612:	0f 8e       	sub	r14,	r15	
    6614:	82 43 80 01 	mov	#0,	&0x0180	;r3 As==00
    6618:	3f 90 78 00 	cmp	#120,	r15	;#0x0078
    661c:	0a 28       	jnc	$+22     	;abs 0x6632
    661e:	f2 53 56 00 	add.b	#-1,	&0x0056	;r3 As==11
    6622:	5f 42 56 00 	mov.b	&0x0056,r15	
    6626:	7f 93       	cmp.b	#-1,	r15	;r3 As==11
    6628:	12 20       	jnz	$+38     	;abs 0x664e
    662a:	5f 42 57 00 	mov.b	&0x0057,r15	
    662e:	7f 53       	add.b	#-1,	r15	;r3 As==11
    6630:	0c 3c       	jmp	$+26     	;abs 0x664a
    6632:	3f 90 77 00 	cmp	#119,	r15	;#0x0077
    6636:	0b 24       	jz	$+24     	;abs 0x664e
    6638:	d2 53 56 00 	inc.b	&0x0056	
    663c:	5f 42 56 00 	mov.b	&0x0056,r15	
    6640:	4f 93       	tst.b	r15		
    6642:	05 20       	jnz	$+12     	;abs 0x664e
    6644:	5f 42 57 00 	mov.b	&0x0057,r15	
    6648:	5f 53       	inc.b	r15		
    664a:	c2 4f 57 00 	mov.b	r15,	&0x0057	
    664e:	30 41       	ret			

00006650 <netstack_init>:
    6650:	92 12 64 ab 	call	&0xab64	
    6654:	92 12 b4 ab 	call	&0xabb4	
    6658:	92 12 d2 ae 	call	&0xaed2	
    665c:	30 41       	ret			

0000665e <node_id_init>:
    665e:	3f 40 f1 2d 	mov	#11761,	r15	;#0x2df1
    6662:	6e 4f       	mov.b	@r15,	r14	
    6664:	5f 4f ff ff 	mov.b	-1(r15),r15	;0xffff(r15)
    6668:	8f 10       	swpb	r15		
    666a:	0e 5f       	add	r15,	r14	
    666c:	82 4e 2a 24 	mov	r14,	&0x242a	
    6670:	30 41       	ret			

00006672 <process_thread_nullnet_example_process>:
    6672:	0b 12       	push	r11		
    6674:	0a 12       	push	r10		
    6676:	09 12       	push	r9		
    6678:	0a 4f       	mov	r15,	r10	
    667a:	2f 4f       	mov	@r15,	r15	
    667c:	0f 93       	tst	r15		
    667e:	04 24       	jz	$+10     	;abs 0x6688
    6680:	3f 90 7c 02 	cmp	#636,	r15	;#0x027c
    6684:	d6 20       	jnz	$+430    	;abs 0x6832
    6686:	dc 3c       	jmp	$+442    	;abs 0x6840
    6688:	b2 40 2a 24 	mov	#9258,	&0x2e1e	;#0x242a
    668c:	1e 2e 
    668e:	a2 43 20 2e 	mov	#2,	&0x2e20	;r3 As==10
    6692:	3f 40 56 68 	mov	#26710,	r15	;#0x6856
    6696:	b0 12 42 71 	call	#0x7142	
    669a:	30 12 68 ac 	push	#-21400	;#0xac68
    669e:	30 12 6c ac 	push	#-21396	;#0xac6c
    66a2:	30 12 71 ac 	push	#-21391	;#0xac71
    66a6:	b0 12 cc 9e 	call	#0x9ecc	
    66aa:	31 50 06 00 	add	#6,	r1	;#0x0006
    66ae:	30 12 80 ac 	push	#-21376	;#0xac80
    66b2:	b0 12 cc 9e 	call	#0x9ecc	
    66b6:	21 53       	incd	r1		
    66b8:	3f 40 ea 2d 	mov	#11754,	r15	;#0x2dea
    66bc:	b0 12 c4 62 	call	#0x62c4	
    66c0:	30 12 68 ac 	push	#-21400	;#0xac68
    66c4:	30 12 6c ac 	push	#-21396	;#0xac6c
    66c8:	30 12 71 ac 	push	#-21391	;#0xac71
    66cc:	b0 12 cc 9e 	call	#0x9ecc	
    66d0:	31 50 06 00 	add	#6,	r1	;#0x0006
    66d4:	3f 40 0a 00 	mov	#10,	r15	;#0x000a
    66d8:	b0 12 e0 7c 	call	#0x7ce0	
    66dc:	1b 42 2a 24 	mov	&0x242a,r11	
    66e0:	82 4b 46 25 	mov	r11,	&0x2546	
    66e4:	3e 40 64 00 	mov	#100,	r14	;#0x0064
    66e8:	0f 4b       	mov	r11,	r15	
    66ea:	b0 12 d4 a9 	call	#0xa9d4	
    66ee:	0f 12       	push	r15		
    66f0:	0b 12       	push	r11		
    66f2:	30 12 98 ac 	push	#-21352	;#0xac98
    66f6:	b0 12 cc 9e 	call	#0x9ecc	
    66fa:	31 50 06 00 	add	#6,	r1	;#0x0006
    66fe:	1f 42 2a 24 	mov	&0x242a,r15	
    6702:	3f 50 b4 21 	add	#8628,	r15	;#0x21b4
    6706:	cf 93 ff ff 	tst.b	-1(r15)	;0xffff(r15)
    670a:	93 24       	jz	$+296    	;abs 0x6832
    670c:	30 12 68 ac 	push	#-21400	;#0xac68
    6710:	30 12 6c ac 	push	#-21396	;#0xac6c
    6714:	30 12 71 ac 	push	#-21391	;#0xac71
    6718:	b0 12 cc 9e 	call	#0x9ecc	
    671c:	31 50 06 00 	add	#6,	r1	;#0x0006
    6720:	03 12       	push	#0		;r3 As==00
    6722:	30 12 80 00 	push	#128		;#0x0080
    6726:	30 12 b1 ac 	push	#-21327	;#0xacb1
    672a:	b0 12 cc 9e 	call	#0x9ecc	
    672e:	31 50 06 00 	add	#6,	r1	;#0x0006
    6732:	3f 40 0a 00 	mov	#10,	r15	;#0x000a
    6736:	b0 12 e0 7c 	call	#0x7ce0	
    673a:	1e 42 46 25 	mov	&0x2546,r14	
    673e:	0f 43       	clr	r15		
    6740:	b0 12 ba 99 	call	#0x99ba	
    6744:	3c 40 9a 99 	mov	#-26214,r12	;#0x999a
    6748:	3d 40 99 3f 	mov	#16281,	r13	;#0x3f99
    674c:	b0 12 f6 93 	call	#0x93f6	
    6750:	0c 43       	clr	r12		
    6752:	3d 40 00 43 	mov	#17152,	r13	;#0x4300
    6756:	b0 12 5a 93 	call	#0x935a	
    675a:	b0 12 34 8e 	call	#0x8e34	
    675e:	0d 4e       	mov	r14,	r13	
    6760:	0e 4f       	mov	r15,	r14	
    6762:	3f 40 48 25 	mov	#9544,	r15	;#0x2548
    6766:	b0 12 36 59 	call	#0x5936	
    676a:	ba 40 7c 02 	mov	#636,	0(r10)	;#0x027c, 0x0000(r10)
    676e:	00 00 
    6770:	65 3c       	jmp	$+204    	;abs 0x683c
    6772:	30 12 68 ac 	push	#-21400	;#0xac68
    6776:	30 12 6c ac 	push	#-21396	;#0xac6c
    677a:	30 12 71 ac 	push	#-21391	;#0xac71
    677e:	b0 12 cc 9e 	call	#0x9ecc	
    6782:	31 50 06 00 	add	#6,	r1	;#0x0006
    6786:	19 42 2a 24 	mov	&0x242a,r9	
    678a:	0b 49       	mov	r9,	r11	
    678c:	3b 53       	add	#-1,	r11	;r3 As==11
    678e:	0b 5b       	rla	r11		
    6790:	0e 4b       	mov	r11,	r14	
    6792:	0e 5e       	rla	r14		
    6794:	0e 5e       	rla	r14		
    6796:	0b 5e       	add	r14,	r11	
    6798:	3b 50 e4 19 	add	#6628,	r11	;#0x19e4
    679c:	3c 40 00 24 	mov	#9216,	r12	;#0x2400
    67a0:	3d 40 74 49 	mov	#18804,	r13	;#0x4974
    67a4:	1e 4b 06 00 	mov	6(r11),	r14	;0x0006(r11)
    67a8:	1f 4b 08 00 	mov	8(r11),	r15	;0x0008(r11)
    67ac:	b0 12 f6 93 	call	#0x93f6	
    67b0:	b0 12 76 8e 	call	#0x8e76	
    67b4:	0f 12       	push	r15		
    67b6:	0e 12       	push	r14		
    67b8:	0d 12       	push	r13		
    67ba:	0c 12       	push	r12		
    67bc:	3c 40 00 24 	mov	#9216,	r12	;#0x2400
    67c0:	3d 40 74 49 	mov	#18804,	r13	;#0x4974
    67c4:	1e 4b 02 00 	mov	2(r11),	r14	;0x0002(r11)
    67c8:	1f 4b 04 00 	mov	4(r11),	r15	;0x0004(r11)
    67cc:	b0 12 f6 93 	call	#0x93f6	
    67d0:	b0 12 76 8e 	call	#0x8e76	
    67d4:	0f 12       	push	r15		
    67d6:	0e 12       	push	r14		
    67d8:	0d 12       	push	r13		
    67da:	0c 12       	push	r12		
    67dc:	09 12       	push	r9		
    67de:	30 12 c2 ac 	push	#-21310	;#0xacc2
    67e2:	b0 12 cc 9e 	call	#0x9ecc	
    67e6:	31 50 14 00 	add	#20,	r1	;#0x0014
    67ea:	3f 40 0a 00 	mov	#10,	r15	;#0x000a
    67ee:	b0 12 e0 7c 	call	#0x7ce0	
    67f2:	3f 40 48 25 	mov	#9544,	r15	;#0x2548
    67f6:	b0 12 48 59 	call	#0x5948	
    67fa:	0f 43       	clr	r15		
    67fc:	92 12 d6 ae 	call	&0xaed6	
    6800:	3f 40 48 25 	mov	#9544,	r15	;#0x2548
    6804:	b0 12 48 59 	call	#0x5948	
    6808:	92 53 54 25 	inc	&0x2554	
    680c:	30 12 68 ac 	push	#-21400	;#0xac68
    6810:	30 12 6c ac 	push	#-21396	;#0xac6c
    6814:	30 12 71 ac 	push	#-21391	;#0xac71
    6818:	b0 12 cc 9e 	call	#0x9ecc	
    681c:	31 50 06 00 	add	#6,	r1	;#0x0006
    6820:	12 12 2a 24 	push	&0x242a	
    6824:	30 12 e8 ac 	push	#-21272	;#0xace8
    6828:	b0 12 cc 9e 	call	#0x9ecc	
    682c:	21 52       	add	#4,	r1	;r2 As==10
    682e:	92 12 bc ab 	call	&0xabbc	
    6832:	8a 43 00 00 	mov	#0,	0(r10)	;r3 As==00, 0x0000(r10)
    6836:	7f 40 03 00 	mov.b	#3,	r15	;#0x0003
    683a:	09 3c       	jmp	$+20     	;abs 0x684e
    683c:	5f 43       	mov.b	#1,	r15	;r3 As==01
    683e:	07 3c       	jmp	$+16     	;abs 0x684e
    6840:	3f 40 48 25 	mov	#9544,	r15	;#0x2548
    6844:	b0 12 5a 59 	call	#0x595a	
    6848:	0f 93       	tst	r15		
    684a:	f8 27       	jz	$-14     	;abs 0x683c
    684c:	92 3f       	jmp	$-218    	;abs 0x6772
    684e:	39 41       	pop	r9		
    6850:	3a 41       	pop	r10		
    6852:	3b 41       	pop	r11		
    6854:	30 41       	ret			

00006856 <input_callback>:
    6856:	0b 12       	push	r11		
    6858:	0a 12       	push	r10		
    685a:	09 12       	push	r9		
    685c:	08 12       	push	r8		
    685e:	07 12       	push	r7		
    6860:	06 12       	push	r6		
    6862:	05 12       	push	r5		
    6864:	04 12       	push	r4		
    6866:	04 41       	mov	r1,	r4	
    6868:	34 50 10 00 	add	#16,	r4	;#0x0010
    686c:	31 50 fc fe 	add	#-260,	r1	;#0xfefc
    6870:	0a 4f       	mov	r15,	r10	
    6872:	09 4d       	mov	r13,	r9	
    6874:	12 12 18 2e 	push	&0x2e18	
    6878:	30 12 fe ac 	push	#-21250	;#0xacfe
    687c:	b0 12 cc 9e 	call	#0x9ecc	
    6880:	21 52       	add	#4,	r1	;r2 As==10
    6882:	92 53 18 2e 	inc	&0x2e18	
    6886:	1f 42 2a 24 	mov	&0x242a,r15	
    688a:	3f 50 b4 21 	add	#8628,	r15	;#0x21b4
    688e:	cf 93 ff ff 	tst.b	-1(r15)	;0xffff(r15)
    6892:	02 24       	jz	$+6      	;abs 0x6898
    6894:	30 40 a4 70 	br	#0x70a4	
    6898:	0b 43       	clr	r11		
    689a:	0e 4b       	mov	r11,	r14	
    689c:	0e 5e       	rla	r14		
    689e:	1e 12 54 24 	push	9300(r14)	;0x2454(r14)
    68a2:	0b 12       	push	r11		
    68a4:	30 12 2f ad 	push	#-21201	;#0xad2f
    68a8:	b0 12 cc 9e 	call	#0x9ecc	
    68ac:	31 50 06 00 	add	#6,	r1	;#0x0006
    68b0:	1b 53       	inc	r11		
    68b2:	3b 90 64 00 	cmp	#100,	r11	;#0x0064
    68b6:	f1 23       	jnz	$-28     	;abs 0x689a
    68b8:	e4 4a aa ff 	mov.b	@r10,	-86(r4)	;0xffaa(r4)
    68bc:	d4 4a 01 00 	mov.b	1(r10),	-85(r4)	;0x0001(r10), 0xffab(r4)
    68c0:	ab ff 
    68c2:	30 12 68 ac 	push	#-21400	;#0xac68
    68c6:	30 12 6c ac 	push	#-21396	;#0xac6c
    68ca:	30 12 71 ac 	push	#-21391	;#0xac71
    68ce:	b0 12 cc 9e 	call	#0x9ecc	
    68d2:	31 50 06 00 	add	#6,	r1	;#0x0006
    68d6:	1a 44 aa ff 	mov	-86(r4),r10	;0xffaa(r4)
    68da:	12 12 2a 24 	push	&0x242a	
    68de:	0a 12       	push	r10		
    68e0:	30 12 38 ad 	push	#-21192	;#0xad38
    68e4:	b0 12 cc 9e 	call	#0x9ecc	
    68e8:	31 50 06 00 	add	#6,	r1	;#0x0006
    68ec:	0f 49       	mov	r9,	r15	
    68ee:	b0 12 c4 62 	call	#0x62c4	
    68f2:	30 12 68 ac 	push	#-21400	;#0xac68
    68f6:	30 12 6c ac 	push	#-21396	;#0xac6c
    68fa:	30 12 71 ac 	push	#-21391	;#0xac71
    68fe:	b0 12 cc 9e 	call	#0x9ecc	
    6902:	31 50 06 00 	add	#6,	r1	;#0x0006
    6906:	6f 42       	mov.b	#4,	r15	;r2 As==10
    6908:	b0 12 12 73 	call	#0x7312	
    690c:	0f 12       	push	r15		
    690e:	30 12 58 ad 	push	#-21160	;#0xad58
    6912:	b0 12 cc 9e 	call	#0x9ecc	
    6916:	21 52       	add	#4,	r1	;r2 As==10
    6918:	3f 40 0a 00 	mov	#10,	r15	;#0x000a
    691c:	b0 12 e0 7c 	call	#0x7ce0	
    6920:	3a 53       	add	#-1,	r10	;r3 As==11
    6922:	6f 42       	mov.b	#4,	r15	;r2 As==10
    6924:	b0 12 12 73 	call	#0x7312	
    6928:	0e 4f       	mov	r15,	r14	
    692a:	0b 4a       	mov	r10,	r11	
    692c:	0b 5b       	rla	r11		
    692e:	09 4b       	mov	r11,	r9	
    6930:	39 50 54 24 	add	#9300,	r9	;#0x2454
    6934:	89 4f 00 00 	mov	r15,	0(r9)	;0x0000(r9)
    6938:	8f 10       	swpb	r15		
    693a:	8f 11       	sxt	r15		
    693c:	8f 10       	swpb	r15		
    693e:	8f 11       	sxt	r15		
    6940:	b0 12 86 98 	call	#0x9886	
    6944:	3c 40 49 d1 	mov	#-11959,r12	;#0xd149
    6948:	3d 40 ad 42 	mov	#17069,	r13	;#0x42ad
    694c:	b0 12 5a 93 	call	#0x935a	
    6950:	3c 40 b8 40 	mov	#16568,	r12	;#0x40b8
    6954:	3d 40 bb 42 	mov	#17083,	r13	;#0x42bb
    6958:	b0 12 06 96 	call	#0x9606	
    695c:	0c 4e       	mov	r14,	r12	
    695e:	0d 4f       	mov	r15,	r13	
    6960:	3e 40 d9 77 	mov	#30681,	r14	;#0x77d9
    6964:	3f 40 d9 3f 	mov	#16345,	r15	;#0x3fd9
    6968:	b0 12 a6 93 	call	#0x93a6	
    696c:	0c 4e       	mov	r14,	r12	
    696e:	0d 4f       	mov	r15,	r13	
    6970:	0e 43       	clr	r14		
    6972:	3f 40 20 41 	mov	#16672,	r15	;#0x4120
    6976:	b0 12 48 8b 	call	#0x8b48	
    697a:	84 4e ac ff 	mov	r14,	-84(r4)	;0xffac(r4)
    697e:	84 4f ae ff 	mov	r15,	-82(r4)	;0xffae(r4)
    6982:	92 93 18 2e 	cmp	#1,	&0x2e18	;r3 As==01
    6986:	5e 20       	jnz	$+190    	;abs 0x6a44
    6988:	0e 4b       	mov	r11,	r14	
    698a:	0e 5e       	rla	r14		
    698c:	0e 5e       	rla	r14		
    698e:	0e 5b       	add	r11,	r14	
    6990:	3e 50 e4 19 	add	#6628,	r14	;#0x19e4
    6994:	92 4e 02 00 	mov	2(r14),	&0x2e08	;0x0002(r14)
    6998:	08 2e 
    699a:	92 4e 04 00 	mov	4(r14),	&0x2e0a	;0x0004(r14)
    699e:	0a 2e 
    69a0:	92 4e 06 00 	mov	6(r14),	&0x2e14	;0x0006(r14)
    69a4:	14 2e 
    69a6:	92 4e 08 00 	mov	8(r14),	&0x2e16	;0x0008(r14)
    69aa:	16 2e 
    69ac:	92 44 ac ff 	mov	-84(r4),&0x2df4	;0xffac(r4)
    69b0:	f4 2d 
    69b2:	92 44 ae ff 	mov	-82(r4),&0x2df6	;0xffae(r4)
    69b6:	f6 2d 
    69b8:	2b 49       	mov	@r9,	r11	
    69ba:	6f 42       	mov.b	#4,	r15	;r2 As==10
    69bc:	b0 12 12 73 	call	#0x7312	
    69c0:	0b 12       	push	r11		
    69c2:	0f 12       	push	r15		
    69c4:	3c 40 00 24 	mov	#9216,	r12	;#0x2400
    69c8:	3d 40 74 49 	mov	#18804,	r13	;#0x4974
    69cc:	1e 42 f4 2d 	mov	&0x2df4,r14	
    69d0:	1f 42 f6 2d 	mov	&0x2df6,r15	
    69d4:	b0 12 f6 93 	call	#0x93f6	
    69d8:	b0 12 76 8e 	call	#0x8e76	
    69dc:	0f 12       	push	r15		
    69de:	0e 12       	push	r14		
    69e0:	0d 12       	push	r13		
    69e2:	0c 12       	push	r12		
    69e4:	3c 40 00 24 	mov	#9216,	r12	;#0x2400
    69e8:	3d 40 74 49 	mov	#18804,	r13	;#0x4974
    69ec:	1e 42 14 2e 	mov	&0x2e14,r14	
    69f0:	1f 42 16 2e 	mov	&0x2e16,r15	
    69f4:	b0 12 f6 93 	call	#0x93f6	
    69f8:	b0 12 76 8e 	call	#0x8e76	
    69fc:	0f 12       	push	r15		
    69fe:	0e 12       	push	r14		
    6a00:	0d 12       	push	r13		
    6a02:	0c 12       	push	r12		
    6a04:	3c 40 00 24 	mov	#9216,	r12	;#0x2400
    6a08:	3d 40 74 49 	mov	#18804,	r13	;#0x4974
    6a0c:	1e 42 08 2e 	mov	&0x2e08,r14	
    6a10:	1f 42 0a 2e 	mov	&0x2e0a,r15	
    6a14:	b0 12 f6 93 	call	#0x93f6	
    6a18:	b0 12 76 8e 	call	#0x8e76	
    6a1c:	0f 12       	push	r15		
    6a1e:	0e 12       	push	r14		
    6a20:	0d 12       	push	r13		
    6a22:	0c 12       	push	r12		
    6a24:	30 12 66 ad 	push	#-21146	;#0xad66
    6a28:	38 40 ec fe 	mov	#-276,	r8	;#0xfeec
    6a2c:	08 54       	add	r4,	r8	
    6a2e:	08 12       	push	r8		
    6a30:	b0 12 38 9f 	call	#0x9f38	
    6a34:	31 50 20 00 	add	#32,	r1	;#0x0020
    6a38:	08 12       	push	r8		
    6a3a:	30 12 9e ad 	push	#-21090	;#0xad9e
    6a3e:	b0 12 cc 9e 	call	#0x9ecc	
    6a42:	21 52       	add	#4,	r1	;r2 As==10
    6a44:	1f 42 18 2e 	mov	&0x2e18,r15	
    6a48:	2f 93       	cmp	#2,	r15	;r3 As==10
    6a4a:	02 34       	jge	$+6      	;abs 0x6a50
    6a4c:	30 40 4c 6e 	br	#0x6e4c	
    6a50:	0f 12       	push	r15		
    6a52:	30 12 aa ad 	push	#-21078	;#0xadaa
    6a56:	b0 12 cc 9e 	call	#0x9ecc	
    6a5a:	21 52       	add	#4,	r1	;r2 As==10
    6a5c:	0b 4a       	mov	r10,	r11	
    6a5e:	0b 5b       	rla	r11		
    6a60:	0f 4b       	mov	r11,	r15	
    6a62:	0f 5f       	rla	r15		
    6a64:	0f 5f       	rla	r15		
    6a66:	0b 5f       	add	r15,	r11	
    6a68:	3b 50 e4 19 	add	#6628,	r11	;#0x19e4
    6a6c:	1c 42 08 2e 	mov	&0x2e08,r12	
    6a70:	1d 42 0a 2e 	mov	&0x2e0a,r13	
    6a74:	1e 4b 02 00 	mov	2(r11),	r14	;0x0002(r11)
    6a78:	1f 4b 04 00 	mov	4(r11),	r15	;0x0004(r11)
    6a7c:	b0 12 a6 93 	call	#0x93a6	
    6a80:	3c 40 00 24 	mov	#9216,	r12	;#0x2400
    6a84:	3d 40 74 49 	mov	#18804,	r13	;#0x4974
    6a88:	b0 12 f6 93 	call	#0x93f6	
    6a8c:	3f f0 ff 7f 	and	#32767,	r15	;#0x7fff
    6a90:	b0 12 76 8e 	call	#0x8e76	
    6a94:	84 4c c8 ff 	mov	r12,	-56(r4)	;0xffc8(r4)
    6a98:	84 4d ca ff 	mov	r13,	-54(r4)	;0xffca(r4)
    6a9c:	84 4e cc ff 	mov	r14,	-52(r4)	;0xffcc(r4)
    6aa0:	84 4f ce ff 	mov	r15,	-50(r4)	;0xffce(r4)
    6aa4:	1c 42 14 2e 	mov	&0x2e14,r12	
    6aa8:	1d 42 16 2e 	mov	&0x2e16,r13	
    6aac:	1e 4b 06 00 	mov	6(r11),	r14	;0x0006(r11)
    6ab0:	1f 4b 08 00 	mov	8(r11),	r15	;0x0008(r11)
    6ab4:	b0 12 a6 93 	call	#0x93a6	
    6ab8:	3c 40 00 24 	mov	#9216,	r12	;#0x2400
    6abc:	3d 40 74 49 	mov	#18804,	r13	;#0x4974
    6ac0:	b0 12 f6 93 	call	#0x93f6	
    6ac4:	3f f0 ff 7f 	and	#32767,	r15	;#0x7fff
    6ac8:	b0 12 76 8e 	call	#0x8e76	
    6acc:	84 4c d0 ff 	mov	r12,	-48(r4)	;0xffd0(r4)
    6ad0:	84 4d d2 ff 	mov	r13,	-46(r4)	;0xffd2(r4)
    6ad4:	84 4e d4 ff 	mov	r14,	-44(r4)	;0xffd4(r4)
    6ad8:	84 4f d6 ff 	mov	r15,	-42(r4)	;0xffd6(r4)
    6adc:	1c 42 f4 2d 	mov	&0x2df4,r12	
    6ae0:	1d 42 f6 2d 	mov	&0x2df6,r13	
    6ae4:	1e 44 ac ff 	mov	-84(r4),r14	;0xffac(r4)
    6ae8:	1f 44 ae ff 	mov	-82(r4),r15	;0xffae(r4)
    6aec:	b0 12 a6 93 	call	#0x93a6	
    6af0:	3c 40 00 24 	mov	#9216,	r12	;#0x2400
    6af4:	3d 40 74 49 	mov	#18804,	r13	;#0x4974
    6af8:	b0 12 f6 93 	call	#0x93f6	
    6afc:	3f f0 ff 7f 	and	#32767,	r15	;#0x7fff
    6b00:	b0 12 76 8e 	call	#0x8e76	
    6b04:	84 4c d8 ff 	mov	r12,	-40(r4)	;0xffd8(r4)
    6b08:	84 4d da ff 	mov	r13,	-38(r4)	;0xffda(r4)
    6b0c:	84 4e dc ff 	mov	r14,	-36(r4)	;0xffdc(r4)
    6b10:	84 4f de ff 	mov	r15,	-34(r4)	;0xffde(r4)
    6b14:	94 42 34 24 	mov	&0x2434,-80(r4)	;0xffb0(r4)
    6b18:	b0 ff 
    6b1a:	94 42 36 24 	mov	&0x2436,-78(r4)	;0xffb2(r4)
    6b1e:	b2 ff 
    6b20:	94 42 38 24 	mov	&0x2438,-76(r4)	;0xffb4(r4)
    6b24:	b4 ff 
    6b26:	94 42 3a 24 	mov	&0x243a,-74(r4)	;0xffb6(r4)
    6b2a:	b6 ff 
    6b2c:	94 42 4c 24 	mov	&0x244c,-72(r4)	;0xffb8(r4)
    6b30:	b8 ff 
    6b32:	94 42 4e 24 	mov	&0x244e,-70(r4)	;0xffba(r4)
    6b36:	ba ff 
    6b38:	94 42 50 24 	mov	&0x2450,-68(r4)	;0xffbc(r4)
    6b3c:	bc ff 
    6b3e:	94 42 52 24 	mov	&0x2452,-66(r4)	;0xffbe(r4)
    6b42:	be ff 
    6b44:	94 42 3c 24 	mov	&0x243c,-64(r4)	;0xffc0(r4)
    6b48:	c0 ff 
    6b4a:	94 42 3e 24 	mov	&0x243e,-62(r4)	;0xffc2(r4)
    6b4e:	c2 ff 
    6b50:	94 42 40 24 	mov	&0x2440,-60(r4)	;0xffc4(r4)
    6b54:	c4 ff 
    6b56:	94 42 42 24 	mov	&0x2442,-58(r4)	;0xffc6(r4)
    6b5a:	c6 ff 
    6b5c:	94 42 44 24 	mov	&0x2444,-24(r4)	;0xffe8(r4)
    6b60:	e8 ff 
    6b62:	94 42 46 24 	mov	&0x2446,-22(r4)	;0xffea(r4)
    6b66:	ea ff 
    6b68:	94 42 48 24 	mov	&0x2448,-20(r4)	;0xffec(r4)
    6b6c:	ec ff 
    6b6e:	94 42 4a 24 	mov	&0x244a,-18(r4)	;0xffee(r4)
    6b72:	ee ff 
    6b74:	12 12 18 2e 	push	&0x2e18	
    6b78:	14 12 b6 ff 	push	-74(r4)	;0xffb6(r4)
    6b7c:	14 12 b4 ff 	push	-76(r4)	;0xffb4(r4)
    6b80:	14 12 b2 ff 	push	-78(r4)	;0xffb2(r4)
    6b84:	14 12 b0 ff 	push	-80(r4)	;0xffb0(r4)
    6b88:	1c 44 b8 ff 	mov	-72(r4),r12	;0xffb8(r4)
    6b8c:	1d 44 ba ff 	mov	-70(r4),r13	;0xffba(r4)
    6b90:	1e 44 bc ff 	mov	-68(r4),r14	;0xffbc(r4)
    6b94:	1f 44 be ff 	mov	-66(r4),r15	;0xffbe(r4)
    6b98:	b0 12 44 a9 	call	#0xa944	
    6b9c:	84 4c e0 ff 	mov	r12,	-32(r4)	;0xffe0(r4)
    6ba0:	84 4d e2 ff 	mov	r13,	-30(r4)	;0xffe2(r4)
    6ba4:	84 4e e4 ff 	mov	r14,	-28(r4)	;0xffe4(r4)
    6ba8:	84 4f e6 ff 	mov	r15,	-26(r4)	;0xffe6(r4)
    6bac:	91 44 c0 ff 	mov	-64(r4),0(r1)	;0xffc0(r4), 0x0000(r1)
    6bb0:	00 00 
    6bb2:	91 44 c2 ff 	mov	-62(r4),2(r1)	;0xffc2(r4), 0x0002(r1)
    6bb6:	02 00 
    6bb8:	91 44 c4 ff 	mov	-60(r4),4(r1)	;0xffc4(r4), 0x0004(r1)
    6bbc:	04 00 
    6bbe:	91 44 c6 ff 	mov	-58(r4),6(r1)	;0xffc6(r4), 0x0006(r1)
    6bc2:	06 00 
    6bc4:	1c 44 e8 ff 	mov	-24(r4),r12	;0xffe8(r4)
    6bc8:	1d 44 ea ff 	mov	-22(r4),r13	;0xffea(r4)
    6bcc:	1e 44 ec ff 	mov	-20(r4),r14	;0xffec(r4)
    6bd0:	1f 44 ee ff 	mov	-18(r4),r15	;0xffee(r4)
    6bd4:	b0 12 44 a9 	call	#0xa944	
    6bd8:	18 44 e0 ff 	mov	-32(r4),r8	;0xffe0(r4)
    6bdc:	19 44 e2 ff 	mov	-30(r4),r9	;0xffe2(r4)
    6be0:	1a 44 e4 ff 	mov	-28(r4),r10	;0xffe4(r4)
    6be4:	1b 44 e6 ff 	mov	-26(r4),r11	;0xffe6(r4)
    6be8:	08 8c       	sub	r12,	r8	
    6bea:	09 7d       	subc	r13,	r9	
    6bec:	0a 7e       	subc	r14,	r10	
    6bee:	0b 7f       	subc	r15,	r11	
    6bf0:	81 48 00 00 	mov	r8,	0(r1)	;0x0000(r1)
    6bf4:	81 49 02 00 	mov	r9,	2(r1)	;0x0002(r1)
    6bf8:	81 4a 04 00 	mov	r10,	4(r1)	;0x0004(r1)
    6bfc:	81 4b 06 00 	mov	r11,	6(r1)	;0x0006(r1)
    6c00:	14 12 be ff 	push	-66(r4)	;0xffbe(r4)
    6c04:	14 12 bc ff 	push	-68(r4)	;0xffbc(r4)
    6c08:	14 12 ba ff 	push	-70(r4)	;0xffba(r4)
    6c0c:	14 12 b8 ff 	push	-72(r4)	;0xffb8(r4)
    6c10:	14 12 ee ff 	push	-18(r4)	;0xffee(r4)
    6c14:	14 12 ec ff 	push	-20(r4)	;0xffec(r4)
    6c18:	14 12 ea ff 	push	-22(r4)	;0xffea(r4)
    6c1c:	14 12 e8 ff 	push	-24(r4)	;0xffe8(r4)
    6c20:	14 12 c6 ff 	push	-58(r4)	;0xffc6(r4)
    6c24:	14 12 c4 ff 	push	-60(r4)	;0xffc4(r4)
    6c28:	14 12 c2 ff 	push	-62(r4)	;0xffc2(r4)
    6c2c:	14 12 c0 ff 	push	-64(r4)	;0xffc0(r4)
    6c30:	14 12 b6 ff 	push	-74(r4)	;0xffb6(r4)
    6c34:	14 12 b4 ff 	push	-76(r4)	;0xffb4(r4)
    6c38:	14 12 b2 ff 	push	-78(r4)	;0xffb2(r4)
    6c3c:	14 12 b0 ff 	push	-80(r4)	;0xffb0(r4)
    6c40:	30 12 cb ad 	push	#-21045	;#0xadcb
    6c44:	39 40 ec fe 	mov	#-276,	r9	;#0xfeec
    6c48:	09 54       	add	r4,	r9	
    6c4a:	09 12       	push	r9		
    6c4c:	b0 12 38 9f 	call	#0x9f38	
    6c50:	31 50 2e 00 	add	#46,	r1	;#0x002e
    6c54:	09 12       	push	r9		
    6c56:	12 12 2a 24 	push	&0x242a	
    6c5a:	30 12 19 ae 	push	#-20967	;#0xae19
    6c5e:	b0 12 cc 9e 	call	#0x9ecc	
    6c62:	31 50 06 00 	add	#6,	r1	;#0x0006
    6c66:	18 44 c8 ff 	mov	-56(r4),r8	;0xffc8(r4)
    6c6a:	19 44 ca ff 	mov	-54(r4),r9	;0xffca(r4)
    6c6e:	1a 44 cc ff 	mov	-52(r4),r10	;0xffcc(r4)
    6c72:	1b 44 ce ff 	mov	-50(r4),r11	;0xffce(r4)
    6c76:	08 58       	rla	r8		
    6c78:	09 69       	rlc	r9		
    6c7a:	0a 6a       	rlc	r10		
    6c7c:	0b 6b       	rlc	r11		
    6c7e:	82 58 34 24 	add	r8,	&0x2434	
    6c82:	82 69 36 24 	addc	r9,	&0x2436	
    6c86:	82 6a 38 24 	addc	r10,	&0x2438	
    6c8a:	82 6b 3a 24 	addc	r11,	&0x243a	
    6c8e:	1c 44 d0 ff 	mov	-48(r4),r12	;0xffd0(r4)
    6c92:	1d 44 d2 ff 	mov	-46(r4),r13	;0xffd2(r4)
    6c96:	1e 44 d4 ff 	mov	-44(r4),r14	;0xffd4(r4)
    6c9a:	1f 44 d6 ff 	mov	-42(r4),r15	;0xffd6(r4)
    6c9e:	0c 5c       	rla	r12		
    6ca0:	0d 6d       	rlc	r13		
    6ca2:	0e 6e       	rlc	r14		
    6ca4:	0f 6f       	rlc	r15		
    6ca6:	82 5c 3c 24 	add	r12,	&0x243c	
    6caa:	82 6d 3e 24 	addc	r13,	&0x243e	
    6cae:	82 6e 40 24 	addc	r14,	&0x2440	
    6cb2:	82 6f 42 24 	addc	r15,	&0x2442	
    6cb6:	82 58 44 24 	add	r8,	&0x2444	
    6cba:	82 69 46 24 	addc	r9,	&0x2446	
    6cbe:	82 6a 48 24 	addc	r10,	&0x2448	
    6cc2:	82 6b 4a 24 	addc	r11,	&0x244a	
    6cc6:	82 5c 4c 24 	add	r12,	&0x244c	
    6cca:	82 6d 4e 24 	addc	r13,	&0x244e	
    6cce:	82 6e 50 24 	addc	r14,	&0x2450	
    6cd2:	82 6f 52 24 	addc	r15,	&0x2452	
    6cd6:	03 12       	push	#0		;r3 As==00
    6cd8:	03 12       	push	#0		;r3 As==00
    6cda:	30 12 0f 00 	push	#15		;#0x000f
    6cde:	30 12 40 42 	push	#16960		;#0x4240
    6ce2:	1c 44 d8 ff 	mov	-40(r4),r12	;0xffd8(r4)
    6ce6:	1d 44 da ff 	mov	-38(r4),r13	;0xffda(r4)
    6cea:	1e 44 dc ff 	mov	-36(r4),r14	;0xffdc(r4)
    6cee:	1f 44 de ff 	mov	-34(r4),r15	;0xffde(r4)
    6cf2:	b0 12 7a aa 	call	#0xaa7a	
    6cf6:	31 52       	add	#8,	r1	;r2 As==11
    6cf8:	b0 12 9a 8f 	call	#0x8f9a	
    6cfc:	0c 4e       	mov	r14,	r12	
    6cfe:	0d 4f       	mov	r15,	r13	
    6d00:	b0 12 f6 93 	call	#0x93f6	
    6d04:	0a 4e       	mov	r14,	r10	
    6d06:	0b 4f       	mov	r15,	r11	
    6d08:	03 12       	push	#0		;r3 As==00
    6d0a:	03 12       	push	#0		;r3 As==00
    6d0c:	30 12 0f 00 	push	#15		;#0x000f
    6d10:	30 12 40 42 	push	#16960		;#0x4240
    6d14:	1c 44 c8 ff 	mov	-56(r4),r12	;0xffc8(r4)
    6d18:	1d 44 ca ff 	mov	-54(r4),r13	;0xffca(r4)
    6d1c:	1e 44 cc ff 	mov	-52(r4),r14	;0xffcc(r4)
    6d20:	1f 44 ce ff 	mov	-50(r4),r15	;0xffce(r4)
    6d24:	b0 12 7a aa 	call	#0xaa7a	
    6d28:	31 52       	add	#8,	r1	;r2 As==11
    6d2a:	b0 12 9a 8f 	call	#0x8f9a	
    6d2e:	06 4e       	mov	r14,	r6	
    6d30:	07 4f       	mov	r15,	r7	
    6d32:	03 12       	push	#0		;r3 As==00
    6d34:	03 12       	push	#0		;r3 As==00
    6d36:	30 12 0f 00 	push	#15		;#0x000f
    6d3a:	30 12 40 42 	push	#16960		;#0x4240
    6d3e:	1c 44 d0 ff 	mov	-48(r4),r12	;0xffd0(r4)
    6d42:	1d 44 d2 ff 	mov	-46(r4),r13	;0xffd2(r4)
    6d46:	1e 44 d4 ff 	mov	-44(r4),r14	;0xffd4(r4)
    6d4a:	1f 44 d6 ff 	mov	-42(r4),r15	;0xffd6(r4)
    6d4e:	b0 12 7a aa 	call	#0xaa7a	
    6d52:	31 52       	add	#8,	r1	;r2 As==11
    6d54:	b0 12 9a 8f 	call	#0x8f9a	
    6d58:	84 4e b0 ff 	mov	r14,	-80(r4)	;0xffb0(r4)
    6d5c:	84 4f b2 ff 	mov	r15,	-78(r4)	;0xffb2(r4)
    6d60:	1c 44 ac ff 	mov	-84(r4),r12	;0xffac(r4)
    6d64:	1d 44 ae ff 	mov	-82(r4),r13	;0xffae(r4)
    6d68:	0e 4c       	mov	r12,	r14	
    6d6a:	0f 4d       	mov	r13,	r15	
    6d6c:	b0 12 f6 93 	call	#0x93f6	
    6d70:	0c 4e       	mov	r14,	r12	
    6d72:	0d 4f       	mov	r15,	r13	
    6d74:	0e 4a       	mov	r10,	r14	
    6d76:	0f 4b       	mov	r11,	r15	
    6d78:	b0 12 a6 93 	call	#0x93a6	
    6d7c:	08 4e       	mov	r14,	r8	
    6d7e:	09 4f       	mov	r15,	r9	
    6d80:	0c 46       	mov	r6,	r12	
    6d82:	0d 47       	mov	r7,	r13	
    6d84:	0e 46       	mov	r6,	r14	
    6d86:	0f 47       	mov	r7,	r15	
    6d88:	b0 12 f6 93 	call	#0x93f6	
    6d8c:	0c 4e       	mov	r14,	r12	
    6d8e:	0d 4f       	mov	r15,	r13	
    6d90:	0e 48       	mov	r8,	r14	
    6d92:	0f 49       	mov	r9,	r15	
    6d94:	b0 12 5a 93 	call	#0x935a	
    6d98:	08 4e       	mov	r14,	r8	
    6d9a:	09 4f       	mov	r15,	r9	
    6d9c:	1c 44 b0 ff 	mov	-80(r4),r12	;0xffb0(r4)
    6da0:	1d 44 b2 ff 	mov	-78(r4),r13	;0xffb2(r4)
    6da4:	0e 4c       	mov	r12,	r14	
    6da6:	0f 4d       	mov	r13,	r15	
    6da8:	b0 12 f6 93 	call	#0x93f6	
    6dac:	0c 4e       	mov	r14,	r12	
    6dae:	0d 4f       	mov	r15,	r13	
    6db0:	0e 48       	mov	r8,	r14	
    6db2:	0f 49       	mov	r9,	r15	
    6db4:	b0 12 5a 93 	call	#0x935a	
    6db8:	0c 4a       	mov	r10,	r12	
    6dba:	0d 4b       	mov	r11,	r13	
    6dbc:	b0 12 5a 93 	call	#0x935a	
    6dc0:	08 4e       	mov	r14,	r8	
    6dc2:	09 4f       	mov	r15,	r9	
    6dc4:	1c 42 2c 24 	mov	&0x242c,r12	
    6dc8:	1d 42 2e 24 	mov	&0x242e,r13	
    6dcc:	b0 12 5a 93 	call	#0x935a	
    6dd0:	0a 4e       	mov	r14,	r10	
    6dd2:	0b 4f       	mov	r15,	r11	
    6dd4:	82 4e 2c 24 	mov	r14,	&0x242c	
    6dd8:	82 4f 2e 24 	mov	r15,	&0x242e	
    6ddc:	1c 42 30 24 	mov	&0x2430,r12	
    6de0:	1d 42 32 24 	mov	&0x2432,r13	
    6de4:	0e 48       	mov	r8,	r14	
    6de6:	0f 49       	mov	r9,	r15	
    6de8:	b0 12 5a 93 	call	#0x935a	
    6dec:	82 4e 30 24 	mov	r14,	&0x2430	
    6df0:	82 4f 32 24 	mov	r15,	&0x2432	
    6df4:	12 12 18 2e 	push	&0x2e18	
    6df8:	3c 40 00 24 	mov	#9216,	r12	;#0x2400
    6dfc:	3d 40 74 49 	mov	#18804,	r13	;#0x4974
    6e00:	b0 12 f6 93 	call	#0x93f6	
    6e04:	b0 12 76 8e 	call	#0x8e76	
    6e08:	0f 12       	push	r15		
    6e0a:	0e 12       	push	r14		
    6e0c:	0d 12       	push	r13		
    6e0e:	0c 12       	push	r12		
    6e10:	3c 40 00 24 	mov	#9216,	r12	;#0x2400
    6e14:	3d 40 74 49 	mov	#18804,	r13	;#0x4974
    6e18:	0e 4a       	mov	r10,	r14	
    6e1a:	0f 4b       	mov	r11,	r15	
    6e1c:	b0 12 f6 93 	call	#0x93f6	
    6e20:	b0 12 76 8e 	call	#0x8e76	
    6e24:	0f 12       	push	r15		
    6e26:	0e 12       	push	r14		
    6e28:	0d 12       	push	r13		
    6e2a:	0c 12       	push	r12		
    6e2c:	30 12 24 ae 	push	#-20956	;#0xae24
    6e30:	3b 40 ec fe 	mov	#-276,	r11	;#0xfeec
    6e34:	0b 54       	add	r4,	r11	
    6e36:	0b 12       	push	r11		
    6e38:	b0 12 38 9f 	call	#0x9f38	
    6e3c:	31 50 16 00 	add	#22,	r1	;#0x0016
    6e40:	0b 12       	push	r11		
    6e42:	30 12 45 ae 	push	#-20923	;#0xae45
    6e46:	b0 12 cc 9e 	call	#0x9ecc	
    6e4a:	21 52       	add	#4,	r1	;r2 As==10
    6e4c:	12 12 3a 24 	push	&0x243a	
    6e50:	12 12 38 24 	push	&0x2438	
    6e54:	12 12 36 24 	push	&0x2436	
    6e58:	12 12 34 24 	push	&0x2434	
    6e5c:	1c 42 4c 24 	mov	&0x244c,r12	
    6e60:	1d 42 4e 24 	mov	&0x244e,r13	
    6e64:	1e 42 50 24 	mov	&0x2450,r14	
    6e68:	1f 42 52 24 	mov	&0x2452,r15	
    6e6c:	b0 12 44 a9 	call	#0xa944	
    6e70:	08 4c       	mov	r12,	r8	
    6e72:	09 4d       	mov	r13,	r9	
    6e74:	0a 4e       	mov	r14,	r10	
    6e76:	0b 4f       	mov	r15,	r11	
    6e78:	91 42 3c 24 	mov	&0x243c,0(r1)	;0x0000(r1)
    6e7c:	00 00 
    6e7e:	91 42 3e 24 	mov	&0x243e,2(r1)	;0x0002(r1)
    6e82:	02 00 
    6e84:	91 42 40 24 	mov	&0x2440,4(r1)	;0x0004(r1)
    6e88:	04 00 
    6e8a:	91 42 42 24 	mov	&0x2442,6(r1)	;0x0006(r1)
    6e8e:	06 00 
    6e90:	1c 42 44 24 	mov	&0x2444,r12	
    6e94:	1d 42 46 24 	mov	&0x2446,r13	
    6e98:	1e 42 48 24 	mov	&0x2448,r14	
    6e9c:	1f 42 4a 24 	mov	&0x244a,r15	
    6ea0:	b0 12 44 a9 	call	#0xa944	
    6ea4:	31 52       	add	#8,	r1	;r2 As==11
    6ea6:	08 8c       	sub	r12,	r8	
    6ea8:	09 7d       	subc	r13,	r9	
    6eaa:	0a 7e       	subc	r14,	r10	
    6eac:	0b 7f       	subc	r15,	r11	
    6eae:	08 93       	tst	r8		
    6eb0:	08 20       	jnz	$+18     	;abs 0x6ec2
    6eb2:	09 93       	tst	r9		
    6eb4:	06 20       	jnz	$+14     	;abs 0x6ec2
    6eb6:	0a 93       	tst	r10		
    6eb8:	04 20       	jnz	$+10     	;abs 0x6ec2
    6eba:	0b 93       	tst	r11		
    6ebc:	02 20       	jnz	$+6      	;abs 0x6ec2
    6ebe:	30 40 a4 70 	br	#0x70a4	
    6ec2:	0c 48       	mov	r8,	r12	
    6ec4:	0d 49       	mov	r9,	r13	
    6ec6:	0e 4a       	mov	r10,	r14	
    6ec8:	0f 4b       	mov	r11,	r15	
    6eca:	b0 12 9a 8f 	call	#0x8f9a	
    6ece:	0c 4e       	mov	r14,	r12	
    6ed0:	0d 4f       	mov	r15,	r13	
    6ed2:	0e 43       	clr	r14		
    6ed4:	3f 40 80 3f 	mov	#16256,	r15	;#0x3f80
    6ed8:	b0 12 06 96 	call	#0x9606	
    6edc:	b0 12 76 8e 	call	#0x8e76	
    6ee0:	84 4c b0 ff 	mov	r12,	-80(r4)	;0xffb0(r4)
    6ee4:	84 4d b2 ff 	mov	r13,	-78(r4)	;0xffb2(r4)
    6ee8:	84 4e b4 ff 	mov	r14,	-76(r4)	;0xffb4(r4)
    6eec:	84 4f b6 ff 	mov	r15,	-74(r4)	;0xffb6(r4)
    6ef0:	12 12 18 2e 	push	&0x2e18	
    6ef4:	0f 12       	push	r15		
    6ef6:	0e 12       	push	r14		
    6ef8:	0d 12       	push	r13		
    6efa:	0c 12       	push	r12		
    6efc:	0b 12       	push	r11		
    6efe:	0a 12       	push	r10		
    6f00:	09 12       	push	r9		
    6f02:	08 12       	push	r8		
    6f04:	30 12 4f ae 	push	#-20913	;#0xae4f
    6f08:	38 40 ec fe 	mov	#-276,	r8	;#0xfeec
    6f0c:	08 54       	add	r4,	r8	
    6f0e:	08 12       	push	r8		
    6f10:	b0 12 38 9f 	call	#0x9f38	
    6f14:	31 50 16 00 	add	#22,	r1	;#0x0016
    6f18:	08 12       	push	r8		
    6f1a:	30 12 6c ae 	push	#-20884	;#0xae6c
    6f1e:	b0 12 cc 9e 	call	#0x9ecc	
    6f22:	21 52       	add	#4,	r1	;r2 As==10
    6f24:	18 42 2c 24 	mov	&0x242c,r8	
    6f28:	19 42 2e 24 	mov	&0x242e,r9	
    6f2c:	1a 42 30 24 	mov	&0x2430,r10	
    6f30:	1b 42 32 24 	mov	&0x2432,r11	
    6f34:	1c 44 b0 ff 	mov	-80(r4),r12	;0xffb0(r4)
    6f38:	1d 44 b2 ff 	mov	-78(r4),r13	;0xffb2(r4)
    6f3c:	1e 44 b4 ff 	mov	-76(r4),r14	;0xffb4(r4)
    6f40:	1f 44 b6 ff 	mov	-74(r4),r15	;0xffb6(r4)
    6f44:	b0 12 9a 8f 	call	#0x8f9a	
    6f48:	84 4e ac ff 	mov	r14,	-84(r4)	;0xffac(r4)
    6f4c:	84 4f ae ff 	mov	r15,	-82(r4)	;0xffae(r4)
    6f50:	1c 42 4c 24 	mov	&0x244c,r12	
    6f54:	1d 42 4e 24 	mov	&0x244e,r13	
    6f58:	1e 42 50 24 	mov	&0x2450,r14	
    6f5c:	1f 42 52 24 	mov	&0x2452,r15	
    6f60:	b0 12 9a 8f 	call	#0x8f9a	
    6f64:	0c 48       	mov	r8,	r12	
    6f66:	0d 49       	mov	r9,	r13	
    6f68:	b0 12 f6 93 	call	#0x93f6	
    6f6c:	06 4e       	mov	r14,	r6	
    6f6e:	07 4f       	mov	r15,	r7	
    6f70:	1c 42 3c 24 	mov	&0x243c,r12	
    6f74:	1d 42 3e 24 	mov	&0x243e,r13	
    6f78:	1e 42 40 24 	mov	&0x2440,r14	
    6f7c:	1f 42 42 24 	mov	&0x2442,r15	
    6f80:	b0 12 9a 8f 	call	#0x8f9a	
    6f84:	0c 4a       	mov	r10,	r12	
    6f86:	0d 4b       	mov	r11,	r13	
    6f88:	b0 12 f6 93 	call	#0x93f6	
    6f8c:	0c 4e       	mov	r14,	r12	
    6f8e:	0d 4f       	mov	r15,	r13	
    6f90:	0e 46       	mov	r6,	r14	
    6f92:	0f 47       	mov	r7,	r15	
    6f94:	b0 12 a6 93 	call	#0x93a6	
    6f98:	1c 44 ac ff 	mov	-84(r4),r12	;0xffac(r4)
    6f9c:	1d 44 ae ff 	mov	-82(r4),r13	;0xffae(r4)
    6fa0:	b0 12 f6 93 	call	#0x93f6	
    6fa4:	b0 12 76 8e 	call	#0x8e76	
    6fa8:	84 4c b0 ff 	mov	r12,	-80(r4)	;0xffb0(r4)
    6fac:	84 4d b2 ff 	mov	r13,	-78(r4)	;0xffb2(r4)
    6fb0:	84 4e b4 ff 	mov	r14,	-76(r4)	;0xffb4(r4)
    6fb4:	84 4f b6 ff 	mov	r15,	-74(r4)	;0xffb6(r4)
    6fb8:	82 4c 00 2e 	mov	r12,	&0x2e00	
    6fbc:	82 4d 02 2e 	mov	r13,	&0x2e02	
    6fc0:	82 4e 04 2e 	mov	r14,	&0x2e04	
    6fc4:	82 4f 06 2e 	mov	r15,	&0x2e06	
    6fc8:	1c 42 34 24 	mov	&0x2434,r12	
    6fcc:	1d 42 36 24 	mov	&0x2436,r13	
    6fd0:	1e 42 38 24 	mov	&0x2438,r14	
    6fd4:	1f 42 3a 24 	mov	&0x243a,r15	
    6fd8:	b0 12 9a 8f 	call	#0x8f9a	
    6fdc:	0c 4a       	mov	r10,	r12	
    6fde:	0d 4b       	mov	r11,	r13	
    6fe0:	b0 12 f6 93 	call	#0x93f6	
    6fe4:	0a 4e       	mov	r14,	r10	
    6fe6:	0b 4f       	mov	r15,	r11	
    6fe8:	1c 42 44 24 	mov	&0x2444,r12	
    6fec:	1d 42 46 24 	mov	&0x2446,r13	
    6ff0:	1e 42 48 24 	mov	&0x2448,r14	
    6ff4:	1f 42 4a 24 	mov	&0x244a,r15	
    6ff8:	b0 12 9a 8f 	call	#0x8f9a	
    6ffc:	0c 48       	mov	r8,	r12	
    6ffe:	0d 49       	mov	r9,	r13	
    7000:	b0 12 f6 93 	call	#0x93f6	
    7004:	0c 4e       	mov	r14,	r12	
    7006:	0d 4f       	mov	r15,	r13	
    7008:	0e 4a       	mov	r10,	r14	
    700a:	0f 4b       	mov	r11,	r15	
    700c:	b0 12 a6 93 	call	#0x93a6	
    7010:	1c 44 ac ff 	mov	-84(r4),r12	;0xffac(r4)
    7014:	1d 44 ae ff 	mov	-82(r4),r13	;0xffae(r4)
    7018:	b0 12 f6 93 	call	#0x93f6	
    701c:	b0 12 76 8e 	call	#0x8e76	
    7020:	82 4c 0c 2e 	mov	r12,	&0x2e0c	
    7024:	82 4d 0e 2e 	mov	r13,	&0x2e0e	
    7028:	82 4e 10 2e 	mov	r14,	&0x2e10	
    702c:	82 4f 12 2e 	mov	r15,	&0x2e12	
    7030:	12 12 18 2e 	push	&0x2e18	
    7034:	03 12       	push	#0		;r3 As==00
    7036:	03 12       	push	#0		;r3 As==00
    7038:	30 12 0f 00 	push	#15		;#0x000f
    703c:	30 12 40 42 	push	#16960		;#0x4240
    7040:	b0 12 44 a9 	call	#0xa944	
    7044:	81 4c 00 00 	mov	r12,	0(r1)	;0x0000(r1)
    7048:	81 4d 02 00 	mov	r13,	2(r1)	;0x0002(r1)
    704c:	81 4e 04 00 	mov	r14,	4(r1)	;0x0004(r1)
    7050:	81 4f 06 00 	mov	r15,	6(r1)	;0x0006(r1)
    7054:	03 12       	push	#0		;r3 As==00
    7056:	03 12       	push	#0		;r3 As==00
    7058:	30 12 0f 00 	push	#15		;#0x000f
    705c:	30 12 40 42 	push	#16960		;#0x4240
    7060:	1c 44 b0 ff 	mov	-80(r4),r12	;0xffb0(r4)
    7064:	1d 44 b2 ff 	mov	-78(r4),r13	;0xffb2(r4)
    7068:	1e 44 b4 ff 	mov	-76(r4),r14	;0xffb4(r4)
    706c:	1f 44 b6 ff 	mov	-74(r4),r15	;0xffb6(r4)
    7070:	b0 12 44 a9 	call	#0xa944	
    7074:	81 4c 00 00 	mov	r12,	0(r1)	;0x0000(r1)
    7078:	81 4d 02 00 	mov	r13,	2(r1)	;0x0002(r1)
    707c:	81 4e 04 00 	mov	r14,	4(r1)	;0x0004(r1)
    7080:	81 4f 06 00 	mov	r15,	6(r1)	;0x0006(r1)
    7084:	30 12 76 ae 	push	#-20874	;#0xae76
    7088:	3a 40 ec fe 	mov	#-276,	r10	;#0xfeec
    708c:	0a 54       	add	r4,	r10	
    708e:	0a 12       	push	r10		
    7090:	b0 12 38 9f 	call	#0x9f38	
    7094:	31 50 16 00 	add	#22,	r1	;#0x0016
    7098:	0a 12       	push	r10		
    709a:	30 12 89 ae 	push	#-20855	;#0xae89
    709e:	b0 12 cc 9e 	call	#0x9ecc	
    70a2:	21 52       	add	#4,	r1	;r2 As==10
    70a4:	31 50 04 01 	add	#260,	r1	;#0x0104
    70a8:	34 41       	pop	r4		
    70aa:	35 41       	pop	r5		
    70ac:	36 41       	pop	r6		
    70ae:	37 41       	pop	r7		
    70b0:	38 41       	pop	r8		
    70b2:	39 41       	pop	r9		
    70b4:	3a 41       	pop	r10		
    70b6:	3b 41       	pop	r11		
    70b8:	30 41       	ret			

000070ba <init>:
    70ba:	82 43 56 25 	mov	#0,	&0x2556	;r3 As==00
    70be:	30 41       	ret			

000070c0 <output>:
    70c0:	0b 12       	push	r11		
    70c2:	0b 4f       	mov	r15,	r11	
    70c4:	b0 12 80 72 	call	#0x7280	
    70c8:	1e 42 20 2e 	mov	&0x2e20,r14	
    70cc:	1f 42 1e 2e 	mov	&0x2e1e,r15	
    70d0:	b0 12 92 72 	call	#0x7292	
    70d4:	0b 93       	tst	r11		
    70d6:	02 24       	jz	$+6      	;abs 0x70dc
    70d8:	0e 4b       	mov	r11,	r14	
    70da:	02 3c       	jmp	$+6      	;abs 0x70e0
    70dc:	3e 40 c6 ab 	mov	#-21562,r14	;#0xabc6
    70e0:	7f 40 0d 00 	mov.b	#13,	r15	;#0x000d
    70e4:	b0 12 1c 73 	call	#0x731c	
    70e8:	3e 40 ea 2d 	mov	#11754,	r14	;#0x2dea
    70ec:	7f 40 0c 00 	mov.b	#12,	r15	;#0x000c
    70f0:	b0 12 1c 73 	call	#0x731c	
    70f4:	0e 43       	clr	r14		
    70f6:	0f 43       	clr	r15		
    70f8:	92 12 b6 ab 	call	&0xabb6	
    70fc:	5f 43       	mov.b	#1,	r15	;r3 As==01
    70fe:	3b 41       	pop	r11		
    7100:	30 41       	ret			

00007102 <input>:
    7102:	0b 12       	push	r11		
    7104:	0a 12       	push	r10		
    7106:	09 12       	push	r9		
    7108:	08 12       	push	r8		
    710a:	1b 42 56 25 	mov	&0x2556,r11	
    710e:	0b 93       	tst	r11		
    7110:	13 24       	jz	$+40     	;abs 0x7138
    7112:	7f 40 0d 00 	mov.b	#13,	r15	;#0x000d
    7116:	b0 12 34 73 	call	#0x7334	
    711a:	08 4f       	mov	r15,	r8	
    711c:	7f 40 0c 00 	mov.b	#12,	r15	;#0x000c
    7120:	b0 12 34 73 	call	#0x7334	
    7124:	09 4f       	mov	r15,	r9	
    7126:	b0 12 ae 71 	call	#0x71ae	
    712a:	0a 4f       	mov	r15,	r10	
    712c:	b0 12 be 71 	call	#0x71be	
    7130:	0c 48       	mov	r8,	r12	
    7132:	0d 49       	mov	r9,	r13	
    7134:	0e 4a       	mov	r10,	r14	
    7136:	8b 12       	call	r11		
    7138:	38 41       	pop	r8		
    713a:	39 41       	pop	r9		
    713c:	3a 41       	pop	r10		
    713e:	3b 41       	pop	r11		
    7140:	30 41       	ret			

00007142 <nullnet_set_input_callback>:
    7142:	82 4f 56 25 	mov	r15,	&0x2556	
    7146:	30 41       	ret			

00007148 <init>:
    7148:	30 41       	ret			

0000714a <root_set_prefix>:
    714a:	30 41       	ret			

0000714c <root_start>:
    714c:	0f 43       	clr	r15		
    714e:	30 41       	ret			

00007150 <node_is_root>:
    7150:	0f 43       	clr	r15		
    7152:	30 41       	ret			

00007154 <get_root_ipaddr>:
    7154:	0f 43       	clr	r15		
    7156:	30 41       	ret			

00007158 <get_sr_node_ipaddr>:
    7158:	0f 43       	clr	r15		
    715a:	30 41       	ret			

0000715c <leave_network>:
    715c:	30 41       	ret			

0000715e <node_has_joined>:
    715e:	1f 43       	mov	#1,	r15	;r3 As==01
    7160:	30 41       	ret			

00007162 <node_is_reachable>:
    7162:	1f 43       	mov	#1,	r15	;r3 As==01
    7164:	30 41       	ret			

00007166 <global_repair>:
    7166:	30 41       	ret			

00007168 <local_repair>:
    7168:	30 41       	ret			

0000716a <ext_header_remove>:
    716a:	5f 43       	mov.b	#1,	r15	;r3 As==01
    716c:	30 41       	ret			

0000716e <ext_header_update>:
    716e:	1f 43       	mov	#1,	r15	;r3 As==01
    7170:	30 41       	ret			

00007172 <ext_header_hbh_update>:
    7172:	1f 43       	mov	#1,	r15	;r3 As==01
    7174:	30 41       	ret			

00007176 <ext_header_srh_update>:
    7176:	0f 43       	clr	r15		
    7178:	30 41       	ret			

0000717a <ext_header_srh_get_next_hop>:
    717a:	0f 43       	clr	r15		
    717c:	30 41       	ret			

0000717e <link_callback>:
    717e:	30 41       	ret			

00007180 <neighbor_state_changed>:
    7180:	30 41       	ret			

00007182 <drop_route>:
    7182:	30 41       	ret			

00007184 <is_in_leaf_mode>:
    7184:	4f 43       	clr.b	r15		
    7186:	30 41       	ret			

00007188 <packetbuf_hdrreduce>:
    7188:	1e 42 5a 25 	mov	&0x255a,r14	
    718c:	0e 9f       	cmp	r15,	r14	
    718e:	07 28       	jnc	$+16     	;abs 0x719e
    7190:	82 5f 58 25 	add	r15,	&0x2558	
    7194:	0e 8f       	sub	r15,	r14	
    7196:	82 4e 5a 25 	mov	r14,	&0x255a	
    719a:	1f 43       	mov	#1,	r15	;r3 As==01
    719c:	30 41       	ret			
    719e:	0f 43       	clr	r15		
    71a0:	30 41       	ret			

000071a2 <packetbuf_set_datalen>:
    71a2:	82 4f 5a 25 	mov	r15,	&0x255a	
    71a6:	30 41       	ret			

000071a8 <packetbuf_hdrptr>:
    71a8:	3f 40 5e 25 	mov	#9566,	r15	;#0x255e
    71ac:	30 41       	ret			

000071ae <packetbuf_datalen>:
    71ae:	1f 42 5a 25 	mov	&0x255a,r15	
    71b2:	30 41       	ret			

000071b4 <packetbuf_hdrlen>:
    71b4:	5f 42 5c 25 	mov.b	&0x255c,r15	
    71b8:	5f 52 58 25 	add.b	&0x2558,r15	
    71bc:	30 41       	ret			

000071be <packetbuf_dataptr>:
    71be:	b0 12 b4 71 	call	#0x71b4	
    71c2:	4f 4f       	mov.b	r15,	r15	
    71c4:	3f 50 5e 25 	add	#9566,	r15	;#0x255e
    71c8:	30 41       	ret			

000071ca <packetbuf_copyto>:
    71ca:	0b 12       	push	r11		
    71cc:	0a 12       	push	r10		
    71ce:	09 12       	push	r9		
    71d0:	08 12       	push	r8		
    71d2:	08 4f       	mov	r15,	r8	
    71d4:	5b 42 5c 25 	mov.b	&0x255c,r11	
    71d8:	19 42 5a 25 	mov	&0x255a,r9	
    71dc:	0a 4b       	mov	r11,	r10	
    71de:	0a 59       	add	r9,	r10	
    71e0:	3a 90 81 00 	cmp	#129,	r10	;#0x0081
    71e4:	0f 2c       	jc	$+32     	;abs 0x7204
    71e6:	0d 4b       	mov	r11,	r13	
    71e8:	3e 40 5e 25 	mov	#9566,	r14	;#0x255e
    71ec:	b0 12 b2 a7 	call	#0xa7b2	
    71f0:	b0 12 be 71 	call	#0x71be	
    71f4:	0d 49       	mov	r9,	r13	
    71f6:	0e 4f       	mov	r15,	r14	
    71f8:	0f 48       	mov	r8,	r15	
    71fa:	0f 5b       	add	r11,	r15	
    71fc:	b0 12 b2 a7 	call	#0xa7b2	
    7200:	0f 4a       	mov	r10,	r15	
    7202:	01 3c       	jmp	$+4      	;abs 0x7206
    7204:	0f 43       	clr	r15		
    7206:	38 41       	pop	r8		
    7208:	39 41       	pop	r9		
    720a:	3a 41       	pop	r10		
    720c:	3b 41       	pop	r11		
    720e:	30 41       	ret			

00007210 <packetbuf_totlen>:
    7210:	b0 12 b4 71 	call	#0x71b4	
    7214:	4f 4f       	mov.b	r15,	r15	
    7216:	1f 52 5a 25 	add	&0x255a,r15	
    721a:	30 41       	ret			

0000721c <packetbuf_hdralloc>:
    721c:	0b 12       	push	r11		
    721e:	0b 4f       	mov	r15,	r11	
    7220:	b0 12 10 72 	call	#0x7210	
    7224:	0e 4f       	mov	r15,	r14	
    7226:	0e 5b       	add	r11,	r14	
    7228:	3e 90 81 00 	cmp	#129,	r14	;#0x0081
    722c:	12 2c       	jc	$+38     	;abs 0x7252
    722e:	0e 4f       	mov	r15,	r14	
    7230:	3e 53       	add	#-1,	r14	;r3 As==11
    7232:	0f 4b       	mov	r11,	r15	
    7234:	3f 50 5e 25 	add	#9566,	r15	;#0x255e
    7238:	06 3c       	jmp	$+14     	;abs 0x7246
    723a:	0d 4f       	mov	r15,	r13	
    723c:	0d 5e       	add	r14,	r13	
    723e:	dd 4e 5e 25 	mov.b	9566(r14),0(r13)	;0x255e(r14), 0x0000(r13)
    7242:	00 00 
    7244:	3e 53       	add	#-1,	r14	;r3 As==11
    7246:	0e 93       	tst	r14		
    7248:	f8 37       	jge	$-14     	;abs 0x723a
    724a:	c2 5b 5c 25 	add.b	r11,	&0x255c	
    724e:	1f 43       	mov	#1,	r15	;r3 As==01
    7250:	01 3c       	jmp	$+4      	;abs 0x7254
    7252:	0f 43       	clr	r15		
    7254:	3b 41       	pop	r11		
    7256:	30 41       	ret			

00007258 <packetbuf_attr_clear>:
    7258:	3d 40 18 00 	mov	#24,	r13	;#0x0018
    725c:	0e 43       	clr	r14		
    725e:	3f 40 32 2e 	mov	#11826,	r15	;#0x2e32
    7262:	b0 12 ac a8 	call	#0xa8ac	
    7266:	3e 40 c6 ab 	mov	#-21562,r14	;#0xabc6
    726a:	3f 40 22 2e 	mov	#11810,	r15	;#0x2e22
    726e:	b0 12 08 62 	call	#0x6208	
    7272:	3e 40 c6 ab 	mov	#-21562,r14	;#0xabc6
    7276:	3f 40 2a 2e 	mov	#11818,	r15	;#0x2e2a
    727a:	b0 12 08 62 	call	#0x6208	
    727e:	30 41       	ret			

00007280 <packetbuf_clear>:
    7280:	82 43 58 25 	mov	#0,	&0x2558	;r3 As==00
    7284:	82 43 5a 25 	mov	#0,	&0x255a	;r3 As==00
    7288:	c2 43 5c 25 	mov.b	#0,	&0x255c	;r3 As==00
    728c:	b0 12 58 72 	call	#0x7258	
    7290:	30 41       	ret			

00007292 <packetbuf_copyfrom>:
    7292:	0b 12       	push	r11		
    7294:	0a 12       	push	r10		
    7296:	0a 4f       	mov	r15,	r10	
    7298:	0b 4e       	mov	r14,	r11	
    729a:	b0 12 80 72 	call	#0x7280	
    729e:	3b 90 81 00 	cmp	#129,	r11	;#0x0081
    72a2:	02 28       	jnc	$+6      	;abs 0x72a8
    72a4:	3b 40 80 00 	mov	#128,	r11	;#0x0080
    72a8:	0d 4b       	mov	r11,	r13	
    72aa:	0e 4a       	mov	r10,	r14	
    72ac:	3f 40 5e 25 	mov	#9566,	r15	;#0x255e
    72b0:	b0 12 b2 a7 	call	#0xa7b2	
    72b4:	82 4b 5a 25 	mov	r11,	&0x255a	
    72b8:	0f 4b       	mov	r11,	r15	
    72ba:	3a 41       	pop	r10		
    72bc:	3b 41       	pop	r11		
    72be:	30 41       	ret			

000072c0 <packetbuf_attr_copyto>:
    72c0:	0b 12       	push	r11		
    72c2:	0b 4e       	mov	r14,	r11	
    72c4:	3d 40 18 00 	mov	#24,	r13	;#0x0018
    72c8:	3e 40 32 2e 	mov	#11826,	r14	;#0x2e32
    72cc:	b0 12 b2 a7 	call	#0xa7b2	
    72d0:	3d 40 10 00 	mov	#16,	r13	;#0x0010
    72d4:	3e 40 22 2e 	mov	#11810,	r14	;#0x2e22
    72d8:	0f 4b       	mov	r11,	r15	
    72da:	b0 12 b2 a7 	call	#0xa7b2	
    72de:	3b 41       	pop	r11		
    72e0:	30 41       	ret			

000072e2 <packetbuf_attr_copyfrom>:
    72e2:	0b 12       	push	r11		
    72e4:	0b 4e       	mov	r14,	r11	
    72e6:	3d 40 18 00 	mov	#24,	r13	;#0x0018
    72ea:	0e 4f       	mov	r15,	r14	
    72ec:	3f 40 32 2e 	mov	#11826,	r15	;#0x2e32
    72f0:	b0 12 b2 a7 	call	#0xa7b2	
    72f4:	3d 40 10 00 	mov	#16,	r13	;#0x0010
    72f8:	0e 4b       	mov	r11,	r14	
    72fa:	3f 40 22 2e 	mov	#11810,	r15	;#0x2e22
    72fe:	b0 12 b2 a7 	call	#0xa7b2	
    7302:	3b 41       	pop	r11		
    7304:	30 41       	ret			

00007306 <packetbuf_set_attr>:
    7306:	4f 4f       	mov.b	r15,	r15	
    7308:	0f 5f       	rla	r15		
    730a:	8f 4e 32 2e 	mov	r14,	11826(r15);0x2e32(r15)
    730e:	1f 43       	mov	#1,	r15	;r3 As==01
    7310:	30 41       	ret			

00007312 <packetbuf_attr>:
    7312:	4f 4f       	mov.b	r15,	r15	
    7314:	0f 5f       	rla	r15		
    7316:	1f 4f 32 2e 	mov	11826(r15),r15	;0x2e32(r15)
    731a:	30 41       	ret			

0000731c <packetbuf_set_addr>:
    731c:	4f 4f       	mov.b	r15,	r15	
    731e:	3f 50 f4 ff 	add	#-12,	r15	;#0xfff4
    7322:	0f 5f       	rla	r15		
    7324:	0f 5f       	rla	r15		
    7326:	0f 5f       	rla	r15		
    7328:	3f 50 22 2e 	add	#11810,	r15	;#0x2e22
    732c:	b0 12 08 62 	call	#0x6208	
    7330:	1f 43       	mov	#1,	r15	;r3 As==01
    7332:	30 41       	ret			

00007334 <packetbuf_addr>:
    7334:	4f 4f       	mov.b	r15,	r15	
    7336:	3f 50 f4 ff 	add	#-12,	r15	;#0xfff4
    733a:	0f 5f       	rla	r15		
    733c:	0f 5f       	rla	r15		
    733e:	0f 5f       	rla	r15		
    7340:	3f 50 22 2e 	add	#11810,	r15	;#0x2e22
    7344:	30 41       	ret			

00007346 <packetbuf_holds_broadcast>:
    7346:	3e 40 c6 ab 	mov	#-21562,r14	;#0xabc6
    734a:	3f 40 2a 2e 	mov	#11818,	r15	;#0x2e2a
    734e:	b0 12 10 62 	call	#0x6210	
    7352:	30 41       	ret			

00007354 <platform_init_stage_one>:
    7354:	b0 12 b0 65 	call	#0x65b0	
    7358:	b0 12 de 61 	call	#0x61de	
    735c:	7f 40 10 00 	mov.b	#16,	r15	;#0x0010
    7360:	b0 12 e4 61 	call	#0x61e4	
    7364:	30 41       	ret			

00007366 <platform_init_stage_two>:
    7366:	31 82       	sub	#8,	r1	;r2 As==11
    7368:	3e 40 21 00 	mov	#33,	r14	;#0x0021
    736c:	0f 43       	clr	r15		
    736e:	b0 12 7a 7d 	call	#0x7d7a	
    7372:	7f 40 20 00 	mov.b	#32,	r15	;#0x0020
    7376:	b0 12 e4 61 	call	#0x61e4	
    737a:	b0 12 84 56 	call	#0x5684	
    737e:	d2 c3 4e 2e 	bic.b	#1,	&0x2e4e	;r3 As==01
    7382:	4f 43       	clr.b	r15		
    7384:	b0 12 e4 61 	call	#0x61e4	
    7388:	b0 12 c2 7e 	call	#0x7ec2	
    738c:	7f 40 10 00 	mov.b	#16,	r15	;#0x0010
    7390:	b0 12 f6 61 	call	#0x61f6	
    7394:	5f 42 4c 2e 	mov.b	&0x2e4c,r15	
    7398:	b0 12 ee 77 	call	#0x77ee	
    739c:	4f 43       	clr.b	r15		
    739e:	b0 12 f6 61 	call	#0x61f6	
    73a2:	3d 42       	mov	#8,	r13	;r2 As==11
    73a4:	0e 43       	clr	r14		
    73a6:	0f 41       	mov	r1,	r15	
    73a8:	b0 12 ac a8 	call	#0xa8ac	
    73ac:	0e 41       	mov	r1,	r14	
    73ae:	3f 42       	mov	#8,	r15	;r2 As==11
    73b0:	04 3c       	jmp	$+10     	;abs 0x73ba
    73b2:	de 4f 4c 2e 	mov.b	11852(r15),0(r14)	;0x2e4c(r15), 0x0000(r14)
    73b6:	00 00 
    73b8:	1e 53       	inc	r14		
    73ba:	3f 53       	add	#-1,	r15	;r3 As==11
    73bc:	3f 93       	cmp	#-1,	r15	;r3 As==11
    73be:	f9 23       	jnz	$-12     	;abs 0x73b2
    73c0:	0f 41       	mov	r1,	r15	
    73c2:	b0 12 22 62 	call	#0x6222	
    73c6:	b0 12 82 4d 	call	#0x4d82	
    73ca:	31 52       	add	#8,	r1	;r2 As==11
    73cc:	30 41       	ret			

000073ce <platform_init_stage_three>:
    73ce:	0b 12       	push	r11		
    73d0:	31 82       	sub	#8,	r1	;r2 As==11
    73d2:	b0 12 96 4f 	call	#0x4f96	
    73d6:	5b 42 ea 2d 	mov.b	&0x2dea,r11	
    73da:	8b 10       	swpb	r11		
    73dc:	5f 42 eb 2d 	mov.b	&0x2deb,r15	
    73e0:	0b 5f       	add	r15,	r11	
    73e2:	3d 42       	mov	#8,	r13	;r2 As==11
    73e4:	0e 43       	clr	r14		
    73e6:	0f 41       	mov	r1,	r15	
    73e8:	b0 12 ac a8 	call	#0xa8ac	
    73ec:	3e 40 ea 2d 	mov	#11754,	r14	;#0x2dea
    73f0:	0f 41       	mov	r1,	r15	
    73f2:	b0 12 08 62 	call	#0x6208	
    73f6:	0d 41       	mov	r1,	r13	
    73f8:	0e 4b       	mov	r11,	r14	
    73fa:	3f 40 cd ab 	mov	#-21555,r15	;#0xabcd
    73fe:	b0 12 06 4a 	call	#0x4a06	
    7402:	b2 90 03 00 	cmp	#3,	&0x118c	;#0x0003
    7406:	8c 11 
    7408:	11 38       	jl	$+36     	;abs 0x742c
    740a:	30 12 1b b0 	push	#-20453	;#0xb01b
    740e:	30 12 1f b0 	push	#-20449	;#0xb01f
    7412:	30 12 24 b0 	push	#-20444	;#0xb024
    7416:	b0 12 cc 9e 	call	#0x9ecc	
    741a:	31 50 06 00 	add	#6,	r1	;#0x0006
    741e:	30 12 d3 ff 	push	#-45		;#0xffd3
    7422:	30 12 33 b0 	push	#-20429	;#0xb033
    7426:	b0 12 cc 9e 	call	#0x9ecc	
    742a:	21 52       	add	#4,	r1	;r2 As==10
    742c:	3f 40 84 7a 	mov	#31364,	r15	;#0x7a84
    7430:	b0 12 42 7d 	call	#0x7d42	
    7434:	b0 12 c6 7a 	call	#0x7ac6	
    7438:	7f 40 20 00 	mov.b	#32,	r15	;#0x0020
    743c:	b0 12 f6 61 	call	#0x61f6	
    7440:	3d 40 00 0f 	mov	#3840,	r13	;#0x0f00
    7444:	0e 43       	clr	r14		
    7446:	3f 40 de 25 	mov	#9694,	r15	;#0x25de
    744a:	b0 12 7e 7c 	call	#0x7c7e	
    744e:	31 52       	add	#8,	r1	;r2 As==11
    7450:	3b 41       	pop	r11		
    7452:	30 41       	ret			

00007454 <platform_idle>:
    7454:	0b 12       	push	r11		
    7456:	b0 12 da 65 	call	#0x65da	
    745a:	0b 4f       	mov	r15,	r11	
    745c:	b0 12 6c 76 	call	#0x766c	
    7460:	0f 93       	tst	r15		
    7462:	02 24       	jz	$+6      	;abs 0x7468
    7464:	02 db       	bis	r11,	r2	
    7466:	1e 3c       	jmp	$+62     	;abs 0x74a4
    7468:	b0 12 2a 7d 	call	#0x7d2a	
    746c:	4f 93       	tst.b	r15		
    746e:	fa 23       	jnz	$-10     	;abs 0x7464
    7470:	3f 40 de 25 	mov	#9694,	r15	;#0x25de
    7474:	b0 12 9a 7c 	call	#0x7c9a	
    7478:	0f 93       	tst	r15		
    747a:	08 24       	jz	$+18     	;abs 0x748c
    747c:	b0 12 88 7e 	call	#0x7e88	
    7480:	3f 40 de 25 	mov	#9694,	r15	;#0x25de
    7484:	b0 12 c4 7c 	call	#0x7cc4	
    7488:	b0 12 e4 65 	call	#0x65e4	
    748c:	b0 12 9a 7e 	call	#0x7e9a	
    7490:	82 93 f2 2d 	tst	&0x2df2	
    7494:	03 24       	jz	$+8      	;abs 0x749c
    7496:	32 d0 18 00 	bis	#24,	r2	;#0x0018
    749a:	02 3c       	jmp	$+6      	;abs 0x74a0
    749c:	32 d0 d8 00 	bis	#216,	r2	;#0x00d8
    74a0:	b0 12 74 7e 	call	#0x7e74	
    74a4:	3b 41       	pop	r11		
    74a6:	30 41       	ret			

000074a8 <call_process>:
    74a8:	0b 12       	push	r11		
    74aa:	0a 12       	push	r10		
    74ac:	0b 4f       	mov	r15,	r11	
    74ae:	4a 4e       	mov.b	r14,	r10	
    74b0:	df b3 08 00 	bit.b	#1,	8(r15)	;r3 As==01, 0x0008(r15)
    74b4:	19 24       	jz	$+52     	;abs 0x74e8
    74b6:	1c 4f 04 00 	mov	4(r15),	r12	;0x0004(r15)
    74ba:	0c 93       	tst	r12		
    74bc:	15 24       	jz	$+44     	;abs 0x74e8
    74be:	82 4f e6 25 	mov	r15,	&0x25e6	
    74c2:	ef 43 08 00 	mov.b	#2,	8(r15)	;r3 As==10, 0x0008(r15)
    74c6:	3f 50 06 00 	add	#6,	r15	;#0x0006
    74ca:	8c 12       	call	r12		
    74cc:	8f 11       	sxt	r15		
    74ce:	2f 83       	decd	r15		
    74d0:	2f 93       	cmp	#2,	r15	;r3 As==10
    74d2:	03 28       	jnc	$+8      	;abs 0x74da
    74d4:	7a 90 83 ff 	cmp.b	#-125,	r10	;#0xff83
    74d8:	05 20       	jnz	$+12     	;abs 0x74e4
    74da:	0e 4b       	mov	r11,	r14	
    74dc:	0f 4b       	mov	r11,	r15	
    74de:	b0 12 ee 74 	call	#0x74ee	
    74e2:	02 3c       	jmp	$+6      	;abs 0x74e8
    74e4:	db 43 08 00 	mov.b	#1,	8(r11)	;r3 As==01, 0x0008(r11)
    74e8:	3a 41       	pop	r10		
    74ea:	3b 41       	pop	r11		
    74ec:	30 41       	ret			

000074ee <exit_process>:
    74ee:	0b 12       	push	r11		
    74f0:	0a 12       	push	r10		
    74f2:	09 12       	push	r9		
    74f4:	08 12       	push	r8		
    74f6:	0b 4f       	mov	r15,	r11	
    74f8:	08 4e       	mov	r14,	r8	
    74fa:	19 42 e6 25 	mov	&0x25e6,r9	
    74fe:	1a 42 e8 25 	mov	&0x25e8,r10	
    7502:	0f 4a       	mov	r10,	r15	
    7504:	01 3c       	jmp	$+4      	;abs 0x7508
    7506:	2f 4f       	mov	@r15,	r15	
    7508:	0f 9b       	cmp	r11,	r15	
    750a:	03 24       	jz	$+8      	;abs 0x7512
    750c:	0f 93       	tst	r15		
    750e:	fb 23       	jnz	$-8      	;abs 0x7506
    7510:	34 3c       	jmp	$+106    	;abs 0x757a
    7512:	0b 93       	tst	r11		
    7514:	32 24       	jz	$+102    	;abs 0x757a
    7516:	cb 93 08 00 	tst.b	8(r11)		;0x0008(r11)
    751a:	1d 24       	jz	$+60     	;abs 0x7556
    751c:	cb 43 08 00 	mov.b	#0,	8(r11)	;r3 As==00, 0x0008(r11)
    7520:	09 3c       	jmp	$+20     	;abs 0x7534
    7522:	0b 9a       	cmp	r10,	r11	
    7524:	06 24       	jz	$+14     	;abs 0x7532
    7526:	0d 4b       	mov	r11,	r13	
    7528:	7e 40 87 ff 	mov.b	#-121,	r14	;#0xff87
    752c:	0f 4a       	mov	r10,	r15	
    752e:	b0 12 a8 74 	call	#0x74a8	
    7532:	2a 4a       	mov	@r10,	r10	
    7534:	0a 93       	tst	r10		
    7536:	f5 23       	jnz	$-20     	;abs 0x7522
    7538:	1c 4b 04 00 	mov	4(r11),	r12	;0x0004(r11)
    753c:	0c 93       	tst	r12		
    753e:	0b 24       	jz	$+24     	;abs 0x7556
    7540:	0b 98       	cmp	r8,	r11	
    7542:	09 24       	jz	$+20     	;abs 0x7556
    7544:	82 4b e6 25 	mov	r11,	&0x25e6	
    7548:	0d 43       	clr	r13		
    754a:	7e 40 83 ff 	mov.b	#-125,	r14	;#0xff83
    754e:	0f 4b       	mov	r11,	r15	
    7550:	3f 50 06 00 	add	#6,	r15	;#0x0006
    7554:	8c 12       	call	r12		
    7556:	1f 42 e8 25 	mov	&0x25e8,r15	
    755a:	0b 9f       	cmp	r15,	r11	
    755c:	0a 20       	jnz	$+22     	;abs 0x7572
    755e:	a2 4b e8 25 	mov	@r11,	&0x25e8	
    7562:	09 3c       	jmp	$+20     	;abs 0x7576
    7564:	2e 4f       	mov	@r15,	r14	
    7566:	0e 9b       	cmp	r11,	r14	
    7568:	03 20       	jnz	$+8      	;abs 0x7570
    756a:	af 4b 00 00 	mov	@r11,	0(r15)	;0x0000(r15)
    756e:	03 3c       	jmp	$+8      	;abs 0x7576
    7570:	0f 4e       	mov	r14,	r15	
    7572:	0f 93       	tst	r15		
    7574:	f7 23       	jnz	$-16     	;abs 0x7564
    7576:	82 49 e6 25 	mov	r9,	&0x25e6	
    757a:	38 41       	pop	r8		
    757c:	39 41       	pop	r9		
    757e:	3a 41       	pop	r10		
    7580:	3b 41       	pop	r11		
    7582:	30 41       	ret			

00007584 <do_poll>:
    7584:	0b 12       	push	r11		
    7586:	c2 43 ea 25 	mov.b	#0,	&0x25ea	;r3 As==00
    758a:	1b 42 e8 25 	mov	&0x25e8,r11	
    758e:	0e 3c       	jmp	$+30     	;abs 0x75ac
    7590:	cb 93 09 00 	tst.b	9(r11)		;0x0009(r11)
    7594:	0a 24       	jz	$+22     	;abs 0x75aa
    7596:	db 43 08 00 	mov.b	#1,	8(r11)	;r3 As==01, 0x0008(r11)
    759a:	cb 43 09 00 	mov.b	#0,	9(r11)	;r3 As==00, 0x0009(r11)
    759e:	0d 43       	clr	r13		
    75a0:	7e 40 82 ff 	mov.b	#-126,	r14	;#0xff82
    75a4:	0f 4b       	mov	r11,	r15	
    75a6:	b0 12 a8 74 	call	#0x74a8	
    75aa:	2b 4b       	mov	@r11,	r11	
    75ac:	0b 93       	tst	r11		
    75ae:	f0 23       	jnz	$-30     	;abs 0x7590
    75b0:	3b 41       	pop	r11		
    75b2:	30 41       	ret			

000075b4 <process_alloc_event>:
    75b4:	5f 42 eb 25 	mov.b	&0x25eb,r15	
    75b8:	4e 4f       	mov.b	r15,	r14	
    75ba:	5e 53       	inc.b	r14		
    75bc:	c2 4e eb 25 	mov.b	r14,	&0x25eb	
    75c0:	30 41       	ret			

000075c2 <process_init>:
    75c2:	f2 40 8a ff 	mov.b	#-118,	&0x25eb	;#0xff8a
    75c6:	eb 25 
    75c8:	c2 43 ec 25 	mov.b	#0,	&0x25ec	;r3 As==00
    75cc:	c2 43 ed 25 	mov.b	#0,	&0x25ed	;r3 As==00
    75d0:	82 43 e8 25 	mov	#0,	&0x25e8	;r3 As==00
    75d4:	82 43 e6 25 	mov	#0,	&0x25e6	;r3 As==00
    75d8:	30 41       	ret			

000075da <process_run>:
    75da:	0b 12       	push	r11		
    75dc:	0a 12       	push	r10		
    75de:	09 12       	push	r9		
    75e0:	5f 42 ea 25 	mov.b	&0x25ea,r15	
    75e4:	4f 93       	tst.b	r15		
    75e6:	02 24       	jz	$+6      	;abs 0x75ec
    75e8:	b0 12 84 75 	call	#0x7584	
    75ec:	5d 42 ed 25 	mov.b	&0x25ed,r13	
    75f0:	4d 93       	tst.b	r13		
    75f2:	32 24       	jz	$+102    	;abs 0x7658
    75f4:	5e 42 ec 25 	mov.b	&0x25ec,r14	
    75f8:	0f 4e       	mov	r14,	r15	
    75fa:	0f 5f       	rla	r15		
    75fc:	0f 5e       	add	r14,	r15	
    75fe:	0f 5f       	rla	r15		
    7600:	3f 50 ee 25 	add	#9710,	r15	;#0x25ee
    7604:	6a 4f       	mov.b	@r15,	r10	
    7606:	19 4f 02 00 	mov	2(r15),	r9	;0x0002(r15)
    760a:	1f 4f 04 00 	mov	4(r15),	r15	;0x0004(r15)
    760e:	1e 53       	inc	r14		
    7610:	7e f0 1f 00 	and.b	#31,	r14	;#0x001f
    7614:	c2 4e ec 25 	mov.b	r14,	&0x25ec	
    7618:	7d 53       	add.b	#-1,	r13	;r3 As==11
    761a:	c2 4d ed 25 	mov.b	r13,	&0x25ed	
    761e:	0f 93       	tst	r15		
    7620:	12 20       	jnz	$+38     	;abs 0x7646
    7622:	1b 42 e8 25 	mov	&0x25e8,r11	
    7626:	0c 3c       	jmp	$+26     	;abs 0x7640
    7628:	5f 42 ea 25 	mov.b	&0x25ea,r15	
    762c:	4f 93       	tst.b	r15		
    762e:	02 24       	jz	$+6      	;abs 0x7634
    7630:	b0 12 84 75 	call	#0x7584	
    7634:	0d 49       	mov	r9,	r13	
    7636:	4e 4a       	mov.b	r10,	r14	
    7638:	0f 4b       	mov	r11,	r15	
    763a:	b0 12 a8 74 	call	#0x74a8	
    763e:	2b 4b       	mov	@r11,	r11	
    7640:	0b 93       	tst	r11		
    7642:	f2 23       	jnz	$-26     	;abs 0x7628
    7644:	09 3c       	jmp	$+20     	;abs 0x7658
    7646:	7a 90 81 ff 	cmp.b	#-127,	r10	;#0xff81
    764a:	02 20       	jnz	$+6      	;abs 0x7650
    764c:	df 43 08 00 	mov.b	#1,	8(r15)	;r3 As==01, 0x0008(r15)
    7650:	0d 49       	mov	r9,	r13	
    7652:	4e 4a       	mov.b	r10,	r14	
    7654:	b0 12 a8 74 	call	#0x74a8	
    7658:	5f 42 ea 25 	mov.b	&0x25ea,r15	
    765c:	5e 42 ed 25 	mov.b	&0x25ed,r14	
    7660:	4f 4f       	mov.b	r15,	r15	
    7662:	0f 5e       	add	r14,	r15	
    7664:	39 41       	pop	r9		
    7666:	3a 41       	pop	r10		
    7668:	3b 41       	pop	r11		
    766a:	30 41       	ret			

0000766c <process_nevents>:
    766c:	5f 42 ea 25 	mov.b	&0x25ea,r15	
    7670:	5e 42 ed 25 	mov.b	&0x25ed,r14	
    7674:	4f 4f       	mov.b	r15,	r15	
    7676:	0f 5e       	add	r14,	r15	
    7678:	30 41       	ret			

0000767a <process_post>:
    767a:	0b 12       	push	r11		
    767c:	0a 12       	push	r10		
    767e:	5c 42 ed 25 	mov.b	&0x25ed,r12	
    7682:	7c 90 20 00 	cmp.b	#32,	r12	;#0x0020
    7686:	16 24       	jz	$+46     	;abs 0x76b4
    7688:	4b 4c       	mov.b	r12,	r11	
    768a:	5b 52 ec 25 	add.b	&0x25ec,r11	
    768e:	3b f0 1f 00 	and	#31,	r11	;#0x001f
    7692:	0a 4b       	mov	r11,	r10	
    7694:	0a 5a       	rla	r10		
    7696:	0b 5a       	add	r10,	r11	
    7698:	0b 5b       	rla	r11		
    769a:	3b 50 ee 25 	add	#9710,	r11	;#0x25ee
    769e:	cb 4e 00 00 	mov.b	r14,	0(r11)	;0x0000(r11)
    76a2:	8b 4d 02 00 	mov	r13,	2(r11)	;0x0002(r11)
    76a6:	8b 4f 04 00 	mov	r15,	4(r11)	;0x0004(r11)
    76aa:	5c 53       	inc.b	r12		
    76ac:	c2 4c ed 25 	mov.b	r12,	&0x25ed	
    76b0:	0f 43       	clr	r15		
    76b2:	01 3c       	jmp	$+4      	;abs 0x76b6
    76b4:	1f 43       	mov	#1,	r15	;r3 As==01
    76b6:	3a 41       	pop	r10		
    76b8:	3b 41       	pop	r11		
    76ba:	30 41       	ret			

000076bc <process_post_synch>:
    76bc:	0b 12       	push	r11		
    76be:	1b 42 e6 25 	mov	&0x25e6,r11	
    76c2:	b0 12 a8 74 	call	#0x74a8	
    76c6:	82 4b e6 25 	mov	r11,	&0x25e6	
    76ca:	3b 41       	pop	r11		
    76cc:	30 41       	ret			

000076ce <process_start>:
    76ce:	0b 12       	push	r11		
    76d0:	1b 42 e8 25 	mov	&0x25e8,r11	
    76d4:	0c 4b       	mov	r11,	r12	
    76d6:	01 3c       	jmp	$+4      	;abs 0x76da
    76d8:	2c 4c       	mov	@r12,	r12	
    76da:	0c 9f       	cmp	r15,	r12	
    76dc:	11 24       	jz	$+36     	;abs 0x7700
    76de:	0c 93       	tst	r12		
    76e0:	fb 23       	jnz	$-8      	;abs 0x76d8
    76e2:	0f 93       	tst	r15		
    76e4:	0d 24       	jz	$+28     	;abs 0x7700
    76e6:	8f 4b 00 00 	mov	r11,	0(r15)	;0x0000(r15)
    76ea:	82 4f e8 25 	mov	r15,	&0x25e8	
    76ee:	df 43 08 00 	mov.b	#1,	8(r15)	;r3 As==01, 0x0008(r15)
    76f2:	8f 43 06 00 	mov	#0,	6(r15)	;r3 As==00, 0x0006(r15)
    76f6:	0d 4e       	mov	r14,	r13	
    76f8:	7e 40 81 ff 	mov.b	#-127,	r14	;#0xff81
    76fc:	b0 12 bc 76 	call	#0x76bc	
    7700:	3b 41       	pop	r11		
    7702:	30 41       	ret			

00007704 <process_poll>:
    7704:	0f 93       	tst	r15		
    7706:	09 24       	jz	$+20     	;abs 0x771a
    7708:	5e 4f 08 00 	mov.b	8(r15),	r14	;0x0008(r15)
    770c:	7e 53       	add.b	#-1,	r14	;r3 As==11
    770e:	6e 93       	cmp.b	#2,	r14	;r3 As==10
    7710:	04 2c       	jc	$+10     	;abs 0x771a
    7712:	df 43 09 00 	mov.b	#1,	9(r15)	;r3 As==01, 0x0009(r15)
    7716:	d2 43 ea 25 	mov.b	#1,	&0x25ea	;r3 As==01
    771a:	30 41       	ret			

0000771c <queuebuf_init>:
    771c:	3f 40 18 22 	mov	#8728,	r15	;#0x2218
    7720:	b0 12 52 64 	call	#0x6452	
    7724:	3f 40 20 22 	mov	#8736,	r15	;#0x2220
    7728:	b0 12 52 64 	call	#0x6452	
    772c:	30 41       	ret			

0000772e <queuebuf_new_from_packetbuf>:
    772e:	0b 12       	push	r11		
    7730:	0a 12       	push	r10		
    7732:	3f 40 20 22 	mov	#8736,	r15	;#0x2220
    7736:	b0 12 88 64 	call	#0x6488	
    773a:	0b 4f       	mov	r15,	r11	
    773c:	0f 93       	tst	r15		
    773e:	1c 24       	jz	$+58     	;abs 0x7778
    7740:	3f 40 18 22 	mov	#8728,	r15	;#0x2218
    7744:	b0 12 88 64 	call	#0x6488	
    7748:	0a 4f       	mov	r15,	r10	
    774a:	8b 4f 00 00 	mov	r15,	0(r11)	;0x0000(r11)
    774e:	0f 93       	tst	r15		
    7750:	07 20       	jnz	$+16     	;abs 0x7760
    7752:	0e 4b       	mov	r11,	r14	
    7754:	3f 40 20 22 	mov	#8736,	r15	;#0x2220
    7758:	b0 12 c6 64 	call	#0x64c6	
    775c:	0b 43       	clr	r11		
    775e:	0c 3c       	jmp	$+26     	;abs 0x7778
    7760:	b0 12 ca 71 	call	#0x71ca	
    7764:	8a 4f 80 00 	mov	r15,	128(r10);0x0080(r10)
    7768:	0e 4a       	mov	r10,	r14	
    776a:	3e 50 9a 00 	add	#154,	r14	;#0x009a
    776e:	0f 4a       	mov	r10,	r15	
    7770:	3f 50 82 00 	add	#130,	r15	;#0x0082
    7774:	b0 12 c0 72 	call	#0x72c0	
    7778:	0f 4b       	mov	r11,	r15	
    777a:	3a 41       	pop	r10		
    777c:	3b 41       	pop	r11		
    777e:	30 41       	ret			

00007780 <queuebuf_update_attr_from_packetbuf>:
    7780:	2f 4f       	mov	@r15,	r15	
    7782:	0e 4f       	mov	r15,	r14	
    7784:	3e 50 9a 00 	add	#154,	r14	;#0x009a
    7788:	3f 50 82 00 	add	#130,	r15	;#0x0082
    778c:	b0 12 c0 72 	call	#0x72c0	
    7790:	30 41       	ret			

00007792 <queuebuf_free>:
    7792:	0b 12       	push	r11		
    7794:	0b 4f       	mov	r15,	r11	
    7796:	0e 4f       	mov	r15,	r14	
    7798:	3f 40 20 22 	mov	#8736,	r15	;#0x2220
    779c:	b0 12 f8 64 	call	#0x64f8	
    77a0:	0f 93       	tst	r15		
    77a2:	0a 24       	jz	$+22     	;abs 0x77b8
    77a4:	2e 4b       	mov	@r11,	r14	
    77a6:	3f 40 18 22 	mov	#8728,	r15	;#0x2218
    77aa:	b0 12 c6 64 	call	#0x64c6	
    77ae:	0e 4b       	mov	r11,	r14	
    77b0:	3f 40 20 22 	mov	#8736,	r15	;#0x2220
    77b4:	b0 12 c6 64 	call	#0x64c6	
    77b8:	3b 41       	pop	r11		
    77ba:	30 41       	ret			

000077bc <queuebuf_to_packetbuf>:
    77bc:	0b 12       	push	r11		
    77be:	0b 4f       	mov	r15,	r11	
    77c0:	0e 4f       	mov	r15,	r14	
    77c2:	3f 40 20 22 	mov	#8736,	r15	;#0x2220
    77c6:	b0 12 f8 64 	call	#0x64f8	
    77ca:	0f 93       	tst	r15		
    77cc:	0e 24       	jz	$+30     	;abs 0x77ea
    77ce:	2b 4b       	mov	@r11,	r11	
    77d0:	1e 4b 80 00 	mov	128(r11),r14	;0x0080(r11)
    77d4:	0f 4b       	mov	r11,	r15	
    77d6:	b0 12 92 72 	call	#0x7292	
    77da:	0e 4b       	mov	r11,	r14	
    77dc:	3e 50 9a 00 	add	#154,	r14	;#0x009a
    77e0:	0f 4b       	mov	r11,	r15	
    77e2:	3f 50 82 00 	add	#130,	r15	;#0x0082
    77e6:	b0 12 e2 72 	call	#0x72e2	
    77ea:	3b 41       	pop	r11		
    77ec:	30 41       	ret			

000077ee <random_init>:
    77ee:	b0 12 78 a7 	call	#0xa778	
    77f2:	30 41       	ret			

000077f4 <random_rand>:
    77f4:	b0 12 52 a7 	call	#0xa752	
    77f8:	30 41       	ret			

000077fa <ringbuf_init>:
    77fa:	8f 4e 00 00 	mov	r14,	0(r15)	;0x0000(r15)
    77fe:	7d 53       	add.b	#-1,	r13	;r3 As==11
    7800:	cf 4d 02 00 	mov.b	r13,	2(r15)	;0x0002(r15)
    7804:	cf 43 03 00 	mov.b	#0,	3(r15)	;r3 As==00, 0x0003(r15)
    7808:	cf 43 04 00 	mov.b	#0,	4(r15)	;r3 As==00, 0x0004(r15)
    780c:	30 41       	ret			

0000780e <ringbuf_put>:
    780e:	0b 12       	push	r11		
    7810:	5c 4f 03 00 	mov.b	3(r15),	r12	;0x0003(r15)
    7814:	5d 4f 04 00 	mov.b	4(r15),	r13	;0x0004(r15)
    7818:	0b 4c       	mov	r12,	r11	
    781a:	0b 8d       	sub	r13,	r11	
    781c:	0d 4b       	mov	r11,	r13	
    781e:	5b 4f 02 00 	mov.b	2(r15),	r11	;0x0002(r15)
    7822:	0d fb       	and	r11,	r13	
    7824:	4d 9b       	cmp.b	r11,	r13	
    7826:	0c 24       	jz	$+26     	;abs 0x7840
    7828:	2c 5f       	add	@r15,	r12	
    782a:	cc 4e 00 00 	mov.b	r14,	0(r12)	;0x0000(r12)
    782e:	5e 4f 03 00 	mov.b	3(r15),	r14	;0x0003(r15)
    7832:	5e 53       	inc.b	r14		
    7834:	5e ff 02 00 	and.b	2(r15),	r14	;0x0002(r15)
    7838:	cf 4e 03 00 	mov.b	r14,	3(r15)	;0x0003(r15)
    783c:	1f 43       	mov	#1,	r15	;r3 As==01
    783e:	01 3c       	jmp	$+4      	;abs 0x7842
    7840:	0f 43       	clr	r15		
    7842:	3b 41       	pop	r11		
    7844:	30 41       	ret			

00007846 <ringbuf_get>:
    7846:	0b 12       	push	r11		
    7848:	0a 12       	push	r10		
    784a:	5e 4f 04 00 	mov.b	4(r15),	r14	;0x0004(r15)
    784e:	5c 4f 02 00 	mov.b	2(r15),	r12	;0x0002(r15)
    7852:	5d 4f 03 00 	mov.b	3(r15),	r13	;0x0003(r15)
    7856:	4b 4e       	mov.b	r14,	r11	
    7858:	0d 8b       	sub	r11,	r13	
    785a:	4a 4c       	mov.b	r12,	r10	
    785c:	0d ba       	bit	r10,	r13	
    785e:	08 24       	jz	$+18     	;abs 0x7870
    7860:	2b 5f       	add	@r15,	r11	
    7862:	6d 4b       	mov.b	@r11,	r13	
    7864:	5e 53       	inc.b	r14		
    7866:	4e fc       	and.b	r12,	r14	
    7868:	cf 4e 04 00 	mov.b	r14,	4(r15)	;0x0004(r15)
    786c:	4f 4d       	mov.b	r13,	r15	
    786e:	01 3c       	jmp	$+4      	;abs 0x7872
    7870:	3f 43       	mov	#-1,	r15	;r3 As==11
    7872:	3a 41       	pop	r10		
    7874:	3b 41       	pop	r11		
    7876:	30 41       	ret			

00007878 <timera0>:
    7878:	0f 12       	push	r15		
    787a:	0e 12       	push	r14		
    787c:	0d 12       	push	r13		
    787e:	0c 12       	push	r12		
    7880:	b0 12 74 7e 	call	#0x7e74	
    7884:	b0 12 ce 78 	call	#0x78ce	
    7888:	b0 12 6c 76 	call	#0x766c	
    788c:	0f 93       	tst	r15		
    788e:	04 24       	jz	$+10     	;abs 0x7898
    7890:	03 38       	jl	$+8      	;abs 0x7898
    7892:	b1 c0 f0 00 	bic	#240,	8(r1)	;#0x00f0, 0x0008(r1)
    7896:	08 00 
    7898:	b0 12 9a 7e 	call	#0x7e9a	
    789c:	3c 41       	pop	r12		
    789e:	3d 41       	pop	r13		
    78a0:	3e 41       	pop	r14		
    78a2:	3f 41       	pop	r15		
    78a4:	00 13       	reti			

000078a6 <rtimer_arch_init>:
    78a6:	32 c2       	dint			
    78a8:	03 43       	nop			
    78aa:	b2 40 10 00 	mov	#16,	&0x0162	;#0x0010
    78ae:	62 01 
    78b0:	32 d2       	eint			
    78b2:	30 41       	ret			

000078b4 <rtimer_arch_now>:
    78b4:	1f 42 70 01 	mov	&0x0170,r15	
    78b8:	1e 42 70 01 	mov	&0x0170,r14	
    78bc:	0f 9e       	cmp	r14,	r15	
    78be:	fa 23       	jnz	$-10     	;abs 0x78b4
    78c0:	30 41       	ret			

000078c2 <rtimer_arch_schedule>:
    78c2:	82 4f 72 01 	mov	r15,	&0x0172	
    78c6:	30 41       	ret			

000078c8 <rtimer_init>:
    78c8:	b0 12 a6 78 	call	#0x78a6	
    78cc:	30 41       	ret			

000078ce <rtimer_run_next>:
    78ce:	1d 42 1e 2c 	mov	&0x2c1e,r13	
    78d2:	0d 93       	tst	r13		
    78d4:	0e 24       	jz	$+30     	;abs 0x78f2
    78d6:	82 43 1e 2c 	mov	#0,	&0x2c1e	;r3 As==00
    78da:	1e 4d 04 00 	mov	4(r13),	r14	;0x0004(r13)
    78de:	0f 4d       	mov	r13,	r15	
    78e0:	9d 12 02 00 	call	2(r13)		;0x0002(r13)
    78e4:	1f 42 1e 2c 	mov	&0x2c1e,r15	
    78e8:	0f 93       	tst	r15		
    78ea:	03 24       	jz	$+8      	;abs 0x78f2
    78ec:	2f 4f       	mov	@r15,	r15	
    78ee:	b0 12 c2 78 	call	#0x78c2	
    78f2:	30 41       	ret			

000078f4 <process_thread_sensors_process>:
    78f4:	0b 12       	push	r11		
    78f6:	0b 4f       	mov	r15,	r11	
    78f8:	2f 4f       	mov	@r15,	r15	
    78fa:	3f 90 75 00 	cmp	#117,	r15	;#0x0075
    78fe:	23 24       	jz	$+72     	;abs 0x7946
    7900:	3f 90 7c 00 	cmp	#124,	r15	;#0x007c
    7904:	52 24       	jz	$+166    	;abs 0x79aa
    7906:	0f 93       	tst	r15		
    7908:	49 20       	jnz	$+148    	;abs 0x799c
    790a:	b0 12 b4 75 	call	#0x75b4	
    790e:	c2 4f 54 2e 	mov.b	r15,	&0x2e54	
    7912:	82 43 22 2c 	mov	#0,	&0x2c22	;r3 As==00
    7916:	09 3c       	jmp	$+20     	;abs 0x792a
    7918:	cf 43 4a 2e 	mov.b	#0,	11850(r15);r3 As==00, 0x2e4a(r15)
    791c:	0e 43       	clr	r14		
    791e:	3f 40 80 00 	mov	#128,	r15	;#0x0080
    7922:	9d 12 04 00 	call	4(r13)		;0x0004(r13)
    7926:	92 53 22 2c 	inc	&0x2c22	
    792a:	1f 42 22 2c 	mov	&0x2c22,r15	
    792e:	0e 4f       	mov	r15,	r14	
    7930:	0e 5e       	rla	r14		
    7932:	1d 4e 0c 11 	mov	4364(r14),r13	;0x110c(r14)
    7936:	0d 93       	tst	r13		
    7938:	ef 23       	jnz	$-32     	;abs 0x7918
    793a:	c2 4f 20 2c 	mov.b	r15,	&0x2c20	
    793e:	bb 40 75 00 	mov	#117,	0(r11)	;#0x0075, 0x0000(r11)
    7942:	00 00 
    7944:	30 3c       	jmp	$+98     	;abs 0x79a6
    7946:	82 43 24 2c 	mov	#0,	&0x2c24	;r3 As==00
    794a:	82 43 22 2c 	mov	#0,	&0x2c22	;r3 As==00
    794e:	1c 3c       	jmp	$+58     	;abs 0x7988
    7950:	cf 93 4a 2e 	tst.b	11850(r15)	;0x2e4a(r15)
    7954:	17 34       	jge	$+48     	;abs 0x7984
    7956:	0f 5f       	rla	r15		
    7958:	1d 4f 0c 11 	mov	4364(r15),r13	;0x110c(r15)
    795c:	5e 42 54 2e 	mov.b	&0x2e54,r14	
    7960:	0f 43       	clr	r15		
    7962:	b0 12 7a 76 	call	#0x767a	
    7966:	0f 93       	tst	r15		
    7968:	04 20       	jnz	$+10     	;abs 0x7972
    796a:	bb 40 7c 00 	mov	#124,	0(r11)	;#0x007c, 0x0000(r11)
    796e:	00 00 
    7970:	1a 3c       	jmp	$+54     	;abs 0x79a6
    7972:	1f 42 22 2c 	mov	&0x2c22,r15	
    7976:	3f 50 4a 2e 	add	#11850,	r15	;#0x2e4a
    797a:	ff f0 7f 00 	and.b	#127,	0(r15)	;#0x007f, 0x0000(r15)
    797e:	00 00 
    7980:	92 53 24 2c 	inc	&0x2c24	
    7984:	92 53 22 2c 	inc	&0x2c22	
    7988:	1f 42 22 2c 	mov	&0x2c22,r15	
    798c:	5e 42 20 2c 	mov.b	&0x2c20,r14	
    7990:	0f 9e       	cmp	r14,	r15	
    7992:	de 3b       	jl	$-66     	;abs 0x7950
    7994:	82 93 24 2c 	tst	&0x2c24	
    7998:	d6 23       	jnz	$-82     	;abs 0x7946
    799a:	d1 3f       	jmp	$-92     	;abs 0x793e
    799c:	8b 43 00 00 	mov	#0,	0(r11)	;r3 As==00, 0x0000(r11)
    79a0:	7f 40 03 00 	mov.b	#3,	r15	;#0x0003
    79a4:	06 3c       	jmp	$+14     	;abs 0x79b2
    79a6:	5f 43       	mov.b	#1,	r15	;r3 As==01
    79a8:	04 3c       	jmp	$+10     	;abs 0x79b2
    79aa:	5e 92 54 2e 	cmp.b	&0x2e54,r14	
    79ae:	fb 23       	jnz	$-8      	;abs 0x79a6
    79b0:	e0 3f       	jmp	$-62     	;abs 0x7972
    79b2:	3b 41       	pop	r11		
    79b4:	30 41       	ret			

000079b6 <sensors_changed>:
    79b6:	5c 42 20 2c 	mov.b	&0x2c20,r12	
    79ba:	0e 43       	clr	r14		
    79bc:	0e 3c       	jmp	$+30     	;abs 0x79da
    79be:	0d 4e       	mov	r14,	r13	
    79c0:	0d 5d       	rla	r13		
    79c2:	8d 9f 0c 11 	cmp	r15,	4364(r13);0x110c(r13)
    79c6:	08 20       	jnz	$+18     	;abs 0x79d8
    79c8:	fe d0 80 ff 	bis.b	#-128,	11850(r14);#0xff80, 0x2e4a(r14)
    79cc:	4a 2e 
   79ce:	3f 40 28 22 	mov	#8744,	r15	;#0x2228
    79d2:	b0 12 04 77 	call	#0x7704	
    79d6:	30 41       	ret			
    79d8:	1e 53       	inc	r14		
    79da:	0e 9c       	cmp	r12,	r14	
    79dc:	f0 3b       	jl	$-30     	;abs 0x79be
    79de:	f4 3f       	jmp	$-22     	;abs 0x79c8

000079e0 <process_thread_serial_line_process>:
    79e0:	0b 12       	push	r11		
    79e2:	0b 4f       	mov	r15,	r11	
    79e4:	2f 4f       	mov	@r15,	r15	
    79e6:	3f 90 67 00 	cmp	#103,	r15	;#0x0067
    79ea:	0b 24       	jz	$+24     	;abs 0x7a02
    79ec:	3f 90 79 00 	cmp	#121,	r15	;#0x0079
    79f0:	43 24       	jz	$+136    	;abs 0x7a78
    79f2:	0f 93       	tst	r15		
    79f4:	3a 20       	jnz	$+118    	;abs 0x7a6a
    79f6:	b0 12 b4 75 	call	#0x75b4	
    79fa:	c2 4f 55 2e 	mov.b	r15,	&0x2e55	
    79fe:	82 43 2e 2c 	mov	#0,	&0x2c2e	;r3 As==00
    7a02:	3f 40 28 2c 	mov	#11304,	r15	;#0x2c28
    7a06:	b0 12 46 78 	call	#0x7846	
    7a0a:	3f 93       	cmp	#-1,	r15	;r3 As==11
    7a0c:	04 20       	jnz	$+10     	;abs 0x7a16
    7a0e:	bb 40 67 00 	mov	#103,	0(r11)	;#0x0067, 0x0000(r11)
    7a12:	00 00 
    7a14:	2f 3c       	jmp	$+96     	;abs 0x7a74
    7a16:	1e 42 2e 2c 	mov	&0x2c2e,r14	
    7a1a:	3f 90 0a 00 	cmp	#10,	r15	;#0x000a
    7a1e:	0c 24       	jz	$+26     	;abs 0x7a38
    7a20:	3f 90 0d 00 	cmp	#13,	r15	;#0x000d
    7a24:	09 24       	jz	$+20     	;abs 0x7a38
    7a26:	3e 90 7f 00 	cmp	#127,	r14	;#0x007f
    7a2a:	eb 37       	jge	$-40     	;abs 0x7a02
    7a2c:	ce 4f 30 2c 	mov.b	r15,	11312(r14);0x2c30(r14)
    7a30:	1e 53       	inc	r14		
    7a32:	82 4e 2e 2c 	mov	r14,	&0x2c2e	
    7a36:	e5 3f       	jmp	$-52     	;abs 0x7a02
    7a38:	ce 43 30 2c 	mov.b	#0,	11312(r14);r3 As==00, 0x2c30(r14)
    7a3c:	1e 53       	inc	r14		
    7a3e:	82 4e 2e 2c 	mov	r14,	&0x2c2e	
    7a42:	3d 40 30 2c 	mov	#11312,	r13	;#0x2c30
    7a46:	5e 42 55 2e 	mov.b	&0x2e55,r14	
    7a4a:	0f 43       	clr	r15		
    7a4c:	b0 12 7a 76 	call	#0x767a	
    7a50:	0d 43       	clr	r13		
    7a52:	7e 40 85 ff 	mov.b	#-123,	r14	;#0xff85
    7a56:	1f 42 e6 25 	mov	&0x25e6,r15	
    7a5a:	b0 12 7a 76 	call	#0x767a	
    7a5e:	0f 93       	tst	r15		
    7a60:	ce 23       	jnz	$-98     	;abs 0x79fe
    7a62:	bb 40 79 00 	mov	#121,	0(r11)	;#0x0079, 0x0000(r11)
    7a66:	00 00 
    7a68:	05 3c       	jmp	$+12     	;abs 0x7a74
    7a6a:	8b 43 00 00 	mov	#0,	0(r11)	;r3 As==00, 0x0000(r11)
    7a6e:	7f 40 03 00 	mov.b	#3,	r15	;#0x0003
    7a72:	06 3c       	jmp	$+14     	;abs 0x7a80
    7a74:	5f 43       	mov.b	#1,	r15	;r3 As==01
    7a76:	04 3c       	jmp	$+10     	;abs 0x7a80
    7a78:	7e 90 85 ff 	cmp.b	#-123,	r14	;#0xff85
    7a7c:	fb 23       	jnz	$-8      	;abs 0x7a74
    7a7e:	bf 3f       	jmp	$-128    	;abs 0x79fe
    7a80:	3b 41       	pop	r11		
    7a82:	30 41       	ret			

00007a84 <serial_line_input_byte>:
    7a84:	4e 4f       	mov.b	r15,	r14	
    7a86:	c2 93 26 2c 	tst.b	&0x2c26	
    7a8a:	09 20       	jnz	$+20     	;abs 0x7a9e
    7a8c:	3f 40 28 2c 	mov	#11304,	r15	;#0x2c28
    7a90:	b0 12 0e 78 	call	#0x780e	
    7a94:	0f 93       	tst	r15		
    7a96:	11 20       	jnz	$+36     	;abs 0x7aba
    7a98:	d2 43 26 2c 	mov.b	#1,	&0x2c26	;r3 As==01
    7a9c:	0e 3c       	jmp	$+30     	;abs 0x7aba
    7a9e:	7f 90 0a 00 	cmp.b	#10,	r15	;#0x000a
    7aa2:	03 24       	jz	$+8      	;abs 0x7aaa
    7aa4:	7f 90 0d 00 	cmp.b	#13,	r15	;#0x000d
    7aa8:	08 20       	jnz	$+18     	;abs 0x7aba
    7aaa:	3f 40 28 2c 	mov	#11304,	r15	;#0x2c28
    7aae:	b0 12 0e 78 	call	#0x780e	
    7ab2:	0f 93       	tst	r15		
    7ab4:	02 24       	jz	$+6      	;abs 0x7aba
    7ab6:	c2 43 26 2c 	mov.b	#0,	&0x2c26	;r3 As==00
    7aba:	3f 40 32 22 	mov	#8754,	r15	;#0x2232
    7abe:	b0 12 04 77 	call	#0x7704	
    7ac2:	1f 43       	mov	#1,	r15	;r3 As==01
    7ac4:	30 41       	ret			

00007ac6 <serial_line_init>:
    7ac6:	7d 40 80 ff 	mov.b	#-128,	r13	;#0xff80
    7aca:	3e 40 b0 2c 	mov	#11440,	r14	;#0x2cb0
    7ace:	3f 40 28 2c 	mov	#11304,	r15	;#0x2c28
    7ad2:	b0 12 fa 77 	call	#0x77fa	
    7ad6:	0e 43       	clr	r14		
    7ad8:	3f 40 32 22 	mov	#8754,	r15	;#0x2232
    7adc:	b0 12 ce 76 	call	#0x76ce	
    7ae0:	30 41       	ret			

00007ae2 <spi_init>:
    7ae2:	f2 40 17 00 	mov.b	#23,	&0x0070	;#0x0017
    7ae6:	70 00 
    7ae8:	f2 40 a2 ff 	mov.b	#-94,	&0x0071	;#0xffa2
    7aec:	71 00 
    7aee:	e2 43 74 00 	mov.b	#2,	&0x0074	;r3 As==10
    7af2:	c2 43 75 00 	mov.b	#0,	&0x0075	;r3 As==00
    7af6:	c2 43 73 00 	mov.b	#0,	&0x0073	;r3 As==00
    7afa:	f2 d0 0e 00 	bis.b	#14,	&0x001b	;#0x000e
    7afe:	1b 00 
    7b00:	f2 d0 0a 00 	bis.b	#10,	&0x001a	;#0x000a
    7b04:	1a 00 
    7b06:	f2 d0 40 00 	bis.b	#64,	&0x0004	;#0x0040
    7b0a:	04 00 
    7b0c:	d2 c3 70 00 	bic.b	#1,	&0x0070	;r3 As==01
    7b10:	30 41       	ret			

00007b12 <stack_check_init>:
    7b12:	21 83       	decd	r1		
    7b14:	82 41 30 2d 	mov	r1,	&0x2d30	
    7b18:	b1 40 58 2e 	mov	#11864,	0(r1)	;#0x2e58, 0x0000(r1)
    7b1c:	00 00 
    7b1e:	06 3c       	jmp	$+14     	;abs 0x7b2c
    7b20:	ff 40 cd ff 	mov.b	#-51,	0(r15)	;#0xffcd, 0x0000(r15)
    7b24:	00 00 
    7b26:	1f 53       	inc	r15		
    7b28:	81 4f 00 00 	mov	r15,	0(r1)	;0x0000(r1)
    7b2c:	2f 41       	mov	@r1,	r15	
    7b2e:	0f 91       	cmp	r1,	r15	
    7b30:	f7 2b       	jnc	$-16     	;abs 0x7b20
    7b32:	0e 43       	clr	r14		
    7b34:	3f 40 3c 22 	mov	#8764,	r15	;#0x223c
    7b38:	b0 12 ce 76 	call	#0x76ce	
    7b3c:	21 53       	incd	r1		
    7b3e:	30 41       	ret			

00007b40 <stack_check_get_usage>:
    7b40:	0b 12       	push	r11		
    7b42:	b0 12 88 7e 	call	#0x7e88	
    7b46:	3b 40 58 2e 	mov	#11864,	r11	;#0x2e58
    7b4a:	01 3c       	jmp	$+4      	;abs 0x7b4e
    7b4c:	1b 53       	inc	r11		
    7b4e:	fb 90 cd ff 	cmp.b	#-51,	0(r11)	;#0xffcd, 0x0000(r11)
    7b52:	00 00 
    7b54:	05 24       	jz	$+12     	;abs 0x7b60
    7b56:	3b 90 00 39 	cmp	#14592,	r11	;#0x3900
    7b5a:	f8 2b       	jnc	$-14     	;abs 0x7b4c
    7b5c:	01 3c       	jmp	$+4      	;abs 0x7b60
    7b5e:	1b 53       	inc	r11		
    7b60:	fb 90 cd ff 	cmp.b	#-51,	0(r11)	;#0xffcd, 0x0000(r11)
    7b64:	00 00 
    7b66:	03 20       	jnz	$+8      	;abs 0x7b6e
    7b68:	3b 90 00 39 	cmp	#14592,	r11	;#0x3900
    7b6c:	f8 2b       	jnc	$-14     	;abs 0x7b5e
    7b6e:	b0 12 88 7e 	call	#0x7e88	
    7b72:	3b 90 00 39 	cmp	#14592,	r11	;#0x3900
    7b76:	0a 2c       	jc	$+22     	;abs 0x7b8c
    7b78:	3d 40 00 39 	mov	#14592,	r13	;#0x3900
    7b7c:	0d 8b       	sub	r11,	r13	
    7b7e:	0e 4d       	mov	r13,	r14	
    7b80:	8d 10       	swpb	r13		
    7b82:	8d 11       	sxt	r13		
    7b84:	8d 10       	swpb	r13		
    7b86:	8d 11       	sxt	r13		
    7b88:	0f 4d       	mov	r13,	r15	
    7b8a:	02 3c       	jmp	$+6      	;abs 0x7b90
    7b8c:	3e 43       	mov	#-1,	r14	;r3 As==11
    7b8e:	3f 43       	mov	#-1,	r15	;r3 As==11
    7b90:	3b 41       	pop	r11		
    7b92:	30 41       	ret			

00007b94 <process_thread_stack_check_process>:
    7b94:	0b 12       	push	r11		
    7b96:	0a 12       	push	r10		
    7b98:	09 12       	push	r9		
    7b9a:	08 12       	push	r8		
    7b9c:	07 12       	push	r7		
    7b9e:	07 4f       	mov	r15,	r7	
    7ba0:	2f 4f       	mov	@r15,	r15	
    7ba2:	0f 93       	tst	r15		
    7ba4:	04 24       	jz	$+10     	;abs 0x7bae
    7ba6:	3f 90 92 00 	cmp	#146,	r15	;#0x0092
    7baa:	55 20       	jnz	$+172    	;abs 0x7c56
    7bac:	5b 3c       	jmp	$+184    	;abs 0x7c64
    7bae:	3d 40 00 05 	mov	#1280,	r13	;#0x0500
    7bb2:	0e 43       	clr	r14		
    7bb4:	3f 40 32 2d 	mov	#11570,	r15	;#0x2d32
    7bb8:	b0 12 36 59 	call	#0x5936	
    7bbc:	b7 40 92 00 	mov	#146,	0(r7)	;#0x0092, 0x0000(r7)
    7bc0:	00 00 
    7bc2:	4e 3c       	jmp	$+158    	;abs 0x7c60
    7bc4:	b0 12 40 7b 	call	#0x7b40	
    7bc8:	08 4e       	mov	r14,	r8	
    7bca:	09 4f       	mov	r15,	r9	
    7bcc:	3e 40 00 39 	mov	#14592,	r14	;#0x3900
    7bd0:	3e 80 58 2e 	sub	#11864,	r14	;#0x2e58
    7bd4:	0a 4e       	mov	r14,	r10	
    7bd6:	8e 10       	swpb	r14		
    7bd8:	8e 11       	sxt	r14		
    7bda:	8e 10       	swpb	r14		
    7bdc:	8e 11       	sxt	r14		
    7bde:	0b 4e       	mov	r14,	r11	
    7be0:	09 93       	tst	r9		
    7be2:	05 38       	jl	$+12     	;abs 0x7bee
    7be4:	0e 93       	tst	r14		
    7be6:	03 38       	jl	$+8      	;abs 0x7bee
    7be8:	0e 99       	cmp	r9,	r14	
    7bea:	19 38       	jl	$+52     	;abs 0x7c1e
    7bec:	14 3c       	jmp	$+42     	;abs 0x7c16
    7bee:	92 93 8c 11 	cmp	#1,	&0x118c	;r3 As==01
    7bf2:	2c 38       	jl	$+90     	;abs 0x7c4c
    7bf4:	30 12 62 b0 	push	#-20382	;#0xb062
    7bf8:	30 12 68 b0 	push	#-20376	;#0xb068
    7bfc:	30 12 6c b0 	push	#-20372	;#0xb06c
    7c00:	b0 12 cc 9e 	call	#0x9ecc	
    7c04:	31 50 06 00 	add	#6,	r1	;#0x0006
    7c08:	0b 12       	push	r11		
    7c0a:	0a 12       	push	r10		
    7c0c:	09 12       	push	r9		
    7c0e:	08 12       	push	r8		
    7c10:	30 12 7b b0 	push	#-20357	;#0xb07b
    7c14:	17 3c       	jmp	$+48     	;abs 0x7c44
    7c16:	09 9e       	cmp	r14,	r9	
    7c18:	19 38       	jl	$+52     	;abs 0x7c4c
    7c1a:	0a 98       	cmp	r8,	r10	
    7c1c:	17 2c       	jc	$+48     	;abs 0x7c4c
    7c1e:	92 93 8c 11 	cmp	#1,	&0x118c	;r3 As==01
    7c22:	14 38       	jl	$+42     	;abs 0x7c4c
    7c24:	30 12 62 b0 	push	#-20382	;#0xb062
    7c28:	30 12 68 b0 	push	#-20376	;#0xb068
    7c2c:	30 12 6c b0 	push	#-20372	;#0xb06c
    7c30:	b0 12 cc 9e 	call	#0x9ecc	
    7c34:	31 50 06 00 	add	#6,	r1	;#0x0006
    7c38:	0b 12       	push	r11		
    7c3a:	0a 12       	push	r10		
    7c3c:	09 12       	push	r9		
    7c3e:	08 12       	push	r8		
    7c40:	30 12 a5 b0 	push	#-20315	;#0xb0a5
    7c44:	b0 12 cc 9e 	call	#0x9ecc	
    7c48:	31 50 0a 00 	add	#10,	r1	;#0x000a
    7c4c:	3f 40 32 2d 	mov	#11570,	r15	;#0x2d32
    7c50:	b0 12 48 59 	call	#0x5948	
    7c54:	b3 3f       	jmp	$-152    	;abs 0x7bbc
    7c56:	87 43 00 00 	mov	#0,	0(r7)	;r3 As==00, 0x0000(r7)
    7c5a:	7f 40 03 00 	mov.b	#3,	r15	;#0x0003
    7c5e:	09 3c       	jmp	$+20     	;abs 0x7c72
    7c60:	5f 43       	mov.b	#1,	r15	;r3 As==01
    7c62:	07 3c       	jmp	$+16     	;abs 0x7c72
    7c64:	3f 40 32 2d 	mov	#11570,	r15	;#0x2d32
    7c68:	b0 12 5a 59 	call	#0x595a	
    7c6c:	0f 93       	tst	r15		
    7c6e:	f8 27       	jz	$-14     	;abs 0x7c60
    7c70:	a9 3f       	jmp	$-172    	;abs 0x7bc4
    7c72:	37 41       	pop	r7		
    7c74:	38 41       	pop	r8		
    7c76:	39 41       	pop	r9		
    7c78:	3a 41       	pop	r10		
    7c7a:	3b 41       	pop	r11		
    7c7c:	30 41       	ret			

00007c7e <timer_set>:
    7c7e:	0b 12       	push	r11		
    7c80:	0b 4f       	mov	r15,	r11	
    7c82:	8f 4d 04 00 	mov	r13,	4(r15)	;0x0004(r15)
    7c86:	8f 4e 06 00 	mov	r14,	6(r15)	;0x0006(r15)
    7c8a:	b0 12 48 4f 	call	#0x4f48	
    7c8e:	8b 4e 00 00 	mov	r14,	0(r11)	;0x0000(r11)
    7c92:	8b 4f 02 00 	mov	r15,	2(r11)	;0x0002(r11)
    7c96:	3b 41       	pop	r11		
    7c98:	30 41       	ret			

00007c9a <timer_expired>:
    7c9a:	0b 12       	push	r11		
    7c9c:	0b 4f       	mov	r15,	r11	
    7c9e:	b0 12 48 4f 	call	#0x4f48	
    7ca2:	2e 8b       	sub	@r11,	r14	
    7ca4:	1f 7b 02 00 	subc	2(r11),	r15	;0x0002(r11)
    7ca8:	1e 53       	inc	r14		
    7caa:	0f 63       	adc	r15		
    7cac:	1d 43       	mov	#1,	r13	;r3 As==01
    7cae:	8b 9f 06 00 	cmp	r15,	6(r11)	;0x0006(r11)
    7cb2:	05 28       	jnc	$+12     	;abs 0x7cbe
    7cb4:	03 20       	jnz	$+8      	;abs 0x7cbc
    7cb6:	8b 9e 04 00 	cmp	r14,	4(r11)	;0x0004(r11)
    7cba:	01 28       	jnc	$+4      	;abs 0x7cbe
    7cbc:	0d 43       	clr	r13		
    7cbe:	0f 4d       	mov	r13,	r15	
    7cc0:	3b 41       	pop	r11		
    7cc2:	30 41       	ret			

00007cc4 <timer_reset>:
    7cc4:	0b 12       	push	r11		
    7cc6:	0b 4f       	mov	r15,	r11	
    7cc8:	b0 12 9a 7c 	call	#0x7c9a	
    7ccc:	0f 93       	tst	r15		
    7cce:	06 24       	jz	$+14     	;abs 0x7cdc
    7cd0:	9b 5b 04 00 	add	4(r11),	0(r11)	;0x0004(r11), 0x0000(r11)
    7cd4:	00 00 
    7cd6:	9b 6b 06 00 	addc	6(r11),	2(r11)	;0x0006(r11), 0x0002(r11)
    7cda:	02 00 
    7cdc:	3b 41       	pop	r11		
    7cde:	30 41       	ret			

00007ce0 <putchar>:
    7ce0:	0b 12       	push	r11		
    7ce2:	0b 4f       	mov	r15,	r11	
    7ce4:	4f 4f       	mov.b	r15,	r15	
    7ce6:	b0 12 62 7d 	call	#0x7d62	
    7cea:	0f 4b       	mov	r11,	r15	
    7cec:	3b 41       	pop	r11		
    7cee:	30 41       	ret			

00007cf0 <handle_rxdma_timer>:
    7cf0:	0b 12       	push	r11		
    7cf2:	1b 42 e6 01 	mov	&0x01e6,r11	
    7cf6:	0f 3c       	jmp	$+32     	;abs 0x7d16
    7cf8:	3f 40 d6 2d 	mov	#11734,	r15	;#0x2dd6
    7cfc:	0f 8e       	sub	r14,	r15	
    7cfe:	6f 4f       	mov.b	@r15,	r15	
    7d00:	92 12 54 2d 	call	&0x2d54	
    7d04:	1f 42 d6 2d 	mov	&0x2dd6,r15	
    7d08:	3f 53       	add	#-1,	r15	;r3 As==11
    7d0a:	82 4f d6 2d 	mov	r15,	&0x2dd6	
    7d0e:	03 20       	jnz	$+8      	;abs 0x7d16
    7d10:	b2 40 80 00 	mov	#128,	&0x2dd6	;#0x0080
    7d14:	d6 2d 
    7d16:	1e 42 d6 2d 	mov	&0x2dd6,r14	
    7d1a:	0e 9b       	cmp	r11,	r14	
    7d1c:	ed 23       	jnz	$-36     	;abs 0x7cf8
    7d1e:	3f 40 40 2d 	mov	#11584,	r15	;#0x2d40
    7d22:	b0 12 dc 55 	call	#0x55dc	
    7d26:	3b 41       	pop	r11		
    7d28:	30 41       	ret			

00007d2a <uart1_active>:
    7d2a:	5f 42 79 00 	mov.b	&0x0079,r15	
    7d2e:	5d 42 3f 2d 	mov.b	&0x2d3f,r13	
    7d32:	5e 42 3e 2d 	mov.b	&0x2d3e,r14	
    7d36:	4e dd       	bis.b	r13,	r14	
    7d38:	5d 43       	mov.b	#1,	r13	;r3 As==01
    7d3a:	4d cf       	bic.b	r15,	r13	
    7d3c:	4f 4d       	mov.b	r13,	r15	
    7d3e:	4f de       	bis.b	r14,	r15	
    7d40:	30 41       	ret			

00007d42 <uart1_set_input>:
    7d42:	0b 12       	push	r11		
    7d44:	0b 4f       	mov	r15,	r11	
    7d46:	03 12       	push	#0		;r3 As==00
    7d48:	3c 40 f0 7c 	mov	#31984,	r12	;#0x7cf0
    7d4c:	2d 43       	mov	#2,	r13	;r3 As==10
    7d4e:	0e 43       	clr	r14		
    7d50:	3f 40 40 2d 	mov	#11584,	r15	;#0x2d40
    7d54:	b0 12 cc 55 	call	#0x55cc	
    7d58:	21 53       	incd	r1		
    7d5a:	82 4b 54 2d 	mov	r11,	&0x2d54	
    7d5e:	3b 41       	pop	r11		
    7d60:	30 41       	ret			

00007d62 <uart1_writeb>:
    7d62:	0b 12       	push	r11		
    7d64:	4b 4f       	mov.b	r15,	r11	
    7d66:	b0 12 88 7e 	call	#0x7e88	
    7d6a:	f2 b0 20 00 	bit.b	#32,	&0x0003	;#0x0020
    7d6e:	03 00 
    7d70:	fc 27       	jz	$-6      	;abs 0x7d6a
    7d72:	c2 4b 7f 00 	mov.b	r11,	&0x007f	
    7d76:	3b 41       	pop	r11		
    7d78:	30 41       	ret			

00007d7a <uart1_init>:
    7d7a:	f2 f0 7f 00 	and.b	#127,	&0x001a	;#0x007f
    7d7e:	1a 00 
    7d80:	f2 d0 40 00 	bis.b	#64,	&0x001a	;#0x0040
    7d84:	1a 00 
    7d86:	f2 d0 c0 ff 	bis.b	#-64,	&0x001b	;#0xffc0
    7d8a:	1b 00 
    7d8c:	f2 40 11 00 	mov.b	#17,	&0x0078	;#0x0011
    7d90:	78 00 
    7d92:	f2 40 20 00 	mov.b	#32,	&0x0079	;#0x0020
    7d96:	79 00 
    7d98:	c2 4e 7c 00 	mov.b	r14,	&0x007c	
    7d9c:	0c 4f       	mov	r15,	r12	
    7d9e:	0d 4e       	mov	r14,	r13	
    7da0:	8d 10       	swpb	r13		
    7da2:	8c 10       	swpb	r12		
    7da4:	4d ec       	xor.b	r12,	r13	
    7da6:	0d ec       	xor	r12,	r13	
    7da8:	c2 4d 7d 00 	mov.b	r13,	&0x007d	
    7dac:	3e 90 65 00 	cmp	#101,	r14	;#0x0065
    7db0:	02 20       	jnz	$+6      	;abs 0x7db6
    7db2:	0f 93       	tst	r15		
    7db4:	25 24       	jz	$+76     	;abs 0x7e00
    7db6:	1f 93       	cmp	#1,	r15	;r3 As==01
    7db8:	0f 2c       	jc	$+32     	;abs 0x7dd8
    7dba:	3e 90 66 00 	cmp	#102,	r14	;#0x0066
    7dbe:	0c 2c       	jc	$+26     	;abs 0x7dd8
    7dc0:	3e 90 21 00 	cmp	#33,	r14	;#0x0021
    7dc4:	03 20       	jnz	$+8      	;abs 0x7dcc
    7dc6:	0f 93       	tst	r15		
    7dc8:	13 24       	jz	$+40     	;abs 0x7df0
    7dca:	24 3c       	jmp	$+74     	;abs 0x7e14
    7dcc:	3e 90 43 00 	cmp	#67,	r14	;#0x0043
    7dd0:	21 20       	jnz	$+68     	;abs 0x7e14
    7dd2:	0f 93       	tst	r15		
    7dd4:	11 24       	jz	$+36     	;abs 0x7df8
    7dd6:	1e 3c       	jmp	$+62     	;abs 0x7e14
    7dd8:	3e 90 cb 00 	cmp	#203,	r14	;#0x00cb
    7ddc:	03 20       	jnz	$+8      	;abs 0x7de4
    7dde:	0f 93       	tst	r15		
    7de0:	13 24       	jz	$+40     	;abs 0x7e08
    7de2:	18 3c       	jmp	$+50     	;abs 0x7e14
    7de4:	3e 90 96 01 	cmp	#406,	r14	;#0x0196
    7de8:	15 20       	jnz	$+44     	;abs 0x7e14
    7dea:	0f 93       	tst	r15		
    7dec:	10 24       	jz	$+34     	;abs 0x7e0e
    7dee:	12 3c       	jmp	$+38     	;abs 0x7e14
    7df0:	f2 40 f7 ff 	mov.b	#-9,	&0x007b	;#0xfff7
    7df4:	7b 00 
    7df6:	0e 3c       	jmp	$+30     	;abs 0x7e14
    7df8:	f2 40 ed ff 	mov.b	#-19,	&0x007b	;#0xffed
    7dfc:	7b 00 
    7dfe:	0a 3c       	jmp	$+22     	;abs 0x7e14
    7e00:	f2 40 d6 ff 	mov.b	#-42,	&0x007b	;#0xffd6
    7e04:	7b 00 
    7e06:	06 3c       	jmp	$+14     	;abs 0x7e14
    7e08:	f2 42 7b 00 	mov.b	#8,	&0x007b	;r2 As==11
    7e0c:	03 3c       	jmp	$+8      	;abs 0x7e14
    7e0e:	f2 40 22 00 	mov.b	#34,	&0x007b	;#0x0022
    7e12:	7b 00 
    7e14:	f2 f0 ef ff 	and.b	#-17,	&0x0005	;#0xffef
    7e18:	05 00 
    7e1a:	f2 d0 30 00 	bis.b	#48,	&0x0005	;#0x0030
    7e1e:	05 00 
    7e20:	d2 c3 78 00 	bic.b	#1,	&0x0078	;r3 As==01
    7e24:	f2 f0 ef ff 	and.b	#-17,	&0x0003	;#0xffef
    7e28:	03 00 
    7e2a:	f2 d2 79 00 	bis.b	#8,	&0x0079	;r2 As==11
    7e2e:	c2 43 3f 2d 	mov.b	#0,	&0x2d3f	;r3 As==00
    7e32:	c2 43 3e 2d 	mov.b	#0,	&0x2d3e	;r3 As==00
    7e36:	f2 d0 10 00 	bis.b	#16,	&0x0001	;#0x0010
    7e3a:	01 00 
    7e3c:	f2 f0 ef ff 	and.b	#-17,	&0x0001	;#0xffef
    7e40:	01 00 
    7e42:	b2 40 09 00 	mov	#9,	&0x0122	;#0x0009
    7e46:	22 01 
    7e48:	b2 40 7e 00 	mov	#126,	&0x01e2	;#0x007e
    7e4c:	e2 01 
    7e4e:	b2 40 56 2d 	mov	#11606,	&0x01e4	;#0x2d56
    7e52:	e4 01 
    7e54:	b2 40 80 00 	mov	#128,	&0x01e6	;#0x0080
    7e58:	e6 01 
    7e5a:	b2 40 80 00 	mov	#128,	&0x2dd6	;#0x0080
    7e5e:	d6 2d 
    7e60:	b2 40 d1 4c 	mov	#19665,	&0x01e0	;#0x4cd1
    7e64:	e0 01 
    7e66:	1f 43       	mov	#1,	r15	;r3 As==01
    7e68:	b0 12 a4 65 	call	#0x65a4	
    7e6c:	30 41       	ret			

00007e6e <watchdog_interrupt>:
    7e6e:	82 43 20 01 	mov	#0,	&0x0120	;r3 As==00
    7e72:	00 13       	reti			

00007e74 <watchdog_start>:
    7e74:	1f 42 d8 2d 	mov	&0x2dd8,r15	
    7e78:	3f 53       	add	#-1,	r15	;r3 As==11
    7e7a:	82 4f d8 2d 	mov	r15,	&0x2dd8	
    7e7e:	03 20       	jnz	$+8      	;abs 0x7e86
    7e80:	b2 40 1c 5a 	mov	#23068,	&0x0120	;#0x5a1c
    7e84:	20 01 
    7e86:	30 41       	ret			

00007e88 <watchdog_periodic>:
    7e88:	1f 42 20 01 	mov	&0x0120,r15	
    7e8c:	3f f0 ff 00 	and	#255,	r15	;#0x00ff
    7e90:	3f d0 18 5a 	bis	#23064,	r15	;#0x5a18
    7e94:	82 4f 20 01 	mov	r15,	&0x0120	
    7e98:	30 41       	ret			

00007e9a <watchdog_stop>:
    7e9a:	1f 42 d8 2d 	mov	&0x2dd8,r15	
    7e9e:	1f 53       	inc	r15		
    7ea0:	82 4f d8 2d 	mov	r15,	&0x2dd8	
    7ea4:	1f 93       	cmp	#1,	r15	;r3 As==01
    7ea6:	03 20       	jnz	$+8      	;abs 0x7eae
    7ea8:	b2 40 80 5a 	mov	#23168,	&0x0120	;#0x5a80
    7eac:	20 01 
    7eae:	30 41       	ret			

00007eb0 <watchdog_init>:
    7eb0:	82 43 d8 2d 	mov	#0,	&0x2dd8	;r3 As==00
    7eb4:	b0 12 9a 7e 	call	#0x7e9a	
    7eb8:	d2 c3 02 00 	bic.b	#1,	&0x0002	;r3 As==01
    7ebc:	d2 d3 00 00 	bis.b	#1,	&0x0000	;r3 As==01
    7ec0:	30 41       	ret			

00007ec2 <xmem_init>:
    7ec2:	b0 12 e2 7a 	call	#0x7ae2	
    7ec6:	f2 d0 98 ff 	bis.b	#-104,	&0x001e	;#0xff98
    7eca:	1e 00 
    7ecc:	f2 d2 1d 00 	bis.b	#8,	&0x001d	;r2 As==11
    7ed0:	b0 12 da 65 	call	#0x65da	
    7ed4:	f2 f0 ef ff 	and.b	#-17,	&0x001d	;#0xffef
    7ed8:	1d 00 
    7eda:	5e 42 02 00 	mov.b	&0x0002,r14	
    7ede:	4e 93       	tst.b	r14		
    7ee0:	fc 37       	jge	$-6      	;abs 0x7eda
    7ee2:	f2 40 ab ff 	mov.b	#-85,	&0x0077	;#0xffab
    7ee6:	77 00 
    7ee8:	d2 b3 71 00 	bit.b	#1,	&0x0071	;r3 As==01
    7eec:	fd 27       	jz	$-4      	;abs 0x7ee8
    7eee:	f2 d0 10 00 	bis.b	#16,	&0x001d	;#0x0010
    7ef2:	1d 00 
    7ef4:	02 df       	bis	r15,	r2	
    7ef6:	f2 d0 80 ff 	bis.b	#-128,	&0x001d	;#0xff80
    7efa:	1d 00 
    7efc:	30 41       	ret			

00007efe <__ieee754_powf>:
    7efe:	0b 12       	push	r11		
    7f00:	0a 12       	push	r10		
    7f02:	09 12       	push	r9		
    7f04:	08 12       	push	r8		
    7f06:	07 12       	push	r7		
    7f08:	06 12       	push	r6		
    7f0a:	05 12       	push	r5		
    7f0c:	04 12       	push	r4		
    7f0e:	31 50 dc ff 	add	#-36,	r1	;#0xffdc
    7f12:	04 4c       	mov	r12,	r4	
    7f14:	05 4d       	mov	r13,	r5	
    7f16:	81 4c 14 00 	mov	r12,	20(r1)	;0x0014(r1)
    7f1a:	81 4d 16 00 	mov	r13,	22(r1)	;0x0016(r1)
    7f1e:	0a 4c       	mov	r12,	r10	
    7f20:	0b 4d       	mov	r13,	r11	
    7f22:	3a f3       	and	#-1,	r10	;r3 As==11
    7f24:	3b f0 ff 7f 	and	#32767,	r11	;#0x7fff
    7f28:	81 4a 00 00 	mov	r10,	0(r1)	;0x0000(r1)
    7f2c:	81 4b 02 00 	mov	r11,	2(r1)	;0x0002(r1)
    7f30:	0a 93       	tst	r10		
    7f32:	04 20       	jnz	$+10     	;abs 0x7f3c
    7f34:	0b 93       	tst	r11		
    7f36:	02 20       	jnz	$+6      	;abs 0x7f3c
    7f38:	30 40 1a 8b 	br	#0x8b1a	
    7f3c:	81 4e 08 00 	mov	r14,	8(r1)	;0x0008(r1)
    7f40:	81 4f 0a 00 	mov	r15,	10(r1)	;0x000a(r1)
    7f44:	06 4e       	mov	r14,	r6	
    7f46:	07 4f       	mov	r15,	r7	
    7f48:	36 f3       	and	#-1,	r6	;r3 As==11
    7f4a:	37 f0 ff 7f 	and	#32767,	r7	;#0x7fff
    7f4e:	37 90 80 7f 	cmp	#32640,	r7	;#0x7f80
    7f52:	05 38       	jl	$+12     	;abs 0x7f5e
    7f54:	37 90 81 7f 	cmp	#32641,	r7	;#0x7f81
    7f58:	0a 34       	jge	$+22     	;abs 0x7f6e
    7f5a:	16 93       	cmp	#1,	r6	;r3 As==01
    7f5c:	08 2c       	jc	$+18     	;abs 0x7f6e
    7f5e:	b1 90 80 7f 	cmp	#32640,	2(r1)	;#0x7f80, 0x0002(r1)
    7f62:	02 00 
    7f64:	0c 38       	jl	$+26     	;abs 0x7f7e
    7f66:	03 20       	jnz	$+8      	;abs 0x7f6e
    7f68:	91 93 00 00 	cmp	#1,	0(r1)	;r3 As==01, 0x0000(r1)
    7f6c:	08 28       	jnc	$+18     	;abs 0x7f7e
    7f6e:	0c 4e       	mov	r14,	r12	
    7f70:	0d 4f       	mov	r15,	r13	
    7f72:	0e 44       	mov	r4,	r14	
    7f74:	0f 45       	mov	r5,	r15	
    7f76:	b0 12 5a 93 	call	#0x935a	
    7f7a:	30 40 14 8b 	br	#0x8b14	
    7f7e:	91 41 0a 00 	mov	10(r1),	16(r1)	;0x000a(r1), 0x0010(r1)
    7f82:	10 00 
    7f84:	91 41 14 00 	mov	20(r1),	12(r1)	;0x0014(r1), 0x000c(r1)
    7f88:	0c 00 
    7f8a:	19 41 16 00 	mov	22(r1),	r9	;0x0016(r1)
    7f8e:	81 93 10 00 	tst	16(r1)		;0x0010(r1)
    7f92:	05 38       	jl	$+12     	;abs 0x7f9e
    7f94:	81 43 04 00 	mov	#0,	4(r1)	;r3 As==00, 0x0004(r1)
    7f98:	81 43 06 00 	mov	#0,	6(r1)	;r3 As==00, 0x0006(r1)
    7f9c:	49 3c       	jmp	$+148    	;abs 0x8030
    7f9e:	b1 90 80 4b 	cmp	#19328,	2(r1)	;#0x4b80, 0x0002(r1)
    7fa2:	02 00 
    7fa4:	05 38       	jl	$+12     	;abs 0x7fb0
    7fa6:	a1 43 04 00 	mov	#2,	4(r1)	;r3 As==10, 0x0004(r1)
    7faa:	81 43 06 00 	mov	#0,	6(r1)	;r3 As==00, 0x0006(r1)
    7fae:	40 3c       	jmp	$+130    	;abs 0x8030
    7fb0:	b1 90 80 3f 	cmp	#16256,	2(r1)	;#0x3f80, 0x0002(r1)
    7fb4:	02 00 
    7fb6:	02 34       	jge	$+6      	;abs 0x7fbc
    7fb8:	30 40 22 8b 	br	#0x8b22	
    7fbc:	1c 41 02 00 	mov	2(r1),	r12	;0x0002(r1)
    7fc0:	0d 4c       	mov	r12,	r13	
    7fc2:	8d 10       	swpb	r13		
    7fc4:	8d 11       	sxt	r13		
    7fc6:	8d 10       	swpb	r13		
    7fc8:	8d 11       	sxt	r13		
    7fca:	7b 40 07 00 	mov.b	#7,	r11	;#0x0007
    7fce:	0d 11       	rra	r13		
    7fd0:	0c 10       	rrc	r12		
    7fd2:	7b 53       	add.b	#-1,	r11	;r3 As==11
    7fd4:	fc 23       	jnz	$-6      	;abs 0x7fce
    7fd6:	38 40 96 00 	mov	#150,	r8	;#0x0096
    7fda:	08 8c       	sub	r12,	r8	
    7fdc:	4b 48       	mov.b	r8,	r11	
    7fde:	7b f0 1f 00 	and.b	#31,	r11	;#0x001f
    7fe2:	2c 41       	mov	@r1,	r12	
    7fe4:	1d 41 02 00 	mov	2(r1),	r13	;0x0002(r1)
    7fe8:	4b 93       	tst.b	r11		
    7fea:	04 24       	jz	$+10     	;abs 0x7ff4
    7fec:	0d 11       	rra	r13		
    7fee:	0c 10       	rrc	r12		
    7ff0:	7b 53       	add.b	#-1,	r11	;r3 As==11
    7ff2:	fa 3f       	jmp	$-10     	;abs 0x7fe8
    7ff4:	78 f0 1f 00 	and.b	#31,	r8	;#0x001f
    7ff8:	0a 4c       	mov	r12,	r10	
    7ffa:	0b 4d       	mov	r13,	r11	
    7ffc:	48 93       	tst.b	r8		
    7ffe:	04 24       	jz	$+10     	;abs 0x8008
    8000:	0a 5a       	rla	r10		
    8002:	0b 6b       	rlc	r11		
    8004:	78 53       	add.b	#-1,	r8	;r3 As==11
    8006:	fa 3f       	jmp	$-10     	;abs 0x7ffc
    8008:	2a 91       	cmp	@r1,	r10	
    800a:	02 24       	jz	$+6      	;abs 0x8010
    800c:	30 40 22 8b 	br	#0x8b22	
    8010:	1b 91 02 00 	cmp	2(r1),	r11	;0x0002(r1)
    8014:	02 24       	jz	$+6      	;abs 0x801a
    8016:	30 40 22 8b 	br	#0x8b22	
    801a:	1c f3       	and	#1,	r12	;r3 As==01
    801c:	0d f3       	and	#0,	r13	;r3 As==00
    801e:	a1 43 04 00 	mov	#2,	4(r1)	;r3 As==10, 0x0004(r1)
    8022:	81 43 06 00 	mov	#0,	6(r1)	;r3 As==00, 0x0006(r1)
    8026:	81 8c 04 00 	sub	r12,	4(r1)	;0x0004(r1)
    802a:	81 7d 06 00 	subc	r13,	6(r1)	;0x0006(r1)
    802e:	25 3c       	jmp	$+76     	;abs 0x807a
    8030:	81 93 00 00 	tst	0(r1)		;0x0000(r1)
    8034:	22 20       	jnz	$+70     	;abs 0x807a
    8036:	b1 90 80 7f 	cmp	#32640,	2(r1)	;#0x7f80, 0x0002(r1)
    803a:	02 00 
    803c:	1e 20       	jnz	$+62     	;abs 0x807a
    803e:	06 93       	tst	r6		
    8040:	0b 20       	jnz	$+24     	;abs 0x8058
    8042:	37 90 80 3f 	cmp	#16256,	r7	;#0x3f80
    8046:	08 20       	jnz	$+18     	;abs 0x8058
    8048:	0c 44       	mov	r4,	r12	
    804a:	0d 45       	mov	r5,	r13	
    804c:	0e 44       	mov	r4,	r14	
    804e:	0f 45       	mov	r5,	r15	
    8050:	b0 12 a6 93 	call	#0x93a6	
    8054:	30 40 14 8b 	br	#0x8b14	
    8058:	37 90 80 3f 	cmp	#16256,	r7	;#0x3f80
    805c:	0b 38       	jl	$+24     	;abs 0x8074
    805e:	02 20       	jnz	$+6      	;abs 0x8064
    8060:	16 93       	cmp	#1,	r6	;r3 As==01
    8062:	08 28       	jnc	$+18     	;abs 0x8074
    8064:	09 93       	tst	r9		
    8066:	02 38       	jl	$+6      	;abs 0x806c
    8068:	30 40 2e 8b 	br	#0x8b2e	
    806c:	04 43       	clr	r4		
    806e:	05 43       	clr	r5		
    8070:	30 40 2e 8b 	br	#0x8b2e	
    8074:	09 93       	tst	r9		
    8076:	fa 37       	jge	$-10     	;abs 0x806c
    8078:	5f 3c       	jmp	$+192    	;abs 0x8138
    807a:	81 93 00 00 	tst	0(r1)		;0x0000(r1)
    807e:	0e 20       	jnz	$+30     	;abs 0x809c
    8080:	b1 90 80 3f 	cmp	#16256,	2(r1)	;#0x3f80, 0x0002(r1)
    8084:	02 00 
    8086:	0a 20       	jnz	$+22     	;abs 0x809c
    8088:	09 93       	tst	r9		
    808a:	02 38       	jl	$+6      	;abs 0x8090
    808c:	30 40 14 8b 	br	#0x8b14	
    8090:	0c 4e       	mov	r14,	r12	
    8092:	0d 4f       	mov	r15,	r13	
    8094:	0e 43       	clr	r14		
    8096:	3f 40 80 3f 	mov	#16256,	r15	;#0x3f80
    809a:	77 3c       	jmp	$+240    	;abs 0x818a
    809c:	81 93 0c 00 	tst	12(r1)		;0x000c(r1)
    80a0:	10 20       	jnz	$+34     	;abs 0x80c2
    80a2:	39 90 00 40 	cmp	#16384,	r9	;#0x4000
    80a6:	03 20       	jnz	$+8      	;abs 0x80ae
    80a8:	0c 4e       	mov	r14,	r12	
    80aa:	0d 4f       	mov	r15,	r13	
    80ac:	89 3c       	jmp	$+276    	;abs 0x81c0
    80ae:	39 90 00 3f 	cmp	#16128,	r9	;#0x3f00
    80b2:	07 20       	jnz	$+16     	;abs 0x80c2
    80b4:	81 93 10 00 	tst	16(r1)		;0x0010(r1)
    80b8:	04 38       	jl	$+10     	;abs 0x80c2
    80ba:	b0 12 c2 8c 	call	#0x8cc2	
    80be:	30 40 14 8b 	br	#0x8b14	
    80c2:	0a 4e       	mov	r14,	r10	
    80c4:	0b 4f       	mov	r15,	r11	
    80c6:	3b f0 ff 7f 	and	#32767,	r11	;#0x7fff
    80ca:	06 93       	tst	r6		
    80cc:	03 20       	jnz	$+8      	;abs 0x80d4
    80ce:	37 90 80 7f 	cmp	#32640,	r7	;#0x7f80
    80d2:	09 24       	jz	$+20     	;abs 0x80e6
    80d4:	06 93       	tst	r6		
    80d6:	02 20       	jnz	$+6      	;abs 0x80dc
    80d8:	07 93       	tst	r7		
    80da:	05 24       	jz	$+12     	;abs 0x80e6
    80dc:	06 93       	tst	r6		
    80de:	30 20       	jnz	$+98     	;abs 0x8140
    80e0:	37 90 80 3f 	cmp	#16256,	r7	;#0x3f80
    80e4:	2d 20       	jnz	$+92     	;abs 0x8140
    80e6:	09 93       	tst	r9		
    80e8:	03 38       	jl	$+8      	;abs 0x80f0
    80ea:	0e 4a       	mov	r10,	r14	
    80ec:	0f 4b       	mov	r11,	r15	
    80ee:	07 3c       	jmp	$+16     	;abs 0x80fe
    80f0:	0c 4a       	mov	r10,	r12	
    80f2:	0d 4b       	mov	r11,	r13	
    80f4:	0e 43       	clr	r14		
    80f6:	3f 40 80 3f 	mov	#16256,	r15	;#0x3f80
    80fa:	b0 12 06 96 	call	#0x9606	
    80fe:	81 93 10 00 	tst	16(r1)		;0x0010(r1)
    8102:	02 38       	jl	$+6      	;abs 0x8108
    8104:	30 40 14 8b 	br	#0x8b14	
    8108:	06 53       	add	#0,	r6	;r3 As==00
    810a:	37 60 80 c0 	addc	#-16256,r7	;#0xc080
    810e:	16 d1 04 00 	bis	4(r1),	r6	;0x0004(r1)
    8112:	17 d1 06 00 	bis	6(r1),	r7	;0x0006(r1)
    8116:	06 93       	tst	r6		
    8118:	03 20       	jnz	$+8      	;abs 0x8120
    811a:	07 93       	tst	r7		
    811c:	01 20       	jnz	$+4      	;abs 0x8120
    811e:	2f 3c       	jmp	$+96     	;abs 0x817e
    8120:	04 4e       	mov	r14,	r4	
    8122:	05 4f       	mov	r15,	r5	
    8124:	91 93 04 00 	cmp	#1,	4(r1)	;r3 As==01, 0x0004(r1)
    8128:	02 24       	jz	$+6      	;abs 0x812e
    812a:	30 40 2e 8b 	br	#0x8b2e	
    812e:	81 93 06 00 	tst	6(r1)		;0x0006(r1)
    8132:	02 24       	jz	$+6      	;abs 0x8138
    8134:	30 40 2e 8b 	br	#0x8b2e	
    8138:	35 e0 00 80 	xor	#-32768,r5	;#0x8000
    813c:	30 40 2e 8b 	br	#0x8b2e	
    8140:	18 41 0a 00 	mov	10(r1),	r8	;0x000a(r1)
    8144:	08 58       	rla	r8		
    8146:	08 43       	clr	r8		
    8148:	08 68       	rlc	r8		
    814a:	81 48 08 00 	mov	r8,	8(r1)	;0x0008(r1)
    814e:	81 43 0a 00 	mov	#0,	10(r1)	;r3 As==00, 0x000a(r1)
    8152:	1c 41 08 00 	mov	8(r1),	r12	;0x0008(r1)
    8156:	1d 41 0a 00 	mov	10(r1),	r13	;0x000a(r1)
    815a:	3c 53       	add	#-1,	r12	;r3 As==11
    815c:	3d 63       	addc	#-1,	r13	;r3 As==11
    815e:	81 4c 1c 00 	mov	r12,	28(r1)	;0x001c(r1)
    8162:	81 4d 1e 00 	mov	r13,	30(r1)	;0x001e(r1)
    8166:	1c 41 04 00 	mov	4(r1),	r12	;0x0004(r1)
    816a:	1d 41 06 00 	mov	6(r1),	r13	;0x0006(r1)
    816e:	1c d1 1c 00 	bis	28(r1),	r12	;0x001c(r1)
    8172:	1d d1 1e 00 	bis	30(r1),	r13	;0x001e(r1)
    8176:	0c 93       	tst	r12		
    8178:	0c 20       	jnz	$+26     	;abs 0x8192
    817a:	0d 93       	tst	r13		
    817c:	0a 20       	jnz	$+22     	;abs 0x8192
    817e:	0c 4e       	mov	r14,	r12	
    8180:	0d 4f       	mov	r15,	r13	
    8182:	b0 12 a6 93 	call	#0x93a6	
    8186:	0c 4e       	mov	r14,	r12	
    8188:	0d 4f       	mov	r15,	r13	
    818a:	b0 12 06 96 	call	#0x9606	
    818e:	30 40 14 8b 	br	#0x8b14	
    8192:	b1 90 00 4d 	cmp	#19712,	2(r1)	;#0x4d00, 0x0002(r1)
    8196:	02 00 
    8198:	90 38       	jl	$+290    	;abs 0x82ba
    819a:	03 20       	jnz	$+8      	;abs 0x81a2
    819c:	91 93 00 00 	cmp	#1,	0(r1)	;r3 As==01, 0x0000(r1)
    81a0:	8c 28       	jnc	$+282    	;abs 0x82ba
    81a2:	37 90 7f 3f 	cmp	#16255,	r7	;#0x3f7f
    81a6:	06 38       	jl	$+14     	;abs 0x81b4
    81a8:	37 90 80 3f 	cmp	#16256,	r7	;#0x3f80
    81ac:	0d 34       	jge	$+28     	;abs 0x81c8
    81ae:	36 90 f8 ff 	cmp	#-8,	r6	;#0xfff8
    81b2:	0a 2c       	jc	$+22     	;abs 0x81c8
    81b4:	09 93       	tst	r9		
    81b6:	5a 37       	jge	$-330    	;abs 0x806c
    81b8:	3c 40 ca f2 	mov	#-3382,	r12	;#0xf2ca
    81bc:	3d 40 49 71 	mov	#29001,	r13	;#0x7149
    81c0:	0e 4c       	mov	r12,	r14	
    81c2:	0f 4d       	mov	r13,	r15	
    81c4:	30 40 10 8b 	br	#0x8b10	
    81c8:	37 90 80 3f 	cmp	#16256,	r7	;#0x3f80
    81cc:	0b 38       	jl	$+24     	;abs 0x81e4
    81ce:	02 20       	jnz	$+6      	;abs 0x81d4
    81d0:	36 92       	cmp	#8,	r6	;r2 As==11
    81d2:	08 28       	jnc	$+18     	;abs 0x81e4
    81d4:	09 93       	tst	r9		
    81d6:	4a 3b       	jl	$-362    	;abs 0x806c
    81d8:	19 93       	cmp	#1,	r9	;r3 As==01
    81da:	ee 37       	jge	$-34     	;abs 0x81b8
    81dc:	91 93 0c 00 	cmp	#1,	12(r1)	;r3 As==01, 0x000c(r1)
    81e0:	eb 2f       	jc	$-40     	;abs 0x81b8
    81e2:	44 3f       	jmp	$-374    	;abs 0x806c
    81e4:	0c 43       	clr	r12		
    81e6:	3d 40 80 3f 	mov	#16256,	r13	;#0x3f80
    81ea:	b0 12 a6 93 	call	#0x93a6	
    81ee:	0a 4e       	mov	r14,	r10	
    81f0:	0b 4f       	mov	r15,	r11	
    81f2:	3c 40 00 aa 	mov	#-22016,r12	;#0xaa00
    81f6:	3d 40 b8 3f 	mov	#16312,	r13	;#0x3fb8
    81fa:	b0 12 f6 93 	call	#0x93f6	
    81fe:	08 4e       	mov	r14,	r8	
    8200:	09 4f       	mov	r15,	r9	
    8202:	3c 40 70 a5 	mov	#-23184,r12	;#0xa570
    8206:	3d 40 ec 36 	mov	#14060,	r13	;#0x36ec
    820a:	0e 4a       	mov	r10,	r14	
    820c:	0f 4b       	mov	r11,	r15	
    820e:	b0 12 f6 93 	call	#0x93f6	
    8212:	81 4e 00 00 	mov	r14,	0(r1)	;0x0000(r1)
    8216:	81 4f 02 00 	mov	r15,	2(r1)	;0x0002(r1)
    821a:	0c 4a       	mov	r10,	r12	
    821c:	0d 4b       	mov	r11,	r13	
    821e:	0e 4a       	mov	r10,	r14	
    8220:	0f 4b       	mov	r11,	r15	
    8222:	b0 12 f6 93 	call	#0x93f6	
    8226:	06 4e       	mov	r14,	r6	
    8228:	07 4f       	mov	r15,	r7	
    822a:	0c 43       	clr	r12		
    822c:	3d 40 80 3e 	mov	#16000,	r13	;#0x3e80
    8230:	0e 4a       	mov	r10,	r14	
    8232:	0f 4b       	mov	r11,	r15	
    8234:	b0 12 f6 93 	call	#0x93f6	
    8238:	0c 4e       	mov	r14,	r12	
    823a:	0d 4f       	mov	r15,	r13	
    823c:	3e 40 ab aa 	mov	#-21845,r14	;#0xaaab
    8240:	3f 40 aa 3e 	mov	#16042,	r15	;#0x3eaa
    8244:	b0 12 a6 93 	call	#0x93a6	
    8248:	0c 4e       	mov	r14,	r12	
    824a:	0d 4f       	mov	r15,	r13	
    824c:	0e 4a       	mov	r10,	r14	
    824e:	0f 4b       	mov	r11,	r15	
    8250:	b0 12 f6 93 	call	#0x93f6	
    8254:	0c 4e       	mov	r14,	r12	
    8256:	0d 4f       	mov	r15,	r13	
    8258:	0e 43       	clr	r14		
    825a:	3f 40 00 3f 	mov	#16128,	r15	;#0x3f00
    825e:	b0 12 a6 93 	call	#0x93a6	
    8262:	0c 4e       	mov	r14,	r12	
    8264:	0d 4f       	mov	r15,	r13	
    8266:	0e 46       	mov	r6,	r14	
    8268:	0f 47       	mov	r7,	r15	
    826a:	b0 12 f6 93 	call	#0x93f6	
    826e:	3c 40 3b aa 	mov	#-21957,r12	;#0xaa3b
    8272:	3d 40 b8 3f 	mov	#16312,	r13	;#0x3fb8
    8276:	b0 12 f6 93 	call	#0x93f6	
    827a:	0c 4e       	mov	r14,	r12	
    827c:	0d 4f       	mov	r15,	r13	
    827e:	2e 41       	mov	@r1,	r14	
    8280:	1f 41 02 00 	mov	2(r1),	r15	;0x0002(r1)
    8284:	b0 12 a6 93 	call	#0x93a6	
    8288:	0a 4e       	mov	r14,	r10	
    828a:	0b 4f       	mov	r15,	r11	
    828c:	0c 4e       	mov	r14,	r12	
    828e:	0d 4f       	mov	r15,	r13	
    8290:	0e 48       	mov	r8,	r14	
    8292:	0f 49       	mov	r9,	r15	
    8294:	b0 12 5a 93 	call	#0x935a	
    8298:	3e f0 00 f0 	and	#-4096,	r14	;#0xf000
    829c:	3f f3       	and	#-1,	r15	;r3 As==11
    829e:	81 4e 08 00 	mov	r14,	8(r1)	;0x0008(r1)
    82a2:	81 4f 0a 00 	mov	r15,	10(r1)	;0x000a(r1)
    82a6:	0c 48       	mov	r8,	r12	
    82a8:	0d 49       	mov	r9,	r13	
    82aa:	b0 12 a6 93 	call	#0x93a6	
    82ae:	0c 4e       	mov	r14,	r12	
    82b0:	0d 4f       	mov	r15,	r13	
    82b2:	0e 4a       	mov	r10,	r14	
    82b4:	0f 4b       	mov	r11,	r15	
    82b6:	30 40 c6 86 	br	#0x86c6	
    82ba:	37 90 80 00 	cmp	#128,	r7	;#0x0080
    82be:	03 38       	jl	$+8      	;abs 0x82c6
    82c0:	0e 43       	clr	r14		
    82c2:	0f 43       	clr	r15		
    82c4:	0c 3c       	jmp	$+26     	;abs 0x82de
    82c6:	0c 43       	clr	r12		
    82c8:	3d 40 80 4b 	mov	#19328,	r13	;#0x4b80
    82cc:	0e 4a       	mov	r10,	r14	
    82ce:	0f 4b       	mov	r11,	r15	
    82d0:	b0 12 f6 93 	call	#0x93f6	
    82d4:	06 4e       	mov	r14,	r6	
    82d6:	07 4f       	mov	r15,	r7	
    82d8:	3e 40 e8 ff 	mov	#-24,	r14	;#0xffe8
    82dc:	3f 43       	mov	#-1,	r15	;r3 As==11
    82de:	0c 47       	mov	r7,	r12	
    82e0:	0d 47       	mov	r7,	r13	
    82e2:	8d 10       	swpb	r13		
    82e4:	8d 11       	sxt	r13		
    82e6:	8d 10       	swpb	r13		
    82e8:	8d 11       	sxt	r13		
    82ea:	7b 40 07 00 	mov.b	#7,	r11	;#0x0007
    82ee:	0d 11       	rra	r13		
    82f0:	0c 10       	rrc	r12		
    82f2:	7b 53       	add.b	#-1,	r11	;r3 As==11
    82f4:	fc 23       	jnz	$-6      	;abs 0x82ee
    82f6:	0a 4c       	mov	r12,	r10	
    82f8:	0b 4d       	mov	r13,	r11	
    82fa:	3a 50 81 ff 	add	#-127,	r10	;#0xff81
    82fe:	3b 63       	addc	#-1,	r11	;r3 As==11
    8300:	0a 5e       	add	r14,	r10	
    8302:	0b 6f       	addc	r15,	r11	
    8304:	81 4a 10 00 	mov	r10,	16(r1)	;0x0010(r1)
    8308:	81 4b 12 00 	mov	r11,	18(r1)	;0x0012(r1)
    830c:	36 f3       	and	#-1,	r6	;r3 As==11
    830e:	37 f0 7f 00 	and	#127,	r7	;#0x007f
    8312:	0a 46       	mov	r6,	r10	
    8314:	0b 47       	mov	r7,	r11	
    8316:	0a d3       	bis	#0,	r10	;r3 As==00
    8318:	3b d0 80 3f 	bis	#16256,	r11	;#0x3f80
    831c:	37 90 1c 00 	cmp	#28,	r7	;#0x001c
    8320:	12 38       	jl	$+38     	;abs 0x8346
    8322:	03 20       	jnz	$+8      	;abs 0x832a
    8324:	36 90 72 c4 	cmp	#-15246,r6	;#0xc472
    8328:	0e 28       	jnc	$+30     	;abs 0x8346
    832a:	37 90 5d 00 	cmp	#93,	r7	;#0x005d
    832e:	10 38       	jl	$+34     	;abs 0x8350
    8330:	03 20       	jnz	$+8      	;abs 0x8338
    8332:	36 90 d7 b3 	cmp	#-19497,r6	;#0xb3d7
    8336:	0c 28       	jnc	$+26     	;abs 0x8350
    8338:	91 53 10 00 	inc	16(r1)		;0x0010(r1)
    833c:	81 63 12 00 	adc	18(r1)		;0x0012(r1)
    8340:	0a 53       	add	#0,	r10	;r3 As==00
    8342:	3b 60 80 ff 	addc	#-128,	r11	;#0xff80
    8346:	81 43 08 00 	mov	#0,	8(r1)	;r3 As==00, 0x0008(r1)
    834a:	81 43 0a 00 	mov	#0,	10(r1)	;r3 As==00, 0x000a(r1)
    834e:	04 3c       	jmp	$+10     	;abs 0x8358
    8350:	91 43 08 00 	mov	#1,	8(r1)	;r3 As==01, 0x0008(r1)
    8354:	81 43 0a 00 	mov	#0,	10(r1)	;r3 As==00, 0x000a(r1)
    8358:	81 4a 20 00 	mov	r10,	32(r1)	;0x0020(r1)
    835c:	81 4b 22 00 	mov	r11,	34(r1)	;0x0022(r1)
    8360:	1f 41 08 00 	mov	8(r1),	r15	;0x0008(r1)
    8364:	0f 5f       	rla	r15		
    8366:	0f 5f       	rla	r15		
    8368:	18 4f 0e af 	mov	-20722(r15),r8	;0xaf0e(r15)
    836c:	19 4f 10 af 	mov	-20720(r15),r9	;0xaf10(r15)
    8370:	0c 48       	mov	r8,	r12	
    8372:	0d 49       	mov	r9,	r13	
    8374:	0e 4a       	mov	r10,	r14	
    8376:	0f 4b       	mov	r11,	r15	
    8378:	b0 12 a6 93 	call	#0x93a6	
    837c:	06 4e       	mov	r14,	r6	
    837e:	07 4f       	mov	r15,	r7	
    8380:	0c 48       	mov	r8,	r12	
    8382:	0d 49       	mov	r9,	r13	
    8384:	0e 4a       	mov	r10,	r14	
    8386:	0f 4b       	mov	r11,	r15	
    8388:	b0 12 5a 93 	call	#0x935a	
    838c:	0c 4e       	mov	r14,	r12	
    838e:	0d 4f       	mov	r15,	r13	
    8390:	0e 43       	clr	r14		
    8392:	3f 40 80 3f 	mov	#16256,	r15	;#0x3f80
    8396:	b0 12 06 96 	call	#0x9606	
    839a:	81 4e 18 00 	mov	r14,	24(r1)	;0x0018(r1)
    839e:	81 4f 1a 00 	mov	r15,	26(r1)	;0x001a(r1)
    83a2:	0c 4e       	mov	r14,	r12	
    83a4:	0d 4f       	mov	r15,	r13	
    83a6:	0e 46       	mov	r6,	r14	
    83a8:	0f 47       	mov	r7,	r15	
    83aa:	b0 12 f6 93 	call	#0x93f6	
    83ae:	81 4e 0c 00 	mov	r14,	12(r1)	;0x000c(r1)
    83b2:	81 4f 0e 00 	mov	r15,	14(r1)	;0x000e(r1)
    83b6:	1e 41 0c 00 	mov	12(r1),	r14	;0x000c(r1)
    83ba:	1f 41 0e 00 	mov	14(r1),	r15	;0x000e(r1)
    83be:	3e f0 00 f0 	and	#-4096,	r14	;#0xf000
    83c2:	3f f3       	and	#-1,	r15	;r3 As==11
    83c4:	81 4e 00 00 	mov	r14,	0(r1)	;0x0000(r1)
    83c8:	81 4f 02 00 	mov	r15,	2(r1)	;0x0002(r1)
    83cc:	0b 11       	rra	r11		
    83ce:	0a 10       	rrc	r10		
    83d0:	0a d3       	bis	#0,	r10	;r3 As==00
    83d2:	3b d0 00 20 	bis	#8192,	r11	;#0x2000
    83d6:	0a 53       	add	#0,	r10	;r3 As==00
    83d8:	2b 62       	addc	#4,	r11	;r2 As==10
    83da:	0e 43       	clr	r14		
    83dc:	0f 43       	clr	r15		
    83de:	1f 41 08 00 	mov	8(r1),	r15	;0x0008(r1)
    83e2:	7d 40 05 00 	mov.b	#5,	r13	;#0x0005
    83e6:	0e 5e       	rla	r14		
    83e8:	0f 6f       	rlc	r15		
    83ea:	7d 53       	add.b	#-1,	r13	;r3 As==11
    83ec:	fc 23       	jnz	$-6      	;abs 0x83e6
    83ee:	0a 5e       	add	r14,	r10	
    83f0:	0b 6f       	addc	r15,	r11	
    83f2:	0c 4a       	mov	r10,	r12	
    83f4:	0d 4b       	mov	r11,	r13	
    83f6:	2e 41       	mov	@r1,	r14	
    83f8:	1f 41 02 00 	mov	2(r1),	r15	;0x0002(r1)
    83fc:	b0 12 f6 93 	call	#0x93f6	
    8400:	0c 4e       	mov	r14,	r12	
    8402:	0d 4f       	mov	r15,	r13	
    8404:	0e 46       	mov	r6,	r14	
    8406:	0f 47       	mov	r7,	r15	
    8408:	b0 12 a6 93 	call	#0x93a6	
    840c:	06 4e       	mov	r14,	r6	
    840e:	07 4f       	mov	r15,	r7	
    8410:	0c 48       	mov	r8,	r12	
    8412:	0d 49       	mov	r9,	r13	
    8414:	0e 4a       	mov	r10,	r14	
    8416:	0f 4b       	mov	r11,	r15	
    8418:	b0 12 a6 93 	call	#0x93a6	
    841c:	0c 4e       	mov	r14,	r12	
    841e:	0d 4f       	mov	r15,	r13	
    8420:	1e 41 20 00 	mov	32(r1),	r14	;0x0020(r1)
    8424:	1f 41 22 00 	mov	34(r1),	r15	;0x0022(r1)
    8428:	b0 12 a6 93 	call	#0x93a6	
    842c:	0c 4e       	mov	r14,	r12	
    842e:	0d 4f       	mov	r15,	r13	
    8430:	2e 41       	mov	@r1,	r14	
    8432:	1f 41 02 00 	mov	2(r1),	r15	;0x0002(r1)
    8436:	b0 12 f6 93 	call	#0x93f6	
    843a:	0c 4e       	mov	r14,	r12	
    843c:	0d 4f       	mov	r15,	r13	
    843e:	0e 46       	mov	r6,	r14	
    8440:	0f 47       	mov	r7,	r15	
    8442:	b0 12 a6 93 	call	#0x93a6	
    8446:	0c 4e       	mov	r14,	r12	
    8448:	0d 4f       	mov	r15,	r13	
    844a:	1e 41 18 00 	mov	24(r1),	r14	;0x0018(r1)
    844e:	1f 41 1a 00 	mov	26(r1),	r15	;0x001a(r1)
    8452:	b0 12 f6 93 	call	#0x93f6	
    8456:	06 4e       	mov	r14,	r6	
    8458:	07 4f       	mov	r15,	r7	
    845a:	1c 41 0c 00 	mov	12(r1),	r12	;0x000c(r1)
    845e:	1d 41 0e 00 	mov	14(r1),	r13	;0x000e(r1)
    8462:	0e 4c       	mov	r12,	r14	
    8464:	0f 4d       	mov	r13,	r15	
    8466:	b0 12 f6 93 	call	#0x93f6	
    846a:	0a 4e       	mov	r14,	r10	
    846c:	0b 4f       	mov	r15,	r11	
    846e:	0c 4e       	mov	r14,	r12	
    8470:	0d 4f       	mov	r15,	r13	
    8472:	b0 12 f6 93 	call	#0x93f6	
    8476:	08 4e       	mov	r14,	r8	
    8478:	09 4f       	mov	r15,	r9	
    847a:	3c 40 42 f1 	mov	#-3774,	r12	;#0xf142
    847e:	3d 40 53 3e 	mov	#15955,	r13	;#0x3e53
    8482:	0e 4a       	mov	r10,	r14	
    8484:	0f 4b       	mov	r11,	r15	
    8486:	b0 12 f6 93 	call	#0x93f6	
    848a:	3c 40 55 32 	mov	#12885,	r12	;#0x3255
    848e:	3d 40 6c 3e 	mov	#15980,	r13	;#0x3e6c
    8492:	b0 12 5a 93 	call	#0x935a	
    8496:	0c 4e       	mov	r14,	r12	
    8498:	0d 4f       	mov	r15,	r13	
    849a:	0e 4a       	mov	r10,	r14	
    849c:	0f 4b       	mov	r11,	r15	
    849e:	b0 12 f6 93 	call	#0x93f6	
    84a2:	3c 40 05 a3 	mov	#-23803,r12	;#0xa305
    84a6:	3d 40 8b 3e 	mov	#16011,	r13	;#0x3e8b
    84aa:	b0 12 5a 93 	call	#0x935a	
    84ae:	0c 4e       	mov	r14,	r12	
    84b0:	0d 4f       	mov	r15,	r13	
    84b2:	0e 4a       	mov	r10,	r14	
    84b4:	0f 4b       	mov	r11,	r15	
    84b6:	b0 12 f6 93 	call	#0x93f6	
    84ba:	3c 40 ab aa 	mov	#-21845,r12	;#0xaaab
    84be:	3d 40 aa 3e 	mov	#16042,	r13	;#0x3eaa
    84c2:	b0 12 5a 93 	call	#0x935a	
    84c6:	0c 4e       	mov	r14,	r12	
    84c8:	0d 4f       	mov	r15,	r13	
    84ca:	0e 4a       	mov	r10,	r14	
    84cc:	0f 4b       	mov	r11,	r15	
    84ce:	b0 12 f6 93 	call	#0x93f6	
    84d2:	3c 40 b7 6d 	mov	#28087,	r12	;#0x6db7
    84d6:	3d 40 db 3e 	mov	#16091,	r13	;#0x3edb
    84da:	b0 12 5a 93 	call	#0x935a	
    84de:	0c 4e       	mov	r14,	r12	
    84e0:	0d 4f       	mov	r15,	r13	
    84e2:	0e 4a       	mov	r10,	r14	
    84e4:	0f 4b       	mov	r11,	r15	
    84e6:	b0 12 f6 93 	call	#0x93f6	
    84ea:	3c 40 9a 99 	mov	#-26214,r12	;#0x999a
    84ee:	3d 40 19 3f 	mov	#16153,	r13	;#0x3f19
    84f2:	b0 12 5a 93 	call	#0x935a	
    84f6:	0c 4e       	mov	r14,	r12	
    84f8:	0d 4f       	mov	r15,	r13	
    84fa:	0e 48       	mov	r8,	r14	
    84fc:	0f 49       	mov	r9,	r15	
    84fe:	b0 12 f6 93 	call	#0x93f6	
    8502:	0a 4e       	mov	r14,	r10	
    8504:	0b 4f       	mov	r15,	r11	
    8506:	1c 41 0c 00 	mov	12(r1),	r12	;0x000c(r1)
    850a:	1d 41 0e 00 	mov	14(r1),	r13	;0x000e(r1)
    850e:	2e 41       	mov	@r1,	r14	
    8510:	1f 41 02 00 	mov	2(r1),	r15	;0x0002(r1)
    8514:	b0 12 5a 93 	call	#0x935a	
    8518:	0c 4e       	mov	r14,	r12	
    851a:	0d 4f       	mov	r15,	r13	
    851c:	0e 46       	mov	r6,	r14	
    851e:	0f 47       	mov	r7,	r15	
    8520:	b0 12 f6 93 	call	#0x93f6	
    8524:	0c 4e       	mov	r14,	r12	
    8526:	0d 4f       	mov	r15,	r13	
    8528:	0e 4a       	mov	r10,	r14	
    852a:	0f 4b       	mov	r11,	r15	
    852c:	b0 12 5a 93 	call	#0x935a	
    8530:	08 4e       	mov	r14,	r8	
    8532:	09 4f       	mov	r15,	r9	
    8534:	2c 41       	mov	@r1,	r12	
    8536:	1d 41 02 00 	mov	2(r1),	r13	;0x0002(r1)
    853a:	0e 4c       	mov	r12,	r14	
    853c:	0f 4d       	mov	r13,	r15	
    853e:	b0 12 f6 93 	call	#0x93f6	
    8542:	81 4e 18 00 	mov	r14,	24(r1)	;0x0018(r1)
    8546:	81 4f 1a 00 	mov	r15,	26(r1)	;0x001a(r1)
    854a:	0c 43       	clr	r12		
    854c:	3d 40 40 40 	mov	#16448,	r13	;#0x4040
    8550:	b0 12 5a 93 	call	#0x935a	
    8554:	0c 48       	mov	r8,	r12	
    8556:	0d 49       	mov	r9,	r13	
    8558:	b0 12 5a 93 	call	#0x935a	
    855c:	0a 4e       	mov	r14,	r10	
    855e:	0b 4f       	mov	r15,	r11	
    8560:	3a f0 00 f0 	and	#-4096,	r10	;#0xf000
    8564:	3b f3       	and	#-1,	r11	;r3 As==11
    8566:	0c 4a       	mov	r10,	r12	
    8568:	0d 4b       	mov	r11,	r13	
    856a:	2e 41       	mov	@r1,	r14	
    856c:	1f 41 02 00 	mov	2(r1),	r15	;0x0002(r1)
    8570:	b0 12 f6 93 	call	#0x93f6	
    8574:	81 4e 00 00 	mov	r14,	0(r1)	;0x0000(r1)
    8578:	81 4f 02 00 	mov	r15,	2(r1)	;0x0002(r1)
    857c:	0c 4a       	mov	r10,	r12	
    857e:	0d 4b       	mov	r11,	r13	
    8580:	0e 46       	mov	r6,	r14	
    8582:	0f 47       	mov	r7,	r15	
    8584:	b0 12 f6 93 	call	#0x93f6	
    8588:	06 4e       	mov	r14,	r6	
    858a:	07 4f       	mov	r15,	r7	
    858c:	0c 43       	clr	r12		
    858e:	3d 40 40 40 	mov	#16448,	r13	;#0x4040
    8592:	0e 4a       	mov	r10,	r14	
    8594:	0f 4b       	mov	r11,	r15	
    8596:	b0 12 a6 93 	call	#0x93a6	
    859a:	1c 41 18 00 	mov	24(r1),	r12	;0x0018(r1)
    859e:	1d 41 1a 00 	mov	26(r1),	r13	;0x001a(r1)
    85a2:	b0 12 a6 93 	call	#0x93a6	
    85a6:	0c 4e       	mov	r14,	r12	
    85a8:	0d 4f       	mov	r15,	r13	
    85aa:	0e 48       	mov	r8,	r14	
    85ac:	0f 49       	mov	r9,	r15	
    85ae:	b0 12 a6 93 	call	#0x93a6	
    85b2:	1c 41 0c 00 	mov	12(r1),	r12	;0x000c(r1)
    85b6:	1d 41 0e 00 	mov	14(r1),	r13	;0x000e(r1)
    85ba:	b0 12 f6 93 	call	#0x93f6	
    85be:	0c 4e       	mov	r14,	r12	
    85c0:	0d 4f       	mov	r15,	r13	
    85c2:	0e 46       	mov	r6,	r14	
    85c4:	0f 47       	mov	r7,	r15	
    85c6:	b0 12 5a 93 	call	#0x935a	
    85ca:	08 4e       	mov	r14,	r8	
    85cc:	09 4f       	mov	r15,	r9	
    85ce:	0c 4e       	mov	r14,	r12	
    85d0:	0d 4f       	mov	r15,	r13	
    85d2:	2e 41       	mov	@r1,	r14	
    85d4:	1f 41 02 00 	mov	2(r1),	r15	;0x0002(r1)
    85d8:	b0 12 5a 93 	call	#0x935a	
    85dc:	0a 4e       	mov	r14,	r10	
    85de:	0b 4f       	mov	r15,	r11	
    85e0:	3a f0 00 f0 	and	#-4096,	r10	;#0xf000
    85e4:	3b f3       	and	#-1,	r11	;r3 As==11
    85e6:	3c 40 00 38 	mov	#14336,	r12	;#0x3800
    85ea:	3d 40 76 3f 	mov	#16246,	r13	;#0x3f76
    85ee:	0e 4a       	mov	r10,	r14	
    85f0:	0f 4b       	mov	r11,	r15	
    85f2:	b0 12 f6 93 	call	#0x93f6	
    85f6:	81 4e 0c 00 	mov	r14,	12(r1)	;0x000c(r1)
    85fa:	81 4f 0e 00 	mov	r15,	14(r1)	;0x000e(r1)
    85fe:	3c 40 a0 c3 	mov	#-15456,r12	;#0xc3a0
    8602:	3d 40 9d 36 	mov	#13981,	r13	;#0x369d
    8606:	0e 4a       	mov	r10,	r14	
    8608:	0f 4b       	mov	r11,	r15	
    860a:	b0 12 f6 93 	call	#0x93f6	
    860e:	06 4e       	mov	r14,	r6	
    8610:	07 4f       	mov	r15,	r7	
    8612:	2c 41       	mov	@r1,	r12	
    8614:	1d 41 02 00 	mov	2(r1),	r13	;0x0002(r1)
    8618:	0e 4a       	mov	r10,	r14	
    861a:	0f 4b       	mov	r11,	r15	
    861c:	b0 12 a6 93 	call	#0x93a6	
    8620:	0c 4e       	mov	r14,	r12	
    8622:	0d 4f       	mov	r15,	r13	
    8624:	0e 48       	mov	r8,	r14	
    8626:	0f 49       	mov	r9,	r15	
    8628:	b0 12 a6 93 	call	#0x93a6	
    862c:	3c 40 4f 38 	mov	#14415,	r12	;#0x384f
    8630:	3d 40 76 3f 	mov	#16246,	r13	;#0x3f76
    8634:	b0 12 f6 93 	call	#0x93f6	
    8638:	0c 4e       	mov	r14,	r12	
    863a:	0d 4f       	mov	r15,	r13	
    863c:	0e 46       	mov	r6,	r14	
    863e:	0f 47       	mov	r7,	r15	
    8640:	b0 12 5a 93 	call	#0x935a	
    8644:	1b 41 08 00 	mov	8(r1),	r11	;0x0008(r1)
    8648:	0b 5b       	rla	r11		
    864a:	0b 5b       	rla	r11		
    864c:	1c 4b 16 af 	mov	-20714(r11),r12	;0xaf16(r11)
    8650:	1d 4b 18 af 	mov	-20712(r11),r13	;0xaf18(r11)
    8654:	b0 12 5a 93 	call	#0x935a	
    8658:	06 4e       	mov	r14,	r6	
    865a:	07 4f       	mov	r15,	r7	
    865c:	1e 41 10 00 	mov	16(r1),	r14	;0x0010(r1)
    8660:	1f 41 12 00 	mov	18(r1),	r15	;0x0012(r1)
    8664:	b0 12 86 98 	call	#0x9886	
    8668:	08 4e       	mov	r14,	r8	
    866a:	09 4f       	mov	r15,	r9	
    866c:	1a 4b 1e af 	mov	-20706(r11),r10	;0xaf1e(r11)
    8670:	1b 4b 20 af 	mov	-20704(r11),r11	;0xaf20(r11)
    8674:	0c 46       	mov	r6,	r12	
    8676:	0d 47       	mov	r7,	r13	
    8678:	1e 41 0c 00 	mov	12(r1),	r14	;0x000c(r1)
    867c:	1f 41 0e 00 	mov	14(r1),	r15	;0x000e(r1)
    8680:	b0 12 5a 93 	call	#0x935a	
    8684:	0c 4a       	mov	r10,	r12	
    8686:	0d 4b       	mov	r11,	r13	
    8688:	b0 12 5a 93 	call	#0x935a	
    868c:	0c 48       	mov	r8,	r12	
    868e:	0d 49       	mov	r9,	r13	
    8690:	b0 12 5a 93 	call	#0x935a	
    8694:	3e f0 00 f0 	and	#-4096,	r14	;#0xf000
    8698:	3f f3       	and	#-1,	r15	;r3 As==11
    869a:	81 4e 08 00 	mov	r14,	8(r1)	;0x0008(r1)
    869e:	81 4f 0a 00 	mov	r15,	10(r1)	;0x000a(r1)
    86a2:	0c 48       	mov	r8,	r12	
    86a4:	0d 49       	mov	r9,	r13	
    86a6:	b0 12 a6 93 	call	#0x93a6	
    86aa:	0c 4a       	mov	r10,	r12	
    86ac:	0d 4b       	mov	r11,	r13	
    86ae:	b0 12 a6 93 	call	#0x93a6	
    86b2:	1c 41 0c 00 	mov	12(r1),	r12	;0x000c(r1)
    86b6:	1d 41 0e 00 	mov	14(r1),	r13	;0x000e(r1)
    86ba:	b0 12 a6 93 	call	#0x93a6	
    86be:	0c 4e       	mov	r14,	r12	
    86c0:	0d 4f       	mov	r15,	r13	
    86c2:	0e 46       	mov	r6,	r14	
    86c4:	0f 47       	mov	r7,	r15	
    86c6:	b0 12 a6 93 	call	#0x93a6	
    86ca:	08 4e       	mov	r14,	r8	
    86cc:	09 4f       	mov	r15,	r9	
    86ce:	1e 41 04 00 	mov	4(r1),	r14	;0x0004(r1)
    86d2:	1f 41 06 00 	mov	6(r1),	r15	;0x0006(r1)
    86d6:	3e 53       	add	#-1,	r14	;r3 As==11
    86d8:	3f 63       	addc	#-1,	r15	;r3 As==11
    86da:	1e d1 1c 00 	bis	28(r1),	r14	;0x001c(r1)
    86de:	1f d1 1e 00 	bis	30(r1),	r15	;0x001e(r1)
    86e2:	0e 93       	tst	r14		
    86e4:	08 20       	jnz	$+18     	;abs 0x86f6
    86e6:	0f 93       	tst	r15		
    86e8:	06 20       	jnz	$+14     	;abs 0x86f6
    86ea:	81 43 00 00 	mov	#0,	0(r1)	;r3 As==00, 0x0000(r1)
    86ee:	b1 40 80 bf 	mov	#-16512,2(r1)	;#0xbf80, 0x0002(r1)
    86f2:	02 00 
    86f4:	05 3c       	jmp	$+12     	;abs 0x8700
    86f6:	81 43 00 00 	mov	#0,	0(r1)	;r3 As==00, 0x0000(r1)
    86fa:	b1 40 80 3f 	mov	#16256,	2(r1)	;#0x3f80, 0x0002(r1)
    86fe:	02 00 
    8700:	1a 41 14 00 	mov	20(r1),	r10	;0x0014(r1)
    8704:	1b 41 16 00 	mov	22(r1),	r11	;0x0016(r1)
    8708:	3a f0 00 f0 	and	#-4096,	r10	;#0xf000
    870c:	3b f3       	and	#-1,	r11	;r3 As==11
    870e:	0c 4a       	mov	r10,	r12	
    8710:	0d 4b       	mov	r11,	r13	
    8712:	0e 44       	mov	r4,	r14	
    8714:	0f 45       	mov	r5,	r15	
    8716:	b0 12 a6 93 	call	#0x93a6	
    871a:	1c 41 08 00 	mov	8(r1),	r12	;0x0008(r1)
    871e:	1d 41 0a 00 	mov	10(r1),	r13	;0x000a(r1)
    8722:	b0 12 f6 93 	call	#0x93f6	
    8726:	06 4e       	mov	r14,	r6	
    8728:	07 4f       	mov	r15,	r7	
    872a:	0c 48       	mov	r8,	r12	
    872c:	0d 49       	mov	r9,	r13	
    872e:	0e 44       	mov	r4,	r14	
    8730:	0f 45       	mov	r5,	r15	
    8732:	b0 12 f6 93 	call	#0x93f6	
    8736:	0c 4e       	mov	r14,	r12	
    8738:	0d 4f       	mov	r15,	r13	
    873a:	0e 46       	mov	r6,	r14	
    873c:	0f 47       	mov	r7,	r15	
    873e:	b0 12 5a 93 	call	#0x935a	
    8742:	81 4e 04 00 	mov	r14,	4(r1)	;0x0004(r1)
    8746:	81 4f 06 00 	mov	r15,	6(r1)	;0x0006(r1)
    874a:	1c 41 08 00 	mov	8(r1),	r12	;0x0008(r1)
    874e:	1d 41 0a 00 	mov	10(r1),	r13	;0x000a(r1)
    8752:	0e 4a       	mov	r10,	r14	
    8754:	0f 4b       	mov	r11,	r15	
    8756:	b0 12 f6 93 	call	#0x93f6	
    875a:	06 4e       	mov	r14,	r6	
    875c:	07 4f       	mov	r15,	r7	
    875e:	0c 4e       	mov	r14,	r12	
    8760:	0d 4f       	mov	r15,	r13	
    8762:	1e 41 04 00 	mov	4(r1),	r14	;0x0004(r1)
    8766:	1f 41 06 00 	mov	6(r1),	r15	;0x0006(r1)
    876a:	b0 12 5a 93 	call	#0x935a	
    876e:	04 4e       	mov	r14,	r4	
    8770:	05 4f       	mov	r15,	r5	
    8772:	08 4e       	mov	r14,	r8	
    8774:	09 4f       	mov	r15,	r9	
    8776:	0a 4e       	mov	r14,	r10	
    8778:	0b 4f       	mov	r15,	r11	
    877a:	3a f3       	and	#-1,	r10	;r3 As==11
    877c:	3b f0 ff 7f 	and	#32767,	r11	;#0x7fff
    8780:	09 93       	tst	r9		
    8782:	3d 38       	jl	$+124    	;abs 0x87fe
    8784:	02 20       	jnz	$+6      	;abs 0x878a
    8786:	1e 93       	cmp	#1,	r14	;r3 As==01
    8788:	3a 28       	jnc	$+118    	;abs 0x87fe
    878a:	3b 90 00 43 	cmp	#17152,	r11	;#0x4300
    878e:	04 38       	jl	$+10     	;abs 0x8798
    8790:	27 20       	jnz	$+80     	;abs 0x87e0
    8792:	1a 93       	cmp	#1,	r10	;r3 As==01
    8794:	01 28       	jnc	$+4      	;abs 0x8798
    8796:	24 3c       	jmp	$+74     	;abs 0x87e0
    8798:	0a 93       	tst	r10		
    879a:	5d 20       	jnz	$+188    	;abs 0x8856
    879c:	3b 90 00 43 	cmp	#17152,	r11	;#0x4300
    87a0:	5a 20       	jnz	$+182    	;abs 0x8856
    87a2:	3c 40 3c aa 	mov	#-21956,r12	;#0xaa3c
    87a6:	3d 40 38 33 	mov	#13112,	r13	;#0x3338
    87aa:	1e 41 04 00 	mov	4(r1),	r14	;0x0004(r1)
    87ae:	1f 41 06 00 	mov	6(r1),	r15	;0x0006(r1)
    87b2:	b0 12 5a 93 	call	#0x935a	
    87b6:	81 4e 08 00 	mov	r14,	8(r1)	;0x0008(r1)
    87ba:	81 4f 0a 00 	mov	r15,	10(r1)	;0x000a(r1)
    87be:	0c 46       	mov	r6,	r12	
    87c0:	0d 47       	mov	r7,	r13	
    87c2:	0e 44       	mov	r4,	r14	
    87c4:	0f 45       	mov	r5,	r15	
    87c6:	b0 12 a6 93 	call	#0x93a6	
    87ca:	0c 4e       	mov	r14,	r12	
    87cc:	0d 4f       	mov	r15,	r13	
    87ce:	1e 41 08 00 	mov	8(r1),	r14	;0x0008(r1)
    87d2:	1f 41 0a 00 	mov	10(r1),	r15	;0x000a(r1)
    87d6:	b0 12 4e 97 	call	#0x974e	
    87da:	0f 93       	tst	r15		
    87dc:	42 24       	jz	$+134    	;abs 0x8862
    87de:	41 38       	jl	$+132    	;abs 0x8862
    87e0:	3c 40 ca f2 	mov	#-3382,	r12	;#0xf2ca
    87e4:	3d 40 49 71 	mov	#29001,	r13	;#0x7149
    87e8:	2e 41       	mov	@r1,	r14	
    87ea:	1f 41 02 00 	mov	2(r1),	r15	;0x0002(r1)
    87ee:	b0 12 f6 93 	call	#0x93f6	
    87f2:	3c 40 ca f2 	mov	#-3382,	r12	;#0xf2ca
    87f6:	3d 40 49 71 	mov	#29001,	r13	;#0x7149
    87fa:	30 40 10 8b 	br	#0x8b10	
    87fe:	3b 90 16 43 	cmp	#17174,	r11	;#0x4316
    8802:	04 38       	jl	$+10     	;abs 0x880c
    8804:	19 20       	jnz	$+52     	;abs 0x8838
    8806:	1a 93       	cmp	#1,	r10	;r3 As==01
    8808:	01 28       	jnc	$+4      	;abs 0x880c
    880a:	16 3c       	jmp	$+46     	;abs 0x8838
    880c:	0a 93       	tst	r10		
    880e:	23 20       	jnz	$+72     	;abs 0x8856
    8810:	3b 90 16 43 	cmp	#17174,	r11	;#0x4316
    8814:	20 20       	jnz	$+66     	;abs 0x8856
    8816:	0c 46       	mov	r6,	r12	
    8818:	0d 47       	mov	r7,	r13	
    881a:	0e 44       	mov	r4,	r14	
    881c:	0f 45       	mov	r5,	r15	
    881e:	b0 12 a6 93 	call	#0x93a6	
    8822:	0c 4e       	mov	r14,	r12	
    8824:	0d 4f       	mov	r15,	r13	
    8826:	1e 41 04 00 	mov	4(r1),	r14	;0x0004(r1)
    882a:	1f 41 06 00 	mov	6(r1),	r15	;0x0006(r1)
    882e:	b0 12 38 98 	call	#0x9838	
    8832:	0f 93       	tst	r15		
    8834:	01 24       	jz	$+4      	;abs 0x8838
    8836:	15 34       	jge	$+44     	;abs 0x8862
    8838:	3c 40 60 42 	mov	#16992,	r12	;#0x4260
    883c:	3d 40 a2 0d 	mov	#3490,	r13	;#0x0da2
    8840:	2e 41       	mov	@r1,	r14	
    8842:	1f 41 02 00 	mov	2(r1),	r15	;0x0002(r1)
    8846:	b0 12 f6 93 	call	#0x93f6	
    884a:	3c 40 60 42 	mov	#16992,	r12	;#0x4260
    884e:	3d 40 a2 0d 	mov	#3490,	r13	;#0x0da2
    8852:	30 40 10 8b 	br	#0x8b10	
    8856:	3b 90 00 3f 	cmp	#16128,	r11	;#0x3f00
    885a:	62 38       	jl	$+198    	;abs 0x8920
    885c:	02 20       	jnz	$+6      	;abs 0x8862
    885e:	1a 93       	cmp	#1,	r10	;r3 As==01
    8860:	5f 28       	jnc	$+192    	;abs 0x8920
    8862:	0e 4b       	mov	r11,	r14	
    8864:	0f 4b       	mov	r11,	r15	
    8866:	8f 10       	swpb	r15		
    8868:	8f 11       	sxt	r15		
    886a:	8f 10       	swpb	r15		
    886c:	8f 11       	sxt	r15		
    886e:	7d 40 07 00 	mov.b	#7,	r13	;#0x0007
    8872:	0f 11       	rra	r15		
    8874:	0e 10       	rrc	r14		
    8876:	7d 53       	add.b	#-1,	r13	;r3 As==11
    8878:	fc 23       	jnz	$-6      	;abs 0x8872
    887a:	7e 50 82 ff 	add.b	#-126,	r14	;#0xff82
    887e:	7e f0 1f 00 	and.b	#31,	r14	;#0x001f
    8882:	04 43       	clr	r4		
    8884:	35 40 80 00 	mov	#128,	r5	;#0x0080
    8888:	4e 93       	tst.b	r14		
    888a:	04 24       	jz	$+10     	;abs 0x8894
    888c:	05 11       	rra	r5		
    888e:	04 10       	rrc	r4		
    8890:	7e 53       	add.b	#-1,	r14	;r3 As==11
    8892:	fa 3f       	jmp	$-10     	;abs 0x8888
    8894:	04 58       	add	r8,	r4	
    8896:	05 69       	addc	r9,	r5	
    8898:	0c 44       	mov	r4,	r12	
    889a:	0d 45       	mov	r5,	r13	
    889c:	3c f3       	and	#-1,	r12	;r3 As==11
    889e:	3d f0 ff 7f 	and	#32767,	r13	;#0x7fff
    88a2:	0e 4d       	mov	r13,	r14	
    88a4:	0f 4d       	mov	r13,	r15	
    88a6:	8f 10       	swpb	r15		
    88a8:	8f 11       	sxt	r15		
    88aa:	8f 10       	swpb	r15		
    88ac:	8f 11       	sxt	r15		
    88ae:	7d 40 07 00 	mov.b	#7,	r13	;#0x0007
    88b2:	0f 11       	rra	r15		
    88b4:	0e 10       	rrc	r14		
    88b6:	7d 53       	add.b	#-1,	r13	;r3 As==11
    88b8:	fc 23       	jnz	$-6      	;abs 0x88b2
    88ba:	0a 4e       	mov	r14,	r10	
    88bc:	0b 4f       	mov	r15,	r11	
    88be:	3a 50 81 ff 	add	#-127,	r10	;#0xff81
    88c2:	3b 63       	addc	#-1,	r11	;r3 As==11
    88c4:	4d 4a       	mov.b	r10,	r13	
    88c6:	7d f0 1f 00 	and.b	#31,	r13	;#0x001f
    88ca:	3e 43       	mov	#-1,	r14	;r3 As==11
    88cc:	3f 40 7f 00 	mov	#127,	r15	;#0x007f
    88d0:	4d 93       	tst.b	r13		
    88d2:	04 24       	jz	$+10     	;abs 0x88dc
    88d4:	0f 11       	rra	r15		
    88d6:	0e 10       	rrc	r14		
    88d8:	7d 53       	add.b	#-1,	r13	;r3 As==11
    88da:	fa 3f       	jmp	$-10     	;abs 0x88d0
    88dc:	0c 44       	mov	r4,	r12	
    88de:	0d 45       	mov	r5,	r13	
    88e0:	0c ce       	bic	r14,	r12	
    88e2:	0d cf       	bic	r15,	r13	
    88e4:	34 f3       	and	#-1,	r4	;r3 As==11
    88e6:	35 f0 7f 00 	and	#127,	r5	;#0x007f
    88ea:	3f 40 17 00 	mov	#23,	r15	;#0x0017
    88ee:	4f 8a       	sub.b	r10,	r15	
    88f0:	7f f0 1f 00 	and.b	#31,	r15	;#0x001f
    88f4:	04 d3       	bis	#0,	r4	;r3 As==00
    88f6:	35 d0 80 00 	bis	#128,	r5	;#0x0080
    88fa:	4f 93       	tst.b	r15		
    88fc:	04 24       	jz	$+10     	;abs 0x8906
    88fe:	05 11       	rra	r5		
    8900:	04 10       	rrc	r4		
    8902:	7f 53       	add.b	#-1,	r15	;r3 As==11
    8904:	fa 3f       	jmp	$-10     	;abs 0x88fa
    8906:	09 93       	tst	r9		
    8908:	04 34       	jge	$+10     	;abs 0x8912
    890a:	34 e3       	inv	r4		
    890c:	35 e3       	inv	r5		
    890e:	14 53       	inc	r4		
    8910:	05 63       	adc	r5		
    8912:	0e 46       	mov	r6,	r14	
    8914:	0f 47       	mov	r7,	r15	
    8916:	b0 12 a6 93 	call	#0x93a6	
    891a:	06 4e       	mov	r14,	r6	
    891c:	07 4f       	mov	r15,	r7	
    891e:	02 3c       	jmp	$+6      	;abs 0x8924
    8920:	04 43       	clr	r4		
    8922:	05 43       	clr	r5		
    8924:	0c 46       	mov	r6,	r12	
    8926:	0d 47       	mov	r7,	r13	
    8928:	1e 41 04 00 	mov	4(r1),	r14	;0x0004(r1)
    892c:	1f 41 06 00 	mov	6(r1),	r15	;0x0006(r1)
    8930:	b0 12 5a 93 	call	#0x935a	
    8934:	0a 4e       	mov	r14,	r10	
    8936:	0b 4f       	mov	r15,	r11	
    8938:	3a f0 00 f0 	and	#-4096,	r10	;#0xf000
    893c:	3b f3       	and	#-1,	r11	;r3 As==11
    893e:	3c 40 00 72 	mov	#29184,	r12	;#0x7200
    8942:	3d 40 31 3f 	mov	#16177,	r13	;#0x3f31
    8946:	0e 4a       	mov	r10,	r14	
    8948:	0f 4b       	mov	r11,	r15	
    894a:	b0 12 f6 93 	call	#0x93f6	
    894e:	08 4e       	mov	r14,	r8	
    8950:	09 4f       	mov	r15,	r9	
    8952:	0c 46       	mov	r6,	r12	
    8954:	0d 47       	mov	r7,	r13	
    8956:	0e 4a       	mov	r10,	r14	
    8958:	0f 4b       	mov	r11,	r15	
    895a:	b0 12 a6 93 	call	#0x93a6	
    895e:	0c 4e       	mov	r14,	r12	
    8960:	0d 4f       	mov	r15,	r13	
    8962:	1e 41 04 00 	mov	4(r1),	r14	;0x0004(r1)
    8966:	1f 41 06 00 	mov	6(r1),	r15	;0x0006(r1)
    896a:	b0 12 a6 93 	call	#0x93a6	
    896e:	3c 40 18 72 	mov	#29208,	r12	;#0x7218
    8972:	3d 40 31 3f 	mov	#16177,	r13	;#0x3f31
    8976:	b0 12 f6 93 	call	#0x93f6	
    897a:	06 4e       	mov	r14,	r6	
    897c:	07 4f       	mov	r15,	r7	
    897e:	3c 40 8c be 	mov	#-16756,r12	;#0xbe8c
    8982:	3d 40 bf 35 	mov	#13759,	r13	;#0x35bf
    8986:	0e 4a       	mov	r10,	r14	
    8988:	0f 4b       	mov	r11,	r15	
    898a:	b0 12 f6 93 	call	#0x93f6	
    898e:	0c 4e       	mov	r14,	r12	
    8990:	0d 4f       	mov	r15,	r13	
    8992:	0e 46       	mov	r6,	r14	
    8994:	0f 47       	mov	r7,	r15	
    8996:	b0 12 5a 93 	call	#0x935a	
    899a:	06 4e       	mov	r14,	r6	
    899c:	07 4f       	mov	r15,	r7	
    899e:	0c 4e       	mov	r14,	r12	
    89a0:	0d 4f       	mov	r15,	r13	
    89a2:	0e 48       	mov	r8,	r14	
    89a4:	0f 49       	mov	r9,	r15	
    89a6:	b0 12 5a 93 	call	#0x935a	
    89aa:	0a 4e       	mov	r14,	r10	
    89ac:	0b 4f       	mov	r15,	r11	
    89ae:	0c 48       	mov	r8,	r12	
    89b0:	0d 49       	mov	r9,	r13	
    89b2:	b0 12 a6 93 	call	#0x93a6	
    89b6:	0c 4e       	mov	r14,	r12	
    89b8:	0d 4f       	mov	r15,	r13	
    89ba:	0e 46       	mov	r6,	r14	
    89bc:	0f 47       	mov	r7,	r15	
    89be:	b0 12 a6 93 	call	#0x93a6	
    89c2:	06 4e       	mov	r14,	r6	
    89c4:	07 4f       	mov	r15,	r7	
    89c6:	0c 4a       	mov	r10,	r12	
    89c8:	0d 4b       	mov	r11,	r13	
    89ca:	0e 4a       	mov	r10,	r14	
    89cc:	0f 4b       	mov	r11,	r15	
    89ce:	b0 12 f6 93 	call	#0x93f6	
    89d2:	08 4e       	mov	r14,	r8	
    89d4:	09 4f       	mov	r15,	r9	
    89d6:	3c 40 4c bb 	mov	#-17588,r12	;#0xbb4c
    89da:	3d 40 31 33 	mov	#13105,	r13	;#0x3331
    89de:	b0 12 f6 93 	call	#0x93f6	
    89e2:	3c 40 0e ea 	mov	#-5618,	r12	;#0xea0e
    89e6:	3d 40 dd 35 	mov	#13789,	r13	;#0x35dd
    89ea:	b0 12 a6 93 	call	#0x93a6	
    89ee:	0c 4e       	mov	r14,	r12	
    89f0:	0d 4f       	mov	r15,	r13	
    89f2:	0e 48       	mov	r8,	r14	
    89f4:	0f 49       	mov	r9,	r15	
    89f6:	b0 12 f6 93 	call	#0x93f6	
    89fa:	3c 40 55 b3 	mov	#-19627,r12	;#0xb355
    89fe:	3d 40 8a 38 	mov	#14474,	r13	;#0x388a
    8a02:	b0 12 5a 93 	call	#0x935a	
    8a06:	0c 4e       	mov	r14,	r12	
    8a08:	0d 4f       	mov	r15,	r13	
    8a0a:	0e 48       	mov	r8,	r14	
    8a0c:	0f 49       	mov	r9,	r15	
    8a0e:	b0 12 f6 93 	call	#0x93f6	
    8a12:	3c 40 61 0b 	mov	#2913,	r12	;#0x0b61
    8a16:	3d 40 36 3b 	mov	#15158,	r13	;#0x3b36
    8a1a:	b0 12 a6 93 	call	#0x93a6	
    8a1e:	0c 4e       	mov	r14,	r12	
    8a20:	0d 4f       	mov	r15,	r13	
    8a22:	0e 48       	mov	r8,	r14	
    8a24:	0f 49       	mov	r9,	r15	
    8a26:	b0 12 f6 93 	call	#0x93f6	
    8a2a:	3c 40 ab aa 	mov	#-21845,r12	;#0xaaab
    8a2e:	3d 40 2a 3e 	mov	#15914,	r13	;#0x3e2a
    8a32:	b0 12 5a 93 	call	#0x935a	
    8a36:	0c 4e       	mov	r14,	r12	
    8a38:	0d 4f       	mov	r15,	r13	
    8a3a:	0e 48       	mov	r8,	r14	
    8a3c:	0f 49       	mov	r9,	r15	
    8a3e:	b0 12 f6 93 	call	#0x93f6	
    8a42:	0c 4e       	mov	r14,	r12	
    8a44:	0d 4f       	mov	r15,	r13	
    8a46:	0e 4a       	mov	r10,	r14	
    8a48:	0f 4b       	mov	r11,	r15	
    8a4a:	b0 12 a6 93 	call	#0x93a6	
    8a4e:	08 4e       	mov	r14,	r8	
    8a50:	09 4f       	mov	r15,	r9	
    8a52:	0c 4e       	mov	r14,	r12	
    8a54:	0d 4f       	mov	r15,	r13	
    8a56:	0e 4a       	mov	r10,	r14	
    8a58:	0f 4b       	mov	r11,	r15	
    8a5a:	b0 12 f6 93 	call	#0x93f6	
    8a5e:	81 4e 04 00 	mov	r14,	4(r1)	;0x0004(r1)
    8a62:	81 4f 06 00 	mov	r15,	6(r1)	;0x0006(r1)
    8a66:	0c 43       	clr	r12		
    8a68:	3d 40 00 40 	mov	#16384,	r13	;#0x4000
    8a6c:	0e 48       	mov	r8,	r14	
    8a6e:	0f 49       	mov	r9,	r15	
    8a70:	b0 12 a6 93 	call	#0x93a6	
    8a74:	0c 4e       	mov	r14,	r12	
    8a76:	0d 4f       	mov	r15,	r13	
    8a78:	1e 41 04 00 	mov	4(r1),	r14	;0x0004(r1)
    8a7c:	1f 41 06 00 	mov	6(r1),	r15	;0x0006(r1)
    8a80:	b0 12 06 96 	call	#0x9606	
    8a84:	08 4e       	mov	r14,	r8	
    8a86:	09 4f       	mov	r15,	r9	
    8a88:	0c 46       	mov	r6,	r12	
    8a8a:	0d 47       	mov	r7,	r13	
    8a8c:	0e 4a       	mov	r10,	r14	
    8a8e:	0f 4b       	mov	r11,	r15	
    8a90:	b0 12 f6 93 	call	#0x93f6	
    8a94:	0c 4e       	mov	r14,	r12	
    8a96:	0d 4f       	mov	r15,	r13	
    8a98:	0e 46       	mov	r6,	r14	
    8a9a:	0f 47       	mov	r7,	r15	
    8a9c:	b0 12 5a 93 	call	#0x935a	
    8aa0:	0c 4e       	mov	r14,	r12	
    8aa2:	0d 4f       	mov	r15,	r13	
    8aa4:	0e 48       	mov	r8,	r14	
    8aa6:	0f 49       	mov	r9,	r15	
    8aa8:	b0 12 a6 93 	call	#0x93a6	
    8aac:	0c 4a       	mov	r10,	r12	
    8aae:	0d 4b       	mov	r11,	r13	
    8ab0:	b0 12 a6 93 	call	#0x93a6	
    8ab4:	0c 4e       	mov	r14,	r12	
    8ab6:	0d 4f       	mov	r15,	r13	
    8ab8:	0e 43       	clr	r14		
    8aba:	3f 40 80 3f 	mov	#16256,	r15	;#0x3f80
    8abe:	b0 12 a6 93 	call	#0x93a6	
    8ac2:	0a 4e       	mov	r14,	r10	
    8ac4:	0b 4f       	mov	r15,	r11	
    8ac6:	0c 43       	clr	r12		
    8ac8:	0d 43       	clr	r13		
    8aca:	0d 44       	mov	r4,	r13	
    8acc:	79 40 07 00 	mov.b	#7,	r9	;#0x0007
    8ad0:	0c 5c       	rla	r12		
    8ad2:	0d 6d       	rlc	r13		
    8ad4:	79 53       	add.b	#-1,	r9	;r3 As==11
    8ad6:	fc 23       	jnz	$-6      	;abs 0x8ad0
    8ad8:	0c 5a       	add	r10,	r12	
    8ada:	0d 6b       	addc	r11,	r13	
    8adc:	0a 4d       	mov	r13,	r10	
    8ade:	0b 4d       	mov	r13,	r11	
    8ae0:	8b 10       	swpb	r11		
    8ae2:	8b 11       	sxt	r11		
    8ae4:	8b 10       	swpb	r11		
    8ae6:	8b 11       	sxt	r11		
    8ae8:	79 40 07 00 	mov.b	#7,	r9	;#0x0007
    8aec:	0b 11       	rra	r11		
    8aee:	0a 10       	rrc	r10		
    8af0:	79 53       	add.b	#-1,	r9	;r3 As==11
    8af2:	fc 23       	jnz	$-6      	;abs 0x8aec
    8af4:	0b 93       	tst	r11		
    8af6:	04 38       	jl	$+10     	;abs 0x8b00
    8af8:	1b 93       	cmp	#1,	r11	;r3 As==01
    8afa:	07 34       	jge	$+16     	;abs 0x8b0a
    8afc:	1a 93       	cmp	#1,	r10	;r3 As==01
    8afe:	05 2c       	jc	$+12     	;abs 0x8b0a
    8b00:	0d 44       	mov	r4,	r13	
    8b02:	b0 12 4e 8b 	call	#0x8b4e	
    8b06:	0c 4e       	mov	r14,	r12	
    8b08:	0d 4f       	mov	r15,	r13	
    8b0a:	2e 41       	mov	@r1,	r14	
    8b0c:	1f 41 02 00 	mov	2(r1),	r15	;0x0002(r1)
    8b10:	b0 12 f6 93 	call	#0x93f6	
    8b14:	04 4e       	mov	r14,	r4	
    8b16:	05 4f       	mov	r15,	r5	
    8b18:	0a 3c       	jmp	$+22     	;abs 0x8b2e
    8b1a:	04 43       	clr	r4		
    8b1c:	35 40 80 3f 	mov	#16256,	r5	;#0x3f80
    8b20:	06 3c       	jmp	$+14     	;abs 0x8b2e
    8b22:	81 43 04 00 	mov	#0,	4(r1)	;r3 As==00, 0x0004(r1)
    8b26:	81 43 06 00 	mov	#0,	6(r1)	;r3 As==00, 0x0006(r1)
    8b2a:	30 40 7a 80 	br	#0x807a	
    8b2e:	0e 44       	mov	r4,	r14	
    8b30:	0f 45       	mov	r5,	r15	
    8b32:	31 50 24 00 	add	#36,	r1	;#0x0024
    8b36:	34 41       	pop	r4		
    8b38:	35 41       	pop	r5		
    8b3a:	36 41       	pop	r6		
    8b3c:	37 41       	pop	r7		
    8b3e:	38 41       	pop	r8		
    8b40:	39 41       	pop	r9		
    8b42:	3a 41       	pop	r10		
    8b44:	3b 41       	pop	r11		
    8b46:	30 41       	ret			

00008b48 <powf>:
    8b48:	b0 12 fe 7e 	call	#0x7efe	
    8b4c:	30 41       	ret			

00008b4e <scalbnf>:
    8b4e:	0b 12       	push	r11		
    8b50:	0a 12       	push	r10		
    8b52:	09 12       	push	r9		
    8b54:	08 12       	push	r8		
    8b56:	07 12       	push	r7		
    8b58:	0a 4f       	mov	r15,	r10	
    8b5a:	0b 4d       	mov	r13,	r11	
    8b5c:	08 4e       	mov	r14,	r8	
    8b5e:	09 4f       	mov	r15,	r9	
    8b60:	0c 48       	mov	r8,	r12	
    8b62:	0d 49       	mov	r9,	r13	
    8b64:	3c f3       	and	#-1,	r12	;r3 As==11
    8b66:	3d f0 ff 7f 	and	#32767,	r13	;#0x7fff
    8b6a:	0c 93       	tst	r12		
    8b6c:	02 20       	jnz	$+6      	;abs 0x8b72
    8b6e:	0d 93       	tst	r13		
    8b70:	a1 24       	jz	$+324    	;abs 0x8cb4
    8b72:	3d 90 80 7f 	cmp	#32640,	r13	;#0x7f80
    8b76:	06 28       	jnc	$+14     	;abs 0x8b84
    8b78:	0f 4a       	mov	r10,	r15	
    8b7a:	0c 4e       	mov	r14,	r12	
    8b7c:	0d 4a       	mov	r10,	r13	
    8b7e:	b0 12 5a 93 	call	#0x935a	
    8b82:	97 3c       	jmp	$+304    	;abs 0x8cb2
    8b84:	3d 90 80 00 	cmp	#128,	r13	;#0x0080
    8b88:	0c 28       	jnc	$+26     	;abs 0x8ba2
    8b8a:	0e 48       	mov	r8,	r14	
    8b8c:	0f 49       	mov	r9,	r15	
    8b8e:	0c 4d       	mov	r13,	r12	
    8b90:	0d 43       	clr	r13		
    8b92:	79 40 07 00 	mov.b	#7,	r9	;#0x0007
    8b96:	12 c3       	clrc			
    8b98:	0d 10       	rrc	r13		
    8b9a:	0c 10       	rrc	r12		
    8b9c:	79 53       	add.b	#-1,	r9	;r3 As==11
    8b9e:	fb 23       	jnz	$-8      	;abs 0x8b96
    8ba0:	1b 3c       	jmp	$+56     	;abs 0x8bd8
    8ba2:	0c 43       	clr	r12		
    8ba4:	3d 40 00 4c 	mov	#19456,	r13	;#0x4c00
    8ba8:	0f 4a       	mov	r10,	r15	
    8baa:	b0 12 f6 93 	call	#0x93f6	
    8bae:	0a 4f       	mov	r15,	r10	
    8bb0:	08 4e       	mov	r14,	r8	
    8bb2:	09 4f       	mov	r15,	r9	
    8bb4:	08 f3       	and	#0,	r8	;r3 As==00
    8bb6:	39 f0 80 7f 	and	#32640,	r9	;#0x7f80
    8bba:	0c 49       	mov	r9,	r12	
    8bbc:	0d 49       	mov	r9,	r13	
    8bbe:	8d 10       	swpb	r13		
    8bc0:	8d 11       	sxt	r13		
    8bc2:	8d 10       	swpb	r13		
    8bc4:	8d 11       	sxt	r13		
    8bc6:	79 40 07 00 	mov.b	#7,	r9	;#0x0007
    8bca:	0d 11       	rra	r13		
    8bcc:	0c 10       	rrc	r12		
    8bce:	79 53       	add.b	#-1,	r9	;r3 As==11
    8bd0:	fc 23       	jnz	$-6      	;abs 0x8bca
    8bd2:	3c 50 e7 ff 	add	#-25,	r12	;#0xffe7
    8bd6:	3d 63       	addc	#-1,	r13	;r3 As==11
    8bd8:	08 4b       	mov	r11,	r8	
    8bda:	07 4b       	mov	r11,	r7	
    8bdc:	87 10       	swpb	r7		
    8bde:	87 11       	sxt	r7		
    8be0:	87 10       	swpb	r7		
    8be2:	87 11       	sxt	r7		
    8be4:	09 47       	mov	r7,	r9	
    8be6:	0c 58       	add	r8,	r12	
    8be8:	0d 69       	addc	r9,	r13	
    8bea:	0d 93       	tst	r13		
    8bec:	0b 38       	jl	$+24     	;abs 0x8c04
    8bee:	03 20       	jnz	$+8      	;abs 0x8bf6
    8bf0:	3c 90 ff 00 	cmp	#255,	r12	;#0x00ff
    8bf4:	07 28       	jnc	$+16     	;abs 0x8c04
    8bf6:	3e 40 ca f2 	mov	#-3382,	r14	;#0xf2ca
    8bfa:	3f 40 49 71 	mov	#29001,	r15	;#0x7149
    8bfe:	0a 93       	tst	r10		
    8c00:	2f 34       	jge	$+96     	;abs 0x8c60
    8c02:	2a 3c       	jmp	$+86     	;abs 0x8c58
    8c04:	0d 93       	tst	r13		
    8c06:	16 38       	jl	$+46     	;abs 0x8c34
    8c08:	02 20       	jnz	$+6      	;abs 0x8c0e
    8c0a:	1c 93       	cmp	#1,	r12	;r3 As==01
    8c0c:	13 28       	jnc	$+40     	;abs 0x8c34
    8c0e:	0a 43       	clr	r10		
    8c10:	0b 43       	clr	r11		
    8c12:	0b 4c       	mov	r12,	r11	
    8c14:	7d 40 07 00 	mov.b	#7,	r13	;#0x0007
    8c18:	0a 5a       	rla	r10		
    8c1a:	0b 6b       	rlc	r11		
    8c1c:	7d 53       	add.b	#-1,	r13	;r3 As==11
    8c1e:	fc 23       	jnz	$-6      	;abs 0x8c18
    8c20:	0c 4e       	mov	r14,	r12	
    8c22:	0d 4f       	mov	r15,	r13	
    8c24:	3c f3       	and	#-1,	r12	;r3 As==11
    8c26:	3d f0 7f 80 	and	#-32641,r13	;#0x807f
    8c2a:	0c da       	bis	r10,	r12	
    8c2c:	0d db       	bis	r11,	r13	
    8c2e:	0e 4c       	mov	r12,	r14	
    8c30:	0a 4d       	mov	r13,	r10	
    8c32:	40 3c       	jmp	$+130    	;abs 0x8cb4
    8c34:	3d 93       	cmp	#-1,	r13	;r3 As==11
    8c36:	05 38       	jl	$+12     	;abs 0x8c42
    8c38:	0d 93       	tst	r13		
    8c3a:	26 34       	jge	$+78     	;abs 0x8c88
    8c3c:	3c 90 ea ff 	cmp	#-22,	r12	;#0xffea
    8c40:	23 2c       	jc	$+72     	;abs 0x8c88
    8c42:	3a f0 00 80 	and	#-32768,r10	;#0x8000
    8c46:	3b 90 31 75 	cmp	#30001,	r11	;#0x7531
    8c4a:	0f 38       	jl	$+32     	;abs 0x8c6a
    8c4c:	3e 40 ca f2 	mov	#-3382,	r14	;#0xf2ca
    8c50:	3f 40 49 71 	mov	#29001,	r15	;#0x7149
    8c54:	0a 93       	tst	r10		
    8c56:	04 24       	jz	$+10     	;abs 0x8c60
    8c58:	3e 40 ca f2 	mov	#-3382,	r14	;#0xf2ca
    8c5c:	3f 40 49 f1 	mov	#-3767,	r15	;#0xf149
    8c60:	3c 40 ca f2 	mov	#-3382,	r12	;#0xf2ca
    8c64:	3d 40 49 71 	mov	#29001,	r13	;#0x7149
    8c68:	22 3c       	jmp	$+70     	;abs 0x8cae
    8c6a:	3e 40 60 42 	mov	#16992,	r14	;#0x4260
    8c6e:	3f 40 a2 0d 	mov	#3490,	r15	;#0x0da2
    8c72:	0a 93       	tst	r10		
    8c74:	04 24       	jz	$+10     	;abs 0x8c7e
    8c76:	3e 40 60 42 	mov	#16992,	r14	;#0x4260
    8c7a:	3f 40 a2 8d 	mov	#-29278,r15	;#0x8da2
    8c7e:	3c 40 60 42 	mov	#16992,	r12	;#0x4260
    8c82:	3d 40 a2 0d 	mov	#3490,	r13	;#0x0da2
    8c86:	13 3c       	jmp	$+40     	;abs 0x8cae
    8c88:	0a 43       	clr	r10		
    8c8a:	0b 43       	clr	r11		
    8c8c:	0b 4c       	mov	r12,	r11	
    8c8e:	3b 50 19 00 	add	#25,	r11	;#0x0019
    8c92:	7d 40 07 00 	mov.b	#7,	r13	;#0x0007
    8c96:	0a 5a       	rla	r10		
    8c98:	0b 6b       	rlc	r11		
    8c9a:	7d 53       	add.b	#-1,	r13	;r3 As==11
    8c9c:	fc 23       	jnz	$-6      	;abs 0x8c96
    8c9e:	3e f3       	and	#-1,	r14	;r3 As==11
    8ca0:	3f f0 7f 80 	and	#-32641,r15	;#0x807f
    8ca4:	0e da       	bis	r10,	r14	
    8ca6:	0f db       	bis	r11,	r15	
    8ca8:	0c 43       	clr	r12		
    8caa:	3d 40 00 33 	mov	#13056,	r13	;#0x3300
    8cae:	b0 12 f6 93 	call	#0x93f6	
    8cb2:	0a 4f       	mov	r15,	r10	
    8cb4:	0f 4a       	mov	r10,	r15	
    8cb6:	37 41       	pop	r7		
    8cb8:	38 41       	pop	r8		
    8cba:	39 41       	pop	r9		
    8cbc:	3a 41       	pop	r10		
    8cbe:	3b 41       	pop	r11		
    8cc0:	30 41       	ret			

00008cc2 <__ieee754_sqrtf>:
    8cc2:	0b 12       	push	r11		
    8cc4:	0a 12       	push	r10		
    8cc6:	09 12       	push	r9		
    8cc8:	08 12       	push	r8		
    8cca:	07 12       	push	r7		
    8ccc:	06 12       	push	r6		
    8cce:	05 12       	push	r5		
    8cd0:	04 12       	push	r4		
    8cd2:	21 83       	decd	r1		
    8cd4:	0a 4e       	mov	r14,	r10	
    8cd6:	0b 4f       	mov	r15,	r11	
    8cd8:	0c 4e       	mov	r14,	r12	
    8cda:	0d 4f       	mov	r15,	r13	
    8cdc:	06 4e       	mov	r14,	r6	
    8cde:	07 4f       	mov	r15,	r7	
    8ce0:	36 f3       	and	#-1,	r6	;r3 As==11
    8ce2:	37 f0 ff 7f 	and	#32767,	r7	;#0x7fff
    8ce6:	37 90 80 7f 	cmp	#32640,	r7	;#0x7f80
    8cea:	0b 28       	jnc	$+24     	;abs 0x8d02
    8cec:	0c 4e       	mov	r14,	r12	
    8cee:	0d 4f       	mov	r15,	r13	
    8cf0:	b0 12 f6 93 	call	#0x93f6	
    8cf4:	0c 4e       	mov	r14,	r12	
    8cf6:	0d 4f       	mov	r15,	r13	
    8cf8:	0e 4a       	mov	r10,	r14	
    8cfa:	0f 4b       	mov	r11,	r15	
    8cfc:	b0 12 5a 93 	call	#0x935a	
    8d00:	19 3c       	jmp	$+52     	;abs 0x8d34
    8d02:	06 93       	tst	r6		
    8d04:	02 20       	jnz	$+6      	;abs 0x8d0a
    8d06:	07 93       	tst	r7		
    8d08:	89 24       	jz	$+276    	;abs 0x8e1c
    8d0a:	0d 93       	tst	r13		
    8d0c:	09 38       	jl	$+20     	;abs 0x8d20
    8d0e:	08 4d       	mov	r13,	r8	
    8d10:	09 4d       	mov	r13,	r9	
    8d12:	89 10       	swpb	r9		
    8d14:	89 11       	sxt	r9		
    8d16:	89 10       	swpb	r9		
    8d18:	89 11       	sxt	r9		
    8d1a:	7f 40 07 00 	mov.b	#7,	r15	;#0x0007
    8d1e:	0d 3c       	jmp	$+28     	;abs 0x8d3a
    8d20:	0c 4a       	mov	r10,	r12	
    8d22:	0d 4b       	mov	r11,	r13	
    8d24:	0e 4a       	mov	r10,	r14	
    8d26:	0f 4b       	mov	r11,	r15	
    8d28:	b0 12 a6 93 	call	#0x93a6	
    8d2c:	0c 4e       	mov	r14,	r12	
    8d2e:	0d 4f       	mov	r15,	r13	
    8d30:	b0 12 06 96 	call	#0x9606	
    8d34:	0a 4e       	mov	r14,	r10	
    8d36:	0b 4f       	mov	r15,	r11	
    8d38:	71 3c       	jmp	$+228    	;abs 0x8e1c
    8d3a:	09 11       	rra	r9		
    8d3c:	08 10       	rrc	r8		
    8d3e:	7f 53       	add.b	#-1,	r15	;r3 As==11
    8d40:	fc 23       	jnz	$-6      	;abs 0x8d3a
    8d42:	37 90 80 00 	cmp	#128,	r7	;#0x0080
    8d46:	14 2c       	jc	$+42     	;abs 0x8d70
    8d48:	0e 43       	clr	r14		
    8d4a:	0f 43       	clr	r15		
    8d4c:	04 3c       	jmp	$+10     	;abs 0x8d56
    8d4e:	0c 5c       	rla	r12		
    8d50:	0d 6d       	rlc	r13		
    8d52:	1e 53       	inc	r14		
    8d54:	0f 63       	adc	r15		
    8d56:	0a 4c       	mov	r12,	r10	
    8d58:	0b 4d       	mov	r13,	r11	
    8d5a:	0a f3       	and	#0,	r10	;r3 As==00
    8d5c:	3b f0 80 00 	and	#128,	r11	;#0x0080
    8d60:	0a 93       	tst	r10		
    8d62:	02 20       	jnz	$+6      	;abs 0x8d68
    8d64:	0b 93       	tst	r11		
    8d66:	f3 27       	jz	$-24     	;abs 0x8d4e
    8d68:	08 8e       	sub	r14,	r8	
    8d6a:	09 7f       	subc	r15,	r9	
    8d6c:	18 53       	inc	r8		
    8d6e:	09 63       	adc	r9		
    8d70:	38 50 81 ff 	add	#-127,	r8	;#0xff81
    8d74:	39 63       	addc	#-1,	r9	;r3 As==11
    8d76:	3c f3       	and	#-1,	r12	;r3 As==11
    8d78:	3d f0 7f 00 	and	#127,	r13	;#0x007f
    8d7c:	0c d3       	bis	#0,	r12	;r3 As==00
    8d7e:	3d d0 80 00 	bis	#128,	r13	;#0x0080
    8d82:	0e 48       	mov	r8,	r14	
    8d84:	0f 49       	mov	r9,	r15	
    8d86:	1e f3       	and	#1,	r14	;r3 As==01
    8d88:	0f f3       	and	#0,	r15	;r3 As==00
    8d8a:	0e 93       	tst	r14		
    8d8c:	02 20       	jnz	$+6      	;abs 0x8d92
    8d8e:	0f 93       	tst	r15		
    8d90:	02 24       	jz	$+6      	;abs 0x8d96
    8d92:	0c 5c       	rla	r12		
    8d94:	0d 6d       	rlc	r13		
    8d96:	09 11       	rra	r9		
    8d98:	08 10       	rrc	r8		
    8d9a:	0c 5c       	rla	r12		
    8d9c:	0d 6d       	rlc	r13		
    8d9e:	b1 40 19 00 	mov	#25,	0(r1)	;#0x0019, 0x0000(r1)
    8da2:	00 00 
    8da4:	0e 43       	clr	r14		
    8da6:	0f 43       	clr	r15		
    8da8:	04 43       	clr	r4		
    8daa:	05 43       	clr	r5		
    8dac:	0a 43       	clr	r10		
    8dae:	3b 40 00 01 	mov	#256,	r11	;#0x0100
    8db2:	06 44       	mov	r4,	r6	
    8db4:	07 45       	mov	r5,	r7	
    8db6:	06 5a       	add	r10,	r6	
    8db8:	07 6b       	addc	r11,	r7	
    8dba:	0d 97       	cmp	r7,	r13	
    8dbc:	0b 38       	jl	$+24     	;abs 0x8dd4
    8dbe:	02 20       	jnz	$+6      	;abs 0x8dc4
    8dc0:	0c 96       	cmp	r6,	r12	
    8dc2:	08 28       	jnc	$+18     	;abs 0x8dd4
    8dc4:	04 46       	mov	r6,	r4	
    8dc6:	05 47       	mov	r7,	r5	
    8dc8:	04 5a       	add	r10,	r4	
    8dca:	05 6b       	addc	r11,	r5	
    8dcc:	0c 86       	sub	r6,	r12	
    8dce:	0d 77       	subc	r7,	r13	
    8dd0:	0e 5a       	add	r10,	r14	
    8dd2:	0f 6b       	addc	r11,	r15	
    8dd4:	0c 5c       	rla	r12		
    8dd6:	0d 6d       	rlc	r13		
    8dd8:	12 c3       	clrc			
    8dda:	0b 10       	rrc	r11		
    8ddc:	0a 10       	rrc	r10		
    8dde:	b1 53 00 00 	add	#-1,	0(r1)	;r3 As==11, 0x0000(r1)
    8de2:	e7 23       	jnz	$-48     	;abs 0x8db2
    8de4:	0c 93       	tst	r12		
    8de6:	02 20       	jnz	$+6      	;abs 0x8dec
    8de8:	0d 93       	tst	r13		
    8dea:	06 24       	jz	$+14     	;abs 0x8df8
    8dec:	0c 4e       	mov	r14,	r12	
    8dee:	0d 4f       	mov	r15,	r13	
    8df0:	1c f3       	and	#1,	r12	;r3 As==01
    8df2:	0d f3       	and	#0,	r13	;r3 As==00
    8df4:	0e 5c       	add	r12,	r14	
    8df6:	0f 6d       	addc	r13,	r15	
    8df8:	0f 11       	rra	r15		
    8dfa:	0e 10       	rrc	r14		
    8dfc:	0e 53       	add	#0,	r14	;r3 As==00
    8dfe:	3f 60 00 3f 	addc	#16128,	r15	;#0x3f00
    8e02:	0c 43       	clr	r12		
    8e04:	0d 43       	clr	r13		
    8e06:	0d 48       	mov	r8,	r13	
    8e08:	7b 40 07 00 	mov.b	#7,	r11	;#0x0007
    8e0c:	0c 5c       	rla	r12		
    8e0e:	0d 6d       	rlc	r13		
    8e10:	7b 53       	add.b	#-1,	r11	;r3 As==11
    8e12:	fc 23       	jnz	$-6      	;abs 0x8e0c
    8e14:	0a 4e       	mov	r14,	r10	
    8e16:	0b 4f       	mov	r15,	r11	
    8e18:	0a 5c       	add	r12,	r10	
    8e1a:	0b 6d       	addc	r13,	r11	
    8e1c:	0e 4a       	mov	r10,	r14	
    8e1e:	0f 4b       	mov	r11,	r15	
    8e20:	21 53       	incd	r1		
    8e22:	34 41       	pop	r4		
    8e24:	35 41       	pop	r5		
    8e26:	36 41       	pop	r6		
    8e28:	37 41       	pop	r7		
    8e2a:	38 41       	pop	r8		
    8e2c:	39 41       	pop	r9		
    8e2e:	3a 41       	pop	r10		
    8e30:	3b 41       	pop	r11		
    8e32:	30 41       	ret			

00008e34 <__fixunssfsi>:
    8e34:	0b 12       	push	r11		
    8e36:	0a 12       	push	r10		
    8e38:	0a 4e       	mov	r14,	r10	
    8e3a:	0b 4f       	mov	r15,	r11	
    8e3c:	0c 43       	clr	r12		
    8e3e:	3d 40 00 4f 	mov	#20224,	r13	;#0x4f00
    8e42:	b0 12 9c 97 	call	#0x979c	
    8e46:	0f 93       	tst	r15		
    8e48:	07 34       	jge	$+16     	;abs 0x8e58
    8e4a:	0e 4a       	mov	r10,	r14	
    8e4c:	0f 4b       	mov	r11,	r15	
    8e4e:	b0 12 2e 99 	call	#0x992e	
    8e52:	3a 41       	pop	r10		
    8e54:	3b 41       	pop	r11		
    8e56:	30 41       	ret			
    8e58:	0c 43       	clr	r12		
    8e5a:	3d 40 00 4f 	mov	#20224,	r13	;#0x4f00
    8e5e:	0e 4a       	mov	r10,	r14	
    8e60:	0f 4b       	mov	r11,	r15	
    8e62:	b0 12 a6 93 	call	#0x93a6	
    8e66:	b0 12 2e 99 	call	#0x992e	
    8e6a:	0e 53       	add	#0,	r14	;r3 As==00
    8e6c:	3f 60 00 80 	addc	#-32768,r15	;#0x8000
    8e70:	3a 41       	pop	r10		
    8e72:	3b 41       	pop	r11		
    8e74:	30 41       	ret			

00008e76 <__fixunssfdi>:
    8e76:	0b 12       	push	r11		
    8e78:	0a 12       	push	r10		
    8e7a:	09 12       	push	r9		
    8e7c:	08 12       	push	r8		
    8e7e:	07 12       	push	r7		
    8e80:	06 12       	push	r6		
    8e82:	05 12       	push	r5		
    8e84:	04 12       	push	r4		
    8e86:	21 83       	decd	r1		
    8e88:	0a 4e       	mov	r14,	r10	
    8e8a:	0b 4f       	mov	r15,	r11	
    8e8c:	0c 43       	clr	r12		
    8e8e:	3d 40 80 3f 	mov	#16256,	r13	;#0x3f80
    8e92:	b0 12 ea 97 	call	#0x97ea	
    8e96:	0f 93       	tst	r15		
    8e98:	2d 38       	jl	$+92     	;abs 0x8ef4
    8e9a:	0c 43       	clr	r12		
    8e9c:	3d 40 80 4f 	mov	#20352,	r13	;#0x4f80
    8ea0:	0e 4a       	mov	r10,	r14	
    8ea2:	0f 4b       	mov	r11,	r15	
    8ea4:	b0 12 ea 97 	call	#0x97ea	
    8ea8:	0f 93       	tst	r15		
    8eaa:	1b 38       	jl	$+56     	;abs 0x8ee2
    8eac:	0c 43       	clr	r12		
    8eae:	3d 40 80 5f 	mov	#24448,	r13	;#0x5f80
    8eb2:	0e 4a       	mov	r10,	r14	
    8eb4:	0f 4b       	mov	r11,	r15	
    8eb6:	b0 12 ea 97 	call	#0x97ea	
    8eba:	0f 93       	tst	r15		
    8ebc:	20 38       	jl	$+66     	;abs 0x8efe
    8ebe:	38 43       	mov	#-1,	r8	;r3 As==11
    8ec0:	39 43       	mov	#-1,	r9	;r3 As==11
    8ec2:	3a 43       	mov	#-1,	r10	;r3 As==11
    8ec4:	3b 43       	mov	#-1,	r11	;r3 As==11
    8ec6:	0c 48       	mov	r8,	r12	
    8ec8:	0d 49       	mov	r9,	r13	
    8eca:	0e 4a       	mov	r10,	r14	
    8ecc:	0f 4b       	mov	r11,	r15	
    8ece:	21 53       	incd	r1		
    8ed0:	34 41       	pop	r4		
    8ed2:	35 41       	pop	r5		
    8ed4:	36 41       	pop	r6		
    8ed6:	37 41       	pop	r7		
    8ed8:	38 41       	pop	r8		
    8eda:	39 41       	pop	r9		
    8edc:	3a 41       	pop	r10		
    8ede:	3b 41       	pop	r11		
    8ee0:	30 41       	ret			
    8ee2:	0e 4a       	mov	r10,	r14	
    8ee4:	0f 4b       	mov	r11,	r15	
    8ee6:	b0 12 34 8e 	call	#0x8e34	
    8eea:	08 4e       	mov	r14,	r8	
    8eec:	09 4f       	mov	r15,	r9	
    8eee:	0a 43       	clr	r10		
    8ef0:	0b 43       	clr	r11		
    8ef2:	e9 3f       	jmp	$-44     	;abs 0x8ec6
    8ef4:	08 43       	clr	r8		
    8ef6:	09 43       	clr	r9		
    8ef8:	0a 43       	clr	r10		
    8efa:	0b 43       	clr	r11		
    8efc:	e4 3f       	jmp	$-54     	;abs 0x8ec6
    8efe:	0c 43       	clr	r12		
    8f00:	3d 40 80 2f 	mov	#12160,	r13	;#0x2f80
    8f04:	0e 4a       	mov	r10,	r14	
    8f06:	0f 4b       	mov	r11,	r15	
    8f08:	b0 12 f6 93 	call	#0x93f6	
    8f0c:	08 4e       	mov	r14,	r8	
    8f0e:	09 4f       	mov	r15,	r9	
    8f10:	b1 40 05 00 	mov	#5,	0(r1)	;#0x0005, 0x0000(r1)
    8f14:	00 00 
    8f16:	3a 40 10 00 	mov	#16,	r10	;#0x0010
    8f1a:	0b 43       	clr	r11		
    8f1c:	04 43       	clr	r4		
    8f1e:	05 43       	clr	r5		
    8f20:	4d 4a       	mov.b	r10,	r13	
    8f22:	7d f0 1f 00 	and.b	#31,	r13	;#0x001f
    8f26:	1e 43       	mov	#1,	r14	;r3 As==01
    8f28:	0f 43       	clr	r15		
    8f2a:	04 24       	jz	$+10     	;abs 0x8f34
    8f2c:	0e 5e       	rla	r14		
    8f2e:	0f 6f       	rlc	r15		
    8f30:	7d 53       	add.b	#-1,	r13	;r3 As==11
    8f32:	fc 23       	jnz	$-6      	;abs 0x8f2c
    8f34:	b0 12 ba 99 	call	#0x99ba	
    8f38:	06 4e       	mov	r14,	r6	
    8f3a:	07 4f       	mov	r15,	r7	
    8f3c:	0c 48       	mov	r8,	r12	
    8f3e:	0d 49       	mov	r9,	r13	
    8f40:	b0 12 38 98 	call	#0x9838	
    8f44:	0f 93       	tst	r15		
    8f46:	01 24       	jz	$+4      	;abs 0x8f4a
    8f48:	0a 34       	jge	$+22     	;abs 0x8f5e
    8f4a:	04 da       	bis	r10,	r4	
    8f4c:	05 db       	bis	r11,	r5	
    8f4e:	0c 46       	mov	r6,	r12	
    8f50:	0d 47       	mov	r7,	r13	
    8f52:	0e 48       	mov	r8,	r14	
    8f54:	0f 49       	mov	r9,	r15	
    8f56:	b0 12 06 96 	call	#0x9606	
    8f5a:	08 4e       	mov	r14,	r8	
    8f5c:	09 4f       	mov	r15,	r9	
    8f5e:	12 c3       	clrc			
    8f60:	0b 10       	rrc	r11		
    8f62:	0a 10       	rrc	r10		
    8f64:	b1 53 00 00 	add	#-1,	0(r1)	;r3 As==11, 0x0000(r1)
    8f68:	db 23       	jnz	$-72     	;abs 0x8f20
    8f6a:	0c 43       	clr	r12		
    8f6c:	3d 40 80 4f 	mov	#20352,	r13	;#0x4f80
    8f70:	0e 48       	mov	r8,	r14	
    8f72:	0f 49       	mov	r9,	r15	
    8f74:	b0 12 f6 93 	call	#0x93f6	
    8f78:	b0 12 34 8e 	call	#0x8e34	
    8f7c:	4d 44       	mov.b	r4,	r13	
    8f7e:	7d f0 3f 00 	and.b	#63,	r13	;#0x003f
    8f82:	08 4e       	mov	r14,	r8	
    8f84:	09 4f       	mov	r15,	r9	
    8f86:	0a 43       	clr	r10		
    8f88:	0b 43       	clr	r11		
    8f8a:	9d 27       	jz	$-196    	;abs 0x8ec6
    8f8c:	08 58       	rla	r8		
    8f8e:	09 69       	rlc	r9		
    8f90:	0a 6a       	rlc	r10		
    8f92:	0b 6b       	rlc	r11		
    8f94:	7d 53       	add.b	#-1,	r13	;r3 As==11
    8f96:	fa 23       	jnz	$-10     	;abs 0x8f8c
    8f98:	96 3f       	jmp	$-210    	;abs 0x8ec6

00008f9a <__floatundisf>:
    8f9a:	0b 12       	push	r11		
    8f9c:	0a 12       	push	r10		
    8f9e:	09 12       	push	r9		
    8fa0:	08 12       	push	r8		
    8fa2:	07 12       	push	r7		
    8fa4:	06 12       	push	r6		
    8fa6:	05 12       	push	r5		
    8fa8:	04 12       	push	r4		
    8faa:	04 4c       	mov	r12,	r4	
    8fac:	05 4d       	mov	r13,	r5	
    8fae:	06 4e       	mov	r14,	r6	
    8fb0:	07 4f       	mov	r15,	r7	
    8fb2:	3c f3       	and	#-1,	r12	;r3 As==11
    8fb4:	3d f3       	and	#-1,	r13	;r3 As==11
    8fb6:	0e f3       	and	#0,	r14	;r3 As==00
    8fb8:	0f f3       	and	#0,	r15	;r3 As==00
    8fba:	0c 94       	cmp	r4,	r12	
    8fbc:	62 24       	jz	$+198    	;abs 0x9082
    8fbe:	0c 47       	mov	r7,	r12	
    8fc0:	0b 46       	mov	r6,	r11	
    8fc2:	17 93       	cmp	#1,	r7	;r3 As==01
    8fc4:	75 28       	jnc	$+236    	;abs 0x90b0
    8fc6:	37 90 00 01 	cmp	#256,	r7	;#0x0100
    8fca:	6c 2c       	jc	$+218    	;abs 0x90a4
    8fcc:	3d 40 10 00 	mov	#16,	r13	;#0x0010
    8fd0:	38 40 10 00 	mov	#16,	r8	;#0x0010
    8fd4:	09 43       	clr	r9		
    8fd6:	4d 4d       	mov.b	r13,	r13	
    8fd8:	0e 4b       	mov	r11,	r14	
    8fda:	0f 4c       	mov	r12,	r15	
    8fdc:	4d 93       	tst.b	r13		
    8fde:	05 24       	jz	$+12     	;abs 0x8fea
    8fe0:	12 c3       	clrc			
    8fe2:	0f 10       	rrc	r15		
    8fe4:	0e 10       	rrc	r14		
    8fe6:	7d 53       	add.b	#-1,	r13	;r3 As==11
    8fe8:	fb 23       	jnz	$-8      	;abs 0x8fe0
    8fea:	3e 50 cc b0 	add	#-20276,r14	;#0xb0cc
    8fee:	6a 4e       	mov.b	@r14,	r10	
    8ff0:	0b 43       	clr	r11		
    8ff2:	0a 58       	add	r8,	r10	
    8ff4:	0b 69       	addc	r9,	r11	
    8ff6:	08 4a       	mov	r10,	r8	
    8ff8:	49 4a       	mov.b	r10,	r9	
    8ffa:	79 f0 3f 00 	and.b	#63,	r9	;#0x003f
    8ffe:	0c 44       	mov	r4,	r12	
    9000:	0d 45       	mov	r5,	r13	
    9002:	0e 46       	mov	r6,	r14	
    9004:	0f 47       	mov	r7,	r15	
    9006:	07 24       	jz	$+16     	;abs 0x9016
    9008:	12 c3       	clrc			
    900a:	0f 10       	rrc	r15		
    900c:	0e 10       	rrc	r14		
    900e:	0d 10       	rrc	r13		
    9010:	0c 10       	rrc	r12		
    9012:	79 53       	add.b	#-1,	r9	;r3 As==11
    9014:	f9 23       	jnz	$-12     	;abs 0x9008
    9016:	39 40 20 00 	mov	#32,	r9	;#0x0020
    901a:	49 8a       	sub.b	r10,	r9	
    901c:	79 f0 1f 00 	and.b	#31,	r9	;#0x001f
    9020:	04 24       	jz	$+10     	;abs 0x902a
    9022:	04 54       	rla	r4		
    9024:	05 65       	rlc	r5		
    9026:	79 53       	add.b	#-1,	r9	;r3 As==11
    9028:	fc 23       	jnz	$-6      	;abs 0x9022
    902a:	04 93       	tst	r4		
    902c:	48 24       	jz	$+146    	;abs 0x90be
    902e:	1c d3       	bis	#1,	r12	;r3 As==01
    9030:	0d d3       	bis	#0,	r13	;r3 As==00
    9032:	0e d3       	bis	#0,	r14	;r3 As==00
    9034:	0f d3       	bis	#0,	r15	;r3 As==00
    9036:	0e 4c       	mov	r12,	r14	
    9038:	0f 4d       	mov	r13,	r15	
    903a:	b0 12 ba 99 	call	#0x99ba	
    903e:	06 4e       	mov	r14,	r6	
    9040:	07 4f       	mov	r15,	r7	
    9042:	3a 90 20 00 	cmp	#32,	r10	;#0x0020
    9046:	28 24       	jz	$+82     	;abs 0x9098
    9048:	3a 90 1f 00 	cmp	#31,	r10	;#0x001f
    904c:	3f 24       	jz	$+128    	;abs 0x90cc
    904e:	78 f0 1f 00 	and.b	#31,	r8	;#0x001f
    9052:	1e 43       	mov	#1,	r14	;r3 As==01
    9054:	0f 43       	clr	r15		
    9056:	04 24       	jz	$+10     	;abs 0x9060
    9058:	0e 5e       	rla	r14		
    905a:	0f 6f       	rlc	r15		
    905c:	78 53       	add.b	#-1,	r8	;r3 As==11
    905e:	fc 23       	jnz	$-6      	;abs 0x9058
    9060:	b0 12 86 98 	call	#0x9886	
    9064:	0c 4e       	mov	r14,	r12	
    9066:	0d 4f       	mov	r15,	r13	
    9068:	0e 46       	mov	r6,	r14	
    906a:	0f 47       	mov	r7,	r15	
    906c:	b0 12 f6 93 	call	#0x93f6	
    9070:	34 41       	pop	r4		
    9072:	35 41       	pop	r5		
    9074:	36 41       	pop	r6		
    9076:	37 41       	pop	r7		
    9078:	38 41       	pop	r8		
    907a:	39 41       	pop	r9		
    907c:	3a 41       	pop	r10		
    907e:	3b 41       	pop	r11		
    9080:	30 41       	ret			
    9082:	0d 95       	cmp	r5,	r13	
    9084:	9c 23       	jnz	$-198    	;abs 0x8fbe
    9086:	0e 96       	cmp	r6,	r14	
    9088:	9a 23       	jnz	$-202    	;abs 0x8fbe
    908a:	0f 97       	cmp	r7,	r15	
    908c:	98 23       	jnz	$-206    	;abs 0x8fbe
    908e:	0e 4c       	mov	r12,	r14	
    9090:	0f 4d       	mov	r13,	r15	
    9092:	b0 12 ba 99 	call	#0x99ba	
    9096:	ec 3f       	jmp	$-38     	;abs 0x9070
    9098:	0b 93       	tst	r11		
    909a:	d6 23       	jnz	$-82     	;abs 0x9048
    909c:	0c 43       	clr	r12		
    909e:	3d 40 80 4f 	mov	#20352,	r13	;#0x4f80
    90a2:	e2 3f       	jmp	$-58     	;abs 0x9068
    90a4:	3d 40 18 00 	mov	#24,	r13	;#0x0018
    90a8:	38 40 18 00 	mov	#24,	r8	;#0x0018
    90ac:	09 43       	clr	r9		
    90ae:	93 3f       	jmp	$-216    	;abs 0x8fd6
    90b0:	36 90 00 01 	cmp	#256,	r6	;#0x0100
    90b4:	07 2c       	jc	$+16     	;abs 0x90c4
    90b6:	0d 43       	clr	r13		
    90b8:	08 43       	clr	r8		
    90ba:	09 43       	clr	r9		
    90bc:	8c 3f       	jmp	$-230    	;abs 0x8fd6
    90be:	05 93       	tst	r5		
    90c0:	b6 23       	jnz	$-146    	;abs 0x902e
    90c2:	b9 3f       	jmp	$-140    	;abs 0x9036
    90c4:	3d 42       	mov	#8,	r13	;r2 As==11
    90c6:	38 42       	mov	#8,	r8	;r2 As==11
    90c8:	09 43       	clr	r9		
    90ca:	85 3f       	jmp	$-244    	;abs 0x8fd6
    90cc:	0b 93       	tst	r11		
    90ce:	bf 23       	jnz	$-128    	;abs 0x904e
    90d0:	0c 43       	clr	r12		
    90d2:	3d 40 00 4f 	mov	#20224,	r13	;#0x4f00
    90d6:	c8 3f       	jmp	$-110    	;abs 0x9068

000090d8 <_fpadd_parts>:
    90d8:	0b 12       	push	r11		
    90da:	0a 12       	push	r10		
    90dc:	09 12       	push	r9		
    90de:	08 12       	push	r8		
    90e0:	07 12       	push	r7		
    90e2:	06 12       	push	r6		
    90e4:	05 12       	push	r5		
    90e6:	04 12       	push	r4		
    90e8:	21 82       	sub	#4,	r1	;r2 As==10
    90ea:	09 4d       	mov	r13,	r9	
    90ec:	6c 4f       	mov.b	@r15,	r12	
    90ee:	6c 93       	cmp.b	#2,	r12	;r3 As==10
    90f0:	64 28       	jnc	$+202    	;abs 0x91ba
    90f2:	6d 4e       	mov.b	@r14,	r13	
    90f4:	6d 93       	cmp.b	#2,	r13	;r3 As==10
    90f6:	e4 28       	jnc	$+458    	;abs 0x92c0
    90f8:	6c 92       	cmp.b	#4,	r12	;r2 As==10
    90fa:	02 20       	jnz	$+6      	;abs 0x9100
    90fc:	30 40 48 93 	br	#0x9348	
    9100:	6d 92       	cmp.b	#4,	r13	;r2 As==10
    9102:	de 24       	jz	$+446    	;abs 0x92c0
    9104:	6d 93       	cmp.b	#2,	r13	;r3 As==10
    9106:	b4 24       	jz	$+362    	;abs 0x9270
    9108:	6c 93       	cmp.b	#2,	r12	;r3 As==10
    910a:	da 24       	jz	$+438    	;abs 0x92c0
    910c:	18 4f 02 00 	mov	2(r15),	r8	;0x0002(r15)
    9110:	1c 4e 02 00 	mov	2(r14),	r12	;0x0002(r14)
    9114:	14 4f 04 00 	mov	4(r15),	r4	;0x0004(r15)
    9118:	15 4f 06 00 	mov	6(r15),	r5	;0x0006(r15)
    911c:	16 4e 04 00 	mov	4(r14),	r6	;0x0004(r14)
    9120:	17 4e 06 00 	mov	6(r14),	r7	;0x0006(r14)
    9124:	0d 48       	mov	r8,	r13	
    9126:	0d 8c       	sub	r12,	r13	
    9128:	0b 4d       	mov	r13,	r11	
    912a:	0d 93       	tst	r13		
    912c:	b9 38       	jl	$+372    	;abs 0x92a0
    912e:	3b 90 20 00 	cmp	#32,	r11	;#0x0020
    9132:	4d 34       	jge	$+156    	;abs 0x91ce
    9134:	1d 93       	cmp	#1,	r13	;r3 As==01
    9136:	d3 38       	jl	$+424    	;abs 0x92de
    9138:	4d 4b       	mov.b	r11,	r13	
    913a:	7d f0 1f 00 	and.b	#31,	r13	;#0x001f
    913e:	81 46 00 00 	mov	r6,	0(r1)	;0x0000(r1)
    9142:	81 47 02 00 	mov	r7,	2(r1)	;0x0002(r1)
    9146:	0c 24       	jz	$+26     	;abs 0x9160
    9148:	4a 4d       	mov.b	r13,	r10	
    914a:	0c 46       	mov	r6,	r12	
    914c:	0d 47       	mov	r7,	r13	
    914e:	12 c3       	clrc			
    9150:	0d 10       	rrc	r13		
    9152:	0c 10       	rrc	r12		
    9154:	7a 53       	add.b	#-1,	r10	;r3 As==11
    9156:	fb 23       	jnz	$-8      	;abs 0x914e
    9158:	81 4c 00 00 	mov	r12,	0(r1)	;0x0000(r1)
    915c:	81 4d 02 00 	mov	r13,	2(r1)	;0x0002(r1)
    9160:	7b f0 1f 00 	and.b	#31,	r11	;#0x001f
    9164:	1c 43       	mov	#1,	r12	;r3 As==01
    9166:	0d 43       	clr	r13		
    9168:	04 24       	jz	$+10     	;abs 0x9172
    916a:	0c 5c       	rla	r12		
    916c:	0d 6d       	rlc	r13		
    916e:	7b 53       	add.b	#-1,	r11	;r3 As==11
    9170:	fc 23       	jnz	$-6      	;abs 0x916a
    9172:	3c 53       	add	#-1,	r12	;r3 As==11
    9174:	3d 63       	addc	#-1,	r13	;r3 As==11
    9176:	0c f6       	and	r6,	r12	
    9178:	0d f7       	and	r7,	r13	
    917a:	1a 43       	mov	#1,	r10	;r3 As==01
    917c:	0b 43       	clr	r11		
    917e:	0c 93       	tst	r12		
    9180:	02 20       	jnz	$+6      	;abs 0x9186
    9182:	0d 93       	tst	r13		
    9184:	de 24       	jz	$+446    	;abs 0x9342
    9186:	26 41       	mov	@r1,	r6	
    9188:	17 41 02 00 	mov	2(r1),	r7	;0x0002(r1)
    918c:	06 da       	bis	r10,	r6	
    918e:	07 db       	bis	r11,	r7	
    9190:	5f 4f 01 00 	mov.b	1(r15),	r15	;0x0001(r15)
    9194:	5f 9e 01 00 	cmp.b	1(r14),	r15	;0x0001(r14)
    9198:	24 20       	jnz	$+74     	;abs 0x91e2
    919a:	c9 4f 01 00 	mov.b	r15,	1(r9)	;0x0001(r9)
    919e:	89 48 02 00 	mov	r8,	2(r9)	;0x0002(r9)
    91a2:	06 54       	add	r4,	r6	
    91a4:	07 65       	addc	r5,	r7	
    91a6:	89 46 04 00 	mov	r6,	4(r9)	;0x0004(r9)
    91aa:	89 47 06 00 	mov	r7,	6(r9)	;0x0006(r9)
    91ae:	f9 40 03 00 	mov.b	#3,	0(r9)	;#0x0003, 0x0000(r9)
    91b2:	00 00 
    91b4:	07 93       	tst	r7		
    91b6:	49 38       	jl	$+148    	;abs 0x924a
    91b8:	0f 49       	mov	r9,	r15	
    91ba:	21 52       	add	#4,	r1	;r2 As==10
    91bc:	34 41       	pop	r4		
    91be:	35 41       	pop	r5		
    91c0:	36 41       	pop	r6		
    91c2:	37 41       	pop	r7		
    91c4:	38 41       	pop	r8		
    91c6:	39 41       	pop	r9		
    91c8:	3a 41       	pop	r10		
    91ca:	3b 41       	pop	r11		
    91cc:	30 41       	ret			
    91ce:	0c 98       	cmp	r8,	r12	
    91d0:	64 38       	jl	$+202    	;abs 0x929a
    91d2:	08 4c       	mov	r12,	r8	
    91d4:	04 43       	clr	r4		
    91d6:	05 43       	clr	r5		
    91d8:	5f 4f 01 00 	mov.b	1(r15),	r15	;0x0001(r15)
    91dc:	5f 9e 01 00 	cmp.b	1(r14),	r15	;0x0001(r14)
    91e0:	dc 27       	jz	$-70     	;abs 0x919a
    91e2:	4f 93       	tst.b	r15		
    91e4:	66 24       	jz	$+206    	;abs 0x92b2
    91e6:	06 84       	sub	r4,	r6	
    91e8:	07 75       	subc	r5,	r7	
    91ea:	07 93       	tst	r7		
    91ec:	6b 38       	jl	$+216    	;abs 0x92c4
    91ee:	c9 43 01 00 	mov.b	#0,	1(r9)	;r3 As==00, 0x0001(r9)
    91f2:	89 48 02 00 	mov	r8,	2(r9)	;0x0002(r9)
    91f6:	89 46 04 00 	mov	r6,	4(r9)	;0x0004(r9)
    91fa:	89 47 06 00 	mov	r7,	6(r9)	;0x0006(r9)
    91fe:	0e 46       	mov	r6,	r14	
    9200:	0f 47       	mov	r7,	r15	
    9202:	3e 53       	add	#-1,	r14	;r3 As==11
    9204:	3f 63       	addc	#-1,	r15	;r3 As==11
    9206:	3f 90 ff 3f 	cmp	#16383,	r15	;#0x3fff
    920a:	05 28       	jnc	$+12     	;abs 0x9216
    920c:	3f 90 00 40 	cmp	#16384,	r15	;#0x4000
    9210:	17 2c       	jc	$+48     	;abs 0x9240
    9212:	3e 93       	cmp	#-1,	r14	;r3 As==11
    9214:	15 2c       	jc	$+44     	;abs 0x9240
    9216:	1d 49 02 00 	mov	2(r9),	r13	;0x0002(r9)
    921a:	3d 53       	add	#-1,	r13	;r3 As==11
    921c:	06 56       	rla	r6		
    921e:	07 67       	rlc	r7		
    9220:	0c 4d       	mov	r13,	r12	
    9222:	3d 53       	add	#-1,	r13	;r3 As==11
    9224:	0e 46       	mov	r6,	r14	
    9226:	0f 47       	mov	r7,	r15	
    9228:	3e 53       	add	#-1,	r14	;r3 As==11
    922a:	3f 63       	addc	#-1,	r15	;r3 As==11
    922c:	3f 90 ff 3f 	cmp	#16383,	r15	;#0x3fff
    9230:	f5 2b       	jnc	$-20     	;abs 0x921c
    9232:	3c 24       	jz	$+122    	;abs 0x92ac
    9234:	89 46 04 00 	mov	r6,	4(r9)	;0x0004(r9)
    9238:	89 47 06 00 	mov	r7,	6(r9)	;0x0006(r9)
    923c:	89 4c 02 00 	mov	r12,	2(r9)	;0x0002(r9)
    9240:	f9 40 03 00 	mov.b	#3,	0(r9)	;#0x0003, 0x0000(r9)
    9244:	00 00 
    9246:	07 93       	tst	r7		
    9248:	b7 37       	jge	$-144    	;abs 0x91b8
    924a:	0e 46       	mov	r6,	r14	
    924c:	0f 47       	mov	r7,	r15	
    924e:	1e f3       	and	#1,	r14	;r3 As==01
    9250:	0f f3       	and	#0,	r15	;r3 As==00
    9252:	12 c3       	clrc			
    9254:	07 10       	rrc	r7		
    9256:	06 10       	rrc	r6		
    9258:	0c 4e       	mov	r14,	r12	
    925a:	0d 4f       	mov	r15,	r13	
    925c:	0c d6       	bis	r6,	r12	
    925e:	0d d7       	bis	r7,	r13	
    9260:	89 4c 04 00 	mov	r12,	4(r9)	;0x0004(r9)
    9264:	89 4d 06 00 	mov	r13,	6(r9)	;0x0006(r9)
    9268:	99 53 02 00 	inc	2(r9)		;0x0002(r9)
    926c:	0f 49       	mov	r9,	r15	
    926e:	a5 3f       	jmp	$-180    	;abs 0x91ba
    9270:	6c 93       	cmp.b	#2,	r12	;r3 As==10
    9272:	a3 23       	jnz	$-184    	;abs 0x91ba
    9274:	a9 4f 00 00 	mov	@r15,	0(r9)	;0x0000(r9)
    9278:	99 4f 02 00 	mov	2(r15),	2(r9)	;0x0002(r15), 0x0002(r9)
    927c:	02 00 
    927e:	99 4f 04 00 	mov	4(r15),	4(r9)	;0x0004(r15), 0x0004(r9)
    9282:	04 00 
    9284:	99 4f 06 00 	mov	6(r15),	6(r9)	;0x0006(r15), 0x0006(r9)
    9288:	06 00 
    928a:	5e 4e 01 00 	mov.b	1(r14),	r14	;0x0001(r14)
    928e:	5e ff 01 00 	and.b	1(r15),	r14	;0x0001(r15)
    9292:	c9 4e 01 00 	mov.b	r14,	1(r9)	;0x0001(r9)
    9296:	0f 49       	mov	r9,	r15	
    9298:	90 3f       	jmp	$-222    	;abs 0x91ba
    929a:	06 43       	clr	r6		
    929c:	07 43       	clr	r7		
    929e:	9c 3f       	jmp	$-198    	;abs 0x91d8
    92a0:	3b e3       	inv	r11		
    92a2:	1b 53       	inc	r11		
    92a4:	3b 90 20 00 	cmp	#32,	r11	;#0x0020
    92a8:	92 37       	jge	$-218    	;abs 0x91ce
    92aa:	44 3f       	jmp	$-374    	;abs 0x9134
    92ac:	3e 93       	cmp	#-1,	r14	;r3 As==11
    92ae:	b6 2b       	jnc	$-146    	;abs 0x921c
    92b0:	c1 3f       	jmp	$-124    	;abs 0x9234
    92b2:	0c 44       	mov	r4,	r12	
    92b4:	0d 45       	mov	r5,	r13	
    92b6:	0c 86       	sub	r6,	r12	
    92b8:	0d 77       	subc	r7,	r13	
    92ba:	06 4c       	mov	r12,	r6	
    92bc:	07 4d       	mov	r13,	r7	
    92be:	95 3f       	jmp	$-212    	;abs 0x91ea
    92c0:	0f 4e       	mov	r14,	r15	
    92c2:	7b 3f       	jmp	$-264    	;abs 0x91ba
    92c4:	d9 43 01 00 	mov.b	#1,	1(r9)	;r3 As==01, 0x0001(r9)
    92c8:	89 48 02 00 	mov	r8,	2(r9)	;0x0002(r9)
    92cc:	36 e3       	inv	r6		
    92ce:	37 e3       	inv	r7		
    92d0:	16 53       	inc	r6		
    92d2:	07 63       	adc	r7		
    92d4:	89 46 04 00 	mov	r6,	4(r9)	;0x0004(r9)
    92d8:	89 47 06 00 	mov	r7,	6(r9)	;0x0006(r9)
    92dc:	90 3f       	jmp	$-222    	;abs 0x91fe
    92de:	0d 93       	tst	r13		
    92e0:	7b 27       	jz	$-264    	;abs 0x91d8
    92e2:	08 5b       	add	r11,	r8	
    92e4:	4d 4b       	mov.b	r11,	r13	
    92e6:	7d f0 1f 00 	and.b	#31,	r13	;#0x001f
    92ea:	81 44 00 00 	mov	r4,	0(r1)	;0x0000(r1)
    92ee:	81 45 02 00 	mov	r5,	2(r1)	;0x0002(r1)
    92f2:	0c 24       	jz	$+26     	;abs 0x930c
    92f4:	4a 4d       	mov.b	r13,	r10	
    92f6:	0c 44       	mov	r4,	r12	
    92f8:	0d 45       	mov	r5,	r13	
    92fa:	12 c3       	clrc			
    92fc:	0d 10       	rrc	r13		
    92fe:	0c 10       	rrc	r12		
    9300:	7a 53       	add.b	#-1,	r10	;r3 As==11
    9302:	fb 23       	jnz	$-8      	;abs 0x92fa
    9304:	81 4c 00 00 	mov	r12,	0(r1)	;0x0000(r1)
    9308:	81 4d 02 00 	mov	r13,	2(r1)	;0x0002(r1)
    930c:	7b f0 1f 00 	and.b	#31,	r11	;#0x001f
    9310:	1c 43       	mov	#1,	r12	;r3 As==01
    9312:	0d 43       	clr	r13		
    9314:	04 24       	jz	$+10     	;abs 0x931e
    9316:	0c 5c       	rla	r12		
    9318:	0d 6d       	rlc	r13		
    931a:	7b 53       	add.b	#-1,	r11	;r3 As==11
    931c:	fc 23       	jnz	$-6      	;abs 0x9316
    931e:	3c 53       	add	#-1,	r12	;r3 As==11
    9320:	3d 63       	addc	#-1,	r13	;r3 As==11
    9322:	0c f4       	and	r4,	r12	
    9324:	0d f5       	and	r5,	r13	
    9326:	1a 43       	mov	#1,	r10	;r3 As==01
    9328:	0b 43       	clr	r11		
    932a:	0c 93       	tst	r12		
    932c:	04 20       	jnz	$+10     	;abs 0x9336
    932e:	0d 93       	tst	r13		
    9330:	02 20       	jnz	$+6      	;abs 0x9336
    9332:	0a 43       	clr	r10		
    9334:	0b 43       	clr	r11		
    9336:	24 41       	mov	@r1,	r4	
    9338:	15 41 02 00 	mov	2(r1),	r5	;0x0002(r1)
    933c:	04 da       	bis	r10,	r4	
    933e:	05 db       	bis	r11,	r5	
    9340:	4b 3f       	jmp	$-360    	;abs 0x91d8
    9342:	0a 43       	clr	r10		
    9344:	0b 43       	clr	r11		
    9346:	1f 3f       	jmp	$-448    	;abs 0x9186
    9348:	6d 92       	cmp.b	#4,	r13	;r2 As==10
    934a:	37 23       	jnz	$-400    	;abs 0x91ba
    934c:	df 9e 01 00 	cmp.b	1(r14),	1(r15)	;0x0001(r14), 0x0001(r15)
    9350:	01 00 
    9352:	33 27       	jz	$-408    	;abs 0x91ba
    9354:	3f 40 26 af 	mov	#-20698,r15	;#0xaf26
    9358:	30 3f       	jmp	$-414    	;abs 0x91ba

0000935a <__addsf3>:
    935a:	31 50 e0 ff 	add	#-32,	r1	;#0xffe0
    935e:	81 4e 1c 00 	mov	r14,	28(r1)	;0x001c(r1)
    9362:	81 4f 1e 00 	mov	r15,	30(r1)	;0x001e(r1)
    9366:	81 4c 18 00 	mov	r12,	24(r1)	;0x0018(r1)
    936a:	81 4d 1a 00 	mov	r13,	26(r1)	;0x001a(r1)
    936e:	0e 41       	mov	r1,	r14	
    9370:	3e 50 10 00 	add	#16,	r14	;#0x0010
    9374:	0f 41       	mov	r1,	r15	
    9376:	3f 50 1c 00 	add	#28,	r15	;#0x001c
    937a:	b0 12 ec 9c 	call	#0x9cec	
    937e:	0e 41       	mov	r1,	r14	
    9380:	3e 52       	add	#8,	r14	;r2 As==11
    9382:	0f 41       	mov	r1,	r15	
    9384:	3f 50 18 00 	add	#24,	r15	;#0x0018
    9388:	b0 12 ec 9c 	call	#0x9cec	
    938c:	0d 41       	mov	r1,	r13	
    938e:	0e 41       	mov	r1,	r14	
    9390:	3e 52       	add	#8,	r14	;r2 As==11
    9392:	0f 41       	mov	r1,	r15	
    9394:	3f 50 10 00 	add	#16,	r15	;#0x0010
    9398:	b0 12 d8 90 	call	#0x90d8	
    939c:	b0 12 12 9b 	call	#0x9b12	
    93a0:	31 50 20 00 	add	#32,	r1	;#0x0020
    93a4:	30 41       	ret			

000093a6 <__subsf3>:
    93a6:	31 50 e0 ff 	add	#-32,	r1	;#0xffe0
    93aa:	81 4e 1c 00 	mov	r14,	28(r1)	;0x001c(r1)
    93ae:	81 4f 1e 00 	mov	r15,	30(r1)	;0x001e(r1)
    93b2:	81 4c 18 00 	mov	r12,	24(r1)	;0x0018(r1)
    93b6:	81 4d 1a 00 	mov	r13,	26(r1)	;0x001a(r1)
    93ba:	0e 41       	mov	r1,	r14	
    93bc:	3e 50 10 00 	add	#16,	r14	;#0x0010
    93c0:	0f 41       	mov	r1,	r15	
    93c2:	3f 50 1c 00 	add	#28,	r15	;#0x001c
    93c6:	b0 12 ec 9c 	call	#0x9cec	
    93ca:	0e 41       	mov	r1,	r14	
    93cc:	3e 52       	add	#8,	r14	;r2 As==11
    93ce:	0f 41       	mov	r1,	r15	
    93d0:	3f 50 18 00 	add	#24,	r15	;#0x0018
    93d4:	b0 12 ec 9c 	call	#0x9cec	
    93d8:	d1 e3 09 00 	xor.b	#1,	9(r1)	;r3 As==01, 0x0009(r1)
    93dc:	0d 41       	mov	r1,	r13	
    93de:	0e 41       	mov	r1,	r14	
    93e0:	3e 52       	add	#8,	r14	;r2 As==11
    93e2:	0f 41       	mov	r1,	r15	
    93e4:	3f 50 10 00 	add	#16,	r15	;#0x0010
    93e8:	b0 12 d8 90 	call	#0x90d8	
    93ec:	b0 12 12 9b 	call	#0x9b12	
    93f0:	31 50 20 00 	add	#32,	r1	;#0x0020
    93f4:	30 41       	ret			

000093f6 <__mulsf3>:
    93f6:	0b 12       	push	r11		
    93f8:	0a 12       	push	r10		
    93fa:	09 12       	push	r9		
    93fc:	08 12       	push	r8		
    93fe:	07 12       	push	r7		
    9400:	06 12       	push	r6		
    9402:	05 12       	push	r5		
    9404:	04 12       	push	r4		
    9406:	31 50 de ff 	add	#-34,	r1	;#0xffde
    940a:	81 4e 1c 00 	mov	r14,	28(r1)	;0x001c(r1)
    940e:	81 4f 1e 00 	mov	r15,	30(r1)	;0x001e(r1)
    9412:	81 4c 18 00 	mov	r12,	24(r1)	;0x0018(r1)
    9416:	81 4d 1a 00 	mov	r13,	26(r1)	;0x001a(r1)
    941a:	0e 41       	mov	r1,	r14	
    941c:	3e 50 10 00 	add	#16,	r14	;#0x0010
    9420:	0f 41       	mov	r1,	r15	
    9422:	3f 50 1c 00 	add	#28,	r15	;#0x001c
    9426:	b0 12 ec 9c 	call	#0x9cec	
    942a:	0e 41       	mov	r1,	r14	
    942c:	3e 52       	add	#8,	r14	;r2 As==11
    942e:	0f 41       	mov	r1,	r15	
    9430:	3f 50 18 00 	add	#24,	r15	;#0x0018
    9434:	b0 12 ec 9c 	call	#0x9cec	
    9438:	5f 41 10 00 	mov.b	16(r1),	r15	;0x0010(r1)
    943c:	6f 93       	cmp.b	#2,	r15	;r3 As==10
    943e:	17 2c       	jc	$+48     	;abs 0x946e
    9440:	5f 43       	mov.b	#1,	r15	;r3 As==01
    9442:	d1 91 09 00 	cmp.b	9(r1),	17(r1)	;0x0009(r1), 0x0011(r1)
    9446:	11 00 
    9448:	20 24       	jz	$+66     	;abs 0x948a
    944a:	c1 4f 11 00 	mov.b	r15,	17(r1)	;0x0011(r1)
    944e:	0f 41       	mov	r1,	r15	
    9450:	3f 50 10 00 	add	#16,	r15	;#0x0010
    9454:	b0 12 12 9b 	call	#0x9b12	
    9458:	31 50 22 00 	add	#34,	r1	;#0x0022
    945c:	34 41       	pop	r4		
    945e:	35 41       	pop	r5		
    9460:	36 41       	pop	r6		
    9462:	37 41       	pop	r7		
    9464:	38 41       	pop	r8		
    9466:	39 41       	pop	r9		
    9468:	3a 41       	pop	r10		
    946a:	3b 41       	pop	r11		
    946c:	30 41       	ret			
    946e:	5e 41 08 00 	mov.b	8(r1),	r14	;0x0008(r1)
    9472:	6e 93       	cmp.b	#2,	r14	;r3 As==10
    9474:	0e 2c       	jc	$+30     	;abs 0x9492
    9476:	5f 43       	mov.b	#1,	r15	;r3 As==01
    9478:	d1 91 09 00 	cmp.b	9(r1),	17(r1)	;0x0009(r1), 0x0011(r1)
    947c:	11 00 
    947e:	07 24       	jz	$+16     	;abs 0x948e
    9480:	c1 4f 09 00 	mov.b	r15,	9(r1)	;0x0009(r1)
    9484:	0f 41       	mov	r1,	r15	
    9486:	3f 52       	add	#8,	r15	;r2 As==11
    9488:	e5 3f       	jmp	$-52     	;abs 0x9454
    948a:	4f 43       	clr.b	r15		
    948c:	de 3f       	jmp	$-66     	;abs 0x944a
    948e:	4f 43       	clr.b	r15		
    9490:	f7 3f       	jmp	$-16     	;abs 0x9480
    9492:	6f 92       	cmp.b	#4,	r15	;r2 As==10
    9494:	05 20       	jnz	$+12     	;abs 0x94a0
    9496:	6e 93       	cmp.b	#2,	r14	;r3 As==10
    9498:	d3 23       	jnz	$-88     	;abs 0x9440
    949a:	3f 40 26 af 	mov	#-20698,r15	;#0xaf26
    949e:	da 3f       	jmp	$-74     	;abs 0x9454
    94a0:	6e 92       	cmp.b	#4,	r14	;r2 As==10
    94a2:	03 20       	jnz	$+8      	;abs 0x94aa
    94a4:	6f 93       	cmp.b	#2,	r15	;r3 As==10
    94a6:	f9 27       	jz	$-12     	;abs 0x949a
    94a8:	e6 3f       	jmp	$-50     	;abs 0x9476
    94aa:	6f 93       	cmp.b	#2,	r15	;r3 As==10
    94ac:	c9 27       	jz	$-108    	;abs 0x9440
    94ae:	6e 93       	cmp.b	#2,	r14	;r3 As==10
    94b0:	e2 27       	jz	$-58     	;abs 0x9476
    94b2:	16 41 14 00 	mov	20(r1),	r6	;0x0014(r1)
    94b6:	17 41 16 00 	mov	22(r1),	r7	;0x0016(r1)
    94ba:	1e 41 0c 00 	mov	12(r1),	r14	;0x000c(r1)
    94be:	1f 41 0e 00 	mov	14(r1),	r15	;0x000e(r1)
    94c2:	b1 40 20 00 	mov	#32,	32(r1)	;#0x0020, 0x0020(r1)
    94c6:	20 00 
    94c8:	0c 43       	clr	r12		
    94ca:	0d 43       	clr	r13		
    94cc:	0a 43       	clr	r10		
    94ce:	0b 43       	clr	r11		
    94d0:	04 43       	clr	r4		
    94d2:	05 43       	clr	r5		
    94d4:	08 4c       	mov	r12,	r8	
    94d6:	09 4d       	mov	r13,	r9	
    94d8:	08 3c       	jmp	$+18     	;abs 0x94ea
    94da:	0e 5e       	rla	r14		
    94dc:	0f 6f       	rlc	r15		
    94de:	12 c3       	clrc			
    94e0:	07 10       	rrc	r7		
    94e2:	06 10       	rrc	r6		
    94e4:	b1 53 20 00 	add	#-1,	32(r1)	;r3 As==11, 0x0020(r1)
    94e8:	21 24       	jz	$+68     	;abs 0x952c
    94ea:	0c 46       	mov	r6,	r12	
    94ec:	0d 47       	mov	r7,	r13	
    94ee:	1c f3       	and	#1,	r12	;r3 As==01
    94f0:	0d f3       	and	#0,	r13	;r3 As==00
    94f2:	0c 93       	tst	r12		
    94f4:	02 20       	jnz	$+6      	;abs 0x94fa
    94f6:	0d 93       	tst	r13		
    94f8:	0f 24       	jz	$+32     	;abs 0x9518
    94fa:	04 5e       	add	r14,	r4	
    94fc:	05 6f       	addc	r15,	r5	
    94fe:	0c 48       	mov	r8,	r12	
    9500:	0d 49       	mov	r9,	r13	
    9502:	0c 5a       	add	r10,	r12	
    9504:	0d 6b       	addc	r11,	r13	
    9506:	18 43       	mov	#1,	r8	;r3 As==01
    9508:	09 43       	clr	r9		
    950a:	05 9f       	cmp	r15,	r5	
    950c:	03 28       	jnc	$+8      	;abs 0x9514
    950e:	0b 24       	jz	$+24     	;abs 0x9526
    9510:	08 43       	clr	r8		
    9512:	09 43       	clr	r9		
    9514:	08 5c       	add	r12,	r8	
    9516:	09 6d       	addc	r13,	r9	
    9518:	0a 5a       	rla	r10		
    951a:	0b 6b       	rlc	r11		
    951c:	0f 93       	tst	r15		
    951e:	dd 37       	jge	$-68     	;abs 0x94da
    9520:	1a d3       	bis	#1,	r10	;r3 As==01
    9522:	0b d3       	bis	#0,	r11	;r3 As==00
    9524:	da 3f       	jmp	$-74     	;abs 0x94da
    9526:	04 9e       	cmp	r14,	r4	
    9528:	f5 2b       	jnc	$-20     	;abs 0x9514
    952a:	f2 3f       	jmp	$-26     	;abs 0x9510
    952c:	0c 48       	mov	r8,	r12	
    952e:	0d 49       	mov	r9,	r13	
    9530:	0e 4d       	mov	r13,	r14	
    9532:	1b 41 12 00 	mov	18(r1),	r11	;0x0012(r1)
    9536:	1b 51 0a 00 	add	10(r1),	r11	;0x000a(r1)
    953a:	0f 4b       	mov	r11,	r15	
    953c:	2f 53       	incd	r15		
    953e:	81 4f 02 00 	mov	r15,	2(r1)	;0x0002(r1)
    9542:	5f 43       	mov.b	#1,	r15	;r3 As==01
    9544:	d1 91 09 00 	cmp.b	9(r1),	17(r1)	;0x0009(r1), 0x0011(r1)
    9548:	11 00 
    954a:	45 24       	jz	$+140    	;abs 0x95d6
    954c:	c1 4f 01 00 	mov.b	r15,	1(r1)	;0x0001(r1)
    9550:	0e 93       	tst	r14		
    9552:	27 38       	jl	$+80     	;abs 0x95a2
    9554:	3d 90 00 40 	cmp	#16384,	r13	;#0x4000
    9558:	10 2c       	jc	$+34     	;abs 0x957a
    955a:	1f 41 02 00 	mov	2(r1),	r15	;0x0002(r1)
    955e:	3f 53       	add	#-1,	r15	;r3 As==11
    9560:	0e 4f       	mov	r15,	r14	
    9562:	0c 5c       	rla	r12		
    9564:	0d 6d       	rlc	r13		
    9566:	05 93       	tst	r5		
    9568:	19 38       	jl	$+52     	;abs 0x959c
    956a:	04 54       	rla	r4		
    956c:	05 65       	rlc	r5		
    956e:	3f 53       	add	#-1,	r15	;r3 As==11
    9570:	3d 90 00 40 	cmp	#16384,	r13	;#0x4000
    9574:	f5 2b       	jnc	$-20     	;abs 0x9560
    9576:	81 4e 02 00 	mov	r14,	2(r1)	;0x0002(r1)
    957a:	0e 4c       	mov	r12,	r14	
    957c:	0f 4d       	mov	r13,	r15	
    957e:	3e f0 7f 00 	and	#127,	r14	;#0x007f
    9582:	0f f3       	and	#0,	r15	;r3 As==00
    9584:	3e 90 40 00 	cmp	#64,	r14	;#0x0040
    9588:	28 24       	jz	$+82     	;abs 0x95da
    958a:	81 4c 04 00 	mov	r12,	4(r1)	;0x0004(r1)
    958e:	81 4d 06 00 	mov	r13,	6(r1)	;0x0006(r1)
    9592:	f1 40 03 00 	mov.b	#3,	0(r1)	;#0x0003, 0x0000(r1)
    9596:	00 00 
    9598:	0f 41       	mov	r1,	r15	
    959a:	5c 3f       	jmp	$-326    	;abs 0x9454
    959c:	1c d3       	bis	#1,	r12	;r3 As==01
    959e:	0d d3       	bis	#0,	r13	;r3 As==00
    95a0:	e4 3f       	jmp	$-54     	;abs 0x956a
    95a2:	3b 50 03 00 	add	#3,	r11	;#0x0003
    95a6:	0a 4b       	mov	r11,	r10	
    95a8:	0e 4c       	mov	r12,	r14	
    95aa:	0f 4d       	mov	r13,	r15	
    95ac:	1e f3       	and	#1,	r14	;r3 As==01
    95ae:	0f f3       	and	#0,	r15	;r3 As==00
    95b0:	0e 93       	tst	r14		
    95b2:	02 20       	jnz	$+6      	;abs 0x95b8
    95b4:	0f 93       	tst	r15		
    95b6:	06 24       	jz	$+14     	;abs 0x95c4
    95b8:	12 c3       	clrc			
    95ba:	05 10       	rrc	r5		
    95bc:	04 10       	rrc	r4		
    95be:	04 d3       	bis	#0,	r4	;r3 As==00
    95c0:	35 d0 00 80 	bis	#-32768,r5	;#0x8000
    95c4:	12 c3       	clrc			
    95c6:	0d 10       	rrc	r13		
    95c8:	0c 10       	rrc	r12		
    95ca:	1b 53       	inc	r11		
    95cc:	0d 93       	tst	r13		
    95ce:	eb 3b       	jl	$-40     	;abs 0x95a6
    95d0:	81 4a 02 00 	mov	r10,	2(r1)	;0x0002(r1)
    95d4:	bf 3f       	jmp	$-128    	;abs 0x9554
    95d6:	4f 43       	clr.b	r15		
    95d8:	b9 3f       	jmp	$-140    	;abs 0x954c
    95da:	0f 93       	tst	r15		
    95dc:	d6 23       	jnz	$-82     	;abs 0x958a
    95de:	0e 4c       	mov	r12,	r14	
    95e0:	0f 4d       	mov	r13,	r15	
    95e2:	3e f0 80 00 	and	#128,	r14	;#0x0080
    95e6:	0f f3       	and	#0,	r15	;r3 As==00
    95e8:	0e 93       	tst	r14		
    95ea:	cf 23       	jnz	$-96     	;abs 0x958a
    95ec:	0f 93       	tst	r15		
    95ee:	cd 23       	jnz	$-100    	;abs 0x958a
    95f0:	04 93       	tst	r4		
    95f2:	02 20       	jnz	$+6      	;abs 0x95f8
    95f4:	05 93       	tst	r5		
    95f6:	c9 27       	jz	$-108    	;abs 0x958a
    95f8:	3c 50 40 00 	add	#64,	r12	;#0x0040
    95fc:	0d 63       	adc	r13		
    95fe:	3c f0 80 ff 	and	#-128,	r12	;#0xff80
    9602:	3d f3       	and	#-1,	r13	;r3 As==11
    9604:	c2 3f       	jmp	$-122    	;abs 0x958a

00009606 <__divsf3>:
    9606:	0b 12       	push	r11		
    9608:	0a 12       	push	r10		
    960a:	09 12       	push	r9		
    960c:	08 12       	push	r8		
    960e:	07 12       	push	r7		
    9610:	31 50 e8 ff 	add	#-24,	r1	;#0xffe8
    9614:	81 4e 14 00 	mov	r14,	20(r1)	;0x0014(r1)
    9618:	81 4f 16 00 	mov	r15,	22(r1)	;0x0016(r1)
    961c:	81 4c 10 00 	mov	r12,	16(r1)	;0x0010(r1)
    9620:	81 4d 12 00 	mov	r13,	18(r1)	;0x0012(r1)
    9624:	0e 41       	mov	r1,	r14	
    9626:	3e 52       	add	#8,	r14	;r2 As==11
    9628:	0f 41       	mov	r1,	r15	
    962a:	3f 50 14 00 	add	#20,	r15	;#0x0014
    962e:	b0 12 ec 9c 	call	#0x9cec	
    9632:	0e 41       	mov	r1,	r14	
    9634:	0f 41       	mov	r1,	r15	
    9636:	3f 50 10 00 	add	#16,	r15	;#0x0010
    963a:	b0 12 ec 9c 	call	#0x9cec	
    963e:	5f 41 08 00 	mov.b	8(r1),	r15	;0x0008(r1)
    9642:	6f 93       	cmp.b	#2,	r15	;r3 As==10
    9644:	0c 2c       	jc	$+26     	;abs 0x965e
    9646:	0f 41       	mov	r1,	r15	
    9648:	3f 52       	add	#8,	r15	;r2 As==11
    964a:	b0 12 12 9b 	call	#0x9b12	
    964e:	31 50 18 00 	add	#24,	r1	;#0x0018
    9652:	37 41       	pop	r7		
    9654:	38 41       	pop	r8		
    9656:	39 41       	pop	r9		
    9658:	3a 41       	pop	r10		
    965a:	3b 41       	pop	r11		
    965c:	30 41       	ret			
    965e:	6e 41       	mov.b	@r1,	r14	
    9660:	6e 93       	cmp.b	#2,	r14	;r3 As==10
    9662:	02 2c       	jc	$+6      	;abs 0x9668
    9664:	0f 41       	mov	r1,	r15	
    9666:	f1 3f       	jmp	$-28     	;abs 0x964a
    9668:	d1 e1 01 00 	xor.b	1(r1),	9(r1)	;0x0001(r1), 0x0009(r1)
    966c:	09 00 
    966e:	6f 92       	cmp.b	#4,	r15	;r2 As==10
    9670:	02 24       	jz	$+6      	;abs 0x9676
    9672:	6f 93       	cmp.b	#2,	r15	;r3 As==10
    9674:	05 20       	jnz	$+12     	;abs 0x9680
    9676:	4f 9e       	cmp.b	r14,	r15	
    9678:	e6 23       	jnz	$-50     	;abs 0x9646
    967a:	3f 40 26 af 	mov	#-20698,r15	;#0xaf26
    967e:	e5 3f       	jmp	$-52     	;abs 0x964a
    9680:	6e 92       	cmp.b	#4,	r14	;r2 As==10
    9682:	34 24       	jz	$+106    	;abs 0x96ec
    9684:	6e 93       	cmp.b	#2,	r14	;r3 As==10
    9686:	48 24       	jz	$+146    	;abs 0x9718
    9688:	1d 41 0a 00 	mov	10(r1),	r13	;0x000a(r1)
    968c:	1d 81 02 00 	sub	2(r1),	r13	;0x0002(r1)
    9690:	81 4d 0a 00 	mov	r13,	10(r1)	;0x000a(r1)
    9694:	1e 41 0c 00 	mov	12(r1),	r14	;0x000c(r1)
    9698:	1f 41 0e 00 	mov	14(r1),	r15	;0x000e(r1)
    969c:	1a 41 04 00 	mov	4(r1),	r10	;0x0004(r1)
    96a0:	1b 41 06 00 	mov	6(r1),	r11	;0x0006(r1)
    96a4:	0f 9b       	cmp	r11,	r15	
    96a6:	04 28       	jnc	$+10     	;abs 0x96b0
    96a8:	0b 9f       	cmp	r15,	r11	
    96aa:	07 28       	jnc	$+16     	;abs 0x96ba
    96ac:	0e 9a       	cmp	r10,	r14	
    96ae:	05 2c       	jc	$+12     	;abs 0x96ba
    96b0:	0e 5e       	rla	r14		
    96b2:	0f 6f       	rlc	r15		
    96b4:	3d 53       	add	#-1,	r13	;r3 As==11
    96b6:	81 4d 0a 00 	mov	r13,	10(r1)	;0x000a(r1)
    96ba:	37 40 1f 00 	mov	#31,	r7	;#0x001f
    96be:	0c 43       	clr	r12		
    96c0:	3d 40 00 40 	mov	#16384,	r13	;#0x4000
    96c4:	08 43       	clr	r8		
    96c6:	09 43       	clr	r9		
    96c8:	0b 3c       	jmp	$+24     	;abs 0x96e0
    96ca:	08 dc       	bis	r12,	r8	
    96cc:	09 dd       	bis	r13,	r9	
    96ce:	0e 8a       	sub	r10,	r14	
    96d0:	0f 7b       	subc	r11,	r15	
    96d2:	12 c3       	clrc			
    96d4:	0d 10       	rrc	r13		
    96d6:	0c 10       	rrc	r12		
    96d8:	0e 5e       	rla	r14		
    96da:	0f 6f       	rlc	r15		
    96dc:	37 53       	add	#-1,	r7	;r3 As==11
    96de:	0f 24       	jz	$+32     	;abs 0x96fe
    96e0:	0f 9b       	cmp	r11,	r15	
    96e2:	f7 2b       	jnc	$-16     	;abs 0x96d2
    96e4:	f2 23       	jnz	$-26     	;abs 0x96ca
    96e6:	0e 9a       	cmp	r10,	r14	
    96e8:	f4 2b       	jnc	$-22     	;abs 0x96d2
    96ea:	ef 3f       	jmp	$-32     	;abs 0x96ca
    96ec:	81 43 0c 00 	mov	#0,	12(r1)	;r3 As==00, 0x000c(r1)
    96f0:	81 43 0e 00 	mov	#0,	14(r1)	;r3 As==00, 0x000e(r1)
    96f4:	81 43 0a 00 	mov	#0,	10(r1)	;r3 As==00, 0x000a(r1)
    96f8:	0f 41       	mov	r1,	r15	
    96fa:	3f 52       	add	#8,	r15	;r2 As==11
    96fc:	a6 3f       	jmp	$-178    	;abs 0x964a
    96fe:	0c 48       	mov	r8,	r12	
    9700:	0d 49       	mov	r9,	r13	
    9702:	3c f0 7f 00 	and	#127,	r12	;#0x007f
    9706:	0d f3       	and	#0,	r13	;r3 As==00
    9708:	3c 90 40 00 	cmp	#64,	r12	;#0x0040
    970c:	0a 24       	jz	$+22     	;abs 0x9722
    970e:	81 48 0c 00 	mov	r8,	12(r1)	;0x000c(r1)
    9712:	81 49 0e 00 	mov	r9,	14(r1)	;0x000e(r1)
    9716:	97 3f       	jmp	$-208    	;abs 0x9646
    9718:	e1 42 08 00 	mov.b	#4,	8(r1)	;r2 As==10, 0x0008(r1)
    971c:	0f 41       	mov	r1,	r15	
    971e:	3f 52       	add	#8,	r15	;r2 As==11
    9720:	94 3f       	jmp	$-214    	;abs 0x964a
    9722:	0d 93       	tst	r13		
    9724:	f4 23       	jnz	$-22     	;abs 0x970e
    9726:	0c 48       	mov	r8,	r12	
    9728:	0d 49       	mov	r9,	r13	
    972a:	3c f0 80 00 	and	#128,	r12	;#0x0080
    972e:	0d f3       	and	#0,	r13	;r3 As==00
    9730:	0c 93       	tst	r12		
    9732:	ed 23       	jnz	$-36     	;abs 0x970e
    9734:	0d 93       	tst	r13		
    9736:	eb 23       	jnz	$-40     	;abs 0x970e
    9738:	0e 93       	tst	r14		
    973a:	02 20       	jnz	$+6      	;abs 0x9740
    973c:	0f 93       	tst	r15		
    973e:	e7 27       	jz	$-48     	;abs 0x970e
    9740:	38 50 40 00 	add	#64,	r8	;#0x0040
    9744:	09 63       	adc	r9		
    9746:	38 f0 80 ff 	and	#-128,	r8	;#0xff80
    974a:	39 f3       	and	#-1,	r9	;r3 As==11
    974c:	e0 3f       	jmp	$-62     	;abs 0x970e
0000974e <__gtsf2>:
    974e:	31 50 e8 ff 	add	#-24,	r1	;#0xffe8
    9752:	81 4e 14 00 	mov	r14,	20(r1)	;0x0014(r1)
    9756:	81 4f 16 00 	mov	r15,	22(r1)	;0x0016(r1)
    975a:	81 4c 10 00 	mov	r12,	16(r1)	;0x0010(r1)
    975e:	81 4d 12 00 	mov	r13,	18(r1)	;0x0012(r1)
    9762:	0e 41       	mov	r1,	r14	
    9764:	3e 52       	add	#8,	r14	;r2 As==11
    9766:	0f 41       	mov	r1,	r15	
    9768:	3f 50 14 00 	add	#20,	r15	;#0x0014
    976c:	b0 12 ec 9c 	call	#0x9cec	
    9770:	0e 41       	mov	r1,	r14	
    9772:	0f 41       	mov	r1,	r15	
    9774:	3f 50 10 00 	add	#16,	r15	;#0x0010
    9778:	b0 12 ec 9c 	call	#0x9cec	
    977c:	e1 93 08 00 	cmp.b	#2,	8(r1)	;r3 As==10, 0x0008(r1)
    9780:	0b 28       	jnc	$+24     	;abs 0x9798
    9782:	e1 93 00 00 	cmp.b	#2,	0(r1)	;r3 As==10, 0x0000(r1)
    9786:	08 28       	jnc	$+18     	;abs 0x9798
    9788:	0e 41       	mov	r1,	r14	
    978a:	0f 41       	mov	r1,	r15	
    978c:	3f 52       	add	#8,	r15	;r2 As==11
    978e:	b0 12 28 9e 	call	#0x9e28	
    9792:	31 50 18 00 	add	#24,	r1	;#0x0018
    9796:	30 41       	ret			
    9798:	3f 43       	mov	#-1,	r15	;r3 As==11
    979a:	fb 3f       	jmp	$-8      	;abs 0x9792

0000979c <__gesf2>:
    979c:	31 50 e8 ff 	add	#-24,	r1	;#0xffe8
    97a0:	81 4e 14 00 	mov	r14,	20(r1)	;0x0014(r1)
    97a4:	81 4f 16 00 	mov	r15,	22(r1)	;0x0016(r1)
    97a8:	81 4c 10 00 	mov	r12,	16(r1)	;0x0010(r1)
    97ac:	81 4d 12 00 	mov	r13,	18(r1)	;0x0012(r1)
    97b0:	0e 41       	mov	r1,	r14	
    97b2:	3e 52       	add	#8,	r14	;r2 As==11
    97b4:	0f 41       	mov	r1,	r15	
    97b6:	3f 50 14 00 	add	#20,	r15	;#0x0014
    97ba:	b0 12 ec 9c 	call	#0x9cec	
    97be:	0e 41       	mov	r1,	r14	
    97c0:	0f 41       	mov	r1,	r15	
    97c2:	3f 50 10 00 	add	#16,	r15	;#0x0010
    97c6:	b0 12 ec 9c 	call	#0x9cec	
    97ca:	e1 93 08 00 	cmp.b	#2,	8(r1)	;r3 As==10, 0x0008(r1)
    97ce:	0b 28       	jnc	$+24     	;abs 0x97e6
    97d0:	e1 93 00 00 	cmp.b	#2,	0(r1)	;r3 As==10, 0x0000(r1)
    97d4:	08 28       	jnc	$+18     	;abs 0x97e6
    97d6:	0e 41       	mov	r1,	r14	
    97d8:	0f 41       	mov	r1,	r15	
    97da:	3f 52       	add	#8,	r15	;r2 As==11
    97dc:	b0 12 28 9e 	call	#0x9e28	
    97e0:	31 50 18 00 	add	#24,	r1	;#0x0018
    97e4:	30 41       	ret			
    97e6:	3f 43       	mov	#-1,	r15	;r3 As==11
    97e8:	fb 3f       	jmp	$-8      	;abs 0x97e0

000097ea <__ltsf2>:
    97ea:	31 50 e8 ff 	add	#-24,	r1	;#0xffe8
    97ee:	81 4e 14 00 	mov	r14,	20(r1)	;0x0014(r1)
    97f2:	81 4f 16 00 	mov	r15,	22(r1)	;0x0016(r1)
    97f6:	81 4c 10 00 	mov	r12,	16(r1)	;0x0010(r1)
    97fa:	81 4d 12 00 	mov	r13,	18(r1)	;0x0012(r1)
    97fe:	0e 41       	mov	r1,	r14	
    9800:	3e 52       	add	#8,	r14	;r2 As==11
    9802:	0f 41       	mov	r1,	r15	
    9804:	3f 50 14 00 	add	#20,	r15	;#0x0014
    9808:	b0 12 ec 9c 	call	#0x9cec	
    980c:	0e 41       	mov	r1,	r14	
    980e:	0f 41       	mov	r1,	r15	
    9810:	3f 50 10 00 	add	#16,	r15	;#0x0010
    9814:	b0 12 ec 9c 	call	#0x9cec	
    9818:	e1 93 08 00 	cmp.b	#2,	8(r1)	;r3 As==10, 0x0008(r1)
    981c:	0b 28       	jnc	$+24     	;abs 0x9834
    981e:	e1 93 00 00 	cmp.b	#2,	0(r1)	;r3 As==10, 0x0000(r1)
    9822:	08 28       	jnc	$+18     	;abs 0x9834
    9824:	0e 41       	mov	r1,	r14	
    9826:	0f 41       	mov	r1,	r15	
    9828:	3f 52       	add	#8,	r15	;r2 As==11
    982a:	b0 12 28 9e 	call	#0x9e28	
    982e:	31 50 18 00 	add	#24,	r1	;#0x0018
    9832:	30 41       	ret			
    9834:	1f 43       	mov	#1,	r15	;r3 As==01
    9836:	fb 3f       	jmp	$-8      	;abs 0x982e

00009838 <__lesf2>:
    9838:	31 50 e8 ff 	add	#-24,	r1	;#0xffe8
    983c:	81 4e 14 00 	mov	r14,	20(r1)	;0x0014(r1)
    9840:	81 4f 16 00 	mov	r15,	22(r1)	;0x0016(r1)
    9844:	81 4c 10 00 	mov	r12,	16(r1)	;0x0010(r1)
    9848:	81 4d 12 00 	mov	r13,	18(r1)	;0x0012(r1)
    984c:	0e 41       	mov	r1,	r14	
    984e:	3e 52       	add	#8,	r14	;r2 As==11
    9850:	0f 41       	mov	r1,	r15	
    9852:	3f 50 14 00 	add	#20,	r15	;#0x0014
    9856:	b0 12 ec 9c 	call	#0x9cec	
    985a:	0e 41       	mov	r1,	r14	
    985c:	0f 41       	mov	r1,	r15	
    985e:	3f 50 10 00 	add	#16,	r15	;#0x0010
    9862:	b0 12 ec 9c 	call	#0x9cec	
    9866:	e1 93 08 00 	cmp.b	#2,	8(r1)	;r3 As==10, 0x0008(r1)
    986a:	0b 28       	jnc	$+24     	;abs 0x9882
    986c:	e1 93 00 00 	cmp.b	#2,	0(r1)	;r3 As==10, 0x0000(r1)
    9870:	08 28       	jnc	$+18     	;abs 0x9882
    9872:	0e 41       	mov	r1,	r14	
    9874:	0f 41       	mov	r1,	r15	
    9876:	3f 52       	add	#8,	r15	;r2 As==11
    9878:	b0 12 28 9e 	call	#0x9e28	
    987c:	31 50 18 00 	add	#24,	r1	;#0x0018
    9880:	30 41       	ret			
    9882:	1f 43       	mov	#1,	r15	;r3 As==01
    9884:	fb 3f       	jmp	$-8      	;abs 0x987c

00009886 <__floatsisf>:
    9886:	0b 12       	push	r11		
    9888:	0a 12       	push	r10		
    988a:	31 82       	sub	#8,	r1	;r2 As==11
    988c:	f1 40 03 00 	mov.b	#3,	0(r1)	;#0x0003, 0x0000(r1)
    9890:	00 00 
    9892:	0d 4f       	mov	r15,	r13	
    9894:	0d 5d       	rla	r13		
    9896:	0d 43       	clr	r13		
    9898:	0d 6d       	rlc	r13		
    989a:	4c 4d       	mov.b	r13,	r12	
    989c:	c1 4d 01 00 	mov.b	r13,	1(r1)	;0x0001(r1)
    98a0:	0e 93       	tst	r14		
    98a2:	0b 20       	jnz	$+24     	;abs 0x98ba
    98a4:	0f 93       	tst	r15		
    98a6:	09 20       	jnz	$+20     	;abs 0x98ba
    98a8:	e1 43 00 00 	mov.b	#2,	0(r1)	;r3 As==10, 0x0000(r1)
    98ac:	0f 41       	mov	r1,	r15	
    98ae:	b0 12 12 9b 	call	#0x9b12	
    98b2:	31 52       	add	#8,	r1	;r2 As==11
    98b4:	3a 41       	pop	r10		
    98b6:	3b 41       	pop	r11		
    98b8:	30 41       	ret			
    98ba:	b1 40 1e 00 	mov	#30,	2(r1)	;#0x001e, 0x0002(r1)
    98be:	02 00 
    98c0:	4c 93       	tst.b	r12		
    98c2:	17 20       	jnz	$+48     	;abs 0x98f2
    98c4:	0a 4e       	mov	r14,	r10	
    98c6:	0b 4f       	mov	r15,	r11	
    98c8:	0e 4a       	mov	r10,	r14	
    98ca:	0f 4b       	mov	r11,	r15	
    98cc:	b0 12 a0 9a 	call	#0x9aa0	
    98d0:	3f 53       	add	#-1,	r15	;r3 As==11
    98d2:	1f 93       	cmp	#1,	r15	;r3 As==01
    98d4:	27 38       	jl	$+80     	;abs 0x9924
    98d6:	4e 4f       	mov.b	r15,	r14	
    98d8:	7e f0 1f 00 	and.b	#31,	r14	;#0x001f
    98dc:	81 4a 04 00 	mov	r10,	4(r1)	;0x0004(r1)
    98e0:	81 4b 06 00 	mov	r11,	6(r1)	;0x0006(r1)
    98e4:	0f 20       	jnz	$+32     	;abs 0x9904
    98e6:	3e 40 1e 00 	mov	#30,	r14	;#0x001e
    98ea:	0e 8f       	sub	r15,	r14	
    98ec:	81 4e 02 00 	mov	r14,	2(r1)	;0x0002(r1)
    98f0:	dd 3f       	jmp	$-68     	;abs 0x98ac
    98f2:	0e 93       	tst	r14		
    98f4:	10 24       	jz	$+34     	;abs 0x9916
    98f6:	0a 4e       	mov	r14,	r10	
    98f8:	0b 4f       	mov	r15,	r11	
    98fa:	3a e3       	inv	r10		
    98fc:	3b e3       	inv	r11		
    98fe:	1a 53       	inc	r10		
    9900:	0b 63       	adc	r11		
    9902:	e2 3f       	jmp	$-58     	;abs 0x98c8
    9904:	91 51 04 00 	rla	4(r1)		;0x0004(r1)
    9908:	04 00 
    990a:	91 61 06 00 	rlc	6(r1)		;0x0006(r1)
    990e:	06 00 
    9910:	7e 53       	add.b	#-1,	r14	;r3 As==11
    9912:	f8 23       	jnz	$-14     	;abs 0x9904
    9914:	e8 3f       	jmp	$-46     	;abs 0x98e6
    9916:	3f 90 00 80 	cmp	#-32768,r15	;#0x8000
    991a:	ed 23       	jnz	$-36     	;abs 0x98f6
    991c:	0e 43       	clr	r14		
    991e:	3f 40 00 cf 	mov	#-12544,r15	;#0xcf00
    9922:	c7 3f       	jmp	$-112    	;abs 0x98b2
    9924:	81 4a 04 00 	mov	r10,	4(r1)	;0x0004(r1)
    9928:	81 4b 06 00 	mov	r11,	6(r1)	;0x0006(r1)
    992c:	bf 3f       	jmp	$-128    	;abs 0x98ac

0000992e <__fixsfsi>:
    992e:	31 50 f4 ff 	add	#-12,	r1	;#0xfff4
    9932:	81 4e 08 00 	mov	r14,	8(r1)	;0x0008(r1)
    9936:	81 4f 0a 00 	mov	r15,	10(r1)	;0x000a(r1)
    993a:	0e 41       	mov	r1,	r14	
    993c:	0f 41       	mov	r1,	r15	
    993e:	3f 52       	add	#8,	r15	;r2 As==11
    9940:	b0 12 ec 9c 	call	#0x9cec	
    9944:	6f 41       	mov.b	@r1,	r15	
    9946:	6f 93       	cmp.b	#2,	r15	;r3 As==10
    9948:	27 24       	jz	$+80     	;abs 0x9998
    994a:	26 28       	jnc	$+78     	;abs 0x9998
    994c:	6f 92       	cmp.b	#4,	r15	;r2 As==10
    994e:	07 24       	jz	$+16     	;abs 0x995e
    9950:	1f 41 02 00 	mov	2(r1),	r15	;0x0002(r1)
    9954:	0f 93       	tst	r15		
    9956:	20 38       	jl	$+66     	;abs 0x9998
    9958:	3f 90 1f 00 	cmp	#31,	r15	;#0x001f
    995c:	09 38       	jl	$+20     	;abs 0x9970
    995e:	c1 93 01 00 	tst.b	1(r1)		;0x0001(r1)
    9962:	25 20       	jnz	$+76     	;abs 0x99ae
    9964:	3e 43       	mov	#-1,	r14	;r3 As==11
    9966:	3f 40 ff 7f 	mov	#32767,	r15	;#0x7fff
    996a:	31 50 0c 00 	add	#12,	r1	;#0x000c
    996e:	30 41       	ret			
    9970:	3d 40 1e 00 	mov	#30,	r13	;#0x001e
    9974:	4d 8f       	sub.b	r15,	r13	
    9976:	7d f0 1f 00 	and.b	#31,	r13	;#0x001f
    997a:	1e 41 04 00 	mov	4(r1),	r14	;0x0004(r1)
    997e:	1f 41 06 00 	mov	6(r1),	r15	;0x0006(r1)
    9982:	0f 20       	jnz	$+32     	;abs 0x99a2
    9984:	c1 93 01 00 	tst.b	1(r1)		;0x0001(r1)
    9988:	f0 27       	jz	$-30     	;abs 0x996a
    998a:	3e e3       	inv	r14		
    998c:	3f e3       	inv	r15		
    998e:	1e 53       	inc	r14		
    9990:	0f 63       	adc	r15		
    9992:	31 50 0c 00 	add	#12,	r1	;#0x000c
    9996:	30 41       	ret			
    9998:	0e 43       	clr	r14		
    999a:	0f 43       	clr	r15		
    999c:	31 50 0c 00 	add	#12,	r1	;#0x000c
    99a0:	30 41       	ret			
    99a2:	12 c3       	clrc			
    99a4:	0f 10       	rrc	r15		
    99a6:	0e 10       	rrc	r14		
    99a8:	7d 53       	add.b	#-1,	r13	;r3 As==11
    99aa:	fb 23       	jnz	$-8      	;abs 0x99a2
    99ac:	eb 3f       	jmp	$-40     	;abs 0x9984
    99ae:	0e 43       	clr	r14		
    99b0:	3f 40 00 80 	mov	#-32768,r15	;#0x8000
    99b4:	31 50 0c 00 	add	#12,	r1	;#0x000c
    99b8:	30 41       	ret			

000099ba <__floatunsisf>:
    99ba:	0b 12       	push	r11		
    99bc:	0a 12       	push	r10		
    99be:	09 12       	push	r9		
    99c0:	08 12       	push	r8		
    99c2:	31 82       	sub	#8,	r1	;r2 As==11
    99c4:	0a 4e       	mov	r14,	r10	
    99c6:	0b 4f       	mov	r15,	r11	
    99c8:	c1 43 01 00 	mov.b	#0,	1(r1)	;r3 As==00, 0x0001(r1)
    99cc:	0e 93       	tst	r14		
    99ce:	0d 20       	jnz	$+28     	;abs 0x99ea
    99d0:	0b 93       	tst	r11		
    99d2:	0b 20       	jnz	$+24     	;abs 0x99ea
    99d4:	e1 43 00 00 	mov.b	#2,	0(r1)	;r3 As==10, 0x0000(r1)
    99d8:	0f 41       	mov	r1,	r15	
    99da:	b0 12 12 9b 	call	#0x9b12	
    99de:	31 52       	add	#8,	r1	;r2 As==11
    99e0:	38 41       	pop	r8		
    99e2:	39 41       	pop	r9		
    99e4:	3a 41       	pop	r10		
    99e6:	3b 41       	pop	r11		
    99e8:	30 41       	ret			
    99ea:	f1 40 03 00 	mov.b	#3,	0(r1)	;#0x0003, 0x0000(r1)
    99ee:	00 00 
    99f0:	b1 40 1e 00 	mov	#30,	2(r1)	;#0x001e, 0x0002(r1)
    99f4:	02 00 
    99f6:	0e 4a       	mov	r10,	r14	
    99f8:	0f 4b       	mov	r11,	r15	
    99fa:	b0 12 a0 9a 	call	#0x9aa0	
    99fe:	09 4f       	mov	r15,	r9	
    9a00:	39 53       	add	#-1,	r9	;r3 As==11
    9a02:	09 93       	tst	r9		
    9a04:	18 38       	jl	$+50     	;abs 0x9a36
    9a06:	41 24       	jz	$+132    	;abs 0x9a8a
    9a08:	4f 49       	mov.b	r9,	r15	
    9a0a:	7f f0 1f 00 	and.b	#31,	r15	;#0x001f
    9a0e:	81 4a 04 00 	mov	r10,	4(r1)	;0x0004(r1)
    9a12:	81 4b 06 00 	mov	r11,	6(r1)	;0x0006(r1)
    9a16:	06 20       	jnz	$+14     	;abs 0x9a24
    9a18:	3f 40 1e 00 	mov	#30,	r15	;#0x001e
    9a1c:	0f 89       	sub	r9,	r15	
    9a1e:	81 4f 02 00 	mov	r15,	2(r1)	;0x0002(r1)
    9a22:	da 3f       	jmp	$-74     	;abs 0x99d8
    9a24:	91 51 04 00 	rla	4(r1)		;0x0004(r1)
    9a28:	04 00 
    9a2a:	91 61 06 00 	rlc	6(r1)		;0x0006(r1)
    9a2e:	06 00 
    9a30:	7f 53       	add.b	#-1,	r15	;r3 As==11
    9a32:	f8 23       	jnz	$-14     	;abs 0x9a24
    9a34:	f1 3f       	jmp	$-28     	;abs 0x9a18
    9a36:	08 49       	mov	r9,	r8	
    9a38:	38 e3       	inv	r8		
    9a3a:	18 53       	inc	r8		
    9a3c:	4d 48       	mov.b	r8,	r13	
    9a3e:	7d f0 1f 00 	and.b	#31,	r13	;#0x001f
    9a42:	1e 43       	mov	#1,	r14	;r3 As==01
    9a44:	0f 43       	clr	r15		
    9a46:	04 24       	jz	$+10     	;abs 0x9a50
    9a48:	0e 5e       	rla	r14		
    9a4a:	0f 6f       	rlc	r15		
    9a4c:	7d 53       	add.b	#-1,	r13	;r3 As==11
    9a4e:	fc 23       	jnz	$-6      	;abs 0x9a48
    9a50:	3e 53       	add	#-1,	r14	;r3 As==11
    9a52:	3f 63       	addc	#-1,	r15	;r3 As==11
    9a54:	0e fa       	and	r10,	r14	
    9a56:	0f fb       	and	r11,	r15	
    9a58:	1c 43       	mov	#1,	r12	;r3 As==01
    9a5a:	0d 43       	clr	r13		
    9a5c:	0e 93       	tst	r14		
    9a5e:	04 20       	jnz	$+10     	;abs 0x9a68
    9a60:	0f 93       	tst	r15		
    9a62:	02 20       	jnz	$+6      	;abs 0x9a68
    9a64:	0c 43       	clr	r12		
    9a66:	0d 43       	clr	r13		
    9a68:	78 f0 1f 00 	and.b	#31,	r8	;#0x001f
    9a6c:	13 20       	jnz	$+40     	;abs 0x9a94
    9a6e:	0e 4c       	mov	r12,	r14	
    9a70:	0f 4d       	mov	r13,	r15	
    9a72:	0e da       	bis	r10,	r14	
    9a74:	0f db       	bis	r11,	r15	
    9a76:	81 4e 04 00 	mov	r14,	4(r1)	;0x0004(r1)
    9a7a:	81 4f 06 00 	mov	r15,	6(r1)	;0x0006(r1)
    9a7e:	3f 40 1e 00 	mov	#30,	r15	;#0x001e
    9a82:	0f 89       	sub	r9,	r15	
    9a84:	81 4f 02 00 	mov	r15,	2(r1)	;0x0002(r1)
    9a88:	a7 3f       	jmp	$-176    	;abs 0x99d8
    9a8a:	81 4a 04 00 	mov	r10,	4(r1)	;0x0004(r1)
    9a8e:	81 4b 06 00 	mov	r11,	6(r1)	;0x0006(r1)
    9a92:	a2 3f       	jmp	$-186    	;abs 0x99d8
    9a94:	12 c3       	clrc			
    9a96:	0b 10       	rrc	r11		
    9a98:	0a 10       	rrc	r10		
    9a9a:	78 53       	add.b	#-1,	r8	;r3 As==11
    9a9c:	fb 23       	jnz	$-8      	;abs 0x9a94
    9a9e:	e7 3f       	jmp	$-48     	;abs 0x9a6e

00009aa0 <__clzsi2>:
    9aa0:	0b 12       	push	r11		
    9aa2:	0a 12       	push	r10		
    9aa4:	09 12       	push	r9		
    9aa6:	1f 93       	cmp	#1,	r15	;r3 As==01
    9aa8:	17 2c       	jc	$+48     	;abs 0x9ad8
    9aaa:	3e 90 00 01 	cmp	#256,	r14	;#0x0100
    9aae:	2c 28       	jnc	$+90     	;abs 0x9b08
    9ab0:	3a 40 18 00 	mov	#24,	r10	;#0x0018
    9ab4:	0b 43       	clr	r11		
    9ab6:	39 42       	mov	#8,	r9	;r2 As==11
    9ab8:	49 49       	mov.b	r9,	r9	
    9aba:	0c 4e       	mov	r14,	r12	
    9abc:	0d 4f       	mov	r15,	r13	
    9abe:	49 93       	tst.b	r9		
    9ac0:	17 20       	jnz	$+48     	;abs 0x9af0
    9ac2:	3c 50 cc b0 	add	#-20276,r12	;#0xb0cc
    9ac6:	6e 4c       	mov.b	@r12,	r14	
    9ac8:	0f 43       	clr	r15		
    9aca:	0a 8e       	sub	r14,	r10	
    9acc:	0b 7f       	subc	r15,	r11	
    9ace:	0f 4a       	mov	r10,	r15	
    9ad0:	39 41       	pop	r9		
    9ad2:	3a 41       	pop	r10		
    9ad4:	3b 41       	pop	r11		
    9ad6:	30 41       	ret			
    9ad8:	3f 90 00 01 	cmp	#256,	r15	;#0x0100
    9adc:	0f 28       	jnc	$+32     	;abs 0x9afc
    9ade:	3a 42       	mov	#8,	r10	;r2 As==11
    9ae0:	0b 43       	clr	r11		
    9ae2:	39 40 18 00 	mov	#24,	r9	;#0x0018
    9ae6:	49 49       	mov.b	r9,	r9	
    9ae8:	0c 4e       	mov	r14,	r12	
    9aea:	0d 4f       	mov	r15,	r13	
    9aec:	49 93       	tst.b	r9		
    9aee:	e9 27       	jz	$-44     	;abs 0x9ac2
    9af0:	12 c3       	clrc			
    9af2:	0d 10       	rrc	r13		
    9af4:	0c 10       	rrc	r12		
    9af6:	79 53       	add.b	#-1,	r9	;r3 As==11
    9af8:	fb 23       	jnz	$-8      	;abs 0x9af0
    9afa:	e3 3f       	jmp	$-56     	;abs 0x9ac2
    9afc:	3a 40 10 00 	mov	#16,	r10	;#0x0010
    9b00:	0b 43       	clr	r11		
    9b02:	39 40 10 00 	mov	#16,	r9	;#0x0010
    9b06:	ef 3f       	jmp	$-32     	;abs 0x9ae6
    9b08:	3a 40 20 00 	mov	#32,	r10	;#0x0020
    9b0c:	0b 43       	clr	r11		
    9b0e:	09 43       	clr	r9		
    9b10:	ea 3f       	jmp	$-42     	;abs 0x9ae6

00009b12 <__pack_f>:
    9b12:	0b 12       	push	r11		
    9b14:	0a 12       	push	r10		
    9b16:	09 12       	push	r9		
    9b18:	08 12       	push	r8		
    9b1a:	0d 4f       	mov	r15,	r13	
    9b1c:	1e 4f 04 00 	mov	4(r15),	r14	;0x0004(r15)
    9b20:	1f 4f 06 00 	mov	6(r15),	r15	;0x0006(r15)
    9b24:	5b 4d 01 00 	mov.b	1(r13),	r11	;0x0001(r13)
    9b28:	6c 4d       	mov.b	@r13,	r12	
    9b2a:	6c 93       	cmp.b	#2,	r12	;r3 As==10
    9b2c:	6e 28       	jnc	$+222    	;abs 0x9c0a
    9b2e:	6c 92       	cmp.b	#4,	r12	;r2 As==10
    9b30:	68 24       	jz	$+210    	;abs 0x9c02
    9b32:	6c 93       	cmp.b	#2,	r12	;r3 As==10
    9b34:	36 24       	jz	$+110    	;abs 0x9ba2
    9b36:	0e 93       	tst	r14		
    9b38:	32 24       	jz	$+102    	;abs 0x9b9e
    9b3a:	19 4d 02 00 	mov	2(r13),	r9	;0x0002(r13)
    9b3e:	39 90 82 ff 	cmp	#-126,	r9	;#0xff82
    9b42:	6b 38       	jl	$+216    	;abs 0x9c1a
    9b44:	39 90 80 00 	cmp	#128,	r9	;#0x0080
    9b48:	5c 34       	jge	$+186    	;abs 0x9c02
    9b4a:	0c 4e       	mov	r14,	r12	
    9b4c:	0d 4f       	mov	r15,	r13	
    9b4e:	3c f0 7f 00 	and	#127,	r12	;#0x007f
    9b52:	0d f3       	and	#0,	r13	;r3 As==00
    9b54:	3c 90 40 00 	cmp	#64,	r12	;#0x0040
    9b58:	3e 24       	jz	$+126    	;abs 0x9bd6
    9b5a:	3e 50 3f 00 	add	#63,	r14	;#0x003f
    9b5e:	0f 63       	adc	r15		
    9b60:	0f 93       	tst	r15		
    9b62:	48 38       	jl	$+146    	;abs 0x9bf4
    9b64:	0c 49       	mov	r9,	r12	
    9b66:	3c 50 7f 00 	add	#127,	r12	;#0x007f
    9b6a:	12 c3       	clrc			
    9b6c:	0f 10       	rrc	r15		
    9b6e:	0e 10       	rrc	r14		
    9b70:	12 c3       	clrc			
    9b72:	0f 10       	rrc	r15		
    9b74:	0e 10       	rrc	r14		
    9b76:	12 c3       	clrc			
    9b78:	0f 10       	rrc	r15		
    9b7a:	0e 10       	rrc	r14		
    9b7c:	12 c3       	clrc			
    9b7e:	0f 10       	rrc	r15		
    9b80:	0e 10       	rrc	r14		
    9b82:	12 c3       	clrc			
    9b84:	0f 10       	rrc	r15		
    9b86:	0e 10       	rrc	r14		
    9b88:	12 c3       	clrc			
    9b8a:	0f 10       	rrc	r15		
    9b8c:	0e 10       	rrc	r14		
    9b8e:	12 c3       	clrc			
    9b90:	0f 10       	rrc	r15		
    9b92:	0e 10       	rrc	r14		
    9b94:	3e f3       	and	#-1,	r14	;r3 As==11
    9b96:	3f f0 7f 00 	and	#127,	r15	;#0x007f
    9b9a:	4c 4c       	mov.b	r12,	r12	
    9b9c:	05 3c       	jmp	$+12     	;abs 0x9ba8
    9b9e:	0f 93       	tst	r15		
    9ba0:	cc 23       	jnz	$-102    	;abs 0x9b3a
    9ba2:	4c 43       	clr.b	r12		
    9ba4:	0e 43       	clr	r14		
    9ba6:	0f 43       	clr	r15		
    9ba8:	4d 4c       	mov.b	r12,	r13	
    9baa:	0d 5d       	rla	r13		
    9bac:	0d 5d       	rla	r13		
    9bae:	0d 5d       	rla	r13		
    9bb0:	0d 5d       	rla	r13		
    9bb2:	0d 5d       	rla	r13		
    9bb4:	0d 5d       	rla	r13		
    9bb6:	0d 5d       	rla	r13		
    9bb8:	3f f0 7f 00 	and	#127,	r15	;#0x007f
    9bbc:	0f dd       	bis	r13,	r15	
    9bbe:	4b 4b       	mov.b	r11,	r11	
    9bc0:	0b 11       	rra	r11		
    9bc2:	0b 43       	clr	r11		
    9bc4:	0b 10       	rrc	r11		
    9bc6:	0d 4f       	mov	r15,	r13	
    9bc8:	0d db       	bis	r11,	r13	
    9bca:	0f 4d       	mov	r13,	r15	
    9bcc:	38 41       	pop	r8		
    9bce:	39 41       	pop	r9		
    9bd0:	3a 41       	pop	r10		
    9bd2:	3b 41       	pop	r11		
    9bd4:	30 41       	ret			
    9bd6:	0d 93       	tst	r13		
    9bd8:	c0 23       	jnz	$-126    	;abs 0x9b5a
    9bda:	0c 4e       	mov	r14,	r12	
    9bdc:	0d 4f       	mov	r15,	r13	
    9bde:	3c f0 80 00 	and	#128,	r12	;#0x0080
    9be2:	0d f3       	and	#0,	r13	;r3 As==00
    9be4:	0c 93       	tst	r12		
    9be6:	02 20       	jnz	$+6      	;abs 0x9bec
    9be8:	0d 93       	tst	r13		
    9bea:	ba 27       	jz	$-138    	;abs 0x9b60
    9bec:	3e 50 40 00 	add	#64,	r14	;#0x0040
    9bf0:	0f 63       	adc	r15		
    9bf2:	b6 3f       	jmp	$-146    	;abs 0x9b60
    9bf4:	12 c3       	clrc			
    9bf6:	0f 10       	rrc	r15		
    9bf8:	0e 10       	rrc	r14		
    9bfa:	0c 49       	mov	r9,	r12	
    9bfc:	3c 50 80 00 	add	#128,	r12	;#0x0080
    9c00:	b4 3f       	jmp	$-150    	;abs 0x9b6a
    9c02:	7c 43       	mov.b	#-1,	r12	;r3 As==11
    9c04:	0e 43       	clr	r14		
    9c06:	0f 43       	clr	r15		
    9c08:	cf 3f       	jmp	$-96     	;abs 0x9ba8
    9c0a:	0e d3       	bis	#0,	r14	;r3 As==00
    9c0c:	3f d0 10 00 	bis	#16,	r15	;#0x0010
    9c10:	3e f3       	and	#-1,	r14	;r3 As==11
    9c12:	3f f0 7f 00 	and	#127,	r15	;#0x007f
    9c16:	7c 43       	mov.b	#-1,	r12	;r3 As==11
    9c18:	c7 3f       	jmp	$-112    	;abs 0x9ba8
    9c1a:	3d 40 82 ff 	mov	#-126,	r13	;#0xff82
    9c1e:	0d 89       	sub	r9,	r13	
    9c20:	3d 90 1a 00 	cmp	#26,	r13	;#0x001a
    9c24:	50 34       	jge	$+162    	;abs 0x9cc6
    9c26:	4c 4d       	mov.b	r13,	r12	
    9c28:	7c f0 1f 00 	and.b	#31,	r12	;#0x001f
    9c2c:	08 4e       	mov	r14,	r8	
    9c2e:	09 4f       	mov	r15,	r9	
    9c30:	05 24       	jz	$+12     	;abs 0x9c3c
    9c32:	12 c3       	clrc			
    9c34:	09 10       	rrc	r9		
    9c36:	08 10       	rrc	r8		
    9c38:	7c 53       	add.b	#-1,	r12	;r3 As==11
    9c3a:	fb 23       	jnz	$-8      	;abs 0x9c32
    9c3c:	4a 4d       	mov.b	r13,	r10	
    9c3e:	7a f0 1f 00 	and.b	#31,	r10	;#0x001f
    9c42:	1c 43       	mov	#1,	r12	;r3 As==01
    9c44:	0d 43       	clr	r13		
    9c46:	04 24       	jz	$+10     	;abs 0x9c50
    9c48:	0c 5c       	rla	r12		
    9c4a:	0d 6d       	rlc	r13		
    9c4c:	7a 53       	add.b	#-1,	r10	;r3 As==11
    9c4e:	fc 23       	jnz	$-6      	;abs 0x9c48
    9c50:	3c 53       	add	#-1,	r12	;r3 As==11
    9c52:	3d 63       	addc	#-1,	r13	;r3 As==11
    9c54:	0c fe       	and	r14,	r12	
    9c56:	0d ff       	and	r15,	r13	
    9c58:	1e 43       	mov	#1,	r14	;r3 As==01
    9c5a:	0f 43       	clr	r15		
    9c5c:	0c 93       	tst	r12		
    9c5e:	04 20       	jnz	$+10     	;abs 0x9c68
    9c60:	0d 93       	tst	r13		
    9c62:	02 20       	jnz	$+6      	;abs 0x9c68
    9c64:	0e 43       	clr	r14		
    9c66:	0f 43       	clr	r15		
    9c68:	0c 4e       	mov	r14,	r12	
    9c6a:	0d 4f       	mov	r15,	r13	
    9c6c:	0c d8       	bis	r8,	r12	
    9c6e:	0d d9       	bis	r9,	r13	
    9c70:	0e 4c       	mov	r12,	r14	
    9c72:	0f 4d       	mov	r13,	r15	
    9c74:	3e f0 7f 00 	and	#127,	r14	;#0x007f
    9c78:	0f f3       	and	#0,	r15	;r3 As==00
    9c7a:	3e 90 40 00 	cmp	#64,	r14	;#0x0040
    9c7e:	26 24       	jz	$+78     	;abs 0x9ccc
    9c80:	3c 50 3f 00 	add	#63,	r12	;#0x003f
    9c84:	0d 63       	adc	r13		
    9c86:	0e 4c       	mov	r12,	r14	
    9c88:	0f 4d       	mov	r13,	r15	
    9c8a:	12 c3       	clrc			
    9c8c:	0f 10       	rrc	r15		
    9c8e:	0e 10       	rrc	r14		
    9c90:	12 c3       	clrc			
    9c92:	0f 10       	rrc	r15		
    9c94:	0e 10       	rrc	r14		
    9c96:	12 c3       	clrc			
    9c98:	0f 10       	rrc	r15		
    9c9a:	0e 10       	rrc	r14		
    9c9c:	12 c3       	clrc			
    9c9e:	0f 10       	rrc	r15		
    9ca0:	0e 10       	rrc	r14		
    9ca2:	12 c3       	clrc			
    9ca4:	0f 10       	rrc	r15		
    9ca6:	0e 10       	rrc	r14		
    9ca8:	12 c3       	clrc			
    9caa:	0f 10       	rrc	r15		
    9cac:	0e 10       	rrc	r14		
    9cae:	12 c3       	clrc			
    9cb0:	0f 10       	rrc	r15		
    9cb2:	0e 10       	rrc	r14		
    9cb4:	3e f3       	and	#-1,	r14	;r3 As==11
    9cb6:	3f f0 7f 00 	and	#127,	r15	;#0x007f
    9cba:	5c 43       	mov.b	#1,	r12	;r3 As==01
    9cbc:	3d 90 00 40 	cmp	#16384,	r13	;#0x4000
    9cc0:	73 2f       	jc	$-280    	;abs 0x9ba8
    9cc2:	4c 43       	clr.b	r12		
    9cc4:	71 3f       	jmp	$-284    	;abs 0x9ba8
    9cc6:	0c 43       	clr	r12		
    9cc8:	0d 43       	clr	r13		
    9cca:	da 3f       	jmp	$-74     	;abs 0x9c80
    9ccc:	0f 93       	tst	r15		
    9cce:	d8 23       	jnz	$-78     	;abs 0x9c80
    9cd0:	0e 4c       	mov	r12,	r14	
    9cd2:	0f 4d       	mov	r13,	r15	
    9cd4:	3e f0 80 00 	and	#128,	r14	;#0x0080
    9cd8:	0f f3       	and	#0,	r15	;r3 As==00
    9cda:	0e 93       	tst	r14		
    9cdc:	04 24       	jz	$+10     	;abs 0x9ce6
    9cde:	3c 50 40 00 	add	#64,	r12	;#0x0040
    9ce2:	0d 63       	adc	r13		
    9ce4:	d0 3f       	jmp	$-94     	;abs 0x9c86
    9ce6:	0f 93       	tst	r15		
    9ce8:	ce 27       	jz	$-98     	;abs 0x9c86
    9cea:	f9 3f       	jmp	$-12     	;abs 0x9cde

00009cec <__unpack_f>:
    9cec:	0b 12       	push	r11		
    9cee:	0a 12       	push	r10		
    9cf0:	09 12       	push	r9		
    9cf2:	08 12       	push	r8		
    9cf4:	2a 4f       	mov	@r15,	r10	
    9cf6:	59 4f 02 00 	mov.b	2(r15),	r9	;0x0002(r15)
    9cfa:	0b 49       	mov	r9,	r11	
    9cfc:	3b f0 7f 00 	and	#127,	r11	;#0x007f
    9d00:	08 4a       	mov	r10,	r8	
    9d02:	09 4b       	mov	r11,	r9	
    9d04:	1d 4f 02 00 	mov	2(r15),	r13	;0x0002(r15)
    9d08:	12 c3       	clrc			
    9d0a:	0d 10       	rrc	r13		
    9d0c:	12 c3       	clrc			
    9d0e:	0d 10       	rrc	r13		
    9d10:	12 c3       	clrc			
    9d12:	0d 10       	rrc	r13		
    9d14:	12 c3       	clrc			
    9d16:	0d 10       	rrc	r13		
    9d18:	12 c3       	clrc			
    9d1a:	0d 10       	rrc	r13		
    9d1c:	12 c3       	clrc			
    9d1e:	0d 10       	rrc	r13		
    9d20:	12 c3       	clrc			
    9d22:	0d 10       	rrc	r13		
    9d24:	4d 4d       	mov.b	r13,	r13	
    9d26:	5f 4f 03 00 	mov.b	3(r15),	r15	;0x0003(r15)
    9d2a:	4f 5f       	rla.b	r15		
    9d2c:	0f 43       	clr	r15		
    9d2e:	0f 6f       	rlc	r15		
    9d30:	ce 4f 01 00 	mov.b	r15,	1(r14)	;0x0001(r14)
    9d34:	0d 93       	tst	r13		
    9d36:	2f 20       	jnz	$+96     	;abs 0x9d96
    9d38:	0a 93       	tst	r10		
    9d3a:	55 24       	jz	$+172    	;abs 0x9de6
    9d3c:	be 40 82 ff 	mov	#-126,	2(r14)	;#0xff82, 0x0002(r14)
    9d40:	02 00 
    9d42:	0c 48       	mov	r8,	r12	
    9d44:	0d 49       	mov	r9,	r13	
    9d46:	0c 5c       	rla	r12		
    9d48:	0d 6d       	rlc	r13		
    9d4a:	0c 5c       	rla	r12		
    9d4c:	0d 6d       	rlc	r13		
    9d4e:	0c 5c       	rla	r12		
    9d50:	0d 6d       	rlc	r13		
    9d52:	0c 5c       	rla	r12		
    9d54:	0d 6d       	rlc	r13		
    9d56:	0c 5c       	rla	r12		
    9d58:	0d 6d       	rlc	r13		
    9d5a:	0c 5c       	rla	r12		
    9d5c:	0d 6d       	rlc	r13		
    9d5e:	0c 5c       	rla	r12		
    9d60:	0d 6d       	rlc	r13		
    9d62:	fe 40 03 00 	mov.b	#3,	0(r14)	;#0x0003, 0x0000(r14)
    9d66:	00 00 
    9d68:	3d 90 00 40 	cmp	#16384,	r13	;#0x4000
    9d6c:	0b 2c       	jc	$+24     	;abs 0x9d84
    9d6e:	3f 40 81 ff 	mov	#-127,	r15	;#0xff81
    9d72:	0c 5c       	rla	r12		
    9d74:	0d 6d       	rlc	r13		
    9d76:	0b 4f       	mov	r15,	r11	
    9d78:	3f 53       	add	#-1,	r15	;r3 As==11
    9d7a:	3d 90 00 40 	cmp	#16384,	r13	;#0x4000
    9d7e:	f9 2b       	jnc	$-12     	;abs 0x9d72
    9d80:	8e 4b 02 00 	mov	r11,	2(r14)	;0x0002(r14)
    9d84:	8e 4c 04 00 	mov	r12,	4(r14)	;0x0004(r14)
    9d88:	8e 4d 06 00 	mov	r13,	6(r14)	;0x0006(r14)
    9d8c:	38 41       	pop	r8		
    9d8e:	39 41       	pop	r9		
    9d90:	3a 41       	pop	r10		
    9d92:	3b 41       	pop	r11		
    9d94:	30 41       	ret			
    9d96:	3d 90 ff 00 	cmp	#255,	r13	;#0x00ff
    9d9a:	2e 24       	jz	$+94     	;abs 0x9df8
    9d9c:	3d 50 81 ff 	add	#-127,	r13	;#0xff81
    9da0:	8e 4d 02 00 	mov	r13,	2(r14)	;0x0002(r14)
    9da4:	fe 40 03 00 	mov.b	#3,	0(r14)	;#0x0003, 0x0000(r14)
    9da8:	00 00 
    9daa:	0c 4a       	mov	r10,	r12	
    9dac:	0d 4b       	mov	r11,	r13	
    9dae:	0c 5c       	rla	r12		
    9db0:	0d 6d       	rlc	r13		
    9db2:	0c 5c       	rla	r12		
    9db4:	0d 6d       	rlc	r13		
    9db6:	0c 5c       	rla	r12		
    9db8:	0d 6d       	rlc	r13		
    9dba:	0c 5c       	rla	r12		
    9dbc:	0d 6d       	rlc	r13		
    9dbe:	0c 5c       	rla	r12		
    9dc0:	0d 6d       	rlc	r13		
    9dc2:	0c 5c       	rla	r12		
    9dc4:	0d 6d       	rlc	r13		
    9dc6:	0c 5c       	rla	r12		
    9dc8:	0d 6d       	rlc	r13		
    9dca:	0a 4c       	mov	r12,	r10	
    9dcc:	0b 4d       	mov	r13,	r11	
    9dce:	0a d3       	bis	#0,	r10	;r3 As==00
    9dd0:	3b d0 00 40 	bis	#16384,	r11	;#0x4000
    9dd4:	8e 4a 04 00 	mov	r10,	4(r14)	;0x0004(r14)
    9dd8:	8e 4b 06 00 	mov	r11,	6(r14)	;0x0006(r14)
    9ddc:	38 41       	pop	r8		
    9dde:	39 41       	pop	r9		
    9de0:	3a 41       	pop	r10		
    9de2:	3b 41       	pop	r11		
    9de4:	30 41       	ret			
    9de6:	0b 93       	tst	r11		
    9de8:	a9 23       	jnz	$-172    	;abs 0x9d3c
    9dea:	ee 43 00 00 	mov.b	#2,	0(r14)	;r3 As==10, 0x0000(r14)
    9dee:	38 41       	pop	r8		
    9df0:	39 41       	pop	r9		
    9df2:	3a 41       	pop	r10		
    9df4:	3b 41       	pop	r11		
    9df6:	30 41       	ret			
    9df8:	0a 93       	tst	r10		
    9dfa:	0e 24       	jz	$+30     	;abs 0x9e18
    9dfc:	0a f3       	and	#0,	r10	;r3 As==00
    9dfe:	3b f0 10 00 	and	#16,	r11	;#0x0010
    9e02:	0a 93       	tst	r10		
    9e04:	02 20       	jnz	$+6      	;abs 0x9e0a
    9e06:	0b 93       	tst	r11		
    9e08:	0c 24       	jz	$+26     	;abs 0x9e22
    9e0a:	de 43 00 00 	mov.b	#1,	0(r14)	;r3 As==01, 0x0000(r14)
    9e0e:	8e 48 04 00 	mov	r8,	4(r14)	;0x0004(r14)
    9e12:	8e 49 06 00 	mov	r9,	6(r14)	;0x0006(r14)
    9e16:	e2 3f       	jmp	$-58     	;abs 0x9ddc
    9e18:	0b 93       	tst	r11		
    9e1a:	f0 23       	jnz	$-30     	;abs 0x9dfc
    9e1c:	ee 42 00 00 	mov.b	#4,	0(r14)	;r2 As==10, 0x0000(r14)
    9e20:	dd 3f       	jmp	$-68     	;abs 0x9ddc
    9e22:	ce 43 00 00 	mov.b	#0,	0(r14)	;r3 As==00, 0x0000(r14)
    9e26:	f3 3f       	jmp	$-24     	;abs 0x9e0e

00009e28 <__fpcmp_parts_f>:
    9e28:	0b 12       	push	r11		
    9e2a:	6d 4f       	mov.b	@r15,	r13	
    9e2c:	6d 93       	cmp.b	#2,	r13	;r3 As==10
    9e2e:	12 28       	jnc	$+38     	;abs 0x9e54
    9e30:	6c 4e       	mov.b	@r14,	r12	
    9e32:	6c 93       	cmp.b	#2,	r12	;r3 As==10
    9e34:	0f 28       	jnc	$+32     	;abs 0x9e54
    9e36:	6d 92       	cmp.b	#4,	r13	;r2 As==10
    9e38:	41 24       	jz	$+132    	;abs 0x9ebc
    9e3a:	6c 92       	cmp.b	#4,	r12	;r2 As==10
    9e3c:	11 24       	jz	$+36     	;abs 0x9e60
    9e3e:	6d 93       	cmp.b	#2,	r13	;r3 As==10
    9e40:	0d 24       	jz	$+28     	;abs 0x9e5c
    9e42:	6c 93       	cmp.b	#2,	r12	;r3 As==10
    9e44:	14 24       	jz	$+42     	;abs 0x9e6e
    9e46:	5d 4f 01 00 	mov.b	1(r15),	r13	;0x0001(r15)
    9e4a:	5d 9e 01 00 	cmp.b	1(r14),	r13	;0x0001(r14)
    9e4e:	14 24       	jz	$+42     	;abs 0x9e78
    9e50:	4d 93       	tst.b	r13		
    9e52:	09 20       	jnz	$+20     	;abs 0x9e66
    9e54:	1e 43       	mov	#1,	r14	;r3 As==01
    9e56:	0f 4e       	mov	r14,	r15	
    9e58:	3b 41       	pop	r11		
    9e5a:	30 41       	ret			
    9e5c:	6c 93       	cmp.b	#2,	r12	;r3 As==10
    9e5e:	28 24       	jz	$+82     	;abs 0x9eb0
    9e60:	ce 93 01 00 	tst.b	1(r14)		;0x0001(r14)
    9e64:	f7 23       	jnz	$-16     	;abs 0x9e54
    9e66:	3e 43       	mov	#-1,	r14	;r3 As==11
    9e68:	0f 4e       	mov	r14,	r15	
    9e6a:	3b 41       	pop	r11		
    9e6c:	30 41       	ret			
    9e6e:	cf 93 01 00 	tst.b	1(r15)		;0x0001(r15)
    9e72:	f0 27       	jz	$-30     	;abs 0x9e54
    9e74:	3e 43       	mov	#-1,	r14	;r3 As==11
    9e76:	f8 3f       	jmp	$-14     	;abs 0x9e68
    9e78:	1b 4f 02 00 	mov	2(r15),	r11	;0x0002(r15)
    9e7c:	1c 4e 02 00 	mov	2(r14),	r12	;0x0002(r14)
    9e80:	0c 9b       	cmp	r11,	r12	
    9e82:	e6 3b       	jl	$-50     	;abs 0x9e50
    9e84:	0b 9c       	cmp	r12,	r11	
    9e86:	16 38       	jl	$+46     	;abs 0x9eb4
    9e88:	1b 4f 04 00 	mov	4(r15),	r11	;0x0004(r15)
    9e8c:	1f 4f 06 00 	mov	6(r15),	r15	;0x0006(r15)
    9e90:	1c 4e 04 00 	mov	4(r14),	r12	;0x0004(r14)
    9e94:	1e 4e 06 00 	mov	6(r14),	r14	;0x0006(r14)
    9e98:	0e 9f       	cmp	r15,	r14	
    9e9a:	da 2b       	jnc	$-74     	;abs 0x9e50
    9e9c:	0f 9e       	cmp	r14,	r15	
    9e9e:	02 28       	jnc	$+6      	;abs 0x9ea4
    9ea0:	0c 9b       	cmp	r11,	r12	
    9ea2:	d6 2b       	jnc	$-82     	;abs 0x9e50
    9ea4:	0f 9e       	cmp	r14,	r15	
    9ea6:	06 28       	jnc	$+14     	;abs 0x9eb4
    9ea8:	0e 9f       	cmp	r15,	r14	
    9eaa:	02 28       	jnc	$+6      	;abs 0x9eb0
    9eac:	0b 9c       	cmp	r12,	r11	
    9eae:	02 28       	jnc	$+6      	;abs 0x9eb4
    9eb0:	0e 43       	clr	r14		
    9eb2:	d1 3f       	jmp	$-92     	;abs 0x9e56
    9eb4:	4d 93       	tst.b	r13		
    9eb6:	ce 23       	jnz	$-98     	;abs 0x9e54
    9eb8:	3e 43       	mov	#-1,	r14	;r3 As==11
    9eba:	d6 3f       	jmp	$-82     	;abs 0x9e68
    9ebc:	6c 92       	cmp.b	#4,	r12	;r2 As==10
    9ebe:	d7 23       	jnz	$-80     	;abs 0x9e6e
    9ec0:	5e 4e 01 00 	mov.b	1(r14),	r14	;0x0001(r14)
    9ec4:	5f 4f 01 00 	mov.b	1(r15),	r15	;0x0001(r15)
    9ec8:	0e 8f       	sub	r15,	r14	
    9eca:	c5 3f       	jmp	$-116    	;abs 0x9e56

00009ecc <printf>:
    9ecc:	0d 41       	mov	r1,	r13	
    9ece:	2d 53       	incd	r13		
    9ed0:	3e 4d       	mov	@r13+,	r14	
    9ed2:	3f 40 e0 7c 	mov	#31968,	r15	;#0x7ce0
    9ed6:	b0 12 e8 a0 	call	#0xa0e8	
    9eda:	30 41       	ret			

00009edc <append>:
    9edc:	1e 42 dc 2d 	mov	&0x2ddc,r14	
    9ee0:	1e 93       	cmp	#1,	r14	;r3 As==01
    9ee2:	0b 38       	jl	$+24     	;abs 0x9efa
    9ee4:	1d 42 da 2d 	mov	&0x2dda,r13	
    9ee8:	cd 4f 00 00 	mov.b	r15,	0(r13)	;0x0000(r13)
    9eec:	1d 53       	inc	r13		
    9eee:	82 4d da 2d 	mov	r13,	&0x2dda	
    9ef2:	3e 53       	add	#-1,	r14	;r3 As==11
    9ef4:	82 4e dc 2d 	mov	r14,	&0x2ddc	
    9ef8:	30 41       	ret			
    9efa:	3f 43       	mov	#-1,	r15	;r3 As==11
    9efc:	30 41       	ret			

00009efe <call_vuprintf>:
    9efe:	0b 12       	push	r11		
    9f00:	0a 12       	push	r10		
    9f02:	21 83       	decd	r1		
    9f04:	81 4e 00 00 	mov	r14,	0(r1)	;0x0000(r1)
    9f08:	1a 42 da 2d 	mov	&0x2dda,r10	
    9f0c:	1b 42 dc 2d 	mov	&0x2ddc,r11	
    9f10:	0d 4e       	mov	r14,	r13	
    9f12:	0e 4f       	mov	r15,	r14	
    9f14:	3f 40 dc 9e 	mov	#-24868,r15	;#0x9edc
    9f18:	b0 12 e8 a0 	call	#0xa0e8	
    9f1c:	0f 9b       	cmp	r11,	r15	
    9f1e:	04 38       	jl	$+10     	;abs 0x9f28
    9f20:	0b 5a       	add	r10,	r11	
    9f22:	cb 43 ff ff 	mov.b	#0,	-1(r11)	;r3 As==00, 0xffff(r11)
    9f26:	04 3c       	jmp	$+10     	;abs 0x9f30
    9f28:	1e 42 da 2d 	mov	&0x2dda,r14	
    9f2c:	ce 43 00 00 	mov.b	#0,	0(r14)	;r3 As==00, 0x0000(r14)
    9f30:	21 53       	incd	r1		
    9f32:	3a 41       	pop	r10		
    9f34:	3b 41       	pop	r11		
    9f36:	30 41       	ret			

00009f38 <sprintf>:
    9f38:	92 41 02 00 	mov	2(r1),	&0x2dda	;0x0002(r1)
    9f3c:	da 2d 
    9f3e:	b2 40 ff 7f 	mov	#32767,	&0x2ddc	;#0x7fff
    9f42:	dc 2d 
    9f44:	0e 41       	mov	r1,	r14	
    9f46:	3e 50 06 00 	add	#6,	r14	;#0x0006
    9f4a:	1f 41 04 00 	mov	4(r1),	r15	;0x0004(r1)
    9f4e:	b0 12 fe 9e 	call	#0x9efe	
    9f52:	30 41       	ret			

00009f54 <print_field>:
    9f54:	0b 12       	push	r11		
    9f56:	0a 12       	push	r10		
    9f58:	09 12       	push	r9		
    9f5a:	08 12       	push	r8		
    9f5c:	07 12       	push	r7		
    9f5e:	06 12       	push	r6		
    9f60:	05 12       	push	r5		
    9f62:	04 12       	push	r4		
    9f64:	31 82       	sub	#8,	r1	;r2 As==11
    9f66:	09 4f       	mov	r15,	r9	
    9f68:	06 4e       	mov	r14,	r6	
    9f6a:	0b 4d       	mov	r13,	r11	
    9f6c:	15 41 1a 00 	mov	26(r1),	r5	;0x001a(r1)
    9f70:	1d 41 1c 00 	mov	28(r1),	r13	;0x001c(r1)
    9f74:	07 4d       	mov	r13,	r7	
    9f76:	87 10       	swpb	r7		
    9f78:	4e 47       	mov.b	r7,	r14	
    9f7a:	4c 4d       	mov.b	r13,	r12	
    9f7c:	4f 45       	mov.b	r5,	r15	
    9f7e:	7f b0 40 00 	bit.b	#64,	r15	;#0x0040
    9f82:	11 24       	jz	$+36     	;abs 0x9fa6
    9f84:	f1 40 30 00 	mov.b	#48,	0(r1)	;#0x0030, 0x0000(r1)
    9f88:	00 00 
    9f8a:	0d 45       	mov	r5,	r13	
    9f8c:	8d 10       	swpb	r13		
    9f8e:	5d f3       	and.b	#1,	r13	;r3 As==01
    9f90:	03 24       	jz	$+8      	;abs 0x9f98
    9f92:	7d 40 58 00 	mov.b	#88,	r13	;#0x0058
    9f96:	02 3c       	jmp	$+6      	;abs 0x9f9c
    9f98:	7d 40 78 00 	mov.b	#120,	r13	;#0x0078
    9f9c:	c1 4d 01 00 	mov.b	r13,	1(r1)	;0x0001(r1)
    9fa0:	0a 41       	mov	r1,	r10	
    9fa2:	2a 53       	incd	r10		
    9fa4:	0f 3c       	jmp	$+32     	;abs 0x9fc4
    9fa6:	7f b0 20 00 	bit.b	#32,	r15	;#0x0020
    9faa:	04 24       	jz	$+10     	;abs 0x9fb4
    9fac:	f1 40 30 00 	mov.b	#48,	0(r1)	;#0x0030, 0x0000(r1)
    9fb0:	00 00 
    9fb2:	04 3c       	jmp	$+10     	;abs 0x9fbc
    9fb4:	4c 93       	tst.b	r12		
    9fb6:	05 24       	jz	$+12     	;abs 0x9fc2
    9fb8:	c1 4d 00 00 	mov.b	r13,	0(r1)	;0x0000(r1)
    9fbc:	0a 41       	mov	r1,	r10	
    9fbe:	1a 53       	inc	r10		
    9fc0:	01 3c       	jmp	$+4      	;abs 0x9fc4
    9fc2:	0a 41       	mov	r1,	r10	
    9fc4:	0a 81       	sub	r1,	r10	
    9fc6:	85 10       	swpb	r5		
    9fc8:	65 b2       	bit.b	#4,	r5	;r2 As==10
    9fca:	02 24       	jz	$+6      	;abs 0x9fd0
    9fcc:	08 4e       	mov	r14,	r8	
    9fce:	01 3c       	jmp	$+4      	;abs 0x9fd2
    9fd0:	38 43       	mov	#-1,	r8	;r3 As==11
    9fd2:	7f b0 10 00 	bit.b	#16,	r15	;#0x0010
    9fd6:	47 20       	jnz	$+144    	;abs 0xa066
    9fd8:	0c 46       	mov	r6,	r12	
    9fda:	3c 53       	add	#-1,	r12	;r3 As==11
    9fdc:	1c 53       	inc	r12		
    9fde:	cc 93 00 00 	tst.b	0(r12)		;0x0000(r12)
    9fe2:	fc 23       	jnz	$-6      	;abs 0x9fdc
    9fe4:	0c 86       	sub	r6,	r12	
    9fe6:	0b 9a       	cmp	r10,	r11	
    9fe8:	02 28       	jnc	$+6      	;abs 0x9fee
    9fea:	0b 8a       	sub	r10,	r11	
    9fec:	01 3c       	jmp	$+4      	;abs 0x9ff0
    9fee:	0b 43       	clr	r11		
    9ff0:	65 b3       	bit.b	#2,	r5	;r3 As==10
    9ff2:	05 24       	jz	$+12     	;abs 0x9ffe
    9ff4:	0b 9e       	cmp	r14,	r11	
    9ff6:	02 28       	jnc	$+6      	;abs 0x9ffc
    9ff8:	0b 8e       	sub	r14,	r11	
    9ffa:	01 3c       	jmp	$+4      	;abs 0x9ffe
    9ffc:	0b 43       	clr	r11		
    9ffe:	08 9c       	cmp	r12,	r8	
    a000:	01 2c       	jc	$+4      	;abs 0xa004
    a002:	0c 48       	mov	r8,	r12	
    a004:	4f 93       	tst.b	r15		
    a006:	11 38       	jl	$+36     	;abs 0xa02a
    a008:	f1 40 20 00 	mov.b	#32,	2(r1)	;#0x0020, 0x0002(r1)
    a00c:	02 00 
    a00e:	04 43       	clr	r4		
    a010:	0d 43       	clr	r13		
    a012:	16 3c       	jmp	$+46     	;abs 0xa040
    a014:	0f 41       	mov	r1,	r15	
    a016:	0f 54       	add	r4,	r15	
    a018:	6f 4f       	mov.b	@r15,	r15	
    a01a:	8f 11       	sxt	r15		
    a01c:	14 53       	inc	r4		
    a01e:	81 4c 06 00 	mov	r12,	6(r1)	;0x0006(r1)
    a022:	89 12       	call	r9		
    a024:	1c 41 06 00 	mov	6(r1),	r12	;0x0006(r1)
    a028:	01 3c       	jmp	$+4      	;abs 0xa02c
    a02a:	04 43       	clr	r4		
    a02c:	04 9a       	cmp	r10,	r4	
    a02e:	f2 3b       	jl	$-26     	;abs 0xa014
    a030:	04 4a       	mov	r10,	r4	
    a032:	0a 93       	tst	r10		
    a034:	01 34       	jge	$+4      	;abs 0xa038
    a036:	04 43       	clr	r4		
    a038:	0d 4a       	mov	r10,	r13	
    a03a:	f1 40 30 00 	mov.b	#48,	2(r1)	;#0x0030, 0x0002(r1)
    a03e:	02 00 
    a040:	0c 8d       	sub	r13,	r12	
    a042:	81 4c 04 00 	mov	r12,	4(r1)	;0x0004(r1)
    a046:	09 3c       	jmp	$+20     	;abs 0xa05a
    a048:	5f 41 02 00 	mov.b	2(r1),	r15	;0x0002(r1)
    a04c:	8f 11       	sxt	r15		
    a04e:	81 4d 06 00 	mov	r13,	6(r1)	;0x0006(r1)
    a052:	89 12       	call	r9		
    a054:	1d 41 06 00 	mov	6(r1),	r13	;0x0006(r1)
    a058:	1d 53       	inc	r13		
    a05a:	1f 41 04 00 	mov	4(r1),	r15	;0x0004(r1)
    a05e:	0f 5d       	add	r13,	r15	
    a060:	0f 9b       	cmp	r11,	r15	
    a062:	f2 2b       	jnc	$-26     	;abs 0xa048
    a064:	02 3c       	jmp	$+6      	;abs 0xa06a
    a066:	04 43       	clr	r4		
    a068:	0d 43       	clr	r13		
    a06a:	0d 84       	sub	r4,	r13	
    a06c:	81 4d 04 00 	mov	r13,	4(r1)	;0x0004(r1)
    a070:	05 3c       	jmp	$+12     	;abs 0xa07c
    a072:	14 53       	inc	r4		
    a074:	0d 51       	add	r1,	r13	
    a076:	6f 4d       	mov.b	@r13,	r15	
    a078:	8f 11       	sxt	r15		
    a07a:	89 12       	call	r9		
    a07c:	0d 44       	mov	r4,	r13	
    a07e:	1f 41 04 00 	mov	4(r1),	r15	;0x0004(r1)
    a082:	0f 54       	add	r4,	r15	
    a084:	81 4f 02 00 	mov	r15,	2(r1)	;0x0002(r1)
    a088:	04 9a       	cmp	r10,	r4	
    a08a:	f3 3b       	jl	$-24     	;abs 0xa072
    a08c:	65 f3       	and.b	#2,	r5	;r3 As==10
    a08e:	05 24       	jz	$+12     	;abs 0xa09a
    a090:	4a 47       	mov.b	r7,	r10	
    a092:	0a 3c       	jmp	$+22     	;abs 0xa0a8
    a094:	4f 47       	mov.b	r7,	r15	
    a096:	1f 51 02 00 	add	2(r1),	r15	;0x0002(r1)
    a09a:	08 5f       	add	r15,	r8	
    a09c:	0a 4f       	mov	r15,	r10	
    a09e:	06 8f       	sub	r15,	r6	
    a0a0:	0a 3c       	jmp	$+22     	;abs 0xa0b6
    a0a2:	3f 40 30 00 	mov	#48,	r15	;#0x0030
    a0a6:	89 12       	call	r9		
    a0a8:	7a 53       	add.b	#-1,	r10	;r3 As==11
    a0aa:	7a 93       	cmp.b	#-1,	r10	;r3 As==11
    a0ac:	fa 23       	jnz	$-10     	;abs 0xa0a2
    a0ae:	f2 3f       	jmp	$-26     	;abs 0xa094
    a0b0:	8f 11       	sxt	r15		
    a0b2:	89 12       	call	r9		
    a0b4:	1a 53       	inc	r10		
    a0b6:	0f 46       	mov	r6,	r15	
    a0b8:	0f 5a       	add	r10,	r15	
    a0ba:	6f 4f       	mov.b	@r15,	r15	
    a0bc:	4f 93       	tst.b	r15		
    a0be:	07 24       	jz	$+16     	;abs 0xa0ce
    a0c0:	0a 98       	cmp	r8,	r10	
    a0c2:	f6 23       	jnz	$-18     	;abs 0xa0b0
    a0c4:	04 3c       	jmp	$+10     	;abs 0xa0ce
    a0c6:	3f 40 20 00 	mov	#32,	r15	;#0x0020
    a0ca:	89 12       	call	r9		
    a0cc:	1a 53       	inc	r10		
    a0ce:	0a 9b       	cmp	r11,	r10	
    a0d0:	fa 2b       	jnc	$-10     	;abs 0xa0c6
    a0d2:	0f 4a       	mov	r10,	r15	
    a0d4:	31 52       	add	#8,	r1	;r2 As==11
    a0d6:	34 41       	pop	r4		
    a0d8:	35 41       	pop	r5		
    a0da:	36 41       	pop	r6		
    a0dc:	37 41       	pop	r7		
    a0de:	38 41       	pop	r8		
    a0e0:	39 41       	pop	r9		
    a0e2:	3a 41       	pop	r10		
    a0e4:	3b 41       	pop	r11		
    a0e6:	30 41       	ret			

0000a0e8 <vuprintf>:
    a0e8:	0b 12       	push	r11		
    a0ea:	0a 12       	push	r10		
    a0ec:	09 12       	push	r9		
    a0ee:	08 12       	push	r8		
    a0f0:	07 12       	push	r7		
    a0f2:	06 12       	push	r6		
    a0f4:	05 12       	push	r5		
    a0f6:	04 12       	push	r4		
    a0f8:	31 50 c4 ff 	add	#-60,	r1	;#0xffc4
    a0fc:	81 4f 38 00 	mov	r15,	56(r1)	;0x0038(r1)
    a100:	0b 4d       	mov	r13,	r11	
    a102:	81 4e 3a 00 	mov	r14,	58(r1)	;0x003a(r1)
    a106:	c1 43 29 00 	mov.b	#0,	41(r1)	;r3 As==00, 0x0029(r1)
    a10a:	c1 43 21 00 	mov.b	#0,	33(r1)	;r3 As==00, 0x0021(r1)
    a10e:	c1 43 28 00 	mov.b	#0,	40(r1)	;r3 As==00, 0x0028(r1)
    a112:	c1 43 20 00 	mov.b	#0,	32(r1)	;r3 As==00, 0x0020(r1)
    a116:	81 43 2c 00 	mov	#0,	44(r1)	;r3 As==00, 0x002c(r1)
    a11a:	81 43 1e 00 	mov	#0,	30(r1)	;r3 As==00, 0x001e(r1)
    a11e:	0d 43       	clr	r13		
    a120:	81 43 22 00 	mov	#0,	34(r1)	;r3 As==00, 0x0022(r1)
    a124:	0c 41       	mov	r1,	r12	
    a126:	3c 50 18 00 	add	#24,	r12	;#0x0018
    a12a:	81 4c 1c 00 	mov	r12,	28(r1)	;0x001c(r1)
    a12e:	30 40 f8 a6 	br	#0xa6f8	
    a132:	0d 93       	tst	r13		
    a134:	1d 20       	jnz	$+60     	;abs 0xa170
    a136:	7f 90 25 00 	cmp.b	#37,	r15	;#0x0025
    a13a:	13 20       	jnz	$+40     	;abs 0xa162
    a13c:	81 43 18 00 	mov	#0,	24(r1)	;r3 As==00, 0x0018(r1)
    a140:	81 43 1a 00 	mov	#0,	26(r1)	;r3 As==00, 0x001a(r1)
    a144:	81 4e 3a 00 	mov	r14,	58(r1)	;0x003a(r1)
    a148:	c1 43 29 00 	mov.b	#0,	41(r1)	;r3 As==00, 0x0029(r1)
    a14c:	c1 43 21 00 	mov.b	#0,	33(r1)	;r3 As==00, 0x0021(r1)
    a150:	c1 43 28 00 	mov.b	#0,	40(r1)	;r3 As==00, 0x0028(r1)
    a154:	c1 43 20 00 	mov.b	#0,	32(r1)	;r3 As==00, 0x0020(r1)
    a158:	81 43 2c 00 	mov	#0,	44(r1)	;r3 As==00, 0x002c(r1)
    a15c:	30 40 ee a6 	br	#0xa6ee	
    a160:	0b 4a       	mov	r10,	r11	
    a162:	8f 11       	sxt	r15		
    a164:	91 12 3a 00 	call	58(r1)		;0x003a(r1)
    a168:	91 53 22 00 	inc	34(r1)		;0x0022(r1)
    a16c:	30 40 d4 a6 	br	#0xa6d4	
    a170:	7f 90 63 00 	cmp.b	#99,	r15	;#0x0063
    a174:	c9 24       	jz	$+404    	;abs 0xa308
    a176:	7f 90 64 00 	cmp.b	#100,	r15	;#0x0064
    a17a:	27 34       	jge	$+80     	;abs 0xa1ca
    a17c:	7f 90 30 00 	cmp.b	#48,	r15	;#0x0030
    a180:	91 24       	jz	$+292    	;abs 0xa2a4
    a182:	7f 90 31 00 	cmp.b	#49,	r15	;#0x0031
    a186:	1a 34       	jge	$+54     	;abs 0xa1bc
    a188:	7f 90 2a 00 	cmp.b	#42,	r15	;#0x002a
    a18c:	77 24       	jz	$+240    	;abs 0xa27c
    a18e:	7f 90 2b 00 	cmp.b	#43,	r15	;#0x002b
    a192:	0a 34       	jge	$+22     	;abs 0xa1a8
    a194:	7f 90 23 00 	cmp.b	#35,	r15	;#0x0023
    a198:	41 24       	jz	$+132    	;abs 0xa21c
    a19a:	7f 90 25 00 	cmp.b	#37,	r15	;#0x0025
    a19e:	e1 27       	jz	$-60     	;abs 0xa162
    a1a0:	7f 90 20 00 	cmp.b	#32,	r15	;#0x0020
    a1a4:	32 20       	jnz	$+102    	;abs 0xa20a
    a1a6:	56 3c       	jmp	$+174    	;abs 0xa254
    a1a8:	7f 90 2d 00 	cmp.b	#45,	r15	;#0x002d
    a1ac:	49 24       	jz	$+148    	;abs 0xa240
    a1ae:	7f 90 2e 00 	cmp.b	#46,	r15	;#0x002e
    a1b2:	5b 24       	jz	$+184    	;abs 0xa26a
    a1b4:	7f 90 2b 00 	cmp.b	#43,	r15	;#0x002b
    a1b8:	28 20       	jnz	$+82     	;abs 0xa20a
    a1ba:	47 3c       	jmp	$+144    	;abs 0xa24a
    a1bc:	7f 90 3a 00 	cmp.b	#58,	r15	;#0x003a
    a1c0:	90 38       	jl	$+290    	;abs 0xa2e2
    a1c2:	7f 90 58 00 	cmp.b	#88,	r15	;#0x0058
    a1c6:	21 20       	jnz	$+68     	;abs 0xa20a
    a1c8:	ea 3c       	jmp	$+470    	;abs 0xa39e
    a1ca:	7f 90 6f 00 	cmp.b	#111,	r15	;#0x006f
    a1ce:	24 24       	jz	$+74     	;abs 0xa218
    a1d0:	7f 90 70 00 	cmp.b	#112,	r15	;#0x0070
    a1d4:	0a 34       	jge	$+22     	;abs 0xa1ea
    a1d6:	7f 90 69 00 	cmp.b	#105,	r15	;#0x0069
    a1da:	e4 24       	jz	$+458    	;abs 0xa3a4
    a1dc:	7f 90 6c 00 	cmp.b	#108,	r15	;#0x006c
    a1e0:	21 24       	jz	$+68     	;abs 0xa224
    a1e2:	7f 90 64 00 	cmp.b	#100,	r15	;#0x0064
    a1e6:	11 20       	jnz	$+36     	;abs 0xa20a
    a1e8:	dd 3c       	jmp	$+444    	;abs 0xa3a4
    a1ea:	7f 90 73 00 	cmp.b	#115,	r15	;#0x0073
    a1ee:	9b 24       	jz	$+312    	;abs 0xa326
    a1f0:	7f 90 74 00 	cmp.b	#116,	r15	;#0x0074
    a1f4:	04 34       	jge	$+10     	;abs 0xa1fe
    a1f6:	7f 90 70 00 	cmp.b	#112,	r15	;#0x0070
    a1fa:	07 20       	jnz	$+16     	;abs 0xa20a
    a1fc:	bb 3c       	jmp	$+376    	;abs 0xa374
    a1fe:	7f 90 75 00 	cmp.b	#117,	r15	;#0x0075
    a202:	d2 24       	jz	$+422    	;abs 0xa3a8
    a204:	7f 90 78 00 	cmp.b	#120,	r15	;#0x0078
    a208:	d2 24       	jz	$+422    	;abs 0xa3ae
    a20a:	19 41 3a 00 	mov	58(r1),	r9	;0x003a(r1)
    a20e:	1a 41 22 00 	mov	34(r1),	r10	;0x0022(r1)
    a212:	0a 89       	sub	r9,	r10	
    a214:	30 40 c2 a6 	br	#0xa6c2	
    a218:	3a 42       	mov	#8,	r10	;r2 As==11
    a21a:	cb 3c       	jmp	$+408    	;abs 0xa3b2
    a21c:	f1 d2 18 00 	bis.b	#8,	24(r1)	;r2 As==11, 0x0018(r1)
    a220:	30 40 f2 a6 	br	#0xa6f2	
    a224:	5e 41 18 00 	mov.b	24(r1),	r14	;0x0018(r1)
    a228:	5e f3       	and.b	#1,	r14	;r3 As==01
    a22a:	5f 41 18 00 	mov.b	24(r1),	r15	;0x0018(r1)
    a22e:	03 24       	jz	$+8      	;abs 0xa236
    a230:	5f c3       	bic.b	#1,	r15	;r3 As==01
    a232:	6f d3       	bis.b	#2,	r15	;r3 As==10
    a234:	01 3c       	jmp	$+4      	;abs 0xa238
    a236:	5f d3       	bis.b	#1,	r15	;r3 As==01
    a238:	c1 4f 18 00 	mov.b	r15,	24(r1)	;0x0018(r1)
    a23c:	30 40 f2 a6 	br	#0xa6f2	
    a240:	f1 d0 10 00 	bis.b	#16,	24(r1)	;#0x0010, 0x0018(r1)
    a244:	18 00 
    a246:	30 40 f2 a6 	br	#0xa6f2	
    a24a:	f1 40 2b 00 	mov.b	#43,	26(r1)	;#0x002b, 0x001a(r1)
    a24e:	1a 00 
    a250:	30 40 f2 a6 	br	#0xa6f2	
    a254:	f1 90 2b 00 	cmp.b	#43,	26(r1)	;#0x002b, 0x001a(r1)
    a258:	1a 00 
    a25a:	02 20       	jnz	$+6      	;abs 0xa260
    a25c:	30 40 f2 a6 	br	#0xa6f2	
    a260:	f1 40 20 00 	mov.b	#32,	26(r1)	;#0x0020, 0x001a(r1)
    a264:	1a 00 
    a266:	30 40 f2 a6 	br	#0xa6f2	
    a26a:	c1 93 20 00 	tst.b	32(r1)		;0x0020(r1)
    a26e:	02 24       	jz	$+6      	;abs 0xa274
    a270:	30 40 d8 a6 	br	#0xa6d8	
    a274:	d1 43 28 00 	mov.b	#1,	40(r1)	;r3 As==01, 0x0028(r1)
    a278:	30 40 f2 a6 	br	#0xa6f2	
    a27c:	0f 4b       	mov	r11,	r15	
    a27e:	2f 53       	incd	r15		
    a280:	2e 4b       	mov	@r11,	r14	
    a282:	0e 93       	tst	r14		
    a284:	01 38       	jl	$+4      	;abs 0xa288
    a286:	0a 3c       	jmp	$+22     	;abs 0xa29c
    a288:	c1 93 28 00 	tst.b	40(r1)		;0x0028(r1)
    a28c:	02 24       	jz	$+6      	;abs 0xa292
    a28e:	30 40 e8 a6 	br	#0xa6e8	
    a292:	f1 d0 10 00 	bis.b	#16,	24(r1)	;#0x0010, 0x0018(r1)
    a296:	18 00 
    a298:	3e e3       	inv	r14		
    a29a:	1e 53       	inc	r14		
    a29c:	81 4e 1e 00 	mov	r14,	30(r1)	;0x001e(r1)
    a2a0:	0b 4f       	mov	r15,	r11	
    a2a2:	2e 3c       	jmp	$+94     	;abs 0xa300
    a2a4:	81 93 1e 00 	tst	30(r1)		;0x001e(r1)
    a2a8:	1c 20       	jnz	$+58     	;abs 0xa2e2
    a2aa:	c1 93 28 00 	tst.b	40(r1)		;0x0028(r1)
    a2ae:	19 20       	jnz	$+52     	;abs 0xa2e2
    a2b0:	5f 41 18 00 	mov.b	24(r1),	r15	;0x0018(r1)
    a2b4:	12 c3       	clrc			
    a2b6:	4f 10       	rrc.b	r15		
    a2b8:	12 c3       	clrc			
    a2ba:	4f 10       	rrc.b	r15		
    a2bc:	12 c3       	clrc			
    a2be:	4f 10       	rrc.b	r15		
    a2c0:	12 c3       	clrc			
    a2c2:	4f 10       	rrc.b	r15		
    a2c4:	1e 43       	mov	#1,	r14	;r3 As==01
    a2c6:	0e cf       	bic	r15,	r14	
    a2c8:	0f 4e       	mov	r14,	r15	
    a2ca:	0f 11       	rra	r15		
    a2cc:	0f 43       	clr	r15		
    a2ce:	4f 10       	rrc.b	r15		
    a2d0:	5e 41 18 00 	mov.b	24(r1),	r14	;0x0018(r1)
    a2d4:	7e f0 7f 00 	and.b	#127,	r14	;#0x007f
    a2d8:	4e df       	bis.b	r15,	r14	
    a2da:	c1 4e 18 00 	mov.b	r14,	24(r1)	;0x0018(r1)
    a2de:	30 40 f2 a6 	br	#0xa6f2	
    a2e2:	1d 41 1e 00 	mov	30(r1),	r13	;0x001e(r1)
    a2e6:	0d 5d       	rla	r13		
    a2e8:	0e 4d       	mov	r13,	r14	
    a2ea:	0e 5e       	rla	r14		
    a2ec:	0e 5e       	rla	r14		
    a2ee:	0d 5e       	add	r14,	r13	
    a2f0:	81 4d 1e 00 	mov	r13,	30(r1)	;0x001e(r1)
    a2f4:	b1 50 d0 ff 	add	#-48,	30(r1)	;#0xffd0, 0x001e(r1)
    a2f8:	1e 00 
    a2fa:	8f 11       	sxt	r15		
    a2fc:	81 5f 1e 00 	add	r15,	30(r1)	;0x001e(r1)
    a300:	d1 43 20 00 	mov.b	#1,	32(r1)	;r3 As==01, 0x0020(r1)
    a304:	30 40 f2 a6 	br	#0xa6f2	
    a308:	0a 4b       	mov	r11,	r10	
    a30a:	2a 53       	incd	r10		
    a30c:	6f 4b       	mov.b	@r11,	r15	
    a30e:	c1 93 28 00 	tst.b	40(r1)		;0x0028(r1)
    a312:	03 20       	jnz	$+8      	;abs 0xa31a
    a314:	c1 93 20 00 	tst.b	32(r1)		;0x0020(r1)
    a318:	23 27       	jz	$-440    	;abs 0xa160
    a31a:	c1 4f 00 00 	mov.b	r15,	0(r1)	;0x0000(r1)
    a31e:	c1 43 01 00 	mov.b	#0,	1(r1)	;r3 As==00, 0x0001(r1)
    a322:	0e 41       	mov	r1,	r14	
    a324:	03 3c       	jmp	$+8      	;abs 0xa32c
    a326:	0a 4b       	mov	r11,	r10	
    a328:	2a 53       	incd	r10		
    a32a:	2e 4b       	mov	@r11,	r14	
    a32c:	c1 93 28 00 	tst.b	40(r1)		;0x0028(r1)
    a330:	07 24       	jz	$+16     	;abs 0xa340
    a332:	e1 d2 19 00 	bis.b	#4,	25(r1)	;r2 As==10, 0x0019(r1)
    a336:	1f 41 1e 00 	mov	30(r1),	r15	;0x001e(r1)
    a33a:	c1 4f 1b 00 	mov.b	r15,	27(r1)	;0x001b(r1)
    a33e:	06 3c       	jmp	$+14     	;abs 0xa34c
    a340:	c1 93 20 00 	tst.b	32(r1)		;0x0020(r1)
    a344:	03 24       	jz	$+8      	;abs 0xa34c
    a346:	91 41 1e 00 	mov	30(r1),	44(r1)	;0x001e(r1), 0x002c(r1)
    a34a:	2c 00 
    a34c:	0e 93       	tst	r14		
    a34e:	02 20       	jnz	$+6      	;abs 0xa354
    a350:	3e 40 cc b1 	mov	#-20020,r14	;#0xb1cc
    a354:	11 12 1c 00 	push	28(r1)		;0x001c(r1)
    a358:	11 12 1c 00 	push	28(r1)		;0x001c(r1)
    a35c:	1d 41 30 00 	mov	48(r1),	r13	;0x0030(r1)
    a360:	1f 41 3c 00 	mov	60(r1),	r15	;0x003c(r1)
    a364:	b0 12 54 9f 	call	#0x9f54	
    a368:	21 52       	add	#4,	r1	;r2 As==10
    a36a:	81 5f 22 00 	add	r15,	34(r1)	;0x0022(r1)
    a36e:	0b 4a       	mov	r10,	r11	
    a370:	30 40 d4 a6 	br	#0xa6d4	
    a374:	0d 4b       	mov	r11,	r13	
    a376:	2d 53       	incd	r13		
    a378:	2e 4b       	mov	@r11,	r14	
    a37a:	04 4e       	mov	r14,	r4	
    a37c:	5f 43       	mov.b	#1,	r15	;r3 As==01
    a37e:	0e 93       	tst	r14		
    a380:	01 20       	jnz	$+4      	;abs 0xa384
    a382:	4f 43       	clr.b	r15		
    a384:	4f 5f       	rla.b	r15		
    a386:	4f 5f       	rla.b	r15		
    a388:	4f 5f       	rla.b	r15		
    a38a:	5e 41 18 00 	mov.b	24(r1),	r14	;0x0018(r1)
    a38e:	7e c2       	bic.b	#8,	r14	;r2 As==11
    a390:	4e df       	bis.b	r15,	r14	
    a392:	c1 4e 18 00 	mov.b	r14,	24(r1)	;0x0018(r1)
    a396:	0b 4d       	mov	r13,	r11	
    a398:	3a 40 10 00 	mov	#16,	r10	;#0x0010
    a39c:	56 3c       	jmp	$+174    	;abs 0xa44a
    a39e:	d1 d3 19 00 	bis.b	#1,	25(r1)	;r3 As==01, 0x0019(r1)
    a3a2:	05 3c       	jmp	$+12     	;abs 0xa3ae
    a3a4:	e1 d2 18 00 	bis.b	#4,	24(r1)	;r2 As==10, 0x0018(r1)
    a3a8:	3a 40 0a 00 	mov	#10,	r10	;#0x000a
    a3ac:	02 3c       	jmp	$+6      	;abs 0xa3b2
    a3ae:	3a 40 10 00 	mov	#16,	r10	;#0x0010
    a3b2:	5f 41 18 00 	mov.b	24(r1),	r15	;0x0018(r1)
    a3b6:	6f b3       	bit.b	#2,	r15	;r3 As==10
    a3b8:	20 24       	jz	$+66     	;abs 0xa3fa
    a3ba:	0c 4b       	mov	r11,	r12	
    a3bc:	3c 52       	add	#8,	r12	;r2 As==11
    a3be:	2d 4b       	mov	@r11,	r13	
    a3c0:	1e 4b 02 00 	mov	2(r11),	r14	;0x0002(r11)
    a3c4:	1f 4b 04 00 	mov	4(r11),	r15	;0x0004(r11)
    a3c8:	1b 4b 06 00 	mov	6(r11),	r11	;0x0006(r11)
    a3cc:	04 4d       	mov	r13,	r4	
    a3ce:	05 4e       	mov	r14,	r5	
    a3d0:	06 4f       	mov	r15,	r6	
    a3d2:	07 4b       	mov	r11,	r7	
    a3d4:	d1 43 21 00 	mov.b	#1,	33(r1)	;r3 As==01, 0x0021(r1)
    a3d8:	0d 93       	tst	r13		
    a3da:	06 20       	jnz	$+14     	;abs 0xa3e8
    a3dc:	0e 93       	tst	r14		
    a3de:	04 20       	jnz	$+10     	;abs 0xa3e8
    a3e0:	0f 93       	tst	r15		
    a3e2:	02 20       	jnz	$+6      	;abs 0xa3e8
    a3e4:	0b 93       	tst	r11		
    a3e6:	02 24       	jz	$+6      	;abs 0xa3ec
    a3e8:	c1 43 21 00 	mov.b	#0,	33(r1)	;r3 As==00, 0x0021(r1)
    a3ec:	0b 5b       	rla	r11		
    a3ee:	0b 43       	clr	r11		
    a3f0:	0b 6b       	rlc	r11		
    a3f2:	c1 4b 29 00 	mov.b	r11,	41(r1)	;0x0029(r1)
    a3f6:	0b 4c       	mov	r12,	r11	
    a3f8:	28 3c       	jmp	$+82     	;abs 0xa44a
    a3fa:	5f f3       	and.b	#1,	r15	;r3 As==01
    a3fc:	16 24       	jz	$+46     	;abs 0xa42a
    a3fe:	0e 4b       	mov	r11,	r14	
    a400:	2e 52       	add	#4,	r14	;r2 As==10
    a402:	2f 4b       	mov	@r11,	r15	
    a404:	1b 4b 02 00 	mov	2(r11),	r11	;0x0002(r11)
    a408:	04 4f       	mov	r15,	r4	
    a40a:	05 4b       	mov	r11,	r5	
    a40c:	d1 43 21 00 	mov.b	#1,	33(r1)	;r3 As==01, 0x0021(r1)
    a410:	0f 93       	tst	r15		
    a412:	02 20       	jnz	$+6      	;abs 0xa418
    a414:	0b 93       	tst	r11		
    a416:	02 24       	jz	$+6      	;abs 0xa41c
    a418:	c1 43 21 00 	mov.b	#0,	33(r1)	;r3 As==00, 0x0021(r1)
    a41c:	0b 5b       	rla	r11		
    a41e:	0b 43       	clr	r11		
    a420:	0b 6b       	rlc	r11		
    a422:	c1 4b 29 00 	mov.b	r11,	41(r1)	;0x0029(r1)
    a426:	0b 4e       	mov	r14,	r11	
    a428:	10 3c       	jmp	$+34     	;abs 0xa44a
    a42a:	0f 4b       	mov	r11,	r15	
    a42c:	2f 53       	incd	r15		
    a42e:	2b 4b       	mov	@r11,	r11	
    a430:	04 4b       	mov	r11,	r4	
    a432:	d1 43 21 00 	mov.b	#1,	33(r1)	;r3 As==01, 0x0021(r1)
    a436:	0b 93       	tst	r11		
    a438:	02 24       	jz	$+6      	;abs 0xa43e
    a43a:	c1 43 21 00 	mov.b	#0,	33(r1)	;r3 As==00, 0x0021(r1)
    a43e:	0b 5b       	rla	r11		
    a440:	0b 43       	clr	r11		
    a442:	0b 6b       	rlc	r11		
    a444:	c1 4b 29 00 	mov.b	r11,	41(r1)	;0x0029(r1)
    a448:	0b 4f       	mov	r15,	r11	
    a44a:	f1 b2 18 00 	bit.b	#8,	24(r1)	;r2 As==11, 0x0018(r1)
    a44e:	11 24       	jz	$+36     	;abs 0xa472
    a450:	c1 93 21 00 	tst.b	33(r1)		;0x0021(r1)
    a454:	0e 20       	jnz	$+30     	;abs 0xa472
    a456:	5f 41 18 00 	mov.b	24(r1),	r15	;0x0018(r1)
    a45a:	3a 90 10 00 	cmp	#16,	r10	;#0x0010
    a45e:	03 20       	jnz	$+8      	;abs 0xa466
    a460:	7f d0 40 00 	bis.b	#64,	r15	;#0x0040
    a464:	04 3c       	jmp	$+10     	;abs 0xa46e
    a466:	3a 92       	cmp	#8,	r10	;r2 As==11
    a468:	04 20       	jnz	$+10     	;abs 0xa472
    a46a:	7f d0 20 00 	bis.b	#32,	r15	;#0x0020
    a46e:	c1 4f 18 00 	mov.b	r15,	24(r1)	;0x0018(r1)
    a472:	5d 41 18 00 	mov.b	24(r1),	r13	;0x0018(r1)
    a476:	6d b2       	bit.b	#4,	r13	;r2 As==10
    a478:	20 24       	jz	$+66     	;abs 0xa4ba
    a47a:	c1 93 29 00 	tst.b	41(r1)		;0x0029(r1)
    a47e:	1d 24       	jz	$+60     	;abs 0xa4ba
    a480:	f1 40 2d 00 	mov.b	#45,	26(r1)	;#0x002d, 0x001a(r1)
    a484:	1a 00 
    a486:	6d b3       	bit.b	#2,	r13	;r3 As==10
    a488:	09 24       	jz	$+20     	;abs 0xa49c
    a48a:	34 e3       	inv	r4		
    a48c:	35 e3       	inv	r5		
    a48e:	36 e3       	inv	r6		
    a490:	37 e3       	inv	r7		
    a492:	14 53       	inc	r4		
    a494:	05 63       	adc	r5		
    a496:	06 63       	adc	r6		
    a498:	07 63       	adc	r7		
    a49a:	0f 3c       	jmp	$+32     	;abs 0xa4ba
    a49c:	5d b3       	bit.b	#1,	r13	;r3 As==01
    a49e:	09 24       	jz	$+20     	;abs 0xa4b2
    a4a0:	0e 44       	mov	r4,	r14	
    a4a2:	0f 45       	mov	r5,	r15	
    a4a4:	3e e3       	inv	r14		
    a4a6:	3f e3       	inv	r15		
    a4a8:	04 4e       	mov	r14,	r4	
    a4aa:	05 4f       	mov	r15,	r5	
    a4ac:	14 53       	inc	r4		
    a4ae:	05 63       	adc	r5		
    a4b0:	04 3c       	jmp	$+10     	;abs 0xa4ba
    a4b2:	0f 44       	mov	r4,	r15	
    a4b4:	3f e3       	inv	r15		
    a4b6:	04 4f       	mov	r15,	r4	
    a4b8:	14 53       	inc	r4		
    a4ba:	c1 43 17 00 	mov.b	#0,	23(r1)	;r3 As==00, 0x0017(r1)
    a4be:	6d b3       	bit.b	#2,	r13	;r3 As==10
    a4c0:	63 24       	jz	$+200    	;abs 0xa588
    a4c2:	09 44       	mov	r4,	r9	
    a4c4:	81 45 24 00 	mov	r5,	36(r1)	;0x0024(r1)
    a4c8:	81 46 26 00 	mov	r6,	38(r1)	;0x0026(r1)
    a4cc:	08 41       	mov	r1,	r8	
    a4ce:	38 50 15 00 	add	#21,	r8	;#0x0015
    a4d2:	81 4a 2e 00 	mov	r10,	46(r1)	;0x002e(r1)
    a4d6:	0f 4a       	mov	r10,	r15	
    a4d8:	8f 10       	swpb	r15		
    a4da:	8f 11       	sxt	r15		
    a4dc:	8f 10       	swpb	r15		
    a4de:	8f 11       	sxt	r15		
    a4e0:	81 4f 30 00 	mov	r15,	48(r1)	;0x0030(r1)
    a4e4:	81 4f 32 00 	mov	r15,	50(r1)	;0x0032(r1)
    a4e8:	81 4f 34 00 	mov	r15,	52(r1)	;0x0034(r1)
    a4ec:	11 12 36 00 	push	54(r1)		;0x0036(r1)
    a4f0:	11 12 36 00 	push	54(r1)		;0x0036(r1)
    a4f4:	11 12 36 00 	push	54(r1)		;0x0036(r1)
    a4f8:	11 12 36 00 	push	54(r1)		;0x0036(r1)
    a4fc:	0c 49       	mov	r9,	r12	
    a4fe:	1d 41 2c 00 	mov	44(r1),	r13	;0x002c(r1)
    a502:	1e 41 2e 00 	mov	46(r1),	r14	;0x002e(r1)
    a506:	0f 47       	mov	r7,	r15	
    a508:	b0 12 a0 aa 	call	#0xaaa0	
    a50c:	31 52       	add	#8,	r1	;r2 As==11
    a50e:	3c 90 0a 00 	cmp	#10,	r12	;#0x000a
    a512:	07 34       	jge	$+16     	;abs 0xa522
    a514:	81 48 2a 00 	mov	r8,	42(r1)	;0x002a(r1)
    a518:	7c 50 30 00 	add.b	#48,	r12	;#0x0030
    a51c:	c8 4c 01 00 	mov.b	r12,	1(r8)	;0x0001(r8)
    a520:	0e 3c       	jmp	$+30     	;abs 0xa53e
    a522:	4c 4c       	mov.b	r12,	r12	
    a524:	d1 b3 19 00 	bit.b	#1,	25(r1)	;r3 As==01, 0x0019(r1)
    a528:	03 24       	jz	$+8      	;abs 0xa530
    a52a:	7f 40 37 00 	mov.b	#55,	r15	;#0x0037
    a52e:	02 3c       	jmp	$+6      	;abs 0xa534
    a530:	7f 40 57 00 	mov.b	#87,	r15	;#0x0057
    a534:	81 48 2a 00 	mov	r8,	42(r1)	;0x002a(r1)
    a538:	4f 5c       	add.b	r12,	r15	
    a53a:	c8 4f 01 00 	mov.b	r15,	1(r8)	;0x0001(r8)
    a53e:	11 12 36 00 	push	54(r1)		;0x0036(r1)
    a542:	11 12 36 00 	push	54(r1)		;0x0036(r1)
    a546:	11 12 36 00 	push	54(r1)		;0x0036(r1)
    a54a:	11 12 36 00 	push	54(r1)		;0x0036(r1)
    a54e:	0c 49       	mov	r9,	r12	
    a550:	1d 41 2c 00 	mov	44(r1),	r13	;0x002c(r1)
    a554:	1e 41 2e 00 	mov	46(r1),	r14	;0x002e(r1)
    a558:	0f 47       	mov	r7,	r15	
    a55a:	b0 12 7a aa 	call	#0xaa7a	
    a55e:	31 52       	add	#8,	r1	;r2 As==11
    a560:	09 4c       	mov	r12,	r9	
    a562:	81 4d 24 00 	mov	r13,	36(r1)	;0x0024(r1)
    a566:	81 4e 26 00 	mov	r14,	38(r1)	;0x0026(r1)
    a56a:	07 4f       	mov	r15,	r7	
    a56c:	38 53       	add	#-1,	r8	;r3 As==11
    a56e:	0c 93       	tst	r12		
    a570:	b0 23       	jnz	$-158    	;abs 0xa4d2
    a572:	0d 93       	tst	r13		
    a574:	ae 23       	jnz	$-162    	;abs 0xa4d2
    a576:	0e 93       	tst	r14		
    a578:	ac 23       	jnz	$-166    	;abs 0xa4d2
    a57a:	0f 93       	tst	r15		
    a57c:	aa 23       	jnz	$-170    	;abs 0xa4d2
    a57e:	04 43       	clr	r4		
    a580:	05 43       	clr	r5		
    a582:	06 43       	clr	r6		
    a584:	07 43       	clr	r7		
    a586:	6a 3c       	jmp	$+214    	;abs 0xa65c
    a588:	5d f3       	and.b	#1,	r13	;r3 As==01
    a58a:	40 24       	jz	$+130    	;abs 0xa60c
    a58c:	81 44 24 00 	mov	r4,	36(r1)	;0x0024(r1)
    a590:	81 45 26 00 	mov	r5,	38(r1)	;0x0026(r1)
    a594:	09 41       	mov	r1,	r9	
    a596:	39 50 15 00 	add	#21,	r9	;#0x0015
    a59a:	08 4a       	mov	r10,	r8	
    a59c:	88 10       	swpb	r8		
    a59e:	88 11       	sxt	r8		
    a5a0:	88 10       	swpb	r8		
    a5a2:	88 11       	sxt	r8		
    a5a4:	0c 4a       	mov	r10,	r12	
    a5a6:	0d 48       	mov	r8,	r13	
    a5a8:	1e 41 24 00 	mov	36(r1),	r14	;0x0024(r1)
    a5ac:	1f 41 26 00 	mov	38(r1),	r15	;0x0026(r1)
    a5b0:	b0 12 12 aa 	call	#0xaa12	
    a5b4:	3e 90 0a 00 	cmp	#10,	r14	;#0x000a
    a5b8:	07 34       	jge	$+16     	;abs 0xa5c8
    a5ba:	81 49 2a 00 	mov	r9,	42(r1)	;0x002a(r1)
    a5be:	7e 50 30 00 	add.b	#48,	r14	;#0x0030
    a5c2:	c9 4e 01 00 	mov.b	r14,	1(r9)	;0x0001(r9)
    a5c6:	0e 3c       	jmp	$+30     	;abs 0xa5e4
    a5c8:	4e 4e       	mov.b	r14,	r14	
    a5ca:	d1 b3 19 00 	bit.b	#1,	25(r1)	;r3 As==01, 0x0019(r1)
    a5ce:	03 24       	jz	$+8      	;abs 0xa5d6
    a5d0:	7f 40 37 00 	mov.b	#55,	r15	;#0x0037
    a5d4:	02 3c       	jmp	$+6      	;abs 0xa5da
    a5d6:	7f 40 57 00 	mov.b	#87,	r15	;#0x0057
    a5da:	81 49 2a 00 	mov	r9,	42(r1)	;0x002a(r1)
    a5de:	4f 5e       	add.b	r14,	r15	
    a5e0:	c9 4f 01 00 	mov.b	r15,	1(r9)	;0x0001(r9)
    a5e4:	0c 4a       	mov	r10,	r12	
    a5e6:	0d 48       	mov	r8,	r13	
    a5e8:	1e 41 24 00 	mov	36(r1),	r14	;0x0024(r1)
    a5ec:	1f 41 26 00 	mov	38(r1),	r15	;0x0026(r1)
    a5f0:	b0 12 dc a9 	call	#0xa9dc	
    a5f4:	81 4e 24 00 	mov	r14,	36(r1)	;0x0024(r1)
    a5f8:	81 4f 26 00 	mov	r15,	38(r1)	;0x0026(r1)
    a5fc:	39 53       	add	#-1,	r9	;r3 As==11
    a5fe:	0e 93       	tst	r14		
    a600:	cc 23       	jnz	$-102    	;abs 0xa59a
    a602:	0f 93       	tst	r15		
    a604:	ca 23       	jnz	$-106    	;abs 0xa59a
    a606:	04 43       	clr	r4		
    a608:	05 43       	clr	r5		
    a60a:	28 3c       	jmp	$+82     	;abs 0xa65c
    a60c:	09 44       	mov	r4,	r9	
    a60e:	08 41       	mov	r1,	r8	
    a610:	38 50 15 00 	add	#21,	r8	;#0x0015
    a614:	0e 4a       	mov	r10,	r14	
    a616:	0f 49       	mov	r9,	r15	
    a618:	b0 12 d4 a9 	call	#0xa9d4	
    a61c:	3f 90 0a 00 	cmp	#10,	r15	;#0x000a
    a620:	07 34       	jge	$+16     	;abs 0xa630
    a622:	81 48 2a 00 	mov	r8,	42(r1)	;0x002a(r1)
    a626:	7f 50 30 00 	add.b	#48,	r15	;#0x0030
    a62a:	c8 4f 01 00 	mov.b	r15,	1(r8)	;0x0001(r8)
    a62e:	0e 3c       	jmp	$+30     	;abs 0xa64c
    a630:	4f 4f       	mov.b	r15,	r15	
    a632:	d1 b3 19 00 	bit.b	#1,	25(r1)	;r3 As==01, 0x0019(r1)
    a636:	03 24       	jz	$+8      	;abs 0xa63e
    a638:	7e 40 37 00 	mov.b	#55,	r14	;#0x0037
    a63c:	02 3c       	jmp	$+6      	;abs 0xa642
    a63e:	7e 40 57 00 	mov.b	#87,	r14	;#0x0057
    a642:	81 48 2a 00 	mov	r8,	42(r1)	;0x002a(r1)
    a646:	4e 5f       	add.b	r15,	r14	
    a648:	c8 4e 01 00 	mov.b	r14,	1(r8)	;0x0001(r8)
    a64c:	0e 4a       	mov	r10,	r14	
    a64e:	0f 49       	mov	r9,	r15	
    a650:	b0 12 ba a9 	call	#0xa9ba	
    a654:	09 4f       	mov	r15,	r9	
    a656:	38 53       	add	#-1,	r8	;r3 As==11
    a658:	0f 93       	tst	r15		
    a65a:	dc 23       	jnz	$-70     	;abs 0xa614
    a65c:	3a 90 0a 00 	cmp	#10,	r10	;#0x000a
    a660:	02 24       	jz	$+6      	;abs 0xa666
    a662:	c1 43 1a 00 	mov.b	#0,	26(r1)	;r3 As==00, 0x001a(r1)
    a666:	c1 93 28 00 	tst.b	40(r1)		;0x0028(r1)
    a66a:	10 24       	jz	$+34     	;abs 0xa68c
    a66c:	1f 41 1c 00 	mov	28(r1),	r15	;0x001c(r1)
    a670:	1f 81 2a 00 	sub	42(r1),	r15	;0x002a(r1)
    a674:	2f 83       	decd	r15		
    a676:	1f 91 1e 00 	cmp	30(r1),	r15	;0x001e(r1)
    a67a:	0e 2c       	jc	$+30     	;abs 0xa698
    a67c:	e1 d3 19 00 	bis.b	#2,	25(r1)	;r3 As==10, 0x0019(r1)
    a680:	5c 41 1e 00 	mov.b	30(r1),	r12	;0x001e(r1)
    a684:	4c 8f       	sub.b	r15,	r12	
    a686:	c1 4c 1b 00 	mov.b	r12,	27(r1)	;0x001b(r1)
    a68a:	06 3c       	jmp	$+14     	;abs 0xa698
    a68c:	c1 93 20 00 	tst.b	32(r1)		;0x0020(r1)
    a690:	03 24       	jz	$+8      	;abs 0xa698
    a692:	91 41 1e 00 	mov	30(r1),	44(r1)	;0x001e(r1), 0x002c(r1)
    a696:	2c 00 
    a698:	11 12 1c 00 	push	28(r1)		;0x001c(r1)
    a69c:	11 12 1c 00 	push	28(r1)		;0x001c(r1)
    a6a0:	1d 41 30 00 	mov	48(r1),	r13	;0x0030(r1)
    a6a4:	1e 41 2e 00 	mov	46(r1),	r14	;0x002e(r1)
    a6a8:	1e 53       	inc	r14		
    a6aa:	1f 41 3c 00 	mov	60(r1),	r15	;0x003c(r1)
    a6ae:	b0 12 54 9f 	call	#0x9f54	
    a6b2:	21 52       	add	#4,	r1	;r2 As==10
    a6b4:	81 5f 22 00 	add	r15,	34(r1)	;0x0022(r1)
    a6b8:	0d 3c       	jmp	$+28     	;abs 0xa6d4
    a6ba:	7f 49       	mov.b	@r9+,	r15	
    a6bc:	8f 11       	sxt	r15		
    a6be:	91 12 3a 00 	call	58(r1)		;0x003a(r1)
    a6c2:	0f 49       	mov	r9,	r15	
    a6c4:	0f 5a       	add	r10,	r15	
    a6c6:	19 91 36 00 	cmp	54(r1),	r9	;0x0036(r1)
    a6ca:	f7 2b       	jnc	$-16     	;abs 0xa6ba
    a6cc:	81 49 3a 00 	mov	r9,	58(r1)	;0x003a(r1)
    a6d0:	81 4f 22 00 	mov	r15,	34(r1)	;0x0022(r1)
    a6d4:	0d 43       	clr	r13		
    a6d6:	0e 3c       	jmp	$+30     	;abs 0xa6f4
    a6d8:	91 41 1e 00 	mov	30(r1),	44(r1)	;0x001e(r1), 0x002c(r1)
    a6dc:	2c 00 
    a6de:	d1 43 28 00 	mov.b	#1,	40(r1)	;r3 As==01, 0x0028(r1)
    a6e2:	c1 43 20 00 	mov.b	#0,	32(r1)	;r3 As==00, 0x0020(r1)
    a6e6:	03 3c       	jmp	$+8      	;abs 0xa6ee
    a6e8:	0b 4f       	mov	r15,	r11	
    a6ea:	d1 43 20 00 	mov.b	#1,	32(r1)	;r3 As==01, 0x0020(r1)
    a6ee:	81 43 1e 00 	mov	#0,	30(r1)	;r3 As==00, 0x001e(r1)
    a6f2:	1d 43       	mov	#1,	r13	;r3 As==01
    a6f4:	1e 41 36 00 	mov	54(r1),	r14	;0x0036(r1)
    a6f8:	81 4e 36 00 	mov	r14,	54(r1)	;0x0036(r1)
    a6fc:	0c 4e       	mov	r14,	r12	
    a6fe:	91 53 36 00 	inc	54(r1)		;0x0036(r1)
    a702:	7f 4c       	mov.b	@r12+,	r15	
    a704:	4f 93       	tst.b	r15		
    a706:	02 24       	jz	$+6      	;abs 0xa70c
    a708:	30 40 32 a1 	br	#0xa132	
    a70c:	1f 41 22 00 	mov	34(r1),	r15	;0x0022(r1)
    a710:	31 50 3c 00 	add	#60,	r1	;#0x003c
    a714:	34 41       	pop	r4		
    a716:	35 41       	pop	r5		
    a718:	36 41       	pop	r6		
    a71a:	37 41       	pop	r7		
    a71c:	38 41       	pop	r8		
    a71e:	39 41       	pop	r9		
    a720:	3a 41       	pop	r10		
    a722:	3b 41       	pop	r11		
    a724:	30 41       	ret			

0000a726 <puts>:
    a726:	0b 12       	push	r11		
    a728:	0b 4f       	mov	r15,	r11	
    a72a:	6f 4b       	mov.b	@r11,	r15	
    a72c:	4f 93       	tst.b	r15		
    a72e:	06 24       	jz	$+14     	;abs 0xa73c
    a730:	1b 53       	inc	r11		
    a732:	8f 11       	sxt	r15		
    a734:	b0 12 e0 7c 	call	#0x7ce0	
    a738:	0f 93       	tst	r15		
    a73a:	f7 37       	jge	$-16     	;abs 0xa72a
    a73c:	cb 93 00 00 	tst.b	0(r11)		;0x0000(r11)
    a740:	05 20       	jnz	$+12     	;abs 0xa74c
    a742:	3f 40 0a 00 	mov	#10,	r15	;#0x000a
    a746:	b0 12 e0 7c 	call	#0x7ce0	
    a74a:	01 3c       	jmp	$+4      	;abs 0xa74e
    a74c:	3f 43       	mov	#-1,	r15	;r3 As==11
    a74e:	3b 41       	pop	r11		
    a750:	30 41       	ret			

0000a752 <rand>:
    a752:	3c 40 6d 4e 	mov	#20077,	r12	;#0x4e6d
    a756:	3d 40 c6 41 	mov	#16838,	r13	;#0x41c6
    a75a:	1e 42 46 22 	mov	&0x2246,r14	
    a75e:	1f 42 48 22 	mov	&0x2248,r15	
    a762:	b0 12 18 a9 	call	#0xa918	
    a766:	3e 50 39 30 	add	#12345,	r14	;#0x3039
    a76a:	0f 63       	adc	r15		
    a76c:	82 4e 46 22 	mov	r14,	&0x2246	
    a770:	82 4f 48 22 	mov	r15,	&0x2248	
    a774:	0f 4e       	mov	r14,	r15	
    a776:	30 41       	ret			

0000a778 <srand>:
    a778:	82 4f 46 22 	mov	r15,	&0x2246	
    a77c:	82 43 48 22 	mov	#0,	&0x2248	;r3 As==00
    a780:	30 41       	ret			

0000a782 <memcmp>:
    a782:	0b 12       	push	r11		
    a784:	0a 12       	push	r10		
    a786:	0d 93       	tst	r13		
    a788:	10 24       	jz	$+34     	;abs 0xa7aa
    a78a:	0c 43       	clr	r12		
    a78c:	0b 4f       	mov	r15,	r11	
    a78e:	0b 5c       	add	r12,	r11	
    a790:	6a 4b       	mov.b	@r11,	r10	
    a792:	0b 4e       	mov	r14,	r11	
    a794:	0b 5c       	add	r12,	r11	
    a796:	6b 4b       	mov.b	@r11,	r11	
    a798:	4a 9b       	cmp.b	r11,	r10	
    a79a:	04 24       	jz	$+10     	;abs 0xa7a4
    a79c:	4f 4a       	mov.b	r10,	r15	
    a79e:	4b 4b       	mov.b	r11,	r11	
    a7a0:	0f 8b       	sub	r11,	r15	
    a7a2:	04 3c       	jmp	$+10     	;abs 0xa7ac
    a7a4:	1c 53       	inc	r12		
    a7a6:	0d 9c       	cmp	r12,	r13	
    a7a8:	f1 23       	jnz	$-28     	;abs 0xa78c
    a7aa:	0f 43       	clr	r15		
    a7ac:	3a 41       	pop	r10		
    a7ae:	3b 41       	pop	r11		
    a7b0:	30 41       	ret			

0000a7b2 <memcpy>:
    a7b2:	0b 12       	push	r11		
    a7b4:	0a 12       	push	r10		
    a7b6:	09 12       	push	r9		
    a7b8:	08 12       	push	r8		
    a7ba:	0d 93       	tst	r13		
    a7bc:	72 24       	jz	$+230    	;abs 0xa8a2
    a7be:	0f 9e       	cmp	r14,	r15	
    a7c0:	70 24       	jz	$+226    	;abs 0xa8a2
    a7c2:	36 2c       	jc	$+110    	;abs 0xa830
    a7c4:	0c 4e       	mov	r14,	r12	
    a7c6:	0c df       	bis	r15,	r12	
    a7c8:	1c f3       	and	#1,	r12	;r3 As==01
    a7ca:	1d 24       	jz	$+60     	;abs 0xa806
    a7cc:	0c 4e       	mov	r14,	r12	
    a7ce:	0c ef       	xor	r15,	r12	
    a7d0:	1c f3       	and	#1,	r12	;r3 As==01
    a7d2:	07 20       	jnz	$+16     	;abs 0xa7e2
    a7d4:	2d 93       	cmp	#2,	r13	;r3 As==10
    a7d6:	07 28       	jnc	$+16     	;abs 0xa7e6
    a7d8:	0c 4e       	mov	r14,	r12	
    a7da:	1c f3       	and	#1,	r12	;r3 As==01
    a7dc:	2b 43       	mov	#2,	r11	;r3 As==10
    a7de:	0b 8c       	sub	r12,	r11	
    a7e0:	03 3c       	jmp	$+8      	;abs 0xa7e8
    a7e2:	0b 4d       	mov	r13,	r11	
    a7e4:	01 3c       	jmp	$+4      	;abs 0xa7e8
    a7e6:	1b 43       	mov	#1,	r11	;r3 As==01
    a7e8:	0d 8b       	sub	r11,	r13	
    a7ea:	0c 43       	clr	r12		
    a7ec:	09 4e       	mov	r14,	r9	
    a7ee:	09 5c       	add	r12,	r9	
    a7f0:	0a 4f       	mov	r15,	r10	
    a7f2:	0a 5c       	add	r12,	r10	
    a7f4:	ea 49 00 00 	mov.b	@r9,	0(r10)	;0x0000(r10)
    a7f8:	1c 53       	inc	r12		
    a7fa:	0c 9b       	cmp	r11,	r12	
    a7fc:	f7 23       	jnz	$-16     	;abs 0xa7ec
    a7fe:	0b 4f       	mov	r15,	r11	
    a800:	0b 5c       	add	r12,	r11	
    a802:	0e 5c       	add	r12,	r14	
    a804:	01 3c       	jmp	$+4      	;abs 0xa808
    a806:	0b 4f       	mov	r15,	r11	
    a808:	0c 4d       	mov	r13,	r12	
    a80a:	12 c3       	clrc			
    a80c:	0c 10       	rrc	r12		
    a80e:	0b 24       	jz	$+24     	;abs 0xa826
    a810:	0a 4c       	mov	r12,	r10	
    a812:	08 4e       	mov	r14,	r8	
    a814:	09 4b       	mov	r11,	r9	
    a816:	b9 48 00 00 	mov	@r8+,	0(r9)	;0x0000(r9)
    a81a:	29 53       	incd	r9		
    a81c:	3a 53       	add	#-1,	r10	;r3 As==11
    a81e:	fb 23       	jnz	$-8      	;abs 0xa816
    a820:	0c 5c       	rla	r12		
    a822:	0e 5c       	add	r12,	r14	
    a824:	0b 5c       	add	r12,	r11	
    a826:	1d f3       	and	#1,	r13	;r3 As==01
    a828:	3c 24       	jz	$+122    	;abs 0xa8a2
    a82a:	eb 4e 00 00 	mov.b	@r14,	0(r11)	;0x0000(r11)
    a82e:	39 3c       	jmp	$+116    	;abs 0xa8a2
    a830:	0e 5d       	add	r13,	r14	
    a832:	0c 4f       	mov	r15,	r12	
    a834:	0c 5d       	add	r13,	r12	
    a836:	0b 4c       	mov	r12,	r11	
    a838:	0b de       	bis	r14,	r11	
    a83a:	1b f3       	and	#1,	r11	;r3 As==01
    a83c:	1b 24       	jz	$+56     	;abs 0xa874
    a83e:	0b 4c       	mov	r12,	r11	
    a840:	0b ee       	xor	r14,	r11	
    a842:	1b f3       	and	#1,	r11	;r3 As==01
    a844:	06 20       	jnz	$+14     	;abs 0xa852
    a846:	3d 90 03 00 	cmp	#3,	r13	;#0x0003
    a84a:	03 28       	jnc	$+8      	;abs 0xa852
    a84c:	0a 4e       	mov	r14,	r10	
    a84e:	1a f3       	and	#1,	r10	;r3 As==01
    a850:	01 3c       	jmp	$+4      	;abs 0xa854
    a852:	0a 4d       	mov	r13,	r10	
    a854:	0d 8a       	sub	r10,	r13	
    a856:	0b 4a       	mov	r10,	r11	
    a858:	3b 53       	add	#-1,	r11	;r3 As==11
    a85a:	3a e3       	inv	r10		
    a85c:	1a 53       	inc	r10		
    a85e:	0e 5a       	add	r10,	r14	
    a860:	0c 5a       	add	r10,	r12	
    a862:	09 4e       	mov	r14,	r9	
    a864:	09 5b       	add	r11,	r9	
    a866:	0a 4c       	mov	r12,	r10	
    a868:	0a 5b       	add	r11,	r10	
    a86a:	ea 49 00 00 	mov.b	@r9,	0(r10)	;0x0000(r10)
    a86e:	3b 53       	add	#-1,	r11	;r3 As==11
    a870:	3b 93       	cmp	#-1,	r11	;r3 As==11
    a872:	f7 23       	jnz	$-16     	;abs 0xa862
    a874:	0b 4d       	mov	r13,	r11	
    a876:	12 c3       	clrc			
    a878:	0b 10       	rrc	r11		
    a87a:	0e 24       	jz	$+30     	;abs 0xa898
    a87c:	0a 4b       	mov	r11,	r10	
    a87e:	08 4e       	mov	r14,	r8	
    a880:	09 4c       	mov	r12,	r9	
    a882:	28 83       	decd	r8		
    a884:	29 83       	decd	r9		
    a886:	a9 48 00 00 	mov	@r8,	0(r9)	;0x0000(r9)
    a88a:	3a 53       	add	#-1,	r10	;r3 As==11
    a88c:	fa 23       	jnz	$-10     	;abs 0xa882
    a88e:	0a 8b       	sub	r11,	r10	
    a890:	0b 4a       	mov	r10,	r11	
    a892:	0b 5b       	rla	r11		
    a894:	0e 5b       	add	r11,	r14	
    a896:	0c 5b       	add	r11,	r12	
    a898:	1d f3       	and	#1,	r13	;r3 As==01
    a89a:	03 24       	jz	$+8      	;abs 0xa8a2
    a89c:	dc 4e ff ff 	mov.b	-1(r14),-1(r12)	;0xffff(r14), 0xffff(r12)
    a8a0:	ff ff 
    a8a2:	38 41       	pop	r8		
    a8a4:	39 41       	pop	r9		
    a8a6:	3a 41       	pop	r10		
    a8a8:	3b 41       	pop	r11		
    a8aa:	30 41       	ret			

0000a8ac <memset>:
    a8ac:	0b 12       	push	r11		
    a8ae:	0a 12       	push	r10		
    a8b0:	09 12       	push	r9		
    a8b2:	08 12       	push	r8		
    a8b4:	3d 90 06 00 	cmp	#6,	r13	;#0x0006
    a8b8:	09 2c       	jc	$+20     	;abs 0xa8cc
    a8ba:	0d 5f       	add	r15,	r13	
    a8bc:	0c 4f       	mov	r15,	r12	
    a8be:	03 3c       	jmp	$+8      	;abs 0xa8c6
    a8c0:	cc 4e 00 00 	mov.b	r14,	0(r12)	;0x0000(r12)
    a8c4:	1c 53       	inc	r12		
    a8c6:	0c 9d       	cmp	r13,	r12	
    a8c8:	fb 23       	jnz	$-8      	;abs 0xa8c0
    a8ca:	20 3c       	jmp	$+66     	;abs 0xa90c
    a8cc:	0c 4e       	mov	r14,	r12	
    a8ce:	3c f0 ff 00 	and	#255,	r12	;#0x00ff
    a8d2:	03 24       	jz	$+8      	;abs 0xa8da
    a8d4:	0b 4c       	mov	r12,	r11	
    a8d6:	8b 10       	swpb	r11		
    a8d8:	0c db       	bis	r11,	r12	
    a8da:	1f b3       	bit	#1,	r15	;r3 As==01
    a8dc:	06 24       	jz	$+14     	;abs 0xa8ea
    a8de:	3d 53       	add	#-1,	r13	;r3 As==11
    a8e0:	cf 4e 00 00 	mov.b	r14,	0(r15)	;0x0000(r15)
    a8e4:	0a 4f       	mov	r15,	r10	
    a8e6:	1a 53       	inc	r10		
    a8e8:	01 3c       	jmp	$+4      	;abs 0xa8ec
    a8ea:	0a 4f       	mov	r15,	r10	
    a8ec:	0b 4d       	mov	r13,	r11	
    a8ee:	12 c3       	clrc			
    a8f0:	0b 10       	rrc	r11		
    a8f2:	08 4a       	mov	r10,	r8	
    a8f4:	09 4b       	mov	r11,	r9	
    a8f6:	88 4c 00 00 	mov	r12,	0(r8)	;0x0000(r8)
    a8fa:	28 53       	incd	r8		
    a8fc:	39 53       	add	#-1,	r9	;r3 As==11
    a8fe:	fb 23       	jnz	$-8      	;abs 0xa8f6
    a900:	0b 5b       	rla	r11		
    a902:	0b 5a       	add	r10,	r11	
    a904:	1d f3       	and	#1,	r13	;r3 As==01
    a906:	02 24       	jz	$+6      	;abs 0xa90c
    a908:	cb 4e 00 00 	mov.b	r14,	0(r11)	;0x0000(r11)
    a90c:	38 41       	pop	r8		
    a90e:	39 41       	pop	r9		
    a910:	3a 41       	pop	r10		
    a912:	3b 41       	pop	r11		
    a914:	30 41       	ret			

0000a916 <_unexpected_>:
    a916:	00 13       	reti			

0000a918 <__mulsi3>:
    a918:	0b 12       	push	r11		
    a91a:	0a 12       	push	r10		
    a91c:	0b 43       	clr	r11		
    a91e:	0a 43       	clr	r10		
    a920:	08 3c       	jmp	$+18     	;abs 0xa932
    a922:	12 c3       	clrc			
    a924:	0d 10       	rrc	r13		
    a926:	0c 10       	rrc	r12		
    a928:	02 28       	jnc	$+6      	;abs 0xa92e
    a92a:	0a 5e       	add	r14,	r10	
    a92c:	0b 6f       	addc	r15,	r11	
    a92e:	0e 5e       	rla	r14		
    a930:	0f 6f       	rlc	r15		
    a932:	0c 93       	tst	r12		
    a934:	f6 23       	jnz	$-18     	;abs 0xa922
    a936:	0d 93       	tst	r13		
    a938:	f4 23       	jnz	$-22     	;abs 0xa922
    a93a:	0e 4a       	mov	r10,	r14	
    a93c:	0f 4b       	mov	r11,	r15	
    a93e:	3a 41       	pop	r10		
    a940:	3b 41       	pop	r11		
    a942:	30 41       	ret			

0000a944 <__muldi3>:
    a944:	0b 12       	push	r11		
    a946:	0a 12       	push	r10		
    a948:	09 12       	push	r9		
    a94a:	08 12       	push	r8		
    a94c:	07 12       	push	r7		
    a94e:	06 12       	push	r6		
    a950:	05 12       	push	r5		
    a952:	04 12       	push	r4		
    a954:	18 41 12 00 	mov	18(r1),	r8	;0x0012(r1)
    a958:	19 41 14 00 	mov	20(r1),	r9	;0x0014(r1)
    a95c:	1a 41 16 00 	mov	22(r1),	r10	;0x0016(r1)
    a960:	1b 41 18 00 	mov	24(r1),	r11	;0x0018(r1)
    a964:	b0 12 7a a9 	call	#0xa97a	
    a968:	34 41       	pop	r4		
    a96a:	35 41       	pop	r5		
    a96c:	36 41       	pop	r6		
    a96e:	37 41       	pop	r7		
    a970:	38 41       	pop	r8		
    a972:	39 41       	pop	r9		
    a974:	3a 41       	pop	r10		
    a976:	3b 41       	pop	r11		
    a978:	30 41       	ret			

0000a97a <__xabi_muldi3>:
    a97a:	04 43       	clr	r4		
    a97c:	05 43       	clr	r5		
    a97e:	06 43       	clr	r6		
    a980:	07 43       	clr	r7		
    a982:	0e 3c       	jmp	$+30     	;abs 0xa9a0
    a984:	12 c3       	clrc			
    a986:	0b 10       	rrc	r11		
    a988:	0a 10       	rrc	r10		
    a98a:	09 10       	rrc	r9		
    a98c:	08 10       	rrc	r8		
    a98e:	04 28       	jnc	$+10     	;abs 0xa998
    a990:	04 5c       	add	r12,	r4	
    a992:	05 6d       	addc	r13,	r5	
    a994:	06 6e       	addc	r14,	r6	
    a996:	07 6f       	addc	r15,	r7	
    a998:	0c 5c       	rla	r12		
    a99a:	0d 6d       	rlc	r13		
    a99c:	0e 6e       	rlc	r14		
    a99e:	0f 6f       	rlc	r15		
    a9a0:	08 93       	tst	r8		
    a9a2:	f0 23       	jnz	$-30     	;abs 0xa984
    a9a4:	09 93       	tst	r9		
    a9a6:	ee 23       	jnz	$-34     	;abs 0xa984
    a9a8:	0a 93       	tst	r10		
    a9aa:	ec 23       	jnz	$-38     	;abs 0xa984
    a9ac:	0b 93       	tst	r11		
    a9ae:	ea 23       	jnz	$-42     	;abs 0xa984
    a9b0:	0c 44       	mov	r4,	r12	
    a9b2:	0d 45       	mov	r5,	r13	
    a9b4:	0e 46       	mov	r6,	r14	
    a9b6:	0f 47       	mov	r7,	r15	
    a9b8:	30 41       	ret			

0000a9ba <__udivhi3>:
    a9ba:	7c 40 10 00 	mov.b	#16,	r12	;#0x0010
    a9be:	0d 4e       	mov	r14,	r13	
    a9c0:	0e 43       	clr	r14		
    a9c2:	0f 5f       	rla	r15		
    a9c4:	0e 6e       	rlc	r14		
    a9c6:	0e 9d       	cmp	r13,	r14	
    a9c8:	02 28       	jnc	$+6      	;abs 0xa9ce
    a9ca:	0e 8d       	sub	r13,	r14	
    a9cc:	1f d3       	bis	#1,	r15	;r3 As==01
    a9ce:	1c 83       	dec	r12		
    a9d0:	f8 23       	jnz	$-14     	;abs 0xa9c2
    a9d2:	30 41       	ret			

0000a9d4 <__umodhi3>:
    a9d4:	b0 12 ba a9 	call	#0xa9ba	
    a9d8:	0f 4e       	mov	r14,	r15	
    a9da:	30 41       	ret			

0000a9dc <__udivsi3>:
    a9dc:	0b 12       	push	r11		
    a9de:	0a 12       	push	r10		
    a9e0:	09 12       	push	r9		
    a9e2:	79 40 20 00 	mov.b	#32,	r9	;#0x0020
    a9e6:	0a 4c       	mov	r12,	r10	
    a9e8:	0b 4d       	mov	r13,	r11	
    a9ea:	0c 43       	clr	r12		
    a9ec:	0d 43       	clr	r13		
    a9ee:	0e 5e       	rla	r14		
    a9f0:	0f 6f       	rlc	r15		
    a9f2:	0c 6c       	rlc	r12		
    a9f4:	0d 6d       	rlc	r13		
    a9f6:	0d 9b       	cmp	r11,	r13	
    a9f8:	06 28       	jnc	$+14     	;abs 0xaa06
    a9fa:	02 20       	jnz	$+6      	;abs 0xaa00
    a9fc:	0c 9a       	cmp	r10,	r12	
    a9fe:	03 28       	jnc	$+8      	;abs 0xaa06
    aa00:	0c 8a       	sub	r10,	r12	
    aa02:	0d 7b       	subc	r11,	r13	
    aa04:	1e d3       	bis	#1,	r14	;r3 As==01
    aa06:	19 83       	dec	r9		
    aa08:	f2 23       	jnz	$-26     	;abs 0xa9ee
    aa0a:	39 41       	pop	r9		
    aa0c:	3a 41       	pop	r10		
    aa0e:	3b 41       	pop	r11		
    aa10:	30 41       	ret			

0000aa12 <__umodsi3>:
    aa12:	b0 12 dc a9 	call	#0xa9dc	
    aa16:	0e 4c       	mov	r12,	r14	
    aa18:	0f 4d       	mov	r13,	r15	
    aa1a:	30 41       	ret			

0000aa1c <__xabi_udivmod64>:
    aa1c:	07 12       	push	r7		
    aa1e:	06 12       	push	r6		
    aa20:	05 12       	push	r5		
    aa22:	04 12       	push	r4		
    aa24:	30 12 40 00 	push	#64		;#0x0040
    aa28:	04 48       	mov	r8,	r4	
    aa2a:	05 49       	mov	r9,	r5	
    aa2c:	06 4a       	mov	r10,	r6	
    aa2e:	07 4b       	mov	r11,	r7	
    aa30:	08 43       	clr	r8		
    aa32:	09 43       	clr	r9		
    aa34:	0a 43       	clr	r10		
    aa36:	0b 43       	clr	r11		
    aa38:	0c 5c       	rla	r12		
    aa3a:	0d 6d       	rlc	r13		
    aa3c:	0e 6e       	rlc	r14		
    aa3e:	0f 6f       	rlc	r15		
    aa40:	08 68       	rlc	r8		
    aa42:	09 69       	rlc	r9		
    aa44:	0a 6a       	rlc	r10		
    aa46:	0b 6b       	rlc	r11		
    aa48:	0b 97       	cmp	r7,	r11	
    aa4a:	0e 28       	jnc	$+30     	;abs 0xaa68
    aa4c:	08 20       	jnz	$+18     	;abs 0xaa5e
    aa4e:	0a 96       	cmp	r6,	r10	
    aa50:	0b 28       	jnc	$+24     	;abs 0xaa68
    aa52:	05 20       	jnz	$+12     	;abs 0xaa5e
    aa54:	09 95       	cmp	r5,	r9	
    aa56:	08 28       	jnc	$+18     	;abs 0xaa68
    aa58:	02 20       	jnz	$+6      	;abs 0xaa5e
    aa5a:	08 94       	cmp	r4,	r8	
    aa5c:	05 28       	jnc	$+12     	;abs 0xaa68
    aa5e:	08 84       	sub	r4,	r8	
    aa60:	09 75       	subc	r5,	r9	
    aa62:	0a 76       	subc	r6,	r10	
    aa64:	0b 77       	subc	r7,	r11	
    aa66:	1c d3       	bis	#1,	r12	;r3 As==01
    aa68:	91 83 00 00 	dec	0(r1)		;0x0000(r1)
    aa6c:	e5 23       	jnz	$-52     	;abs 0xaa38
    aa6e:	21 53       	incd	r1		
    aa70:	34 41       	pop	r4		
    aa72:	35 41       	pop	r5		
    aa74:	36 41       	pop	r6		
    aa76:	37 41       	pop	r7		
    aa78:	30 41       	ret			

0000aa7a <__udivdi3>:
    aa7a:	0b 12       	push	r11		
    aa7c:	0a 12       	push	r10		
    aa7e:	09 12       	push	r9		
    aa80:	08 12       	push	r8		
    aa82:	18 41 0a 00 	mov	10(r1),	r8	;0x000a(r1)
    aa86:	19 41 0c 00 	mov	12(r1),	r9	;0x000c(r1)
    aa8a:	1a 41 0e 00 	mov	14(r1),	r10	;0x000e(r1)
    aa8e:	1b 41 10 00 	mov	16(r1),	r11	;0x0010(r1)
    aa92:	b0 12 1c aa 	call	#0xaa1c	
    aa96:	38 41       	pop	r8		
    aa98:	39 41       	pop	r9		
    aa9a:	3a 41       	pop	r10		
    aa9c:	3b 41       	pop	r11		
    aa9e:	30 41       	ret			

0000aaa0 <__umoddi3>:
    aaa0:	0b 12       	push	r11		
    aaa2:	0a 12       	push	r10		
    aaa4:	09 12       	push	r9		
    aaa6:	08 12       	push	r8		
    aaa8:	18 41 0a 00 	mov	10(r1),	r8	;0x000a(r1)
    aaac:	19 41 0c 00 	mov	12(r1),	r9	;0x000c(r1)
    aab0:	1a 41 0e 00 	mov	14(r1),	r10	;0x000e(r1)
    aab4:	1b 41 10 00 	mov	16(r1),	r11	;0x0010(r1)
    aab8:	b0 12 1c aa 	call	#0xaa1c	
    aabc:	0c 48       	mov	r8,	r12	
    aabe:	0d 49       	mov	r9,	r13	
    aac0:	0e 4a       	mov	r10,	r14	
    aac2:	0f 4b       	mov	r11,	r15	
    aac4:	38 41       	pop	r8		
    aac6:	39 41       	pop	r9		
    aac8:	3a 41       	pop	r10		
    aaca:	3b 41       	pop	r11		
    aacc:	30 41       	ret			

0000aace <__udivmoddi4>:
    aace:	0b 12       	push	r11		
    aad0:	0a 12       	push	r10		
    aad2:	09 12       	push	r9		
    aad4:	08 12       	push	r8		
    aad6:	07 12       	push	r7		
    aad8:	18 41 0c 00 	mov	12(r1),	r8	;0x000c(r1)
    aadc:	19 41 0e 00 	mov	14(r1),	r9	;0x000e(r1)
    aae0:	1a 41 10 00 	mov	16(r1),	r10	;0x0010(r1)
    aae4:	1b 41 12 00 	mov	18(r1),	r11	;0x0012(r1)
    aae8:	b0 12 1c aa 	call	#0xaa1c	
    aaec:	17 41 14 00 	mov	20(r1),	r7	;0x0014(r1)
    aaf0:	87 48 00 00 	mov	r8,	0(r7)	;0x0000(r7)
    aaf4:	87 49 02 00 	mov	r9,	2(r7)	;0x0002(r7)
    aaf8:	87 4a 04 00 	mov	r10,	4(r7)	;0x0004(r7)
    aafc:	87 4b 06 00 	mov	r11,	6(r7)	;0x0006(r7)
    ab00:	37 41       	pop	r7		
    ab02:	38 41       	pop	r8		
    ab04:	39 41       	pop	r9		
    ab06:	3a 41       	pop	r10		
    ab08:	3b 41       	pop	r11		
    ab0a:	30 41       	ret			

Disassembly of section .vectors:

0000ffe0 <__ivtbl_16>:
    ffe0:	08 42 a6 42 08 42 08 42 12 43 6c 4e 78 78 08 42     .B.B.B.B.ClNxx.B
    fff0:	08 42 08 42 6e 7e 08 42 ec 42 08 42 08 42 00 40     .B.Bn~.B.B.B.B.@
msp430-objdump -x

user@409f9b5f2321:/work$ msp430-objdump -x nullnet-unicast.sky

nullnet-unicast.sky:     file format elf32-msp430
nullnet-unicast.sky
architecture: msp430:430, flags 0x00000112:
EXEC_P, HAS_SYMS, D_PAGED
start address 0x00004000

Program Header:
    LOAD off    0x00000000 vaddr 0x00003f4c paddr 0x00003f4c align 2**0
         filesz 0x00007287 memsz 0x00007287 flags r-x
    LOAD off    0x00007288 vaddr 0x00001100 paddr 0x0000b1d4 align 2**0
         filesz 0x0000114a memsz 0x00001d56 flags rw-
    LOAD off    0x000083d2 vaddr 0x00002e56 paddr 0x0000c31e align 2**0
         filesz 0x00000000 memsz 0x00000002 flags rw-
    LOAD off    0x000083d2 vaddr 0x0000ffe0 paddr 0x0000ffe0 align 2**0
         filesz 0x00000020 memsz 0x00000020 flags r-x

Sections:
Idx Name          Size      VMA       LMA       File off  Algn
  0 .text         00006b0c  00004000  00004000  000000b4  2**1
                  CONTENTS, ALLOC, LOAD, READONLY, CODE
  1 .rodata       000006c7  0000ab0c  0000ab0c  00006bc0  2**2
                  CONTENTS, ALLOC, LOAD, READONLY, DATA
  2 .data         0000114a  00001100  0000b1d4  00007288  2**1
                  CONTENTS, ALLOC, LOAD, DATA
  3 .bss          00000c0c  0000224a  0000c31e  000083d2  2**1
                  ALLOC
  4 .noinit       00000002  00002e56  0000c31e  000083d2  2**1
                  ALLOC
  5 .vectors      00000020  0000ffe0  0000ffe0  000083d2  2**0
                  CONTENTS, ALLOC, LOAD, READONLY, CODE
  6 .comment      00000030  00000000  00000000  000083f2  2**0
                  CONTENTS, READONLY
  7 .debug_aranges 00000374  00000000  00000000  00008424  2**2
                  CONTENTS, READONLY, DEBUGGING
  8 .debug_info   00004e6a  00000000  00000000  00008798  2**0
                  CONTENTS, READONLY, DEBUGGING
  9 .debug_abbrev 00002684  00000000  00000000  0000d602  2**0
                  CONTENTS, READONLY, DEBUGGING
 10 .debug_line   00001c0d  00000000  00000000  0000fc86  2**0
                  CONTENTS, READONLY, DEBUGGING
 11 .debug_frame  00000682  00000000  00000000  00011894  2**1
                  CONTENTS, READONLY, DEBUGGING
 12 .debug_str    0000089d  00000000  00000000  00011f16  2**0
                  CONTENTS, READONLY, DEBUGGING
 13 .debug_loc    000033b8  00000000  00000000  000127b3  2**0
                  CONTENTS, READONLY, DEBUGGING
 14 .debug_ranges 00000148  00000000  00000000  00015b6b  2**0
                  CONTENTS, READONLY, DEBUGGING
SYMBOL TABLE:
00004000 l    d  .text	00000000 .text
0000ab0c l    d  .rodata	00000000 .rodata
00001100 l    d  .data	00000000 .data
0000224a l    d  .bss	00000000 .bss
00002e56 l    d  .noinit	00000000 .noinit
0000ffe0 l    d  .vectors	00000000 .vectors
00000000 l    d  .comment	00000000 .comment
00000000 l    d  .debug_aranges	00000000 .debug_aranges
00000000 l    d  .debug_info	00000000 .debug_info
00000000 l    d  .debug_abbrev	00000000 .debug_abbrev
00000000 l    d  .debug_line	00000000 .debug_line
00000000 l    d  .debug_frame	00000000 .debug_frame
00000000 l    d  .debug_str	00000000 .debug_str
00000000 l    d  .debug_loc	00000000 .debug_loc
00000000 l    d  .debug_ranges	00000000 .debug_ranges
00000000 l    df *ABS*	00000000 contiki-main.c
00004208 l       .text	00000000 __br_unexpected_
00000000 l    df *ABS*	00000000 autostart.c
00000000 l    df *ABS*	00000000 button-sensor.c
00004222 l     F .text	00000018 status
0000423a l     F .text	00000020 value
0000224a l     O .bss	00000008 debouncetimer
0000425a l     F .text	0000004c configure
00000000 l    df *ABS*	00000000 cc2420-arch-sfd.c
00000000 l    df *ABS*	00000000 cc2420-arch.c
00000000 l    df *ABS*	00000000 cc2420.c
0000434c l     F .text	00000004 get_object
00004350 l     F .text	00000004 set_object
00004354 l     F .text	0000001c strobe
00004370 l     F .text	0000004c getreg
000043bc l     F .text	0000004c setreg
00004408 l     F .text	0000007c write_ram
00004484 l     F .text	0000003c write_fifo_buf
000044c0 l     F .text	00000020 get_status
000044e0 l     F .text	0000001a on
00002252 l     O .bss	00000001 poll_mode
00002259 l     O .bss	00000001 receive_on
000044fa l     F .text	0000000c cc2420_receiving_packet
00004506 l     F .text	00000008 pending_packet
0000450e l     F .text	00000022 wait_for_transmission
00004530 l     F .text	00000028 wait_for_status
00004558 l     F .text	00000050 getrxdata
000045a8 l     F .text	0000001a flushrx
000045c2 l     F .text	00000028 off
000045ea l     F .text	00000028 RELEASE_LOCK
00002256 l     O .bss	00000001 locked
00002257 l     O .bss	00000001 lock_on
00002258 l     O .bss	00000001 lock_off
00004612 l     F .text	00000018 set_key
0000462a l     F .text	00000030 set_frame_filtering
0000465a l     F .text	00000030 set_auto_ack
0000468a l     F .text	0000002c set_poll_mode
000046b6 l     F .text	00000046 cc2420_prepare
0000471e l     F .text	00000066 cc2420_transmit
0000110a l     O .data	00000001 send_on_cca
00004784 l     F .text	00000012 cc2420_send
000047c6 l     F .text	00000068 cc2420_cca
0000482e l     F .text	000000be cc2420_read
000048ec l     F .text	00000056 process_thread_cc2420_process
00004942 l     F .text	00000088 encrypt
00002260 l     O .bss	00000002 channel
00002254 l     O .bss	00000002 last_packet_timestamp
00004afe l     F .text	0000011e get_value
0000ab8e l     O .rodata	00000010 output_power
00004c32 l     F .text	00000150 set_value
0000225a l     O .bss	00000001 was_on
0000225c l     O .bss	00000002 prev_MDMCTRL1
0000225e l     O .bss	00000002 prev_DACTST
00000000 l    df *ABS*	00000000 clock.c
00002264 l     O .bss	00000004 count
00002268 l     O .bss	00000004 seconds
00002262 l     O .bss	00000002 last_tar
00000000 l    df *ABS*	00000000 contiki-sky-platform.c
00000000 l    df *ABS*	00000000 csma-output.c
00004fa2 l     F .text	00000070 schedule_transmission
000050ac l     F .text	000001c0 transmit_from_queue
00005012 l     F .text	0000009a tx_done
00001120 l     O .data	00000008 metadata_memb
00001118 l     O .data	00000008 packet_memb
0000226c l     O .bss	00000002 neighbor_list_list
00001110 l     O .data	00000008 neighbor_memb
0000226e l     O .bss	00000002 neighbor_memb_memb_used
00002270 l     O .bss	00000048 neighbor_memb_memb_mem
000022b8 l     O .bss	00000008 packet_memb_memb_used
000022c0 l     O .bss	00000030 packet_memb_memb_mem
000022f0 l     O .bss	00000008 metadata_memb_memb_used
000022f8 l     O .bss	00000030 metadata_memb_memb_mem
00000000 l    df *ABS*	00000000 csma-security.c
00000000 l    df *ABS*	00000000 csma.c
000053f4 l     F .text	00000006 on
000053fa l     F .text	00000006 off
00005400 l     F .text	00000038 max_payload
00005438 l     F .text	00000006 send_packet
0000543e l     F .text	00000060 input_packet
0000549e l     F .text	00000020 init
00000000 l    df *ABS*	00000000 ctimer.c
000054be l     F .text	000000a8 process_thread_ctimer_process
0000232a l     O .bss	00000002 ctimer_list_list
00002328 l     O .bss	00000001 initialized
00000000 l    df *ABS*	00000000 ds2411.c
00005634 l     F .text	00000050 owreadb
00000000 l    df *ABS*	00000000 energest.c
00000000 l    df *ABS*	00000000 etimer.c
000057a8 l     F .text	00000078 update_time
0000232c l     O .bss	00000002 timerlist
0000232e l     O .bss	00000004 next_expiration
0000582a l     F .text	000000cc process_thread_etimer_process
000058f6 l     F .text	00000040 add_timer
00000000 l    df *ABS*	00000000 frame802154.c
0000113c l     O .data	00000002 mac_pan_id
00005aae l     F .text	000000ac field_len
0000b019 l     O .rodata	00000002 CSWTCH.16
00000000 l    df *ABS*	00000000 framer-802154.c
00005f52 l     F .text	000000a2 parse
000060ac l     F .text	000000a2 create_frame
0000614e l     F .text	00000008 create
00006156 l     F .text	00000008 hdr_length
00000000 l    df *ABS*	00000000 leds-arch.c
00000000 l    df *ABS*	00000000 leds.c
00000000 l    df *ABS*	00000000 linkaddr.c
00000000 l    df *ABS*	00000000 list.c
00000000 l    df *ABS*	00000000 log.c
0000ac5e l     O .rodata	0000000a CSWTCH.8
00000000 l    df *ABS*	00000000 mac-sequence.c
00002348 l     O .bss	00000001 mac_dsn
0000234a l     O .bss	000000e0 received_seqnos
00000000 l    df *ABS*	00000000 mac.c
00000000 l    df *ABS*	00000000 memb.c
00000000 l    df *ABS*	00000000 msp430.c
0000118e l     O .data	00000002 cur_break
00000000 l    df *ABS*	00000000 netstack.c
00000000 l    df *ABS*	00000000 node-id.c
00000000 l    df *ABS*	00000000 nullnet-unicast.c
00006672 l     F .text	000001e4 process_thread_nullnet_example_process
00002546 l     O .bss	00000002 count.3214
00002548 l     O .bss	0000000c periodic_timer.3213
00002554 l     O .bss	00000002 count4Edges.3215
00000000 l    df *ABS*	00000000 nullnet.c
000070ba l     F .text	00000006 init
00002556 l     O .bss	00000002 current_callback
000070c0 l     F .text	00000042 output
00007102 l     F .text	00000040 input
00000000 l    df *ABS*	00000000 nullrouting.c
00007148 l     F .text	00000002 init
0000714a l     F .text	00000002 root_set_prefix
0000714c l     F .text	00000004 root_start
00007150 l     F .text	00000004 node_is_root
00007154 l     F .text	00000004 get_root_ipaddr
00007158 l     F .text	00000004 get_sr_node_ipaddr
0000715c l     F .text	00000002 leave_network
0000715e l     F .text	00000004 node_has_joined
00007162 l     F .text	00000004 node_is_reachable
00007166 l     F .text	00000002 global_repair
00007168 l     F .text	00000002 local_repair
0000716a l     F .text	00000004 ext_header_remove
0000716e l     F .text	00000004 ext_header_update
00007172 l     F .text	00000004 ext_header_hbh_update
00007176 l     F .text	00000004 ext_header_srh_update
0000717a l     F .text	00000004 ext_header_srh_get_next_hop
0000717e l     F .text	00000002 link_callback
00007180 l     F .text	00000002 neighbor_state_changed
00007182 l     F .text	00000002 drop_route
00007184 l     F .text	00000004 is_in_leaf_mode
00000000 l    df *ABS*	00000000 packetbuf.c
0000255a l     O .bss	00000002 buflen
00002558 l     O .bss	00000002 bufptr
0000255e l     O .bss	00000080 packetbuf_aligned
0000255c l     O .bss	00000001 hdrlen
00000000 l    df *ABS*	00000000 platform.c
000025de l     O .bss	00000008 mgt_timer
00000000 l    df *ABS*	00000000 process.c
000074a8 l     F .text	00000046 call_process
000074ee l     F .text	00000096 exit_process
00007584 l     F .text	00000030 do_poll
000025ea l     O .bss	00000001 poll_requested
000025eb l     O .bss	00000001 lastevent
000025ec l     O .bss	00000001 fevent
000025ed l     O .bss	00000001 nevents
000025ee l     O .bss	000000c0 events
00000000 l    df *ABS*	00000000 queuebuf.c
00002218 l     O .data	00000008 buframmem
00002220 l     O .data	00000008 bufmem
000026ae l     O .bss	00000008 buframmem_memb_used
000026b6 l     O .bss	00000550 buframmem_memb_mem
00002c06 l     O .bss	00000008 bufmem_memb_used
00002c0e l     O .bss	00000010 bufmem_memb_mem
00000000 l    df *ABS*	00000000 random.c
00000000 l    df *ABS*	00000000 ringbuf.c
00000000 l    df *ABS*	00000000 rtimer-arch.c
00000000 l    df *ABS*	00000000 rtimer.c
00002c1e l     O .bss	00000002 next_rtimer
00000000 l    df *ABS*	00000000 sensors.c
000078f4 l     F .text	000000c2 process_thread_sensors_process
00002c22 l     O .bss	00000002 i.2007
00002c20 l     O .bss	00000001 num_sensors
00002c24 l     O .bss	00000002 events.2008
00000000 l    df *ABS*	00000000 serial-line.c
000079e0 l     F .text	000000a4 process_thread_serial_line_process
00002c2e l     O .bss	00000002 ptr.1992
00002c28 l     O .bss	00000006 rxbuf
00002c30 l     O .bss	00000080 buf.1991
00002c26 l     O .bss	00000001 overflow.1985
00002cb0 l     O .bss	00000080 rxbuf_data
00000000 l    df *ABS*	00000000 spi-legacy.c
00000000 l    df *ABS*	00000000 stack-check.c
00002d30 l     O .bss	00000002 stack_top.2047
00007b94 l     F .text	000000ea process_thread_stack_check_process
00002d32 l     O .bss	0000000c et.2069
00000000 l    df *ABS*	00000000 timer.c
00000000 l    df *ABS*	00000000 uart1-putchar.c
00000000 l    df *ABS*	00000000 uart1.c
00007cf0 l     F .text	0000003a handle_rxdma_timer
00002d56 l     O .bss	00000080 rxbuf
00002d54 l     O .bss	00000002 uart1_input_handler
00002dd6 l     O .bss	00000002 last_size
00002d40 l     O .bss	00000014 rxdma_timer
00002d3f l     O .bss	00000001 rx_in_progress
00002d3e l     O .bss	00000001 transmitting
00000000 l    df *ABS*	00000000 watchdog.c
00002dd8 l     O .bss	00000002 counter
00000000 l    df *ABS*	00000000 xmem.c
00000000 l    df *ABS*	00000000 ef_pow.c
0000af0e l     O .rodata	00000008 bp
0000af16 l     O .rodata	00000008 dp_l
0000af1e l     O .rodata	00000008 dp_h
00000000 l    df *ABS*	00000000 sf_scalbn.c
00000000 l    df *ABS*	00000000 ef_sqrt.c
00000000 l    df *ABS*	00000000 libgcc2.c
00000000 l    df *ABS*	00000000 libgcc2.c
00000000 l    df *ABS*	00000000 libgcc2.c
00000000 l    df *ABS*	00000000 fp-bit.c
000090d8 l     F .text	00000282 _fpadd_parts
00000000 l    df *ABS*	00000000 fp-bit.c
00000000 l    df *ABS*	00000000 fp-bit.c
00000000 l    df *ABS*	00000000 fp-bit.c
00000000 l    df *ABS*	00000000 fp-bit.c
00000000 l    df *ABS*	00000000 fp-bit.c
00000000 l    df *ABS*	00000000 fp-bit.c
00000000 l    df *ABS*	00000000 fp-bit.c
00000000 l    df *ABS*	00000000 fp-bit.c
00000000 l    df *ABS*	00000000 fp-bit.c
00000000 l    df *ABS*	00000000 libgcc2.c
00000000 l    df *ABS*	00000000 fp-bit.c
00000000 l    df *ABS*	00000000 fp-bit.c
00000000 l    df *ABS*	00000000 fp-bit.c
00000000 l    df *ABS*	00000000 printf.c
00000000 l    df *ABS*	00000000 sprintf.c
00009edc l     F .text	00000022 append
00002ddc l     O .bss	00000002 available_
00002dda l     O .bss	00000002 destination_
00009efe l     F .text	0000003a call_vuprintf
00000000 l    df *ABS*	00000000 vuprintf.c
00009f54 l     F .text	00000194 print_field
00000000 l    df *ABS*	00000000 puts.c
00000000 l    df *ABS*	00000000 rand.c
00002246 l     O .data	00000004 next
00000000 l    df *ABS*	00000000 memcmp.c
00000000 l    df *ABS*	00000000 memcpy.c
00000000 l    df *ABS*	00000000 memset.c
00000000 l    df *ABS*	00000000 fp-bit.c
00000000 l    df *ABS*	00000000 libgcc2.c
00007ce0 g     F .text	00000010 putchar
0000119c g     O .data	00000064 isAnchor90Percent
00000057 g       *ABS*	00000000 __BCSCTL1
0000005a g       *ABS*	00000000 __CACTL2
00000174 g       *ABS*	00000000 __TACCR1
00000000         *UND*	00000000 gpio_hal_arch_port_pin_set_input
00000000 g       *ABS*	00000000 _far_end
000077f4 g     F .text	00000006 random_rand
00002e1e g     O .bss	00000002 nullnet_buf
00004d82 g     F .text	000000ea cc2420_init
0000aeb4 g     O .rodata	00000004 anchorx17
00000084 g       *ABS*	00000000 __ADC12MCTL4
000078b4 g     F .text	0000000e rtimer_arch_now
00000000         *UND*	00000000 _clear_bss_init__
0000114a g       *ABS*	00000000 __data_size
0000015a g       *ABS*	00000000 __ADC12MEM13
00000052 g       *ABS*	00000000 __I2CNDAT
00004208  w      .text	00000000 __isr_14
00000128 g       *ABS*	00000000 __FCTL1
00001200 g     O .data	00000064 isAnchor80Percent
0000615e g     F .text	0000000e leds_arch_init
00000024 g       *ABS*	00000000 __P1IES
000071ca g     F .text	00000046 packetbuf_copyto
00000000 g       .vectors	00000000 _efardata
0000007b g       *ABS*	00000000 __U1MCTL
00002dde g     O .bss	00000001 cc2420_last_rssi
000001f6 g       *ABS*	00000000 __DMA2SZ
00009ecc g     F .text	00000010 printf
00000000         *UND*	00000000 gpio_hal_arch_port_write_pin
0000242c g     O .bss	00000008 b
00004312 g       .text	00000000 __isr_4
00000002 g       *ABS*	00000000 __IFG1
000072c0 g     F .text	00000022 packetbuf_attr_copyto
00007454 g     F .text	00000054 platform_idle
00005968 g     F .text	0000000c etimer_pending
00000076 g       *ABS*	00000000 __I2CDRW
0000113e g     O .data	0000004e all_modules
00001f5c g     O .data	00000064 percentage70
00005ff4 g     F .text	000000b8 framer_802154_setup_params
0000007e g       *ABS*	00000000 __U1RXBUF
00000138 g       *ABS*	00000000 __OP2
00000076 g       *ABS*	00000000 __U0RXBUF
0000616c g     F .text	00000034 leds_arch_get
00009606 g     F .text	00000148 __divsf3
00004a06 g     F .text	0000004c cc2420_set_pan_addr
000001a4 g       *ABS*	00000000 __ADC12IFG
00007292 g     F .text	0000002e packetbuf_copyfrom
0000632a g     F .text	00000084 mac_sequence_is_duplicate
0000012e g       *ABS*	00000000 __TAIV
00008b48 g     F .text	00000006 powf
00006312 g     F .text	00000018 mac_sequence_set_dsn
00000000         *UND*	00000000 gpio_hal_arch_port_pin_cfg_set
0000767a g     F .text	00000042 process_post
0000992e g     F .text	0000008c __fixsfsi
000001e6 g       *ABS*	00000000 __DMA0SZ
00010000 g       *ABS*	00000000 _efartext
00001132 g     O .data	0000000a etimer_process
0000a9ba g     F .text	00000000 __udivhi3
0000007c g       *ABS*	00000000 __U1BR0
00000130 g       *ABS*	00000000 __MPY
00000001 g       *ABS*	00000000 __IE2
00002de0 g     O .bss	00000002 cc2420_sfd_start_time
0000ab64 g     O .rodata	0000001c cc2420_driver
0000013a g       *ABS*	00000000 __RESLO
00000136 g       *ABS*	00000000 __MACS
000042a6 g     F .text	00000046 irq_p2
00000087 g       *ABS*	00000000 __ADC12MCTL7
000055cc g     F .text	00000010 ctimer_set
0000002b g       *ABS*	00000000 __P2IFG
00005bb4 g     F .text	00000096 frame802154_create_fcf
0000001a g       *ABS*	00000000 __P3DIR
00007312 g     F .text	0000000a packetbuf_attr
0000aed0 g     O .rodata	00000008 nullnet_driver
000078ce g     F .text	00000026 rtimer_run_next
0000b1d4 g       *ABS*	00000000 _etext
00000190 g       *ABS*	00000000 __TBR
00005948 g     F .text	00000012 etimer_reset
00004a52 g     F .text	00000016 cc2420_interrupt
00000000         *UND*	00000000 button_hal_button_count
000093a6 g     F .text	00000050 __subsf3
0000001d g       *ABS*	00000000 __P4OUT
00000000         *UND*	00000000 gpio_hal_arch_port_read_pin
0000233c g     O .bss	00000002 curr_log_level_mac
0000766c g     F .text	0000000e process_nevents
000077fa g     F .text	00000014 ringbuf_init
000021b4 g     O .data	00000064 percentage10
0000627e g     F .text	0000002a list_add
000001f4 g       *ABS*	00000000 __DMA2DA
00000c0c g       *ABS*	00000000 __bss_size
00000081 g       *ABS*	00000000 __ADC12MCTL1
00007d7a g     F .text	000000f4 uart1_init
00000152 g       *ABS*	00000000 __ADC12MEM9
0000233a g     O .bss	00000002 curr_log_level_framer
0000ab60 g     O .rodata	00000004 cc2420_aes_128_driver
000049ca g     F .text	0000003c cc2420_set_channel
00004000  w      .text	00000000 __watchdog_support
00004202  w      .text	00000000 __stop_progExec__
000025e8 g     O .bss	00000002 process_list
00002434 g     O .bss	00000020 A
0000a7b2 g     F .text	000000fa memcpy
00001192 g     O .data	0000000a nullnet_example_process
00000050 g       *ABS*	00000000 __I2CIE
00001dcc g     O .data	000000c8 AnchorIndexes
0000002d g       *ABS*	00000000 __P2IE
00004a68 g     F .text	0000002c cc2420_set_txpower
000001e4 g       *ABS*	00000000 __DMA0DA
00005c4a g     F .text	000000e4 frame802154_create
000071a2 g     F .text	00000006 packetbuf_set_datalen
00000000         *UND*	00000000 slip_input_byte
0000a726 g     F .text	0000002c puts
00004f96 g     F .text	0000000c init_platform
00001100 g     O .data	0000000a cc2420_process
000071ae g     F .text	00000006 packetbuf_datalen
00002e22 g     O .bss	00000010 packetbuf_addrs
000062a8 g     F .text	00000010 list_length
000073ce g     F .text	00000086 platform_init_stage_three
00000192 g       *ABS*	00000000 __TBCCR0
00005b5a g     F .text	00000028 frame802154_is_broadcast_addr
0000abb2 g     O .rodata	0000000e csma_driver
00004208  w      .text	00000000 __isr_11
00001520 g     O .data	000004c4 anchor_nodes
00000186 g       *ABS*	00000000 __TBCCTL2
0000a9dc g     F .text	00000000 __udivsi3
00000025 g       *ABS*	00000000 __P1IE
000072e2 g     F .text	00000024 packetbuf_attr_copyfrom
00007ae2 g     F .text	00000030 spi_init
00002df4 g     O .bss	00000004 distance_zero
000001a0 g       *ABS*	00000000 __ADC12CTL0
000076ce g     F .text	00000036 process_start
00007e88 g     F .text	00000012 watchdog_periodic
00009838 g     F .text	0000004e __lesf2
000065da g     F .text	0000000a splhigh_
00000072 g       *ABS*	00000000 __I2CDCTL
000053ee g     F .text	00000006 csma_security_parse_frame
00000073 g       *ABS*	00000000 __U0MCTL
000076bc g     F .text	00000012 process_post_synch
00000000         *UND*	00000000 gpio_hal_arch_port_write_pins
00002334 g     O .bss	00000002 curr_log_level_snmp
0000007a g       *ABS*	00000000 __U1RCTL
000065e4 g     F .text	0000006c msp430_sync_dco
00006238 g     F .text	00000012 list_tail
000042ec g     F .text	00000026 cc2420_timerb1_interrupt
00002df8 g     O .bss	00000004 d_diff
00000082 g       *ABS*	00000000 __ADC12MCTL2
0000019c g       *ABS*	00000000 __TBCCR5
00007e74 g     F .text	00000014 watchdog_start
0000aace g       .text	00000000 __udivmoddi4
0000118c g     O .data	00000002 curr_log_level_main
00005936 g     F .text	00000012 etimer_set
00004a94 g     F .text	0000001e cc2420_get_txpower
00000035 g       *ABS*	00000000 __P6OUT
0000a97a g       .text	00000000 __xabi_muldi3
00002dfc g     O .bss	00000004 y_diff
00000034 g       *ABS*	00000000 __P6IN
0000aeb8 g     O .rodata	00000004 anchory4
000001c8 g       *ABS*	00000000 __DAC12_0DAT
00000182 g       *ABS*	00000000 __TBCCTL0
0000abc6 g     O .rodata	00000008 linkaddr_null
00000000         *UND*	00000000 gpio_hal_arch_init
00006222 g     F .text	0000000c linkaddr_set_node_addr
000061a0 g     F .text	0000003e leds_arch_set
00007b12 g     F .text	0000002e stack_check_init
000055dc g     F .text	00000030 ctimer_reset
0000019e g       *ABS*	00000000 __TBCCR6
00004e6c g       .text	00000000 __isr_5
00000000         *UND*	00000000 uip_aligned_buf
0000aaa0 g     F .text	00000000 __umoddi3
0000b1d4 g       *ABS*	00000000 __data_load_start
000061e4 g     F .text	00000012 leds_on
00001ef8 g     O .data	00000064 percentage80
00004208 g       .text	00000000 __dtors_end
000059c8 g     F .text	00000006 frame802154_get_pan_id
00007704 g     F .text	00000018 process_poll
00007792 g     F .text	0000002a queuebuf_free
000001ea g       *ABS*	00000000 __DMA1SA
00002e56 g       .bss	00000000 __bss_end
00000088 g       *ABS*	00000000 __ADC12MCTL8
00000166 g       *ABS*	00000000 __TACCTL2
0000aebc g     O .rodata	00000004 anchorx4
0000771c g     F .text	00000012 queuebuf_init
0000aa7a g     F .text	00000000 __udivdi3
000001f0 g       *ABS*	00000000 __DMA2CTL
0000242a g     O .bss	00000002 node_id
0000233e g     O .bss	00000002 curr_log_level_nullnet
000019e4 g     O .data	000003e8 node_positions
000062c4 g     F .text	00000044 log_lladdr
00004208  w      .text	00000000 __isr_2
00000156 g       *ABS*	00000000 __ADC12MEM11
00006234 g     F .text	00000004 list_head
00000160 g       *ABS*	00000000 __TACTL
00000158 g       *ABS*	00000000 __ADC12MEM12
00000071 g       *ABS*	00000000 __I2CTCTL
0000012c g       *ABS*	00000000 __FCTL3
00002454 g     O .bss	000000f2 rssiList
00006208 g     F .text	00000008 linkaddr_copy
00007e6e g       .text	00000000 __isr_10
000075b4 g     F .text	0000000e process_alloc_event
00000148 g       *ABS*	00000000 __ADC12MEM4
0000011a g       *ABS*	00000000 __I2CSA
0000002e g       *ABS*	00000000 __P2SEL
000065b0 g     F .text	0000002a msp430_cpu_init
00000180 g       *ABS*	00000000 __TBCTL
00002150 g     O .data	00000064 percentage20
0000008d g       *ABS*	00000000 __ADC12MCTL13
00002de2 g     O .bss	00000001 cc2420_last_correlation
00002dea g     O .bss	00000008 linkaddr_node_addr
0000014c g       *ABS*	00000000 __ADC12MEM6
00000023 g       *ABS*	00000000 __P1IFG
00009cec g     F .text	0000013c __unpack_f
0000557e g     F .text	0000004e ctimer_set_with_process
0000013c g       *ABS*	00000000 __RESHI
00000072 g       *ABS*	00000000 __U0RCTL
00000172 g       *ABS*	00000000 __TACCR0
00000071 g       *ABS*	00000000 __U0TCTL
000061f6 g     F .text	00000012 leds_off
00000056 g       *ABS*	00000000 __DCOCTL
00000085 g       *ABS*	00000000 __ADC12MCTL5
00000003 g       *ABS*	00000000 __IFG2
00000005 g       *ABS*	00000000 __ME2
0000780e g     F .text	00000038 ringbuf_put
00002e56 g     O .noinit	00000002 __wdt_clear_value
00000000 g       *ABS*	00000000 __far_data_size
0000aec0 g     O .rodata	00000004 anchory1
00005566 g     F .text	00000018 ctimer_init
00002e00 g     O .bss	00000008 estimated_position_x
00000079 g       *ABS*	00000000 __U1TCTL
000059ce g     F .text	000000e0 frame802154_has_panid
0000001b g       *ABS*	00000000 __P3SEL
000001e0 g       *ABS*	00000000 __DMA0CTL
0000974e g     F .text	0000004e __gtsf2
00000000         *UND*	00000000 InterruptVectors
00004208  w      .text	00000000 __isr_7
00002de4 g     O .bss	00000002 cc2420_authority_level_of_sender
0000ffe0 g     O .vectors	00000020 __ivtbl_16
00004c1c g     F .text	00000016 cc2420_set_cca_threshold
00004f62 g     F .text	00000028 clock_init
0000aa12 g     F .text	00000000 __umodsi3
00007306 g     F .text	0000000c packetbuf_set_attr
00000028 g       *ABS*	00000000 __P2IN
00007c9a g     F .text	0000002a timer_expired
00007210 g     F .text	0000000c packetbuf_totlen
0000014e g       *ABS*	00000000 __ADC12MEM7
00009b12 g     F .text	000001da __pack_f
00000184 g       *ABS*	00000000 __TBCCTL1
0000005b g       *ABS*	00000000 __CAPD
00000075 g       *ABS*	00000000 __I2CSCLL
0000a9d4 g     F .text	00000000 __umodhi3
000078a6 g     F .text	0000000e rtimer_arch_init
00004208  w      .text	00000000 __isr_0
00002e32 g     O .bss	00000018 packetbuf_attrs
00000029 g       *ABS*	00000000 __P2OUT
00006308 g     F .text	0000000a mac_sequence_init
00009aa0 g     F .text	00000072 __clzsi2
0000012a g       *ABS*	00000000 __FCTL2
00002df2 g     O .bss	00000002 msp430_dco_required
00006650 g     F .text	0000000e netstack_init
00004028  w      .text	00000000 __do_clear_bss
0000008f g       *ABS*	00000000 __ADC12MCTL15
000046fc g     F .text	00000022 cc2420_on
0000772e g     F .text	00000052 queuebuf_new_from_packetbuf
00002332 g     O .bss	00000002 curr_log_level_lwm2m
00000021 g       *ABS*	00000000 __P1OUT
000078c2 g     F .text	00000006 rtimer_arch_schedule
00002346 g     O .bss	00000002 curr_log_level_rpl
00007e6e g     F .text	00000006 watchdog_interrupt
0000002c g       *ABS*	00000000 __P2IES
0000015c g       *ABS*	00000000 __ADC12MEM14
00000000         *UND*	00000000 _end_of_init__
00000026 g       *ABS*	00000000 __P1SEL
00006210 g     F .text	00000012 linkaddr_cmp
00007e9a g     F .text	00000016 watchdog_stop
00001390 g     O .data	00000064 isAnchor40Percent
00000198 g       *ABS*	00000000 __TBCCR3
00000080 g       *ABS*	00000000 __ADC12MCTL0
0000a752 g     F .text	00000026 rand
00002228 g     O .data	0000000a sensors_process
00000140 g       *ABS*	00000000 __ADC12MEM0
00007780 g     F .text	00000012 queuebuf_update_attr_from_packetbuf
00009886 g     F .text	000000a8 __floatsisf
00002232 g     O .data	0000000a serial_line_process
00000074 g       *ABS*	00000000 __U0BR0
00002de6 g     O .bss	00000001 cc2420_sfd_counter
000065a4 g     F .text	0000000c msp430_add_lpm_req
00000051 g       *ABS*	00000000 __I2CIFG
00000000         *UND*	00000000 button_hal_buttons
0000a9dc g       .text	00000000 __ext_udivmod32
00007846 g     F .text	00000032 ringbuf_get
00000000         *UND*	00000000 gpio_hal_arch_port_interrupt_enable
00002338 g     O .bss	00000002 curr_log_level_6top
0000a918 g       .text	00000000 __mulsi3
0000aee4 g     O .rodata	0000002a nullrouting_driver
00001190 g     O .data	00000002 anchor_count
0000a916  w      .text	00000000 _unexpected_
00004208  w      .text	00000000 __isr_8
0000014a g       *ABS*	00000000 __ADC12MEM5
00005974 g     F .text	00000016 etimer_next_expiration_time
00000070 g       *ABS*	00000000 __U0CTL
0000018a g       *ABS*	00000000 __TBCCTL4
0000721c g     F .text	0000003c packetbuf_hdralloc
00000073 g       *ABS*	00000000 __I2CPSC
0000008e g       *ABS*	00000000 __ADC12MCTL14
00004208  w      .text	00000000 __isr_3
000001a6 g       *ABS*	00000000 __ADC12IE
0000a0e8 g     F .text	0000063e vuprintf
00005820 g     F .text	0000000a etimer_request_poll
0000a782 g     F .text	00000030 memcmp
00000144 g       *ABS*	00000000 __ADC12MEM2
00007d62 g     F .text	00000018 uart1_writeb
00008f9a g     F .text	0000013e __floatundisf
000001ee g       *ABS*	00000000 __DMA1SZ
00000033 g       *ABS*	00000000 __P5SEL
0000ffe0 g       .vectors	00000000 __vectors_start
0000a9ba g       .text	00000000 __ext_udivmod16
00004e6c g     F .text	000000dc timera1
0000731c g     F .text	00000018 packetbuf_set_addr
00000030 g       *ABS*	00000000 __P5IN
00004000  w      .text	00000000 _reset_vector__
00004208 g       .text	00000000 __ctors_start
0000aa1c g       .text	00000000 __xabi_udivmod64
000042ec g       .text	00000000 __isr_12
00007efe g     F .text	00000c4a __ieee754_powf
00000036 g       *ABS*	00000000 __P6DIR
00001128 g     O .data	0000000a ctimer_process
0000af26 g     O .rodata	00000008 __thenan_sf
00007d42 g     F .text	00000020 uart1_set_input
00002024 g     O .data	00000064 percentage50
00001458 g     O .data	00000064 isAnchor20Percent
00004f8a g     F .text	0000000c clock_delay
00000018 g       *ABS*	00000000 __P3IN
00004010  w      .text	00000000 __do_copy_data
00008b4e g     F .text	00000174 scalbnf
00002e20 g     O .bss	00000002 nullnet_len
0000aec4 g     O .rodata	00000004 anchorx1
00002e08 g     O .bss	00000004 anchors_zero_x
000071b4 g     F .text	0000000a packetbuf_hdrlen
00004312 g     F .text	00000020 cc2420_port1_interrupt
00000150 g       *ABS*	00000000 __ADC12MEM8
00007d2a g     F .text	00000018 uart1_active
00000142 g       *ABS*	00000000 __ADC12MEM1
0000224a g       .bss	00000000 __bss_start
0000007d g       *ABS*	00000000 __U1BR1
000075c2 g     F .text	00000018 process_init
0000a8ac g     F .text	0000006a memset
00008cc2 g     F .text	00000172 __ieee754_sqrtf
0000403e g     F .text	000001c4 main
00001e94 g     O .data	00000064 percentage90
00000176 g       *ABS*	00000000 __TACCR2
00007334 g     F .text	00000012 packetbuf_addr
0000019a g       *ABS*	00000000 __TBCCR4
00007ec2 g     F .text	0000003c xmem_init
00007346 g     F .text	0000000e packetbuf_holds_broadcast
0000a778 g     F .text	0000000a srand
00004208  w      .text	00000000 __isr_13
000097ea g     F .text	0000004e __ltsf2
00000078 g       *ABS*	00000000 __U1CTL
00002344 g     O .bss	00000002 curr_log_level_tcpip
00000000         *UND*	00000000 gpio_hal_arch_port_clear_pin
000001e2 g       *ABS*	00000000 __DMA0SA
00000170 g       *ABS*	00000000 __TAR
00000124 g       *ABS*	00000000 __DMACTL1
000020ec g     O .data	00000064 percentage30
0000001e g       *ABS*	00000000 __P4DIR
000062b8 g     F .text	0000000c list_item_next
00002340 g     O .bss	00000002 curr_log_level_6lowpan
00006488 g     F .text	0000003e memb_alloc
00008e76 g     F .text	00000124 __fixunssfdi
00000162 g       *ABS*	00000000 __TACCTL0
00010000 g       .vectors	00000000 _vectors_end
00000154 g       *ABS*	00000000 __ADC12MEM10
000093f6 g     F .text	00000210 __mulsf3
0000223c g     O .data	0000000a stack_check_process
000053c4 g     F .text	0000001a csma_output_init
000001f2 g       *ABS*	00000000 __DMA2SA
000071a8 g     F .text	00000006 packetbuf_hdrptr
0000002a g       *ABS*	00000000 __P2DIR
000064c6 g     F .text	00000032 memb_free
00000089 g       *ABS*	00000000 __ADC12MCTL9
0000008a g       *ABS*	00000000 __ADC12MCTL10
0000598a g     F .text	0000003e etimer_stop
0000622e g     F .text	00000006 list_init
0000665e g     F .text	00000014 node_id_init
00000032 g       *ABS*	00000000 __P5DIR
00004332 g     F .text	0000001a cc2420_arch_init
00009f38 g     F .text	0000001c sprintf
0000b0cc g     O .rodata	00000100 __clz_tab
000001c2 g       *ABS*	00000000 __DAC12_1CTL
000057a6 g     F .text	00000002 energest_flush
000001a2 g       *ABS*	00000000 __ADC12CTL1
000077bc g     F .text	00000032 queuebuf_to_packetbuf
0000979c g     F .text	0000004e __gesf2
00002e0c g     O .bss	00000008 estimated_position_y
000077ee g     F .text	00000006 random_init
00000000 g       .vectors	00000000 __far_bss_start
00007a84 g     F .text	00000042 serial_line_input_byte
000001a8 g       *ABS*	00000000 __ADC12IV
000001e8 g       *ABS*	00000000 __DMA1CTL
00000075 g       *ABS*	00000000 __U0BR1
00002e56 g       .noinit	00000000 __noinit_start
00006452 g     F .text	00000036 memb_init
00007142 g     F .text	00000006 nullnet_set_input_callback
00006856 g     F .text	00000864 input_callback
000064f8 g     F .text	0000002a memb_inmemb
00004208  w      .text	00000000 __isr_9
00000000         *UND*	00000000 gpio_hal_arch_port_set_pin
000053de g     F .text	00000010 csma_security_create_frame
0000b1d4 g       *ABS*	00000000 __data_start_rom
00002e58 g       .noinit	00000000 __noinit_end
0000018c g       *ABS*	00000000 __TBCCTL5
00000000         *UND*	00000000 spi_arch_has_lock
00000000 g       .vectors	00000000 __far_bss_end
0000400c  w      .text	00000000 __init_stack
000063ae g     F .text	00000090 mac_sequence_register_seqno
00000086 g       *ABS*	00000000 __ADC12MCTL6
000057a4 g     F .text	00000002 energest_init
0000560c g     F .text	00000028 ctimer_stop
00007c7e g     F .text	0000001c timer_set
000012c8 g     O .data	00000064 isAnchor60Percent
00001264 g     O .data	00000064 isAnchor70Percent
00000188 g       *ABS*	00000000 __TBCCTL3
00007b40 g     F .text	00000054 stack_check_get_usage
00004796 g     F .text	00000030 cc2420_off
00000019 g       *ABS*	00000000 __P3OUT
00007cc4 g     F .text	0000001c timer_reset
000001ca g       *ABS*	00000000 __DAC12_1DAT
00005dea g     F .text	00000168 frame802154_parse
00004208 g       .text	00000000 __dtors_start
00007878 g       .text	00000000 __isr_6
00004208 g       .text	00000000 __ctors_end
00000132 g       *ABS*	00000000 __MPYS
0000011c g       *ABS*	00000000 __I2CIV
00005b82 g     F .text	00000032 frame802154_hdrlen
00000004 g       *ABS*	00000000 __ME1
00003900 g       *ABS*	00000000 __stack
000079b6 g     F .text	0000002a sensors_changed
00000037 g       *ABS*	00000000 __P6SEL
000042a6 g       .text	00000000 __isr_1
000075da g     F .text	00000092 process_run
0000008c g       *ABS*	00000000 __ADC12MCTL12
00002342 g     O .bss	00000002 curr_log_level_ipv6
00005d2e g     F .text	000000bc frame802154_parse_fcf
0000abc0 g     O .rodata	00000006 framer_802154
00000000 g       .vectors	00000000 __far_data_start
0000224a g       .data	00000000 _edata
00000077 g       *ABS*	00000000 __U0TXBUF
000025e6 g     O .bss	00000002 process_current
00002e58 g       *ABS*	00000000 _end
00000000         *UND*	00000000 gpio_hal_arch_port_read_pins
00007878 g     F .text	0000002e timera0
0000595a g     F .text	0000000e etimer_expired
0000526c g     F .text	00000158 csma_output_packet
00000194 g       *ABS*	00000000 __TBCCR1
00002e4a g     O .bss	00000002 sensors_flags
00001fc0 g     O .data	00000064 percentage60
0000ae94 g     O .rodata	00000004 autostart_processes
00002e14 g     O .bss	00000004 anchors_zero_y
00004ab2 g     F .text	0000004c cc2420_rssi
0000011e g       *ABS*	00000000 __TBIV
00007188 g     F .text	0000001a packetbuf_hdrreduce
00002e55 g     O .bss	00000001 serial_line_event_message
000001c0 g       *ABS*	00000000 __DAC12_0CTL
00000000 g       *ABS*	00000000 __far_data_load_start
000099ba g     F .text	000000e6 __floatunsisf
0000015e g       *ABS*	00000000 __ADC12MEM15
0000c31e g       *ABS*	00000000 __data_end_rom
00002088 g     O .data	00000064 percentage40
000071be g     F .text	0000000c packetbuf_dataptr
00000134 g       *ABS*	00000000 __MAC
00002336 g     O .bss	00000002 curr_log_level_coap
00000058 g       *ABS*	00000000 __BCSCTL2
0000132c g     O .data	00000064 isAnchor50Percent
00004202  w      .text	00000000 _endless_loop__
00000122 g       *ABS*	00000000 __DMACTL0
0000001f g       *ABS*	00000000 __P4SEL
00000196 g       *ABS*	00000000 __TBCCR2
000014bc g     O .data	00000064 isAnchor10Percent
00007ac6 g     F .text	0000001c serial_line_init
00000022 g       *ABS*	00000000 __P1DIR
00000146 g       *ABS*	00000000 __ADC12MEM3
00000076 g       *ABS*	00000000 __I2CDRB
000013f4 g     O .data	00000064 isAnchor30Percent
00000118 g       *ABS*	00000000 __I2COA
00008e34 g     F .text	00000042 __fixunssfsi
00000000         *UND*	00000000 _copy_data_init__
00009e28 g     F .text	000000a4 __fpcmp_parts_f
00004f48 g     F .text	0000001a clock_time
00002e18 g     O .bss	00000002 num_signal_received_anchors
00000164 g       *ABS*	00000000 __TACCTL1
0000007f g       *ABS*	00000000 __U1TXBUF
0000a944 g       .text	00000000 __muldi3
00007366 g     F .text	00000068 platform_init_stage_two
00002de8 g     O .bss	00000002 cc2420_sfd_end_time
00000000 g       *ABS*	00000000 __far_bss_size
00000055 g       *ABS*	00000000 __SVSCTL
00002e58 g       *ABS*	00000000 _stack
00004010  w      .text	00000000 __low_level_init
0000aeb0 g     O .rodata	00000004 anchory17
00007280 g     F .text	00000012 packetbuf_clear
00002e54 g     O .bss	00000001 sensors_event
000078c8 g     F .text	00000006 rtimer_init
00001100 g       .data	00000000 __data_start
0000018e g       *ABS*	00000000 __TBCCTL6
0000ab58 g     O .rodata	00000008 button_sensor
00006522 g     F .text	00000082 msp430_init_dco
00007eb0 g     F .text	00000012 watchdog_init
00000074 g       *ABS*	00000000 __I2CSCLH
000001ec g       *ABS*	00000000 __DMA1DA
00000120 g       *ABS*	00000000 __WDTCTL
0000420c g     F .text	00000016 autostart_start
00000083 g       *ABS*	00000000 __ADC12MCTL3
00000000 g       *ABS*	00000000 __IE1
0000624a g     F .text	00000034 list_remove
0000110c g     O .data	00000004 sensors
00002e4c g     O .bss	00000008 ds2411_id
00000059 g       *ABS*	00000000 __CACTL1
00000020 g       *ABS*	00000000 __P1IN
0000001c g       *ABS*	00000000 __P4IN
00007258 g     F .text	00000028 packetbuf_attr_clear
0000008b g       *ABS*	00000000 __ADC12MCTL11
0000935a g     F .text	0000004c __addsf3
00005684 g     F .text	00000120 ds2411_init
0000013e g       *ABS*	00000000 __SUMEXT
00002e1a g     O .bss	00000004 x_diff
00000031 g       *ABS*	00000000 __P5OUT
0000643e g     F .text	00000014 mac_call_sent_callback
000061de g     F .text	00000006 leds_init
00007354 g     F .text	00000012 platform_init_stage_one
