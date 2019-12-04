---
title: Erreur du compilateur C2377
ms.date: 11/04/2016
f1_keywords:
- C2377
helpviewer_keywords:
- C2377
ms.assetid: f7660965-bf4c-4cd9-8307-1bd7016678a1
ms.openlocfilehash: a1e8c50f7e5d822571daeefffc93d3e8c572c01b
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74745497"
---
# <a name="compiler-error-c2377"></a>Erreur du compilateur C2377

'identificateur' : redéfinition ; un typedef ne peut pas être surchargé avec un autre symbole

Un identificateur `typedef` est redéfini.

L’exemple suivant génère l’erreur C2377 :

```cpp
// C2377.cpp
// compile with: /c
typedef int i;
int i;   // C2377
int j;   // OK
```
