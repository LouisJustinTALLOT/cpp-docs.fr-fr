---
title: Erreur du compilateur C2428
ms.date: 11/04/2016
f1_keywords:
- C2428
helpviewer_keywords:
- C2428
ms.assetid: 74aa5714-e930-4f9e-9061-68ccce7f0d38
ms.openlocfilehash: 299a4e899a41bf47eec5eaf5b54d2307e557078e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50614667"
---
# <a name="compiler-error-c2428"></a>Erreur du compilateur C2428

'opération' : non autorisé sur un opérande de type 'bool'

Vous ne pouvez pas appliquer un opérateur de décrémentation aux objets de type `bool`.

L’exemple suivant génère l’erreur C2428 :

```
// C2428.cpp
void g(bool fFlag) {
   --fFlag;   // C2428
   fFlag--;   // C2428
}
```