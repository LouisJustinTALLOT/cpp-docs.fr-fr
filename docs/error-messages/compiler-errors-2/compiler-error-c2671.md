---
title: Erreur du compilateur C2671 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2671
dev_langs:
- C++
helpviewer_keywords:
- C2671
ms.assetid: fc0ee40f-c8f3-408f-b89d-745d149c4169
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b37d9dc1e50da921bdbe758e73257100853517eb
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46026153"
---
# <a name="compiler-error-c2671"></a>Erreur du compilateur C2671

'fonction' : les fonctions membres statiques n’ont pas de pointeurs 'this'

Un `static` fonction membre a tenté d’accéder à `this`.

L’exemple suivant génère l’erreur C2671 :

```
// C2671.cpp
struct S {
   static S* const func() { return this; }  // C2671
};
```