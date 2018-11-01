---
title: Avertissement du compilateur (niveau 1) C4251
ms.date: 11/04/2016
f1_keywords:
- C4251
helpviewer_keywords:
- C4251
ms.assetid: a9992038-f0c2-4fc4-a9be-4509442cbc1e
ms.openlocfilehash: d2fff1d2f30c4ac80af6d5b9ca452fa5f30f5a15
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50649655"
---
# <a name="compiler-warning-level-1-c4251"></a>Avertissement du compilateur (niveau 1) C4251

'identificateur' : classe 'type' doit avoir une interface dll pour être utilisé par les clients de la classe 'type2'

Pour minimiser le risque d’altération des données lors de l’exportation d’une classe avec [__declspec (dllexport)](../../cpp/dllexport-dllimport.md), vérifiez que :

- Toutes vos données statiques est l’accès via les fonctions exportées à partir de la DLL.

- Aucune méthode inline de votre classe ne peut modifier des données statiques.

- Aucune méthode inline de votre classe n’utilise des fonctions CRT ou d’autres fonctions de bibliothèque utilisent des données statiques (consultez [erreurs potentielles en passant CRT objets entre frontières DLL](../../c-runtime-library/potential-errors-passing-crt-objects-across-dll-boundaries.md) pour plus d’informations).

- Aucune méthode de votre classe (indépendamment du incorporation (inlining)) peuvent utiliser des types où l’instanciation de l’EXE et DLL présentent les différences de données statiques.

Vous pouvez éviter d’exporter des classes en définissant une DLL qui définit une classe avec des fonctions virtuelles et les fonctions que vous pouvez appeler pour instancier et de supprimer des objets du type.  Vous pouvez ensuite simplement appeler des fonctions virtuelles sur le type.

C4251 peut être ignorée si vous dérivez d’un type dans la bibliothèque Standard C++, compilez une version debug (**/MTd**) et où le message d’erreur du compilateur fait référence à _Container_base.

```cpp
// C4251.cpp
// compile with: /EHsc /MTd /W2 /c
#include <vector>
using namespace std;
class Node;
class __declspec(dllimport) VecWrapper : vector<Node *> {};   // C4251
```