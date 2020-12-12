---
description: 'En savoir plus sur : expressions lambda en C++'
title: Expressions lambda en C++
ms.date: 05/07/2019
helpviewer_keywords:
- lambda expressions [C++]
- lambda expressions [C++], overview
- lambda expressions [C++], vs. function objects
ms.assetid: 713c7638-92be-4ade-ab22-fa33417073bf
ms.openlocfilehash: 5e65279fa8740876ad8824803ec459ced154f952
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97321039"
---
# <a name="lambda-expressions-in-c"></a>Expressions lambda en C++

En C++ 11 et versions ultérieures, une expression lambda, souvent appelée *lambda*, est un moyen pratique de définir un objet de fonction anonyme (une *fermeture*) juste à l’emplacement où il est appelé ou passé comme argument à une fonction. Les expressions lambda sont généralement utilisées pour encapsuler quelques lignes de code qui sont passées à des algorithmes ou méthodes asynchrones. Cet article explique ce que sont les expressions lambda, les compare à d'autres techniques de programmation, décrit leurs avantages et fournit un exemple simple.

## <a name="related-topics"></a>Rubriques connexes

- [Expressions lambda et objets de fonction](lambda-expression-syntax.md)
- [Utilisation d’expressions lambda](examples-of-lambda-expressions.md)
- [Expressions lambda constexpr](lambda-expressions-constexpr.md)

## <a name="parts-of-a-lambda-expression"></a>Éléments d’une expression lambda

La norme ISO C++ montre une expression lambda simple qui est passée en tant que troisième argument à la fonction `std::sort()` :

```cpp
#include <algorithm>
#include <cmath>

void abssort(float* x, unsigned n) {
    std::sort(x, x + n,
        // Lambda expression begins
        [](float a, float b) {
            return (std::abs(a) < std::abs(b));
        } // end of lambda expression
    );
}
```

Cette illustration montre les éléments d'une expression lambda :

![Éléments structurels d'une expression lambda](../cpp/media/lambdaexpsyntax.png "Éléments structurels d'une expression lambda")

1. *clause de capture* (également appelée *lambda-introducteur* dans la spécification C++.)

1. *liste de paramètres* Facultatif. (Également appelé *déclarateur lambda*)

1. *spécification mutable* Facultatif.

1. *spécification d’exception* Facultatif.

1. *type de retour de fin* Facultatif.

1. *corps lambda*.

### <a name="capture-clause"></a>Clause de capture

Une expression lambda peut introduire de nouvelles variables dans son corps (en **C++ 14**) et elle peut également accéder aux variables de la portée environnante, ou les *capturer*. Une expression lambda commence par la clause de capture (*lambda-introducteur* dans la syntaxe standard), qui spécifie quelles variables sont capturées, et si la capture est par valeur ou par référence. Les variables avec le préfixe esperluette (`&`) sont accessibles par référence et celles qui n'ont pas ce préfixe sont accessibles par valeur.

Une clause de capture vide, `[ ]`, indique que le corps de l’expression lambda n’accède à aucune variable dans la portée englobante.

Vous pouvez utiliser le mode de capture par défaut (*capture-default* dans la syntaxe standard) pour indiquer comment capturer toutes les variables externes référencées dans l’expression lambda : `[&]` signifie que toutes les variables que vous faites référence à sont capturées par référence et `[=]` signifie qu’elles sont capturées par valeur. Vous pouvez utiliser un mode de capture par défaut, puis spécifier le mode opposé explicitement pour des variables spécifiques. Par exemple, si le corps d'une expression lambda accède à la variable externe `total` par référence et à la variable externe `factor` par valeur, les clauses de capture suivantes sont équivalentes :

```cpp
[&total, factor]
[factor, &total]
[&, factor]
[factor, &]
[=, &total]
[&total, =]
```

Seules les variables mentionnées dans l’expression lambda sont capturées lors de l’utilisation d’une capture par défaut.

Si une clause de capture comprend une capture (valeur par défaut `&` ), non `identifier` dans une `capture` de cette clause de capture peut avoir la forme `& identifier` . De même, si la clause de capture comprend une capture-default `=` , alors aucune `capture` de cette clause de capture ne peut avoir la forme `= identifier` . Un identificateur ou **`this`** ne peut pas apparaître plusieurs fois dans une clause de capture. Quelques exemples sont illustrés dans l'extrait de code suivant.

```cpp
struct S { void f(int i); };

void S::f(int i) {
    [&, i]{};      // OK
    [&, &i]{};     // ERROR: i preceded by & when & is the default
    [=, this]{};   // ERROR: this when = is the default
    [=, *this]{ }; // OK: captures this by value. See below.
    [i, i]{};      // ERROR: i repeated
}
```

Une capture suivie d’un bouton de sélection est une expansion à en-tête pack, comme illustré dans cet exemple de [modèle variadiques](../cpp/ellipses-and-variadic-templates.md) :

```cpp
template<class... Args>
void f(Args... args) {
    auto x = [args...] { return g(args...); };
    x();
}
```

Pour utiliser des expressions lambda dans le corps d’une méthode de classe, transmettez le **`this`** pointeur à la clause de capture pour permettre l’accès aux méthodes et aux données membres de la classe englobante.

**Visual Studio 2017 version 15,3 et versions ultérieures** (disponibles avec [/std : c++ 17](../build/reference/std-specify-language-standard-version.md)) : le **`this`** pointeur peut être capturé par valeur en spécifiant **`*this`** dans la clause de capture. La capture par valeur signifie que la *fermeture* entière, qui est l’objet de fonction anonyme qui encapulates l’expression lambda, est copiée sur chaque site d’appel où le lambda est appelé. La capture par valeur est utile lorsque l’expression lambda s’exécute en opérations parallèles ou asynchrones, en particulier sur certaines architectures matérielles telles que NUMA.

Pour obtenir un exemple qui montre comment utiliser des expressions lambda avec des méthodes de classe, consultez « exemple : utilisation d’une expression lambda dans une méthode » dans [exemples d’expressions lambda](../cpp/examples-of-lambda-expressions.md).

Quand vous utilisez une clause de capture, nous vous conseillons de garder les points suivants à l'esprit, en particulier si vous utilisez des expressions lambda avec le multithreading :

- les captures de référence peuvent être utilisées pour modifier les variables externes, contrairement aux captures de valeur. ( **`mutable`** permet de modifier les copies, mais pas les originaux.)

- les captures de référence reflètent les mises à jour des variables externes, contrairement aux captures de valeur ;

- les captures de référence introduisent une dépendance liée à la durée de vie, contrairement aux captures de valeur. Ceci est particulièrement important lorsque l'expression lambda s'exécute de façon asynchrone. Si vous capturez une variable locale par référence dans une expression lambda asynchrone, cette variable locale aura très probablement disparu au moment de l'exécution de l'expression lambda, ce qui entraîne une violation d'accès au moment de l'exécution.

### <a name="generalized-capture-c-14"></a>Capture généralisée (C++14)

En C++14, vous pouvez introduire et initialiser des variables dans la clause de capture, sans qu'il ne soit nécessaire que ces variables existent dans la portée englobante de la fonction lambda. L'initialisation peut être exprimée comme n'importe quelle expression arbitraire ; le type de la nouvelle variable est déduit du type produit par l'expression. L’un des avantages de cette fonctionnalité est que, en C++14, vous pouvez capturer des variables move-only (par exemple, std::unique_ptr) dans la portée environnante et les utiliser dans une expression lambda.

```cpp
pNums = make_unique<vector<int>>(nums);
//...
      auto a = [ptr = move(pNums)]()
        {
           // use ptr
        };
```

### <a name="parameter-list"></a>Liste de paramètres

Outre la capture des variables, une expression lambda peut accepter des paramètres d'entrée. Une liste de paramètres (*déclarateur lambda* dans la syntaxe standard) est facultative et, dans la plupart des aspects, ressemble à la liste des paramètres d’une fonction.

```cpp
auto y = [] (int first, int second)
{
    return first + second;
};
```

En **C++ 14**, si le type de paramètre est générique, vous pouvez utiliser le **`auto`** mot clé comme spécificateur de type. Cela indique au compilateur de créer l'opérateur d'appel de fonction en tant que modèle. Chaque instance de **`auto`** dans une liste de paramètres équivaut à un paramètre de type distinct.

```cpp
auto y = [] (auto first, auto second)
{
    return first + second;
};
```

Une expression lambda peut accepter une autre expression lambda comme argument. Pour plus d’informations, consultez « Expressions lambda d’ordre supérieur » dans la rubrique [exemples d’expressions lambda](../cpp/examples-of-lambda-expressions.md).

Comme une liste de paramètres est facultative, vous pouvez omettre les parenthèses vides si vous ne passez pas d’arguments à l’expression lambda et que son lambda-déclarateur ne contient pas *de spécification d’exception*, de *type de retour de fin* ou **`mutable`** .

### <a name="mutable-specification"></a>Spécification mutable

En règle générale, l’opérateur d’appel de fonction d’une expression lambda est const par valeur, mais l’utilisation du **`mutable`** mot clé annule cette opération. Elle ne produit pas de membres de données mutables. La spécification "mutable" permet au corps d’une expression lambda de modifier les variables capturées par valeur. Certains des exemples fournis plus loin dans cet article montrent comment utiliser **`mutable`** .

### <a name="exception-specification"></a>Spécification d'exception

Vous pouvez utiliser la **`noexcept`** spécification d’exception pour indiquer que l’expression lambda ne lève pas d’exceptions. Comme avec les fonctions ordinaires, le compilateur Microsoft C++ génère un avertissement [C4297](../error-messages/compiler-warnings/compiler-warning-level-1-c4297.md) si une expression lambda déclare la **`noexcept`** spécification d’exception et que le corps lambda lève une exception, comme illustré ici :

```cpp
// throw_lambda_expression.cpp
// compile with: /W4 /EHsc
int main() // C4297 expected
{
   []() noexcept { throw 5; }();
}
```

Pour plus d’informations, consultez [spécifications d’exception (throw)](../cpp/exception-specifications-throw-cpp.md).

### <a name="return-type"></a>Type de retour

Le type de retour d’une expression lambda est déduit automatiquement. Vous n’êtes pas obligé d’utiliser le [`auto`](../cpp/auto-cpp.md) mot clé sauf si vous spécifiez un *type de retour de fin*. Le *type de retour de fin* ressemble à la partie de type de retour d’une méthode ou d’une fonction ordinaire. Toutefois, le type de retour doit suivre la liste de paramètres et vous devez inclure le mot clé de type de retour de fin **`->`** avant le type de retour.

Vous pouvez omettre la partie return-type d'une expression lambda si le corps de l'expression lambda contient une seule instruction return ou que l'expression lambda ne retourne pas de valeur. Si le corps d’une expression lambda contient une seule instruction return, le compilateur déduit le type de retour du type de l’expression de retour. Sinon, le compilateur déduit que le type de retour est **`void`** . Étudiez les extraits de code suivants qui illustrent ce principe.

```cpp
auto x1 = [](int i){ return i; }; // OK: return type is int
auto x2 = []{ return{ 1, 2 }; };  // ERROR: return type is void, deducing
                                  // return type from braced-init-list is not valid
```

Une expression lambda peut générer une autre expression lambda comme valeur de retour. Pour plus d’informations, consultez « Expressions lambda d’ordre supérieur » dans [exemples d’expressions lambda](../cpp/examples-of-lambda-expressions.md).

### <a name="lambda-body"></a>Corps lambda

Le corps lambda (*Compound-Statement* dans la syntaxe standard) d’une expression lambda peut contenir tout ce que le corps d’une méthode ou d’une fonction ordinaire peut contenir. Le corps d’une fonction ordinaire et d’une expression lambda peut accéder aux types de variables suivants :

- Variables capturées dans la portée englobante, comme décrit précédemment.

- Paramètres

- Variables déclarées localement

- Membres de données de classe, lorsqu’ils sont déclarés à l’intérieur d’une classe et **`this`** sont capturés

- Toute variable ayant une durée de stockage statique (par exemple, les variables globales)

L’exemple suivant contient une expression lambda qui capture explicitement la variable `n` par valeur, et capture implicitement la variable `m` par référence :

```cpp
// captures_lambda_expression.cpp
// compile with: /W4 /EHsc
#include <iostream>
using namespace std;

int main()
{
   int m = 0;
   int n = 0;
   [&, n] (int a) mutable { m = ++n + a; }(4);
   cout << m << endl << n << endl;
}
```

```Output
5
0
```

La variable `n` étant capturée par valeur, sa valeur reste `0` après l'appel à l'expression lambda. La **`mutable`** spécification permet `n` une modification dans l’expression lambda.

Bien qu’une expression lambda ne puisse capturer que les variables qui ont une durée de stockage automatique, vous pouvez utiliser les variables qui ont une durée de stockage statique dans le corps d’une expression lambda. L'exemple suivant utilise la fonction `generate` et une expression lambda pour assigner une valeur à chaque élément dans un objet `vector`. L'expression lambda modifie la variable statique pour générer la valeur de l'élément suivant.

```cpp
void fillVector(vector<int>& v)
{
    // A local static variable.
    static int nextValue = 1;

    // The lambda expression that appears in the following call to
    // the generate function modifies and uses the local static
    // variable nextValue.
    generate(v.begin(), v.end(), [] { return nextValue++; });
    //WARNING: this is not thread-safe and is shown for illustration only
}
```

Pour plus d’informations, consultez [generate](../standard-library/algorithm-functions.md#generate).

L’exemple de code suivant utilise la fonction de l’exemple précédent et ajoute un exemple d’expression lambda qui utilise l’algorithme de la bibliothèque standard C++ `generate_n` . Cette expression lambda affecte un élément d’un objet `vector` à la somme des deux éléments précédents. Le **`mutable`** mot clé est utilisé pour que le corps de l’expression lambda puisse modifier ses copies des variables externes `x` et `y` , que l’expression lambda capture par valeur. Étant donné que l'expression lambda capture les variables `x` et `y` d'origine par valeur, leurs valeurs restent égales à `1` après l'exécution de l'expression.

```cpp
// compile with: /W4 /EHsc
#include <algorithm>
#include <iostream>
#include <vector>
#include <string>

using namespace std;

template <typename C> void print(const string& s, const C& c) {
    cout << s;

    for (const auto& e : c) {
        cout << e << " ";
    }

    cout << endl;
}

void fillVector(vector<int>& v)
{
    // A local static variable.
    static int nextValue = 1;

    // The lambda expression that appears in the following call to
    // the generate function modifies and uses the local static
    // variable nextValue.
    generate(v.begin(), v.end(), [] { return nextValue++; });
    //WARNING: this is not thread-safe and is shown for illustration only
}

int main()
{
    // The number of elements in the vector.
    const int elementCount = 9;

    // Create a vector object with each element set to 1.
    vector<int> v(elementCount, 1);

    // These variables hold the previous two elements of the vector.
    int x = 1;
    int y = 1;

    // Sets each element in the vector to the sum of the
    // previous two elements.
    generate_n(v.begin() + 2,
        elementCount - 2,
        [=]() mutable throw() -> int { // lambda is the 3rd parameter
        // Generate current value.
        int n = x + y;
        // Update previous two values.
        x = y;
        y = n;
        return n;
    });
    print("vector v after call to generate_n() with lambda: ", v);

    // Print the local variables x and y.
    // The values of x and y hold their initial values because
    // they are captured by value.
    cout << "x: " << x << " y: " << y << endl;

    // Fill the vector with a sequence of numbers
    fillVector(v);
    print("vector v after 1st call to fillVector(): ", v);
    // Fill the vector with the next sequence of numbers
    fillVector(v);
    print("vector v after 2nd call to fillVector(): ", v);
}
```

```Output
vector v after call to generate_n() with lambda: 1 1 2 3 5 8 13 21 34
x: 1 y: 1
vector v after 1st call to fillVector(): 1 2 3 4 5 6 7 8 9
vector v after 2nd call to fillVector(): 10 11 12 13 14 15 16 17 18
```

Pour plus d’informations, consultez [generate_n](../standard-library/algorithm-functions.md#generate_n).

## <a name="constexpr-lambda-expressions"></a>`constexpr` expressions lambda

**Visual Studio 2017 version 15,3 et versions ultérieures** (disponibles avec [`/std:c++17`](../build/reference/std-specify-language-standard-version.md) ) : une expression lambda peut être déclarée comme **`constexpr`** ou utilisée dans une expression constante lorsque l’initialisation de chaque membre de données qu’elle capture ou introduit est autorisée dans une expression constante.

```cpp
    int y = 32;
    auto answer = [y]() constexpr
    {
        int x = 10;
        return y + x;
    };

    constexpr int Increment(int n)
    {
        return [n] { return n + 1; }();
    }
```

Une expression lambda est implicitement **`constexpr`** si son résultat satisfait aux exigences d’une **`constexpr`** fonction :

```cpp
    auto answer = [](int n)
    {
        return 32 + n;
    };

    constexpr int response = answer(10);
```

Si une expression lambda est implicitement ou explicitement **`constexpr`** , la conversion en pointeur de fonction produit une **`constexpr`** fonction :

```cpp
    auto Increment = [](int n)
    {
        return n + 1;
    };

    constexpr int(*inc)(int) = Increment;
```

## <a name="microsoft-specific"></a>Spécifique à Microsoft

Les expressions lambda ne sont pas prises en charge dans les entités managées Common Language Runtime (CLR) suivantes : **`ref class`** , **`ref struct`** , **`value class`** ou **`value struct`** .

Si vous utilisez un modificateur spécifique à Microsoft tel que [`__declspec`](../cpp/declspec.md) , vous pouvez l’insérer dans une expression lambda immédiatement après, `parameter-declaration-clause` par exemple :

```cpp
auto Sqr = [](int t) __declspec(code_seg("PagedMem")) -> int { return t*t; };
```

Pour déterminer si un modificateur est pris en charge par les expressions lambda, consultez l’article qui le concerne dans la section [modificateurs spécifiques à Microsoft](../cpp/microsoft-specific-modifiers.md) de la documentation.

En plus de la fonctionnalité lambda standard C++ 11, Visual Studio prend en charge les expressions lambda sans État, qui sont omni-convertibles en pointeurs de fonction qui utilisent des conventions d’appel arbitraires.

## <a name="see-also"></a>Voir aussi

[Informations de référence sur le langage C++](../cpp/cpp-language-reference.md)<br/>
[Objets de fonction dans la bibliothèque C++ standard](../standard-library/function-objects-in-the-stl.md)<br/>
[Appel de fonction](../cpp/function-call-cpp.md)<br/>
[`for_each`](../standard-library/algorithm-functions.md#for_each)
