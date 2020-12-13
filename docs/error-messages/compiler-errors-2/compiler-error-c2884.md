---
description: 'En savoir plus sur : erreur du compilateur C2884'
title: Erreur du compilateur C2884
ms.date: 11/04/2016
f1_keywords:
- C2884
helpviewer_keywords:
- C2884
ms.assetid: 8b4d43e3-3fb5-4360-86c8-de59d8736d4f
ms.openlocfilehash: 008c72ba24bdea260fffc4a49145ecf67c610b15
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97332326"
---
# <a name="compiler-error-c2884"></a>Erreur du compilateur C2884

'name' : introduit par des conflits de déclaration using avec la fonction locale’Function'

Vous avez essayé de définir une fonction plusieurs fois. La première définition est une définition locale. La seconde provient d’un espace de noms avec une **`using`** déclaration.

L’exemple suivant génère l’C2884 :

```cpp
// C2884.cpp
namespace A {
   void z(int);
}

void f() {
   void z(int);
   using A::z;   // C2884 z is already defined
}
```
