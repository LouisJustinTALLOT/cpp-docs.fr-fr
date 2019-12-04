---
title: Erreur du compilateur C2249
ms.date: 11/04/2016
f1_keywords:
- C2249
helpviewer_keywords:
- C2249
ms.assetid: bdd6697c-e04b-49b9-8e40-d9eb6d74f2b6
ms.openlocfilehash: 24db84c9205173f098e493c4ea6393fb96592276
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74758890"
---
# <a name="compiler-error-c2249"></a>Erreur du compilateur C2249

'membre' : aucun chemin d’accès accessible au membre d’accès déclaré dans la base virtuelle’classe'

La `member` est héritée d’une classe ou d’une structure de base `virtual` non publique.

## <a name="example"></a>Exemple

L’exemple suivant génère l’C2249.

```cpp
// C2249.cpp
class A {
private:
   void privFunc( void ) {};
public:
   void pubFunc( void ) {};
};

class B : virtual public A {} b;

int main() {
   b.privFunc();    // C2249, private member of A
   b.pubFunc();    // OK
}
```

## <a name="example"></a>Exemple

C2249 peut également se produire si vous essayez d’assigner un C++ flux de la bibliothèque standard à un autre flux.  L’exemple suivant génère l’C2249.

```cpp
// C2249_2.cpp
#include <iostream>
using namespace std;
int main() {
   cout = cerr;   // C2249
   #define cout cerr;   // OK
}
```
