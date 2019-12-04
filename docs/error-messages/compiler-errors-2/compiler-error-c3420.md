---
title: Erreur du compilateur C3420
ms.date: 11/04/2016
f1_keywords:
- C3420
helpviewer_keywords:
- C3420
ms.assetid: 99b53c77-f36b-4574-9199-b53111becccb
ms.openlocfilehash: 5e165a0c181bc27adebe75111050f49130305693
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74756251"
---
# <a name="compiler-error-c3420"></a>Erreur du compilateur C3420

'finalizer' : un finaliseur ne peut pas être virtuel

Un finaliseur peut uniquement être appelé de façon non virtuelle depuis son type englobant. Ainsi, il est incorrect de déclarer un finaliseur virtuel.

Pour plus d’informations, consultez [destructeurs et finaliseurs dans Guide pratique pour définir et consommer des classes et desC++structs (/CLI)](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Destructors_and_finalizers).

## <a name="example"></a>Exemple

L’exemple suivant génère l’erreur C3420.

```cpp
// C3420.cpp
// compile with: /clr /c
ref class R {
   virtual !R() {}   // C3420
};
```
