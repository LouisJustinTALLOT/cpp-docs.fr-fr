---
title: Erreur du compilateur C2640 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2640
dev_langs:
- C++
helpviewer_keywords:
- C2640
ms.assetid: e4d137ab-ed1d-457c-9eec-b70d97f1b0b4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ad39b2a9e3397f97ddc4a900bc45d1983ebbf574
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46085278"
---
# <a name="compiler-error-c2640"></a>Erreur du compilateur C2640

'identificateur' : modificateur __based non conforme sur une référence

Le `__based` modificateur peut être utilisé sur les pointeurs uniquement.

L’exemple suivant génère l’erreur C2640 :

```
// C2640.cpp
void f(int i) {
    void *vp;
    int _based(vp) &vr = I;  // C2640
}
```