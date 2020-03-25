---
title: Évaluateur d'expression, erreur CXX0024
ms.date: 11/04/2016
f1_keywords:
- CXX0024
helpviewer_keywords:
- CXX0024
- CAN0024
ms.assetid: eca6adbd-8ff2-4f51-a1cc-a2e9d5d0a47d
ms.openlocfilehash: 525210090b0a4c2966f2e1432f85fd4bb6a8156d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80195758"
---
# <a name="expression-evaluator-error-cxx0024"></a>Évaluateur d'expression, erreur CXX0024

l’opération nécessite une l-value

Une expression qui ne correspond pas à une l-value a été spécifiée pour une opération qui requiert une l-value.

Une l-value (appelée, car elle apparaît sur le côté gauche d’une instruction d’assignation) est une expression qui fait référence à un emplacement de mémoire.

Par exemple, `buffer[count]` est une l-value valide, car elle pointe vers un emplacement de mémoire spécifique. La comparaison logique `zed != 0` n’est pas une l-value valide, car elle prend la valeur TRUE ou FALSe, et non une adresse mémoire.

Cette erreur est identique à CAN0024.
