---
title: Erreur du compilateur C2079
ms.date: 11/04/2016
f1_keywords:
- C2079
helpviewer_keywords:
- C2079
ms.assetid: ca58d6d5-eccd-40b7-ba14-c003223c5bc7
ms.openlocfilehash: 68435610680e3b21415a1d9439a8133fd1e2557f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62391957"
---
# <a name="compiler-error-c2079"></a>Erreur du compilateur C2079

'identificateur' utilise la classe/struct/union non défini 'name'

L’identificateur spécifié est une classe non définie, une structure ou une union.

Cette erreur peut résulter de l’initialisation d’une union anonyme.

L’exemple suivant génère l’erreur C2079 :

```
// C2079.cpp
// compile with: /EHsc
#include <iostream>
int main() {
   std::ifstream g;   // C2079
}
```

Solution possible :

```
// C2079b.cpp
// compile with: /EHsc
#include <fstream>
int main( ) {
   std::ifstream g;
}
```

C2079 peut également se produire si vous tentez de déclarer un objet sur la pile d’un type dont la déclaration anticipée est uniquement dans la portée.

```
// C2079c.cpp
class A;

class B {
   A a;   // C2079
};

class A {};
```

Solution possible :

```
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