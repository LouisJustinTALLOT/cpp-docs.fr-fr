---
title: Avertissement du compilateur (niveau 1) C4311
ms.date: 11/04/2016
f1_keywords:
- C4311
helpviewer_keywords:
- C4311
ms.assetid: ddc579d0-d051-47bc-915d-71ffb32323c9
ms.openlocfilehash: 6e44dafb6675882a1a62fba5144f85120378421d
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69510057"
---
# <a name="compiler-warning-level-1-c4311"></a>Avertissement du compilateur (niveau 1) C4311

'variable' : troncation de pointeur de 'type' à 'type'

Cet avertissement détecte les problèmes de troncation de pointeur 64 bits. Par exemple, si le code est compilé pour une architecture 64 bits, la valeur d'un pointeur (64 bits) est tronquée si elle est affectée à un `int` (32 bits). Pour plus d’informations, consultez [règles d’utilisation des pointeurs](/windows/win32/WinProg64/rules-for-using-pointers).

Pour plus d’informations sur les causes courantes des C4311 d’avertissement, consultez [Erreurs de compilateur courantes](/windows/win32/WinProg64/common-compiler-errors).

L'exemple de code suivant génère l'avertissement C4311 quand il est compilé pour une cible 64 bits, puis indique comment le corriger :

```
// C4311.cpp
// compile by using: cl /W1 C4311.cpp
int main() {
   void* p = &p;
   unsigned int i = (unsigned int) p;   // C4311 for 64-bit targets
   unsigned long long j = (unsigned long long) p;   // OK
}
```