---
title: Openblas
date: 2016-12-30 09:36:50
tags:
	- D05
	- CentOS
categories:
	- Estuary
	- Documents
---
- **Source code:**
  ```bash
  git clone https://github.com/xianyi/OpenBLAS.git
  git reset --hard d4da3fb
  ```
- **Build:**
  ```bash
  cd OpenBLAS
  make TARGET=ARMV8 BINARY=64
  cd benchmark
  make TARGET=ARMV8 BINARY=64

  ```
- **Test:**
  ```bash
  cd OpenBLAS
  cd benchmark
  export OPENBLAS_NUM_THREADS=1
  taskset -c 0 ./sgemm.goto 200 4000 200
  export OPENBLAS_NUM_THREADS=10
  taskset -c 0-9 ./sgemm.goto 200 4000 200
  export OPENBLAS_NUM_THREADS=32
  taskset -c 0-31 ./sgemm.goto 200 4000 200
  export OPENBLAS_NUM_THREADS=64
  taskset -c 0-63 ./sgemm.goto 200 4000 200

  ```
