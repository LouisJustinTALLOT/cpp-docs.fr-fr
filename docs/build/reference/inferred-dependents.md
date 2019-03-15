---
title: Dépendants inférés
ms.date: 11/04/2016
helpviewer_keywords:
- inferred dependents in NMAKE
- dependents, inferred
ms.assetid: 9303045c-69b3-4f35-bffc-19d5cd6ea3c3
ms.openlocfilehash: 2382dec960ef93fc2f73987ad27b4670768a68cc
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2019
ms.locfileid: "57825559"
---
# <a name="inferred-dependents"></a>Dépendants inférés

Un dépendant déduit est dérivé d’une règle d’inférence et est évalué avant les dépendants explicites. Si un dépendant déduit est obsolète par rapport à sa cible, NMAKE appelle le bloc de commandes de la dépendance. Si un dépendant déduit n’existe pas ou est obsolète par rapport à ses propres dépendants, NMAKE met à jour le dépendant déduit en premier. Pour plus d’informations sur les dépendants inférés, consultez [règles d’inférence](inference-rules.md).

## <a name="see-also"></a>Voir aussi

[Dépendants](dependents.md)