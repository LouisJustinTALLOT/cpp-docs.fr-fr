---
title: Erreur du compilateur C2457 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2457
dev_langs:
- C++
helpviewer_keywords:
- C2457
ms.assetid: 347e169d-23ad-434f-8836-5b09b53980ff
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 61cdb4f4b679bab858717a6fb96838f389822a6b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33224921"
---
# <a name="compiler-error-c2457"></a>Erreur du compilateur C2457

> '*macro*' : une macro prédéfinie ne peut pas apparaître en dehors d’un corps de fonction

Vous avez tenté d’utiliser une macro prédéfinie, tel que [ &#95; &#95;fonction&#95;&#95;](../../preprocessor/predefined-macros.md), dans un espace global.

## <a name="example"></a>Exemple

L’exemple suivant génère l’erreur C2457 et montre également l’utilisation correcte :

```cpp
// C2457.cpp
#include <stdio.h>

__FUNCTION__;   // C2457, cannot be global

int main()
{
    printf_s("\n%s", __FUNCTION__);   // OK
}
```