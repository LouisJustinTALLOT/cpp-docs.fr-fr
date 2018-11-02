---
title: Attribution
ms.date: 11/04/2016
helpviewer_keywords:
- operators [C++], assignment
- assignment operators [C++], overloaded
ms.assetid: d87e4f89-f8f5-42c1-9d3c-184bca9d0e15
ms.openlocfilehash: 1e6d715011cfaab7e250e23a9a31bb3f0c83f36a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50603431"
---
# <a name="assignment"></a>Attribution

L’opérateur d’assignation (**=**) est à proprement parler, un opérateur binaire. Sa déclaration est identique à celle de tout autre opérateur binaire, avec les exceptions suivantes :

- Il doit s'agir d'une fonction membre non statique. Ne **opérateur =** peuvent être déclarées comme une fonction non membre.
- Il n'est pas hérité par les classes dérivées.
- Une valeur par défaut **opérateur =** fonction peut être générée par le compilateur pour les types de classe, si aucune n’existe.

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

L’argument fourni est le côté droit de l’expression. L'opérateur retourne l'objet pour conserver le comportement de l'opérateur d'assignation, qui retourne la valeur du côté gauche une fois l'assignation terminée. Cela permet le chaînage des affectations, telles que :

```cpp
pt1 = pt2 = pt3;
```

L’opérateur d’assignation de copie est à ne pas confondre avec le constructeur de copie. Celle-ci est appelée pendant la construction d’un nouvel objet à partir d’une existante :

```cpp
// Copy constructor is called--not overloaded copy assignment operator!
Point pt3 = pt1;

// The previous initialization is similar to the following:
Point pt4(pt1); // Copy constructor call.
```

> [!NOTE]
> Il est recommandé de suivre le [règle de trois](https://en.wikipedia.org/wiki/Rule_of_three_(C%2B%2B_programming)) qu’une classe qui définit un opérateur d’assignation de copie doit également définir explicitement le constructeur de copie, le destructeur et, en commençant par C ++ 11, déplacent constructeur et déplacer l’attribution d’opérateur.

## <a name="see-also"></a>Voir aussi

- [Surcharge d'opérateur](../cpp/operator-overloading.md)
- [Constructeurs de copie et opérateurs d’assignation de copie (C++)](../cpp/copy-constructors-and-copy-assignment-operators-cpp.md)