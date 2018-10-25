---
title: Évaluateur d’expression, erreur CXX0019 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- CXX0019
dev_langs:
- C++
helpviewer_keywords:
- CXX0019
- CAN0019
ms.assetid: 4c6431fd-3310-4a61-934d-58b070b330fe
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9f1e78bd88f35240e90332ef9a9139558051cab5
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50070125"
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