---
description: 'En savoir plus sur : erreur du compilateur C2535'
title: Erreur du compilateur C2535
ms.date: 11/04/2016
f1_keywords:
- C2535
helpviewer_keywords:
- C2535
ms.assetid: a958f83e-e2bf-4a59-b44b-d406ec325d7e
ms.openlocfilehash: 149ddabcde7364513379701c55d4801fd403206b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97258081"
---
# <a name="compiler-error-c2535"></a>Erreur du compilateur C2535

'identificateur' : fonction membre déjà définie ou déclarée

Cette erreur peut être due à l’utilisation d’une même liste de paramètres formels dans plusieurs définitions ou déclarations d’une fonction surchargée.

Si vous obtenez C2535 en raison de la fonction dispose, consultez [destructeurs et finaliseurs](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Destructors_and_finalizers) pour plus d’informations.

L’exemple suivant génère l’C2535 :

```cpp
// C2535.cpp
// compile with: /c
class C {
public:
   void func();   // forward declaration
   void func() {}   // C2535
};
```
