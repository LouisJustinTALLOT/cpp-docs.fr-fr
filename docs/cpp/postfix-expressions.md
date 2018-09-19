---
title: Expressions suffixées | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- operators [C++], postfix
- postfix expressions
- expressions [C++], postfix
ms.assetid: 7ac62a57-06df-422f-b012-a75b37d7cb9b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 77bcb8257fc6907b48330301cf009fa44f00578d
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46082531"
---
# <a name="postfix-expressions"></a>Expressions suffixées

Les expressions suffixées se composent d'expressions primaires ou d'expressions dans lesquelles les opérateurs suffixés suivent une expression primaire. Les opérateurs suffixés sont répertoriées dans le tableau suivant.

### <a name="postfix-operators"></a>Opérateurs suffixés

|Nom d'opérateur|Notation de l'opérateur|
|-------------------|-----------------------|
|[Opérateur d’indice](../cpp/subscript-operator.md)|**[ ]**|
|[Opérateur d’appel de fonction](../cpp/function-call-operator-parens.md)|**( )**|
|[Opérateur de conversion de type explicite](../cpp/explicit-type-conversion-operator-parens.md)|*nom de type* **)**|
|[Opérateur d’accès au membre](../cpp/member-access-operators-dot-and.md)|**.** Ou **->**|
|[Opérateur d’Incrément suffixé](../cpp/postfix-increment-and-decrement-operators-increment-and-decrement.md)|**++**|
|[Opérateur de décrémentation suffixé](../cpp/postfix-increment-and-decrement-operators-increment-and-decrement.md)|**--**|

La syntaxe suivante décrit les expressions suffixées possibles :

```
primary-expression 
postfix-expression[expression]postfix-expression(expression-list)simple-type-name(expression-list)postfix-expression.namepostfix-expression->namepostfix-expression++postfix-expression--cast-keyword < typename > (expression )typeid ( typename )
```

Le *postfix-expression* ci-dessus peut être une expression primaire ou une autre expression suffixée.  Consultez **expressions primaires**.  Les expressions suffixées sont regroupées de gauche à droite. Elles peuvent ainsi être chaînées les unes aux autres comme suit :

```cpp
func(1)->GetValue()++
```

Dans l’expression ci-dessus, `func` est une expression primaire, `func(1)` est une expression de fonction suffixée, `func(1)->GetValue` est une expression suffixée spécifiant un membre de la classe, `func(1)->GetValue()` est une autre expression de fonction suffixée et l’ensemble expression est une expression suffixée incrémentant la valeur de retour de GetValue.  L’expression entière signifie : Appeler fonction passant 1 comme argument et obtenir un pointeur vers une classe comme valeur de retour.  Appelez ensuite `GetValue()` sur cette classe, puis incrémenter la valeur retournée.

Les expressions répertoriées ci-dessus sont des expressions d'assignation, ce qui signifie que le résultat de ces expressions doit être une r-value.

Forme de l'expression suffixée

```cpp
simple-type-name ( expression-list )
```

indique l'appel du constructeur.  Si le nom-type-simple est un type fondamental, la liste d'expressions doit être une expression unique, et cette expression montre un cast de la valeur de l'expression au type fondamental.  Ce type d'expression de cast simule un constructeur.  Cette forme permet aux classes et aux types fondamentaux d'être construits à l'aide de la même syntaxe. Elle est donc particulièrement utile lorsque vous définissez des classes de modèles.

Le *mot clé cast* est un des **dynamic_cast**, **static_cast** ou **reinterpret_cast**.  Vous trouverez plus d’informations dans **dynamic_cast**, **static_cast** et **reinterpet_cast**.

Le **typeid** opérateur est considéré comme une expression suffixée.  Consultez **opérateur typeid**.

## <a name="formal-and-actual-arguments"></a>Arguments formels et arguments réels

Les programmes appelants passent des informations aux fonctions appelées dans des « arguments réels ». Les fonctions appelées accèdent aux informations à l'aide des « arguments formels » correspondants.

Lorsqu’une fonction est appelée, les tâches suivantes sont effectuées :

- Tous les arguments réels (ceux fournis par l’appelant) sont évalués. Il n'y a pas d'ordre implicite dans lequel ces arguments sont évalués, mais ils sont tous évalués et les effets secondaires sont résolus avant l'entrée dans la fonction.

- Chaque argument formel est initialisé avec son argument réel correspondant dans la liste d'expressions. (Un argument formel est un argument déclaré dans l'en-tête de fonction et utilisé dans le corps d'une fonction.) Les conversions sont effectuées suite à une initialisation — les conversions standard et celles définies par l’utilisateur sont exécutées en convertissant un argument réel en type correct. L'initialisation exécutée est illustrée conceptuellement par le code suivant :

    ```cpp
    void Func( int i ); // Function prototype
    ...
    Func( 7 );          // Execute function call
    ```

     Les initialisations conceptuelles avant l'appel sont :

    ```cpp
    int Temp_i = 7;
    Func( Temp_i );
    ```

     Notez que l'initialisation est exécutée comme si la syntaxe de signe égal était utilisée au lieu de la syntaxe de parenthèses. Une copie de `i` est effectuée avant de passer la valeur à la fonction. (Pour plus d’informations, consultez [initialiseurs](../cpp/initializers.md) et [Conversions](../cpp/user-defined-type-conversions-cpp.md)).

     Par conséquent, si le prototype de fonction (déclaration) fait appel à un argument de type **long**, et si le programme appelant fournit un argument réel de type **int**, l’argument réel est promu à l’aide un conversion de type standard vers le type **long** (consultez [Conversions Standard](../cpp/standard-conversions.md)).

     C’est une erreur de fournir un argument réel pour lequel il n’existe aucune conversion standard ou définie par l’utilisateur au type de l’argument formel.

     Pour les arguments réels du type classe, l’argument formel est initialisé en appelant le constructeur de la classe. (Consultez [constructeurs](../cpp/constructors-cpp.md) pour plus d’informations sur ces fonctions de membre de classe spéciale.)

- L'appel de fonction est exécuté.

Le fragment de programme suivant montre un appel de fonction :

```cpp
// expre_Formal_and_Actual_Arguments.cpp
void func( long param1, double param2 );

int main()
{
    long i = 1;
    double j = 2;

    // Call func with actual arguments i and j.
    func( i, j );
}

// Define func with formal parameters param1 and param2.
void func( long param1, double param2 )
{
}
```

Lorsque `func` est appelée à partir de main, le paramètre formel `param1` est initialisé avec la valeur de `i` (`i` est converti en type **long** pour correspondre au type correct à l’aide d’une norme conversion) et le paramètre formel `param2` est initialisé avec la valeur de `j` (`j` est converti en type **double** à l’aide d’une conversion standard).

## <a name="treatment-of-argument-types"></a>Traitement des types d’arguments

Les arguments formels déclarés en tant que types const ne peuvent pas être modifiés dans le corps d’une fonction. Fonctions peuvent modifier tout argument qui n’est pas de type **const**. Toutefois, la modification est locale à la fonction et n’affecte pas la valeur d’argument réel, sauf si l’argument réel faisait référence à un objet pas de type **const**.

Les fonctions suivantes illustrent certains de ces concepts :

```cpp
// expre_Treatment_of_Argument_Types.cpp
int func1( const int i, int j, char *c ) {
   i = 7;   // C3892 i is const.
   j = i;   // value of j is lost at return
   *c = 'a' + j;   // changes value of c in calling function
   return i;
}

double& func2( double& d, const char *c ) {
   d = 14.387;   // changes value of d in calling function.
   *c = 'a';   // C3892 c is a pointer to a const object.
    return d;
}
```

## <a name="ellipses-and-default-arguments"></a>Ellipses et arguments par défaut

Les fonctions peuvent être déclarées pour accepter moins d'arguments que le nombre spécifié dans la définition de fonction, en utilisant l'une des deux méthodes suivantes : points de suspension (`...`) ou arguments par défaut.

Les points de suspension indiquent que des arguments peuvent être requis mais que leur nombre et leurs types ne sont pas spécifiés dans la déclaration. C'est habituellement une mauvaise pratique de programmation C++ car elle occulte l'un des avantages du C++ : la sécurité de type. Différentes conversions sont appliquées aux fonctions déclarées avec des points de suspension par rapport aux fonctions pour lesquelles les types d’argument formels et réels sont connus :

- Si l’argument réel est de type **float**, il est promu au type **double** avant l’appel de fonction.

- N’importe quel signé ou non signé **char**, **court**, type énuméré ou champ de bits est converti en signée ou non signée **int** à l’aide de la promotion intégrale.

- Tout argument de type classe est transmis par valeur comme une structure de données. La copie est créée par copie binaire plutôt que par appel d’un constructeur de copie de la classe (le cas échéant).

Les points de suspension, s’ils sont utilisés, doivent être déclarés en dernier dans la liste d’arguments. Pour plus d’informations sur la transmission d’un nombre variable d’arguments, consultez la discussion de [va_arg, va_start et va_list](../c-runtime-library/reference/va-arg-va-copy-va-end-va-start.md) dans le *Run-Time Library Reference*.

Pour plus d’informations sur les arguments par défaut dans la programmation CLR, consultez [listes d’arguments variables (...) (C + C++ / CLI) ](../windows/variable-argument-lists-dot-dot-dot-cpp-cli.md).

Les arguments par défaut vous permettent de spécifier la valeur qu’un argument doit prendre si aucune n’est fournie dans l’appel de fonction. Le fragment de code suivant montre le fonctionnement des arguments par défaut. Pour plus d’informations sur les restrictions sur la spécification des arguments par défaut, consultez [Arguments par défaut](../cpp/default-arguments.md).

```cpp
// expre_Ellipses_and_Default_Arguments.cpp
// compile with: /EHsc
#include <iostream>

// Declare the function print that prints a string,
// then a terminator.
void print( const char *string,
            const char *terminator = "\n" );

int main()
{
    print( "hello," );
    print( "world!" );

    print( "good morning", ", " );
    print( "sunshine." );
}

using namespace std;
// Define print.
void print( const char *string, const char *terminator )
{
    if( string != NULL )
        cout << string;

    if( terminator != NULL )
        cout << terminator;
}
```

Le programme précédent déclare une fonction, `print`, qui accepte deux arguments. Toutefois, le deuxième argument, *terminateur*, a la valeur par défaut, `"\n"`. Dans `main`, les deux premiers appels à `print` autoriser le deuxième argument par défaut fournir une nouvelle ligne pour terminer la chaîne imprimée. Le troisième appel indique une valeur explicite pour le deuxième argument. Le résultat généré par le programme est

```Output
hello,
world!
good morning, sunshine.
```

## <a name="see-also"></a>Voir aussi

[Types d’expressions](../cpp/types-of-expressions.md)