---
title: '&lt;new&gt;, fonctions'
ms.date: 11/04/2016
f1_keywords:
- new/std::nothrow
- new/std::set_new_handler
ms.assetid: e250f06a-b025-4509-ae7a-5356d56aad7d
ms.openlocfilehash: b5803b5fdf44392b6096f9c9a5ebdde7f94eae59
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50604020"
---
# <a name="ltnewgt-functions"></a>&lt;new&gt;, fonctions

|||
|-|-|
|[nothrow](#nothrow)|[set_new_handler](#set_new_handler)|

## <a name="nothrow"></a>  nothrow

Fournit un objet à utiliser en tant qu’argument pour le **nothrow** versions de **nouveau** et **supprimer**.

```cpp
extern const std::nothrow_t nothrow;
```

### <a name="remarks"></a>Notes

L’objet est utilisé comme argument de fonction pour correspondre au type de paramètre [std::nothrow_t](../standard-library/nothrow-t-structure.md).

### <a name="example"></a>Exemple

Pour obtenir des exemples d’utilisation de `std::nothrow_t` comme paramètre de fonction, consultez [new, opérateur](../standard-library/new-operators.md#op_new) et [new &#91;&#93;, opérateur](../standard-library/new-operators.md#op_new_arr).

## <a name="set_new_handler"></a>  set_new_handler

Installe une fonction de l’utilisateur qui doit être appelée lorsque **opérateur new** échoue dans sa tentative d’allocation de mémoire.

```cpp
new_handler set_new_handler(new_handler Pnew) throw();
```

### <a name="parameters"></a>Paramètres

*Pnew*<br/>
Le `new_handler` doit être installé.

### <a name="return-value"></a>Valeur de retour

0 lors du premier appel et `new_handler` précédent lors des appels ultérieurs.

### <a name="remarks"></a>Notes

La fonction stocke *Pnew* dans statique [nouveau gestionnaire](../standard-library/new-typedefs.md#new_handler) pointeur qu’il gère, puis retourne la valeur précédemment stockée dans le pointeur. Le nouveau gestionnaire est utilisé par [opérateur new](../standard-library/new-operators.md#op_new)(**size_t**).

### <a name="example"></a>Exemple

```cpp
// new_set_new_handler.cpp
// compile with: /EHsc
#include<new>
#include<iostream>

using namespace std;
void __cdecl newhandler( )
{
   cout << "The new_handler is called:" << endl;
   throw bad_alloc( );
   return;
}

int main( )
{
   set_new_handler (newhandler);
   try
   {
      while ( 1 )
      {
         new int[5000000];
         cout << "Allocating 5000000 ints." << endl;
      }
   }
   catch ( exception e )
   {
      cout << e.what( ) << endl;
   }
}
```

```Output
Allocating 5000000 ints.
Allocating 5000000 ints.
Allocating 5000000 ints.
Allocating 5000000 ints.
Allocating 5000000 ints.
Allocating 5000000 ints.
Allocating 5000000 ints.
Allocating 5000000 ints.
Allocating 5000000 ints.
Allocating 5000000 ints.
Allocating 5000000 ints.
Allocating 5000000 ints.
Allocating 5000000 ints.
Allocating 5000000 ints.
Allocating 5000000 ints.
Allocating 5000000 ints.
Allocating 5000000 ints.
Allocating 5000000 ints.
Allocating 5000000 ints.
Allocating 5000000 ints.
Allocating 5000000 ints.
Allocating 5000000 ints.
Allocating 5000000 ints.
Allocating 5000000 ints.
The new_handler is called:
bad allocation
```

## <a name="see-also"></a>Voir aussi

[\<new>](../standard-library/new.md)<br/>
