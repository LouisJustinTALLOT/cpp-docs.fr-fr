---
title: Erreur du compilateur C2082
ms.date: 11/04/2016
f1_keywords:
- C2082
helpviewer_keywords:
- C2082
ms.assetid: 87a6d442-157c-46e8-9bff-8388f8338ae0
ms.openlocfilehash: 8bfb54dc91ef9132e3930e2c0799070f80f5cd0f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50577253"
---
# <a name="compiler-error-c2082"></a>Erreur du compilateur C2082

redéfinition du paramètre formel 'identifier'

Un paramètre formel d’une fonction est redéclaré dans le corps de la fonction. Pour corriger l’erreur, supprimez la redéfinition.

L’exemple suivant génère l’erreur C2082 :

```
// C2082.cpp
void func(int i) {
   int i;   // C2082
   int ii;   // OK
}
```