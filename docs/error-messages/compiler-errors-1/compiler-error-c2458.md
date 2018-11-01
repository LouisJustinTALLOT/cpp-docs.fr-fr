---
title: Erreur du compilateur C2458
ms.date: 11/04/2016
f1_keywords:
- C2458
helpviewer_keywords:
- C2458
ms.assetid: ed21901f-1067-42f5-b275-19b480decf5c
ms.openlocfilehash: 8131b259f89c5cacd07d04edbf6c45adaa25b145
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50637851"
---
# <a name="compiler-error-c2458"></a>Erreur du compilateur C2458

'identificateur' : redéfinition au sein de la définition

Une classe, structure, union, énumération ou est redéfinie dans sa propre déclaration.

L’exemple suivant génère l’erreur C2458 :

```
// C2458.cpp
class C {
   enum i { C };   // C2458
};
```