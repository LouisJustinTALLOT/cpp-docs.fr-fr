---
description: 'En savoir plus sur : erreur du compilateur C3420'
title: Erreur du compilateur C3420
ms.date: 11/04/2016
f1_keywords:
- C3420
helpviewer_keywords:
- C3420
ms.assetid: 99b53c77-f36b-4574-9199-b53111becccb
ms.openlocfilehash: 3c79693823255ed7335e5805c0ac17de5ddcead7
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97315996"
---
# <a name="compiler-error-c3420"></a>Erreur du compilateur C3420

'finalizer' : un finaliseur ne peut pas être virtuel

Un finaliseur peut uniquement être appelé de façon non virtuelle depuis son type englobant. Ainsi, il est incorrect de déclarer un finaliseur virtuel.

Pour plus d’informations, consultez [destructeurs et finaliseurs dans Guide pratique pour définir et consommer des classes et des structs (C++/CLI)](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Destructors_and_finalizers).

## <a name="example"></a>Exemple

L’exemple suivant génère l’erreur C3420.

```cpp
// C3420.cpp
// compile with: /clr /c
ref class R {
   virtual !R() {}   // C3420
};
```
