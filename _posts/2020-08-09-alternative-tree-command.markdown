---
layout: post
comments: true
title:  "Treeコマンドがない時にLinuxコマンドで代替する"
date:   2020-05-20 00:00:00 +0000
categories: linux
tags: tree linuxコマンド 
published: false
---
treeコマンドがインストールされていない場合や、treeコマンドがインストールできない環境で、
treeコマンドと同様の表示がしたくて方法を調べました。

## tree コマンドとは

ディレクトリやファイルをツリー状に表示するコマンドです。
以下のような表示が確認できます。

### 実行結果

```ruby
$ tree
.
├── index.html
├── test1
│   ├── index1.html
│   └── test1-1
│       └── index1-1.html
└── test2
    └── test2-1
        └── index2.html
```

## treeコマンドの代替コマンド

```ruby
$ pwd;find . | sort | sed '1d;s/^\.//;s/\/\([^/]*\)$/|--\1/;s/\/[^/|]*/|  /g'
```

### 実行結果

```
/Users/rhinonolike/sample
|--index.html
|--test1
|  |--index1.html
|  |--test1-1
|  |  |--index1-1.html
|--test2
|  |--test2-1
|  |  |--index2.html
```
