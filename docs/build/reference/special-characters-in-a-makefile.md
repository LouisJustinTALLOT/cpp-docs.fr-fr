---
description: 'En savoir plus sur : caractères spéciaux dans un Makefile'
title: Caractères spéciaux dans un makefile
ms.date: 11/04/2016
helpviewer_keywords:
- NMAKE program, special characters
- makefiles, special characters
- special characters, in NMAKE macros
- macros, special characters
ms.assetid: 92c34ab5-ca6b-4fc0-bcf4-3172eaeda9f0
ms.openlocfilehash: 22b8f6dd82191c88a23eaf1dabb551d468293a42
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97224671"
---
# <a name="special-characters-in-a-makefile"></a>Caractères spéciaux dans un makefile

Pour utiliser un caractère spécial NMAKE comme caractère littéral, placez le signe insertion (^) devant. NMAKE ignore les signes d’insertion qui précèdent les autres caractères. Les caractères spéciaux ont les suivants :

`:  ;  #  (  )  $  ^  \  {  }  !  @  —`

Le signe insertion (^) dans une chaîne entre guillemets est traité comme un caractère de signe insertion littéral. Un signe insertion à la fin d’une ligne insère un caractère de saut de ligne littéral dans une chaîne ou une macro.

Dans les macros, une barre oblique inverse ( \\ ) suivie d’un caractère de saut de ligne est remplacée par un espace.

Dans les commandes, symbole de pourcentage (%) est un spécificateur de fichier. Pour représenter% littéralement dans une commande, spécifiez un signe de pourcentage double (%%) au lieu d’un seul. Dans d’autres situations, NMAKE interprète un seul% littéralement, mais interprète toujours un double%% comme un% unique. Par conséquent, pour représenter un littéral%%, spécifiez soit trois signes de pourcentage, soit%%%, soit quatre signes de pourcentage,%%%%.

Pour utiliser le signe dollar ($) comme caractère littéral dans une commande, spécifiez deux signes dollar ($ $). Cette méthode peut également être utilisée dans d’autres situations où ^ $ fonctionne.

## <a name="see-also"></a>Voir aussi

[Contenu d’un Makefile](contents-of-a-makefile.md)
