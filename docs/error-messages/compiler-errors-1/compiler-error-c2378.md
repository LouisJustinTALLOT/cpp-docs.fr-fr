---
title: Erreur du compilateur C2378
ms.date: 11/04/2016
f1_keywords:
- C2378
helpviewer_keywords:
- C2378
ms.assetid: 507a91c6-ca72-48df-b3a4-2cf931c86806
ms.openlocfilehash: fb6d228826cf1b21904863505c0963069e89d32d
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/24/2019
ms.locfileid: "64344879"
---
# <a name="compiler-error-c2378"></a>Erreur du compilateur C2378

'identificateur' : redéfinition ; un symbole ne peut pas être surchargé avec un typedef

L’identificateur a été redéfini en tant que `typedef`.

L’exemple suivant génère l’erreur C2378 :

```
// C2378.cpp
// compile with: /c
int i;
typedef int i;   // C2378
typedef int b;   // OK
```