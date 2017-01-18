---
title: Hibench
date: 2016-12-30 09:46:32
tags:
	- D05
	- CentOS
categories:
	- Estuary
	- Documents
---
**Server side:**
- *Download scripts:*
  ```bash
  git clone https://github.com/sjtuhjh/applications
  cd applications/apps/hadoop/hadoop_test1/
  ```

- *Init:* 	
  ```
  ./setup.sh server
  ```

- *Run:*
  ```
  ./run_server.sh
  ```
**Client side:**
- *Download scripts:*
  ```bash
  git clone https://github.com/sjtuhjh/applications
  cd applications/apps/hadoop/hadoop_test1/
  ```
- *Init:*
  ```
  ./setup.sh client
  ```
- *Run:*
  ```
  ./run_test_all.sh
  ```
