---
title: '&lt;utility&gt;, opérateurs'
ms.date: 11/04/2016
f1_keywords:
- utility/std::operator!=
- utility/std::operator&gt;
- utility/std::operator&gt;=
- utility/std::operator&lt;
- utility/std::operator&lt;=
- utility/std::operator==
ms.assetid: a6617109-2cec-4a69-948f-6c87116eda5f
helpviewer_keywords:
- std::operator!= (utility)
- std::operator&gt; (utility)
- std::operator&gt;= (utility)
- std::operator&lt; (utility)
- std::operator&lt;= (utility)
- std::operator== (utility)
ms.openlocfilehash: ec6c996487dc2e6c5ce628fe5e080b4f601479d9
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/06/2020
ms.locfileid: "78854859"
---
# <a name="ltutilitygt-operators"></a>&lt;utility&gt;, opérateurs

> [!NOTE]
> Les opérateurs qui utilisent `Type&` sont inclus sous `namespace rel_ops`.

## <a name="op_neq"></a>opérateur ! =

Teste si l'objet pair situé à gauche de l'opérateur n'est pas égal à l'objet pair situé à droite.

```cpp
template <class Type>
    constexpr bool operator!=(const Type& left, const Type& right);

template <class T, class U>
    constexpr bool operator!=(const pair<T, U>& left, const pair<T, U>& right);
```

### <a name="parameters"></a>Paramètres

\ *gauche*
Objet de type `pair`.

\ *droit*
Objet de type `pair`.

### <a name="return-value"></a>Valeur de retour

**true** si les paires ne sont pas égales ; **false** si les paires sont égales.

### <a name="remarks"></a>Notes

Une paire est égale à une autre paire si chacun de leurs éléments respectifs sont égaux. Deux paires sont inégales si le premier ou le deuxième élément de l'une n'est pas égal à l'élément correspondant de l'autre paire.

### <a name="example"></a>Exemple

```cpp
// utility_op_ne.cpp
// compile with: /EHsc
#include <utility>
#include <iomanip>
#include <iostream>

int main( )
{
   using namespace std;
   pair <int, double> p1, p2, p3;

   p1 = make_pair ( 10, 1.11e-1 );
   p2 = make_pair ( 1000, 1.11e-3 );
   p3 = make_pair ( 10, 1.11e-1 );

   cout.precision ( 3 );
   cout << "The pair p1 is: ( " << p1.first << ", "
        << p1.second << " )." << endl;
   cout << "The pair p2 is: ( " << p2.first << ", "
        << p2.second << " )." << endl;
   cout << "The pair p3 is: ( " << p3.first << ", "
        << p3.second << " )." << endl << endl;

   if ( p1 != p2 )
      cout << "The pairs p1 and p2 are not equal." << endl;
   else
      cout << "The pairs p1 and p2 are equal." << endl;

   if ( p1 != p3 )
      cout << "The pairs p1 and p3 are not equal." << endl;
   else
      cout << "The pairs p1 and p3 are equal." << endl;
}
```

```Output
The pair p1 is: ( 10, 0.111 ).
The pair p2 is: ( 1000, 0.00111 ).
The pair p3 is: ( 10, 0.111 ).

The pairs p1 and p2 are not equal.
The pairs p1 and p3 are equal.
```

## <a name="op_eq_eq"></a>opérateur = =

Teste si l'objet pair situé à gauche de l'opérateur est égal à l'objet pair situé à droite.

```cpp
template <class T, class U>
constexpr bool operator==(const pair<T, U>& left, const pair<T, U>& right);
```

### <a name="parameters"></a>Paramètres

\ *gauche*
Objet de type `pair`.

\ *droit*
Objet de type `pair`.

### <a name="return-value"></a>Valeur de retour

**true** si les paires sont égales ; **false** si les objets `pair` ne sont pas égaux.

### <a name="remarks"></a>Notes

Une paire est égale à une autre paire si chacun de leurs éléments respectifs sont égaux. La fonction retourne `left`. **premier** == `right`. **premier** && `left`. **second** == `right`. **second**. Deux paires sont inégales si le premier ou le deuxième élément de l'une n'est pas égal à l'élément correspondant de l'autre paire.

### <a name="example"></a>Exemple

```cpp
// utility_op_eq.cpp
// compile with: /EHsc
#include <utility>
#include <iomanip>
#include <iostream>

int main( )
{
   using namespace std;
   pair <int, double> p1, p2, p3;

   p1 = make_pair ( 10, 1.11e-1 );
   p2 = make_pair ( 1000, 1.11e-3 );
   p3 = make_pair ( 10, 1.11e-1 );

   cout.precision ( 3 );
   cout << "The pair p1 is: ( " << p1.first << ", "
        << p1.second << " )." << endl;
   cout << "The pair p2 is: ( " << p2.first << ", "
        << p2.second << " )." << endl;
   cout << "The pair p3 is: ( " << p3.first << ", "
        << p3.second << " )." << endl << endl;

   if ( p1 == p2 )
      cout << "The pairs p1 and p2 are equal." << endl;
   else
      cout << "The pairs p1 and p2 are not equal." << endl;

   if ( p1 == p3 )
      cout << "The pairs p1 and p3 are equal." << endl;
   else
      cout << "The pairs p1 and p3 are not equal." << endl;
}
```

## <a name="op_lt"></a>, opérateur&lt;

Teste si l'objet pair situé à gauche de l'opérateur est inférieur à l'objet pair situé à droite.

```cpp
template <class T, class U>
constexpr bool operator<(const pair<T, U>& left, const pair<T, U>& right);
```

### <a name="parameters"></a>Paramètres

\ *gauche*
Objet de type `pair` situé à gauche de l'opérateur.

\ *droit*
Objet de type `pair` situé à droite de l'opérateur.

### <a name="return-value"></a>Valeur de retour

**true** si l’objet `pair` situé à gauche de l’opérateur est strictement inférieur à l’objet `pair` situé à droite de l’opérateur ; sinon, **false**.

### <a name="remarks"></a>Notes

L’objet `left` `pair` est dit qu’il est strictement inférieur à l’objet `pair` `right` si *Left* est inférieur à et différent de *Right*.

Dans une comparaison de paires, le premier élément des valeurs des deux paires a la priorité la plus élevée. Si elles diffèrent, le résultat de leur comparaison est pris comme résultat de la comparaison de la paire. Si les valeurs des premiers éléments ne sont pas différentes, les valeurs des deuxièmes éléments sont comparées et le résultat de leur comparaison est pris comme résultat de la comparaison de la paire.

### <a name="example"></a>Exemple

```cpp
// utility_op_lt.cpp
// compile with: /EHsc
#include <utility>
#include <iomanip>
#include <iostream>

int main( )
{
   using namespace std;
   pair <int, double> p1, p2, p3;

   p1 = make_pair ( 10, 2.22e-1 );
   p2 = make_pair ( 100, 1.11e-1 );
   p3 = make_pair ( 10, 1.11e-1 );

   cout.precision ( 3 );
   cout << "The pair p1 is: ( " << p1.first << ", "
        << p1.second << " )." << endl;
   cout << "The pair p2 is: ( " << p2.first << ", "
        << p2.second << " )." << endl;
   cout << "The pair p3 is: ( " << p3.first << ", "
        << p3.second << " )." << endl << endl;

   if ( p1 < p2 )
      cout << "The pair p1 is less than the pair p2." << endl;
   else
      cout << "The pair p1 is not less than the pair p2." << endl;

   if ( p1 < p3 )
      cout << "The pair p1 is less than the pair p3." << endl;
   else
      cout << "The pair p1 is not less than the pair p3." << endl;
}
```

```Output
The pair p1 is: ( 10, 0.222 ).
The pair p2 is: ( 100, 0.111 ).
The pair p3 is: ( 10, 0.111 ).

The pair p1 is less than the pair p2.
The pair p1 is not less than the pair p3.
```

## <a name="op_lt_eq"></a>&lt;d’opérateur =

Teste si l'objet pair situé à gauche de l'opérateur est inférieur ou égal à l'objet pair situé à droite.

```cpp
template <class Type>
constexpr bool operator<=(const Type& left, const Type& right);

template <class T, class U>
constexpr bool operator<=(const pair<T, U>& left, const pair<T, U>& right);
```

### <a name="parameters"></a>Paramètres

\ *gauche*
Objet de type `pair` situé à gauche de l'opérateur.

\ *droit*
Objet de type `pair` situé à droite de l'opérateur.

### <a name="return-value"></a>Valeur de retour

**true** si l’objet `pair` situé à gauche de l’opérateur est inférieur ou égal à l’objet `pair` situé à droite de l’opérateur ; sinon, **false**.

### <a name="remarks"></a>Notes

Dans une comparaison de paires, le premier élément des valeurs des deux paires a la priorité la plus élevée. Si elles diffèrent, le résultat de leur comparaison est pris comme résultat de la comparaison de la paire. Si les valeurs des premiers éléments ne sont pas différentes, les valeurs des deuxièmes éléments sont comparées et le résultat de leur comparaison est pris comme résultat de la comparaison de la paire.

### <a name="example"></a>Exemple

```cpp
// utility_op_le.cpp
// compile with: /EHsc
#include <utility>
#include <iomanip>
#include <iostream>

int main( )
{
   using namespace std;
   pair <int, double> p1, p2, p3, p4;

   p1 = make_pair ( 10, 2.22e-1 );
   p2 = make_pair ( 100, 1.11e-1 );
   p3 = make_pair ( 10, 1.11e-1 );
   p4 = make_pair ( 10, 2.22e-1 );

   cout.precision ( 3 );
   cout << "The pair p1 is: ( " << p1.first << ", "
        << p1.second << " )." << endl;
   cout << "The pair p2 is: ( " << p2.first << ", "
        << p2.second << " )." << endl;
   cout << "The pair p3 is: ( " << p3.first << ", "
        << p3.second << " )." << endl;
   cout << "The pair p4 is: ( " << p4.first << ", "
        << p4.second << " )." << endl << endl;

   if ( p1 <= p2 )
      cout << "The pair p1 is less than or equal to the pair p2." << endl;
   else
      cout << "The pair p1 is greater than the pair p2." << endl;

   if ( p1 <= p3 )
      cout << "The pair p1 is less than or equal to the pair p3." << endl;
   else
      cout << "The pair p1 is greater than the pair p3." << endl;

   if ( p1 <= p4 )
      cout << "The pair p1 is less than or equal to the pair p4." << endl;
   else
      cout << "The pair p1 is greater than the pair p4." << endl;
}
```

```Output
The pair p1 is: ( 10, 0.222 ).
The pair p2 is: ( 100, 0.111 ).
The pair p3 is: ( 10, 0.111 ).
The pair p4 is: ( 10, 0.222 ).

The pair p1 is less than or equal to the pair p2.
The pair p1 is greater than the pair p3.
The pair p1 is less than or equal to the pair p4.
```

## <a name="op_gt"></a>, opérateur&gt;

Teste si l'objet pair situé à gauche de l'opérateur est supérieur à l'objet pair situé à droite.

```cpp
template <class Type>
constexpr bool operator>(const Type& left, const Type& right);

template <class T, class U>
constexpr bool operator>(const pair<T, U>& left, const pair<T, U>& right);
```

### <a name="parameters"></a>Paramètres

\ *gauche*
Objet de type `pair` situé à gauche de l'opérateur.

\ *droit*
Objet de type `pair` situé à droite de l'opérateur.

### <a name="return-value"></a>Valeur de retour

**true** si l’objet `pair` situé à gauche de l’opérateur est strictement supérieur à l’objet `pair` situé à droite de l’opérateur ; sinon, **false**.

### <a name="remarks"></a>Notes

L’objet `left` `pair` est dit qu’il est strictement supérieur à l’objet `pair` `right` si *Left* est supérieur et différent de *Right*.

Dans une comparaison de paires, le premier élément des valeurs des deux paires a la priorité la plus élevée. Si elles diffèrent, le résultat de leur comparaison est pris comme résultat de la comparaison de la paire. Si les valeurs des premiers éléments ne sont pas différentes, les valeurs des deuxièmes éléments sont comparées et le résultat de leur comparaison est pris comme résultat de la comparaison de la paire.

### <a name="example"></a>Exemple

```cpp
// utility_op_gt.cpp
// compile with: /EHsc
#include <utility>
#include <iomanip>
#include <iostream>

int main( )
{
   using namespace std;
   pair <int, double> p1, p2, p3, p4;

   p1 = make_pair ( 10, 2.22e-1 );
   p2 = make_pair ( 100, 1.11e-1 );
   p3 = make_pair ( 10, 1.11e-1 );
   p4 = make_pair ( 10, 2.22e-1 );

   cout.precision ( 3 );
   cout << "The pair p1 is: ( " << p1.first << ", "
        << p1.second << " )." << endl;
   cout << "The pair p2 is: ( " << p2.first << ", "
        << p2.second << " )." << endl;
   cout << "The pair p3 is: ( " << p3.first << ", "
        << p3.second << " )." << endl;
   cout << "The pair p4 is: ( " << p4.first << ", "
        << p4.second << " )." << endl << endl;

   if ( p1 > p2 )
      cout << "The pair p1 is greater than the pair p2." << endl;
   else
      cout << "The pair p1 is not greater than the pair p2." << endl;

   if ( p1 > p3 )
      cout << "The pair p1 is greater than the pair p3." << endl;
   else
      cout << "The pair p1 is not greater than the pair p3." << endl;

   if ( p1 > p4 )
      cout << "The pair p1 is greater than the pair p4." << endl;
   else
      cout << "The pair p1 is not greater than the pair p4." << endl;
}
```

```Output
The pair p1 is: ( 10, 0.222 ).
The pair p2 is: ( 100, 0.111 ).
The pair p3 is: ( 10, 0.111 ).
The pair p4 is: ( 10, 0.222 ).

The pair p1 is not greater than the pair p2.
The pair p1 is greater than the pair p3.
The pair p1 is not greater than the pair p4.
```

## <a name="op_gt_eq"></a>&gt;d’opérateur =

Teste si l'objet pair situé à gauche de l'opérateur est supérieur ou égal à l'objet pair situé à droite.

```cpp
template <class Type>
    constexpr bool operator>=(const Type& left, const Type& right);

template <class T, class U>
    constexpr bool operator>=(const pair<T, U>& left, const pair<T, U>& right);
```

### <a name="parameters"></a>Paramètres

\ *gauche*
Objet de type `pair` situé à gauche de l'opérateur.

\ *droit*
Objet de type `pair` situé à droite de l'opérateur.

### <a name="return-value"></a>Valeur de retour

**true** si l’objet `pair` situé à gauche de l’opérateur est supérieur ou égal à l’objet `pair` situé à droite de l’opérateur ; sinon, **false**.

### <a name="remarks"></a>Notes

Dans une comparaison de paires, le premier élément des valeurs des deux paires a la priorité la plus élevée. Si elles diffèrent, le résultat de leur comparaison est pris comme résultat de la comparaison de la paire. Si les valeurs des premiers éléments ne sont pas différentes, les valeurs des deuxièmes éléments sont comparées et le résultat de leur comparaison est pris comme résultat de la comparaison de la paire.

### <a name="example"></a>Exemple

```cpp
// utility_op_ge.cpp
// compile with: /EHsc
#include <utility>
#include <iomanip>
#include <iostream>

int main( )
{
   using namespace std;
   pair <int, double> p1, p2, p3, p4;

   p1 = make_pair ( 10, 2.22e-1 );
   p2 = make_pair ( 100, 1.11e-1 );
   p3 = make_pair ( 10, 1.11e-1 );
   p4 = make_pair ( 10, 2.22e-1 );

   cout.precision ( 3 );
   cout << "The pair p1 is: ( " << p1.first << ", "
        << p1.second << " )." << endl;
   cout << "The pair p2 is: ( " << p2.first << ", "
        << p2.second << " )." << endl;
   cout << "The pair p3 is: ( " << p3.first << ", "
        << p3.second << " )." << endl;
   cout << "The pair p4 is: ( " << p4.first << ", "
        << p4.second << " )." << endl << endl;

   if ( p1 >= p2 )
      cout << "Pair p1 is greater than or equal to pair p2." << endl;
   else
      cout << "The pair p1 is less than the pair p2." << endl;

   if ( p1 >= p3 )
      cout << "Pair p1 is greater than or equal to pair p3." << endl;
   else
      cout << "The pair p1 is less than the pair p3." << endl;

   if ( p1 >= p4 )
      cout << "Pair p1 is greater than or equal to pair p4." << endl;
   else
      cout << "The pair p1 is less than the pair p4." << endl;
}
```

```Output
The pair p1 is: ( 10, 0.222 ).
The pair p2 is: ( 100, 0.111 ).
The pair p3 is: ( 10, 0.111 ).
The pair p4 is: ( 10, 0.222 ).

The pair p1 is less than the pair p2.
Pair p1 is greater than or equal to pair p3.
Pair p1 is greater than or equal to pair p4.
```
