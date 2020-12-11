---
description: 'En savoir plus sur : erreur du compilateur C3199'
title: Erreur du compilateur C3199
ms.date: 11/04/2016
f1_keywords:
- C3199
helpviewer_keywords:
- C3199
ms.assetid: e7a478d3-115a-40a3-991b-c7454fd2e28e
ms.openlocfilehash: 598d21edbddc91d39edb9623dc59537d3e27bdf3
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97155473"
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
