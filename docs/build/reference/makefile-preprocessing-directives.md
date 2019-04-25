---
title: Directives de prétraitement d'un makefile
ms.date: 06/14/2018
f1_keywords:
- '!UNDEF'
- '!INCLUDE'
- '!IFNDEF'
- '!MESSAGE'
helpviewer_keywords:
- ERROR directive
- '!MESSAGE directive'
- IF directive
- '!UNDEF directive'
- IFDEF directive
- '!ELSEIF directive'
- '!IFDEF directive'
- '!IF directive'
- UNDEF directive
- '!CMDSWITCHES directive'
- ENDIF directive
- directives, makefile preprocessing
- INCLUDE directive
- IFNDEF directive
- preprocessing directives, makefiles
- '!IFNDEF directive'
- ELSEIFNDEF directive
- NMAKE program, expressions
- ELSEIF directive
- '!ERROR directive'
- '!ENDIF directive'
- MESSAGE directive
- '!INCLUDE directive'
- '!ELSEIFNDEF directive'
- CMDSWITCHES directive
- '!ELSEIFDEF directive'
- '!ELSE directive'
- NMAKE program, preprocessor directives
- makefiles, preprocessing directives
- ELSE directive
- ELSEIFDEF directive
ms.assetid: bcedeccb-d981-469d-b9e8-ab5d097fd8c2
ms.openlocfilehash: 0945d0e1c149b7e1ab31b0dbbd5003f8b15a1e4d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62321557"
---
# <a name="makefile-preprocessing-directives"></a>Directives de prétraitement d'un makefile

Directives de prétraitement ne respectent pas la casse. Le point d’exclamation initial ( !) doit apparaître au début de la ligne. Zéro ou plusieurs espaces ou des tabulations peuvent apparaître après le point d’exclamation, pour la mise en retrait.

- **!CMDSWITCHES** {**+** &#124; **-**}*option* ...

   Transforme tous *option* répertoriés ou désactiver. Espaces ou des tabulations doivent apparaître avant le + ou - opérateur. aucun ne peut apparaître entre l’opérateur et la [option lettres](nmake-options.md). Des lettres ne sont pas sensible à la casse et sont spécifiés sans une barre oblique (/). Pour activer ou désactiver certaines options, utilisez des spécifications séparées de **! CMDSWITCHES**.

   /D uniquement, / I, /N et /S sont admises dans un makefile. Tools.ini, toutes les options sont autorisées à l’exception de /F, /HELP /NOLOGO, / X, et / ?. Modifications spécifiées dans un bloc de description ne prennent pas d’effet jusqu'à ce que le bloc de description suivant. Met à jour de cette directive **MAKEFLAGS**; les modifications sont héritées lors de la récursivité si **MAKEFLAGS** est spécifié.

- **!ERROR**  *text*

   Affiche *texte* dans l’erreur U1050, puis arrête NMAKE, même si /K, / I, **. Ignorer**, **! CMDSWITCHES**, ou le modificateur de commande tiret (-) est utilisé. Des espaces ou des onglets avant *texte* sont ignorés.

- **!MESSAGE**  *text*

   Affiche *texte* dans la sortie standard. Des espaces ou des onglets avant *texte* sont ignorés.

- **!INCLUDE** [ **\<** ] *filename* [ **>** ]

   Lit *filename* en tant que makefile, puis passe le makefile en cours. NMAKE recherche *filename* tout d’abord dans le répertoire spécifié ou en cours, puis de manière récursive dans les répertoires de n’importe quel parent makefiles, puis, si *filename* est mis entre crochets (\<>), dans les répertoires spécifiés par la **INCLUDE** macro, qui est initialement définie sur la variable d’environnement INCLUDE. Utile pour passer **. SUFFIXES** paramètres, **. PRÉCIEUX**et les règles d’inférence aux fichiers Make récursifs.

- **!IF** *constant_expression*

   Traite les instructions entre **! IF** et la prochaine **! AUTRE** ou **! ENDIF** si *constant_expression* prend une valeur différente de zéro.

- **!IFDEF**  *macroname*

   Traite les instructions entre **! IFDEF** et la prochaine **! AUTRE** ou **! ENDIF** si *nom_macro* est défini. Une macro null est considéré comme étant défini.

- **!IFNDEF**  *macroname*

   Traite les instructions entre **! IFNDEF** et la prochaine **! AUTRE** ou **! ENDIF** si *nom_macro* n’est pas défini.

- **!ELSE** [**IF** *constant_expression* &#124; **IFDEF** *macroname* &#124; **IFNDEF** *macroname*]

   Traite les instructions entre **! AUTRE** et la prochaine **! ENDIF** si l’accord préalable **! IF**, **! IFDEF**, ou **! IFNDEF** instruction évaluée à zéro. Les mots clés facultatifs donnent davantage de contrôle du prétraitement.

- **!ELSEIF**

   Synonyme de **! ELSE IF**.

- **!ELSEIFDEF**

   Synonyme de **! IFDEF ELSE**.

- **!ELSEIFNDEF**

   Synonyme de **! IFNDEF ELSE**.

- **!ENDIF**

   Marque la fin d’un **! IF**, **! IFDEF**, ou **! IFNDEF** bloc. N’importe quel texte qui suit **! ENDIF** sur la même ligne est ignoré.

- **!UNDEF**  *macroname*

   Annule la définition de *nom_macro*.

## <a name="see-also"></a>Voir aussi

- [Prétraitement d’un makefile](makefile-preprocessing.md)