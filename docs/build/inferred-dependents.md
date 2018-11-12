---
title: Dépendants inférés
ms.date: 11/04/2016
helpviewer_keywords:
- inferred dependents in NMAKE
- dependents, inferred
ms.assetid: 9303045c-69b3-4f35-bffc-19d5cd6ea3c3
ms.openlocfilehash: 958a33c29be0d68fee1044fff1d81235ea9370c6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50641374"
---
# <a name="inferred-dependents"></a>Dépendants inférés

Un dépendant déduit est dérivé d’une règle d’inférence et est évalué avant les dépendants explicites. Si un dépendant déduit est obsolète par rapport à sa cible, NMAKE appelle le bloc de commandes de la dépendance. Si un dépendant déduit n’existe pas ou est obsolète par rapport à ses propres dépendants, NMAKE met à jour le dépendant déduit en premier. Pour plus d’informations sur les dépendants inférés, consultez [règles d’inférence](../build/inference-rules.md).

## <a name="see-also"></a>Voir aussi

[Dépendants](../build/dependents.md)