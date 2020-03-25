---
title: if-else, instruction (C++)
ms.date: 07/20/2019
description: Utilisez les instructions if-else C++ dans pour contrôler la gestion des branches conditionnelles.
f1_keywords:
- else_cpp
- if_cpp
helpviewer_keywords:
- if keyword [C++]
- else keyword [C++]
ms.assetid: f8c45cde-6bce-42ae-81db-426b3dbd4caa
ms.openlocfilehash: fd2736d80d68249773c9aa6cf7cb9edffdaadac4
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80178429"
---
# <a name="if-else-statement-c"></a>if-else, instruction (C++)

Contrôle la branche conditionnelle. Les instructions du *bloc If* ne sont exécutées que si l' *expression if-expression* prend la valeur d’une valeur différente de zéro (ou true). Si la valeur de l' *expression* est différente de zéro, *instruction1* et toutes les autres instructions du bloc sont exécutées et le bloc Else, s’il est présent, est ignoré. Si la valeur de l' *expression* est égale à zéro, le bloc If est ignoré et le bloc Else, s’il est présent, est exécuté. Les expressions qui sont évaluées à une valeur différente de zéro sont

- TRUE
- pointeur non null,
- toute valeur arithmétique différente de zéro, ou
- type de classe qui définit une conversion non ambiguë en type arithmétique, booléen ou pointeur. (Pour plus d’informations sur les conversions, consultez [conversions standard](../cpp/standard-conversions.md).)

## <a name="syntax"></a>Syntaxe

```cpp
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

// C++17 - Visual Studio 2017 version 15.3 and later:
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

// C++17 - Visual Studio 2017 version 15.3 and later:
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

## <a name="if-statement-with-an-initializer"></a><a name="if_with_init"></a>instruction if avec un initialiseur

**Visual Studio 2017 version 15,3 et versions ultérieures** (disponibles avec [/std : c++ 17](../build/reference/std-specify-language-standard-version.md)) : une instruction **If** peut également contenir une expression qui déclare et Initialise une variable nommée. Utilisez cette forme de l’instruction if si la variable est uniquement requise dans la portée du bloc If.

## <a name="example"></a>Exemple

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

Dans toutes les formes de l’instruction **If** , *expression*, qui peut avoir n’importe quelle valeur à l’exception d’une structure, est évaluée, y compris tous les effets secondaires. Le contrôle passe de l’instruction **If** à l’instruction suivante dans le programme, sauf si l’une des *instructions*contient une instruction [break](../cpp/break-statement-cpp.md), [continue](../cpp/continue-statement-cpp.md)ou [goto](../cpp/goto-statement-cpp.md).

La clause **else** d’une instruction `if...else` est associée à l’instruction **If** précédente la plus proche dans la même portée qui n’a pas d’instruction **else** correspondante.

## <a name="a-nameif_constexpr-if-constexpr-statements"></a><a name="if_constexpr"> si les instructions constexpr

**Visual Studio 2017 version 15,3 et versions ultérieures** (disponibles avec [/std : c++ 17](../build/reference/std-specify-language-standard-version.md)) : dans les modèles de fonction, vous pouvez utiliser une instruction **If constexpr** pour prendre des décisions de création de branche au moment de la compilation sans avoir à recourir à plusieurs surcharges de fonction. Par exemple, vous pouvez écrire une seule fonction qui gère la décompression des paramètres (aucune surcharge de paramètre zéro n’est nécessaire) :

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

[Instructions de sélection](../cpp/selection-statements-cpp.md)<br/>
[Mots clés](../cpp/keywords-cpp.md)<br/>
[switch, instruction (C++)](../cpp/switch-statement-cpp.md)
