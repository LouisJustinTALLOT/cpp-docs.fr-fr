---
title: Avertissement du compilateur (niveau 4) C4559
ms.date: 08/27/2018
f1_keywords:
- C4559
helpviewer_keywords:
- C4559
ms.assetid: ed542f60-454d-45cb-85da-987ede61b1ab
ms.openlocfilehash: afb4fb493c7c3e34ca691720a30d74517b0ab5b7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62220871"
---
# <a name="compiler-warning-level-4-c4559"></a>Avertissement du compilateur (niveau 4) C4559

> «*fonction*' : redéfinition ; la __declspec gains (fonction) (*modificateur*)

## <a name="remarks"></a>Notes

Une fonction a été redéfinie ou redéclarée et la deuxième définition ou déclaration un **__declspec** modificateur (*modificateur*). Cet avertissement possède un caractère informatif. Pour résoudre cet avertissement, supprimez une des définitions.

## <a name="example"></a>Exemple

L’exemple suivant génère l’erreur C4559 :

```cpp
// C4559.cpp
// compile with: /W4 /LD
void f();
__declspec(noalias) void f();   // C4559
```