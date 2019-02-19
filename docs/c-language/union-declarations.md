---
title: Déclarations d'union
ms.date: 11/04/2016
helpviewer_keywords:
- unions
- union keyword [C], declarations
- variant records
ms.assetid: 978c6165-e0ae-4196-afa7-6d94e24f62f7
ms.openlocfilehash: dbc85a467161457641dd86acf5f3720bf4e14247
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/12/2019
ms.locfileid: "56149256"
---
# <a name="union-declarations"></a>Déclarations d'union

Une « déclaration d’union » spécifie un ensemble de valeurs variables et, éventuellement, une étiquette d’attribution de nom à l’union. Les valeurs variables sont appelées « membres » de l'union et peuvent avoir différents types. Les unions sont similaires aux « enregistrements de variants » dans d'autres langages.

## <a name="syntax"></a>Syntaxe

*struct-or-union-specifier* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*struct-ou-union* *identificateur*<sub>opt</sub> **{** *liste-déclarations-struct* **}**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*struct-ou-union* *identificateur*

*struct-or-union* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**struct**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**union**

*struct-declaration-list* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*struct-declaration*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*struct-declaration-list* *struct-declaration*

Le contenu d'union est défini comme

*struct-declaration* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*specifier-qualifier-list* *struct-declarator-list*  **;**

*specifier-qualifier-list* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*type-specifier* *specifier-qualifier-list*<sub>opt</sub> <br/>
&nbsp;&nbsp;&nbsp;&nbsp;*type-qualifier* *specifier-qualifier-list*<sub>opt</sub>

*struct-declarator-list* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*struct-declarator*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*struct-declarator-list*  **,**  *struct-declarator*

Une variable du type **union** stocke l'une des valeurs définies par ce type. Les mêmes règles gouvernent les déclarations de structure et d'union. Les unions peuvent également avoir des champs de bits.

Les membres des unions ne peuvent pas avoir de type incomplet, de type `void`, ou de type de fonction. Par conséquent les membres ne peuvent pas être une instance de l'union mais peuvent être des pointeurs vers le type d'union déclaré.

Une déclaration de type union est un modèle uniquement. La mémoire n'est pas réservée jusqu'à ce que la variable soit déclarée.

> [!NOTE]
> Si une union de deux types est déclarée et qu'une valeur est enregistrée, mais que l'union est accessible par l'autre type, les résultats ne sont pas fiables. Par exemple, une union de type **float** et `int` est déclarée. Une valeur de type **float** est stockée, mais le programme y accède ultérieurement en tant que `int`. Dans ce cas, la valeur dépend du stockage interne des valeurs **float**. La valeur entière n'est pas fiable.

## <a name="examples"></a>Exemples

Voici des exemples d'unions :

```C
union sign   /* A definition and a declaration */
{
    int svar;
    unsigned uvar;
} number;
```

Cet exemple définit une variable d'union avec le type `sign` et déclare une variable nommée `number` qui possède deux membres : `svar`, un entier signé, et `uvar`, un entier non signé. Cette déclaration permet d'enregistrer la valeur `number` comme valeur signée ou non signée. La balise associée à ce type d'union est `sign`.

```C
union               /* Defines a two-dimensional */
{                   /*  array named screen */
    struct
    {
      unsigned int icon : 8;
      unsigned color : 4;
    } window1;
    int screenval;
} screen[25][80];
```

Le tableau `screen` contient 2 000 éléments. Chaque élément du tableau est une union individuelle avec deux membres : `window1` et `screenval`. Le membre `window1` est une structure avec deux membres de champ de bits `icon` et `color`. Le membre `screenval` est `int`. À un moment donné, chaque élément union contient soit `int` représenté par `screenval` soit la structure représentée par `window1`.

**Section spécifique à Microsoft**

Les unions imbriquées peuvent être déclarées de façon anonyme lorsqu'elles sont membres d'une structure ou d'une union. Voici un exemple d'une union sans nom.

```C
struct str
{
    int a, b;
    union            / * Unnamed union */
    {
      char c[4];
      long l;
      float f;
   };
   char c_array[10];
} my_str;
.
.
.
my_str.l == 0L;  /* A reference to a field in the my_str union */
```

Les unions sont souvent imbriquées dans une structure qui inclut un champ donnant le type de données contenu dans une union à un moment donné. Voici un exemple d'une déclaration pour ce type d'union :

```C
struct x
{
    int type_tag;
    union
    {
      int x;
      float y;
    }
}
```

Consultez [Membres de structure et d'union](../c-language/structure-and-union-members.md) pour plus d'informations sur le référencement des unions.

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Déclarateurs et déclarations de variable](../c-language/declarators-and-variable-declarations.md)
