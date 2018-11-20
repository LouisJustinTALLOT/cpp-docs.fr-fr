---
title: Sémantique des expressions
ms.date: 11/19/2018
helpviewer_keywords:
- grammar, expressions
- expressions [C++], semantics
- expression evaluation
- expression evaluation, about expression evaluation
ms.assetid: 4a792154-533b-48b9-8709-31bfc170f0a7
ms.openlocfilehash: d2ce510478bcf1574429c85f704552e6b73100ea
ms.sourcegitcommit: 9e891eb17b73d98f9086d9d4bfe9ca50415d9a37
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2018
ms.locfileid: "52175782"
---
# <a name="semantics-of-expressions"></a>Sémantique des expressions

Les expressions sont évaluées selon la priorité et le regroupement de leurs opérateurs. ([Priorité et associativité](../cpp/cpp-built-in-operators-precedence-and-associativity.md) dans [Conventions lexicales](../cpp/lexical-conventions.md), montre les relations du C++ opérateurs imposent aux expressions.)

## <a name="order-of-evaluation"></a>Ordre d'évaluation

Considérez cet exemple :

```cpp
// Order_of_Evaluation.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;
int main()
{
    int a = 2, b = 4, c = 9;

    cout << a + b * c << "\n";
    cout << a + (b * c) << "\n";
    cout << (a + b) * c << "\n";
}
```

```Output
38
38
54
```

![Ordre d’évaluation dans une expression](../cpp/media/vc38zv1.gif "ordre d’évaluation dans une expression") <br/>
Ordre expression-évaluation

L'ordre dans lequel l'expression affichée dans l'illustration ci-dessus est évaluée est déterminé par la priorité et l'associativité des opérateurs :

1. La multiplication (*) a la priorité la plus élevée dans cette expression. Donc, la sous-expression `b * c` est évaluée en premier.

1. L'ajout (+) a la priorité la plus élevée suivante, donc `a` est ajouté au produit de `b` et `c`.

1. Le décalage vers la gauche (<<) a la plus faible priorité dans l'expression mais il existe deux occurrences. Étant donné que l'opérateur de décalage vers la gauche groupe de gauche à droite, la sous-expression gauche est évaluée en premier avant la sous-expression droite.

Lorsque les parenthèses sont utilisées pour grouper les sous-expressions, elles modifient la priorité et également l'ordre dans lequel l'expression est évaluée, comme indiqué dans l'illustration suivante.

![Ordre d’évaluation d’expression avec parenthèses](../cpp/media/vc38zv2.gif "ordre d’évaluation d’expression avec parenthèses") <br/>
Ordre expression-évaluation avec parenthèses

Les expressions telles qu'elles existent dans l'illustration ci-dessus sont purement évaluées pour leurs effets secondaires, dans ce cas pour transférer des informations au périphérique de sortie standard.

## <a name="notation-in-expressions"></a>Notation dans les expressions

Le langage C++ spécifie certaines compatibilités lors de la spécification des opérandes. Le tableau suivant présente les types d’opérandes acceptables pour les opérateurs qui nécessitent des opérandes de type *type*.

### <a name="operand-types-acceptable-to-operators"></a>Types d’opérande acceptables pour les opérateurs

|Type attendu|Types autorisés|
|-------------------|-------------------|
|*type*|`const` *Type*<br /> `volatile` *Type*<br /> *type*&<br /> `const` *Type*&<br /> `volatile` *Type*&<br /> `volatile const` *Type*<br /> `volatile const` *Type*&|
|*Type* \*|*Type* \*<br /> `const` *Type* \*<br /> `volatile` *Type* \*<br /> `volatile const` *Type* \*|
|`const` *Type*|*type*<br /> `const` *Type*<br />`const` *Type*&|
|`volatile` *Type*|*type*<br /> `volatile` *Type*<br /> `volatile` *Type*&|

Comme les règles précédentes peuvent toujours être utilisées de manière combinée, un pointeur const vers un objet volatile peut être fourni là où un pointeur est attendu.

## <a name="ambiguous-expressions"></a>Expressions ambiguës

La signification de certaines expressions est ambiguë. Ces expressions se rencontrent généralement lorsque la valeur d'un objet change plusieurs fois dans la même expression. Elles reposent sur un ordre particulier d'évaluation lorsque le langage n'en définit aucun. Prenons l'exemple suivant :

```
int i = 7;

func( i, ++i );
```

Le langage C++ ne garantit pas l'ordre dans lequel les arguments d'un appel de fonction sont évalués. Par conséquent, dans l'exemple précédent, `func` peut recevoir comme paramètres les valeurs 7 et 8, ou 8 et 8, selon que les paramètres sont évalués de gauche à droite ou de droite à gauche.

## <a name="c-sequence-points-microsoft-specific"></a>Points de séquence C++ (section spécifique à Microsoft)

Une expression peut modifier la valeur d'un objet une seule fois entre des points de séquence consécutifs.

La définition de langage C++ ne spécifie pas actuellement les points de séquence. Microsoft C++ utilise les mêmes points de séquence que C ANSI pour toute expression utilisant des opérateurs C et n'impliquent pas les opérateurs surchargés. Lorsque des opérateurs sont surchargés, la sémantique passe de la séquence par l'opérateur à la séquence par l'appel de fonction. Microsoft C++ utilise les points de séquence ci-dessous.

- Opérande de gauche de l’opérateur AND logique (&&). L’opérande gauche de l’opérateur AND logique est complètement évalué et tous les effets secondaires sont terminés avant de continuer. Il n’existe aucune garantie que l’opérande droite de l’opérateur AND logique sera évalué.

- Opérande gauche de l’opérateur OR logique (&#124;&#124;). L’opérande gauche de l’opérateur OR logique est complètement évalué et tous les effets secondaires sont terminés avant de continuer. Il n’existe aucune garantie que l’opérande droite de l’opérateur OR logique sera évalué.

- Opérande gauche de l'opérateur virgule. L’opérande gauche de l’opérateur virgule est complètement évalué et tous les effets secondaires sont terminés avant de continuer. Les deux opérandes de l'opérateur virgule sont toujours évalués.

- Opérateur d'appel de fonction. L’expression appel-fonction et tous les arguments d’une fonction, notamment les arguments par défaut, sont évalués et tous les effets secondaires sont terminés avant l’entrée dans la fonction. Il n'y a aucun ordre spécifié d'évaluation entre les arguments ou l'expression appel-fonction.

- Premier opérande de l'opérateur conditionnel. Le premier opérande de l'opérateur conditionnel est complètement évalué et tous les effets secondaires sont terminés avant de continuer.

- La fin d'une expression complète d'initialisation, comme la fin d'une initialisation dans une instruction de déclaration.

- L'expression dans une instruction d'expression. Les instructions Expression sont composées d'une expression facultative suivie d'un point-virgule (;). L'expression est complètement évaluée pour ses effets secondaires.

- L'expression de contrôle d'une instruction de sélection (if ou switch). L'expression est complètement évaluée et tous les effets secondaires sont terminés avant que le code dépendant de la sélection soit exécuté.

- Expression de contrôle d'une instruction while ou do. L'expression est complètement évaluée et tous les effets secondaires sont terminés avant que toutes les instructions de l'itération suivante de la boucle while ne soient exécutées.

- Chacune des trois expressions d'une instruction for. Chaque expression est complètement évaluée et tous les effets secondaires sont terminés avant de passer à l'expression suivante.

- Expression dans une instruction return. L'expression est complètement évaluée et tous les effets secondaires sont terminés avant que le contrôle ne retourne à la fonction appelante.

## <a name="see-also"></a>Voir aussi

[Expressions](../cpp/expressions-cpp.md)