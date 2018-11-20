---
title: Cast
ms.date: 11/19/2018
helpviewer_keywords:
- casting [C++]
- coercion [C++]
- virtual functions [C++], in derived classes [C++]
- static cast operator
- dynamic cast operator
- polymorphic classes [C++]
- classes [C++], polymorphism
ms.assetid: 3dbeb06e-2f4b-4693-832d-624bc8ec95de
ms.openlocfilehash: 02ade663ee92d3a301fda95bb385c3ffa48ead12
ms.sourcegitcommit: 9e891eb17b73d98f9086d9d4bfe9ca50415d9a37
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2018
ms.locfileid: "52175546"
---
# <a name="casting"></a>Cast

Le langage C++ prévoit que si une classe est dérivée d'une classe de base contenant des fonctions virtuelles, un pointeur vers ce type de classe de base peut être utilisé pour appeler les implémentations des fonctions virtuelles résidant dans l'objet classe dérivé. Une classe contenant des fonctions virtuelles est parfois appelée une classe polymorphe.

Étant donné qu'une classe dérivée contient les définitions de toutes les classes de base dont elle est dérivée, il est possible de convertir un pointeur qui va jusqu'en haut de la hiérarchie de classes en l'une de ces classes de base. S'il existe un pointeur vers une classe de base, il est possible de le convertit jusqu'en bas de la hiérarchie. Cela est possible si l'objet qui est pointé est réellement d'un type dérivé de la classe de base. Dans ce cas, l'objet lui-même est appelé l'objet complet. On dit que le pointeur vers la classe de base pointe vers un sous-objet de l'objet complet. Considérons, par exemple, la hiérarchie de classe représentée dans l'illustration ci-dessous.

![Hiérarchie de classes](../cpp/media/vc38zz1.gif "hiérarchie de classes") <br/>
Hiérarchie de classes

Un objet de type `C` peut être visualisé comme indiqué dans l'illustration ci-dessous.

![Classe C avec sub&#45;objets B et A](../cpp/media/vc38zz2.gif "classe C avec sub&#45;objets B et A") <br/>
Classe C avec les sous-objets B et A

Avec une instance de classe `C`, il y a un sous-objet `B` et un sous-objet `A`. L'instance de `C`, avec les sous-objets `A` et `B` forme l'objet complet.

En utilisant les informations de type au moment de l'exécution, il est possible de vérifier si un pointeur pointe réellement vers un objet complet et peut être casté sans risque vers un autre objet de sa hiérarchie. Le [dynamic_cast](../cpp/dynamic-cast-operator.md) opérateur peut être utilisé pour effectuer ces types de casts. Il exécute également le contrôle à l'exécution nécessaire pour sécuriser l'opération.

Pour la conversion des types non polymorphes, vous pouvez utiliser la [static_cast](../cpp/static-cast-operator.md) opérateur (cette rubrique explique la différence entre les conversions de casting statiques et dynamiques, et quand il convient d’utiliser chaque).

Cette section couvre les rubriques suivantes :

- [Opérateurs de casting](../cpp/casting-operators.md)

- [Informations de type au moment de l’exécution](../cpp/run-time-type-information.md)

## <a name="see-also"></a>Voir aussi

[Expressions](../cpp/expressions-cpp.md)