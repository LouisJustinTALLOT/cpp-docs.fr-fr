---
title: Erreur du compilateur C2711 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2711
dev_langs:
- C++
helpviewer_keywords:
- C2711
ms.assetid: 9df9f808-7419-4e63-abdd-e6538ff0871f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c5a2e757c525d272055077cb95516abf42c06dbc
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46088434"
---
# <a name="compiler-error-c2711"></a>Erreur du compilateur C2711

'fonction' : cette fonction ne peut pas être compilé comme code managé, utilisez #pragma unmanaged

Certaines instructions empêche le compilateur de générer le code MSIL pour la fonction englobante.

L’exemple suivant génère l’erreur C2711 :

```
// C2711.cpp
// compile with: /clr
// processor: x86
using namespace System;
value struct V {
   static const t = 10;
};

void bar() {
   V::t;
   __asm int 3   // C2711 inline asm can't be compiled managed
}
```