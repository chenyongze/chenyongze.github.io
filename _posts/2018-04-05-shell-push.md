---
layout: post
title:  "shell 打包发布"
date:   2018-04-05 02:00:00
categories: shell
tags: [shell,ssh]
---

## 发布代码 服务器[ linux ]

```
    #!/bin/bash
    #author:yongze.chen
    WEBIP="114.215.xx.xx"
    S_PATH="/data/excel/"
    echo " ========= start==== $WEBIP ===="
    cd $S_PATH
    TAG_PACK=`date +%Y%m%d%s`-excel.tar.gz
    tar -zcvf  $TAG_PACK *
    echo "========== scp $TAG_PACK========"
    scp $TAG_PACK root@${WEBIP}:$S_PATH
    rm $TAG_PACK
    ssh root@$WEBIP "cd ${S_PATH} && tar -zxvf ${TAG_PACK} && rm ${TAG_PACK}"
    echo "=========== sucess ================"
```