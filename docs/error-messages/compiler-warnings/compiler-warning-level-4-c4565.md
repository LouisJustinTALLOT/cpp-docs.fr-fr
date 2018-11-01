---
title: Avertissement du compilateur (niveau 4) C4565
ms.date: 08/27/2018
f1_keywords:
- C4565
helpviewer_keywords:
- C4565
ms.assetid: a71f1341-a4a1-4060-ad1e-9322531883ed
ms.openlocfilehash: b655dcfb456d32e45833e89e5a48926ad70d1d9e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50588680"
---
# <a name="compiler-warning-level-4-c4565"></a>Avertissement du compilateur (niveau 4) C4565

> «*fonction*' : redéfinition ; le symbole a été précédemment déclaré avec __declspec (*modificateur*)

## <a name="remarks"></a>Notes

Un symbole a été redéfini ou redéclaré et la deuxième définition ou déclaration, contrairement à la première, n’a pas un `__declspec` modificateur (*modificateur*). Cet avertissement possède un caractère informatif. Pour résoudre cet avertissement, supprimez une des définitions.

## <a name="example"></a>Exemple

L’exemple suivant génère l’erreur C4565 :

```cpp
// C4565.cpp
// compile with: /W4 /LD
__declspec(noalias) void f();
void f();   // C4565
```