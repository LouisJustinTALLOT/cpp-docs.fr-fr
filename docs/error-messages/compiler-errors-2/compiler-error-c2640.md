---
description: 'En savoir plus sur : erreur du compilateur C2640'
title: Erreur du compilateur C2640
ms.date: 11/04/2016
f1_keywords:
- C2640
helpviewer_keywords:
- C2640
ms.assetid: e4d137ab-ed1d-457c-9eec-b70d97f1b0b4
ms.openlocfilehash: e1bbcc2e0db1b12cb4b72f8346c1d5a55532d6da
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97160894"
---
# <a name="compiler-error-c2640"></a>Erreur du compilateur C2640

'identificateur' : modificateur de __based non conforme sur une référence

Le **`__based`** modificateur ne peut être utilisé que sur les pointeurs.

L’exemple suivant génère l’C2640 :

```cpp
// C2640.cpp
void f(int i) {
    void *vp;
    int _based(vp) &vr = I;  // C2640
}
```
