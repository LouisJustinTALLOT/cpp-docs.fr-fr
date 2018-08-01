---
title: extern (C++) | Microsoft Docs
ms.custom: ''
ms.date: 04/12/2018
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-language
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- extern
- extern_CPP
dev_langs:
- C++
helpviewer_keywords:
- extern keyword [C++], linkage to non-C++ functions
- declarations, external
- external linkage, extern modifier
ms.assetid: 1e2f0ae3-ae98-4410-85b5-222d6abc865a
caps.latest.revision: 11
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 133cbb01ba54ccc8bc0ce0c31b5d7b4436c2488d
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/01/2018
ms.locfileid: "39403041"
---
# <a name="extern-c"></a>extern (C++)

Le **extern** mot clé est appliqué à une déclaration de variable, de fonction ou de modèle globale pour spécifier que le nom de ceci a *une liaison externe*. Pour des informations générales sur la liaison et pourquoi l’utilisation de variables globales est déconseillée, consultez [programme et liaison](program-and-linkage-cpp.md).

Le **extern** mot-clé a quatre significations en fonction du contexte :

1. dans une déclaration de variable globale non const, **extern** Spécifie que la variable ou la fonction est définie dans une autre unité de traduction. Le **extern** doit être appliqué dans tous les fichiers à l’exception de celui où la variable est définie.
1. dans une déclaration de variable const, il spécifie que la variable a une liaison externe. Le **extern** doivent être appliquées à toutes les déclarations dans tous les fichiers. (Les variables constantes globales ont une liaison interne par défaut).
1. **extern « C »** Spécifie que la fonction est définie ailleurs et utilise la convention d’appel en langage C. Le modificateur de « C » externe peut-être également être appliqué à plusieurs déclarations de fonction dans un bloc.
1. dans une déclaration de modèle, il spécifie que le modèle a déjà été instancié ailleurs. Il s’agit d’une optimisation qui indique au compilateur qu’il peut ré-utiliser autres l’instanciation, plutôt que de créer un nouveau à l’emplacement actuel. Pour plus d’informations sur cette utilisation de **extern**, consultez [modèles](templates-cpp.md).

## <a name="extern-linkage-for-non-const-globals"></a>liaison extern pour les variables globales non const

Lorsque l’éditeur de liens voit **extern** avant une déclaration de variable globale, il recherche la définition dans une autre unité de traduction. Les déclarations de variables non const avec une portée globale sont externes par défaut ; s’appliquent uniquement **extern** aux déclarations qui ne fournissent pas la définition.

```cpp
//fileA.cpp
int i = 42; // declaration and definition

//fileB.cpp
extern int i;  // declaration only. same as i in FileA

//fileC.cpp
extern int i;  // declaration only. same as i in FileA

//fileD.cpp
int i = 43; // LNK2005! 'i' already has a definition.
extern int i = 43; // same error (extern is ignored on definitions)
```

## <a name="extern-linkage-for-const-globals"></a>liaison extern pour globals const

Un **const** variable globale possède une liaison interne par défaut. Si vous souhaitez que la variable ont une liaison externe, appliquer la **extern** mot clé à définition ainsi que pour toutes les autres déclarations dans d’autres fichiers :

```cpp
//fileA.cpp
extern const int i = 42; // extern const definition

//fileB.cpp
extern const int i;  // declaration only. same as i in FileA
```

## <a name="extern-constexpr-linkage"></a>liaison extern constexpr

Dans Visual Studio 2017 version 15.3 et versions antérieures, le compilateur retournait toujours une liaison interne variable constexpr même quand la variable a été marqué comme extern. Dans Visual Studio 2017 version 15.5, un nouveau commutateur de compilateur ([/Zc:externConstexpr](../build/reference/zc-externconstexpr.md)) active le comportement correct de conformité aux normes. Cela deviendra le comportement par défaut.

```cpp
extern constexpr int x = 10; //error LNK2005: "int const x" already defined
```

Si un fichier d’en-tête contient un constexpr variables extern déclaré, il doit être marqué **__declspec (selectany)** afin d’avoir correctement ses déclarations dupliquées combinées :

```cpp
extern constexpr __declspec(selectany) int x = 10;
```

## <a name="extern-c-and-extern-c-function-declarations"></a>déclarations de fonction extern « C » et extern « C++ »

 En C++, lorsqu’il est utilisé avec une chaîne, **extern** Spécifie que les conventions de liaison d’un autre langage sont utilisées pour l’ou les déclarateurs. Les données et les fonctions C sont accessibles uniquement si elles sont déclarées auparavant comme ayant une liaison C. Toutefois, elles doivent être définies dans une unité de traduction compilée séparément.

 Microsoft C++ prend en charge les chaînes **« C »** et **« C++ »** dans le *littéral de chaîne* champ. Tous de la norme incluent l’utilisation de fichiers le **extern** syntaxe « C » pour autoriser les fonctions de bibliothèque du run-time à utiliser dans les programmes C++.

## <a name="example"></a>Exemple

L’exemple suivant montre comment déclarer des noms qui ont une liaison C :

```cpp
// Declare printf with C linkage.
extern "C" int printf(const char *fmt, ...);

//  Cause everything in the specified
//  header files to have C linkage.
extern "C" {
    // add your #include statements here
#include <stdio.h>
}

//  Declare the two functions ShowChar
//  and GetChar with C linkage.
extern "C" {
    char ShowChar(char ch);
    char GetChar(void);
}

//  Define the two functions 
//  ShowChar and GetChar with C linkage.
extern "C" char ShowChar(char ch) {
    putchar(ch);
    return ch;
}

extern "C" char GetChar(void) {
    char ch;
    ch = getchar();
    return ch;
}

// Declare a global variable, errno, with C linkage.
extern "C" int errno;
```

 Si une fonction a plusieurs spécifications de liaison, ils doivent concorder ; le fait de déclarer des fonctions comme ayant à la fois une liaison C et une liaison C++ constitue une erreur. En outre, si deux déclarations pour une fonction se produisent dans un programme (une avec une spécification de liaison et une autre sans), la déclaration avec la spécification de la liaison doit être la première. Toutes les déclarations redondantes de fonctions qui ont déjà une spécification de liaison sont affectées de la liaison spécifiée dans la première déclaration. Exemple :

```cpp
extern "C" int CFunc1();
...
int CFunc1();            // Redeclaration is benign; C linkage is
                         //  retained.

int CFunc2();
...
extern "C" int CFunc2(); // Error: not the first declaration of
                         //  CFunc2;  cannot contain linkage
                         //  specifier.
```

## <a name="see-also"></a>Voir aussi
 [Mots clés](../cpp/keywords-cpp.md)  
 [Programme et liaison](program-and-linkage-cpp.md)  
 [Spécificateur de classe de stockage en C extern](../c-language/extern-storage-class-specifier.md)  
 [Comportement des identificateurs en C](../c-language/behavior-of-identifiers.md)  
 [Liaison en C](../c-language/linkage.md)