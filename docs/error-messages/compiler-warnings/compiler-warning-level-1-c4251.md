---
title: Compilateur avertissement (niveau 1) C4251 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4251
dev_langs:
- C++
helpviewer_keywords:
- C4251
ms.assetid: a9992038-f0c2-4fc4-a9be-4509442cbc1e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ad47d769dbfd09cc741be18598355dc34486bd54
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46045690"
---
# <a name="compiler-warning-level-1-c4251"></a>Avertissement du compilateur (niveau 1) C4251

'identificateur' : classe 'type' doit avoir une interface dll pour être utilisé par les clients de la classe 'type2'

Pour minimiser le risque d’altération des données lors de l’exportation d’une classe avec [__declspec (dllexport)](../../cpp/dllexport-dllimport.md), vérifiez que :

- Toutes vos données statiques est l’accès via les fonctions exportées à partir de la DLL.

- Aucune méthode inline de votre classe ne peut modifier des données statiques.

- Aucune méthode inline de votre classe n’utilise des fonctions CRT ou d’autres fonctions de bibliothèque utilisent des données statiques (consultez [erreurs potentielles en passant CRT objets entre frontières DLL](../../c-runtime-library/potential-errors-passing-crt-objects-across-dll-boundaries.md) pour plus d’informations).

- Aucune méthode de votre classe (indépendamment du incorporation (inlining)) peuvent utiliser des types où l’instanciation de l’EXE et DLL présentent les différences de données statiques.

Vous pouvez éviter d’exporter des classes en définissant une DLL qui définit une classe avec des fonctions virtuelles et les fonctions que vous pouvez appeler pour instancier et de supprimer des objets du type.  Vous pouvez ensuite simplement appeler des fonctions virtuelles sur le type.

Pour plus d’informations sur l’exportation de modèles, consultez [ http://support.microsoft.com/default.aspx?scid=KB; EN-US ; 168958](http://support.microsoft.com/default.aspx?scid=KB;EN-US;168958).

C4251 peut être ignorée si vous dérivez d’un type dans la bibliothèque Standard C++, compilez une version debug (**/MTd**) et où le message d’erreur du compilateur fait référence à _Container_base.

```
// C4251.cpp
// compile with: /EHsc /MTd /W2 /c
#include <vector>
using namespace std;
class Node;
class __declspec(dllimport) VecWrapper : vector<Node *> {};   // C4251
```