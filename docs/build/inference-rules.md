---
title: Règles d’inférence | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- inference rules in NMAKE
- rules, inference
- NMAKE program, inference rules
ms.assetid: caff320f-fb07-4eea-80c3-a6a2133a8492
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ed45e5ad61ea1cc50172cd86716b357baa64fa39
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45724383"
---
# <a name="inference-rules"></a>Règles d'inférence

Règles d’inférence fournissent des commandes pour mettre à jour les cibles et de déduire des dépendants pour les cibles. Les extensions dans une règle d’inférence correspondent à une seule cible et dépendants qui ont le même nom de base. Règles d’inférence sont définies par l’utilisateur ou prédéfinies ; règles prédéfinies peuvent être redéfinies.

Si une dépendance obsolète n’a pas de commandes et si [. SUFFIXES](../build/dot-directives.md) contient l’extension du dépendant, utilise NMAKE une règle dont les extensions correspondent à la cible et fichier dans le répertoire actuel ou spécifié. Si plusieurs règles correspondent à des fichiers existants, le **. SUFFIXES** liste détermine lequel utiliser ; priorité de la liste va de gauche à droite. Si un fichier dépendant n’existe pas et n’est pas répertorié en tant que cible dans un autre bloc de description, une règle d’inférence peut créer le dépendant manquant à partir d’un autre fichier portant le même nom de base. Si la cible d’un bloc description n’a aucun dépendants ou des commandes, une règle d’inférence peut mettre à jour la cible. Règles d’inférence peuvent générer une cible de ligne de commande même si aucun bloc de description. NMAKE peut appeler une règle pour un dépendant déduit même si un dépendant explicite est spécifié.

## <a name="what-do-you-want-to-know-more-about"></a>Sur quels éléments souhaitez-vous obtenir des informations supplémentaires ?

[Définition d’une règle](../build/defining-a-rule.md)

[Règles en mode batch](../build/batch-mode-rules.md)

[Règles prédéfinies](../build/predefined-rules.md)

[Règles et dépendants inférés](../build/inferred-dependents-and-rules.md)

[Priorité dans les règles d’inférence](../build/precedence-in-inference-rules.md)

## <a name="see-also"></a>Voir aussi

[NMAKE, référence](../build/nmake-reference.md)