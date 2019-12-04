---
title: Erreur du compilateur C3075
ms.date: 11/04/2016
f1_keywords:
- C3075
helpviewer_keywords:
- C3075
ms.assetid: f431daa9-e0fa-48f0-a5c3-f99be96b55e3
ms.openlocfilehash: 345cdd17b9da0be8f8d6e9f7b5f48624ade412bd
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74761580"
---
# <a name="compiler-error-c3075"></a>Erreur du compilateur C3075

'instance' : vous ne pouvez pas incorporer une instance d’un type référence, 'type', dans un type valeur

Un type valeur ne peut pas contenir une instance d’un type référence.

Pour plus d’informations, consultez [ C++ sémantique de pile pour les types référence](../../dotnet/cpp-stack-semantics-for-reference-types.md).

## <a name="example"></a>Exemple

L’exemple suivant génère l’erreur C3075.

```cpp
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
