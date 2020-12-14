---
description: 'En savoir plus sur : Comment : marshaler des structures à l’aide de l’interopérabilité C++'
title: 'Comment : marshaler des structures à l’aide de l’interopérabilité C++'
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- C++ Interop, structures
- structures [C++], marshaling
- data marshaling [C++], structures
- interop [C++], structures
- marshaling [C++], structures
ms.assetid: c2080200-f983-4d6e-a557-cd870f060a54
ms.openlocfilehash: 96622c48034ddf3126e68867ad5a4bd8ab25fa43
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97302541"
---
# <a name="how-to-marshal-structures-using-c-interop"></a>Comment : marshaler des structures à l’aide de l’interopérabilité C++

Cette rubrique présente une facette de Visual C++ interopérabilité. Pour plus d’informations, consultez [utilisation de l’interopérabilité C++ (PInvoke implicite)](../dotnet/using-cpp-interop-implicit-pinvoke.md).

Les exemples de code suivants utilisent les directives de #pragma [managées et non managées](../preprocessor/managed-unmanaged.md) pour implémenter des fonctions managées et non managées dans le même fichier, mais ces fonctions interagissent de la même manière si elles sont définies dans des fichiers distincts. Les fichiers contenant uniquement des fonctions non managées n’ont pas besoin d’être compilés avec [/clr (compilation pour le Common Language Runtime)](../build/reference/clr-common-language-runtime-compilation.md).

## <a name="example-pass-structure-from-managed-to-unmanaged-function"></a>Exemple : passer la structure d’une fonction managée à une fonction non managée

L’exemple suivant illustre le passage d’une structure d’une fonction managée à une fonction non managée, à la fois par valeur et par référence. Étant donné que la structure de cet exemple contient uniquement des types de données intrinsèques simples (voir les [types blittables et non blittables](/dotnet/framework/interop/blittable-and-non-blittable-types)), aucun marshaling spécial n’est requis. Pour marshaler des structures non blittables, telles que celles qui contiennent des pointeurs, consultez Guide pratique [pour marshaler des pointeurs incorporés à l’aide de l’interopérabilité C++](../dotnet/how-to-marshal-embedded-pointers-using-cpp-interop.md).

```cpp
// PassStruct1.cpp
// compile with: /clr

#include <stdio.h>
#include <math.h>

using namespace System;
using namespace System::Runtime::InteropServices;

#pragma unmanaged

struct Location {
   int x;
   int y;
};

double GetDistance(Location loc1, Location loc2) {
   printf_s("[unmanaged] loc1(%d,%d)", loc1.x, loc1.y);
   printf_s(" loc2(%d,%d)\n", loc2.x, loc2.y);

   double h = loc1.x - loc2.x;
   double v = loc1.y = loc2.y;
   double dist = sqrt( pow(h,2) + pow(v,2) );

   return dist;
}

void InitLocation(Location* lp) {
   printf_s("[unmanaged] Initializing location...\n");
   lp->x = 50;
   lp->y = 50;
}

#pragma managed

int main() {
   Location loc1;
   loc1.x = 0;
   loc1.y = 0;

   Location loc2;
   loc2.x = 100;
   loc2.y = 100;

   double dist = GetDistance(loc1, loc2);
   Console::WriteLine("[managed] distance = {0}", dist);

   Location loc3;
   InitLocation(&loc3);
   Console::WriteLine("[managed] x={0} y={1}", loc3.x, loc3.y);
}
```

## <a name="example-pass-structure-from-unmanaged-to-managed-function"></a>Exemple : passer la structure d’une fonction non managée à une fonction managée

L’exemple suivant illustre le passage d’une structure d’une fonction non managée à une fonction managée, à la fois par valeur et par référence. Étant donné que la structure de cet exemple contient uniquement des types de données intrinsèques simples (voir les [types blittables et non blittables](/dotnet/framework/interop/blittable-and-non-blittable-types)), aucun marshaling spécial n’est requis. Pour marshaler des structures non blittables, telles que celles qui contiennent des pointeurs, consultez Guide pratique [pour marshaler des pointeurs incorporés à l’aide de l’interopérabilité C++](../dotnet/how-to-marshal-embedded-pointers-using-cpp-interop.md).

```cpp
// PassStruct2.cpp
// compile with: /clr
#include <stdio.h>
#include <math.h>
using namespace System;

// native structure definition
struct Location {
   int x;
   int y;
};

#pragma managed

double GetDistance(Location loc1, Location loc2) {
   Console::Write("[managed] got loc1({0},{1})", loc1.x, loc1.y);
   Console::WriteLine(" loc2({0},{1})", loc2.x, loc2.y);

   double h = loc1.x - loc2.x;
   double v = loc1.y = loc2.y;
   double dist = sqrt( pow(h,2) + pow(v,2) );

   return dist;
}

void InitLocation(Location* lp) {
   Console::WriteLine("[managed] Initializing location...");
   lp->x = 50;
   lp->y = 50;
}

#pragma unmanaged

int UnmanagedFunc() {
   Location loc1;
   loc1.x = 0;
   loc1.y = 0;

   Location loc2;
   loc2.x = 100;
   loc2.y = 100;

   printf_s("(unmanaged) loc1=(%d,%d)", loc1.x, loc1.y);
   printf_s(" loc2=(%d,%d)\n", loc2.x, loc2.y);

   double dist = GetDistance(loc1, loc2);
   printf_s("[unmanaged] distance = %f\n", dist);

   Location loc3;
   InitLocation(&loc3);
   printf_s("[unmanaged] got x=%d y=%d\n", loc3.x, loc3.y);

    return 0;
}

#pragma managed

int main() {
   UnmanagedFunc();
}
```

## <a name="see-also"></a>Voir aussi

[Utilisation de l’interopérabilité C++ (PInvoke implicite)](../dotnet/using-cpp-interop-implicit-pinvoke.md)
