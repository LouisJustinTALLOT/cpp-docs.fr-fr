---
title: Extensions Microsoft | Documents Microsoft
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
ms.openlocfilehash: beac75a8a27fc4638b541228330e83e7b665fbcb
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32419821"
---
# <a name="microsoft-extensions"></a>Extensions Microsoft
*l’instruction asm*:  
 **__asm***assembly-instruction* **;** s’abonner    
  
 **__asm {***assembly-instruction-list***} ;** s’abonner      
  
 *assembly-instruction-list*:  
 *assembly-instruction* **;** s’abonner  
  
 *assembly-instruction* **;** *assembly-instruction-list* **;** s’abonner  
  
 *MS-modifier-list*:  
 *MS-modifier ms-modifier-list*opt  
  
 *MS-modifier*:  
 **__cdecl**  
  
 **__fastcall**  
  
 **__stdcall**  
  
 **__syscall** (réservé pour les implémentations futures)  
  
 **__oldcall** (réservé pour les implémentations futures)  
  
 **__unaligned** (réservé pour les implémentations futures)  
  
 *modificateur de base*  
  
 *modificateur en fonction*:  
 **__based (** *en fonction de type* **)**  
  
 *en fonction de type*:  
 *name*  
