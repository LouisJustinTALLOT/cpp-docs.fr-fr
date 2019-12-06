---
title: Parameters
ms.date: 11/04/2016
helpviewer_keywords:
- arguments [C++], function
- function parameters
- parameters [C++]
- function arguments, vs. parameters
- parameters [C++], function
- functions [C], parameters
- function parameters, syntax
- ellipses (...), parameters
- '... ellipsis'
ms.assetid: 8f2b8026-78b5-4e21-86a3-bf0f91f05689
ms.openlocfilehash: f2fd4b49e08149f8ea5ce8fa6af46da39907dcf9
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857045"
---
# <a name="parameters"></a>Parameters

Les arguments sont les noms des valeurs passées à une fonction par un appel de fonction. Les paramètres sont les valeurs que la fonction compte recevoir. Dans un prototype de fonction, les parenthèses suivant le nom de la fonction contiennent une liste complète des types et des paramètres de la fonction. Les déclarations de paramètres spécifient les types, les tailles et les identificateurs des valeurs stockées dans les paramètres.

## <a name="syntax"></a>Syntaxe

*function-definition*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*declaration-specifiers*<sub>opt</sub> *attribute-seq*<sub>opt</sub> *declarator* *declaration-list*<sub>opt</sub> *compound-statement*

/\* *attribute-SEQ* est un \*spécifique à Microsoft /

*declarator* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*pointer*<sub>opt</sub> *direct-declarator*

*direct-declarator* : /\*Déclarateur de fonction \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*direct-declarator*  **(**  *parameter-type-list*  **)**  /\* Déclarateur de nouveau style \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*direct-declarator*  **(**  *identifier-list*<sub>opt</sub> **)**  /\* Déclarateur de style obsolète \*/

*parameter-type-list* : /\* La liste de paramètrest \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*parameter-list* <br/>
&nbsp;&nbsp;&nbsp;&nbsp;*parameter-list* **, ...**

*parameter-list* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*parameter-declaration*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*parameter-list* **,**  *parameter-declaration*

*parameter-declaration* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*declaration-specifiers* *declarator*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*declaration-specifiers* *abstract-declarator*<sub>opt</sub>

*parameter-type-list* est une séquence de déclarations de paramètre séparée par des virgules. La formule de chaque paramètre dans la liste des paramètres ressemble à ceci :

```C
[register]  type-specifier [declarator]
```

Les paramètres de fonction déclarés avec l'attribut **auto** génèrent des erreurs. Les identificateurs des paramètres sont utilisés dans le corps de la fonction pour faire référence aux valeurs passées à la fonction. Vous pouvez nommer les paramètres dans un prototype, mais les noms sont hors de portée à la fin de la déclaration. Par conséquent, des noms de paramètres peuvent être assignés de la même façon ou différemment dans la définition de fonction. Ces identificateurs ne peuvent pas être redéfinis dans le bloc extérieur du corps de la fonction, mais ils peuvent être redéfinis dans les blocs internes et imbriqués comme si la liste des paramètres était un bloc englobant.

Chaque identificateur figurant dans *parameter-type-list* doit être précédé par son spécificateur de type approprié, comme illustré dans cet exemple :

```C
void new( double x, double y, double z )
{
    /* Function body here */
}
```

Si au moins un paramètre apparaît dans la liste de paramètres, la liste peut se terminer par une virgule suivie de trois points ( **,...** ). Cette construction, appelée « notation de sélection », indique un nombre variable d’arguments à la fonction. (Pour plus d’informations, consultez [appels avec un nombre variable d’arguments](../c-language/calls-with-a-variable-number-of-arguments.md) .) Toutefois, un appel à la fonction doit avoir au moins autant d’arguments qu’il y a de paramètres avant la dernière virgule.

Si aucun argument ne doit être passé à la fonction, la liste des paramètres est remplacée par le mot clé `void`. Cette utilisation de `void` est distincte de son utilisation comme un spécificateur de type.

L'ordre et le type des paramètres, y compris toute utilisation de la notation de sélection, doivent être identiques dans toutes les déclarations de fonctions (le cas échéant) et dans la définition de fonction. Les types des arguments après les conversions arithmétiques habituelles doivent être compatibles-assignation avec les types de paramètres correspondants. (Consultez [conversions arithmétiques habituelles](../c-language/usual-arithmetic-conversions.md) pour plus d’informations sur les conversions arithmétiques.) Les arguments qui suivent les points de suspension ne sont pas activés. Un paramètre peut avoir n'importe quel type fondamental, structure, union, pointeur ou tableau.

Le compilateur effectue les conversions arithmétiques habituelles indépendamment sur chaque paramètre et sur chaque argument, si nécessaire. Après la conversion, aucun paramètre n'est plus court que `int`, et aucun paramètre n'a le type **float** à moins que le type de paramètre soit explicitement spécifié comme **float** dans le prototype. Cela signifie, par exemple, que la déclaration d'un paramètre comme `char` revient à la déclarer comme `int`.

## <a name="see-also"></a>Voir aussi

[Définitions de fonction C](../c-language/c-function-definitions.md)
