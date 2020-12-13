---
description: 'En savoir plus sur : directives de prétraitement d’un Makefile'
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
ms.openlocfilehash: 7c394e3547044be661fea5a8ec86f05a3b93e967
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97138070"
---
# <a name="makefile-preprocessing-directives"></a>Directives de prétraitement d'un makefile

Les directives de prétraitement ne respectent pas la casse. Le point d’exclamation initial ( !) doit apparaître au début de la ligne. Zéro, un ou plusieurs espaces ou tabulations peuvent apparaître après le point d’exclamation, pour la mise en retrait.

- `!CMDSWITCHES``+`Option { `-` &#124; }...

   Active ou désactive chaque *option* . Les espaces et les tabulations doivent apparaître avant l' `+` `-` opérateur or ; aucun ne peut apparaître entre l’opérateur et les [lettres d’option](running-nmake.md#nmake-options). Les lettres ne respectent pas la casse et sont spécifiées sans barre oblique ( `/` ). Pour activer certaines options et désactiver d’autres, utilisez des spécifications distinctes de `!CMDSWITCHES` .

   Seuls/D,/I,/N et/S peuvent être utilisés dans un Makefile. Dans Tools.ini, toutes les options sont autorisées, à l’exception de/F,/HELP,/NOLOGO,/X et/ ?. Les modifications spécifiées dans un bloc de description ne prennent pas effet avant le bloc de description suivant. Cette directive met à jour **MAKEFLAGS**; les modifications sont héritées pendant la récursivité si **MAKEFLAGS** est spécifié.

- `!ERROR`*texte*

   Affiche le *texte* dans l’erreur NMAKE U1050, puis arrête NMAKE, même si/K,/i, `.IGNORE` , `!CMDSWITCHES` ou le modificateur de commande Dash ( `-` ) est utilisé. Les espaces ou les tabulations avant le *texte* sont ignorés.

- `!MESSAGE`*texte*

   Affiche le *texte* vers la sortie standard. Les espaces ou les tabulations avant le *texte* sont ignorés.

- `!INCLUDE` [ `<` ] *nom de fichier* [ `>` ]

   Lit le *nom de fichier* en tant que Makefile, puis continue avec le Makefile en cours. NMAKE recherche d’abord le *nom de fichier* dans le répertoire spécifié ou actif, puis de manière récursive dans les répertoires des makefiles parents, puis, si *filename* est placé entre crochets pointus ( `< >` ), dans les répertoires spécifiés par la macro **include** , qui est initialement définie sur la variable d’environnement include. Utile pour passer des `.SUFFIXES` paramètres, `.PRECIOUS` , et des règles d’inférence à des makefiles récursifs.

- `!IF` *constant_expression*

   Traite les instructions entre `!IF` et le suivant `!ELSE` ou `!ENDIF` si *constant_expression* prend une valeur différente de zéro.

- `!IFDEF` *nom_macro*

   Traite les instructions entre `!IFDEF` et le suivant `!ELSE` ou `!ENDIF` si *macroname* est défini. Une macro null est considérée comme étant définie.

- `!IFNDEF` *nom_macro*

   Traite les instructions entre `!IFNDEF` et le suivant `!ELSE` ou `!ENDIF` si *nommacro* n’est pas défini.

- `!ELSE` [ `IF` *constant_expression* &#124; `IFDEF` *nommacro* &#124; `IFNDEF` *nommacro*]

   Traite les instructions entre `!ELSE` et la Next `!ENDIF` si l' `!IF` instruction précédente, `!IFDEF` ou a évalué la `!IFNDEF` valeur zéro. Les mots clés facultatifs permettent de mieux contrôler le prétraitement.

- `!ELSEIF`

   Synonyme de `!ELSE IF`.

- `!ELSEIFDEF`

   Synonyme de `!ELSE IFDEF`.

- `!ELSEIFNDEF`

   Synonyme de `!ELSE IFNDEF`.

- `!ENDIF`

   Marque la fin d’un `!IF` `!IFDEF` bloc, ou `!IFNDEF` . Tout texte situé après `!ENDIF` sur la même ligne est ignoré.

- `!UNDEF` *nom_macro*

   Annule la définition de *nommacro*.

## <a name="see-also"></a>Voir aussi

- [Prétraitement d’un Makefile](makefile-preprocessing.md)
