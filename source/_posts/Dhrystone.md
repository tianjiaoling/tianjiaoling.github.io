---
title: Dhrystone
date: 2016-12-29 14:40:01
tags:
	- D05
	- CentOS
categories:
	- Estuary
	- Documents
---
- **Source code:**
  *Openlab:192.168.1.101:/home/chenzhihui/All-test/dhrystone/dhrystone-2.1*

- **Build:**
  ```bash
  cd dhrystone-2.1
  make unix
  ```
- **Test:**
  ```bash
  cd dhrystone-2.1
  taskset -c 0 ./gcc_dry2<<EOF
  1000000000
  EOF
  ```
