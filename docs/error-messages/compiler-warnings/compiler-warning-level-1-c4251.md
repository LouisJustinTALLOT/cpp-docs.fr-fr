---
title: Avertissement du compilateur (niveau 1) C4251
ms.date: 04/21/2020
f1_keywords:
- C4251
helpviewer_keywords:
- C4251
ms.assetid: a9992038-f0c2-4fc4-a9be-4509442cbc1e
ms.openlocfilehash: 9f261d3deb7f1cac8cd5c60b920e0be49bc8b7a6
ms.sourcegitcommit: 89d9e1cb08fa872483d1cde98bc2a7c870e505e9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "82032328"
---
# <a name="compiler-warning-level-1-c4251"></a>Avertissement du compilateur (niveau 1) C4251

> '*type*' : classe '*type1*' doit avoir dll-interface pour être utilisé par les clients de classe '*type2*'

## <a name="remarks"></a>Notes

Pour minimiser la possibilité de corruption des données lors de l’exportation d’une classe déclarée [__declspec (dllexport)](../../cpp/dllexport-dllimport.md), assurez-vous que :

- Toutes vos données statiques sont accessibles par le biais de fonctions qui sont exportées à partir de la DLL.

- Aucune méthode inlinée de votre classe ne peut modifier les données statiques.

- Aucune méthode inlinisée de votre classe n’utilise les fonctions CRT ou d’autres fonctions de bibliothèque qui utilisent des données statiques. Pour plus d’informations, voir [erreurs potentielles passant des objets CRT à travers les limites DLL](../../c-runtime-library/potential-errors-passing-crt-objects-across-dll-boundaries.md).

- Aucune méthode de votre classe (qu’elle soit inlinnée ou non) ne peut utiliser des types où l’instantanéisation dans l’EXE et le DLL ont des différences de données statiques.

Vous pouvez éviter les problèmes lors de l’exportation d’une classe à partir d’un DLL: Définissez votre classe pour avoir des fonctions virtuelles, et fonctionne pour instantanéiser et supprimer des objets du type. Vous pouvez alors simplement appeler des fonctions virtuelles sur le type.

C4251 peut être ignoré si votre classe est dérivée d’un type de la Bibliothèque standard C, vous compilez une version de `_Container_base`déboiffée (**/MTd**), et où le message d’erreur de compilateur se réfère à .

## <a name="example"></a>Exemple

Cet échantillon exporte `VecWrapper` une `std::vector`classe spécialisée dérivée de .

```cpp
// C4251.cpp
// compile with: /EHsc /MTd /W2 /c
#include <vector>
using namespace std;
class Node;
class __declspec(dllexport) VecWrapper : vector<Node *> {};   // C4251
```
