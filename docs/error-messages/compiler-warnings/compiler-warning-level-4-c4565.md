---
title: Avertissement du compilateur (niveau 4) C4565
ms.date: 08/27/2018
f1_keywords:
- C4565
helpviewer_keywords:
- C4565
ms.assetid: a71f1341-a4a1-4060-ad1e-9322531883ed
ms.openlocfilehash: 5eccb3c29da612a39f7fcdf4ef25dedb898c8d43
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80198326"
---
# <a name="compiler-warning-level-4-c4565"></a>Avertissement du compilateur (niveau 4) C4565

> '*fonction*' : redéfinition ; le symbole a été précédemment déclaré avec __declspec (*modificateur*)

## <a name="remarks"></a>Notes

Un symbole a été redéfini ou redéclaré, et la deuxième définition ou déclaration, à la différence de la première définition ou déclaration, n’avait pas de modificateur de `__declspec` (*modificateur*). Cet avertissement est à caractère informatif. Pour résoudre cet avertissement, supprimez l’une des définitions.

## <a name="example"></a>Exemple

L’exemple suivant génère l’C4565 :

```cpp
// C4565.cpp
// compile with: /W4 /LD
__declspec(noalias) void f();
void f();   // C4565
```
