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
ms.openlocfilehash: bb06db3af6aee031b6cb2d69b38a9404304420fc
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80190126"
---
# <a name="casting"></a>Cast

Le langage C++ prévoit que si une classe est dérivée d'une classe de base contenant des fonctions virtuelles, un pointeur vers ce type de classe de base peut être utilisé pour appeler les implémentations des fonctions virtuelles résidant dans l'objet classe dérivé. Une classe contenant des fonctions virtuelles est parfois appelée une classe polymorphe.

Étant donné qu'une classe dérivée contient les définitions de toutes les classes de base dont elle est dérivée, il est possible de convertir un pointeur qui va jusqu'en haut de la hiérarchie de classes en l'une de ces classes de base. S'il existe un pointeur vers une classe de base, il est possible de le convertit jusqu'en bas de la hiérarchie. Cela est possible si l'objet qui est pointé est réellement d'un type dérivé de la classe de base. Dans ce cas, l'objet lui-même est appelé l'objet complet. On dit que le pointeur vers la classe de base pointe vers un sous-objet de l'objet complet. Considérons, par exemple, la hiérarchie de classe représentée dans l'illustration ci-dessous.

![Hiérarchie de classes](../cpp/media/vc38zz1.gif "Hiérarchie de classes") <br/>
Hiérarchie de classes

Un objet de type `C` peut être visualisé comme indiqué dans l'illustration ci-dessous.

![Classe C avec les&#45;sous-objets B et A](../cpp/media/vc38zz2.gif "Classe C avec les&#45;sous-objets B et A") <br/>
Classe C avec les sous-objets B et A

Avec une instance de classe `C`, il y a un sous-objet `B` et un sous-objet `A`. L'instance de `C`, avec les sous-objets `A` et `B` forme l'objet complet.

En utilisant les informations de type au moment de l'exécution, il est possible de vérifier si un pointeur pointe réellement vers un objet complet et peut être casté sans risque vers un autre objet de sa hiérarchie. L’opérateur [dynamic_cast](../cpp/dynamic-cast-operator.md) peut être utilisé pour effectuer ces types de casts. Il exécute également le contrôle à l'exécution nécessaire pour sécuriser l'opération.

Pour la conversion de types des non polymorphes, vous pouvez utiliser l’opérateur [static_cast](../cpp/static-cast-operator.md) (cette rubrique explique la différence entre les conversions de cast statique et dynamique, et quand il est approprié d’utiliser chacune d’elles).

Cette section couvre les sujets suivants :

- [Opérateurs de cast](../cpp/casting-operators.md)

- [Informations de type au moment de l’exécution](../cpp/run-time-type-information.md)

## <a name="see-also"></a>Voir aussi

[Expressions](../cpp/expressions-cpp.md)
