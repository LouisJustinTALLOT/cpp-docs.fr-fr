---
description: 'En savoir plus sur : avertissement du compilateur (niveau 3) C4522'
title: Avertissement du compilateur (niveau 3) C4522
ms.date: 11/04/2016
f1_keywords:
- C4522
helpviewer_keywords:
- C4522
ms.assetid: 7065dc27-0b6c-4e68-a345-c51cdb99a20b
ms.openlocfilehash: 8663bf6ea70edd6612fd3d124989f6e657185947
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97257964"
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
