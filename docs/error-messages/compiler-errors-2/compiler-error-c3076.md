---
title: Erreur du compilateur C3076 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3076
dev_langs:
- C++
helpviewer_keywords:
- C3076
ms.assetid: 8a87b3e4-2c17-4b87-9622-ef0962d6a34e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f2d507e13c6dde451e6693774f708333a9301f8b
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46064059"
---
# <a name="compiler-error-c3076"></a>Erreur du compilateur C3076

'instance' : vous ne pouvez pas incorporer une instance d’un type référence, 'type', dans un type natif

Un type natif ne peut pas contenir une instance d’un type CLR.

Pour plus d’informations, consultez [sémantique de pile C++ pour les Types référence](../../dotnet/cpp-stack-semantics-for-reference-types.md).

## <a name="example"></a>Exemple

L’exemple suivant génère l’erreur C3076 :.

```
// C3076.cpp
// compile with: /clr /c
ref struct U {};

struct V {
   U y;   // C3076
};

ref struct W {
   U y;   // OK
};
```