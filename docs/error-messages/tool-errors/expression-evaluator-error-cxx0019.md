---
description: 'En savoir plus sur : évaluateur d’expression, erreur CXX0019'
title: Évaluateur d'expression, erreur CXX0019
ms.date: 11/04/2016
f1_keywords:
- CXX0019
helpviewer_keywords:
- CXX0019
- CAN0019
ms.assetid: 4c6431fd-3310-4a61-934d-58b070b330fe
ms.openlocfilehash: 1caf4714c1fc719883ee889c14225e4f69e961a9
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97228233"
---
# <a name="expression-evaluator-error-cxx0019"></a>Évaluateur d'expression, erreur CXX0019

conversion de type incorrecte

L’évaluateur d’expression C ne peut pas effectuer la conversion de type telle qu’elle est écrite.

Cette erreur est identique à CAN0019.

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Pour corriger en vérifiant les causes possibles suivantes

1. Le type spécifié est inconnu.

1. Trop de niveaux de types pointeur. Par exemple, la conversion de type

    ```
    (char **)h_message
    ```

   ne peut pas être évaluée par l’évaluateur d’expression C.
