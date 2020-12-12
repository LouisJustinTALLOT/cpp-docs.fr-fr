---
description: 'En savoir plus sur : les points de suspension et les modèles variadiques'
title: Points de suspension et modèles variadiques
ms.date: 11/04/2016
ms.assetid: f20967d9-c967-4fd2-b902-2bb1d5ed87e3
ms.openlocfilehash: 37cb2e02f818cc5d4db8954a348fc749a477b7d4
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97195462"
---
# <a name="ellipsis-and-variadic-templates"></a>Points de suspension et modèles variadiques

Cet article explique comment utiliser les points de suspension ( `...` ) avec des modèles variadiques C++. Les points de suspension ont eu de nombreuses utilisations en C et C++. Celles-ci incluent les listes d’arguments de variable pour les fonctions. La `printf()` fonction de la bibliothèque Runtime C est l’un des exemples les plus connus.

Un *modèle variadiques* est une classe ou un modèle de fonction qui prend en charge un nombre arbitraire d’arguments. Ce mécanisme est particulièrement utile pour les développeurs de bibliothèques C++, car vous pouvez l’appliquer aux modèles de classe et aux modèles de fonction, et fournir ainsi un large éventail de fonctionnalités et de flexibilité de type sécurisé et non trivial.

## <a name="syntax"></a>Syntaxe

Les points de suspension sont utilisés de deux façons par les modèles variadiques. À gauche du nom du paramètre, il s’agit d’un *Pack de paramètres*, et à droite du nom du paramètre, il étend les paquets de paramètres dans des noms distincts.

Voici un exemple de base de la syntaxe de définition de *classe de modèle variadiques* :

```cpp
template<typename... Arguments> class classname;
```

Pour les packs de paramètres et les expansions, vous pouvez ajouter des espaces autour des points de suspension, en fonction de vos préférences, comme indiqué dans les exemples suivants :

```cpp
template<typename ...Arguments> class classname;
```

Ou cela :

```cpp
template<typename ... Arguments> class classname;
```

Notez que cet article utilise la Convention indiquée dans le premier exemple (les points de suspension sont attachés à **`typename`** ).

Dans les exemples précédents, *arguments* est un package de paramètres. La classe `classname` peut accepter un nombre variable d’arguments, comme dans les exemples suivants :

```cpp
template<typename... Arguments> class vtclass;

vtclass< > vtinstance1;
vtclass<int> vtinstance2;
vtclass<float, bool> vtinstance3;
vtclass<long, std::vector<int>, std::string> vtinstance4;
```

En utilisant une définition de classe de modèle variadiques, vous pouvez également avoir besoin d’au moins un paramètre :

```cpp
template <typename First, typename... Rest> class classname;
```

Voici un exemple de base de la syntaxe de la *fonction de modèle variadiques* :

```cpp
template <typename... Arguments> returntype functionname(Arguments... args);
```

Le Pack de paramètres d' *arguments* est ensuite développé pour être utilisé, comme indiqué dans la section suivante, **Understanding variadiques templates**.

D’autres formes de syntaxe de la fonction de modèle variadiques sont possibles, y compris, mais sans s’y limiter, les exemples suivants :

```cpp
template <typename... Arguments> returntype functionname(Arguments&... args);
template <typename... Arguments> returntype functionname(Arguments&&... args);
template <typename... Arguments> returntype functionname(Arguments*... args);
```

Les spécificateurs comme **`const`** sont également autorisés :

```cpp
template <typename... Arguments> returntype functionname(const Arguments&... args);
```

Comme avec les définitions de classe de modèle variadiques, vous pouvez créer des fonctions qui nécessitent au moins un paramètre :

```cpp
template <typename First, typename... Rest> returntype functionname(const First& first, const Rest&... args);
```

Les modèles variadiques utilisent l' `sizeof...()` opérateur (sans lien avec l’ancien `sizeof()` opérateur) :

```cpp
template<typename... Arguments>
void tfunc(const Arguments&... args)
{
    constexpr auto numargs{ sizeof...(Arguments) };

    X xobj[numargs]; // array of some previously defined type X

    helper_func(xobj, args...);
}
```

## <a name="more-about-ellipsis-placement"></a>En savoir plus sur l’emplacement des points de suspension

Précédemment, cet article a décrit les points de suspension qui définissent les jeux de paramètres et les expansions comme suit : « à gauche du nom du paramètre, il s’agit d’un pack de paramètres, et à droite du nom du paramètre, il étend les packs de paramètres dans des noms distincts ». Cela est techniquement vrai, mais peut prêter à confusion dans le code. Considérez les aspects suivants :

- Dans un modèle-parameter-list ( `template <parameter-list>` ), `typename...` introduit un package de paramètres de modèle.

- Dans une clause Parameter-declaration ( `func(parameter-list)` ), les points de suspension « de niveau supérieur » introduisent un pack de paramètres de fonction et la position des points de suspension est importante :

    ```cpp
    // v1 is NOT a function parameter pack:
    template <typename... Types> void func1(std::vector<Types...> v1);

    // v2 IS a function parameter pack:
    template <typename... Types> void func2(std::vector<Types>... v2);
    ```

- Lorsque les points de suspension apparaissent immédiatement après un nom de paramètre, vous avez une expansion de package de paramètres.

## <a name="example"></a>Exemple

Un bon moyen d’illustrer le mécanisme de la fonction de modèle variadiques consiste à l’utiliser dans une nouvelle écriture de certaines fonctionnalités de `printf` :

```cpp
#include <iostream>

using namespace std;

void print() {
    cout << endl;
}

template <typename T> void print(const T& t) {
    cout << t << endl;
}

template <typename First, typename... Rest> void print(const First& first, const Rest&... rest) {
    cout << first << ", ";
    print(rest...); // recursive call using pack expansion syntax
}

int main()
{
    print(); // calls first overload, outputting only a newline
    print(1); // calls second overload

    // these call the third overload, the variadic template,
    // which uses recursion as needed.
    print(10, 20);
    print(100, 200, 300);
    print("first", 2, "third", 3.14159);
}
```

## <a name="output"></a>Output

```Output
1
10, 20
100, 200, 300
first, 2, third, 3.14159
```

> [!NOTE]
> La plupart des implémentations qui intègrent des fonctions de modèle variadiques utilisent la récursivité d’une certaine forme, mais elle est légèrement différente de la récursivité traditionnelle.  La récursivité traditionnelle implique une fonction qui s’appelle elle-même à l’aide de la même signature. (Elle peut être surchargée ou basée sur un modèle, mais la même signature est choisie à chaque fois.) La récursivité variadiques implique l’appel d’un modèle de fonction variadiques à l’aide de nombres d’arguments différents (presque toujours décroissants) et, par conséquent, le marquage d’une signature différente à chaque fois. Un « cas de base » est toujours requis, mais la nature de la récursivité est différente.
