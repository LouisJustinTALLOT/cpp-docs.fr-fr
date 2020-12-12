---
description: 'En savoir plus sur : modificateurs de commande'
title: Modificateurs de commandes
ms.date: 11/04/2016
helpviewer_keywords:
- NMAKE program, command modifiers
- command modifiers
ms.assetid: b661c432-210f-4f05-bc56-744a46e0fc0b
ms.openlocfilehash: d17d5f25719dfe5638ca6688105517d385bdf68e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97182370"
---
# <a name="command-modifiers"></a>Modificateurs de commandes

Vous pouvez spécifier un ou plusieurs modificateurs de commande précédant une commande, éventuellement séparés par des espaces ou des tabulations. Comme avec les commandes, les modificateurs doivent être mis en retrait.

|Modificateur|Objectif|
|--------------|-------------|
|\@*commande*|Empêche l’affichage de la commande. L’affichage par commandes n’est pas supprimé. Par défaut, NMAKE répercute toutes les commandes exécutées. Utilisez/S pour supprimer l’affichage du Makefile entier ; Utilisez **. SILENT** pour supprimer l’affichage pour une partie du Makefile.|
|**-**\[*nombre*] *commande*|Désactive la vérification des erreurs pour la *commande*. Par défaut, NMAKE s’arrête lorsqu’une commande retourne un code de sortie différent de zéro. Si-*Number* est utilisé, NMAKE s’arrête si le code de sortie dépasse *Number*. Les espaces et les tabulations ne peuvent pas apparaître entre le tiret et le *nombre.* Au moins un espace ou une tabulation doit apparaître entre `number` et la *commande*. Utilisez/I pour désactiver la vérification des erreurs pour le Makefile entier ; Utilisez **. IGNORER** pour désactiver la vérification des erreurs pour une partie du Makefile.|
|**!** *command*|Exécute la *commande* pour chaque fichier dépendant si la *commande* utilise <strong>$\*\*</strong> (tous les fichiers dépendants dans la dépendance) ou **$ ?** (tous les fichiers dépendants dans la dépendance avec un horodateur ultérieur à la cible).|

## <a name="see-also"></a>Voir aussi

[Commandes dans un Makefile](commands-in-a-makefile.md)
