---
description: 'En savoir plus sur : erreur du compilateur C2184'
title: Erreur du compilateur C2184
ms.date: 11/04/2016
f1_keywords:
- C2184
helpviewer_keywords:
- C2184
ms.assetid: 80fc8bff-7d76-4bde-94d2-01d84bb6824a
ms.openlocfilehash: 26513ff4162023398336eae3396e7be6abb8f8a6
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97335147"
---
# <a name="compiler-error-c2184"></a>Erreur du compilateur C2184

'type' : type interdit pour l’expression __except, il doit s’agir d’un type intégral

Un type a été utilisé dans une instruction [__except](../../c-language/try-except-statement-c.md) , mais ce type n’est pas autorisé.

L’exemple suivant génère l’erreur C2184 :

```cpp
// C2184.cpp
void f() {
   int * p;
   __try{}
   __except(p){};   // C2184
}
```

Solution possible :

```cpp
// C2184b.cpp
// compile with: /c
void f() {
   int i = 0;
   __try{}
   __except(i){};
}
```
