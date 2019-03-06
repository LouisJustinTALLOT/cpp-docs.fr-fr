---
title: Caractères spéciaux dans un makefile
ms.date: 11/04/2016
helpviewer_keywords:
- NMAKE program, special characters
- makefiles, special characters
- special characters, in NMAKE macros
- macros, special characters
ms.assetid: 92c34ab5-ca6b-4fc0-bcf4-3172eaeda9f0
ms.openlocfilehash: e2703adbbdba392b1a317e2656c6f3dba30a36b6
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57420752"
---
# <a name="special-characters-in-a-makefile"></a>Caractères spéciaux dans un makefile

Pour utiliser un caractère spécial NMAKE comme un caractère littéral, placez un accent circonflexe (^) placés devant lui. NMAKE ignore les signes qui précèdent les autres caractères. Les caractères spéciaux sont :

`:  ;  #  (  )  $  ^  \  {  }  !  @  —`

Un accent circonflexe (^) dans une chaîne entre guillemets est traité comme un caractère de signe insertion littéral. Un point d’insertion à la fin d’une ligne insère un caractère de saut de ligne littéral dans une chaîne ou une macro.

Dans les macros, une barre oblique inverse (\\) suivi par un saut de ligne est remplacé par un espace.

Dans les commandes, un symbole de pourcentage (%) est un spécificateur de fichier. Pour représenter % littéralement dans une commande, spécifiez un double signe de pourcentage (%) à la place d’un seul d'entre eux. Dans d’autres situations, NMAKE interprète % seul littéralement, mais il interprète toujours un double %% comme % unique. Par conséquent, pour représenter un littéral %%, spécifiez soit trois signes de pourcentage %%%, ou des quatre signes de pourcentage, %%%.

Pour utiliser le symbole dollar ($) comme un caractère littéral dans une commande, spécifiez deux signes dollar ($$). Cette méthode peut également être utilisée dans d’autres situations où ^ $ fonctionne.

## <a name="see-also"></a>Voir aussi

[Contenu d’un makefile](../build/contents-of-a-makefile.md)
