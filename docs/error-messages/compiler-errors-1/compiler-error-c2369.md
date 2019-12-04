---
title: Erreur du compilateur C2369
ms.date: 11/04/2016
f1_keywords:
- C2369
helpviewer_keywords:
- C2369
ms.assetid: 2a3933f6-2313-40ff-800f-921b296fdbbf
ms.openlocfilehash: ed7bcbf24ec7ef88ec12d83af4f08b12d56b347b
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74745757"
---
# <a name="compiler-error-c2369"></a>Erreur du compilateur C2369

'array' : redéfinition ; indices différents

Le tableau est déjà déclaré avec un indice différent.

L’exemple suivant génère l’erreur C2369 :

```cpp
// C2369.cpp
// compile with: /c
int a[10];
int a[20];   // C2369
int b[20];   // OK
```
