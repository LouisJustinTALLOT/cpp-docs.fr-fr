---
title: if-else, instruction (C++)
description: Utilisez if-else, if-else avec initializer et les instructions If-constexpr pour contrôler la gestion des branches conditionnelles.
ms.date: 10/02/2020
f1_keywords:
- else_cpp
- if_cpp
helpviewer_keywords:
- if keyword [C++]
- else keyword [C++]
ms.assetid: f8c45cde-6bce-42ae-81db-426b3dbd4caa
ms.openlocfilehash: 20d828bf00a79687fe0a9fffbeb1a9cc56fae08c
ms.sourcegitcommit: 30792632548d1c71894f9fecbe2f554294b86020
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/06/2020
ms.locfileid: "91765297"
---
# <a name="if-else-statement-c"></a>if-else, instruction (C++)

Une instruction if-else contrôle la gestion des branches conditionnelles. Les instructions dans le *`if-branch`* sont exécutées uniquement si la valeur de est *`condition`* différente de zéro (ou **`true`** ). Si la valeur de *`condition`* est différente de zéro, l’instruction suivante est exécutée et l’instruction qui suit l’option facultative est **`else`** ignorée. Dans le cas contraire, l’instruction suivante est ignorée et, si c’est le cas, **`else`** l’instruction qui suit **`else`** est exécutée.

*`condition`* les expressions qui sont évaluées à une valeur différente de zéro sont :

- **`true`**
- pointeur non null,
- toute valeur arithmétique différente de zéro, ou
- type de classe qui définit une conversion non ambiguë en type arithmétique, booléen ou pointeur. (Pour plus d’informations sur les conversions, consultez [conversions standard](../cpp/standard-conversions.md).)

## <a name="syntax"></a>Syntaxe

*`init-statement`*:\
&emsp; *`expression-statement`*\
&emsp; *`simple-declaration`*

*`condition`*:\
&emsp; *`expression`*\
&emsp;*`attribute-specifier-seq`* <sub>*opt*</sub> *`decl-specifier-seq`* OPT *`declarator`**`brace-or-equal-initializer`*

*`statement`*:\
&emsp; *`expression-statement`*\
&emsp; *`compound-statement`*

*`expression-statement`*:\
&emsp;*`expression`* <sub>*OPT*</sub>**`;`**

*`compound-statement`*:\
&emsp;**`{`** *`statement-seq`* <sub>*OPT*</sub>**`}`**

*`statement-seq`*:\
&emsp; *`statement`*\
&emsp; *`statement-seq`* *`statement`*

*`if-branch`*:\
&emsp; *`statement`*

*`else-branch`*:\
&emsp; *`statement`*

*`selection-statement`*:\
&emsp;**`if`** **`constexpr`** <sub>*OPT*</sub><sup>17</sup> **`(`** *`init-statement`* <sub>*opt*</sub><sup>17</sup> opt *`condition`* **`)`***`if-branch`*\
&emsp;**`if`** **`constexpr`** <sub>*OPT*</sub><sup>17</sup> **`(`** *`init-statement`* <sub>*opt*</sub><sup>17</sup> opt *`condition`* **`)`** *`if-branch`* **`else`***`else-branch`*

<sup>17</sup> cet élément facultatif est disponible à partir de c++ 17.

## <a name="if-else-statements"></a>instructions if-else

Dans toutes les formes de l' **`if`** instruction, *`condition`* , qui peut avoir n’importe quelle valeur, à l’exception d’une structure, est évaluée, y compris tous les effets secondaires. Le contrôle passe de l' **`if`** instruction à l’instruction suivante dans le programme à moins que le soit exécuté ou qu’il ne *`if-branch`* *`else-branch`* contienne un [`break`](../cpp/break-statement-cpp.md) , [`continue`](../cpp/continue-statement-cpp.md) ou [`goto`](../cpp/goto-statement-cpp.md) .

La **`else`** clause d’une `if...else` instruction est associée à l’instruction précédente la plus proche **`if`** dans la même étendue qui n’a pas d' **`else`** instruction correspondante.

### <a name="example"></a>Exemple

Cet exemple de code illustre plusieurs **`if`** instructions en cours d’utilisation, avec et sans **`else`** :

```cpp
// if_else_statement.cpp
#include <iostream>

using namespace std;

class C
{
    public:
    void do_something(){}
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

## <a name="if-statement-with-an-initializer"></a><a name="if_with_init"></a> instruction if avec un initialiseur

À partir de C++ 17, une **`if`** instruction peut également contenir une *`init-statement`* expression qui déclare et Initialise une variable nommée. Utilisez cette forme de l’instruction if-lorsque la variable est uniquement requise dans la portée de l’instruction if. **Spécifique à Microsoft**: ce formulaire est disponible à partir de Visual Studio 2017 version 15,3, et nécessite au moins l' [`/std:c++17`](../build/reference/std-specify-language-standard-version.md) option de compilateur.

### <a name="example"></a>Exemple

```cpp
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

## <a name="a-nameif_constexpr-if-constexpr-statements"></a><a name="if_constexpr"> Si les instructions constexpr

À partir de C++ 17, vous pouvez utiliser une **`if constexpr`** instruction dans les modèles de fonction pour prendre des décisions de création de branche au moment de la compilation sans avoir à recourir à plusieurs surcharges de fonction. **Spécifique à Microsoft**: ce formulaire est disponible à partir de Visual Studio 2017 version 15,3, et nécessite au moins l' [`/std:c++17`](../build/reference/std-specify-language-standard-version.md) option de compilateur.

### <a name="example"></a>Exemple

Cet exemple montre comment vous pouvez écrire une seule fonction qui gère la décompression de paramètres. Aucune surcharge de paramètre zéro n’est nécessaire :

```cpp
template <class T, class... Rest>
void f(T&& t, Rest&&... r)
{
    // handle t
    do_something(t);

    // handle r conditionally
    if constexpr (sizeof...(r))
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

[Instructions de sélection](../cpp/selection-statements-cpp.md)\
[Mot](../cpp/keywords-cpp.md)\
[`switch` Instruction (C++)](../cpp/switch-statement-cpp.md)
