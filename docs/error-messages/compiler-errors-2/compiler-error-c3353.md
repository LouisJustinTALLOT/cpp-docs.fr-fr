---
title: Erreur du compilateur C3353
ms.date: 11/04/2016
f1_keywords:
- C3353
helpviewer_keywords:
- C3353
ms.assetid: 5699c04b-d504-46ce-bf71-c200318fed71
ms.openlocfilehash: 332e0b253aed53f2adadf448b6a9c0681abc825e
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74747448"
---
# <a name="compiler-error-c3353"></a>Erreur du compilateur C3353

'délégué' : un délégué ne peut être créé qu'à partir d'une fonction globale ou à partir d'une fonction membre d'un type managé ou WinRT

Les délégués, déclarés avec le mot clé [Delegate](../../extensions/delegate-cpp-component-extensions.md) , peuvent uniquement être déclarés au niveau de la portée globale.

L'exemple suivant génère l'erreur C3353 :

```cpp
// C3353.cpp
// compile with: /clr
delegate int f;   // C3353
```
