---
title: SPECint
date: 2016-12-29 10:38:05
tags:
	- D05
	- CentOS
categories:
	- Estuary
	- Documents
---

- **Dependency:**
  ```bash
  yum install automake
  yum install numactl
  yum install gcc*
  yum install libgfortran
  yum install *cmp
  yum install cmp*
  ```
- **Source code:**
  *Openlab:192.168.1.101:/home/chenzhihui/Ali-test/speccpu2006*

- **Build:**
  ```bash
  export FORCE_UMSAFE_CONFIGURE=1
  SPEC_DIR=speccpu2006
  cd $SPEC_DIR/tools/src&&echo y | ./buildtools
  ```
- **Test:**
  ```bash
  SPEC_DIR=speccpu2006
  cd $SPEC_DIR
  . ./shrc
  ./bin/runspec -c config/lemon-2cpu.cfg int --rate 1 -n 1 -noreportable
  ./bin/runspec -c config/lemon-2cpu.cfg int --rate 32 -n 1 -noreportable
  ./bin/runspec -c config/lemon-2cpu.cfg int --rate 64 -n 1 -noreportable
  ```

