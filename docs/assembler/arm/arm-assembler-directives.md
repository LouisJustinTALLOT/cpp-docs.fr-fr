---
title: Directive d’assembleur ARM | Microsoft Docs
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: reference
dev_langs:
- C++
ms.assetid: 9cfa8896-ec10-4e77-855a-3135c40d7d2a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5c37e010caa6c7cfb44ddaf2f7dd1e28bbb5c291
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45717702"
---
# <a name="arm-assembler-directives"></a>Directive d'assembleur ARM

La plupart du temps, l’assembleur Microsoft ARM utilise le langage d’assembly ARM, qui est décrite dans le [du compilateur ARM armasm Guide de référence](http://infocenter.arm.com/help/topic/com.arm.doc.dui0802b/index.html). Toutefois, les implémentations de Microsoft de certaines directives d’assembly diffèrent dans les directives d’assembly ARM. Cet article explique les différences.

## <a name="microsoft-implementations-of-arm-assembly-directives"></a>Implémentations de Microsoft de Directives d’Assembly ARM

- ZONE

   L’assembleur Microsoft ARM prend en charge ces `AREA` attributs : `ALIGN`, `CODE`, `CODEALIGN`, `DATA`, `NOINIT`, `READONLY`, `READWRITE`, `THUMB`, `ARM`.

   Tout sauf `THUMB` et `ARM` fonctionne comme décrit dans la [du compilateur ARM armasm Guide de référence](http://infocenter.arm.com/help/topic/com.arm.doc.dui0802b/index.html).

   Dans l’assembleur Microsoft ARM, `THUMB` indique qu’un `CODE` section contient du code Thumb et est la valeur par défaut pour `CODE` sections.  `ARM` Indique que la section contient le code d’ARM.

- ATTR

   Non pris en charge.

- CODE16

   Non pris en charge, car il implique la syntaxe de Thumb pre-UAL, l’assembleur Microsoft ARM n’autorise pas.  Utilisez la `THUMB` directive au lieu de cela, ainsi que de la syntaxe de la journalisation des accès utilisateur.

- COURANTES

   Spécification d’un alignement de la région commune n’est pas prise en charge.

- DCDO

   Non pris en charge.

- `DN`, `QN`, `SN`

   Spécification d’un type ou un couloir sur l’alias de Registre n’est pas pris en charge.

- ENTRÉE

   Non pris en charge.

- EQU

   Spécification d’un type pour le symbole défini n’est pas prise en charge.

- `EXPORT` et `GLOBAL`

   Spécifie des exportations à l’aide de cette syntaxe :

   > **Exporter**|**GLOBAL** <em>sym</em>{**[**<em>type</em>**]**}

   *SYM* est le symbole à exporter.  [*type*], si spécifiée, peut être `[DATA]` pour indiquer que le symbole pointe vers les données ou `[FUNC]` pour indiquer que le symbole pointe vers du code. `GLOBAL` est un synonyme de `EXPORT`.

- EXPORTAS

   Non pris en charge.

- FRAME

   Non pris en charge.

- `FUNCTION` et `PROC`

   Bien que la syntaxe de l’assembly prend en charge la spécification d’un personnalisé convention d’appel sur les procédures en répertoriant les registres sont enregistrer à l’appelant et celles qui sont appelé enregistrement, l’assembleur Microsoft ARM accepte la syntaxe, mais ignore les listes de Registre.  Les informations de débogage qui sont générées par l’assembleur prend en charge uniquement la valeur par défaut convention d’appel.

- `IMPORT` et `EXTERN`

   Spécifie les importations à l’aide de cette syntaxe :

   > **IMPORTATION**|**EXTERN** *sym*{**, faible** *alias*{**, TYPE** *t*}}

   *SYM* est le nom du symbole à importer.

   Si `WEAK` *alias* est spécifié, il indique que *sym* est un faible externe. Si aucune définition pour qu’il se trouve au moment de la liaison, toutes les références à lier à la place à *alias*.

   Si `TYPE` *t* est spécifié, puis *t* indique comment l’éditeur de liens doit tenter de résoudre *sym*.  Ces valeurs pour *t* sont possibles :

   |Value|Description|
   |-|-|
   |1|N’effectuez pas une recherche de bibliothèque pour *sym*|
   |2|Effectuer une recherche de la bibliothèque de *sym*|
   |3|*SYM* est un alias pour *alias* (valeur par défaut)|

   `EXTERN` est un synonyme de `IMPORT`, sauf que *sym* est importé uniquement s’il existe des références à celle-ci dans l’assembly actuel.

- MACRO

   L’utilisation d’une variable pour contenir le code de la condition d’une macro n’est pas pris en charge. Valeurs par défaut des paramètres ne sont pas pris en charge de macro.

- NOFP

   Non pris en charge.

- `OPT`, `TTL`, `SUBT`

   Non pris en charge, car l’assembleur Microsoft ARM ne génère pas de listes.

- PRESERVE8

   Non pris en charge.

- RÉADRESSAGE

   `RELOC n` ne peut suivre qu’une instruction ou une directive de définition de données. Il n’existe aucun « symbole anonyme » qui peut être déplacé.

- NÉCESSITENT

   Non pris en charge.

- REQUIRE8

   Non pris en charge.

- THUMBX

   Non pris en charge car l’assembleur Microsoft ARM ne prend pas en charge le jeu d’instructions Thumb-2EE.

## <a name="see-also"></a>Voir aussi

[Référence de la ligne de commande de l’assembleur ARM](../../assembler/arm/arm-assembler-command-line-reference.md)<br/>
[Messages de diagnostic de l’assembleur ARM](../../assembler/arm/arm-assembler-diagnostic-messages.md)<br/>
