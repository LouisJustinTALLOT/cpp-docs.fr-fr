---
description: 'En savoir plus sur : directives de l’assembleur ARM'
title: Directive d'assembleur ARM
ms.date: 08/30/2018
ms.assetid: 9cfa8896-ec10-4e77-855a-3135c40d7d2a
ms.openlocfilehash: 8362453f2113922c5e834d1d68583b4199cf8d4c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97118116"
---
# <a name="arm-assembler-directives"></a>Directive d'assembleur ARM

Pour l’essentiel, l’assembleur Microsoft ARM utilise le langage d’assembly ARM, qui est documenté dans le [Guide de référence Armasm du compilateur ARM](http://infocenter.arm.com/help/topic/com.arm.doc.dui0802b/index.html). Toutefois, les implémentations Microsoft de certaines directives d’assembly diffèrent des directives d’assembly ARM. Cet article explique les différences.

## <a name="microsoft-implementations-of-arm-assembly-directives"></a>Implémentations Microsoft des directives d’assembly ARM

- PARTIE

   L’assembleur Microsoft ARM prend en charge les `AREA` attributs suivants : `ALIGN` , `CODE` , `CODEALIGN` , `DATA` , `NOINIT` , `READONLY` , `READWRITE` , `THUMB` , `ARM` .

   Tout sauf `THUMB` et `ARM` fonctionne comme décrit dans le [Guide de référence Armasm du compilateur ARM](http://infocenter.arm.com/help/topic/com.arm.doc.dui0802b/index.html).

   Dans l’assembleur Microsoft ARM, `THUMB` indique qu’une `CODE` section contient du code Thumb et est la valeur par défaut pour les `CODE` sections.  `ARM` indique que la section contient du code ARM.

- AVERTISSEMENT

   Non pris en charge.

- CODE16

   Non pris en charge, car il implique une syntaxe de curseur de défilement, que l’assembleur Microsoft ARM n’autorise pas.  Utilisez la `THUMB` directive à la place, ainsi que la syntaxe de la journalisation des utilisation.

- CLASSIQUES

   La spécification d’un alignement pour la région commune n’est pas prise en charge.

- DCDO

   Non pris en charge.

- `DN`, `QN`, `SN`

   La spécification d’un type ou d’un couloir sur l’alias Register n’est pas prise en charge.

- ENTRY

   Non pris en charge.

- EQU

   La spécification d’un type pour le symbole défini n’est pas prise en charge.

- `EXPORT` et `GLOBAL`

   Spécifie les exportations à l’aide de la syntaxe suivante :

   > **Exporter** |  <em>Sym</em>global {**[**<em>type</em>**]**}

   *sym* est le symbole à exporter.  [*type*], s’il est spécifié, peut être `[DATA]` pour indiquer que le symbole pointe vers les données ou `[FUNC]` pour indiquer que le symbole pointe vers le code. `GLOBAL` est un synonyme de `EXPORT`.

- Exportas

   Non pris en charge.

- FRAME

   Non pris en charge.

- `FUNCTION` et `PROC`

   Bien que la syntaxe d’assembly prenne en charge la spécification d’une convention d’appel personnalisée sur les procédures en répertoriant les registres qui sont l’appelant-Save et ceux qui sont appelés-Save, l’assembleur Microsoft ARM accepte la syntaxe mais ignore les listes de registres.  Les informations de débogage produites par l’assembleur ne prennent en charge que la Convention d’appel par défaut.

- `IMPORT` et `EXTERN`

   Spécifie les importations à l’aide de la syntaxe suivante :

   > **Importer** | **Extern** *sym*{**, faible** *alias*{**, type** *t*}}

   *sym* est le nom du symbole à importer.

   Si `WEAK` *alias* est spécifié, il indique que *sym* est un externe faible. Si aucune définition n’est trouvée au moment de la liaison, toutes les références à ce dernier sont liées au lieu d’un *alias*.

   Si `TYPE` *t* est spécifié, *t* indique comment l’éditeur de liens doit tenter de résoudre *sym*.  Ces valeurs pour *t* sont possibles :

   |Valeur|Description|
   |-|-|
   |1|Ne pas effectuer de recherche de bibliothèque pour *sym*|
   |2|Effectuer une recherche de bibliothèque *sym*|
   |3|*sym* est un alias pour l' *alias* (valeur par défaut)|

   `EXTERN` est un synonyme de `IMPORT` , sauf que *sym* est importé uniquement s’il existe des références à celui-ci dans l’assembly actuel.

- MACRO

   L’utilisation d’une variable pour contenir le code de condition d’une macro n’est pas prise en charge. Les valeurs par défaut des paramètres de macro ne sont pas prises en charge.

- NOFP

   Non pris en charge.

- `OPT`, `TTL`, `SUBT`

   Non pris en charge, car l’assembleur Microsoft ARM ne produit pas de listes.

- PRESERVE8

   Non pris en charge.

- RELOC

   `RELOC n` peut uniquement suivre une instruction ou une directive de définition de données. Il n’y a aucun « symbole anonyme » qui peut être déplacé.

- IMPOSANT

   Non pris en charge.

- REQUIRE8

   Non pris en charge.

- THUMBX

   Non pris en charge, car l’assembleur Microsoft ARM ne prend pas en charge le jeu d’instructions Thumb-2EE.

## <a name="see-also"></a>Voir aussi

[Référence Command-Line assembly ARM](../../assembler/arm/arm-assembler-command-line-reference.md)<br/>
[Messages de diagnostic de l’assembleur ARM](../../assembler/arm/arm-assembler-diagnostic-messages.md)<br/>
