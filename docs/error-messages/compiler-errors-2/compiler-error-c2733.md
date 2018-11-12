---
title: Erreur du compilateur C2733
ms.date: 11/04/2016
f1_keywords:
- C2733
helpviewer_keywords:
- C2733
ms.assetid: 67f83561-c633-407c-a2ee-f9fd16e165bf
ms.openlocfilehash: 26819f1928223b5fa96d275290105f32787057f5
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50518844"
---
# <a name="compiler-error-c2733"></a>Erreur du compilateur C2733

seconde liaison C d’une fonction surchargée 'fonction' non autorisée

Plus d’une fonction surchargée est déclarée avec liaison C. Lorsque vous utilisez une liaison C, seule une forme d’une fonction spécifiée peut être externe. Dans la mesure où les fonctions surchargées portent le même nom non décoré, ils ne peuvent pas être utilisés avec les programmes C.

L’exemple suivant génère l’erreur C2733 :

```
// C2733.cpp
extern "C" {
   void F1(int);
}

extern "C" {
   void F1();   // C2733
   // try the following line instead
   // void F2();
}
```