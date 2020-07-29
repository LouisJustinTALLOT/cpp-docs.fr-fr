---
title: Erreur du compilateur C2378
ms.date: 11/04/2016
f1_keywords:
- C2378
helpviewer_keywords:
- C2378
ms.assetid: 507a91c6-ca72-48df-b3a4-2cf931c86806
ms.openlocfilehash: c72a46bbc5778bf95ddc49426f97df0320b22a30
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87218232"
---
# <a name="compiler-error-c2378"></a>Erreur du compilateur C2378

'identificateur' : redéfinition ; un symbole ne peut pas être surchargé avec un typedef

L’identificateur a été redéfini en tant que **`typedef`** .

L’exemple suivant génère l’erreur C2378 :

```cpp
// C2378.cpp
// compile with: /c
int i;
typedef int i;   // C2378
typedef int b;   // OK
```
