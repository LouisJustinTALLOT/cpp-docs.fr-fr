---
title: runtime_error, classe
ms.date: 11/04/2016
f1_keywords:
- stdexcept/std::runtime_error
helpviewer_keywords:
- runtime_error class
ms.assetid: 4d0227bf-847b-45a2-a320-2351ebf98368
ms.openlocfilehash: c4c4436c32f5f23c6bea119e95b165631384f583
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68451123"
---
# <a name="runtimeerror-class"></a>runtime_error, classe

Classe qui sert de classe de base pour toutes les exceptions levées pour signaler des erreurs normalement détectables uniquement durant l'exécution du programme.

## <a name="syntax"></a>Syntaxe

```cpp
class runtime_error : public exception {
public:
    explicit runtime_error(const string& message);

    explicit runtime_error(const char *message);

};
```

## <a name="remarks"></a>Notes

La valeur retournée par la [classe exception](../standard-library/exception-class.md) est une copie de **message**`.`[data](../standard-library/basic-string-class.md#data).

## <a name="example"></a>Exemple

```cpp
// runtime_error.cpp
// compile with: /EHsc /GR
#include <iostream>

using namespace std;

int main( )
{
// runtime_error
   try
   {
      locale loc( "test" );
   }
   catch ( exception &e )
   {
      cerr << "Caught " << e.what( ) << endl;
      cerr << "Type " << typeid( e ).name( ) << endl;
   };
}
/* Output:
Caught bad locale name
Type class std::runtime_error
*/
```

## <a name="requirements"></a>Configuration requise

**En-tête :** \<stdexcept>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[Classe d’exception](../standard-library/exception-class.md)\
[Sécurité des threads dans la bibliothèque standard C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
