---
title: Compilateur avertissement (niveau 2) C4156
ms.date: 11/04/2016
f1_keywords:
- C4156
helpviewer_keywords:
- C4156
ms.assetid: 9adf3acb-c0fe-42a8-a4db-5822b1493f77
ms.openlocfilehash: 7d9a4ed09f026267e2c0f37fbbe4550ecd668dfc
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62350463"
---
# <a name="compiler-warning-level-2-c4156"></a>Compilateur avertissement (niveau 2) C4156

suppression d’une expression de tableau sans utiliser la forme 'delete' ; substituée par la forme tableau

La forme non tableau **supprimer** ne peut pas supprimer un tableau. Le compilateur a traduit **supprimer** à la forme de tableau.

Cet avertissement se produit uniquement dans les extensions Microsoft (/Ze).

## <a name="example"></a>Exemple

```
// C4156.cpp
// compile with: /W2
int main()
{
   int (*array)[ 10 ] = new int[ 5 ][ 10 ];
   delete array; // C4156, changed by compiler to "delete [] array;"
}
```