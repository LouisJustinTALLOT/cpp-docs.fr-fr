---
title: Compilateur avertissement (niveau 1) C4945 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4945
dev_langs:
- C++
helpviewer_keywords:
- C4945
ms.assetid: 6d2079ea-dc59-4611-bc68-9a22c06f7587
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 48797667c880bcd441065da3651adabdb955b52b
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46027516"
---
# <a name="compiler-warning-level-1-c4945"></a>Avertissement du compilateur (niveau 1) C4945

'symbole' : Impossible d’importer le symbole de 'assembly2' : comme 'symbol' a déjà été importé à partir d’un autre assembly 'assembly1'

Un symbole a été importé à partir d’un assembly référencé, mais ce symbole a déjà été importé à partir d’un autre assembly référencé. Ne pas référencer un des assemblys ou obtenir le nom du symbole modifié dans un des assemblys.

Les exemples suivants génèrent l’erreur C4945.

```
// C4945a.cs
// compile with: /target:library
// C# source code to create a dll
public class ClassA {
   public int i;
}
```

Et puis

```
// C4945b.cs
// compile with: /target:library
// C# source code to create a dll
public class ClassA {
   public int i;
}
```

Et puis

```
// C4945c.cpp
// compile with: /clr /LD /W1
#using "C4945a.dll"
#using "C4945b.dll"   // C4945
```