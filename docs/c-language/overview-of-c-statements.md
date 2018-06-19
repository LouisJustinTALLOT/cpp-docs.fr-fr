---
title: Vue d’ensemble des instructions C | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- semicolon, in C statements
- statements, C
- semicolon
- statements, about statements
- Visual C, statements
ms.assetid: 0d49837a-5399-4881-b60c-af5f4e9720de
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4a3cf80e6237b21101f737f496eb39688ec6ed0a
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32387175"
---
# <a name="overview-of-c-statements"></a>Vue d'ensemble des instructions C
Les instructions C se composent de jetons, d'expressions et d'autres instructions. Une instruction qui forme un composant d'une autre instruction est qualifiée de « corps » de l'instruction englobante. Chaque type d'instruction donné par la syntaxe suivante est décrit dans cette section.  
  
## <a name="syntax"></a>Syntaxe  
 *instruction* :  
 [labeled-statement](../c-language/goto-and-labeled-statements-c.md)  
  
 [compound-statement](../c-language/compound-statement-c.md)  
  
 [expression-statement](../c-language/expression-statement-c.md)  
  
 [selection-statement](../c-language/if-statement-c.md)  
  
 [iteration-statement](../c-language/do-while-statement-c.md)  
  
 [jump-statement](../c-language/break-statement-c.md)  
  
 [try-except-statement](../c-language/try-except-statement-c.md)  
  
 /* Spécifique à Microsoft \*/[try-finally-statement](../c-language/try-finally-statement-c.md) /\* Spécifique à Microsoft \*/  
  
 Souvent, le corps de l'instruction est une « instruction composée ». Une instruction composée se compose d'autres instructions qui peuvent inclure des mots clés. L'instruction composée est délimitée par des accolades (**{ }**). Toutes les autres instructions C se terminent par un point-virgule (**;**). Le point-virgule est une marque de fin d'instruction.  
  
 Une instruction d'expression contient une expression C qui peut contenir les opérateurs arithmétiques ou logiques présentés dans [Expressions et assignations](../c-language/expressions-and-assignments.md). L'instruction null est une instruction vide.  
  
 Toute instruction C peut commencer par une étiquette d'identification composée d'un nom et d'un signe deux-points. Comme seule l'instruction `goto` identifie des étiquettes d'instruction, les étiquettes d'instruction sont présentées avec `goto`. Consultez [Instructions goto et étiquetées](../c-language/goto-and-labeled-statements-c.md) pour plus d'informations.  
  
## <a name="see-also"></a>Voir aussi  
 [Instructions](../c-language/statements-c.md)