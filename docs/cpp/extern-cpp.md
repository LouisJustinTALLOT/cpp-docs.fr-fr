---
title: extern (C++)
description: Guide du mot C++ clé extern du langage.
ms.date: 01/28/2020
f1_keywords:
- extern
- extern_CPP
helpviewer_keywords:
- extern keyword [C++], linkage to non-C++ functions
- declarations, external
- external linkage, extern modifier
ms.assetid: 1e2f0ae3-ae98-4410-85b5-222d6abc865a
no-loc:
- extern
- const
- constexpr
- permissive
ms.openlocfilehash: 422b6960802c59f1c45e0c22a4a85988c808a5b3
ms.sourcegitcommit: b8c22e6d555cf833510753cba7a368d57e5886db
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76821764"
---
# <a name="opno-locextern-c"></a>extern (C++)

Le mot clé **extern** peut être appliqué à une variable globale, une fonction ou une déclaration de modèle. Il spécifie que le symbole a une *liaison externe*. Pour obtenir des informations générales sur la liaison et la raison pour laquelle l’utilisation de variables globales est déconseillée, consultez [unités de traduction et liaison](program-and-linkage-cpp.md).

Le mot clé **extern** a quatre significations selon le contexte :

- Dans une déclaration de variable globale non **const** , **extern** spécifie que la variable ou la fonction est définie dans une autre unité de traduction. Le **extern** doit être appliqué dans tous les fichiers à l’exception de celui où la variable est définie.

- Dans une déclaration de variable **const** , elle spécifie que la variable a une liaison externe. Le **extern** doit être appliqué à toutes les déclarations dans tous les fichiers. (Les variables de **const** globales ont une liaison interne par défaut.)

- **extern « C »** spécifie que la fonction est définie ailleurs et utilise la Convention d’appel du langage C. Le modificateur « C » extern peut également être appliqué à plusieurs déclarations de fonction dans un bloc.

- Dans une déclaration de modèle, **extern** spécifie que le modèle a déjà été instancié ailleurs. **extern** indique au compilateur qu’il peut réutiliser l’autre instanciation, plutôt que d’en créer une nouvelle à l’emplacement actuel. Pour plus d’informations sur cette utilisation de **extern** , consultez [instanciation explicite](explicit-instantiation.md).

## <a name="opno-locextern-linkage-for-non-opno-locconst-globals"></a>extern de la liaison pour les globales nonconst

Lorsque l’éditeur de liens voit **extern** avant une déclaration de variable globale, il recherche la définition dans une autre unité de traduction. Les déclarations de variables non **constes** au niveau de la portée globale sont externes par défaut. Appliquez uniquement les **extern** aux déclarations qui ne fournissent pas la définition.

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

## <a name="opno-locextern-linkage-for-opno-locconst-globals"></a>extern de la liaison pour les const globaux

Une variable globale **const** a une liaison interne par défaut. Si vous souhaitez que la variable ait une liaison externe, appliquez le mot clé **extern** à la définition et à toutes les autres déclarations dans d’autres fichiers :

```cpp
//fileA.cpp
extern const int i = 42; // extern const definition

//fileB.cpp
extern const int i;  // declaration only. same as i in FileA
```

## <a name="opno-locextern-opno-locconstexpr-linkage"></a>liaison de constexpr extern

Dans Visual Studio 2017 version 15,3 et les versions antérieures, le compilateur a toujours donné une liaison interne de **constexpr** variable, même lorsque la variable a été marquée **extern** . Dans Visual Studio 2017 version 15,5 et versions ultérieures, le commutateur du compilateur [/Zc : externConstexpr](../build/reference/zc-externconstexpr.md) active le comportement correct de conformité aux normes. Finalement, l’option devient la valeur par défaut. L’option [/permissive-](../build/reference/permissive-standards-conformance.md) n’active pas **/Zc : externConstexpr**.

```cpp
extern constexpr int x = 10; //error LNK2005: "int const x" already defined
```

Si un fichier d’en-tête contient une variable déclarée **extern** **constexpr** , il doit être marqué `__declspec(selectany)` pour que ses déclarations dupliquées soient correctement combinées :

```cpp
extern constexpr __declspec(selectany) int x = 10;
```

## <a name="opno-locextern-c-and-opno-locextern-c-function-declarations"></a>extern les déclarations de fonction « CC++» et extern «»

Dans C++, lorsqu’il est utilisé avec une chaîne, **extern** spécifie que les conventions de liaison d’un autre langage sont utilisées pour le ou les déclarateurs. Les fonctions et les données C sont accessibles uniquement si elles sont précédemment déclarées comme ayant une liaison C. Toutefois, elles doivent être définies dans une unité de traduction compilée séparément.

Microsoft C++ prend en charge les chaînes **« C »** et **C++«»** dans le champ de *littéral de chaîne* . Tous les fichiers Include standard utilisent la syntaxe **extern « C »** pour permettre l’utilisation des fonctions de la bibliothèque Runtime dans C++ les programmes.

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

Si une fonction a plus d’une spécification de liaison, elle doit s’accorder. Il est erroné de déclarer des fonctions comme ayant à la fois C++ le C et la liaison. En outre, si deux déclarations pour une fonction se produisent dans un programme (une avec une spécification de liaison et une autre sans), la déclaration avec la spécification de la liaison doit être la première. Toutes les déclarations redondantes de fonctions qui ont déjà une spécification de liaison sont affectées de la liaison spécifiée dans la première déclaration. Par exemple :

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

[Mots clés](../cpp/keywords-cpp.md)\
[Unités de traduction et\ de liaison](program-and-linkage-cpp.md)
[extern spécificateur de classe de stockage en C](../c-language/extern-storage-class-specifier.md)\
[Comportement des identificateurs en C](../c-language/behavior-of-identifiers.md)\
[Liaison en C](../c-language/linkage.md)
