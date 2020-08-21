---
title: union
description: Description du union class type et du mot clé C++ standard, de son utilisation et de ses restrictions.
ms.date: 08/18/2020
f1_keywords:
- union_cpp
helpviewer_keywords:
- class type [C++], union as
- union keyword [C++]
ms.assetid: 25c4e219-fcbb-4b7b-9b64-83f3252a92ca
no-loc:
- union
- struct
- enum
- class
- static
ms.openlocfilehash: a4dc07df5e7858dffe62478509ee1d8dc759ce96
ms.sourcegitcommit: f1752bf90b4f869633a859ace85439ca19e208b2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/21/2020
ms.locfileid: "88722178"
---
# `union`

> [!NOTE]
> Dans C++ 17 et versions ultérieures, `std::variant` class est une alternative de type sécurisé pour un union .

Un **`union`** est un type défini par l’utilisateur dans lequel tous les membres partagent le même emplacement de mémoire. Cette définition signifie qu’à un moment donné, un union ne peut pas contenir plus d’un objet de sa liste de membres. Cela signifie également que, quel que soit le nombre de membres d’un union , il n’utilise toujours que suffisamment de mémoire pour stocker le plus grand membre.

Un union peut être utile pour conserver de la mémoire lorsque vous avez un grand nombre d’objets et une quantité de mémoire limitée. Toutefois, un union nécessite une attention supplémentaire pour être correctement utilisé. Vous êtes tenu de vous assurer que vous accédez toujours au même membre que vous avez attribué. Si des types de membres ont un con non trivial struct ou, vous devez écrire du code supplémentaire pour explicitement con struct et détruire ce membre. Avant d’utiliser un union , déterminez si le problème que vous tentez de résoudre peut être mieux exprimé à l’aide d’un type de base class et de types dérivés class .

## <a name="syntax"></a>Syntaxe

> **`union`***`tag`* <sub>opt</sub> **`{`** OPT *`member-list`***`};`**

### <a name="parameters"></a>Paramètres

*`tag`*<br/>
Nom de type donné à union .

*`member-list`*<br/>
Membres que union peut contenir.

## <a name="declare-a-no-locunion"></a>Déclarer un union

Commencez la déclaration d’un union en utilisant le **`union`** mot clé et mettez la liste des membres entre accolades :

```cpp
// declaring_a_union.cpp
union RecordType    // Declare a simple union type
{
    char   ch;
    int    i;
    long   l;
    float  f;
    double d;
    int *int_ptr;
};

int main()
{
    RecordType t;
    t.i = 5; // t holds an int
    t.f = 7.25; // t now holds a float
}
```

## <a name="use-a-no-locunion"></a>Utilisez une union

Dans l’exemple précédent, tout code qui accède au union doit savoir quel membre contient les données. La solution la plus courante à ce problème est dite *discriminée union *. Il englobe le union dans un struct et comprend un enum membre qui indique le type de membre actuellement stocké dans le union . L'exemple suivant illustre le modèle de base :

```cpp
#include <queue>

using namespace std;

enum class WeatherDataType
{
    Temperature, Wind
};

struct TempData
{
    int StationId;
    time_t time;
    double current;
    double max;
    double min;
};

struct WindData
{
    int StationId;
    time_t time;
    int speed;
    short direction;
};

struct Input
{
    WeatherDataType type;
    union
    {
        TempData temp;
        WindData wind;
    };
};

// Functions that are specific to data types
void Process_Temp(TempData t) {}
void Process_Wind(WindData w) {}

void Initialize(std::queue<Input>& inputs)
{
    Input first;
    first.type = WeatherDataType::Temperature;
    first.temp = { 101, 1418855664, 91.8, 108.5, 67.2 };
    inputs.push(first);

    Input second;
    second.type = WeatherDataType::Wind;
    second.wind = { 204, 1418859354, 14, 27 };
    inputs.push(second);
}

int main(int argc, char* argv[])
{
    // Container for all the data records
    queue<Input> inputs;
    Initialize(inputs);
    while (!inputs.empty())
    {
        Input const i = inputs.front();
        switch (i.type)
        {
        case WeatherDataType::Temperature:
            Process_Temp(i.temp);
            break;
        case WeatherDataType::Wind:
            Process_Wind(i.wind);
            break;
        default:
            break;
        }
        inputs.pop();

    }
    return 0;
}
```

Dans l’exemple précédent, le union dans le n' `Input` struct a pas de nom, il s’agit donc d’un *anonyme* union . Vous pouvez accéder directement à ses membres comme s’ils étaient membres du struct . Pour plus d’informations sur l’utilisation d’un anonyme union , consultez la section [anonyme union ](#anonymous_unions) .

L’exemple précédent montre un problème que vous pouvez également résoudre en utilisant class des types qui dérivent d’une base commune class . Vous pouvez créer une branche de votre code en fonction du type d’exécution de chaque objet dans le conteneur. Votre code peut être plus facile à gérer et à comprendre, mais il peut également être plus lent que d’utiliser un union . En outre, avec un union , vous pouvez stocker des types non liés. Un vous union permet de modifier dynamiquement le type de la valeur stockée sans modifier le type de la union variable elle-même. Par exemple, vous pouvez créer un tableau hétérogène de `MyUnionType` , dont les éléments stockent différentes valeurs de types différents.

Il est facile d’abuser du `Input` struct dans l’exemple. Il appartient à l’utilisateur d’utiliser le discriminateur correctement pour accéder au membre qui contient les données. Vous pouvez vous protéger contre une utilisation incorrecte en créant union **`private`** et en fournissant des fonctions d’accès spéciales, comme indiqué dans l’exemple suivant.

## <a name="unrestricted-no-locunion-c11"></a>Non restreint union (c++ 11)

Dans C++ 03 et les versions antérieures, un union peut contenir des static membres qui ne sont pas des données qui ont un class type, tant que le type n’a aucun utilisateur con struct ors, de en struct ORS ou d’assignation. En C++11, ces restrictions sont supprimées. Si vous incluez un tel membre dans votre union , le compilateur marque automatiquement toutes les fonctions membres spéciales qui ne sont pas fournies par l’utilisateur comme **`deleted`** . Si le union est un anonyme union à l’intérieur d’un ou d’un class struct , toutes les fonctions membres spéciales du class ou struct qui ne sont pas fournies par l’utilisateur sont marquées comme **`deleted`** . L’exemple suivant montre comment gérer ce cas. L’un des membres du union a un membre qui requiert ce traitement spécial :

```cpp
// for MyVariant
#include <crtdbg.h>
#include <new>
#include <utility>

// for sample objects and output
#include <string>
#include <vector>
#include <iostream>

using namespace std;

struct A
{
    A() = default;
    A(int i, const string& str) : num(i), name(str) {}

    int num;
    string name;
    //...
};

struct B
{
    B() = default;
    B(int i, const string& str) : num(i), name(str) {}

    int num;
    string name;
    vector<int> vec;
    // ...
};

enum class Kind { None, A, B, Integer };

#pragma warning (push)
#pragma warning(disable:4624)
class MyVariant
{
public:
    MyVariant()
        : kind_(Kind::None)
    {
    }

    MyVariant(Kind kind)
        : kind_(kind)
    {
        switch (kind_)
        {
        case Kind::None:
            break;
        case Kind::A:
            new (&a_) A();
            break;
        case Kind::B:
            new (&b_) B();
            break;
        case Kind::Integer:
            i_ = 0;
            break;
        default:
            _ASSERT(false);
            break;
        }
    }

    ~MyVariant()
    {
        switch (kind_)
        {
        case Kind::None:
            break;
        case Kind::A:
            a_.~A();
            break;
        case Kind::B:
            b_.~B();
            break;
        case Kind::Integer:
            break;
        default:
            _ASSERT(false);
            break;
        }
        kind_ = Kind::None;
    }

    MyVariant(const MyVariant& other)
        : kind_(other.kind_)
    {
        switch (kind_)
        {
        case Kind::None:
            break;
        case Kind::A:
            new (&a_) A(other.a_);
            break;
        case Kind::B:
            new (&b_) B(other.b_);
            break;
        case Kind::Integer:
            i_ = other.i_;
            break;
        default:
            _ASSERT(false);
            break;
        }
    }

    MyVariant(MyVariant&& other)
        : kind_(other.kind_)
    {
        switch (kind_)
        {
        case Kind::None:
            break;
        case Kind::A:
            new (&a_) A(move(other.a_));
            break;
        case Kind::B:
            new (&b_) B(move(other.b_));
            break;
        case Kind::Integer:
            i_ = other.i_;
            break;
        default:
            _ASSERT(false);
            break;
        }
        other.kind_ = Kind::None;
    }

    MyVariant& operator=(const MyVariant& other)
    {
        if (&other != this)
        {
            switch (other.kind_)
            {
            case Kind::None:
                this->~MyVariant();
                break;
            case Kind::A:
                *this = other.a_;
                break;
            case Kind::B:
                *this = other.b_;
                break;
            case Kind::Integer:
                *this = other.i_;
                break;
            default:
                _ASSERT(false);
                break;
            }
        }
        return *this;
    }

    MyVariant& operator=(MyVariant&& other)
    {
        _ASSERT(this != &other);
        switch (other.kind_)
        {
        case Kind::None:
            this->~MyVariant();
            break;
        case Kind::A:
            *this = move(other.a_);
            break;
        case Kind::B:
            *this = move(other.b_);
            break;
        case Kind::Integer:
            *this = other.i_;
            break;
        default:
            _ASSERT(false);
            break;
        }
        other.kind_ = Kind::None;
        return *this;
    }

    MyVariant(const A& a)
        : kind_(Kind::A), a_(a)
    {
    }

    MyVariant(A&& a)
        : kind_(Kind::A), a_(move(a))
    {
    }

    MyVariant& operator=(const A& a)
    {
        if (kind_ != Kind::A)
        {
            this->~MyVariant();
            new (this) MyVariant(a);
        }
        else
        {
            a_ = a;
        }
        return *this;
    }

    MyVariant& operator=(A&& a)
    {
        if (kind_ != Kind::A)
        {
            this->~MyVariant();
            new (this) MyVariant(move(a));
        }
        else
        {
            a_ = move(a);
        }
        return *this;
    }

    MyVariant(const B& b)
        : kind_(Kind::B), b_(b)
    {
    }

    MyVariant(B&& b)
        : kind_(Kind::B), b_(move(b))
    {
    }

    MyVariant& operator=(const B& b)
    {
        if (kind_ != Kind::B)
        {
            this->~MyVariant();
            new (this) MyVariant(b);
        }
        else
        {
            b_ = b;
        }
        return *this;
    }

    MyVariant& operator=(B&& b)
    {
        if (kind_ != Kind::B)
        {
            this->~MyVariant();
            new (this) MyVariant(move(b));
        }
        else
        {
            b_ = move(b);
        }
        return *this;
    }

    MyVariant(int i)
        : kind_(Kind::Integer), i_(i)
    {
    }

    MyVariant& operator=(int i)
    {
        if (kind_ != Kind::Integer)
        {
            this->~MyVariant();
            new (this) MyVariant(i);
        }
        else
        {
            i_ = i;
        }
        return *this;
    }

    Kind GetKind() const
    {
        return kind_;
    }

    A& GetA()
    {
        _ASSERT(kind_ == Kind::A);
        return a_;
    }

    const A& GetA() const
    {
        _ASSERT(kind_ == Kind::A);
        return a_;
    }

    B& GetB()
    {
        _ASSERT(kind_ == Kind::B);
        return b_;
    }

    const B& GetB() const
    {
        _ASSERT(kind_ == Kind::B);
        return b_;
    }

    int& GetInteger()
    {
        _ASSERT(kind_ == Kind::Integer);
        return i_;
    }

    const int& GetInteger() const
    {
        _ASSERT(kind_ == Kind::Integer);
        return i_;
    }

private:
    Kind kind_;
    union
    {
        A a_;
        B b_;
        int i_;
    };
};
#pragma warning (pop)

int main()
{
    A a(1, "Hello from A");
    B b(2, "Hello from B");

    MyVariant mv_1 = a;

    cout << "mv_1 = a: " << mv_1.GetA().name << endl;
    mv_1 = b;
    cout << "mv_1 = b: " << mv_1.GetB().name << endl;
    mv_1 = A(3, "hello again from A");
    cout << R"aaa(mv_1 = A(3, "hello again from A"): )aaa" << mv_1.GetA().name << endl;
    mv_1 = 42;
    cout << "mv_1 = 42: " << mv_1.GetInteger() << endl;

    b.vec = { 10,20,30,40,50 };

    mv_1 = move(b);
    cout << "After move, mv_1 = b: vec.size = " << mv_1.GetB().vec.size() << endl;

    cout << endl << "Press a letter" << endl;
    char c;
    cin >> c;
}
```

Un union ne peut pas stocker de référence. Un union ne prend pas non plus en charge l’héritage. Cela signifie que vous ne pouvez pas utiliser union comme base class , ni hériter d’un autre class , ou avoir des fonctions virtuelles.

## <a name="initialize-a-no-locunion"></a>Initialise un union

Vous pouvez déclarer et initialiser un union dans la même instruction en assignant une expression entre accolades. L’expression est évaluée et assignée au premier champ du union .

```cpp
#include <iostream>
using namespace std;

union NumericType
{
    short       iValue;
    long        lValue;
    double      dValue;
};

int main()
{
    union NumericType Values = { 10 };   // iValue = 10
    cout << Values.iValue << endl;
    Values.dValue = 3.1416;
    cout << Values.dValue << endl;
}
/* Output:
10
3.141600
*/
```

Le `NumericType` union est organisé en mémoire (conceptuellement) comme indiqué dans l’illustration suivante.

![Stockage des données dans un type numérique ::: No-Loc (Union) :::](../cpp/media/vc38ul1.png "Stockage des données dans un NumericType ::: No-Loc (Union) :::") <br/>
Stockage des données dans un `NumericType`union

## <a name="anonymous-no-locunion"></a><a name="anonymous_unions"></a> Façon union

Un anonyme union est un déclaré sans *`class-name`* ou *`declarator-list`* .

> **`union  {`**  *`member-list`*  **`}`**

Les noms déclarés dans un anonyme union sont utilisés directement, comme les variables non membres. Cela implique que les noms déclarés dans un anonyme union doivent être uniques dans la portée environnante.

Un anonyme union est soumis à ces restrictions supplémentaires :

- Si elle est déclarée dans la portée de fichier ou d’espace de noms, elle doit également être déclarée comme **`static`** .

- Elle ne peut avoir que des **`public`** membres ; having **`private`** et **`protected`** les membres d’un anonyme union génèrent des erreurs.

- Elle ne peut pas avoir de fonctions membres.

## <a name="see-also"></a>Voir aussi

[Classes et structs](../cpp/classes-and-structs-cpp.md)<br/>
[Mots clés](../cpp/keywords-cpp.md)<br/>
[`class`](../cpp/class-cpp.md)<br/>
[`struct`](../cpp/struct-cpp.md)
