---
title: Erreur du compilateur C2065
ms.date: 09/01/2017
f1_keywords:
- C2065
helpviewer_keywords:
- C2065
ms.assetid: 78093376-acb7-45f5-9323-5ed7e0aab1dc
ms.openlocfilehash: 3daf2cd532cd07225b822c80b46fc28274d4e2a8
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59779399"
---
# <a name="compiler-error-c2065"></a>Erreur du compilateur C2065

> «*identificateur*' : identificateur non déclaré

Le compilateur ne peut pas trouver la déclaration d’un identificateur. Il existe de nombreuses causes possibles pour cette erreur. Les causes les plus courantes de l’erreur C2065 sont que l’identificateur n’a pas été déclaré, l’identificateur est mal orthographié, l’en-tête où l’identificateur est déclaré n’est pas inclus dans le fichier, ou l’identificateur n’a pas un qualificateur d’étendue, par exemple, `cout` au lieu de `std::cout`. Pour plus d’informations sur les déclarations en C++, consultez [déclarations et définitions (C++)](../../cpp/declarations-and-definitions-cpp.md).

Voici quelques problèmes courants et les solutions de manière plus détaillée.

## <a name="the-identifier-is-undeclared"></a>L’identificateur n’est pas déclaré

Si l’identificateur est une variable ou un nom de fonction, vous devez le déclarer avant de pouvoir être utilisé. Une déclaration de fonction doit également inclure les types de ses paramètres avant de pouvoir utiliser la fonction. Si la variable est déclarée à l’aide de `auto`, le compilateur doit être en mesure de déduire le type à partir de son initialiseur.

Si l’identificateur est un membre d’une classe ou un struct ou déclarés dans un espace de noms, il doit être qualifié par le nom de classe ou un struct, ou le nom de l’espace de noms, lorsqu’il est utilisé en dehors de l’étendue de struct, classe ou espace de noms. Vous pouvez également l’espace de noms doive être mise en portée par un `using` directive comme `using namespace std;`, ou le nom de membre doive être mis en portée par un `using` déclaration, tel que `using std::string;`. Sinon, le nom non qualifié est considéré comme un identificateur non déclaré dans la portée actuelle.

Si l’identificateur est la balise pour un type défini par l’utilisateur, par exemple, un `class` ou `struct`, le type de la balise doit être déclaré avant de pouvoir être utilisé. Par exemple, la déclaration `struct SomeStruct { /*...*/ };` doit exister avant que vous pouvez déclarer une variable `SomeStruct myStruct;` dans votre code.

Si l’identificateur est un alias de type, le type doit être déclaré à l’aide un `using` déclaration ou `typedef` avant de pouvoir être utilisé. Par exemple, vous devez déclarer `using my_flags = std::ios_base::fmtflags;` avant de pouvoir utiliser `my_flags` comme alias de type pour `std::ios_base::fmtflags`.

## <a name="example-misspelled-identifier"></a>Exemple : identificateur mal orthographié

Cette erreur se produit généralement lorsque le nom d’identificateur est mal orthographié ou l’identificateur utilise les lettres majuscules et minuscules incorrects. Le nom dans la déclaration doit correspondre exactement à celui que vous utilisez.

```cpp
// C2065_spell.cpp
// compile with: cl /EHsc C2065_spell.cpp
#include <iostream>
using namespace std;
int main() {
    int someIdentifier = 42;
    cout << "Some Identifier: " << SomeIdentifier << endl;
    // C2065: 'SomeIdentifier': undeclared identifier
    // To fix, correct the spelling:
    // cout << "Some Identifier: " << someIdentifier << endl;
}
```

## <a name="example-use-an-unscoped-identifier"></a>Exemple : utiliser un identificateur non délimité

Cette erreur peut se produire si votre identificateur n’est pas correctement repérée. Si vous voyez une erreur C2065 lorsque vous utilisez `cout`, c’est la cause. Lorsque les fonctions de bibliothèque Standard C++ et les opérateurs ne sont pas entièrement qualifiés par espace de noms, ou vous n’avez pas mis la `std` espace de noms dans la portée actuelle en utilisant un `using` directive, le compilateur ne peut pas trouver les. Pour résoudre ce problème, vous devez entièrement qualifier les noms d’identificateur, ou spécifiez l’espace de noms avec la `using` directive.

Cet exemple ne parvient pas à compiler, car `cout` et `endl` sont définies dans le `std` espace de noms :

```cpp
// C2065_scope.cpp
// compile with: cl /EHsc C2065_scope.cpp
#include <iostream>
// using namespace std;   // Uncomment this line to fix

int main() {
    cout << "Hello" << endl;   // C2065 'cout': undeclared identifier
                               // C2065 'endl': undeclared identifier
    // Or try the following line instead
    std::cout << "Hello" << std::endl;
}
```

Les identificateurs qui sont déclarés à l’intérieur de `class`, `struct`, ou `enum class` types doivent également être qualifiés par le nom de leur portée englobante lorsque vous les utilisez en dehors de cette étendue.

## <a name="example-precompiled-header-isnt-first"></a>Exemple : en-tête précompilé n’est pas premier

Cette erreur peut se produire si vous placez les directives de préprocesseur, telles que #include, #define, ou #pragma, avant le #include d’un fichier d’en-tête précompilé. Si votre fichier source utilise un fichier d’en-tête précompilé (autrement dit, s’il est compilé à l’aide de la **/Yu** option du compilateur), toutes les directives de préprocesseur avant le fichier d’en-tête précompilé sont ignorés.

Cet exemple ne parvient pas à compiler, car `cout` et `endl` sont définies dans le \<iostream > en-tête, qui est ignorée, car il est inclus avant le fichier d’en-tête précompilé. Pour générer cet exemple, créez les trois fichiers, puis compiler stdafx.cpp, puis compiler C2065_pch.cpp.

```cpp
// stdafx.h
#include <stdio.h>
```

```cpp
// stdafx.cpp
// Compile by using: cl /EHsc /W4 /c /Ycstdafx.h stdafx.cpp
#include <stdafx.h>
```

```cpp
// C2065_pch.cpp
// compile with: cl /EHsc /W4 /Yustdafx.h C2065_pch.cpp
#include <iostream>
#include "stdafx.h"
using namespace std;

int main() {
    cout << "Hello" << endl;   // C2065 'cout': undeclared identifier
                               // C2065 'endl': undeclared identifier
}
```

Pour résoudre ce problème, ajoutez le #include de \<iostream > dans le fichier d’en-tête précompilé, ni de déplacement après le fichier d’en-tête précompilé est inclus dans votre fichier source.

## <a name="example-missing-header-file"></a>Exemple : le fichier d’en-tête est introuvable

Vous n’avez pas inclus le fichier d’en-tête qui déclare l’identificateur. Assurez-vous que le fichier qui contient la déclaration de l’identificateur est inclus dans chaque fichier source qui l’utilise.

```cpp
// C2065_header.cpp
// compile with: cl /EHsc C2065_header.cpp

//#include <stdio.h>
int main() {
    fpos_t file_position = 42; // C2065: 'fpos_t': undeclared identifier
    // To fix, uncomment the #include <stdio.h> line
    // to include the header where fpos_t is defined
}
```

Autre cause possible : Si vous utilisez une liste d’initialiseurs sans inclure le \<initializer_list > en-tête.

```cpp
// C2065_initializer.cpp
// compile with: cl /EHsc C2065_initializer.cpp

// #include <initializer_list>
int main() {
    for (auto strList : {"hello", "world"})
        if (strList == "hello") // C2065: 'strList': undeclared identifier
            return 1;
    // To fix, uncomment the #include <initializer_list> line
}
```

Vous pouvez voir cette erreur dans les fichiers source Windows Desktop app si vous définissez `VC_EXTRALEAN`, `WIN32_LEAN_AND_MEAN`, ou `WIN32_EXTRA_LEAN`. Ces macros de préprocesseur exclure certains fichiers d’en-tête de windows.h et afxv\_w32.h pour accélérer le compile. Recherchez dans windows.h et afxv_w32.h une description à jour de ce qui est exclu.

## <a name="example-missing-closing-quote"></a>Exemple : le guillemet fermant manquant

Cette erreur peut se produire si un guillemet fermant est manquant après une constante de chaîne. Il s’agit d’un moyen simple de confondre le compilateur. Notez que le guillemet fermant manquant peut y avoir plusieurs lignes avant l’emplacement de l’erreur signalée.

```cpp
// C2065_quote.cpp
// compile with: cl /EHsc C2065_quote.cpp
#include <iostream>

int main() {
    // Fix this issue by adding the closing quote to "Aaaa"
    char * first = "Aaaa, * last = "Zeee";
    std::cout << "Name: " << first
        << " " << last << std::endl; // C2065: 'last': undeclared identifier
}
```

## <a name="example-use-iterator-outside-for-loop-scope"></a>Exemple : utiliser itérateur en dehors de la portée de la boucle

Cette erreur peut se produire si vous déclarez une variable d’itérateur dans un `for` boucle et que vous essayez d’utiliser cette variable d’itérateur en dehors de l’étendue de la `for` boucle. Le compilateur permet la [/Zc : forScope](../../build/reference/zc-forscope-force-conformance-in-for-loop-scope.md) option du compilateur par défaut. Consultez [Debug Iterator Support](../../standard-library/debug-iterator-support.md) pour plus d’informations.

```cpp
// C2065_iter.cpp
// compile with: cl /EHsc C2065_iter.cpp
#include <iostream>
#include <string>

int main() {
    // char last = '!';
    std::string letters{ "ABCDEFGHIJKLMNOPQRSTUVWXYZ" };
    for (const char& c : letters) {
        if ('Q' == c) {
            std::cout << "Found Q!" << std::endl;
        }
        // last = c;
    }
    std::cout << "Last letter was " << c << std::endl; // C2065
    // Fix by using a variable declared in an outer scope.
    // Uncomment the lines that declare and use 'last' for an example.
    // std::cout << "Last letter was " << last << std::endl; // C2065
}
```

## <a name="example-preprocessor-removed-declaration"></a>Exemple : de préprocesseur déclaration supprimée

Cette erreur peut se produire si vous faites référence à une fonction ou une variable qui se trouve dans le code compilé conditionnellement qui n’est pas compilé pour votre configuration actuelle. Cela peut également se produire si vous appelez une fonction dans un fichier d’en-tête qui n’est actuellement pas pris en charge dans votre environnement de génération. Si certaines variables ou des fonctions sont disponibles uniquement quand une macro de préprocesseur particulier est définie, assurez-vous que le code qui appelle ces fonctions peut uniquement être compilé lors de la macro de préprocesseur même est définie. Ce problème est facile de repérer dans l’IDE, car la déclaration de la fonction est grisée si les macros de préprocesseur requis ne sont pas définies pour la configuration de build actuelle.

Il s’agit d’un exemple de code qui fonctionne lorsque vous générez en mode de débogage, mais pas de la vente au détail :

```cpp
// C2065_defined.cpp
// Compile with: cl /EHsc /W4 /MT C2065_defined.cpp
#include <iostream>
#include <crtdbg.h>
#ifdef _DEBUG
    _CrtMemState oldstate;
#endif
int main() {
    _CrtMemDumpStatistics(&oldstate);
    std::cout << "Total count " << oldstate.lTotalCount; // C2065
    // Fix by guarding references the same way as the declaration:
    // #ifdef _DEBUG
    //    std::cout << "Total count " << oldstate.lTotalCount;
    // #endif
}
```

## <a name="example-ccli-type-deduction-failure"></a>Exemple : C++ / c++ / Échec de déduction de type CLI

Cette erreur peut se produire lors de l’appel d’une fonction générique, si l’argument de type prévu ne peut pas être déduit à partir des paramètres utilisés. Pour plus d’informations, consultez [fonctions génériques (C++ / c++ / CLI)](../../extensions/generic-functions-cpp-cli.md).

```cpp
// C2065_b.cpp
// compile with: cl /clr C2065_b.cpp
generic <typename ItemType>
void G(int i) {}

int main() {
   // global generic function call
   G<T>(10);     // C2065
   G<int>(10);   // OK - fix with a specific type argument
}
```

## <a name="example-ccli-attribute-parameters"></a>Exemple : C++ / c++ / Paramètres d’attribut CLI

Cette erreur peut également être due à la mise en conformité du compilateur pour Visual C++ 2005 : vérification des paramètres des attributs Visual C++.

```cpp
// C2065_attributes.cpp
// compile with: cl /c /clr C2065_attributes.cpp
[module(DLL, name=MyLibrary)];   // C2065
// try the following line instead
// [module(dll, name="MyLibrary")];

[export]
struct MyStruct {
   int i;
};
```
