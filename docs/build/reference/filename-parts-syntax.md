---
description: 'En savoir plus sur : syntaxe de Filename-Parts'
title: Syntaxe des éléments d'un nom de fichier
ms.date: 11/04/2016
helpviewer_keywords:
- syntax, filename-parts
- filename-parts syntax in NMAKE
- NMAKE program, syntax
ms.assetid: 48fe38e0-3f3b-40e6-894c-330ee775a656
ms.openlocfilehash: 436481d52324b4c638b5fa0a9840ce0d9ef654f4
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97192133"
---
# <a name="filename-parts-syntax"></a>Syntaxe des éléments d'un nom de fichier

La syntaxe des parties de noms de fichier dans les commandes représente les composants du premier nom de fichier dépendant (qui peut être un dépendant implicite). Les composants de nom de fichier sont le lecteur, le chemin d’accès, le nom de base et l’extension du fichier, tels qu’ils sont spécifiés, et non sur le disque. Utilisez **% s** pour représenter le nom de fichier complet. Utilisez **% &#124;**[*parts*]**F** (un caractère de barre verticale suit le symbole de pourcentage) pour représenter les parties du nom de fichier, où les *parties* peuvent être zéro ou plusieurs des lettres suivantes, dans n’importe quel ordre.

|Lettre|Description|
|------------|-----------------|
|Aucune lettre|Nom complet (identique à **% s**)|
|**d**|Lecteur|
|**p**|Path|
|**f**|Nom de base du fichier|
|**Envoyer**|Extension de fichier|

Par exemple, si le nom de fichier est c:\prog.exe :

- % s sera c:\prog.exe

- % &#124;F sera c:\prog.exe

- % &#124;dF sera c

- % &#124;pF sera c:\

- % &#124;fF sera Prog

- % &#124;eF sera exe

## <a name="see-also"></a>Voir aussi

[Commandes dans un Makefile](commands-in-a-makefile.md)
