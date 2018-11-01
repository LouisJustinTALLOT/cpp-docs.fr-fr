---
title: Erreur du compilateur C3753
ms.date: 11/04/2016
f1_keywords:
- C3753
helpviewer_keywords:
- C3753
ms.assetid: a5b99e28-796c-4107-a673-97c2ae3bb2b9
ms.openlocfilehash: b6b1e8c3241a778b29045e734fffebb663554e62
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50498369"
---
# <a name="compiler-error-c3753"></a>Erreur du compilateur C3753

une propriété générique n’est pas autorisée.

Listes de paramètres génériques peuvent apparaître uniquement sur les classes managées, des structs ou des fonctions.

Pour plus d’informations, consultez [génériques](../../windows/generics-cpp-component-extensions.md) et [propriété](../../windows/property-cpp-component-extensions.md).

## <a name="example"></a>Exemple

L’exemple suivant génère C3753.

```
// C3753.cpp
// compile with: /clr /c
ref struct A {
   generic <typename T>
   property int i;   // C3753 error
};
```