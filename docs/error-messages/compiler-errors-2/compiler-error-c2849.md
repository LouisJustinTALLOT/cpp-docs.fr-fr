---
description: 'En savoir plus sur : erreur du compilateur C2849'
title: Erreur du compilateur C2849
ms.date: 11/04/2016
f1_keywords:
- C2849
helpviewer_keywords:
- C2849
ms.assetid: e28f6b3e-e0e7-4f92-b006-ebaa81d368e6
ms.openlocfilehash: 890d8e9d257e1efc20058f0e2f47ccf04ea3217b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97260187"
---
# <a name="compiler-error-c2849"></a>Erreur du compilateur C2849

'destructeur' : une interface ne peut pas avoir de destructeur

Une [interface](../../cpp/interface.md) de Visual C++ ne peut pas avoir de destructeur.

L’exemple suivant génère l’C2849 :

```cpp
// C2849.cpp
// compile with: /c
__interface C {
   ~C();   // C2849 destructor not allowed in an interface
};
```
