---
title: Erreur du compilateur C2646
ms.date: 11/04/2016
f1_keywords:
- C2646
helpviewer_keywords:
- C2646
ms.assetid: 92ff1f02-5eaf-40a5-8b7a-a682f149e967
ms.openlocfilehash: a5c4dbc967c304fc6b13eb00e2c7093380ec8be9
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74758214"
---
# <a name="compiler-error-c2646"></a>Erreur du compilateur C2646

une struct ou union anonyme au niveau de la portée globale ou de la portée de l'espace de noms doit être déclarée statique

Un struct ou une union anonyme possède une portée globale ou une portée d'espace de noms mais n'est pas déclaré(e) `static`.

L'exemple suivant génère l'erreur C2646 et montre comment la corriger :

```cpp
// C2646.cpp
// compile with: /c
union { int i; };   // C2646 not static

// OK
static union { int j; };
union U { int i; };
```
