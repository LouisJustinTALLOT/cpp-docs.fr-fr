---
description: 'En savoir plus sur : évaluateur d’expression, erreur CXX0064'
title: Évaluateur d'expression, erreur CXX0064
ms.date: 11/04/2016
f1_keywords:
- CXX0064
helpviewer_keywords:
- CAN0064
- CXX0064
ms.assetid: aa509e71-0616-41ca-a94e-6c376b041e57
ms.openlocfilehash: 58356a48fc52ee479c92cf5d65494763c3fc4adb
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97173192"
---
# <a name="expression-evaluator-error-cxx0064"></a>Évaluateur d'expression, erreur CXX0064

Impossible de définir un point d’arrêt sur la fonction membre virtuelle liée

Un point d’arrêt a été défini sur une fonction membre virtuelle par le biais d’un pointeur vers un objet, par exemple :

```
pClass->vfunc( int );
```

Vous pouvez définir un point d’arrêt sur une fonction virtuelle en entrant la classe, par exemple :

```
Class::vfunc( int );
```

Cette erreur est identique à CAN0064.
