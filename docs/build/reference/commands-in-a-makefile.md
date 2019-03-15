---
title: Commandes dans un makefile
ms.date: 11/04/2016
helpviewer_keywords:
- commands, makefiles
ms.assetid: 8085517e-42f4-493b-b8f8-44311fc08c64
ms.openlocfilehash: fcb8737070931cf95d7bfb3971a84e22c7ad70a4
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2019
ms.locfileid: "57825329"
---
# <a name="commands-in-a-makefile"></a>Commandes dans un makefile

Une règle de bloc ou d’inférence description Spécifie un bloc de commandes à exécuter si la dépendance est obsolète. NMAKE affiche chaque commande avant de l’exécuter, sauf si /S, **. En mode silencieux**, **! CMDSWITCHES**, ou \@ est utilisé. NMAKE recherche une règle d’inférence correspondante si un bloc de description n’est pas suivi d’un bloc de commandes.

Un bloc de commandes contient une ou plusieurs commandes, chacun sur sa propre ligne. Aucune ligne vide ne peut apparaître entre la dépendance ou une règle et le bloc de commandes. Toutefois, une ligne contenant uniquement des espaces ou des tabulations peut apparaître. Cette ligne est interprétée comme une commande null, et aucune erreur ne se produit. Lignes vides sont autorisées entre les lignes de commande.

Une ligne de commande commence par un ou plusieurs espaces ou des tabulations. Une barre oblique inverse (\) suivie d’un caractère de saut de ligne est interprétée comme un espace dans la commande ; utiliser une barre oblique inverse à la fin d’une ligne pour continuer une commande sur la ligne suivante. NMAKE interprète la barre oblique inverse littéralement si tout autre caractère, y compris un espace ou une tabulation, suit la barre oblique inverse.

Une commande précédé par un point-virgule ( ;) peut apparaître sur une règle de ligne ou de l’inférence de dépendance, si un bloc de commandes :

```
project.obj : project.c project.h ; cl /c project.c
```

## <a name="what-do-you-want-to-know-more-about"></a>Sur quels éléments souhaitez-vous obtenir des informations supplémentaires ?

[Modificateurs de commandes](command-modifiers.md)

[Syntaxe de parties de nom de fichier](filename-parts-syntax.md)

[Fichiers inline dans un makefile](inline-files-in-a-makefile.md)

## <a name="see-also"></a>Voir aussi

[NMAKE, référence](nmake-reference.md)