---
title: Règles générales de surcharge d'opérateur
ms.date: 11/04/2016
helpviewer_keywords:
- operator overloading [C++], rules
ms.assetid: eb2b3754-35f7-4832-b1da-c502893dc0c7
ms.openlocfilehash: 0c8cbea3411acd50be376ae0853a143af57458f3
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80188590"
---
# <a name="general-rules-for-operator-overloading"></a>Règles générales de surcharge d'opérateur

Les règles suivantes limitent le mode d'implémentation des opérateurs surchargés. Toutefois, ils ne s’appliquent pas aux opérateurs [New](../cpp/new-operator-cpp.md) et [Delete](../cpp/delete-operator-cpp.md) , qui sont couverts séparément.

- Vous ne pouvez pas définir de nouveaux opérateurs, tels que **.**

- Vous ne pouvez pas redéfinir la signification d'opérateurs lorsqu'ils sont appliqués à des types de données intégrés.

- Les opérateurs surchargés doivent être soit une fonction de membre de classe non statique, soit une fonction globale. Une fonction globale qui nécessite un accès à des membres de classe privés ou protégés doit être déclarée comme amie de cette classe. Une fonction globale doit prendre au moins un argument qui est de type classe ou énuméré ou qui est une référence à un type énuméré ou classe. Par exemple :

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

   L'exemple de code précédent déclare l'opérateur Inférieur à comme fonction membre ; toutefois, les opérateurs d'addition sont déclarés comme fonctions globales qui ont un accès ami. Notez que plusieurs implémentations peuvent être fournies pour un opérateur donné. Dans le cas de l'opérateur d'addition précédent, les deux implémentations sont fournies pour faciliter la commutativité. Il est tout aussi probable que les opérateurs qui ajoutent un `Point` à un `Point`, **int** à un `Point`, etc., peuvent être implémentés.

- Les opérateurs obéissent aux règles de priorité, de regroupement et de nombre d'opérandes dictées par leur utilisation classique avec les types intégrés. Par conséquent, il n’existe aucun moyen d’exprimer le concept « ajouter 2 et 3 à un objet de type `Point`», «2 à ajouter à la coordonnée *x* et 3 à ajouter à la coordonnée *y* .

- Les opérateurs unaires déclarés comme fonctions membres n’acceptent pas d’argument ; s’ils sont déclarés comme fonctions globales, ils en prennent un.

- Les opérateurs binaires déclarés comme fonctions membres acceptent un argument ; s’ils sont déclarés comme fonctions globales, ils en prennent deux.

- Si un opérateur peut être utilisé comme opérateur unaire ou binaire ( __&__ , __*__ , __+__ et __-__ ), vous pouvez surcharger chaque utilisation séparément.

- Les opérateurs surchargés ne peuvent pas avoir d’arguments par défaut.

- Tous les opérateurs surchargés, à l’exception de l’assignation (**Operator =** ), sont hérités par les classes dérivées.

- Le premier argument pour les opérateurs surchargés déclarés comme fonctions membres est toujours le type de classe de l’objet pour lequel l’opérateur est appelé (la classe dans laquelle l’opérateur est déclaré ou une classe dérivée de cette classe). Aucune conversion n'est fournie pour le premier argument.

Notez que la signification de n'importe quel opérateur peut être modifiée complètement. Cela comprend la signification des opérateurs Address-of ( **&** ), Assignment ( **=** ) et Function-Call. En outre, les identités sur lesquelles on peut se reposer pour les types intégrés peuvent être modifiées à l'aide de la surcharge d'opérateur. Par exemple, les quatre instructions suivantes sont généralement équivalentes une fois leur évaluation terminée :

```cpp
var = var + 1;
var += 1;
var++;
++var;
```

On ne peut pas se reposer sur cette identité pour les types de classe qui surchargent des opérateurs. De plus, certaines des exigences implicites dans l’utilisation de ces opérateurs pour les types de base sont allégées pour les opérateurs surchargés. Par exemple, l’opérateur d’addition/assignation, **+=** , requiert que l’opérande gauche soit une l-value lorsqu’il est appliqué à des types de base ; Il n’existe aucune exigence de ce type lorsque l’opérateur est surchargé.

> [!NOTE]
> Pour des raisons de cohérence, il est souvent préférable de suivre le modèle des types intégrés lors de la définition des opérateurs surchargés. Si la sémantique d'un opérateur surchargé diffère sensiblement de sa signification dans d'autres contextes, il peut être plus perturbant qu'utile.

## <a name="see-also"></a>Voir aussi

[Surcharge d'opérateur](../cpp/operator-overloading.md)
