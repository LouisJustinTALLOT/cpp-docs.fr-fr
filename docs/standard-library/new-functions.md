---
title: '&lt;new&gt;, fonctions'
ms.date: 11/04/2016
f1_keywords:
- new/std::get_new_handler
- new/std::nothrow
- new/std::set_new_handler
ms.assetid: e250f06a-b025-4509-ae7a-5356d56aad7d
ms.openlocfilehash: c912e5be07ea0ebdd3148d30c80c39a5f8cfa1a5
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/16/2019
ms.locfileid: "68243665"
---
# <a name="ltnewgt-functions"></a>&lt;new&gt;, fonctions

## <a name="get_new_handler"></a> get_new_handler

```cpp
new_handler get_new_handler() noexcept;
```

### <a name="remarks"></a>Notes

Retourne l’actuel `new_handler`.

## <a name="launder"></a> blanchiment

```cpp
template <class T>
    constexpr T* launder(T* ptr) noexcept;
```

### <a name="parameters"></a>Paramètres

*PTR*\
L’adresse d’un octet dans la mémoire qui contient un objet dont le type est similaire à *T*.

### <a name="return-value"></a>Valeur de retour

Une valeur de type *T\**  qui pointe vers X.

### <a name="remarks"></a>Notes

Également appelé une barrière de l’optimisation du pointeur.

Utilisé comme une expression constante lorsque la valeur de son argument peut être utilisée dans une expression constante. Un octet de stockage est accessible via une valeur de pointeur qui pointe vers un objet si, dans le stockage occupé par un autre objet, un objet avec un pointeur similaire.

### <a name="example"></a>Exemple

```cpp
struct X { const int n; };

X *p = new X{3};
const int a = p->n;
new (p) X{5}; // p does not point to new object because X::n is const
const int b = p->n; // undefined behavior
const int c = std::launder(p)->n; // OK
```

## <a name="nothrow"></a> nothrow

Fournit un objet à utiliser en tant qu’argument pour le **nothrow** versions de **nouveau** et **supprimer**.

```cpp
extern const std::nothrow_t nothrow;
```

### <a name="remarks"></a>Notes

L’objet est utilisé comme argument de fonction pour correspondre au type de paramètre [std::nothrow_t](../standard-library/nothrow-t-structure.md).

### <a name="example"></a>Exemple

Pour obtenir des exemples d’utilisation de `std::nothrow_t` comme paramètre de fonction, consultez [new, opérateur](../standard-library/new-operators.md#op_new) et [new &#91;&#93;, opérateur](../standard-library/new-operators.md#op_new_arr).

## <a name="set_new_handler"></a> set_new_handler

Installe une fonction de l’utilisateur qui doit être appelée lorsque **opérateur new** échoue dans sa tentative d’allocation de mémoire.

```cpp
new_handler set_new_handler(new_handler Pnew) throw();
```

### <a name="parameters"></a>Paramètres

*Pnew*\
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
