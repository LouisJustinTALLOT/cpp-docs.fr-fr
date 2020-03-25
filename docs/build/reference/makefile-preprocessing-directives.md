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
ms.openlocfilehash: 1dd30c8e338343626d8a8cc3157d118e44f0ea18
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80170486"
---
# <a name="makefile-preprocessing-directives"></a>Directives de prétraitement d'un makefile

Les directives de prétraitement ne respectent pas la casse. Le point d’exclamation initial ( !) doit apparaître au début de la ligne. Zéro, un ou plusieurs espaces ou tabulations peuvent apparaître après le point d’exclamation, pour la mise en retrait.

- `!CMDSWITCHES` l' &#124; *option* {`+` `-`}...

   Active ou désactive chaque *option* . Des espaces ou des tabulations doivent apparaître avant l’opérateur `+` ou `-` ; aucun ne peut apparaître entre l’opérateur et les [lettres d’option](running-nmake.md#nmake-options). Les lettres ne respectent pas la casse et sont spécifiées sans barre oblique (`/`). Pour activer certaines options et désactiver d’autres, utilisez des spécifications distinctes de `!CMDSWITCHES`.

   Seuls/D,/I,/N et/S peuvent être utilisés dans un Makefile. Dans Tools. ini, toutes les options sont autorisées, à l’exception de/F,/HELP,/NOLOGO,/X et/ ?. Les modifications spécifiées dans un bloc de description ne prennent pas effet avant le bloc de description suivant. Cette directive met à jour **MAKEFLAGS**; les modifications sont héritées pendant la récursivité si **MAKEFLAGS** est spécifié.

- *texte* `!ERROR`

   Affiche le *texte* dans l’erreur NMAKE U1050, puis arrête NMAKE, même si le modificateur de commande/K,/i, `.IGNORE`, `!CMDSWITCHES`ou dash (`-`) est utilisé. Les espaces ou les tabulations avant le *texte* sont ignorés.

- *texte* `!MESSAGE`

   Affiche le *texte* vers la sortie standard. Les espaces ou les tabulations avant le *texte* sont ignorés.

- `!INCLUDE` [`<`] *nom de fichier* [`>`]

   Lit le *nom de fichier* en tant que Makefile, puis continue avec le Makefile en cours. NMAKE recherche d’abord le *nom de fichier* dans le répertoire spécifié ou actif, puis de manière récursive dans les répertoires des makefiles parents, puis, si *filename* est placé entre crochets pointus (`< >`), dans les répertoires spécifiés par la macro **include** , qui est initialement définie sur la variable d’environnement include. Utile pour passer les paramètres de `.SUFFIXES`, `.PRECIOUS`et les règles d’inférence aux makefiles récursifs.

- `!IF` *constant_expression*

   Traite les instructions entre les `!IF` et les `!ELSE` ou `!ENDIF` suivants si *constant_expression* prend une valeur différente de zéro.

- `!IFDEF` *nommacro*

   Traite les instructions entre `!IFDEF` et les `!ELSE` ou `!ENDIF` suivants si *macroname* est défini. Une macro null est considérée comme étant définie.

- `!IFNDEF` *nommacro*

   Traite les instructions entre `!IFNDEF` et le `!ELSE` ou `!ENDIF` suivant si *nommacro* n’est pas défini.

- `!ELSE` [`IF` *constant_expression* &#124; `IFDEF` *nommacro* &#124; `IFNDEF` *nommacro*]

   Traite les instructions entre `!ELSE` et la `!ENDIF` suivante si l’instruction `!IF`, `!IFDEF`ou `!IFNDEF` précédente a évalué la valeur zéro. Les mots clés facultatifs permettent de mieux contrôler le prétraitement.

- `!ELSEIF`

   Synonyme de `!ELSE IF`.

- `!ELSEIFDEF`

   Synonyme de `!ELSE IFDEF`.

- `!ELSEIFNDEF`

   Synonyme de `!ELSE IFNDEF`.

- `!ENDIF`

   Marque la fin d’un bloc `!IF`, `!IFDEF`ou `!IFNDEF`. Tout texte situé après `!ENDIF` sur la même ligne est ignoré.

- `!UNDEF` *nommacro*

   Annule la définition de *nommacro*.

## <a name="see-also"></a>Voir aussi

- [Prétraitement d’un makefile](makefile-preprocessing.md)
