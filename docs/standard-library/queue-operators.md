---
description: 'En savoir plus sur : &lt; opérateurs de file d’attente &gt;'
title: '&lt;queue&gt;, opérateurs'
ms.date: 11/04/2016
f1_keywords:
- queue/std::operator!=
- queue/std::operator&gt;
- queue/std::operator&gt;=
- queue/std::operator&lt;
- queue/std::operator&lt;=
- queue/std::operator==
ms.assetid: 7c435b48-175c-45b0-88eb-24561044019c
helpviewer_keywords:
- std::operator!= (queue)
- std::operator&gt; (queue)
- std::operator&gt;= (queue)
- std::operator&lt; (queue)
- std::operator&lt;= (queue)
- std::operator== (queue)
ms.openlocfilehash: 6d6280ca4fe1e1277a79862a5016d55dfbecc425
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97327579"
---
# <a name="ltqueuegt-operators"></a>&lt;queue&gt;, opérateurs

## <a name="operator"></a><a name="op_neq"></a> opérateur ! =

Teste si l'objet de file d'attente situé à gauche de l'opérateur n'est pas égal à l'objet de file d'attente situé à droite.

```cpp
bool operator!=(const queue <Type, Container>& left, const queue <Type, Container>& right,);
```

### <a name="parameters"></a>Paramètres

*gauche*\
Objet de type `queue`.

*Oui*\
Objet de type `queue`.

### <a name="return-value"></a>Valeur renvoyée

**`true`** Si les files d’attente ne sont pas égales ; **`false`** si les files d’attente sont égales.

### <a name="remarks"></a>Notes

La comparaison entre les objets queue est basée sur une comparaison par paire de leurs éléments. Deux objets queue sont égaux s’ils ont le même nombre d’éléments et si leurs éléments respectifs ont les mêmes valeurs. Sinon, elles sont inégales.

### <a name="example"></a>Exemple

```cpp
// queue_op_ne.cpp
// compile with: /EHsc
#include <queue>
#include <list>
#include <iostream>

int main( )
{
   using namespace std;

   // Declares queues with list base containers
   queue <int, list<int> > q1, q2, q3;

   // The following line would have caused an error because vector
   // does not support pop_front( ) and so cannot be adapted
   // by queue as a base container
   // queue <int, vector<int> > q1, q2, q3;

   q1.push( 1 );
   q2.push( 1 );
   q2.push( 2 );
   q3.push( 1 );

   if ( q1 != q2 )
      cout << "The queues q1 and q2 are not equal." << endl;
   else
      cout << "The queues q1 and q2 are equal." << endl;

   if ( q1 != q3 )
      cout << "The queues q1 and q3 are not equal." << endl;
   else
      cout << "The queues q1 and q3 are equal." << endl;
}
```

```Output
The queues q1 and q2 are not equal.
The queues q1 and q3 are equal.
```

## <a name="operatorlt"></a><a name="op_lt"></a> and&lt;

Teste si l'objet de file d'attente situé à gauche de l'opérateur est inférieur à l'objet de file d'attente situé à droite.

```cpp
bool operator<(const queue <Type, Container>& left, const queue <Type, Container>& right,);
```

### <a name="parameters"></a>Paramètres

*gauche*\
Objet de type `queue`.

*Oui*\
Objet de type `queue`.

### <a name="return-value"></a>Valeur renvoyée

**`true`** Si la file d’attente située à gauche de l’opérateur est inférieure et non égale à la file d’attente située à droite de l’opérateur ; Sinon, **`false`** .

### <a name="remarks"></a>Notes

La comparaison entre les objets queue est basée sur une comparaison par paire de leurs éléments. La relation d’infériorité entre deux objets queue est basée sur une comparaison de la première paire d’éléments inégaux.

### <a name="example"></a>Exemple

```cpp
// queue_op_lt.cpp
// compile with: /EHsc
#include <queue>
#include <iostream>

int main( )
{
   using namespace std;

   // Declares queues with default deque base container
   queue <int> q1, q2, q3;

   q1.push( 1 );
   q1.push( 2 );
   q2.push( 5 );
   q2.push( 10 );
   q3.push( 1 );
   q3.push( 2 );

   if ( q1 < q2 )
      cout << "The queue q1 is less than the queue q2." << endl;
   else
      cout << "The queue q1 is not less than the queue q2." << endl;

   if ( q1 < q3 )
      cout << "The queue q1 is less than the queue q3." << endl;
   else
      cout << "The queue q1 is not less than the queue q3." << endl;
}
```

```Output
The queue q1 is less than the queue q2.
The queue q1 is not less than the queue q3.
```

## <a name="operatorlt"></a><a name="op_lt_eq"></a> and&lt;=

Teste si l'objet de file d'attente situé à gauche de l'opérateur est inférieur ou égal à l'objet de file d'attente situé à droite.

```cpp
bool operator<=(const queue <Type, Container>& left, const queue <Type, Container>& right,);
```

### <a name="parameters"></a>Paramètres

*gauche*\
Objet de type `queue`.

*Oui*\
Objet de type `queue`.

### <a name="return-value"></a>Valeur renvoyée

**`true`** Si la file d’attente située à gauche de l’opérateur est strictement inférieure à la file d’attente du côté droit de l’opérateur ; Sinon, **`false`** .

### <a name="remarks"></a>Notes

La comparaison entre les objets queue est basée sur une comparaison par paire de leurs éléments. La relation d’infériorité ou d’égalité entre deux objets queue est basée sur une comparaison de la première paire d’éléments inégaux.

### <a name="example"></a>Exemple

```cpp
// queue_op_le.cpp
// compile with: /EHsc
#include <queue>
#include <iostream>

int main( )
{
   using namespace std;
   queue <int> q1, q2, q3;

   q1.push( 5 );
   q1.push( 10 );
   q2.push( 1 );
   q2.push( 2 );
   q3.push( 5 );
   q3.push( 10 );

   if ( q1 <= q2 )
      cout << "The queue q1 is less than or equal to "
           << "the queue q2." << endl;
   else
      cout << "The queue q1 is greater than "
           << "the queue q2." << endl;

   if ( q1 <= q3 )
      cout << "The queue q1 is less than or equal to "
           << "the queue q3." << endl;
   else
      cout << "The queue q1 is greater than "
           << "the queue q3." << endl;
}
```

```Output
The queue q1 is greater than the queue q2.
The queue q1 is less than or equal to the queue q3.
```

## <a name="operator"></a><a name="op_eq_eq"></a> opérateur = =

Teste si l’objet queue situé à gauche de l’opérateur est égal à l’objet queue situé à droite.

```cpp
bool operator==(const queue <Type, Container>& left, const queue <Type, Container>& right,);
```

### <a name="parameters"></a>Paramètres

*gauche*\
Objet de type `queue`.

*Oui*\
Objet de type `queue`.

### <a name="return-value"></a>Valeur renvoyée

**`true`** Si les files d’attente ne sont pas égales ; **`false`** si les files d’attente sont égales.

### <a name="remarks"></a>Notes

La comparaison entre les objets queue est basée sur une comparaison par paire de leurs éléments. Deux objets queue sont égaux s’ils ont le même nombre d’éléments et si leurs éléments respectifs ont les mêmes valeurs. Sinon, elles sont inégales.

### <a name="example"></a>Exemple

```cpp
// queue_op_eq.cpp
// compile with: /EHsc
#include <queue>
#include <list>
#include <iostream>

int main( )
{
   using namespace std;

   // Declares queues with list base containers
   queue <int, list<int> > q1, q2, q3;

   // The following line would have caused an error because vector
   // does not support pop_front( ) and so cannot be adapted
   // by queue as a base container
   // queue <int, vector<int> > q1, q2, q3;

   q1.push( 1 );
   q2.push( 2 );
   q3.push( 1 );

   if ( q1 != q2 )
      cout << "The queues q1 and q2 are not equal." << endl;
   else
      cout << "The queues q1 and q2 are equal." << endl;

   if ( q1 != q3 )
      cout << "The queues q1 and q3 are not equal." << endl;
   else
      cout << "The queues q1 and q3 are equal." << endl;
}
```

```Output
The queues q1 and q2 are not equal.
The queues q1 and q3 are equal.
```

## <a name="operatorgt"></a><a name="op_gt"></a> and&gt;

Teste si l'objet de file d'attente situé à gauche de l'opérateur est supérieur à l'objet de file d'attente situé à droite.

```cpp
bool operator>(const queue <Type, Container>& left, const queue <Type, Container>& right,);
```

### <a name="parameters"></a>Paramètres

*gauche*\
Objet de type `queue`.

*Oui*\
Objet de type `queue`.

### <a name="return-value"></a>Valeur renvoyée

**`true`** Si la file d’attente située à gauche de l’opérateur est strictement inférieure à la file d’attente du côté droit de l’opérateur ; Sinon, **`false`** .

### <a name="remarks"></a>Notes

La comparaison entre les objets queue est basée sur une comparaison par paire de leurs éléments. La relation de supériorité entre deux objets queue est basée sur une comparaison de la première paire d’éléments inégaux.

### <a name="example"></a>Exemple

```cpp
// queue_op_gt.cpp
// compile with: /EHsc
#include <queue>
#include <iostream>

int main( )
{
   using namespace std;
   queue <int> q1, q2, q3;

   q1.push( 1 );
   q1.push( 2 );
   q1.push( 3 );
   q2.push( 5 );
   q2.push( 10 );
   q3.push( 1 );
   q3.push( 2 );

   if ( q1 > q2 )
      cout << "The queue q1 is greater than "
           << "the queue q2." << endl;
   else
      cout << "The queue q1 is not greater than "
           << "the queue q2." << endl;

   if ( q1> q3 )
      cout << "The queue q1 is greater than "
           << "the queue q3." << endl;
   else
      cout << "The queue q1 is not greater than "
           << "the queue q3." << endl;
}
```

```Output
The queue q1 is not greater than the queue q2.
The queue q1 is greater than the queue q3.
```

## <a name="operatorgt"></a><a name="op_gt_eq"></a> and&gt;=

Teste si l'objet de file d'attente situé à gauche de l'opérateur est supérieur ou égal à l'objet de file d'attente situé à droite.

```cpp
bool operator>=(const queue <Type, Container>& left, const queue <Type, Container>& right,);
```

### <a name="parameters"></a>Paramètres

*gauche*\
Objet de type `queue`.

*Oui*\
Objet de type `queue`.

### <a name="return-value"></a>Valeur renvoyée

**`true`** Si la file d’attente située à gauche de l’opérateur est strictement inférieure à la file d’attente du côté droit de l’opérateur ; Sinon, **`false`** .

### <a name="remarks"></a>Notes

La comparaison entre les objets queue est basée sur une comparaison par paire de leurs éléments. Deux objets queue sont égaux s’ils ont le même nombre d’éléments et si leurs éléments respectifs ont les mêmes valeurs. Sinon, elles sont inégales.

### <a name="example"></a>Exemple

```cpp
// queue_op_ge.cpp
// compile with: /EHsc
#include <queue>
#include <iostream>

int main( )
{
   using namespace std;
   queue <int> q1, q2, q3;

   q1.push( 1 );
   q1.push( 2 );
   q2.push( 5 );
   q2.push( 10 );
   q3.push( 1 );
   q3.push( 2 );

   if ( q1 >= q2 )
      cout << "The queue q1 is greater than or equal to "
           << "the queue q2." << endl;
   else
      cout << "The queue q1 is less than "
           << "the queue q2." << endl;

   if ( q1>= q3 )
      cout << "The queue q1 is greater than or equal to "
           << "the queue q3." << endl;
   else
      cout << "The queue q1 is less than "
           << "the queue q3." << endl;
}
```

```Output
The queue q1 is less than the queue q2.
The queue q1 is greater than or equal to the queue q3.
```
