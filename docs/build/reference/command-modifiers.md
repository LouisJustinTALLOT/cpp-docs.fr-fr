---
title: Modificateurs de commandes
ms.date: 11/04/2016
helpviewer_keywords:
- NMAKE program, command modifiers
- command modifiers
ms.assetid: b661c432-210f-4f05-bc56-744a46e0fc0b
ms.openlocfilehash: 6131b94a6ee78026b8d5337061a6238df785b64d
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2019
ms.locfileid: "57825227"
---
# <a name="command-modifiers"></a>Modificateurs de commandes

Vous pouvez spécifier un ou plusieurs modificateurs de commandes devant une commande, éventuellement séparée par des espaces ou des tabulations. Comme avec les commandes, modificateurs doivent être mis en retrait.

|Modificateur|Objectif|
|--------------|-------------|
|\@*command*|Empêche l’affichage de la commande. Affichage par les commandes n’est pas supprimé. Par défaut, NMAKE répercute toutes les commandes exécutées. /S permet de supprimer l’affichage du makefile entier ; Utilisez **. En mode silencieux** pour supprimer l’affichage d’une partie du makefile.|
|**-**\[*number*] *command*|Désactive la vérification des erreurs pour *commande*. Par défaut, NMAKE s’arrête quand une commande retourne un code de sortie différent de zéro. If -*nombre* est utilisé, NMAKE s’arrête si le code de sortie dépasse *nombre*. Espaces ou des tabulations ne peut pas apparaître entre le tiret et *nombre.* Au moins un espace ou tabulation doit apparaître entre `number` et *commande*. Utilisez l’option /I pour désactiver la vérification des erreurs pour le makefile entier ; Utilisez **. Ignorer** pour désactiver la vérification des erreurs pour la partie du makefile.|
|**\!** *command*|Exécute *commande* pour chaque fichier dépendant si *commande* utilise <strong>$ \* \*</strong> (tous les fichiers dépendants dans la dépendance) ou **$?** (tous les fichiers dépendants dans la dépendance avec une horodatage la plus récente que la cible).|

## <a name="see-also"></a>Voir aussi

[Commandes dans un makefile](commands-in-a-makefile.md)
