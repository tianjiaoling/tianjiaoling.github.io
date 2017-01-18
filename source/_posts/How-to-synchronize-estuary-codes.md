---
title: How to synchronize estuary codes
date: 2016-12-26 13:47:58
tags:
  - D03
  - D05
categories:
  - Estuary
  - Documents
---

### repo_sync.sh

使用{% asset_link repo_sync.sh %}脚本同步estuary相关源码：
```bash
#!/bin/bash

VERSION=$1

BIN_DIR=~/bin
if [ ! -e $BIN_DIR ]; then
	mkdir -p $BIN_DIR
fi

if [ ! -e ${BIN_DIR}/repo ]; then
	wget -c http://www.open-estuary.com/EstuaryDownloads/tools/repo -O ${BIN_DIR}/repo
	chmod +x ${BIN_DIR}/repo
fi

export PATH=${BIN_DIR}:$PATH

ESTUARY_DIR=~/open-estuary
if [ ! -e $ESTUARY_DIR ]; then
	mkdir -p $ESTUARY_DIR
	cd $ESTUARY_DIR
else
	cd $ESTUARY_DIR
	repo forall -c git reset --hard
	repo forall -c git clean -dxf
fi

if [ x"$VERSION" != x"" ]; then
	repo init -u "https://github.com/open-estuary/estuary.git" -b refs/tags/$VERSION --no-repo-verify --repo-url=git://android.git.linaro.org/tools/repo
else
	repo init -u "https://github.com/open-estuary/estuary.git" -b master --no-repo-verify --repo-url=git://android.git.linaro.org/tools/repo
fi

#false; while [ $? -ne 0 ]; do repo sync --force-sync --fetch-submodules; done
false; while [ $? -ne 0 ]; do repo sync --force-sync; done
repo status
```
<!--more-->

### 使用说明

1. 不指定任何参数，默认同步`master`分支代码
```bash
./repo_sync.sh
```
2. 指定`tag`标签，则同步相应标签的代码
```bash
./repo_sync.sh estuary-v2.3
```
上述脚本执行，将下载`repo`工具并存放于用户主目录下的`bin`目录，estuary相关代码同步于用户主目录下的`open-estuary`目录下。
