---
layout: single
title: "윈도우 알림 메뉴 안 열림 issue"
---

<br>


Windows **알림 메뉴**가 안열리기에 해결 방법을 찾고 있다.



 Powershell 을 관리자 모드로 실행한 뒤

```ts
Get-AppXPackage -AllUsers | Foreach {Add-AppxPackage -DisableDevelopmentMode -Register "$($_.InstallLocation)\AppXManifest.xml"}
```

 를 Ctrl v 해봤으나 해결되지 않았다.

 귀찮으니 그냥 냅두려고 한다...