---
description: 'En savoir plus sur : avertissement du compilateur (niveau 2) C4156'
title: Avertissement du compilateur (niveau 2) C4156
ms.date: 11/04/2016
f1_keywords:
- C4156
helpviewer_keywords:
- C4156
ms.assetid: 9adf3acb-c0fe-42a8-a4db-5822b1493f77
ms.openlocfilehash: 243652ec191e315d7ad06a571c78a1dedce0f032
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97326489"
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
