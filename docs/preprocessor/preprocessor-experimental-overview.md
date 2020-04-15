---
title: Aperçu du préprocesseur expérimental MSVC
description: Le préprocesseur MSVC est mis à jour pour être conforme aux normes C/CMD.
ms.date: 02/09/2020
helpviewer_keywords:
- preprocessor, experimental
ms.openlocfilehash: 00c34ef75270e505d3781cf7eedf4d8aba95ee6e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81337486"
---
# <a name="msvc-experimental-preprocessor-overview"></a>Aperçu du préprocesseur expérimental MSVC

::: moniker range="vs-2015"

Visual Studio 2015 utilise le préprocesseur traditionnel, qui n’est pas conforme à Standard C. Un préprocesseur expérimental est disponible dans Visual Studio 2017 et Visual Studio 2019 en utilisant le compilateur [/experimental:preprocessor](../build/reference/experimental-preprocessor.md) compilateur. Plus d’informations sur l’utilisation du nouveau préprocesseur dans Visual Studio 2017 et Visual Studio 2019 sont disponibles. Pour voir la documentation de votre version préférée de Visual Studio, utilisez le contrôle du sélecteur **Version.** On le trouve en haut de la table des contenus sur cette page.

::: moniker-end

::: moniker range=">=vs-2017"

Nous mettons à jour le préprocesseur Microsoft CMD pour améliorer la conformité aux normes, corriger les bogues de longue date et changer certains comportements qui sont officiellement indéfinis. Nous avons également ajouté de nouveaux diagnostics pour mettre en garde contre les erreurs dans les définitions macro.

Ces modifications sont disponibles en utilisant le commutateur [de compilateur /experimental:preprocessor](../build/reference/experimental-preprocessor.md) dans Visual Studio 2017 ou Visual Studio 2019. Le comportement du préprocesseur par défaut reste le même que dans les versions précédentes.

À partir de Visual Studio 2019 version 16.5, le support préprocesseur expérimental pour la norme C-20 est complet.

## <a name="new-predefined-macro"></a>Nouvelle macro prédéfinie

Vous pouvez détecter quel préprocesseur est utilisé au moment de la compilation. Vérifiez la valeur de la macro [ \_MSVC\_TRADITIONAL](predefined-macros.md) prédéfinie pour savoir si le préprocesseur traditionnel est utilisé. Cette macro est définie sans condition par des versions du compilateur qui le soutiennent, indépendamment de laquelle le préprocesseur est invoqué. Sa valeur est de 1 pour le préprocesseur traditionnel. C’est 0 pour le préprocesseur conforme.

```cpp
#if defined(_MSVC_TRADITIONAL) && _MSVC_TRADITIONAL
// Logic using the traditional preprocessor
#else
// Logic using cross-platform compatible preprocessor
#endif
```

## <a name="behavior-changes-in-the-experimental-preprocessor"></a>Changements de comportement dans le préprocesseur expérimental

Les travaux initiaux sur le préprocesseur expérimental ont été axés sur la conformité de toutes les macro-extensions à la norme. Il vous permet d’utiliser le compilateur MSVC avec des bibliothèques qui sont actuellement bloquées par les comportements traditionnels. Nous avons testé le préprocesseur mis à jour sur des projets du monde réel. Voici quelques-uns des changements de rupture les plus courants que nous avons trouvés:

### <a name="macro-comments"></a>Commentaires macro

Le préprocesseur traditionnel est basé sur des tampons de caractère plutôt que des jetons de préprocesseur. Il permet un comportement inhabituel comme le truc de commentaire préprocesseur suivant, qui ne fonctionne pas sous le préprocesseur conforme:

```cpp
#if DISAPPEAR
#define DISAPPEARING_TYPE /##/
#else
#define DISAPPEARING_TYPE int
#endif

// myVal disappears when DISAPPEARING_TYPE is turned into a comment
DISAPPEARING_TYPE myVal;
```

Le correctif conforme aux normes `int myVal` est `#ifdef/#endif` de déclarer à l’intérieur des directives appropriées:

```cpp
#define MYVAL 1

#ifdef MYVAL
int myVal;
#endif
```

### <a name="lval"></a>Le val

Le préprocesseur traditionnel combine incorrectement un préfixe de chaîne au résultat de [l’opérateur de cordage](stringizing-operator-hash.md) :

```cpp
 #define DEBUG_INFO(val) L"debug prefix:" L#val
//                                       ^
//                                       this prefix

const wchar_t *info = DEBUG_INFO(hello world);
```

Dans ce cas, le `L` préfixe n’est pas nécessaire parce que les littérals de chaîne adjacents sont combinés après l’expansion macro de toute façon. Le correctif rétro-compatible est de changer la définition:

```cpp
#define DEBUG_INFO(val) L"debug prefix:" #val
//                                       ^
//                                       no prefix
```

La même question se trouve également dans les macros de commodité qui «enchaîner» l’argument à une large chaîne littérale:

```cpp
 // The traditional preprocessor creates a single wide string literal token
#define STRING(str) L#str
```

Vous pouvez résoudre le problème de diverses façons :

- Utilisez la concatenation `#str` de chaîne et ajouter le `L""` préfixe. Les littérals adjacents de chaîne sont combinés après l’expansion macro :

   ```cpp
   #define STRING1(str) L""#str
   ```

- Ajouter le préfixe après `#str` est enchaîné avec l’expansion macro supplémentaire

   ```cpp
   #define WIDE(str) L##str
   #define STRING2(str) WIDE(#str)
   ```

- Utilisez l’opérateur `##` de concatenation pour combiner les jetons. L’ordre `##` d’exploitation pour et `#` n’est pas précisé, `#` bien `##` que tous les compilateurs semblent évaluer l’opérateur avant dans ce cas.

   ```cpp
   #define STRING3(str) L## #str
   ```

### <a name="warning-on-invalid-"></a>Avertissement sur invalide\#\#

Lorsque [l’opérateur de jtonote-coller (MD)](token-pasting-operator-hash-hash.md) n’entraîne pas un seul jeton de prétraitement valide, le comportement n’est pas défini. Le préprocesseur traditionnel ne parvient pas silencieusement à combiner les jetons. Le nouveau préprocesseur correspond au comportement de la plupart des autres compilateurs et émet un diagnostic.

```cpp
// The ## is unnecessary and does not result in a single preprocessing token.
#define ADD_STD(x) std::##x
// Declare a std::string
ADD_STD(string) s;
```

### <a name="comma-elision-in-variadic-macros"></a>Comma élision en macros variadic

Le préprocesseur TRADITIONNEL MSVC enlève toujours `__VA_ARGS__` les virgules avant les remplacements vides. Le préprocesseur expérimental suit de plus près le comportement d’autres compilateurs cross-platform populaires. Pour que la virgule soit enlevée, l’argument variadique doit manquer (pas seulement vide) et il doit être marqué avec un `##` opérateur. Prenons l’exemple suivant :

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

Dans l’exemple suivant, `FUNC2(1)` dans l’appel à l’argument variadique est absent dans la macro étant invoquée. Dans l’appel à l’argument `FUNC2(1, )` variad est vide, mais ne manque pas (remarquez la virgule dans la liste d’argument).

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

Dans la prochaine norme C-20, cette question `__VA_OPT__`a été abordée en ajoutant . Le préprocesseur `__VA_OPT__` expérimental de support est disponible à partir de Visual Studio 2019 version 16.5.

### <a name="c20-variadic-macro-extension"></a>Extension macro variadic de C 20

Le préprocesseur expérimental prend en charge l’élision de l’argument macro variad de C 20 :

```cpp
#define FUNC(a, ...) __VA_ARGS__ + a
int main()
  {
  int ret = FUNC(0);
  return ret;
  }
```

Ce code n’est pas conforme avant la norme C 20. Dans MSVC, le préprocesseur expérimental étend ce comportement de C**`/std:c++14`** 20 à des modes standard de langue inférieurs (, **`/std:c++17`**). Cette extension correspond au comportement d’autres grands compilateurs multiplateformes C.

### <a name="macro-arguments-are-unpacked"></a>Les arguments macro sont " déballés »

Dans le préprocesseur traditionnel, si une macro avance l’un de ses arguments à une autre macro dépendante, puis l’argument ne devient pas "déballé" quand il est inséré. Habituellement, cette optimisation passe inaperçue, mais elle peut conduire à un comportement inhabituel:

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

Lors `A()`de l’expansion , le préprocesseur traditionnel `__VA_ARGS__` avance tous les arguments emballés dans le premier `TWO_STRINGS` argument de TWO_STRINGS, ce qui laisse l’argument variad de vide. Cela entraîne le `#first` résultat d’être "1, 2" plutôt que juste "1". Si vous suivez de près, alors vous vous demandez `#__VA_ARGS__` peut-être ce qui est arrivé au résultat de l’expansion traditionnelle de `""`préprocesseur: si le paramètre variadique est vide, il devrait entraîner une chaîne vide littérale . Un problème distinct a empêché le jeton littéral de chaîne vide d’être généré.

### <a name="rescanning-replacement-list-for-macros"></a>Liste de remplacement de rescanning pour les macros

Après qu’une macro est remplacée, les jetons qui en résultent sont rescannés pour que d’autres identificateurs macro remplacent. L’algorithme utilisé par le préprocesseur traditionnel pour faire le rescan n’est pas conforme, comme le montre cet exemple basé sur le code réel:

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

Bien que cet exemple puisse sembler un peu artificiel, nous l’avons vu dans le code du monde réel. Pour voir ce qui se passe, nous pouvons `DO_THING`décomposer l’expansion en commençant par :

1. `DO_THING(1, "World")`s’étend à`CAT(IMPL, 1) ECHO(("Hello", "World"))`
1. `CAT(IMPL, 1)`s’étend `IMPL ## 1`à , ce qui s’étend à`IMPL1`
1. Maintenant, les jetons sont dans cet état:`IMPL1 ECHO(("Hello", "World"))`
1. Le préprocesseur trouve l’identificateur `IMPL1`macro fonction-like . Puisqu’il n’est `(`pas suivi par un , il n’est pas considéré comme une invocation macro fonction-like.
1. Le préprocesseur passe aux jetons suivants. Il trouve que la `ECHO` macro fonction-like est invoquée: `ECHO(("Hello", "World"))`, qui s’étend à`("Hello", "World")`
1. `IMPL1`n’est jamais considéré à nouveau pour l’expansion, de sorte que le résultat complet des expansions est:`IMPL1("Hello", "World");`

Pour modifier la macro pour se comporter de la même manière sous le préprocesseur expérimental et le préprocesseur traditionnel, ajoutez une autre couche d’indirection :

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

## <a name="incomplete-features"></a>Caractéristiques incomplètes

À partir de Visual Studio 2019 version 16.5, le préprocesseur expérimental est complet pour le C 20. Dans les versions précédentes de Visual Studio, le préprocesseur expérimental est pour la plupart complet, bien que certaines logiques de directive préprocesseur retombe encore au comportement traditionnel. Voici une liste partielle des fonctionnalités incomplètes dans les versions Visual Studio avant 16.5:

- Prise en charge de `_Pragma`
- Caractéristiques de C 20
- Boost bug blocage: Opérateurs logiques dans les expressions constantes préprocesseur ne sont pas entièrement implémenté dans le nouveau préprocesseur avant la version 16.5. Sur `#if` certaines directives, le nouveau préprocesseur peut retomber au préprocesseur traditionnel. L’effet n’est perceptible que lorsque les macros incompatibles avec le préprocesseur traditionnel sont élargis. Il peut se produire lors de la construction de fentes de préprocesseur Boost.

::: moniker-end
