---
title: Syntaxe d’expression lambda
ms.date: 05/07/2019
helpviewer_keywords:
- lambda expressions [C++], syntax
ms.assetid: 5d6154a4-f34d-4a15-970d-7e7de45f54e9
ms.openlocfilehash: 8db094dd14e63c08fbe8514f245c1777922224cf
ms.sourcegitcommit: d9c94dcabd94537e304be0261b3263c2071b437b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/25/2020
ms.locfileid: "91352711"
---
# <a name="lambda-expression-syntax"></a>Syntaxe d’expression lambda

Cet article décrit la syntaxe et les éléments structuraux des expressions lambda. Pour obtenir une description des expressions lambda, consultez [expressions lambda](../cpp/lambda-expressions-in-cpp.md).

## <a name="function-objects-vs-lambdas"></a>Comparaison des objets de fonction et des expressions lambda

Lorsque vous écrivez du code, vous utilisez probablement des pointeurs de fonction et des objets de fonction pour résoudre les problèmes et effectuer des calculs, en particulier quand vous utilisez des [algorithmes de bibliothèque standard C++](../standard-library/algorithms.md). Les pointeurs de fonction et les objets de fonction présentent chacun des avantages et des inconvénients. Par exemple, les pointeurs de fonction possèdent une charge mémoire syntaxique minimale, mais leur état n'est pas conservé au sein d'une portée. Les objets de fonction, quant à eux, peuvent conserver leur état, mais ils nécessitent la charge mémoire syntaxique d'une définition de classe.

Une expression lambda combine les avantages des pointeurs et des objets de fonction, tout en évitant leurs inconvénients. Tout comme les objets de fonction, les expressions lambda sont flexibles et peuvent conserver leur état. Toutefois, contrairement aux objets de fonction, leur syntaxe compacte ne requiert pas de définition de classe explicite. Grâce aux expressions lambda, votre code est moins encombré et moins sujet aux erreurs que le code nécessaire pour un objet de fonction équivalent.

Les exemples suivants comparent l'utilisation d'une expression lambda et d'un objet de fonction. Le premier exemple utilise une expression lambda pour afficher sur la console si chaque élément d'un objet `vector` est pair ou impair. Le deuxième exemple utilise un objet de fonction pour accomplir la même tâche.

## <a name="example-1-using-a-lambda"></a>Exemple 1 : Utilisation d'une expression lambda

Cet exemple passe une expression lambda à la fonction **for_each** . L'expression lambda imprime un résultat qui indique si chaque élément dans un objet `vector` est pair ou impair.

### <a name="code"></a>Code

```cpp
// even_lambda.cpp
// compile with: cl /EHsc /nologo /W4 /MTd
#include <algorithm>
#include <iostream>
#include <vector>
using namespace std;

int main()
{
   // Create a vector object that contains 9 elements.
   vector<int> v;
   for (int i = 1; i < 10; ++i) {
      v.push_back(i);
   }

   // Count the number of even numbers in the vector by
   // using the for_each function and a lambda.
   int evenCount = 0;
   for_each(v.begin(), v.end(), [&evenCount] (int n) {
      cout << n;
      if (n % 2 == 0) {
         cout << " is even " << endl;
         ++evenCount;
      } else {
         cout << " is odd " << endl;
      }
   });

   // Print the count of even numbers to the console.
   cout << "There are " << evenCount
        << " even numbers in the vector." << endl;
}
```

```Output
1 is odd
2 is even
3 is odd
4 is even
5 is odd
6 is even
7 is odd
8 is even
9 is odd
There are 4 even numbers in the vector.
```

### <a name="comments"></a>Commentaires

Dans l’exemple, le troisième argument de la fonction **for_each** est une expression lambda. La partie `[&evenCount]` spécifie la clause de capture de l'expression, `(int n)` spécifie la liste des paramètres, et la partie restante spécifie le corps de l'expression.

## <a name="example-2-using-a-function-object"></a>Exemple 2 : Utilisation d'un objet de fonction

Il arrive qu'une expression lambda soit trop complexe pour être utilisée autrement que dans l'exemple précédent. L’exemple suivant utilise un objet de fonction au lieu d’une expression lambda, ainsi que la fonction **for_each** , pour produire les mêmes résultats que l’exemple 1. Les deux exemples indiquent le nombre de chiffres pairs dans un objet `vector`. Pour conserver l'état de l'opération, la classe `FunctorClass` enregistre la variable `m_evenCount` par référence comme variable membre. Pour effectuer cette opération, `FunctorClass` implémente l’opérateur d’appel de fonction, **Operator ()**. Le compilateur Microsoft C++ génère du code dont la taille et les performances sont comparables à celles du code lambda de l’exemple 1. Pour un problème simple comme celui de cet article, la plus simple des expressions lambda convient probablement mieux qu'un objet de fonction. Toutefois, si vous pensez que les fonctionnalités peuvent nécessiter une expansion significative à l'avenir, il serait plus judicieux d'utiliser un objet de fonction afin que la maintenance du code soit facilitée.

Pour plus d’informations sur l' **opérateur ()**, consultez [appel de fonction](../cpp/function-call-cpp.md). Pour plus d’informations sur la fonction **for_each** , consultez [for_each](../standard-library/algorithm-functions.md#for_each).

### <a name="code"></a>Code

```cpp
// even_functor.cpp
// compile with: /EHsc
#include <algorithm>
#include <iostream>
#include <vector>
using namespace std;

class FunctorClass
{
public:
    // The required constructor for this example.
    explicit FunctorClass(int& evenCount)
        : m_evenCount(evenCount) { }

    // The function-call operator prints whether the number is
    // even or odd. If the number is even, this method updates
    // the counter.
    void operator()(int n) const {
        cout << n;

        if (n % 2 == 0) {
            cout << " is even " << endl;
            ++m_evenCount;
        } else {
            cout << " is odd " << endl;
        }
    }

private:
    // Default assignment operator to silence warning C4512.
    FunctorClass& operator=(const FunctorClass&);

    int& m_evenCount; // the number of even variables in the vector.
};

int main()
{
    // Create a vector object that contains 9 elements.
    vector<int> v;
    for (int i = 1; i < 10; ++i) {
        v.push_back(i);
    }

    // Count the number of even numbers in the vector by
    // using the for_each function and a function object.
    int evenCount = 0;
    for_each(v.begin(), v.end(), FunctorClass(evenCount));

    // Print the count of even numbers to the console.
    cout << "There are " << evenCount
        << " even numbers in the vector." << endl;
}
```

```Output
1 is odd
2 is even
3 is odd
4 is even
5 is odd
6 is even
7 is odd
8 is even
9 is odd
There are 4 even numbers in the vector.
```

## <a name="see-also"></a>Voir aussi

[Expressions lambda](../cpp/lambda-expressions-in-cpp.md)<br/>
[Exemples d’expressions lambda](../cpp/examples-of-lambda-expressions.md)<br/>
[automatiquement](../standard-library/algorithm-functions.md#generate)<br/>
[generate_n](../standard-library/algorithm-functions.md#generate_n)<br/>
[for_each](../standard-library/algorithm-functions.md#for_each)<br/>
[Spécifications d’exception (throw)](../cpp/exception-specifications-throw-cpp.md)<br/>
[Avertissement du compilateur (niveau 1) C4297](../error-messages/compiler-warnings/compiler-warning-level-1-c4297.md)<br/>
[Modificateurs spécifiques à Microsoft](../cpp/microsoft-specific-modifiers.md)
