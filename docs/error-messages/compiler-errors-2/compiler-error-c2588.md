---
title: Erreur du compilateur C2588
ms.date: 11/04/2016
f1_keywords:
- C2588
helpviewer_keywords:
- C2588
ms.assetid: 19a0cabd-ca13-44a5-9be3-ee676abf9bc4
ms.openlocfilehash: 15f9ba62751d9b3cb17ab56659310292dab41adf
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50596779"
---
# <a name="compiler-error-c2588"></a>Erreur du compilateur C2588

' :: ~ identificateur ' : destructeur global non conforme

Le destructeur est défini pour un élément autre qu’une classe, une structure ou une union. Cette opération n’est pas autorisée.

Cette erreur peut être due à un manquant nom de classe, structure ou union sur le côté gauche de la résolution de portée (`::`) opérateur.

L’exemple suivant génère l’erreur C2588 :

```
// C2588.cpp
~F();   // C2588
```