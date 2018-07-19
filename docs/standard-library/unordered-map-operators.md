---
title: '&lt;unordered_map&gt;, opérateurs | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- unordered_map/std::operator!=
- unordered_map/std::operator==
dev_langs:
- C++
ms.assetid: 9d5add0b-84bd-4a79-bd82-3f58b55145ed
ms.openlocfilehash: a43528b270571a9994187711e2a21ca5a0e1f096
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2018
ms.locfileid: "38958901"
---
# <a name="ltunorderedmapgt-operators"></a>&lt;unordered_map&gt;, opérateurs

|||||
|-|-|-|-|
|[operator!=](#op_neq)|[operator==](#op_eq_eq)|[operator!=](#op_neq_multimap)|[operator==](#op_eq_eq_multimap)|

## <a name="op_neq"></a>  operator!=

Teste si l’objet [unordered_map](../standard-library/unordered-map-class.md) situé à gauche de l’opérateur n’est pas égal à l’objet unordered_map situé à droite.

```cpp
bool operator!=(const unordered_map <Key, Type, Hash, Pred, Allocator>& left, const unordered_map <Key, Type, Hash, Pred, Allocator>& right);
```

### <a name="parameters"></a>Paramètres

*left*  
 Objet de type `unordered_map`.

*right*  
 Objet de type `unordered_map`.

### <a name="return-value"></a>Valeur de retour

**true** si les objets unordered_map ne sont pas égaux ; **false** s’ils sont égaux.

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

```

**Sortie :**

`um1 != um2: true`

`um1 != um3: false`

`um2 != um3: true`

## <a name="op_eq_eq"></a>  operator==

Teste si l’objet [unordered_map](../standard-library/unordered-map-class.md) situé à gauche de l’opérateur est égal à l’objet unordered_map situé à droite.

```cpp
bool operator==(const unordered_map <Key, Type, Hash, Pred, Allocator>& left, const unordered_map <Key, Type, Hash, Pred, Allocator>& right);
```

### <a name="parameters"></a>Paramètres

*left*  
 Objet de type `unordered_map`.

*right*  
 Objet de type `unordered_map`.

### <a name="return-value"></a>Valeur de retour

**true** si les objets unordered_map sont égaux ; **false** s’ils ne sont pas égaux.

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

```

**Sortie :**

`um1 == um2: false`

`um1 == um3: true`

`um2 == um3: false`

## <a name="op_neq_multimap"></a>  operator!=

Teste si l’objet [unordered_multimap](../standard-library/unordered-multimap-class.md) situé à gauche de l’opérateur n’est pas égal à l’objet unordered_multimap situé à droite.

```cpp
bool operator!=(const unordered_multimap <Key, Type, Hash, Pred, Allocator>& left, const unordered_multimap <Key, Type, Hash, Pred, Allocator>& right);
```

### <a name="parameters"></a>Paramètres

*left*  
 Objet de type `unordered_multimap`.

*right*  
 Objet de type `unordered_multimap`.

### <a name="return-value"></a>Valeur de retour

**true** si les objets unordered_multimap ne sont pas égaux ; **false** s’ils sont égaux.

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

```

**Sortie :**

`um1 != um2: true`

`um1 != um3: false`

`um2 != um3: true`

## <a name="op_eq_eq_multimap"></a>  operator==

Teste si l’objet [unordered_multimap](../standard-library/unordered-multimap-class.md) situé à gauche de l’opérateur est égal à l’objet unordered_multimap situé à droite.

```cpp
bool operator==(const unordered_multimap <Key, Type, Hash, Pred, Allocator>& left, const unordered_multimap <Key, Type, Hash, Pred, Allocator>& right);
```

### <a name="parameters"></a>Paramètres

*left*  
 Objet de type `unordered_multimap`.

*right*  
 Objet de type `unordered_multimap`.

### <a name="return-value"></a>Valeur de retour

**true** si les objets unordered_multimap sont égaux ; **false** s’ils ne sont pas égaux.

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

```

**Sortie :**

`um1 == um2: false`

`um1 == um3: true`

`um2 == um3: false`

## <a name="see-also"></a>Voir aussi

[<unordered_map>](../standard-library/unordered-map.md)<br/>
