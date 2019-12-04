---
title: Erreur du compilateur C2201
ms.date: 11/04/2016
f1_keywords:
- C2201
helpviewer_keywords:
- C2201
ms.assetid: ed927659-6e9c-447d-9963-19969ae1e957
ms.openlocfilehash: 0b2a73358dc6e5991ebf086e8c774116e2fbd3de
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74758968"
---
# <a name="compiler-error-c2201"></a>Erreur du compilateur C2201

'identificateur' : doit avoir une liaison externe pour pouvoir être exporté/importé

L’identificateur exporté est `static`.

L’exemple suivant génère l’erreur C2286 :

```cpp
// C2201.cpp
// compile with: /c
__declspec(dllexport) static void func() {}   // C2201 func() is static
__declspec(dllexport) void func2() {}   // OK
```

## <a name="see-also"></a>Voir aussi

[Types de liaison](../../cpp/types-of-linkage.md)
