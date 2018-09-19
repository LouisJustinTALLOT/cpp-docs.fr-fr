---
title: Erreur du compilateur C2575 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2575
dev_langs:
- C++
helpviewer_keywords:
- C2575
ms.assetid: 9eb45706-37ef-4481-b373-6d193ba13634
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 321c226cf9edcb0860abb6917c6cff67a6df348d
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46052034"
---
# <a name="compiler-error-c2575"></a>Erreur du compilateur C2575

'identificateur' : seules les fonctions membres et les bases peuvent être virtuelles

Une fonction globale ou la classe est déclarée `virtual`. Cette opération n’est pas autorisée.

L’exemple suivant génère l’erreur C2575 :

```
// C2575.cpp
// compile with: /c
virtual void func() {}   // C2575

void func2() {}
struct A {
   virtual void func2(){}
};
```