---
description: 'En savoir plus sur : déclarations de structure'
title: Déclarations de structure
ms.date: 11/04/2016
helpviewer_keywords:
- structure declarations
- anonymous structures
- types [C], declarations
- structure members
- embedded structures
ms.assetid: 5be3be77-a236-4153-b574-7aa77675df7f
ms.openlocfilehash: 6fe2a241e28ce9b8c9c1ee114c18e2aa9afc704c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97114609"
---
# <a name="structure-declarations"></a>Déclarations de structure

Une déclaration de structure désigne un type et spécifie une séquence de valeurs variables (appelées membres ou champs de la structure) qui peuvent avoir des types. Un identificateur facultatif, appelé balise indique le nom du type de structure et peut être utilisé dans les références suivantes au type structure. Une variable de ce type structure contient la séquence entière définie par ce type. Les structures en C sont semblables aux types appelés enregistrements dans d'autres langages.

## <a name="syntax"></a>Syntaxe

*spécificateur struct-or-Union*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*identificateur struct-or-Union* <sub>OPT</sub> **{** *struct-declaration-list* **}**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*struct-ou-union* *identificateur*

*struct-or-union* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`struct`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`union`**

*struct-declaration-list* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*struct-declaration*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*struct-declaration-list* *struct-declaration*

*struct-DECLARATION*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*specifier-qualifier-list* *struct-declarator-list* **;**

*specifier-qualifier-list* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*type-specifier* *specifier-qualifier-list*<sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*type-qualifier* *specifier-qualifier-list*<sub>opt</sub>

*struct-declarator-list* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;struct *-déclarateur* struct *-declarator-List* **,** *struct-declarator*

*déclarateur de struct*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*declarator*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*type-specifier* *declarator*<sub>OPT</sub> **:** *constant-expression*

La déclaration d'un type structure ne met pas de côté l'espace pour une structure. C'est uniquement un modèle pour les déclarations suivantes de variables de structure.

Un *identifier* (étiquette) défini peut être utilisé pour faire référence à un type structure défini ailleurs. Dans ce cas, *struct-declaration-list* ne peut pas être répété tant que la définition est visible. Les déclarations de pointeurs vers les structures et typedefs pour les types de structure peuvent utiliser l’étiquette de structure avant que le type de structure ne soit défini. Toutefois, la définition de structure doit être produite avant toute utilisation réelle de la taille des champs. C'est une définition incomplète du type et de la balise de type. Pour que cette définition soit terminée, une définition de type doit apparaître plus loin dans la même portée.

*struct-declaration-list* spécifie les types et les noms des membres de structures. Un argument *struct-declaration-list* contient une ou plusieurs déclarations de variable ou de champ de bits.

Chaque variable déclarée dans *struct-declaration-list* est définie comme membre du type structure. Les déclarations de variables dans *struct-declaration-list* ont la même forme que d’autres déclarations de variables décrites dans cette section, mais les déclarations ne peuvent pas contenir des spécificateurs ou initialiseurs de classe de stockage. Les membres de structure peuvent avoir des types de variable, à l’exception de type **`void`** , un type incomplet ou un type de fonction.

Un membre ne peut pas être déclaré comme ayant le type de la structure dans laquelle il apparaît. Toutefois, un membre peut être déclaré comme pointeur vers le type structure dans lequel il apparaît tant que le type structure a une balise. Cela vous permet de créer des listes de structures liées.

Les structures respectent la même portée que les autres identificateurs. Les identificateurs de structure doivent être distingués des autres étiquettes de structure, d’union et d’énumération ayant la même visibilité.

Chaque *struct-declaration* présent dans *struct-declaration-list* doit être unique dans la liste. Toutefois, les noms d’identificateur présents dans un argument *struct-declaration-list* ne doivent pas être distingués des noms de variables ordinaires ou des identificateurs présents dans d’autres listes de déclaration de structure.

Les structures imbriquées sont également accessibles comme si elles avaient été déclarées au niveau de la portée du fichier. Par exemple, supposons cette déclaration :

```C
struct a
{
    int x;
    struct b
    {
      int y;
    } var2;
} var1;
```

ces déclarations sont toutes deux valides :

```C
struct a var3;
struct b var4;
```

## <a name="examples"></a>Exemples

Les exemples suivants montrent des déclarations de structure :

```C
struct employee   /* Defines a structure variable named temp */
{
    char name[20];
    int id;
    long class;
} temp;
```

La structure `employee` a trois membres : `name`, `id` et `class`. Le `name` membre est un tableau de 20 éléments et `id` et `class` sont des membres simples avec **`int`** et **`long`** type, respectivement. L'identificateur `employee` est l'identificateur de structure.

```C
struct employee student, faculty, staff;
```

Cet exemple définit trois variables de structure : `student`, `faculty` et `staff`. Chaque structure possède la même liste de trois membres. Les membres sont déclarés comme ayant le type structure `employee`, défini dans l'exemple précédent.

```C
struct           /* Defines an anonymous struct and a */
{                /* structure variable named complex  */
    float x, y;
} complex;
```

La `complex` structure a deux membres de **`float`** type, `x` et `y` . Le type de structure n’a aucune étiquette et est par conséquent sans nom ou anonyme.

```C
struct sample   /* Defines a structure named x */
{
    char c;
    float *pf;
    struct sample *next;
} x;
```

Les deux premiers membres de la structure sont une **`char`** variable et un pointeur vers une **`float`** valeur. Le troisième membre, `next`, est déclaré comme un pointeur vers le type de structure définie (`sample`).

Les structures anonymes peuvent être utiles lorsque la balise nommée n'est pas nécessaire. C'est le cas lorsqu'une déclaration définit toutes les instances de structure. Par exemple :

```C
struct
{
    int x;
    int y;
} mystruct;
```

Les structures incorporées sont souvent anonymes.

```C
struct somestruct
{
    struct    /* Anonymous structure */
    {
        int x, y;
    } point;
    int type;
} w;
```

**Spécifique à Microsoft**

Le compilateur autorise un tableau non dimensionné ou un tableau de taille zéro comme dernier membre d'une structure. Cela peut être utile si la taille d'un tableau fixe diffère lorsqu'elle est utilisée dans différentes situations. La déclaration de cette structure ressemble à ceci :

**`struct`***identificateur* **{** *set-of-declarations* de *type* <em>tableau</em>**\[ ];};**

Les tableaux non dimensionnés peuvent apparaître uniquement comme dernier membre d'une structure. Les structures contenant des déclarations de tableau non dimensionné peuvent être imbriquées dans d'autres structures tant qu'aucun autre membre n'est déclaré dans une structure englobante. Les tableaux de ces structures ne sont pas autorisés. L' **`sizeof`** opérateur, lorsqu’il est appliqué à une variable de ce type ou au type lui-même, suppose 0 pour la taille du tableau.

Les déclarations de structure peuvent également être spécifiées sans déclarateur lorsqu'elles sont membres d'une autre structure ou union. Les noms de champ sont promus dans la structure englobante. Par exemple, une structure sans nom ressemble à ceci :

```C
struct s
{
    float y;
    struct
    {
        int a, b, c;
    };
    char str[10];
} *p_s;
.
.
.
p_s->b = 100;  /* A reference to a field in the s structure */
```

Pour plus d’informations sur les références de structure, consultez [Membres de structure et d’union](../c-language/structure-and-union-members.md).

**FIN spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Déclarateurs et déclarations de variable](../c-language/declarators-and-variable-declarations.md)
