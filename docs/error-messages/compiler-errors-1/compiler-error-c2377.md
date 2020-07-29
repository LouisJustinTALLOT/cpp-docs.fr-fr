---
title: Erreur du compilateur C2377
ms.date: 11/04/2016
f1_keywords:
- C2377
helpviewer_keywords:
- C2377
ms.assetid: f7660965-bf4c-4cd9-8307-1bd7016678a1
ms.openlocfilehash: 2bf73aa9aee2a45e5271570b4c45c8fecaa4a4bf
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87225538"
---
# <a name="compiler-error-c2377"></a>Erreur du compilateur C2377

'identificateur' : redéfinition ; un typedef ne peut pas être surchargé avec un autre symbole

Un **`typedef`** identificateur est redéfini.

L’exemple suivant génère l’erreur C2377 :

```cpp
// C2377.cpp
// compile with: /c
typedef int i;
int i;   // C2377
int j;   // OK
```
