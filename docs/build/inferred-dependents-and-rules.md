---
title: Règles et dépendants inférés
ms.date: 11/04/2016
helpviewer_keywords:
- rules, inferred
- inferred dependents in NMAKE
- inferred rules in NMAKE
- dependents, inferred
ms.assetid: 9381e74a-53d9-445c-836d-0ff7ef6112d9
ms.openlocfilehash: 6d2f439a0e936b06012045c62d55b6ad76e5817d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50548900"
---
# <a name="inferred-dependents-and-rules"></a>Règles et dépendants inférés

NMAKE suppose un dépendant déduit pour une cible si une règle d’inférence applicable existe. Une règle s’applique si :

- *toext* correspond à extension de la cible.

- *fromext* correspond à l’extension d’un fichier qui a le nom de base de la cible et qui existe dans le répertoire actuel ou spécifié.

- *fromext* est dans [. SUFFIXES](../build/dot-directives.md); aucun autre *fromext* dans une règle de correspondance a un degré plus élevé **. SUFFIXES** priorité.

- Aucun dépendant explicite n’est plus élevé **. SUFFIXES** priorité.

Dépendants inférés peuvent provoquer des effets secondaires inattendus. Si le bloc de description de la cible contient des commandes, NMAKE exécute ces commandes au lieu des commandes dans la règle.

## <a name="see-also"></a>Voir aussi

[Règles d’inférence](../build/inference-rules.md)