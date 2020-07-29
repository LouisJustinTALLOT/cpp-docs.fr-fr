---
title: '&lt;map&gt;, opérateurs'
ms.date: 03/27/2019
f1_keywords:
- map/std::operator!=
- map/std::operator&gt;
- map/std::operator&gt;=
- map/std::operator&lt;
- map/std::operator&lt;=
- map/std::operator==
ms.assetid: 7df02b9f-701c-44ed-834a-a819badc5bd0
helpviewer_keywords:
- std::operator!= (map)
- std::operator&gt; (map)
- std::operator&gt;= (map)
- std::operator&lt; (map)
- std::operator&lt;= (map)
- std::operator== (map)
ms.openlocfilehash: 2c632966c9ac1264747568facd459a33d1e13338
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87233078"
---
# <a name="ltmapgt-operators"></a>&lt;map&gt;, opérateurs

## <a name="operator"></a><a name="op_neq"></a>opérateur ! =

Teste si l’objet map situé à gauche de l’opérateur n’est pas égal à l’objet map situé à droite.

```cpp
bool operator!=(
      const map <Key, Type, Traits, Allocator>& left,
      const map <Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>Paramètres

*gauche*\
Objet de type `map`.

*Oui*\
Objet de type `map`.

### <a name="return-value"></a>Valeur de retour

**`true`** Si les mappages ne sont pas égaux ; **`false`** si les mappages sont égaux.

### <a name="remarks"></a>Notes

La comparaison entre les objets map est basée sur une comparaison par paire de leurs éléments. Deux mappages sont égaux s’ils ont le même nombre d’éléments et si leurs éléments respectifs ont les mêmes valeurs. Sinon, elles sont inégales.

### <a name="example"></a>Exemple

```cpp
// map_op_ne.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   map <int, int> m1, m2, m3;
   int i;
   typedef pair <int, int> Int_Pair;

   for ( i = 0 ; i < 3 ; i++ )
   {
      m1.insert ( Int_Pair ( i, i ) );
      m2.insert ( Int_Pair ( i, i * i ) );
      m3.insert ( Int_Pair ( i, i ) );
   }

   if ( m1 != m2 )
      cout << "The maps m1 and m2 are not equal." << endl;
   else
      cout << "The maps m1 and m2 are equal." << endl;

   if ( m1 != m3 )
      cout << "The maps m1 and m3 are not equal." << endl;
   else
      cout << "The maps m1 and m3 are equal." << endl;
}
```

```Output
The maps m1 and m2 are not equal.
The maps m1 and m3 are equal.
```

## <a name="operatorlt"></a><a name="op_lt"></a>and&lt;

Teste si l’objet map situé à gauche de l’opérateur est inférieur à l’objet map situé à droite.

```cpp
bool operator<(
      const map <Key, Type, Traits, Allocator>& left,
      const map <Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>Paramètres

*gauche*\
Objet de type `map`.

*Oui*\
Objet de type `map`.

### <a name="return-value"></a>Valeur de retour

**`true`** Si la carte située à gauche de l’opérateur est strictement inférieure à la carte située à droite de l’opérateur ; Sinon, **`false`** .

### <a name="remarks"></a>Notes

La comparaison entre les objets map est basée sur une comparaison par paire de leurs éléments. La relation d'infériorité entre deux objets est basée sur une comparaison de la première paire d'éléments inégaux.

### <a name="example"></a>Exemple

```cpp
// map_op_lt.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   map<int, int> m1, m2, m3;
   int i;
   typedef pair<int, int> Int_Pair;

   for ( i = 1 ; i < 3 ; i++ )
   {
      m1.insert ( Int_Pair ( i, i ) );
      m2.insert ( Int_Pair ( i, i * i ) );
      m3.insert ( Int_Pair ( i, i - 1 ) );
   }

   if ( m1 < m2 )
      cout << "The map m1 is less than the map m2." << endl;
   else
      cout << "The map m1 is not less than the map m2." << endl;

   if ( m1 < m3 )
      cout << "The map m1 is less than the map m3." << endl;
   else
      cout << "The map m1 is not less than the map m3." << endl;
}
```

```Output
The map m1 is less than the map m2.
The map m1 is not less than the map m3.
```

## <a name="operatorlt"></a><a name="op_lt_eq"></a>and&lt;=

Teste si l’objet map situé à gauche de l’opérateur est inférieur ou égal à l’objet map situé à droite.

```cpp
bool operator<=(
      const map <Key, Type, Traits, Allocator>& left,
      const map <Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>Paramètres

*gauche*\
Objet de type `map`.

*Oui*\
Objet de type `map`.

### <a name="return-value"></a>Valeur de retour

**`true`** Si la carte située à gauche de l’opérateur est inférieure ou égale à la carte située à droite de l’opérateur ; Sinon, **`false`** .

### <a name="example"></a>Exemple

```cpp
// map_op_le.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   map <int, int> m1, m2, m3, m4;
   int i;
   typedef pair <int, int> Int_Pair;

   for ( i = 1 ; i < 3 ; i++ )
   {
      m1.insert ( Int_Pair ( i, i ) );
      m2.insert ( Int_Pair ( i, i * i ) );
      m3.insert ( Int_Pair ( i, i - 1 ) );
      m4.insert ( Int_Pair ( i, i ) );
   }

   if ( m1 <= m2 )
      cout << "The map m1 is less than or equal to the map m2." << endl;
   else
      cout << "The map m1 is greater than the map m2." << endl;

   if ( m1 <= m3 )
      cout << "The map m1 is less than or equal to the map m3." << endl;
   else
      cout << "The map m1 is greater than the map m3." << endl;

   if ( m1 <= m4 )
      cout << "The map m1 is less than or equal to the map m4." << endl;
   else
      cout << "The map m1 is greater than the map m4." << endl;
}
```

```Output
The map m1 is less than or equal to the map m2.
The map m1 is greater than the map m3.
The map m1 is less than or equal to the map m4.
```

## <a name="operator"></a><a name="op_eq_eq"></a>opérateur = =

Teste si l’objet map situé à gauche de l’opérateur est égal à l’objet map situé à droite.

```cpp
bool operator==(
      const map <Key, Type, Traits, Allocator>& left,
      const map <Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>Paramètres

*gauche*\
Objet de type `map`.

*Oui*\
Objet de type `map`.

### <a name="return-value"></a>Valeur de retour

**`true`** Si la carte sur le côté gauche de l’opérateur est égale à la carte située à droite de l’opérateur ; Sinon, **`false`** .

### <a name="remarks"></a>Notes

La comparaison entre les objets map est basée sur une comparaison par paire de leurs éléments. Deux mappages sont égaux s’ils ont le même nombre d’éléments et si leurs éléments respectifs ont les mêmes valeurs. Sinon, elles sont inégales.

### <a name="example"></a>Exemple

```cpp
// map_op_eq.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   map < int, int > m1, m2, m3;
   int i;
   typedef pair < int, int > Int_Pair;

   for ( i = 0 ; i < 3 ; i++ )
   {
      m1.insert ( Int_Pair ( i, i ) );
      m2.insert ( Int_Pair ( i, i * i ) );
      m3.insert ( Int_Pair ( i, i ) );
   }

   if ( m1 == m2 )
      cout << "The maps m1 and m2 are equal." << endl;
   else
      cout << "The maps m1 and m2 are not equal." << endl;

   if ( m1 == m3 )
      cout << "The maps m1 and m3 are equal." << endl;
   else
      cout << "The maps m1 and m3 are not equal." << endl;
}
```

```Output
The maps m1 and m2 are not equal.
The maps m1 and m3 are equal.
```

## <a name="operatorgt"></a><a name="op_gt"></a>and&gt;

Teste si l’objet map situé à gauche de l’opérateur est supérieur à l’objet map situé à droite.

```cpp
bool operator>(
      const map <Key, Type, Traits, Allocator>& left,
      const map <Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>Paramètres

*gauche*\
Objet de type `map`.

*Oui*\
Objet de type `map`.

### <a name="return-value"></a>Valeur de retour

**`true`** Si la carte sur le côté gauche de l’opérateur est supérieure à la carte située à droite de l’opérateur ; Sinon, **`false`** .

### <a name="remarks"></a>Notes

La comparaison entre les objets map est basée sur une comparaison par paire de leurs éléments. La relation de supériorité entre deux objets est basée sur une comparaison de la première paire d'éléments inégaux.

### <a name="example"></a>Exemple

```cpp
// map_op_gt.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   map < int, int > m1, m2, m3;
   int i;
   typedef pair < int, int > Int_Pair;

   for ( i = 0 ; i < 3 ; i++ )
   {
      m1.insert ( Int_Pair ( i, i ) );
      m2.insert ( Int_Pair ( i, i * i ) );
      m3.insert ( Int_Pair ( i, i - 1 ) );
   }

   if ( m1 > m2 )
      cout << "The map m1 is greater than the map m2." << endl;
   else
      cout << "The map m1 is not greater than the map m2." << endl;

   if ( m1 > m3 )
      cout << "The map m1 is greater than the map m3." << endl;
   else
      cout << "The map m1 is not greater than the map m3." << endl;
}
/* Output:
The map m1 is not greater than the map m2.
The map m1 is greater than the map m3.
*/
```

## <a name="operatorgt"></a><a name="op_gt_eq"></a>and&gt;=

Teste si l’objet map situé à gauche de l’opérateur est supérieur ou égal à l’objet map situé à droite.

```cpp
bool operator>=(
      const map <Key, Type, Traits, Allocator>& left,
      const map <Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>Paramètres

*gauche*\
Objet de type `map`.

*Oui*\
Objet de type `map`.

### <a name="return-value"></a>Valeur de retour

**`true`** Si la carte située à gauche de l’opérateur est supérieure ou égale à la carte située sur le côté droit de la liste ; Sinon, **`false`** .

### <a name="example"></a>Exemple

```cpp
// map_op_ge.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   map < int, int > m1, m2, m3, m4;
   int i;
   typedef pair < int, int > Int_Pair;

   for ( i = 1 ; i < 3 ; i++ )
   {
      m1.insert ( Int_Pair ( i, i ) );
      m2.insert ( Int_Pair ( i, i * i ) );
      m3.insert ( Int_Pair ( i, i - 1 ) );
      m4.insert ( Int_Pair ( i, i ) );
   }

   if ( m1 >= m2 )
      cout << "Map m1 is greater than or equal to map m2." << endl;
   else
      cout << "The map m1 is less than the map m2." << endl;

   if ( m1 >= m3 )
      cout << "Map m1 is greater than or equal to map m3." << endl;
   else
      cout << "The map m1 is less than the map m3." << endl;

   if ( m1 >= m4 )
      cout << "Map m1 is greater than or equal to map m4." << endl;
   else
      cout << "The map m1 is less than the map m4." << endl;
}
```

```Output
The map m1 is less than the map m2.
Map m1 is greater than or equal to map m3.
Map m1 is greater than or equal to map m4.
```

## <a name="operator-multimap"></a><a name="op_neq_multimap"></a>opérateur ! = (Multimap)

Teste si l’objet multimap situé à gauche de l’opérateur n’est pas égal à l’objet multimap situé à droite.

```cpp
bool operator!=(
      const multimap <Key, Type, Traits, Allocator>& left,
      const multimap <Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>Paramètres

*gauche*\
Objet de type `multimap`.

*Oui*\
Objet de type `multimap`.

### <a name="return-value"></a>Valeur de retour

**`true`** Si les multimappages ne sont pas égaux ; **`false`** si les multimappages sont égaux.

### <a name="remarks"></a>Notes

La comparaison entre les objets multimap est basée sur une comparaison par paire de leurs éléments. Deux multimaps sont égaux s’ils ont le même nombre d’éléments et si leurs éléments respectifs ont les mêmes valeurs. Sinon, elles sont inégales.

### <a name="example"></a>Exemple

```cpp
// multimap_op_ne.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   multimap <int, int> m1, m2, m3;
   int i;
   typedef pair <int, int> Int_Pair;

   for ( i = 0 ; i < 3 ; i++ )
   {
      m1.insert ( Int_Pair ( i, i ) );
      m2.insert ( Int_Pair ( i, i * i ) );
      m3.insert ( Int_Pair ( i, i ) );
   }

   if ( m1 != m2 )
      cout << "The multimaps m1 and m2 are not equal." << endl;
   else
      cout << "The multimaps m1 and m2 are equal." << endl;

   if ( m1 != m3 )
      cout << "The multimaps m1 and m3 are not equal." << endl;
   else
      cout << "The multimaps m1 and m3 are equal." << endl;
}
```

```Output
The multimaps m1 and m2 are not equal.
The multimaps m1 and m3 are equal.
```

## <a name="operatorlt"></a><a name="op_lt_multimap"></a>and&lt;

Teste si l’objet multimap situé à gauche de l’opérateur est inférieur à l’objet multimap situé à droite.

```cpp
bool operator<(
      const multimap <Key, Type, Traits, Allocator>& left,
      const multimap <Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>Paramètres

*gauche*\
Objet de type `multimap`.

*Oui*\
Objet de type `multimap`.

### <a name="return-value"></a>Valeur de retour

**`true`** Si le Multimap situé à gauche de l’opérateur est strictement inférieur au Multimap situé à droite de l’opérateur ; Sinon, **`false`** .

### <a name="remarks"></a>Notes

La comparaison entre les objets multimap est basée sur une comparaison par paire de leurs éléments. La relation d'infériorité entre deux objets est basée sur une comparaison de la première paire d'éléments inégaux.

### <a name="example"></a>Exemple

```cpp
// multimap_op_lt.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   multimap < int, int > m1, m2, m3;
   int i;
   typedef pair < int, int > Int_Pair;

   for ( i = 1 ; i < 3 ; i++ )
   {
      m1.insert ( Int_Pair ( i, i ) );
      m2.insert ( Int_Pair ( i, i * i ) );
      m3.insert ( Int_Pair ( i, i - 1 ) );
   }

   if ( m1 < m2 )
      cout << "The multimap m1 is less than the multimap m2." << endl;
   else
      cout << "The multimap m1 is not less than the multimap m2." << endl;

   if ( m1 < m3 )
      cout << "The multimap m1 is less than the multimap m3." << endl;
   else
      cout << "The multimap m1 is not less than the multimap m3." << endl;
}
```

```Output
The multimap m1 is less than the multimap m2.
The multimap m1 is not less than the multimap m3.
```

## <a name="operatorlt"></a><a name="op_lt_eq_multimap"></a>and&lt;=

Teste si l’objet multimap situé à gauche de l’opérateur est inférieur ou égal à l’objet multimap situé à droite.

```cpp
bool operator<=(
      const multimap <Key, Type, Traits, Allocator>& left,
      const multimap <Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>Paramètres

*gauche*\
Objet de type `multimap`.

*Oui*\
Objet de type `multimap`.

### <a name="return-value"></a>Valeur de retour

**`true`** Si le Multimap situé à gauche de l’opérateur est inférieur ou égal au Multimap situé à droite de l’opérateur ; Sinon, **`false`** .

### <a name="example"></a>Exemple

```cpp
// multimap_op_le.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   multimap <int, int> m1, m2, m3, m4;
   int i;
   typedef pair <int, int> Int_Pair;

   for ( i = 1 ; i < 3 ; i++ )
   {
      m1.insert ( Int_Pair ( i, i ) );
      m2.insert ( Int_Pair ( i, i * i ) );
      m3.insert ( Int_Pair ( i, i - 1 ) );
      m4.insert ( Int_Pair ( i, i ) );
   }

   if ( m1 <= m2 )
      cout << "m1 is less than or equal to m2" << endl;
   else
      cout << "m1 is greater than m2" << endl;

   if ( m1 <= m3 )
      cout << "m1 is less than or equal to m3" << endl;
   else
      cout << "m1 is greater than m3" << endl;

   if ( m1 <= m4 )
      cout << "m1 is less than or equal to m4" << endl;
   else
      cout << "m1 is greater than m4" << endl;
}
```

```Output
m1 is less than or equal to m2
m1 is greater than m3
m1 is less than or equal to m4
```

## <a name="operator"></a><a name="op_eq_eq_multimap"></a>opérateur = =

Teste si l’objet multimap situé à gauche de l’opérateur est égal à l’objet multimap situé à droite.

```cpp
bool operator==(
      const multimap <Key, Type, Traits, Allocator>& left,
      const multimap <Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>Paramètres

*gauche*\
Objet de type `multimap`.

*Oui*\
Objet de type `multimap`.

### <a name="return-value"></a>Valeur de retour

**`true`** Si le Multimap situé à gauche de l’opérateur est égal au Multimap situé à droite de l’opérateur ; Sinon, **`false`** .

### <a name="remarks"></a>Notes

La comparaison entre les objets multimap est basée sur une comparaison par paire de leurs éléments. Deux multimaps sont égaux s’ils ont le même nombre d’éléments et si leurs éléments respectifs ont les mêmes valeurs. Sinon, elles sont inégales.

### <a name="example"></a>Exemple

```cpp
// multimap_op_eq.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   multimap<int, int> m1, m2, m3;
   int i;
   typedef pair<int, int> Int_Pair;

   for (i = 0; i < 3; i++)
   {
      m1.insert(Int_Pair(i, i));
      m2.insert(Int_Pair(i, i*i));
      m3.insert(Int_Pair(i, i));
   }

   if ( m1 == m2 )
      cout << "m1 and m2 are equal" << endl;
   else
      cout << "m1 and m2 are not equal" << endl;

   if ( m1 == m3 )
      cout << "m1 and m3 are equal" << endl;
   else
      cout << "m1 and m3 are not equal" << endl;
}
```

```Output
m1 and m2 are not equal
m1 and m3 are equal
```

## <a name="operatorgt"></a><a name="op_gt_multimap"></a>and&gt;

Teste si l’objet multimap situé à gauche de l’opérateur est supérieur à l’objet multimap situé à droite.

```cpp
bool operator>(
      const multimap <Key, Type, Traits, Allocator>& left,
      const multimap <Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>Paramètres

*gauche*\
Objet de type `multimap`.

*Oui*\
Objet de type `multimap`.

### <a name="return-value"></a>Valeur de retour

**`true`** Si le Multimap situé à gauche de l’opérateur est supérieur au Multimap situé à droite de l’opérateur ; Sinon, **`false`** .

### <a name="remarks"></a>Notes

La comparaison entre les objets multimap est basée sur une comparaison par paire de leurs éléments. La relation de supériorité entre deux objets est basée sur une comparaison de la première paire d'éléments inégaux.

### <a name="example"></a>Exemple

```cpp
// multimap_op_gt.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   multimap < int, int > m1, m2, m3;
   int i;
   typedef pair < int, int > Int_Pair;

   for ( i = 0 ; i < 3 ; i++ )
   {
      m1.insert ( Int_Pair ( i, i ) );
      m2.insert ( Int_Pair ( i, i * i ) );
      m3.insert ( Int_Pair ( i, i - 1 ) );
   }

   if ( m1 > m2 )
      cout << "The multimap m1 is greater than the multimap m2." << endl;
   else
      cout << "Multimap m1 is not greater than multimap m2." << endl;

   if ( m1 > m3 )
      cout << "The multimap m1 is greater than the multimap m3." << endl;
   else
      cout << "The multimap m1 is not greater than the multimap m3." << endl;
}
```

```Output
Multimap m1 is not greater than multimap m2.
The multimap m1 is greater than the multimap m3.
```

## <a name="operatorgt"></a><a name="op_gt_eq_multimap"></a>and&gt;=

Teste si l’objet multimap situé à gauche de l’opérateur est supérieur ou égal à l’objet multimap situé à droite.

```cpp
bool operator>=(
      const multimap <Key, Type, Traits, Allocator>& left,
      const multimap <Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>Paramètres

*gauche*\
Objet de type `multimap`.

*Oui*\
Objet de type `multimap`.

### <a name="return-value"></a>Valeur de retour

**`true`** Si le Multimap situé à gauche de l’opérateur est supérieur ou égal au Multimap situé à droite de la liste ; Sinon, **`false`** .

### <a name="example"></a>Exemple

```cpp
// multimap_op_ge.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   multimap < int, int > m1, m2, m3, m4;
   int i;
   typedef pair < int, int > Int_Pair;

   for ( i = 1 ; i < 3 ; i++ )
   {
      m1.insert ( Int_Pair ( i, i ) );
      m2.insert ( Int_Pair ( i, i * i ) );
      m3.insert ( Int_Pair ( i, i - 1 ) );
      m4.insert ( Int_Pair ( i, i ) );
   }

   if ( m1 >= m2 )
      cout << "The multimap m1 is greater than or equal to the multimap m2." << endl;
   else
      cout << "The multimap m1 is less than the multimap m2." << endl;

   if ( m1 >= m3 )
      cout << "The multimap m1 is greater than or equal to the multimap m3." << endl;
   else
      cout << "The multimap m1 is less than the multimap m3." << endl;

   if ( m1 >= m4 )
      cout << "The multimap m1 is greater than or equal to the multimap m4." << endl;
   else
      cout << "The multimap m1 is less than the multimap m4." << endl;
}
```

```Output
The multimap m1 is less than the multimap m2.
The multimap m1 is greater than or equal to the multimap m3.
The multimap m1 is greater than or equal to the multimap m4.
```
