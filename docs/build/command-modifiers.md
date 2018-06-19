---
title: Modificateurs de commandes | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- NMAKE program, command modifiers
- command modifiers
ms.assetid: b661c432-210f-4f05-bc56-744a46e0fc0b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3739c053797bdccd08310e17bf669413ead0db48
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32367171"
---
# <a name="command-modifiers"></a>Modificateurs de commandes
Vous pouvez spécifier un ou plusieurs modificateurs de commandes devant une commande, éventuellement séparée par des espaces ou des tabulations. Comme avec les commandes, modificateurs doivent être mis en retrait.  
  
|Modificateur|Objectif|  
|--------------|-------------|  
|@*Commande*|Empêche l’affichage de la commande. Affichage par les commandes n’est pas supprimé. Par défaut, NMAKE répercute toutes les commandes exécutées. /S permet de supprimer l’affichage du makefile entier ; Utilisez **. En mode silencieux** pour supprimer l’affichage d’une partie du makefile.|  
|**-**[`number` ]*commande*|Désactive la vérification des erreurs pour *commande*. Par défaut, NMAKE s’arrête quand une commande retourne un code de sortie différent de zéro. If -`number` est utilisé, NMAKE s’arrête si le code de sortie dépasse `number`. Des espaces ou des onglets ne peut pas apparaître entre le tiret et *nombre.* Au moins un espace ou tabulation doit apparaître entre `number` et *commande*. Utilisez l’option /I pour désactiver la vérification des erreurs pour le makefile entier ; Utilisez **. Ignorer** pour désactiver la vérification des erreurs pour la partie du makefile.|  
|**!** *command*|Exécute *commande* pour chaque fichier dépendant si *commande* utilise **$ \* \*** (tous les fichiers dépendants dans la dépendance) ou **$?** (tous les fichiers dépendants dans la dépendance avec un horodatage postérieur à la cible).|  
  
## <a name="see-also"></a>Voir aussi  
 [Commandes dans un makefile](../build/commands-in-a-makefile.md)