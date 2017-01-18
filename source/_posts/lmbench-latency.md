---
title: Lmbench-latency
date: 2016-12-28 16:22:52
tags:
	- D05
	- CentOS
categories:
	- Estuary
	- Documents
---

- **Dependency:**

  ```bash
  yum install numactl
  ```

- **Source code:**
  *Openlab:192.168.1.101:/home/chenzhihui/Ali-test/lmbench-3.0-a9*

- **Build:**

  ```bash
  cd lmbench-3.0-a9
  sed -i 's/--static//' src/Makefile
  sed -i 's/-O/-O2/g' src/Makefile
  make OS=lmbench 
  ```

- **Test:**
  Local memory access:
  ```bash
  numactl --membind=0 --physcpubind=0 ./lat_mem_rd -P 1 -t 32M 128
  numactl --membind=0 --physcpubind=0-3 ./lat_mem_rd -P 4 -t 32M 128
  numactl --membind=0 --physcpubind=0-15 ./lat_mem_rd -P 16 -t 32M 128
  numactl --physcpubind=0-31 ./lat_mem_rd -P 32 -t 32M 128
  ```
  <!--more-->
  Cross die memory access:
  ```bash
  numactl --membind=1 --physcpubind=0 ./lat_mem_rd -P 1 -t 32M 128
  numactl --membind=1 --physcpubind=0-3 ./lat_mem_rd -P 4 -t 32M 128
  numactl --membind=1 --physcpubind=0-15 ./lat_mem_rd -P 16 -t 32M 128
  ```
