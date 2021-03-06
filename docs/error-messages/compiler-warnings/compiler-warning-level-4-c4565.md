---
description: 'En savoir plus sur : avertissement du compilateur (niveau 4) C4565'
title: Avertissement du compilateur (niveau 4) C4565
ms.date: 08/27/2018
f1_keywords:
- C4565
helpviewer_keywords:
- C4565
ms.assetid: a71f1341-a4a1-4060-ad1e-9322531883ed
ms.openlocfilehash: bdcf36234ef5a7d8f371d8d25d31b9cb3a36590d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97255143"
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
