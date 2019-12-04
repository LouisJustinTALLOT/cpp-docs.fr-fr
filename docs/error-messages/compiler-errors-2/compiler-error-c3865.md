---
title: Erreur du compilateur C3865
ms.date: 11/04/2016
f1_keywords:
- C3865
helpviewer_keywords:
- C3865
ms.assetid: 9bc62bb0-4fb8-4856-a5cf-c7cb4029a596
ms.openlocfilehash: 960c795fe934433e4e3cf79e4c01c49d00205b9b
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74761489"
---
# <a name="compiler-error-c3865"></a>Erreur du compilateur C3865

'calling_convention' : ne peut être utilisé que sur des fonctions membres natives

Une convention d’appel a été utilisée sur une fonction qui était soit une fonction globale, soit une fonction membre managée. La Convention d’appel ne peut être utilisée que sur une fonction membre native (non managée).

Pour plus d’informations, consultez [conventions d’appel](../../cpp/calling-conventions.md).

L’exemple suivant génère l’C3865 :

```cpp
// C3865.cpp
// compile with: /clr
// processor: x86
void __thiscall Func(){}   // C3865

// OK
struct MyType {
   void __thiscall Func(){}
};
```
