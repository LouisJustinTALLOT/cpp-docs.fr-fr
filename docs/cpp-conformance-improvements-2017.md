---
title: Améliorations de la conformité de C++
ms.date: 10/31/2018
ms.technology:
- cpp-language
ms.assetid: 8801dbdb-ca0b-491f-9e33-01618bff5ae9
author: mikeblome
ms.author: mblome
ms.openlocfilehash: 7755e0f1cb2292fc88788ab1b75e19c00f144310
ms.sourcegitcommit: 48d7d17820be7a95b793e2485b7223879ece5f08
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/14/2018
ms.locfileid: "51635163"
---
# <a name="c-conformance-improvements-in-visual-studio-2017-versions-150-153improvements153-155improvements155-156improvements156-157improvements157-158update158-159update159"></a>Améliorations de la conformité de C++ dans Visual Studio 2017 versions 15.0, [15.3](#improvements_153), [15.5](#improvements_155), [15.6](#improvements_156), [15.7](#improvements_157), [15.8](#update_158), [15.9](#update_159)

Avec la prise en charge des expressions constexpr généralisées et de NSDMI pour les agrégats, le compilateur Microsoft Visual C++ est désormais complet pour les fonctionnalités ajoutées à la norme C++14. Notez que le compilateur ne dispose pas encore de certaines fonctionnalités des normes C++11 et C++98. Consultez [Conformité du langage Visual C++](visual-cpp-language-conformance.md) pour obtenir un tableau affichant l’état actuel du compilateur.

## <a name="c11"></a>C++11

### <a name="expression-sfinae-support-in-more-libraries"></a>Prise en charge de la fonctionnalité SFINAE pour les expressions dans d’autres bibliothèques

Le compilateur Visual C++ continue d’améliorer sa prise en charge de la fonctionnalité SFINAE pour les expressions, qui est nécessaire pour la déduction et la substitution d’argument de modèle dans lesquelles les expressions decltype et constexpr peuvent apparaître en tant que paramètres de modèle. Pour plus d’informations, consultez [Expression SFINAE improvements in Visual Studio 2017 RC](https://blogs.msdn.microsoft.com/vcblog/2016/06/07/expression-sfinae-improvements-in-vs-2015-update-3).

## <a name="c-14"></a>C++14

### <a name="nsdmi-for-aggregates"></a>NSDMI pour les agrégats

Un agrégat est un tableau ou une classe sans constructeur fourni par l’utilisateur, sans membres de données non statiques privés ou protégés, sans classes de base et sans fonctions virtuelles. À compter de C++14, les agrégats peuvent contenir des initialiseurs de membres. Pour plus d’informations, consultez [Member initializers and aggregates](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3605.html).

### <a name="extended-constexpr"></a>Fonctions constexpr étendues

Les expressions déclarées en tant qu’expressions constexpr sont désormais autorisées à contenir certains types de déclarations, des instructions if et switch, des instructions de boucle et une mutation d’objets dont la vie a commencé dans l’évaluation de l’expression constexpr. En outre, il n’est plus nécessaire qu’une fonction membre non statique constexpr soit implicitement de type const. Pour plus d’informations, consultez [Relaxing constraints on constexpr functions](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3652.html).

## <a name="c17"></a>C++17

### <a name="terse-staticassert"></a>Terse static_assert

Le paramètre de message pour static_assert est facultatif. Pour plus d’informations, consultez [Extending static_assert, v2](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n3928.pdf).

### <a name="fallthrough-attribute"></a>Attribut [[fallthrough]]

En mode **/std:c++17** mode, l’attribut [[fallthrough]] est utilisable dans le contexte des instructions switch en tant qu’indicateur informant le compilateur que le comportement fallthrough est prévu. Ce dispositif empêche le compilateur d’émettre des avertissements dans de tels cas. Pour plus d’informations, consultez [Wording for [[fallthrough]] attribute](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0188r0.pdf).

### <a name="generalized-range-based-for-loops"></a>Boucles For basées sur une plage généralisées

Range-based pour les boucles ne nécessitent plus que begin() et end() retournent des objets du même type. Ainsi, end() peut retourner un objet sentinel, à l’image de ceux utilisés par les plages définies dans [range-v3](https://github.com/ericniebler/range-v3) et la spécification technique d’autres plages disponibles mais pas encore publiées. Pour plus d’informations, consultez [Generalizing the Range-Based For Loop](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0184r0.html).

## <a name="improvements_153"></a> Améliorations dans Visual Studio 2017 version 15.3

### <a name="constexpr-lambdas"></a>Expressions lambda dans des contextes constexpr

Les expressions lambda peuvent désormais être utilisées dans les expressions constantes. Pour plus d’informations, consultez [Expressions lambda constexpr en C++](cpp/lambda-expressions-constexpr.md).

### <a name="if-constexpr-in-function-templates"></a>if constexpr dans les modèles de fonction

Un modèle de fonction peut contenir des instructions `if constexpr` permettant de créer une branche au moment de la compilation. Pour plus d’informations, consultez [Instructions if constexpr](cpp/if-else-statement-cpp.md#if_constexpr).

### <a name="selection-statements-with-initializers"></a>Instructions Selection avec initialiseurs

Une instruction `if` peut inclure un initialiseur qui présente une variable à portée de bloc dans l’instruction elle-même. Pour plus d’informations, consultez [Instructions if avec initialiseur](cpp/if-else-statement-cpp.md#if_with_init).

### <a name="maybeunused-and-nodiscard-attributes"></a>Attributs [[maybe_unused]] et [[nodiscard]]

Nouveaux attributs permettant de mettre en silence les avertissements quand une entité n’est pas utilisée, ou de créer un avertissement si la valeur de retour d’un appel de fonction est ignorée. Pour plus d’informations, consultez [Attributes in C++](cpp/attributes.md).

### <a name="using-attribute-namespaces-without-repetition"></a>Utilisation des espaces de noms d’attribut sans répétition

Nouvelle syntaxe pour activer uniquement un seul identificateur d’espace de noms dans une liste d’attributs. Pour plus d’informations, consultez [Attributes in C++](cpp/attributes.md).

### <a name="structured-bindings"></a>Liaisons structurées

Il est désormais possible dans une déclaration unique de stocker une valeur avec des noms individuels pour ses composants, lorsque la valeur est un tableau, un std::tuple ou std::pair, ou contient uniquement des membres de données non statiques publiques. Pour plus d’informations, consultez [Liaisons structurées](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0144r0.pdf) et [Retour de plusieurs valeurs à partir d’une fonction](cpp/functions-cpp.md#multi_val).

### <a name="construction-rules-for-enum-class-values"></a>Règles de construction pour les valeurs de classe enum

Il existe désormais une conversion implicite/non restrictive à partir du type sous-jacent d’une énumération étendue vers l’énumération elle-même, lorsque sa définition ne présente aucun énumérateur et que la source utilise une syntaxe d’initialisation de liste. Pour plus d’informations, consultez [Règles de construction pour les valeurs de classe enum](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0138r2.pdf) et [Énumérations](cpp/enumerations-cpp.md#no_enumerators).

### <a name="capturing-this-by-value"></a>Capture de \*this par valeur

L’objet `*this` dans une expression lambda peut désormais être capturé par sa valeur. Cela permet des scénarios dans lesquels l’expression lambda est invoquée dans des opérations parallèles et asynchrones, en particulier sur des architectures de machines plus récentes. Pour plus d’informations, consultez [Lambda Capture of \*this by Value as [=,\*this]](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0018r3.html).

### <a name="removing-operator-for-bool"></a>Suppression d’operator++ pour bool

`operator++` n’est plus pris en charge sur les types `bool`. Pour plus d’informations, consultez [Remove Deprecated operator++(bool)](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0002r1.html).

### <a name="removing-deprecated-register-keyword"></a>Suppression du mot clé « register » déprécié

Le mot clé `register`, déjà déprécié (et ignoré par le compilateur), est maintenant supprimé du langage. Pour plus d’informations, consultez [Remove Deprecated Use of the register Keyword](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0001r1.html).

Pour obtenir la liste complète des améliorations de la conformité jusqu’à Visual Studio 2015 Update 3, consultez [Visual C++ What’s New 2003 through 2015](https://msdn.microsoft.com/library/mt723604.aspx).

## <a name="improvements_155"></a>  Améliorations dans Visual Studio 2017 version 15.5

Les fonctionnalités marquées avec [14] sont disponibles sans conditions, même en mode **/std:c++14**.

### <a name="new-compiler-switch-for-extern-constexpr"></a>Nouveau commutateur de compilateur pour extern constexpr

Dans les versions antérieures de Visual Studio, le compilateur retournait toujours une liaison interne pour la variable `constexpr`, même quand la variable était marquée comme `extern`. Dans Visual Studio 2017 version 15.5, un nouveau commutateur de compilateur, [/Zc:externConstexpr](build/reference/zc-externconstexpr.md), active le comportement correct de conformité aux normes. Pour plus d’informations, consultez [Liaison extern constexpr](#extern_linkage).

### <a name="removing-dynamic-exception-specifications"></a>Suppression des spécifications d’exceptions dynamiques

[P0003R5](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0003r5.html)Les spécifications d’exceptions dynamiques ont été dépréciées dans C++11. La fonctionnalité est supprimée dans C++17, mais la spécification (toujours) dépréciée `throw()` est conservée uniquement comme alias pour `noexcept(true)`. Pour plus d’informations, consultez [Suppression des spécifications d’exceptions dynamiques et noexcept](#noexcept_removal).

### <a name="notfn"></a>not_fn()

[P0005R4](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0005r4.html) `not_fn` vient remplacer `not1` et `not2`.

### <a name="rewording-enablesharedfromthis"></a>Reformulation de enable_shared_from_this

[P0033R1](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0033r1.html) `enable_shared_from_this` a été ajouté dans C++11. La norme C++17 met à jour la spécification pour mieux gérer certains cas extrêmes. [14]

### <a name="splicing-maps-and-sets"></a>Ajout de mappages et d’ensembles

[P0083R3](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0083r3.pdf) Cette fonctionnalité permet d’extraire des nœuds de conteneurs associatifs (par exemple, map, set, unordered\_map, unordered\_set) pour les modifier, puis de les réinsérer dans le même conteneur ou dans un autre conteneur qui utilise le même type de nœud. (Un cas d’usage courant consiste à extraire un nœud d’un `std::map`, à changer la clé et à réinsérer le nœud.)

### <a name="deprecating-vestigial-library-parts"></a>Composants de bibliothèque rudimentaires dépréciés

[P0174R2](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0174r2.html) Plusieurs fonctionnalités de la bibliothèque standard C++ ont été remplacées par de nouvelles fonctionnalités au fil des années, ou ont été jugées inutiles ou problématiques. Ces fonctionnalités sont officiellement dépréciées dans C++17.

### <a name="removing-allocator-support-in-stdfunction"></a>Suppression de la prise en charge des allocateurs dans std::function

[P0302R1](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0302r1.html) Dans les versions antérieures à C++17, le modèle de classe `std::function` avait plusieurs constructeurs avec un argument allocateur. Toutefois, l’utilisation d’allocateurs dans ce contexte était problématique et la sémantique n’était pas claire. Les constructeurs en question ont été supprimés.

### <a name="fixes-for-notfn"></a>Correctifs pour not_fn()

[P0358R1](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0358r1.html) La nouvelle formulation pour `std::not_fn` permet de prendre en charge la propagation de la catégorie de valeur quand un wrapper est appelé.

### <a name="sharedptrt-sharedptrtn"></a>shared_ptr\<T[]>, shared_ptr\<T[N]>

[P0414R2](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0414r2.html) Fusion des modifications apportées à `shared_ptr` dans C++17 dans Library Fundamentals. [14]

### <a name="fixing-sharedptr-for-arrays"></a>Correction de shared_ptr pour les tableaux

[P0497R0](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0497r0.html) Correctifs apportés à la prise en charge de shared_ptr pour les tableaux. [14]

### <a name="clarifying-insertreturntype"></a>Clarification d’insert_return_type

[P0508R0](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0508r0.html) Les conteneurs associatifs ou non ordonnés avec des clés uniques ont une fonction membre `insert` qui retourne un type imbriqué `insert_return_type`. Le type de retour est maintenant défini comme une spécialisation d’un type qui est paramétré sur les éléments Iterator et NodeType du conteneur.

### <a name="inline-variables-for-the-stl"></a>Variables inline pour la bibliothèque STL

[P0607R0](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0607r0.html)

### <a name="annex-d-features-deprecated"></a>Fonctionnalités dépréciées de l’annexe D

L’annexe D de la norme C++ contient toutes les fonctionnalités qui ont été dépréciées, notamment `shared_ptr::unique()`, `<codecvt>` et `namespace std::tr1`. Quand le commutateur de compilateur **/std:c++17** est défini, presque toutes les fonctionnalités de la bibliothèque standard listées dans l’annexe D sont marquées comme dépréciées. Pour plus d’informations, consultez [Les fonctionnalités de la bibliothèque standard répertoriées dans l’annexe D sont marquées comme dépréciées](#annex_d).

Maintenant, l’espace de noms `std::tr2::sys` dans `<experimental/filesystem>` émet un avertissement de dépréciation en mode **/std:c++14** par défaut, et est supprimé en mode **/std:c++17** par défaut.

La conformité est améliorée dans iostreams, car l’utilisation d’une extension non standard (spécialisations de classe explicites) n’est plus nécessaire.

La bibliothèque standard utilise désormais les modèles de variable en interne.

La bibliothèque standard a été mise à jour en réponse aux modifications apportées au compilateur C++17, notamment l’ajout de noexcept dans le système de type et la suppression des spécifications d’exceptions dynamiques.

## <a name="improvements_156"></a>  Améliorations dans Visual Studio 2017 version 15.6

### <a name="c17-library-fundamentals-v1"></a>C++17 - Library Fundamentals V1

[P0220R1](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0220r1.html) incorpore la spécification technique relative aux notions de base des bibliothèques (Library Fundamentals TS) pour C++17 à la norme. Ce document traite des mises à jour apportées à \<experimental/tuple>, \<experimental/optional>, \<experimental/functional>, \<experimental/any>, \<experimental/string_view>, \<experimental/memory>, \<experimental/memory_resource> et \<experimental/algorithm>.

### <a name="c17-improving-class-template-argument-deduction-for-the-stl"></a>C++17 - Amélioration de la déduction d’arguments de modèle de classe pour la bibliothèque STL

[P0739R0](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0739r0.html) `adopt_lock_t` est déplacé au début de la liste des paramètres de `scoped_lock` pour garantir une utilisation cohérente de `scoped_lock`. Le constructeur `std::variant` est autorisé à participer à la résolution de surcharge dans davantage de cas pour permettre l’assignation de copie.

## <a name="improvements_157"></a> Améliorations dans Visual Studio 2017 version 15.7

### <a name="c17-rewording-inheriting-constructors"></a>C++17 - Reformulation de l’héritage des constructeurs

[P0136R1](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0136r1.html) Dans une déclaration **using** qui nomme un constructeur, les initialisations de la classe dérivée peuvent désormais voir les constructeurs de la classe de base correspondante, évitant ainsi la déclaration de constructeurs supplémentaires pour la classe dérivée. Il s’agit là d’un changement par rapport à C++14. Dans Visual Studio 2017 versions 15.7 et ultérieures, en mode **/std:c++17**, le code qui utilise l’héritage de constructeurs et qui est valide dans C++14 peut être non valide ou avoir une sémantique différente.

L’exemple suivant montre le comportement de C++14 :

```cpp
struct A {
    template<typename T>
    A(T, typename T::type = 0);
    A(int);
};

struct B : A {
    using A::A;
    B(int n) = delete; // Error C2280
};

B b(42L); // Calls B<long>(long), which calls A(int)
          //  due to substitution failure in A<long>(long).
```

L’exemple suivant montre le comportement de **/std:c++17** dans Visual Studio 15.7 :

```cpp
struct A {
    template<typename T>
    A(T, typename T::type = 0);
    A(int);
};

struct B : A {
    using A::A;
    B(int n)
    {
        //do something
    }
};

B b(42L); // now calls B(int)
```

Pour plus d’informations, consultez [Constructeurs](cpp/constructors-cpp.md#inheriting_constructors).

### <a name="c17-extended-aggregate-initialization"></a>C++17 - Initialisation d’agrégats étendue

[P0017R1](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0017r1.html)

Si le constructeur d’une classe de base est non public, mais qu’il est accessible à une classe dérivée, vous ne pouvez plus utiliser d’accolades vides pour initialiser un objet du type dérivé en mode **/std:c++17** dans Visual Studio version 15.7.

L’exemple suivant montre le comportement conforme à C++14 :

```cpp
struct Derived;

struct Base {
    friend struct Derived;
private:
    Base() {}
};

struct Derived : Base {};

Derived d1; // OK. No aggregate init involved.
Derived d2 {}; // OK in C++14: Calls Derived::Derived()
               // which can call Base ctor.
```

Dans C++17, `Derived` est désormais considéré comme un type d’agrégat. L’initialisation de `Base` par le biais du constructeur par défaut privé se produit donc directement dans le cadre de la règle d’initialisation d’agrégats étendue. Auparavant, le constructeur privé `Base` était appelé par le biais du constructeur `Derived`, ce qui réussissait en raison de la déclaration friend.

L’exemple suivant montre le comportement de C++17 dans Visual Studio version 15.7 en mode **/std:c++17** :

```cpp
struct Derived;

struct Base {
    friend struct Derived;
private:
    Base() {}
};

struct Derived : Base {
    Derived() {} // add user-defined constructor
                 // to call with {} initialization
};

Derived d1; // OK. No aggregate init involved.

Derived d2 {}; // error C2248: 'Base::Base': cannot access
               // private member declared in class 'Base'
```

### <a name="c17-declaring-non-type-template-parameters-with-auto"></a>C++17 - Déclaration de paramètres de modèle sans type avec auto

[P0127R2](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0127r2.html)

En mode **/std:c++17**, le compilateur peut désormais déduire le type d’un argument de modèle sans type déclaré avec **auto** :

```cpp
template <auto x> constexpr auto constant = x;

auto v1 = constant<5>;      // v1 == 5, decltype(v1) is int
auto v2 = constant<true>;   // v2 == true, decltype(v2) is bool
auto v3 = constant<'a'>;    // v3 == 'a', decltype(v3) is char
```

L’une des conséquences de cette nouvelle fonctionnalité est que le code valide dans C++14 peut être non valide ou avoir une sémantique différente. Par exemple, certaines surcharges qui étaient précédemment non valides sont à présent valides. L’exemple suivant montre du code C++14 dont la compilation réussit car l’appel à `foo(p)` est lié à `foo(void*);`. Dans Visual Studio 2017 version 15.7, en mode **/std:c++17**, le modèle de fonction `foo` offre la meilleure correspondance.

```cpp
template <int N> struct A;
template <typename T, T N> int foo(A<N>*) = delete;

void foo(void *);

void bar(A<0> *p)
{
    foo(p); // OK in C++14
}
```

L’exemple suivant montre du code C++17 dans Visual Studio 15.7 en mode **/std:c++17** :

```cpp
template <int N> struct A;
template <typename T, T N> int foo(A<N>*);

void foo(void *);

void bar(A<0> *p)
{
    foo(p); // C2280: 'int foo<int,0>(A<0>*)': attempting to reference a deleted function
}
```

### <a name="c17-elementary-string-conversions-partial"></a>C++17 - Conversions de chaîne élémentaires (état partiel)

[P0067R5](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0067r5.html) Fonctions de bas niveau indépendantes des paramètres régionaux pour les conversions entre entiers et chaînes et entre nombres à virgule flottante et chaînes. (Dans Visual Studio 15.7 Preview 2, seuls les entiers sont pris en charge.)

### <a name="c20-avoiding-unnecessary-decay-partial"></a>C++20 - Prévention des dégradations inutiles (état partiel)

[P0777R1](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0777r1.pdf) Ajoute une distinction entre le concept de « dégradation » et la simple opération consistant à supprimer const ou des qualificateurs de référence.  Le nouveau trait de type `remove_reference_t` remplace `decay_t` dans certains contextes. La prise en charge de `remove_cvref_t` n’est pas encore implémentée dans Visual Studio 2017 version 15.7 Preview 2.

### <a name="c17-parallel-algorithms"></a>C++17 - Algorithmes parallèles

[P0024R2](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0024r2.html) La spécification technique relative au parallélisme (Parallelism TS) est intégrée à la norme, avec des modifications mineures.

### <a name="c17-hypotx-y-z"></a>C++17 - hypot(x, y, z)

[P0030R1](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0030r1.pdf) Ajoute trois nouvelles surcharges à `std::hypot` pour les types **float**, **double** et **long double** (chacun d’eux ayant trois paramètres d’entrée).

### <a name="c17-filesystem"></a>C++17 - \<filesystem>

[P0218R1](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0218r1.html) Intègre la spécification technique relative au système de fichiers (File System TS) à la norme, avec quelques modifications de formulation.

### <a name="c17-mathematical-special-functions"></a>C++17 - Fonctions mathématiques spéciales

[P0226R1](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0220r1.html) Intègre les spécifications techniques précédentes pour les fonctions mathématiques spéciales à l’en-tête \<cmath> standard.

### <a name="c17-deduction-guides-for-the-stl"></a>C++17 - Guides de déduction pour la bibliothèque STL

[P0433R2](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0433r2.html) Met à jour STL pour tirer parti de l’adoption par C++17 de [P0091R3](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0091r3.html), qui ajoute la prise en charge de la déduction d’arguments de modèle de classe.

### <a name="c17-repairing-elementary-string-conversions"></a>C++17 - Réparation de conversions de chaînes élémentaires

[P0682R1](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0682r1.html) Déplace les nouvelles fonctions de conversion de chaîne élémentaire de P0067R5 vers un nouvel en-tête \<charconv> et apporte d’autres améliorations, notamment l’utilisation de `std::errc` pour la gestion des erreurs au lieu de `std::error_code`.

### <a name="c17-constexpr-for-chartraits-partial"></a>C++17 - constexpr pour char_traits (état partiel)

[P0426R1](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0426r1.html) Changements apportés aux fonctions membres `std::traits_type` `length`, `compare` et `find` pour rendre `std::string_view` utilisable dans les expressions constantes. (Dans Visual Studio 2017 version 15.6, prise en charge pour Clang/LLVM uniquement. Dans la version 15.7 Preview 2, la prise en charge est presque complète pour ClXX.)

## <a name="bug-fixes-in-visual-studio-versions-150-153update153-155update155-157update157-158update158-and-159update159"></a>Correctifs de bogues dans Visual Studio versions 15.0, [15.3](#update_153), [15.5](#update_155), [15.7](#update_157), [15.8](#update_158) et [15.9](#update_159)

### <a name="copy-list-initialization"></a>Copy-list-initialization

Visual Studio 2017 déclenche correctement les erreurs de compilateur liées à la création d’objets à l’aide de listes d’initialiseurs qui n’étaient pas interceptées dans Visual Studio 2015 et qui pouvaient entraîner des blocages ou un comportement d’exécution non défini. Conformément au document N4594, point 13.3.1.7p1, dans copy-list-initialization, le compilateur doit envisager un constructeur explicite pour la résolution de la surcharge, mais doit générer une erreur si cette surcharge est choisie.

Les deux exemples suivants se compilent dans Visual Studio 2015, mais pas dans Visual Studio 2017.

```cpp
struct A
{
    explicit A(int) {}
    A(double) {}
};

int main()
{
    A a1 = { 1 }; // error C3445: copy-list-initialization of 'A' cannot use an explicit constructor
    const A& a2 = { 1 }; // error C2440: 'initializing': cannot convert from 'int' to 'const A &'

}
```

Pour corriger l’erreur, utilisez une initialisation directe :

```cpp
A a1{ 1 };
const A& a2{ 1 };
```

Dans Visual Studio 2015, le compilateur traitait à tort copy-list-initialization de la même façon que l’instruction copy-initialization ordinaire ; il envisageait uniquement de convertir les constructeurs pour résoudre la surcharge. Dans l’exemple suivant, Visual Studio 2015 choisit MyInt(23), mais Visual Studio 2017 déclenche l’erreur correctement.

```cpp
// From http://www.open-std.org/jtc1/sc22/wg21/docs/cwg_closed.html#1228
struct MyStore {
    explicit MyStore(int initialCapacity);
};

struct MyInt {
    MyInt(int i);
};

struct Printer {
    void operator()(MyStore const& s);
    void operator()(MyInt const& i);
};

void f() {
    Printer p;
    p({ 23 }); // C3066: there are multiple ways that an object of this type can be called with these arguments
}
```

Cet exemple est semblable au précédent, mais génère une erreur différente. Il réussit dans Visual Studio 2015, mais échoue dans Visual Studio 2017 avec l’erreur C2668.

```cpp
struct A {
    explicit A(int) {}
};

struct B {
    B(int) {}
};

void f(const A&) {}
void f(const B&) {}

int main()
{
    f({ 1 }); // error C2668: 'f': ambiguous call to overloaded function
}
```

### <a name="deprecated-typedefs"></a>Typedefs dépréciées

Visual Studio 2017 émet désormais l’avertissement correct pour les typedefs dépréciées qui sont déclarées dans une classe ou une structure. L’exemple suivant se compile sans avertissements dans Visual Studio 2015, mais génère l’erreur C4996 dans Visual Studio 2017.

```cpp
struct A
{
    // also for __declspec(deprecated)
    [[deprecated]] typedef int inttype;
};

int main()
{
    A::inttype a = 0; // C4996 'A::inttype': was declared deprecated
}
```

### <a name="constexpr"></a>constexpr

Visual Studio 2017 génère correctement une erreur quand l’opérande de gauche d’une opération à évaluation conditionnelle n’est pas valide dans un contexte constexpr. Le code suivant compile dans Visual Studio 2015, mais pas dans Visual Studio 2017 (C3615, la fonction constexpr 'f' ne peut pas produire une expression constante) :

```cpp
template<int N>
struct array
{
    int size() const { return N; }
};

constexpr bool f(const array<1> &arr)
{
    return arr.size() == 10 || arr.size() == 11; // C3615
}
```

Pour corriger cette erreur, déclarez la fonction `array::size()` en tant que `constexpr` ou supprimez le qualificateur `constexpr` de `f`.

### <a name="class-types-passed-to-variadic-functions"></a>Types de classe transmis aux fonctions variadiques

Dans Visual Studio 2017, les classes ou structures qui sont passées à une fonction variadique telle que printf doivent être copiables de manière triviale. Quand de tels objets sont passés, le compilateur effectue simplement une copie au niveau du bit et n’appelle pas le constructeur ou le destructeur.

```cpp
#include <atomic>
#include <memory>
#include <stdio.h>

int main()
{
    std::atomic<int> i(0);
    printf("%i\n", i); // error C4839: non-standard use of class 'std::atomic<int>'
                        // as an argument to a variadic function.
                        // note: the constructor and destructor will not be called;
                        // a bitwise copy of the class will be passed as the argument
                        // error C2280: 'std::atomic<int>::atomic(const std::atomic<int> &)':
                        // attempting to reference a deleted function

    struct S {
        S(int i) : i(i) {}
        S(const S& other) : i(other.i) {}
        operator int() { return i; }
    private:
        int i;
    } s(0);
    printf("%i\n", s); // warning C4840 : non-portable use of class 'main::S'
                      // as an argument to a variadic function
}
```

Pour corriger cette erreur, vous pouvez appeler une fonction membre qui retourne un type copiable de manière triviale,

```cpp
    std::atomic<int> i(0);
    printf("%i\n", i.load());
```

ou effectuer un cast statique pour convertir l’objet avant de le transmettre :

```cpp
    struct S {/* as before */} s(0);
    printf("%i\n", static_cast<int>(s))
```

Pour les chaînes générées et gérées à l’aide de CString, vous devez utiliser le `operator LPCTSTR()` fourni pour caster un objet CString vers le pointeur C attendu par la chaîne de format.

```cpp
CString str1;
CString str2 = _T("hello!");
str1.Format(_T("%s"), static_cast<LPCTSTR>(str2));
```

### <a name="cv-qualifiers-in-class-construction"></a>Qualificateurs cv dans la construction de la classe

Dans Visual Studio 2015, le compilateur ignore parfois à tort le qualificateur cv pendant la génération d’un objet de classe par le biais d’un appel de constructeur. Cela peut provoquer un incident ou un comportement inattendu au moment de l’exécution. L’exemple suivant se compile dans Visual Studio 2015, mais génère une erreur de compilateur dans Visual Studio 2017 :

```cpp
struct S
{
    S(int);
    operator int();
};

int i = (const S)0; // error C2440
```

Pour corriger l’erreur, déclarez `operator int()` en tant que `const`.

### <a name="access-checking-on-qualified-names-in-templates"></a>Contrôle d’accès sur les noms qualifiés dans les modèles

Les versions précédentes du compilateur n’effectuaient pas de contrôle d’accès sur les noms qualifiés dans certains contextes de modèle. Cela peut interférer avec le comportement attendu de la fonctionnalité SFINAE où la substitution est supposée échouer en raison de l’inaccessibilité d’un nom. Cette situation peut entraîner un incident ou un comportement inattendu au moment de l’exécution en raison de l’appel par le compilateur de la surcharge incorrecte de l’opérateur. Dans Visual Studio 2017, une erreur de compilateur est générée. L’erreur spécifique peut varier, mais, en général, il s’agit de « C2672 fonction correspondante surchargée introuvable ». Le code suivant se compile dans Visual Studio 2015, mais génère une erreur dans Visual Studio 2017 :

```cpp
#include <type_traits>

template <class T> class S {
    typedef typename T type;
};

template <class T, std::enable_if<std::is_integral<typename S<T>::type>::value, T> * = 0>
bool f(T x);

int main()
{
    f(10); // C2672: No matching overloaded function found.
}
```

### <a name="missing-template-argument-lists"></a>Listes d’arguments de modèle manquantes

Dans Visual Studio 2015 et versions antérieures, le compilateur ne diagnostiquait pas les listes d’arguments de modèle manquantes quand le modèle apparaissait dans une liste de paramètres de modèle (par exemple, dans le cadre d’un argument de modèle par défaut ou d’un paramètre de modèle sans type). Cela peut entraîner un comportement imprévisible, y compris des pannes du compilateur ou un comportement inattendu au moment de l’exécution. Le code suivant se compile dans Visual Studio 2015, mais génère une erreur dans Visual Studio 2017 :

```cpp
template <class T> class ListNode;
template <class T> using ListNodeMember = ListNode<T> T::*;
template <class T, ListNodeMember M> class ListHead; // C2955: 'ListNodeMember': use of alias
                                                     // template requires template argument list

// correct:  template <class T, ListNodeMember<T> M> class ListHead;
```

### <a name="expression-sfinae"></a>Fonctionnalité SFINAE pour les expressions

Pour prendre en charge la fonctionnalité SFINAE pour les expressions, le compilateur analyse maintenant les arguments decltype quand les modèles sont déclarés et non instanciés. Ainsi, si une spécialisation non dépendante est trouvée dans l’argument decltype, elle n’est pas reportée à l’instanciation et est traitée immédiatement, et toute erreur résultante est diagnostiquée à ce moment-là.

L’exemple suivant montre une erreur de compilateur de ce type générée au moment de la déclaration :

```cpp
#include <utility>
template <class T, class ReturnT, class... ArgsT>
class IsCallable
{
public:
    struct BadType {};

    template <class U>
    static decltype(std::declval<T>()(std::declval<ArgsT>()...)) Test(int); //C2064. Should be declval<U>

    template <class U>
    static BadType Test(...);

    static constexpr bool value = std::is_convertible<decltype(Test<T>(0)), ReturnT>::value;
};

constexpr bool test1 = IsCallable<int(), int>::value;
static_assert(test1, "PASS1");
constexpr bool test2 = !IsCallable<int*, int>::value;
static_assert(test2, "PASS2");
```

### <a name="classes-declared-in-anonymous-namespaces"></a>Classes déclarées dans des espaces de noms anonymes

Selon la norme C++, une classe déclarée dans un espace de noms anonyme a une liaison interne et, par conséquent, ne peut pas être exportée. Dans Visual Studio 2015 et versions antérieures, cette règle n’était pas appliquée. Dans Visual Studio 2017, la règle est partiellement appliquée. L’exemple suivant génère cette erreur dans Visual Studio 2017 : « erreur C2201 : const anonymous namespace::S1::vftable doit avoir une liaison externe afin d’être exporté/importé. »

```cpp
struct __declspec(dllexport) S1 { virtual void f() {} }; //C2201
```

### <a name="default-initializers-for-value-class-members-ccli"></a>Initialiseurs par défaut pour les membres de classe value (C++/CLI)

Dans Visual Studio 2015 et antérieur, le compilateur autorisait (mais ignorait) un initialiseur de membre par défaut pour un membre d’une classe value. L’initialisation par défaut d’une classe value initialise systématiquement les membres à zéro ; un constructeur par défaut n’est pas autorisé. Dans Visual Studio 2017, les initialiseurs de membres par défaut déclenchent une erreur de compilateur, comme illustré dans cet exemple :

```cpp
value struct V
{
    int i = 0; // error C3446: 'V::i': a default member initializer
               // is not allowed for a member of a value class
};
```

### <a name="default-indexers-ccli"></a>Indexeurs par défaut (C++/CLI)

Dans Visual Studio 2015 et antérieur, le compilateur identifiait à tort une propriété par défaut en tant qu’indexeur par défaut dans certaines circonstances. Il était possible de contourner le problème en utilisant l’identificateur `default` pour accéder à la propriété. La solution de contournement elle-même est devenue problématique dès que `default` a été introduit comme mot clé dans C++11. Ainsi, dans Visual Studio 2017, les bogues qui nécessitaient la solution de contournement ont été corrigés, et le compilateur génère maintenant une erreur quand l’utilisateur recourt à `default` pour accéder à la propriété par défaut d’une classe.

```cpp
//class1.cs

using System.Reflection;
using System.Runtime.InteropServices;

namespace ClassLibrary1
{
    [DefaultMember("Value")]
    public class Class1
    {
        public int Value
        {
            // using attribute on the return type triggers the compiler bug
            [return: MarshalAs(UnmanagedType.I4)]
            get;
        }
    }
    [DefaultMember("Value")]
    public class Class2
    {
        public int Value
        {
            get;
        }
    }
}

// code.cpp
#using "class1.dll"

void f(ClassLibrary1::Class1 ^r1, ClassLibrary1::Class2 ^r2)
{
       r1->Value; // error
       r1->default;
       r2->Value;
       r2->default; // error
}
```

Dans Visual Studio 2017, vous pouvez accéder aux deux propriétés Value par leur nom :

```cpp
#using "class1.dll"

void f(ClassLibrary1::Class1 ^r1, ClassLibrary1::Class2 ^r2)
{
       r1->Value;
       r2->Value;
}
```

## <a name="update_153"></a> Correctifs de bogues dans Visual Studio 2017 version 15.3

### <a name="calls-to-deleted-member-templates"></a>Appels à des modèles membres supprimés

Dans les versions précédentes de Visual Studio, le compilateur ne parvenait pas dans certains cas à émettre une erreur pour les appels incorrects à un modèle membre supprimé qui pouvaient éventuellement provoquer des incidents lors de l’exécution. Le code suivant génère désormais l’erreur C2280, « 'int S\<int>::f\<int>(void)' : tentative de référencement d’une fonction supprimée » :

```cpp
template<typename T>
struct S {
   template<typename U> static int f() = delete;
};

void g()
{
   decltype(S<int>::f<int>()) i; // this should fail
}
```

Pour corriger cette erreur, déclarez i comme `int`.

### <a name="pre-condition-checks-for-type-traits"></a>Vérifications de conditions préalables pour les traits de type

Visual Studio 2017 version 15.3 améliore les vérifications de conditions préalables pour les traits de type afin de suivre plus strictement la norme. Une telle vérification doit être affectée. Le code suivant génère l’erreur C2139 dans Visual Studio 2017 version 15.3 :

```cpp
struct S;
enum E;

static_assert(!__is_assignable(S, S), "fail"); // C2139 in 15.3
static_assert(__is_convertible_to(E, E), "fail"); // C2139 in 15.3
```

### <a name="new-compiler-warning-and-runtime-checks-on-native-to-managed-marshaling"></a>Nouvel avertissement du compilateur et nouvelles vérifications à l’exécution sur du marshaling de fonctions natives à managées

L’appel des fonctions managées aux fonctions natives nécessite un marshaling. Le CLR exécute le marshaling, mais il ne comprend pas la sémantique C++. Si vous passez un objet natif par valeur, le CLR appelle le constructeur de copie de l’objet ou utilise BitBlt, ce qui peut provoquer un comportement non défini lors de l’exécution.

Désormais, le compilateur émet un avertissement s’il peut savoir au moment de la compilation qu’un objet natif avec un constructeur de copie supprimé est transmis entre les limites native et managée par valeur. Pour les cas où le compilateur ne sait rien au moment de la compilation, il injecte une vérification à l’exécution afin que le programme appelle `std::terminate` immédiatement dès qu’un marshaling incorrect se produit. Dans Visual Studio 2017 version 15.3, le code suivant génère l’avertissement C4606, « 'A' : le passage d’un argument par valeur à travers une frontière native/managée nécessite un constructeur de copie valide. Sinon, le comportement au moment de l’exécution est non défini. »

```cpp
class A
{
public:
   A() : p_(new int) {}
   ~A() { delete p_; }

   A(A const &) = delete;
   A(A &&rhs) {
   p_ = rhs.p_;
}

private:
   int *p_;
};

#pragma unmanaged

void f(A a)
{
}

#pragma managed

int main()
{
    f(A()); // This call from managed to native requires marshalling. The CLR doesn't understand C++ and uses BitBlt, which results in a double-free later.
}
```

Pour corriger cette erreur, supprimez la directive `#pragma managed` pour marquer l’appelant comme natif et éviter le marshaling.

### <a name="experimental-api-warning-for-winrt"></a>Avertissement d’API expérimentale pour WinRT

Les API WinRT publiées pour l’expérimentation et les commentaires sont décorées avec `Windows.Foundation.Metadata.ExperimentalAttribute`. Dans Visual Studio 2017 version 15.3, le compilateur génère l’avertissement C4698 quand il rencontre l’attribut. Certaines API dans les versions précédentes du SDK Windows ont déjà été décorées avec l’attribut et les appels à ces API déclenchent cet avertissement du compilateur. L’attribut est supprimé de tous les types fournis dans les SDK Windows plus récents mais, si vous utilisez un SDK plus ancien, vous devez supprimer ces avertissements pour tous les appels aux types fournis.

Le code suivant génère l’avertissement C4698 : « 'Windows::Storage::IApplicationDataStatics2::GetForUserAsync' est utilisé à des fins d’évaluation uniquement. Il sera peut-être changé ou supprimé au cours des prochaines mises à jour. » :

```cpp
Windows::Storage::IApplicationDataStatics2::GetForUserAsync(); //C4698
```

Pour désactiver l’avertissement, ajoutez un #pragma :

```cpp
#pragma warning(push)
#pragma warning(disable:4698)

Windows::Storage::IApplicationDataStatics2::GetForUserAsync();

#pragma warning(pop)
```

### <a name="out-of-line-definition-of-a-template-member-function"></a>Définition hors ligne d’une fonction membre de modèle

Visual Studio 2017 version 15.3 génère une erreur quand elle rencontre une définition hors ligne d’une fonction membre de modèle qui n’a pas été déclarée dans la classe. Le code suivant génère désormais l’erreur C2039 : 'f' : n’est pas un membre de 'S' :

```cpp
struct S {};

template <typename T>
void S::f(T t) {} //C2039: 'f': is not a member of 'S'
```

Pour corriger cette erreur, ajoutez une déclaration à la classe :

```cpp
struct S {
    template <typename T>
    void f(T t);
};
template <typename T>
void S::f(T t) {}
```

### <a name="attempting-to-take-the-address-of-this-pointer"></a>Tentative de prendre l’adresse du pointeur 'this'

En C++, `this` est une prvalue de pointeur de type vers X. Vous ne pouvez pas prendre l’adresse de `this` ni la lier à une référence lvalue. Dans les versions précédentes de Visual Studio, le compilateur vous permettait de contourner cette restriction en effectuant un cast. Dans Visual Studio 2017 version 15.3, le compilateur génère l’erreur C2664.

### <a name="conversion-to-an-inaccessible-base-class"></a>Conversion vers une classe de base inaccessible

Visual Studio 2017 version 15.3 génère une erreur quand vous essayez de convertir un type en une classe de base qui n’est pas accessible. Le compilateur génère désormais « erreur C2243 : 'cast de type' : la conversion de 'D *' en 'B *' existe, mais n’est pas accessible ». Le code suivant est incorrect et peut éventuellement provoquer un incident lors de l’exécution. Le compilateur génère désormais l’erreur C2243 quand il rencontre un code tel que le suivant :

```cpp
#include <memory>

class B { };
class D : B { }; // C2243. should be public B { };

void f()
{
   std::unique_ptr<B>(new D());
}
```

### <a name="default-arguments-are-not-allowed-on-out-of-line-definitions-of-member-functions"></a>Les arguments par défaut ne sont pas autorisés sur les définitions hors ligne des fonctions membres

Les arguments par défaut ne sont pas autorisés sur les définitions hors ligne des fonctions membres dans les classes de modèles. Le compilateur émet un avertissement sous **/permissive** et une erreur matérielle sous **/permissive-**.

Dans les versions précédentes de Visual Studio, le code incorrect suivant peut entraîner un incident lors de l’exécution. Visual Studio 2017 version 15.3 génère l’avertissement C5034 : 'A\<T>::f' : une définition hors ligne d’un membre d’un modèle de classe ne peut pas avoir d’arguments par défaut :

```cpp
template <typename T>
struct A {
    T f(T t, bool b = false);
};

template <typename T>
T A<T>::f(T t, bool b = false) // C5034
{
    // ...
}
```

Pour corriger cette erreur, supprimez l’argument par défaut `= false`.

### <a name="use-of-offsetof-with-compound-member-designator"></a>Utilisation d’offsetof avec désignateur de membre composé

Dans Visual Studio 2017 version 15.3, l’utilisation de `offsetof(T, m)` où *m* est un « désignateur de membre composé » aboutit à un avertissement quand vous compilez avec l’option **/Wall**. Le code suivant est incorrect et peut éventuellement provoquer un incident lors de l’exécution. Visual Studio 2017 version 15.3 génère « l’avertissement C4841 : extension non standard utilisée : désignateur de membre composé dans offsetof » :

```cpp
struct A {
   int arr[10];
};

// warning C4841: non-standard extension used: compound member designator in offsetof
constexpr auto off = offsetof(A, arr[2]);
```

Pour corriger le code, désactivez l’avertissement avec un pragma ou modifiez le code pour ne pas utiliser `offsetof` :

```cpp
#pragma warning(push)
#pragma warning(disable: 4841)
constexpr auto off = offsetof(A, arr[2]);
#pragma warning(pop)
```

### <a name="using-offsetof-with-static-data-member-or-member-function"></a>Utilisation d’offsetof avec des données membres static ou une fonction membre

Dans Visual Studio 2017 version 15.3, l’utilisation de `offsetof(T, m)` où *m* fait référence à des données membres static ou une fonction membre aboutit à une erreur. Le code suivant génère « erreur C4597 : comportement non défini : offsetof appliqué à la fonction membre « foo » » et « erreur C4597 : comportement non défini : offsetof appliqué à des données membres static 'bar' » :

```cpp
#include <cstddef>

struct A {
   int foo() { return 10; }
   static constexpr int bar = 0;
};

constexpr auto off = offsetof(A, foo);
constexpr auto off2 = offsetof(A, bar);
```

Ce code est incorrect et peut éventuellement provoquer un incident lors de l’exécution. Pour corriger cette erreur, modifiez le code pour ne plus appeler un comportement non défini. Il s’agit de code non portable qui n’est pas autorisé par la norme C++.

### <a name="declspec"></a> Nouvel avertissement sur les attributs declspec

Dans Visual Studio 2017 version 15.3, le compilateur n’ignore plus les attributs si `__declspec(...)` est appliqué avant une spécification de liaison `extern "C"` externe. Avant, le compilateur ignorait l’attribut, ce qui pouvait avoir des implications lors de l’exécution. Quand les options **/Wall** et **/WX** sont définies, le code suivant génère « avertissement C4768 : les attributs __declspec avant la spécification de liaison sont ignorés » :

```cpp
__declspec(noinline) extern "C" HRESULT __stdcall //C4768
```

Pour corriger l’avertissement, placez 'C' externe en premier :

```cpp
extern "C" __declspec(noinline) HRESULT __stdcall
```

Cet avertissement est désactivé par défaut dans la version  15.3 (mais activé par défaut dans la version 15.5) et impacte uniquement le code compilé avec **/Wall** **/WX**.

### <a name="decltype-and-calls-to-deleted-destructors"></a>decltype et appels à des destructeurs supprimés

Dans les versions précédentes de Visual Studio, le compilateur ne détectait pas quand un appel à un destructeur supprimé se produisait dans le contexte de l’expression associée à « decltype ». Dans Visual Studio 2017 version 15.3, le code suivant génère « erreur C2280 : 'A\<T>::~A(void)' : tentative de référencement d’une fonction supprimée » :

```cpp
template<typename T>
struct A
{
   ~A() = delete;
};

template<typename T>
auto f() -> A<T>;

template<typename T>
auto g(T) -> decltype((f<T>()));

void h()
{
   g(42);
}
```

### <a name="uninitialized-const-variables"></a>Variables const non initialisées

La version Visual Studio 2017 RTW avait une régression dans laquelle le compilateur C++ n’émettait pas de diagnostic si une variable 'const' n’était pas initialisée. Cette régression a été corrigée dans Visual Studio 2017 version 15.3. Le code suivant génère désormais « avertissement C4132 : 'Value' : un objet const doit être initialisé » :

```cpp
const int Value; //C4132
```

Pour corriger cette erreur, attribuez une valeur à `Value`.

### <a name="empty-declarations"></a>Déclarations vides

Visual Studio 2017 version 15.3 émet désormais un avertissement relatif aux déclarations vides pour tous les types, non seulement les types intégrés. Le code suivant génère désormais un avertissement C4091 de niveau 2 pour les quatre déclarations :

```cpp
struct A {};
template <typename> struct B {};
enum C { c1, c2, c3 };

int;    // warning C4091 : '' : ignored on left of 'int' when no variable is declared
A;      // warning C4091 : '' : ignored on left of 'main::A' when no variable is declared
B<int>; // warning C4091 : '' : ignored on left of 'B<int>' when no variable is declared
C;      // warning C4091 : '' : ignored on left of 'C' when no variable is declared
```

Pour supprimer les avertissements, il vous suffit de commenter ou de supprimer les déclarations vides. Dans les cas où l’objet sans nom doit avoir un effet secondaire (par exemple, RAII), vous devez lui affecter un nom.

L’avertissement est exclu sous **/Wv:18** et est activé par défaut sous le niveau d’avertissement W2.

### <a name="stdisconvertible-for-array-types"></a>std::is_convertible pour les types tableau

Les versions précédentes du compilateur ont donné des résultats incorrects avec [std::is_convertible](standard-library/is-convertible-class.md) pour les types tableau. Cela obligeait les auteurs de bibliothèques à particulariser le compilateur Microsoft Visual C++ lors de l’utilisation du trait de type `std::is_convertible<...>`. Dans l’exemple suivant, les assertions statiques passent dans les versions antérieures de Visual Studio, mais échouent dans Visual Studio 2017 version 15.3 :

```cpp
#include <type_traits>

using Array = char[1];

static_assert(std::is_convertible<Array, Array>::value);
static_assert(std::is_convertible<const Array, const Array>::value, "");
static_assert(std::is_convertible<Array&, Array>::value, "");
static_assert(std::is_convertible<Array, Array&>::value, "");
```

`std::is_convertible<From, To>` est calculé en vérifiant si une définition de fonction imaginaire est correcte :

```cpp
   To test() { return std::declval<From>(); }
```

### <a name="private-destructors-and-stdisconstructible"></a>Les destructeurs privés et std::is_constructible

Les versions précédentes du compilateur ignoraient si un destructeur était privé lors de la détermination du résultat de [std::is_constructible](standard-library/is-constructible-class.md). Il en tient compte désormais. Dans l’exemple suivant, les assertions statiques passent dans les versions antérieures de Visual Studio, mais échouent dans Visual Studio 2017 version 15.3 :

```cpp
#include <type_traits>

class PrivateDtor {
   PrivateDtor(int) { }
private:
   ~PrivateDtor() { }
};

// This assertion used to succeed. It now correctly fails.
static_assert(std::is_constructible<PrivateDtor, int>::value);
```

Les destructeurs privés entraînent la non-constructibilité d’un type. `std::is_constructible<T, Args...>` est calculé comme si la déclaration suivante était écrite :

```cpp
   T obj(std::declval<Args>()...)
```

Cet appel implique un appel de destructeur.

### <a name="c2668-ambiguous-overload-resolution"></a>C2668 : Résolution de surcharge ambiguë

Parfois, les versions précédentes du compilateur ne parvenaient pas à détecter une ambiguïté lors de la découverte de plusieurs candidats par le biais simultanément des déclarations et des recherches dépendantes d’arguments. Cela pouvait conduire à choisir une surcharge incorrecte et entraîner un comportement inattendu au moment de l’exécution. Dans l’exemple suivant, Visual Studio 2017 version 15.3 déclenche correctement C2668, 'f' : appel ambigu à une fonction surchargée :

```cpp
namespace N {
   template<class T>
   void f(T&, T&);

   template<class T>
   void f();
}

template<class T>
void f(T&, T&);

struct S {};
void f()
{
   using N::f;

   S s1, s2;
   f(s1, s2); // C2668
}
```

Pour corriger le code, supprimez l’instruction using `N::f` si vous souhaitez appeler `::f()`.

### <a name="c2660-local-function-declarations-and-argument-dependent-lookup"></a>C2660 : Déclarations de fonction locale et recherche dépendante d’argument

Les déclarations de fonction locale masquent la déclaration de fonction dans la portée englobante et désactivent la recherche dépendante d’argument. Pourtant, les versions précédentes du compilateur effectuaient une recherche dépendante d’argument dans ce cas, conduisant éventuellement à choisir une surcharge incorrecte et entraînant un comportement inattendu au moment de l’exécution. En règle générale, l’erreur est due à une signature incorrecte de la déclaration de fonction locale. Dans l’exemple suivant, Visual Studio 2017 version 15.3 déclenche correctement C2660, 'f' : la fonction n’accepte pas 2 arguments :

```cpp
struct S {};
void f(S, int);

void g()
{
   void f(S); // C2660 'f': function does not take 2 arguments:
   // or void f(S, int);
   S s;
   f(s, 0);
}
```

Pour résoudre le problème, changez la signature `f(S)` ou supprimez-la.

### <a name="c5038-order-of-initialization-in-initializer-lists"></a>C5038 : Ordre d’initialisation dans les listes d’initialiseurs

Les membres de classe sont initialisés dans l’ordre suivant lequel ils sont déclarés, et non selon celui de leur apparition dans les listes d’initialiseurs. Les versions précédentes du compilateur n’avertissaient pas lorsque l’ordre de la liste d’initialiseurs était différent de celui des déclarations. Cela pouvait aboutir à un comportement d’exécution non défini si l’initialisation d’un membre dépendait d’un autre membre dans la liste déjà en cours d’initialisation. Dans l’exemple suivant, Visual Studio 2017 version 15.3 (avec **/Wall**) génère "l’avertissement C5038 : le membre de données 'A::y' sera initialisé après le membre de données 'A::x'" :

```cpp
struct A
{
    A(int a) : y(a), x(y) {} // Initialized in reverse, y reused
    int x;
    int y;
};
```

Pour résoudre le problème, réorganisez la liste d’initialiseurs afin d’avoir le même ordre que dans les déclarations. Un avertissement similaire est déclenché lorsqu’un ou les deux initialiseurs se réfèrent aux membres de classe de base.

Notez que l’avertissement est désactivé par défaut et affecte uniquement le code compilé avec **/Wall**.

## <a name="update_155"></a> Correctifs de bogues et autres changements du comportement dans Visual Studio 2017 version 15.5

### <a name="partial-ordering-change"></a>Changement de classement partiel

Le compilateur rejette maintenant le code suivant et génère le message d’erreur approprié :

```cpp
template<typename... T>
int f(T* ...)
{
    return 1;
}

template<typename T>
int f(const T&)
{
    return 2;
}

int main()
{
    int i = 0;
    f(&i);    // C2668
}
```

```Output
t161.cpp
t161.cpp(16): error C2668: 'f': ambiguous call to overloaded function
t161.cpp(8): note: could be 'int f<int*>(const T &)'
        with
        [
            T=int*
        ]
t161.cpp(2): note: or       'int f<int>(int*)'
t161.cpp(16): note: while trying to match the argument list '(int*)'
```

Dans l’exemple ci-dessus, le problème provient de l’utilisation de fonctions de deux types différents (const/non-const et pack/non-pack). Pour éviter l’erreur du compilateur, utilisez des fonctions d’un même type. Le compilateur pourra ainsi classer les fonctions sans ambiguïté.

```cpp
template<typename... T>
int f(T* ...)
{
    return 1;
}

template<typename T>
int f(T&)
{
    return 2;
}

int main()
{
    int i = 0;
    f(&i);
}
```

### <a name="exception-handlers"></a>Gestionnaires d’exceptions

Les gestionnaires de référence au type tableau ou fonction ne sont plus mis en correspondance pour les objets exception. Le compilateur applique maintenant cette règle correctement et déclenche un avertissement de niveau 4. De plus, il ne met plus en correspondance un gestionnaire de `char*` ou `wchar_t*` avec un littéral de chaîne quand **/Zc:strictStrings** est utilisé.

```cpp
int main()
{
    try {
        throw "";
    }
    catch (int (&)[1]) {} // C4843 (This should always be dead code.)
    catch (void (&)()) {} // C4843 (This should always be dead code.)
    catch (char*) {} // This should not be a match under /Zc:strictStrings
}
```

```Output
warning C4843: 'int (&)[1]': An exception handler of reference to array or function type is unreachable, use 'int*' instead
warning C4843: 'void (__cdecl &)(void)': An exception handler of reference to array or function type is unreachable, use 'void (__cdecl*)(void)' instead
```

Le code suivant permet d’éviter cette erreur :

```cpp
catch (int (*)[1]) {}
```

### <a name="tr1"></a>L’espace de noms std::tr1 est déprécié

L’espace de noms `std::tr1` non standard est désormais marqué comme déprécié dans les deux modes C++14 et C++17. Dans Visual Studio 2017 version 15.5, le code suivant génère l’erreur C4996 :

```cpp
#include <functional>
#include <iostream>
using namespace std;

int main() {
    std::tr1::function<int (int, int)> f = std::plus<int>(); //C4996
    cout << f(3, 5) << std::endl;
    f = std::multiplies<int>();
    cout << f(3, 5) << std::endl;
}
```

```Output
warning C4996: 'std::tr1': warning STL4002: The non-Standard std::tr1 namespace and TR1-only machinery are deprecated and will be REMOVED. You can define _SILENCE_TR1_NAMESPACE_DEPRECATION_WARNING to acknowledge that you have received this warning.
```

Pour corriger cette erreur, supprimez la référence à l’espace de noms `tr1` :

```cpp
#include <functional>
#include <iostream>
using namespace std;

int main() {
    std::function<int (int, int)> f = std::plus<int>();
    cout << f(3, 5) << std::endl;
    f = std::multiplies<int>();
    cout << f(3, 5) << std::endl;
}
```

### <a name="annex_d"></a>Les fonctionnalités de la bibliothèque standard dans l’annexe D sont marquées comme dépréciées

Quand le commutateur de compilateur en mode **/std:c++17** est défini, presque toutes les fonctionnalités de la bibliothèque standard listées dans l’annexe D sont marquées comme dépréciées.

Dans Visual Studio 2017 version 15.5, le code suivant génère l’erreur C4996 :

```cpp
#include <iterator>

class MyIter : public std::iterator<std::random_access_iterator_tag, int> {
public:
    // ... other members ...
};

#include <type_traits>

static_assert(std::is_same<MyIter::pointer, int*>::value, "BOOM");
```

```Output
warning C4996: 'std::iterator<std::random_access_iterator_tag,int,ptrdiff_t,_Ty*,_Ty &>::pointer': warning STL4015: The std::iterator class template (used as a base class to provide typedefs) is deprecated in C++17. (The <iterator> header is NOT deprecated.) The C++ Standard has never required user-defined iterators to derive from std::iterator. To fix this warning, stop deriving from std::iterator and start providing publicly accessible typedefs named iterator_category, value_type, difference_type, pointer, and reference. Note that value_type is required to be non-const, even for constant iterators. You can define _SILENCE_CXX17_ITERATOR_BASE_CLASS_DEPRECATION_WARNING or _SILENCE_ALL_CXX17_DEPRECATION_WARNINGS to acknowledge that you have received this warning.
```

Pour corriger cette erreur, suivez les instructions données dans le texte d’avertissement, comme illustré dans le code suivant :

```cpp
#include <iterator>

class MyIter {
public:
    typedef std::random_access_iterator_tag iterator_category;
    typedef int value_type;
    typedef ptrdiff_t difference_type;
    typedef int* pointer;
    typedef int& reference;

    // ... other members ...
};

#include <type_traits>

static_assert(std::is_same<MyIter::pointer, int*>::value, "BOOM");
```

### <a name="unreferenced-local-variables"></a>Variables locales non référencées

Dans Visual Studio 15.5, l’avertissement C4189 est affiché dans plus de cas, comme indiqué dans le code suivant :

```cpp
void f() {
    char s[2] = {0}; // C4189. Either use the variable or remove it.
}
```

```Output
warning C4189: 's': local variable is initialized but not referenced
```

Pour corriger cette erreur, supprimez la variable inutilisée.

### <a name="single-line-comments"></a>Commentaires sur une seule ligne

Dans Visual Studio 2017 version 15.5, les avertissements C4001 et C4179 ne sont plus générés par le compilateur C. Auparavant, ils étaient uniquement générés quand le commutateur du compilateur **/Za** était défini.  Ces avertissements ne sont plus utiles, car les commentaires sur une seule ligne sont intégrés à la norme C depuis la version C99.

```cpp
/* C only */
#pragma warning(disable:4001) //C4619
#pragma warning(disable:4179)
// single line comment
//* single line comment */
```

```Output
warning C4619: #pragma warning: there is no warning number '4001'
```

Si le code n’a pas besoin d’offrir une compatibilité descendante, vous pouvez éviter la génération des avertissements en supprimant C4001 et C4179. Si le code doit offrir une compatibilité descendante, supprimez uniquement C4619.

```C

/* C only */

#pragma warning(disable:4619)
#pragma warning(disable:4001)
#pragma warning(disable:4179)

// single line comment
/* single line comment */
```

### <a name="declspec-attributes-with-extern-c-linkage"></a>Attributs __declspec avec une liaison extern "C"

Dans les versions antérieures de Visual Studio, le compilateur ignorait les attributs `__declspec(...)` quand `__declspec(...)` était appliqué avant la spécification de la liaison `extern "C"`. Ce comportement provoquait la génération de code de façon inattendue pour l’utilisateur, avec un impact possible sur l’exécution. L’avertissement, ajouté dans Visual Studio 2017 version 15.3, était désactivé par défaut. Dans Visual Studio 2017 version 15.5, l’avertissement est activé par défaut.

```cpp
__declspec(noinline) extern "C" HRESULT __stdcall //C4768
```

```Output
warning C4768: __declspec attributes before linkage specification are ignored
```

Pour corriger cette erreur, ajoutez la spécification de liaison avant l’attribut __declspec :

```cpp
extern "C" __declspec(noinline) HRESULT __stdcall
```

Le nouvel avertissement C4768 ci-dessous est généré sur certains en-têtes Windows SDK fournis avec Visual Studio 2017 version 15.3 ou antérieure (par exemple, dans la version 10.0.15063.0, appelée RS2 SDK). Les versions ultérieures des en-têtes Windows SDK (en particulier, ShlObj.h et ShlObj_core.h) ont été corrigées pour ne plus générer cet avertissement. Si vous voyez cet avertissement généré par les en-têtes Windows SDK, effectuez les actions suivantes :

1. Installez le dernier Windows SDK, fourni avec Visual Studio 2017 version 15.5.

1. Désactivez l’avertissement pour l’élément #include de l’instruction d’en-tête Windows SDK :

```cpp
   #pragma warning (push)
   #pragma warning(disable:4768)
   #include <shlobj.h>
   #pragma warning (pop)
   ```

### <a name="extern_linkage"></a>Liaison extern constexpr

Dans les versions antérieures de Visual Studio, le compilateur retournait toujours une liaison interne pour la variable `constexpr`, même quand la variable était marquée comme `extern`. Dans Visual Studio 2017 version 15.5, un nouveau commutateur de compilateur (**/Zc:externConstexpr**) active le comportement correct de conformité aux normes. Cela deviendra le comportement par défaut.

```cpp
extern constexpr int x = 10;
```

```Output
error LNK2005: "int const x" already defined
```

Si un fichier d’en-tête contient une variable déclarée `extern constexpr`, la variable doit être marquée comme `__declspec(selectany)` pour permettre la combinaison correcte de ses déclarations dupliquées :

```cpp
extern constexpr __declspec(selectany) int x = 10;
```

### <a name="typeid-cant-be-used-on-incomplete-class-type"></a>typeid ne peut pas être utilisé sur un type de classe incomplet

Dans les versions antérieures de Visual Studio, le compilateur autorisait à tort le code suivant, ce qui pouvait produire des informations de type incorrectes. Dans Visual Studio 2017 version 15.5, le compilateur génère une erreur :

```cpp
#include <typeinfo>

struct S;

void f() { typeid(S); } //C2027 in 15.5
```

```Output
error C2027: use of undefined type 'S'
```

### <a name="stdisconvertible-target-type"></a>Type de cible std::is_convertible

`std::is_convertible` exige que le type de cible soit un type de retour valide. Dans les versions antérieures de Visual Studio, le compilateur autorisait à tort les types abstraits, ce qui pouvait entraîner une résolution de surcharge incorrecte et un comportement inattendu au moment de l’exécution.  Le code suivant génère désormais correctement l’erreur C2338 :

```cpp
#include <type_traits>

struct B { virtual ~B() = 0; };
struct D : public B { virtual ~D(); };

static_assert(std::is_convertible<D, B>::value, "fail"); // C2338 in 15.5
```

Pour éviter cette erreur, quand vous utilisez `is_convertible`, vous devez comparer les types de pointeur, car une comparaison de type non pointeur peut échouer si un type est abstrait :

```cpp
#include <type_traits>

struct B { virtual ~B() = 0; };
struct D : public B { virtual ~D(); };

static_assert(std::is_convertible<D *, B *>::value, "fail");
```

### <a name="noexcept_removal"></a> Suppression des spécifications d’exceptions dynamiques et noexcept

Dans C++17, `throw()` est un alias de `noexcept`, les exceptions `throw(<type list>)` et `throw(...)` sont supprimées, et certains types peuvent inclure `noexcept`. Ces changements entraînent parfois des problèmes de compatibilité avec le code conforme à C++14 ou une version antérieure. Vous pouvez utiliser le commutateur **/Zc:noexceptTypes-** pour rétablir la version C++14 de `noexcept` si vous utilisez généralement le mode C++17. Cela vous permet de mettre à jour votre code source pour le rendre conforme à C++17 sans pour autant avoir à réécrire tout votre code `throw()`.

Avec le nouvel avertissement C5043, le compilateur diagnostique également maintenant davantage de spécifications d’exceptions incompatibles dans les déclarations en mode C++17 ou avec **/permissive-**.

Le code suivant génère les avertissements C5043 et C5040 dans Visual Studio 2017 version 15.5 quand le commutateur **/std:c++17** est défini :

```cpp
void f() throw(); // equivalent to void f() noexcept;
void f() {} // warning C5043
void g() throw(); // warning C5040

struct A {
    virtual void f() throw();
};

struct B : A {
    virtual void f() { } // error C2694
};
```

Pour éviter ces erreurs quand vous utilisez **/std:c++17**, ajoutez le commutateur **/Zc:noexceptTypes-** dans la ligne de commande ou bien mettez à jour votre code pour utiliser `noexcept`, comme illustré dans l’exemple suivant :

```cpp
void f() noexcept;
void f() noexcept { }
void g() noexcept(false);

struct A {
    virtual void f() noexcept;
};

struct B : A {
    virtual void f() noexcept { }
};
```

### <a name="inline-variables"></a>Variables inline

Les membres de données static constexpr sont désormais implicitement inline, ce qui signifie que leur déclaration dans une classe correspond maintenant à leur définition. L’utilisation d’une définition hors ligne pour un membre de données static constexpr est redondante et est donc maintenant dépréciée. Dans Visual Studio 2017 version 15.5, quand le commutateur **/std:c++17** est défini, le code suivant génère désormais l’avertissement C5041 *'size' : la définition hors ligne du membre de données statique constexpr n’est pas nécessaire et est dépréciée en C++17* :

```cpp
struct X {
    static constexpr int size = 3;
};
const int X::size; // C5041
```

### <a name="extern-c-declspec-warning-c4768-now-on-by-default"></a>L’avertissement C4768 extern "C" __declspec(...) est maintenant activé par défaut

L’avertissement, ajouté dans Visual Studio 2017 version 15.3, était désactivé par défaut. Dans Visual Studio 2017 version 15.5, il est activé par défaut. Pour plus d’informations, consultez [Nouvel avertissement sur les attributs declspec](#declspec).

### <a name="defaulted-functions-and-declspecnothrow"></a>Fonctions par défaut et __declspec(nothrow)

Auparavant, le compilateur autorisait la déclaration de fonctions par défaut à l’aide de `__declspec(nothrow)` quand les fonctions de base/membres correspondantes autorisaient les exceptions. Ce comportement non conforme à la norme C++ peut entraîner un comportement inattendu au moment de l’exécution. La norme exige que ces fonctions soient marquées comme supprimées en cas de non-correspondance d’une spécification d’exception.  En mode **/std:c++17**, le code suivant déclenche l’avertissement C2280 *Tentative de référencement d’une fonction supprimée. La fonction a été supprimée implicitement, car la spécification d’exception explicite est incompatible avec la spécification de déclaration implicite.*  :

```cpp
struct A {
    A& operator=(const A& other) { // No exception specification; this function may throw.
        ...
    }
};

struct B : public A {
    __declspec(nothrow) B& operator=(const B& other) = default;
};

int main()
{
    B b1, b2;
    b2 = b1; // error C2280
}
```

Pour corriger ce code, supprimez __declspec (nothrow) dans la fonction par défaut, ou supprimez `= default` et ajoutez une définition de la fonction et la gestion d’exceptions nécessaire :

```cpp
struct A {
    A& operator=(const A& other) {
        // ...
    }
};

struct B : public A {
    B& operator=(const B& other) = default;
};

int main()
{
    B b1, b2;
    b2 = b1;
}
```

### <a name="noexcept-and-partial-specializations"></a>noexcept et spécialisations partielles

Quand noexcept est utilisé dans le système de type, les spécialisations partielles pour la correspondance de certains types « pouvant être appelés » peuvent ne pas réussir à compiler ou choisir le modèle principal en raison d’une spécialisation partielle manquante pour les pointeurs de fonctions noexcept.

Dans ce cas de figure, vous devrez peut-être ajouter d’autres spécialisations partielles pour gérer les pointeurs de fonctions noexcept ainsi que les pointeurs noexcept de fonctions membres. Ces surcharges sont uniquement autorisées en mode **/std:c++17**. Si vous devez garantir la compatibilité descendante avec C++14 et que votre code est destiné à être utilisé par d’autres personnes, vous devez protéger ces nouvelles surcharges à l’intérieur de directives `#ifdef`. Si votre code fait partie d’un module autonome, au lieu d’utiliser des protections `#ifdef`, vous pouvez simplement compiler le code avec le commutateur **/Zc:noexceptTypes-**.

Le code suivant se compile correctement en mode **/std:c++14**, mais échoue en mode **/std:c++17** avec "l’erreur C2027 : utilisation du type non défini 'A\<T>'":

```cpp
template <typename T> struct A;

template <>
struct A<void(*)()>
{
    static const bool value = true;
};

template <typename T>
bool g(T t)
{
    return A<T>::value;
}

void f() noexcept {}

int main()
{
    return g(&f) ? 0 : 1; // C2027
}
```

Le code suivant se compile correctement en mode **/std:c++17**, car le compilateur choisit la nouvelle spécialisation partielle `A<void (*)() noexcept>` :

```cpp
template <typename T> struct A;

template <>
struct A<void(*)()>
{
    static const bool value = true;
};

template <>
struct A<void(*)() noexcept>
{
    static const bool value = true;
};

template <typename T>
bool g(T t)
{
    return A<T>::value;
}

void f() noexcept {}

int main()
{
    return g(&f) ? 0 : 1; // OK
}
```

## <a name="update_157"></a> Correctifs de bogues et autres changements du comportement dans Visual Studio 2017 version 15.7

### <a name="c17-default-argument-in-the-primary-class-template"></a>C++17 - Argument par défaut dans le modèle de classe primaire

Ce changement de comportement est une précondition à la spécification [P0091R3 - Déduction d’arguments de modèle pour les modèles de classe](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0091r3.html), qui sera entièrement prise en charge dans une future préversion de Visual Studio 2017 version 15.7.

Auparavant, le compilateur ignorait l’argument par défaut dans le modèle de classe primaire.

```cpp
template<typename T>
struct S {
    void f(int = 0);
};

template<typename T>
void S<T>::f(int = 0) {} // Re-definition necessary
```

Dans Visual Studio 2017 version 15.7, en mode **/std:c++17**, l’argument par défaut n’est pas ignoré :

```cpp
template<typename T>
struct S {
    void f(int = 0);
};

template<typename T>
void S<T>::f(int) {} // Default argument is used
```

### <a name="dependent-name-resolution"></a>Résolution de noms indépendante

Ce changement de comportement est une précondition à la spécification [P0091R3 - Déduction d’arguments de modèle pour les modèles de classe](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0091r3.html), qui sera entièrement prise en charge dans une future préversion de Visual Studio 2017 version 15.7.

Dans l’exemple suivant, le compilateur dans Visual Studio 15.6 et antérieur résout `D::type` en `B<T>::type` dans le modèle de classe primaire.

```cpp
template<typename T>
struct B {
    using type = T;
};

template<typename T>
struct D : B<T*> {
    using type = B<T*>::type;
};
```

Visual Studio 2017 version 15.7, en mode **/std:c++17**, nécessite le mot clé `typename` dans l’instruction `using` dans D. Sans `typename`, le compilateur génère l’avertissement C4346 : *'B<T\*>::type' : le nom dépendant n’est pas un type* et l’erreur C2061 : *erreur de syntaxe : identificateur 'type'* :

```cpp
template<typename T>
struct B {
    using type = T;
};

template<typename T>
struct D : B<T*> {
    using type = typename B<T*>::type;
};
```

### <a name="c17-nodiscard-attribute---warning-level-increase"></a>C++17 - Attribut [[nodiscard]] - élévation du niveau d’avertissement

Dans Visual Studio 2017 version 15.7, en mode **/std:c++17**, le niveau d’avertissement de C4834 (« abandon de la valeur de retour de la fonction ayant l’attribut 'nodiscard' ») passe de W3 à W1. Vous pouvez désactiver l’avertissement en effectuant un cast en `void` ou en passant **/wd:4834** au compilateur.

```cpp
[[nodiscard]] int f() { return 0; }

int main() {
    f(); // warning: discarding return value
         // of function with 'nodiscard'
}
```

### <a name="variadic-template-constructor-base-class-initialization-list"></a>Liste d’initialisation de classe de base du constructeur de modèle variadique

Dans les éditions précédentes de Visual Studio, une liste d’initialisation de classe de base du constructeur de modèle variadique dont des arguments de modèle étaient manquants était autorisée par erreur sans signaler d’erreur. Dans Visual Studio 2017 version 15.7, une erreur de compilateur est générée.

L’exemple de code suivant dans Visual Studio 2017 version 15.7 déclenche *l’erreur C2614: D\<int> : initialisation de membre non conforme : 'B' n’est pas une base ni un membre*

```cpp
template<typename T>
struct B {};

template<typename T>
struct D : B<T>
{

    template<typename ...C>
    D() : B() {} // C2614. Missing template arguments to B.
};

D<int> d;
```

Pour corriger l’erreur, remplacez l’expression B() par B\<T>().

### <a name="constexpr-aggregate-initialization"></a>Initialisation d’agrégats constexpr

Les versions précédentes du compilateur C++ traitaient de façon incorrecte l’initialisation d’agrégats constexpr ; elles acceptaient du code non valide dans lequel aggregate-init-list comportait trop d’éléments et générait un codegen incorrect. Le code suivant en est un exemple :

```cpp
#include <array>
struct X {
    unsigned short a;
    unsigned char b;
};

int main() {
    constexpr std::array<X, 2> xs = {
        { 1, 2 },
        { 3, 4 }
    };
    return 0;
}
```

Dans Visual Studio 2017 version 15.7 mise à jour 3 et ultérieures, l’exemple précédent génère désormais l’erreur *C2078 initialiseurs trop nombreux*. L’exemple de code suivant montre corriger le code. Lors de l’initialisation d’un `std::array` avec nested brace-init-lists, attribuez au tableau interne son propre braced-list :

```cpp
#include <array>
struct X {
    unsigned short a;
    unsigned char b;
};

int main() {
    constexpr std::array<X, 2> xs = {{ // note double braces
        { 1, 2 },
        { 3, 4 }
    }}; // note double braces
    return 0;
}
```

## <a name="update_158"></a> Correctifs de bogues et changements de comportement dans Visual Studio 2017 version 15.8

Les modifications apportées au compilateur dans Visual Studio 2017 version 15.8 appartiennent toutes à la catégorie des correctifs de bogues et des changements de comportement. Elles sont répertoriées ci-dessous :

### <a name="typename-on-unqualified-identifiers"></a>typename sur les identificateurs non qualifiés

Dans le mode [/permissive-](build/reference/permissive-standards-conformance.md), les mots clés `typename` parasites sur les identificateurs non qualifiés dans les définitions de modèle d’alias ne sont plus acceptés par le compilateur. Le code suivant génère désormais l’erreur C7511 *'T' : le mot clé 'typename' doit être suivi d’un nom qualifié* :

```cpp
template <typename T>
using  X = typename T;
```

Pour corriger cette erreur, remplacez simplement la deuxième ligne par `using  X = T;`.

### <a name="declspec-on-right-side-of-alias-template-definitions"></a>__declspec() dans la partie droite des définitions de modèle d’alias

[__declspec](cpp/declspec.md) n’est plus autorisé dans la partie droite d’une définition de modèle d’alias. Même si cette décision a déjà été acceptée par le compilateur, elle a été complètement ignorée. Aucun avertissement de dépréciation n’était donc généré quand l’alias était utilisé.

Vous pouvez utiliser l’attribut C++ standard [\[\[deprecated\]\]](cpp/attributes.md) à la place. Celui-ci sera pris en compte à compter de Visual Studio 2017 version 15.6. Le code suivant génère désormais l’erreur C2760 *erreur de syntaxe : jeton inattendu '__declspec', attendu 'type specifier'* :

```cpp
template <typename T>
using X = __declspec(deprecated("msg")) T;
```

Pour corriger cette erreur, remplacez le code par ce qui suit (attribut placé avant le signe '=' de la définition d’alias) :

```cpp
template <typename T>
using  X [[deprecated("msg")]] = T;
```

### <a name="two-phase-name-lookup-diagnostics"></a>Diagnostics de la recherche de nom en deux phases

La recherche de nom en deux phases nécessite que les noms non dépendants utilisés dans les corps de modèle soient visibles par le modèle au moment de la définition. Avant, le compilateur Microsoft C++ ne procédait pas à la recherche d’un nom introuvable avant les phases d’instanciation. Il exige désormais que les noms non dépendants soient liés dans le corps du modèle.

Cela peut notamment se manifester par une recherche dans les classes de base dépendantes. Le compilateur autorisait précédemment l’utilisation de noms définis dans des classes de base dépendantes, car ils faisaient l’objet d’une recherche au moment de l’instanciation (une fois tous les types résolus). Ce code est désormais traité comme une erreur. Dans ces cas, vous pouvez forcer la recherche de la variable au moment de l’instanciation en la qualifiant avec le type de classe de base ou en la rendant dépendante, par exemple en ajoutant un pointeur `this->`.

Dans le mode **/permissive-**, le code suivant génère désormais l’erreur C3861 *'base_value' : identificateur introuvable* :

```cpp
template <class T>
struct Base {
    int base_value = 42;
};

template <class T>
struct S : Base<T> {
    int f() {
        return base_value;
    }
};
```

Pour corriger cette erreur, remplacez l’instruction `return` par `return this->base_value;`.

**Remarque :** dans la bibliothèque python Boost, il a existé pendant longtemps une solution de contournement spécifique à MSVC pour une déclaration anticipée de modèle dans [unwind_type.hpp](https://github.com/boostorg/python/blame/develop/include/boost/python/detail/unwind_type.hpp). Sous le mode [/permissive-](build/reference/permissive-standards-conformance.md) à partir de Visual Studio 2017 version 15.8 (_MSC_VER=1915), le compilateur MSVC effectue la recherche de nom dépendante d’un argument (ADL) correctement et est cohérent avec d’autres compilateurs, rendant cette solution de contournement inutile. Afin d’éviter cette erreur *C3861: 'unwind_type': identificateur introuvable*, consultez [PR 229](https://github.com/boostorg/python/pull/229) dans le référentiel Boostorg pour mettre à jour le fichier d’en-tête. Nous avons déjà corrigé le package Boost [vcpkg](vcpkg.md), donc si vous obtenez ou mettez à niveau vos sources Boost à partir de vcpkg, il est inutile d’appliquer le correctif séparément.

### <a name="forward-declarations-and-definitions-in-namespace-std"></a>définitions et déclarations anticipées dans l’espace de noms std

La norme C++ ne permet pas à un utilisateur d’ajouter des définitions ou des déclarations anticipées dans l’espace de noms `std`. L’ajout de définitions ou de déclarations à l’espace de noms `std` ou à un espace de noms dans l’espace de noms std donne désormais lieu à un comportement non défini.

Il est prévu que Microsoft affecte la définition de certains types STL à un autre emplacement. Ce changement entraînera l’arrêt de tout code existant qui ajoute des déclarations anticipées à l’espace de noms `std`. Un nouvel avertissement, C4643, vous aide à identifier de tels problèmes liés la source. Cet avertissement est activé dans le mode **/default** (il est désactivé par défaut). Il impacte les programmes compilés avec **/Wall** ou **/WX**.

Le code suivant génère désormais l’erreur C4643 *La déclaration anticipée de 'vector' dans l’espace de noms std n’est pas autorisée par la norme C++*.

```cpp
namespace std {
    template<typename T> class vector;
}
```

Pour corriger cette erreur, utilisez une directive **include** plutôt qu’une déclaration anticipée :

```cpp
#include <vector>
```

### <a name="constructors-that-delegate-to-themselves"></a>Constructeurs déléguant à eux-mêmes

La norme C++ suggère qu’un compilateur doit émettre un diagnostic quand un constructeur de délégation délègue à lui-même. Le compilateur Microsoft C++ dans les modes [/std:c++17](build/reference/std-specify-language-standard-version.md) et [/std:c++latest](build/reference/std-specify-language-standard-version.md) génère désormais l’erreur C7535 : *'X::X': le constructeur de délégation s'appelle lui-même*.

Sans cette erreur, la compilation du programme suivant aboutit, mais une boucle infinie est générée :

```cpp
class X {
public:
    X(int, int);
    X(int v) : X(v){}
};
```

Pour éviter la boucle infinie, déléguez à un autre constructeur :

```cpp
class X {
public:

    X(int, int);
    X(int v) : X(v, 0) {}
};
```

### <a name="offsetof-with-constant-expressions"></a>offsetof avec des expressions constantes

[offsetof](c-runtime-library/reference/offsetof-macro.md) est habituellement implémenté à l’aide d’une macro qui nécessite un [reinterpret_cast](cpp/reinterpret-cast-operator.md). Même si cette approche n’est pas conforme dans les contextes nécessitant une expression constante, le compilateur Microsoft C++ l’a toujours autorisée. La macro offsetof fournie dans le cadre de la bibliothèque STL utilise correctement une fonction intrinsèque du compilateur (**__builtin_offsetof**), mais de nombreuses personnes utilisent l’astuce de la macro pour définir leur propre **offsetof**.

Dans Visual Studio 2017 version 15.8, le compilateur contraint les zones dans lesquelles ces reinterpret_casts peuvent apparaître dans le mode par défaut pour améliorer la conformité du code au comportement C++ standard. Sous [/permissive-](build/reference/permissive-standards-conformance.md), les contraintes sont encore plus strictes. L’utilisation du résultat d’un offsetof dans les emplacements qui nécessitent des expressions constantes peut générer du code qui émet l’avertissement C4644 (*utilisation non standard du modèle offsetof de type macro dans les expressions constantes ; utilisez plutôt l’offsetof défini dans la bibliothèque standard C++*) ou C2975 (*argument template non valide, expression constante évaluée au moment de la compilation attendue*).

Le code suivant génère l’erreur C4644 dans les modes **/default** et **/std:c++17**, et l’erreur C2975 dans le mode **/permissive-** :

```cpp
struct Data {
    int x;
};

// Common pattern of user-defined offsetof
#define MY_OFFSET(T, m) (unsigned long long)(&(((T*)nullptr)->m))

int main()

{
    switch (0) {
    case MY_OFFSET(Data, x): return 0;
    default: return 1;
    }
}
```

Pour corriger cette erreur, utilisez **offsetof** tel que défini par le biais de \<cstddef> :

```cpp
#include <cstddef>

struct Data {
    int x;
};

int main()
{
    switch (0) {
    case offsetof(Data, x): return 0;
    default: return 1;
    }
}
```

### <a name="cv-qualifiers-on-base-classes-subject-to-pack-expansion"></a>qualificateurs cv sur les classes de base soumises à une expansion de pack

Les versions précédentes du compilateur Microsoft C++ ne détectaient pas la présence de qualificateurs cv dans une classe de base si celle-ci était également soumise à une expansion de pack.

Dans Visual Studio 2017 version 15.8, dans le mode **/permissive-**, le code suivant génère l’erreur C3770 *'const S' : n’est pas une classe de base valide* :

```cpp
template<typename... T>
class X : public T... { };

class S { };

int main()
{
    X<const S> x;
}
```

### <a name="template-keyword-and-nested-name-specifiers"></a>mot clé template et spécificateurs de noms imbriqués

Dans le mode **/permissive-**, le compilateur exige désormais que le mot clé `template` précède un nom de modèle quand celui-ci se situe après un spécificateur de nom imbriqué dépendant.

Le code suivant dans le mode **/permissive-** génère désormais l’erreur C7510 *'foo' : un nom de modèle dépendant doit être précédé de 'template'. Remarque : voir la référence à l’instanciation du modèle de classe 'X<T>' en cours de compilation* :

```cpp
template<typename T> struct Base
{
    template<class U> void foo() {}
};

template<typename T>
struct X : Base<T>
{
    void foo()
    {
        Base<T>::foo<int>();
    }
};
```

Pour corriger cette erreur, ajoutez le mot clé `template` à l’instruction `Base<T>::foo<int>();`, comme illustré dans l’exemple suivant :

```cpp
template<typename T> struct Base
{
    template<class U> void foo() {}
};

template<typename T>
struct X : Base<T>
{
    void foo()
    {
        // Add template keyword here:
        Base<T>::template foo<int>();
    }
};
```
## <a name="update_159"></a> Correctifs de bogues et changements de comportement dans Visual Studio 2017 version 15.9

### <a name="identifiers-in-member-alias-templates"></a>Identificateurs dans les modèles d’alias de membre
Un identificateur utilisé dans une définition de modèle d’alias de membre doit être déclaré avant toute utilisation. 

Dans les versions précédentes du compilateur, le code suivant était autorisé :

```cpp
template <typename... Ts>
struct A
{
  public:
    template <typename U>
    using from_template_t = decltype(from_template(A<U>{}));

  private:
    template <template <typename...> typename Type, typename... Args>
    static constexpr A<Args...> from_template(A<Type<Args...>>);
};

A<>::from_template_t<A<int>> a;
```

Dans Visual Studio 2017 version 15.9, en mode **/permissive-**, le compilateur génère C3861 : *'from_template' : identificateur introuvable*.

Pour corriger cette erreur, déclarez `from_template` avant `from_template_t`.

### <a name="modules-changes"></a>Changements apportés aux modules

Dans Visual Studio 2017 version 15.9, le compilateur génère C5050 chaque fois que les options de ligne de commande pour les modules ne sont pas cohérentes entre la partie création et la partie consommation du module. L’exemple suivant présente deux problèmes :

- Dans la partie consommation (main.cpp), l’option **/EHsc** n’est pas spécifiée.
- La version C++ est **/std:c++17** dans la partie création et **/std:c++14** dans la partie consommation. 

```cmd
cl /EHsc /std:c++17 m.ixx /experimental:module
cl /experimental:module /module:reference m.ifc main.cpp /std:c++14
```

Le compilateur génère C5050 dans ces deux cas : *avertissement C5050 : Environnement potentiellement incompatible durant l’importation du module 'm' : versions de C++ incompatibles.  Version actuelle "201402", version du module "201703"*.

De plus, le compilateur génère C7536 chaque fois que le fichier .ifc est falsifié. L’en-tête de l’interface de module contient un hachage SHA2 du contenu situé en dessous. Durant l’importation, le fichier .ifc est haché de la même façon et comparé au hachage fourni dans l’en-tête. S’ils diffèrent, l’erreur C7536 est générée : *ifc n’a pas réussi les vérifications de l’intégrité.  SHA2 attendu : '66d5c8154df0c71d4cab7665bab4a125c7ce5cb9a401a4d8b461b706ddd771c6'*.

### <a name="partial-ordering-involving-aliases-and-non-deduced-contexts"></a>Classement partiel impliquant des alias et des contextes non déduits

L’implémentation des règles de classement partiel impliquant des alias dans des contextes non déduits fait l’objet de divergences. Dans l’exemple suivant, GCC et le compilateur Microsoft C++ (en mode **/permissive-**) génèrent une erreur, alors que Clang accepte le code. 

```cpp
#include <utility>
using size_t = std::size_t;

template <typename T>
struct A {};
template <size_t, size_t>
struct AlignedBuffer {};
template <size_t len>
using AlignedStorage = AlignedBuffer<len, 4>;

template <class T, class Alloc>
int f(Alloc &alloc, const AlignedStorage<T::size> &buffer)
{
    return 1;
}

template <class T, class Alloc>
int f(A<Alloc> &alloc, const AlignedStorage<T::size> &buffer)
{
    return 2;
}

struct Alloc
{
    static constexpr size_t size = 10;
};

int main()
{
    A<void> a;
    AlignedStorage<Alloc::size> buf;
    if (f<Alloc>(a, buf) != 2)
    {
        return 1;
    }

    return 0;
}
```

L’exemple précédent génère C2668 :

```Output
partial_alias.cpp(32): error C2668: 'f': ambiguous call to overloaded function
partial_alias.cpp(18): note: could be 'int f<Alloc,void>(A<void> &,const AlignedBuffer<10,4> &)'
partial_alias.cpp(12): note: or       'int f<Alloc,A<void>>(Alloc &,const AlignedBuffer<10,4> &)'
        with
        [
            Alloc=A<void>
        ]
partial_alias.cpp(32): note: while trying to match the argument list '(A<void>, AlignedBuffer<10,4>)'
```

Cette divergence en matière d’implémentation est due à une régression dans la formulation de la norme. En effet, la résolution du problème de base 2235 a supprimé le texte qui permettait le classement de ces surcharges. La norme C++ actuelle ne fournissant pas de mécanisme pour classer partiellement ces fonctions, elles sont considérées comme ambiguës.

Pour résoudre ce problème, nous vous recommandons de ne pas recourir au classement partiel et d’utiliser à la place SFINAE pour supprimer des surcharges particulières. Dans l’exemple suivant, nous utilisons une classe d’assistance `IsA` pour supprimer la première surcharge quand `Alloc` est une spécialisation de `A` :

```cpp
#include <utility>
using size_t = std::size_t;

template <typename T>
struct A {};
template <size_t, size_t>
struct AlignedBuffer {};
template <size_t len>
using AlignedStorage = AlignedBuffer<len, 4>;

template <typename T> struct IsA : std::false_type {};
template <typename T> struct IsA<A<T>> : std::true_type {};

template <class T, class Alloc, typename = std::enable_if_t<!IsA<Alloc>::value>>
int f(Alloc &alloc, const AlignedStorage<T::size> &buffer)
{
    return 1;
}

template <class T, class Alloc>
int f(A<Alloc> &alloc, const AlignedStorage<T::size> &buffer)
{
    return 2;
}

struct Alloc
{
    static constexpr size_t size = 10;
};

int main()
{
    A<void> a;
    AlignedStorage<Alloc::size> buf;
    if (f<Alloc>(a, buf) != 2)
    {
        return 1;
    }

    return 0;
}
```

## <a name="see-also"></a>Voir aussi

[Conformité du langage Visual C++](visual-cpp-language-conformance.md)
