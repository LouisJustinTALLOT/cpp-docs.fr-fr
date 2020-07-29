---
title: Erreur du compilateur C2646
ms.date: 11/04/2016
f1_keywords:
- C2646
helpviewer_keywords:
- C2646
ms.assetid: 92ff1f02-5eaf-40a5-8b7a-a682f149e967
ms.openlocfilehash: a05c98564c4e45dc380690c1b8c9bace5fc14cf4
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87216152"
---
# <a name="compiler-error-c2646"></a>Erreur du compilateur C2646

une struct ou union anonyme au niveau de la portée globale ou de la portée de l'espace de noms doit être déclarée statique

Une struct ou une Union anonyme a une portée globale ou d’espace de noms, mais n’est pas déclarée **`static`** .

L'exemple suivant génère l'erreur C2646 et montre comment la corriger :

```cpp
// C2646.cpp
// compile with: /c
union { int i; };   // C2646 not static

// OK
static union { int j; };
union U { int i; };
```
