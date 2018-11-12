---
title: Erreur du compilateur C3353
ms.date: 11/04/2016
f1_keywords:
- C3353
helpviewer_keywords:
- C3353
ms.assetid: 5699c04b-d504-46ce-bf71-c200318fed71
ms.openlocfilehash: eb7b55f63e911f155c13e777e2e84ae7b587e9a3
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50432667"
---
# <a name="compiler-error-c3353"></a>Erreur du compilateur C3353

'délégué' : un délégué ne peut être créé qu'à partir d'une fonction globale ou à partir d'une fonction membre d'un type managé ou WinRT

Les délégués, déclarés avec le [déléguer](../../windows/delegate-cpp-component-extensions.md) mot clé, peuvent uniquement être déclarés avec une portée globale.

L'exemple suivant génère l'erreur C3353 :

```
// C3353.cpp
// compile with: /clr
delegate int f;   // C3353
```