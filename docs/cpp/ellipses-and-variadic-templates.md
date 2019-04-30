---
title: Ellipses et modèles variadiques
ms.date: 11/04/2016
ms.assetid: f20967d9-c967-4fd2-b902-2bb1d5ed87e3
ms.openlocfilehash: 387cf4478192cb9470804c219eee8046f8e47abe
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62392217"
---
# <a name="ellipses-and-variadic-templates"></a>Ellipses et modèles variadiques

Cet article explique comment utiliser les points de suspension (`...`) avec les modèles variadic C++. L’ellipse a de nombreux usages dans C et C++. Ceux-ci incluent des listes d’arguments variables pour les fonctions. Le `printf()` fonction à partir de la bibliothèque Runtime C est un des exemples plus connus.

Un *modèle variadique* est un modèle de classe ou une fonction qui prend en charge un nombre arbitraire d’arguments. Ce mécanisme est particulièrement utile pour les développeurs de bibliothèques C++ car vous pouvez appliquer à des modèles de classe et des modèles de fonction et donc fournir un large éventail de fonctionnalités de type sécurisé et non triviales et de flexibilité.

## <a name="syntax"></a>Syntaxe

Points de suspension est utilisé de deux façons par les modèles variadiques. À gauche du nom de paramètre, cela signifie un *pack de paramètre*, et à droite du nom de paramètre, il développe les paquets de paramètre dans des noms différents.

Voici un exemple de base *classe de modèle variadique* syntaxe de définition :

```cpp
template<typename... Arguments> class classname;
```

Pour les packs de paramètres et les expansions, vous pouvez ajouter un espace blanc autour des points de suspension, selon votre préférence, comme indiqué dans ces exemples :

```cpp
template<typename ...Arguments> class classname;
```

Ou cela :

```cpp
template<typename ... Arguments> class classname;
```

Notez que cet article utilise la convention est indiquée dans le premier exemple (les points de suspension est attaché à `typename`).

Dans les exemples précédents, *Arguments* est un package de paramètres. La classe `classname` peut accepter un nombre variable d’arguments, comme dans les exemples :

```cpp
template<typename... Arguments> class vtclass;

vtclass< > vtinstance1;
vtclass<int> vtinstance2;
vtclass<float, bool> vtinstance3;
vtclass<long, std::vector<int>, std::string> vtinstance4;
```

En utilisant une définition de classe de modèle variadique, vous pouvez également exiger au moins un paramètre :

```cpp
template <typename First, typename... Rest> class classname;
```

Voici un exemple de base *fonction de modèle variadique* syntaxe :

```cpp
template <typename... Arguments> returntype functionname(Arguments... args);
```

Le *Arguments* pack de paramètre est ensuite étendue pour une utilisation, comme indiqué dans la section suivante, **présentation des modèles variadiques**.

Autres formes de syntaxe de fonction de modèle variadique sont possibles, y compris, mais sans limitation, ces exemples :

```cpp
template <typename... Arguments> returntype functionname(Arguments&... args);
template <typename... Arguments> returntype functionname(Arguments&&... args);
template <typename... Arguments> returntype functionname(Arguments*... args);
```

Spécificateurs tels que **const** sont également autorisées :

```cpp
template <typename... Arguments> returntype functionname(const Arguments&... args);
```

Comme avec les définitions de classe de modèle variadique, vous pouvez apporter des fonctions qui requièrent au moins un paramètre :

```cpp
template <typename First, typename... Rest> returntype functionname(const First& first, const Rest&... args);
```

Les modèles Variadiques utilisent la `sizeof...()` opérateur (non liés à l’ancien `sizeof()` opérateur) :

```cpp
template<typename... Arguments>
void tfunc(const Arguments&... args)
{
    constexpr auto numargs{ sizeof...(Arguments) };

    X xobj[numargs]; // array of some previously defined type X

    helper_func(xobj, args...);
}
```

## <a name="more-about-ellipsis-placement"></a>Plus d’informations sur le positionnement des points de suspension

Auparavant, cet article décrit le placement de points de suspension qui définit des packs de paramètres et des extensions en tant que « à gauche du nom de paramètre, il désigne un package de paramètres, et à droite du nom de paramètre, il développe les paquets de paramètre dans des noms ». Cela est techniquement true mais peut prêter à confusion dans la traduction au code. Prenez en compte ce qui suit :

- Dans une liste de paramètres de modèle (`template <parameter-list>`), `typename...` introduit un package de paramètres de modèle.

- Dans une clause de déclaration de paramètre (`func(parameter-list)`), un bouton de sélection de « niveau supérieur » présente un package de paramètres de fonction, et le positionnement des points de suspension est important :

    ```cpp
    // v1 is NOT a function parameter pack:
    template <typename... Types> void func1(std::vector<Types...> v1);

    // v2 IS a function parameter pack:
    template <typename... Types> void func2(std::vector<Types>... v2);
    ```

- Où les points de suspension s’affiche immédiatement après un nom de paramètre, vous avez une expansion de paramètre.

## <a name="example"></a>Exemple

Un bon moyen pour illustrer le mécanisme de fonction de modèle variadique consiste à utiliser dans une réécriture de certaines des fonctionnalités de `printf`:

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

## <a name="output"></a>Sortie

```Output
1
10, 20
100, 200, 300
first, 2, third, 3.14159
```

> [!NOTE]
>  La plupart des implémentations qui intègrent des fonctions de modèle variadique utilisent la récurrence sous une forme quelconque, mais il est légèrement différente de la récurrence classique.  La récurrence classique implique une fonction s’appelle lui-même à l’aide de la même signature. (Il peut être surchargée ou modélisée, mais la même signature est choisie à chaque fois.) La récursivité Variadique implique l’appel d’un modèle de fonction variadique en utilisant des nombres (presque toujours décroissants) d’arguments et ainsi en horodatant une signature différente chaque fois. Un « cas de base » est toujours requis, mais la nature de la récursivité est différente.