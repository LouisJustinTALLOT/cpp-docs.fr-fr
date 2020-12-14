---
description: 'En savoir plus sur : évaluateur d’expression, erreur CXX0039'
title: Évaluateur d'expression, erreur CXX0039
ms.date: 11/04/2016
f1_keywords:
- CXX0039
helpviewer_keywords:
- CXX0039
- CAN0039
ms.assetid: 8bf698d2-e015-4595-944f-72b81aa43d22
ms.openlocfilehash: 19d8e01e3eb8f599319988a8aa9fc0bf401701fc
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97244730"
---
# <a name="expression-evaluator-error-cxx0039"></a>Évaluateur d'expression, erreur CXX0039

symbole ambigu

L’évaluateur d’expression C ne peut pas déterminer quelle instance d’un symbole utiliser dans une expression. Le symbole apparaît plusieurs fois dans l’arborescence d’héritage.

Vous devez utiliser l’opérateur de résolution de portée ( `::` ) pour spécifier explicitement l’instance à utiliser dans l’expression.

Cette erreur est identique à CAN0039.
