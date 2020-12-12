---
description: 'En savoir plus sur : erreur du compilateur C3865'
title: Erreur du compilateur C3865
ms.date: 11/04/2016
f1_keywords:
- C3865
helpviewer_keywords:
- C3865
ms.assetid: 9bc62bb0-4fb8-4856-a5cf-c7cb4029a596
ms.openlocfilehash: 956cbfeb5bac97cae7e9a9a411c29326062e15b2
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97222877"
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
