---
title: Initialisation des classes et structs sans constructeurs (C++)
ms.date: 10/17/2018
ms.assetid: 3e55c3d6-1c6b-4084-b9e5-221b151402f4
ms.openlocfilehash: 4f696f4fc8862b953e40a03c96b88d1a0b7f720b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50547327"
---
# <a name="initializing-classes-and-structs-without-constructors-c"></a>Initialisation des classes et structs sans constructeurs (C++)

Il n'est pas toujours nécessaire de définir un constructeur pour une classe, en particulier celles qui sont relativement simples. Les utilisateurs peuvent initialiser des objets d'une classe ou d'un struct à l'aide de l'initialisation uniforme, comme illustré dans l'exemple suivant :

```cpp
// no_constructor.cpp
// Compile with: cl /EHsc no_constructor.cpp
#include <time.h>

// No constructor
struct TempData
{
    int StationId;
    time_t timeSet;
    double current;
    double maxTemp;
    double minTemp;
};

// Has a constructor
struct TempData2
{
    TempData2(double minimum, double maximum, double cur, int id, time_t t) :
       stationId{id}, timeSet{t}, current{cur}, maxTemp{maximum}, minTemp{minimum} {}
    int stationId;
    time_t timeSet;
    double current;
    double maxTemp;
    double minTemp;
};

int main()
{
    time_t time_to_set;

    // Member initialization (in order of declaration):
    TempData td{ 45978, time(&time_to_set), 28.9, 37.0, 16.7 };

    // Default initialization = {0,0,0,0,0}
    TempData td_default{};

    // Uninitialized = if used, emits warning C4700 uninitialized local variable
    TempData td_noInit;

    // Member declaration (in order of ctor parameters)
    TempData2 td2{ 16.7, 37.0, 28.9, 45978, time(&time_to_set) };

    return 0;
}
```

Notez que lorsqu’une classe ou un struct n’a aucun constructeur, vous fournir les éléments de liste dans l’ordre que les membres sont déclarés dans la classe. Si la classe a un constructeur, fournissent les éléments dans l’ordre des paramètres.

## <a name="see-also"></a>Voir aussi

[Classes et structs](../cpp/classes-and-structs-cpp.md)<br/>
[Constructeurs](../cpp/constructors-cpp.md)
