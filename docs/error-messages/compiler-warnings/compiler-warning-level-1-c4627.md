---
description: 'En savoir plus sur : avertissement du compilateur (niveau 1) C4627'
title: Avertissement du compilateur (niveau 1) C4627
ms.date: 09/09/2018
f1_keywords:
- C4627
helpviewer_keywords:
- C4627
ms.assetid: 8840f3e6-b496-423a-8635-eb55d5f854a2
ms.openlocfilehash: fc4c6c3931775b090dfd4c7c2fd5fd97441d40d3
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97281442"
---
# <a name="compiler-warning-level-1-c4627"></a>Avertissement du compilateur (niveau 1) C4627

> '*HEADER_FILE*' : ignoré lors de la recherche d’une utilisation d’en-tête précompilé

Si l’option [/Yu utiliser le fichier d' \( en-tête précompilé](../../build/reference/yu-use-precompiled-header-file.md) est définie pour le fichier source actuel, le compilateur ignore tout ce qui se trouve dans le fichier avant l’inclusion de l’en-tête précompilé. L’avertissement **C4627** est généré dans Visual Studio 2015 et versions antérieures si *HEADER_FILE* est inclus avant le fichier d’en-tête précompilé, et si l’en-tête précompilé n’inclut pas non plus *HEADER_FILE*.

## <a name="example"></a>Exemple

Cet exemple montre comment l’erreur peut se produire et montre comment la corriger :

```cpp
// c4627.cpp
#include <iostream>       // C4627 - iostream not included by pch.h
#include "pch.h"          // precompiled header file that does not include iostream
// #include <iostream>    // To fix, move the iostream header include here from above
int main()
{
    std::cout << "std::cout is defined!\n";
}
```

## <a name="see-also"></a>Voir aussi

[Création de fichiers d’en-tête précompilé](../../build/creating-precompiled-header-files.md)
