---
title: Opérateurs d’accès au membre :. et -&gt;
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
ms.openlocfilehash: 0f370aa04af2e78efd5edfb7836fb71a4c4516a7
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50468742"
---
# <a name="member-access-operators--and--gt"></a>Opérateurs d’accès au membre :. et -&gt;

## <a name="syntax"></a>Syntaxe

```
postfix-expression . name
postfix-expression -> name
```

## <a name="remarks"></a>Notes

Les opérateurs d’accès de membre **.** et **->** sont utilisés pour faire référence aux membres de structures, unions et classes. Les expressions d’accès au membre ont la valeur et le type du membre sélectionné.

Il existe deux formes d’expressions d’accès au membre :

1. Dans la première forme, *postfix-expression* représente une valeur de struct, classe ou type d’union, et *nom* désigne un membre de la structure spécifiée, d’union ou classe. La valeur de l’opération est celle de *nom* et est une l-value Si *postfix-expression* est une l-value.

1. Dans la seconde forme, *postfix-expression* représente un pointeur vers une structure, union ou classe, et *nom* désigne un membre de la structure spécifiée, d’union ou classe. La valeur est celle de *nom* et est une l-value. Le **->** opérateur de déréférence le pointeur. Par conséquent, les expressions `e->member` et `(*e).member` (où *e* représente un pointeur) produisent des résultats (sauf lorsque les opérateurs **->** ou <strong>\*</strong> sont surchargés).

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
[Structure et membres d’union](../c-language/structure-and-union-members.md)