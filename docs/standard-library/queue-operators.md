---
title: '&lt;queue&gt;, opérateurs | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- queue/std::operator!=
- queue/std::operator&gt;
- queue/std::operator&gt;=
- queue/std::operator&lt;
- queue/std::operator&lt;=
- queue/std::operator==
dev_langs:
- C++
ms.assetid: 7c435b48-175c-45b0-88eb-24561044019c
helpviewer_keywords:
- std::operator!= (queue)
- std::operator&gt; (queue)
- std::operator&gt;= (queue)
- std::operator&lt; (queue)
- std::operator&lt;= (queue)
- std::operator== (queue)
ms.openlocfilehash: d2d8efe00e5fc03e882086e3c7cfa5c0b7f3ee0c
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44101065"
---
# <a name="ltqueuegt-operators"></a>&lt;queue&gt;, opérateurs

||||
|-|-|-|
|[operator!=](#op_neq)|[operator&gt;](#op_gt)|[operator&gt;=](#op_gt_eq)|
|[operator&lt;](#op_lt)|[operator&lt;=](#op_lt_eq)|[operator==](#op_eq_eq)|

## <a name="op_neq"></a>  operator!=

Teste si l'objet de file d'attente situé à gauche de l'opérateur n'est pas égal à l'objet de file d'attente situé à droite.

```cpp
bool operator!=(const queue <Type, Container>& left, const queue <Type, Container>& right,);
```

### <a name="parameters"></a>Paramètres

*left*<br/>
Objet de type `queue`.

*right*<br/>
Objet de type `queue`.

### <a name="return-value"></a>Valeur de retour

**true** si les objets queue ne sont pas égaux. **false** s’ils sont égaux.

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

## <a name="op_lt"></a>  operator&lt;

Teste si l'objet de file d'attente situé à gauche de l'opérateur est inférieur à l'objet de file d'attente situé à droite.

```cpp
bool operator<(const queue <Type, Container>& left, const queue <Type, Container>& right,);
```

### <a name="parameters"></a>Paramètres

*left*<br/>
Objet de type `queue`.

*right*<br/>
Objet de type `queue`.

### <a name="return-value"></a>Valeur de retour

**true** si l’objet queue à gauche de l’opérateur est strictement inférieur à l’objet queue à droite de l’opérateur. Sinon, **false**.

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

## <a name="op_lt_eq"></a>  operator&lt;=

Teste si l'objet de file d'attente situé à gauche de l'opérateur est inférieur ou égal à l'objet de file d'attente situé à droite.

```cpp
bool operator<=(const queue <Type, Container>& left, const queue <Type, Container>& right,);
```

### <a name="parameters"></a>Paramètres

*left*<br/>
Objet de type `queue`.

*right*<br/>
Objet de type `queue`.

### <a name="return-value"></a>Valeur de retour

**true** si l’objet queue situé à gauche de l’opérateur est strictement inférieur à l’objet queue situé à droite de l’opérateur. Sinon, **false**.

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

## <a name="op_eq_eq"></a>  operator==

Teste si l’objet queue situé à gauche de l’opérateur est égal à l’objet queue situé à droite.

```cpp
bool operator==(const queue <Type, Container>& left, const queue <Type, Container>& right,);
```

### <a name="parameters"></a>Paramètres

*left*<br/>
Objet de type `queue`.

*right*<br/>
Objet de type `queue`.

### <a name="return-value"></a>Valeur de retour

**true** si les objets queue ne sont pas égaux. **false** s’ils sont égaux.

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

## <a name="op_gt"></a>  operator&gt;

Teste si l'objet de file d'attente situé à gauche de l'opérateur est supérieur à l'objet de file d'attente situé à droite.

```cpp
bool operator>(const queue <Type, Container>& left, const queue <Type, Container>& right,);
```

### <a name="parameters"></a>Paramètres

*left*<br/>
Objet de type `queue`.

*right*<br/>
Objet de type `queue`.

### <a name="return-value"></a>Valeur de retour

**true** si l’objet queue situé à gauche de l’opérateur est strictement inférieur à l’objet queue situé à droite de l’opérateur. Sinon, **false**.

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

## <a name="op_gt_eq"></a>  operator&gt;=

Teste si l'objet de file d'attente situé à gauche de l'opérateur est supérieur ou égal à l'objet de file d'attente situé à droite.

```cpp
bool operator>=(const queue <Type, Container>& left, const queue <Type, Container>& right,);
```

### <a name="parameters"></a>Paramètres

*left*<br/>
Objet de type `queue`.

*right*<br/>
Objet de type `queue`.

### <a name="return-value"></a>Valeur de retour

**true** si l’objet queue situé à gauche de l’opérateur est strictement inférieur à l’objet queue situé à droite de l’opérateur. Sinon, **false**.

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

## <a name="see-also"></a>Voir aussi

[\<queue>](../standard-library/queue.md)<br/>
