---
title: Extensions Microsoft
ms.date: 11/04/2016
helpviewer_keywords:
- Microsoft extensions to C/C++
ms.assetid: 68654516-24ef-4f33-aae2-175f86cc1979
ms.openlocfilehash: d8104c2df2335e11dcb711108d566e0fdd069762
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62301771"
---
# <a name="microsoft-extensions"></a>Extensions Microsoft

*instruction d’ASM*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**__asm**  *assembly-instruction* **;**<sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;**__asm {**  *assembly-instruction-list*  **} ;**<sub>opt</sub>

*liste d’instructions d’assembly*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*assembly-instruction* **;**<sub>opt</sub> <br/>
&nbsp;&nbsp;&nbsp;&nbsp;*assembly-instruction* **;** *assembly-instruction-list* **;**<sub>opt</sub>

*MS-modificateur-list*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*ms-modifier* *ms-modifier-list*<sub>opt</sub>

*MS-modificateur*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**__cdecl**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**__fastcall**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**__stdcall**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**__syscall** (réservé pour les implémentations futures)<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**__oldcall** (réservé pour les implémentations futures)<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**__unaligned** (réservé pour les implémentations futures)<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*based-modifier*

*modificateur basé*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**__based (** *based-type* **)**

*based-type*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*name*