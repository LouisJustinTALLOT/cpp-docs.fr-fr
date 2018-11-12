---
title: Évaluateur d'expression, erreur CXX0030
ms.date: 11/04/2016
f1_keywords:
- CXX0030
helpviewer_keywords:
- CAN0030
- CXX0030
ms.assetid: ada8b48c-09c8-49bf-ae23-313ed663c4fe
ms.openlocfilehash: 1e52b238905fba5c310a89377b81548a1c6b5784
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50500345"
---
# <a name="expression-evaluator-error-cxx0030"></a>Évaluateur d'expression, erreur CXX0030

expression non évaluée

Évaluateur d’expression du débogueur n’a pas pu obtenir une valeur pour l’expression comme écrite. Une cause probable est que l’expression fait référence à la mémoire qui est en dehors de l’espace d’adressage du programme (déréférencement d’un pointeur null n’est un exemple). Windows n’autorise pas l’accès à la mémoire qui est en dehors de l’espace d’adressage du programme.

Vous pouvez, si vous le souhaitez, réécrivez votre expression à l’aide de parenthèses pour contrôler l’ordre d’évaluation.

Cette erreur est identique à CAN0030.