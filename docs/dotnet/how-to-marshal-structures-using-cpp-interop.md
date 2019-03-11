---
title: 'Procédure : Marshaler des Structures à l’aide de C++ Interop'
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- C++ Interop, structures
- structures [C++], marshaling
- data marshaling [C++], structures
- interop [C++], structures
- marshaling [C++], structures
ms.assetid: c2080200-f983-4d6e-a557-cd870f060a54
ms.openlocfilehash: 93aeabc3fe984bee8a9281281320d61dccd182bf
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/11/2019
ms.locfileid: "57739384"
---
# <a name="how-to-marshal-structures-using-c-interop"></a>Procédure : Marshaler des Structures à l’aide de C++ Interop

Cette rubrique illustre une facette de l’interopérabilité de Visual C++. Pour plus d’informations, consultez [à l’aide du interopérabilité C++ (PInvoke implicite)](../dotnet/using-cpp-interop-implicit-pinvoke.md).

Exemple de code suit le [managed, unmanaged](../preprocessor/managed-unmanaged.md) directives #pragma pour implémenter des fonctions managées et dans le même fichier, mais ces fonctions interagissent de la même manière, si elles sont définies dans des fichiers distincts. Fichiers contenant uniquement des fonctions non managées ne doivent pas être compilé avec [/clr (Compilation pour le Common Language Runtime)](../build/reference/clr-common-language-runtime-compilation.md).

## <a name="example"></a>Exemple

L’exemple suivant illustre le passage d’une structure d’une fonction managée à une fonction non managée, à la fois par valeur et par référence. Étant donné que la structure de cet exemple contient les types de données intrinsèques simples uniquement (consultez [Types blittables et Non blittables](/dotnet/framework/interop/blittable-and-non-blittable-types)), aucun marshaling spécial n’est requis. Pour marshaler des structures non blittables, telles que celles qui contiennent des pointeurs, consultez [Comment : Marshaler des pointeurs à l’aide de C++ Interop incorporés](../dotnet/how-to-marshal-embedded-pointers-using-cpp-interop.md).

```
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

## <a name="example"></a>Exemple

L’exemple suivant illustre le passage d’une structure à partir d’une fonction non managée à une fonction managée, à la fois par valeur et par référence. Étant donné que la structure de cet exemple contient les types de données intrinsèques simples uniquement (consultez [Types blittables et Non blittables](/dotnet/framework/interop/blittable-and-non-blittable-types)), aucun marshaling spécial n’est requis. Pour marshaler des structures non blittables, telles que celles qui contiennent des pointeurs, consultez [Comment : Marshaler des pointeurs à l’aide de C++ Interop incorporés](../dotnet/how-to-marshal-embedded-pointers-using-cpp-interop.md).

```
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
