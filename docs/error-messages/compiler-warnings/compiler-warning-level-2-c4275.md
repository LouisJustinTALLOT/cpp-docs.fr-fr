---
description: 'En savoir plus sur : avertissement du compilateur (niveau 2) C4275'
title: Avertissement du compilateur (niveau 2) C4275
ms.date: 02/08/2019
f1_keywords:
- C4275
helpviewer_keywords:
- C4275
ms.assetid: 18de967a-0a44-4dbc-a2e8-fc4c067ba909
ms.openlocfilehash: 0dd212d7439b73c28a5426574b72ff8150abe93c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97173647"
---
# <a name="compiler-warning-level-2-c4275"></a>Avertissement du compilateur (niveau 2) C4275

> classe'*class_1*'non-dll utilisée comme base pour la classe'*class_2*'de l’interface dll

Une classe exportée a été dérivée d’une classe qui n’a pas été exportée.

Pour réduire le risque d’altération des données lors de l’exportation d’une classe avec [__declspec (dllexport)](../../cpp/dllexport-dllimport.md), assurez-vous que :

- Toutes vos données statiques sont accessibles via des fonctions exportées à partir de la DLL.

- Aucune méthode inline de votre classe ne peut modifier des données statiques.

- Aucune méthode inline de votre classe n’utilise des fonctions CRT ou d’autres fonctions de bibliothèque qui utilisent des données statiques.

- Aucune fonction de classe inline n’utilise des fonctions CRT, ni d’autres fonctions de bibliothèque, où vous accédez à des données statiques.

- Aucune méthode de votre classe (indépendamment de l’incorporation) ne peut utiliser des types où l’instanciation dans l’EXE et la DLL ont des différences de données statiques.

Vous pouvez éviter d’exporter des classes en définissant une DLL qui définit une classe avec des fonctions virtuelles, et des fonctions que vous pouvez appeler pour instancier et supprimer des objets du type.  Vous pouvez ensuite simplement appeler des fonctions virtuelles sur le type.

C4275 peut être ignoré dans Visual C++ si vous dérivez d’un type dans la bibliothèque standard C++, en compilant une version de débogage (**/MTD**) et en faisant référence au message d’erreur du compilateur `_Container_base` .

```cpp
// C4275.cpp
// compile with: /EHsc /MTd /W2 /c
#include <vector>
using namespace std;
class Node;
class __declspec(dllimport) VecWrapper : vector<Node *> {};   // C4275
```
