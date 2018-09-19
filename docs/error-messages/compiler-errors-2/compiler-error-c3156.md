---
title: Erreur du compilateur C3156 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3156
dev_langs:
- C++
helpviewer_keywords:
- C3156
ms.assetid: 1876da78-b94e-4af7-9795-28f72b209b3e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: cfb52ad730df486ee804bcf958505512fadc0150
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46116698"
---
# <a name="compiler-error-c3156"></a>Erreur du compilateur C3156

'classe' : vous ne pouvez pas avoir de définition locale d'un type managé ou WinRT

Une fonction ne peut pas contenir la définition, ou la déclaration, d'une classe, d'un struct ou d'une interface managé(e) ou WinRT.

## <a name="example"></a>Exemple

L'exemple suivant génère l'erreur C3156.

```
// C3156.cpp
// compile with: /clr /c
void f() {
   ref class X {};   // C3156
   ref class Y;   // C3156
}
```
