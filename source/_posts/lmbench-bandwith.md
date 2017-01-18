---
title: lmbench_bandwith
date: 2016-12-28 15:48:17
tags:
	- D05
	- CentOS
categories:
 	- Estuary
	- Documents
---

- **Dependency:**
  ```  
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
- **Test**
  Local memory access:
  ```bash
taskset -c 0 ./bw_mem -P 1 -N 5 32M rd
taskset -c 0 ./bw_mem -P 1 -N 5 32M frd
taskset -c 0 ./bw_mem -P 1 -N 5 32M wr
taskset -c 0 ./bw_mem -P 1 -N 5 32M fwr
taskset -c 0 ./bw_mem -P 1 -N 5 32M bzero
taskset -c 0 ./bw_mem -P 1 -N 5 32M rdwr
taskset -c 0 ./bw_mem -P 1 -N 5 32M cp
taskset -c 0 ./bw_mem -P 1 -N 5 32M fcp
taskset -c 0 ./bw_mem -P 1 -N 5 32M bcopy

taskset -c 0-3 ./bw_mem -P 4 -N 5 32M rd
taskset -c 0-3 ./bw_mem -P 4 -N 5 32M frd
taskset -c 0-3 ./bw_mem -P 4 -N 5 32M wr
taskset -c 0-3 ./bw_mem -P 4 -N 5 32M fwr
taskset -c 0-3 ./bw_mem -P 4 -N 5 32M bzero
taskset -c 0-3 ./bw_mem -P 4 -N 5 32M rdwr
taskset -c 0-3 ./bw_mem -P 4 -N 5 32M cp
taskset -c 0-3 ./bw_mem -P 4 -N 5 32M fcp
taskset -c 0-3 ./bw_mem -P 4 -N 5 32M bcopy

taskset -c 0-15 ./bw_mem -P 16 -N 5 32M rd
taskset -c 0-15 ./bw_mem -P 16 -N 5 32M frd
taskset -c 0-15 ./bw_mem -P 16 -N 5 32M wr
taskset -c 0-15 ./bw_mem -P 16 -N 5 32M fwr
taskset -c 0-15 ./bw_mem -P 16 -N 5 32M bzero
taskset -c 0-15 ./bw_mem -P 16 -N 5 32M rdwr
taskset -c 0-15 ./bw_mem -P 16 -N 5 32M cp
taskset -c 0-15 ./bw_mem -P 16 -N 5 32M fcp
taskset -c 0-15 ./bw_mem -P 16 -N 5 32M bcopy

taskset -c 0-31 ./bw_mem -P 32 -N 5 32M rd
taskset -c 0-31 ./bw_mem -P 32 -N 5 32M frd
taskset -c 0-31 ./bw_mem -P 32 -N 5 32M wr
taskset -c 0-31 ./bw_mem -P 32 -N 5 32M fwr
taskset -c 0-31 ./bw_mem -P 32 -N 5 32M bzero
taskset -c 0-31 ./bw_mem -P 32 -N 5 32M rdwr
taskset -c 0-31 ./bw_mem -P 32 -N 5 32M cp
taskset -c 0-31 ./bw_mem -P 32 -N 5 32M fcp
taskset -c 0-31 ./bw_mem -P 32 -N 5 32M bcopy

numactl -C 0-31,32-63 ./bw_mem -P 64 -N 5 32M rd
numactl -C 0-31,32-63 ./bw_mem -P 64 -N 5 32M rd
numactl -C 0-31,32-63 ./bw_mem -P 64 -N 5 32M rd
numactl -C 0-31,32-63 ./bw_mem -P 64 -N 5 32M rd
numactl -C 0-31,32-63 ./bw_mem -P 64 -N 5 32M rd
numactl -C 0-31,32-63 ./bw_mem -P 64 -N 5 32M rd
numactl -C 0-31,32-63 ./bw_mem -P 64 -N 5 32M rd
numactl -C 0-31,32-63 ./bw_mem -P 64 -N 5 32M rd
numactl -C 0-31,32-63 ./bw_mem -P 64 -N 5 32M rd
  ```
  <!--more-->

- **Cross die memory access:**
  ```bash
numactl -C 0 -m 1 ./bw_mem -P 1 -N 5 32M rd
numactl -C 0 -m 1 ./bw_mem -P 1 -N 5 32M frd
numactl -C 0 -m 1 ./bw_mem -P 1 -N 5 32M wr
numactl -C 0 -m 1 ./bw_mem -P 1 -N 5 32M fwr
numactl -C 0 -m 1 ./bw_mem -P 1 -N 5 32M bzero
numactl -C 0 -m 1 ./bw_mem -P 1 -N 5 32M rdwr
numactl -C 0 -m 1 ./bw_mem -P 1 -N 5 32M cp
numactl -C 0 -m 1 ./bw_mem -P 1 -N 5 32M fcp
numactl -C 0 -m 1 ./bw_mem -P 1 -N 5 32M bcopy

numactl -C 0-3 -m 1 ./bw_mem -P 4 -N 5 32M rd
numactl -C 0-3 -m 1 ./bw_mem -P 4 -N 5 32M frd
numactl -C 0-3 -m 1 ./bw_mem -P 4 -N 5 32M wr
numactl -C 0-3 -m 1 ./bw_mem -P 4 -N 5 32M fwr
numactl -C 0-3 -m 1 ./bw_mem -P 4 -N 5 32M bzero
numactl -C 0-3 -m 1 ./bw_mem -P 4 -N 5 32M rdwr
numactl -C 0-3 -m 1 ./bw_mem -P 4 -N 5 32M cp
numactl -C 0-3 -m 1 ./bw_mem -P 4 -N 5 32M fcp
numactl -C 0-3 -m 1 ./bw_mem -P 4 -N 5 32M bcopy

numactl -C 0-15 -m 1 ./bw_mem -P 16 -N 5 32M rd
numactl -C 0-15 -m 1 ./bw_mem -P 16 -N 5 32M frd
numactl -C 0-15 -m 1 ./bw_mem -P 16 -N 5 32M wr
numactl -C 0-15 -m 1 ./bw_mem -P 16 -N 5 32M fwr
numactl -C 0-15 -m 1 ./bw_mem -P 16 -N 5 32M bzero
numactl -C 0-15 -m 1 ./bw_mem -P 16 -N 5 32M rdwr
numactl -C 0-15 -m 1 ./bw_mem -P 16 -N 5 32M cp
numactl -C 0-15 -m 1 ./bw_mem -P 16 -N 5 32M fcp
numactl -C 0-15 -m 1 ./bw_mem -P 16 -N 5 32M bcopy
  ```
