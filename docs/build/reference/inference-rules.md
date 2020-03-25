---
title: Règles d'inférence
ms.date: 11/04/2016
helpviewer_keywords:
- inference rules in NMAKE
- rules, inference
- NMAKE program, inference rules
ms.assetid: caff320f-fb07-4eea-80c3-a6a2133a8492
ms.openlocfilehash: d3d7ca41d96d3845237b445edefff05044dacdc2
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80170512"
---
# <a name="inference-rules"></a>Règles d'inférence

Les règles d’inférence fournissent des commandes pour mettre à jour les cibles et déduire les dépendants pour les cibles. Les extensions d’une règle d’inférence correspondent à une cible unique et à un dépendant qui ont le même nom de base. Les règles d’inférence sont définies par l’utilisateur ou prédéfinies ; les règles prédéfinies peuvent être redéfinies.

Si une dépendance obsolète n’a pas de commande et si [. Les SUFFIXes](dot-directives.md) contiennent l’extension de dépendante, NMAKE utilise une règle dont les extensions correspondent à la cible et à un fichier existant dans le répertoire actuel ou spécifié. Si plusieurs règles correspondent à des fichiers existants, le **.** La liste des suffixes détermine laquelle utiliser ; Liste des priorités décroissantes de gauche à droite. Si un fichier dépendant n’existe pas et n’est pas listé comme cible dans un autre bloc de description, une règle d’inférence peut créer le dépendant manquant d’un autre fichier portant le même nom de base. Si la cible d’un bloc de description n’a pas de dépendants ou de commandes, une règle d’inférence peut mettre à jour la cible. Les règles d’inférence peuvent générer une cible de ligne de commande même si aucun bloc de description n’existe. NMAKE peut appeler une règle pour un dépendant déduit, même si un dépendant explicite est spécifié.

## <a name="what-do-you-want-to-know-more-about"></a>Sur quels éléments souhaitez-vous obtenir des informations supplémentaires ?

[Définition d’une règle](defining-a-rule.md)

[Règles en mode batch](batch-mode-rules.md)

[Règles prédéfinies](predefined-rules.md)

[Règles et dépendants inférés](inferred-dependents-and-rules.md)

[Priorité dans les règles d’inférence](precedence-in-inference-rules.md)

## <a name="see-also"></a>Voir aussi

[NMAKE, référence](nmake-reference.md)
