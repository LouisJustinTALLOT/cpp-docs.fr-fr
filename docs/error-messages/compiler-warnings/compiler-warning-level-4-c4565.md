---
title: Compilateur avertissement (niveau 4) C4565 | Microsoft Docs
ms.custom: ''
ms.date: 08/27/2018
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4565
dev_langs:
- C++
helpviewer_keywords:
- C4565
ms.assetid: a71f1341-a4a1-4060-ad1e-9322531883ed
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c25f2f1fc16c6d45a7d1eddec8d3efe62db142f2
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/29/2018
ms.locfileid: "43211260"
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