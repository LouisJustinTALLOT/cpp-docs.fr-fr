---
title: Évaluation d'expression (C)
ms.date: 11/04/2016
helpviewer_keywords:
- expression evaluation
- expressions [C++], evaluating
ms.assetid: 9493f8cc-64a2-4284-9aaf-26eec11c4f40
ms.openlocfilehash: 37affedc0bcf3fb1423898ecf2c570794d9625c0
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/12/2019
ms.locfileid: "56151089"
---
# <a name="expression-evaluation-c"></a>Évaluation d'expression (C)

Les expressions impliquant une assignation, un incrément unaire, une décrémentation unaire, ou appelant une fonction peuvent avoir des conséquences sur leur évaluation (effets secondaires). Lorsqu'un « point de séquence » est atteint, tout ce qui le précède, y compris tous les effets secondaires, est garanti avoir été évalué avant que l'évaluation commence sur tout ce qui suit le point de séquence.

Les « effets secondaires » sont des modifications déclenchées par l'évaluation d'une expression. Les effets secondaires se produisent chaque fois que la valeur d'une variable est modifiée par une évaluation de l'expression. Toutes les opérations d'assignation ont des effets secondaires. Les appels de fonction peuvent également avoir des effets secondaires s'ils modifient la valeur d'un élément visible, par assignation directe ou indirecte via un pointeur.

## <a name="see-also"></a>Voir aussi

[Opérandes et expressions](../c-language/operands-and-expressions.md)
