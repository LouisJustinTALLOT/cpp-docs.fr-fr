---
title: Erreur du compilateur C2460 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2460
dev_langs:
- C++
helpviewer_keywords:
- C2460
ms.assetid: d969fca9-3ac5-4e4e-88fc-df05510e2093
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: cb2d85ffbc7aa799f0688fbb10021a04ef9455ad
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46022613"
---
# <a name="compiler-error-c2460"></a>Erreur du compilateur C2460

'identificateur1' : utilise 'identificateur2', qui est défini

Une classe ou structure (`identifier2`) est déclaré en tant que membre de lui-même (`identifier1`). Les définitions des classes et des structures récursives ne sont pas autorisées.

L’exemple suivant génère l’erreur C2460 :

```
// C2460.cpp
class C {
   C aC;    // C2460
};
```

Au lieu de cela, utilisez une référence de pointeur de la classe.

```
// C2460.cpp
class C {
   C * aC;    // OK
};
```