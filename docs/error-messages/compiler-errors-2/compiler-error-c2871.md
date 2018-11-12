---
title: Erreur du compilateur C2871
ms.date: 11/04/2016
f1_keywords:
- C2871
helpviewer_keywords:
- C2871
ms.assetid: 44aeb84d-61f0-45e0-8dad-22a3cd46b7f8
ms.openlocfilehash: 355a485de46916977be6f7b801794806a9c9e0ba
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50492862"
---
# <a name="compiler-error-c2871"></a>Erreur du compilateur C2871

'name' : un espace de noms portant ce nom n’existe pas

Cette erreur se produit lorsque vous passez un identificateur qui n’est pas un espace de noms à un [à l’aide de](../../cpp/namespaces-cpp.md#using_directives) directive.

## <a name="example"></a>Exemple

L’exemple suivant génère C2871 :

```cpp
// C2871.cpp
// compile with: /c
namespace a {
   int fn(int i) { return i; }
}
namespace b {
   using namespace d;   // C2871 because d is not a namespace
   using namespace a;   // OK
}
```