---
description: 'En savoir plus sur : opérateur d’appel de fonction : ()'
title: 'Opérateur d’appel de fonction : ()'
ms.date: 06/11/2020
helpviewer_keywords:
- ( ) function call operator
- function calls, C++ functions
- () function call operator
- postfix operators [C++]
- function calls, operator
- functions [C++], function-call operator
- function call operator ()
ms.assetid: 50c92e59-a4bf-415a-a6ab-d66c679ee80a
no-loc:
- opt
ms.openlocfilehash: 351674f345c7213a3c164ff88e9a165775088c68
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97344560"
---
# <a name="function-call-operator-"></a>Opérateur d'appel de fonction : ()

Un appel de fonction est un type de *`postfix-expression`* , formé par une expression qui prend la valeur d’une fonction ou d’un objet pouvant être appelé, suivi par l’opérateur d’appel de fonction, **`()`** . Un objet peut déclarer une `operator ()` fonction qui fournit la sémantique d’appel de fonction pour l’objet.

## <a name="syntax"></a>Syntaxe

> *`postfix-expression`*:\
> &emsp;*`postfix-expression`* **`(`** *`argument-expression-list`* <sub>opt</sub> **`)`**

## <a name="remarks"></a>Notes

Les arguments de l’opérateur d’appel de fonction proviennent d’un *`argument-expression-list`* , d’une liste d’expressions séparées par des virgules. Les valeurs de ces expressions sont passées à la fonction en tant qu’arguments. L' *argument-expression-List* peut être vide. Avant C++ 17, l’ordre d’évaluation de l’expression de fonction et des expressions d’argument n’est pas spécifié et peut se produire dans n’importe quel ordre. Dans C++ 17 et versions ultérieures, l’expression de fonction est évaluée avant toute expression d’argument ou argument par défaut. Les expressions d’arguments sont évaluées dans une séquence indéterminée.

*`postfix-expression`* Prend la valeur de la fonction à appeler. Il peut prendre l’une des formes suivantes :

- identificateur de fonction, visible dans la portée actuelle ou dans la portée de l’un des arguments de fonction fournis.
- expression qui prend la valeur d’une fonction, d’un pointeur de fonction, d’un objet pouvant être appelé ou d’une référence à une.
- accesseur de fonction membre, explicite ou implicite,
- pointeur déréférencé vers une fonction membre.

*`postfix-expression`* Peut être un identificateur de fonction surchargé ou un accesseur de fonction membre surchargé. Les règles de résolution de surcharge déterminent la fonction réelle à appeler. Si la fonction membre est virtuelle, la fonction à appeler est déterminée au moment de l’exécution.

Exemples de déclarations :

- Fonction retournant le type `T`. Voici un exemple de déclaration

    ```cpp
    T func( int i );
    ```

- Pointeur d'une fonction qui retourne le type `T`. Voici un exemple de déclaration

    ```cpp
    T (*func)( int i );
    ```

- Référence à une fonction qui retourne le type `T`. Voici un exemple de déclaration

    ```cpp
    T (&func)(int i);
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

Un appel de fonction prend la valeur Rvalue, sauf si la fonction est déclarée en tant que type référence. Les fonctions avec des types de retour de référence prennent la valeur lvalues. Ces fonctions peuvent être utilisées sur le côté gauche d’une instruction d’assignation, comme illustré ici :

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

Le code précédent définit une classe appelée `Point` , qui contient des objets de données privés qui représentent les coordonnées *x* et *y* . Ces objets de données doivent être modifiés et leurs valeurs, récupérées. Ce programme n'est qu'une des nombreuses conceptions de ce type de classe ; l'utilisation des fonctions `GetX` et `SetX` ou `GetY` et `SetY` est une autre conception possible.

Les fonctions qui retournent des types de classe, des pointeurs vers des types de classe ou des références à des types de classe peuvent être utilisées comme opérande gauche pour les opérateurs de sélection de membres. Le code suivant est légal :

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
[Opérateurs, priorité et associativité C++ intégrés](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[Appel de fonction](../c-language/function-call-c.md)
