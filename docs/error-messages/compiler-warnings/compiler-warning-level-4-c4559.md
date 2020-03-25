---
title: Avertissement du compilateur (niveau 4) C4559
ms.date: 08/27/2018
f1_keywords:
- C4559
helpviewer_keywords:
- C4559
ms.assetid: ed542f60-454d-45cb-85da-987ede61b1ab
ms.openlocfilehash: 0788824dd4180476d81d9682f99fb95883b8c4f0
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80198339"
---
# <a name="compiler-warning-level-4-c4559"></a>Avertissement du compilateur (niveau 4) C4559

> '*fonction*' : redéfinition ; la fonction gagne __declspec (*modificateur*)

## <a name="remarks"></a>Notes

Une fonction a été redéfinie ou redéclarée et la deuxième définition ou déclaration a ajouté un modificateur de **__declspec** (*modificateur*). Cet avertissement est à caractère informatif. Pour résoudre cet avertissement, supprimez l’une des définitions.

## <a name="example"></a>Exemple

L’exemple suivant génère l’C4559 :

```cpp
// C4559.cpp
// compile with: /W4 /LD
void f();
__declspec(noalias) void f();   // C4559
```
