---
title: Règles et dépendants inférés
ms.date: 11/04/2016
helpviewer_keywords:
- rules, inferred
- inferred dependents in NMAKE
- inferred rules in NMAKE
- dependents, inferred
ms.assetid: 9381e74a-53d9-445c-836d-0ff7ef6112d9
ms.openlocfilehash: b9c3055db0cc173999e1737986166eb334dcf96c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62269906"
---
# <a name="inferred-dependents-and-rules"></a>Règles et dépendants inférés

NMAKE suppose un dépendant déduit pour une cible si une règle d’inférence applicable existe. Une règle s’applique si :

- *toext* correspond à extension de la cible.

- *fromext* correspond à l’extension d’un fichier qui a le nom de base de la cible et qui existe dans le répertoire actuel ou spécifié.

- *fromext* est dans [. SUFFIXES](dot-directives.md); aucun autre *fromext* dans une règle de correspondance a un degré plus élevé **. SUFFIXES** priorité.

- Aucun dépendant explicite n’est plus élevé **. SUFFIXES** priorité.

Dépendants inférés peuvent provoquer des effets secondaires inattendus. Si le bloc de description de la cible contient des commandes, NMAKE exécute ces commandes au lieu des commandes dans la règle.

## <a name="see-also"></a>Voir aussi

[Règles d’inférence](inference-rules.md)
