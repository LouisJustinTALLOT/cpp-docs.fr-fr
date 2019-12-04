---
title: Erreur du compilateur C3199
ms.date: 11/04/2016
f1_keywords:
- C3199
helpviewer_keywords:
- C3199
ms.assetid: e7a478d3-115a-40a3-991b-c7454fd2e28e
ms.openlocfilehash: 2f0ca98dc44a78adde378a0f80078ae30c590e11
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74738815"
---
# <a name="compiler-error-c3199"></a>Erreur du compilateur C3199

utilisation non valide des pragmas à virgule flottante : les exceptions ne sont pas prises en charge en mode non précis

Le pragma [float_control](../../preprocessor/float-control.md) a été utilisé pour spécifier le modèle d’exception à virgule flottante sous un paramètre [/FP](../../build/reference/fp-specify-floating-point-behavior.md) autre que **/FP : precise**.

L’exemple suivant génère l’C3199 :

```cpp
// C3199.cpp
// compile with: /fp:fast
#pragma float_control(except, on)   // C3199
```
