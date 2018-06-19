---
title: Déclarations typedef | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- declarations, typedef
- typedef declarations
- types [C], declarations
ms.assetid: e92a3b82-9269-4bc6-834a-6f431ccac83e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 192f7ab037362219261852cfdb0a5eac53e5df9f
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32391650"
---
# <a name="typedef-declarations"></a>Déclarations typedef
Une déclaration typedef est une déclaration avec typedef comme classe de stockage. Le déclarateur devient un nouveau type. Vous pouvez utiliser des déclarations typedef pour construire des noms plus courts ou plus explicites pour des types déjà définis par C ou pour des types que vous avez déclarés. Les noms typedef vous permettent d'encapsuler des détails d'implémentation susceptibles de changer.  
  
 Une déclaration typedef est interprétée de la même façon qu'une déclaration de fonction ou variable, mais l'identificateur, au lieu d'assumer le type spécifié par la déclaration, devient un synonyme du type.  
  
## <a name="syntax"></a>Syntaxe  
 `declaration`:  
 *declaration-specifiers init-declarator-list* opt **;**  
  
 *declaration-specifiers* :  
 *storage-class-specifier declaration-specifiers* opt  
  
 *type-specifier declaration-specifiers* opt  
  
 *type-qualifier declaration-specifiers* opt  
  
 *storage-class-specifier* :  
 `typedef`  
  
 *type-specifier* :  
 **void**  
  
 **char**  
  
 **short**  
  
 **int**  
  
 **long**  
  
 **float**  
  
 **double**  
  
 **signed**  
  
 **unsigned**  
  
 *struct-or-union-specifier*  
  
 *enum-specifier*  
  
 *typedef-name*  
  
 *typedef-name* :  
 *identifier*  
  
 Notez qu'une déclaration typedef ne crée pas de types. Elle crée des synonymes pour des types existants ou des noms pour des types qui peuvent être spécifiés d'autres manières. Lorsqu'un nom typedef est utilisé comme spécificateur de type, il peut être combiné avec certains spécificateurs de type, mais pas d'autres. Les modificateurs acceptables sont **const** et `volatile`.  
  
 Les noms typedef partagent l'espace de noms avec les identificateurs ordinaires (pour plus d'informations, consultez [Espaces de noms](../c-language/name-spaces.md)). Par conséquent, un programme peut avoir un nom typedef et un identificateur de portée locale du même nom. Exemple :  
  
```  
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
  
```  
typedef char FlagType;  
const FlagType x;  
```  
  
 Pour réutiliser le nom `FlagType` pour un identificateur, un membre de structure ou un membre d'union, le type doit être fourni :  
  
```  
const int FlagType;  /* Type specifier required */  
```  
  
 Il ne suffit pas de dire  
  
```  
const FlagType;      /* Incomplete specification */  
```  
  
 car `FlagType` est considéré comme faisant partie du type, et non comme un identificateur qui est redéclaré. Cette déclaration est considérée comme étant une déclaration non conforme comme  
  
```  
int;  /* Illegal declaration */  
```  
  
 Vous pouvez déclarer tout type avec typedef, y compris des types pointeur, fonction et tableau. Vous pouvez déclarer un nom typedef pour un pointeur vers une structure ou un type union avant de définir la structure ou le type union, tant que la définition a la même visibilité que la déclaration.  
  
 Les noms typedef peuvent servir à améliorer la lisibilité du code. Les trois déclarations suivantes de `signal` spécifient exactement le même type, la première sans utiliser aucun nom typedef.  
  
```  
typedef void fv( int ), (*pfv)( int );  /* typedef declarations */  
  
void ( *signal( int, void (*) (int)) ) ( int );  
fv *signal( int, fv * );   /* Uses typedef type */  
pfv signal( int, pfv );    /* Uses typedef type */  
```  
  
## <a name="examples"></a>Exemples  
 Les exemples suivants illustrent des déclarations typedef :  
  
```  
typedef int WHOLE; /* Declares WHOLE to be a synonym for int */  
```  
  
 Notez que `WHOLE` pourrait maintenant être utilisé dans une déclaration de variable comme `WHOLE i;` ou `const WHOLE i;`. Toutefois, la déclaration `long WHOLE i;` serait non conforme.  
  
```  
typedef struct club   
{  
    char name[30];  
    int size, year;  
} GROUP;  
```  
  
 Cette instruction déclare `GROUP` comme type de structure avec trois membres. Étant donné qu'une balise de structure, `club`, est également spécifiée, vous pouvez utiliser le nom typedef (`GROUP`) ou la balise de structure dans les déclarations. Vous devez utiliser le mot clé struct avec la balise et vous ne pouvez pas utiliser le mot clé struct avec le nom typedef.  
  
```  
typedef GROUP *PG; /* Uses the previous typedef name   
                      to declare a pointer            */  
```  
  
 Le type `PG` est déclaré comme pointeur vers le type `GROUP`, qui à son tour est défini comme un type structure.  
  
```  
typedef void DRAWF( int, int );  
```  
  
 Cet exemple fournit le type `DRAWF` pour une fonction qui ne retourne aucune valeur et qui accepte deux arguments int. Cela signifie, par exemple, que la déclaration  
  
```  
DRAWF box;   
```  
  
 équivaut à la déclaration  
  
```  
void box( int, int );  
```  
  
## <a name="see-also"></a>Voir aussi  


