---
layout: post
title: "Websocket 壓測工具"
date: 2019-06-30 22:48:14 +0800
comments: true
categories: golang
---

這是一個以 go語言編寫的 websocket壓測工具，提供併發連線、結果驗證、時間計算等功能。筆者目前使用的環境多為 Linux & MacOS，如果想在CLI簡單地對 websocket服務進行壓力測試的話，這邊提供一個簡單的工具給大家。

[Github Link](https://github.com/WeiWeiWesley/WsTestTool)

<!--more-->

## 使用方式

由於已經預先編譯好不同OS可執行的執行檔，大家可自行依照所使用的環境於 ./exe 中找到適合的執行版本。

### 參數介紹
```
# ./exe/mac_amd64 -h

  -H string
    	Host.
  -d int
    	Time duration(nanosecond) between each request (default 10)
  -h	Usage
  -n int
    	Number of connections (default 1)
  -r int
    	Re-send message times (default 1)
  -req string
    	Json string param
  -resEq string
    	Check response msg equivalent to something
  -resHas string
    	Check response msg contain sub string
  -timing string
    	Start at particular time ex. 2019-05-08 15:04:00
  -to int
    	Max waitting time(second) (default 10)
  -w	Watch each resposnes
```

- \-h:   使用說明
- \-H:   連線目標（必填）
- \-n:   併發連線數量 （預設1）
- \-r:   相同請求重複發送次數（預設1）
- \-req: 請求發送字串
- \-d:   重複發送間隔（預設 10ns）
- \-resEq: 期望結果全等於特定自串才算成功
- \-resHas: 期望結果包含特定字串才算成功
- \-to: 最大測試時間
- \-timing: 定時器，提供多台電腦同時進行壓測
- \-w: 逐一觀察回傳結果內容

