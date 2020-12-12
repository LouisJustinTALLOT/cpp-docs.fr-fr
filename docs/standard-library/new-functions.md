---
description: 'En savoir plus sur : &lt; nouvelles &gt; fonctions'
title: '&lt;new&gt;, fonctions'
ms.date: 11/04/2016
f1_keywords:
- new/std::get_new_handler
- new/std::nothrow
- new/std::set_new_handler
ms.assetid: e250f06a-b025-4509-ae7a-5356d56aad7d
ms.openlocfilehash: b46a21223fcee4f1e208f97e087e47445d5526c5
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97338187"
---
# <a name="ltnewgt-functions"></a>&lt;new&gt;, fonctions

## <a name="get_new_handler"></a><a name="get_new_handler"></a> get_new_handler

```cpp
new_handler get_new_handler() noexcept;
```

### <a name="remarks"></a>Notes

Retourne la `new_handler` actuelle.

## <a name="launder"></a><a name="launder"></a> blanchi

```cpp
template <class T>
    constexpr T* launder(T* ptr) noexcept;
```

### <a name="parameters"></a>Paramètres

*effectués*\
Adresse d’un octet en mémoire qui contient un objet dont le type est similaire à *T*.

### <a name="return-value"></a>Valeur renvoyée

Valeur de type *T \** qui pointe vers X.

### <a name="remarks"></a>Notes

Également appelée barrière d’optimisation des pointeurs.

Utilisé en tant qu’expression constante lorsque la valeur de son argument peut être utilisée dans une expression constante. Un octet de stockage est accessible via une valeur de pointeur qui pointe vers un objet si dans le stockage occupé par un autre objet, un objet avec un pointeur similaire.

### <a name="example"></a>Exemple

```cpp
struct X { const int n; };

X *p = new X{3};
const int a = p->n;
new (p) X{5}; // p does not point to new object because X::n is const
const int b = p->n; // undefined behavior
const int c = std::launder(p)->n; // OK
```

## <a name="nothrow"></a><a name="nothrow"></a> nothrow

Fournit un objet à utiliser comme argument pour les **`nothrow`** versions de **`new`** et **`delete`** .

```cpp
extern const std::nothrow_t nothrow;
```

### <a name="remarks"></a>Notes

L’objet est utilisé comme argument de fonction pour correspondre au type de paramètre [std::nothrow_t](../standard-library/nothrow-t-structure.md).

### <a name="example"></a>Exemple

Pour obtenir des exemples d’utilisation de `std::nothrow_t` comme paramètre de fonction, consultez [new, opérateur](../standard-library/new-operators.md#op_new) et [new &#91;&#93;, opérateur](../standard-library/new-operators.md#op_new_arr).

## <a name="set_new_handler"></a><a name="set_new_handler"></a> set_new_handler

Installe une fonction utilisateur qui doit être appelée lorsque l' **opérateur New** échoue lors de sa tentative d’allocation de mémoire.

```cpp
new_handler set_new_handler(new_handler Pnew) throw();
```

### <a name="parameters"></a>Paramètres

*Pnew*\
`new_handler`À installer.

### <a name="return-value"></a>Valeur renvoyée

0 lors du premier appel et `new_handler` précédent lors des appels ultérieurs.

### <a name="remarks"></a>Notes

La fonction stocke *PNEW* dans un [nouveau](../standard-library/new-typedefs.md#new_handler) pointeur de gestionnaire statique qu’elle gère, puis retourne la valeur précédemment stockée dans le pointeur. Le nouveau gestionnaire est utilisé par l' [opérateur New](../standard-library/new-operators.md#op_new)(**size_t**).

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
