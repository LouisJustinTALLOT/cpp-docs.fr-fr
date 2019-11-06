---
title: Avertissement du compilateur (niveau 1) C4186
ms.date: 11/04/2016
f1_keywords:
- C4186
helpviewer_keywords:
- C4186
ms.assetid: caf3f7d8-f305-426b-8d4e-2b96f5c269ea
ms.openlocfilehash: 3dd339d7535d0a6ef077a562dd82b6c70d17bfb5
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/05/2019
ms.locfileid: "73624953"
---
# <a name="compiler-warning-level-1-c4186"></a>Avertissement du compilateur (niveau 1) C4186

\#attribut d’importation’attribut’requiert des arguments Count ; pas

Un attribut `#import` présente un nombre incorrect d’arguments.

## <a name="example"></a>Exemple

```cpp
// C4186.cpp
// compile with: /W1 /c
#import "stdole2.tlb" no_namespace("abc") rename("a","b","c")  // C4186
```

L’attribut `no_namespace` n’accepte aucun argument. L’attribut **rename** accepte uniquement deux arguments.