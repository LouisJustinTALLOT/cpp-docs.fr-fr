---
title: Extensions Microsoft
ms.date: 11/04/2016
helpviewer_keywords:
- Microsoft extensions to C/C++
ms.assetid: 68654516-24ef-4f33-aae2-175f86cc1979
ms.openlocfilehash: d8104c2df2335e11dcb711108d566e0fdd069762
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50592203"
---
# <a name="microsoft-extensions"></a>Extensions Microsoft

*instruction d’ASM*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**__asm***instruction d’assembly* **;** <sub>opt  </sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;**__asm {***liste d’instructions d’assembly***} ;** <sub>opt    </sub>

*liste d’instructions d’assembly*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*instruction d’assembly* **;** <sub>opt</sub> <br/>
&nbsp;&nbsp;&nbsp;&nbsp;*instruction d’assembly* **;** *liste d’instructions d’assembly* **;** <sub>opt</sub>

*MS-modificateur-list*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*MS-modificateur* *ms-modificateur-list*<sub>opt</sub>

*MS-modificateur*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**__cdecl**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**__fastcall**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**__stdcall**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**__syscall** (réservé pour les implémentations futures)<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**__oldcall** (réservé pour les implémentations futures)<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**__unaligned** (réservé pour les implémentations futures)<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*modificateur en fonction*

*modificateur basé*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**__based (** *en fonction de type* **)**

*en fonction de type*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Nom*