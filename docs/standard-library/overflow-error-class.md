---
title: overflow_error, classe
ms.date: 11/04/2016
f1_keywords:
- stdexcept/std::overflow_error
helpviewer_keywords:
- overflow_error class
ms.assetid: bae7128d-e36b-4a45-84f1-2f89da441d20
ms.openlocfilehash: 33819d9f57c9ee29b82c24d7919f68a97e50d98e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50583532"
---
# <a name="overflowerror-class"></a>overflow_error, classe

Classe qui sert de classe de base pour toutes les exceptions levées pour signaler un dépassement de capacité arithmétique positif.

## <a name="syntax"></a>Syntaxe

```cpp
class overflow_error : public runtime_error {
public:
    explicit overflow_error(const string& message);

    explicit overflow_error(const char *message);

};
```

## <a name="remarks"></a>Notes

La valeur retournée par [what](../standard-library/exception-class.md) est une copie de **message**`.`[data](../standard-library/basic-string-class.md#data).

## <a name="example"></a>Exemple

```cpp
// overflow_error.cpp
// compile with: /EHsc /GR
#include <bitset>
#include <iostream>

using namespace std;

int main( )
{
   try
   {
      bitset< 33 > bitset;
      bitset[32] = 1;
      bitset[0] = 1;
      unsigned long x = bitset.to_ulong( );
   }
   catch ( exception &e )
   {
      cerr << "Caught " << e.what( ) << endl;
      cerr << "Type " << typeid( e ).name( ) << endl;
   };
}
/* Output:
Caught bitset<N> overflow
Type class std::overflow_error
*/
```

## <a name="requirements"></a>Configuration requise

**En-tête :** \<stdexcept>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[runtime_error, classe](../standard-library/runtime-error-class.md)<br/>
[Sécurité des threads dans la bibliothèque standard C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
