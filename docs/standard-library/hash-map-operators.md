---
title: '&lt;hash_map&gt;, opérateurs | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- hash_map/std::operator!=
- hash_map/std::operator==
dev_langs:
- C++
ms.assetid: 24b9bb9e-e983-4060-bce5-2c7c8161ee61
ms.openlocfilehash: bd140fed954c097fa73f179c92cbc64f3148e77c
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44108459"
---
# <a name="lthashmapgt-operators"></a>&lt;hash_map&gt;, opérateurs

|||
|-|-|
|[operator!=](#op_neq)|[operator!= (multimap)](#op_neq_mm)|
|[operator==](#op_eq_eq)|[operator== (multimap)](#op_eq_eq_mm)|

## <a name="op_neq"></a>  operator!=

> [!NOTE]
> Cette API est obsolète. L’alternative est [unordered_map, classe](unordered-map-class.md).

Vérifie si l’objet hash_map situé à gauche de l’opérateur n’est pas égal à l’objet hash_map situé à droite.

```cpp
bool operator!=(const hash_map <Key, Type, Traits, Allocator>& left, const hash_map <Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>Paramètres

*left*<br/>
Objet de type `hash_map`.

*right*<br/>
Objet de type `hash_map`.

### <a name="return-value"></a>Valeur de retour

**true** si les hash_maps ne sont pas égaux ; **false** si les hash_maps sont égaux.

### <a name="remarks"></a>Notes

La comparaison entre les objets hash_map est basée sur une comparaison par paire de leurs éléments. Deux hash_map sont égaux s’ils ont le même nombre d’éléments et si leurs éléments respectifs ont les mêmes valeurs. Sinon, elles sont inégales.

Membres de la [< hash_map >](hash-map.md) et [< hash_set >](hash-set.md) fichiers d’en-tête dans le [ stdext Namespace](stdext-namespace.md).

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

## <a name="op_eq_eq"></a>  operator==

> [!NOTE]
> Cette API est obsolète. L’alternative est [unordered_map, classe](unordered-map-class.md).

Vérifie si l’objet hash_map situé à gauche de l’opérateur est égal à l’objet hash_map situé à droite.

```cpp
bool operator==(const hash_map <Key, Type, Traits, Allocator>& left, const hash_map <Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>Paramètres

*left*<br/>
Objet de type `hash_map`.

*right*<br/>
Objet de type `hash_map`.

### <a name="return-value"></a>Valeur de retour

**true** si le hash_map situé à gauche de l’opérateur est égal au hash_map situé à droite de l’opérateur. Sinon, **false**.

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

## <a name="op_neq_mm"></a>  opérateur ! = (hash_multimap)

> [!NOTE]
> Cette API est obsolète. L’alternative est [unordered_multimap, classe](unordered-multimap-class.md).

Vérifie si l’objet hash_multimap situé à gauche de l’opérateur n’est pas égal à l’objet hash_multimap situé à droite.

```cpp
bool operator!=(const hash_multimap <Key, Type, Traits, Allocator>& left, const hash_multimap <Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>Paramètres

*left*<br/>
Objet de type `hash_multimap`.

*right*<br/>
Objet de type `hash_multimap`.

### <a name="return-value"></a>Valeur de retour

**true** si les hash_multimaps ne sont pas égaux ; **false** si les hash_multimaps sont égaux.

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

## <a name="op_eq_eq_mm"></a>  opérateur == (hash_multimap)

> [!NOTE]
> Cette API est obsolète. L’alternative est [unordered_multimap, classe](unordered-multimap-class.md).

Vérifie si l’objet hash_multimap situé à gauche de l’opérateur est égal à l’objet hash_multimap situé à droite.

```cpp
bool operator==(const hash_multimap <Key, Type, Traits, Allocator>& left, const hash_multimap <Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>Paramètres

*left*<br/>
Objet de type `hash_multimap`.

*right*<br/>
Objet de type `hash_multimap`.

### <a name="return-value"></a>Valeur de retour

**true** si le hash_multimap situé à gauche de l’opérateur est égal au hash_multimap situé à droite de l’opérateur. Sinon, **false**.

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

[<hash_map>](hash-map.md)<br/>
