---
title: Erreur du compilateur C2535
ms.date: 11/04/2016
f1_keywords:
- C2535
helpviewer_keywords:
- C2535
ms.assetid: a958f83e-e2bf-4a59-b44b-d406ec325d7e
ms.openlocfilehash: b2b5452cfe59284d56b019674ffbabbda0dc62d1
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/24/2019
ms.locfileid: "64344706"
---
# <a name="compiler-error-c2535"></a>Erreur du compilateur C2535

'identificateur' : fonction membre déjà définie ou déclarée

Cette erreur peut être dû à l’aide de la même liste de paramètres formels dans plus d’une définition ou déclaration d’une fonction surchargée.

Si vous obtenez C2535 en raison de la fonction Dispose, consultez [destructeurs et finaliseurs](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Destructors_and_finalizers) pour plus d’informations.

L’exemple suivant génère l’erreur C2535 :

```
// C2535.cpp
// compile with: /c
class C {
public:
   void func();   // forward declaration
   void func() {}   // C2535
};
```