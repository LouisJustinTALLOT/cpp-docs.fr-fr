---
description: 'En savoir plus sur : Comment : marshaler des pointeurs incorporés à l’aide de l’interopérabilité C++'
title: "Comment : marshaler des pointeurs incorporés à l'aide de l'interopérabilité C++"
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- structures [C++], marshaling embedded pointers
- interop [C++], embedded pointers
- C++ Interop, embedded pointers
- marshaling [C++], embedded pointers
- pointers [C++], marshaling
- data marshaling [C++], embedded pointers
ms.assetid: 05fb8858-97f2-47aa-86b2-2c0ad713bdb2
ms.openlocfilehash: 74ea5cdec755b7845796d1b61339811adb4f0b28
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97302593"
---
# <a name="how-to-marshal-embedded-pointers-using-c-interop"></a>Comment : marshaler des pointeurs incorporés à l'aide de l'interopérabilité C++

Les exemples de code suivants utilisent les directives de #pragma [managées et non managées](../preprocessor/managed-unmanaged.md) pour implémenter des fonctions managées et non managées dans le même fichier, mais ces fonctions interagissent de la même manière si elles sont définies dans des fichiers distincts. Les fichiers contenant uniquement des fonctions non managées n’ont pas besoin d’être compilés avec [/clr (compilation pour le Common Language Runtime)](../build/reference/clr-common-language-runtime-compilation.md).

## <a name="example"></a>Exemple

L’exemple suivant montre comment une fonction non managée qui prend une structure contenant des pointeurs peut être appelée à partir d’une fonction managée. La fonction managée crée une instance de la structure et initialise le pointeur incorporé avec le mot clé New (au lieu du mot clé [ref New, gcnew](../extensions/ref-new-gcnew-cpp-component-extensions.md) ). Étant donné que cette valeur alloue la mémoire sur le tas natif, il n’est pas nécessaire d’épingler le tableau pour supprimer garbage collection. Toutefois, la mémoire doit être supprimée explicitement pour éviter les fuites de mémoire.

```cpp
// marshal_embedded_pointer.cpp
// compile with: /clr
#include <iostream>

using namespace System;
using namespace System::Runtime::InteropServices;

// unmanaged struct
struct ListStruct {
   int count;
   double* item;
};

#pragma unmanaged

void UnmanagedTakesListStruct(ListStruct list) {
   printf_s("[unmanaged] count = %d\n", list.count);
   for (int i=0; i<list.count; i++)
      printf_s("array[%d] = %f\n", i, list.item[i]);
}

#pragma managed

int main() {
   ListStruct list;
   list.count = 10;
   list.item = new double[list.count];

   Console::WriteLine("[managed] count = {0}", list.count);
   Random^ r = gcnew Random(0);
   for (int i=0; i<list.count; i++) {
      list.item[i] = r->NextDouble() * 100.0;
      Console::WriteLine("array[{0}] = {1}", i, list.item[i]);
   }

   UnmanagedTakesListStruct( list );
   delete list.item;
}
```

```Output
[managed] count = 10
array[0] = 72.624326996796
array[1] = 81.7325359590969
array[2] = 76.8022689394663
array[3] = 55.8161191436537
array[4] = 20.6033154021033
array[5] = 55.8884794618415
array[6] = 90.6027066011926
array[7] = 44.2177873310716
array[8] = 97.754975314138
array[9] = 27.370445768987
[unmanaged] count = 10
array[0] = 72.624327
array[1] = 81.732536
array[2] = 76.802269
array[3] = 55.816119
array[4] = 20.603315
array[5] = 55.888479
array[6] = 90.602707
array[7] = 44.217787
array[8] = 97.754975
array[9] = 27.370446
```

## <a name="see-also"></a>Voir aussi

[Utilisation de l’interopérabilité C++ (PInvoke implicite)](../dotnet/using-cpp-interop-implicit-pinvoke.md)
