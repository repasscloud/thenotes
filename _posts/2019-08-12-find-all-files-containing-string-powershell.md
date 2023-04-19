---
title: Find All Files Containing String
author: danijeljw-rpc
date: 2019-08-12 00:00:00 +1000
categories: [PowerShell, utility]
tags: [powershell, cli]
math: true
mermaid: true 
image:
  path: /assets/image/2019/08/12/PowerShell_5.0_icon.png
  alt: Cat sitting in a hamburger single colour background pixel art by Dall-E
---

Search all files recurisvely for text using PowerShell:

```powershell
Get-ChildItem -Recuse | Select-String "search_string" -List | Select Path
```