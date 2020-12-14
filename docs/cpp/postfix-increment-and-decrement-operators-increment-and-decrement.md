---
description: 'En savoir plus sur : opérateurs suffixés d’incrémentation et de décrémentation : + + et--'
title: "Opérateurs suffixés d'incrémentation et de décrémentation : ++ et --"
ms.date: 11/04/2016
f1_keywords:
- --
- ++
helpviewer_keywords:
- increment operators [C++], syntax
- member-selection operators [C++]
- -- operator [C++], postfix decrement operators
- postfix operators [C++]
- ++ operator [C++], postfix increment operators
- decrement operators [C++], syntax
- operators [C++], postfix
- decrement operators [C++]
ms.assetid: 0204d5c8-51b0-4108-b8a1-074c5754d89c
ms.openlocfilehash: 56f955fc4c8b5508c4b2c4e03c37e89f9d2d8bc0
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97258510"
---
# <a name="postfix-increment-and-decrement-operators--and---"></a>Opérateurs suffixés d'incrémentation et de décrémentation : ++ et --

## <a name="syntax"></a>Syntaxe

```
postfix-expression ++
postfix-expression --
```

## <a name="remarks"></a>Notes

C++ fournit des opérateurs d'incrémentation et de décrémentation préfixés et suffixés. Cette section décrit uniquement les opérateurs d'incrémentation et de décrémentation suffixés. (Pour plus d’informations, consultez [opérateurs de préfixe d’incrémentation et de décrémentation](../cpp/prefix-increment-and-decrement-operators-increment-and-decrement.md).) La différence entre les deux est que dans la notation suffixée, l’opérateur apparaît après *postfix-expression*, alors que dans la notation de préfixe, l’opérateur apparaît avant *expression.* L'exemple suivant montre un opérateur d'incrémentation suffixé :

```cpp
i++;
```

L’application de l’opérateur d’incrémentation postfix ( **++** ) a pour effet que la valeur de l’opérande est augmentée d’une unité du type approprié. De même, l’effet de l’application de l’opérateur de décrémentation postfixé ( **--** ) est que la valeur de l’opérande est diminuée d’une unité du type approprié.

Il est important de noter qu’une expression d’incrémentation ou de décrémentation suffixée prend la valeur de l’expression *avant* l’application de l’opérateur respectif. L’opération d’incrémentation ou de décrémentation se produit *après* l’évaluation de l’opérande. Ce problème survient uniquement lorsque l'opération d'incrémentation ou de décrémentation suffixée intervient dans le contexte d'une plus grande expression.

Lorsqu'un opérateur suffixé est appliqué à un argument de fonction, il n'est pas garanti que la valeur de cet argument sera incrémentée ou décrémentée avant d'être passée à la fonction.  Pour plus d'informations, reportez-vous à la section 1.9.17 de la norme C++.

L’application de l’opérateur d’incrémentation postfixé à un pointeur vers un tableau d’objets de type **`long`** ajoute en fait quatre à la représentation interne du pointeur. Ce comportement fait que le pointeur, qui faisait précédemment référence au *n* ème élément du tableau, fait référence à l’élément (*n*+ 1) th.

Les opérandes pour les opérateurs d’incrémentation et de décrémentation postfix et suffixe doivent être modifiables (pas **`const`** ) des valeurs de l-i de type arithmétique ou pointeur. Le type du résultat est le même que celui de l' *expression postfix*, mais il n’est plus une l-value.

**Visual Studio 2017 version 15,3 et versions ultérieures** (disponibles avec [/std : c++ 17](../build/reference/std-specify-language-standard-version.md)) : l’opérande d’un opérateur d’incrémentation ou de décrémentation suffixé ne peut pas être de type **`bool`** .

Le code suivant illustre l'opérateur d'incrémentation suffixé :

```cpp
// expre_Postfix_Increment_and_Decrement_Operators.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;

int main() {
   int i = 10;
   cout << i++ << endl;
   cout << i << endl;
}
```

Les opérations d'incrémentation et de décrémentation suffixées sur les types énumérés ne sont pas prises en charge :

```cpp
enum Compass { North, South, East, West );
Compass myCompass;
for( myCompass = North; myCompass != West; myCompass++ ) // Error
```

## <a name="see-also"></a>Voir aussi

[Expressions suffixées](../cpp/postfix-expressions.md)<br/>
[Opérateurs intégrés, priorité et associativité C++](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[Opérateurs suffixés d’incrémentation et de décrémentation C](../c-language/c-postfix-increment-and-decrement-operators.md)
