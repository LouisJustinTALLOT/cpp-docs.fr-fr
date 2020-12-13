---
description: 'En savoir plus sur : erreur du compilateur C2486'
title: Erreur du compilateur C2486
ms.date: 11/04/2016
f1_keywords:
- C2486
helpviewer_keywords:
- C2486
ms.assetid: 436da349-6461-4e32-bfca-4f3e620108e2
ms.openlocfilehash: c45e0bdb0f515743694fe372bea3afdb24e00177
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97339356"
---
# <a name="compiler-error-c2486"></a>Erreur du compilateur C2486

' __LOCAL_SIZE’uniquement autorisé dans une fonction avec l’attribut’Naked'

Dans les fonctions d’assembly inline, le nom `__LOCAL_SIZE` est réservé pour les fonctions déclarées avec l’attribut [Naked](../../cpp/naked-cpp.md) .

L’exemple suivant génère l’C2486 :

```cpp
// C2486.cpp
// processor: x86
void __declspec(naked) f1() {
   __asm {
      mov   eax,   __LOCAL_SIZE
   }
}
void f2() {
   __asm {
      mov   eax,   __LOCAL_SIZE   // C2486
   }
}
```
