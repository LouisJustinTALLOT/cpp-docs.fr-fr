---
title: Évaluateur d'expression, erreur CXX0064
ms.date: 11/04/2016
f1_keywords:
- CXX0064
helpviewer_keywords:
- CAN0064
- CXX0064
ms.assetid: aa509e71-0616-41ca-a94e-6c376b041e57
ms.openlocfilehash: 71e4e3e87b33849e6b487b79268ebc9574c2e5a6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62299476"
---
# <a name="expression-evaluator-error-cxx0064"></a>Évaluateur d'expression, erreur CXX0064

ne peut pas définir le point d’arrêt sur fonction membre virtuelle liée

Un point d’arrêt a été défini sur une fonction membre virtuelle via un pointeur vers un objet, tel que :

```
pClass->vfunc( int );
```

Peut indiquer un point d’arrêt sur une fonction virtuelle en entrant la classe, par exemple :

```
Class::vfunc( int );
```

Cette erreur est identique à CAN0064.