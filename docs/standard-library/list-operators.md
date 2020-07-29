---
title: '&lt;list&gt;, opérateurs'
ms.date: 11/04/2016
f1_keywords:
- list/std::operator!=
- list/std::operator&gt;
- list/std::operator&gt;=
- list/std::operator&lt;
- list/std::operator&lt;=
- list/std::operator==
ms.assetid: 8103d8f2-c30f-49ad-ac50-b3ba6a907ebe
helpviewer_keywords:
- std::operator!= (list)
- std::operator&gt; (list)
- std::operator&gt;= (list)
- std::operator&lt; (list)
- std::operator&lt;= (list)
- std::operator== (list)
ms.openlocfilehash: 8648258f17bff577ba1c0dde5016f5f284b82e25
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87224836"
---
# <a name="ltlistgt-operators"></a>&lt;list&gt;, opérateurs

## <a name="operator"></a><a name="op_neq"></a>opérateur ! =

Teste si l'objet de liste situé à gauche de l'opérateur n'est pas égal à l'objet de liste situé à droite.

```cpp
bool operator!=(
    const list<Type, Allocator>& left,
    const list<Type, Allocator>& right);
```

### <a name="parameters"></a>Paramètres

*gauche*\
Objet de type `list`.

*Oui*\
Objet de type `list`.

### <a name="return-value"></a>Valeur de retour

**`true`** Si les listes ne sont pas égales ; **`false`** si les listes sont égales.

### <a name="remarks"></a>Notes

La comparaison entre les objets de liste est basée sur une comparaison par paire de leurs éléments. Deux listes sont égales si elles ont le même nombre d'éléments et si leurs éléments respectifs ont les mêmes valeurs. Sinon, elles sont inégales.

### <a name="example"></a>Exemple

```cpp
// list_op_ne.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
using namespace std;
list <int> c1, c2;
c1.push_back( 1 );
c2.push_back( 2 );

if ( c1 != c2 )
cout << "Lists not equal." << endl;
else
cout << "Lists equal." << endl;
}
/* Output:
Lists not equal.
*/
```

## <a name="operatorlt"></a><a name="op_lt"></a>and&lt;

Teste si l'objet de liste situé à gauche de l'opérateur est inférieur à l'objet de liste situé à droite.

```cpp
bool operator<(
    const list<Type, Allocator>& left,
    const list<Type, Allocator>& right);
```

### <a name="parameters"></a>Paramètres

*gauche*\
Objet de type `list`.

*Oui*\
Objet de type `list`.

### <a name="return-value"></a>Valeur de retour

**`true`** Si la liste située à gauche de l’opérateur est inférieure mais pas égale à la liste située à droite de l’opérateur ; Sinon, **`false`** .

### <a name="remarks"></a>Notes

La comparaison entre les objets de liste est basée sur une comparaison par paire de leurs éléments. La relation d'infériorité entre deux objets est basée sur une comparaison de la première paire d'éléments inégaux.

### <a name="example"></a>Exemple

```cpp
// list_op_lt.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   list <int> c1, c2;
   c1.push_back( 1 );
   c1.push_back( 2 );
   c1.push_back( 4 );

   c2.push_back( 1 );
   c2.push_back( 3 );

   if ( c1 < c2 )
      cout << "List c1 is less than list c2." << endl;
   else
      cout << "List c1 is not less than list c2." << endl;
}
/* Output:
List c1 is less than list c2.
*/
```

## <a name="operatorlt"></a><a name="op_lt_eq"></a>and&lt;=

Teste si l'objet de liste situé à gauche de l'opérateur est inférieur ou égal à l'objet de liste situé à droite.

```cpp
bool operator<=(
    const list<Type, Allocator>& left,
    const list<Type, Allocator>& right);
```

### <a name="parameters"></a>Paramètres

*gauche*\
Objet de type `list`.

*Oui*\
Objet de type `list`.

### <a name="return-value"></a>Valeur de retour

**`true`** Si la liste située à gauche de l’opérateur est inférieure ou égale à la liste située à droite de l’opérateur ; Sinon, **`false`** .

### <a name="remarks"></a>Notes

La comparaison entre les objets de liste est basée sur une comparaison par paire de leurs éléments. La relation d'infériorité ou d'égalité entre deux objets est basée sur une comparaison de la première paire d'éléments inégaux.

### <a name="example"></a>Exemple

```cpp
// list_op_le.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   list <int> c1, c2;
   c1.push_back( 1 );
   c1.push_back( 2 );
   c1.push_back( 4 );

   c2.push_back( 1 );
   c2.push_back( 3 );

   if ( c1 <= c2 )
      cout << "List c1 is less than or equal to list c2." << endl;
   else
      cout << "List c1 is greater than list c2." << endl;
}
/* Output:
List c1 is less than or equal to list c2.
*/
```

## <a name="operator"></a><a name="op_eq_eq"></a>opérateur = =

Teste si l'objet de liste situé à gauche de l'opérateur est égal à l'objet de liste situé à droite.

```cpp
bool operator==(
    const list<Type, Allocator>& left,
    const list<Type, Allocator>& right);
```

### <a name="parameters"></a>Paramètres

*gauche*\
Objet de type `list`.

*Oui*\
Objet de type `list`.

### <a name="return-value"></a>Valeur de retour

**`true`** Si la liste située à gauche de l’opérateur est égale à la liste située à droite de l’opérateur ; Sinon, **`false`** .

### <a name="remarks"></a>Notes

La comparaison entre les objets de liste est basée sur une comparaison par paire de leurs éléments. Deux listes sont égales si elles ont le même nombre d'éléments et si leurs éléments respectifs ont les mêmes valeurs. Sinon, elles sont inégales.

### <a name="example"></a>Exemple

```cpp
// list_op_eq.cpp
// compile with: /EHsc
#include <list>
#include <iostream>
int main( )
{
   using namespace std;

   list <int> c1, c2;
   c1.push_back( 1 );
   c2.push_back( 1 );

   if ( c1 == c2 )
      cout << "The lists are equal." << endl;
   else
      cout << "The lists are not equal." << endl;
}
/* Output:
The lists are equal.
*/
```

## <a name="operatorgt"></a><a name="op_gt"></a>and&gt;

Teste si l'objet de liste situé à gauche de l'opérateur est supérieur à l'objet de liste situé à droite.

```cpp
bool operator>(
    const list<Type, Allocator>& left,
    const list<Type, Allocator>& right);
```

### <a name="parameters"></a>Paramètres

*gauche*\
Objet de type `list`.

*Oui*\
Objet de type `list`.

### <a name="return-value"></a>Valeur de retour

**`true`** Si la liste située à gauche de l’opérateur est supérieure à la liste située à droite de l’opérateur ; Sinon, **`false`** .

### <a name="remarks"></a>Notes

La comparaison entre les objets de liste est basée sur une comparaison par paire de leurs éléments. La relation de supériorité entre deux objets est basée sur une comparaison de la première paire d'éléments inégaux.

### <a name="example"></a>Exemple

```cpp
// list_op_gt.cpp
// compile with: /EHsc
#include <list>
#include <iostream>
int main( )
{
   using namespace std;
   list <int> c1, c2;
   c1.push_back( 1 );
   c1.push_back( 3 );
   c1.push_back( 1 );

   c2.push_back( 1 );
   c2.push_back( 2 );
   c2.push_back( 2 );

   if ( c1 > c2 )
      cout << "List c1 is greater than list c2." << endl;
   else
      cout << "List c1 is not greater than list c2." << endl;
}
/* Output:
List c1 is greater than list c2.
*/
```

## <a name="operatorgt"></a><a name="op_gt_eq"></a>and&gt;=

Teste si l'objet de liste situé à gauche de l'opérateur est supérieur ou égal à l'objet de liste situé à droite.

```cpp
bool operator>=(
    const list<Type, Allocator>& left,
    const list<Type, Allocator>& right);
```

### <a name="parameters"></a>Paramètres

*gauche*\
Objet de type `list`.

*Oui*\
Objet de type `list`.

### <a name="return-value"></a>Valeur de retour

**`true`** Si la liste située à gauche de l’opérateur est supérieure ou égale à la liste située à droite de l’opérateur ; Sinon, **`false`** .

### <a name="remarks"></a>Notes

La comparaison entre les objets de liste est basée sur une comparaison par paire de leurs éléments. La relation de supériorité ou d'égalité entre deux objets est basée sur une comparaison de la première paire d'éléments inégaux.

### <a name="example"></a>Exemple

```cpp
// list_op_ge.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   list <int> c1, c2;
   c1.push_back( 1 );
   c1.push_back( 3 );
   c1.push_back( 1 );

   c2.push_back( 1 );
   c2.push_back( 2 );
   c2.push_back( 2 );

   if ( c1 >= c2 )
      cout << "List c1 is greater than or equal to list c2." << endl;
   else
      cout << "List c1 is less than list c2." << endl;
}
/* Output:
List c1 is greater than or equal to list c2.
*/
```
