---
title: Vue d'ensemble des instructions C
ms.date: 11/04/2016
helpviewer_keywords:
- semicolon, in C statements
- statements, C
- semicolon
- statements, about statements
- Visual C, statements
ms.assetid: 0d49837a-5399-4881-b60c-af5f4e9720de
ms.openlocfilehash: 6b6cf9ee7aab3f14b3cb4b48c10e59125391c14c
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87211773"
---
# <a name="overview-of-c-statements"></a>Vue d'ensemble des instructions C

Les instructions C se composent de jetons, d'expressions et d'autres instructions. Une instruction qui forme un composant d'une autre instruction est qualifiée de « corps » de l'instruction englobante. Chaque type d'instruction donné par la syntaxe suivante est décrit dans cette section.

## <a name="syntax"></a>Syntaxe

*statement*: [labeled-statement](../c-language/goto-and-labeled-statements-c.md)

[compound-statement](../c-language/compound-statement-c.md)

[expression-statement](../c-language/expression-statement-c.md)

[selection-statement](../c-language/if-statement-c.md)

[itération-instruction](../c-language/do-while-statement-c.md)

[jump-statement](../c-language/break-statement-c.md)

[try-except-Statement](../c-language/try-except-statement-c.md) /* spécifique à Microsoft\*/

[try-finally-Statement](../c-language/try-finally-statement-c.md)  / \* Spécifique à Microsoft\*/

Souvent, le corps de l'instruction est une « instruction composée ». Une instruction composée se compose d'autres instructions qui peuvent inclure des mots clés. L'instruction composée est délimitée par des accolades (**{ }**). Toutes les autres instructions C se terminent par un point-virgule (**;**). Le point-virgule est une marque de fin d'instruction.

Une instruction d'expression contient une expression C qui peut contenir les opérateurs arithmétiques ou logiques présentés dans [Expressions et assignations](../c-language/expressions-and-assignments.md). L'instruction null est une instruction vide.

Toute instruction C peut commencer par une étiquette d'identification composée d'un nom et d'un signe deux-points. Étant donné que seule l' **`goto`** instruction reconnaît des étiquettes d’instruction, les étiquettes d’instruction sont présentées avec **`goto`** . Consultez [Instructions goto et étiquetées](../c-language/goto-and-labeled-statements-c.md) pour plus d'informations.

## <a name="see-also"></a>Voir aussi

[Instructions](../c-language/statements-c.md)
