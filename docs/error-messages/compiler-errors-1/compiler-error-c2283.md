---
title: Erreur du compilateur C2283
ms.date: 11/04/2016
f1_keywords:
- C2283
helpviewer_keywords:
- C2283
ms.assetid: 8a5b3175-b480-4598-a1f7-0b50504c5caa
ms.openlocfilehash: 7f3568aa5dfee116a225256a4452465c05f72f6f
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74759150"
---
# <a name="compiler-error-c2283"></a>Erreur du compilateur C2283

'identificateur' : spécificateur pure ou spécificateur de substitution abstrait non autorisé sur un struct sans nom

Une fonction membre d’une classe ou d’une structure sans nom est déclarée avec un spécificateur pure, ce qui n’est pas autorisé.

L’exemple suivant génère l’erreur C2283 :

```cpp
// C2283.cpp
// compile with: /c
struct {
   virtual void func() = 0;   // C2283
};
struct T {
   virtual void func() = 0;   // OK
};
```
