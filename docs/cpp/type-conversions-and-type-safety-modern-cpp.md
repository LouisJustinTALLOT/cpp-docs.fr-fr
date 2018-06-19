---
title: Conversions de types et sécurité de Type (Modern C++) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 629b361a-2ce1-4700-8b5d-ab4f57b245d5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 13dabba7b7cfc769d91471c2dfc6f92f1b414996
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32424774"
---
# <a name="type-conversions-and-type-safety-modern-c"></a>Conversions de types et sécurité de type (Modern C++)
Ce document identifie les problèmes de conversion de type courants et explique comment les éviter dans votre code C++.  
  
 Lorsque vous écrivez un programme C++, il est important de s’assurer qu’il est de type sécurisé. Cela signifie que chaque variable, argument de fonction et stocke un type acceptable de données de valeur de retour de fonction, et que les opérations qui impliquent des valeurs de types différents « sens » et ne provoquent pas la perte de données, mauvaise interprétation des modèles de bits, ou altération de la mémoire. Un programme qui convertit jamais explicitement ou implicitement les valeurs d’un type à l’autre est de type sécurisé par définition. Toutefois, conversions de type, même les conversions unsafe, sont parfois nécessaires. Par exemple, vous devrez peut-être stocker le résultat de flottante pointez l’opération dans une variable de type `int`, ou vous devrez peut-être passer la valeur non signée `int` à une fonction qui accepte un signé `int`. Les deux exemples illustrent les conversions non sécurisées, car elles peuvent entraîner une perte de données ou nouvelle interprétation d’une valeur.  
  
 Lorsque le compilateur détecte une conversion non sécurisée, il émet une erreur ou un avertissement. Une erreur arrête la compilation ; un avertissement permet à la compilation continuer, mais indique une erreur possible dans le code. Toutefois, même si votre programme est compilé sans avertissements, il reste peut contenir du code qui aboutissent à des conversions de types implicites qui produisent des résultats incorrects. Erreurs de type peuvent également être introduites par les conversions explicites, ou casts, dans le code.  
  
## <a name="implicit-type-conversions"></a>Conversions de types implicites  
 Lorsqu’une expression contient des opérandes de différents types intégrés, et aucune des casts explicites ne sont présents, le compilateur utilise intégrées *conversions standard* de convertir l’un des opérandes afin que les types correspondent. Le compilateur tente des conversions dans un ordre bien défini jusqu'à ce qu’un d’eux réussisse. Si la conversion sélectionnée est une promotion, le compilateur n’émet pas d’avertissement. Si la conversion est un restrictives, le compilateur émet un avertissement concernant les pertes de données possibles. Si une perte de données réel se produit dépend des valeurs réelles impliquées, mais nous vous recommandons de vous traiter cet avertissement comme une erreur. Si un type défini par l’utilisateur est impliqué, le compilateur tente d’utiliser les conversions que vous avez spécifié dans la définition de classe. S’il ne trouve pas une conversion acceptable, le compilateur génère une erreur et ne compile pas le programme. Pour plus d’informations sur les règles qui régissent les conversions standard, consultez [Conversions Standard](../cpp/standard-conversions.md). Pour plus d’informations sur les conversions définies par l’utilisateur, consultez [les Conversions définies par l’utilisateur (C + c++ / CLI)](../dotnet/user-defined-conversions-cpp-cli.md).  
  
### <a name="widening-conversions-promotion"></a>Conversions (promotion) étendues  
 Dans une conversion étendue, une valeur dans une plus petite variable est attribuée à une variable supérieure sans perte de données. Étant donné que les conversions étendues sont toujours sécurisées, le compilateur effectue en mode silencieux et n’émet pas d’avertissements. Les conversions suivantes sont des conversions étendues.  
  
|From|À|  
|----------|--------|  
|Tout signés ou non signés de type intégral sauf `long long` ou `__int64`|`double`|  
|`bool` ou `char`|Tout autre type intégré|  
|`short` ou `wchar_t`|`int`, `long`, `long long`|  
|`int`, `long`|`long long`|  
|`float`|`double`|  
  
### <a name="narrowing-conversions-coercion"></a>Conversions restrictives (contrainte)  
 Le compilateur effectue des conversions restrictives implicitement, mais il vous avertit de perdre des données. Prendre ces avertissements très au sérieux. Si vous êtes certain qu’aucune perte de données ne se produit, car les valeurs dans la variable plus grande sont toujours ajusté dans la variable plus petite, puis ajoutez une conversion explicite afin que le compilateur émet un avertissement n’est plus. Si vous n’êtes pas certain que la conversion est sécurisée, ajoutez à votre code une sorte de vérification de l’exécution pour gérer la perte de données afin qu’elle n’entraîne pas de votre programme à produire des résultats incorrects. 
  
 Toute conversion flottante point type vers un type intégral est une conversion restrictive, car la valeur du point de la partie fractionnaire de flottante est ignorée et a perdu.  
  
 L’exemple de code suivant montre certaines implicite conversions restrictives lors des conversions et les avertissements générés par le compilateur émet pour eux.  
  
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
  
### <a name="signed---unsigned-conversions"></a>Signé - conversions non signés  
 Un type intégral signé et son équivalent non signé sont toujours la même taille, mais elles diffèrent dans la façon dont le modèle binaire est interprété pour la transformation de la valeur. L’exemple de code suivant montre ce qui se passe lorsque le même modèle de bits est interprété comme une valeur signée et comme une valeur non signée. Le modèle de bits stocké dans les deux `num` et `num2` ne change jamais à partir de ce qui est affiché dans l’illustration précédente.  
  
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
  
 Notez que les valeurs sont réinterprétées dans les deux sens. Si votre programme produit des résultats impairs dans lequel le signe de la valeur semble inversées par rapport à vos attentes, recherchez les conversions implicites entre les types intégraux signés et non signés. Dans l’exemple suivant, le résultat de l’expression (0 - 1) est converti implicitement `int` à `unsigned int` lorsqu’il est stocké dans `num`. Cela entraîne le modèle binaire qui doit être réinterprétée.  
  
```cpp  
unsigned int u3 = 0 - 1;  
cout << u3 << endl; // prints 4294967295  
  
```  
  
 Le compilateur ne pas avertit à propos des conversions implicites entre les types intégraux signés et non signés. Par conséquent, nous vous recommandons d’éviter signed à unsigned des conversions complètement. Si vous ne pouvez pas éviter les, puis ajouter à votre code une vérification à l’exécution pour détecter si la valeur convertie est supérieure ou égale à zéro et inférieur ou égal à la valeur maximale du type signé. Les valeurs dans cette plage transfère de signé en non signé ou de non signé en signé sans être réinterprétée.  
  
### <a name="pointer-conversions"></a>Conversions de pointeurs  
 Dans de nombreuses expressions, un tableau de style C est implicitement converti en un pointeur vers le premier élément du tableau et conversions de constantes peuvent se produire en mode silencieux. Bien que cela est pratique, il est également sujette aux erreurs. Par exemple, l’exemple suivant mal conçues semble absurde et encore, il sera compilé dans Visual C++ et produit un résultat de « p ». Tout d’abord, le littéral de chaîne constant « Help » est converti en un `char*` qui pointe vers le premier élément du tableau ; ce pointeur est ensuite incrémenté de trois éléments afin qu’elle pointe vers la dernière élément « p ».  
  
```cpp  
char* s = "Help" + 3;  
  
```  
  
## <a name="explicit-conversions-casts"></a>Conversions explicites (casts)  
 En utilisant une opération de conversion, vous pouvez indiquer au compilateur de convertir une valeur d’un type en un autre type. Le compilateur génère une erreur dans certains cas si les deux types sont complètement indépendants, mais dans d’autres cas elle ne déclenche pas une erreur même si l’opération n’est pas un type sécurisé. Utiliser des casts avec parcimonie, car une conversion d’un type est une source potentielle d’erreurs de programme. Toutefois, les casts sont parfois nécessaires, et pas tous les casts sont également dangereux. Une utilisation efficace d’une conversion est lorsque votre code effectue une conversion restrictive et que vous savez que la conversion n’est pas dû à votre programme à produire des résultats incorrects. En effet, cela indique au compilateur que vous savez que vous effectuez et d’arrêt vous déranger avec des avertissements sur elle. Une autre utilisation est converti à partir d’une classe de pointeur vers dérivé en une classe de base de pointeur. Une autre utilisation consiste à caster la `const`- nature d’une variable pour passer à une fonction qui nécessite un non -`const` argument. La plupart de ces opérations de conversion implique un risque.  
  
 Dans la programmation de style C, l’opérateur de cast de style C même est utilisé pour tous les types de conversions.  
  
```cpp  
(int) x; // old-style cast, old-style syntax  
int(x); // old-style cast, functional syntax  
  
```  
  
 L’opérateur de cast de style C est identique à l’opérateur d’appel () et est donc discrète dans le code et facile d’oublier. Les deux sont incorrectes, car ils sont difficiles à reconnaître à le œil ou recherchez pour, et elles sont suffisamment disparates à appeler n’importe quelle combinaison de `static`, `const`, et `reinterpret_cast`. Essayer de comprendre ce que fait un cast de style ancien peut être difficile et sujette à erreurs. Pour toutes ces raisons, lorsqu’un cast est requis, nous vous recommandons d’utiliser un des opérateurs de cast C++ suivants, qui, dans certains cas sont considérablement plus de type sécurisé et qui expriment beaucoup plus explicitement l’intention de programmation :  
  
-   `static_cast`, des casts sont vérifiées à la compilation de l’heure seulement. `static_cast` Retourne une erreur si le compilateur détecte que vous tentez d’effectuer un cast entre des types qui ne sont pas complètement compatibles. Vous pouvez également l’utiliser pour effectuer un cast entre un pointeur vers base et de pointeur vers dérivé, mais le compilateur ne peut pas toujours déterminer si ces conversions est sécurisées lors de l’exécution.  
  
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
  
-   `dynamic_cast`, des casts sécurisés, vérifiée au moment de l’exécution d’un pointeur vers la base de pointeur vers dérivé. A `dynamic_cast` est plus sûre qu’un `static_cast` pour downcasts, mais l’exécution du contrôle entraîne une certaine charge.  
  
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
  
-   `const_cast`, pour effectuer le cast immédiatement la `const`- caractère d’une variable, ou lors de la conversion d’un non -`const` variable comme étant `const`. Cast `const`-nature à l’aide de cet opérateur est simplement comme erreurs qu’utilise un cast, à ceci près qu’avec C-style `const-cast` sont moins susceptibles d’effectuer le cast accidentellement. Parfois, vous devez caster le `const`-nature d’une variable, par exemple, pour passer un `const` variable à une fonction qui accepte un non -`const` paramètre. L'exemple suivant montre comment effectuer cette opération.  
  
    ```cpp  
    void Func(double& d) { ... }  
    void ConstCast()  
    {  
       const double pi = 3.14;  
       Func(const_cast<double&>(pi)); //No error.  
    }  
  
    ```  
  
     Pour plus d’informations, consultez [const_cast](../cpp/const-cast-operator.md).  
  
-   `reinterpret_cast`, des informations sur les casts entre types tels que `pointer` à `int`.  
  
    > [!NOTE]
    >  Cet opérateur de cast n’est pas utilisé aussi souvent que les autres, et il n’a pas systématiquement à d’autres compilateurs.  
  
     L’exemple suivant illustre comment `reinterpret_cast` diffère `static_cast`.  
  
    ```cpp  
    const char* str = "hello";  
    int i = static_cast<int>(str);//error C2440: 'static_cast' : cannot  
                                  // convert from 'const char *' to 'int'  
    int j = (int)str; // C-style cast. Did the programmer really intend  
                      // to do this?  
    int k = reinterpret_cast<int>(str);// Programming intent is clear.  
                                       // However, it is not 64-bit safe.  
  
    ```  
  
     Pour plus d’informations, consultez [opérateur reinterpret_cast](../cpp/reinterpret-cast-operator.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Système de Type C++](../cpp/cpp-type-system-modern-cpp.md)   
 [Bienvenue dans C++](../cpp/welcome-back-to-cpp-modern-cpp.md)   
 [Référence du langage C++](../cpp/cpp-language-reference.md)   
 [Bibliothèque C++ standard](../standard-library/cpp-standard-library-reference.md)