---
title: Déclarations d’énumération C
description: Déclarations d’énumération dans le langage de programmation C.
ms.date: 10/02/2020
helpviewer_keywords:
- declarations, enumerations
- define directive (#define), alternative to
- enumerators, declaring
- '#define directive, alternative to'
- named constants, enumeration declarations
- declaring enumerations
ms.assetid: bd18f673-4dda-4bc1-92fd-d1ce10074910
ms.openlocfilehash: b7df41475a630b9f6e1d735f5454f6d9601cdd16
ms.sourcegitcommit: 30792632548d1c71894f9fecbe2f554294b86020
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/06/2020
ms.locfileid: "91765206"
---
# <a name="c-enumeration-declarations"></a>Déclarations d’énumération C

Une énumération se compose d'un ensemble de constantes entières nommées. Une déclaration de type énumération donne le nom de la balise d’énumération (facultative). Et, il définit l’ensemble des identificateurs entiers nommés (appelés *jeu d’énumération*, *constantes d’énumérateur*, *énumérateurs*ou *membres*). Une variable du type énumération stocke l’une des valeurs de l’ensemble d’énumération défini par ce type.

Les variables de **`enum`** type peuvent être utilisées dans des expressions d’indexation et comme opérandes de tous les opérateurs arithmétiques et relationnels. Les énumérations offrent une alternative à la directive de préprocesseur `#define` et présentent l'avantage suivant : les valeurs peuvent être générées pour vous et se conformer aux règles normales de portée.

En C ANSI, les expressions qui définissent la valeur d’une constante d’énumérateur ont toujours le **`int`** type. Cela signifie que le stockage associé à une variable d’énumération est le stockage requis pour une **`int`** valeur unique. Une constante d'énumération ou une valeur de type énuméré peut être utilisée partout où le langage C autorise une expression d'entier.

## <a name="syntax"></a>Syntaxe

*`enum-specifier`*:\
&emsp;**`enum`***`identifier`* <sub>opt</sub> **`{`** OPT *`enumerator-list`***`}`**\
&emsp;**`enum`** *`identifier`*

*`enumerator-list`*:\
&emsp;*`enumerator`*\
&emsp;*`enumerator-list`* **`,`** *`enumerator`*

*`enumerator`*:\
&emsp;*`enumeration-constant`*\
&emsp;*`enumeration-constant`* **`=`** *`constant-expression`*

*`enumeration-constant`*:\
&emsp;*`identifier`*

Facultatif *`identifier`* nomme le type énumération défini par *`enumerator-list`* . Cet identificateur est souvent appelé « étiquette » de l’énumération spécifiée par la liste. Un spécificateur de type déclare `identifier` comme étant la balise de l’énumération spécifiée par le non *`enumerator-list`* Terminal, comme illustré ici :

```C
enum identifier
{
    // enumerator-list
}
```

*`enumerator-list`* Définit les membres du jeu d’énumération.

Si la déclaration d’une balise est visible, les déclarations ultérieures qui utilisent la balise mais omettent *`enumerator-list`* spécifient le type énuméré précédemment déclaré. L’étiquette doit faire référence à un type énumération défini, et ce type énumération doit se trouver dans la portée actuelle. Étant donné que le type énumération est défini ailleurs, le *`enumerator-list`* n’apparaît pas dans cette déclaration. Les déclarations de types dérivées des énumérations et des **`typedef`** déclarations pour les types énumération peuvent utiliser la balise d’énumération avant que le type énumération soit défini.

Chaque *`enumeration-constant`* dans un *`enumerator-list`* nomme une valeur de l’énumération définie. Par défaut, le premier *`enumeration-constant`* est associé à la valeur 0. Le suivant *`enumeration-constant`* dans la liste est associé à la valeur de ( *`constant-expression`* + 1), sauf si vous l’associez explicitement à une autre valeur. Le nom d’un *`enumeration-constant`* est équivalent à sa valeur.

Vous pouvez utiliser *`enumeration-constant`*  =  *`constant-expression`* pour remplacer la séquence de valeurs par défaut. Autrement dit, si *`enumeration-constant`*  =  *`constant-expression`* apparaît dans *`enumerator-list`* , le *`enumeration-constant`* est associé à la valeur donnée par *`constant-expression`* . Le *`constant-expression`* doit avoir le **`int`** type et peut être négatif.

Les règles suivantes s'appliquent aux membres d'un ensemble d'énumération :

- Un ensemble d'énumération peut contenir des valeurs de constante en double. Par exemple, vous pouvez associer la valeur 0 à deux identificateurs différents, par exemple, les membres nommés `null` et `zero` , dans le même ensemble.

- Les identificateurs de la liste d’énumération doivent être distincts des autres identificateurs dans la même portée avec la même visibilité. Qui comprend des noms de variables ordinaires et des identificateurs dans d’autres listes d’énumération.

- Les balises d'énumération obéissent aux règles normales de portée. Elles doivent être distinctes des autres balises d'énumération, de structure et d'union ayant la même visibilité.

## <a name="examples"></a>Exemples

Les exemples suivants illustrent des déclarations d'énumération :

```C
enum DAY            /* Defines an enumeration type    */
{
    saturday,       /* Names day and declares a       */
    sunday = 0,     /* variable named workday with    */
    monday,         /* that type                      */
    tuesday,
    wednesday,      /* wednesday is associated with 3 */
    thursday,
    friday
} workday;
```

La valeur 0 est associée à `saturday` par défaut. L'identificateur `sunday` est explicitement défini à 0. Les autres identificateurs sont définis avec les valeurs 1 à 5 par défaut.

Dans cet exemple, une valeur de l'ensemble `DAY` est assignée à la variable `today`.

```C
enum DAY today = wednesday;
```

Le nom de la constante d’énumération est utilisé pour assigner la valeur. Étant donné que le type énumération `DAY` a été déclaré précédemment, seule la balise d'énumération `DAY` est nécessaire.

Pour assigner explicitement une valeur d'entier à une variable d'un type de données énuméré, utilisez un cast de type :

```C
workday = ( enum DAY ) ( day_value - 1 );
```

Ce cast est recommandé dans C, mais n’est pas obligatoire.

```C
enum BOOLEAN  /* Declares an enumeration data type called BOOLEAN */
{
    false,     /* false = 0, true = 1 */
    true
};

enum BOOLEAN end_flag, match_flag; /* Two variables of type BOOLEAN */
```

Cette déclaration peut également être spécifiée sous la forme

```C
enum BOOLEAN { false, true } end_flag, match_flag;\
```

ou sous la forme

```C
enum BOOLEAN { false, true } end_flag;
enum BOOLEAN match_flag;
```

Voici un exemple qui utilise ces variables :

```C
if ( match_flag == false )
    {
     .
     .   /* statement */
     .
    }
    end_flag = true;
```

Les types de données d'énumérateur sans nom peuvent également être déclarés. Le nom du type de données est omis, mais les variables peuvent être déclarées. La variable `response` est une variable du type défini :

```C
enum { yes, no } response;
```

## <a name="see-also"></a>Voir aussi

[Énumérations](../cpp/enumerations-cpp.md)
