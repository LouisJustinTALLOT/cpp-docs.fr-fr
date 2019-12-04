---
title: Erreur du compilateur C2637
ms.date: 11/04/2016
f1_keywords:
- C2637
helpviewer_keywords:
- C2637
ms.assetid: 58d94447-eb96-4d8f-a690-dd78d322462e
ms.openlocfilehash: a17bd95cf1727d058e0cbd9e3dfb93c500da9fb5
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74758253"
---
# <a name="compiler-error-c2637"></a>Erreur du compilateur C2637

'identificateur' : impossible de modifier les pointeurs vers des données membres

Un pointeur vers un membre de données ne peut pas avoir de convention d’appel. Pour résoudre le, supprimez la Convention d’appel ou déclarez un pointeur vers une fonction membre.

L’exemple suivant génère l’C2637 :

```cpp
// C2637.cpp
// compile with: /c
struct S {};
int __stdcall S::*pms1;   // C2637

// OK
int S::*pms2;
int (__stdcall S::*pms3)(...);
```
