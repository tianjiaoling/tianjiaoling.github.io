---
title: Redis
date: 2016-12-30 14:53:49
tags:
	- D05
	- CentOS
categories:
	- Estuary
	- Documents
---
**Server side:**
- Download scripts:
	```bash
	git clone https://github.com/sjtuhjh/applications
	cd applications/apps/redis/redis_test1
	```
- Init:
	```bash
	./setup.sh server
	```
- Run:
	```bash
	./run_server.sh
	```
**Client side:**
- Download:
	```bash
	git clone https://github.com/sjtuhjh/applications
	cd applications/apps/redis/redis_test1
	```
- Init:
	```bash
	./setup.sh client
	```
- Run:
	```bash
	./run_test.sh
	```
