---
title: Qperf
date: 2016-12-30 14:15:51
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
	yum install gperf
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
	Qperf
	```
**Client side:**
- Build:
	```bash
	yum install qperf
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
	qperf -oo msg_size:1:64k:*2<server ip> tcp_bw tcp_lat
	```
