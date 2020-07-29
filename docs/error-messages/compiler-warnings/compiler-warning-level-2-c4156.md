---
title: Avertissement du compilateur (niveau 2) C4156
ms.date: 11/04/2016
f1_keywords:
- C4156
helpviewer_keywords:
- C4156
ms.assetid: 9adf3acb-c0fe-42a8-a4db-5822b1493f77
ms.openlocfilehash: 279ab5d9de738fb4e2aa6dece4bb16353eca031b
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87206482"
---
# <a name="compiler-warning-level-2-c4156"></a>Avertissement du compilateur (niveau 2) C4156

suppression d’une expression de tableau sans utiliser la forme de tableau de’Delete'; forme de tableau substituée

La forme non-tableau de **`delete`** ne peut pas supprimer un tableau. Le compilateur a traduit **`delete`** la forme de tableau.

Cet avertissement se produit uniquement sous les extensions Microsoft (/Ze).

## <a name="example"></a>Exemple

```cpp
// C4156.cpp
// compile with: /W2
int main()
{
   int (*array)[ 10 ] = new int[ 5 ][ 10 ];
   delete array; // C4156, changed by compiler to "delete [] array;"
}
```
