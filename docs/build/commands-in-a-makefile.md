---
title: Commandes dans un Makefile | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: commands, makefiles
ms.assetid: 8085517e-42f4-493b-b8f8-44311fc08c64
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 5361012fd388f49d8eb956ec1a4fa1bdd53a2dcc
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="commands-in-a-makefile"></a>Commandes dans un makefile
Une règle de bloc ou l’inférence de description Spécifie un bloc de commandes à exécuter si la dépendance est obsolète. NMAKE affiche chaque commande avant de l’exécuter, sauf si/s, **. En mode silencieux**, **! CMDSWITCHES**, ou @ n’est pas utilisé. NMAKE recherche une règle d’inférence correspondante si un bloc de description n’est pas suivi d’un bloc de commandes.  
  
 Un bloc de commandes contient une ou plusieurs commandes, chacune sur sa propre ligne. Aucune ligne vide ne peut apparaître entre la dépendance ou la règle et le bloc de commandes. Toutefois, une ligne contenant uniquement des espaces ou des tabulations peut apparaître. Cette ligne est interprétée comme une commande null, et aucune erreur ne se produit. Lignes vides sont autorisées entre les lignes de commande.  
  
 Une ligne de commande commence par un ou plusieurs des espaces ou des tabulations. Une barre oblique inverse (\) suivie d’un caractère de saut de ligne est interprétée comme un espace dans la commande ; Utilisez une barre oblique inverse à la fin d’une ligne pour continuer la commande sur la ligne suivante. NMAKE interprète la barre oblique inverse littéralement si n’importe quel autre caractère, y compris un espace ou une tabulation, suit la barre oblique inverse.  
  
 Une commande précédée par un point-virgule ( ;) peut apparaître sur une règle de ligne ou de l’inférence de dépendance, ou non un bloc de commandes :  
  
```  
project.obj : project.c project.h ; cl /c project.c  
```  
  
## <a name="what-do-you-want-to-know-more-about"></a>Sur quels éléments souhaitez-vous obtenir des informations supplémentaires ?  
 [Modificateurs de commandes](../build/command-modifiers.md)  
  
 [Syntaxe de parties de nom de fichier](../build/filename-parts-syntax.md)  
  
 [Fichiers inline dans un makefile](../build/inline-files-in-a-makefile.md)  
  
## <a name="see-also"></a>Voir aussi  
 [NMAKE, référence](../build/nmake-reference.md)