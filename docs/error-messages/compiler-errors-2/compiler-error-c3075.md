---
description: 'En savoir plus sur : erreur du compilateur C3075'
title: Erreur du compilateur C3075
ms.date: 11/04/2016
f1_keywords:
- C3075
helpviewer_keywords:
- C3075
ms.assetid: f431daa9-e0fa-48f0-a5c3-f99be96b55e3
ms.openlocfilehash: 68169ade5e9de13b618fe6d90936cbe887690775
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97320221"
---
# <a name="compiler-error-c3075"></a>Erreur du compilateur C3075

'instance' : vous ne pouvez pas incorporer une instance d’un type référence, 'type', dans un type valeur

Un type valeur ne peut pas contenir une instance d’un type référence.

Pour plus d’informations, consultez [sémantique de pile C++ pour les types référence](../../dotnet/cpp-stack-semantics-for-reference-types.md).

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
