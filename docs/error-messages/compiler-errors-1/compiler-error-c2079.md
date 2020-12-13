---
description: 'En savoir plus sur : erreur du compilateur C2079'
title: Erreur du compilateur C2079
ms.date: 11/04/2016
f1_keywords:
- C2079
helpviewer_keywords:
- C2079
ms.assetid: ca58d6d5-eccd-40b7-ba14-c003223c5bc7
ms.openlocfilehash: 73ca5d334ac3bf3157b61a1b2a9489282ae1fe00
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97151214"
---
# <a name="compiler-error-c2079"></a>Erreur du compilateur C2079

'identifier’utilise une classe/struct/union’name’non définie

L’identificateur spécifié est une classe, une structure ou une Union non définie.

Cette erreur peut être due à l’initialisation d’une Union anonyme.

L’exemple suivant génère l’C2079 :

```cpp
// C2079.cpp
// compile with: /EHsc
#include <iostream>
int main() {
   std::ifstream g;   // C2079
}
```

Solution possible :

```cpp
// C2079b.cpp
// compile with: /EHsc
#include <fstream>
int main( ) {
   std::ifstream g;
}
```

C2079 peut également se produire si vous tentez de déclarer un objet sur la pile d’un type dont la déclaration anticipée est uniquement dans la portée.

```cpp
// C2079c.cpp
class A;

class B {
   A a;   // C2079
};

class A {};
```

Solution possible :

```cpp
// C2079d.cpp
// compile with: /c
class A;
class C {};

class B {
   A * a;
   C c;
};

class A {};
```
