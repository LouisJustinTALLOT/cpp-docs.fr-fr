---
description: 'En savoir plus sur : Comment : épingler des pointeurs et des tableaux'
title: 'Comment : épingler des pointeurs et des tableaux'
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- pointers, pinning
- arrays [C++], pinning
ms.assetid: ee783260-e676-46b8-a38e-11a06f1d57b0
ms.openlocfilehash: ab0e09e94c45cc31862ef8d0b6c0771bfeae115d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97119133"
---
# <a name="how-to-pin-pointers-and-arrays"></a>Comment : épingler des pointeurs et des tableaux

L’épinglage d’un sous-objet défini dans un objet managé a pour effet d’épingler l’objet entier.  Par exemple, si un élément d’un tableau est épinglé, la totalité du tableau est également épinglée. Il n’existe aucune extension pour le langage pour déclarer un tableau épinglé. Pour épingler un tableau, déclarez un pointeur épingle à son type d’élément, et épinglez un de ses éléments.

## <a name="example"></a>Exemple

### <a name="code"></a>Code

```cpp
// pin_ptr_array.cpp
// compile with: /clr
#include <stdio.h>
using namespace System;

int main() {
   array<Byte>^ arr = gcnew array<Byte>(4);
   arr[0] = 'C';
   arr[1] = '+';
   arr[2] = '+';
   arr[3] = '\0';
   pin_ptr<Byte> p = &arr[1];   // entire array is now pinned
   unsigned char * cp = p;

   printf_s("%s\n", cp); // bytes pointed at by cp
                         // will not move during call
}
```

```Output
++
```

## <a name="see-also"></a>Voir aussi

[pin_ptr (C++/CLI)](pin-ptr-cpp-cli.md)
