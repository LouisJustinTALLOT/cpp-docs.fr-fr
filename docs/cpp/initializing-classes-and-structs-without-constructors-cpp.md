---
title: Initialisation de brace pour les classes, les structs et les syndicats
description: Utilisez l’initialisation d’accolade avec n’importe quelle classe, struct ou syndicat de CMD
ms.date: 11/19/2019
ms.assetid: 3e55c3d6-1c6b-4084-b9e5-221b151402f4
ms.openlocfilehash: 4628ffe8935fc32e86468c631d5d9e9622d63d2e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374073"
---
# <a name="brace-initialization"></a>Initialisation de l’accolade

Il n'est pas toujours nécessaire de définir un constructeur pour une classe, en particulier celles qui sont relativement simples. Les utilisateurs peuvent initialiser des objets d'une classe ou d'un struct à l'aide de l'initialisation uniforme, comme illustré dans l'exemple suivant :

```cpp
// no_constructor.cpp
// Compile with: cl /EHsc no_constructor.cpp
#include <time.h>

// No constructor
struct TempData
{
    int StationId;
    time_t timeSet;
    double current;
    double maxTemp;
    double minTemp;
};

// Has a constructor
struct TempData2
{
    TempData2(double minimum, double maximum, double cur, int id, time_t t) :
       stationId{id}, timeSet{t}, current{cur}, maxTemp{maximum}, minTemp{minimum} {}
    int stationId;
    time_t timeSet;
    double current;
    double maxTemp;
    double minTemp;
};

int main()
{
    time_t time_to_set;

    // Member initialization (in order of declaration):
    TempData td{ 45978, time(&time_to_set), 28.9, 37.0, 16.7 };

    // Default initialization = {0,0,0,0,0}
    TempData td_default{};

    // Uninitialized = if used, emits warning C4700 uninitialized local variable
    TempData td_noInit;

    // Member declaration (in order of ctor parameters)
    TempData2 td2{ 16.7, 37.0, 28.9, 45978, time(&time_to_set) };

    return 0;
}
```

Notez que lorsqu’une classe ou une struct n’a pas de constructeur, vous fournissez les éléments de liste dans l’ordre que les membres sont déclarés dans la classe. Si la classe a un constructeur, fournir les éléments dans l’ordre des paramètres. Si un type a un constructeur par défaut, implicitement ou explicitement déclaré, vous pouvez utiliser l’initialisation d’attelle par défaut (avec des accolades vides). Par exemple, la classe suivante peut être parascée en utilisant à la fois l’initialisation par défaut et l’initialisation d’accolade non par défaut :

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

Si une classe a des constructeurs non par défaut, l’ordre dans lequel les membres de la classe apparaissent dans l’initialisateur d’accolade est l’ordre dans lequel les paramètres correspondants apparaissent dans le constructeur, et non l’ordre dans lequel les membres sont déclarés (comme dans l’exemple `class_a` précédent). Dans le cas contraire, si le type n’a pas de constructeur déclaré, l’ordre dans lequel les membres apparaissent dans l’initialisateur d’accolade est le même que l’ordre dans lequel ils sont déclarés; dans ce cas, vous pouvez initialiser autant de membres du public que vous le souhaitez, mais vous ne pouvez pas sauter n’importe quel membre. L’exemple suivant montre l’ordre utilisé dans l’initialisation de l’attelle lorsqu’il n’y a pas de constructeur déclaré :

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
    class_d d5{ "string", 'c', 2.0 }; // compiler error
}
```

Si le constructeur par défaut est explicitement déclaré mais marqué comme supprimé, l’initialisation par défaut d’accolade ne peut pas être utilisée :

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

Vous pouvez utiliser l’initialisation d’accolade où vous feriez généralement l’initialisation, par exemple, comme paramètre de fonction ou valeur de retour, ou avec le **nouveau** mot clé :

```cpp
class_d* cf = new class_d{4.5};
kr->add_d({ 4.5 });
return { 4.5 };
```

En **mode /std:c -17,** les règles d’initialisation des accolades vides sont légèrement plus restrictives. Voir [les constructeurs dérivés et l’initialisation globale étendue](constructors-cpp.md#extended_aggregate).

## <a name="initializer_list-constructors"></a>initializer_list constructeurs

La [classe initializer_list](../standard-library/initializer-list-class.md) représente une liste d’objets d’un type spécifié qui peuvent être utilisés dans un constructeur, et dans d’autres contextes. Vous pouvez construire un initializer_list en utilisant l’initialisation d’accolade :

```cpp
initializer_list<int> int_list{5, 6, 7};
```

> [!IMPORTANT]
> Pour utiliser cette classe, [ \<](../standard-library/initializer-list.md) vous devez inclure le initializer_list>en-tête.

On `initializer_list` peut copier un. Dans ce cas, les membres de la nouvelle liste sont des références aux membres de la liste originale :

```cpp
initializer_list<int> ilist1{ 5, 6, 7 };
initializer_list<int> ilist2( ilist1 );
if (ilist1.begin() == ilist2.begin())
    cout << "yes" << endl; // expect "yes"
```

Les classes standard de `string`récipient `wstring`de `regex`bibliothèque, et aussi , et , ont `initializer_list` des constructeurs. Les exemples suivants montrent comment faire l’initialisation de l’accolade avec ces constructeurs :

```cpp
vector<int> v1{ 9, 10, 11 };
map<int, string> m1{ {1, "a"}, {2, "b"} };
string s{ 'a', 'b', 'c' };
regex rgx{ 'x', 'y', 'z' };
```

## <a name="see-also"></a>Voir aussi

[Classes et structs](../cpp/classes-and-structs-cpp.md)<br/>
[Constructeurs](../cpp/constructors-cpp.md)
