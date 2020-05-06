---
title: Déclarations d'énumération C
ms.date: 11/04/2016
helpviewer_keywords:
- declarations, enumerations
- define directive (#define), alternative to
- enumerators, declaring
- '#define directive, alternative to'
- named constants, enumeration declarations
- declaring enumerations
ms.assetid: bd18f673-4dda-4bc1-92fd-d1ce10074910
ms.openlocfilehash: bc238dd0088558233d84f8bbd15d06743e133449
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62326012"
---
# <a name="c-enumeration-declarations"></a>Déclarations d'énumération C

Une énumération se compose d'un ensemble de constantes entières nommées. Une déclaration de type énumération indique le nom de la balise d'énumération (facultative) et définit l'ensemble des identificateurs d'entiers nommés (appelés « ensemble d'énumération », « constantes d'énumérateur », « énumérateurs » ou « membres »). Une variable avec type énumération stocke une des valeurs de l'ensemble d'énumération défini par ce type.

Les variables de type `enum` peuvent être utilisées dans des expressions d'indexation et comme opérandes de tous les opérateurs arithmétiques et relationnels. Les énumérations offrent une alternative à la directive de préprocesseur `#define` et présentent l'avantage suivant : les valeurs peuvent être générées pour vous et se conformer aux règles normales de portée.

En C ANSI, les expressions qui définissent la valeur d'une constante d'énumérateur ont toujours le type `int` ; par conséquent, le stockage associé à une variable d'énumération est celui requis pour une seule valeur `int` unique. Une constante d'énumération ou une valeur de type énuméré peut être utilisée partout où le langage C autorise une expression d'entier.

## <a name="syntax"></a>Syntaxe

*enum-specifier* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;identificateur d' **énumération** *identifier*<sub>OPT</sub> **{** *Enumerator-List* **}**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*identificateur* d' **énumération**

L'élément facultatif *identifier* désigne le type énumération défini par *enumerator-list*. Cet identificateur est souvent appelé « étiquette » de l’énumération spécifiée par la liste. Un spécificateur de type de la forme

```
enum identifier
{
    enumerator-list
}
```

déclare l'élément *identifier* comme devant être la balise de l'énumération spécifiée par l'élément non terminal *enumerator-list*. L'élément *enumerator-list* définit le « contenu d'énumérateur ». L'élément *enumerator-list* est décrit en détail ci-dessous.

Si la déclaration d’une étiquette est visible, les déclarations suivantes qui utilisent l’étiquette mais omettent l’élément *enumerator-list* spécifient le type énuméré déclaré précédemment. L’étiquette doit faire référence à un type énumération défini, et ce type énumération doit se trouver dans la portée actuelle. Étant donné que le type énumération est défini ailleurs, l'élément *enumerator-list* n'apparaît pas dans cette déclaration. Les déclarations des types dérivés à partir des énumérations et les déclarations de `typedef` pour les types énumération peuvent utiliser la balise d'énumération avant que le type énumération ne soit défini.

## <a name="syntax"></a>Syntaxe

*énumérateur-List*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*énumérateur*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Enumerator-List* **,** *énumérateur*

*énumérateur*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*énumération-constante*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*énumération-* **=** constante constante *-expression*

*énumération-constante*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*identificateur*

Chaque élément *enumeration-constant* d'un élément *enumeration-list* désigne une valeur de l'ensemble d'énumération. Par défaut, le premier élément *enumeration-constant* est associé à la valeur 0. L'élément *enumeration-constant* suivant dans la liste est associé à la valeur de (*constant-expression* + 1), sauf si vous l'associez explicitement à une autre valeur. Le nom d'un élément *enumeration-constant* est équivalent à sa valeur.

Vous pouvez utiliser *enumeration-constant = constant-expression* pour remplacer la séquence de valeurs par défaut. Par conséquent, si *enumeration-constant = constant-expression* apparaît dans l'élément *enumerator-list*, l'élément *enumeration-constant* est associé à la valeur indiquée par *constant-expression*. L'élément *constant-expression* doit avoir le type `int` et peut être négatif.

Les règles suivantes s'appliquent aux membres d'un ensemble d'énumération :

- Un ensemble d'énumération peut contenir des valeurs de constante en double. Par exemple, vous pouvez associer la valeur 0 à deux identificateurs différents, peut-être nommés `null` et `zero`, dans le même ensemble.

- Les identificateurs dans la liste d'énumérations doivent être distincts des autres identificateurs dans la même portée ayant la même visibilité, y compris des noms de variable ordinaire et des identificateurs dans les autres listes d'énumération.

- Les balises d'énumération obéissent aux règles normales de portée. Elles doivent être distinctes des autres balises d'énumération, de structure et d'union ayant la même visibilité.

## <a name="examples"></a>Exemples

Les exemples suivants illustrent des déclarations d'énumération :

```
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

```
enum DAY today = wednesday;
```

Notez que le nom de la constante d'énumération est utilisé pour assigner la valeur. Étant donné que le type énumération `DAY` a été déclaré précédemment, seule la balise d'énumération `DAY` est nécessaire.

Pour assigner explicitement une valeur d'entier à une variable d'un type de données énuméré, utilisez un cast de type :

```
workday = ( enum DAY ) ( day_value - 1 );
```

Ce cast est recommandé mais C n'est pas requis.

```
enum BOOLEAN  /* Declares an enumeration data type called BOOLEAN */
{
    false,     /* false = 0, true = 1 */
    true
};

enum BOOLEAN end_flag, match_flag; /* Two variables of type BOOLEAN */
```

Cette déclaration peut également être spécifiée sous la forme

```
enum BOOLEAN { false, true } end_flag, match_flag;\
```

ou sous la forme

```
enum BOOLEAN { false, true } end_flag;
enum BOOLEAN match_flag;
```

Voici un exemple qui utilise ces variables :

```
if ( match_flag == false )
    {
     .
     .   /* statement */
     .
    }
    end_flag = true;
```

Les types de données d'énumérateur sans nom peuvent également être déclarés. Le nom du type de données est omis, mais les variables peuvent être déclarées. La variable `response` est une variable du type défini :

```
enum { yes, no } response;
```

## <a name="see-also"></a>Voir aussi

[Énumérations](../cpp/enumerations-cpp.md)
