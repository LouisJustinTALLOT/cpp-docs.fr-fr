---
title: Erreur du compilateur C3865 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3865
dev_langs:
- C++
helpviewer_keywords:
- C3865
ms.assetid: 9bc62bb0-4fb8-4856-a5cf-c7cb4029a596
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8fd5c83d922601ca4cdffe0f3772723b31e630b6
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46090839"
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