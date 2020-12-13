---
description: 'En savoir plus sur : classe range_error'
title: range_error, classe
ms.date: 08/14/2018
f1_keywords:
- stdexcept/std::range_error
helpviewer_keywords:
- range_error class
ms.assetid: 8afb3e88-fc49-4213-b096-ed63d7aea37c
ms.openlocfilehash: c9d1ef328ba077b4b675d782df9c85d2db3a2072
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97337959"
---
# <a name="range_error-class"></a>range_error, classe

Classe qui sert de classe de base pour toutes les exceptions levées pour signaler une erreur de plage.

## <a name="syntax"></a>Syntaxe

```cpp
class range_error : public runtime_error {
public:
    explicit range_error(const string& message);
    explicit range_error(const char *message);
};
```

## <a name="remarks"></a>Notes

Valeur retournée par [ce qu'](../standard-library/exception-class.md) il s’agit d’une copie de `message.data` . Pour plus d’informations, consultez [basic_string ::d ATA](../standard-library/basic-string-class.md#data).

## <a name="example"></a>Exemple

```cpp
// range_error.cpp
// compile with: /EHsc /GR
#include <iostream>
using namespace std;
int main()
{
   try
   {
      throw range_error( "The range is in error!" );
   }
   catch (range_error &e)
   {
      cerr << "Caught: " << e.what( ) << endl;
      cerr << "Type: " << typeid( e ).name( ) << endl;
   };
}
/* Output:
Caught: The range is in error!
Type: class std::range_error
*/
```

## <a name="requirements"></a>Spécifications

**En-tête :**\<stdexcept>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[Classe runtime_error](../standard-library/runtime-error-class.md)\
[Sécurité des threads dans la bibliothèque C++ standard](../standard-library/thread-safety-in-the-cpp-standard-library.md)
