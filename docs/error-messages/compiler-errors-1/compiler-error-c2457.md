---
title: Erreur du compilateur C2457
ms.date: 11/04/2016
f1_keywords:
- C2457
helpviewer_keywords:
- C2457
ms.assetid: 347e169d-23ad-434f-8836-5b09b53980ff
ms.openlocfilehash: 40e666b1f2b566ca6309ee7759452647f8101a38
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80205242"
---
# <a name="compiler-error-c2457"></a>Erreur du compilateur C2457

> '*macro*' : une macro prédéfinie ne peut pas apparaître en dehors d’un corps de fonction

Vous avez tenté d’utiliser une macro prédéfinie, telle [ &#95; &#95;que&#95;Function](../../preprocessor/predefined-macros.md), dans un espace global.

## <a name="example"></a>Exemple

L’exemple suivant génère l’erreur C2457 et affiche également l’utilisation correcte :

```cpp
// C2457.cpp
#include <stdio.h>

__FUNCTION__;   // C2457, cannot be global

int main()
{
    printf_s("\n%s", __FUNCTION__);   // OK
}
```
