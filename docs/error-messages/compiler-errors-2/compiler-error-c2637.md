---
description: 'En savoir plus sur : erreur du compilateur C2637'
title: Erreur du compilateur C2637
ms.date: 11/04/2016
f1_keywords:
- C2637
helpviewer_keywords:
- C2637
ms.assetid: 58d94447-eb96-4d8f-a690-dd78d322462e
ms.openlocfilehash: 1f42a732d5dfa3f7c94e0cc755bd1db00c8ff56b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97208721"
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
