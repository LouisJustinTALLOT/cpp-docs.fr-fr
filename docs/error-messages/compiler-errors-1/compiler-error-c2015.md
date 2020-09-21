---
title: Erreur du compilateur C2015
ms.date: 11/04/2016
f1_keywords:
- C2015
helpviewer_keywords:
- C2015
ms.assetid: 8f40af0a-3a5a-4d6a-8ed7-125966e6bfed
ms.openlocfilehash: 5453009e1c2bd091ed3507f3c43bd7fcecd33abc
ms.sourcegitcommit: 72161bcd21d1ad9cc3f12261aa84a5b026884afa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2020
ms.locfileid: "90743098"
---
# <a name="compiler-error-c2015"></a>Erreur du compilateur C2015

trop de caractères dans la constante

Une constante caractère contient plus de deux caractères. La limite est un caractère pour les constantes caractère standard et deux caractères pour les constantes de caractères longs.

Une séquence d’échappement, telle que \t, est convertie en un seul caractère.

## <a name="examples"></a>Exemples

L’exemple suivant génère l’C2015 :

```cpp
// C2015.cpp
// compile with: /c

char test1 = 'error';   // C2015
char test2 = 'e';   // OK
```

C2015 peut également se produire lors de l’utilisation d’une extension Microsoft, de constantes caractère converties en entiers.  L’exemple suivant génère l’C2015 :

```cpp
// C2015b.cpp
#include <stdio.h>

int main()
{
    int a = 'abcde';   // C2015

    int b = 'a';   // 'a' = ascii 0x61
    printf_s("%x\n", b);
}
```
