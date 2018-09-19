---
title: Erreur du compilateur C2871 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2871
dev_langs:
- C++
helpviewer_keywords:
- C2871
ms.assetid: 44aeb84d-61f0-45e0-8dad-22a3cd46b7f8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1e960dd6bc9fdf81d6a1bb127330f1066628fffd
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46117619"
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