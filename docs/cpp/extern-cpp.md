---
title: :::no-loc(extern):::C++
description: 'Guide du mot clé du langage C++ :::no-loc(extern)::: .'
ms.date: 01/28/2020
f1_keywords:
- ':::no-loc(extern):::'
- :::no-loc(extern):::_CPP
helpviewer_keywords:
- ':::no-loc(extern)::: keyword [C++], linkage to non-C++ functions'
- declarations, :::no-loc(extern):::al
- ':::no-loc(extern):::al linkage, :::no-loc(extern)::: modifier'
ms.assetid: 1e2f0ae3-ae98-4410-85b5-222d6abc865a
no-loc:
- ':::no-loc(extern):::'
- ':::no-loc(const):::'
- ':::no-loc(constexpr):::'
- ':::no-loc(permissive):::'
ms.openlocfilehash: 510352f9e99e513f4a426f6ef89be4474085d97c
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87227502"
---
# <a name="no-locextern-c"></a>:::no-loc(extern):::C++

Le **`:::no-loc(extern):::`** mot clé peut être appliqué à une variable globale, une fonction ou une déclaration de modèle. Il spécifie que le symbole a une * :::no-loc(extern)::: liaison Al*. Pour obtenir des informations générales sur la liaison et la raison pour laquelle l’utilisation de variables globales est déconseillée, consultez [unités de traduction et liaison](program-and-linkage-cpp.md).

Le **`:::no-loc(extern):::`** mot clé a quatre significations selon le contexte :

- Dans une déclaration de **`:::no-loc(const):::`** variable non globale, **`:::no-loc(extern):::`** spécifie que la variable ou la fonction est définie dans une autre unité de traduction. **`:::no-loc(extern):::`** Doit être appliqué à tous les fichiers à l’exception de celui où la variable est définie.

- Dans une **`:::no-loc(const):::`** déclaration de variable, elle spécifie que la variable a une :::no-loc(extern)::: liaison al. **`:::no-loc(extern):::`** Doit être appliqué à toutes les déclarations dans tous les fichiers. (Les **`:::no-loc(const):::`** variables globales ont une liaison interne par défaut.)

- ** :::no-loc(extern)::: "C"** spécifie que la fonction est définie ailleurs et utilise la Convention d’appel du langage C. Le :::no-loc(extern)::: modificateur « C » peut également être appliqué à plusieurs déclarations de fonction dans un bloc.

- Dans une déclaration de modèle, **`:::no-loc(extern):::`** spécifie que le modèle a déjà été instancié ailleurs. **`:::no-loc(extern):::`** indique au compilateur qu’il peut réutiliser l’autre instanciation, au lieu d’en créer un nouveau à l’emplacement actuel. Pour plus d’informations sur cette utilisation de **`:::no-loc(extern):::`** , consultez [instanciation explicite](explicit-instantiation.md).

## <a name="no-locextern-linkage-for-non-no-locconst-globals"></a>:::no-loc(extern):::liaison pour les non- :::no-loc(const)::: globales

Lorsque l’éditeur de liens voit **`:::no-loc(extern):::`** avant une déclaration de variable globale, il recherche la définition dans une autre unité de traduction. Les déclarations de non- **`:::no-loc(const):::`** variables au niveau de la portée globale sont :::no-loc(extern)::: al par défaut. S’applique uniquement **`:::no-loc(extern):::`** aux déclarations qui ne fournissent pas la définition.

```cpp
//fileA.cpp
int i = 42; // declaration and definition

//fileB.cpp
:::no-loc(extern)::: int i;  // declaration only. same as i in FileA

//fileC.cpp
:::no-loc(extern)::: int i;  // declaration only. same as i in FileA

//fileD.cpp
int i = 43; // LNK2005! 'i' already has a definition.
:::no-loc(extern)::: int i = 43; // same error (:::no-loc(extern)::: is ignored on definitions)
```

## <a name="no-locextern-linkage-for-no-locconst-globals"></a>:::no-loc(extern):::liaison pour les :::no-loc(const)::: globales

Par **`:::no-loc(const):::`** défaut, une variable globale a une liaison interne. Si vous souhaitez que la variable ait une :::no-loc(extern)::: liaison Al, appliquez le **`:::no-loc(extern):::`** mot clé à la définition et à toutes les autres déclarations dans d’autres fichiers :

```cpp
//fileA.cpp
:::no-loc(extern)::: :::no-loc(const)::: int i = 42; // :::no-loc(extern)::: :::no-loc(const)::: definition

//fileB.cpp
:::no-loc(extern)::: :::no-loc(const)::: int i;  // declaration only. same as i in FileA
```

## <a name="no-locextern-no-locconstexpr-linkage"></a>:::no-loc(extern)::::::no-loc(constexpr):::liaison

Dans Visual Studio 2017 version 15,3 et les versions antérieures, le compilateur a toujours donné une **`:::no-loc(constexpr):::`** liaison interne variable, même lorsque la variable a été marquée **`:::no-loc(extern):::`** . Dans Visual Studio 2017 version 15,5 et versions ultérieures, le commutateur du compilateur [/Zc : :::no-loc(extern)::: Constexpr](../build/reference/zc-:::no-loc(extern)::::::no-loc(constexpr):::.md) active le comportement correct de conformité aux normes. Finalement, l’option devient la valeur par défaut. L' [/:::no-loc(permissive):::-](../build/reference/:::no-loc(permissive):::-standards-conformance.md) option n’active pas **/Zc : :::no-loc(extern)::: Constexpr**.

```cpp
:::no-loc(extern)::: :::no-loc(constexpr)::: int x = 10; //error LNK2005: "int :::no-loc(const)::: x" already defined
```

Si un fichier d’en-tête contient une variable déclarée **`:::no-loc(extern):::`** **`:::no-loc(constexpr):::`** , il doit être marqué `__declspec(selectany)` pour que ses déclarations dupliquées soient correctement combinées :

```cpp
:::no-loc(extern)::: :::no-loc(constexpr)::: __declspec(selectany) int x = 10;
```

## <a name="no-locextern-c-and-no-locextern-c-function-declarations"></a>:::no-loc(extern):::Déclarations de fonction "C" et :::no-loc(extern)::: "C++"

En C++, en cas d’utilisation avec une chaîne, **`:::no-loc(extern):::`** spécifie que les conventions de liaison d’un autre langage sont utilisées pour le ou les déclarateurs. Les fonctions et les données C sont accessibles uniquement si elles sont précédemment déclarées comme ayant une liaison C. Toutefois, elles doivent être définies dans une unité de traduction compilée séparément.

Microsoft C++ prend en charge les chaînes **« C »** et **« C++ »** dans le champ de *littéral de chaîne* . Tous les fichiers Include standard utilisent la syntaxe ** :::no-loc(extern)::: « C »** pour permettre l’utilisation des fonctions de la bibliothèque Runtime dans les programmes C++.

## <a name="example"></a>Exemple

L’exemple suivant montre comment déclarer des noms qui ont une liaison C :

```cpp
// Declare printf with C linkage.
:::no-loc(extern)::: "C" int printf(:::no-loc(const)::: char *fmt, ...);

//  Cause everything in the specified
//  header files to have C linkage.
:::no-loc(extern)::: "C" {
    // add your #include statements here
#include <stdio.h>
}

//  Declare the two functions ShowChar
//  and GetChar with C linkage.
:::no-loc(extern)::: "C" {
    char ShowChar(char ch);
    char GetChar(void);
}

//  Define the two functions
//  ShowChar and GetChar with C linkage.
:::no-loc(extern)::: "C" char ShowChar(char ch) {
    putchar(ch);
    return ch;
}

:::no-loc(extern)::: "C" char GetChar(void) {
    char ch;
    ch = getchar();
    return ch;
}

// Declare a global variable, errno, with C linkage.
:::no-loc(extern)::: "C" int errno;
```

Si une fonction a plus d’une spécification de liaison, elle doit s’accorder. Déclarer des fonctions comme ayant à la fois une liaison C et C++ est une erreur. En outre, si deux déclarations pour une fonction se produisent dans un programme (une avec une spécification de liaison et une autre sans), la déclaration avec la spécification de la liaison doit être la première. Toutes les déclarations redondantes de fonctions qui ont déjà une spécification de liaison sont affectées de la liaison spécifiée dans la première déclaration. Par exemple :

```cpp
:::no-loc(extern)::: "C" int CFunc1();
...
int CFunc1();            // Redeclaration is benign; C linkage is
                         //  retained.

int CFunc2();
...
:::no-loc(extern)::: "C" int CFunc2(); // Error: not the first declaration of
                         //  CFunc2;  cannot contain linkage
                         //  specifier.
```

## <a name="see-also"></a>Voir aussi

[Mot](../cpp/keywords-cpp.md)\
[Unités de traduction et liaison](program-and-linkage-cpp.md)\
[:::no-loc(extern):::Spécificateur de classe de stockage en C](../c-language/:::no-loc(extern):::-storage-class-specifier.md)\
[Comportement des identificateurs en C](../c-language/behavior-of-identifiers.md)\
[Liaison en C](../c-language/linkage.md)
