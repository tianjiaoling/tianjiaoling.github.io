---
title: Stream
date: 2016-12-27 17:30:31
tags:
  - D05
  - CentOS
categories:
  - Estuary
  - Documents
---

- **Denpendency:**
  ```bash
  yum install numactl
  ```
- **Source code:**  
  *Openlab:192.168.1.101:/home/chenzhihui/Ali-test/lmbench-3.0-a9/*
- **Build:**
  ```bash
  cd lmbench-3.0-a9
  sed -i 's/--static//' src/Makefile # 去掉src/Makefile里面的--static
  sed -i 's/-O/-O2/g' src/Makefile # 使用 O2 级别优化
  make OS=lmbench
  numactl -H  # 查看node信息,然后修改下面对应参数
  ```
- **Test:**
  ```bash
  cd ./bin/lmbench/
  for((i=0;i<10;i++));do
	  numactl --cpunodebind=0,1,2,3 --localalloc ./stream -v 1 -M 200M -P 64
	  numactl --cpunodebind=0,1,2,3 --localalloc ./stream -v 2 -M 200M -P 64
  done
  ```
