---
description: 'En savoir plus sur : erreur du compilateur C2726'
title: Erreur du compilateur C2726
ms.date: 11/04/2016
f1_keywords:
- C2726
helpviewer_keywords:
- C2726
ms.assetid: f0191bb7-c175-450b-bf09-a3213db96d09
ms.openlocfilehash: 9318ea0cbf695f1c42253a680143edb7b541d25e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97245328"
---
# <a name="compiler-error-c2726"></a>Erreur du compilateur C2726

'gcnew' peut uniquement être utilisé pour créer un objet avec un type managé ou WinRT

Vous ne pouvez pas créer une instance d'un type natif sur le tas récupéré par le garbage collector.

L'exemple suivant génère l'erreur C2726 et montre comment la corriger :

```cpp
// C2726.cpp
// compile with: /clr
using namespace System;
class U {};
ref class V {};
value class W {};

int main() {
   U* pU = gcnew U;    // C2726
   U* pU2 = new U;   // OK
   V^ p2 = gcnew V;   // OK
   W p3;   // OK

}
```
