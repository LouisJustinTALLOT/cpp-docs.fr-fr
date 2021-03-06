---
description: 'En savoir plus sur : indices'
title: Indices
ms.date: 11/04/2016
helpviewer_keywords:
- subscript operator [C++], overloaded
- arrays [C++], subscripting
- subscripting [C++]
- operators [C++], overloading
- operator overloading [C++], examples
- subscript operator
ms.assetid: eb151281-6733-401d-9787-39ab6754c62c
ms.openlocfilehash: 77230045e66336e9989f49dd54557fa92d2ab001
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97178197"
---
# <a name="subscripting"></a>Indices

L’opérateur d’indice (**[]**), comme l’opérateur d’appel de fonction, est considéré comme un opérateur binaire. L’opérateur d’indice doit être une fonction membre non statique qui accepte un seul argument. Cet argument peut être de tout type et désigne l’indice de tableau souhaité.

## <a name="example"></a>Exemple

L’exemple suivant montre comment créer un vecteur de type **`int`** qui implémente la vérification des limites :

```cpp
// subscripting.cpp
// compile with: /EHsc
#include <iostream>

using namespace std;
class IntVector {
public:
   IntVector( int cElements );
   ~IntVector() { delete [] _iElements; }
   int& operator[](int nSubscript);
private:
   int *_iElements;
   int _iUpperBound;
};

// Construct an IntVector.
IntVector::IntVector( int cElements ) {
   _iElements = new int[cElements];
   _iUpperBound = cElements;
}

// Subscript operator for IntVector.
int& IntVector::operator[](int nSubscript) {
   static int iErr = -1;

   if( nSubscript >= 0 && nSubscript < _iUpperBound )
      return _iElements[nSubscript];
   else {
      clog << "Array bounds violation." << endl;
      return iErr;
   }
}

// Test the IntVector class.
int main() {
   IntVector v( 10 );
   int i;

   for( i = 0; i <= 10; ++i )
      v[i] = i;

   v[3] = v[9];

   for ( i = 0; i <= 10; ++i )
      cout << "Element: [" << i << "] = " << v[i] << endl;
}
```

```Output
Array bounds violation.
Element: [0] = 0
Element: [1] = 1
Element: [2] = 2
Element: [3] = 9
Element: [4] = 4
Element: [5] = 5
Element: [6] = 6
Element: [7] = 7
Element: [8] = 8
Element: [9] = 9
Array bounds violation.
Element: [10] = 10
```

## <a name="comments"></a>Commentaires

Lorsque `i` atteint 10 dans le programme précédent, **Operator []** détecte qu’un indice hors limites est utilisé et émet un message d’erreur.

Notez que la fonction **Operator []** retourne un type référence. Il s'agit par conséquent d'une l-value, ce qui vous permet d'utiliser des expressions indicées de chaque côté des opérateurs d'assignation.

## <a name="see-also"></a>Voir aussi

[Surcharge d’opérateur](../cpp/operator-overloading.md)
