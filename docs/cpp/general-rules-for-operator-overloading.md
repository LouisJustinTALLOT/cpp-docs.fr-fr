---
title: Règles générales de surcharge d’opérateur | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- operator overloading [C++], rules
ms.assetid: eb2b3754-35f7-4832-b1da-c502893dc0c7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6c3064da609c8a81a6e264c7f46d37d4cd5681d1
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46107141"
---
# <a name="general-rules-for-operator-overloading"></a>Règles générales de surcharge d'opérateur

Les règles suivantes limitent le mode d'implémentation des opérateurs surchargés. Toutefois, ils ne s’appliquent pas à la [nouveau](../cpp/new-operator-cpp.md) et [supprimer](../cpp/delete-operator-cpp.md) operators, qui sont traités séparément.

- Vous ne pouvez pas définir de nouveaux opérateurs tels que **.**.

- Vous ne pouvez pas redéfinir la signification d'opérateurs lorsqu'ils sont appliqués à des types de données intégrés.

- Les opérateurs surchargés doivent être soit une fonction de membre de classe non statique, soit une fonction globale. Une fonction globale qui nécessite un accès à des membres de classe privés ou protégés doit être déclarée comme amie de cette classe. Une fonction globale doit prendre au moins un argument qui est de type classe ou énuméré ou qui est une référence à un type énuméré ou classe. Exemple :

    ```cpp
    // rules_for_operator_overloading.cpp
    class Point
    {
    public:
        Point operator<( Point & );  // Declare a member operator
                                     //  overload.
        // Declare addition operators.
        friend Point operator+( Point&, int );
        friend Point operator+( int, Point& );
    };

    int main()
    {
    }
    ```

     L'exemple de code précédent déclare l'opérateur Inférieur à comme fonction membre ; toutefois, les opérateurs d'addition sont déclarés comme fonctions globales qui ont un accès ami. Notez que plusieurs implémentations peuvent être fournies pour un opérateur donné. Dans le cas de l'opérateur d'addition précédent, les deux implémentations sont fournies pour faciliter la commutativité. Il est tout aussi probable que des opérateurs qui ajoutent un `Point` à un `Point`, **int** à un `Point`, et ainsi de suite, peut être implémenté.

- Les opérateurs obéissent aux règles de priorité, de regroupement et de nombre d’opérandes dictées par leur utilisation classique avec les types intégrés. Par conséquent, il n’existe aucun moyen d’exprimer le concept « ajouter 2 et 3 à un objet de type `Point`, » attendu 2 à ajouter à la *x* coordonnées et 3 à ajouter à la *y* coordonner.

- Les opérateurs unaires déclarés comme fonctions membres n’acceptent pas d’argument ; s’ils sont déclarés comme fonctions globales, ils en prennent un.

- Les opérateurs binaires déclarés comme fonctions membres acceptent un argument ; s’ils sont déclarés comme fonctions globales, ils en prennent deux.

- Si un opérateur peut être utilisé comme un opérateur unaire ou un opérateur binaire (__&__, __*__, __+__, et __-__), vous pouvez surcharger séparément chaque utilisation.

- Les opérateurs surchargés ne peuvent pas avoir d’arguments par défaut.

- Tous les opérateurs à l’exception d’assignation surchargés (**opérateur =**) sont héritées par les classes dérivées.

- Le premier argument pour les opérateurs surchargés déclarés comme fonctions membres est toujours le type de classe de l’objet pour lequel l’opérateur est appelé (la classe dans laquelle l’opérateur est déclaré ou une classe dérivée de cette classe). Aucune conversion n'est fournie pour le premier argument.

Notez que la signification de n'importe quel opérateur peut être modifiée complètement. Cela comprend la signification de l’adresse de (**&**), affectation (**=**) et les opérateurs d’appel de fonction. En outre, les identités sur lesquelles on peut se reposer pour les types intégrés peuvent être modifiées à l'aide de la surcharge d'opérateur. Par exemple, les quatre instructions suivantes sont généralement équivalentes une fois leur évaluation terminée :

```cpp
var = var + 1;
var += 1;
var++;
++var;
```

On ne peut pas se reposer sur cette identité pour les types de classe qui surchargent des opérateurs. De plus, certaines des exigences implicites dans l’utilisation de ces opérateurs pour les types de base sont allégées pour les opérateurs surchargés. Par exemple, l’opérateur d’addition/assignation, **+=**, nécessite l’opérande gauche soit une l-value lorsqu’il est appliqué aux types de base ; n’est pas obligatoire de ce type lors de l’opérateur est surchargé.

> [!NOTE]
> Pour des raisons de cohérence, il est souvent préférable de suivre le modèle des types intégrés lors de la définition des opérateurs surchargés. Si la sémantique d'un opérateur surchargé diffère sensiblement de sa signification dans d'autres contextes, il peut être plus perturbant qu'utile.

## <a name="see-also"></a>Voir aussi

[Surcharge d'opérateur](../cpp/operator-overloading.md)