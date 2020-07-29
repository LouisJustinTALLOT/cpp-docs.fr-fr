---
title: Avertissement du compilateur (niveau 4) C4565
ms.date: 08/27/2018
f1_keywords:
- C4565
helpviewer_keywords:
- C4565
ms.assetid: a71f1341-a4a1-4060-ad1e-9322531883ed
ms.openlocfilehash: ba2e1e7eb490a28626937a3911608ff9686d6f38
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87195978"
---
# <a name="compiler-warning-level-4-c4565"></a>Avertissement du compilateur (niveau 4) C4565

> '*fonction*' : redéfinition ; le symbole a été précédemment déclaré avec __declspec (*modificateur*)

## <a name="remarks"></a>Notes

Un symbole a été redéfini ou redéclaré, et la deuxième définition ou déclaration, à la différence de la première définition ou déclaration, n’avait pas de **`__declspec`** modificateur (*modificateur*). Cet avertissement possède un caractère informatif. Pour résoudre cet avertissement, supprimez l’une des définitions.

## <a name="example"></a>Exemple

L’exemple suivant génère l’C4565 :

```cpp
// C4565.cpp
// compile with: /W4 /LD
__declspec(noalias) void f();
void f();   // C4565
```
