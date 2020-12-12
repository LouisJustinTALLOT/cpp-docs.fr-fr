---
description: 'En savoir plus sur : évaluation d’expression (C)'
title: Évaluation d'expression (C)
ms.date: 11/04/2016
helpviewer_keywords:
- expression evaluation
- expressions [C++], evaluating
ms.assetid: 9493f8cc-64a2-4284-9aaf-26eec11c4f40
ms.openlocfilehash: 740cb7a7bc14b598c45b3c8f45e719dcb85372e5
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97196449"
---
# <a name="expression-evaluation-c"></a>Évaluation d'expression (C)

Les expressions impliquant une assignation, un incrément unaire, une décrémentation unaire, ou appelant une fonction peuvent avoir des conséquences sur leur évaluation (effets secondaires). Lorsqu'un « point de séquence » est atteint, tout ce qui le précède, y compris tous les effets secondaires, est garanti avoir été évalué avant que l'évaluation commence sur tout ce qui suit le point de séquence.

Les « effets secondaires » sont des modifications déclenchées par l'évaluation d'une expression. Les effets secondaires se produisent chaque fois que la valeur d'une variable est modifiée par une évaluation de l'expression. Toutes les opérations d'assignation ont des effets secondaires. Les appels de fonction peuvent également avoir des effets secondaires s'ils modifient la valeur d'un élément visible, par assignation directe ou indirecte via un pointeur.

## <a name="see-also"></a>Voir aussi

[Opérandes et expressions](../c-language/operands-and-expressions.md)
