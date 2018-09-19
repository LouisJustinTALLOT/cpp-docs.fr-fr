---
title: Compilateur avertissement (niveau 1) C4733 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4733
dev_langs:
- C++
helpviewer_keywords:
- C4733
ms.assetid: 7ef4f577-772d-4b66-a7bf-8958a6b250bc
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 75b4aac2d71267b4ba012384fe83f167f44ec2d2
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46092932"
---
# <a name="compiler-warning-level-1-c4733"></a>Avertissement du compilateur (niveau 1) C4733

Affectation de inline asm à 'FS : 0' : gestionnaire non inscrit en tant que gestionnaire safe

Une fonction de modification de la valeur en FS : 0 pour ajouter un nouveau gestionnaire d’exceptions peut ne pas fonctionne avec les Exceptions sécurisées, car le gestionnaire ne peut pas être inscrit en tant que gestionnaire d’exceptions valide (consultez [/SAFESEH](../../build/reference/safeseh-image-has-safe-exception-handlers.md)).

Pour résoudre cet avertissement, supprimez la définition FS : 0 ou désactivez cette avertissement et utilisez [. SAFESEH](../../assembler/masm/dot-safeseh.md) pour spécifier les gestionnaires d’exceptions sécurisés.

L’exemple suivant génère l’erreur C4733 :

```
// C4733.cpp
// compile with: /W1 /c
// processor: x86
#include "stdlib.h"
#include "stdio.h"
void my_handler()
{
   printf("Hello from my_handler\n");
   exit(1);
}

int main()
{
   _asm {
      push    my_handler
      mov     eax, DWORD PTR fs:0
      push    eax
      mov     DWORD PTR fs:0, esp   // C4733
   }

   *(int*)0 = 0;
}
```