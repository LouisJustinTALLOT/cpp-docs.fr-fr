---
title: '&lt;hash_set&gt;, opérateurs'
ms.date: 03/27/2019
f1_keywords:
- hash_set/std::operator!=
- hash_set/std::operator==
ms.assetid: 403d8e4e-0b3f-43fb-bc5a-8100c4f331c5
ms.openlocfilehash: 3900e9c6e4fb7f5a163279165a51b440d138a8e5
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/16/2020
ms.locfileid: "79418999"
---
# <a name="lthash_setgt-operators"></a>&lt;hash_set&gt;, opérateurs

||||
|-|-|-|
|[operator!=](#op_neq)|[operator!= (hash_multiset)](#op_neq_hash_multiset)|[operator==](#op_eq_eq)|
|[operator== (hash_multiset)](#op_eq_eq_hash_multiset)|

## <a name="op_neq"></a>  operator!=

> [!NOTE]
> Cette API est obsolète. L’alternative est [unordered_set, classe](../standard-library/unordered-set-class.md).

Vérifie si l’objet hash_set situé à gauche de l’opérateur n’est pas égal à l’objet hash_set situé à droite.

```cpp
bool operator!=(const hash_set <Key, Traits, Allocator>& left, const hash_set <Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>Paramètres

\ *gauche*
Objet de type `hash_set`.

\ *droit*
Objet de type `hash_set`.

### <a name="return-value"></a>Valeur de retour

**true** si les hash_sets ne sont pas égaux ; **false** si les hash_sets sont égaux.

### <a name="remarks"></a>Notes

La comparaison entre les objets hash_set est basée sur une comparaison par paire de leurs éléments. Deux hash_sets sont égaux s’ils ont le même nombre d’éléments et si leurs éléments respectifs ont les mêmes valeurs. Sinon, elles sont inégales.

Les membres des fichiers d’en-tête [< hash_map >](../standard-library/hash-map.md) et [< hash_set](../standard-library/hash-set.md) > se trouvent dans l' [espace de noms stdext](../standard-library/stdext-namespace.md).

### <a name="example"></a>Exemple

```cpp
// hash_set_op_ne.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_set <int> hs1, hs2, hs3;
   int i;

   for ( i = 0 ; i < 3 ; i++ )
   {
      hs1.insert ( i );
      hs2.insert ( i * i );
      hs3.insert ( i );
   }

   if ( hs1 != hs2 )
      cout << "The hash_sets hs1 and hs2 are not equal." << endl;
   else
      cout << "The hash_sets hs1 and hs2 are equal." << endl;

   if ( hs1 != hs3 )
      cout << "The hash_sets hs1 and hs3 are not equal." << endl;
   else
      cout << "The hash_sets hs1 and hs3 are equal." << endl;
}
```

```Output
The hash_sets hs1 and hs2 are not equal.
The hash_sets hs1 and hs3 are equal.
```

## <a name="op_eq_eq"></a>  operator==

> [!NOTE]
> Cette API est obsolète. L’alternative est [unordered_set, classe](../standard-library/unordered-set-class.md).

Vérifie si l’objet hash_set situé à gauche de l’opérateur est égal à l’objet hash_set situé à droite.

```cpp
bool operator!==(const hash_set <Key, Traits, Allocator>& left, const hash_set <Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>Paramètres

\ *gauche*
Objet de type `hash_set`.

\ *droit*
Objet de type `hash_set`.

### <a name="return-value"></a>Valeur de retour

**true** si le hash_set situé à gauche de l’opérateur est égal au hash_set situé à droite de l’opérateur. Sinon, **false**.

### <a name="remarks"></a>Notes

La comparaison entre les objets hash_set est basée sur une comparaison par paire de leurs éléments. Deux hash_sets sont égaux s’ils ont le même nombre d’éléments et si leurs éléments respectifs ont les mêmes valeurs. Sinon, elles sont inégales.

### <a name="example"></a>Exemple

```cpp
// hash_set_op_eq.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_set <int> s1, s2, s3;
   int i;

   for ( i = 0 ; i < 3 ; i++ )
   {
      s1.insert ( i );
      s2.insert ( i * i );
      s3.insert ( i );
   }

   if ( s1 == s2 )
      cout << "The hash_sets s1 and s2 are equal." << endl;
   else
      cout << "The hash_sets s1 and s2 are not equal." << endl;

   if ( s1 == s3 )
      cout << "The hash_sets s1 and s3 are equal." << endl;
   else
      cout << "The hash_sets s1 and s3 are not equal." << endl;
}
```

```Output
The hash_sets s1 and s2 are not equal.
The hash_sets s1 and s3 are equal.
```

## <a name="op_neq_hash_multiset"></a>  operator!= (hash_multiset)

> [!NOTE]
> Cette API est obsolète. L’alternative est [unordered_set, classe](../standard-library/unordered-set-class.md).

Vérifie si l’objet hash_multiset situé à gauche de l’opérateur n’est pas égal à l’objet hash_multiset situé à droite.

```cpp
bool operator!=(const hash_multiset <Key, Traits, Allocator>& left, const hash_multiset <Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>Paramètres

\ *gauche*
Objet de type `hash_multiset`.

\ *droit*
Objet de type `hash_multiset`.

### <a name="return-value"></a>Valeur de retour

**true** si les hash_multisets ne sont pas égaux ; **false** si les hash_multisets sont égaux.

### <a name="remarks"></a>Notes

La comparaison entre les objets hash_multiset est basée sur une comparaison par paire de leurs éléments. Deux hash_multisets sont égaux s’ils ont le même nombre d’éléments et si leurs éléments respectifs ont les mêmes valeurs. Sinon, elles sont inégales.

### <a name="example"></a>Exemple

```cpp
// hashset_op_ne.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multiset <int> hs1, hs2, hs3;
   int i;

   for ( i = 0 ; i < 3 ; i++ )
   {
      hs1.insert ( i );
      hs2.insert ( i * i );
      hs3.insert ( i );
   }

   if ( hs1 != hs2 )
      cout << "The hash_multisets hs1 and hs2 are not equal." << endl;
   else
      cout << "The hash_multisets hs1 and hs2 are equal." << endl;

   if ( hs1 != hs3 )
      cout << "The hash_multisets hs1 and hs3 are not equal." << endl;
   else
      cout << "The hash_multisets hs1 and hs3 are equal." << endl;
}
```

```Output
The hash_multisets hs1 and hs2 are not equal.
The hash_multisets hs1 and hs3 are equal.
```

## <a name="op_eq_eq_hash_multiset"></a>  operator== (hash_multiset)

> [!NOTE]
> Cette API est obsolète. L’alternative est [unordered_set, classe](../standard-library/unordered-set-class.md).

Vérifie si l’objet hash_multiset situé à gauche de l’opérateur est égal à l’objet hash_multiset situé à droite.

```cpp
bool operator!==(const hash_multiset <Key, Traits, Allocator>& left, const hash_multiset <Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>Paramètres

\ *gauche*
Objet de type `hash_multiset`.

\ *droit*
Objet de type `hash_multiset`.

### <a name="return-value"></a>Valeur de retour

**true** si le hash_multiset situé à gauche de l’opérateur est égal au hash_multiset situé à droite de l’opérateur. Sinon, **false**.

### <a name="remarks"></a>Notes

La comparaison entre les objets hash_multiset est basée sur une comparaison par paire de leurs éléments. Deux hash_multisets sont égaux s’ils ont le même nombre d’éléments et si leurs éléments respectifs ont les mêmes valeurs. Sinon, elles sont inégales.

### <a name="example"></a>Exemple

```cpp
// hash_multiset_op_eq.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multiset <int> s1, s2, s3;
   int i;

   for ( i = 0 ; i < 3 ; i++ )
   {
      s1.insert ( i );
      s2.insert ( i * i );
      s3.insert ( i );
   }

   if ( s1 == s2 )
      cout << "The hash_multisets s1 and s2 are equal." << endl;
   else
      cout << "The hash_multisets s1 and s2 are not equal." << endl;

   if ( s1 == s3 )
      cout << "The hash_multisets s1 and s2 are equal." << endl;
   else
      cout << "The hash_multisets s1 and s2 are not equal." << endl;
}
```

```Output
The hash_multisets s1 and s2 are not equal.
The hash_multisets s1 and s2 are equal.
```

## <a name="see-also"></a>Voir aussi

[<hash_set>](../standard-library/hash-set.md)
