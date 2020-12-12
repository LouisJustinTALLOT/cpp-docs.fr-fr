---
description: 'En savoir plus sur : assembleur inline (C)'
title: Assembleur inline (C)
ms.date: 11/04/2016
helpviewer_keywords:
- __asm keyword [C]
- inline assembler [C]
ms.assetid: 821acc77-60b1-434c-ba54-2ba930a25ab4
ms.openlocfilehash: 8c5dc8ecc713968786b05eca6ab38e4752ea48c4
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97181850"
---
# <a name="inline-assembler-c"></a>Assembleur inline (C)

**Spécifique à Microsoft**

L'assembleur inline vous permet d'incorporer des instructions en langage assembleur directement dans vos programmes sources C sans code assembleur ni étapes de liaison supplémentaires. L'assembleur inline est intégré au compilateur. Vous n'avez pas besoin d'assembleur distinct tel que MASM (Microsoft Macro Assembler).

Étant donné que l'assembleur inline n'a pas besoin de code assembleur ni d'étapes de liaison distinctes, il est plus pratique qu'un assembleur distinct. Le code assembleur inline peut utiliser tout nom de fonction ou variable C qui est dans la portée. Il est par conséquent facile de l'intégrer au code C de votre programme. En outre, le code assembleur pouvant être combiné avec des instructions C, il peut exécuter des tâches lourdes ou impossibles en C seul.

Le **`__asm`** mot clé appelle l’assembleur inline et peut apparaître partout où une instruction C est légale. Il ne peut pas apparaître de lui-même. Il doit être suivi par une instruction assembleur, un groupe d'instructions entre accolades ou, au minimum, par une paire d'accolades vide. Ici, le terme « **`__asm`** bloc » fait référence à toute instruction ou à tout groupe d’instructions, qu’elles soient ou non placées entre accolades.

Le code ci-dessous est un **`__asm`** bloc simple entre accolades. (Le code est une séquence de prologue de fonction personnalisée.)

```
__asm
{
   push ebp
   mov  ebp, esp
   sub  esp, __LOCAL_SIZE
}
```

Vous pouvez également placer **`__asm`** devant chaque instruction d’assembly :

```
__asm push ebp
__asm mov  ebp, esp
__asm sub  esp, __LOCAL_SIZE
```

Étant donné que le **`__asm`** mot clé est un séparateur d’instruction, vous pouvez également placer des instructions d’assembly sur la même ligne :

```
__asm push ebp   __asm mov  ebp, esp   __asm sub  esp, __LOCAL_SIZE
```

**FIN spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Attributs de fonction](../c-language/function-attributes.md)
