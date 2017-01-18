---
title: Percona
date: 2016-12-30 11:33:46
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
  git clone https://github.com/sjtuhjh/applicstions
  cd applicstions/apps/mysql/percona_1
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
- Download scripts:
  ```bash
  git clone https://github.com/sjtuhjh/applicstions
  cd applicstions/apps/mysql/percona_1
  ```
- Init:
  ```bash
  ./setup.sh client
  ```
- Run: 
  ```bash
  ./run_test.sh <server ip>
  ```
