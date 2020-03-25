---
title: Avertissement du compilateur (niveau 1) C4733
ms.date: 11/04/2016
f1_keywords:
- C4733
helpviewer_keywords:
- C4733
ms.assetid: 7ef4f577-772d-4b66-a7bf-8958a6b250bc
ms.openlocfilehash: 39674c32deb506725aa5f7c1f5f875e771519938
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80185670"
---
# <a name="compiler-warning-level-1-c4733"></a>Avertissement du compilateur (niveau 1) C4733

Assignation de Inline asm à’FS : 0 ' : gestionnaire non inscrit en tant que gestionnaire sécurisé

Fonction modifiant la valeur sur FS : 0 l’ajout d’un nouveau gestionnaire d’exceptions peut ne pas fonctionner avec des exceptions sécurisées, car il est possible que le gestionnaire ne soit pas inscrit en tant que gestionnaire d’exceptions valide (consultez [/SAFESEH](../../build/reference/safeseh-image-has-safe-exception-handlers.md)).

Pour résoudre cet avertissement, supprimez le FS : 0 définition ou désactivez cet avertissement et utilisez [. SAFESEH](../../assembler/masm/dot-safeseh.md) pour spécifier les gestionnaires d’exceptions sécurisés.

L’exemple suivant génère l’C4733 :

```cpp
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
