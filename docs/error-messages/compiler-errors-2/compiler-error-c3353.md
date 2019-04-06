---
title: Erreur du compilateur C3353
ms.date: 11/04/2016
f1_keywords:
- C3353
helpviewer_keywords:
- C3353
ms.assetid: 5699c04b-d504-46ce-bf71-c200318fed71
ms.openlocfilehash: c38642d7abd4f2fd50792c548c9a5521b2da10ad
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/05/2019
ms.locfileid: "58776139"
---
# <a name="compiler-error-c3353"></a>Erreur du compilateur C3353

'délégué' : un délégué ne peut être créé qu'à partir d'une fonction globale ou à partir d'une fonction membre d'un type managé ou WinRT

Les délégués, déclarés avec le [déléguer](../../extensions/delegate-cpp-component-extensions.md) mot clé, peuvent uniquement être déclarés avec une portée globale.

L'exemple suivant génère l'erreur C3353 :

```
// C3353.cpp
// compile with: /clr
delegate int f;   // C3353
```