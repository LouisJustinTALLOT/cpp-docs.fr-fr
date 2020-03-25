---
title: Avertissement du compilateur (niveau 1) C4251
ms.date: 11/04/2016
f1_keywords:
- C4251
helpviewer_keywords:
- C4251
ms.assetid: a9992038-f0c2-4fc4-a9be-4509442cbc1e
ms.openlocfilehash: 8a723b7ce7fc79fb6be9c9dd2b500631098622b0
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80163217"
---
# <a name="compiler-warning-level-1-c4251"></a>Avertissement du compilateur (niveau 1) C4251

'identificateur' : la classe’type’doit avoir une interface dll pour être utilisée par les clients de la classe’type2 '

Pour réduire le risque d’altération des données lors de l’exportation d’une classe avec [__declspec (dllexport)](../../cpp/dllexport-dllimport.md), assurez-vous que :

- Toutes vos données statiques sont accessibles via des fonctions exportées à partir de la DLL.

- Aucune méthode inline de votre classe ne peut modifier des données statiques.

- Aucune méthode inline de votre classe n’utilise des fonctions CRT ou d’autres fonctions de bibliothèque utilisent des données statiques (pour plus d’informations, consultez [erreurs potentielles passant des objets CRT dans les limites](../../c-runtime-library/potential-errors-passing-crt-objects-across-dll-boundaries.md) de la dll).

- Aucune méthode de votre classe (indépendamment de l’incorporation) ne peut utiliser des types où l’instanciation dans l’EXE et la DLL ont des différences de données statiques.

Vous pouvez éviter d’exporter des classes en définissant une DLL qui définit une classe avec des fonctions virtuelles, et des fonctions que vous pouvez appeler pour instancier et supprimer des objets du type.  Vous pouvez ensuite simplement appeler des fonctions virtuelles sur le type.

C4251 peut être ignoré si vous dérivez d’un type dans la C++ bibliothèque standard, en compilant une version de débogage ( **/MTD**) et où le message d’erreur du compilateur fait référence à _Container_base.

```cpp
// C4251.cpp
// compile with: /EHsc /MTd /W2 /c
#include <vector>
using namespace std;
class Node;
class __declspec(dllimport) VecWrapper : vector<Node *> {};   // C4251
```
