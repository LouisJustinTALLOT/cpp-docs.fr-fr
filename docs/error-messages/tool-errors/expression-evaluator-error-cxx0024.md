---
title: Évaluateur d’expression, erreur CXX0024 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- CXX0024
dev_langs:
- C++
helpviewer_keywords:
- CXX0024
- CAN0024
ms.assetid: eca6adbd-8ff2-4f51-a1cc-a2e9d5d0a47d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2816be7bb1d33757d9722d605d461ac6fb34fadd
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46118191"
---
# <a name="expression-evaluator-error-cxx0024"></a>Évaluateur d'expression, erreur CXX0024

opération nécessite une l-value

Une expression qui ne correspond pas à une l-value a été spécifiée pour une opération qui nécessite une l-value.

Une l-value (appelée ainsi car il s’affiche sur le côté gauche d’une instruction d’assignation) est une expression qui fait référence à un emplacement de mémoire.

Par exemple, `buffer[count]` est une l-value valide car elle pointe vers un emplacement de mémoire spécifique. La comparaison logique `zed != 0` n’est pas une l-value valide, car il a la valeur TRUE ou FALSE, non à une adresse mémoire.

Cette erreur est identique à CAN0024.