---
description: En savoir plus sur les points de séquence C
title: Points de séquence C
ms.date: 11/04/2016
helpviewer_keywords:
- sequence points
ms.assetid: c84885a5-4336-4eba-a643-058df4249903
ms.openlocfilehash: 7ba46978271cafbdc6b06fd01d69673dbf905d33
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97207109"
---
# <a name="c-sequence-points"></a>Points de séquence C

La valeur d'un objet peut être modifiée une seule fois par une expression entre les « points de séquence » consécutifs. Le langage C définit les points de séquence suivants :

- Opérande gauche de l’opérateur AND logique ( **&&** ). L’opérande gauche de l’opérateur AND logique est complètement évalué et tous les effets secondaires sont terminés avant la poursuite du traitement. Si l'opérande gauche a la valeur false (0), l'autre opérande n'est pas évaluée.

- Opérande gauche de l'opérateur OR logique (`||`). L'opérande gauche de l'opérateur OR logique est complètement évalué et tous les effets secondaires sont terminés avant la poursuite du traitement. Si l'opérande gauche a la valeur true (différent de zéro), l'autre opérande n'est pas évalué.

- Opérande gauche de l'opérateur virgule. L'opérande gauche de l'opérateur virgule est complètement évalué et tous les effets secondaires sont terminés avant la poursuite du traitement. Les deux opérandes de l'opérateur virgule sont toujours évalués. Notez que l'opérateur virgule dans un appel de fonction ne garantit pas un ordre d'évaluation.

- Opérateur d'appel de fonction. Tous les arguments d'une fonction sont évalués et tous les effets secondaires se terminent avant l'entrée dans la fonction. Aucun ordre d'évaluation entre les arguments n'est spécifié.

- Premier opérande de l'opérateur conditionnel. Le premier opérande de l'opérateur conditionnel est complètement évalué et tous les effets secondaires sont terminés avant la poursuite du traitement.

- La fin d'une expression d'initialisation complète (c'est-à-dire une expression qui ne fait pas partie d'une autre expression telle que la fin d'une initialisation dans une instruction de déclaration).

- L'expression dans une instruction d'expression. Les instructions Expression sont composées d'une expression facultative suivie d'un point-virgule (**;**). L'expression est évaluée pour ses effets secondaires, et un point de séquence est ajouté à la suite de cette évaluation.

- Expression de contrôle dans une instruction de sélection ( **`if`** ou **`switch`** ). L'expression est complètement évaluée et tous les effets secondaires sont terminés avant l'exécution du code dépendant de la sélection.

- Expression de contrôle d’une **`while`** **`do`** instruction ou. L’expression est complètement évaluée et tous les effets secondaires sont terminés avant l’exécution des instructions de l’itération suivante de la **`while`** **`do`** boucle ou.

- Chacune des trois expressions d’une **`for`** instruction. Les expressions sont complètement évaluées et tous les effets secondaires sont terminés avant l’exécution des instructions de l’itération suivante de la **`for`** boucle.

- Expression dans une **`return`** instruction. L'expression est complètement évaluée et tous les effets secondaires sont terminés avant que le contrôle ne retourne à la fonction appelante.

## <a name="see-also"></a>Voir aussi

[Évaluation d’expression](../c-language/expression-evaluation-c.md)
