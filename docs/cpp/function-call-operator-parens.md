---
title: "Opérateur d'appel de fonction : ()"
ms.date: 11/04/2016
helpviewer_keywords:
- ( ) function call operator
- function calls, C++ functions
- () function call operator
- postfix operators [C++]
- function calls, operator
- functions [C++], function-call operator
- function call operator ()
ms.assetid: 50c92e59-a4bf-415a-a6ab-d66c679ee80a
ms.openlocfilehash: 3194c34bacfe7b2ed758ab245c5858eadb18e64e
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/20/2019
ms.locfileid: "75301520"
---
# <a name="function-call-operator-"></a>Opérateur d'appel de fonction : ()

Une expression postfixer suivie de l’opérateur d’appel de fonction, **()** , spécifie un appel de fonction.

## <a name="syntax"></a>Syntaxe

```
postfix-expression
( [argument-expression-list ] )
```

## <a name="remarks"></a>Notes

Les arguments de l’opérateur d’appel de fonction sont zéro expression ou plus séparées par des virgules, les arguments réels de la fonction.

*Postfix-expression* doit correspondre à une adresse de fonction (par exemple, un identificateur de fonction ou la valeur d’un pointeur de fonction), et *argument-expression-List* est une liste d’expressions (séparées par des virgules) dont les valeurs (les arguments) sont passées à la fonction. L’argument *argument-expression-list* peut être vide.

*Postfix-expression* doit être de l’un des types suivants :

- Fonction retournant le type `T`. Voici un exemple de déclaration

    ```cpp
    T func( int i )
    ```

- Pointeur d'une fonction qui retourne le type `T`. Voici un exemple de déclaration

    ```cpp
    T (*func)( int i )
    ```

- Référence à une fonction qui retourne le type `T`. Voici un exemple de déclaration

    ```cpp
    T (&func)(int i)
    ```

- Déréférencement de fonction de pointeur de membre qui retourne le type `T`. Voici des exemples d'appels de fonction

    ```cpp
    (pObject->*pmf)();
    (Object.*pmf)();
    ```

## <a name="example"></a>Exemple

L’exemple suivant appelle la fonction de bibliothèque standard `strcat_s` avec trois arguments :

```cpp
// expre_Function_Call_Operator.cpp
// compile with: /EHsc

#include <iostream>
#include <string>

// C++ Standard Library name space
using namespace std;

int main()
{
    enum
    {
        sizeOfBuffer = 20
    };

    char s1[ sizeOfBuffer ] = "Welcome to ";
    char s2[ ] = "C++";

    strcat_s( s1, sizeOfBuffer, s2 );

    cout << s1 << endl;
}
```

```Output
Welcome to C++
```

## <a name="function-call-results"></a>Résultats de l'appel de fonction

Un appel de fonction prend une r-value, sauf si la fonction est déclarée en tant que type de référence. Les fonctions avec type de retour de référence ont des l-values et peuvent être utilisées à gauche d’une instruction d’assignation, comme suit :

```cpp
// expre_Function_Call_Results.cpp
// compile with: /EHsc
#include <iostream>
class Point
{
public:
    // Define "accessor" functions as
    // reference types.
    unsigned& x() { return _x; }
    unsigned& y() { return _y; }
private:
    unsigned _x;
    unsigned _y;
};

using namespace std;
int main()
{
    Point ThePoint;

    ThePoint.x() = 7;           // Use x() as an l-value.
    unsigned y = ThePoint.y();  // Use y() as an r-value.

    // Use x() and y() as r-values.
    cout << "x = " << ThePoint.x() << "\n"
         << "y = " << ThePoint.y() << "\n";
}
```

Le code précédent définit une classe appelée `Point`, qui contient des objets de données privés qui représentent les coordonnées *x* et *y* . Ces objets de données doivent être modifiés et leurs valeurs, récupérées. Ce programme n'est qu'une des nombreuses conceptions de ce type de classe ; l'utilisation des fonctions `GetX` et `SetX` ou `GetY` et `SetY` est une autre conception possible.

Les fonctions qui retournent des types de classe, des pointeurs vers des types de classe ou des références à des types de classe peuvent être utilisées comme opérande gauche pour les opérateurs de sélection de membres. Par conséquent, le code suivant est conforme :

```cpp
// expre_Function_Results2.cpp
class A {
public:
   A() {}
   A(int i) {}
   int SetA( int i ) {
      return (I = i);
   }

   int GetA() {
      return I;
   }

private:
   int I;
};

A func1() {
   A a = 0;
   return a;
}

A* func2() {
   A *a = new A();
   return a;
}

A& func3() {
   A *a = new A();
   A &b = *a;
   return b;
}

int main() {
   int iResult = func1().GetA();
   func2()->SetA( 3 );
   func3().SetA( 7 );
}
```

Les fonctions peuvent être appelées de manière récursive. Pour plus d’informations sur les déclarations de fonction, consultez [fonctions](functions-cpp.md). Le matériel associé se trouve dans [les unités de traduction et la liaison](../cpp/program-and-linkage-cpp.md).

## <a name="see-also"></a>Voir aussi

[Expressions suffixées](../cpp/postfix-expressions.md)<br/>
[Opérateurs intégrés, priorité et associativité C++](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[Appel de fonction ](../c-language/function-call-c.md)