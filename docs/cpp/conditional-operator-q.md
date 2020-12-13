---
description: 'En savoir plus sur : opérateur conditionnel : &quest; :'
title: 'Opérateur conditionnel : &quest; :'
ms.date: 11/04/2016
f1_keywords:
- '?:'
- '?'
helpviewer_keywords:
- conditional operators [C++]
- '? : operator'
ms.assetid: 88643ee8-7100-4f86-880a-705ec22b6271
ms.openlocfilehash: fac9a6553af428664535ca4ce5e6e201a1819d6b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97344690"
---
# <a name="conditional-operator-quest-"></a>Opérateur conditionnel : &quest; :

## <a name="syntax"></a>Syntaxe

```
expression ? expression : expression
```

## <a name="remarks"></a>Notes

L’opérateur conditionnel (**?:**) est un opérateur ternaire (il prend trois opérandes). L'opérateur conditionnel fonctionne comme suit :

- Le premier opérande est implicitement converti en **`bool`** . Il est évalué et tous les effets secondaires sont résolus avant de continuer.

- Si le premier opérande a la valeur **`true`** (1), le deuxième opérande est évalué.

- Si le premier opérande a la valeur **`false`** (0), le troisième opérande est évalué.

Le résultat de l’opérateur conditionnel est que le résultat de tout opérande est évalué — le deuxième ou le troisième. Seul l’un des deux derniers opérandes est évalué dans une expression conditionnelle.

Les expressions conditionnelles ont une associativité de droite à gauche. Le premier opérande doit être de type intégral ou de type pointeur. Les règles suivantes s'appliquent au deuxième et au troisième opérandes :

- Si les deux opérandes sont du même type, le résultat est de ce type.

- Si les deux opérandes sont de types arithmétiques ou d’énumération, les conversions arithmétiques habituelles (couvertes dans les [conversions standard](standard-conversions.md)) sont exécutées pour les convertir en un type commun.

- Si les deux opérandes sont des types pointeur ou si l'un est de type pointeur et l'autre une expression constante qui correspond à 0, les conversions de pointeur sont exécutées pour les convertir en un type commun.

- Si les deux opérandes sont des types référence, les conversions de référence sont exécutées pour les convertir en un type commun.

- Si les deux opérandes sont de type void, le type commun est le type void.

- Si les deux opérandes sont du même type défini par l’utilisateur, le type commun correspond à ce type.

- Si les opérandes ont des types différents et qu’au moins un des opérandes a un type défini par l’utilisateur, alors les règles de langage sont utilisées pour déterminer le type commun. (Voir l'avertissement ci-dessous.)

Toutes les combinaisons des deuxième et troisième opérandes qui ne sont pas dans la liste précédente ne sont pas conformes. Le type du résultat est le type commun, et c’est une l-value si le deuxième et le troisième opérande sont du même type et si les deux sont des valeurs l-value.

> [!WARNING]
> Si les types des deuxième et troisième opérandes ne sont pas identiques, les règles de conversion de type complexe, telles que spécifiées par la norme C++, sont appelées. Ces conversions peuvent entraîner un comportement inattendu, notamment la construction et la destruction d'objets temporaires. Pour cette raison, il est fortement conseillé de soit (1) éviter d’utiliser les types définis par l’utilisateur comme des opérandes avec l’opérateur conditionnel ou (2) si vous utilisez des types définis par l’utilisateur, d’effectuer une conversion de type explicite pour chaque opérande vers un type commun.

## <a name="example"></a>Exemple

```cpp
// expre_Expressions_with_the_Conditional_Operator.cpp
// compile with: /EHsc
// Demonstrate conditional operator
#include <iostream>
using namespace std;
int main() {
   int i = 1, j = 2;
   cout << ( i > j ? i : j ) << " is greater." << endl;
}
```

## <a name="see-also"></a>Voir aussi

[Opérateurs intégrés, priorité et associativité C++](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[Opérateur d’expression conditionnelle](../c-language/conditional-expression-operator.md)
