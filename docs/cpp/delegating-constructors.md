---
title: Constructeurs de délégation (C++)
description: Utilisez des constructeurs de délégation dans C++ pour appeler d’autres constructeurs et réduire la répétition de code.
ms.date: 11/19/2019
ms.openlocfilehash: 533cdfbeb882f3770cc554b0633611a4ffc2cfbd
ms.sourcegitcommit: 654aecaeb5d3e3fe6bc926bafd6d5ace0d20a80e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2019
ms.locfileid: "74250673"
---
# <a name="delegating-constructors"></a>Constructeurs effectuant une délégation

De nombreuses classes ont plusieurs constructeurs qui effectuent des opérations similaires, par exemple valider des paramètres :

```cpp
class class_c {
public:
    int max;
    int min;
    int middle;

    class_c() {}
    class_c(int my_max) {
        max = my_max > 0 ? my_max : 10;
    }
    class_c(int my_max, int my_min) {
        max = my_max > 0 ? my_max : 10;
        min = my_min > 0 && my_min < max ? my_min : 1;
    }
    class_c(int my_max, int my_min, int my_middle) {
        max = my_max > 0 ? my_max : 10;
        min = my_min > 0 && my_min < max ? my_min : 1;
        middle = my_middle < max && my_middle > min ? my_middle : 5;
    }
};
```

Vous pouvez réduire le code répétitif en ajoutant une fonction qui effectue toute la validation, mais le code pour `class_c` serait plus facile à comprendre et à gérer si un constructeur pourrait déléguer une partie du travail à un autre. Pour ajouter des constructeurs de délégation, utilisez la syntaxe `constructor (. . .) : constructor (. . .)` :

```cpp
class class_c {
public:
    int max;
    int min;
    int middle;

    class_c(int my_max) {
        max = my_max > 0 ? my_max : 10;
    }
    class_c(int my_max, int my_min) : class_c(my_max) {
        min = my_min > 0 && my_min < max ? my_min : 1;
    }
    class_c(int my_max, int my_min, int my_middle) : class_c (my_max, my_min){
        middle = my_middle < max && my_middle > min ? my_middle : 5;
}
};
int main() {

    class_c c1{ 1, 3, 2 };
}
```

À mesure que vous parcourez l’exemple précédent, remarquez que le constructeur `class_c(int, int, int)` appelle d’abord le constructeur `class_c(int, int)`, qui à son tour appelle `class_c(int)`. Chacun des constructeurs exécute uniquement le travail qui n’est pas effectué par les autres constructeurs.

Le premier constructeur appelé Initialise l’objet de sorte que tous ses membres soient initialisés à ce stade. Vous ne pouvez pas effectuer d’initialisation de membre dans un constructeur qui délègue à un autre constructeur, comme illustré ici :

```cpp
class class_a {
public:
    class_a() {}
    // member initialization here, no delegate
    class_a(string str) : m_string{ str } {}

    //can’t do member initialization here
    // error C3511: a call to a delegating constructor shall be the only member-initializer
    class_a(string str, double dbl) : class_a(str) , m_double{ dbl } {}

    // only member assignment
    class_a(string str, double dbl) : class_a(str) { m_double = dbl; }
    double m_double{ 1.0 };
    string m_string;
};
```

L’exemple suivant illustre l’utilisation d’initialiseurs de membres de données non statiques. Notez que si un constructeur initialise également un membre de données donné, l’initialiseur de membre est substitué :

```cpp
class class_a {
public:
    class_a() {}
    class_a(string str) : m_string{ str } {}
    class_a(string str, double dbl) : class_a(str) { m_double = dbl; }
    double m_double{ 1.0 };
    string m_string{ m_double < 10.0 ? "alpha" : "beta" };
};

int main() {
    class_a a{ "hello", 2.0 };  //expect a.m_double == 2.0, a.m_string == "hello"
    int y = 4;
}
```

La syntaxe de délégation du constructeur n’empêche pas la création accidentelle de la récursivité du constructeur (constructor1 appelle Constructor2 qui appelle constructor1) et aucune erreur n’est levée tant qu’il n’y a pas de dépassement de capacité de la pile. Il vous incombe d’éviter les cycles.

```cpp
class class_f{
public:
    int max;
    int min;

    // don't do this
    class_f() : class_f(6, 3){ }
    class_f(int my_max, int my_min) : class_f() { }
};
```
