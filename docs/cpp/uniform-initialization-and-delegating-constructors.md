---
title: Constructeurs d'initialisation uniforme et de délégation
ms.date: 11/04/2016
ms.assetid: aa4daa64-eaec-4a3c-ade4-d9325e31e9d4
ms.openlocfilehash: 5c5cb6421d9c8ce20f0c5e24de986ee50d9b2238
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50496601"
---
# <a name="uniform-initialization-and-delegating-constructors"></a>Constructeurs d'initialisation uniforme et de délégation

En C++ moderne, vous pouvez utiliser *accolade initialisation* pour n’importe quel type, sans le signe égal. En outre, vous pouvez utiliser les constructeurs de délégation pour simplifier votre code lorsque vous avez plusieurs constructeurs qui effectuent un travail similaire.

## <a name="brace-initialization"></a>Initialisation de l’accolade

Vous pouvez utiliser des accolades pour toute classe, un struct ou une union. Si un type a un constructeur par défaut, implicitement ou explicitement déclaré, vous pouvez utiliser des accolades par défaut (avec accolades vides). Par exemple, la classe suivante peut être initialisée à l’aide de la valeur par défaut et les accolades non définis par défaut :

```cpp
#include <string>
using namespace std;

class class_a {
public:
    class_a() {}
    class_a(string str) : m_string{ str } {}
    class_a(string str, double dbl) : m_string{ str }, m_double{ dbl } {}
double m_double;
string m_string;
};

int main()
{
    class_a c1{};
    class_a c1_1;

    class_a c2{ "ww" };
    class_a c2_1("xx");

    // order of parameters is the same as the constructor
    class_a c3{ "yy", 4.4 };
    class_a c3_1("zz", 5.5);
}
```

Si une classe a des constructeurs non définis par défaut, l’ordre dans la classe que les membres apparaissent dans l’initialiseur accolade est l’ordre dans lequel les paramètres correspondants dans le constructeur, pas l’ordre dans lequel les membres sont déclarés (comme avec `class_a` dans le exemple précédent). Sinon, si le type ne possède aucun constructeur déclaré, l’ordre dans lequel les membres dans l’initialiseur accolade est identique à l’ordre dans lequel ils sont déclarés. Dans ce cas, vous pouvez initialiser autant de membres publics comme vous le souhaitez, mais vous ne pouvez pas ignorer tous les membres. L’exemple suivant montre l’ordre qui est utilisé dans les accolades quand il n’existe aucun constructeur déclaré :

```cpp
class class_d {
public:
    float m_float;
    string m_string;
    wchar_t m_char;
};

int main()
{
    class_d d1{};
    class_d d1{ 4.5 };
    class_d d2{ 4.5, "string" };
    class_d d3{ 4.5, "string", 'c' };

    class_d d4{ "string", 'c' }; // compiler error
    class_d d5("string", 'c', 2.0 }; // compiler error
}
```

Si le constructeur par défaut n’est explicitement déclaré mais est marqué comme supprimé, accolades par défaut ne peut pas être utilisé :

```cpp
class class_f {
public:
    class_f() = delete;
    class_f(string x): m_string { x } {}
    string m_string;
};
int main()
{
    class_f cf{ "hello" };
    class_f cf1{}; // compiler error C2280: attempting to reference a deleted function
}
```

Vous pouvez utiliser des accolades n’importe où vous le feriez d’initialisation, par exemple, comme un paramètre de fonction ou une valeur de retour, ou avec la **nouveau** mot clé :

```cpp
class_d* cf = new class_d{4.5};
kr->add_d({ 4.5 });
return { 4.5 };
```

## <a name="initializerlist-constructors"></a>initializer_list constructeurs

Le [initializer_list, classe](../standard-library/initializer-list-class.md) représente une liste d’objets d’un type spécifié qui peut être utilisé dans un constructeur et dans d’autres contextes. Vous pouvez construire un objet initializer_list à l’aide d’accolades :

```cpp
initializer_list<int> int_list{5, 6, 7};
```

> [!IMPORTANT]
>  Pour utiliser cette classe, vous devez inclure le [ \<initializer_list >](../standard-library/initializer-list.md) en-tête.

Un `initializer_list` peuvent être copiés. Dans ce cas, les membres de la nouvelle liste sont des références aux membres de la liste d’origine :

```cpp
initializer_list<int> ilist1{ 5, 6, 7 };
initializer_list<int> ilist2( ilist1 );
if (ilist1.begin() == ilist2.begin())
    cout << "yes" << endl; // expect "yes"
```

Les classes de conteneur de bibliothèque standard et également `string`, `wstring`, et `regex`, ont `initializer_list` constructeurs. Les exemples suivants montrent comment accolade l’initialisation avec ces constructeurs :

```cpp
vector<int> v1{ 9, 10, 11 };
map<int, string> m1{ {1, "a"}, {2, "b"} };
string s{ 'a', 'b', 'c' };
regex rgx{'x', 'y', 'z'};
```

## <a name="delegating-constructors"></a>Constructeurs qui effectuent une délégation

De nombreuses classes possèdent plusieurs constructeurs qui faire des choses similaires, par exemple, valider les paramètres :

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

Vous pouvez réduire le code répétitif en ajoutant une fonction qui effectue tout de la validation, mais le code pour `class_c` serait plus facile à comprendre et à gérer si un constructeur peut déléguer une partie du travail à un autre. Pour ajouter les constructeurs de délégation, utilisez le `constructor (. . .) : constructor (. . .)` syntaxe :

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

À mesure que vous parcourez l’exemple précédent, notez que le constructeur `class_c(int, int, int)` appelle d’abord le constructeur `class_c(int, int)`, qui appelle à son tour `class_c(int)`. Chacun des constructeurs effectue uniquement le travail qui n’est pas effectué par les autres constructeurs.

Le premier constructeur est appelé initialise l’objet afin que tous ses membres sont initialisés à ce stade. Vous ne pouvez pas faire d’initialisation de membre dans un constructeur qui délègue à un autre constructeur, comme illustré ici :

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

L’exemple suivant illustre l’utilisation d’initialiseurs de membre de données non statiques. Notez que si un constructeur initialise également un membre de données donné, l’initialiseur de membre est remplacée :

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

La syntaxe de délégation du constructeur n’empêche pas la création accidentelle de récursivité de constructeur — Constructor1 appelle Constructor2 qui appelle Constructor1 — et qu’aucune erreur n’est levée jusqu'à ce qu’un dépassement de capacité de pile. Il vous incombe d’éviter les cycles.

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