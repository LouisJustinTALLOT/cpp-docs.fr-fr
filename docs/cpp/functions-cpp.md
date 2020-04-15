---
title: Fonctions (C++)
ms.date: 11/19/2018
helpviewer_keywords:
- defaults, arguments
- function definitions
- function definitions, about function definitions
- default arguments
- declarators, functions
ms.assetid: 33ba01d5-75b5-48d2-8eab-5483ac7d2274
ms.openlocfilehash: 1425ddebffc150158e88e44b1d2c22e3f85e5a31
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375740"
---
# <a name="functions-c"></a>Fonctions (C++)

Une fonction est un bloc de code qui effectue une opération. Une fonction peut éventuellement définir les paramètres d'entrée qui permettent aux appelants de passer des arguments dans la fonction. Une fonction peut éventuellement retourner une valeur en tant que sortie. Les fonctions sont utiles pour encapsuler les opérations courantes dans un seul bloc réutilisable, idéalement avec un nom qui décrit clairement ce que fait la fonction. La fonction suivante accepte deux entiers d’un appelant et retourne leur somme; *a* et *b* sont des *paramètres* de type **int**.

```cpp
int sum(int a, int b)
{
    return a + b;
}
```

La fonction peut être invoquée, ou *appelée,* à partir de n’importe quel nombre d’endroits dans le programme. Les valeurs qui sont transmises à la fonction sont les *arguments*, dont les types doivent être compatibles avec les types de paramètres dans la définition de fonction.

```cpp
int main()
{
    int i = sum(10, 32);
    int j = sum(i, 66);
    cout << "The value of j is" << j << endl; // 108
}
```

Il n’existe aucune limite pratique à la longueur de la fonction, mais une conception judicieuse s’adresse aux fonctions qui effectuent une seule tâche bien définie. Les algorithmes complexes doivent être divisés en fonctions plus simples à comprendre chaque fois que possible.

Les fonctions qui sont définies au niveau de la portée de classe sont appelées fonctions membres. En C++, contrairement à d'autres langages, une fonction peut également être définie au niveau de la portée d'espace de noms (y compris l'espace de noms global implicite). Ces fonctions sont *appelées fonctions libres* ou *fonctions non membres*; ils sont largement utilisés dans la Bibliothèque Standard.

Les fonctions peuvent être *surchargées,* ce qui signifie que différentes versions d’une fonction peuvent partager le même nom si elles diffèrent par le nombre et / ou le type de paramètres formels. Pour plus d’informations, voir [Chargement de fonction](../cpp/function-overloading.md).

## <a name="parts-of-a-function-declaration"></a>Éléments d'une déclaration de fonction

Une *déclaration* de fonction minimale se compose du type de retour, du nom de la fonction et de la liste des paramètres (qui peuvent être vides), ainsi que des mots clés facultatifs qui fournissent des instructions supplémentaires au compilateur. L’exemple suivant est une déclaration de fonction :

```cpp
int sum(int a, int b);
```

Une définition de fonction se compose d’une déclaration, plus le *corps*, qui est tout le code entre les accolades bouclées:

```cpp
int sum(int a, int b)
{
    return a + b;
}
```

Une déclaration de fonction suivie d'un point-virgule peut apparaître à plusieurs endroits dans un programme. Elle doit apparaître avant tout appel à cette fonction dans chaque unité de traduction. La définition de fonction doit apparaître une seule fois dans le programme, en fonction de la règle de définitions.

Les éléments requis d'une déclaration de fonction sont les suivants :

1. Le type de retour, qui spécifie le type de valeur que la fonction retourne, ou **vide** si aucune valeur n’est retournée. Dans le C 11, **l’automobile** est un type de retour valide qui demande au compilateur d’inférer le type de l’énoncé de retour. En C++14, decltype(auto) est également autorisé. Pour plus d'informations, consultez Déduction de type dans les types de retours ci-dessous.

1. Le nom de fonction, qui doit commencer par une lettre ou un trait de soulignement et ne peut pas contenir d'espaces. En général, les traits de soulignement de début dans les noms de fonctions de bibliothèque standard indiquent des fonctions membres privées ou des fonctions non membres qui ne sont pas destinées à être utilisées par votre code.

1. La liste de paramètres, un ensemble de zéro ou plusieurs paramètres séparés par des virgules et délimités par des accolades qui spécifient le type et éventuellement un nom local selon lequel les valeurs sont accessibles à l'intérieur du corps de la fonction.

Les éléments facultatifs d'une déclaration de fonction sont les suivants :

1. `constexpr`, qui indique que la valeur de retour de la fonction est une valeur de constante pouvant être calculée au moment de la compilation.

    ```cpp
    constexpr float exp(float x, int n)
    {
        return n == 0 ? 1 :
            n % 2 == 0 ? exp(x * x, n / 2) :
            exp(x * x, (n - 1) / 2) * x;
    };
    ```

1. Sa spécification de liaison, **externe** ou **statique**.

    ```cpp
    //Declare printf with C linkage.
    extern "C" int printf( const char *fmt, ... );

    ```

   Pour plus d’informations, voir [unités de traduction et lien](../cpp/program-and-linkage-cpp.md).

1. **inline**, qui demande au compilateur de remplacer chaque appel à la fonction par le code de fonction lui-même. L'incorporation peut améliorer les performances dans les scénarios où une fonction s'exécute rapidement et est appelée à plusieurs reprises dans une section du code critique pour les performances.

    ```cpp
    inline double Account::GetBalance()
    {
        return balance;
    }
    ```

   Pour plus d’informations, voir [Inline Functions](../cpp/inline-functions-cpp.md).

1. Une `noexcept` expression, qui précise si oui ou non la fonction peut jeter une exception. Dans l’exemple suivant, la fonction ne `is_pod` jette pas d’exception si l’expression s’évalue à **vrai**.

    ```cpp
    #include <type_traits>

    template <typename T>
    T copy_object(T& obj) noexcept(std::is_pod<T>) {...}
    ```

   Pour plus d’informations, ne voyez [pasexcept](../cpp/noexcept-cpp.md).

1. (Fonctions membres seulement) Les cv-qualifiers, qui spécifient si la fonction est **const** ou **volatile**.

1. (Fonctions membres seulement) **virtuel** `override`, `final`, ou . **virtuel** spécifie qu’une fonction peut être remplacée dans une classe dérivée. `override` signifie qu'une fonction dans une classe dérivée remplace une fonction virtuelle. `final` signifie qu'une fonction ne peut pas être substituée dans toute classe dérivée supplémentaire. Pour plus d’informations, voir [Fonctions virtuelles](../cpp/virtual-functions.md).

1. (fonctions membres seulement) **statique** appliquée à une fonction membre signifie que la fonction n’est associée à aucun cas d’objet de la classe.

1. (Fonctions non statiques des membres seulement) L’arbitre-qualification, qui spécifie au compilateur qui surcharge d’une\*fonction à choisir lorsque le paramètre implicite de l’objet (ceci) est une référence rvalue par rapport à une référence lvalue. Pour plus d’informations, voir [Chargement de fonction](function-overloading.md#ref-qualifiers).

L'illustration suivante montre les parties d'une définition de fonction. La zone grisée est le corps de la fonction.

![Éléments de définition de fonction](../cpp/media/vc38ru1.gif "Éléments de définition de fonction") <br/>
Éléments de définition de fonction

## <a name="function-definitions"></a>Définitions de fonction

Une définition de *fonction* se compose de la déclaration et du corps de la fonction, enfermé dans des accolades bouclées, qui contient des déclarations variables, des déclarations et des expressions. L’exemple suivant montre une définition complète de la fonction :

```cpp
    int foo(int i, std::string s)
    {
       int value {i};
       MyClass mc;
       if(strcmp(s, "default") != 0)
       {
            value = mc.do_something(i);
       }
       return value;
    }
```

Les variables déclarées à l'intérieur du corps sont appelées variables locales. Elles sortent de la portée lors de la fermeture de la fonction ; par conséquent, une fonction ne doit jamais retourner une référence à une variable locale !

```cpp
    MyClass& boom(int i, std::string s)
    {
       int value {i};
       MyClass mc;
       mc.Initialize(i,s);
       return mc;
    }
```

## <a name="const-and-constexpr-functions"></a>fonctions const et constexpr

Vous pouvez déclarer une fonction de membre comme **const** pour spécifier que la fonction n’est pas autorisée à changer les valeurs des membres de données de la classe. En déclarant une fonction de membre comme **const**, vous aidez le compilateur à faire respecter *la const-correctness*. Si quelqu’un tente par erreur de modifier l’objet en utilisant une fonction déclarée **const,** une erreur de compilateur est soulevée. Pour plus d’informations, voir [const](const-cpp.md).

Déclarer une `constexpr` fonction comme lorsque la valeur qu’il produit peut éventuellement être déterminée au moment de la compilation. Une fonction constexpr s’exécute généralement plus rapidement qu’une fonction régulière. Pour plus d’informations, voir [constexpr](constexpr-cpp.md).

## <a name="function-templates"></a>Modèles de fonctions

Un modèle de fonction est similaire à un modèle de classe ; il génère des fonctions concrètes basées sur les arguments template. Dans de nombreux cas, le modèle est capable de déduire les arguments de type et, par conséquent, il n'est pas nécessaire de les spécifier explicitement.

```cpp
template<typename Lhs, typename Rhs>
auto Add2(const Lhs& lhs, const Rhs& rhs)
{
    return lhs + rhs;
}

auto a = Add2(3.13, 2.895); // a is a double
auto b = Add2(string{ "Hello" }, string{ " World" }); // b is a std::string
```

Pour plus d’informations, voir [Modèles de fonction](../cpp/function-templates.md)

## <a name="function-parameters-and-arguments"></a>Paramètres et arguments de fonction

Une fonction possède une liste de paramètres séparés par des virgules de zéro, un ou plusieurs types, chacun d'eux ayant un nom selon lequel il est accessible à l'intérieur du corps de la fonction. Un modèle de fonction peut spécifier des paramètres de type ou de valeur supplémentaires. L'appelant transmet les arguments, qui sont des valeurs concrètes dont les types sont compatibles avec la liste de paramètres.

Par défaut, les arguments sont passés à la fonction par valeur, ce qui signifie que la fonction reçoit une copie de l'objet passé. Pour les objets volumineux, une copie peut être coûteuse et n'est pas toujours nécessaire. Pour faire passer les arguments par référence (en particulier la référence lvalue), ajoutez un quantificateur de référence au paramètre :

```cpp
void DoSomething(std::string& input){...}
```

Lorsqu’une fonction modifie un argument passé par référence, elle modifie l’objet d’origine, pas une copie locale. Pour empêcher une fonction de modifier un tel argument, qualifier le paramètre comme const& :

```cpp
void DoSomething(const std::string& input){...}
```

**11 :**  Pour traiter explicitement les arguments qui sont adoptés par rvalue-référence ou lvalue-référence, utilisez un double ampersand sur le paramètre pour indiquer une référence universelle :

```cpp
void DoSomething(const std::string&& input){...}
```

Une fonction déclarée avec le seul mot clé **vide** dans la liste de déclaration de paramètres ne prend pas d’arguments, tant que le mot clé **vide** est le premier et le seul membre de la liste de déclaration d’argument. Les arguments de type **nul** ailleurs dans la liste produisent des erreurs. Par exemple :

```cpp

// OK same as GetTickCount()
long GetTickCount( void );
```

Notez que, bien qu’il soit illégal de spécifier un argument **nul,** sauf tel qu’il est décrit ici, les types dérivés du **vide** de type (tels que les pointeurs à **vider** et les tableaux de **vide**) peuvent apparaître n’importe où la liste de déclaration d’argument.

### <a name="default-arguments"></a>Arguments par défaut

Le ou les derniers paramètres dans une signature de fonction peuvent recevoir un argument par défaut, ce qui signifie que l’appelant peut omettre l’argument lors de l’appel de la fonction, à moins de vouloir spécifier une autre valeur.

```cpp
int DoSomething(int num,
    string str,
    Allocator& alloc = defaultAllocator)
{ ... }

// OK both parameters are at end
int DoSomethingElse(int num,
    string str = string{ "Working" },
    Allocator& alloc = defaultAllocator)
{ ... }

// C2548: 'DoMore': missing default parameter for parameter 2
int DoMore(int num = 5, // Not a trailing parameter!
    string str,
    Allocator& = defaultAllocator)
{...}
```

Pour plus d’informations, voir [Arguments par défaut](../cpp/default-arguments.md).

## <a name="function-return-types"></a>Types de retour de fonction

Une fonction ne peut pas retourner une autre fonction, ou un tableau intégré; cependant il peut retourner des pointeurs à ces types, ou un *lambda*, qui produit un objet de fonction. À l’exception de ces cas, une fonction peut retourner une valeur de tout type de portée, ou elle ne peut rapporter aucune valeur, auquel cas le type de déclaration est **nul**.

### <a name="trailing-return-types"></a>Types de retours de fin

Un type de retour « ordinaire » se trouve sur le côté gauche de la signature de fonction. Un *type de retour de fuite* est situé sur le côté droit le plus de la signature et est précédé par l’opérateur ->. Les types de retours de fin sont particulièrement utiles dans les modèles de fonction quand le type de la valeur de retour dépend des paramètres de modèle.

```cpp
template<typename Lhs, typename Rhs>
auto Add(const Lhs& lhs, const Rhs& rhs) -> decltype(lhs + rhs)
{
    return lhs + rhs;
}
```

Lorsque **l’automobile** est utilisée en conjonction avec un type de retour de fuite, il sert juste de placeholder pour tout ce que l’expression decltype produit, et ne fait pas lui-même la déduction de type.

## <a name="function-local-variables"></a>Variables locales de fonction

Une variable qui est déclarée à l’intérieur d’un corps de fonction est appelée une *variable locale* ou tout simplement un *local*. Les variables locales non statiques sont uniquement visibles à l'intérieur du corps de la fonction et, si elles sont déclarées sur la pile, sortent de la portée lors de la fermeture de la fonction. Lorsque vous construisez une variable locale et la retournez par valeur, le compilateur peut généralement effectuer *l’optimisation de la valeur de retour nommée* pour éviter les opérations inutiles de copie. Si vous retournez une variable locale par référence, le compilateur émet un avertissement, car toute tentative d’utiliser cette référence par l’appelant se produit après la destruction de la variable locale.

En C++, une variable locale peut être déclarée comme statique. La variable n'est visible que dans le corps de fonction, mais une seule copie de la variable existe pour toutes les instances de la fonction. Les objets statiques locaux sont détruits durant l’arrêt spécifié par `atexit`. Si un objet statique n’a pas été construit car le flux de contrôle du programme a contourné sa déclaration, aucune tentative de destruction de cet objet n’est effectuée.

## <a name="type-deduction-in-return-types-c14"></a><a name="type_deduction"></a>Déduction de type dans les types de rendement (C 14)

Dans le C 14, vous pouvez utiliser **l’auto** pour demander au compilateur d’inférer le type de retour du corps de fonction sans avoir à fournir un type de retour de fuite. Notez que **l’automobile** déduit toujours à un retour par valeur. Utilisez `auto&&` pour indiquer au compilateur de déduire une référence.

Dans cet exemple, **l’automobile** sera déduite comme une copie de valeur non-const de la somme de lhs et rhs.

```cpp
template<typename Lhs, typename Rhs>
auto Add2(const Lhs& lhs, const Rhs& rhs)
{
    return lhs + rhs; //returns a non-const object by value
}
```

Notez que **l’automobile** ne conserve pas la const-ness du type qu’elle déduit. Pour les fonctions de mise en service dont la valeur de retour doit préserver la const-ness ou la ref-ness de ses arguments, vous pouvez utiliser le mot clé **decltype (auto),** qui utilise les règles d’inférence de type **decltype** et préserve toutes les informations de type. **le déchanttype (auto)** peut être utilisé comme valeur de retour ordinaire sur le côté gauche, ou comme valeur de retour de fuite.

L’exemple suivant (basé sur le code de [N3493](https://wg21.link/n3493)), montre **le decltype (auto)** utilisé pour permettre l’avance parfaite des arguments de fonction dans un type de retour qui n’est pas connu jusqu’à ce que le modèle est instantané.

```cpp
template<typename F, typename Tuple = tuple<T...>, int... I>
decltype(auto) apply_(F&& f, Tuple&& args, index_sequence<I...>)
{
    return std::forward<F>(f)(std::get<I>(std::forward<Tuple>(args))...);
}

template<typename F, typename Tuple = tuple<T...>,
    typename Indices = make_index_sequence<tuple_size<Tuple>::value >>
   decltype( auto)
    apply(F&& f, Tuple&& args)
{
    return apply_(std::forward<F>(f), std::forward<Tuple>(args), Indices());
}
```

## <a name="returning-multiple-values-from-a-function"></a><a name="multi_val"></a>Retour de plusieurs valeurs d’une fonction

Il existe différentes façons de retourner plus d’une valeur à partir d’une fonction :

1. Encapsulez les valeurs dans une classe ou un objet structurant nommé. Exige que la définition de classe ou de struct soit visible par l’appelant :

    ```cpp
    #include <string>
    #include <iostream>

    using namespace std;

    struct S
    {
        string name;
        int num;
    };

    S g()
    {
        string t{ "hello" };
        int u{ 42 };
        return { t, u };
    }

    int main()
    {
        S s = g();
        cout << s.name << " " << s.num << endl;
        return 0;
    }
    ```

1. Retournez une std::tuple ou std::pa objet d’escalier :

    ```cpp
    #include <tuple>
    #include <string>
    #include <iostream>

    using namespace std;

    tuple<int, string, double> f()
    {
        int i{ 108 };
        string s{ "Some text" };
        double d{ .01 };
        return { i,s,d };
    }

    int main()
    {
        auto t = f();
        cout << get<0>(t) << " " << get<1>(t) << " " << get<2>(t) << endl;

        // --or--

        int myval;
        string myname;
        double mydecimal;
        tie(myval, myname, mydecimal) = f();
        cout << myval << " " << myname << " " << mydecimal << endl;

        return 0;
    }
    ```

1. **Visual Studio 2017 version 15.3 et plus tard** (disponible avec [/std:c '17):](../build/reference/std-specify-language-standard-version.md)Utilisez des fixations structurées. L’avantage des fixations structurées est que les variables qui stockent les valeurs de rendement sont paradées en même temps qu’elles sont déclarées, ce qui, dans certains cas, peut être beaucoup plus efficace. Dans cette déclaration`auto[x, y, z] = f();`-- les parenthèses introduisent et initialisent les noms qui sont en portée pour l’ensemble du bloc de fonction.

    ```cpp
    #include <tuple>
    #include <string>
    #include <iostream>

    using namespace std;

    tuple<int, string, double> f()
    {
        int i{ 108 };
        string s{ "Some text" };
        double d{ .01 };
        return { i,s,d };
    }
    struct S
    {
        string name;
        int num;
    };

    S g()
    {
        string t{ "hello" };
        int u{ 42 };
        return { t, u };
    }

    int main()
    {
        auto[x, y, z] = f(); // init from tuple
        cout << x << " " << y << " " << z << endl;

        auto[a, b] = g(); // init from POD struct
        cout << a << " " << b << endl;
        return 0;
    }
    ```

1. En plus d’utiliser la valeur de retour elle-même, vous pouvez « retourner » les valeurs en définissant n’importe quel nombre de paramètres à utiliser pass-by-reference afin que la fonction puisse modifier ou initialiser les valeurs des objets que l’appelant fournit. Pour plus d’informations, voir [Arguments de fonction de référence-type](reference-type-function-arguments.md).

## <a name="function-pointers"></a>Pointeurs fonction

C++ prend en charge les pointeurs de fonction de la même manière que le langage C. Toutefois, une alternative de type plus sécurisé consiste généralement à utiliser un objet de fonction.

Il est recommandé que **le tapdef** soit utilisé pour déclarer un alias pour le type de pointeur de fonction si vous déclarez une fonction qui renvoie un type de pointeur de fonction.  Par exemple

```cpp
typedef int (*fp)(int);
fp myFunction(char* s); // function returning function pointer
```

Si vous ne procédez pas ainsi, la syntaxe appropriée pour la déclaration de fonction peut être déduite de la syntaxe des déclarateurs pour le pointeur fonction, en remplaçant l’identificateur (`fp` dans l’exemple ci-dessus) par la liste de noms et d’arguments de fonctions, comme suit :

```cpp
int (*myFunction(char* s))(int);
```

La déclaration précédente est équivalente à la déclaration utilisant typedef ci-dessus.

## <a name="see-also"></a>Voir aussi

[Surcharge de fonction](../cpp/function-overloading.md)<br/>
[Fonctions avec listes d’arguments variables](../cpp/functions-with-variable-argument-lists-cpp.md)<br/>
[Fonctions utilisées par défaut et supprimées explicitement](../cpp/explicitly-defaulted-and-deleted-functions.md)<br/>
[Recherche de nom qui dépend de l’argument (Koenig) sur les fonctions](../cpp/argument-dependent-name-koenig-lookup-on-functions.md)<br/>
[Arguments par défaut](../cpp/default-arguments.md)<br/>
[Fonctions inline](../cpp/inline-functions-cpp.md)
