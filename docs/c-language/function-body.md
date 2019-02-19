---
title: Corps de fonction
ms.date: 11/04/2016
helpviewer_keywords:
- functions [C], syntax
- variables, function syntax
- function definitions, function body
- function body
ms.assetid: f7e74822-fac8-4dc8-8f3a-2b1611da4640
ms.openlocfilehash: c227640e45943fb57b1029a4f03329241d1d6b34
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/12/2019
ms.locfileid: "56146864"
---
# <a name="function-body"></a>Corps de fonction

Un *corps de fonction* est une instruction composée contenant les instructions qui spécifient ce que fait la fonction.

## <a name="syntax"></a>Syntaxe

*function-definition*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*declaration-specifiers*<sub>opt</sub> *attribute-seq*<sub>opt</sub> *declarator* *declaration-list*<sub>opt</sub> *compound-statement*

/\* *attribute-seq* est spécifique à Microsoft \*/

*compound-statement*: /\* Le corps de la fonction \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**{** *declaration-list*<sub>opt</sub> *statement-list*<sub>opt</sub> **}**

Les variables déclarées dans un corps de fonction, appelées *variables locales*, ont une classe de stockage **auto**, sauf indication contraire. Lorsque la fonction est appelée, du stockage est créé pour les variables locales et les initialisations locales sont exécutées. Le contrôle d'exécution passe à la première instruction dans *compound-statement* et continue jusqu'à ce qu'une instruction **return** soit exécutée ou jusqu'à la fin du corps de la fonction. Le contrôle revient ensuite au point auquel la fonction a été appelée.

Une instruction **return** contenant une expression doit être exécutée si la fonction doit retourner une valeur. La valeur renvoyée d'une fonction est non définie si aucune instruction **return** n'est exécutée ou si l'instruction **return** n'inclut pas d'expression.

## <a name="see-also"></a>Voir aussi

[Définitions de fonction C](../c-language/c-function-definitions.md)
