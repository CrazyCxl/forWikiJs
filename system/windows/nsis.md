---
title: Nsis
description: win package tool
published: true
date: 2024-10-09T02:11:32.118Z
tags: win
editor: markdown
dateCreated: 2024-10-09T02:11:32.118Z
---

# Path set
plugin:https://nsis.sourceforge.io/EnVar_plug-in
```
!include LogicLib.nsh
Section
EnVar::SetHKCU
EnVar::Check "Path" "$InstDir"
Pop $0
${If} $0 = 0
  DetailPrint "Already there"
${Else}
  EnVar::AddValue "Path" "$InstDir"
  Pop $0 ; 0 on success
${EndIf}

EnVar::DeleteValue "Path" "$InstDir"
Pop $0
SectionEnd
```