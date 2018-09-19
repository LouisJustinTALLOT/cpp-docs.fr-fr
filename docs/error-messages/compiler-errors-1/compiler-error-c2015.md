---
title: Erreur du compilateur C2015 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2015
dev_langs:
- C++
helpviewer_keywords:
- C2015
ms.assetid: 8f40af0a-3a5a-4d6a-8ed7-125966e6bfed
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5fb9c3ba86224906f749088b96e5daae364d99e2
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46076045"
---
# <a name="compiler-error-c2015"></a>Erreur du compilateur C2015

trop de caractères dans la constante

Une constante caractère contient plus de deux caractères. La limite est un caractère pour les constantes de caractère standard et deux caractères pour les constantes de caractère de long.

Une séquence d’échappement, tels que \t, est convertie en un seul caractère.

## <a name="example"></a>Exemple

L’exemple suivant génère l’erreur C2015 :

```
// C2015.cpp
// compile with: /c

char test1 = 'error';   // C2015
char test2 = 'e';   // OK
```

## <a name="example"></a>Exemple

C2015 peut également se produire lorsque vous utilisez une extension Microsoft, constantes caractère convertis en entiers.  L’exemple suivant génère l’erreur C2015 :

```
// C2015b.cpp
#include <stdio.h>

int main()
{
    int a = 'abcde';   // C2015

    int b = 'a';   // 'a' = ascii 0x61
    printf_s("%x\n", b);
}
```