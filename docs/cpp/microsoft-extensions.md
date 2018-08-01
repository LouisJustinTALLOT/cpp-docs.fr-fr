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
ms.openlocfilehash: 70b1e0e6ef1294ff23952816db6f468022609f4f
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/01/2018
ms.locfileid: "39408373"
---
# <a name="microsoft-extensions"></a>Extensions Microsoft
*instruction d’ASM*:  
 **__asm***instruction d’assembly* **;** opt    
  
 **__asm {***liste d’instructions d’assembly***} ;** opt      
  
 *liste d’instructions d’assembly*:  
 *instruction d’assembly* **;** opt  
  
 *instruction d’assembly* **;** *liste d’instructions d’assembly* **;** opt  
  
 *MS-modificateur-list*:  
 *MS-modificateur ms-modificateur-list*opt  
  
 *MS-modificateur*:  
 **__cdecl**  
  
 **__fastcall**  
  
 **__stdcall**  
  
 **__syscall** (réservé pour les implémentations futures)  
  
 **__oldcall** (réservé pour les implémentations futures)  
  
 **__unaligned** (réservé pour les implémentations futures)  
  
 *modificateur en fonction*  
  
 *modificateur basé*:  
 **__based (** *en fonction de type* **)**  
  
 *en fonction de type*:  
 *name*  