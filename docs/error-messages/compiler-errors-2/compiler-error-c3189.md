---
title: Erreur du compilateur C3189 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3189
dev_langs:
- C++
helpviewer_keywords:
- C3189
ms.assetid: b254de79-931e-4a59-a9f4-1c690d90ca5e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c4666a16aed6d26f1cf38e4b32523c7c36948274
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46093868"
---
# <a name="compiler-error-c3189"></a>Erreur du compilateur C3189

' typeid\<tapez déclarateur abstrait >': cette syntaxe n’est plus pris en charge, utilisez :: typeid à la place

Une forme obsolète de [typeid](../../windows/typeid-cpp-component-extensions.md) a été utilisé, utiliser le nouveau formulaire.

L’exemple suivant génère l’erreur C3189 :

```
// C3189.cpp
// compile with: /clr
int main() {
   System::Type^ t  = typeid<System::Object>;   // C3189
   System::Type^ t2  = System::Object::typeid;   // OK
}
```