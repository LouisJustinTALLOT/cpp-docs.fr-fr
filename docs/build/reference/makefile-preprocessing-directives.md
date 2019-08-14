---
title: Directives de prétraitement d'un makefile
ms.date: 08/11/2019
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
ms.openlocfilehash: 4825ca180cb1b419a9ffa5232575ba1a24f8805d
ms.sourcegitcommit: db1ed91fa7451ade91c3fb76bc7a2b857f8a5eef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/13/2019
ms.locfileid: "68980511"
---
# <a name="makefile-preprocessing-directives"></a>Directives de prétraitement d'un makefile

Les directives de prétraitement ne respectent pas la casse. Le point d’exclamation initial (!) doit apparaître au début de la ligne. Zéro, un ou plusieurs espaces ou tabulations peuvent apparaître après le point d’exclamation, pour la mise en retrait.

- `!CMDSWITCHES``+` *option* { &#124; }...`-`

   Active ou désactive chaque *option* . Les espaces et les tabulations doivent `+` apparaître `-` avant l’opérateur or; aucun ne peut apparaître entre l’opérateur et les [lettres d’option](running-nmake.md#nmake-options). Les lettres ne respectent pas la casse et sont spécifiées sans`/`barre oblique (). Pour activer certaines options et désactiver d’autres, utilisez des spécifications distinctes de `!CMDSWITCHES`.

   Seuls/D,/I,/N et/S peuvent être utilisés dans un Makefile. Dans Tools. ini, toutes les options sont autorisées, à l’exception de/F,/HELP,/NOLOGO,/X et/?. Les modifications spécifiées dans un bloc de description ne prennent pas effet avant le bloc de description suivant. Cette directive met à jour **MAKEFLAGS**; les modifications sont héritées pendant la récursivité si **MAKEFLAGS** est spécifié.

- `!ERROR`*texte*

   Affiche le *texte* dans l’erreur NMAKE U1050, puis arrête NMAKE, même si/k,/i `.IGNORE`, `!CMDSWITCHES`, ou le modificateur`-`de commande Dash () est utilisé. Les espaces ou les tabulations avant le *texte* sont ignorés.

- `!MESSAGE`*texte*

   Affiche le *texte* vers la sortie standard. Les espaces ou les tabulations avant le *texte* sont ignorés.

- `!INCLUDE`[ `<` ] *nom* de `>` fichier []

   Lit le *nom de fichier* en tant que Makefile, puis continue avec le Makefile en cours. NMAKE recherche d’abord le *nom de fichier* dans le répertoire spécifié ou actif, puis de manière récursive dans les répertoires des makefiles parents, puis, si le nom de`< >` *fichier* est placé entre crochets pointus (), dans les répertoires spécifiés par le  **INCLUT** la macro, qui est initialement définie sur la variable d’environnement include. Utile pour passer `.SUFFIXES` des paramètres `.PRECIOUS`,, et des règles d’inférence à des makefiles récursifs.

- `!IF`*constant_expression*

   Traite les instructions `!IF` entre et le `!ELSE` suivant `!ENDIF` ou si *constant_expression* prend une valeur différente de zéro.

- `!IFDEF`*nommacro*

   Traite les instructions `!IFDEF` entre et le `!ELSE` suivant `!ENDIF` ou si *macroname* est défini. Une macro null est considérée comme étant définie.

- `!IFNDEF`*nommacro*

   Traite les instructions `!IFNDEF` entre et le `!ELSE` suivant `!ENDIF` ou si *nommacro* n’est pas défini.

- `!ELSE`[`IF` &#124; *constant_expression* &#124; *nommacro* nommacro] `IFDEF` `IFNDEF`

   Traite les instructions `!ELSE` entre et la `!ENDIF` Next si l' `!IF`instruction `!IFDEF`précédente, `!IFNDEF` ou a évalué la valeur zéro. Les mots clés facultatifs permettent de mieux contrôler le prétraitement.

- `!ELSEIF`

   Synonyme de `!ELSE IF`.

- `!ELSEIFDEF`

   Synonyme de `!ELSE IFDEF`.

- `!ELSEIFNDEF`

   Synonyme de `!ELSE IFNDEF`.

- `!ENDIF`

   Marque la fin d’un `!IF`bloc `!IFDEF`, ou `!IFNDEF` . Tout texte situé `!ENDIF` après sur la même ligne est ignoré.

- `!UNDEF`*nommacro*

   Annule la définition de *nommacro*.

## <a name="see-also"></a>Voir aussi

- [Prétraitement d’un makefile](makefile-preprocessing.md)