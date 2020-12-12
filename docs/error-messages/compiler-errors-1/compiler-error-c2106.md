---
description: 'En savoir plus sur : erreur du compilateur C2106'
title: Erreur du compilateur C2106
ms.date: 11/04/2016
f1_keywords:
- C2106
helpviewer_keywords:
- C2106
ms.assetid: d5c91a2e-04e4-4770-8478-788b98c52a53
ms.openlocfilehash: edcd926763fc76fba0329ccc22b4d263b5042f4e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97170150"
---
# <a name="compiler-error-c2106"></a>Erreur du compilateur C2106

'operator' : l’opérande gauche doit être une l-value

L’opérateur doit avoir une l-value comme opérande gauche.

L’exemple suivant génère l’C2106 :

```cpp
// C2106.cpp
int main() {
   int a;
   1 = a;   // C2106
   a = 1;   // OK
}
```
