---
title: Erreur du compilateur C2065
ms.date: 08/19/2019
f1_keywords:
- C2065
helpviewer_keywords:
- C2065
ms.assetid: 78093376-acb7-45f5-9323-5ed7e0aab1dc
ms.openlocfilehash: 40d1d0744588c4b7911e84f5e57a6b40372b48cf
ms.sourcegitcommit: 9d4ffb8e6e0d70520a1e1a77805785878d445b8a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/20/2019
ms.locfileid: "69630133"
---
# <a name="compiler-error-c2065"></a>Erreur du compilateur C2065

> '*identificateur*': identificateur non déclaré

Le compilateur ne peut pas trouver la déclaration pour un identificateur. Il existe de nombreuses causes possibles pour cette erreur. Les causes les plus courantes de la variable C2065 sont que l’identificateur n’a pas été déclaré, que l’identificateur est mal orthographié, que l’en-tête dans lequel l’identificateur est déclaré n’est pas inclus dans le fichier, ou `cout` qu’il manque un qualificateur d’étendue dans l’identificateur, par exemple au lieu de `std::cout`. Pour plus d’informations sur les C++déclarations dans, consultez [déclarations etC++définitions ()](../../cpp/declarations-and-definitions-cpp.md).

Voici quelques problèmes et solutions courants plus en détail.

## <a name="the-identifier-is-undeclared"></a>L’identificateur n’est pas déclaré

Si l’identificateur est une variable ou un nom de fonction, vous devez le déclarer avant de pouvoir l’utiliser. Une déclaration de fonction doit également inclure les types de ses paramètres avant que la fonction puisse être utilisée. Si la variable est déclarée `auto`à l’aide de, le compilateur doit être en mesure de déduire le type à partir de son initialiseur.

Si l’identificateur est membre d’une classe ou d’un struct, ou déclaré dans un espace de noms, il doit être qualifié par le nom de la classe ou du struct, ou le nom de l’espace de noms, lorsqu’il est utilisé en dehors de la portée de la structure, de la classe ou de l’espace de noms. L’espace de noms doit également être placé dans la portée par `using` une directive telle `using namespace std;`que, ou le nom du membre doit être placé dans la `using` portée par une déclaration `using std::string;`, telle que. Dans le cas contraire, le nom non qualifié est considéré comme un identificateur non déclaré dans l’étendue actuelle.

Si l’identificateur est la balise d’un type défini par l’utilisateur, par exemple, `class` ou `struct`, le type de la balise doit être déclaré avant de pouvoir être utilisé. Par exemple, la Déclaration `struct SomeStruct { /*...*/ };` doit exister pour que vous puissiez déclarer une `SomeStruct myStruct;` variable dans votre code.

Si l’identificateur est un alias de type, le type doit être déclaré à l’aide `using` d’une `typedef` déclaration ou avant de pouvoir être utilisé. Par exemple, vous devez déclarer `using my_flags = std::ios_base::fmtflags;` avant de pouvoir utiliser `my_flags` comme alias de type pour `std::ios_base::fmtflags`.

## <a name="example-misspelled-identifier"></a>Exemple: identificateur mal orthographié

Cette erreur se produit généralement lorsque le nom de l’identificateur est mal orthographié ou que l’identificateur utilise des lettres majuscules et minuscules incorrectes. Le nom dans la déclaration doit correspondre exactement au nom que vous utilisez.

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

## <a name="example-use-an-unscoped-identifier"></a>Exemple: utiliser un identificateur non étendu

Cette erreur peut se produire si votre identificateur n’est pas correctement étendu. Si vous voyez la page C2065 lorsque `cout`vous utilisez, c’est la cause. Lorsque C++ les fonctions et les opérateurs de la bibliothèque standard ne sont pas entièrement qualifiés par l’espace de `std` noms, ou que vous n’avez pas `using` mis l’espace de noms dans la portée actuelle à l’aide d’une directive, le compilateur ne peut pas les trouver. Pour résoudre ce problème, vous devez qualifier entièrement les noms d’identificateurs ou spécifier l’espace de noms avec `using` la directive.

Cet exemple ne parvient pas `cout` à `endl` compiler car et sont `std` définis dans l’espace de noms:

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

Les identificateurs qui sont déclarés `class`à `struct`l’intérieur `enum class` de types, ou doivent également être qualifiés par le nom de leur portée englobante lorsque vous les utilisez en dehors de cette portée.

## <a name="example-precompiled-header-isnt-first"></a>Exemple: l’en-tête précompilé n’est pas le premier

Cette erreur peut se produire si vous placez des directives de préprocesseur, telles que #include, #define ou #pragma, avant l' #include d’un fichier d’en-tête précompilé. Si votre fichier source utilise un fichier d’en-tête précompilé (autrement dit, s’il est compilé à l’aide de l’option de compilateur **/Yu** ), toutes les directives de préprocesseur avant le fichier d’en-tête précompilé sont ignorées.

Cet exemple ne parvient pas `cout` à `endl` compiler, car et \<sont définis dans l’en-tête iostream >, ce qui est ignoré, car il est inclus avant le fichier d’en-tête précompilé. Pour générer cet exemple, vous créez les trois fichiers, puis vous compilez stdafx. cpp, puis compilez C2065_pch. cpp.

```cpp
// pch.h (stdafx.h in Visual Studio 2017 and earlier)
#include <stdio.h>
```

```cpp
// pch.cpp (stdafx.cpp in Visual Studio 2017 and earlier)
// Compile by using: cl /EHsc /W4 /c /Ycstdafx.h stdafx.cpp
#include "pch.h"
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

Pour résoudre ce problème, ajoutez la #include de \<la > iostream dans le fichier d’en-tête précompilé, ou déplacez-la après l’inclusion du fichier d’en-tête précompilé dans votre fichier source.

## <a name="example-missing-header-file"></a>Exemple: fichier d’en-tête manquant

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

Une autre cause possible est que vous utilisez une liste d’initialiseurs sans \<inclure l’en-tête > initializer_list.

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

Vous pouvez voir cette erreur dans les fichiers sources de l’application de bureau `VC_EXTRALEAN`Windows `WIN32_LEAN_AND_MEAN`si vous `WIN32_EXTRA_LEAN`définissez, ou. Ces macros de préprocesseur excluent certains fichiers d’en-tête de Windows\_. h et afxv W32. h pour accélérer les compilations. Recherchez dans Windows. h et afxv_w32. h une description à jour de ce qui est exclu.

## <a name="example-missing-closing-quote"></a>Exemple: guillemet fermant manquant

Cette erreur peut se produire si un guillemet fermant est manquant après une constante de chaîne. Il s’agit d’un moyen simple de confondre le compilateur. Notez que le guillemet fermant manquant peut être plusieurs lignes avant l’emplacement de l’erreur signalée.

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

## <a name="example-use-iterator-outside-for-loop-scope"></a>Exemple: utiliser un itérateur en dehors de la portée de la boucle for

Cette erreur peut se produire si vous déclarez une variable d' `for` itérateur dans une boucle, puis que vous essayez d’utiliser cette variable d’itérateur en `for` dehors de la portée de la boucle. Le compilateur active l’option de compilateur [/Zc: forScope](../../build/reference/zc-forscope-force-conformance-in-for-loop-scope.md) par défaut. Pour plus d’informations, consultez [prise en charge](../../standard-library/debug-iterator-support.md) des itérateurs de débogage.

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

## <a name="example-preprocessor-removed-declaration"></a>Exemple: déclaration supprimée par le préprocesseur

Cette erreur peut se produire si vous faites référence à une fonction ou une variable qui se trouve dans du code compilé de manière conditionnelle et qui n’est pas compilé pour votre configuration actuelle. Cela peut également se produire si vous appelez une fonction dans un fichier d’en-tête qui n’est actuellement pas pris en charge dans votre environnement de génération. Si certaines variables ou fonctions sont uniquement disponibles lorsqu’une macro de préprocesseur particulière est définie, assurez-vous que le code qui appelle ces fonctions peut uniquement être compilé quand la même macro de préprocesseur est définie. Ce problème est facile à repérer dans l’IDE, car la déclaration de la fonction est grisée si les macros de préprocesseur requises ne sont pas définies pour la configuration de build actuelle.

Il s’agit d’un exemple de code qui fonctionne lorsque vous générez en débogage, mais pas au détail:

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

## <a name="example-ccli-type-deduction-failure"></a>Exemple : C++Échec de déduction de type/CLI

Cette erreur peut se produire lors de l’appel d’une fonction générique, si l’argument de type prévu ne peut pas être déduit des paramètres utilisés. Pour plus d’informations, consultez [fonctions génériquesC++(/CLI)](../../extensions/generic-functions-cpp-cli.md).

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

## <a name="example-ccli-attribute-parameters"></a>Exemple : C++Paramètres d’attribut/CLI

Cette erreur peut également être générée en raison du travail de conformité du compilateur effectué pour Visual Studio 2005: vérification des paramètres pour les attributs visuels C++ .

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
