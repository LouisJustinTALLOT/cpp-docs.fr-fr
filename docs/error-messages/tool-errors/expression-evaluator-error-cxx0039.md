---
title: Évaluateur d'expression, erreur CXX0039
ms.date: 11/04/2016
f1_keywords:
- CXX0039
helpviewer_keywords:
- CXX0039
- CAN0039
ms.assetid: 8bf698d2-e015-4595-944f-72b81aa43d22
ms.openlocfilehash: 053e57a21f0cb75cbd96732edb6812b3557bcd50
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50463269"
---
# <a name="expression-evaluator-error-cxx0039"></a>Évaluateur d'expression, erreur CXX0039

symbole est ambigu

L’évaluateur d’expression C ne peut pas déterminer quelle instance d’un symbole à utiliser dans une expression. Le symbole apparaît plusieurs fois dans l’arborescence d’héritage.

Vous devez utiliser l’opérateur de résolution de portée (`::`) pour spécifier explicitement l’instance à utiliser dans l’expression.

Cette erreur est identique à CAN0039.