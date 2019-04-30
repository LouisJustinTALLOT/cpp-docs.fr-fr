---
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
ms.openlocfilehash: e1a87fe4815a75b97616d7b11a4b9aa4ae65eb9f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62392139"
---
# <a name="postfix-increment-and-decrement-operators--and---"></a>Opérateurs suffixés d'incrémentation et de décrémentation : ++ et --

## <a name="syntax"></a>Syntaxe

```
postfix-expression ++
postfix-expression --
```

## <a name="remarks"></a>Notes

C++ fournit des opérateurs d'incrémentation et de décrémentation préfixés et suffixés. Cette section décrit uniquement les opérateurs d'incrémentation et de décrémentation suffixés. (Pour plus d’informations, consultez [préfixe opérateurs d’incrémentation et décrémentation](../cpp/prefix-increment-and-decrement-operators-increment-and-decrement.md).) La différence entre les deux est que, dans la notation suffixée, l’opérateur figure après *postfix-expression*, tandis que dans la notation préfixée, l’opérateur figure avant *expression.* L'exemple suivant montre un opérateur d'incrémentation suffixé :

```cpp
i++;
```

L’effet d’appliquer l’opérateur d’incrémentation suffixé (**++**) est que la valeur de l’opérande est augmentée d’une unité du type approprié. De même, l’effet d’appliquer l’opérateur de décrémentation suffixé (**--**) est que la valeur de l’opérande est diminué d’une unité du type approprié.

Il est important de noter qu’un suffixe incrémenter ou décrémenter expression prend la valeur de l’expression *antérieures à* application de l’opérateur respectif. L’opération d’incrémentation ou décrémentation *après* l’opérande est évalué. Ce problème survient uniquement lorsque l'opération d'incrémentation ou de décrémentation suffixée intervient dans le contexte d'une plus grande expression.

Lorsqu'un opérateur suffixé est appliqué à un argument de fonction, il n'est pas garanti que la valeur de cet argument sera incrémentée ou décrémentée avant d'être passée à la fonction.  Pour plus d'informations, reportez-vous à la section 1.9.17 de la norme C++.

Application de l’opérateur d’incrémentation suffixé à un pointeur vers un tableau d’objets de type **long** ajoute en fait quatre à la représentation interne du pointeur. Ce comportement fait que le pointeur, qui référençait auparavant le *n*-ième élément du tableau, pour faire référence à la (*n*+ 1) élément th.

Les opérandes incrémentation et opérateurs de décrément suffixés doivent être modifiables (pas **const**) l-values de type arithmétique ou pointeur. Le type du résultat est identique à celui de la *postfix-expression*, mais il n’est plus une l-value.

**Visual Studio 2017 15.3 et versions ultérieures** (disponible avec [/std : c ++ 17](../build/reference/std-specify-language-standard-version.md)) : L’opérande d’une incrémentation ou de décrémentation opérateur ne peut pas être de type **bool**.

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