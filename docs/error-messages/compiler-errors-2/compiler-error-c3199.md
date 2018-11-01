---
title: Erreur du compilateur C3199
ms.date: 11/04/2016
f1_keywords:
- C3199
helpviewer_keywords:
- C3199
ms.assetid: e7a478d3-115a-40a3-991b-c7454fd2e28e
ms.openlocfilehash: 934e980149ad893e6799b0ab119a148fc5652fdc
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50578956"
---
# <a name="compiler-error-c3199"></a>Erreur du compilateur C3199

utilisation non valide des pragmas à virgule flottante : les exceptions ne sont pas pris en charge en mode sans précision

Le [float_control](../../preprocessor/float-control.md) pragma a été utilisé pour spécifier le modèle de virgule flottante sous un [/FP](../../build/reference/fp-specify-floating-point-behavior.md) paramètre autre que **/fp : precise**.

L’exemple suivant génère l’erreur C3199 :

```
// C3199.cpp
// compile with: /fp:fast
#pragma float_control(except, on)   // C3199
```