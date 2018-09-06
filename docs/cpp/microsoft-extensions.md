---
title: Extensions Microsoft | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- Microsoft extensions to C/C++
ms.assetid: 68654516-24ef-4f33-aae2-175f86cc1979
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5699ce82a6e8537f12da50fdcb8288da167ecca3
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43752237"
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