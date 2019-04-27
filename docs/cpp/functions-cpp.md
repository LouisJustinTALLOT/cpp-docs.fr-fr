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
ms.openlocfilehash: aafd3be3b27fbe134b380a29083b4ca36177e702
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62154132"
---
# <a name="functions-c"></a>Fonctions (C++)

Une fonction est un bloc de code qui effectue une opération. Une fonction peut éventuellement définir les paramètres d'entrée qui permettent aux appelants de passer des arguments dans la fonction. Une fonction peut éventuellement retourner une valeur en tant que sortie. Les fonctions sont utiles pour encapsuler les opérations courantes dans un seul bloc réutilisable, idéalement avec un nom qui décrit clairement ce que fait la fonction. La fonction suivante accepte deux entiers à partir d’un appelant et retourne leur somme ; *un* et *b* sont *paramètres* de type **int**.

```cpp
int sum(int a, int b)
{
    return a + b;
}
```

La fonction peut être appelée, ou *appelé*, à partir de n’importe quel nombre d’emplacements dans le programme. Les valeurs qui sont passés à la fonction sont les *arguments*, dont les types doivent être compatibles avec les types de paramètre dans la définition de fonction.

```cpp
int main()
{
    int i = sum(10, 32);
    int j = sum(i, 66);
    cout << "The value of j is" << j << endl; // 108
}
```

Il n’existe aucune limite pratique à la longueur de la fonction, mais une conception judicieuse s’adresse aux fonctions qui effectuent une seule tâche bien définie. Les algorithmes complexes doivent être divisés en fonctions plus simples à comprendre chaque fois que possible.

Les fonctions qui sont définies au niveau de la portée de classe sont appelées fonctions membres. En C++, contrairement à d'autres langages, une fonction peut également être définie au niveau de la portée d'espace de noms (y compris l'espace de noms global implicite). Ces fonctions sont appelées *fonctions libres* ou *des fonctions non-membres*; elles sont largement utilisées dans la bibliothèque Standard.

Les fonctions peuvent être *surchargé*, ce qui signifie que les différentes versions d’une fonction peut partager le même nom s’ils diffèrent par le nombre et/ou le type de paramètres formels. Pour plus d’informations, consultez [surcharge de fonction](../cpp/function-overloading.md).

## <a name="parts-of-a-function-declaration"></a>Éléments d'une déclaration de fonction

Une fonction minimale *déclaration* est constitué par le type de retour, le nom de fonction et la liste de paramètres (qui peut être vide), ainsi que des mots clés facultatifs qui fournissent des instructions supplémentaires pour le compilateur. L’exemple suivant est une déclaration de fonction :

```cpp
int sum(int a, int b);
```

Une définition de fonction se compose d’une déclaration, ainsi que les *corps*, qui est tout le code entre les accolades :

```cpp
int sum(int a, int b)
{
    return a + b;
}
```

Une déclaration de fonction suivie d'un point-virgule peut apparaître à plusieurs endroits dans un programme. Elle doit apparaître avant tout appel à cette fonction dans chaque unité de traduction. La définition de fonction doit apparaître une seule fois dans le programme, en fonction de la règle de définitions.

Les éléments requis d'une déclaration de fonction sont les suivants :

1. Le type de retour, qui spécifie le type de la valeur retournée par la fonction, ou **void** si aucune valeur n’est retournée. Dans C ++ 11, **automatique** est un type de retour valide qui indique au compilateur de déduire le type à partir de l’instruction return. En C++14, decltype(auto) est également autorisé. Pour plus d'informations, consultez Déduction de type dans les types de retours ci-dessous.

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

1. Sa spécification de liaison, **extern** ou **statique**.

    ```cpp
    //Declare printf with C linkage.
    extern "C" int printf( const char *fmt, ... );

    ```

   Pour plus d’informations, consultez [programme et liaison](../cpp/program-and-linkage-cpp.md).

1. **inline**, qui indique au compilateur de remplacer chaque appel à la fonction avec le code de fonction lui-même. L'incorporation peut améliorer les performances dans les scénarios où une fonction s'exécute rapidement et est appelée à plusieurs reprises dans une section du code critique pour les performances.

    ```cpp
    inline double Account::GetBalance()
    {
        return balance;
    }
    ```

   Pour plus d’informations, consultez [fonctions Inline](../cpp/inline-functions-cpp.md).

1. Un `noexcept` expression, qui spécifie si la fonction peut lever une exception. Dans l’exemple suivant, la fonction ne lève pas d’exception si le `is_pod` expression prend la valeur **true**.

    ```cpp
    #include <type_traits>

    template <typename T>
    T copy_object(T& obj) noexcept(std::is_pod<T>) {...}
    ```

   Pour plus d’informations, consultez [noexcept](../cpp/noexcept-cpp.md).

1. (Fonctions membres uniquement) Les qualificateurs cv, ce qui spécifient si la fonction est **const** ou **volatile**.

1. (Fonctions membres uniquement) **virtuels**, `override`, ou `final`. **virtuel** Spécifie qu’une fonction peut être substituée dans une classe dérivée. `override` signifie qu'une fonction dans une classe dérivée remplace une fonction virtuelle. `final` signifie qu'une fonction ne peut pas être substituée dans toute classe dérivée supplémentaire. Pour plus d’informations, consultez [fonctions virtuelles](../cpp/virtual-functions.md).

1. (fonctions membres uniquement) **statique** appliqué à un membre de fonction signifie que la fonction n’est pas associée à des instances d’objet de la classe.

1. (Fonctions membres Non statiques uniquement) Le qualificateur ref, ce qui indique au compilateur quelle surcharge d’une fonction de choisir quand le paramètre d’objet implicite (\*cela) est une référence rvalue ou une référence lvalue. Pour plus d’informations, consultez [surcharge de fonction](function-overloading.md#ref-qualifiers).

L'illustration suivante montre les parties d'une définition de fonction. La zone grisée est le corps de la fonction.

![Parties d’une définition de fonction](../cpp/media/vc38ru1.gif "parties d’une définition de fonction") <br/>
Éléments de définition de fonction

## <a name="function-definitions"></a>Définitions de fonction

Un *définition de fonction* se compose de la déclaration et le corps de la fonction, entre accolades, qui contient les déclarations de variables, des instructions et des expressions. L’exemple suivant montre une définition de fonction complet :

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

Vous pouvez déclarer une fonction membre en tant que **const** pour spécifier que la fonction n’est pas autorisée à modifier les valeurs des membres de données dans la classe. En déclarant une fonction membre en tant que **const**, vous aider au compilateur d’appliquer *const-exactitude*. Si une personne par inadvertance tente de modifier l’objet à l’aide d’une fonction déclarée en tant que **const**, une erreur du compilateur est générée. Pour plus d’informations, consultez [const](const-cpp.md).

Déclarer une fonction comme `constexpr` lorsque la valeur qu’il génère peut éventuellement être déterminée au moment de la compilation. En règle générale, une fonction constexpr exécute plus rapidement qu’une fonction régulière. Pour plus d’informations, consultez [constexpr](constexpr-cpp.md).

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

Pour plus d’informations, consultez [modèles de fonction](../cpp/function-templates.md)

## <a name="function-parameters-and-arguments"></a>Paramètres et arguments de fonction

Une fonction possède une liste de paramètres séparés par des virgules de zéro, un ou plusieurs types, chacun d'eux ayant un nom selon lequel il est accessible à l'intérieur du corps de la fonction. Un modèle de fonction peut spécifier des paramètres de type ou de valeur supplémentaires. L'appelant transmet les arguments, qui sont des valeurs concrètes dont les types sont compatibles avec la liste de paramètres.

Par défaut, les arguments sont passés à la fonction par valeur, ce qui signifie que la fonction reçoit une copie de l'objet passé. Pour les objets volumineux, une copie peut être coûteuse et n'est pas toujours nécessaire. Pour que les arguments à passer par référence (en particulier la référence lvalue), ajoutez un quantificateur référence au paramètre :

```cpp
void DoSomething(std::string& input){...}
```

Lorsqu’une fonction modifie un argument passé par référence, elle modifie l’objet d’origine, pas une copie locale. Pour empêcher une fonction de modifier un tel argument, qualifiez le paramètre comme const & :

```cpp
void DoSomething(const std::string& input){...}
```

**C++11 :**  Pour gérer explicitement les arguments sont passés par référence rvalue ou référence lvalue, utilisez une double perluète sur le paramètre pour indiquer une référence universelle :

```cpp
void DoSomething(const std::string&& input){...}
```

Une fonction déclarée avec le mot clé unique **void** dans la déclaration du paramètre liste n’accepte aucun argument, tant que le mot clé **void** est le premier et le seul membre de la liste de déclaration d’argument. Arguments de type **void** ailleurs dans la liste génèrent des erreurs. Exemple :

```cpp

// OK same as GetTickCount()
long GetTickCount( void );
```

Notez que, bien qu’il soit non conforme pour spécifier un **void** argument à l’exception, comme expliqué ici, types dérivés du type **void** (comme les pointeurs vers **void** et les tableaux de **void**) peuvent apparaître partout dans la liste de déclaration d’argument.

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

Pour plus d’informations, consultez [Arguments par défaut](../cpp/default-arguments.md).

## <a name="function-return-types"></a>Types de retour de fonction

Une fonction ne peut pas retourner une autre fonction ou un tableau intégré ; Toutefois, elle peut retourner des pointeurs vers ces types, ou un *lambda*, ce qui génère un objet de fonction. Mais dans ce cas, une fonction peut retourner une valeur de n’importe quel type qui est dans la portée, ou elle ne peut retourner aucune valeur, auquel cas le type de retour est **void**.

### <a name="trailing-return-types"></a>Types de retours de fin

Un type de retour « ordinaire » se trouve sur le côté gauche de la signature de fonction. Un *type de retour de fin* se trouve sur le côté droit de la signature et est précédé par l’opérateur ->. Les types de retours de fin sont particulièrement utiles dans les modèles de fonction quand le type de la valeur de retour dépend des paramètres de modèle.

```cpp
template<typename Lhs, typename Rhs>
auto Add(const Lhs& lhs, const Rhs& rhs) -> decltype(lhs + rhs)
{
    return lhs + rhs;
}
```

Lorsque **automatique** est utilisé conjointement avec un type de retour de fin, il sert seulement un espace réservé pour le produit de l’expression decltype et n’effectue pas lui-même de déduction de type.

## <a name="function-local-variables"></a>Variables locales de fonction

Une variable est déclarée à l’intérieur d’un corps de fonction est appelée un *variable locale* ou simplement un *local*. Les variables locales non statiques sont uniquement visibles à l'intérieur du corps de la fonction et, si elles sont déclarées sur la pile, sortent de la portée lors de la fermeture de la fonction. Quand vous construisez une variable locale et la retournez par valeur, le compilateur peut généralement exécuter l'optimisation de la valeur de retour pour éviter des opérations de copie inutiles. Si vous retournez une variable locale par référence, le compilateur émet un avertissement, car toute tentative d’utiliser cette référence par l’appelant se produit après la destruction de la variable locale.

En C++, une variable locale peut être déclarée comme statique. La variable n'est visible que dans le corps de fonction, mais une seule copie de la variable existe pour toutes les instances de la fonction. Les objets statiques locaux sont détruits durant l’arrêt spécifié par `atexit`. Si un objet statique n’a pas été construit car le flux de contrôle du programme a contourné sa déclaration, aucune tentative de destruction de cet objet n’est effectuée.

##  <a name="type_deduction"></a> Déduction de type dans les types de retour (C ++ 14)

Dans C ++ 14, vous pouvez utiliser **automatique** pour indiquer au compilateur de déduire le type de retour à partir du corps de fonction sans avoir à fournir un type de retour de fin. Notez que **automatique** toujours déduit à une retour par valeur. Utilisez `auto&&` pour indiquer au compilateur de déduire une référence.

Dans cet exemple, **automatique** sera déduit en tant que valeur non-const copie de la somme de lhs et rhs.

```cpp
template<typename Lhs, typename Rhs>
auto Add2(const Lhs& lhs, const Rhs& rhs)
{
    return lhs + rhs; //returns a non-const object by value
}
```

Notez que **automatique** ne conserve pas la const-ness de type déduit. Pour les fonctions dont la valeur retournée doit préserver la nature const ou ref de ses arguments de transfert, vous pouvez utiliser la **decltype (auto)** mot clé, qui utilise le **decltype** règles d’inférence de type et conserve les informations de type. **decltype (auto)** peut être utilisé en tant que valeur de retour ordinaire sur le côté gauche, ou comme une valeur de retour de fin.

L’exemple suivant (basé sur le code de [N3493](http://www.open-std.org/JTC1/SC22/WG21/docs/papers/2013/n3493.html)), montre **decltype (auto)** utilisé pour activer le transfert parfait des arguments de fonction dans un type de retour n’est pas connu jusqu'à ce que le modèle est instancié.

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
}
```

## <a name="multi_val"></a> Renvoi de plusieurs valeurs à partir d’une fonction

Il existe différentes manières de retourner plusieurs valeurs d’une fonction :

1. Encapsuler les valeurs dans un objet de classe ou un struct nommé. Requiert la définition de classe ou struct soient visibles à l’appelant :

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

1. Retourne un objet std::tuple ou std::pair :

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

1. **Visual Studio 2017 15.3 et versions ultérieures** (disponible avec [/std : c ++ 17](../build/reference/std-specify-language-standard-version.md)) : Utilisez les liaisons structurées. L’avantage de liaisons structurées est que les variables qui stockent les valeurs de retour sont initialisés en même temps, qu'ils sont déclarés, ce qui, dans certains cas peut être beaucoup plus efficace. Dans cette instruction--`auto[x, y, z] = f();`--les crochets introduire et initialiser des noms qui sont dans la portée pour le bloc de la fonction entière.

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

1. Outre l’utilisation de la valeur de retour, vous pouvez « return » valeurs en définissant un nombre quelconque de paramètres à utiliser le passage par référence afin que la fonction peut être modifiés ou initialiser les valeurs des objets qui fournit de l’appelant. Pour plus d’informations, consultez [Arguments de fonction de Type référence](reference-type-function-arguments.md).

## <a name="function-pointers"></a>Pointeurs fonction

C++ prend en charge les pointeurs de fonction de la même manière que le langage C. Toutefois, une alternative de type plus sécurisé consiste généralement à utiliser un objet de fonction.

Il est recommandé que **typedef** être utilisé pour déclarer un alias pour le type de pointeur fonction si vous déclarez une fonction qui retourne un type de pointeur de fonction.  Exemple :

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
