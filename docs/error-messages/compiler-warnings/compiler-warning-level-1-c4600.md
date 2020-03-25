---
title: Avertissement du compilateur (niveau 1) C4600
ms.date: 11/04/2016
f1_keywords:
- C4600
helpviewer_keywords:
- C4600
ms.assetid: f023a2a1-7fc4-463f-a434-dc93fcd3f4e9
ms.openlocfilehash: 15ad64ad29f6f01253a2329fb04897c299cedff9
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80186073"
---
# <a name="compiler-warning-level-1-c4600"></a>Avertissement du compilateur (niveau 1) C4600

\#pragma’macro Name' : une chaîne non vide valide était attendue

Vous ne pouvez pas spécifier une chaîne vide quand vous effectuez un push ou un pop sur un nom de macro avec l' [pop_macro](../../preprocessor/pop-macro.md) ou [push_macro](../../preprocessor/push-macro.md).

L’exemple suivant génère l’C4600 :

```cpp
// C4600.cpp
// compile with: /W1
int main()
{
   #pragma push_macro("")   // C4600 passing an empty string
}
```
