## GRPID - Another AQM Algorithm ##

## Algorithm ##

Just another AQM (Active Queue Management) algorithm, check [this](https://github.com/zheolong/master-paper).

## Include ##
* linux kernel model version of GAPSO-RBF-PID (dir:"./modules" and "./include")
* modified test tool -- iproute2 (dir: "iproute2-3.1.0")
* test script and gnuplot file (dir: "test")

## Geting started ##

### Requirements ###

GRPID is one of the AQM schemes which are used to manage the queue of the intermediate network devices (typically, routers).

Therefore, you must have at least two computers with linux system. Here we refer to them as *A* and *B*.

You must also ensure that you have compiled a linux kernel source in *A*'s system and boot *A* with the new kernel. The kernel version preferably is **2.6.39.2**.

*A* can ping *B* and *B* can ping *A*.

### Install ###

* For *B*

  install *iperf* (Ubuntu user just run `apt-get install iperf`)

* For *A*

  1. Download source(and unzip)
  2. open your kernel source file "<kernel source dir.>/include/linux/pkt_sched.h"
   insert the content of "./patch/gapso-rbf-pid\_patch\_content" just before "/* GRED section */"
  3. from the terminal navigate to source folder *gapso-rbf-pid* and run `make`
  4. install *iperf* and *gnuplot* (Ubuntu user just run `apt-get install iperf gnuplot`)

### Usage ###

* For *B*

  run `iperf -s` 

* For *A*,

  1. from the terminal navigate to source folder *gapso-rbf-pid*
  2. run `cd test && ./autotest` and wait 50 seconds util the test is done. Not surprisingly, you'll see the drawing of test results.

  ![gapso-rbf-pid 1Gbps(port)-100Mbps(link)-1Gbps(port)](https://github.com/zheolong/gapso-rbf-pid/blob/master/pic_in_readme/1.png)
