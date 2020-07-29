---
title: Fichiers d’en-tête (C++)
ms.date: 12/11/2019
helpviewer_keywords:
- header files [C++]
ms.openlocfilehash: 0b76773b8b7d55645c807588fe41b242df9eea2f
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87227450"
---
# <a name="header-files-c"></a>Fichiers d’en-tête (C++)

Les noms des éléments de programme, tels que les variables, les fonctions, les classes, etc., doivent être déclarés avant de pouvoir être utilisés. Par exemple, vous ne pouvez pas simplement écrire `x = 42` sans déclarer au préalable’x'.

```cpp
int x; // declaration
x = 42; // use x
```

La déclaration indique au compilateur si l’élément est un **`int`** , un **`double`** , une **fonction**, **`class`** ou une autre chose.  En outre, chaque nom doit être déclaré (directement ou indirectement) dans chaque fichier. cpp dans lequel il est utilisé. Quand vous compilez un programme, chaque fichier. cpp est compilé indépendamment dans une unité de compilation. Le compilateur n’a aucune connaissance des noms déclarés dans d’autres unités de compilation. Cela signifie que si vous définissez une classe ou une fonction ou une variable globale, vous devez fournir une déclaration de cette chose dans chaque fichier. cpp supplémentaire qui l’utilise. Chaque déclaration de cet élément doit être exactement identique dans tous les fichiers. Une légère incohérence entraînera des erreurs, ou un comportement inattendu, lorsque l’éditeur de liens tente de fusionner toutes les unités de compilation dans un même programme.

Pour réduire le risque d’erreurs, C++ a adopté la Convention d’utilisation des *fichiers d’en-tête* pour contenir des déclarations. Vous effectuez les déclarations dans un fichier d’en-tête, puis utilisez la directive #include dans chaque fichier. cpp ou tout autre fichier d’en-tête qui requiert cette déclaration. La directive #include insère une copie du fichier d’en-tête directement dans le fichier. cpp avant la compilation.

> [!NOTE]
> Dans Visual Studio 2019, la fonctionnalité *modules* c++ 20 est introduite comme une amélioration et un remplacement éventuel pour les fichiers d’en-tête. Pour plus d’informations, consultez [vue d’ensemble des modules en C++](modules-cpp.md).

## <a name="example"></a>Exemple

L’exemple suivant montre une méthode courante pour déclarer une classe, puis l’utiliser dans un fichier source différent. Nous allons commencer par le fichier d’en-tête, `my_class.h` . Il contient une définition de classe, mais notez que la définition est incomplète ; la fonction membre `do_something` n’est pas définie :

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

Ensuite, créez un fichier d’implémentation (généralement avec une extension. cpp ou similaire). Nous appellerons le fichier my_class. cpp et fournissons une définition pour la déclaration de membre. Nous ajoutons une `#include` directive pour le fichier « my_class. h » afin que la déclaration my_class soit insérée à ce stade dans le fichier. cpp, et que nous incluions `<iostream>` pour extraire la déclaration pour `std::cout` . Notez que les guillemets sont utilisés pour les fichiers d’en-tête dans le même répertoire que le fichier source, tandis que les chevrons sont utilisés pour les en-têtes de bibliothèque standard. En outre, de nombreux en-têtes de bibliothèque standard n’ont pas de fichier. h ou toute autre extension de fichier.

Dans le fichier d’implémentation, nous pouvons éventuellement utiliser une **`using`** instruction pour éviter d’avoir à qualifier chaque mention de « my_class » ou « cout » avec « N :: » ou « std :: ».  Ne placez pas **`using`** les instructions dans vos fichiers d’en-tête !

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

Nous pouvons maintenant utiliser `my_class` dans un autre fichier. cpp. Nous #include le fichier d’en-tête afin que le compilateur extraie la déclaration. Tout le compilateur doit savoir que my_class est une classe qui a une fonction membre publique appelée `do_something()` .

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

Une fois que le compilateur a terminé de compiler chaque fichier. cpp en fichiers. obj, il passe les fichiers. obj à l’éditeur de liens. Lorsque l’éditeur de liens fusionne les fichiers objets, il trouve une seule définition pour my_class ; Il se trouve dans le fichier. obj produit pour my_class. cpp, et la génération est réussie.

## <a name="include-guards"></a>Inclure des gardes

En règle générale, les fichiers d’en-tête ont une *protection include* ou une `#pragma once` directive pour s’assurer qu’ils ne sont pas insérés plusieurs fois dans un seul fichier. cpp.

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

## <a name="what-to-put-in-a-header-file"></a>Éléments à placer dans un fichier d’en-tête

Comme un fichier d’en-tête peut potentiellement être inclus par plusieurs fichiers, il ne peut pas contenir de définitions qui peuvent produire plusieurs définitions du même nom. Les éléments suivants ne sont pas autorisés ou sont considérés comme une mauvaise pratique :

- définitions de type intégrées au niveau de l’espace de noms ou de la portée globale
- définitions de fonction non inline
- définitions de variables non const
- définitions d’agrégats
- espaces de noms sans nom
- Directives using

L’utilisation de la **`using`** directive ne provoquera pas nécessairement une erreur, mais peut entraîner un problème, car elle amène l’espace de noms dans la portée de chaque fichier. cpp qui comprend directement ou indirectement cet en-tête.

## <a name="sample-header-file"></a>Exemple de fichier d’en-tête

L’exemple suivant montre les différents types de déclarations et de définitions qui sont autorisés dans un fichier d’en-tête :

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
