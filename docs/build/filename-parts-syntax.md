---
title: Syntaxe des éléments d'un nom de fichier
ms.date: 11/04/2016
helpviewer_keywords:
- syntax, filename-parts
- filename-parts syntax in NMAKE
- NMAKE program, syntax
ms.assetid: 48fe38e0-3f3b-40e6-894c-330ee775a656
ms.openlocfilehash: 89869ccaea2a9a5c3d16762fe49b72efc462e0ee
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50552046"
---
# <a name="filename-parts-syntax"></a>Syntaxe des éléments d'un nom de fichier

Syntaxe de parties de nom de fichier dans les commandes représente les composants du nom de fichier dépendant première (qui peut être un dépendant implicite). Composants de nom de fichier sont lecteur, chemin d’accès, nom de base et extension tel que spécifié, le fichier pas telle qu’elle existe sur le disque. Utilisez **%s** pour représenter le nom de fichier complet. Utilisez **%&#124;**[*parties*]**F** (une barre verticale caractère suit le symbole de pourcentage) pour représenter les parties du nom de fichier, où *parties*peut être zéro ou plusieurs des lettres suivantes, dans n’importe quel ordre.

|Lettre|Description|
|------------|-----------------|
|Aucune lettre|Nom complet (identique à **%s**)|
|**d**|Lecteur|
|**p**|Chemin d’accès|
|**f**|Nom de base de fichier|
|**e**|Extension de fichier|

Par exemple, si le nom de fichier est c:\prog.exe :

- %s sera c:\prog.exe

- %&#124;F sera c:\prog.exe

- %&#124;dF sera c

- %&#124;pF sera c:\

- %&#124;fF sera prog

- %&#124;eF à exe

## <a name="see-also"></a>Voir aussi

[Commandes dans un makefile](../build/commands-in-a-makefile.md)