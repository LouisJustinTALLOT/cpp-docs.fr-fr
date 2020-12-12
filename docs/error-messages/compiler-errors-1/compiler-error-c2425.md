---
description: 'En savoir plus sur : erreur du compilateur C2425'
title: Erreur du compilateur C2425
ms.date: 11/04/2016
f1_keywords:
- C2425
helpviewer_keywords:
- C2425
ms.assetid: 0ce59404-9aff-4e01-aa8d-27d23e92eb30
ms.openlocfilehash: 03e3ca02e0ceff70135ce14ee982d2d5a0009982
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97190222"
---
# <a name="compiler-error-c2425"></a>Erreur du compilateur C2425

'jeton' : expression non constante dans 'contexte'

Le jeton fait partie d'une expression non constante dans ce contexte.

Pour résoudre ce problème, remplacez le jeton par une constante littérale ou un calcul.

L'exemple suivant génère l'erreur C2425 :

```cpp
// C2425.cpp
// processor: x86
int main() {
   int i = 3;
   __asm {
      mov eax, [ebp - i]   // C2425
      mov eax, [ebp - 3]   // OK
   }
}
```
