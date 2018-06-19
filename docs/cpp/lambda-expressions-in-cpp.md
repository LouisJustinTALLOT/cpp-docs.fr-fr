---
title: Expressions lambda en C++ | Documents Microsoft
ms.custom: ''
ms.date: 07/19/2017
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- lambda expressions [C++]
- lambda expressions [C++], overview
- lambda expressions [C++], vs. function objects
ms.assetid: 713c7638-92be-4ade-ab22-fa33417073bf
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c1cfcb210d3de7ce818d39ecf1703299defedc5d
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32424047"
---
# <a name="lambda-expressions-in-c"></a>Expressions lambda en C++
Dans C ++ 11 et versions ultérieures, une expression lambda, souvent appelé un *lambda*, est un moyen pratique de définir un objet de fonction anonyme (un *fermeture*) à l’emplacement où il est appelé ou passé comme argument pour une fonction. Les expressions lambda sont généralement utilisées pour encapsuler quelques lignes de code qui sont passées à des algorithmes ou méthodes asynchrones. Cet article explique ce que sont les expressions lambda, les compare à d'autres techniques de programmation, décrit leurs avantages et fournit un exemple simple.  

## <a name="related-topics"></a>Rubriques connexes
- [Expressions lambda et les objets de fonction](lambda-expression-syntax.md)
- [Utilisation des expressions lambda](examples-of-lambda-expressions.md)
- [expressions lambda de constexpr](lambda-expressions-constexpr.md)

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
  
 ![Éléments structurels d’une expression lambda](../cpp/media/lambdaexpsyntax.png "LambdaExpSyntax")  
  
1.  *clause de capture* (également connu sous le *lambda-introducer* dans la spécification C++.)  
  
2.  *liste de paramètres* facultatif. (Également connu sous le *lambda-declarator*)  
  
3.  *spécification mutable* facultatif.  
  
4.  *spécification d’exception* facultatif.  
  
5.  *Trailing-return-type* facultatif.  
  
6.  *corps d’expression lambda*)  
  
### <a name="capture-clause"></a>Clause de capture  
 Une expression lambda peut introduire de nouvelles variables dans son corps (dans **C ++ 14**) et il peut également l’accès, ou *capture*, les variables dans la portée environnante. Une expression lambda commence par la clause de capture (*lambda-introducer* dans la syntaxe Standard), qui spécifie quelles variables sont capturées et si la capture par valeur ou par référence. Les variables avec le préfixe esperluette (`&`) sont accessibles par référence et celles qui n'ont pas ce préfixe sont accessibles par valeur.  
  
 Une clause de capture vide, `[ ]`, indique que le corps de l'expression lambda n'accède à aucune variable dans la portée englobante.  
  
 Vous pouvez utiliser le mode de capture par défaut (*par défaut de la capture* dans la syntaxe Standard) pour indiquer comment capturer les variables externes qui sont référencées dans l’expression lambda : `[&]` signifie que toutes les variables référencées sont capturées par référence, et `[=]` signifie qu’ils sont capturés par valeur. Vous pouvez utiliser un mode de capture par défaut, puis spécifier le mode opposé explicitement pour des variables spécifiques. Par exemple, si le corps d'une expression lambda accède à la variable externe `total` par référence et à la variable externe `factor` par valeur, les clauses de capture suivantes sont équivalentes :  
  
```cpp  
[&total, factor]  
[factor, &total]  
[&, factor]  
[factor, &]  
[=, &total]  
[&total, =]  
```  
  
 Seules les variables qui sont mentionnés dans l’expression lambda sont capturées quand une capture par défaut est utilisé.  
  
 Si une clause de capture inclut une capture par défaut `&`, aucune `identifier` dans un `capture` de la capture de cette clause peut avoir la forme `& identifier`. De même, si la clause de capture inclut une capture par défaut `=`, aucune `capture` de la capture de cette clause peut avoir la forme `= identifier`. Les identificateurs (`this`) ne peuvent pas apparaître plusieurs fois dans une clause de capture. Quelques exemples sont illustrés dans l'extrait de code suivant.  
  
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
  
 Une capture suivie d’un bouton de sélection est une expansion, comme indiqué dans cette [modèle variadique](../cpp/ellipses-and-variadic-templates.md) exemple :  
  
```cpp  
template<class... Args>  
void f(Args... args) {  
    auto x = [args...] { return g(args...); };  
    x();  
}  
```  
  
 Pour utiliser les expressions lambda dans le corps d'une méthode de classe, passez le pointeur `this` à la clause de capture pour permettre l'accès aux méthodes et données membres de la classe englobante. 
 
**Visual Studio 2017 15,3 et versions ultérieures** (disponible avec [/std : c ++ 17](../build/reference/std-specify-language-standard-version.md)) : le `this` pointeur peut-être être capturé par valeur, en spécifiant `*this` dans la clause de capture. Capture par valeur signifie que l’ensemble du *fermeture*, qui est l’objet de fonction anonyme qui encapulates l’expression lambda, il est copié vers chaque site d’appel dans lequel l’expression lambda est appelé. Capture par valeur est utile lorsque l’expression lambda ne s’exécutera dans des opérations parallèles ou asynchrones, en particulier sur certaines architectures matérielles telles que NUMA. 

Pour obtenir un exemple qui montre comment utiliser des expressions lambda avec des méthodes de classe, consultez « Exemple : à l’aide d’une Expression Lambda dans une méthode » dans [exemples d’Expressions Lambda](../cpp/examples-of-lambda-expressions.md).  
  
 Quand vous utilisez une clause de capture, nous vous conseillons de garder les points suivants à l'esprit, en particulier si vous utilisez des expressions lambda avec le multithreading :  
  
-   les captures de référence peuvent être utilisées pour modifier les variables externes, contrairement aux captures de valeur. `mutable` autorise la modification des copies et non des originaux.)  
  
-   les captures de référence reflètent les mises à jour des variables externes, contrairement aux captures de valeur ;  
  
-   les captures de référence introduisent une dépendance liée à la durée de vie, contrairement aux captures de valeur. Ceci est particulièrement important lorsque l'expression lambda s'exécute de façon asynchrone. Si vous capturez une variable locale par référence dans une expression lambda asynchrone, cette variable locale aura très probablement disparu au moment de l'exécution de l'expression lambda, ce qui entraîne une violation d'accès au moment de l'exécution.  
  
### <a name="generalized-capture-c-14"></a>Capture généralisée (C++14)  
  
 En C++14, vous pouvez introduire et initialiser des variables dans la clause de capture, sans qu'il ne soit nécessaire que ces variables existent dans la portée englobante de la fonction lambda. L'initialisation peut être exprimée comme n'importe quelle expression arbitraire ; le type de la nouvelle variable est déduit du type produit par l'expression. L'un des avantages de cette fonctionnalité est que, en C++14, vous pouvez capturer des variables move-only (par exemple, std::unique_ptr) dans la portée environnante et les utiliser dans une expression lambda.  
  
```cpp  
pNums = make_unique<vector<int>>(nums);  
//...  
      auto a = [ptr = move(pNums)]()  
        {  
           // use ptr  
        };  
```  
  
### <a name="parameter-list"></a>Liste de paramètres  
 Outre la capture des variables, une expression lambda peut accepter des paramètres d'entrée. Une liste de paramètres (*lambda-declarator* dans la syntaxe Standard) est facultatif et dans la plupart des aspects ressemble à la liste de paramètres pour une fonction.  
  
```cpp  
auto y = [] (int first, int second)  
{  
    return first + second;  
};  
  
```  
  
 Dans **c ++ 14**, si le type de paramètre est générique, vous pouvez utiliser le mot clé auto comme spécificateur de type. Cela indique au compilateur de créer l'opérateur d'appel de fonction en tant que modèle. Chaque instance d'auto dans une liste de paramètres est équivalente à un paramètre de type distinct.  
  
```cpp  
auto y = [] (auto first, auto second)  
{  
    return first + second;  
};  
```  
  
 Une expression lambda peut accepter une autre expression lambda comme argument. Pour plus d’informations, consultez « Expressions Lambda d’ordre supérieur » dans la rubrique [exemples d’Expressions Lambda](../cpp/examples-of-lambda-expressions.md).  
  
 Comme une liste de paramètres est facultative, vous pouvez omettre les parenthèses vides si vous ne passez pas d’arguments à l’expression lambda et ne contient-elle pas de son lambda-declarator *spécification d’exception*,  *Trailing-return-type*, ou `mutable`.  
  
### <a name="mutable-specification"></a>Spécification mutable  
 En règle générale, l'opérateur d'appel de fonction d'une expression lambda est de type const par valeur, mais ceci s'annule lorsque `mutable` est ajouté. Cela ne produit pas de données membres mutables. La spécification "mutable" permet au corps d'une expression lambda de modifier les variables capturées par valeur. Certains des exemples cités plus loin dans cet article montrent comment utiliser `mutable`.  
  
### <a name="exception-specification"></a>Spécification d'exception  
 Vous pouvez utiliser la spécification d'exception `noexcept` pour indiquer que l'expression lambda ne lève pas d'exception. Comme avec les fonctions ordinaires, le compilateur Visual C++ génère l’avertissement [C4297](../error-messages/compiler-warnings/compiler-warning-level-1-c4297.md) si une expression lambda déclare la `noexcept` spécification d’exception et du corps du lambda lève une exception, comme indiqué ici :  
  
```cpp  
// throw_lambda_expression.cpp  
// compile with: /W4 /EHsc   
int main() // C4297 expected  
{  
   []() noexcept { throw 5; }();  
}  
```  
  
 Pour plus d’informations, consultez [spécifications d’Exception (throw)](../cpp/exception-specifications-throw-cpp.md).  
  
### <a name="return-type"></a>Type de retour  
 Le type de retour d’une expression lambda est déduit automatiquement. Vous n’êtes pas obligé d’utiliser le [automatique](../cpp/auto-cpp.md) (mot clé), sauf si vous spécifiez un *trailing-return-type*. Le *trailing-return-type* ressemble à la partie return-type d’une méthode ordinaire ou une fonction. Toutefois, le type de retour doit suivre la liste de paramètres. Vous devez donc ajouter le mot clé trailing-return-type `->` avant le type de retour.  
  
 Vous pouvez omettre la partie return-type d'une expression lambda si le corps de l'expression lambda contient une seule instruction return ou que l'expression lambda ne retourne pas de valeur. Si le corps d'une expression lambda contient une seule instruction return, le compilateur déduit le type de retour du type de l'expression de retour. Sinon, le compilateur déduit que le type de retour doit être `void`. Étudiez les extraits de code suivants qui illustrent ce principe.  
  
```cpp  
auto x1 = [](int i){ return i; }; // OK: return type is int  
auto x2 = []{ return{ 1, 2 }; };  // ERROR: return type is void, deducing   
                                  // return type from braced-init-list is not valid  
```  
  
 Une expression lambda peut générer une autre expression lambda comme valeur de retour. Pour plus d’informations, consultez « Expressions Lambda d’ordre supérieur » dans [exemples d’Expressions Lambda](../cpp/examples-of-lambda-expressions.md).  
  
### <a name="lambda-body"></a>Corps lambda  
 Le corps du lambda (*compound-statement* dans la syntaxe Standard) d’une expression lambda expression permettre contenir tout ce que le corps d’une méthode ordinaire ou une fonction peut contenir. Le corps d’une fonction ordinaire et d’une expression lambda peut accéder aux types de variables suivants :  
  
-   Variables capturées dans la portée englobante, comme décrit précédemment.  
  
-   Paramètres  
  
-   Variables déclarées localement  
  
-   Données membres de classe, quand elles sont déclarées dans une classe et que `this` est capturé  
  
-   Toute variable ayant une durée de stockage statique (par exemple, les variables globales)  
  
 L'exemple suivant contient une expression lambda qui capture explicitement la variable `n` par valeur, et capture implicitement la variable `m` par référence :  
  
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
  
 La variable `n` étant capturée par valeur, sa valeur reste `0` après l'appel à l'expression lambda. La spécification `mutable` permet à `n` d'être modifié au sein d'une expression lambda.  
  
 Bien qu'une expression lambda ne puisse capturer que les variables qui ont une durée de stockage automatique, vous pouvez utiliser les variables qui ont une durée de stockage statique dans le corps d'une expression lambda. L'exemple suivant utilise la fonction `generate` et une expression lambda pour assigner une valeur à chaque élément dans un objet `vector`. L’expression lambda modifie la variable statique pour générer la valeur de l’élément suivant.  
  
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
  
 Pour plus d’informations, consultez [générer](../standard-library/algorithm-functions.md#generate).  
  
 L’exemple de code suivant utilise la fonction de l’exemple précédent et ajoute un exemple d’une expression lambda qui utilise l’algorithme de la bibliothèque Standard C++ `generate_n`. Cette expression lambda affecte un élément d'un objet `vector` à la somme des deux éléments précédents. Le mot clé `mutable` est utilisé pour que le corps de l'expression lambda puisse modifier ses copies des variables externes `x` et `y`, que l'expression lambda capture par valeur. Étant donné que l'expression lambda capture les variables `x` et `y` d'origine par valeur, leurs valeurs restent égales à `1` après l'exécution de l'expression.  
  
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

## <a name="constexpr-lambda-expressions"></a>expressions lambda de constexpr
**Visual Studio 2017 15,3 et versions ultérieures** (disponible avec [/std : c ++ 17](../build/reference/std-specify-language-standard-version.md)) : une expression lambda peut être déclarée comme `constexpr` ou utilisée dans une expression constante lors de l’initialisation de chaque membre de données qu’elle capture ou introduit est autorisée dans une expression constante.  

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
Une expression lambda est implicitement `constexpr` si son résultat répond aux exigences d’un `constexpr` (fonction) :
```cpp
    auto answer = [](int n) 
    {
        return 32 + n; 
    };

    constexpr int response = answer(10);
``` 
Si une expression lambda est implicitement ou explicitement `constexpr`, conversion pointeur fonction génère un `constexpr` (fonction) :

```cpp
    auto Increment = [](int n)
    {
        return n + 1;
    };

    constexpr int(*inc)(int) = Increment;
```
  
## <a name="microsoft-specific"></a>Spécifique à Microsoft  
 Les expressions lambda ne sont pas prises en charge dans les entités managées suivantes du Common Langage Runtime (CLR) : `ref class`, `ref struct`, `value class` et `value struct`.  
  
 Si vous utilisez un modificateur Microsoft spécifique tel que [__declspec](../cpp/declspec.md), vous pouvez l’insérer dans une expression lambda immédiatement après le `parameter-declaration-clause`, par exemple :  
  
```cpp  
auto Sqr = [](int t) __declspec(code_seg("PagedMem")) -> int { return t*t; };  
```  
  
 Pour déterminer si un modificateur est pris en charge par les expressions lambda, consultez l’article sur celui-ci dans le [modificateurs spécifiques Microsoft](../cpp/microsoft-specific-modifiers.md) section de la documentation.  
  
 C ++ 11 fonctionnalités lambda Standard, Visual Studio prend en charge les expressions lambda sans état, qui sont converties en pointeurs de fonction qui utilisent des conventions d’appel arbitraires.  
  
## <a name="see-also"></a>Voir aussi  
 [Référence du langage C++](../cpp/cpp-language-reference.md)   
 [Objets de fonction dans la bibliothèque Standard C++](../standard-library/function-objects-in-the-stl.md)   
 [Appel de fonction](../cpp/function-call-cpp.md)   
 [for_each](../standard-library/algorithm-functions.md#for_each)
