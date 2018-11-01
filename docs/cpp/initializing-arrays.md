---
title: Initialisation des tableaux
ms.date: 11/04/2016
helpviewer_keywords:
- initializing arrays [C++]
- arrays [C++], initializing
ms.assetid: 41efe5f0-15b5-4f49-9196-c4902f8fc705
ms.openlocfilehash: e055e7759865fc151176097c6f0afd9ee237f4c1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50447084"
---
# <a name="initializing-arrays"></a>Initialisation des tableaux

Si une classe a un constructeur, les tableaux de cette classe sont initialisés par un constructeur. S'il y a moins d'éléments dans la liste d'initialiseurs que les éléments du tableau, le constructeur par défaut est utilisé pour les éléments restants. Si aucun constructeur par défaut n'est défini pour la classe, la liste d'initialiseurs doit être complète (autrement dit, il doit y avoir un initialiseur pour chaque élément du tableau.)

Prenons la classe `Point` qui définit deux constructeurs :

```cpp
// initializing_arrays1.cpp
class Point
{
public:
   Point()   // Default constructor.
   {
   }
   Point( int, int )   // Construct from two ints
   {
   }
};

// An array of Point objects can be declared as follows:
Point aPoint[3] = {
   Point( 3, 3 )     // Use int, int constructor.
};

int main()
{
}
```

Le premier élément de `aPoint` est construit en utilisant le constructeur `Point( int, int )`. Les deux éléments restants sont construits à l'aide du constructeur par défaut.

Tableaux membres statiques (si **const** ou non) peuvent être initialisés dans leurs définitions (en dehors de la déclaration de classe). Exemple :

```cpp
// initializing_arrays2.cpp
class WindowColors
{
public:
    static const char *rgszWindowPartList[7];
};

const char *WindowColors::rgszWindowPartList[7] = {
    "Active Title Bar", "Inactive Title Bar", "Title Bar Text",
    "Menu Bar", "Menu Bar Text", "Window Background", "Frame"   };
int main()
{
}
```