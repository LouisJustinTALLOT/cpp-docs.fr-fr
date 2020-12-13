---
description: 'En savoir plus sur : avertissement du compilateur (niveau 1) C4384'
title: Avertissement du compilateur (niveau 1) C4384
ms.date: 11/04/2016
f1_keywords:
- C4384
helpviewer_keywords:
- C4384
ms.assetid: fafa8eb2-cbfc-4edb-8b0f-511ff5d37ac0
ms.openlocfilehash: 1db448de2cfafe684d2d9d366db001848c67c432
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97339907"
---
# <a name="compiler-warning-level-1-c4384"></a>Avertissement du compilateur (niveau 1) C4384

\#le pragma’make_public’doit être utilisé uniquement au niveau de la portée globale

Le pragma [make_public](../../preprocessor/make-public.md) a été appliqué de façon incorrecte.

## <a name="example"></a>Exemple

L’exemple suivant génère l’C4384.

```cpp
// C4384.cpp
// compile with: /c /W1
namespace n {
   #pragma make_public(N::C)   // C4384
   namespace N {
      class C {};
   }
}
```
