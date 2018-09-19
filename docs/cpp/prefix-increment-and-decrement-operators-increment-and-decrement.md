---
title: 'Opérateurs préfixés d’incrémentation et décrémentation : ++ et--| Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- --
- ++
dev_langs:
- C++
helpviewer_keywords:
- increment operators [C++], syntax
- ++ operator [C++], prefix increment operators
- operators [C++], decrement
- -- operator [C++], prefix decrement operators [C++]
- operators [C++], increment
- decrement operators [C++], syntax
- decrement operators [C++]
ms.assetid: 45ea7fc7-f279-4be9-a216-1d9a0ef9eb7b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: cc5ef28f7119316f0c42302d4fd1583a53e53140
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46069727"
---
# <a name="prefix-increment-and-decrement-operators--and---"></a>Opérateurs préfixés d'incrémentation et de décrémentation : ++ et --

## <a name="syntax"></a>Syntaxe

```
++ unary-expression
-- unary-expression
```

## <a name="remarks"></a>Notes

L’opérateur de pré-incrémentation (**++**) ajoute un à son opérande ; cette valeur incrémentée est le résultat de l’expression. L’opérande doit être une l-value pas de type **const**. Le résultat est une l-value du même type que l’opérande.

L’opérateur de pré-décrémentation (**--**) est analogue à l’opérateur de pré-incrémentation, à ceci près que l’opérande est décrémenté d’une unité et le résultat est cette valeur décrémentée.

**Visual Studio 2017 15.3 et versions ultérieures** (disponible avec [/std : c ++ 17](../build/reference/std-specify-language-standard-version.md)) : l’opérande d’un opérateur d’incrémentation ou de décrémentation ne peut pas être de type **bool**.

Les opérateurs préfixés et suffixés d’incrémentation et de décrémentation affectent leurs opérandes. La différence principale qui les distingue est lorsque l'incrémentation ou la décrémentation se produit dans l'évaluation d'une expression. (Pour plus d’informations, consultez [Postfix opérateurs d’incrémentation et décrémentation](../cpp/postfix-increment-and-decrement-operators-increment-and-decrement.md).) Dans leur forme suffixée, l’incrémentation ou la décrémentation ont lieu avant que la valeur ne soit utilisée dans l’évaluation de l’expression. Par conséquent, la valeur de l’expression est différente de la valeur de l’opérande. Dans leur forme suffixée, l'incrémentation ou la décrémentation ont lieu après que la valeur ne soit utilisée dans l'évaluation de l'expression. Par conséquent, la valeur de l'expression est identique à la valeur de l'opérande. Par exemple, le programme suivant affiche `++i = 6` :

```cpp
// expre_Increment_and_Decrement_Operators.cpp
// compile with: /EHsc
#include <iostream>

using namespace std;

int main() {
   int i = 5;
   cout << "++i = " << ++i << endl;
}
```

Un opérande de type intégral ou virgule flottante est incrémenté ou décrémenté par la valeur 1 entière. Le type du résultat est identique au type d'opérande. Un opérande de type pointeur est incrémenté ou décrémenté par la taille de l'objet qu'il adresse. Un pointeur incrémenté pointe vers l'objet suivant. Un pointeur décrémenté pointe vers l'objet précédent.

Étant donné qu’opérateurs d’incrémentation et décrémentation ont des effets secondaires, à l’aide d’expressions avec des opérateurs d’incrémentation ou de décrémentation dans une [macro de préprocesseur](../preprocessor/macros-c-cpp.md) peut avoir des résultats indésirables. Considérez cet exemple :

```cpp
// expre_Increment_and_Decrement_Operators2.cpp
#define max(a,b) ((a)<(b))?(b):(a)

int main()
{
   int i = 0, j = 0, k;
   k = max( ++i, j );
}
```

La macro se développe pour donner :

```cpp
k = ((++i)<(j))?(j):(++i);
```

Si `i` est supérieur ou égal à `j` ou inférieur à `j` par 1, il est incrémenté deux fois.

> [!NOTE]
>  Les fonctions inline C++ sont préférables aux macros dans de nombreux cas car elles éliminent des effets secondaires tels que ceux décrits ici et permettent au langage d'effectuer une vérification de type plus complète.

## <a name="see-also"></a>Voir aussi

[Expressions avec opérateurs unaires](../cpp/expressions-with-unary-operators.md)<br/>
[Opérateurs intégrés, priorité et associativité C++](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[Opérateurs préfixés d’incrémentation et de décrémentation](../c-language/prefix-increment-and-decrement-operators.md)