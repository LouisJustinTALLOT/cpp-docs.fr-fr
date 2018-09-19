---
title: Évaluateur d’expression, erreur CXX0052 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- CXX0052
dev_langs:
- C++
helpviewer_keywords:
- CXX0052
- CAN0052
ms.assetid: 5060d479-d0a4-4682-b858-c8b9a4f324e6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1ba8fb898930ef830857773a89cd80e4c43c59c4
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46028153"
---
# <a name="expression-evaluator-error-cxx0052"></a>Évaluateur d'expression, erreur CXX0052

fonction membre non présente

Une fonction membre a été spécifiée comme un point d’arrêt, mais est introuvable. Définition d’un point d’arrêt sur une fonction qui a été inline peut provoquer cette erreur.

Recompiler le fichier avec incorporation (inlining) fermées de force (/ Ob0) pour définir un point d’arrêt dans cette fonction.

Une expression a appelé une fonction qui n’était pas définie.

Cette erreur est identique à CAN0052.