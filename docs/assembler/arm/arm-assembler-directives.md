---
title: Directive d’assembleur ARM | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
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
ms.openlocfilehash: 9f5ab97fb9ccdff19206b829383c622efd3f7921
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2018
ms.locfileid: "32053299"
---
# <a name="arm-assembler-directives"></a>Directive d'assembleur ARM
Dans la plupart des cas, l’assembleur Microsoft ARM utilise le langage assembleur ARM, qui est décrit dans le chapitre 7 de la [guide des outils assembleur ARM](http://go.microsoft.com/fwlink/p/?linkid=246102). Toutefois, les implémentations de Microsoft de certaines directives d’assembly diffèrent dans les directives d’assembly ARM. Cet article explique les différences.  
  
## <a name="microsoft-implementations-of-arm-assembly-directives"></a>Implémentations de Microsoft de Directives d’Assembly ARM  
 ZONE  
 L’assembleur Microsoft ARM prend en charge ces attributs de la zone : aligner, CODE, CODEALIGN, données, NOINIT, en lecture seule, lecture/écriture, THUMB, ARM.  
  
 Tous sauf le curseur de défilement et ARM de travail comme décrit dans la [guide des outils assembleur ARM](http://go.microsoft.com/fwlink/p/?linkid=246102).  
  
 Dans l’assembleur Microsoft ARM, THUMB indique qu’une section de CODE contient du code Thumb et est la valeur par défaut pour les sections CODE.  ARM indique que la section contient les code ARM.  
  
 ATTR  
 Non pris en charge.  
  
 CODE16  
 Non pris en charge, car elle implique la syntaxe Thumb pre-journalisation des accès utilisateur, l’assembleur Microsoft ARM n’autorise pas.  Utilisez la directive de curseur de défilement à la place, ainsi que de la syntaxe de la journalisation des accès utilisateur.  
  
 COURANTES  
 Spécification d’un alignement de la région commune n’est pas pris en charge.  
  
 DCDO  
 Non pris en charge.  
  
 NOM UNIQUE, QN, SN  
 Spécification d’un type ou un couloir sur l’alias de Registre n’est pas pris en charge.  
  
 ENTRÉE  
 Non pris en charge.  
  
 EQU  
 Spécification d’un type pour le symbole défini n’est pas prise en charge.  
  
 EXPORTATION et GLOBAL  
 ```  
EXPORTsym {[type]}  
```  
  
 `sym` est le symbole doit être exporté.  `[type]`, si spécifié, peut être `[DATA]` pour indiquer que le symbole pointe vers les données ou `[FUNC]` pour indiquer que le symbole pointe vers du code.  
  
 GLOBAL est un synonyme pour l’exportation.  
  
 EXPORTAS  
 Non pris en charge.  
  
 FRAME  
 Non pris en charge.  
  
 FONCTION et PROC  
 Bien que la syntaxe de l’assembly prend en charge la spécification d’un personnalisé convention d’appel de procédures en répertoriant les registres à enregistrer à l’appelant et celles qui sont appelé enregistrement, l’assembleur Microsoft ARM accepte la syntaxe, mais ignore les listes de Registre.  Les informations de débogage qui sont générées par l’assembleur prend en charge uniquement la valeur par défaut convention d’appel.  
  
 IMPORTATION et EXTERN  
 ```  
IMPORT sym{, WEAK alias{, TYPE t}}  
```  
  
 `sym` est le nom du symbole à importer.  
  
 Si faible `alias` est spécifié, il indique que `sym` est un faible externe. Si aucune définition pour qu’il se trouve au moment de la liaison, puis toutes les références à lier à la place à `alias`.  
  
 Si TYPE `t` est spécifié, puis `t` indique comment l’éditeur de liens doit tenter de résoudre `sym`.  Ces valeurs pour `t` sont possibles :   
1 : n’effectuez pas une recherche de bibliothèque pour `sym`  
2 : effectuer une recherche de la bibliothèque de `sym`  
3 :`sym` est un alias de `alias` (par défaut)  
  
 EXTERN est un synonyme pour une importation, à ceci près que `sym` est importé uniquement s’il existe des références à ce dernier dans l’assembly actuel.  
  
 MACRO  
 L’utilisation d’une variable qui doit contenir le code de la condition d’une macro n’est pas pris en charge. Valeurs par défaut pour la macro de paramètres ne sont pas pris en charge.  
  
 NOFP  
 Non prise en charge.  
  
 S’ABONNER, DURÉE DE VIE, SUBT  
 Non pris en charge, car l’assembleur Microsoft ARM ne produit pas de listes.  
  
 PRESERVE8  
 Non pris en charge.  
  
 RÉADRESSAGE  
 `RELOC n` ne peut suivre qu’une instruction ou une directive de définition de données. Il n’existe aucune « symbole anonyme » qui peut être déplacé.  
  
 NÉCESSITENT  
 Non pris en charge.  
  
 REQUIRE8  
 Non pris en charge.  
  
 THUMBX  
 N’est pas prise en charge car l’assembleur Microsoft ARM ne prend pas en charge le jeu d’instructions Thumb-2EE.  
  
## <a name="see-also"></a>Voir aussi  
 [Référence de ligne de commande de l’assembleur ARM](../../assembler/arm/arm-assembler-command-line-reference.md)   
 [Messages de diagnostic de l’assembleur ARM](../../assembler/arm/arm-assembler-diagnostic-messages.md)