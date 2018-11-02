---
title: Espaces de noms (C++)
ms.date: 08/30/2017
f1_keywords:
- namespace_CPP
- using_CPP
helpviewer_keywords:
- namespaces [C++], C++
- namespaces [C++]
- namespaces [C++], global
- global namespace
- Visual C++, namespaces
ms.assetid: d1a5a9ab-1cad-47e6-a82d-385bb77f4188
ms.openlocfilehash: 532fdcb5de179bd2fdeb25091ace7210d55a2658
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50508847"
---
# <a name="namespaces-c"></a>Espaces de noms (C++)

Un espace de noms est une région déclarative qui fournit une portée aux identificateurs (noms de types, fonctions, variables, etc.) à l'intérieur. Les espaces de noms sont utilisés pour organiser le code en groupes logiques et pour éviter les conflits de noms qui peuvent se produire en particulier lorsque votre base de code inclut plusieurs bibliothèques. Tous les identificateurs de portée espace de noms sont visibles les uns pour les autres sans qualification. Les identificateurs en dehors de l’espace de noms peuvent accéder aux membres en utilisant le nom qualifié complet pour chaque identificateur, par exemple `std::vector<std::string> vec;`, ou par un [à l’aide de la déclaration](../cpp/using-declaration.md) pour un identificateur unique (`using std::string`), ou un [à l’aide de la Directive](../cpp/namespaces-cpp.md#using_directives) pour tous les identificateurs dans l’espace de noms (`using namespace std;`). Le code dans les fichiers d'en-tête doit toujours utiliser le nom de l'espace de noms qualifié complet.

L'exemple suivant montre une déclaration d'espace de noms et trois façons pour le code en dehors de l'espace de noms d'accéder à leurs membres.

```cpp
namespace ContosoData
{
    class ObjectManager
    {
    public:
        void DoSomething() {}
    };
    void Func(ObjectManager) {}
}
```

Utiliser le nom qualifié complet :

```cpp
ContosoData::ObjectManager mgr;
mgr.DoSomething();
ContosoData::Func(mgr);
```

Utiliser une déclaration using pour placer un identificateur dans la portée :

```cpp
using ContosoData::ObjectManager;
ObjectManager mgr;
mgr.DoSomething();
```

Utiliser une directive using pour placer tous les éléments de l'espace de noms dans la portée :

```cpp
using namespace ContosoData;

ObjectManager mgr;
mgr.DoSomething();
Func(mgr);
```

## <a id="using_directives"></a> directives using

Le **à l’aide de** directive permet à tous les noms dans un **espace de noms** à être utilisé sans le *nom de l’espace de noms* comme qualificateur explicite. Utilisez une directive dans un fichier d’implémentation (par exemple, *.cpp) si vous utilisez plusieurs identificateurs différents dans un espace de noms ; Si vous utilisez simplement un ou deux identificateurs, envisagez une déclaration pour placer uniquement ces identificateurs dans la portée et pas tous les identificateurs dans l’espace de noms. Si une variable locale a le même nom qu'une variable d'espace de noms, la variable d'espace de noms est masquée. Le fait qu'une variable d'espace de noms porte le même nom qu'une variable globale est une erreur.

> [!NOTE]
>  Une directive using peut être placée en haut d'un fichier .cpp (au niveau de la portée de fichier) ou à l'intérieur d'une définition de classe ou de fonction.
>
>  En règle générale, évitez de placer des directives using dans les fichiers d'en-tête (*.h), car n'importe quel fichier qui inclut cet en-tête placera tous les éléments de l'espace de noms dans la portée, ce qui peut provoquer des problèmes de masquage de noms et de conflits de noms très difficiles à déboguer. Utilisez toujours des noms qualifiés complets dans un fichier d'en-tête. Si ces noms sont trop longs, vous pouvez utiliser un alias d'espace de noms pour les raccourcir. (Voir ci-dessous.)

## <a name="declaring-namespaces-and-namespace-members"></a>Déclaration d'espaces de noms et de membres d'espaces de noms

En général, vous déclarez un espace de noms dans un fichier d'en-tête. Si les implémentations de vos fonctions se trouvent dans un fichier distinct, qualifiez les noms des fonctions, comme dans cet exemple.

```cpp
//contosoData.h
#pragma once
namespace ContosoDataServer
{
    void Foo();
    int Bar();
}
```

Les implémentations de fonctions dans contosodata.cpp doivent utiliser le nom qualifié complet, même si vous placez un **à l’aide de** directive en haut du fichier :

```cpp
#include "contosodata.h"
using namespace ContosoDataServer;

void ContosoDataServer::Foo() // use fully-qualified name here
{
   // no qualification needed for Bar()
   Bar();
}

int ContosoDataServer::Bar(){return 0;}
```

Un espace de noms peut être déclaré dans plusieurs blocs, dans un seul fichier et dans plusieurs fichiers. Le compilateur joint les parties pendant le prétraitement et l'espace de noms obtenu contient tous les membres déclarés dans toutes les parties. Un exemple de ceci est l'espace de noms std qui est déclaré dans chacun des fichiers d'en-tête de la bibliothèque standard.

Membres d’un espace de noms nommé peuvent être définis en dehors de l’espace de noms dans lequel ils sont déclarés par qualification explicite du nom qui est défini. Toutefois, la définition doit figurer après le point de déclaration dans un espace de noms qui englobe l'espace de noms de la déclaration. Exemple :

```cpp
// defining_namespace_members.cpp
// C2039 expected
namespace V {
        void f();
    }

    void V::f() { }        // ok
    void V::g() { }        // C2039, g() is not yet a member of V

    namespace V {
        void g();
    }
}
```

Cette erreur peut se produire quand les membres de l'espace de noms sont déclarés dans plusieurs fichiers d'en-tête et que vous n'avez pas inclus ces en-têtes dans le bon ordre.

## <a name="the-global-namespace"></a>Espace de noms global

Si un identificateur n'est pas déclaré dans un espace de noms explicite, il fait partie de l'espace de noms global implicite. En général, essayez d’éviter de faire des déclarations dans la portée globale, si possible, à l’exception du point d’entrée [fonction principale](../c-language/main-function-and-program-execution.md), qui doit se trouver dans l’espace de noms global. Pour qualifier explicitement un identificateur global, utilisez l’opérateur de résolution de portée sans nom, comme dans `::SomeFunction(x);`. Vous différenciez ainsi l'identificateur de tout élément portant le même nom dans un autre espace de noms et votre code devient également plus facile à comprendre.

## <a name="the-std-namespace"></a>Espace de noms std

Tous les types de bibliothèque standard C++ et les fonctions sont déclarées dans le `std` espace de noms imbriqué dans `std`.

## <a name="nested-namespaces"></a>Espaces de noms imbriqués

Les espaces de noms peuvent être imbriqués. Un espace de noms imbriqué ordinaire dispose d'un accès non qualifié aux membres de son parent, mais les membres parents n'ont pas d'accès non qualifié à l'espace de noms imbriqué (sauf s'il est déclaré comme inline), comme illustré dans l'exemple suivant :

```cpp
namespace ContosoDataServer
{
    void Foo();

    namespace Details
    {
        int CountImpl;
        void Ban() { return Foo(); }
    }

    int Bar(){...};
    int Baz(int i) { return Details::CountImpl; }
}
```

Les espaces de noms imbriqués ordinaires permettent d'encapsuler les détails d'implémentation interne qui ne font pas partie de l'interface publique de l'espace de noms parent.

## <a name="inline-namespaces-c-11"></a>Espaces de noms inline (C++11)

Contrairement à un espace de noms imbriqué ordinaire, les membres d'un espace de noms inline sont traités en tant que membres de l'espace de noms parent. Cette caractéristique permet à une recherche dépendante d'un argument sur les fonctions surchargées de fonctionner sur les fonctions qui ont des surcharges dans un parent et un espace de noms inline imbriqué. Elle vous permet également de déclarer une spécialisation dans un espace de noms parent pour un modèle qui est déclaré dans l'espace de noms inline. L'exemple suivant montre comment le code externe est lié à l'espace de noms inline par défaut :

```cpp
//Header.h
#include <string>

namespace Test
{
    namespace old_ns
    {
        std::string Func() { return std::string("Hello from old"); }
    }

    inline namespace new_ns
    {
        std::string Func() { return std::string("Hello from new"); }
    }
}

#include "header.h"
#include <string>
#include <iostream>

int main()
{
    using namespace Test;
    using namespace std;

    string s = Func();
    std::cout << s << std::endl; // "Hello from new"
    return 0;
}
```

L'exemple suivant vous montre comment déclarer une spécialisation dans un parent d'un modèle qui est déclaré dans un espace de noms inline :

```cpp
namespace Parent
{
    inline namespace new_ns
    {
         template <typename T>
         struct C
         {
             T member;
         };
    }
     template<>
     class C<int> {};
}
```

Vous pouvez utiliser des espaces de noms inline comme mécanisme de contrôle de version pour gérer les modifications apportées à l'interface publique d'une bibliothèque. Par exemple, vous pouvez créer un espace de noms parent unique et encapsuler chaque version de l'interface dans son propre espace de noms imbriqué dans le parent. L'espace de noms qui contient la version la plus récente ou préférée est qualifié comme étant inline et est par conséquent exposé comme s'il s'agissait d'un membre direct de l'espace de noms parent. Le code client qui appelle Parent::Class se liera automatiquement au nouveau code. Les clients qui préfèrent utiliser l'ancienne version peuvent toujours y accéder en utilisant le chemin d'accès qualifié complet à l'espace de noms imbriqué qui possède ce code.

Le mot clé inline doit être appliqué à la première déclaration de l'espace de noms dans une unité de compilation.

L'exemple suivant montre deux versions d'une interface, chacune dans un espace de noms imbriqué. L'espace de noms `v_20` a été modifié à partir de l'interface `v_10` et est marqué comme inline. Le code client qui utilise la nouvelle bibliothèque et appelle `Contoso::Funcs::Add` appelle la version v_20. Le code qui tente d'appeler `Contoso::Funcs::Divide` reçoit désormais une erreur de compilation. S'ils ont vraiment besoin de cette fonction, ils peuvent toujours accéder à la version `v_10` en appelant explicitement `Contoso::v_10::Funcs::Divide`.

```cpp
namespace Contoso
{
    namespace v_10
    {
        template <typename T>
        class Funcs
        {
        public:
            Funcs(void);
            T Add(T a, T b);
            T Subtract(T a, T b);
            T Multiply(T a, T b);
            T Divide(T a, T b);
        };
    }

    inline namespace v_20
    {
        template <typename T>
        class Funcs
        {
        public:
            Funcs(void);
            T Add(T a, T b);
            T Subtract(T a, T b);
            T Multiply(T a, T b);
            std::vector<double> Log(double);
            T Accumulate(std::vector<T> nums);
      };
    }
}
```

## <a id="namespace_aliases"></a> Alias de Namespace

Les noms des espaces de noms doivent être uniques, ce qui signifie qu'ils ne doivent pas être trop courts. Si la longueur d'un nom rend le code difficile à lire ou est fastidieux à taper dans un fichier d'en-tête où les directives using ne peuvent pas être utilisées, vous pouvez créer un alias d'espaces de noms qui sert d'abréviation pour le nom réel. Exemple :

```cpp
namespace a_very_long_namespace_name { class Foo {}; }
namespace AVLNN = a_very_long_namespace_name;
void Bar(AVLNN::Foo foo){ }
```

## <a name="anonymous-or-unnamed-namespaces"></a>espaces de noms anonymes ou sans nom

Vous pouvez créer un espace de noms explicite, mais sans lui donner de nom :

```cpp
namespace
{
    int MyFunc(){}
}
```

Il s’agit d’un espace de noms sans nom ou anonyme et il est utile lorsque vous souhaitez rendre les déclarations de variable invisible au code dans d’autres fichiers (autrement dit, leur donner une liaison interne) sans avoir à créer un espace de noms nommé. Tout le code du même fichier peut voir les identificateurs dans un espace de noms sans nom, mais les identificateurs, ainsi que l'espace de noms lui-même, ne sont pas visibles en dehors de ce fichier ou, plus précisément, à l'extérieur de l'unité de traduction.

## <a name="see-also"></a>Voir aussi

[Déclarations et définitions](declarations-and-definitions-cpp.md)