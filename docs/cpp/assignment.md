---
description: 'En savoir plus sur : affectation'
title: Affectation
ms.date: 11/04/2016
helpviewer_keywords:
- operators [C++], assignment
- assignment operators [C++], overloaded
ms.assetid: d87e4f89-f8f5-42c1-9d3c-184bca9d0e15
ms.openlocfilehash: 696706202e70e8baf50dda34ac98ff9bca5dcda2
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97319484"
---
# <a name="assignment"></a>Affectation

L’opérateur d’assignation ( **=** ) est, strictement parlant, un opérateur binaire. Sa déclaration est identique à celle de tout autre opérateur binaire, avec les exceptions suivantes :

- Il doit s'agir d'une fonction membre non statique. Aucun **opérateur =** ne peut être déclaré en tant que fonction non membre.
- Il n'est pas hérité par les classes dérivées.
- Une fonction **Operator =** par défaut peut être générée par le compilateur pour les types de classe, s’il n’en existe aucun.

L'exemple suivant montre comment déclarer un opérateur d'assignation :

```cpp
class Point
{
public:
    int _x, _y;

    // Right side of copy assignment is the argument.
    Point& operator=(const Point&);
};

// Define copy assignment operator.
Point& Point::operator=(const Point& otherPoint)
{
    _x = otherPoint._x;
    _y = otherPoint._y;

    // Assignment operator returns left side of assignment.
    return *this;
}

int main()
{
    Point pt1, pt2;
    pt1 = pt2;
}
```

L’argument fourni est le côté droit de l’expression. L'opérateur retourne l'objet pour conserver le comportement de l'opérateur d'assignation, qui retourne la valeur du côté gauche une fois l'assignation terminée. Cela permet d’enchaîner des assignations, telles que :

```cpp
pt1 = pt2 = pt3;
```

L’opérateur d’assignation de copie ne doit pas être confondu avec le constructeur de copie. Ce dernier est appelé pendant la construction d’un nouvel objet à partir d’un objet existant :

```cpp
// Copy constructor is called--not overloaded copy assignment operator!
Point pt3 = pt1;

// The previous initialization is similar to the following:
Point pt4(pt1); // Copy constructor call.
```

> [!NOTE]
> Il est recommandé de suivre la [règle de trois](https://en.wikipedia.org/wiki/Rule_of_three_(C%2B%2B_programming)) qu’une classe qui définit un opérateur d’assignation de copie doit également définir explicitement le constructeur de copie, le destructeur et, à partir de c++ 11, le constructeur de déplacement et l’opérateur d’assignation de déplacement.

## <a name="see-also"></a>Voir aussi

- [Surcharge d’opérateur](../cpp/operator-overloading.md)
- [Constructeurs de copie et opérateurs d'assignation de copie (C++)](../cpp/copy-constructors-and-copy-assignment-operators-cpp.md)
