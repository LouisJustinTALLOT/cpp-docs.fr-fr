---
description: En savoir plus sur les commandes suivantes dans un Makefile
title: Commandes dans un makefile
ms.date: 11/04/2016
helpviewer_keywords:
- commands, makefiles
ms.assetid: 8085517e-42f4-493b-b8f8-44311fc08c64
ms.openlocfilehash: a4f3c6d3cc9b5d567548d7b3f2bd7679d492ebf0
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97179081"
---
# <a name="commands-in-a-makefile"></a>Commandes dans un makefile

Un bloc de description ou une règle d’inférence spécifie un bloc de commandes à exécuter si la dépendance est obsolète. NMAKE affiche chaque commande avant de l’exécuter, sauf si/S, **. SILENT**, **! CMDSWITCHES**, ou \@ est utilisé. NMAKE recherche une règle d’inférence correspondante si un bloc de description n’est pas suivi d’un bloc de commandes.

Un bloc de commandes contient une ou plusieurs commandes, chacune sur sa propre ligne. Aucune ligne vide ne peut apparaître entre la dépendance ou la règle et le bloc de commandes. Toutefois, une ligne contenant uniquement des espaces ou des tabulations peut apparaître ; Cette ligne est interprétée comme une commande null et aucune erreur ne se produit. Les lignes vides sont autorisées entre les lignes de commande.

Une ligne de commande commence par un ou plusieurs espaces ou tabulations. Une barre oblique inverse (\) suivie d’un caractère de saut de ligne est interprétée comme un espace dans la commande ; Utilisez une barre oblique inverse à la fin d’une ligne pour continuer une commande sur la ligne suivante. NMAKE interprète la barre oblique inverse littéralement si tout autre caractère, y compris un espace ou un onglet, suit la barre oblique inverse.

Commande précédée d’un point-virgule (;) peut apparaître sur une ligne de dépendance ou une règle d’inférence, qu’il s’agisse ou non d’un bloc de commandes :

```
project.obj : project.c project.h ; cl /c project.c
```

## <a name="what-do-you-want-to-know-more-about"></a>Sur quels éléments souhaitez-vous obtenir des informations supplémentaires ?

[Modificateurs de commandes](command-modifiers.md)

[Syntaxe des éléments d’un nom de fichier](filename-parts-syntax.md)

[Fichiers inline dans un makefile](inline-files-in-a-makefile.md)

## <a name="see-also"></a>Voir aussi

[Référence NMAKE](nmake-reference.md)
