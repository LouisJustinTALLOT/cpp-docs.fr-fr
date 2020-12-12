---
description: 'En savoir plus sur les opérateurs suivants : &lt; hash_map &gt;'
title: '&lt;hash_map&gt;, opérateurs'
ms.date: 11/04/2016
f1_keywords:
- hash_map/std::operator!=
- hash_map/std::operator==
ms.assetid: 24b9bb9e-e983-4060-bce5-2c7c8161ee61
ms.openlocfilehash: f3374ee86a989a90add86e85d6a9bf15959e26b4
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97324120"
---
# <a name="lthash_mapgt-operators"></a>&lt;hash_map&gt;, opérateurs

[opérateur ! =](#op_neq)\
[opérateur ! = (Multimap)](#op_neq_mm)\
[opérateur = =](#op_eq_eq)\
[opérateur = = (Multimap)](#op_eq_eq_mm)

## <a name="operator"></a><a name="op_neq"></a> opérateur ! =

> [!NOTE]
> Cette API est obsolète. L’alternative est [unordered_map, classe](unordered-map-class.md).

Vérifie si l’objet hash_map situé à gauche de l’opérateur n’est pas égal à l’objet hash_map situé à droite.

```cpp
bool operator!=(const hash_map <Key, Type, Traits, Allocator>& left, const hash_map <Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>Paramètres

*gauche*\
Objet de type `hash_map`.

*Oui*\
Objet de type `hash_map`.

### <a name="return-value"></a>Valeur renvoyée

**`true`** Si les hash_maps ne sont pas égales ; **`false`** si les hash_maps sont égales.

### <a name="remarks"></a>Notes

La comparaison entre les objets hash_map est basée sur une comparaison par paire de leurs éléments. Deux hash_map sont égaux s’ils ont le même nombre d’éléments et si leurs éléments respectifs ont les mêmes valeurs. Sinon, elles sont inégales.

Les membres du [<hash_map>](hash-map.md) et [<](hash-set.md) fichiers d’en-tête Hash_set>dans l' [espace de noms stdext](stdext-namespace.md).

### <a name="example"></a>Exemple

```cpp
// hash_map_op_ne.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_map <int, int> hm1, hm2, hm3;
   int i;
   typedef pair <int, int> Int_Pair;

   for ( i = 0 ; i < 3 ; i++ )
   {
      hm1.insert ( Int_Pair ( i, i ) );
      hm2.insert ( Int_Pair ( i, i * i ) );
      hm3.insert ( Int_Pair ( i, i ) );
   }

   if ( hm1 != hm2 )
      cout << "The hash_maps hm1 and hm2 are not equal." << endl;
   else
      cout << "The hash_maps hm1 and hm2 are equal." << endl;

   if ( hm1 != hm3 )
      cout << "The hash_maps hm1 and hm3 are not equal." << endl;
   else
      cout << "The hash_maps hm1 and hm3 are equal." << endl;
}
```

```Output
The hash_maps hm1 and hm2 are not equal.
The hash_maps hm1 and hm3 are equal.
```

## <a name="operator"></a><a name="op_eq_eq"></a> opérateur = =

> [!NOTE]
> Cette API est obsolète. L’alternative est [unordered_map, classe](unordered-map-class.md).

Vérifie si l’objet hash_map situé à gauche de l’opérateur est égal à l’objet hash_map situé à droite.

```cpp
bool operator==(const hash_map <Key, Type, Traits, Allocator>& left, const hash_map <Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>Paramètres

*gauche*\
Objet de type `hash_map`.

*Oui*\
Objet de type `hash_map`.

### <a name="return-value"></a>Valeur renvoyée

**`true`** Si le hash_map situé à gauche de l’opérateur est égal au hash_map situé à droite de l’opérateur ; Sinon, **`false`** .

### <a name="remarks"></a>Notes

La comparaison entre les objets hash_map est basée sur une comparaison par paire de leurs éléments. Deux hash_map sont égaux s’ils ont le même nombre d’éléments et si leurs éléments respectifs ont les mêmes valeurs. Sinon, elles sont inégales.

### <a name="example"></a>Exemple

```cpp
// hash_map_op_eq.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_map <int, int> hm1, hm2, hm3;
   int i;
   typedef pair <int, int> Int_Pair;

   for ( i = 0 ; i < 3 ; i++ )
   {
      hm1.insert ( Int_Pair ( i, i ) );
      hm2.insert ( Int_Pair ( i, i * i ) );
      hm3.insert ( Int_Pair ( i, i ) );
   }

   if ( hm1 == hm2 )
      cout << "The hash_maps hm1 and hm2 are equal." << endl;
   else
      cout << "The hash_maps hm1 and hm2 are not equal." << endl;

   if ( hm1 == hm3 )
      cout << "The hash_maps hm1 and hm3 are equal." << endl;
   else
      cout << "The hash_maps hm1 and hm3 are not equal." << endl;
}
```

```Output
The hash_maps hm1 and hm2 are not equal.
The hash_maps hm1 and hm3 are equal.
```

## <a name="operator-hash_multimap"></a><a name="op_neq_mm"></a> opérateur ! = (hash_multimap)

> [!NOTE]
> Cette API est obsolète. L’alternative est [unordered_multimap Class](unordered-multimap-class.md).

Vérifie si l’objet hash_multimap situé à gauche de l’opérateur n’est pas égal à l’objet hash_multimap situé à droite.

```cpp
bool operator!=(const hash_multimap <Key, Type, Traits, Allocator>& left, const hash_multimap <Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>Paramètres

*gauche*\
Objet de type `hash_multimap`.

*Oui*\
Objet de type `hash_multimap`.

### <a name="return-value"></a>Valeur renvoyée

**`true`** Si les hash_multimaps ne sont pas égales ; **`false`** si les hash_multimaps sont égales.

### <a name="remarks"></a>Notes

La comparaison entre les objets hash_multimap est basée sur une comparaison par paire de leurs éléments. Deux hash_multimaps sont égaux s’ils ont le même nombre d’éléments et si leurs éléments respectifs ont les mêmes valeurs. Sinon, elles sont inégales.

### <a name="example"></a>Exemple

```cpp
// hash_multimap_op_ne.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multimap <int, int> hm1, hm2, hm3;
   int i;
   typedef pair <int, int> Int_Pair;

   for ( i = 0 ; i < 3 ; i++ )
   {
      hm1.insert ( Int_Pair ( i, i ) );
      hm2.insert ( Int_Pair ( i, i * i ) );
      hm3.insert ( Int_Pair ( i, i ) );
   }

   if ( hm1 != hm2 )
      cout << "The hash_multimaps hm1 and hm2 are not equal." << endl;
   else
      cout << "The hash_multimaps hm1 and hm2 are equal." << endl;

   if ( hm1 != hm3 )
      cout << "The hash_multimaps hm1 and hm3 are not equal." << endl;
   else
      cout << "The hash_multimaps hm1 and hm3 are equal." << endl;
}
```

```Output
The hash_multimaps hm1 and hm2 are not equal.
The hash_multimaps hm1 and hm3 are equal.
```

## <a name="operator--hash_multimap"></a><a name="op_eq_eq_mm"></a> opérateur = = (hash_multimap)

> [!NOTE]
> Cette API est obsolète. L’alternative est [unordered_multimap Class](unordered-multimap-class.md).

Vérifie si l’objet hash_multimap situé à gauche de l’opérateur est égal à l’objet hash_multimap situé à droite.

```cpp
bool operator==(const hash_multimap <Key, Type, Traits, Allocator>& left, const hash_multimap <Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>Paramètres

*gauche*\
Objet de type `hash_multimap`.

*Oui*\
Objet de type `hash_multimap`.

### <a name="return-value"></a>Valeur renvoyée

**`true`** Si le hash_multimap situé à gauche de l’opérateur est égal au hash_multimap situé à droite de l’opérateur ; Sinon, **`false`** .

### <a name="remarks"></a>Notes

La comparaison entre les objets hash_multimap est basée sur une comparaison par paire de leurs éléments. Deux hash_multimaps sont égaux s’ils ont le même nombre d’éléments et si leurs éléments respectifs ont les mêmes valeurs. Sinon, elles sont inégales.

### <a name="example"></a>Exemple

```cpp
// hash_multimap_op_eq.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multimap<int, int> hm1, hm2, hm3;
   int i;
   typedef pair<int, int> Int_Pair;

   for (i = 0; i < 3; i++)
   {
      hm1.insert(Int_Pair(i, i));
      hm2.insert(Int_Pair(i, i*i));
      hm3.insert(Int_Pair(i, i));
   }

   if ( hm1 == hm2 )
      cout << "The hash_multimaps hm1 and hm2 are equal." << endl;
   else
      cout << "The hash_multimaps hm1 and hm2 are not equal." << endl;

   if ( hm1 == hm3 )
      cout << "The hash_multimaps hm1 and hm3 are equal." << endl;
   else
      cout << "The hash_multimaps hm1 and hm3 are not equal." << endl;
}
```

```Output
The hash_multimaps hm1 and hm2 are not equal.
The hash_multimaps hm1 and hm3 are equal.
```

## <a name="see-also"></a>Voir aussi

[<hash_map>](hash-map.md)
