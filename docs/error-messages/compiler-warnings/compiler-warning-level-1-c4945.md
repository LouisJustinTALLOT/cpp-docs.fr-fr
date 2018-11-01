---
title: Avertissement du compilateur (niveau 1) C4945
ms.date: 11/04/2016
f1_keywords:
- C4945
helpviewer_keywords:
- C4945
ms.assetid: 6d2079ea-dc59-4611-bc68-9a22c06f7587
ms.openlocfilehash: 62dfbaed28f1afcdedb41d83158dfe4e8e0f61b6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50653854"
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