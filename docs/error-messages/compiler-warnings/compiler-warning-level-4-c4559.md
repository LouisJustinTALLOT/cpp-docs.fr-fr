---
title: Avertissement du compilateur (niveau 4) C4559
ms.date: 08/27/2018
f1_keywords:
- C4559
helpviewer_keywords:
- C4559
ms.assetid: ed542f60-454d-45cb-85da-987ede61b1ab
ms.openlocfilehash: 66e782c2fbb9c39c6a189de496cd0dcb4f1f4991
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87218076"
---
# <a name="compiler-warning-level-4-c4559"></a>Avertissement du compilateur (niveau 4) C4559

> '*fonction*' : redéfinition ; la fonction gagne __declspec (*modificateur*)

## <a name="remarks"></a>Notes

Une fonction a été redéfinie ou redéclarée et la deuxième définition ou déclaration a ajouté un **`__declspec`** modificateur (*modificateur*). Cet avertissement possède un caractère informatif. Pour résoudre cet avertissement, supprimez l’une des définitions.

## <a name="example"></a>Exemple

L’exemple suivant génère l’C4559 :

```cpp
// C4559.cpp
// compile with: /W4 /LD
void f();
__declspec(noalias) void f();   // C4559
```
