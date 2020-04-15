---
title: Déléguer des constructeurs (C)
description: Utilisez des constructeurs délédifiants dans le C POUR invoquer d’autres constructeurs et réduire la répétition du code.
ms.date: 11/19/2019
ms.openlocfilehash: f26a013aa3c081d900ffc3eb32649acc77505db0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81316670"
---
# <a name="delegating-constructors"></a>Constructeurs effectuant une délégation

De nombreuses classes ont plusieurs constructeurs qui font des choses similaires, par exemple, valider les paramètres:

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

Vous pourriez réduire le code répétitif en ajoutant une fonction `class_c` qui fait toute la validation, mais le code pour serait plus facile à comprendre et à maintenir si un constructeur pourrait déléguer une partie du travail à un autre. Pour ajouter des constructeurs délédants, utilisez la `constructor (. . .) : constructor (. . .)` syntaxe :

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

Lorsque vous passez par l’exemple précédent, notez que le constructeur `class_c(int, int, int)` appelle d’abord le `class_c(int, int)`constructeur, qui à son tour appelle `class_c(int)`. Chacun des constructeurs n’exécute que l’œuvre qui n’est pas effectuée par les autres constructeurs.

Le premier constructeur qui s’appelle initialise l’objet de sorte que tous ses membres sont parasécés à ce moment-là. Vous ne pouvez pas faire l’initialisation des membres dans un constructeur qui délègue à un autre constructeur, comme indiqué ici:

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

L’exemple suivant montre l’utilisation d’initialisateurs non statiques de données-membres. Notez que si un constructeur initialise également un membre de données donné, l’initialisateur membre est remplacé :

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

La syntaxe de délégation constructeur n’empêche pas la création accidentelle de récursion constructeur-Constructor1 appelle Constructor2 qui appelle Constructor1 - et aucune erreur n’est lancée jusqu’à ce qu’il y ait un débordement de pile. C’est votre responsabilité d’éviter les cycles.

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
