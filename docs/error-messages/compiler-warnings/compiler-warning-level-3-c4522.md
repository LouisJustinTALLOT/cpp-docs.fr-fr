---
title: Avertissement du compilateur (niveau 3) C4522
ms.date: 11/04/2016
f1_keywords:
- C4522
helpviewer_keywords:
- C4522
ms.assetid: 7065dc27-0b6c-4e68-a345-c51cdb99a20b
ms.openlocfilehash: 84f4785c670c4cc5c167c18b9f15c2417b61df34
ms.sourcegitcommit: 217fac22604639ebd62d366a69e6071ad5b724ac
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/19/2019
ms.locfileid: "74188970"
---
# <a name="compiler-warning-level-3-c4522"></a>Avertissement du compilateur (niveau 3) C4522

'classe' : plusieurs opérateurs d’assignation spécifiés

La classe a plusieurs opérateurs d’assignation d’un même type. Cet avertissement est informatif. les constructeurs peuvent être appelés dans votre programme.

Utilisez le pragma [Warning](../../preprocessor/warning.md) pour supprimer cet avertissement.

## <a name="example"></a>Exemple

L’exemple suivant génère l’C4522.

```cpp
// C4522.cpp
// compile with: /EHsc /W3
#include <iostream>

using namespace std;
class A {
public:
   A& operator=( A & o ) { cout << "A&" << endl; return *this; }
   A& operator=( const A &co ) { cout << "const A&" << endl; return *this; }   // C4522
};

int main() {
   A o1, o2;
   o2 = o1;
   const A o3;
   o1 = o3;
}
```