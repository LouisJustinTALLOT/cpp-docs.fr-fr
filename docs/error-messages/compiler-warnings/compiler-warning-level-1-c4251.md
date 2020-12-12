---
description: 'En savoir plus sur : avertissement du compilateur (niveau 1) C4251'
title: Avertissement du compilateur (niveau 1) C4251
ms.date: 04/21/2020
f1_keywords:
- C4251
helpviewer_keywords:
- C4251
ms.assetid: a9992038-f0c2-4fc4-a9be-4509442cbc1e
ms.openlocfilehash: 4d08462442fd64ebef85573f5d538d6a884c8131
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97266232"
---
# <a name="compiler-warning-level-1-c4251"></a>Avertissement du compilateur (niveau 1) C4251

> '*type*' : la classe'*type1*'doit avoir une interface dll pour être utilisée par les clients de la classe'*type2*'

## <a name="remarks"></a>Notes

Pour réduire le risque d’altération des données lors de l’exportation d’une classe déclarée comme [__declspec (dllexport)](../../cpp/dllexport-dllimport.md), assurez-vous que :

- Toutes vos données statiques sont accessibles via des fonctions exportées à partir de la DLL.

- Aucune méthode inline de votre classe ne peut modifier des données statiques.

- Aucune méthode inline de votre classe n’utilise des fonctions CRT ou d’autres fonctions de bibliothèque qui utilisent des données statiques. Pour plus d’informations, consultez [erreurs potentielles lors du passage d’objets CRT à travers les limites des dll](../../c-runtime-library/potential-errors-passing-crt-objects-across-dll-boundaries.md).

- Aucune méthode de votre classe (qu’elle soit inline ou non) ne peut utiliser des types où l’instanciation dans l’EXE et la DLL ont des différences de données statiques.

Vous pouvez éviter les problèmes lors de l’exportation d’une classe à partir d’une DLL : définissez votre classe pour avoir des fonctions virtuelles, et des fonctions pour instancier et supprimer des objets du type. Vous pouvez ensuite simplement appeler des fonctions virtuelles sur le type.

C4251 peut être ignoré si votre classe est dérivée d’un type dans la bibliothèque standard C++, si vous compilez une version de débogage (**/MTD**) et où le message d’erreur du compilateur fait référence `_Container_base` .

## <a name="example"></a>Exemple

Cet exemple exporte une classe spécialisée `VecWrapper` dérivée de `std::vector` .

```cpp
// C4251.cpp
// compile with: /EHsc /MTd /W2 /c
#include <vector>
using namespace std;
class Node;
class __declspec(dllexport) VecWrapper : vector<Node *> {};   // C4251
```
