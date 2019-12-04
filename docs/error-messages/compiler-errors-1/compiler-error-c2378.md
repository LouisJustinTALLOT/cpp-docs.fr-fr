---
title: Erreur du compilateur C2378
ms.date: 11/04/2016
f1_keywords:
- C2378
helpviewer_keywords:
- C2378
ms.assetid: 507a91c6-ca72-48df-b3a4-2cf931c86806
ms.openlocfilehash: 63063ec98bbc4d42f3237fd42e42b9fdce489892
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74745419"
---
# <a name="compiler-error-c2378"></a>Erreur du compilateur C2378

'identificateur' : redéfinition ; un symbole ne peut pas être surchargé avec un typedef

L’identificateur a été redéfini en tant que `typedef`.

L’exemple suivant génère l’erreur C2378 :

```cpp
// C2378.cpp
// compile with: /c
int i;
typedef int i;   // C2378
typedef int b;   // OK
```
