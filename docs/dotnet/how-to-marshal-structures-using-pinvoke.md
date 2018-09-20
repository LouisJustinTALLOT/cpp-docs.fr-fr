---
title: 'Comment : marshaler des Structures à l’aide de PInvoke | Microsoft Docs'
ms.custom: get-started-article
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- data marshaling [C++], structures
- platform invoke [C++], structures
- interop [C++], structures
- marshaling [C++], structures
ms.assetid: 35997e6f-9251-4af3-8c6e-0712d64d6a5d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 32c77838b8ce88069eb7b9e1a866ffb82b31bfad
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46389688"
---
# <a name="how-to-marshal-structures-using-pinvoke"></a>Comment : marshaler des structures à l’aide de PInvoke

Ce document explique comment les fonctions natives qui acceptent les structures de style C peuvent être appelées à partir de fonctions managées par à l’aide de P/Invoke. Bien que nous vous recommandons d’utiliser les fonctionnalités d’interopérabilité C++ au lieu de P/Invoke, car P/Invoke offre peu une erreur de génération de rapports n’est pas de type sécurisé et peut être fastidieux à implémenter, si l’API non managée est empaqueté en tant que DLL et le code source n’est pas disponible, P/Invoke est la seule option. Sinon, consultez les documents suivants :

- [Utilisation de l’interopérabilité C++ (PInvoke implicite)](../dotnet/using-cpp-interop-implicit-pinvoke.md)

- [Guide pratique pour marshaler des chaînes à l’aide de PInvoke](../dotnet/how-to-marshal-strings-using-pinvoke.md)

Par défaut, les structures natives et managées sont disposés différemment en mémoire, pour réussir le passage de structures entre la limite managée/nécessite des étapes supplémentaires pour conserver l’intégrité des données.

Ce document explique les étapes requises pour définir des équivalents managés de structures natives et comment les structures qui en résulte peuvent être passés aux fonctions non managées. Ce document part du principe que simple structures : ceux qui ne contiennent pas de chaînes ou pointeurs, sont utilisés. Pour plus d’informations sur l’interopérabilité non blittable, consultez [à l’aide du interopérabilité C++ (PInvoke implicite)](../dotnet/using-cpp-interop-implicit-pinvoke.md). P/Invoke ne peut pas avoir de types non blittables comme valeur de retour. Types blittables ont la même représentation dans le code managé et non managé. Pour plus d’informations, consultez [Types blittables et Non blittables](/dotnet/framework/interop/blittable-and-non-blittable-types).

Marshaling simple, des structures blittables entre la limite managée/nécessite tout d’abord que les versions managées de chaque structure native soit définie. Ces structures peuvent avoir n’importe quel nom juridique ; Il n’existe aucune relation entre la version native et managée des deux structures autre que leur mise en page de données. Par conséquent, il est essentiel que la version gérée contienne des champs qui sont la même taille et dans le même ordre que la version native. (Il n’existe aucun mécanisme pour garantir que les versions managées et natives de la structure sont équivalentes, donc les incompatibilités ne deviendra apparentes jusqu'à l’exécution. Il est la responsabilité du programmeur pour garantir que les deux structures ont la même disposition de données).

Étant donné que les membres de structures managées sont parfois réorganisés à des fins de performances, il est nécessaire d’utiliser le <xref:System.Runtime.InteropServices.StructLayoutAttribute> attribut pour indiquer que la structure sont disposés séquentiellement. Il est également judicieux de définir explicitement la structure de paramètre pour être le même que celui utilisé par la structure native de livraison. (Bien que par défaut, Visual C++ utilise une structure de 8 octets pour les deux le code managé de livraison).

1. Ensuite, utilisez <xref:System.Runtime.InteropServices.DllImportAttribute> pour déclarer des points d’entrée qui correspondent à toutes les fonctions non managées qui acceptent la structure, mais utilisez la version managée de la structure dans les signatures de fonction, qui est discutable si vous utilisez le même nom pour les deux versions de la structure.

1. Maintenant du code managé peut passer la version managée de la structure pour les fonctions non managées comme s’ils étaient des fonctions managées réellement. Ces structures peuvent être passées par valeur ou par référence, comme illustré dans l’exemple suivant.

## <a name="example"></a>Exemple

Le code suivant se compose d’une fonction non managée et un module managé. Le module non managé est une DLL qui définit une structure appelée Location et une fonction appelée GetDistance qui accepte deux instances de la structure de l’emplacement. Le deuxième module est une application de ligne de commande managée qui importe la fonction GetDistance, mais la définit en termes d’un équivalent managé de la structure Location, MLocation. Dans la pratique du même nom serait probablement être utilisé pour les deux versions de la structure ; Toutefois, un autre nom est utilisé ici pour montrer que le prototype DllImport est défini en termes de la version gérée.

Notez qu’aucune partie de la DLL est exposée au code managé à l’aide de traditionnel #include, directive. En fait, la DLL est accessible au moment de l’exécution afin de problèmes liés aux fonctions importées avec DllImport ne seront pas détectés au moment de la compilation.

```
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

## <a name="example"></a>Exemple

```
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
