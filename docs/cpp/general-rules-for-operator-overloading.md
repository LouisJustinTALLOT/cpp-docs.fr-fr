---
title: Règles générales de surcharge d’opérateur | Documents Microsoft
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
ms.openlocfilehash: d6912d410018966432ef66331354213bd70dfa8b
ms.sourcegitcommit: e3b4ef19b534a2ed48bb9091e5197a6e536f16c1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2018
ms.locfileid: "34814337"
---
# <a name="general-rules-for-operator-overloading"></a>Règles générales de surcharge d'opérateur
Les règles suivantes limitent le mode d'implémentation des opérateurs surchargés. Toutefois, ils ne s’appliquent pas à la [nouveau](../cpp/new-operator-cpp.md) et [supprimer](../cpp/delete-operator-cpp.md) operators, qui sont traités séparément.  
  
-   Vous ne pouvez pas définir de nouveaux opérateurs tels que **.**.  
  
-   Vous ne pouvez pas redéfinir la signification d'opérateurs lorsqu'ils sont appliqués à des types de données intégrés.  
  
-   Les opérateurs surchargés doivent être soit une fonction de membre de classe non statique, soit une fonction globale. Une fonction globale qui nécessite un accès à des membres de classe privés ou protégés doit être déclarée comme amie de cette classe. Une fonction globale doit prendre au moins un argument qui est de type classe ou énuméré ou qui est une référence à un type énuméré ou classe. Exemple :  
  
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
  
     L'exemple de code précédent déclare l'opérateur Inférieur à comme fonction membre ; toutefois, les opérateurs d'addition sont déclarés comme fonctions globales qui ont un accès ami. Notez que plusieurs implémentations peuvent être fournies pour un opérateur donné. Dans le cas de l'opérateur d'addition précédent, les deux implémentations sont fournies pour faciliter la commutativité. Il est tout aussi probable que des opérateurs qui ajoutent un `Point` à un `Point`, `int` à un `Point`, et ainsi de suite, soient implémentés.  
  
-   Les opérateurs obéissent aux règles de priorité, de regroupement et de nombre d’opérandes dictées par leur utilisation classique avec les types intégrés. Par conséquent, il n’existe aucun moyen d’exprimer le concept « ajouter 2 et 3 pour un objet de type `Point`, « attendu 2 à ajouter à la *x* coordonnée et 3 à ajouter à la *y* coordonner.  
  
-   Les opérateurs unaires déclarés comme fonctions membres n’acceptent pas d’argument ; s’ils sont déclarés comme fonctions globales, ils en prennent un.  
  
-   Les opérateurs binaires déclarés comme fonctions membres acceptent un argument ; s’ils sont déclarés comme fonctions globales, ils en prennent deux.  
  
-   Si un opérateur peut être utilisé comme un opérateur unaire ou un opérateur binaire (__&__, __*__, __+__, et __-__), vous pouvez surcharger séparément chaque utilisation.  
  
-   Les opérateurs surchargés ne peuvent pas avoir d’arguments par défaut.  
  
-   Tous les opérateurs surchargés à l'exception de l'assignation (`operator=`) sont hérités par des classes dérivées.  
  
-   Le premier argument pour les opérateurs surchargés déclarés comme fonctions membres est toujours le type de classe de l’objet pour lequel l’opérateur est appelé (la classe dans laquelle l’opérateur est déclaré ou une classe dérivée de cette classe). Aucune conversion n'est fournie pour le premier argument.  
  
 Notez que la signification de n'importe quel opérateur peut être modifiée complètement. Qui inclut la signification de l’adresse de (**&**), l’attribution (**=**) et les opérateurs d’appel de fonction. En outre, les identités sur lesquelles on peut se reposer pour les types intégrés peuvent être modifiées à l'aide de la surcharge d'opérateur. Par exemple, les quatre instructions suivantes sont généralement équivalentes une fois leur évaluation terminée :  
  
```  
var = var + 1;  
var += 1;  
var++;  
++var;  
```  
  
 On ne peut pas se reposer sur cette identité pour les types de classe qui surchargent des opérateurs. De plus, certaines des exigences implicites dans l’utilisation de ces opérateurs pour les types de base sont allégées pour les opérateurs surchargés. Par exemple, l'opérateur d'addition/assignation, `+=`, requiert que l'opérande gauche soit une l-value en cas d'application à des types de base ; il n'existe aucune spécification de ce genre lorsque l'opérateur est surchargé.  
  
> [!NOTE]
> Pour des raisons de cohérence, il est souvent préférable de suivre le modèle des types intégrés lors de la définition des opérateurs surchargés. Si la sémantique d'un opérateur surchargé diffère sensiblement de sa signification dans d'autres contextes, il peut être plus perturbant qu'utile.  
  
## <a name="see-also"></a>Voir aussi  
 [Surcharge d'opérateur](../cpp/operator-overloading.md)