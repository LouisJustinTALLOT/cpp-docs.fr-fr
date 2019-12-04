---
title: Erreur du compilateur C2015
ms.date: 11/04/2016
f1_keywords:
- C2015
helpviewer_keywords:
- C2015
ms.assetid: 8f40af0a-3a5a-4d6a-8ed7-125966e6bfed
ms.openlocfilehash: 83b78336d74037b9f9f52da8327479f506db1ffc
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74751066"
---
# <a name="compiler-error-c2015"></a>Erreur du compilateur C2015

trop de caractères dans la constante

Une constante caractère contient plus de deux caractères. La limite est un caractère pour les constantes caractère standard et deux caractères pour les constantes de caractères longs.

Une séquence d’échappement, telle que \t, est convertie en un seul caractère.

## <a name="example"></a>Exemple

L’exemple suivant génère l’C2015 :

```cpp
// C2015.cpp
// compile with: /c

char test1 = 'error';   // C2015
char test2 = 'e';   // OK
```

## <a name="example"></a>Exemple

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
