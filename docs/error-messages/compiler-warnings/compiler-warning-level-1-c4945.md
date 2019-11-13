---
title: Avertissement du compilateur (niveau 1) C4945
ms.date: 11/04/2016
f1_keywords:
- C4945
helpviewer_keywords:
- C4945
ms.assetid: 6d2079ea-dc59-4611-bc68-9a22c06f7587
ms.openlocfilehash: 6a20effcebe1a36fa1356fffefa3a23a0056a0f0
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/13/2019
ms.locfileid: "74052262"
---
# <a name="compiler-warning-level-1-c4945"></a>Avertissement du compilateur (niveau 1) C4945

'Symbol' : impossible d’importer le symbole de’Assembly2 ', car’Symbol’a déjà été importé à partir d’un autre assembly’Assembly1 '

Un symbole a été importé à partir d’un assembly référencé, mais ce symbole a déjà été importé à partir d’un autre assembly référencé. Ne référencez pas l’un des assemblys ou récupérez le nom de symbole modifié dans l’un des assemblys.

Les exemples suivants génèrent des C4945.

```csharp
// C4945a.cs
// compile with: /target:library
// C# source code to create a dll
public class ClassA {
   public int i;
}
```

Et puis

```csharp
// C4945b.cs
// compile with: /target:library
// C# source code to create a dll
public class ClassA {
   public int i;
}
```

Et puis

```cpp
// C4945c.cpp
// compile with: /clr /LD /W1
#using "C4945a.dll"
#using "C4945b.dll"   // C4945
```