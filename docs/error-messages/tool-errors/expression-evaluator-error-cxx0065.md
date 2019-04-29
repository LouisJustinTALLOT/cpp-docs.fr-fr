---
title: Évaluateur d'expression, erreur CXX0065
ms.date: 11/04/2016
f1_keywords:
- CXX0065
helpviewer_keywords:
- CAN0065
- CXX0065
ms.assetid: aac68f87-0b90-4c19-afa6-1c587625a5fd
ms.openlocfilehash: 7b62e42da2a74d910e2dc56ce2dfcb5cb38f2bfa
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62299315"
---
# <a name="expression-evaluator-error-cxx0065"></a>Évaluateur d'expression, erreur CXX0065

la variable a besoin de frame de pile

Une expression contient une variable qui existe dans la portée actuelle, mais n’a pas encore été créée.

Cette erreur peut se produire lorsque vous avez exécuté le code dans le prologue d’une fonction, mais pas encore configurer le frame de pile pour la fonction, ou si vous avez exécuté le code dans le code de sortie pour la fonction.

Parcourir le code de prologue jusqu'à ce que le frame de pile a été configuré avant d’évaluer l’expression.

Cette erreur est identique à CAN0065.