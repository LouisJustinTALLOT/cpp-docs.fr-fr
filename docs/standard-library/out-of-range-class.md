---
description: 'En savoir plus sur : classe out_of_range'
title: out_of_range, classe
ms.date: 11/04/2016
f1_keywords:
- stdexcept/std::out_of_range
helpviewer_keywords:
- out_of_range class
ms.assetid: d0e14dc0-065e-4666-9ac9-51e52223c503
ms.openlocfilehash: 28d0982f711dba8d7a7bb069c4ae79e267b902df
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97283275"
---
# <a name="out_of_range-class"></a>out_of_range, classe

Classe qui sert de classe de base pour toutes les exceptions levées pour signaler un argument qui est en dehors de sa plage valide.

## <a name="syntax"></a>Syntaxe

```cpp
class out_of_range : public logic_error {
public:
    explicit out_of_range(const string& message);

    explicit out_of_range(const char *message);

};
```

## <a name="remarks"></a>Notes

La valeur retournée par `what()` est une copie de `message.data()` . Pour plus d’informations, consultez [`what`](../standard-library/exception-class.md) et [`data`](../standard-library/basic-string-class.md#data).

## <a name="example"></a>Exemple

```cpp
// out_of_range.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

using namespace std;

int main() {
// out_of_range
   try {
      string str( "Micro" );
      string rstr( "soft" );
      str.append( rstr, 5, 3 );
      cout << str << endl;
   }
   catch ( exception &e ) {
      cerr << "Caught: " << e.what( ) << endl;
   };
}
```

## <a name="output"></a>Output

```cpp
Caught: invalid string position
```

## <a name="requirements"></a>Spécifications

**En-tête :**\<stdexcept>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[Classe logic_error](../standard-library/logic-error-class.md)\
[Sécurité des threads dans la bibliothèque C++ standard](../standard-library/thread-safety-in-the-cpp-standard-library.md)
