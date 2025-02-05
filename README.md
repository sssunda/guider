[![Build Status](https://travis-ci.org/iipeace/guider.svg?branch=master)](https://travis-ci.org/iipeace/guider) 
[![license](http://img.shields.io/badge/license-GNU-blue.svg)](https://raw.githubusercontent.com/iipeace/guider/master/LICENSE)
[![Coverity](https://scan.coverity.com/projects/15302/badge.svg)](https://scan.coverity.com/projects/iipeace-guider) 
[![PyPI version](https://badge.fury.io/py/guider.svg)](https://badge.fury.io/py/guider)
[![Join the chat at https://gitter.im/guiderchat/Lobby](https://badges.gitter.im/guiderchat/Lobby.svg)](https://gitter.im/guiderchat/Lobby?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge&utm_content=badge)

<pre><code>
   _____       _     _
  / ____|     (_)   | |
 | |  __ _   _ _  __| | ___ _ __
 | | |_ | | | | |/ _` |/ _ \ '__|
 | |__| | |_| | | (_| |  __/ |
  \_____|\__,_|_|\__,_|\___|_|
</code></pre>



Table of contents
=================
<!--ts-->
   * [Intro](#Intro)
   * [Output](#Output)
   * [How to use](#How-to-use)
   * [Requirement](#Requirement)
   * [Build & Installation](#Build-&-Installation)
   * [Kernel Configuration](#Kernel-Configuration)
   * [Help](#Help)
<!--te-->



Intro
=======
Do you struggle to improve system performance or to find root cause that makes system abnormal?   
Guider is made to measure the amount of system resource usage and to trace system behavior.   
You can analyze your performance issues effectively with this tool.   

Guider pursues characteristics as below.
1. Easy to use: just run without any setting and package installation
2. Measure correctly: count, time in from us, size in from byte
3. Provide all features: enough functions for experiment and analysis
4. Submit the report in detail: show as much information as possible

It usually supports all platforms based on the Linux kernel as shown below.
* Android
* distro (Ubuntu, CentOS, RHEL, Linux Mint, Arch Linux, ...)
* webOS
* ccOS
* Tizen
* Windows (only for drawing, reporting, networking)

The features of Guider are as follows.
![guider_mindmap](https://user-images.githubusercontent.com/15862689/46118768-27bb8c00-c243-11e8-8fae-a23c38d5bca3.png)

Output
=======
    $ ./guider.py top -a

    [Top Info] [Time: 71406.120] [Interval: 1.0] [Ctxt: 52687] [Life: +0/-0] [IRQ: 12517] [Core: 24] [Task: 326/433] [Load: 0.2/0.4/0.5] [RAM: 63876] [Swap: 65491]
               [Cycle: 2G / Inst: 6G / IPC: 2.45 / CacheMiss: 77K(6%) / BranchMiss: 857K(0%) / Clock: 22G / MinFlt: 4 / MajFlt: 0]
    ==========================================================================================================================================================
      ID   | CPU (Usr/Ker/Blk/IRQ)| Mem (Diff/ User/Cache/Kern)| Swap (Diff/  I/O  )|NrPgRclm | BlkRW | NrFlt | NrBlk | NrSIRQ | NrMlk | NrDrt  |  Network   |
      
    ----------------------------------------------------------------------------------------------------------------------------------------------------------
    Total  |  6 %( 4 / 0 / 0 / 0 )|11074(   0/  905/50751/1146)|  0   ( 0  /  0/0  )|   0/0   |  0/0  |   0   |   0   |  1658  |   0   |   7    |   1K/11K   |
    ----------------------------------------------------------------------------------------------------------------------------------------------------------
    Core/0 |  1 %( 0 / 0 / 0 / 0 )|                                                                   |   powersave   |  0-0   |   ? C | 1288 Mhz [1171-2441]|
    Core/1 |  1 %( 0 / 0 / 0 / 0 )|                                                                   |   powersave   |  0-1   |   ? C | 1530 Mhz [1171-2441]|
    Core/2 |  1 %( 0 / 0 / 0 / 0 )|                                                                   |   powersave   |  0-2   |   ? C | 1171 Mhz [1171-2441]|
    Core/3 |  1 %( 0 / 0 / 0 / 0 )|                                                                   |   powersave   |  0-3   |   ? C | 1173 Mhz [1171-2441]|
    Core/4 |  8 %( 1 / 2 / 0 / 0 )|#####                                                              |   powersave   |  0-4   |   ? C | 1171 Mhz [1171-2441]|
    Core/5 |  1 %( 0 / 0 / 0 / 0 )|                                                                   |   powersave   |  0-5   |   ? C | 1175 Mhz [1171-2441]|
    Core/6 |  1 %( 0 / 0 / 0 / 0 )|                                                                   |   powersave   |  1-0   |   ? C | 2330 Mhz [1171-2441]|
    Core/7 |  1 %( 0 / 0 / 0 / 0 )|                                                                   |   powersave   |  1-1   |   ? C | 2342 Mhz [1171-2441]|
    Core/8 |  1 %( 0 / 0 / 0 / 0 )|                                                                   |   powersave   |  1-2   |   ? C | 2367 Mhz [1171-2441]|
    Core/9 |  1 %( 0 / 0 / 0 / 0 )|                                                                   |   powersave   |  1-3   |   ? C | 2246 Mhz [1171-2441]|
    Core/10|100 %(99 / 0 / 0 / 0 )|###################################################################|   powersave   |  1-4   |   ? C | 2246 Mhz [1171-2441]|
    Core/11|  1 %( 0 / 0 / 0 / 0 )|                                                                   |   powersave   |  1-5   |   ? C | 2290 Mhz [1171-2441]|
    Core/12|  1 %( 0 / 0 / 0 / 0 )|                                                                   |   powersave   |  0-0   |   ? C | 1171 Mhz [1171-2441]|
    Core/13|  4 %( 3 / 0 / 0 / 0 )|##                                                                 |   powersave   |  0-1   |   ? C | 1953 Mhz [1171-2441]|
    Core/14|  1 %( 0 / 0 / 0 / 0 )|                                                                   |   powersave   |  0-2   |   ? C | 1952 Mhz [1171-2441]|
    Core/15|  1 %( 0 / 0 / 0 / 0 )|                                                                   |   powersave   |  0-3   |   ? C | 1171 Mhz [1171-2441]|
    Core/16| 12 %( 2 / 3 / 0 / 0 )|########                                                           |   powersave   |  0-4   |   ? C | 1953 Mhz [1171-2441]|
    Core/17|  1 %( 0 / 0 / 0 / 0 )|                                                                   |   powersave   |  0-5   |   ? C | 1846 Mhz [1171-2441]|
    Core/18|  1 %( 0 / 0 / 0 / 0 )|                                                                   |   powersave   |  1-0   |   ? C | 2278 Mhz [1171-2441]|
    Core/19|  1 %( 0 / 0 / 0 / 0 )|                                                                   |   powersave   |  1-1   |   ? C | 2243 Mhz [1171-2441]|
    Core/20|  1 %( 0 / 0 / 0 / 0 )|                                                                   |   powersave   |  1-2   |   ? C | 2247 Mhz [1171-2441]|
    Core/21|  1 %( 0 / 0 / 0 / 0 )|                                                                   |   powersave   |  1-3   |   ? C | 2246 Mhz [1171-2441]|
    Core/22|  1 %( 0 / 0 / 0 / 0 )|                                                                   |   powersave   |  1-4   |   ? C | 2440 Mhz [1171-2441]|
    Core/23|  1 %( 0 / 0 / 0 / 0 )|                                                                   |   powersave   |  1-5   |   ? C | 2393 Mhz [1171-2441]|
    ==========================================================================================================================================================
        Process      (  PID/ PPID/  Nr/ Pri)| CPU(Usr/Ker/Dly)|  Mem(RSS/Txt/Shr/Swp)| Blk( RD / WR /NrFlt)| Yld | Prmt | FD | LifeTime|     WaitChannel     |
    ----------------------------------------------------------------------------------------------------------------------------------------------------------
                 yes ( 2075/ 9085/   1/C  0)|  99( 99/  0/  0)|    8(  0/  0/  0/  0)|   0(   -/   -/    0)|    0|     0| 256|  0: 3:43|       RUNNING       |
               a.out ( 2082/ 9085/   3/C  0)|  16(  6/ 10/  -)|   30(  1/  0/  1/  0)|   0(   -/   -/    0)|    0|     0| 256|  0: 3:36| futex_wait_queue_me |
              guider ( 2182/ 9085/   1/C  0)|   3(  3/  0/  0)|  101( 62/  2/  5/  0)|   0(   -/   -/    0)|    1|     1|1024|  0: 0: 2|       RUNNING       |
                bash ( 6960/ 6959/   1/C  0)|   0(  0/  0/  -)|   24(  6/  0/  3/  0)|   0(   -/   -/    0)|    0|     0| 256| 20:26:27|       do_wait       |
                  vi ( 7200/ 7197/   1/C  0)|   0(  0/  0/  -)|   58(  8/  1/  5/  0)|   0(   -/   -/    0)|    0|     0|  64| 20:24:23|poll_schedule_timeout|
                bash ( 7916/ 6959/   1/C  0)|   0(  0/  0/  -)|   24(  6/  0/  3/  0)|   0(   -/   -/    0)|    0|     0| 256| 19:57:58|       do_wait       |
                nmbd ( 2960/    1/   1/C  0)|   0(  0/  0/  -)|   91(  4/  3/  4/  0)|   0(   -/   -/    0)|    0|     0|  64| 1K:20:52|poll_schedule_timeout|
               udevd ( 2222/    1/   1/C  0)|   0(  0/  0/  -)|   21(  2/  0/  1/  0)|   0(   -/   -/    0)|    0|     0|  64| 1K:20:53|       ep_poll       |
       kworker/14:1H ( 3288/    2/   1/C-20)|   0(  0/  0/  -)|    0(  0/  0/  0/  -)|   0(   -/   -/    0)|    0|     0|  64| 1K:20:51|    worker_thread    |
              bioset ( 1265/    2/   1/C-20)|   0(  0/  0/  -)|    0(  0/  0/  0/  -)|   0(   -/   -/    0)|    0|     0|  64| 1K:20:54|   rescuer_thread    |
       kworker/22:1H ( 1787/    2/   1/C-20)|   0(  0/  0/  -)|    0(  0/  0/  0/  -)|   0(   -/   -/    0)|    0|     0|  64| 1K:20:53|    worker_thread    |
     /usr/sbin/apach ( 7221/ 3817/   1/C  0)|   0(  0/  0/  -)|  250( 51/  0/ 12/  0)|   0(   -/   -/    0)|    0|     0|  64| 20:23:39|   inet_csk_accept   |
                sshd ( 1992/ 1977/   1/C  0)|   0(  0/  0/  0)|  131(  4/  0/  2/  0)|   0(   -/   -/    0)|    3|     1|  64|  0: 4:39|poll_schedule_timeout|
               netns (  130/    2/   1/C-20)|   0(  0/  0/  -)|    0(  0/  0/  0/  -)|   0(   -/   -/    0)|    0|     0|  64| 1K:20:54|   rescuer_thread    |
        kworker/20:2 ( 1962/    2/   1/C  0)|   0(  0/  0/  0)|    0(  0/  0/  0/  -)|   0(   -/   -/    0)|    1|     0|  64| 1K:20:53|    worker_thread    |
       kworker/13:1H ( 3286/    2/   1/C-20)|   0(  0/  0/  -)|    0(  0/  0/  0/  -)|   0(   -/   -/    0)|    0|     0|  64| 1K:20:51|    worker_thread    |
                bash ( 9085/ 9084/   1/C  0)|   0(  0/  0/  -)|   23(  5/  0/  3/  0)|   0(   -/   -/    0)|    0|     0| 256| 1K:47:24|       do_wait       |
     ext4-rsv-conver ( 2079/    2/   1/C-20)|   0(  0/  0/  -)|    0(  0/  0/  0/  -)|   0(   -/   -/    0)|    0|     0|  64| 1K:20:53|   rescuer_thread    |
       kworker/12:1H ( 3285/    2/   1/C-20)|   0(  0/  0/  -)|    0(  0/  0/  0/  -)|   0(   -/   -/    0)|    0|     0|  64| 1K:20:51|    worker_thread    |
    ---more---

>>>
           
    $ ./guider.py threadtop

	[Top Info] [Time: 194025.590] [Interval: 1.0] [Ctxt: 4995] [Life: +0/-0] [OOM: 0] [IRQ: 1879] [Core: 8] [Task: 333/1188] [Load: 3.1/1.9/0.9] [RAM: 62.8G]
	==========================================================================================================================================================
	  ID   |  CPU(Usr/Ker/Blk/IRQ)|  Avl(Diff/ User/Cache/Kern)|  Swap(Diff/ In/Out)| PgRclm  | BlkRW | NrFlt | PrBlk | NrSIRQ | PgMlk | PgDrt  |  Network   |
	----------------------------------------------------------------------------------------------------------------------------------------------------------
	Total  |  3 %( 1 / 0 /23 / 0 )|59874(  -3/ 3110/15153/ 355)|     0(   0/  0/  0)|   0/0   |  0/5  |   0   |   2   |  313   | 1607  | 939290 |    0/0     |
	==========================================================================================================================================================
			  Thread (  TID/  PID/  Nr/ Pri)| CPU(Usr/Ker/Dly)|  VSS(RSS/Txt/Shr/Swp)| Blk(  RD/  WR/NrFlt)| Yld | Prmt | FD | LifeTime|       Process       |
	----------------------------------------------------------------------------------------------------------------------------------------------------------
			  guider ( 8160/ 8160/   1/C  0)|   3(  2/  0/  0)|   66( 33/  2/  6/  0)|   0(   -/   -/    0)|    1|     0|2048| 00:00:02|         guider(8160)|
	 gnome-terminal- ( 4864/ 4864/   4/C  0)|   1(  0/  0/  -)|  627( 57/  0/ 40/  0)|   0(   -/   -/    0)|    -|     -| 128| 2d:05:52|gnome-terminal-(4864)|
				Xorg ( 1525/ 1525/   2/C  0)|   1(  0/  0/  -)|  431( 84/  0/ 48/  0)|   0(   -/   -/    0)|    -|     -| 128| 2d:05:53|           Xorg(1525)|
								   [ TOTAL ]|     5(   2/   0)|RSS: 174M / Swp:    0)| 0.0(   -/   -/    0)|      Yld: 1|       Prmt: 0|              Task: 3|
	----------------------------------------------------------------------------------------------------------------------------------------------------------
	[D]kworker/u16:0 ( 7784/ 7784/   1/C  0)|   0(  0/  0/  -)|    0(  0/  0/  -/  -)|   0(   -/   -/    0)|    -|     -|   -| 00:07:07|                    -|
			 [D]pool ( 8024/ 2450/  13/C  0)|   0(  0/  0/  -)| 1025( 82/  1/  -/  -)|   0(   -/   -/    0)|    -|     -|   -| 00:04:31|                    -|
	  [D]usb-storage ( 7825/ 7825/   1/C  0)|   0(  0/  0/  -)|    0(  0/  0/  -/  -)|   0(   -/   -/    0)|    -|     -|   -| 00:06:38|                    -|
	----------------------------------------------------------------------------------------------------------------------------------------------------------

>>>

    # ./guider.py usertop -g yes -H

	[Top Usercall Info] [Time: 69810.230000] [Interval: 1.000658] [NrSamples: 955] [NrSymbols: 9] [CPU: 26.0%(Usr:24.0%/Sys:2.0%)] [SampleTime: 0.0001]
	==========================================================================================================================================================
	 Usage  |                                                                 Function [Path]
	==========================================================================================================================================================
	  33.3% | _IO_file_xsputn@GLIBC_2.17 [/lib/libc-2.24.so]
			   100.0% |  <- fputs_unlocked@GLIBC_2.17[/lib/libc-2.24.so] <- ??[/usr/bin/yes.coreutils] <- __libc_start_main@GLIBC_2.17[/lib/libc-2.24.so] <- ??[/usr/bin/yes.coreutils]
	  16.9% | __libc_start_main@GLIBC_2.17 [/lib/libc-2.24.so]
			   100.0% |  <- ??[/usr/bin/yes.coreutils]
	  16.3% | fputs_unlocked@GLIBC_2.17 [/lib/libc-2.24.so]
			   100.0% |  <- ??[/usr/bin/yes.coreutils] <- __libc_start_main@GLIBC_2.17[/lib/libc-2.24.so] <- ??[/usr/bin/yes.coreutils]
	  12.6% | memcpy@GLIBC_2.17 [/lib/libc-2.24.so]
			   100.0% |  <- _IO_file_xsputn@GLIBC_2.17[/lib/libc-2.24.so] <- fputs_unlocked@GLIBC_2.17[/lib/libc-2.24.so] <- ??[/usr/bin/yes.coreutils] <- __libc_start_main@GLIBC_2.17[/lib/libc-2.24.so] <- ?
	  11.4% | strlen@GLIBC_2.17 [/lib/libc-2.24.so]
			   100.0% |  <- fputs_unlocked@GLIBC_2.17[/lib/libc-2.24.so] <- ??[/usr/bin/yes.coreutils] <- __libc_start_main@GLIBC_2.17[/lib/libc-2.24.so] <- ??[/usr/bin/yes.coreutils]
	   4.6% | _IO_file_write@GLIBC_2.17 [/lib/libc-2.24.so]
			   100.0% |  <- ??[/lib/libc-2.24.so] <- _IO_do_write@GLIBC_2.17[/lib/libc-2.24.so] <- _IO_file_xsputn@GLIBC_2.17[/lib/libc-2.24.so] <- fputs_unlocked@GLIBC_2.17[/lib/libc-2.24.so] <- ??[/usr/bin
	   2.5% | ?? [/usr/bin/yes.coreutils]
	   1.8% | PLT [/usr/bin/yes.coreutils]
			   100.0% |  <- ??[/usr/bin/yes.coreutils] <- __libc_start_main@GLIBC_2.17[/lib/libc-2.24.so] <- ??[/usr/bin/yes.coreutils]
	----------------------------------------------------------------------------------------------------------------------------------------------------------

>>>

	# ./guider.py systop -g yes -H

    [Top Syscall Info] [Time: 69913.860000] [Interval: 1.000497] [NrSamples: 454] [NrSymbols: 1] [CPU: 5.0%(Usr:4.0%/Sys:1.0%)]
	==========================================================================================================================================================
	 Usage  |                                                                 Function [Count]
	==========================================================================================================================================================
	 100.0% | write [Cnt: 454, Err: 0]
			   100.0% |  <- _IO_file_write@GLIBC_2.17[/lib/libc-2.24.so] <- ??[/lib/libc-2.24.so] <- _IO_do_write@GLIBC_2.17[/lib/libc-2.24.so] <- _IO_file_xsputn@GLIBC_2.17[/lib/libc-2.24.so] <- fputs_unloc
	----------------------------------------------------------------------------------------------------------------------------------------------------------

>>>
           
    # ./guider.py filetop -g init

    [Top File Info] [Time: 7176036.720] [Proc: 322] [FD: 1323] [File: 400] (Unit: %/MB/NR)
    ==========================================================================================================================================================
          PROC       ( ID  / Pid / Nr / Pri)| FD |                                                   PATH                                                    |
    ----------------------------------------------------------------------------------------------------------------------------------------------------------
                init (    1/    0/   1/C  0)|  12|  SOCKET: 4   DEVICE: 3   PIPE: 2   EVENT: 2   NORMAL: 1   PROC: 0                                         |
                                            |  11|  /var/log/upstart/mysql.log.1 (deleted)                                                                   |
                                            |  10|  socket:[13414] (@/com/ubuntu/upstart)                                                                    |
                                            |   9|  socket:[23593] (@/com/ubuntu/upstart)                                                                    |
                                            |   8|  socket:[6241]                                                                                            |
                                            |   7|  socket:[3098] (@/com/ubuntu/upstart)                                                                     |
                                            |   6|  anon_inode:inotify                                                                                       |
                                            |   5|  anon_inode:inotify                                                                                       |
                                            |   4|  pipe:[3097]                                                                                              |
                                            |   3|  pipe:[3097]                                                                                              |
                                            |   2|  /dev/null                                                                                                |
                                            |   1|  /dev/null                                                                                                |
                                            |   0|  /dev/null                                                                                                |
    ----------------------------------------------------------------------------------------------------------------------------------------------------------

>>>
           
    # ./guider.py stacktop -g syslog

    [Top Info] [Time: 7176163.830] [Interval: 1.0] [Ctxt: 2914] [Life: +13/-12] [IRQ: 5103] [Core: 24] [Task: 328/435] [RAM: 63876] [Swap: 65491] (Unit: %/MB/NR)
               [Cycle: 2G / Inst: 3G / IPC: 1.34 / CacheMiss: 6M(34%) / BranchMiss: 4M(0%) / Clock: 23G / MinFlt: 53,257 / MajFlt: 0]
    ==========================================================================================================================================================
      ID   | CPU (Usr/Ker/Blk/IRQ)| Mem (Diff/ User/Cache/Kern)| Swap (Diff/  I/O  )|NrPgRclm | BlkRW | NrFlt | NrBlk | NrSIRQ | NrMlk | NrDrt  |  Network   |
    ----------------------------------------------------------------------------------------------------------------------------------------------------------
    Total  |  6 %( 3 / 1 / 0 / 0 )| 4913(-204/  974/56824/1165)|  0   ( 0  /  0/0  )|   0/0   | 0/42  |   0   |   0   |  3713  |   0   | 90901  |   2K/13K   |
    ==========================================================================================================================================================
         Thread      (  TID/  PID/  Nr/ Pri)| CPU(Usr/Ker/Dly)|  Mem(RSS/Txt/Shr/Swp)| Blk( RD / WR /NrFlt)| Yld | Prmt | FD | LifeTime|     WaitChannel     |
    ----------------------------------------------------------------------------------------------------------------------------------------------------------
            rsyslogd ( 2702/ 2702/   4/C  0)|   0(  0/  0/  -)|  244(  5/  0/  2/  0)|   0(   -/   -/    0)|    0|     0|  64| 1K:22:40|poll_schedule_timeout|
                                       100% | poll_schedule_timeout+0x43/0x70 <- do_select+0x711/0x7f0 <- core_sys_select+0x196/0x280 <-
                                              SyS_select+0xa6/0xe0 <- entry_SYSCALL_64_fastpath+0x1a/0xa5
    ----------------------------------------------------------------------------------------------------------------------------------------------------------
            rsyslogd ( 2779/ 2702/   4/C  0)|   0(  0/  0/  -)|  244(  5/  0/  2/  0)|   0(   -/   -/    0)|    0|     0|  64| 1K:22:40|poll_schedule_timeout|
                                       100% | poll_schedule_timeout+0x43/0x70 <- do_select+0x711/0x7f0 <- core_sys_select+0x196/0x280 <-
                                              SyS_select+0xa6/0xe0 <- entry_SYSCALL_64_fastpath+0x1a/0xa5
    ----------------------------------------------------------------------------------------------------------------------------------------------------------
            rsyslogd ( 2780/ 2702/   4/C  0)|   0(  0/  0/  0)|  244(  5/  0/  2/  0)|   0(   -/   -/    0)|  116|     0|  64| 1K:22:40|      do_syslog      |
                                        99% | do_syslog+0x446/0x4c0 <- kmsg_read+0x3f/0x50 <- proc_reg_read+0x3d/0x60 <- __vfs_read+0x23/0x110 <-
                                              vfs_read+0x91/0x130 <- SyS_read+0x41/0xa0 <- entry_SYSCALL_64_fastpath+0x1a/0xa5
    ----------------------------------------------------------------------------------------------------------------------------------------------------------

>>>
           
    # ./guider.py perftop -g yes

    [Top Info] [Time: 7181955.420] [Interval: 1.0] [Ctxt: 121] [Life: +0/-0] [IRQ: 1947] [Core: 24] [Task: 317/424] [RAM: 63876] [Swap: 65491] (Unit: %/MB/NR)
    ==========================================================================================================================================================
      ID   | CPU (Usr/Ker/Blk/IRQ)| Mem (Diff/ User/Cache/Kern)| Swap (Diff/  I/O  )|NrPgRclm | BlkRW | NrFlt | NrBlk | NrSIRQ | NrMlk | NrDrt  |  Network   |
    ----------------------------------------------------------------------------------------------------------------------------------------------------------
    Total  |  5 %( 4 / 0 / 0 / 0 )| 3783(   0/  875/58078/1140)|  0   ( 0  /  0/0  )|   0/0   |  0/0  |   0   |   0   |  2023  |   0   |   0    |   1K/3K    |
    ==========================================================================================================================================================
        Process      (  PID/ PPID/  Nr/ Pri)| CPU(Usr/Ker/Dly)|  Mem(RSS/Txt/Shr/Swp)| Blk( RD / WR /NrFlt)| Yld | Prmt | FD | LifeTime|     WaitChannel     |
    ----------------------------------------------------------------------------------------------------------------------------------------------------------
                 yes (22371/ 9085/   1/R 90)|  99( 99/  0/  0)|    8(  0/  0/  0/  0)|   0(   -/   -/    0)|    0|     0| 256|  1:34:11|       RUNNING       |
                                            | [Cycle: 2G / Inst: 6G / IPC: 2.82 / CacheMiss: 11K(98%) / BranchMiss: 26K(0%) / Clock: 972M / MinFlt: 0 / MajFlt: 0]
    ----------------------------------------------------------------------------------------------------------------------------------------------------------

>>>
           
    # ./guider.py memtop

    [Top Info] [Time: 7176233.650] [Interval: 1.0] [Ctxt: 289] [Life: +2/-2] [IRQ: 1397] [Core: 24] [Task: 323/430] [RAM: 63876] [Swap: 65491] (Unit: %/MB/NR)
               [Cycle: 127M / Inst: 121M / IPC: 0.95 / CacheMiss: 280K(23%) / BranchMiss: 437K(1%) / Clock: 22G / MinFlt: 714 / MajFlt: 0]
    ==========================================================================================================================================================
      ID   | CPU (Usr/Ker/Blk/IRQ)| Mem (Diff/ User/Cache/Kern)| Swap (Diff/  I/O  )|NrPgRclm | BlkRW | NrFlt | NrBlk | NrSIRQ | NrMlk | NrDrt  |  Network   |
    ----------------------------------------------------------------------------------------------------------------------------------------------------------
    Total  |  1 %( 0 / 0 / 0 / 0 )| 4706(   1/  865/57151/1154)|  0   ( 0  /  0/0  )|   0/0   |  0/0  |   0   |   0   |  484   |   0   |   35   |   1K/4K    |
    ==========================================================================================================================================================
        Process      (  PID/ PPID/  Nr/ Pri)| CPU(Usr/Ker/Dly)|  Mem(RSS/Txt/Shr/Swp)| Blk( RD / WR /NrFlt)| Yld | Prmt | FD | LifeTime|     WaitChannel     |
    ----------------------------------------------------------------------------------------------------------------------------------------------------------
              guider (22307/ 9085/   1/C  0)|   2(  2/  0/  0)|  101( 62/  2/  5/  0)|   0(   -/   -/    0)|    1|     0|1024|  0: 0: 5|       RUNNING       |
                                 (1)[STACK] | SIZE:   0M / RSS:   0M / PSS:   0M / SWAP:   0M / HUGE:  0M / LOCK:   0K / SDRT:   0K / PDRT: 140K / NOPM:   0K|
                                   (1)[SHM] | SIZE:   0M / RSS:   0M / PSS:   0M / SWAP:   0M / HUGE:  0M / LOCK:   0K / SDRT:   0K / PDRT:   0K / NOPM:   0K|
                                 (19)[FILE] | SIZE:  44M / RSS:   6M / PSS:   2M / SWAP:   0M / HUGE:  0M / LOCK:   0K / SDRT:   0K / PDRT: 632K / NOPM:  31M|
                                   (3)[ETC] | SIZE:   0M / RSS:   0M / PSS:   0M / SWAP:   0M / HUGE:  0M / LOCK:   0K / SDRT:   0K / PDRT:   0K / NOPM:   0K|
                                 (12)[ANON] | SIZE:  56M / RSS:  56M / PSS:  56M / SWAP:   0M / HUGE:  0M / LOCK:   0K / SDRT:   0K / PDRT:  56M / NOPM:   0K|
    ----------------------------------------------------------------------------------------------------------------------------------------------------------

>>>
           
    # ./guider.py nettop

	[Top Info] [Time: 186473.960] [Interval: 1.0] [Ctxt: 7865] [Life: +0/-0] [OOM: 0] [IRQ: 4229] [Core: 8] [Task: 328/1171] [Load: 0.5/0.3/0.3] [RAM: 62.8G]
	==========================================================================================================================================================
	  ID   |  CPU(Usr/Ker/Blk/IRQ)|  Avl(Diff/ User/Cache/Kern)|  Swap(Diff/ In/Out)| PgRclm  | BlkRW | NrFlt | PrBlk | NrSIRQ | PgMlk | PgDrt  |  Network   |
	----------------------------------------------------------------------------------------------------------------------------------------------------------
	Total  |  1 %( 0 / 0 / 0 / 0 )|59939(  -2/ 3054/ 6429/ 350)|     0(   0/  0/  0)|   0/0   |  0/0  |   0   |   0   |  1661  | 1607  |  343   |  652K/9K   |
	==========================================================================================================================================================
					Network                  |                        Receive                        |                       Transfer                        |
	----------------------------------------------------------------------------------------------------------------------------------------------------------
		  Dev        |          IP           |   Size   |  Packet  |  Error   |   Drop   | Multicast |   Size   |  Packet  |  Error   |   Drop   | Multicast |
	==========================================================================================================================================================
			 docker0 |                       |        0 |        0 |        0 |        0 |         0 |        0 |        0 |        0 |        0 |         0 |
				eno1 |                       |   665.9K |      475 |        0 |        0 |         1 |    12.0K |      168 |        0 |        0 |         0 |
	 enx201601190a25 |                       |       48 |        1 |        0 |        0 |         0 |        0 |        0 |        0 |        0 |         0 |
				  lo |                       |        0 |        0 |        0 |        0 |         0 |        0 |        0 |        0 |        0 |         0 |
			  virbr0 |                       |        0 |        0 |        0 |        0 |         0 |        0 |        0 |        0 |        0 |         0 |
		  virbr0-nic |                       |        0 |        0 |        0 |        0 |         0 |        0 |        0 |        0 |        0 |         0 |
		   [ TOTAL ] |                       |   666.0K |      476 |        0 |        0 |         1 |    12.0K |      168 |        0 |        0 |         0 |
	==========================================================================================================================================================

>>>

	# ./guider.py disktop

	[Top Info] [Time: 186512.750] [Interval: 1.0] [Ctxt: 11963] [Life: +1/-0] [OOM: 0] [IRQ: 6263] [Core: 8] [Task: 329/1176] [Load: 0.4/0.3/0.3] [RAM: 62.8G]
	==========================================================================================================================================================
	  ID   |  CPU(Usr/Ker/Blk/IRQ)|  Avl(Diff/ User/Cache/Kern)|  Swap(Diff/ In/Out)| PgRclm  | BlkRW | NrFlt | PrBlk | NrSIRQ | PgMlk | PgDrt  |  Network   |
	----------------------------------------------------------------------------------------------------------------------------------------------------------
	Total  |  3 %( 1 / 0 / 0 / 0 )|59938(   0/ 3054/ 6469/ 351)|     0(   0/  0/  0)|   0/0   |  0/0  |   0   |   0   |  1997  | 1607  |  2534  |  618K/9K   |
	==========================================================================================================================================================
			  DEV           |BUSY| AVQ | READ  | WRITE |   FREE(   DIFF)|USAGE| TOTAL |  AVF  |   FS   |                 MountPoint <Option>                 |
	----------------------------------------------------------------------------------------------------------------------------------------------------------
	/dev/sda1               |  0%| 12.0|      0|      0|  43.4G(  -1.0M)|  74%| 171.7G|  10.0M|  ext4  | /var/lib/docker/overlay2                            |
	/dev/sdb                |  0%|    0|      0|      0| 291.1G(      0)|  68%| 916.8G|  51.0M|  ext4  | /media/iipeace/445219df-443d-42a9-bf2b-1c94bbdfcb6a |
	/dev/loop3              |  0%|    0|      0|      0|      0(      0)| 100%|  88.0M|      0|squashfs| /snap/core/7270 <ro,nodev,relatime>                 |
	/dev/loop1              |  0%|    0|      0|      0|      0(      0)| 100%|  88.0M|      0|squashfs| /snap/core/7169 <ro,nodev,relatime>                 |
	/dev/loop2              |  0%|    0|      0|      0|      0(      0)| 100%| 144.0M|      0|squashfs| /snap/notepadqq/841 <ro,nodev,relatime>             |
	/dev/loop0              |  0%|    0|      0|      0|      0(      0)| 100%| 145.0M|      0|squashfs| /snap/notepadqq/855 <ro,nodev,relatime>             |
	==========================================================================================================================================================

>>>

    # ./guider.py wsstop -g yes

    [Top Info] [Time: 7176629.490] [Interval: 1.0] [Ctxt: 195] [Life: +0/-0] [IRQ: 2688] [Core: 24] [Task: 327/434] [RAM: 63876] [Swap: 65491] (Unit: %/MB/NR)
               [Cycle: 2G / Inst: 6G / IPC: 2.75 / CacheMiss: 202K(19%) / BranchMiss: 325K(0%) / Clock: 23G / MinFlt: 4 / MajFlt: 0]
    ==========================================================================================================================================================
      ID   | CPU (Usr/Ker/Blk/IRQ)| Mem (Diff/ User/Cache/Kern)| Swap (Diff/  I/O  )|NrPgRclm | BlkRW | NrFlt | NrBlk | NrSIRQ | NrMlk | NrDrt  |  Network   |
    ----------------------------------------------------------------------------------------------------------------------------------------------------------
    Total  |  5 %( 4 / 0 / 0 / 0 )| 4719(   0/  856/57152/1149)|  0   ( 0  /  0/0  )|   0/0   |  0/0  |   0   |   0   |  2410  |   0   |   2    |   1K/5K    |
    ==========================================================================================================================================================
        Process      (  PID/ PPID/  Nr/ Pri)| CPU(Usr/Ker/Dly)|  Mem(RSS/Txt/Shr/Swp)| Blk( RD / WR /NrFlt)| Yld | Prmt | FD | LifeTime|     WaitChannel     |
    ----------------------------------------------------------------------------------------------------------------------------------------------------------
                 yes (22371/ 9085/   1/R 90)|  99( 99/  0/  0)|    8(  0/  0/  0/  0)|   0(   -/   -/    0)|    0|     0| 256|  0: 5:25|       RUNNING       |
                                 (1)[STACK] | SIZE:   0M / RSS:   0M / PSS:   0M / SWAP:   0M / HUGE:  0M / LOCK:   0K / SDRT:   0K / PDRT:   8K / NOPM:   0K|
                                            |  WSS: [   8K] ->    4K ->    4K ->    4K ->    4K ->    4K ->    4K ->    4K ->    4K ->    4K ->    4K ->    4K
                                  (4)[FILE] | SIZE:   7M / RSS:   1M / PSS:   0M / SWAP:   0M / HUGE:  0M / LOCK:   0K / SDRT:   0K / PDRT:  40K / NOPM:2048K|
                                            |  WSS: [   1M] ->    1M ->    1M ->    1M ->    1M ->    1M ->    1M ->    1M ->    1M ->    1M ->    1M ->    1M
                                   (3)[ETC] | SIZE:   0M / RSS:   0M / PSS:   0M / SWAP:   0M / HUGE:  0M / LOCK:   0K / SDRT:   0K / PDRT:   0K / NOPM:   0K|
                                            |  WSS: [   4K] ->    4K ->    4K ->    4K ->    4K ->     0 ->     0 ->     0 ->     0 ->     0 ->    4K ->    4K
                                  (5)[ANON] | SIZE:   0M / RSS:   0M / PSS:   0M / SWAP:   0M / HUGE:  0M / LOCK:   0K / SDRT:   0K / PDRT:  48K / NOPM:   0K|
                                            |  WSS: [  48K] ->    4K ->    4K ->    4K ->    4K ->    4K ->    4K ->    4K ->    4K ->    4K ->    4K ->    4K
    ----------------------------------------------------------------------------------------------------------------------------------------------------------

>>>
           
    $ ./guider.py reptop
    $ cat /tmp/guider.report

    {
      "task": {
        "nrThread": 397,
        "nrBlocked": 0,
        "nrCtx": 4290,
        "nrProc": 292
      },
      "mem": {
        "kernel": 1432,
        "anonDiff": -1,
        "pgRclmFg": 0,
        "cache": 35332,
        "slabDiff": 0,
        "free": 26929,
        "anon": 698,
        "pgDirty": 28,
        "file": 31751,
        "freeDiff": -1,
        "pgRclmBg": 0,
        "total": 64391,
        "slab": 3581,
        "fileDiff": -1
        "procs": {
          "1954": {
            "text": 0,
            "pid": 1954,
            "rank": 2,
            "comm": "ruby1.9.1",
            "runtime": "110:43:32",
            "rss": 104
          },
      },
      "storage": {
        "total": {
          "read": 0,
          "mount": {},
          "favail": 133443655,
          "free": 1141633,
          "write": 1,
          "usage": 1152423,
          "total": 2294056,
          "usageper": 50
        },
        "/dev/sdb1": {
          "read": 0,
          "mount": {
            "path": "/mnt/hdd1",
            "fs": "ext4",
            "option": "rw,relatime,data=ordered"
          },
          "favail": 50709466,
          "free": 293649,
          "write": 0,
          "usage": 645251,
          "total": 938900,
          "usageper": 68
        },
      },
      "system": {
        "load5m": 2.38,
        "uptime": 4191643.92,
        "nrSoftIrq": 7405,
        "nrIrq": 7289,
        "load15m": 0.84,
        "interval": 1.029999999795109,
        "pid": 14578,
        "load1m": 9.39
      },
      "event": {
        "CPU_INTENSIVE": {
          "14592": {
            "kernel": 0,
            "runtime": "0:0:47",
            "pid": 14592,
            "rank": 3,
            "comm": "yes",
            "user": 99,
            "total": 100
          },
          "14593": {
            "kernel": 0,
            "runtime": "0:0:46",
            "pid": 14593,
            "rank": 10,
            "comm": "yes",
            "user": 99,
            "total": 100
          },
      },
      "swap": {
        "usage": 76,
        "total": 65491,
        "usageDiff": 0
      },
      "net": {
        "inbound": 1479,
        "outbound": 392
      },
      "cpu": {
        "kernel": 0,
        "iowait": 0,
        "nrCore": 24,
        "idle": 8,
        "user": 91,
        "irq": 0,
        "total": 92,
        "procs": {
          "14592": {
            "kernel": 0,
            "runtime": "0:0:47",
            "pid": 14592,
            "rank": 3,
            "comm": "yes",
            "user": 99,
            "total": 100
          },
      },
      "block": {
        "read": 0,
        "write": 0,
        "procs": {},
        "nrMajFlt": 0,
        "ioWait": 0
      }
    }

>>>

    # ./guider.py cpulimit -g 22371:50


                _      _
       __ _  _   _ (_)  __| |  ___  _ __
      / _` || | | || | / _` | / _ \| '__|
     | (_| || |_| || || (_| ||  __/| |
      \__, | \__,_||_| \__,_| \___||_|
       |___/


    [Info] priority of 22376 task is changed to -20(C)

    [Info] limited cpu usage of yes(22371) process to 50%, it used 50%

    [Info] limited cpu usage of yes(22371) process to 50%, it used 50%

    [Info] limited cpu usage of yes(22371) process to 50%, it used 50%

    [Info] limited cpu usage of yes(22371) process to 50%, it used 50%

>>>
           
    # ./guider.py setsched r:90:22371


                    _      _
       __ _  _   _ (_)  __| |  ___  _ __
      / _` || | | || | / _` | / _ \| '__|
     | (_| || |_| || || (_| ||  __/| |
      \__, | \__,_||_| \__,_| \___||_|
       |___/


    [Info] priority of 22371 task is changed to 90(R)

>>>
           
    # ./guider.py kill -stop 10594


                    _      _
       __ _  _   _ (_)  __| |  ___  _ __
      / _` || | | || | / _` | / _ \| '__|
     | (_| || |_| || || (_| ||  __/| |
      \__, | \__,_||_| \__,_| \___||_| 
       |___/


    [Info] sent signal SIGSTOP to 10594 process

>>>
           
    # ./guider.py rec -a -e m,b

    [Thread Info] [ Elapsed: 2.050 ] [ Start: 2849868.198 ] [ Running: 112 ] [ CtxSwc: 3357 ] [ LogSize: 4054 KB ] [ Unit: Sec/MB/NR ]
    ==========================================================================================================================================================
    __________Thread Info___________|_____________CPU Info______________|______SCHED Info______|________BLOCK Info________|_____________MEM Info_____________|
                                    |                                   |                      |                          |                                  |
                Name(  Tid/  Pid)|LF|Usage(    %)|Delay(  Max)|Pri| IRQ |  Yld| Lose|Steal| Mig| Read( MB/  Cnt)|WCnt( MB)| Sum(Usr/Buf/Ker)|Rcl|Wst|DRcl(Nr)|
    ==========================================================================================================================================================
    # CPU: 12
 
              CORE/0(-----/-----)|--| 0.00(  0.1)| 0.00( 0.00)|  0| 0.00|    7|    -|    -|   -| 0.00(  0/    1)|   0(  0)|   0(  0/  0/  0)|  0|  0|0.00( 0)|
              CORE/1(-----/-----)|--| 0.00(  0.1)| 0.10( 0.00)|  0| 0.00|  147|    -|    -|   -| 0.00(  0/    0)|   0(  0)|   0(  0/  0/  0)|  0|  0|0.00( 0)|
              CORE/2(-----/-----)|--| 0.00(  0.1)| 0.16( 0.00)|  0| 0.00|  211|    -|    -|   -| 0.00(  0/    0)|   0(  0)|   0(  0/  0/  0)|  0|  0|0.00( 0)|
              CORE/3(-----/-----)|--| 0.00(  0.1)| 0.11( 0.00)|  0| 0.00|  181|    -|    -|   -| 0.00(  0/    0)|  32(  0)|   0(  0/  0/  0)|  0|  0|0.00( 0)|
              CORE/4(-----/-----)|--| 0.00(  0.1)| 0.11( 0.00)|  0| 0.00|  232|    -|    -|   -| 0.00(  0/    0)|   0(  0)|   0(  0/  0/  0)|  0|  0|0.00( 0)|
              CORE/5(-----/-----)|--| 0.30( 14.8)| 0.18( 0.00)|  0| 0.00|  179|    -|    -|   -| 1.26(  6/  495)|  19(  0)|  61( 57/  0/  3)|  0|  0|0.00( 0)|
              CORE/6(-----/-----)|--| 0.00(  0.0)| 0.35( 0.00)|  0| 0.00|   57|    -|    -|   -| 0.00(  0/    0)|   0(  0)|   0(  0/  0/  0)|  0|  0|0.00( 0)|
              CORE/7(-----/-----)|--| 0.00(  0.0)| 0.60( 0.00)|  0| 0.00|  100|    -|    -|   -| 0.00(  0/    0)|   0(  0)|   0(  0/  0/  0)|  0|  0|0.00( 0)|
              CORE/8(-----/-----)|--| 0.00(  0.0)| 0.44( 0.00)|  0| 0.00|   59|    -|    -|   -| 0.00(  0/    0)|   0(  0)|   0(  0/  0/  0)|  0|  0|0.00( 0)|
              CORE/9(-----/-----)|--| 0.00(  0.0)| 1.94( 0.00)|  0| 0.00|   37|    -|    -|   -| 0.00(  0/    0)|   0(  0)|   0(  0/  0/  0)|  0|  0|0.00( 0)|
             CORE/10(-----/-----)|--| 0.07(  3.4)| 0.00( 0.00)|  0| 0.00|    2|    -|    -|   -| 0.00(  0/    0)|   0(  0)|   0(  0/  0/  0)|  0|  0|0.00( 0)|
             CORE/11(-----/-----)|--| 0.00(  0.0)| 2.05( 0.00)|  0| 0.00|   39|    -|    -|   -| 0.00(  0/    0)|   0(  0)|   0(  0/  0/  0)|  0|  0|0.00( 0)|
 
    ----------------------------------------------------------------------------------------------------------------------------------------------------------
    # Hot: 4
 
            synergyc( 3604/ 3602)|  | 0.17(  8.5)| 0.00( 0.00)|  0| 0.00|    3|   14|    3|   0| 0.00(  0/    0)|   0(  0)|   0(  0/  0/  0)|  0|  0|0.00( 0)|
     arm-starfish-li(16087/16087)|  | 0.13(  6.3)| 0.00( 0.00)|  0| 0.00|    0|   20|  157|   4| 1.26(  6/  496)|   0(  0)|  61( 57/  0/  3)|  0|  0|0.00( 0)|
              guider(16088/16088)|  | 0.07(  3.4)| 0.00( 0.00)|R90| 0.00|    2|    0|    2|   0| 0.00(  0/    0)|   0(  0)|   0(  0/  0/  0)|  0|  0|0.00( 0)|
 
    ----------------------------------------------------------------------------------------------------------------------------------------------------------
       
>>>
       
    # ./guider.py sysrec 

    [Thread Syscall Info] (Unit: Sec/NR)
    ==========================================================================================================================================================
                Name(  Tid)                        Syscall( ID)      Elapsed        Count        Error          Min          Max          Avg
    ==========================================================================================================================================================
     arm-linux-gnuea( 3000)
                                                     close(  3)     0.039396           69            0     0.000001     0.005353     0.000571
                                                      stat(  4)     0.011521           74            0     0.000001     0.009423     0.000156
                                                    fchmod( 91)     0.000046            3            0     0.000002     0.000039     0.000015
                                               getpriority(140)     0.000017           33            0     0.000000     0.000001     0.000001
                                                 lgetxattr(192)     0.000014            3            0     0.000003     0.000008     0.000005
                                                  recvfrom( 45)     0.000004            1            0     0.000004     0.000004     0.000004

    ----------------------------------------------------------------------------------------------------------------------------------------------------------
              guider( 3001)
                                                     pause( 34)     0.283474            1            1     0.283474     0.283474     0.283474
                                                    select( 23)     0.100122            1            0     0.100122     0.100122     0.100122
                                                     write(  1)     0.000234            6            0     0.000031     0.000059     0.000039
                                                      open(  2)     0.000084            7            0     0.000007     0.000038     0.000012
                                                     ioctl( 16)     0.000009           14           14     0.000001     0.000001     0.000001
                                                     fstat(  5)     0.000006           14            0     0.000001     0.000001     0.000000
                                                     lseek(  8)     0.000006           21            0     0.000000     0.000001     0.000000
                                                     close(  3)     0.000005            7            0     0.000000     0.000001     0.000001
                                              rt_sigaction( 13)     0.000001            1            0     0.000001     0.000001     0.000001

    ----------------------------------------------------------------------------------------------------------------------------------------------------------
              mysqld( 3237)
                                                     futex(202)     0.000000            1            0     0.000000     0.000000     0.000000

    ----------------------------------------------------------------------------------------------------------------------------------------------------------
              mysqld( 3238)
                                                     futex(202)     0.000002            1            0     0.000002     0.000002     0.000002

    ----------------------------------------------------------------------------------------------------------------------------------------------------------
              screen( 9045)
                                                    select( 23)     0.000082            4            0     0.000004     0.000069     0.000021
    ----------------------------------------------------------------------------------------------------------------------------------------------------------
       
>>>
       
    # ./guider.py rec -e b

    [Thread Block Info] (Unit: KB/NR)
    ==========================================================================================================================================================
              ID              OPT    NrDev            TOTAL       SEQUENTIAL(    %)      FS              PATH
                                                   [ACCESS]                   COUNT
    ==========================================================================================================================================================
             TOTAL           READ     8:33          170,624          158,356( 92.8)     ext4          /dev/sdc1
                                            [   4K -    7K]                   2,024
                                            [   8K -   15K]                      21
                                            [  16K -   31K]                      43
                                            [  32K -   63K]                      44
                                            [  64K -  127K]                     155
                                            [ 128K -  255K]                     112
                                            [ 256K -  511K]                     510
                                            [ 512K - 1023K]                       2

                            WRITE     8:33                8                4( 50.0)     ext4          /dev/sdc1
                                            [   4K -    7K]                       2
    ----------------------------------------------------------------------------------------------------------------------------------------------------------
                 cron(3115)  READ     8:33              644              576( 89.4)     ext4          /dev/sdc1
                                            [   4K -    7K]                     161
    ----------------------------------------------------------------------------------------------------------------------------------------------------------
                 cat(10392)  READ     8:33              604              404( 66.9)     ext4          /dev/sdc1
                                            [   4K -    7K]                     110
                                            [  16K -   31K]                       1
                                            [  32K -   63K]                       1
                                            [  64K -  127K]                       1
    ----------------------------------------------------------------------------------------------------------------------------------------------------------
                 bash(9085)  READ     8:33               28                4( 14.3)     ext4          /dev/sdc1
                                            [   4K -    7K]                       7
    ----------------------------------------------------------------------------------------------------------------------------------------------------------
                 cat(10395)  READ     8:33          169,348          157,384( 92.9)     ext4          /dev/sdc1
                                            [   4K -    7K]                   1,746
                                            [   8K -   15K]                      21
                                            [  16K -   31K]                      42
                                            [  32K -   63K]                      43
                                            [  64K -  127K]                     154
                                            [ 128K -  255K]                     112
                                            [ 256K -  511K]                     510
                                            [ 512K - 1023K]                       2
    ----------------------------------------------------------------------------------------------------------------------------------------------------------
       kworker/u50:0(10304) WRITE     8:33                8                4( 50.0)     ext4          /dev/sdc1
                                            [   4K -    7K]                       2
    ----------------------------------------------------------------------------------------------------------------------------------------------------------
       
>>>
       
    # ./guider.py rec -e L

    [Thread Futex Lock Info] [ Elapsed : 1.225 ] (Unit: Sec/NR)
    ==========================================================================================================================================================
                Name(  Tid/  Pid)    Elapsed    Process      Block  NrBlock    CallMax       Lock    LockMax   NrLock   NrWait     LBlock NrLBlock   LastStat
    ==========================================================================================================================================================
              mysqld( 3236/ 3208)      0.469      0.000      0.469        1      0.469      0.000      0.000        0        1      0.000        0       Wait
    ----------------------------------------------------------------------------------------------------------------------------------------------------------
              mysqld( 3237/ 3208)      0.890      0.000      0.890        1      0.890      0.000      0.000        0        1      0.000        0       Wait
    ----------------------------------------------------------------------------------------------------------------------------------------------------------
              mysqld( 3238/ 3208)      1.075      0.000      1.075        1      1.075      0.000      0.000        0        1      0.000        0       Wait
    ----------------------------------------------------------------------------------------------------------------------------------------------------------

    [Thread File Lock Info] (Unit: Sec/NR)
    ==========================================================================================================================================================
                Name(  Tid)         Wait            Lock     nrTryLock    nrLocked
    ==========================================================================================================================================================
                smbd( 2631)        0.000           0.000             3           3
    ----------------------------------------------------------------------------------------------------------------------------------------------------------
       
>>>
       
    # ./guider.py rec -s . -K openfile:getname::**string

    [Thread KERNEL Event Info]
    ==========================================================================================================================================================
                 Event                           Comm( Tid )      Usage      Count    ProcMax    ProcMin   InterMax   InterMin
    ==========================================================================================================================================================
                openfile                        TOTAL(  -  )   0.000729       1012   0.000013   0.000001   1.979834   0.000109
                                                   ps(10728)   0.000640        968   0.000013   0.000000   0.001636   0.000006
                                              python2(10727)   0.000038         26   0.000004   0.000001   1.979834   0.000020
                                                 tmux( 6959)   0.000031          9   0.000006   0.000003   0.299492   0.201316
                                       PassengerAgent(23183)   0.000008          5   0.000002   0.000001   0.007375   0.000109
                                         sendmail-mta( 3419)   0.000007          2   0.000006   0.000001   0.000077   0.000077
                                       PassengerAgent(10729)   0.000003          1   0.000003   0.000003   0.000000   0.000000
                                                 smbd(11086)   0.000002          1   0.000002   0.000002   0.000000   0.000000
    ----------------------------------------------------------------------------------------------------------------------------------------------------------

    [Thread KERNEL Event History]
    ==========================================================================================================================================================
                 EVENT                TYPE     TIME                COMM(  TID)         CALLER            ELAPSED ARG
    ==========================================================================================================================================================
                openfile               EXIT   0.063942             tmux( 6959)      porch_do_sys_open   0.000003  1>"/proc/7969/cmdline"
                openfile              ENTER   0.137626          python2(10727)                                 -
                openfile               EXIT   0.137628          python2(10727)      porch_do_sys_open   0.000002  1>"/sys/kernel/debug/tracing/trace"
                openfile              ENTER   0.363431             tmux( 6959)                                 -
                openfile               EXIT   0.363437             tmux( 6959)      porch_do_sys_open   0.000006  1>"/proc/7197/cmdline"
                openfile              ENTER   0.510452             smbd(11086)                                 -
                openfile               EXIT   0.510454             smbd(11086)      porch_do_sys_open   0.000002  1>"/var/log/samba/log.jhkim-z97x-ud3h"
                openfile              ENTER   0.564845             tmux( 6959)                                 -
                openfile               EXIT   0.564848             tmux( 6959)      porch_do_sys_open   0.000003  1>"/proc/7969/cmdline"
                openfile              ENTER   0.864255             tmux( 6959)                                 -
                openfile               EXIT   0.864258             tmux( 6959)      porch_do_sys_open   0.000003  1>"/proc/7197/cmdline"
                openfile              ENTER   1.065571             tmux( 6959)                                 -
                openfile               EXIT   1.065574             tmux( 6959)      porch_do_sys_open   0.000003  1>"/proc/7969/cmdline"
                openfile              ENTER   1.364980             tmux( 6959)                                 -
                openfile               EXIT   1.364984             tmux( 6959)      porch_do_sys_open   0.000004  1>"/proc/7197/cmdline"
                openfile              ENTER   1.437128     sendmail-mta( 3419)                                 -
                openfile               EXIT   1.437134     sendmail-mta( 3419)      porch_do_sys_open   0.000006  1>"/proc/loadavg"
                openfile              ENTER   1.437205     sendmail-mta( 3419)                                 -
                openfile               EXIT   1.437206     sendmail-mta( 3419)      porch_do_sys_open   0.000001  1>"/proc/loadavg"
                openfile              ENTER   1.566369             tmux( 6959)                                 -
                openfile               EXIT   1.566372             tmux( 6959)      porch_do_sys_open   0.000003  1>"/proc/7969/cmdline"
                openfile              ENTER   1.865776             tmux( 6959)                                 -
                openfile               EXIT   1.865779             tmux( 6959)      porch_do_sys_open   0.000003  1>"/proc/7197/cmdline"
                openfile              ENTER   1.955265   PassengerAgent(10729)                                 -
                openfile               EXIT   1.955268   PassengerAgent(10729)      porch_do_sys_open   0.000003  1>"/dev/fd"
    ----------------------------------------------------------------------------------------------------------------------------------------------------------
       
>>>
       
    # ./guider.py funcrec -s .
    # ./guider.py guider.dat -o . -a

    [Function CPU Info] [Cnt: 394] [Interval: 8ms] (USER)
    ==========================================================================================================================================================
    __Usage__|___________________Function____________________|_____________________________________________Binary_____________________________________________
    ==========================================================================================================================================================
       99.0% |                    cpuTest                    | /media/disk/work/test/a.out
       +  100.0% | <- startTest [/media/disk/work/test/a.out] <- main [/media/disk/work/test/a.out]
                     <- __libc_start_main [/lib/x86_64-linux-gnu/libc-2.19.so]
    ----------------------------------------------------------------------------------------------------------------------------------------------------------
        0.5% |                    memset                     | /lib/x86_64-linux-gnu/libc-2.19.so
       +  100.0% | <- startTest [/media/disk/work/test/a.out] <- main [/media/disk/work/test/a.out]
                     <- __libc_start_main [/lib/x86_64-linux-gnu/libc-2.19.so]
    ----------------------------------------------------------------------------------------------------------------------------------------------------------
        0.3% |                  _int_malloc                  | /lib/x86_64-linux-gnu/libc-2.19.so
    ----------------------------------------------------------------------------------------------------------------------------------------------------------
        0.3% |               00007f756e3e7ee4                | ??
       +  100.0% | <- 000000000044676f [/media/disk/work/test/a.out]
    ----------------------------------------------------------------------------------------------------------------------------------------------------------
  
    [Function CPU Info] [Cnt: 394] [Interval: 8ms] (KERNEL)
    ==========================================================================================================================================================
    __Usage__|____________________________________________________________________Function____________________________________________________________________
    ==========================================================================================================================================================
      100.0% |                                                          hrtimer_interrupt
       +   99.5% | <- local_apic_timer_interrupt <- smp_apic_timer_interrupt <- apic_timer_interrupt
       +    0.3% | <- local_apic_timer_interrupt <- smp_apic_timer_interrupt <- apic_timer_interrupt <- do_page_fault <- page_fault
       +    0.3% | <- local_apic_timer_interrupt <- smp_apic_timer_interrupt <- apic_timer_interrupt <- __do_fault <- handle_mm_fault <- __do_page_fault
                     <- do_page_fault <- page_fault
    ----------------------------------------------------------------------------------------------------------------------------------------------------------
       
>>>
       
    # ./guider.py funcrecord -e m -s .
    # ./guider.py guider.dat -a

    [Function Page Info] [Total: 11416KB] [Alloc: 11444KB(817)] [Free: 188KB(47)] (USER)
    ==========================================================================================================================================================
     Usage ( Usr  / Buf  / Ker  )|___________________Function____________________|________________LifeTime________________|______________Binary_______________
    ==========================================================================================================================================================
     10256K(  2048/     0/  8208)|                    memset                     | AVR: 1.563 / MIN: 1.560 / MAX: 1.568   | /lib/x86_64-linux-gnu/libc-2.19.so
      +  10256K(  2048/     0/  8208)| <- startTest [/media/disk/work/test/a.out] <- main [/media/disk/work/test/a.out]
                                         <- __libc_start_main [/lib/x86_64-linux-gnu/libc-2.19.so]
    ----------------------------------------------------------------------------------------------------------------------------------------------------------
       960K(   956/     0/     4)|                  _int_malloc                  | AVR: 1.559 / MIN: 1.554 / MAX: 1.560   | /lib/x86_64-linux-gnu/libc-2.19.so
    ----------------------------------------------------------------------------------------------------------------------------------------------------------
        56K(    16/     0/    40)|               00007f756e3e81e7                | AVR: 1.569 / MIN: 1.568 / MAX: 1.569   | ??
    ----------------------------------------------------------------------------------------------------------------------------------------------------------
        44K(    36/     0/     8)|                   sysmalloc                   | AVR: 1.560 / MIN: 1.558 / MAX: 1.568   | /lib/x86_64-linux-gnu/libc-2.19.so
    ----------------------------------------------------------------------------------------------------------------------------------------------------------
        12K(    12/     0/     0)|           elf_machine_rela_relative           | AVR: 1.568 / MIN: 1.568 / MAX: 1.568   | /lib/x86_64-linux-gnu/ld-2.19.so
      +     12K(    12/     0/     0)| <- dl_main [/lib/x86_64-linux-gnu/ld-2.19.so] <- _dl_sysdep_start [/lib/x86_64-linux-gnu/ld-2.19.so]
    ----------------------------------------------------------------------------------------------------------------------------------------------------------
         8K(     8/     0/     0)|                    realloc                    | AVR: 1.568 / MIN: 1.568 / MAX: 1.568   | /lib/x86_64-linux-gnu/ld-2.19.so
      +      4K(     4/     0/     0)| <- _dl_map_object [/lib/x86_64-linux-gnu/ld-2.19.so]
    ----------------------------------------------------------------------------------------------------------------------------------------------------------
         8K(     4/     0/     4)|                    dl_main                    | AVR: 1.568 / MIN: 1.568 / MAX: 1.568   | /lib/x86_64-linux-gnu/ld-2.19.so
      +      8K(     4/     0/     4)| <- _dl_sysdep_start [/lib/x86_64-linux-gnu/ld-2.19.so]
    ----------------------------------------------------------------------------------------------------------------------------------------------------------
  
    [Function Page Info] [Total: 11416KB] [Alloc: 11444KB(817)] [Free: 188KB(47)] (KERNEL)
    ==========================================================================================================================================================
     Usage ( Usr  / Buf  / Ker  )|___________________Function____________________|__________________________________LifeTime__________________________________
    ==========================================================================================================================================================
      8192K(     0/     0/  8192)|          do_huge_pmd_anonymous_page           |                    AVR: 1.563 / MIN: 1.562 / MAX: 1.564
      +   8192K(     0/     0/  8192)| <- handle_mm_fault <- __do_page_fault <- do_page_fault <- page_fault
    ----------------------------------------------------------------------------------------------------------------------------------------------------------
      3084K(  3084/     0/     0)|                handle_mm_fault                |                    AVR: 1.563 / MIN: 1.554 / MAX: 1.569
      +   3076K(  3076/     0/     0)| <- __do_page_fault <- do_page_fault <- page_fault
      +      4K(     4/     0/     0)| <- __get_user_pages <- get_user_pages <- copy_strings.isra.17 <- copy_strings_kernel <- do_execve_common.isra.23
                                         <- SyS_execve <- stub_execve
      +      4K(     4/     0/     0)| <- __do_page_fault <- do_page_fault <- page_fault <- load_elf_binary <- search_binary_handler
                                         <- do_execve_common.isra.23 <- SyS_execve <- stub_execve
    ----------------------------------------------------------------------------------------------------------------------------------------------------------
       
>>>
       
    # ./guider.py filerec 

    [File Usage Info] [ File: 281 ] [ RAM: 78056(KB) ] [ Keys: Foward/Back/Save/Quit ]
    ==========================================================================================================================================================
    __RAM(KB)___|_File(KB)_|__%___|_____________________________________________________Library & Process_____________________________________________________
    ==========================================================================================================================================================
          7,616 |    7,616 |  100 | /run/samba/locking.tdb [Proc: 10] [Link: 1]
                                  |             smbd ( 2937) |             smbd ( 9178) |             smbd (21387) |             smbd ( 3356) |
                                  |             smbd ( 2828) |             smbd ( 2417) |             smbd ( 3862) |             smbd ( 2631) |
                                  |             smbd (11086) |             smbd (  729) |
    ----------------------------------------------------------------------------------------------------------------------------------------------------------
          6,076 |    8,452 |   71 | /usr/lib/apache2/modules/libphp5.so [Proc: 11] [Link: 1]
                                  |  /usr/sbin/apach (13071) |  /usr/sbin/apach (13073) |  /usr/sbin/apach ( 3817) |  /usr/sbin/apach ( 9111) |
                                  |  /usr/sbin/apach (20085) |  /usr/sbin/apach ( 7221) |  /usr/sbin/apach (  345) |  /usr/sbin/apach (  346) |
                                  |  /usr/sbin/apach ( 7222) |  /usr/sbin/apach (14278) |  /usr/sbin/apach ( 9715) |
    ----------------------------------------------------------------------------------------------------------------------------------------------------------
          5,784 |    9,828 |   58 | /usr/sbin/smbd [Proc: 10] [Link: 1]
                                  |             smbd ( 2937) |             smbd ( 9178) |             smbd (21387) |             smbd ( 3356) |
                                  |             smbd ( 2828) |             smbd ( 2417) |             smbd ( 3862) |             smbd ( 2631) |
                                  |             smbd (11086) |             smbd (  729) |
    ----------------------------------------------------------------------------------------------------------------------------------------------------------
          4,800 |   25,880 |   18 | /var/lib/gems/1.9.1/gems/passenger-5.1.0/buildout/support-binaries/PassengerAgent [Proc: 3] [Link: 1]
                                  |   PassengerAgent (23161) |   PassengerAgent (23176) |   PassengerAgent (23191) |
    ----------------------------------------------------------------------------------------------------------------------------------------------------------
          3,612 |   12,016 |   30 | /usr/sbin/mysqld [Proc: 1] [Link: 1]
                                  |           mysqld ( 3208) |
    ----------------------------------------------------------------------------------------------------------------------------------------------------------
          2,988 |    2,988 |  100 | /usr/lib/libpython2.7.so.1.0 [Proc: 6] [Link: 1]
                                  |               vi (18865) |               vi (28546) |               vi ( 7200) |               vi (22546) |
                                  |               vi ( 8826) |               vi ( 8135) |
    ----------------------------------------------------------------------------------------------------------------------------------------------------------
          2,228 |    2,884 |   77 | /usr/bin/python3.2mu [Proc: 1] [Link: 1]
                                  |           guider (22637) |
    ----------------------------------------------------------------------------------------------------------------------------------------------------------
          2,016 |    2,016 |  100 | /usr/lib/libruby-1.9.1.so.1.9.1 [Proc: 1] [Link: 1]
                                  |        ruby1.9.1 (23294) |
    ----------------------------------------------------------------------------------------------------------------------------------------------------------
       
>>>
       
    # ./guider.py draw guider.out

![guider-graph-image](https://cloud.githubusercontent.com/assets/15862689/23285445/a03e0bf0-fa74-11e6-9f5a-872a3f10fe48.png)    
![guider-chart-image](https://cloud.githubusercontent.com/assets/15862689/24597375/67f31f22-1880-11e7-8290-64554ed2859c.png)
![guider-web-image](https://user-images.githubusercontent.com/15862689/60395898-24a85000-9b75-11e9-857b-991bcae731bc.png)

How to use
=======

```
Enter the following command to see all commands supported by the guider:
    $ ./guider.py --help
    $ python -m guider --help
    $ guider --help

Enter the following command to start tracing for all threads:
    # ./guider.py record -a

Enter the following command to start monitoring for all processes:
    $ ./guider.py top -a

Enter the command in the format shown bellow to see options and examples for each command:
    $ ./guider.py record -h
    $ ./guider.py top -h

Visit the following link to see the output of guider:
    - https://github.com/iipeace/guider/wiki
```


Requirement
=======

```
- linux kernel (>= 2.6)
- python (>= 2.7)
```


Build & Installation
=======

```
If you can run 'pip' on your system then just enter the following command:
    # pip install guider
and just run the following commands:
    # python -m guider
    # guider

Otherwise, download the source from https://github.com/iipeace/guider,
and just run "guider/guider.py" on shell.

If you want to run guider faster and lighter after downloading the source,
then build and install it on your system as below.
    # cd guider && make && make install
```


Kernel Configuration
=======

```
Enable kernel options as below to take advantage of all the features
And if CONFIG_STRICT_MEMORY_RWX is enabled then disable it

CONFIG_RING_BUFFER
CONFIG_FTRACE
CONFIG_TRACING
CONFIG_TRACING_SUPPORT
CONFIG_EVENT_TRACING
CONFIG_NOP_TRACER
CONFIG_TRACEPOINTS
CONFIG_DYNAMIC_FTRACE
CONFIG_HAVE_DYNAMIC_FTRACE
CONFIG_FTRACE_SYSCALLS
CONFIG_HAVE_SYSCALL_TRACEPOINTS
CONFIG_TRACE_IRQFLAGS
CONFIG_TRACE_IRQFLAGS_SUPPORT

CONFIG_STACKTRACE
CONFIG_STACKTRACE_SUPPORT
CONFIG_USER_STACKTRACE_SUPPORT
CONFIG_FUNCTION_TRACER
CONFIG_FUNCTION_GRAPH_TRACER
CONFIG_UPROBES
CONFIG_UPROBE_EVENT
CONFIG_KPROBES
CONFIG_KPROBE_EVENTS

CONFIG_TASKSTATS
CONFIG_TASK_DELAY_ACCT
CONFIG_TASK_XACCT
CONFIG_TASK_IO_ACCOUNTING
CONFIG_PERF_EVENTS 
CONFIG_HW_PERF_EVENT
```


Help
=======

```
Usage:
    $ ./guider.py COMMAND|FILE [OPTIONS] [--help] [--version]

COMMAND:
    [monitor]   top         <process>
                threadtop   <thread>
                systemtop   <system>
                bgtop       <background>
                stacktop    <stack>
                perftop     <PMU>
                memtop      <memory>
                disktop     <storage>
                nettop      <network>
                wsstop      <memory>
                reptop      <JSON>
                filetop     <file>
                systop      <syscall>
                usertop     <usercall>
                strace      <syscall>
                utrace      <usercall>

    [profile]   record      <thread>
                funcrecord  <function>
                filerecord  <file>
                syscrecord  <syscall>
                sysrecord   <system>
                report      <report>
                mem         <page>

    [visual]    draw        <image>
                cpudraw     <cpu>
                memdraw     <memory>
                vssdraw     <vss>
                rssdraw     <rss>
                leakdraw    <leak>
                iodraw      <I/O>
                convert     <text>

    [util]      kill        <signal>
                pause       <thread>
                limitcpu    <cpu>
                setcpu      <clock>
                setsched    <priority>
                getaffinity <affinity>
                setaffinity <affinity>
                pstree      <tree>
                printenv    <env>
                printsystem <system>
                readelf     <file>
                addr2line   <symbol>
                leaktrace   <leak>

    [control]   list        <list>
                start       <signal>
                send        <signal>
                event       <event>
                server      <server>
                client      <client>

    [test]      cputest     <cpu>
                alloctest   <mem>

FILE:
    Profile file (e.g. guider.dat)
    Report  file (e.g. guider.out)

OPTIONS:
    Check COMMAND with --help (e.g. ./guider.py top --help)
```
