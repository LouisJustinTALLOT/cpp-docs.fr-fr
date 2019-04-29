---
title: Évaluateur d'expression, erreur CXX0052
ms.date: 11/04/2016
f1_keywords:
- CXX0052
helpviewer_keywords:
- CXX0052
- CAN0052
ms.assetid: 5060d479-d0a4-4682-b858-c8b9a4f324e6
ms.openlocfilehash: 12b4aff2c07e81a77b1a822fa15beb972a7e1e05
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62299579"
---
# <a name="expression-evaluator-error-cxx0052"></a>Évaluateur d'expression, erreur CXX0052

fonction membre non présente

Une fonction membre a été spécifiée comme un point d’arrêt, mais est introuvable. Définition d’un point d’arrêt sur une fonction qui a été inline peut provoquer cette erreur.

Recompiler le fichier avec incorporation (inlining) fermées de force (/ Ob0) pour définir un point d’arrêt dans cette fonction.

Une expression a appelé une fonction qui n’était pas définie.

Cette erreur est identique à CAN0052.