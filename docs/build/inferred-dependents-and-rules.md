---
title: Règles et dépendants inférés
ms.date: 11/04/2016
helpviewer_keywords:
- rules, inferred
- inferred dependents in NMAKE
- inferred rules in NMAKE
- dependents, inferred
ms.assetid: 9381e74a-53d9-445c-836d-0ff7ef6112d9
ms.openlocfilehash: 125d64c47fb8ac9cd86269bedf246a131eda57e7
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57414834"
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
