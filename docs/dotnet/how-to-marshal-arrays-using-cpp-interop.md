---
description: 'En savoir plus sur : Comment : marshaler des tableaux à l’aide de l’interopérabilité C++'
title: "Comment : marshaler des tableaux à l'aide de l'interopérabilité C++"
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- arrays [C++], marshaling
- marshaling [C++], arrays
- interop [C++], arrays
- C++ Interop, arrays
- data marshaling [C++], arrays
ms.assetid: c2b37ab1-8acf-4855-ad3c-7d2864826b14
ms.openlocfilehash: 5c91b9f24a801f7bf1bd1ec3132503535f0334d0
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97258237"
---
# <a name="how-to-marshal-arrays-using-c-interop"></a>Comment : marshaler des tableaux à l'aide de l'interopérabilité C++

Cette rubrique présente une facette de Visual C++ interopérabilité. Pour plus d’informations, consultez [utilisation de l’interopérabilité C++ (PInvoke implicite)](../dotnet/using-cpp-interop-implicit-pinvoke.md).

Les exemples de code suivants utilisent les directives de #pragma [managées et non managées](../preprocessor/managed-unmanaged.md) pour implémenter des fonctions managées et non managées dans le même fichier, mais ces fonctions interagissent de la même manière si elles sont définies dans des fichiers distincts. Les fichiers contenant uniquement des fonctions non managées n’ont pas besoin d’être compilés avec [/clr (compilation pour le Common Language Runtime)](../build/reference/clr-common-language-runtime-compilation.md).

## <a name="example-pass-managed-array-to-unmanaged-function"></a>Exemple : passer un tableau managé à une fonction non managée

L’exemple suivant montre comment passer un tableau managé à une fonction non managée. La fonction managée utilise [pin_ptr (C++/CLI)](../extensions/pin-ptr-cpp-cli.md) pour supprimer garbage collection pour le tableau avant d’appeler la fonction non managée. En fournissant la fonction non managée avec un pointeur épinglé dans le tas GC, la surcharge liée à la création d’une copie du tableau peut être évitée. Pour montrer que la fonction non managée accède à la mémoire du tas GC, elle modifie le contenu du tableau et les modifications sont reflétées lorsque la fonction managée reprend le contrôle.

```cpp
// PassArray1.cpp
// compile with: /clr
#ifndef _CRT_RAND_S
#define _CRT_RAND_S
#endif

#include <iostream>
#include <stdlib.h>
using namespace std;

using namespace System;

#pragma unmanaged

void TakesAnArray(int* a, int c) {
   cout << "(unmanaged) array received:\n";
   for (int i=0; i<c; i++)
      cout << "a[" << i << "] = " << a[i] << "\n";

   unsigned int number;
   errno_t err;

   cout << "(unmanaged) modifying array contents...\n";
   for (int i=0; i<c; i++) {
      err = rand_s( &number );
      if ( err == 0 )
         a[i] = number % 100;
   }
}

#pragma managed

int main() {
   array<int>^ nums = gcnew array<int>(5);

   nums[0] = 0;
   nums[1] = 1;
   nums[2] = 2;
   nums[3] = 3;
   nums[4] = 4;

   Console::WriteLine("(managed) array created:");
   for (int i=0; i<5; i++)
      Console::WriteLine("a[{0}] = {1}", i, nums[i]);

   pin_ptr<int> pp = &nums[0];
   TakesAnArray(pp, 5);

   Console::WriteLine("(managed) contents:");
   for (int i=0; i<5; i++)
      Console::WriteLine("a[{0}] = {1}", i, nums[i]);
}
```

## <a name="example-pass-unmanaged-array-to-managed-function"></a>Exemple : passer un tableau non managé à une fonction managée

L’exemple suivant illustre le passage d’un tableau non managé à une fonction managée. La fonction managée accède directement à la mémoire du tableau (par opposition à la création d’un tableau managé et à la copie du contenu du tableau), ce qui permet aux modifications apportées par la fonction managée d’être reflétées dans la fonction non managée lorsqu’elle acquiert à nouveau le contrôle.

```cpp
// PassArray2.cpp
// compile with: /clr
#include <iostream>
using namespace std;

using namespace System;

#pragma managed

void ManagedTakesAnArray(int* a, int c) {
   Console::WriteLine("(managed) array received:");
   for (int i=0; i<c; i++)
      Console::WriteLine("a[{0}] = {1}", i, a[i]);

   cout << "(managed) modifying array contents...\n";
   Random^ r = gcnew Random(DateTime::Now.Second);
   for (int i=0; i<c; i++)
      a[i] = r->Next(100);
}

#pragma unmanaged

void NativeFunc() {
   int nums[5] = { 0, 1, 2, 3, 4 };

   printf_s("(unmanaged) array created:\n");
   for (int i=0; i<5; i++)
      printf_s("a[%d] = %d\n", i, nums[i]);

   ManagedTakesAnArray(nums, 5);

   printf_s("(ummanaged) contents:\n");
   for (int i=0; i<5; i++)
      printf_s("a[%d] = %d\n", i, nums[i]);
}

#pragma managed

int main() {
   NativeFunc();
}
```

## <a name="see-also"></a>Voir aussi

[Utilisation de l’interopérabilité C++ (PInvoke implicite)](../dotnet/using-cpp-interop-implicit-pinvoke.md)
