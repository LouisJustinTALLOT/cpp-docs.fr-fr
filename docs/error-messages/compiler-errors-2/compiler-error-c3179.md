---
title: Erreur du compilateur C3179
ms.date: 11/04/2016
f1_keywords:
- C3179
helpviewer_keywords:
- C3179
ms.assetid: 60d7e41b-25fd-48ac-8b79-830c062f4dcd
ms.openlocfilehash: 330cc674f137e1d2718cf7535dbaffa96df01e8a
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74761684"
---
# <a name="compiler-error-c3179"></a>Erreur du compilateur C3179

type managé ou WinRT sans nom interdit

Tous les structs et toutes les classes CLR et WinRT doivent avoir des noms.

L'exemple suivant génère l'erreur C3179 et montre comment la corriger :

```cpp
// C3179a.cpp
// compile with: /clr /c
typedef value struct { // C3179
// try the following line instead
// typedef value struct MyStruct {
   int i;
} V;
```
