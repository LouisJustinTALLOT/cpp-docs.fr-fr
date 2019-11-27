---
title: Conversions de types et sécurité de type
ms.date: 11/19/2019
ms.topic: conceptual
ms.assetid: 629b361a-2ce1-4700-8b5d-ab4f57b245d5
ms.openlocfilehash: dbca9057622ab1a92b74e2958b8dfbe8d810fede
ms.sourcegitcommit: 654aecaeb5d3e3fe6bc926bafd6d5ace0d20a80e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2019
ms.locfileid: "74246111"
---
# <a name="type-conversions-and-type-safety"></a>Conversions de types et sécurité de type

Ce document identifie les problèmes de conversion de type courants et explique comment les éviter dans C++ votre code.

Lorsque vous écrivez un C++ programme, il est important de s’assurer qu’il est de type sécurisé. Cela signifie que chaque variable, argument de fonction et valeur de retour de fonction stocke un type de données acceptable, et que les opérations qui impliquent des valeurs de types différents « ont un sens » et ne provoquent pas de perte de données, une interprétation incorrecte des modèles de bits ou altération de la mémoire. Un programme qui ne convertit jamais explicitement ou implicitement les valeurs d’un type en un autre est de type sécurisé par définition. Toutefois, les conversions de type, même les conversions non sûres, sont parfois nécessaires. Par exemple, vous devrez peut-être stocker le résultat d’une opération à virgule flottante dans une variable de type **int**, ou vous devrez peut-être passer la valeur d’un **entier** non signé à une fonction qui accepte un **entier**signé. Les deux exemples illustrent des conversions non sécurisées, car elles peuvent entraîner une perte de données ou une nouvelle interprétation d’une valeur.

Lorsque le compilateur détecte une conversion risquée, il émet une erreur ou un avertissement. Une erreur arrête la compilation. un avertissement permet à la compilation de continuer mais indique une erreur possible dans le code. Toutefois, même si votre programme est compilé sans avertissements, il peut toujours contenir du code qui entraîne des conversions de types implicites qui produisent des résultats incorrects. Les erreurs de type peuvent également être introduites par les conversions explicites, ou casts, dans le code.

## <a name="implicit-type-conversions"></a>Conversions de types implicites

Lorsqu’une expression contient des opérandes de types intégrés différents et qu’aucun cast explicite n’est présent, le compilateur utilise des *conversions standard* intégrées pour convertir l’un des opérandes afin que les types correspondent. Le compilateur essaie les conversions dans une séquence bien définie jusqu’à ce que l’un d’eux aboutisse. Si la conversion sélectionnée est une promotion, le compilateur n’émet pas d’avertissement. Si la conversion est un étroit, le compilateur émet un avertissement à propos de la perte possible de données. L’impossibilité de perdre des données dépend des valeurs réelles impliquées, mais nous vous recommandons de traiter cet avertissement comme une erreur. Si un type défini par l’utilisateur est impliqué, le compilateur essaie d’utiliser les conversions que vous avez spécifiées dans la définition de classe. S’il ne trouve pas de conversion acceptable, le compilateur émet une erreur et ne compile pas le programme. Pour plus d’informations sur les règles qui régissent les conversions standard, consultez [conversions standard](../cpp/standard-conversions.md). Pour plus d’informations sur les conversions définies par l’utilisateur, consultez [conversions définiesC++par l’utilisateur (/CLI)](../dotnet/user-defined-conversions-cpp-cli.md).

### <a name="widening-conversions-promotion"></a>Conversions étendues (promotion)

Dans une conversion étendue, une valeur dans une variable plus petite est assignée à une variable plus grande sans perte de données. Étant donné que les conversions étendues sont toujours sécurisées, le compilateur les exécute en mode silencieux et n’émet pas d’avertissements. Les conversions suivantes sont des conversions étendues.

|De|Pour|
|----------|--------|
|Tout type intégral signé ou non signé, à l’exception de **long long** ou **__int64**|**double**|
|**bool** ou **char**|Tout autre type intégré|
|**short** ou **wchar_t**|**int**, **long**, long **long**|
|**entier** **long**|**long long**|
|**float**|**double**|

### <a name="narrowing-conversions-coercion"></a>Conversions restrictives (contrainte)

Le compilateur effectue des conversions restrictives de manière implicite, mais il vous avertit de la perte potentielle de données. Prenez ces avertissements très au sérieux. Si vous êtes certain qu’aucune perte de données ne se produit parce que les valeurs de la variable plus grande sont toujours contenues dans la variable plus petite, ajoutez un cast explicite afin que le compilateur n’émette plus d’avertissement. Si vous n’êtes pas sûr que la conversion est sécurisée, ajoutez à votre code un certain type de vérification à l’exécution pour gérer la perte de données potentielle afin qu’il n’entraîne pas la génération de résultats incorrects par votre programme.

Toute conversion à partir d’un type à virgule flottante vers un type intégral est une conversion restrictive, car la partie fractionnaire de la valeur à virgule flottante est ignorée et perdue.

L’exemple de code suivant illustre certaines conversions restrictives implicites, ainsi que les avertissements que le compilateur émet pour eux.

```cpp
int i = INT_MAX + 1; //warning C4307:'+':integral constant overflow
wchar_t wch = 'A'; //OK
char c = wch; // warning C4244:'initializing':conversion from 'wchar_t'
              // to 'char', possible loss of data
unsigned char c2 = 0xfffe; //warning C4305:'initializing':truncation from
                           // 'int' to 'unsigned char'
int j = 1.9f; // warning C4244:'initializing':conversion from 'float' to
              // 'int', possible loss of data
int k = 7.7; // warning C4244:'initializing':conversion from 'double' to
             // 'int', possible loss of data
```

### <a name="signed---unsigned-conversions"></a>Conversions signées non signées

Un type intégral signé et son équivalent non signé sont toujours de la même taille, mais ils diffèrent dans la façon dont le modèle binaire est interprété pour la transformation de valeur. L’exemple de code suivant montre ce qui se produit lorsque le même modèle binaire est interprété comme une valeur signée et comme une valeur non signée. Le modèle binaire stocké à la fois dans `num` et `num2` ne change jamais de ce qui est indiqué dans l’illustration précédente.

```cpp
using namespace std;
unsigned short num = numeric_limits<unsigned short>::max(); // #include <limits>
short num2 = num;
cout << "unsigned val = " << num << " signed val = " << num2 << endl;
// Prints: unsigned val = 65535 signed val = -1

// Go the other way.
num2 = -1;
num = num2;
cout << "unsigned val = " << num << " signed val = " << num2 << endl;
// Prints: unsigned val = 65535 signed val = -1
```

Notez que les valeurs sont réinterprétées dans les deux directions. Si votre programme produit des résultats impairs dans lesquels le signe de la valeur semble inversée à partir de ce que vous attendez, recherchez les conversions implicites entre les types intégraux signés et non signés. Dans l’exemple suivant, le résultat de l’expression (0-1) est implicitement converti de **int** en **unsigned int** lorsqu’il est stocké dans `num`. Le modèle binaire est alors réinterprété.

```cpp
unsigned int u3 = 0 - 1;
cout << u3 << endl; // prints 4294967295
```

Le compilateur n’émet pas d’avertissement concernant les conversions implicites entre les types intégraux signés et non signés. Par conséquent, nous vous recommandons d’éviter totalement les conversions signées non signées. Si vous ne pouvez pas les éviter, ajoutez à votre code une vérification de l’exécution pour détecter si la valeur convertie est supérieure ou égale à zéro et inférieure ou égale à la valeur maximale du type signé. Les valeurs de cette plage seront transférées de signé à non signé ou de non signé à signé sans être réinterprété.

### <a name="pointer-conversions"></a>Conversions de pointeurs

Dans de nombreuses expressions, un tableau de style C est implicitement converti en un pointeur vers le premier élément du tableau, et les conversions de constantes peuvent se produire en mode silencieux. Bien que cela soit pratique, elle peut également être sujette aux erreurs. Par exemple, l’exemple de code suivant, mal conçu, semble absurde, mais il se compilera et produira un résultat de « p ». Tout d’abord, le littéral de constante de chaîne « Help » est converti en `char*` qui pointe vers le premier élément du tableau ; ce pointeur est ensuite incrémenté par trois éléments afin qu’il pointe maintenant vers le dernier élément « p ».

```cpp
char* s = "Help" + 3;
```

## <a name="explicit-conversions-casts"></a>Conversions explicites (CASTS)

En utilisant une opération de conversion, vous pouvez indiquer au compilateur de convertir une valeur d’un type en un autre type. Le compilateur génère une erreur dans certains cas si les deux types sont complètement non liés, mais dans d’autres cas, il ne génère pas d’erreur même si l’opération n’est pas de type sécurisé. Utilisez des casts avec modération, car toute conversion d’un type en un autre est une source potentielle d’erreur de programme. Toutefois, les casts sont parfois requis, et tous les casts ne sont pas tout aussi dangereux. Une utilisation efficace d’un cast est que votre code effectue une conversion restrictive et que vous savez que la conversion n’entraîne pas la génération de résultats incorrects par votre programme. En fait, cela indique au compilateur que vous savez ce que vous effectuez et à ne plus vous soucier des avertissements qui le concernent. Une autre utilisation consiste à effectuer un cast d’une classe pointeur vers une classe de type pointeur vers une classe de base. Une autre utilisation consiste à convertir le caractère **const**d’une variable pour la passer à une fonction qui requiert un argument non**const** . La plupart de ces opérations de conversion impliquent des risques.

Dans la programmation de style C, le même opérateur de cast de style C est utilisé pour tous les types de casts.

```cpp
(int) x; // old-style cast, old-style syntax
int(x); // old-style cast, functional syntax
```

L’opérateur de cast de style C est identique à l’opérateur d’appel () et est donc invisible dans le code et facile à oublier. Les deux sont incorrects, car ils sont difficiles à reconnaître d’un coup d’œil ou de recherche, et ils sont assez disparates pour appeler n’importe quelle combinaison de **static**, **const**et **reinterpret_cast**. Il peut être difficile et sujet aux erreurs de savoir ce que fait un cast de style ancien. Pour toutes ces raisons, lorsqu’un cast est requis, nous vous recommandons d’utiliser l’un des opérateurs C++ de cast suivants, qui, dans certains cas, sont beaucoup plus nombreux, et qui expriment beaucoup plus explicitement l’intention de programmation :

- **static_cast**, pour les casts qui sont vérifiés uniquement au moment de la compilation. **static_cast** retourne une erreur si le compilateur détecte que vous essayez d’effectuer un cast d’un type qui n’est pas totalement compatible. Vous pouvez également l’utiliser pour effectuer un cast entre pointeur vers base et pointeur vers dérivé, mais le compilateur ne peut pas toujours déterminer si ces conversions seront sécurisées au moment de l’exécution.

    ```cpp
    double d = 1.58947;
    int i = d;  // warning C4244 possible loss of data
    int j = static_cast<int>(d);       // No warning.
    string s = static_cast<string>(d); // Error C2440:cannot convert from
                                       // double to std:string

    // No error but not necessarily safe.
    Base* b = new Base();
    Derived* d2 = static_cast<Derived*>(b);
    ```

   Pour plus d’informations, consultez [static_cast](../cpp/static-cast-operator.md).

- **dynamic_cast**, pour les casts sécurisés et vérifiés par le runtime de pointeur vers base, en pointeur vers dérivé. Une **dynamic_cast** est plus sûre qu’une **static_cast** pour downcasts, mais la vérification du runtime entraîne une surcharge.

    ```cpp
    Base* b = new Base();

    // Run-time check to determine whether b is actually a Derived*
    Derived* d3 = dynamic_cast<Derived*>(b);

    // If b was originally a Derived*, then d3 is a valid pointer.
    if(d3)
    {
       // Safe to call Derived method.
       cout << d3->DoSomethingMore() << endl;
    }
    else
    {
       // Run-time check failed.
       cout << "d3 is null" << endl;
    }

    //Output: d3 is null;
    ```

   Pour plus d’informations, consultez [dynamic_cast](../cpp/dynamic-cast-operator.md).

- **const_cast**, pour effectuer un cast des **constantes const**d’une variable ou convertir une variable non**const** en **const**. La conversion d’un caractère **const**à l’aide de cet opérateur est tout aussi sujette aux erreurs que l’utilisation d’un cast de style C, à ceci près qu’avec **const-Cast** , vous êtes moins susceptible d’effectuer un cast accidentel. Parfois, vous devez effectuer un cast des **constantes const**d’une variable, par exemple, pour passer une variable **const** à une fonction qui accepte un paramètre non**const** . L'exemple suivant montre comment effectuer cette opération.

    ```cpp
    void Func(double& d) { ... }
    void ConstCast()
    {
       const double pi = 3.14;
       Func(const_cast<double&>(pi)); //No error.
    }
    ```

   Pour plus d’informations, consultez [const_cast](../cpp/const-cast-operator.md).

- **reinterpret_cast**, pour les casts entre des types non liés tels que le **pointeur** vers **int**.

    > [!NOTE]
    >  Cet opérateur de conversion n’est pas utilisé aussi souvent que les autres, et il n’est pas garanti qu’il soit portable à d’autres compilateurs.

   L’exemple suivant montre comment **reinterpret_cast** diffère de **static_cast**.

    ```cpp
    const char* str = "hello";
    int i = static_cast<int>(str);//error C2440: 'static_cast' : cannot
                                  // convert from 'const char *' to 'int'
    int j = (int)str; // C-style cast. Did the programmer really intend
                      // to do this?
    int k = reinterpret_cast<int>(str);// Programming intent is clear.
                                       // However, it is not 64-bit safe.
    ```

   Pour plus d’informations, consultez [Reinterpret_cast Operator](../cpp/reinterpret-cast-operator.md).

## <a name="see-also"></a>Voir aussi

[C++système de type](../cpp/cpp-type-system-modern-cpp.md)<br/>
[Bienvenue dansC++](../cpp/welcome-back-to-cpp-modern-cpp.md)<br/>
[Informations de référence sur le langage C++](../cpp/cpp-language-reference.md)<br/>
[Bibliothèque standard C++](../standard-library/cpp-standard-library-reference.md)
