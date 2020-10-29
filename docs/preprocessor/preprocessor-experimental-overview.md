---
title: Vue d’ensemble du nouveau préprocesseur MSVC
description: Le préprocesseur MSVC est mis à jour pour être conforme aux normes C/C++.
ms.date: 09/10/2020
helpviewer_keywords:
- preprocessor, experimental
- preprocessor, new
ms.openlocfilehash: 5327a8148f78a07e222fae7fb92e6ed741d12011
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/29/2020
ms.locfileid: "92924585"
---
# <a name="msvc-new-preprocessor-overview"></a>Vue d’ensemble du nouveau préprocesseur MSVC

::: moniker range="msvc-140"

Visual Studio 2015 utilise le préprocesseur traditionnel, qui n’est pas conforme à la norme C++ ou C99. À compter de Visual Studio 2019 version 16,5, la prise en charge du nouveau préprocesseur pour la norme C++ 20 est terminée par la fonctionnalité. Ces modifications sont disponibles à l’aide du commutateur du compilateur [/Zc : preprocesseur](../build/reference/zc-preprocessor.md) . Une version expérimentale du nouveau préprocesseur est disponible à partir de Visual Studio 2017 version 15,8 et versions ultérieures à l’aide du commutateur de compilateur de [préprocesseur/experimental :](../build/reference/experimental-preprocessor.md) . Vous trouverez plus d’informations sur l’utilisation du nouveau préprocesseur dans Visual Studio 2017 et Visual Studio 2019. Pour consulter la documentation de votre version par défaut de Visual Studio, utilisez le contrôle sélecteur de **version** . Elle se trouve en haut de la table des matières sur cette page.

::: moniker-end

::: moniker range=">=msvc-150"

Nous mettons à jour le préprocesseur Microsoft C++ pour améliorer la conformité aux normes, résoudre les bogues de longue date et modifier certains comportements qui sont officiellement non définis. Nous avons également ajouté de nouveaux diagnostics pour signaler les erreurs dans les définitions de macros.

À compter de Visual Studio 2019 version 16,5, la prise en charge du préprocesseur pour la norme C++ 20 est terminée par la fonctionnalité. Ces modifications sont disponibles à l’aide du commutateur du compilateur [/Zc : preprocesseur](../build/reference/zc-preprocessor.md) . Une version expérimentale du nouveau préprocesseur est disponible dans les versions antérieures à compter de Visual Studio 2017 version 15,8. Vous pouvez l’activer à l’aide du commutateur de compilateur de [préprocesseur/experimental :](../build/reference/experimental-preprocessor.md) . Le comportement de préprocesseur par défaut reste le même que dans les versions précédentes.

## <a name="new-predefined-macro"></a>Nouvelle macro prédéfinie

Vous pouvez détecter le préprocesseur en cours d’utilisation au moment de la compilation. Vérifiez la valeur de la macro prédéfinie [`_MSVC_TRADITIONAL`](predefined-macros.md) pour déterminer si le préprocesseur traditionnel est en cours d’utilisation. Cette macro est définie de manière inconditionnelle par les versions du compilateur qui la prennent en charge, quel que soit le préprocesseur appelé. Sa valeur est 1 pour le préprocesseur traditionnel. Elle est égale à 0 pour le préprocesseur conforme.

```cpp
#if defined(_MSVC_TRADITIONAL) && _MSVC_TRADITIONAL
// Logic using the traditional preprocessor
#else
// Logic using cross-platform compatible preprocessor
#endif
```

## <a name="behavior-changes-in-the-new-preprocessor"></a>Changements de comportement dans le nouveau préprocesseur

Le travail initial sur le nouveau préprocesseur a été concentré sur le fait que toutes les expansions de macros soient conformes à la norme. Elle vous permet d’utiliser le compilateur MSVC avec des bibliothèques actuellement bloquées par les comportements traditionnels. Nous avons testé le préprocesseur mis à jour sur les projets réels. Voici quelques-unes des modifications les plus courantes que nous avons trouvées :

### <a name="macro-comments"></a>Commentaires sur les macros

Le préprocesseur traditionnel est basé sur des mémoires tampons de caractères plutôt que sur des jetons de préprocesseur. Il autorise un comportement inhabituel, tel que l’astuce de commentaire de préprocesseur suivante, qui ne fonctionne pas dans le préprocesseur conforme :

```cpp
#if DISAPPEAR
#define DISAPPEARING_TYPE /##/
#else
#define DISAPPEARING_TYPE int
#endif

// myVal disappears when DISAPPEARING_TYPE is turned into a comment
DISAPPEARING_TYPE myVal;
```

Le correctif conforme aux normes consiste à déclarer à l' `int myVal` intérieur des `#ifdef/#endif` directives appropriées :

```cpp
#define MYVAL 1

#ifdef MYVAL
int myVal;
#endif
```

### <a name="lval"></a>L # Val

Le préprocesseur traditionnel associe de manière incorrecte un préfixe de chaîne au résultat de l’opérateur de [chaîne (#)](stringizing-operator-hash.md) :

```cpp
 #define DEBUG_INFO(val) L"debug prefix:" L#val
//                                       ^
//                                       this prefix

const wchar_t *info = DEBUG_INFO(hello world);
```

Dans ce cas, le `L` préfixe n’est pas nécessaire, car les littéraux de chaîne adjacents sont combinés après l’expansion macro. Le correctif à compatibilité descendante consiste à modifier la définition :

```cpp
#define DEBUG_INFO(val) L"debug prefix:" #val
//                                       ^
//                                       no prefix
```

Le même problème se trouve également dans les macros pratiques qui « chaînent » l’argument à un littéral de chaîne étendu :

```cpp
 // The traditional preprocessor creates a single wide string literal token
#define STRING(str) L#str
```

Vous pouvez résoudre le problème de plusieurs façons :

- Utilisez la concaténation de chaînes de `L""` et `#str` pour ajouter un préfixe. Les littéraux de chaîne adjacents sont combinés après l’expansion macro :

   ```cpp
   #define STRING1(str) L""#str
   ```

- Ajouter le préfixe après que `#str` est une chaîne avec une expansion macro supplémentaire

   ```cpp
   #define WIDE(str) L##str
   #define STRING2(str) WIDE(#str)
   ```

- Utilisez l’opérateur de concaténation `##` pour combiner les jetons. L’ordre des opérations pour `##` et `#` n’est pas spécifié, bien que tous les compilateurs semblent évaluer l' `#` opérateur avant `##` dans ce cas.

   ```cpp
   #define STRING3(str) L## #str
   ```

### <a name="warning-on-invalid-"></a>Avertissement non valide \#\#

Lorsque l' [opérateur de collage de jeton (# #)](token-pasting-operator-hash-hash.md) ne génère pas de jeton de prétraitement valide unique, le comportement n’est pas défini. Le préprocesseur traditionnel ne parvient pas à combiner les jetons en mode silencieux. Le nouveau préprocesseur correspond au comportement de la plupart des autres compilateurs et émet un diagnostic.

```cpp
// The ## is unnecessary and does not result in a single preprocessing token.
#define ADD_STD(x) std::##x
// Declare a std::string
ADD_STD(string) s;
```

### <a name="comma-elision-in-variadic-macros"></a>Élision de virgule dans les macros variadiques

Le préprocesseur MSVC traditionnel supprime toujours les virgules avant les `__VA_ARGS__` remplacements vides. Le nouveau préprocesseur suit plus fidèlement le comportement d’autres compilateurs multiplateforme populaires. Pour la virgule à supprimer, l’argument variadiques doit être manquant (pas seulement vide) et doit être marqué avec un `##` opérateur. Prenons l’exemple suivant :

```cpp
void func(int, int = 2, int = 3);
// This macro replacement list has a comma followed by __VA_ARGS__
#define FUNC(a, ...) func(a, __VA_ARGS__)
int main()
{
    // In the traditional preprocessor, the
    // following macro is replaced with:
    // func(10,20,30)
    FUNC(10, 20, 30);

    // A conforming preprocessor replaces the
    // following macro with: func(1, ), which
    // results in a syntax error.
    FUNC(1, );
}
```

Dans l’exemple suivant, dans l’appel à `FUNC2(1)` l’argument variadiques est manquant dans la macro appelée. Dans, l’appel à `FUNC2(1, )` l’argument variadiques est vide, mais n’est pas manquant (Notez la virgule dans la liste d’arguments).

```cpp
#define FUNC2(a, ...) func(a , ## __VA_ARGS__)
int main()
{
   // Expands to func(1)
   FUNC2(1);

   // Expands to func(1, )
   FUNC2(1, );
}
```

Dans la norme C++ 20 à venir, ce problème a été résolu en ajoutant `__VA_OPT__` . La nouvelle prise en charge du préprocesseur pour  `__VA_OPT__` est disponible à partir de Visual Studio 2019 version 16,5.

### <a name="c20-variadic-macro-extension"></a>Extension de macro variadiques c++ 20

Le nouveau préprocesseur prend en charge l’élision d’argument de macro C++ 20 variadiques :

```cpp
#define FUNC(a, ...) __VA_ARGS__ + a
int main()
  {
  int ret = FUNC(0);
  return ret;
  }
```

Ce code n’est pas conforme avant la norme C++ 20. Dans MSVC, le nouveau préprocesseur étend ce comportement C++ 20 aux modes standard du langage ( **`/std:c++14`** , **`/std:c++17`** ). Cette extension correspond au comportement d’autres compilateurs C++ multiplateforme.

### <a name="macro-arguments-are-unpacked"></a>Les arguments de macro sont « décompressés »

Dans le préprocesseur traditionnel, si une macro transfère l’un de ses arguments à une autre macro dépendante, l’argument n’est pas « décompressé » lorsqu’il est inséré. En général, cette optimisation passe inaperçue, mais elle peut entraîner un comportement inhabituel :

```cpp
// Create a string out of the first argument, and the rest of the arguments.
#define TWO_STRINGS( first, ... ) #first, #__VA_ARGS__
#define A( ... ) TWO_STRINGS(__VA_ARGS__)
const char* c[2] = { A(1, 2) };

// Conforming preprocessor results:
// const char c[2] = { "1", "2" };

// Traditional preprocessor results, all arguments are in the first string:
// const char c[2] = { "1, 2", };
```

Lors `A()` du développement, le préprocesseur traditionnel transfère tous les arguments empaquetés dans `__VA_ARGS__` le premier argument de TWO_STRINGS, ce qui laisse l’argument variadiques `TWO_STRINGS` vide. En conséquence, le résultat de `#first` est « 1, 2 », et non simplement « 1 ». Si vous suivez les étapes de la même façon, vous vous demandez peut-être ce qui est arrivé au résultat de `#__VA_ARGS__` dans l’expansion du préprocesseur classique : si le paramètre variadiques est vide, il doit générer un littéral de chaîne vide `""` . Un problème distinct A empêché la génération du jeton de littéral de chaîne vide.

### <a name="rescanning-replacement-list-for-macros"></a>Nouvelle analyse de la liste de remplacement pour les macros

Une fois qu’une macro est remplacée, les jetons résultants sont réanalysés pour rechercher d’autres identificateurs de macro à remplacer. L’algorithme utilisé par le préprocesseur traditionnel pour effectuer la nouvelle analyse n’est pas conforme, comme illustré dans cet exemple en fonction du code réel :

```cpp
#define CAT(a,b) a ## b
#define ECHO(...) __VA_ARGS__
// IMPL1 and IMPL2 are implementation details
#define IMPL1(prefix,value) do_thing_one( prefix, value)
#define IMPL2(prefix,value) do_thing_two( prefix, value)

// MACRO chooses the expansion behavior based on the value passed to macro_switch
#define DO_THING(macro_switch, b) CAT(IMPL, macro_switch) ECHO(( "Hello", b))
DO_THING(1, "World");

// Traditional preprocessor:
// do_thing_one( "Hello", "World");
// Conforming preprocessor:
// IMPL1 ( "Hello","World");
```

Bien que cet exemple puisse paraître un peu fictif, nous l’avons vu dans du code réel.

Pour voir ce qui se passe, nous pouvons décomposer l’expansion à partir de `DO_THING` :

1. `DO_THING(1, "World")` se développe en `CAT(IMPL, 1) ECHO(("Hello", "World"))`
1. `CAT(IMPL, 1)` se développe en `IMPL ## 1` , qui se développe en `IMPL1`
1. Maintenant, les jetons sont dans cet État : `IMPL1 ECHO(("Hello", "World"))`
1. Le préprocesseur recherche l’identificateur de macro de type fonction `IMPL1` . Comme il n’est pas suivi d’un `(` , il n’est pas considéré comme un appel de macro de type fonction.
1. Le préprocesseur passe aux jetons suivants. Il recherche la macro de type fonction `ECHO` qui est appelée : `ECHO(("Hello", "World"))` , qui se développe en `("Hello", "World")`
1. `IMPL1` n’est jamais considérée à nouveau pour l’expansion, donc le résultat complet des expansions est le suivant : `IMPL1("Hello", "World");`

Pour modifier la macro de manière à ce qu’elle se comporte de la même façon sous le nouveau préprocesseur et le préprocesseur traditionnel, ajoutez une autre couche d’indirection :

```cpp
#define CAT(a,b) a##b
#define ECHO(...) __VA_ARGS__
// IMPL1 and IMPL2 are macros implementation details
#define IMPL1(prefix,value) do_thing_one( prefix, value)
#define IMPL2(prefix,value) do_thing_two( prefix, value)
#define CALL(macroName, args) macroName args
#define DO_THING_FIXED(a,b) CALL( CAT(IMPL, a), ECHO(( "Hello",b)))
DO_THING_FIXED(1, "World");

// macro expands to:
// do_thing_one( "Hello", "World");
```

## <a name="incomplete-features-before-165"></a>Fonctionnalités incomplètes avant 16,5

À compter de Visual Studio 2019 version 16,5, le nouveau préprocesseur est une fonctionnalité complète pour C++ 20. Dans les versions précédentes de Visual Studio, le nouveau préprocesseur est essentiellement complet, bien que la logique de la directive de préprocesseur repasse toujours au comportement traditionnel. Voici une liste partielle des fonctionnalités incomplètes dans les versions de Visual Studio antérieures à 16,5 :

- Prise en charge de `_Pragma`
- Fonctionnalités c++ 20
- Amélioration du bogue bloquant : les opérateurs logiques dans les expressions de constante de préprocesseur ne sont pas entièrement implémentés dans le nouveau préprocesseur avant la version 16,5. Dans certaines `#if` directives, le nouveau préprocesseur peut revenir au préprocesseur traditionnel. L’effet est visible uniquement lorsque les macros non compatibles avec le préprocesseur traditionnel sont développées. Cela peut se produire lors de la création d’emplacements de préprocesseurs Boost.

::: moniker-end
