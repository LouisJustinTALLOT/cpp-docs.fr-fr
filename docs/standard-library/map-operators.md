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
ms.openlocfilehash: e05aca75f527e1bc78912ab6b4b5a9de6dcd54c5
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/16/2019
ms.locfileid: "68246423"
---
# <a name="ltmapgt-operators"></a>&lt;map&gt;, opérateurs

## <a name="op_neq"></a>  operator!=

Teste si l’objet map situé à gauche de l’opérateur n’est pas égal à l’objet map situé à droite.

```cpp
bool operator!=(
      const map <Key, Type, Traits, Allocator>& left,
      const map <Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>Paramètres

*Gauche*\
Objet de type `map`.

*Oui*\
Objet de type `map`.

### <a name="return-value"></a>Valeur de retour

**true** si les mappages ne sont pas égaux ; **false** si les mappages sont égaux.

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

## <a name="op_lt"></a>, opérateur&lt;

Teste si l’objet map situé à gauche de l’opérateur est inférieur à l’objet map situé à droite.

```cpp
bool operator<(
      const map <Key, Type, Traits, Allocator>& left,
      const map <Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>Paramètres

*Gauche*\
Objet de type `map`.

*Oui*\
Objet de type `map`.

### <a name="return-value"></a>Valeur de retour

**true** si l’objet map situé à gauche de l’opérateur est strictement inférieur à l’objet map situé à droite de l’opérateur. Sinon, **false**.

### <a name="remarks"></a>Notes

La comparaison entre les objets map est basée sur une comparaison par paire de leurs éléments. La relation d'infériorité entre deux objets est basée sur une comparaison de la première paire d'éléments inégaux.

### <a name="example"></a>Exemples

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

## <a name="op_lt_eq"></a> Opérateur&lt;=

Teste si l’objet map situé à gauche de l’opérateur est inférieur ou égal à l’objet map situé à droite.

```cpp
bool operator<=(
      const map <Key, Type, Traits, Allocator>& left,
      const map <Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>Paramètres

*Gauche*\
Objet de type `map`.

*Oui*\
Objet de type `map`.

### <a name="return-value"></a>Valeur de retour

**true** si l’objet map situé à gauche de l’opérateur est inférieur ou égal à l’objet map situé à droite de l’opérateur. Sinon, **false**.

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

## <a name="op_eq_eq"></a> operator==

Teste si l’objet map situé à gauche de l’opérateur est égal à l’objet map situé à droite.

```cpp
bool operator==(
      const map <Key, Type, Traits, Allocator>& left,
      const map <Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>Paramètres

*Gauche*\
Objet de type `map`.

*Oui*\
Objet de type `map`.

### <a name="return-value"></a>Valeur de retour

**true** si l’objet map situé à gauche de l’opérateur est égal à l’objet map situé à droite de l’opérateur. Sinon, **false**.

### <a name="remarks"></a>Notes

La comparaison entre les objets map est basée sur une comparaison par paire de leurs éléments. Deux mappages sont égaux s’ils ont le même nombre d’éléments et si leurs éléments respectifs ont les mêmes valeurs. Sinon, elles sont inégales.

### <a name="example"></a>Exemples

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

## <a name="op_gt"></a>, opérateur&gt;

Teste si l’objet map situé à gauche de l’opérateur est supérieur à l’objet map situé à droite.

```cpp
bool operator>(
      const map <Key, Type, Traits, Allocator>& left,
      const map <Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>Paramètres

*Gauche*\
Objet de type `map`.

*Oui*\
Objet de type `map`.

### <a name="return-value"></a>Valeur de retour

**true** si l’objet map situé à gauche de l’opérateur est supérieur à l’objet map situé à droite de l’opérateur. Sinon, **false**.

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

## <a name="op_gt_eq"></a>  operator&gt;=

Teste si l’objet map situé à gauche de l’opérateur est supérieur ou égal à l’objet map situé à droite.

```cpp
bool operator>=(
      const map <Key, Type, Traits, Allocator>& left,
      const map <Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>Paramètres

*Gauche*\
Objet de type `map`.

*Oui*\
Objet de type `map`.

### <a name="return-value"></a>Valeur de retour

**true** si l’objet map situé à gauche de l’opérateur est supérieur ou égal à l’objet map situé à droite de l’opérateur. Sinon, **false**.

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

## <a name="op_neq_multimap"></a> opérateur ! = (multimap)

Teste si l’objet multimap situé à gauche de l’opérateur n’est pas égal à l’objet multimap situé à droite.

```cpp
bool operator!=(
      const multimap <Key, Type, Traits, Allocator>& left,
      const multimap <Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>Paramètres

*Gauche*\
Objet de type `multimap`.

*Oui*\
Objet de type `multimap`.

### <a name="return-value"></a>Valeur de retour

**true** si les multimaps ne sont pas égaux ; **false** si les multimaps sont égaux.

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

## <a name="op_lt_multimap"></a>, opérateur&lt;

Teste si l’objet multimap situé à gauche de l’opérateur est inférieur à l’objet multimap situé à droite.

```cpp
bool operator<(
      const multimap <Key, Type, Traits, Allocator>& left,
      const multimap <Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>Paramètres

*Gauche*\
Objet de type `multimap`.

*Oui*\
Objet de type `multimap`.

### <a name="return-value"></a>Valeur de retour

**true** si l’objet multimap situé à gauche de l’opérateur est strictement inférieur à l’objet multimap situé à droite de l’opérateur. Sinon, **false**.

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

<<<<<<< HEAD
## <a name="eq_multimap"></a> Opérateur&lt;=
=======
## <a name="op_lt_eq_multimap"></a>  operator&lt;=
>>>>>>> 009c7ce384664f2a62ffb0bc61d6586b585ed38a

Teste si l’objet multimap situé à gauche de l’opérateur est inférieur ou égal à l’objet multimap situé à droite.

```cpp
bool operator<=(
      const multimap <Key, Type, Traits, Allocator>& left,
      const multimap <Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>Paramètres

*Gauche*\
Objet de type `multimap`.

*Oui*\
Objet de type `multimap`.

### <a name="return-value"></a>Valeur de retour

**true** si l’objet multimap situé à gauche de l’opérateur est inférieur ou égal à l’objet multimap situé à droite de l’opérateur. Sinon, **false**.

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

## <a name="op_eq_eq_multimap"></a> operator==

Teste si l’objet multimap situé à gauche de l’opérateur est égal à l’objet multimap situé à droite.

```cpp
bool operator==(
      const multimap <Key, Type, Traits, Allocator>& left,
      const multimap <Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>Paramètres

*Gauche*\
Objet de type `multimap`.

*Oui*\
Objet de type `multimap`.

### <a name="return-value"></a>Valeur de retour

**true** si l’objet multimap situé à gauche de l’opérateur est égal à l’objet multimap situé à droite de l’opérateur. Sinon, **false**.

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

## <a name="op_gt_multimap"></a>, opérateur&gt;

Teste si l’objet multimap situé à gauche de l’opérateur est supérieur à l’objet multimap situé à droite.

```cpp
bool operator>(
      const multimap <Key, Type, Traits, Allocator>& left,
      const multimap <Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>Paramètres

*Gauche*\
Objet de type `multimap`.

*Oui*\
Objet de type `multimap`.

### <a name="return-value"></a>Valeur de retour

**true** si l’objet multimap situé à gauche de l’opérateur est supérieur à l’objet multimap situé à droite de l’opérateur. Sinon, **false**.

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

## <a name="op_gt_eq_multimap"></a> Opérateur&gt;=

Teste si l’objet multimap situé à gauche de l’opérateur est supérieur ou égal à l’objet multimap situé à droite.

```cpp
bool operator>=(
      const multimap <Key, Type, Traits, Allocator>& left,
      const multimap <Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>Paramètres

*Gauche*\
Objet de type `multimap`.

*Oui*\
Objet de type `multimap`.

### <a name="return-value"></a>Valeur de retour

**true** si le multimap situé à gauche de l’opérateur est supérieur ou égal au multimap situé à droite de la liste. Sinon, **false**.

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
