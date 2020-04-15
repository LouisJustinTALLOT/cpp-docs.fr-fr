---
title: Fichiers d’en-tête (C)
ms.date: 12/11/2019
helpviewer_keywords:
- header files [C++]
ms.openlocfilehash: 4ab6a2b2626cde94f35678bc9ec789b80d493b8f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367232"
---
# <a name="header-files-c"></a>Fichiers d’en-tête (C)

Les noms des éléments du programme tels que les variables, les fonctions, les classes, et ainsi de suite doivent être déclarés avant qu’ils puissent être utilisés. Par exemple, vous ne `x = 42` pouvez pas simplement écrire sans d’abord déclarer «x».

```cpp
int x; // declaration
x = 42; // use x
```

La déclaration indique au compilateur si l’élément est un **int**, un **double**, une **fonction**, une **classe** ou une autre chose.  En outre, chaque nom doit être déclaré (directement ou indirectement) dans chaque fichier .cpp dans lequel il est utilisé. Lorsque vous compilez un programme, chaque fichier .cpp est compilé indépendamment dans une unité de compilation. Le compilateur n’a aucune connaissance de ce que les noms sont déclarés dans d’autres unités de compilation. Cela signifie que si vous définissez une classe ou une fonction ou une variable globale, vous devez fournir une déclaration de cette chose dans chaque fichier .cpp supplémentaire qui l’utilise. Chaque déclaration de cette chose doit être exactement identique dans tous les fichiers. Une légère incohérence entraînera des erreurs, ou un comportement involontaire, lorsque le linker tente de fusionner toutes les unités de compilation en un seul programme.

Afin de minimiser les risques d’erreurs, le C a adopté la convention d’utilisation des *fichiers d’en-tête* pour contenir les déclarations. Vous faites les déclarations dans un fichier d’en-tête, puis utilisez la directive #include dans chaque fichier .cpp ou tout autre fichier d’en-tête qui exige cette déclaration. La directive #include insère une copie du fichier d’en-tête directement dans le fichier .cpp avant la compilation.

> [!NOTE]
> Dans Visual Studio 2019, la fonction *modules* C-20 est introduite comme une amélioration et un remplacement éventuel des fichiers d’en-tête. Pour plus d’informations, voir [Aperçu des modules dans C .](modules-cpp.md)

## <a name="example"></a>Exemple

L’exemple suivant montre une façon courante de déclarer une classe et de l’utiliser dans un fichier source différent. Nous allons commencer avec le `my_class.h`fichier d’en-tête, . Il contient une définition de classe, mais notez que la définition est incomplète; la fonction `do_something` membre n’est pas définie :

```cpp
// my_class.h
namespace N
{
    class my_class
    {
    public:
        void do_something();
    };

}
```

Ensuite, créez un fichier de mise en œuvre (généralement avec un .cpp ou une extension similaire). Nous appellerons le dossier my_class.cpp et fournirons une définition de la déclaration du membre. Nous ajoutons une `#include` directive pour le fichier "my_class.h" afin que la déclaration my_class insérée à ce stade `<iostream>` du fichier .cpp, et nous incluons de retirer la déclaration pour `std::cout`. Notez que les devis sont utilisés pour les fichiers d’en-tête dans le même répertoire que le fichier source, et les supports d’angle sont utilisés pour les en-têtes de bibliothèque standard. En outre, de nombreux en-têtes de bibliothèque standard n’ont pas .h ou toute autre extension de fichier.

Dans le fichier de mise en œuvre, nous pouvons utiliser optionnellement une instruction **d’utilisation** pour éviter d’avoir à qualifier chaque mention de "my_class" ou "cout" avec "N::" ou "std::".  Ne mettez pas **en utilisant des** instructions dans vos fichiers d’en-tête!

```cpp
// my_class.cpp
#include "my_class.h" // header in local directory
#include <iostream> // header in standard library

using namespace N;
using namespace std;

void my_class::do_something()
{
    cout << "Doing something!" << endl;
}
```

Maintenant, nous `my_class` pouvons utiliser dans un autre fichier .cpp. Nous #include le fichier d’en-tête de sorte que le compilateur tire dans la déclaration. Tout ce que le compilateur doit savoir, c’est que my_class `do_something()`est une classe qui a une fonction de membre public appelé .

```cpp
// my_program.cpp
#include "my_class.h"

using namespace N;

int main()
{
    my_class mc;
    mc.do_something();
    return 0;
}
```

Une fois que le compilateur termine la compilation de chaque fichier .cpp dans des fichiers .obj, il passe les fichiers .obj au linker. Lorsque le lien fusionne les fichiers d’objets, il trouve exactement une définition pour my_class; il est dans le fichier .obj produit pour my_class.cpp, et la construction réussit.

## <a name="include-guards"></a>Inclure les gardes

En règle générale, les fichiers `#pragma once` d’en-tête ont un garde *inclus* ou une directive pour s’assurer qu’ils ne sont pas insérés plusieurs fois dans un seul fichier .cpp.

```cpp
// my_class.h
#ifndef MY_CLASS_H // include guard
#define MY_CLASS_H

namespace N
{
    class my_class
    {
    public:
        void do_something();
    };
}

#endif /* MY_CLASS_H */
```

## <a name="what-to-put-in-a-header-file"></a>Ce qu’il faut mettre dans un fichier d’en-tête

Étant donné qu’un fichier d’en-tête peut potentiellement être inclus par plusieurs fichiers, il ne peut pas contenir de définitions qui pourraient produire plusieurs définitions du même nom. Les éléments suivants ne sont pas autorisés, ou sont considérés comme de très mauvaises pratiques:

- définitions de type intégrées à l’espace de nom ou à portée globale
- définitions de fonctions non en ligne
- définitions variables non-const
- définitions agrégées
- espaces de noms sans nom
- Directives using

L’utilisation de la directive **d’utilisation** ne causera pas nécessairement une erreur, mais peut potentiellement causer un problème parce qu’elle met l’espace de nom dans la portée dans chaque fichier .cpp qui inclut directement ou indirectement cet en-tête.

## <a name="sample-header-file"></a>Fichier d’en-tête d’échantillon

L’exemple suivant montre les différents types de déclarations et de définitions qui sont autorisées dans un fichier d’en-tête :

```cpp
// sample.h
#pragma once
#include <vector> // #include directive
#include <string>

namespace N  // namespace declaration
{
    inline namespace P
    {
        //...
    }

    enum class colors : short { red, blue, purple, azure };

    const double PI = 3.14;  // const and constexpr definitions
    constexpr int MeaningOfLife{ 42 };
    constexpr int get_meaning()
    {
        static_assert(MeaningOfLife == 42, "unexpected!"); // static_assert
        return MeaningOfLife;
    }
    using vstr = std::vector<int>;  // type alias
    extern double d; // extern variable

#define LOG   // macro definition

#ifdef LOG   // conditional compilation directive
    void print_to_log();
#endif

    class my_class   // regular class definition,
    {                // but no non-inline function definitions

        friend class other_class;
    public:
        void do_something();   // definition in my_class.cpp
        inline void put_value(int i) { vals.push_back(i); } // inline OK

    private:
        vstr vals;
        int i;
    };

    struct RGB
    {
        short r{ 0 };  // member initialization
        short g{ 0 };
        short b{ 0 };
    };

    template <typename T>  // template definition
    class value_store
    {
    public:
        value_store<T>() = default;
        void write_value(T val)
        {
            //... function definition OK in template
        }
    private:
        std::vector<T> vals;
    };

    template <typename T>  // template declaration
    class value_widget;
}
```
