---
title: Erreur du compilateur C2535 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2535
dev_langs:
- C++
helpviewer_keywords:
- C2535
ms.assetid: a958f83e-e2bf-4a59-b44b-d406ec325d7e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5d9bb276ded32d8b263e64a8ea70f2c1953ee24b
ms.sourcegitcommit: d3c41b16bf05af2149090e996d8e71cd6cd55c7a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/09/2018
ms.locfileid: "48890294"
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