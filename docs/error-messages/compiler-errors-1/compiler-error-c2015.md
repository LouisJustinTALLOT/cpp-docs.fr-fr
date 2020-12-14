---
description: 'En savoir plus sur : erreur du compilateur C2015'
title: Erreur du compilateur C2015
ms.date: 11/04/2016
f1_keywords:
- C2015
helpviewer_keywords:
- C2015
ms.assetid: 8f40af0a-3a5a-4d6a-8ed7-125966e6bfed
ms.openlocfilehash: 0c27dbf8f7383ebd6424e9482fd1ce8cc0839a39
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97220953"
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
