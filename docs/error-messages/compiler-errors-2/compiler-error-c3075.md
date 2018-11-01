---
title: Erreur du compilateur C3075
ms.date: 11/04/2016
f1_keywords:
- C3075
helpviewer_keywords:
- C3075
ms.assetid: f431daa9-e0fa-48f0-a5c3-f99be96b55e3
ms.openlocfilehash: 0494961b47e99ce1f3e559302aff56278098a912
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50591631"
---
# <a name="compiler-error-c3075"></a>Erreur du compilateur C3075

'instance' : vous ne pouvez pas incorporer une instance d’un type référence, 'type', dans un type valeur

Un type valeur ne peut pas contenir une instance d’un type référence.

Pour plus d’informations, consultez [sémantique de pile C++ pour les Types référence](../../dotnet/cpp-stack-semantics-for-reference-types.md).

## <a name="example"></a>Exemple

L’exemple suivant génère l’erreur C3075.

```
// C3075.cpp
// compile with: /clr /c
ref struct U {};
value struct X {
   U y;   // C3075
};

ref struct Y {
   U y;   // OK
};
```