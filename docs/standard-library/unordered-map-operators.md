---
description: 'En savoir plus sur les opérateurs suivants : &lt; unordered_map &gt;'
title: '&lt;unordered_map&gt;, opérateurs'
ms.date: 11/04/2016
f1_keywords:
- unordered_map/std::operator!=
- unordered_map/std::operator==
ms.assetid: 9d5add0b-84bd-4a79-bd82-3f58b55145ed
ms.openlocfilehash: b7bf3712a7068b3af2d8316249d169854401b93e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97321476"
---
# <a name="ltunordered_mapgt-operators"></a>&lt;unordered_map&gt;, opérateurs

[unordered_map :: Operator ! =](#op_neq)\
[unordered_map :: Operator = =](#op_eq_eq)\
[unordered_multimap :: Operator ! =](#op_neq_multimap)\
[unordered_multimap :: Operator = =](#op_eq_eq_multimap)

## <a name="operator"></a><a name="op_neq"></a> opérateur ! =

Teste si l’objet [unordered_map](../standard-library/unordered-map-class.md) situé à gauche de l’opérateur n’est pas égal à l’objet unordered_map situé à droite.

```cpp
bool operator!=(const unordered_map <Key, Type, Hash, Pred, Allocator>& left, const unordered_map <Key, Type, Hash, Pred, Allocator>& right);
```

### <a name="parameters"></a>Paramètres

*gauche*\
Objet de type `unordered_map`.

*Oui*\
Objet de type `unordered_map`.

### <a name="return-value"></a>Valeur renvoyée

**`true`** Si les unordered_maps ne sont pas égales ; **`false`** si elles sont égales.

### <a name="remarks"></a>Notes

La comparaison entre les objets unordered_map n’est pas affectée par l’ordre arbitraire dans lequel ils stockent leurs éléments. Deux objets unordered_map sont égaux s’ils ont le même nombre d’éléments et que les éléments d’un conteneur constituent une permutation des éléments de l’autre conteneur. Sinon, elles sont inégales.

### <a name="example"></a>Exemple

```cpp
// unordered_map_op_ne.cpp
// compile by using: cl.exe /EHsc /nologo /W4 /MTd
#include <unordered_map>
#include <iostream>
#include <ios>

int main( )
{
   using namespace std;
   unordered_map<int, int> um1, um2, um3;

   for ( int i = 0 ; i < 3 ; ++i ) {
      um1.insert( make_pair( i+1, i ) );
      um1.insert( make_pair( i, i ) );

      um2.insert( make_pair( i, i+1 ) );
      um2.insert( make_pair( i, i ) );

      um3.insert( make_pair( i, i ) );
      um3.insert( make_pair( i+1, i ) );
   }

   cout << boolalpha;
   cout << "um1 != um2: " << (um1 != um2) << endl;
   cout << "um1 != um3: " << (um1 != um3) << endl;
   cout << "um2 != um3: " << (um2 != um3) << endl;
}

/* Output:
um1 != um2: true
um1 != um3: false
um2 != um3: true
*/
```

## <a name="operator"></a><a name="op_eq_eq"></a> opérateur = =

Teste si l’objet [unordered_map](../standard-library/unordered-map-class.md) situé à gauche de l’opérateur est égal à l’objet unordered_map situé à droite.

```cpp
bool operator==(const unordered_map <Key, Type, Hash, Pred, Allocator>& left, const unordered_map <Key, Type, Hash, Pred, Allocator>& right);
```

### <a name="parameters"></a>Paramètres

*gauche*\
Objet de type `unordered_map`.

*Oui*\
Objet de type `unordered_map`.

### <a name="return-value"></a>Valeur renvoyée

**`true`** Si les unordered_maps sont égales ; **`false`** si elles ne sont pas égales.

### <a name="remarks"></a>Notes

La comparaison entre les objets unordered_map n’est pas affectée par l’ordre arbitraire dans lequel ils stockent leurs éléments. Deux objets unordered_map sont égaux s’ils ont le même nombre d’éléments et que les éléments d’un conteneur constituent une permutation des éléments de l’autre conteneur. Sinon, elles sont inégales.

### <a name="example"></a>Exemple

```cpp
// unordered_map_op_eq.cpp
// compile by using: cl.exe /EHsc /nologo /W4 /MTd
#include <unordered_map>
#include <iostream>
#include <ios>

int main( )
{
   using namespace std;
   unordered_map<int, int> um1, um2, um3;

   for ( int i = 0 ; i < 3 ; ++i ) {
      um1.insert( make_pair( i+1, i ) );
      um1.insert( make_pair( i, i ) );

      um2.insert( make_pair( i, i+1 ) );
      um2.insert( make_pair( i, i ) );

      um3.insert( make_pair( i, i ) );
      um3.insert( make_pair( i+1, i ) );
   }

   cout << boolalpha;
   cout << "um1 == um2: " << (um1 == um2) << endl;
   cout << "um1 == um3: " << (um1 == um3) << endl;
   cout << "um2 == um3: " << (um2 == um3) << endl;
}

/* Output:
um1 == um2: false
um1 == um3: true
um2 == um3: false
*/
```

## <a name="operator-multimap"></a><a name="op_neq_multimap"></a> opérateur ! = (Multimap)

Teste si l’objet [unordered_multimap](../standard-library/unordered-multimap-class.md) situé à gauche de l’opérateur n’est pas égal à l’objet unordered_multimap situé à droite.

```cpp
bool operator!=(const unordered_multimap <Key, Type, Hash, Pred, Allocator>& left, const unordered_multimap <Key, Type, Hash, Pred, Allocator>& right);
```

### <a name="parameters"></a>Paramètres

*gauche*\
Objet de type `unordered_multimap`.

*Oui*\
Objet de type `unordered_multimap`.

### <a name="return-value"></a>Valeur renvoyée

**`true`** Si les unordered_multimaps ne sont pas égales ; **`false`** si elles sont égales.

### <a name="remarks"></a>Notes

La comparaison entre les objets unordered_multimap n’est pas affectée par l’ordre arbitraire dans lequel ils stockent leurs éléments. Deux objets unordered_multimap sont égaux s’ils ont le même nombre d’éléments et que les éléments d’un conteneur constituent une permutation des éléments de l’autre conteneur. Sinon, il ne sont pas égaux.

### <a name="example"></a>Exemple

```cpp
// unordered_multimap_op_ne.cpp
// compile by using: cl.exe /EHsc /nologo /W4 /MTd
#include <unordered_map>
#include <iostream>
#include <ios>

int main( )
{
   using namespace std;
   unordered_multimap<int, int> um1, um2, um3;

   for ( int i = 0 ; i < 3 ; ++i ) {
      um1.insert( make_pair( i, i ) );
      um1.insert( make_pair( i, i ) );

      um2.insert( make_pair( i, i ) );
      um2.insert( make_pair( i, i ) );
      um2.insert( make_pair( i, i ) );

      um3.insert( make_pair( i, i ) );
      um3.insert( make_pair( i, i ) );
   }

   cout << boolalpha;
   cout << "um1 != um2: " << (um1 != um2) << endl;
   cout << "um1 != um3: " << (um1 != um3) << endl;
   cout << "um2 != um3: " << (um2 != um3) << endl;
}

/* Output:
um1 != um2: true
um1 != um3: false
um2 != um3: true
*/
```

## <a name="operator-multimap"></a><a name="op_eq_eq_multimap"></a> opérateur = = (Multimap)

Teste si l’objet [unordered_multimap](../standard-library/unordered-multimap-class.md) situé à gauche de l’opérateur est égal à l’objet unordered_multimap situé à droite.

```cpp
bool operator==(const unordered_multimap <Key, Type, Hash, Pred, Allocator>& left, const unordered_multimap <Key, Type, Hash, Pred, Allocator>& right);
```

### <a name="parameters"></a>Paramètres

*gauche*\
Objet de type `unordered_multimap`.

*Oui*\
Objet de type `unordered_multimap`.

### <a name="return-value"></a>Valeur renvoyée

**`true`** Si les unordered_multimaps sont égales ; **`false`** si elles ne sont pas égales.

### <a name="remarks"></a>Notes

La comparaison entre les objets unordered_multimap n’est pas affectée par l’ordre arbitraire dans lequel ils stockent leurs éléments. Deux objets unordered_multimap sont égaux s’ils ont le même nombre d’éléments et que les éléments d’un conteneur constituent une permutation des éléments de l’autre conteneur. Sinon, elles sont inégales.

### <a name="example"></a>Exemple

```cpp
// unordered_multimap_op_eq.cpp
// compile by using: cl.exe /EHsc /nologo /W4 /MTd
#include <unordered_map>
#include <iostream>
#include <ios>

int main( )
{
   using namespace std;
   unordered_multimap<int, int> um1, um2, um3;

   for ( int i = 0 ; i < 3 ; ++i ) {
      um1.insert( make_pair( i, i ) );
      um1.insert( make_pair( i, i ) );

      um2.insert( make_pair( i, i ) );
      um2.insert( make_pair( i, i ) );
      um2.insert( make_pair( i, i ) );

      um3.insert( make_pair( i, i ) );
      um3.insert( make_pair( i, i ) );
   }

   cout << boolalpha;
   cout << "um1 == um2: " << (um1 == um2) << endl;
   cout << "um1 == um3: " << (um1 == um3) << endl;
   cout << "um2 == um3: " << (um2 == um3) << endl;
}

/* Output:
um1 == um2: false
um1 == um3: true
um2 == um3: false
*/
```

## <a name="see-also"></a>Voir aussi

[<unordered_map>](../standard-library/unordered-map.md)
