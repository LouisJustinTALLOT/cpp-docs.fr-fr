---
title: Déclarations typedef
ms.date: 11/04/2016
helpviewer_keywords:
- declarations, typedef
- typedef declarations
- types [C], declarations
ms.assetid: e92a3b82-9269-4bc6-834a-6f431ccac83e
ms.openlocfilehash: b4bf7bc82cdf792e5a23f6d5533cc4d800fe4252
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62346104"
---
# <a name="typedef-declarations"></a>Déclarations typedef

Une déclaration typedef est une déclaration avec typedef comme classe de stockage. Le déclarateur devient un nouveau type. Vous pouvez utiliser des déclarations typedef pour construire des noms plus courts ou plus explicites pour des types déjà définis par C ou pour des types que vous avez déclarés. Les noms typedef vous permettent d'encapsuler des détails d'implémentation susceptibles de changer.

Une déclaration typedef est interprétée de la même façon qu'une déclaration de fonction ou variable, mais l'identificateur, au lieu d'assumer le type spécifié par la déclaration, devient un synonyme du type.

## <a name="syntax"></a>Syntaxe

*déclaration*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*declaration-specifiers init-declarator-list*<sub>opt</sub> **;**

*declaration-specifiers* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*déclaration de Storage-Class-specifier-Specifiers*<sub>OPT</sub> <br/>
&nbsp;&nbsp;&nbsp;&nbsp;*type-specifier DECLARATION-Specifiers*<sub>OPT</sub> <br/>
&nbsp;&nbsp;&nbsp;&nbsp;*déclaration de qualificateur de type-spécificateurs*<sub>OPT</sub>

*storage-class-specifier* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**typedef**

*type-specifier* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**nullité**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**Char**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**Résumé**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**tiers**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**long**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**dissocié**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**Cliquer**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**abonné**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**non signé**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*struct-or-Union-specifier*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*enum-specifier*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*typedef-name*

*nom de typedef*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*identificateur*

Notez qu'une déclaration typedef ne crée pas de types. Elle crée des synonymes pour des types existants ou des noms pour des types qui peuvent être spécifiés d'autres manières. Lorsqu'un nom typedef est utilisé comme spécificateur de type, il peut être combiné avec certains spécificateurs de type, mais pas d'autres. Les modificateurs acceptables sont **const** et `volatile`.

Les noms typedef partagent l'espace de noms avec les identificateurs ordinaires (pour plus d'informations, consultez [Espaces de noms](../c-language/name-spaces.md)). Par conséquent, un programme peut avoir un nom typedef et un identificateur de portée locale du même nom. Par exemple :

```C
typedef char FlagType;

int main()
{
}

int myproc( int )
{
    int FlagType;
}
```

Lors de la déclaration d'un identificateur de portée locale du même nom qu'un typedef, ou lors de la déclaration d'un membre d'une structure ou d'une union dans la même portée ou dans une portée interne, le spécificateur de type doit être spécifié. Cet exemple illustre cette contrainte :

```C
typedef char FlagType;
const FlagType x;
```

Pour réutiliser le nom `FlagType` pour un identificateur, un membre de structure ou un membre d'union, le type doit être fourni :

```C
const int FlagType;  /* Type specifier required */
```

Il ne suffit pas de dire

```C
const FlagType;      /* Incomplete specification */
```

car `FlagType` est considéré comme faisant partie du type, et non comme un identificateur qui est redéclaré. Cette déclaration est considérée comme étant une déclaration non conforme comme

```C
int;  /* Illegal declaration */
```

Vous pouvez déclarer tout type avec typedef, y compris des types pointeur, fonction et tableau. Vous pouvez déclarer un nom typedef pour un pointeur vers une structure ou un type union avant de définir la structure ou le type union, tant que la définition a la même visibilité que la déclaration.

Les noms typedef peuvent servir à améliorer la lisibilité du code. Les trois déclarations suivantes de `signal` spécifient exactement le même type, la première sans utiliser aucun nom typedef.

```C
typedef void fv( int ), (*pfv)( int );  /* typedef declarations */

void ( *signal( int, void (*) (int)) ) ( int );
fv *signal( int, fv * );   /* Uses typedef type */
pfv signal( int, pfv );    /* Uses typedef type */
```

## <a name="examples"></a>Exemples

Les exemples suivants illustrent des déclarations typedef :

```C
typedef int WHOLE; /* Declares WHOLE to be a synonym for int */
```

Notez que `WHOLE` pourrait maintenant être utilisé dans une déclaration de variable comme `WHOLE i;` ou `const WHOLE i;`. Toutefois, la déclaration `long WHOLE i;` serait non conforme.

```C
typedef struct club
{
    char name[30];
    int size, year;
} GROUP;
```

Cette instruction déclare `GROUP` comme type de structure avec trois membres. Étant donné qu'une balise de structure, `club`, est également spécifiée, vous pouvez utiliser le nom typedef (`GROUP`) ou la balise de structure dans les déclarations. Vous devez utiliser le mot clé struct avec la balise et vous ne pouvez pas utiliser le mot clé struct avec le nom typedef.

```C
typedef GROUP *PG; /* Uses the previous typedef name
                      to declare a pointer            */
```

Le type `PG` est déclaré comme pointeur vers le type `GROUP`, qui à son tour est défini comme un type structure.

```C
typedef void DRAWF( int, int );
```

Cet exemple fournit le type `DRAWF` pour une fonction qui ne retourne aucune valeur et qui accepte deux arguments int. Cela signifie, par exemple, que la déclaration

```C
DRAWF box;
```

équivaut à la déclaration

```C
void box( int, int );
```

## <a name="see-also"></a>Voir aussi

[Déclarations et types](../c-language/declarations-and-types.md)
