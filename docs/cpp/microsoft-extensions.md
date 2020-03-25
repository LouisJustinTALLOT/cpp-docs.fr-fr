---
title: Extensions Microsoft
ms.date: 11/04/2016
helpviewer_keywords:
- Microsoft extensions to C/C++
ms.assetid: 68654516-24ef-4f33-aae2-175f86cc1979
ms.openlocfilehash: a2d0846e55122f177b4868c2e80c4f1d27267f5e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80179404"
---
# <a name="microsoft-extensions"></a>Extensions Microsoft

*ASM-Statement*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **__asm** *-instruction d’assembly* **;** <sub>OPT</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp; **__asm {** *assembly-instruction-List* **};** <sub>OPT</sub>

*assembly-instruction-List*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*assembly-instruction* **;** <sub>OPT</sub> <br/>
&nbsp;&nbsp;&nbsp;&nbsp;*assembly-instruction* **;** *assembly-instruction-List* **;** <sub>OPT</sub>

*MS-modifier-liste*:<br/>
&nbsp;&nbsp; *&nbsp;&nbsp;MS-modifier* MS-modifier *-liste*<sub>OPT</sub>

*MS-modifier*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **__cdecl**<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **__fastcall**<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **__stdcall**<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **__syscall** (réservé aux implémentations futures)<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **__oldcall** (réservé aux implémentations futures)<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **__unaligned** (réservé aux implémentations futures)<br/>
&nbsp;&nbsp;&nbsp;&nbsp; *-modifier*

*modificateur de base*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **__based (** *type basé sur* **)**

*type basé sur*:<br/>
&nbsp;&nbsp;&nbsp;*nom* de &nbsp;
