---
description: 'En savoir plus sur : classe logic_error'
title: logic_error, classe
ms.date: 11/04/2016
f1_keywords:
- stdexcept/std::logic_error
helpviewer_keywords:
- logic_error class
ms.assetid: b290d73d-94e1-4288-af86-2bb5d71f677a
ms.openlocfilehash: b4b592d268a29a1bf1c095beb79904789d695e64
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97277711"
---
# <a name="logic_error-class"></a>logic_error, classe

Classe qui sert de classe de base pour toutes les exceptions levées pour signaler des erreurs normalement détectables avant l'exécution du programme, telles que les violations de conditions préalables logiques.

## <a name="syntax"></a>Syntaxe

```cpp
class logic_error : public exception {
public:
    explicit logic_error(const string& message);

    explicit logic_error(const char *message);

};
```

## <a name="remarks"></a>Notes

La valeur retournée par `what()` est une copie de `message.data()` . Pour plus d’informations, consultez [`what`](../standard-library/exception-class.md) et [`data`](../standard-library/basic-string-class.md#data).

## <a name="example"></a>Exemple

```cpp
// logic_error.cpp
// compile with: /EHsc /GR
#include <iostream>
using namespace std;

int main( )
{
   try
   {
      throw logic_error( "logic error" );
   }
   catch ( exception &e )
   {
      cerr << "Caught: " << e.what( ) << endl;
      cerr << "Type: " << typeid( e ).name( ) << endl;
   };
}
```

```Output
Caught: logic error
Type: class std::logic_error
```

## <a name="requirements"></a>Spécifications

**En-tête :**\<stdexcept>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[Classe d’exception](../standard-library/exception-class.md)\
[Sécurité des threads dans la bibliothèque C++ standard](../standard-library/thread-safety-in-the-cpp-standard-library.md)
