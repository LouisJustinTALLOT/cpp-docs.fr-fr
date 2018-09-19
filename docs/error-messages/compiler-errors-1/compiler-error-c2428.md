---
title: Erreur du compilateur C2428 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2428
dev_langs:
- C++
helpviewer_keywords:
- C2428
ms.assetid: 74aa5714-e930-4f9e-9061-68ccce7f0d38
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ac8b176db26ed615874569a9ed646b9d89ec4db0
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46097937"
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