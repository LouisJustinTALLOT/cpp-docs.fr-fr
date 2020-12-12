---
description: 'En savoir plus sur les directives : dot'
title: Directives précédées par un point
ms.date: 11/04/2016
helpviewer_keywords:
- NMAKE program, dot directives
- dot directives in NMAKE
ms.assetid: ab35da65-30b6-48b7-87d6-61503d7faf9f
ms.openlocfilehash: 41b13d5f0f0f0a04ee47a9958be76c384617fe5f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97192861"
---
# <a name="dot-directives"></a>Directives précédées par un point

Spécifiez des directives point à l’extérieur d’un bloc de description, au début d’une ligne. Les directives dot commencent par un point (. ) et sont suivies d’un signe deux-points ( :). Les espaces et les tabulations sont autorisés. Les noms de directives dot respectent la casse et sont en majuscules.

|Directive|Objectif|
|---------------|-------------|
|**. TENIR**|Ignore les codes de sortie non nuls retournés par les commandes, à partir du lieu où ils sont spécifiés jusqu’à la fin du Makefile. Par défaut, NMAKE s’arrête si une commande retourne un code de sortie différent de zéro. Pour restaurer la vérification des erreurs, utilisez **! CMDSWITCHES**. Pour ignorer le code de sortie d’une commande unique, utilisez le modificateur Dash (-). Pour ignorer les codes de sortie pour un fichier entier, utilisez/I.|
|**. PRÉCIEUX :** *cibles*|Conserve les *cibles* sur le disque si les commandes pour les mettre à jour sont arrêtées ; n’a aucun effet si une commande gère une interruption en supprimant le fichier. Séparez les noms cibles par un ou plusieurs espaces ou tabulations. Par défaut, NMAKE supprime une cible si une build est interrompue par CTRL + C ou CTRL + ATTN. Chaque utilisation de **. PRÉCIEUX** s’applique à l’ensemble du Makefile ; plusieurs spécifications sont cumulatives.|
|**. SANS assistance**|Supprime l’affichage des commandes exécutées, à partir de l’emplacement où elles sont spécifiées jusqu’à la fin du Makefile. Par défaut, NMAKE affiche les commandes qu’il appelle. Pour restaurer l’écho, utilisez **! CMDSWITCHES**. Pour supprimer l’écho d’une seule commande, utilisez le **@** modificateur. Pour supprimer l’écho d’un fichier entier, utilisez/S.|
|**. SUFFIXes :**`list`|Répertorie les extensions pour l’inférence-correspondance de règle ; prédéfini pour inclure les extensions suivantes :. exe. obj. asm. c. cpp. cxx. bas. CBL. for. Pro. res. rc. f. F90|

Pour modifier le **. Liste des SUFFIXes** ou pour spécifier une nouvelle liste, désactivez la liste et spécifiez un nouveau paramètre. Pour effacer la liste, ne spécifiez aucune extension après le signe deux-points :

```
.SUFFIXES :
```

Pour ajouter des suffixes supplémentaires à la fin de la liste, spécifiez

```
.SUFFIXES : suffixlist
```

où *suffixlist* est une liste des suffixes supplémentaires, séparés par un ou plusieurs espaces ou tabulations. Pour afficher la valeur actuelle de **. SUFFIXes**, exécuter NMAKE avec/p.

## <a name="see-also"></a>Voir aussi

[Référence NMAKE](nmake-reference.md)
