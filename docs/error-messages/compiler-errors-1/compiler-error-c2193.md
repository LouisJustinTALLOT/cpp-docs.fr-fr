---
title: Erreur du compilateur C2193
ms.date: 11/04/2016
f1_keywords:
- C2193
helpviewer_keywords:
- C2193
ms.assetid: 9813e853-d581-4f51-bb75-4e242298a844
ms.openlocfilehash: 25ebfc73fb46eca3a27875075af2d4ed46ed2fef
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74758552"
---
# <a name="compiler-error-c2193"></a>Erreur du compilateur C2193

'identificateur' : déjà dans un segment

Une fonction a été placée dans deux segments différents à l’aide des pragmas `alloc_text` et `code_seg`.

L’exemple suivant génère l’C2193 :

```cpp
// C2193.cpp
// compile with: /c
extern "C" void MYFUNCTION();
#pragma alloc_text(MYCODE, MYFUNCTION)
#pragma code_seg("MYCODE2")
extern "C" void MYFUNCTION() {}   // C2193
extern "C" void MYFUNCTION2() {}
```
