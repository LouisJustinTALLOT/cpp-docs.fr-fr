---
description: 'En savoir plus sur : erreur du compilateur C2831'
title: Erreur du compilateur C2831
ms.date: 11/04/2016
f1_keywords:
- C2831
helpviewer_keywords:
- C2831
ms.assetid: c8c04288-0889-4265-a077-17f94cbcdcc9
ms.openlocfilehash: 65fece68763e38de8c5047c66327e0615865fa9b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97194499"
---
# <a name="compiler-error-c2831"></a>Erreur du compilateur C2831

'operator opérateur’ne peut pas avoir de paramètres par défaut

Seuls trois opérateurs peuvent avoir des paramètres par défaut :

- [nouveau](../../cpp/new-operator-cpp.md)

- Attribution =

- Parenthèse ouvrante (

L’exemple suivant génère l’C2831 :

```cpp
// C2831.cpp
// compile with: /c
#define BINOP <=
class A {
public:
   int i;
   int operator BINOP(int x = 1) {   // C2831
   // try the following line instead
   // int operator BINOP(int x) {
      return i+x;
   }
};
```
