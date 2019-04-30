---
title: Évaluateur d'expression, erreur CXX0019
ms.date: 11/04/2016
f1_keywords:
- CXX0019
helpviewer_keywords:
- CXX0019
- CAN0019
ms.assetid: 4c6431fd-3310-4a61-934d-58b070b330fe
ms.openlocfilehash: 266e97f28cf0f27cb87e9743399c66aba87c0e8d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62397105"
---
# <a name="expression-evaluator-error-cxx0019"></a>Évaluateur d'expression, erreur CXX0019

cast de type incorrect

L’évaluateur d’expression C ne peut pas effectuer la conversion comme écrites du type.

Cette erreur est identique à CAN0019.

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Pour corriger en vérifiant les causes possibles suivantes

1. Le type spécifié est inconnu.

1. Il y avait trop de niveaux de types pointeur. Par exemple, la conversion du type

    ```
    (char **)h_message
    ```

   ne peut pas être évaluée par l’évaluateur d’expression C.