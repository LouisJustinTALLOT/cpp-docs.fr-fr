---
title: Exemples d'expressions lambda
ms.date: 11/04/2016
helpviewer_keywords:
- lambda expressions [C++], examples
ms.assetid: 52506b15-0771-4190-a966-2f302049ca86
ms.openlocfilehash: 6854c5710d8a27093078c0f2013d691ac22c5870
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50663951"
---
# <a name="examples-of-lambda-expressions"></a>Exemples d'expressions lambda

Cet article explique comment utiliser des expressions lambda dans vos programmes. Pour une vue d’ensemble des expressions lambda, consultez [Expressions Lambda](../cpp/lambda-expressions-in-cpp.md). Pour plus d’informations sur la structure d’une expression lambda, consultez [syntaxe d’Expression Lambda](../cpp/lambda-expression-syntax.md).

##  <a name="declaringLambdaExpressions"></a> Déclaration d’Expressions Lambda

### <a name="example-1"></a>Exemple 1

Car une expression lambda est typée, vous pouvez l’affecter à un **automatique** variable ou à un [fonction](../standard-library/function-class.md) de l’objet, comme illustré ici :

### <a name="code"></a>Code

```cpp
// declaring_lambda_expressions1.cpp
// compile with: /EHsc /W4
#include <functional>
#include <iostream>

int main()
{

    using namespace std;

    // Assign the lambda expression that adds two numbers to an auto variable.
    auto f1 = [](int x, int y) { return x + y; };

    cout << f1(2, 3) << endl;

    // Assign the same lambda expression to a function object.
    function<int(int, int)> f2 = [](int x, int y) { return x + y; };

    cout << f2(3, 4) << endl;
}
```

### <a name="output"></a>Sortie

```Output
5
7
```

### <a name="remarks"></a>Notes

Pour plus d’informations, consultez [automatique](../cpp/auto-cpp.md), [function, classe](../standard-library/function-class.md), et [appel de fonction](../cpp/function-call-cpp.md).

Bien que les expressions lambda soient le plus souvent déclarées dans le corps d’une fonction, vous pouvez les déclarer partout où vous pouvez initialiser une variable.

### <a name="example-2"></a>Exemple 2

Le compilateur Visual C++ lie une expression lambda à ses variables capturées lorsque l'expression est déclarée plutôt que lorsque l'expression est appelée. L'exemple suivant montre une expression lambda qui capture la variable locale `i` par valeur et la variable locale `j` par référence. Puisque l'expression lambda capture `i` par valeur, la réaffectation de `i` ultérieurement dans le programme n'affecte pas le résultat de l'expression. Toutefois, puisque l'expression lambda enregistre `j` par référence, la réaffectation de `j` influence le résultat de l'expression.

### <a name="code"></a>Code

```cpp
// declaring_lambda_expressions2.cpp
// compile with: /EHsc /W4
#include <functional>
#include <iostream>

int main()
{
   using namespace std;

   int i = 3;
   int j = 5;

   // The following lambda expression captures i by value and
   // j by reference.
   function<int (void)> f = [i, &j] { return i + j; };

   // Change the values of i and j.
   i = 22;
   j = 44;

   // Call f and print its result.
   cout << f() << endl;
}
```

### <a name="output"></a>Sortie

```Output
47
```

[[Dans cet article](#top)]

##  <a name="callingLambdaExpressions"></a> Appel d’Expressions Lambda

Vous pouvez appeler une expression lambda immédiatement, comme indiqué dans l'extrait de code suivant. Le deuxième extrait montre comment passer une expression lambda en tant qu’argument des algorithmes de bibliothèque C++ Standard tel que `find_if`.

### <a name="example-1"></a>Exemple 1

Cet exemple déclare une expression lambda qui retourne la somme de deux entiers et appelle l'expression immédiatement avec les arguments `5` et `4`:

### <a name="code"></a>Code

```cpp
// calling_lambda_expressions1.cpp
// compile with: /EHsc
#include <iostream>

int main()
{
   using namespace std;
   int n = [] (int x, int y) { return x + y; }(5, 4);
   cout << n << endl;
}
```

### <a name="output"></a>Sortie

```Output
9
```

### <a name="example-2"></a>Exemple 2

Cet exemple passe une expression lambda comme argument de la fonction `find_if`. L’expression lambda retourne **true** si son paramètre est un nombre pair.

### <a name="code"></a>Code

```cpp
// calling_lambda_expressions2.cpp
// compile with: /EHsc /W4
#include <list>
#include <algorithm>
#include <iostream>

int main()
{
    using namespace std;

    // Create a list of integers with a few initial elements.
    list<int> numbers;
    numbers.push_back(13);
    numbers.push_back(17);
    numbers.push_back(42);
    numbers.push_back(46);
    numbers.push_back(99);

    // Use the find_if function and a lambda expression to find the
    // first even number in the list.
    const list<int>::const_iterator result =
        find_if(numbers.begin(), numbers.end(),[](int n) { return (n % 2) == 0; });

    // Print the result.
    if (result != numbers.end()) {
        cout << "The first even number in the list is " << *result << "." << endl;
    } else {
        cout << "The list contains no even numbers." << endl;
    }
}
```

### <a name="output"></a>Sortie

```Output
The first even number in the list is 42.
```

### <a name="remarks"></a>Notes

Pour plus d’informations sur la `find_if` de fonction, consultez [find_if](../standard-library/algorithm-functions.md#find_if). Pour plus d’informations sur les fonctions de bibliothèque C++ Standard qui effectuent des algorithmes communs, consultez [ \<algorithme >](../standard-library/algorithm.md).

[[Dans cet article](#top)]

##  <a name="nestingLambdaExpressions"></a> Imbrication d’Expressions Lambda

### <a name="example"></a>Exemple

Vous pouvez imbriquer une expression lambda dans une autre, comme le montre l'exemple suivant. L'expression lambda interne multiplie son argument par 2 et retourne le résultat. L'expression lambda externe appelle l'expression lambda interne avec son argument et ajoute 3 au résultat.

### <a name="code"></a>Code

```cpp
// nesting_lambda_expressions.cpp
// compile with: /EHsc /W4
#include <iostream>

int main()
{
    using namespace std;

    // The following lambda expression contains a nested lambda
    // expression.
    int timestwoplusthree = [](int x) { return [](int y) { return y * 2; }(x) + 3; }(5);

    // Print the result.
    cout << timestwoplusthree << endl;
}
```

### <a name="output"></a>Sortie

```Output
13
```

### <a name="remarks"></a>Notes

Dans cet exemple, `[](int y) { return y * 2; }` est l'expression lambda imbriquée.

[[Dans cet article](#top)]

##  <a name="higherOrderLambdaExpressions"></a> Fonctions Lambda d’ordre supérieur

### <a name="example"></a>Exemple

Nombreux langages de programmation prennent en charge le concept d’un *fonction d’ordre supérieur.* Une fonction d'ordre supérieur est une expression lambda qui prend une autre expression lambda comme argument ou qui retourne une expression lambda. Vous pouvez utiliser la [fonction](../standard-library/function-class.md) classe pour permettre à une expression lambda de C++ se comporte comme une fonction d’ordre supérieur. L'exemple suivant présente une expression lambda qui retourne un objet `function` et une expression lambda qui prend un objet `function` comme argument.

### <a name="code"></a>Code

```cpp
// higher_order_lambda_expression.cpp
// compile with: /EHsc /W4
#include <iostream>
#include <functional>

int main()
{
    using namespace std;

    // The following code declares a lambda expression that returns
    // another lambda expression that adds two numbers.
    // The returned lambda expression captures parameter x by value.
    auto addtwointegers = [](int x) -> function<int(int)> {
        return [=](int y) { return x + y; };
    };

    // The following code declares a lambda expression that takes another
    // lambda expression as its argument.
    // The lambda expression applies the argument z to the function f
    // and multiplies by 2.
    auto higherorder = [](const function<int(int)>& f, int z) {
        return f(z) * 2;
    };

    // Call the lambda expression that is bound to higherorder.
    auto answer = higherorder(addtwointegers(7), 8);

    // Print the result, which is (7+8)*2.
    cout << answer << endl;
}
```

### <a name="output"></a>Sortie

```Output
30
```

[[Dans cet article](#top)]

##  <a name="methodLambdaExpressions"></a> À l’aide d’une Expression Lambda dans une fonction

### <a name="example"></a>Exemple

Vous pouvez utiliser les expressions lambda dans le corps d'une fonction. L’expression lambda peut accéder à toute donnée membre ou fonction accessible à la fonction englobante. Vous pouvez explicitement ou implicitement capturer le **cela** pointeur pour fournir l’accès aux fonctions et les données membres de la classe englobante.
**Visual Studio 2017 15.3 et versions ultérieures** (disponible avec [/std : c ++ 17](../build/reference/std-specify-language-standard-version.md)) : capturer **cela** par valeur (`[*this]`) lorsque l’expression lambda sera utilisé dans les opérations asynchrones ou parallèles où le code peut s’exécuter après l’objet d’origine est hors de portée.

Vous pouvez utiliser la **cela** pointeur explicitement dans une fonction, comme illustré ici :

```cpp
// capture "this" by reference
void ApplyScale(const vector<int>& v) const
{
   for_each(v.begin(), v.end(),
      [this](int n) { cout << n * _scale << endl; });
}

// capture "this" by value (Visual Studio 2017 version 15.3 and later)
void ApplyScale2(const vector<int>& v) const
{
   for_each(v.begin(), v.end(),
      [*this](int n) { cout << n * _scale << endl; });
}
```

Vous pouvez également capturer le **cela** pointeur implicitement :

```cpp
void ApplyScale(const vector<int>& v) const
{
   for_each(v.begin(), v.end(),
      [=](int n) { cout << n * _scale << endl; });
}
```

L'exemple suivant montre la classe `Scale`, qui encapsule une valeur d'échelle.

```cpp
// function_lambda_expression.cpp
// compile with: /EHsc /W4
#include <algorithm>
#include <iostream>
#include <vector>

using namespace std;

class Scale
{
public:
    // The constructor.
    explicit Scale(int scale) : _scale(scale) {}

    // Prints the product of each element in a vector object
    // and the scale value to the console.
    void ApplyScale(const vector<int>& v) const
    {
        for_each(v.begin(), v.end(), [=](int n) { cout << n * _scale << endl; });
    }

private:
    int _scale;
};

int main()
{
    vector<int> values;
    values.push_back(1);
    values.push_back(2);
    values.push_back(3);
    values.push_back(4);

    // Create a Scale object that scales elements by 3 and apply
    // it to the vector object. Does not modify the vector.
    Scale s(3);
    s.ApplyScale(values);
}
```

### <a name="output"></a>Sortie

```Output
3
6
9
12
```

### <a name="remarks"></a>Notes

La fonction `ApplyScale` utilise une expression lambda pour imprimer le produit de la valeur d’échelle et de chaque élément d’un objet `vector`. L’expression lambda capture implicitement **cela** afin qu’il puisse accéder le `_scale` membre.

[[Dans cet article](#top)]

##  <a name="templateLambdaExpressions"></a> Utilisation d’Expressions Lambda avec des modèles

### <a name="example"></a>Exemple

Les expressions lambda étant typées, vous pouvez les utiliser avec des modèles C++. L'exemple suivant illustre les fonctions `negate_all` et `print_all`. Le `negate_all` fonction s’applique l’unaire **operator -** à chaque élément dans le `vector` objet. La fonction `print_all` affiche chaque élément de l'objet `vector` sur la console.

### <a name="code"></a>Code

```cpp
// template_lambda_expression.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <iostream>

using namespace std;

// Negates each element in the vector object. Assumes signed data type.
template <typename T>
void negate_all(vector<T>& v)
{
    for_each(v.begin(), v.end(), [](T& n) { n = -n; });
}

// Prints to the console each element in the vector object.
template <typename T>
void print_all(const vector<T>& v)
{
    for_each(v.begin(), v.end(), [](const T& n) { cout << n << endl; });
}

int main()
{
    // Create a vector of signed integers with a few elements.
    vector<int> v;
    v.push_back(34);
    v.push_back(-43);
    v.push_back(56);

    print_all(v);
    negate_all(v);
    cout << "After negate_all():" << endl;
    print_all(v);
}
```

### <a name="output"></a>Sortie

```Output
34
-43
56
After negate_all():
-34
43
-56
```

### <a name="remarks"></a>Notes

Pour plus d’informations sur les modèles C++, consultez [modèles](../cpp/templates-cpp.md).

[[Dans cet article](#top)]

##  <a name="ehLambdaExpressions"></a> Gestion des Exceptions

### <a name="example"></a>Exemple

Le corps d'une expression lambda suit les règles de la gestion structurée des exceptions (SEH) et la gestion des exceptions C++. Vous pouvez gérer une exception levée dans le corps d'une expression lambda ou différer la gestion des exceptions dans la portée englobante. L’exemple suivant utilise le **for_each** (fonction) et une expression lambda pour remplir un `vector` objet avec les valeurs d’une autre. Il utilise un **essayez**/**catch** bloc pour gérer les accès non valide pour le premier vecteur.

### <a name="code"></a>Code

```cpp
// eh_lambda_expression.cpp
// compile with: /EHsc /W4
#include <vector>
#include <algorithm>
#include <iostream>
using namespace std;

int main()
{
    // Create a vector that contains 3 elements.
    vector<int> elements(3);

    // Create another vector that contains index values.
    vector<int> indices(3);
    indices[0] = 0;
    indices[1] = -1; // This is not a valid subscript. It will trigger an exception.
    indices[2] = 2;

    // Use the values from the vector of index values to
    // fill the elements vector. This example uses a
    // try/catch block to handle invalid access to the
    // elements vector.
    try
    {
        for_each(indices.begin(), indices.end(), [&](int index) {
            elements.at(index) = index;
        });
    }
    catch (const out_of_range& e)
    {
        cerr << "Caught '" << e.what() << "'." << endl;
    };
}
```

### <a name="output"></a>Sortie

```Output
Caught 'invalid vector<T> subscript'.
```

### <a name="remarks"></a>Notes

Pour plus d’informations sur la gestion des exceptions, consultez [gestion des exceptions](../cpp/exception-handling-in-visual-cpp.md).

[[Dans cet article](#top)]

##  <a name="managedLambdaExpressions"></a> Utilisation d’Expressions Lambda avec des Types managés (C++ / c++ / CLI)

### <a name="example"></a>Exemple

La clause de capture d'une expression lambda ne peut pas contenir une variable qui a un type managé. Toutefois, vous pouvez passer un argument qui a un type managé dans la liste de paramètres d'une expression lambda. L'exemple suivant contient une expression lambda qui capture la variable non managée locale `ch` par valeur et prend un objet <xref:System.String?displayProperty=fullName> comme paramètre.

### <a name="code"></a>Code

```cpp
// managed_lambda_expression.cpp
// compile with: /clr
using namespace System;

int main()
{
    char ch = '!'; // a local unmanaged variable

    // The following lambda expression captures local variables
    // by value and takes a managed String object as its parameter.
    [=](String ^s) {
        Console::WriteLine(s + Convert::ToChar(ch));
    }("Hello");
}
```

### <a name="output"></a>Sortie

```Output
Hello!
```

### <a name="remarks"></a>Notes

Vous pouvez également utiliser vos expressions lambda avec la bibliothèque STL/CLR. Pour plus d’informations, consultez [référence de la bibliothèque STL/CLR](../dotnet/stl-clr-library-reference.md).

> [!IMPORTANT]
>  Les expressions lambda ne sont pas pris en charge dans ces entités du common langage managé du runtime (CLR) : **classe ref**, **ref struct**, **classe value**, et **struct value**.

[[Dans cet article](#top)]

## <a name="see-also"></a>Voir aussi

[Expressions lambda](../cpp/lambda-expressions-in-cpp.md)<br/>
[Syntaxe d’expression lambda](../cpp/lambda-expression-syntax.md)<br/>
[auto](../cpp/auto-cpp.md)<br/>
[function, classe](../standard-library/function-class.md)<br/>
[find_if](../standard-library/algorithm-functions.md#find_if)<br/>
[\<algorithm>](../standard-library/algorithm.md)<br/>
[Appel de fonction ](../cpp/function-call-cpp.md)<br/>
[Modèles](../cpp/templates-cpp.md)<br/>
[Gestion des exceptions](../cpp/exception-handling-in-visual-cpp.md)<br/>
[Référence de bibliothèque STL/CLR](../dotnet/stl-clr-library-reference.md)