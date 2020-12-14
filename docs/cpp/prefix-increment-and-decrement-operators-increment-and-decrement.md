---
description: 'En savoir plus sur : opérateurs de préfixe d’incrémentation et de décrémentation : + + et--'
title: "Opérateurs préfixés d'incrémentation et de décrémentation : ++ et --"
ms.date: 11/04/2016
f1_keywords:
- --
- ++
helpviewer_keywords:
- increment operators [C++], syntax
- ++ operator [C++], prefix increment operators
- operators [C++], decrement
- -- operator [C++], prefix decrement operators [C++]
- operators [C++], increment
- decrement operators [C++], syntax
- decrement operators [C++]
ms.assetid: 45ea7fc7-f279-4be9-a216-1d9a0ef9eb7b
ms.openlocfilehash: e484dde59a2bb58e7c408ad28242fc0ab4290051
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97198640"
---
# <a name="prefix-increment-and-decrement-operators--and---"></a>Opérateurs préfixés d'incrémentation et de décrémentation : ++ et --

## <a name="syntax"></a>Syntaxe

```
++ unary-expression
-- unary-expression
```

## <a name="remarks"></a>Notes

L’opérateur de préfixe **++** d’incrément () ajoute un à son opérande ; cette valeur incrémentée est le résultat de l’expression. L’opérande doit être une l-value non de type **`const`** . Le résultat est une l-value du même type que l’opérande.

L’opérateur de décrémentation de préfixe ( **--** ) est analogue à l’opérateur d’incrément de préfixe, sauf que l’opérande est décrémenté par un et que le résultat est cette valeur décrémentée.

**Visual Studio 2017 version 15,3 et versions ultérieures** (disponibles avec [/std : c++ 17](../build/reference/std-specify-language-standard-version.md)) : l’opérande d’un opérateur d’incrémentation ou de décrémentation ne peut pas être de type **`bool`** .

Les opérateurs préfixés et suffixés d'incrémentation et de décrémentation affectent leurs opérandes. La différence principale qui les distingue est lorsque l'incrémentation ou la décrémentation se produit dans l'évaluation d'une expression. (Pour plus d’informations, consultez [opérateurs suffixés d’incrémentation et de décrémentation](../cpp/postfix-increment-and-decrement-operators-increment-and-decrement.md).) Dans le formulaire de préfixe, l’incrémentation ou la décrémentation ont lieu avant que la valeur ne soit utilisée dans l’évaluation de l’expression, donc la valeur de l’expression est différente de la valeur de l’opérande. Dans leur forme suffixée, l’incrémentation ou la décrémentation ont lieu après que la valeur ne soit utilisée dans l’évaluation de l’expression. Par conséquent, la valeur de l’expression est identique à la valeur de l’opérande. Par exemple, le programme suivant affiche `++i = 6` :

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

Étant donné que les opérateurs d’incrémentation et de décrémentation ont des effets secondaires, l’utilisation d’expressions avec des opérateurs d’incrémentation ou de décrémentation dans une [macro de préprocesseur](../preprocessor/macros-c-cpp.md) peut avoir des résultats indésirables. Prenons l’exemple suivant :

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
> Les fonctions inline C++ sont préférables aux macros dans de nombreux cas car elles éliminent des effets secondaires tels que ceux décrits ici et permettent au langage d'effectuer une vérification de type plus complète.

## <a name="see-also"></a>Voir aussi

[Expressions avec opérateurs unaires](../cpp/expressions-with-unary-operators.md)<br/>
[Opérateurs intégrés, priorité et associativité C++](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[Opérateurs de préfixe d’incrémentation et de décrémentation](../c-language/prefix-increment-and-decrement-operators.md)
