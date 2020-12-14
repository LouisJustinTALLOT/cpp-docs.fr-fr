---
description: 'En savoir plus sur : vue d’ensemble des déclarations'
title: Vue d'ensemble des déclarations
ms.date: 11/04/2016
helpviewer_keywords:
- declarations, about declarations
- type qualifiers
ms.assetid: fcd2364c-c2a5-4fbf-9027-19dac4144cb5
ms.openlocfilehash: 53b8c808771aa3bb455655e6e0c5b06ff1fa9acd
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97256846"
---
# <a name="overview-of-declarations"></a>Vue d'ensemble des déclarations

Une « déclaration » spécifie l'interprétation et les attributs d'un ensemble d'identificateurs. Une déclaration qui permet également que le stockage soit réservé pour l'objet ou la fonction nommés par l'identificateur est appelée une « définition ». Les déclarations C pour les variables, fonctions et types présentent la syntaxe suivante :

## <a name="syntax"></a>Syntaxe

*`declaration`*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*`declaration-specifiers`**`attribute-seq`* <sub></sub> opt opt *`init-declarator-list`* <sub></sub>**`;`**

/\**`attribute-seq`* <sub>OPT</sub> est spécifique à Microsoft */

*`declaration-specifiers`*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*`storage-class-specifier`**`declaration-specifiers`* <sub>OPT</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*`type-specifier`**`declaration-specifiers`* <sub>OPT</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*`type-qualifier`**`declaration-specifiers`* <sub>OPT</sub>

*`init-declarator-list`*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*`init-declarator`*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*`init-declarator-list`* **`,`** *`init-declarator`*

*`init-declarator`*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*`declarator`*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*`declarator`* **`=`** *`initializer`*

> [!NOTE]
> Cette syntaxe pour *`declaration`* n’est pas répétée dans les sections suivantes. La syntaxe des sections suivantes commence généralement par le non *`declarator`* terminal.

Les déclarations dans *`init-declarator-list`* contiennent les identificateurs qui sont nommés ; *`init`* est une abréviation pour l’initialiseur. *`init-declarator-list`* Est une séquence de déclarateurs séparés par des virgules, chacun d’entre eux pouvant avoir des informations de type supplémentaires ou un initialiseur, ou les deux. *`declarator`* Contient les identificateurs, le cas échéant, déclarés. Le non *`declaration-specifiers`* terminal se compose d’une séquence de spécificateurs de type et de classe de stockage qui indiquent la liaison, la durée de stockage et au moins une partie du type des entités dénotées par les déclarateurs. Les déclarations sont constituées d’une combinaison de spécificateurs de classe de stockage, de spécificateurs de type, de qualificateurs de type, de déclarateurs et d’initialiseurs.

Les déclarations peuvent contenir un ou plusieurs des attributs facultatifs listés dans *`attribute-seq`* ; *`seq`* est une abréviation pour la séquence. Ces attributs spécifiques à Microsoft effectuent plusieurs fonctions, qui sont décrites en détail dans ce document.

Sous la forme générale d’une déclaration de variable, *`type-specifier`* donne le type de données de la variable. *`type-specifier`* Peut être un composé, comme lorsque le type est modifié par **`const`** ou **`volatile`** . `declarator` donne le nom de la variable, éventuellement modifié pour déclarer un tableau ou un type de pointeur. Par exemple :

```C
int const *fp;
```

déclare une variable nommée `fp` comme pointeur vers une valeur non modifiable ( **`const`** ) **`int`** . Vous pouvez définir plusieurs variables dans une déclaration à l'aide de plusieurs déclarateurs, séparés par une virgule.

Une déclaration doit contenir au moins un déclarateur ou son spécificateur de type doit déclarer une balise de structure, une balise d'union ou des membres d'une énumération. Les déclarateurs fournissent toutes les informations restantes sur un identificateur. Un déclarateur est un identificateur qui peut être modifié à l’aide de crochets () **`[ ]`** , d’astérisques ( <strong>`*`</strong> ) ou de parenthèses ( **`( )`** ) pour déclarer un tableau, un pointeur ou un type de fonction, respectivement. Quand vous déclarez des variables simples (comme un caractère, un entier et des éléments à virgule flottante) ou des structures et des unions de variables simples, `declarator` est juste un identificateur. Pour plus d'informations sur les déclarateurs, voir [Déclarateurs et déclarations de variable](../c-language/declarators-and-variable-declarations.md).

Toutes les définitions sont implicitement des déclarations, mais toutes les déclarations ne sont pas des définitions. Par exemple, les déclarations de variables qui commencent par le **`extern`** spécificateur de classe de stockage sont des déclarations de « référencement » et non de « définition ». Si une variable externe doit être référencée avant d’être définie, ou si elle est définie dans un autre fichier source à partir de celle où elle est utilisée, une **`extern`** déclaration est nécessaire. Le stockage n'est pas alloué par les déclarations de « référencement » et les variables ne peuvent pas être initialisées dans les déclarations.

Une classe de stockage ou un type (ou les deux) sont requis dans les déclarations de variable. À l’exception de **`__declspec`** , un seul spécificateur de classe de stockage est autorisé dans une déclaration et tous les spécificateurs de classe de stockage ne sont pas autorisés dans chaque contexte. La **`__declspec`** classe de stockage est autorisée avec d’autres spécificateurs de classe de stockage et est autorisée plusieurs fois. Le spécificateur de classe de stockage d'une déclaration affecte la façon dont l'élément déclaré est stocké et initialisé, ainsi que les parties d'un programme qui peuvent référencer l'élément.

Les *`storage-class-specifier`* terminaux définis en C incluent **`auto`** , **`extern`** , **`register`** , **`static`** et **`typedef`** . Microsoft C comprend également le *`storage-class-specifier`* Terminal **`__declspec`** . Tous les *`storage-class-specifier`* terminaux, à l’exception de **`typedef`** et, **`__declspec`** sont décrits dans [classes de stockage](../c-language/c-storage-classes.md). Pour plus d’informations sur **`typedef`** , consultez [ `typedef` déclarations](../c-language/typedef-declarations.md). Pour plus d’informations sur **`__declspec`** , consultez [Extended Storage-Class Attributes](../c-language/c-extended-storage-class-attributes.md).

L'emplacement de la déclaration dans le programme source et la présence ou l'absence d'autres déclarations de la variable sont des facteurs importants pour déterminer la durée de vie des variables. Il peut y avoir plusieurs redéclarations, mais une seule définition. Toutefois, une définition peut apparaître dans plusieurs unités de traduction. Pour les objets avec une liaison interne, cette règle s'applique séparément à chaque unité de traduction, car les objets liés de manière interne sont uniques pour une unité de traduction. Pour les objets avec une liaison externe, cette règle s'applique au programme entier. Pour plus d’informations sur la visibilité, consultez [durée de vie, portée, visibilité et liaison](../c-language/lifetime-scope-visibility-and-linkage.md).

Les spécificateurs de type fournissent des informations sur les types de données des identificateurs. Le spécificateur de type par défaut est **`int`** . Pour plus d'informations, voir [Spécificateurs de type](../c-language/c-type-specifiers.md). Les spécificateurs de type peuvent aussi définir des étiquettes de type, des noms de composant de structure et d’union, et des constantes d’énumération. Pour plus d’informations, consultez [déclarations d’énumération](../c-language/c-enumeration-declarations.md), [déclarations de structure](../c-language/structure-declarations.md)et déclarations d' [Union](../c-language/union-declarations.md).

Il existe deux *`type-qualifier`* terminaux : **`const`** et **`volatile`** . Ces qualificateurs spécifient des propriétés supplémentaires de types seulement pour l'accès aux objets de ce type avec des I-values. Pour plus d’informations sur **`const`** et **`volatile`** , consultez [qualificateurs de type](../c-language/type-qualifiers.md). Pour obtenir une définition des I-values, voir [Expressions L-Value et R-Value](../c-language/l-value-and-r-value-expressions.md).

## <a name="see-also"></a>Voir aussi

[Résumé de la syntaxe du langage C](../c-language/c-language-syntax-summary.md)<br/>
[Déclarations et types](../c-language/declarations-and-types.md)<br/>
[Résumé des déclarations](../c-language/summary-of-declarations.md)
