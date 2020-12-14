---
description: 'En savoir plus sur : avertissement du compilateur (niveau 1 et niveau 4) C4700'
title: Avertissement du compilateur (niveaux 1 et 4) C4700
ms.date: 02/21/2018
f1_keywords:
- C4700
helpviewer_keywords:
- C4700
ms.assetid: 2da0deb4-77dd-4b05-98d3-b78d74ac4ca7
ms.openlocfilehash: 7ba19bdd6d8e25e095f796adc8cdb60b5cc8d325
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97241597"
---
# <a name="compiler-warning-level-1-and-level-4-c4700"></a>Avertissement du compilateur (niveaux 1 et 4) C4700

> variable locale'*Name*'non initialisée utilisée

Le *nom* de la variable locale a été *utilisé*, c’est-à-dire lu à partir de, avant qu’une valeur ne lui ait été assignée. En C et C++, les variables locales ne sont pas initialisées par défaut. Les variables non initialisées peuvent contenir n’importe quelle valeur et leur utilisation provoque un comportement non défini. AVERTISSEMENT C4700 indique presque toujours un bogue qui peut provoquer des résultats imprévisibles ou des blocages dans votre programme.

Pour résoudre ce problème, vous pouvez initialiser des variables locales lorsqu’elles sont déclarées ou leur assigner une valeur avant leur utilisation. Une fonction peut être utilisée pour initialiser une variable qui est passée en tant que paramètre de référence, ou lorsque son adresse est passée comme paramètre de pointeur.

## <a name="example"></a>Exemple

Cet exemple génère C4700 quand les variables t, u et v sont utilisées avant d’être initialisées, et affiche le type de valeur de garbage collection qui peut résulter. Les variables x, y et z ne génèrent pas d’avertissement, car elles sont initialisées avant d’être utilisées :

```cpp
// c4700.cpp
// compile by using: cl /EHsc /W4 c4700.cpp
#include <iostream>

// function takes an int reference to initialize
void initialize(int& i)
{
    i = 21;
}

int main()
{
    int s, t, u, v;   // Danger, uninitialized variables

    s = t + u + v;    // C4700: t, u, v used before initialization
    std::cout << "Value in s: " << s << std::endl;

    int w, x;         // Danger, uninitialized variables
    initialize(x);    // fix: call function to init x before use
    int y{10};        // fix: initialize y, z when declared
    int z{11};        // This C++11 syntax is recommended over int z = 11;

    w = x + y + z;    // Okay, all values initialized before use
    std::cout << "Value in w: " << w << std::endl;
}
```

Quand ce code est exécuté, t, u et v ne sont pas initialisés, et la sortie pour s est imprévisible :

```Output
Value in s: 37816963
Value in w: 42
```
