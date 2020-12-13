---
description: 'En savoir plus sur : erreur du compilateur C3353'
title: Erreur du compilateur C3353
ms.date: 11/04/2016
f1_keywords:
- C3353
helpviewer_keywords:
- C3353
ms.assetid: 5699c04b-d504-46ce-bf71-c200318fed71
ms.openlocfilehash: 50ff7a6b104f3e16ce17f1398da49a146c0d41a4
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97335041"
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
