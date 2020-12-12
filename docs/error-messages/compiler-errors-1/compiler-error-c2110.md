---
description: 'En savoir plus sur : erreur du compilateur C2110'
title: Erreur du compilateur C2110
ms.date: 11/04/2016
f1_keywords:
- C2110
helpviewer_keywords:
- C2110
ms.assetid: 48fd76ed-90d6-4a60-9c7b-f6ce9355b4ca
ms.openlocfilehash: 76bb05ceda7eaae6887e4bfd82ee7d1917598f12
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97278491"
---
# <a name="compiler-error-c2110"></a>Erreur du compilateur C2110

'+' : impossible d’ajouter deux pointeurs

L’utilisateur a tenté d’ajouter deux valeurs de pointeur avec l’opérateur `+` (signe plus).

L’exemple suivant génère l’erreur C2110 :

```cpp
// C2110.cpp
int main() {
   int a = 0;
   int *pa;
   int *pb;
   a = pa + pb;   // C2110
}
```
