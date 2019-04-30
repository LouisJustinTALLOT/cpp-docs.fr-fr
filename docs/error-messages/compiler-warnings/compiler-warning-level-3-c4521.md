---
title: Avertissement du compilateur (niveau 3) C4521
ms.date: 11/04/2016
f1_keywords:
- C4521
helpviewer_keywords:
- C4521
ms.assetid: 057d770c-ebcf-44cd-b943-1b1bb1ceaa8c
ms.openlocfilehash: 887526810f7e65280adcde422ef871a67ccdde1f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62401915"
---
# <a name="compiler-warning-level-3-c4521"></a>Avertissement du compilateur (niveau 3) C4521

'classe' : plusieurs constructeurs de copie spécifiés

La classe possède plusieurs constructeurs de copie d’un type unique. Cet avertissement est informatif ; les constructeurs peuvent être appelées dans votre programme.

Utilisez le [avertissement](../../preprocessor/warning.md) pragma pour supprimer cet avertissement.

## <a name="example"></a>Exemple

L’exemple suivant génère l’erreur C4521 :.

```
// C4521.cpp
// compile with: /EHsc /W3
#include <iostream>

using namespace std;
class A {
public:
   A() { cout << "A's default constructor" << endl; }
   A( A &o ) { cout << "A&" << endl; }
   A( const A &co ) { cout << "const A&" << endl; }   // C4521
};

int main() {
   A o1;         // Calls default constructor.
   A o2( o1 );   // Calls A( A& ).
   const A o3;   // Calls default constructor.
   A o4( o3 );   // Calls A( const A& ).
}
```