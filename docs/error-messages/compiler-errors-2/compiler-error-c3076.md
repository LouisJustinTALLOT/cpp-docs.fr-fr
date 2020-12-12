---
description: 'En savoir plus sur : erreur du compilateur C3076'
title: Erreur du compilateur C3076
ms.date: 11/04/2016
f1_keywords:
- C3076
helpviewer_keywords:
- C3076
ms.assetid: 8a87b3e4-2c17-4b87-9622-ef0962d6a34e
ms.openlocfilehash: 27fbfe27d2e8efb1abee611701fdbde8f0d3d09f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97320178"
---
# <a name="compiler-error-c3076"></a>Erreur du compilateur C3076

'instance' : vous ne pouvez pas incorporer une instance d’un type référence, 'type', dans un type natif

Un type natif ne peut pas contenir une instance d’un type CLR.

Pour plus d’informations, consultez [sémantique de pile C++ pour les types référence](../../dotnet/cpp-stack-semantics-for-reference-types.md).

## <a name="example"></a>Exemple

L’exemple suivant génère l’C3076.

```cpp
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
