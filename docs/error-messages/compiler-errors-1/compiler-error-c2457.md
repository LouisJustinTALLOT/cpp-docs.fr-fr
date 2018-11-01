---
title: Erreur du compilateur C2457
ms.date: 11/04/2016
f1_keywords:
- C2457
helpviewer_keywords:
- C2457
ms.assetid: 347e169d-23ad-434f-8836-5b09b53980ff
ms.openlocfilehash: a08ac9f9cfbc332b90ad16c663349ee227427278
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50446632"
---
# <a name="compiler-error-c2457"></a>Erreur du compilateur C2457

> «*macro*' : la macro prédéfinie ne peut pas apparaître en dehors d’un corps de fonction

Vous avez tenté d’utiliser une macro prédéfinie, telle que [ &#95; &#95;fonction&#95;&#95;](../../preprocessor/predefined-macros.md), dans un espace global.

## <a name="example"></a>Exemple

L’exemple suivant génère l’erreur C2457 et illustre également l’utilisation correcte :

```cpp
// C2457.cpp
#include <stdio.h>

__FUNCTION__;   // C2457, cannot be global

int main()
{
    printf_s("\n%s", __FUNCTION__);   // OK
}
```