---
title: Directives précédées par un point
ms.date: 11/04/2016
helpviewer_keywords:
- NMAKE program, dot directives
- dot directives in NMAKE
ms.assetid: ab35da65-30b6-48b7-87d6-61503d7faf9f
ms.openlocfilehash: 18688afedfe076ea2e4485471ffbe92dc2e09a2d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50542868"
---
# <a name="dot-directives"></a>Directives précédées par un point

Spécifiez des directives dot en dehors d’un bloc de description, au début d’une ligne. Directives dot commencent par un point (. ) et sont suivis par un signe deux-points ( :)). Les onglets et les espaces sont autorisés. Les noms de directive point respectent la casse et sont en majuscules.

|Directive|Objectif|
|---------------|-------------|
|**. IGNORER :**|Ignore les codes de sortie différent de zéro retournés par les commandes, à partir de l’emplacement où qu'elle est spécifiée à la fin du makefile. Par défaut, NMAKE s’arrête si une commande retourne un code de sortie différent de zéro. Pour restaurer la vérification des erreurs, utilisez **! CMDSWITCHES**. Pour ignorer le code de sortie pour une seule commande, utilisez le modificateur tiret (-). Pour ignorer les codes de sortie dans un fichier entier, utilisez / I.|
|**. PRÉCIEUX :** *cibles*|Conserve *cibles* sur le disque si les commandes pour les mettre à jour sont interrompus ; n’a aucun effet si une commande gère une interruption en supprimant le fichier. Séparez les noms des cibles par un ou plusieurs espaces ou des tabulations. Par défaut, NMAKE supprime une cible si une build est interrompue par CTRL + C ou CTRL + Pause. L’utilisation de **. PRÉCIEUX** s’applique à tout le makefile ; plusieurs spécifications sont cumulatifs.|
|**. EN MODE SILENCIEUX :**|Supprime l’affichage des commandes exécutées, à partir de l’emplacement où qu'elle est spécifiée à la fin du makefile. Par défaut, NMAKE affiche les commandes qu’il appelle. Pour rétablir l’écho, utilisez **! CMDSWITCHES**. Pour supprimer l’écho d’une seule commande, utilisez le **@** modificateur. Pour supprimer l’écho pour un fichier entier, utilisez/sec.|
|**. SUFFIXES :** `list`|Répertorie les extensions pour la correspondance de règle d’inférence ; prédéfinies pour inclure les extensions suivantes : .exe .obj .asm .c .cpp .cxx .bas .cbl .pour .pas .res .rc .f .f90|

Pour modifier le **. SUFFIXES** liste commande ou pour spécifier une nouvelle liste, effacer la liste et spécifiez un nouveau paramètre. Pour effacer la liste, ne spécifiez aucune extension après le signe deux-points :

```
.SUFFIXES :
```

Pour ajouter des suffixes supplémentaires à la fin de la liste, spécifiez

```
.SUFFIXES : suffixlist
```

où *suffixlist* est une liste de suffixes supplémentaires, séparés par un ou plusieurs espaces ou des tabulations. Pour afficher le paramètre actuel de **. SUFFIXES**, exécutez NMAKE avec /P.

## <a name="see-also"></a>Voir aussi

[NMAKE, référence](../build/nmake-reference.md)