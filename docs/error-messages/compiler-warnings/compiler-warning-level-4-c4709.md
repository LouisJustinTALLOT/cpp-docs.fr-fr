---
title: Compilateur avertissement (niveau 4) C4709 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4709
dev_langs:
- C++
helpviewer_keywords:
- C4709
ms.assetid: 8abfdd45-8c70-4c27-b0fb-ca0c3f0fccf9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: df12a377c3d365eaf274e58f9d573753aa1f0a57
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46078983"
---
# <a name="compiler-warning-level-4-c4709"></a>Avertissement du compilateur (niveau 4) C4709

opérateur virgule au sein de l’expression d’index de tableau

En cas d’une virgule dans une expression d’index de tableau, le compilateur utilise la valeur après la dernière virgule.

## <a name="example"></a>Exemple

L’exemple suivant génère l’erreur C4709 :

```
// C4709.cpp
// compile with: /W4
#include <stdio.h>

int main()
{
    int arr[2][2];
    arr[0][0] = 10;
    arr[0][1] = 11;

    // Prints 10, not 11
    printf_s("\n%d",arr[0][1,0]);   // C4709
}
```