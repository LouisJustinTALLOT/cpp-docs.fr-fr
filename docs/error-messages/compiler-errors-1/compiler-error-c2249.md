---
title: Erreur du compilateur C2249
ms.date: 11/04/2016
f1_keywords:
- C2249
helpviewer_keywords:
- C2249
ms.assetid: bdd6697c-e04b-49b9-8e40-d9eb6d74f2b6
ms.openlocfilehash: ac396fe5fa3505311f5a45ebb49dae283e35248c
ms.sourcegitcommit: 72161bcd21d1ad9cc3f12261aa84a5b026884afa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2020
ms.locfileid: "90741410"
---
# <a name="compiler-error-c2249"></a>Erreur du compilateur C2249

'membre' : aucun chemin d’accès accessible au membre d’accès déclaré dans la base virtuelle’classe'

`member`Est hérité d’une **`virtual`** structure ou classe de base non publique.

## <a name="examples"></a>Exemples

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

C2249 peut également se produire si vous essayez d’assigner un flux de la bibliothèque C++ standard à un autre flux.  L’exemple suivant génère l’C2249.

```cpp
// C2249_2.cpp
#include <iostream>
using namespace std;
int main() {
   cout = cerr;   // C2249
   #define cout cerr;   // OK
}
```
