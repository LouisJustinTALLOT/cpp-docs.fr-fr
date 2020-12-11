---
description: 'En savoir plus sur : erreur du compilateur C2646'
title: Erreur du compilateur C2646
ms.date: 11/04/2016
f1_keywords:
- C2646
helpviewer_keywords:
- C2646
ms.assetid: 92ff1f02-5eaf-40a5-8b7a-a682f149e967
ms.openlocfilehash: 7aa378a0a2dbaeae78a63f97e83a84d94d861c72
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97160816"
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
