---
title: Iperf
date: 2016-12-30 13:54:52
tags:
	- D05
	- CentOS
categories:
	- Estuary
	- Documents
---
**Server side:**
- Build:
	```bash
	wget http://nchc.dl.sourceforge.net/project/iperf/iperf-2.0.5.tar.gz
	tar xf iperf-2.0.5.tar.gz
	cd iperf-2.0.5
	make && make install
	ln -s /usr/local/iperf /usr/bin/iperf
 	```
- Init:
	```bash
	ifconfig eth2 <server ip>
	ethtool -C eth2 rx-usecs 30 rx-frames 30 tx-frames 30
	service iptables stop
	service network-manager stop
	```
- Run:
	```bash
	iperf -s -w 256k
	```
**Client side:**
- Build:
	```bash
	wget http://nchc.dl.sourceforge.net/project/iperf/iperf-2.0.5.tar.gz
	tar xf iperf-2.0.5.tar.gz
	cd iperf-2.0.5
	make && make install
	ln -s /usr/local/iperf /usr/bin/iperf
	```
- Init:
	```bash
	ifconfig eth2 <client ip>
	ethtool -C eth2 rx-usecs 30 rx-frames 30 tx-frames 30
	service iptables stop
	service network-manager stop
	```
- Run:
	```bash
	iperf -c <server ip> -P 1 -t 100 -i 1 -w 256k
	iperf -c <server ip> -P 4 -t 100 -i 1 -w 256k
	```
