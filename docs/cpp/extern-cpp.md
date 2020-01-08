---
title: extern (C++)
ms.date: 04/12/2018
f1_keywords:
- extern
- extern_CPP
helpviewer_keywords:
- extern keyword [C++], linkage to non-C++ functions
- declarations, external
- external linkage, extern modifier
ms.assetid: 1e2f0ae3-ae98-4410-85b5-222d6abc865a
ms.openlocfilehash: d42a32202f7fa67751ea36757c13b2c6af4953b2
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/20/2019
ms.locfileid: "75301533"
---
# <a name="extern-c"></a>extern (C++)

Le mot clé **extern** est appliqué à une variable globale, une fonction ou une déclaration de modèle pour spécifier que le nom de cet élément a une *liaison externe*. Pour obtenir des informations générales sur la liaison et la raison pour laquelle l’utilisation de variables globales est déconseillée, consultez [unités de traduction et liaison](program-and-linkage-cpp.md).

Le mot clé **extern** a quatre significations selon le contexte :

1. dans une déclaration de variable globale non const, **extern** spécifie que la variable ou la fonction est définie dans une autre unité de traduction. L' **extern** doit être appliqué à tous les fichiers à l’exception de celui où la variable est définie.
1. dans une déclaration de variable const, elle spécifie que la variable a une liaison externe. **Extern** doit être appliqué à toutes les déclarations dans tous les fichiers. (Les variables const globales ont une liaison interne par défaut.)
1. **extern "C"** spécifie que la fonction est définie ailleurs et utilise la Convention d’appel du langage C. Le modificateur extern "C" peut également être appliqué à plusieurs déclarations de fonction dans un bloc.
1. dans une déclaration de modèle, il spécifie que le modèle a déjà été instancié ailleurs. Il s’agit d’une optimisation qui indique au compilateur qu’il peut réutiliser l’autre instanciation plutôt que d’en créer une nouvelle à l’emplacement actuel. Pour plus d’informations sur cette utilisation de **extern**, consultez [modèles](templates-cpp.md).

## <a name="extern-linkage-for-non-const-globals"></a>liaison externe pour les variables globales non const

Lorsque l’éditeur de liens voit **extern** avant une déclaration de variable globale, il recherche la définition dans une autre unité de traduction. Les déclarations de variables non const au niveau de la portée globale sont externes par défaut. Appliquez uniquement **extern** aux déclarations qui ne fournissent pas la définition.

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

## <a name="extern-linkage-for-const-globals"></a>liaison externe pour les variables globales const

Par défaut, une variable globale **const** a une liaison interne. Si vous souhaitez que la variable ait une liaison externe, appliquez le mot clé **extern** à la définition et à toutes les autres déclarations dans d’autres fichiers :

```cpp
//fileA.cpp
extern const int i = 42; // extern const definition

//fileB.cpp
extern const int i;  // declaration only. same as i in FileA
```

## <a name="extern-constexpr-linkage"></a>liaison extern constexpr

Dans Visual Studio 2017 version 15,3 et les versions antérieures, le compilateur a toujours donné une liaison interne de variable constexpr même quand la variable était marquée comme extern. Dans Visual Studio 2017 version 15.5, un nouveau commutateur de compilateur ([/Zc:externConstexpr](../build/reference/zc-externconstexpr.md)) active le comportement correct de conformité aux normes. Cela deviendra le comportement par défaut. L’option/permissive-n’active pas/Zc : externConstexpr.

```cpp
extern constexpr int x = 10; //error LNK2005: "int const x" already defined
```

Si un fichier d’en-tête contient une variable extern constexpr, il doit être marqué **__declspec (selectany)** afin de pouvoir combiner correctement ses déclarations dupliquées :

```cpp
extern constexpr __declspec(selectany) int x = 10;
```

## <a name="extern-c-and-extern-c-function-declarations"></a>déclarations de fonction extern "C"C++et extern ""

Dans C++, en cas d’utilisation avec une chaîne, **extern** spécifie que les conventions de liaison d’un autre langage sont utilisées pour le ou les déclarateurs. Les données et les fonctions C sont accessibles uniquement si elles sont déclarées auparavant comme ayant une liaison C. Toutefois, elles doivent être définies dans une unité de traduction compilée séparément.

Microsoft C++ prend en charge les chaînes **« C »** et **C++«»** dans le champ de *littéral de chaîne* . Tous les fichiers Include standard utilisent la syntaxe **extern** "C" pour permettre l’utilisation des fonctions de la bibliothèque Runtime dans C++ les programmes.

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

Si une fonction a plusieurs spécifications de liaison, ils doivent concorder ; le fait de déclarer des fonctions comme ayant à la fois une liaison C et une liaison C++ constitue une erreur. En outre, si deux déclarations pour une fonction se produisent dans un programme (une avec une spécification de liaison et une autre sans), la déclaration avec la spécification de la liaison doit être la première. Toutes les déclarations redondantes de fonctions qui ont déjà une spécification de liaison sont affectées de la liaison spécifiée dans la première déclaration. Par exemple :

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

[Mots clés](../cpp/keywords-cpp.md)<br/>
[Unités de traduction et liaison](program-and-linkage-cpp.md)<br/>
[Spécificateur de classe de stockage extern en C](../c-language/extern-storage-class-specifier.md)<br/>
[Comportement des identificateurs en C](../c-language/behavior-of-identifiers.md)<br/>
[Liaison en C](../c-language/linkage.md)