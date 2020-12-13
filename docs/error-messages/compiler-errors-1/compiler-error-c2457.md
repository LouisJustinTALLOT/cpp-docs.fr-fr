---
description: 'En savoir plus sur : erreur du compilateur C2457'
title: Erreur du compilateur C2457
ms.date: 11/04/2016
f1_keywords:
- C2457
helpviewer_keywords:
- C2457
ms.assetid: 347e169d-23ad-434f-8836-5b09b53980ff
ms.openlocfilehash: 1fea5192b97e280a38f674a67b0bf739041ffe97
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97332365"
---
# <a name="compiler-error-c2457"></a>Erreur du compilateur C2457

> '*macro*' : une macro prédéfinie ne peut pas apparaître en dehors d’un corps de fonction

Vous avez tenté d’utiliser une macro prédéfinie, telle que [&#95;&#95;&#95;&#95;de fonction ](../../preprocessor/predefined-macros.md), dans un espace global.

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
