---
title: Vue d’ensemble de l’assembleur inline | Microsoft Docs
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- inline assembler
- __asm keyword [C++], invoking inline assembler
- invoking inline assembler
- inline assembly, inline assembler
ms.assetid: d990331a-0e33-4760-8d7a-b720b0288335
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0e52316a5080ce7d64d34a09aa265ea561c186ed
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43681217"
---
# <a name="inline-assembler-overview"></a>Vue d'ensemble de l'assembleur inline

**Section spécifique à Microsoft**

L'assembleur inline vous permet d'incorporer des instructions en langage assembleur dans vos programmes sources C et C++ sans code assembleur ni étapes de liaison supplémentaires. L'assembleur inline est intégré au compilateur. Vous n'avez pas besoin d'assembleur distinct tel que MASM (Microsoft Macro Assembler).

Étant donné que l'assembleur inline n'a pas besoin de code assembleur ni d'étapes de liaison distinctes, il est plus pratique qu'un assembleur distinct. Le code assembleur inline peut utiliser tout nom de fonction ou variable C ou C++ qui est dans la portée. Il est par conséquent facile de l'intégrer au code C et C++ de votre programme. En outre, le code assembleur pouvant être combiné avec des instructions C et C++, il peut exécuter des tâches lourdes ou impossibles en C ou C++ seul.

Le [__asm](../../assembler/inline/asm.md) mot clé appelle l’assembleur inline et peut apparaître partout où une instruction C ou C++ est conforme. Il ne peut pas apparaître de lui-même. Il doit être suivi par une instruction assembleur, un groupe d'instructions entre accolades ou, au minimum, par une paire d'accolades vide. Le terme « bloc `__asm`  » fait ici référence à une instruction ou un groupe d'instructions, que ce dernier soit ou non entouré d'accolades.

Le code suivant est un bloc `__asm` simple entre accolades. (Le code est une séquence de prologue de fonction personnalisée.)

```cpp
// asm_overview.cpp
// processor: x86
void __declspec(naked) main()
{
    // Naked functions must provide their own prolog...
    __asm {
        push ebp
        mov ebp, esp
        sub esp, __LOCAL_SIZE
    }

    // ... and epilog
    __asm {
        pop ebp
        ret
    }
}
```

Vous pouvez aussi placer `__asm` devant chaque instruction assembleur :

```cpp
__asm push ebp
__asm mov  ebp, esp
__asm sub  esp, __LOCAL_SIZE
```

Dans la mesure où le mot clé `__asm` est un séparateur d'instruction, vous pouvez également placer des instructions assembleur sur la même ligne :

```cpp
__asm push ebp   __asm mov  ebp, esp   __asm sub  esp, __LOCAL_SIZE
```

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Assembleur inline](../../assembler/inline/inline-assembler.md)<br/>