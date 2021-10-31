---
title: API
description: Access resources and perform actions using the PreMiD API
published: true
date: 2021-09-18T14:19:10.798Z
tags: 
editor: markdown
dateCreated: 2021-09-07T01:31:25.379Z
---

# API

> ベースURL: https://api.premid.app 
> 
> {.is-info}

## APIのバージョン
> API v2 has been deprecated and will be removed in the near future. Please use v3 for any future request to prevent issues. 
> 
> {.is-danger}

PreMiDには異なるバージョンのAPIがあります。 `https://api.premid.app/v{version_number}` のようなリクエストパスを同梱することでバージョンを指定できます。 ルート上からバージョンの番号を省略した場合、自動的に現在のバージョンにルートリクエストされます。(以下にそれに応じてかいてあります)

## 暗号化

PreMiD内のすべてのHTTPレイヤーのサービスやプロトコル (例: http)は TLS 1.2 を使用します。

# ドキュメント
> 現在作成中！ 
> 
> {.is-danger}

**APIのバージョンを選んでください:**
- [v2 *deprecated*](/dev/api/v2)
- [v3 *active*](/dev/api/v3)
{.links-list}