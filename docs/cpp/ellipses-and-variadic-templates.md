---
title: Ellipses et modèles variadiques
ms.date: 11/04/2016
ms.assetid: f20967d9-c967-4fd2-b902-2bb1d5ed87e3
ms.openlocfilehash: 358cdeeaf6f3e8c7f7841bbc796eca6557ccd145
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366339"
---
# <a name="ellipses-and-variadic-templates"></a>Ellipses et modèles variadiques

Cet article montre comment utiliser l’ellipsis ()`...`avec des modèles variadic C. L’ellipsis a eu de nombreuses utilisations en C et en C. Il s’agit notamment de listes d’arguments variables pour les fonctions. La `printf()` fonction de la bibliothèque C Runtime est l’un des exemples les plus connus.

Un *modèle variadique* est un modèle de classe ou de fonction qui prend en charge un nombre arbitraire d’arguments. Ce mécanisme est particulièrement utile pour les développeurs de bibliothèques CMD, car vous pouvez l’appliquer à la fois aux modèles de classe et aux modèles de fonction, et ainsi fournir un large éventail de fonctionnalités et de flexibilités sans danger et non négligeables.

## <a name="syntax"></a>Syntaxe

Une ellipsis est utilisée de deux façons par des modèles variadic. À gauche du nom de paramètre, il signifie un pack de *paramètres*, et à droite du nom du paramètre, il étend les paquets de paramètres en noms séparés.

Voici un exemple de base de syntaxe de définition de *classe de modèle variadic* :

```cpp
template<typename... Arguments> class classname;
```

Pour les packs de paramètres et les extensions, vous pouvez ajouter l’espace blanc autour de l’ellipsis, en fonction de votre préférence, comme indiqué dans ces exemples:

```cpp
template<typename ...Arguments> class classname;
```

Ou cela :

```cpp
template<typename ... Arguments> class classname;
```

Notez que cet article utilise la convention qui est montrée dans `typename`le premier exemple (l’ellipsis est attaché à ).

Dans les exemples précédents, *Arguments* est un pack de paramètres. La `classname` classe peut accepter un nombre variable d’arguments, comme dans ces exemples :

```cpp
template<typename... Arguments> class vtclass;

vtclass< > vtinstance1;
vtclass<int> vtinstance2;
vtclass<float, bool> vtinstance3;
vtclass<long, std::vector<int>, std::string> vtinstance4;
```

En utilisant une définition de classe de modèle variadic, vous pouvez également exiger au moins un paramètre :

```cpp
template <typename First, typename... Rest> class classname;
```

Voici un exemple de base de syntaxe *de fonction de modèle variadic* :

```cpp
template <typename... Arguments> returntype functionname(Arguments... args);
```

Le pack de paramètres *Arguments* est ensuite élargi pour une utilisation, comme indiqué dans la section suivante, **Comprendre les modèles variadic**.

D’autres formes de syntaxe de fonction de modèle variadic sont possibles, y compris, mais sans s’y limiter, ces exemples :

```cpp
template <typename... Arguments> returntype functionname(Arguments&... args);
template <typename... Arguments> returntype functionname(Arguments&&... args);
template <typename... Arguments> returntype functionname(Arguments*... args);
```

Les spéculateurs comme **le cône** sont également autorisés :

```cpp
template <typename... Arguments> returntype functionname(const Arguments&... args);
```

Comme avec les définitions de classe de modèle variadic, vous pouvez faire des fonctions qui nécessitent au moins un paramètre :

```cpp
template <typename First, typename... Rest> returntype functionname(const First& first, const Rest&... args);
```

Les modèles variadic `sizeof...()` utilisent l’opérateur `sizeof()` (sans rapport avec l’ancien opérateur) :

```cpp
template<typename... Arguments>
void tfunc(const Arguments&... args)
{
    constexpr auto numargs{ sizeof...(Arguments) };

    X xobj[numargs]; // array of some previously defined type X

    helper_func(xobj, args...);
}
```

## <a name="more-about-ellipsis-placement"></a>En savoir plus sur le placement d’ellipsis

Auparavant, cet article décrivait le placement d’ellipsis qui définit les packs de paramètres et les extensions comme « à gauche du nom du paramètre, il signifie un pack de paramètres, et à droite du nom du paramètre, il étend les paquets de paramètres en noms distincts ». C’est techniquement vrai, mais peut être déroutant dans la traduction au code. Vous devez :

- Dans un modèle-paramètre-liste (`template <parameter-list>`), `typename...` introduit un pack de paramètres de modèle.

- Dans une clause de`func(parameter-list)`déclaration de paramètres (), une ellipsis « de haut niveau » introduit un pack de paramètres de fonction, et le positionnement d’ellipsis est important :

    ```cpp
    // v1 is NOT a function parameter pack:
    template <typename... Types> void func1(std::vector<Types...> v1);

    // v2 IS a function parameter pack:
    template <typename... Types> void func2(std::vector<Types>... v2);
    ```

- Lorsque l’ellipsis apparaît immédiatement après un nom de paramètre, vous avez une extension de pack de paramètres.

## <a name="example"></a>Exemple

Une bonne façon d’illustrer le mécanisme de fonction de modèle variadic est `printf`de l’utiliser dans une réécritre de certaines fonctionnalités de :

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
> La plupart des implémentations qui intègrent des fonctions de modèle variadic utilisent la récursion d’une certaine forme, mais il est légèrement différent de la récursion traditionnelle.  La récursion traditionnelle implique une fonction qui s’appelle en utilisant la même signature. (Il peut être surchargé ou modélisé, mais la même signature est choisie à chaque fois.) La récursion variadique consiste à appeler un modèle de fonction variadic en utilisant différents (presque toujours en baisse) nombre d’arguments, et ainsi éradiquer une signature différente à chaque fois. Un « cas de base » est toujours nécessaire, mais la nature de la récursion est différente.
