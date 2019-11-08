---
title: Vue d’ensemble du préprocesseur expérimental MSVC
description: Le préprocesseur MSVC est mis à jour pour être conforme aux normes C/C++ .
ms.date: 11/06/2019
helpviewer_keywords:
- preprocessor, experimental
ms.openlocfilehash: 446603b34d9309c256afba9abd7234ae2ab16f5c
ms.sourcegitcommit: 2362d15b5eb18d27773c3f7522da3d0eed9e2571
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73797175"
---
# <a name="msvc-experimental-preprocessor-overview"></a>Vue d’ensemble du préprocesseur expérimental MSVC

Le préprocesseur Microsoft C++ est en cours de mise à jour afin d’améliorer la conformité aux normes, de résoudre les bogues de longue date et de modifier certains comportements qui sont officiellement non définis. En outre, de nouveaux diagnostics ont été ajoutés pour signaler les erreurs dans les définitions de macros.

Ces modifications dans leur état actuel sont disponibles à l’aide du commutateur du compilateur de [préprocesseur/experimental :](../build/reference/experimental-preprocessor.md) dans visual studio 2017 ou visual studio 2019. Le comportement de préprocesseur par défaut reste le même que dans les versions précédentes.

## <a name="new-predefined-macro"></a>Nouvelle macro prédéfinie

Vous pouvez détecter le préprocesseur en cours d’utilisation au moment de la compilation. Vérifiez la valeur de la macro prédéfinie [\_MSVC\_traditionnel](predefined-macros.md) pour savoir si le préprocesseur traditionnel est en cours d’utilisation. Cette macro est définie de manière inconditionnelle par les versions du compilateur qui la prennent en charge, quel que soit le préprocesseur appelé. Sa valeur est 1 pour le préprocesseur traditionnel. Il est égal à 0 pour le préprocesseur expérimental conforme :

```cpp
#if defined(_MSVC_TRADITIONAL) && _MSVC_TRADITIONAL
// Logic using the traditional preprocessor
#else
// Logic using cross-platform compatible preprocessor
#endif
```

```cpp
#if defined(_MSVC_TRADITIONAL) && _MSVC_TRADITIONAL
// Logic using the traditional preprocessor
#else
// Logic using cross-platform compatible preprocessor
#endif
```

## <a name="behavior-changes-in-the-experimental-preprocessor"></a>Changements de comportement dans le préprocesseur expérimental

Le travail initial sur le préprocesseur expérimental a pour objectif de rendre toutes les expansions de macro conformes afin d’autoriser l’utilisation du compilateur MSVC avec des bibliothèques actuellement bloquées en raison de comportements traditionnels. Voici une liste de quelques-unes des modifications les plus courantes qui ont été exécutées dans lors du test du préprocesseur mis à jour avec des projets réels.

### <a name="macro-comments"></a>Commentaires sur les macros

Le préprocesseur traditionnel est basé sur des mémoires tampons de caractères plutôt que sur des jetons de préprocesseur. Cela permet un comportement inhabituel, tel que l’astuce de commentaire de préprocesseur suivante qui ne fonctionnera pas sous le préprocesseur conforme :

```cpp
#if DISAPPEAR
#define DISAPPEARING_TYPE /##/
#else
#define DISAPPEARING_TYPE int
#endif

// myVal disappears when DISAPPEARING_TYPE is turned into a comment
DISAPPEARING_TYPE myVal;
```

Le correctif conforme aux normes consiste à déclarer des `int myVal` à l’intérieur des directives `#ifdef/#endif` appropriées :

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

Dans ce cas, le préfixe `L` n’est pas nécessaire, car les littéraux de chaîne adjacents sont combinés après l’expansion macro. Le correctif à compatibilité descendante consiste à remplacer la définition par ce qui suit :

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

- Utilisez la concaténation de chaînes de `L""` et `#str` pour ajouter un préfixe. Cela fonctionne parce que les littéraux de chaîne adjacents sont combinés après l’expansion macro :

   ```cpp
   #define STRING1(str) L""#str
   ```

- Ajouter le préfixe une fois que `#str` est une chaîne avec une expansion macro supplémentaire

   ```cpp
   #define WIDE(str) L##str
   #define STRING2(str) WIDE(#str)
   ```

- Utilisez l’opérateur de concaténation `##` pour combiner les jetons. L’ordre des opérations pour `##` et `#` n’est pas spécifié, bien que tous les compilateurs semblent évaluer l’opérateur `#` avant `##` dans ce cas.

   ```cpp
   #define STRING3(str) L## #str
   ```

### <a name="warning-on-invalid-"></a>Avertissement en cas de \#non valide \#

Lorsque l' [opérateur de collage de jeton (# #)](token-pasting-operator-hash-hash.md) n’entraîne pas de jeton de prétraitement valide unique, le comportement n’est pas défini. Le préprocesseur traditionnel ne parvient pas à combiner les jetons en mode silencieux. Le nouveau préprocesseur correspondra au comportement de la plupart des autres compilateurs et émettrea un diagnostic.

```cpp
// The ## is unnecessary and does not result in a single preprocessing token.
#define ADD_STD(x) std::##x
// Declare a std::string
ADD_STD(string) s;
```

### <a name="comma-elision-in-variadic-macros"></a>Élision de virgule dans les macros variadiques

Le préprocesseur MSVC traditionnel supprime toujours les virgules avant les remplacements de `__VA_ARGS__` vides. Le préprocesseur expérimental suit plus étroitement le comportement d’autres compilateurs multiplateforme populaires. Pour la virgule à supprimer, l’argument variadiques doit être manquant (pas seulement vide) et doit être marqué avec un opérateur `##`. Prenons l'exemple suivant :

```cpp
void func(int, int = 2, int = 3);
// This macro replacement list has a comma followed by __VA_ARGS__
#define FUNC(a, ...) func(a, __VA_ARGS__)
int main()
{
    // In the traditional preprocessor, the following macro is replaced with:
    // func(10,20,30)
    FUNC(10, 20, 30);

    // A conforming preprocessor will replace the following macro with: func(1, ), which will result in a syntax error.
    FUNC(1, );
}
```

Dans l’exemple suivant, dans l’appel à `FUNC2(1)` l’argument variadiques est manquant dans la macro qui est évoquée. Dans l’appel à `FUNC2(1, )` l’argument variadiques est vide, mais n’est pas manquant (Notez la virgule dans la liste d’arguments).

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

Dans les prochaines normes C + + 2A, ce problème a été résolu en ajoutant `__VA_OPT__`, qui n’est pas encore implémenté.

### <a name="macro-arguments-are-unpacked"></a>Les arguments de macro sont « décompressés »

Dans le préprocesseur traditionnel, si une macro transfère l’un de ses arguments à une autre macro dépendante, l’argument n’obtient pas « décompressé » lorsqu’il est substitué. En général, cette optimisation passe inaperçue, mais elle peut entraîner un comportement inhabituel :

```cpp
// Create a string out of the first argument, and the rest of the arguments.
#define TWO_STRINGS( first, ... ) #first, #__VA_ARGS__
#define A( ... ) TWO_STRINGS(__VA_ARGS__)
const char* c[2] = { A(1, 2) };

// Conformant preprocessor results:
// const char c[2] = { "1", "2" };

// Traditional preprocessor results, all arguments are in the first string:
// const char c[2] = { "1, 2", };
```

Lors du développement `A()`, le préprocesseur traditionnel transfère tous les arguments empaquetés dans `__VA_ARGS__` au premier argument de TWO_STRINGS, ce qui laisse l’argument variadiques de `TWO_STRINGS` vide. Ainsi, le résultat de `#first` est « 1, 2 », plutôt que « 1 ». Si vous effectuez les opérations suivantes, vous vous demandez peut-être ce qui s’est produit dans le résultat de `#__VA_ARGS__` dans l’expansion du préprocesseur classique : si le paramètre variadiques est vide, la valeur doit être un littéral de chaîne vide `""`. En raison d’un problème distinct, le jeton de littéral de chaîne vide n’a pas été généré.

### <a name="rescanning-replacement-list-for-macros"></a>Nouvelle analyse de la liste de remplacement pour les macros

Une fois qu’une macro est remplacée, les jetons obtenus sont réanalysés pour rechercher d’autres identificateurs de macro qui doivent être remplacés. L’algorithme utilisé par le préprocesseur traditionnel pour effectuer la renumérisation n’est pas conforme, comme illustré dans cet exemple en fonction du code réel :

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
// Conformant preprocessor:
// IMPL1 ( "Hello","World");
```

Bien que cet exemple semble un peu fictif, il a été trouvé pour produire du code réel. Pour voir ce qui se passe, nous pouvons décomposer l’expansion à partir de `DO_THING`:

1. `DO_THING(1, "World")` se développe pour `CAT(IMPL, 1) ECHO(("Hello", "World"))`
1. `CAT(IMPL, 1)` se développe en `IMPL ## 1` qui se développe en `IMPL1`
1. Maintenant, les jetons sont dans cet État : `IMPL1 ECHO(("Hello", "World"))`
1. Le préprocesseur recherche l’identificateur de macro de type fonction `IMPL1`, mais il n’est pas suivi d’un `(`, donc il n’est pas considéré comme un appel de macro de type fonction. 
1. Il passe aux jetons suivants et recherche la macro de type fonction `ECHO` appelée : `ECHO(("Hello", "World"))`, qui se développe en `("Hello", "World")`
1. `IMPL1` n’est jamais considérée comme une nouvelle expansion, le résultat complet des expansions est donc le suivant : `IMPL1("Hello", "World");`

La macro peut être modifiée pour se comporter de la même façon dans le préprocesseur expérimental et le préprocesseur traditionnel en ajoutant une autre couche d’indirection :

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

## <a name="incomplete-features"></a>Fonctionnalités incomplètes

Le préprocesseur expérimental est essentiellement terminé, bien que la logique de la directive de préprocesseur repasse toujours au comportement traditionnel. Voici une liste partielle des fonctionnalités incomplètes :

- Prise en charge de `_Pragma`
- Fonctionnalités c++ 20
- Amélioration du bogue bloquant : les opérateurs logiques dans les expressions de constante de préprocesseur ne sont pas entièrement implémentés dans le nouveau préprocesseur. Dans certaines directives `#if`, le nouveau préprocesseur peut revenir au préprocesseur traditionnel. L’effet est visible uniquement lorsque les macros qui ne sont pas compatibles avec le préprocesseur traditionnel sont étendues, ce qui peut se produire lors de la création d’emplacements de préprocesseur d’amélioration.
