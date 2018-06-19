---
title: Assembleur inline (C) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- __asm keyword [C]
- inline assembler [C]
ms.assetid: 821acc77-60b1-434c-ba54-2ba930a25ab4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5bf99606601b86c6a328e9547515b3518cef4ffe
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32384318"
---
# <a name="inline-assembler-c"></a>Assembleur inline (C)
**Section spécifique à Microsoft**  
  
 L'assembleur inline vous permet d'incorporer des instructions en langage assembleur directement dans vos programmes sources C sans code assembleur ni étapes de liaison supplémentaires. L'assembleur inline est intégré au compilateur. Vous n'avez pas besoin d'assembleur distinct tel que MASM (Microsoft Macro Assembler).  
  
 Étant donné que l'assembleur inline n'a pas besoin de code assembleur ni d'étapes de liaison distinctes, il est plus pratique qu'un assembleur distinct. Le code assembleur inline peut utiliser tout nom de fonction ou variable C qui est dans la portée. Il est par conséquent facile de l'intégrer au code C de votre programme. En outre, le code assembleur pouvant être combiné avec des instructions C, il peut exécuter des tâches lourdes ou impossibles en C seul.  
  
 Le mot clé `__asm` appelle l'assembleur inline et peut apparaître partout où une instruction C est conforme. Il ne peut pas apparaître de lui-même. Il doit être suivi par une instruction assembleur, un groupe d'instructions entre accolades ou, au minimum, par une paire d'accolades vide. Le terme « bloc `__asm`  » fait ici référence à une instruction ou un groupe d'instructions, que ce dernier soit ou non entouré d'accolades.  
  
 Le code ci-dessous est un bloc `__asm` simple entre accolades. (Le code est une séquence de prologue de fonction personnalisée.)  
  
```  
__asm  
{  
   push ebp  
   mov  ebp, esp  
   sub  esp, __LOCAL_SIZE  
}  
```  
  
 Vous pouvez aussi placer `__asm` devant chaque instruction assembleur :  
  
```  
__asm push ebp  
__asm mov  ebp, esp  
__asm sub  esp, __LOCAL_SIZE  
```  
  
 Dans la mesure où le mot clé `__asm` est un séparateur d'instruction, vous pouvez également placer des instructions assembleur sur la même ligne :  
  
```  
__asm push ebp   __asm mov  ebp, esp   __asm sub  esp, __LOCAL_SIZE   
```  
  
 **FIN de la section spécifique à Microsoft**  
  
## <a name="see-also"></a>Voir aussi  
 [Attributs de fonctions](../c-language/function-attributes.md)