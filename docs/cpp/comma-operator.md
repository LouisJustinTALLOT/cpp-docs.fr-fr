---
description: 'En savoir plus sur : opérateur virgule :,'
title: 'Opérateur virgule : ,'
ms.date: 11/04/2016
f1_keywords:
- '%2C'
helpviewer_keywords:
- comma operator
ms.assetid: 38e0238e-19da-42ba-ae62-277bfdab6090
ms.openlocfilehash: 1429e2ce444e0f253bffca795f36f4e6194e0395
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97274773"
---
# <a name="comma-operator-"></a>Opérateur virgule : ,

Permet le regroupement de deux instructions lorsque l'une d'elles est attendue.

## <a name="syntax"></a>Syntaxe

```
expression , expression
```

## <a name="remarks"></a>Notes

L'opérateur virgule présente une associativité de gauche à droite. Deux expressions séparées par une virgule sont évaluées de gauche à droite. L'opérande gauche est toujours évalué et tous les effets secondaires sont terminés avant l'évaluation de l'opérande droite.

Les virgules peuvent être utilisées comme séparateurs dans certains contextes, par exemple les listes d’arguments de fonction. Ne confondez pas l'utilisation de la virgule comme séparateur avec son utilisation comme opérateur. Ces deux utilisations sont entièrement différentes.

Prenons l'exemple de l'expression `e1, e2`. Le type et la valeur de l’expression sont le type et la valeur de *E2*; le résultat de l’évaluation de *E1* est ignoré. Le résultat est une l-value si l’opérande droite est une l-value.

Alors que la virgule est normalement utilisée comme séparateur (par exemple dans les arguments réels des fonctions ou les initialiseurs d’agrégat), l’opérateur virgule et ses opérandes doivent être placés entre parenthèses. Par exemple :

```cpp
func_one( x, y + 2, z );
func_two( (x--, y + 2), z );
```

Dans l’appel de fonction à `func_one` ci-dessus, trois arguments, séparés par des virgules, sont passés : `x`, `y + 2` et `z`. Dans l'appel de fonction à `func_two`, les parenthèses forcent le compilateur à interpréter la première virgule comme l'opérateur d'évaluation séquentielle. Cet appel de fonction passe deux arguments à `func_two`. Le premier argument est le résultat de l'opération d'évaluation séquentielle `(x--, y + 2)`, qui a la valeur et le type de l'expression `y + 2`. Le second argument est `z`.

## <a name="example"></a>Exemple

```cpp
// cpp_comma_operator.cpp
#include <stdio.h>
int main () {
   int i = 10, b = 20, c= 30;
   i = b, c;
   printf("%i\n", i);

   i = (b, c);
   printf("%i\n", i);
}
```

```Output
20
30
```

## <a name="see-also"></a>Voir aussi

[Expressions avec opérateurs binaires](../cpp/expressions-with-binary-operators.md)<br/>
[Opérateurs intégrés, priorité et associativité C++](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[Opérateur d’évaluation séquentielle](../c-language/sequential-evaluation-operator.md)
