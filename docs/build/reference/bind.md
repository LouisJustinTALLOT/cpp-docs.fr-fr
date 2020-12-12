---
description: En savoir plus sur:/BIND
title: /BIND
ms.date: 11/04/2016
f1_keywords:
- /bind
helpviewer_keywords:
- -BIND editbin option
- entry points, addresses
- BIND editbin option
- entry points
- /BIND editbin option
- import address table
ms.assetid: 3772b330-1868-4c90-857d-c31faa867982
ms.openlocfilehash: 87ea0265555991fca019760feec4395692c074ae
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97187141"
---
# <a name="bind"></a>/BIND

```
/BIND[:PATH=path]
```

## <a name="remarks"></a>Notes

Cette option définit les adresses des points d’entrée de la table d’adresses d’importation pour un fichier exécutable ou une DLL. Utilisez cette option pour réduire le temps de chargement d’un programme.

Spécifiez le fichier exécutable et les dll du programme dans l’argument *Files* sur la ligne de commande EDITBIN. L’argument facultatif *path* de/bind spécifie l’emplacement des DLL utilisées par les fichiers spécifiés. Séparez plusieurs répertoires par un point-virgule (**;**). Si *path* n’est pas spécifié, EDITBIN recherche les répertoires spécifiés dans la variable d’environnement PATH. Si *path* est spécifié, EDITBIN ignore la variable PATH.

Par défaut, le chargeur de programme définit les adresses des points d’entrée lorsqu’il charge un programme. La durée de ce processus varie selon le nombre de dll et le nombre de points d’entrée référencés dans le programme. Si un programme a été modifié avec/BIND et que les adresses de base du fichier exécutable et de ses dll ne sont pas en conflit avec les dll qui sont déjà chargées, le système d’exploitation n’a pas besoin de définir ces adresses. Dans le cas où les fichiers sont incorrectement basés, le système d’exploitation déplace les dll du programme et recalcule les adresses de point d’entrée, ce qui ajoute au temps de chargement du programme.

## <a name="see-also"></a>Voir aussi

[Options EDITBIN](editbin-options.md)
