---
title: Netperf
date: 2016-12-30 14:25:32
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
	wget ftp://ftp.netperf.org/netperf/netperf-2.7.0.tar.gz
	tar xf netperf-2.7.0.tar.gz
	cd netperf-2.7.0
	./configure --build=aarch64-unknown-linux-gun
	make && make install
	```
- Init:
	```bash
	ifconfig eth2 <server ip>
	ethtool -C eth2 rx-usecs 30 rx-frames 30 tx-usecs 30 tx-frames 30
	service iptables stop
	service network-manager stop
	```
- Run:
	```bash
	Netserver
	```
**Client side:**
- Build:
	```bash
	wget ftp://ftp.netperf.org/netperf/netperf-2.7.0.tar.gz
	tar xf netperf-2.7.0.tar.gz
	cd netperf-2.7.0
	./configure --build=aarch64-unknown-linux-gun
	make && make install
	```
- Init:
	```bash
	ifconfig eth2 <client ip>
	ethtool -C eth2 rx-usecs 30 rx-frames 30 tx-usecs 30 tx-frames 30
	service iptables stop
	service network-manager stop
	```
- Run:
	```bash
	netperf -t TCP_STREAM -H <server ip> -l 60 --m 2048
	netperf -t TCP_RR -H <server ip> -l 60 --r 64,1024
	netperf -t TCP_CRR -H <server ip> -l 60 --r 64,1024
	netperf -t UDP_RR -H <server ip> -l 60 --r 64,1024
	```
