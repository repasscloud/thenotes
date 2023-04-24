---
title: MSSQL Server Express in Docker
author: danijeljw-rpc
date: 2023-03-24 00:00:00 +1000
categories: [Docker, Microsoft]
tags: [C#, sql, mssql, microsoft, docker]
math: true
mermaid: true 
---

Microsoft SQL Server Express can be up and running with a simple docker command:

```bash
docker run -d --name sql_server -e 'ACCEPT_EULA=Y' -e 'SA_PASSWORD=someThingComplicated1234' -p 1433:1433 mcr.microsoft.com/mssql/server:2019-latest
```

Now connect to it with [Azure Data Studio](https://learn.microsoft.com/en-us/sql/azure-data-studio/download-azure-data-studio?view=sql-server-ver16&tabs=redhat-install%2Credhat-uninstall) for macOS.