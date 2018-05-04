---
title: if-else, instruction (C++) | Documents Microsoft
ms.custom: ''
ms.date: 07/17/2017
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- else_cpp
- if_cpp
dev_langs:
- C++
helpviewer_keywords:
- if keyword [C++]
- else keyword [C++]
- if keyword [C++], if-else
ms.assetid: f8c45cde-6bce-42ae-81db-426b3dbd4caa
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8de2511096766cc4852c1c612eccb7dc65713218
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="if-else-statement-c"></a>if-else, instruction (C++)
Contrôles création de branches conditionnelles. Les instructions dans le *-bloc if* sont exécutés uniquement si la *expression if* prend une valeur différente de zéro (ou `true`). Si la valeur de *expression* est différent de zéro, *statement1* et toutes les autres instructions du bloc sont exécutées et l’autre bloc, le cas échéant, est ignoré. Si la valeur de *expression* est égal à zéro, puis le bloc if est ignoré et l’autre bloc, le cas échéant, est exécuté. Sont des expressions qui correspondent à zéro
- `true`
- un pointeur non null,
- toute valeur arithmétique différente de zéro, ou 
- type d’un type de classe qui définit une conversion non ambiguë en arithmétique, booléen ou pointeur. (Pour plus d’informations sur les conversions, consultez [Conversions Standard](../cpp/standard-conversions.md).)   
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
if ( expression )  
{
   statement1;
   ...  
}
else  // optional
{
   statement2;
   ...
} 

// Visual Studio 2017 version 15.3 and later:
if ( initialization; expression )  
{
   statement1;
   ...  
}
else  // optional
{
   statement2;
   ...
}  

// Visual Studio 2017 version 15.3 and later:
if constexpr (expression)
{
    statement1;
    ...
}
else  // optional
{
   statement2;
   ...
} 
```  
## <a name="example"></a>Exemple  
```  
// if_else_statement.cpp  
#include <iostream>

using namespace std;

class C
{
    public:
    void do_somthing(){}
};
void init(C){}
bool is_true() { return true; }
int x = 10;

int main()
{
    if (is_true())
    {
        cout << "b is true!\n";  // executed
    }
    else
    {
        cout << "b is false!\n";
    }

  // no else statement
    if (x == 10)
    {
        x = 0; 
    }
    
  
    C* c;
  init(c);
    if (c)
    {
        c->do_something();
    }
    else
    {
        cout << "c is null!\n";
    }
}
```  
## <a name="if-statement-with-an-initializer"></a>Si l’instruction avec un initialiseur
**Visual Studio 2017 15,3 et versions ultérieures** (disponible avec [/std : c ++ 17](../build/reference/std-specify-language-standard-version.md)) : un **si** instruction peut également contenir une expression qui déclare et initialise une variable nommée. Utilisez cette forme de l’instruction if lorsque la variable est nécessaire uniquement dans la portée du bloc-if. 

```cpp
## Example  
#include <iostream>
#include <mutex>
#include <map>
#include <string>
#include <algorithm>


using namespace std;

map<int, string> m;
mutex mx;
bool shared_flag; // guarded by mx
void unsafe_operation() {}

int main()
{

    if (auto it = m.find(10); it != m.end())
    {
        cout << it->second;
        return 0;
    }

    if (char buf[10]; fgets(buf, 10, stdin))
    {
        m[0] += buf;
    }

    if (lock_guard<mutex> lock(mx); shared_flag)
    {
        unsafe_operation();
        shared_flag = false;
    }


    string s{ "if" };
    if (auto keywords = { "if", "for", "while" }; any_of(keywords.begin(), keywords.end(), [&s](const char* kw) { return s == kw; }))
    {
        cout << "Error! Token must not be a keyword\n";
    }

}
```

 Dans toutes les formes de la **si** instruction, *expression*, qui peut avoir n’importe quelle valeur sauf une structure, est évaluée, y compris tous les effets. Le contrôle passe à partir de la **si** instruction à l’instruction suivante dans le programme, sauf si un de la *instruction*s contient un [saut](../cpp/break-statement-cpp.md), [continuer](../cpp/continue-statement-cpp.md), ou [goto](../cpp/goto-statement-cpp.md).  
  
 Le **else** clause d’une `if...else` instruction est associée à la plus proche précédente **si** instruction dans la même portée que ne pas correspondre à une **else** instruction.   

## <a name="constexpr-if-statements"></a>constexpr si les instructions
**Visual Studio 2017 15,3 et versions ultérieures** (disponible avec [/std : c ++ 17](../build/reference/std-specify-language-standard-version.md)) : dans les modèles de fonction, vous pouvez utiliser un **constexpr si** à prendre des décisions de création de branche lors de la compilation sans instruction avoir recours à plusieurs surcharges de fonction. Par exemple, vous pouvez écrire une fonction unique ce paramètre de handles décompression (aucune surcharge de paramètre de zéro n’est nécessaire) : 

```cpp
template <class T, class... Rest>
void f(T&& t, Rest&&... r)
{
// handle t
   do_something(t);

   // handle r conditionally
   constexpr if (sizeof...(r)) 
   {
      
      f(r...); 
   }
   else
   {
       g(r...);
   }
}
```

  
 
## <a name="see-also"></a>Voir aussi  
 [Instructions de sélection](../cpp/selection-statements-cpp.md)   
 [Mots clés](../cpp/keywords-cpp.md)   
 [switch, instruction (C++)](../cpp/switch-statement-cpp.md)