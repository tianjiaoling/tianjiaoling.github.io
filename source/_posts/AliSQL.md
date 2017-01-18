---
title: AliSQL
date: 2016-12-30 10:10:56
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
  cd applications/apps/mysql/alisql_1
  ```
- Init:
  ```bash
  ./setup.sh server
  ```
- Run:
  ```bash
  ./run_server.sh
  ```
**Client side**
- Download scripts:
  ```bash
  git clone https://github.com/sjtuhjh/applications
  cd applications/apps/mysql/alisql_1
  ```
- Init:
  ```
  ./setup.sh client
  ```
- Run:
  ```
  ./run_test.sh
  ```
