---
title: Avertissement du compilateur (niveau 1) C4602
ms.date: 11/04/2016
f1_keywords:
- C4602
helpviewer_keywords:
- C4602
ms.assetid: c1f0300f-e2a2-4c9e-a7c3-4c7318d10509
ms.openlocfilehash: f93af5b37c87e30891dd09009b53e73c7d384b1c
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80162125"
---
# <a name="compiler-warning-level-1-c4602"></a>Avertissement du compilateur (niveau 1) C4602

\#pragma pop_macro : 'Nom macro’aucun push_macro de #pragma précédent pour cet identificateur

Si vous utilisez [pop_macro](../../preprocessor/pop-macro.md) pour une macro particulière, vous devez au préalable passer le nom de cette macro à [push_macro](../../preprocessor/push-macro.md). L’exemple suivant génère l’avertissement C4602 :

```cpp
// C4602.cpp
// compile with: /W1
int main()
{
   #pragma pop_macro("x")   // C4602 x is not on the stack
}
```
