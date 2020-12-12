---
description: 'En savoir plus sur : Comment : marshaler des structures à l’aide de PInvoke'
title: "Comment : marshaler des structures à l'aide de PInvoke"
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- data marshaling [C++], structures
- platform invoke [C++], structures
- interop [C++], structures
- marshaling [C++], structures
ms.assetid: 35997e6f-9251-4af3-8c6e-0712d64d6a5d
ms.openlocfilehash: 417701ae1459c265e48171a517b7729d0e92c098
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97302528"
---
# <a name="how-to-marshal-structures-using-pinvoke"></a>Comment : marshaler des structures à l'aide de PInvoke

Ce document explique comment les fonctions natives qui acceptent des structs de style C peuvent être appelées à partir de fonctions managées à l’aide de P/Invoke. Bien que nous vous recommandons d’utiliser les fonctionnalités d’interopérabilité C++ au lieu de P/Invoke, car P/Invoke fournit peu de rapports d’erreurs de compilation, n’est pas de type sécurisé et peut être fastidieux à implémenter, si l’API non managée est empaquetée en tant que DLL et que le code source n’est pas disponible, P/Invoke est la seule option. Dans le cas contraire, consultez les documents suivants :

- [Utilisation de l’interopérabilité C++ (PInvoke implicite)](../dotnet/using-cpp-interop-implicit-pinvoke.md)

- [Comment : marshaler des chaînes à l’aide de PInvoke](../dotnet/how-to-marshal-strings-using-pinvoke.md)

Par défaut, les structures natives et managées sont disposées différemment en mémoire. par conséquent, le passage de structures entre les limites managées/non managées requiert des étapes supplémentaires pour préserver l’intégrité des données.

Ce document explique les étapes requises pour définir des équivalents managés de structures natives et comment les structures résultantes peuvent être passées à des fonctions non managées. Ce document suppose que des structures simples, celles qui ne contiennent pas de chaînes ou de pointeurs, sont utilisées. Pour plus d’informations sur l’interopérabilité non blittable, consultez [utilisation de l’interopérabilité C++ (PInvoke implicite)](../dotnet/using-cpp-interop-implicit-pinvoke.md). P/Invoke ne peut pas avoir de types non blittables comme valeur de retour. Les types blittables ont la même représentation dans du code managé et non managé. Pour plus d’informations, consultez [types blittables et non blittables](/dotnet/framework/interop/blittable-and-non-blittable-types).

Le marshaling de structures simples et blittables sur les limites managées/non managées exige d’abord que les versions managées de chaque structure native soient définies. Ces structures peuvent avoir n’importe quel nom légal. Il n’existe aucune relation entre la version native et managée des deux structures, à l’exception de la disposition des données. Par conséquent, il est vital que la version managée contienne des champs de la même taille et dans le même ordre que la version native. (Il n’existe aucun mécanisme permettant de s’assurer que les versions managées et natives de la structure sont équivalentes, de sorte que les incompatibilités ne seront pas visibles jusqu’au moment de l’exécution. Il incombe au programmeur de s’assurer que les deux structures ont la même disposition des données.)

Étant donné que les membres des structures managées sont parfois réorganisés à des fins de performances, il est nécessaire d’utiliser l' <xref:System.Runtime.InteropServices.StructLayoutAttribute> attribut pour indiquer que la structure est disposée de manière séquentielle. Il est également judicieux de définir explicitement le paramètre de compression de la structure de manière à ce qu’il soit identique à celui utilisé par la structure native. (Bien que par défaut, Visual C++ utilise une compression de structure de 8 octets pour le code managé.)

1. Ensuite, utilisez <xref:System.Runtime.InteropServices.DllImportAttribute> pour déclarer des points d’entrée qui correspondent à toutes les fonctions non managées qui acceptent la structure, mais utilisez la version managée de la structure dans les signatures de fonction, qui est un point discutable si vous utilisez le même nom pour les deux versions de la structure.

1. Désormais, le code managé peut passer la version managée de la structure aux fonctions non managées comme s’il s’agissait de fonctions managées. Ces structures peuvent être passées par valeur ou par référence, comme illustré dans l’exemple suivant.

## <a name="unmanaged-and-a-managed-modules"></a>Modules managés et non managés

Le code suivant est constitué d’un module non managé et d’un module managé. Le module non managé est une DLL qui définit une structure appelée location et une fonction appelée GetDistance qui accepte deux instances de la structure location. Le deuxième module est une application de ligne de commande managée qui importe la fonction GetDistance, mais la définit en termes d’équivalent managé de la structure d’emplacement, MLocation. Dans la pratique, le même nom est probablement utilisé pour les deux versions de la structure. Toutefois, un autre nom est utilisé ici pour démontrer que le prototype DllImport est défini en termes de version managée.

Notez qu’aucune partie de la DLL n’est exposée au code managé à l’aide de la directive #include traditionnelle. En fait, la DLL est accessible uniquement au moment de l’exécution. par conséquent, les problèmes liés aux fonctions importées avec DllImport ne seront pas détectés au moment de la compilation.

### <a name="example-unmanaged-dll-module"></a>Exemple : module DLL non managé

```cpp
// TraditionalDll3.cpp
// compile with: /LD /EHsc
#include <iostream>
#include <stdio.h>
#include <math.h>

#define TRADITIONALDLL_EXPORTS
#ifdef TRADITIONALDLL_EXPORTS
   #define TRADITIONALDLL_API __declspec(dllexport)
#else
   #define TRADITIONALDLL_API __declspec(dllimport)
#endif

#pragma pack(push, 8)
struct Location {
   int x;
   int y;
};
#pragma pack(pop)

extern "C" {
   TRADITIONALDLL_API double GetDistance(Location, Location);
   TRADITIONALDLL_API void InitLocation(Location*);
}

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
```

### <a name="example-managed-command-line-application-module"></a>Exemple : module d’application en ligne de commande managé

```cpp
// MarshalStruct_pi.cpp
// compile with: /clr
using namespace System;
using namespace System::Runtime::InteropServices;

[StructLayout(LayoutKind::Sequential, Pack=8)]
value struct MLocation {
   int x;
   int y;
};

value struct TraditionalDLL {
   [DllImport("TraditionalDLL3.dll")]
   static public double GetDistance(MLocation, MLocation);
   [DllImport("TraditionalDLL3.dll")]
   static public double InitLocation(MLocation*);
};

int main() {
   MLocation loc1;
   loc1.x = 0;
   loc1.y = 0;

   MLocation loc2;
   loc2.x = 100;
   loc2.y = 100;

   double dist = TraditionalDLL::GetDistance(loc1, loc2);
   Console::WriteLine("[managed] distance = {0}", dist);

   MLocation loc3;
   TraditionalDLL::InitLocation(&loc3);
   Console::WriteLine("[managed] x={0} y={1}", loc3.x, loc3.y);
}
```

```Output
[unmanaged] loc1(0,0) loc2(100,100)
[managed] distance = 141.42135623731
[unmanaged] Initializing location...
[managed] x=50 y=50
```

## <a name="see-also"></a>Voir aussi

[Utilisation d’un PInvoke explicite en C++ (attribut DllImport)](../dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute.md)
