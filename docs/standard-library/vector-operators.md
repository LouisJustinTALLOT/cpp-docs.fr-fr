---
description: 'En savoir plus sur &lt; : &gt; opérateurs vectoriels'
title: '&lt;vector&gt;, opérateurs'
ms.date: 11/04/2016
f1_keywords:
- vector/std::operator!=
- vector/std::operator&gt;
- vector/std::operator&gt;=
- vector/std::operator&lt;
- vector/std::operator&lt;=
- vector/std::operator==
ms.assetid: 1d14f312-6f59-4ec7-88ae-95f89a558823
helpviewer_keywords:
- std::operator!= (vector)
- std::operator&gt; (vector)
- std::operator&gt;= (vector)
- std::operator&lt; (vector)
- std::operator&lt;= (vector)
- std::operator== (vector)
ms.openlocfilehash: a7a03d3ef843c995970552201e63d2df3cb3161d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97187895"
---
# <a name="ltvectorgt-operators"></a>&lt;vector&gt;, opérateurs

## <a name="operator"></a><a name="op_neq"></a> opérateur ! =

Teste si l’objet situé à gauche de l’opérateur n’est pas égal à l’objet situé à droite.

```cpp
bool operator!=(const vector<Type, Allocator>& left, const vector<Type, Allocator>& right);
```

### <a name="parameters"></a>Paramètres

*gauche*\
Objet de type `vector`.

*Oui*\
Objet de type `vector`.

### <a name="return-value"></a>Valeur renvoyée

**`true`** Si les vecteurs ne sont pas égaux ; **`false`** si les vecteurs sont égaux.

### <a name="remarks"></a>Notes

Deux vecteurs sont égaux s’ils ont le même nombre d’éléments et si leurs éléments respectifs ont les mêmes valeurs. Sinon, elles sont inégales.

### <a name="example"></a>Exemple

```cpp
// vector_op_ne.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;

   vector <int> v1, v2;
   v1.push_back( 1 );
     v2.push_back( 2 );

   if ( v1 != v2 )
      cout << "Vectors not equal." << endl;
   else
      cout << "Vectors equal." << endl;
}
```

```Output
Vectors not equal.
```

## <a name="operatorlt"></a><a name="op_lt"></a> and&lt;

Teste si l’objet situé à gauche de l’opérateur est inférieur à l’objet situé à droite.

```cpp
bool operator<(const vector<Type, Allocator>& left, const vector<Type, Allocator>& right);
```

### <a name="parameters"></a>Paramètres

*gauche*\
Objet de type `vector`.

*Oui*\
Objet de type `vector`.

### <a name="return-value"></a>Valeur renvoyée

**`true`** Si le vecteur situé à gauche de l’opérateur est inférieur au vecteur situé à droite de l’opérateur ; Sinon, **`false`** .

### <a name="example"></a>Exemple

```cpp
// vector_op_lt.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;

   vector <int> v1, v2;
   v1.push_back( 1 );
   v1.push_back( 2 );
   v1.push_back( 4 );

   v2.push_back( 1 );
   v2.push_back( 3 );

   if ( v1 < v2 )
      cout << "Vector v1 is less than vector v2." << endl;
   else
      cout << "Vector v1 is not less than vector v2." << endl;
}
```

```Output
Vector v1 is less than vector v2.
```

## <a name="operatorlt"></a><a name="op_lt_eq"></a> and&lt;=

Teste si l’objet situé à gauche de l’opérateur est inférieur ou égal à l’objet situé à droite.

```cpp
bool operator<=(const vector<Type, Allocator>& left, const vector<Type, Allocator>& right);
```

### <a name="parameters"></a>Paramètres

*gauche*\
Objet de type `vector`.

*Oui*\
Objet de type `vector`.

### <a name="return-value"></a>Valeur renvoyée

**`true`** Si le vecteur situé à gauche de l’opérateur est inférieur ou égal au vecteur situé à droite de l’opérateur ; Sinon, **`false`** .

### <a name="example"></a>Exemple

```cpp
// vector_op_le.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;

   vector <int> v1, v2;
   v1.push_back( 1 );
   v1.push_back( 2 );
   v1.push_back( 4 );

   v2.push_back( 1 );
   v2.push_back( 3 );

   if ( v1 <= v2 )
      cout << "Vector v1 is less than or equal to vector v2." << endl;
   else
      cout << "Vector v1 is greater than vector v2." << endl;
}
```

```Output
Vector v1 is less than or equal to vector v2.
```

## <a name="operator"></a><a name="op_eq_eq"></a> opérateur = =

Teste si l’objet situé à gauche de l’opérateur est égal à l’objet situé à droite.

```cpp
bool operator==(const vector<Type, Allocator>& left, const vector<Type, Allocator>& right);
```

### <a name="parameters"></a>Paramètres

*gauche*\
Objet de type `vector`.

*Oui*\
Objet de type `vector`.

### <a name="return-value"></a>Valeur renvoyée

**`true`** Si le vecteur situé à gauche de l’opérateur est égal au vecteur situé à droite de l’opérateur ; Sinon, **`false`** .

### <a name="remarks"></a>Notes

Deux vecteurs sont égaux s’ils ont le même nombre d’éléments et si leurs éléments respectifs ont les mêmes valeurs. Sinon, elles sont inégales.

### <a name="example"></a>Exemple

```cpp
// vector_op_eq.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;

   vector <int> v1, v2;
   v1.push_back( 1 );
   v2.push_back( 1 );

   if ( v1 == v2 )
      cout << "Vectors equal." << endl;
   else
      cout << "Vectors not equal." << endl;
}
```

```Output
Vectors equal.
```

## <a name="operatorgt"></a><a name="op_gt"></a> and&gt;

Teste si l’objet situé à gauche de l’opérateur est supérieur à l’objet situé à droite.

```cpp
bool operator>(const vector<Type, Allocator>& left, const vector<Type, Allocator>& right);
```

### <a name="parameters"></a>Paramètres

*gauche*\
Objet de type `vector`.

*Oui*\
Objet de type `vector`.

### <a name="return-value"></a>Valeur renvoyée

**`true`** Si le vecteur situé à gauche de l’opérateur est supérieur au vecteur situé à droite de l’opérateur ; Sinon, **`false`** .

### <a name="example"></a>Exemple

```cpp
// vector_op_gt.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;

   vector <int> v1, v2;
   v1.push_back( 1 );
   v1.push_back( 3 );
   v1.push_back( 1 );

   v2.push_back( 1 );
   v2.push_back( 2 );
   v2.push_back( 2 );

   if ( v1 > v2 )
      cout << "Vector v1 is greater than vector v2." << endl;
   else
      cout << "Vector v1 is not greater than vector v2." << endl;
}
```

```Output
Vector v1 is greater than vector v2.
```

## <a name="operatorgt"></a><a name="op_gt_eq"></a> and&gt;=

Teste si l’objet situé à gauche de l’opérateur est supérieur ou égal à l’objet situé à droite.

```cpp
bool operator>=(const vector<Type, Allocator>& left, const vector<Type, Allocator>& right);
```

### <a name="parameters"></a>Paramètres

*gauche*\
Objet de type `vector`.

*Oui*\
Objet de type `vector`.

### <a name="return-value"></a>Valeur renvoyée

**`true`** Si le vecteur situé à gauche de l’opérateur est supérieur ou égal au vecteur situé à droite du vecteur ; Sinon, **`false`** .

### <a name="example"></a>Exemple

```cpp
// vector_op_ge.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;

   vector <int> v1, v2;
   v1.push_back( 1 );
   v1.push_back( 3 );
   v1.push_back( 1 );

     v2.push_back( 1 );
   v2.push_back( 2 );
   v2.push_back( 2 );

   if ( v1 >= v2 )
      cout << "Vector v1 is greater than or equal to vector v2." << endl;
   else
      cout << "Vector v1 is less than vector v2." << endl;
}
```

```Output
Vector v1 is greater than or equal to vector v2.
```
