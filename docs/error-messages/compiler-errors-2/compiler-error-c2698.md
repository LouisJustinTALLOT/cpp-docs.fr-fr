---
description: 'En savoir plus sur : erreur du compilateur C2698'
title: Erreur du compilateur C2698
ms.date: 11/04/2016
f1_keywords:
- C2698
helpviewer_keywords:
- C2698
ms.assetid: 3ebfe395-c20b-4c56-9980-ca9ed8653382
ms.openlocfilehash: a787c43e7a885734f4c6a2d76aa16d51e19615c5
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97326628"
---
# <a name="compiler-error-c2698"></a>Erreur du compilateur C2698

la déclaration using pour’declaration 1 'ne peut pas coexister avec la déclaration using existante pour’declaration 2 '

Une fois que vous avez une [déclaration using](../../cpp/using-declaration.md) pour un membre de données, toute déclaration using dans la même portée qui utilise le même nom n’est pas autorisée, car seules les fonctions peuvent être surchargées.

L’exemple suivant génère l’C2698 :

```cpp
// C2698.cpp
struct A {
   int x;
};

struct B {
   int x;
};

struct C : A, B {
   using A::x;
   using B::x;   // C2698
}
```
