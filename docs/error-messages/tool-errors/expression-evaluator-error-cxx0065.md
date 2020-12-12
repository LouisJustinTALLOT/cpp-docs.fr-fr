---
description: 'En savoir plus sur : évaluateur d’expression, erreur CXX0065'
title: Évaluateur d'expression, erreur CXX0065
ms.date: 11/04/2016
f1_keywords:
- CXX0065
helpviewer_keywords:
- CAN0065
- CXX0065
ms.assetid: aac68f87-0b90-4c19-afa6-1c587625a5fd
ms.openlocfilehash: 8013bdc2541e2ab3719ef700413a87df49731983
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97173166"
---
# <a name="expression-evaluator-error-cxx0065"></a>Évaluateur d'expression, erreur CXX0065

la variable a besoin d’un frame de pile

Une expression contient une variable qui existe dans l’étendue actuelle, mais n’a pas encore été créée.

Cette erreur peut se produire lorsque vous avez effectué un pas à pas détaillé dans le prologue d’une fonction, mais que vous n’avez pas encore configuré le frame de pile pour la fonction, ou si vous avez effectué un pas à pas détaillé dans le code de sortie de la fonction.

Parcourez le code de prologue jusqu’à ce que le frame de pile ait été configuré avant d’évaluer l’expression.

Cette erreur est identique à CAN0065.
