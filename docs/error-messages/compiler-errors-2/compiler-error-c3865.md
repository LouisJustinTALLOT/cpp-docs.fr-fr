---
title: Erreur du compilateur C3865
ms.date: 11/04/2016
f1_keywords:
- C3865
helpviewer_keywords:
- C3865
ms.assetid: 9bc62bb0-4fb8-4856-a5cf-c7cb4029a596
ms.openlocfilehash: 846657d3598e268d78ff3c39f2bfc901756ad370
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62302018"
---
# <a name="compiler-error-c3865"></a>Erreur du compilateur C3865

'convention_appel' : peut uniquement être utilisé sur des fonctions membres natives

Une convention d’appel a été utilisée sur une fonction qui a été soit une fonction globale ou sur une fonction membre managée. La convention d’appel peut uniquement être utilisée sur une fonction membre (non géré) natif.

Pour plus d’informations, consultez [Conventions d’appel](../../cpp/calling-conventions.md).

L’exemple suivant génère l’erreur C3865 :

```
// C3865.cpp
// compile with: /clr
// processor: x86
void __thiscall Func(){}   // C3865

// OK
struct MyType {
   void __thiscall Func(){}
};
```