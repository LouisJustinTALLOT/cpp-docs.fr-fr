---
description: 'En savoir plus sur : corps de fonction'
title: Corps de fonction
ms.date: 11/04/2016
helpviewer_keywords:
- functions [C], syntax
- variables, function syntax
- function definitions, function body
- function body
ms.assetid: f7e74822-fac8-4dc8-8f3a-2b1611da4640
ms.openlocfilehash: 098a759a8fd4fd9ab69e487ab84f7ed7d0d2c25c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97195981"
---
# <a name="function-body"></a>Corps de fonction

Un *corps de fonction* est une instruction composée contenant les instructions qui spécifient ce que fait la fonction.

## <a name="syntax"></a>Syntaxe

*définition de fonction*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*declaration-specifiers*<sub>opt</sub> *attribute-seq*<sub>opt</sub> *declarator* *declaration-list*<sub>opt</sub> *compound-statement*

/\**attribute-SEQ* est spécifique à Microsoft\*/

*Compound-Statement*:/ \* le corps de la fonction \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**{** *declaration-list*<sub>OPT</sub> *Statement-List*<sub>OPT</sub> **}**

Les variables déclarées dans un corps de fonction, appelées « *variables locales*», ont une **`auto`** classe de stockage, sauf indication contraire. Lorsque la fonction est appelée, du stockage est créé pour les variables locales et les initialisations locales sont exécutées. Le contrôle d’exécution passe à la première instruction dans *Compound-Statement* et continue jusqu’à ce qu’une **`return`** instruction soit exécutée ou que la fin du corps de la fonction soit rencontrée. Le contrôle revient ensuite au point auquel la fonction a été appelée.

Une **`return`** instruction contenant une expression doit être exécutée si la fonction doit retourner une valeur. La valeur de retour d’une fonction n’est pas définie si aucune **`return`** instruction n’est exécutée ou si l' **`return`** instruction n’inclut pas d’expression.

## <a name="see-also"></a>Voir aussi

[Définitions de fonction C](../c-language/c-function-definitions.md)
