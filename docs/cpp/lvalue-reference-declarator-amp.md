---
title: 'Déclarateur de référence lvalue : &amp;'
ms.date: 11/04/2016
f1_keywords:
- '&'
helpviewer_keywords:
- reference operator
- '& operator [C++], reference operator'
ms.assetid: edf0513d-3dcc-4663-b276-1269795dda51
ms.openlocfilehash: 595f2b683d2abb4cdc8a328dc6e86338ab90f214
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80178065"
---
# <a name="lvalue-reference-declarator-amp"></a>Déclarateur de référence lvalue : &amp;

Contient l'adresse d'un objet mais se comporte syntaxiquement comme un objet.

## <a name="syntax"></a>Syntaxe

```
type-id & cast-expression
```

## <a name="remarks"></a>Notes

Vous pouvez considérer une référence lvalue comme un autre nom d'un objet. Une déclaration de référence lvalue se compose d'une liste facultative de spécificateurs suivie d'un déclarateur de référence. Une référence doit être initialisée et ne peut pas être modifiée.

Tout objet dont l'adresse peut être convertie en un type pointeur donné peut également être converti en type référence similaire. Par exemple, tout objet dont l'adresse peut être convertie en type `char *` peut également être converti en type `char &`.

Ne confondez pas les déclarations de référence avec l' [opérateur address-of](../cpp/address-of-operator-amp.md). Lorsque l' *identificateur* de `&`est précédé d’un type, tel que **int** ou **char**, l' *identificateur* est déclaré comme une référence au type. Lorsque `&`*identificateur* n’est pas précédé d’un type, l’utilisation est celle de l’opérateur d’adresse.

## <a name="example"></a>Exemple

L'exemple suivant illustre le déclarateur de référence en déclarant un objet `Person` et une référence à cet objet. `rFriend` étant une référence à `myFriend`, la mise à jour de l'une ou l'autre variable modifie le même objet.

```cpp
// reference_declarator.cpp
// compile with: /EHsc
// Demonstrates the reference declarator.
#include <iostream>
using namespace std;

struct Person
{
    char* Name;
    short Age;
};

int main()
{
   // Declare a Person object.
   Person myFriend;

   // Declare a reference to the Person object.
   Person& rFriend = myFriend;

   // Set the fields of the Person object.
   // Updating either variable changes the same object.
   myFriend.Name = "Bill";
   rFriend.Age = 40;

   // Print the fields of the Person object to the console.
   cout << rFriend.Name << " is " << myFriend.Age << endl;
}
```

```Output
Bill is 40
```

## <a name="see-also"></a>Voir aussi

[Informations de référence](../cpp/references-cpp.md)<br/>
[Arguments de fonction de type référence](../cpp/reference-type-function-arguments.md)<br/>
[Retours de fonction de type référence](../cpp/reference-type-function-returns.md)<br/>
[Références aux pointeurs](../cpp/references-to-pointers.md)
