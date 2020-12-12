---
description: 'En savoir plus sur : opérateurs d’accès aux membres :. les&gt;'
title: Opérateurs d’accès aux membres :. les&gt;
ms.date: 11/04/2016
f1_keywords:
- .
- ->
helpviewer_keywords:
- member access, expressions
- operators [C++], member access
- dot operator (.)
- -> operator
- member access, operators
- postfix operators [C++]
- . operator
- member access
ms.assetid: f8fc3df9-d728-40c5-b384-276927f5f1b3
ms.openlocfilehash: 242ded47c22e0cacfc09659fca275c9e412c004e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97276814"
---
# <a name="member-access-operators--and--gt"></a>Opérateurs d’accès aux membres :. les&gt;

## <a name="syntax"></a>Syntaxe

```
postfix-expression . name
postfix-expression -> name
```

## <a name="remarks"></a>Notes

Opérateurs d’accès au membre **.** et **->** sont utilisés pour faire référence aux membres de structures, d’unions et de classes. Les expressions d’accès au membre ont la valeur et le type du membre sélectionné.

Il existe deux formes d’expressions d’accès au membre :

1. Dans la première forme, *postfix-expression* représente une valeur de type struct, Class ou Union, et *Name* désigne un membre de la structure, Union ou classe spécifiée. La valeur de l’opération est celle de *Name* et est une l-value si *postfix-expression* est une l-value.

1. Dans la deuxième forme, *postfix-expression* représente un pointeur vers une structure, une Union ou une classe, et *Name* désigne un membre de la structure, Union ou classe spécifiée. La valeur est celle de *Name* et est une l-value. L' **->** opérateur déréférence le pointeur. Par conséquent, les expressions `e->member` et `(*e).member` (où *e* représente un pointeur) produisent des résultats identiques (sauf lorsque les opérateurs **->** ou <strong>\*</strong> sont surchargés).

## <a name="example"></a>Exemple

L'exemple suivant illustre les deux formes de l'opérateur d'accès aux membres.

```cpp
// expre_Selection_Operator.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;

struct Date {
   Date(int i, int j, int k) : day(i), month(j), year(k){}
   int month;
   int day;
   int year;
};

int main() {
   Date mydate(1,1,1900);
   mydate.month = 2;
   cout  << mydate.month << "/" << mydate.day
         << "/" << mydate.year << endl;

   Date *mydate2 = new Date(1,1,2000);
   mydate2->month = 2;
   cout  << mydate2->month << "/" << mydate2->day
         << "/" << mydate2->year << endl;
   delete mydate2;
}
```

```Output
2/1/1900
2/1/2000
```

## <a name="see-also"></a>Voir aussi

[Expressions suffixées](../cpp/postfix-expressions.md)<br/>
[Opérateurs intégrés, priorité et associativité C++](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[Classes et structs](../cpp/classes-and-structs-cpp.md)<br/>
[Structure et membres d’Union](../c-language/structure-and-union-members.md)
