---
title: Évaluateur d'expression, erreur CXX0024
ms.date: 11/04/2016
f1_keywords:
- CXX0024
helpviewer_keywords:
- CXX0024
- CAN0024
ms.assetid: eca6adbd-8ff2-4f51-a1cc-a2e9d5d0a47d
ms.openlocfilehash: 93f8389ed3959d5747e46c1234fd8d2eae0f1ae5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62359837"
---
# <a name="expression-evaluator-error-cxx0024"></a>Évaluateur d'expression, erreur CXX0024

opération nécessite une l-value

Une expression qui ne correspond pas à une l-value a été spécifiée pour une opération qui nécessite une l-value.

Une l-value (appelée ainsi car il s’affiche sur le côté gauche d’une instruction d’assignation) est une expression qui fait référence à un emplacement de mémoire.

Par exemple, `buffer[count]` est une l-value valide car elle pointe vers un emplacement de mémoire spécifique. La comparaison logique `zed != 0` n’est pas une l-value valide, car il a la valeur TRUE ou FALSE, non à une adresse mémoire.

Cette erreur est identique à CAN0024.