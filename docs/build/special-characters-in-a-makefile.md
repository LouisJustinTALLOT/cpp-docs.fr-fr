---
title: Caractères spéciaux dans un Makefile | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- NMAKE program, special characters
- makefiles, special characters
- special characters, in NMAKE macros
- macros, special characters
ms.assetid: 92c34ab5-ca6b-4fc0-bcf4-3172eaeda9f0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 157f9ed499ef7a0ac9efdd6bebe118ca593acabb
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32380449"
---
# <a name="special-characters-in-a-makefile"></a>Caractères spéciaux dans un makefile
Pour utiliser un caractère spécial NMAKE comme un caractère littéral, placez un point d’insertion (^) placés devant lui. NMAKE ignore les signes qui précèdent les autres caractères. Les caractères spéciaux sont :  
  
 `:  ;  #  (  )  $  ^  \  {  }  !  @  —`  
  
 Un caret (^) dans une chaîne entre guillemets est traité comme un caractère littéral signe insertion. Un point d’insertion à la fin d’une ligne insère un caractère de saut de ligne littéral dans une chaîne ou une macro.  
  
 Dans les macros, une barre oblique inverse (\\) suivi par un saut de ligne est remplacé par un espace.  
  
 Dans les commandes, un symbole de pourcentage (%) est un spécificateur de fichier. Pour représenter % littéralement dans une commande, spécifiez un double signe de pourcentage (%) à la place d’un seul. Dans d’autres situations, NMAKE interprète % seul littéralement, mais il interprète toujours un double %% comme % unique. Par conséquent, pour représenter un littéral %%, spécifiez soit trois signes de pourcentage %%%, ou quatre signes de pourcentage %%%.  
  
 Pour utiliser le symbole dollar ($) comme un caractère littéral dans une commande, spécifiez deux signes dollar ($$). Cette méthode peut également être utilisée dans d’autres situations où ^ $ fonctionne.  
  
## <a name="see-also"></a>Voir aussi  
 [Contenu d’un makefile](../build/contents-of-a-makefile.md)