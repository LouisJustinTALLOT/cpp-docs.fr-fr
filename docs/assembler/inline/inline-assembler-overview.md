---
title: Vue d'ensemble de l'assembleur inline
ms.date: 08/30/2018
helpviewer_keywords:
- inline assembler
- __asm keyword [C++], invoking inline assembler
- invoking inline assembler
- inline assembly, inline assembler
ms.assetid: d990331a-0e33-4760-8d7a-b720b0288335
ms.openlocfilehash: 3872dcb194146bf0f4c89b0be03a49b5fe3a9e37
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87192078"
---
# <a name="inline-assembler-overview"></a>Vue d'ensemble de l'assembleur inline

**Spécifique à Microsoft**

L'assembleur inline vous permet d'incorporer des instructions en langage assembleur dans vos programmes sources C et C++ sans code assembleur ni étapes de liaison supplémentaires. L'assembleur inline est intégré au compilateur. Vous n'avez pas besoin d'assembleur distinct tel que MASM (Microsoft Macro Assembler).

Étant donné que l'assembleur inline n'a pas besoin de code assembleur ni d'étapes de liaison distinctes, il est plus pratique qu'un assembleur distinct. Le code assembleur inline peut utiliser tout nom de fonction ou variable C ou C++ qui est dans la portée. Il est par conséquent facile de l'intégrer au code C et C++ de votre programme. En outre, le code assembleur pouvant être combiné avec des instructions C et C++, il peut exécuter des tâches lourdes ou impossibles en C ou C++ seul.

Le mot clé [__asm](../../assembler/inline/asm.md) appelle l’assembleur inline et peut apparaître partout où une instruction C ou C++ est légale. Il ne peut pas apparaître de lui-même. Il doit être suivi par une instruction assembleur, un groupe d'instructions entre accolades ou, au minimum, par une paire d'accolades vide. Ici, le terme « **`__asm`** bloc » fait référence à toute instruction ou à tout groupe d’instructions, qu’elles soient ou non placées entre accolades.

Le code suivant est un **`__asm`** bloc simple entre accolades. (Le code est une séquence de prologue de fonction personnalisée.)

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

Vous pouvez également placer **`__asm`** devant chaque instruction d’assembly :

```cpp
__asm push ebp
__asm mov  ebp, esp
__asm sub  esp, __LOCAL_SIZE
```

Étant donné que le **`__asm`** mot clé est un séparateur d’instruction, vous pouvez également placer des instructions d’assembly sur la même ligne :

```cpp
__asm push ebp   __asm mov  ebp, esp   __asm sub  esp, __LOCAL_SIZE
```

**FIN spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Assembleur inline](../../assembler/inline/inline-assembler.md)<br/>
