---
title: '/experimental : préprocesseur (activer le mode de conformité de préprocesseur)'
description: 'Utilisez l’option du compilateur de préprocesseur/experimental : pour activer la prise en charge expérimentale du compilateur pour un préprocesseur conforme au standard.'
ms.date: 09/03/2019
f1_keywords:
- preprocessor
- /experimental:preprocessor
helpviewer_keywords:
- preprocessor conformance
- /experimental:preprocessor
- Enable preprocessor conformance mode
ms.openlocfilehash: 3055cfa2a32d1d668dbe0c51b5542415b5bb0af4
ms.sourcegitcommit: fd0f8839da5c6a3663798a47c6b0bb6e63b518bd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70294436"
---
# <a name="experimentalpreprocessor-enable-preprocessor-conformance-mode"></a>/experimental : préprocesseur (activer le mode de conformité de préprocesseur)

Cette option active un préprocesseur expérimental basé sur les jetons qui est conforme aux normes C++ 11, y compris les fonctionnalités du préprocesseur C99.

## <a name="syntax"></a>Syntaxe

> **/experimental : préprocesseur** [ **-** ]

## <a name="remarks"></a>Notes

Utilisez l’option du compilateur de **préprocesseur/experimental :** pour activer le préprocesseur conforme expérimental. Vous pouvez utiliser **/experimental : preprocesseur-** option pour spécifier explicitement le préprocesseur traditionnel.

L’option **/experimental : preprocesser** est disponible à partir de Visual Studio 2017 version 15,8.

Vous pouvez détecter le préprocesseur en cours d’utilisation au moment de la compilation. Vérifiez la valeur de la macro [ \_prédéfinie MSVC\_traditionnelle](../../preprocessor/predefined-macros.md) pour savoir si le préprocesseur traditionnel est en cours d’utilisation. Cette macro est définie de manière inconditionnelle par les versions du compilateur qui la prennent en charge, quel que soit le préprocesseur appelé. Sa valeur est 1 pour le préprocesseur traditionnel. Il est égal à 0 pour le préprocesseur expérimental conforme :

```cpp
#if defined(_MSVC_TRADITIONAL) && _MSVC_TRADITIONAL
// Logic using the traditional preprocessor
#else
// Logic using cross-platform compatible preprocessor
#endif
```

### <a name="behavior-changes-in-the-experimental-preprocessor"></a>Changements de comportement dans le préprocesseur expérimental

Voici quelques-unes des modifications importantes les plus courantes détectées lorsque le mode de conformité de préprocesseur est activé :

#### <a name="macro-comments"></a>Commentaires sur les macros

Le préprocesseur traditionnel utilise des tampons de caractères au lieu des jetons de préprocesseur. Cela permet un comportement inhabituel, tel que l’astuce de commentaire du préprocesseur, qui ne fonctionne pas sous le préprocesseur conforme :

```cpp
#if DISAPPEAR
#define DISAPPEARING_TYPE /##/
#else
#define DISAPPEARING_TYPE int
#endif

// myVal disappears when DISAPPEARING_TYPE is turned into a comment
// To make standards compliant, wrap the following line with the appropriate #if/#endif
DISAPPEARING_TYPE myVal;
```

#### <a name="string-prefixes-lval"></a>Préfixes de chaîne (L # val)

Le préprocesseur traditionnel associe de manière incorrecte un préfixe de chaîne au résultat de l' [opérateur de chaîne (#)](../../preprocessor/stringizing-operator-hash.md):

```cpp
#define DEBUG_INFO(val) L"debug prefix:" L#val
//                                       ^
//                                       this prefix

const wchar_t *info = DEBUG_INFO(hello world);
```

Le `L` préfixe n’est pas nécessaire ici, car les littéraux de chaîne adjacents sont combinés après l’expansion macro. Le correctif à compatibilité descendante consiste à remplacer la définition par :

```cpp
#define DEBUG_INFO(val) L"debug prefix:" #val
//                                       ^
//                                       no prefix
```

Ce problème se trouve également dans les macros pratiques qui « chaînent » l’argument à un littéral de chaîne étendu :

```cpp
// The traditional preprocessor creates a single wide string literal token
#define STRING(str) L#str

// Potential fixes:
// Use string concatenation of L"" and #str to add prefix
// This works because adjacent string literals are combined after macro expansion
#define STRING1(str) L""#str

// Add the prefix after #str is stringized with additional macro expansion
#define WIDE(str) L##str
#define STRING2(str) WIDE(#str)

// Use concatenation operator ## to combine the tokens.
// The order of operations for ## and # is unspecified, although all compilers
// checked perform the # operator before ## in this case.
#define STRING3(str) L## #str
```

#### <a name="warning-on-invalid"></a>Avertissement non valide ##

Lorsque l' [opérateur de collage de jeton (# #)](../../preprocessor/token-pasting-operator-hash-hash.md) ne génère pas de jeton de prétraitement valide unique, le comportement n’est pas défini. Le préprocesseur traditionnel ne parvient pas à combiner les jetons en mode silencieux. Le nouveau préprocesseur correspond au comportement de la plupart des autres compilateurs et émet un diagnostic.

```cpp
// The ## is unnecessary and doesn't result in a single preprocessing token.
#define ADD_STD(x) std::##x

// Declare a std::string
ADD_STD(string) s;
```

#### <a name="comma-elision-in-variadic-macros"></a>Élision de virgule dans les macros variadiques

Prenons l'exemple suivant :

```cpp
void func(int, int = 2, int = 3);
// This macro replacement list has a comma followed by __VA_ARGS__
#define FUNC(a, ...) func(a, __VA_ARGS__)
int main()
{
    // The following macro is replaced with:
    // func(10,20,30)
    FUNC(10, 20, 30);

    // A conforming preprocessor replaces the following macro with:
    // func(1, );
    // which results in a syntax error.
    FUNC(1, );
}
```

Tous les compilateurs principaux ont une extension de préprocesseur qui permet de résoudre ce problème. Le préprocesseur MSVC traditionnel supprime toujours les virgules avant les `__VA_ARGS__` remplacements vides. Le préprocesseur mis à jour suit plus étroitement le comportement d’autres compilateurs interplateformes populaires. Pour la virgule à supprimer, l’argument variadiques doit être manquant, et non vide, et doit être marqué avec un `##` opérateur :

```cpp
#define FUNC2(a, ...) func(a , ## __VA_ARGS__)
int main()
{
    // The variadic argument is missing in the macro being evoked
    // The comma is removed and replaced with:
    // func(1)
    FUNC2(1);

    // The variadic argument is empty, but not missing. (Notice the
    // comma in the argument list.) The comma isn't removed
    // when the macro is replaced:
    // func(1, )
    FUNC2(1, );
}
```

Dans les prochaines normes C + + 2A, ce problème a été résolu par l' `__VA_OPT__`ajout de, qui n’est pas encore implémenté.

#### <a name="macro-arguments-are-unpacked"></a>Les arguments de macro sont « décompressés »

Dans le préprocesseur traditionnel, si une macro transfère l’un de ses arguments à une autre macro dépendante, l’argument n’est pas « décompressé » lorsqu’il est substitué. En général, cette optimisation passe inaperçue, mais elle peut entraîner un comportement inhabituel :

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

Lors du `A()`développement, le préprocesseur traditionnel transfère tous les arguments empaquetés dans `__VA_ARGS__` le premier argument de `TWO_STRINGS`. L’argument variadiques de `TWO_STRINGS` est vide, ce qui a pour `"1, 2"` effet `#first` que le résultat de est `"1"`plutôt que simplement. Vous vous demandez peut-être ce qui est arrivé `#__VA_ARGS__` au résultat de dans l’expansion de préprocesseur classique. Si le paramètre variadiques est vide, il doit générer un littéral de chaîne vide «». En raison d’un problème distinct, le jeton de littéral de chaîne vide n’a pas été généré.

#### <a name="rescanning-replacement-list-for-macros"></a>Nouvelle analyse de la liste de remplacement pour les macros

Une fois qu’une macro est remplacée, les jetons résultants sont réanalysés pour rechercher d’autres identificateurs de macro à remplacer. L’algorithme de renumérisation utilisé par le préprocesseur traditionnel n’est pas conforme, comme illustré dans cet exemple en fonction du code réel :

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

Pour voir ce qui se passe dans cet exemple, nous décomposons l’expansion à `DO_THING`partir de :

`DO_THING(1, "World")` ->
`CAT(IMPL, 1) ECHO(("Hello", "World"))`

Ensuite, CAT est développé :

`CAT(IMPL, 1)` -> `IMPL ## 1` -> `IMPL1`

Qui place les jetons dans cet État :

`IMPL1 ECHO(("Hello", "World"))`

Le préprocesseur recherche l’identificateur `IMPL1`de macro de type fonction, mais il n’est pas suivi d’un « ( », donc il n’est pas considéré comme un appel de macro de type fonction. Il passe aux jetons suivants et recherche la macro `ECHO` de type fonction appelée :

`ECHO(("Hello", "World"))` -> `("Hello", "World")`

`IMPL1`n’est jamais considérée à nouveau pour l’expansion, donc le résultat complet des expansions est le suivant :

`IMPL1("Hello", "World");`

La macro peut être modifiée pour se comporter de la même manière dans le préprocesseur expérimental et le préprocesseur traditionnel. La solution consiste à ajouter une autre couche d’indirection :

```cpp
#define CAT(a,b) a##b
#define ECHO(...) __VA_ARGS__

// IMPL1 and IMPL2 are macros implementation details
#define IMPL1(prefix,value) do_thing_one( prefix, value)
#define IMPL2(prefix,value) do_thing_two( prefix, value)

#define CALL(macroName, args) macroName args
#define DO_THING_FIXED(a,b) CALL( CAT(IMPL, a), ECHO(( "Hello",b)))

DO_THING_FIXED(1, "World");
// macro expanded to:
// do_thing_one( "Hello", "World");
```

### <a name="conformance-mode-conformance"></a>Conformité du mode de conformité

Le préprocesseur expérimental n’est pas encore terminé et une certaine logique de directive de préprocesseur revient toujours au comportement traditionnel. Voici une liste partielle des fonctionnalités incomplètes :

- Prise en charge de`_Pragma`
- Fonctionnalités c++ 20
- Améliorations supplémentaires du diagnostic
- Commutateurs pour contrôler la sortie sous/E et/P
- Augmenter le bogue bloquant : Les opérateurs logiques dans les expressions de constante de préprocesseur ne sont pas entièrement implémentés dans le nouveau préprocesseur. Dans certaines `#if` directives, le nouveau préprocesseur peut revenir au préprocesseur traditionnel. L’effet est visible uniquement lorsque les macros qui ne sont pas compatibles avec le préprocesseur traditionnel sont étendues, ce qui peut se produire lors de la création d’emplacements de préprocesseur d’amélioration.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Sélectionnez la page de propriétés **Propriétés de configuration** > **C/C++**  > **Ligne de commande**.

1. Modifiez la propriété **options supplémentaires** pour inclure **/experimental : préprocesseur** , puis choisissez **OK**.

## <a name="see-also"></a>Voir aussi

[/Zc (Conformité)](zc-conformance.md)
