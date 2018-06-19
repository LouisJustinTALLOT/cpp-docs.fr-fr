---
title: Évaluateur d’expression, erreur CXX0024 | Documents Microsoft
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
ms.openlocfilehash: 50a07297ddabf269b003a1f14d967d1187fea96d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33302459"
---
# <a name="expression-evaluator-error-cxx0024"></a>Évaluateur d'expression, erreur CXX0024
l’opération requiert l-value  
  
 Une expression qui ne correspond pas à une l-value a été spécifiée pour une opération qui requiert une l-value.  
  
 Une l-value (appelée ainsi parce qu’elle apparaît sur le côté gauche d’une instruction d’assignation) est une expression qui fait référence à un emplacement de mémoire.  
  
 Par exemple, `buffer[count]` est une l-value valide car elle pointe vers un emplacement mémoire spécifique. La comparaison logique `zed != 0` n’est pas une l-value valide, car il prend la valeur TRUE ou FALSE, pas une adresse mémoire.  
  
 Cette erreur est identique à CAN0024.