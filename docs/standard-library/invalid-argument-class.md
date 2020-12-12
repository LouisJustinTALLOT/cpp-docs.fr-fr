---
description: 'En savoir plus sur : classe invalid_argument'
title: invalid_argument, classe
ms.date: 11/04/2016
f1_keywords:
- stdexcept/std::invalid_argument
helpviewer_keywords:
- invalid_argument class
ms.assetid: af6c227d-ad7c-4e63-9dee-67af81d83506
ms.openlocfilehash: 58eee3a5e56932bcd045a7e66e59e105b8921813
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97323941"
---
# <a name="invalid_argument-class"></a>invalid_argument, classe

Classe qui sert de classe de base pour toutes les exceptions levées pour signaler un argument non valide.

## <a name="syntax"></a>Syntaxe

```cpp
class invalid_argument : public logic_error {
public:
    explicit invalid_argument(const string& message);

    explicit invalid_argument(const char *message);

};
```

## <a name="remarks"></a>Notes

La valeur retournée par `what()` est une copie de `message.data()` . Pour plus d’informations, consultez [`what`](../standard-library/exception-class.md) et [`data`](../standard-library/basic-string-class.md#data).

## <a name="example"></a>Exemple

```cpp
// invalid_arg.cpp
// compile with: /EHsc /GR
#include <bitset>
#include <iostream>

using namespace std;

int main( )
{
   try
   {
      bitset< 32 > bitset( string( "11001010101100001b100101010110000") );
   }
   catch ( exception &e )
   {
      cerr << "Caught " << e.what( ) << endl;
      cerr << "Type " << typeid( e ).name( ) << endl;
   };
}
/* Output:
Caught invalid bitset<N> char
Type class std::invalid_argument
*/
```

## <a name="requirements"></a>Spécifications

**En-tête :**\<stdexcept>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[Classe logic_error](../standard-library/logic-error-class.md)\
[Sécurité des threads dans la bibliothèque C++ standard](../standard-library/thread-safety-in-the-cpp-standard-library.md)
