---
description: 'En savoir plus sur : évaluateur d’expression, erreur CXX0024'
title: Évaluateur d'expression, erreur CXX0024
ms.date: 11/04/2016
f1_keywords:
- CXX0024
helpviewer_keywords:
- CXX0024
- CAN0024
ms.assetid: eca6adbd-8ff2-4f51-a1cc-a2e9d5d0a47d
ms.openlocfilehash: cb40199c217180b08e62d89dee551130eefefc35
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97228077"
---
# <a name="expression-evaluator-error-cxx0024"></a>Évaluateur d'expression, erreur CXX0024

l’opération nécessite une l-value

Une expression qui ne correspond pas à une l-value a été spécifiée pour une opération qui requiert une l-value.

Une l-value (appelée, car elle apparaît sur le côté gauche d’une instruction d’assignation) est une expression qui fait référence à un emplacement de mémoire.

Par exemple, `buffer[count]` est une l-value valide, car elle pointe vers un emplacement de mémoire spécifique. La comparaison logique `zed != 0` n’est pas une l-value valide, car elle prend la valeur true ou false, et non une adresse mémoire.

Cette erreur est identique à CAN0024.
