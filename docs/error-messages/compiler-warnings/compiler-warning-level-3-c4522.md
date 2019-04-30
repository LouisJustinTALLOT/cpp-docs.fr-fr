---
title: Avertissement du compilateur (niveau 3) C4522
ms.date: 11/04/2016
f1_keywords:
- C4522
helpviewer_keywords:
- C4522
ms.assetid: 7065dc27-0b6c-4e68-a345-c51cdb99a20b
ms.openlocfilehash: de163f0a3925b711f2f3437b700f75bbe994b3e7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62401902"
---
# <a name="compiler-warning-level-3-c4522"></a>Avertissement du compilateur (niveau 3) C4522

'classe' : plusieurs opérateurs d’assignation spécifiés

La classe a plusieurs opérateurs d’assignation d’un type unique. Cet avertissement est informatif ; les constructeurs peuvent être appelées dans votre programme.

Utilisez le [avertissement](../../preprocessor/warning.md) pragma pour supprimer cet avertissement.

## <a name="example"></a>Exemple

L’exemple suivant génère l’erreur C4522 :.

```
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