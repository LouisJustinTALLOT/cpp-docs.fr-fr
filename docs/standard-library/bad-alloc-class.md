---
title: bad_alloc, classe
ms.date: 11/04/2016
f1_keywords:
- new/std::bad_alloc
helpviewer_keywords:
- bad_alloc class
ms.assetid: 6429a8e6-5a49-4907-8d56-f4a4ec8131d0
ms.openlocfilehash: 63b474d0209a5cc385de9dc11b56d5de8382a9cf
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62376417"
---
# <a name="badalloc-class"></a>bad_alloc, classe

La classe décrit une exception levée pour indiquer qu'une demande d'allocation n'a pas réussi.

## <a name="syntax"></a>Syntaxe

```cpp
class bad_alloc : public exception {
    bad_alloc();
virtual ~bad_alloc();

};
```

## <a name="remarks"></a>Notes

La valeur retournée par `what` est une chaîne C définie par l’implémentation. Aucune des fonctions membres ne lève d'exception.

## <a name="requirements"></a>Configuration requise

**En-tête :** \<new>

**Espace de noms :** std

## <a name="example"></a>Exemple

```cpp
// bad_alloc.cpp
// compile with: /EHsc
#include<new>
#include<iostream>
using namespace std;

int main() {
   char* ptr;
   try {
      ptr = new char[(~unsigned int((int)0)/2) - 1];
      delete[] ptr;
   }
   catch( bad_alloc &ba) {
      cout << ba.what( ) << endl;
   }
}
```

## <a name="sample-output"></a>Résultat de l'exemple

```Output
bad allocation
```

## <a name="requirements"></a>Configuration requise

**En-tête :** \<new>

## <a name="see-also"></a>Voir aussi

[exception, classe](../standard-library/exception-class.md)<br/>
[Sécurité des threads dans la bibliothèque standard C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
