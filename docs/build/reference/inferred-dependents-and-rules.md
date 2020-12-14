---
description: 'En savoir plus sur : règles et dépendants inférés'
title: Règles et dépendants inférés
ms.date: 11/04/2016
helpviewer_keywords:
- rules, inferred
- inferred dependents in NMAKE
- inferred rules in NMAKE
- dependents, inferred
ms.assetid: 9381e74a-53d9-445c-836d-0ff7ef6112d9
ms.openlocfilehash: 9f4c1d14d18c9c693a7bd71f9207ff36aede8e22
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97191275"
---
# <a name="inferred-dependents-and-rules"></a>Règles et dépendants inférés

NMAKE suppose une dépendante déduite pour une cible s’il existe une règle d’inférence applicable. Une règle s’applique dans les cas suivants :

- *toext* correspond à l’extension de la cible.

- *fromext* correspond à l’extension d’un fichier qui a le nom de base de la cible et qui existe dans le répertoire actuel ou spécifié.

- *fromext* est dans [. SUFFIXes](dot-directives.md); aucun autre *fromext* dans une règle de correspondance n’a une valeur supérieure **. Priorité des SUFFIXes** .

- Aucun dépendant explicite n’a une valeur supérieure **. Priorité des SUFFIXes** .

Les dépendants inférés peuvent entraîner des effets secondaires inattendus. Si le bloc de description de la cible contient des commandes, NMAKE exécute ces commandes à la place des commandes de la règle.

## <a name="see-also"></a>Voir aussi

[Règles d’inférence](inference-rules.md)
