---
title: Compilateur avertissement (niveau 1) C4627 | Microsoft Docs
ms.custom: ''
ms.date: 09/09/2018
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4627
dev_langs:
- C++
helpviewer_keywords:
- C4627
ms.assetid: 8840f3e6-b496-423a-8635-eb55d5f854a2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8f6be9ba8ba45adecfe5355848126dcb4b3b2fd1
ms.sourcegitcommit: 592a2f402fef502450a45571a846175cc3ab1ceb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/09/2018
ms.locfileid: "44249618"
---
# <a name="compiler-warning-level-1-c4627"></a>Avertissement du compilateur (niveau 1) C4627

> «*header_file*' : ignoré lors de la recherche une utilisation d’en-tête précompilé

Si le fichier source actuel a le [/Yu \(utilisation de fichier d’en-tête précompilé)](../../build/reference/yu-use-precompiled-header-file.md) option set, le compilateur ignore tous les éléments dans le fichier avant de l’en-tête précompilé est inclus. Avertissement **C4627** est générée dans Visual Studio 2015 et versions antérieures si *header_file* est inclus avant le fichier d’en-tête précompilé, et si l’en-tête précompilé n’inclut pas également *header_file*.

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

[Création de fichiers d’en-tête précompilé](../../build/reference/creating-precompiled-header-files.md)
