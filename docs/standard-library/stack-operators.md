---
title: '&lt;stack&gt;, opérateurs | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- stack/std::operator!=
- stack/std::operator&gt;
- stack/std::operator&gt;=
- stack/std::operator&lt;
- stack/std::operator&lt;=
- stack/std::operator==
dev_langs:
- C++
ms.assetid: 9c1fc282-2f61-4727-9e80-84ea5d4934a2
helpviewer_keywords:
- std::operator!= (stack)
- std::operator&gt; (stack)
- std::operator&gt;= (stack)
- std::operator&lt; (stack)
- std::operator&lt;= (stack)
- std::operator== (stack)
ms.openlocfilehash: 5c4e2f6b0b86e7b13c917eaf50d7f7dd0a55d9d6
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2018
ms.locfileid: "38955759"
---
# <a name="ltstackgt-operators"></a>&lt;stack&gt;, opérateurs

||||
|-|-|-|
|[operator!=](#op_neq)|[operator&gt;](#op_gt)|[operator&gt;=](#op_gt_eq)|
|[operator&lt;](#op_lt)|[operator&lt;=](#op_lt_eq)|[operator==](#op_eq_eq)|

## <a name="op_neq"></a>  operator!=

Vérifie si l’objet stack situé à gauche de l’opérateur n’est pas égal à l’objet stack situé à droite.

```cpp
bool operator!=(const stack <Type, Container>& left, const stack <Type, Container>& right,);
```

### <a name="parameters"></a>Paramètres

*gauche* un objet de type `stack`.

*droit* un objet de type `stack`.

### <a name="return-value"></a>Valeur de retour

**true** si les objets stack ne sont pas égaux. **false** s’ils sont égaux.

### <a name="remarks"></a>Notes

La comparaison entre les objets stack est basée sur une comparaison par paire de leurs éléments. Deux objets stack sont égaux s’ils ont le même nombre d’éléments et si leurs éléments respectifs ont les mêmes valeurs. Sinon, elles sont inégales.

### <a name="example"></a>Exemple

```cpp
// stack_op_me.cpp
// compile with: /EHsc
#include <stack>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;

   // Declares stacks with vector base containers
   stack <int, vector<int> > s1, s2, s3;

   // The following would have cause an error because stacks with
   // different base containers are not equality comparable
   // stack <int, list<int> >  s3;

   s1.push( 1 );
   s2.push( 2 );
   s3.push( 1 );

   if ( s1 != s2 )
      cout << "The stacks s1 and s2 are not equal." << endl;
   else
      cout << "The stacks s1 and s2 are equal." << endl;

   if ( s1 != s3 )
      cout << "The stacks s1 and s3 are not equal." << endl;
   else
      cout << "The stacks s1 and s3 are equal." << endl;
}
```

```Output
The stacks s1 and s2 are not equal.
The stacks s1 and s3 are equal.
```

## <a name="op_lt"></a>  operator&lt;

Teste si l'objet de pile situé à gauche de l'opérateur est inférieur à l'objet de pile situé à droite.

```cpp
bool operator<(const stack <Type, Container>& left, const stack <Type, Container>& right);
```

### <a name="parameters"></a>Paramètres

*gauche* un objet de type `stack`.

*droit* un objet de type `stack`.

### <a name="return-value"></a>Valeur de retour

**true** si l’objet stack à gauche de l’opérateur est strictement inférieur à l’objet stack à droite de l’opérateur. Sinon, **false**.

### <a name="remarks"></a>Notes

La comparaison entre les objets stack est basée sur une comparaison par paire de leurs éléments. La relation d’infériorité entre deux objets stack est basée sur une comparaison de la première paire d’éléments inégaux.

### <a name="example"></a>Exemple

```cpp
// stack_op_lt.cpp
// compile with: /EHsc
#include <stack>
#include <list>
#include <iostream>

int main( )
{
   using namespace std;

   // Declares stacks with list base container
   stack <int, list<int> > s1, s2, s3;

   s1.push( 2 );
   s1.push( 4 );
   s1.push( 6 );
   s1.push( 8 );
   s2.push( 5 );
   s2.push( 10 );
   s3.push( 2 );
   s3.push( 4 );
   s3.push( 6 );
   s3.push( 8 );

   if ( s1 >= s2 )
      cout << "The stack s1 is greater than or equal to "
           << "the stack s2." << endl;
   else
      cout << "The stack s1 is less than "
           << "the stack s2." << endl;

   if ( s1>= s3 )
      cout << "The stack s1 is greater than or equal to "
           << "the stack s3." << endl;
   else
      cout << "The stack s1 is less than "
           << "the stack s3." << endl;

   // to print out the stack s1 ( by unstacking the elements):
   stack <int>::size_type i_size_s1 = s1.size( );
   cout << "The stack s1 from the top down is: ( ";
   unsigned int i;
   for ( i = 1 ; i <= i_size_s1 ; i++ )
   {
      cout << s1.top( ) << " ";
      s1.pop( );
   }
   cout << ")." << endl;
}
```

```Output
The stack s1 is less than the stack s2.
The stack s1 is greater than or equal to the stack s3.
The stack s1 from the top down is: ( 8 6 4 2 ).
```

## <a name="op_lt_eq"></a>  operator&lt;=

Teste si l'objet de pile situé à gauche de l'opérateur est inférieur ou égal à l'objet de pile situé à droite.

```cpp
bool operator<=(const stack <Type, Container>& left, const stack <Type, Container>& right);
```

### <a name="parameters"></a>Paramètres

*gauche* un objet de type `stack`.

*droit* un objet de type `stack`.

### <a name="return-value"></a>Valeur de retour

**true** si l’objet stack à gauche de l’opérateur est inférieur ou égal à l’objet stack à droite de l’opérateur. Sinon, **false**.

### <a name="remarks"></a>Notes

La comparaison entre les objets stack est basée sur une comparaison par paire de leurs éléments. La relation d’infériorité ou d’égalité entre deux objets stack est basée sur une comparaison de la première paire d’éléments inégaux.

### <a name="example"></a>Exemple

```cpp
// stack_op_le.cpp
// compile with: /EHsc
#include <stack>
#include <iostream>

int main( )
{
   using namespace std;

   // Declares stacks with default deque base container
   stack <int> s1, s2, s3;

   s1.push( 5 );
   s1.push( 10 );
   s2.push( 1 );
   s2.push( 2 );
   s3.push( 5 );
   s3.push( 10 );

   if ( s1 <= s2 )
      cout << "The stack s1 is less than or equal to "
           << "the stack s2." << endl;
   else
      cout << "The stack s1 is greater than "
           << "the stack s2." << endl;

   if ( s1 <= s3 )
      cout << "The stack s1 is less than or equal to "
           << "the stack s3." << endl;
   else
      cout << "The stack s1 is greater than "
           << "the stack s3." << endl;
}
```

```Output
The stack s1 is greater than the stack s2.
The stack s1 is less than or equal to the stack s3.
```

## <a name="op_eq_eq"></a>  operator==

Vérifie si l’objet stack situé à gauche de l’opérateur est égal à l’objet stack situé à droite.

```cpp
bool operator==(const stack <Type, Container>& left, const stack <Type, Container>& right);
```

### <a name="parameters"></a>Paramètres

*gauche* un objet de type `stack`.

*droit* un objet de type `stack`.

### <a name="return-value"></a>Valeur de retour

**true** si les objets stack sont égaux. **false** s’ils ne sont pas égaux.

### <a name="remarks"></a>Notes

La comparaison entre les objets stack est basée sur une comparaison par paire de leurs éléments. Deux objets stack sont égaux s’ils ont le même nombre d’éléments et si leurs éléments respectifs ont les mêmes valeurs. Sinon, elles sont inégales.

### <a name="example"></a>Exemple

```cpp
// stack_op_eq.cpp
// compile with: /EHsc
#include <stack>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;

   // Declares stacks with vector base containers
   stack <int, vector<int> > s1, s2, s3;

   // The following would have cause an error because stacks with
   // different base containers are not equality comparable
   // stack <int, list<int> > s3;

   s1.push( 1 );
   s2.push( 2 );
   s3.push( 1 );

   if ( s1 == s2 )
      cout << "The stacks s1 and s2 are equal." << endl;
   else
      cout << "The stacks s1 and s2 are not equal." << endl;

   if ( s1 == s3 )
      cout << "The stacks s1 and s3 are equal." << endl;
   else
      cout << "The stacks s1 and s3 are not equal." << endl;
}
```

```Output
The stacks s1 and s2 are not equal.
The stacks s1 and s3 are equal.
```

## <a name="op_gt"></a>  operator&gt;

Teste si l'objet de pile situé à gauche de l'opérateur est supérieur à l'objet de pile situé à droite.

```cpp
bool operator>(const stack <Type, Container>& left, const stack <Type, Container>& right);
```

### <a name="parameters"></a>Paramètres

*gauche* un objet de type `stack`.

*droit* un objet de type `stack`.

### <a name="return-value"></a>Valeur de retour

**true** si l’objet stack à gauche de l’opérateur est supérieur à l’objet stack à droite de l’opérateur. Sinon, **false**.

### <a name="remarks"></a>Notes

La comparaison entre les objets stack est basée sur une comparaison par paire de leurs éléments. La relation de supériorité entre deux objets stack est basée sur une comparaison de la première paire d’éléments inégaux.

### <a name="example"></a>Exemple

```cpp
// stack_op_gt.cpp
// compile with: /EHsc
#include <stack>
#include <list>
#include <iostream>

int main( )
{
   using namespace std;

   // Declares stacks with list base container
   stack <int, list<int> > s1, s2, s3;

   s1.push( 1 );
   s1.push( 2 );
   s1.push( 3 );
   s2.push( 5 );
   s2.push( 10 );
   s3.push( 1 );
   s3.push( 2 );

   if ( s1 > s2 )
      cout << "The stack s1 is greater than "
           << "the stack s2." << endl;
   else
      cout << "The stack s1 is not greater than "
           << "the stack s2." << endl;

   if ( s1> s3 )
      cout << "The stack s1 is greater than "
           << "the stack s3." << endl;
   else
      cout << "The stack s1 is not greater than "
           << "the stack s3." << endl;
}
```

```Output
The stack s1 is not greater than the stack s2.
The stack s1 is greater than the stack s3.
```

## <a name="op_gt_eq"></a>  operator&gt;=

Teste si l'objet de pile situé à gauche de l'opérateur est supérieur ou égal à l'objet de pile situé à droite.

```cpp
bool operator>=(const stack <Type, Container>& left, const stack <Type, Container>& right);
```

### <a name="parameters"></a>Paramètres

*gauche* un objet de type `stack`.

*droit* un objet de type `stack`.

### <a name="return-value"></a>Valeur de retour

**true** si l’objet stack situé à gauche de l’opérateur est strictement inférieur à l’objet stack situé à droite de l’opérateur. Sinon, **false**.

### <a name="remarks"></a>Notes

La comparaison entre les objets stack est basée sur une comparaison par paire de leurs éléments. La relation de supériorité ou d’égalité entre deux objets stack est basée sur une comparaison de la première paire d’éléments inégaux.

### <a name="example"></a>Exemple

```cpp
// stack_op_ge.cpp
// compile with: /EHsc
#include <stack>
#include <list>
#include <iostream>

int main( )
{
   using namespace std;

   // Declares stacks with list base container
   stack <int, list<int> > s1, s2, s3;

   s1.push( 1 );
   s1.push( 2 );
   s2.push( 5 );
   s2.push( 10 );
   s3.push( 1 );
   s3.push( 2 );

   if ( s1 >= s2 )
      cout << "The stack s1 is greater than or equal to "
           << "the stack s2." << endl;
   else
      cout << "The stack s1 is less than "
           << "the stack s2." << endl;

   if ( s1>= s3 )
      cout << "The stack s1 is greater than or equal to "
           << "the stack s3." << endl;
   else
      cout << "The stack s1 is less than "
           << "the stack s3." << endl;
}
```

```Output
The stack s1 is less than the stack s2.
The stack s1 is greater than or equal to the stack s3.
```

## <a name="see-also"></a>Voir aussi

[\<stack>](../standard-library/stack.md)<br/>
