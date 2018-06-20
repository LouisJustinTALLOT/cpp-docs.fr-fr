---
title: Fichiers d’en-tête (C++) | Documents Microsoft
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
ms.openlocfilehash: b571cd2836e66ebef21898af27cf2a6d7082e0e5
ms.sourcegitcommit: d06966efce25c0e66286c8047726ffe743ea6be0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36261051"
---
# <a name="header-files-c"></a>Fichiers d’en-tête (C++)

Les noms d’éléments de programme tels que des variables, des fonctions, des classes et ainsi de suite doivent être déclarés avant de pouvoir être utilisés. Par exemple, vous ne pouvez pas écrivent simplement `x = 42` sans déclarer d’abord « x ». 

```cpp
int x; // declaration
x = 42; // use x
```

 La déclaration indique au compilateur qu’est un **int**, un **double**, un **fonction**, un **classe** ou une autre chose.  En outre, chaque nom doit être déclaré (directement ou indirectement) de chaque fichier .cpp dans lequel elle est utilisée. Lorsque vous compilez un programme, chaque fichier .cpp est compilé séparément dans une unité de compilation. Le compilateur connaît pas les noms sont déclarés dans d’autres unités de compilation. Cela signifie que si vous définissez une classe, une fonction ou une variable globale, vous devez fournir une déclaration de cette opération dans chaque fichier .cpp supplémentaires qui l’utilise. Chaque déclaration de cet élément doit être exactement identique dans tous les fichiers. Une incohérence légère sera provoquer des erreurs, ou un comportement inattendu, lors de l’éditeur de liens tente de fusionner toutes les unités de compilation d’un programme unique.

Pour réduire le risque d’erreurs, C++ a adopté la convention de l’utilisation de *fichiers d’en-tête* pour contenir les déclarations. Vous rendre les déclarations dans un fichier d’en-tête, puis utilisez le #include (directive) dans chaque fichier .cpp ou autre fichier d’en-tête requiert cette déclaration. Le #include directive insère une copie du fichier d’en-tête directement dans le fichier .cpp avant la compilation. 

## <a name="example"></a>Exemple

L’exemple suivant montre une manière courante de déclarer une classe et l’utiliser dans un fichier source différent. Nous allons commencer par le fichier d’en-tête **my_class.h**. Il contient une définition de classe, mais notez que la définition est incomplet. la fonction membre `do_something` n’est pas défini :

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

Ensuite, créez un fichier d’implémentation (généralement avec un .cpp ou une extension similaire). Nous appeler le my_class.cpp de fichier et fournir une définition de la déclaration de membre. Nous ajoutons une `#include` directive pour le fichier « my_class.h » pour que la déclaration ma_classe insérée à ce stade dans .cpp fichier et nous incluent  **\<iostream >** à extraire dans la déclaration de `std::cout`. Notez que les guillemets sont utilisés pour les fichiers d’en-tête dans le même répertoire que le fichier source, et les crochets pointus sont utilisés pour les en-têtes de bibliothèque standard. En outre, plusieurs en-têtes de bibliothèque standard n’aient pas .h ou une autre extension de fichier.

Dans le fichier d’implémentation, nous pouvons éventuellement utiliser un **à l’aide de** instruction pour éviter d’avoir à qualifier chaque mention du « ma_classe » ou « cout » avec « N: : » ou « std :: ».  Ne placez pas **à l’aide de** instructions dans vos fichiers d’en-tête !

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

Nous pouvons maintenant utiliser `my_class` dans un autre fichier .cpp. Nous #include le fichier d’en-tête afin que le compilateur extrait dans la déclaration. Tous les besoins du compilateur savoir est que ma_classe est une classe qui a une fonction membre publique appelée `do_something()`.

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

Une fois que le compilateur a terminé la compilation de chaque fichier .cpp dans les fichiers .obj, il transmet les fichiers .obj à l’éditeur de liens. Lorsque l’éditeur de liens fusionne les fichiers de l’objet qu’il trouve une seule définition pour my_class ; Il est dans le fichier .obj produit pour my_class.cpp, et la génération terminée.

## <a name="include-guards"></a>Inclure les gardes

En règle générale, les fichiers d’en-tête ont un *#include guard* ou un **#pragma une fois** la directive pour vous assurer qu’ils ne sont pas insérées de plusieurs fois dans un fichier .cpp unique. 

my_class.h
#<a name="ifndef-myclassh--include-guard"></a>ifndef MY_CLASS_H / / #include guard
#<a name="define-myclassh"></a>définir MY_CLASS_H


espace de noms N {classe ma_classe {public : void do_something() ;} ;

}

#<a name="endif--myclassh-"></a>endif / * MY_CLASS_H * /

## <a name="what-to-put-in-a-header-file"></a>Les éléments à placer dans un fichier d’en-tête

Un fichier d’en-tête peut potentiellement être inclus par plusieurs fichiers, il ne peut pas contenir de définitions qui peuvent produire plusieurs définitions du même nom. Les éléments suivants ne sont pas autorisées ou sont considérés comme très mauvaise pratique :

- définitions de type intégré à l’espace de noms ou de la portée globale
- définitions de fonction non inline 
- définitions de variables non const
- définitions d’agrégation
- espaces de noms sans nom
- Directives using

Utilisation de la **à l’aide de** directive ne provoquera pas nécessairement une erreur, mais peut provoquer un problème, car il place l’espace de noms dans la portée de chaque fichier .cpp qui directement ou indirectement inclut cet en-tête. 

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
