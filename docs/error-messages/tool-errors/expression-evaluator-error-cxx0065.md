---
title: Évaluateur d’expression, erreur CXX0065 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- CXX0065
dev_langs:
- C++
helpviewer_keywords:
- CAN0065
- CXX0065
ms.assetid: aac68f87-0b90-4c19-afa6-1c587625a5fd
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c100b1edbd36f4384e8deb1abf5b36465e8da479
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46024162"
---
# <a name="expression-evaluator-error-cxx0065"></a>Évaluateur d'expression, erreur CXX0065

la variable a besoin de frame de pile

Une expression contient une variable qui existe dans la portée actuelle, mais n’a pas encore été créée.

Cette erreur peut se produire lorsque vous avez exécuté le code dans le prologue d’une fonction, mais pas encore configurer le frame de pile pour la fonction, ou si vous avez exécuté le code dans le code de sortie pour la fonction.

Parcourir le code de prologue jusqu'à ce que le frame de pile a été configuré avant d’évaluer l’expression.

Cette erreur est identique à CAN0065.