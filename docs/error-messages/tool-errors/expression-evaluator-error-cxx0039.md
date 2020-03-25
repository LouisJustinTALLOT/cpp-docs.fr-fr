---
title: Évaluateur d'expression, erreur CXX0039
ms.date: 11/04/2016
f1_keywords:
- CXX0039
helpviewer_keywords:
- CXX0039
- CAN0039
ms.assetid: 8bf698d2-e015-4595-944f-72b81aa43d22
ms.openlocfilehash: 5706d002eb3d566d05b059cb04b6b1626fdb3d33
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80185124"
---
# <a name="expression-evaluator-error-cxx0039"></a>Évaluateur d'expression, erreur CXX0039

symbole ambigu

L’évaluateur d’expression C ne peut pas déterminer quelle instance d’un symbole utiliser dans une expression. Le symbole apparaît plusieurs fois dans l’arborescence d’héritage.

Vous devez utiliser l’opérateur de résolution de portée (`::`) pour spécifier explicitement l’instance à utiliser dans l’expression.

Cette erreur est identique à CAN0039.
