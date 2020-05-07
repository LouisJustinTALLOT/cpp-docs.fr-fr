---
title: Vue d'ensemble des déclarations
ms.date: 11/04/2016
helpviewer_keywords:
- declarations, about declarations
- type qualifiers
ms.assetid: fcd2364c-c2a5-4fbf-9027-19dac4144cb5
ms.openlocfilehash: 0ffda6522e632533b0aaa4ba146e8fad082ed435
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857058"
---
# <a name="overview-of-declarations"></a>Vue d'ensemble des déclarations

Une « déclaration » spécifie l'interprétation et les attributs d'un ensemble d'identificateurs. Une déclaration qui permet également que le stockage soit réservé pour l'objet ou la fonction nommés par l'identificateur est appelée une « définition ». Les déclarations C pour les variables, fonctions et types présentent la syntaxe suivante :

## <a name="syntax"></a>Syntaxe

*déclaration*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*DECLARATION-Specifiers* *attribute-SEQ*<sub>OPT</sub> *init-declarator-List*<sub>OPT</sub>**;**

/\**attribute-SEQ*<sub>OPT</sub> est spécifique à Microsoft */

*declaration-specifiers* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*storage-class-specifier* *declaration-specifiers*<sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*type-specifier* *declaration-specifiers*<sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*type-qualifier* *declaration-specifiers*<sub>opt</sub>

*init-declarator-list* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*init-declarator*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*init-declarator-List* **,** *init-declarator*

*init-declarator*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*declarator*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**=** *initialiseur* de *déclarateur*

> [!NOTE]
> Cette syntaxe pour *declaration* n’est pas répétée dans les sections suivantes. La syntaxe des sections suivantes commence généralement par le non-terminal *declarator*.

Les déclarations présentes dans *init-declarator-list* contiennent les identificateurs avec nom. *init* est l'abréviation d'initialiseur. *init-declarator-list* est une séquence de déclarateurs séparés par une virgule. Chacun de ces déclarateurs peut avoir des informations de type supplémentaires ou un initialiseur, ou les deux. *declarator* contient les identificateurs déclarés, le cas échéant. Le non terminal *declaration-specifiers* consiste en une séquence de spécificateurs de type et de classe de stockage qui indiquent la liaison, la durée de stockage et au moins une partie du type des entités désignées par les déclarateurs. Par conséquent, les déclarations sont constituées d'une combinaison de spécificateurs de classe de stockage, de spécificateurs de type, de qualificateurs de type, de déclarateurs et d'initialiseurs.

Les déclarations peuvent contenir un ou plusieurs attributs facultatifs répertoriés dans *attribute-seq*, *seq* étant une abréviation de séquence. Ces attributs spécifiques à Microsoft ont une variété de fonctions, que nous aborderons en détail dans ce livre.

Dans la forme générale d'une déclaration de variable, *type-specifier* donne le type de données de la variable. *type-specifier* peut être un composé, par exemple quand le type est modifié par **const** ou `volatile`. `declarator` donne le nom de la variable, éventuellement modifié pour déclarer un tableau ou un type de pointeur. Par exemple,

```C
int const *fp;
```

déclare une variable nommée `fp` comme pointeur vers une valeur non modifiable (**const**). `int` Vous pouvez définir plusieurs variables dans une déclaration à l'aide de plusieurs déclarateurs, séparés par une virgule.

Une déclaration doit contenir au moins un déclarateur ou son spécificateur de type doit déclarer une balise de structure, une balise d'union ou des membres d'une énumération. Les déclarateurs fournissent toutes les informations restantes sur un identificateur. Un déclarateur est un identificateur pouvant être modifié à l'aide de crochets (**[ ]**), d'astérisques (<strong>\*</strong>) ou de parenthèses ( **( )** ) pour déclarer un tableau, un pointeur ou un type de fonction, respectivement. Quand vous déclarez des variables simples (comme un caractère, un entier et des éléments à virgule flottante) ou des structures et des unions de variables simples, `declarator` est juste un identificateur. Pour plus d'informations sur les déclarateurs, voir [Déclarateurs et déclarations de variable](../c-language/declarators-and-variable-declarations.md).

Toutes les définitions sont implicitement des déclarations, mais toutes les déclarations ne sont pas des définitions. Par exemple, les déclarations de variable commençant par le spécificateur de classe de stockage `extern` sont des déclarations de « référencement » et non de « définition ». Si une variable externe doit être référencée avant d'être définie, ou si elle est définie dans un autre fichier source que celui dans lequel elle est utilisée, une déclaration `extern` est nécessaire. Le stockage n'est pas alloué par les déclarations de « référencement » et les variables ne peuvent pas être initialisées dans les déclarations.

Une classe de stockage ou un type (ou les deux) sont requis dans les déclarations de variable. À l'exception de `__declspec`, seul un spécificateur de classe de stockage est autorisé dans une déclaration et tous les spécificateurs de classe de stockage ne sont pas admis dans tous les contextes. La classe de stockage `__declspec` est autorisée avec d'autres spécificateurs de classe de stockage et peut être autorisée plusieurs fois. Le spécificateur de classe de stockage d'une déclaration affecte la façon dont l'élément déclaré est stocké et initialisé, ainsi que les parties d'un programme qui peuvent référencer l'élément.

Les terminaux *storage-class-specifier* définis en C sont notamment **auto**, `extern` , **register**, **static** et `typedef`. Par ailleurs, Microsoft C inclut le terminal *storage-class-specifier*`__declspec`. Tous les terminaux *storage-class-specifier*, sauf `typedef` et `__declspec`, sont abordés dans [Classes de stockage](../c-language/c-storage-classes.md). Voir [Déclarations Typedef](../c-language/typedef-declarations.md) pour plus d'informations sur `typedef`. Voir [Attributs étendus de classe de stockage](../c-language/c-extended-storage-class-attributes.md) pour plus d'informations sur `__declspec`.

L'emplacement de la déclaration dans le programme source et la présence ou l'absence d'autres déclarations de la variable sont des facteurs importants pour déterminer la durée de vie des variables. Il peut y avoir plusieurs redéclarations, mais une seule définition. Toutefois, une définition peut apparaître dans plusieurs unités de traduction. Pour les objets avec une liaison interne, cette règle s'applique séparément à chaque unité de traduction, car les objets liés de manière interne sont uniques pour une unité de traduction. Pour les objets avec une liaison externe, cette règle s'applique au programme entier. Voir [Durée de vie, portée, visibilité et liaison](../c-language/lifetime-scope-visibility-and-linkage.md) pour plus d'informations sur la visibilité.

Les spécificateurs de type fournissent des informations sur les types de données des identificateurs. Le spécificateur de type par défaut est `int`. Pour plus d'informations, voir [Spécificateurs de type](../c-language/c-type-specifiers.md). Les spécificateurs de type peuvent aussi définir des étiquettes de type, des noms de composant de structure et d’union, et des constantes d’énumération. Pour plus d'informations, voir [Déclarations d'énumération](../c-language/c-enumeration-declarations.md), [Déclarations de structure](../c-language/structure-declarations.md) et [Déclarations d'union](../c-language/union-declarations.md).

Il existe deux terminaux *type-qualifier* : **const** et `volatile`. Ces qualificateurs spécifient des propriétés supplémentaires de types seulement pour l'accès aux objets de ce type avec des I-values. Pour plus d'informations sur **const** et `volatile`, voir [Qualificateurs de type](../c-language/type-qualifiers.md). Pour obtenir une définition des I-values, voir [Expressions L-Value et R-Value](../c-language/l-value-and-r-value-expressions.md).

## <a name="see-also"></a>Voir aussi

[Résumé de syntaxe du langage C](../c-language/c-language-syntax-summary.md)<br/>
[Déclarations et types](../c-language/declarations-and-types.md)<br/>
[Résumé des déclarations](../c-language/summary-of-declarations.md)
