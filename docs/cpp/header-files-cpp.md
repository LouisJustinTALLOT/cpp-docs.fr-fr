---
title: Fichiers d’en-tête (C++) | Microsoft Docs
ms.custom: ''
ms.date: 04/20/2018
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-language
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- header files [C++]
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 9f6950049d9bd9b9264383ab6e5e216023526880
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/01/2018
ms.locfileid: "39404763"
---
# <a name="header-files-c"></a>Fichiers d’en-tête (C++)

Les noms d’éléments de programme tels que des variables, fonctions, classes et ainsi de suite doivent être déclarés avant de pouvoir être utilisés. Par exemple, vous ne pouvez pas simplement écrire `x = 42` sans déclarer d’abord « x ». 

```cpp
int x; // declaration
x = 42; // use x
```

 La déclaration indique au compilateur qu’est un **int**, un **double**, un **fonction**, un **classe** ou certaines autres chose.  En outre, chaque nom doit être déclaré (directement ou indirectement) dans chaque fichier .cpp dans lequel elle est utilisée. Lorsque vous compilez un programme, chaque fichier .cpp est compilé en indépendamment dans une unité de compilation. Le compilateur connaît pas les noms sont déclarés dans d’autres unités de compilation. Cela signifie que si vous définissez une classe ou la fonction ou la variable globale, vous devez fournir une déclaration de ceci dans chaque fichier .cpp supplémentaires qui l’utilise. Chaque déclaration de ceci doit être exactement identique dans tous les fichiers. Une incohérence légère sera provoquer des erreurs, ou un comportement inattendu, lorsque l’éditeur de liens tente de fusionner toutes les unités de compilation dans un seul programme.

Pour réduire le risque d’erreurs, C++ a adopté la convention de l’utilisation de *fichiers d’en-tête* pour contenir les déclarations. Vous effectuez les déclarations dans un fichier d’en-tête, puis utiliser le #include, directive dans chaque fichier .cpp ou autre fichier d’en-tête nécessite cette déclaration. Le #include directive insère une copie du fichier d’en-tête directement dans le fichier .cpp avant la compilation. 

## <a name="example"></a>Exemple

L’exemple suivant montre une méthode courante pour déclarer une classe et l’utiliser dans un autre fichier source. Nous allons commencer par le fichier d’en-tête, `my_class.h`. Elle contient une définition de classe, mais notez que la définition est incomplète ; la fonction membre `do_something` n’est pas défini :

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

Ensuite, créez un fichier d’implémentation (généralement avec une .cpp ou une extension similaire). Nous appeler le fichier my_class.cpp et fournir une définition pour la déclaration de membre. Nous ajoutons un `#include` directive pour le fichier « my_class.h » afin de disposer de la déclaration de ma_classe insérée à ce stade dans le .cpp fichier et nous incluent `<iostream>` à extraire dans la déclaration pour `std::cout`. Notez que les guillemets doubles sont utilisés pour les fichiers d’en-tête dans le même répertoire que le fichier source, et ces crochets sont utilisés pour les en-têtes de bibliothèque standard. En outre, plusieurs en-têtes de bibliothèque standard n’ont pas .h ou une autre extension de fichier.

Dans le fichier d’implémentation, nous pouvons éventuellement utiliser un **à l’aide de** instruction afin d’éviter de devoir qualifier chaque mention du « ma_classe » ou « cout » avec « N: : » ou « std :: ».  Ne placez pas **à l’aide de** instructions dans vos fichiers d’en-tête !

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

Maintenant, nous pouvons utiliser `my_class` dans un autre fichier .cpp. Nous #include le fichier d’en-tête afin que le compilateur extrait dans la déclaration. Tous les besoins du compilateur savoir est que ma_classe est une classe qui a une fonction membre publique appelée `do_something()`.

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

Une fois que le compilateur a terminé la compilation de chaque fichier .cpp dans les fichiers .obj, il transmet les fichiers .obj à l’éditeur de liens. Lorsque l’éditeur de liens fusionne les fichiers objets qu’il trouve une seule définition pour my_class ; Il se trouve dans le fichier .obj produit pour my_class.cpp, et la génération réussit.

## <a name="include-guards"></a>Protections de type include

En règle générale, les fichiers d’en-tête ont un *#include guard* ou un `#pragma once` directive pour vous assurer qu’ils ne sont pas insérés plusieurs fois dans un fichier .cpp unique. 

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

## <a name="what-to-put-in-a-header-file"></a>Les éléments à ajouter dans un fichier d’en-tête

Un fichier d’en-tête peut potentiellement être inclus par plusieurs fichiers, il ne peut pas contenir les définitions qui peuvent produire plusieurs définitions du même nom. Les éléments suivants ne sont pas autorisées, ou sont considérées comme très mauvaise pratique :

- définitions de type intégré à l’espace de noms ou portée globale
- définitions de fonction non inline 
- définitions de variable non const
- définitions d’agrégation
- espaces de noms sans nom
- Directives using

Utilisation de la **à l’aide de** directive pas nécessairement provoque une erreur, mais peut entraîner un problème, car il place l’espace de noms dans la portée dans chaque fichier .cpp qui directement ou indirectement inclut cet en-tête. 

## <a name="sample-header-file"></a>Exemple de fichier en-tête

L’exemple suivant montre les différents types de déclarations et définitions qui sont autorisées dans un fichier d’en-tête :

```cpp
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