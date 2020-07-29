---
title: Instruction composite (C)
ms.date: 11/04/2016
helpviewer_keywords:
- compound statements
- statements, compound
ms.assetid: 32d1bf86-cbbc-42a9-ba3a-1be1c6c7754c
ms.openlocfilehash: 93f7fd24049c744874fb0ab3bda37eedef3a139a
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87200580"
---
# <a name="compound-statement-c"></a>Instruction composite (C)

Une instruction composée (également appelée « bloc ») apparaît généralement en tant que corps d’une autre instruction, telle que l' **`if`** instruction. L'article [Déclarations et types](../c-language/declarations-and-types.md) décrit la forme et la signification des déclarations qui peuvent figurer en tête d'une instruction composée.

## <a name="syntax"></a>Syntaxe

*Compound-Statement*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**{** *declaration-list*<sub>OPT</sub> *Statement-List*<sub>OPT</sub> **}**

*declaration-list* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*déclaré*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*declaration-list* *declaration*

*statement-list*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*gestion*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*statement-list* *statement*

S'il existe des déclarations, elles doivent précéder toutes les instructions. La portée de chaque identificateur déclaré au début d'une instruction composée s'étend de son point de déclaration jusqu'à la fin du bloc. Elle est visible dans l'ensemble du bloc à moins qu'une déclaration du même identificateur existe dans un bloc interne.

Les identificateurs dans une instruction composée sont présumés **`auto`** sauf s’ils sont explicitement déclarés avec **`register`** , **`static`** ou **`extern`** , à l’exception des fonctions, qui peuvent être uniquement **`extern`** . Vous pouvez ignorer le **`extern`** spécificateur dans les déclarations de fonction et la fonction sera toujours **`extern`** .

Le stockage n’est pas alloué et l’initialisation n’est pas autorisée si une variable ou une fonction est déclarée dans une instruction composée avec une classe de stockage **`extern`** . La déclaration fait référence à une variable ou fonction externe définie ailleurs.

Les variables déclarées dans un bloc avec le **`auto`** **`register`** mot clé ou sont réallouées et, si nécessaire, initialisées chaque fois que l’instruction composée est entrée. Ces variables ne sont pas définies une fois que vous quittez l'instruction composée. Si une variable déclarée à l’intérieur d’un bloc possède l' **`static`** attribut, la variable est initialisée lorsque l’exécution du programme commence et conserve sa valeur tout au long du programme. Pour plus d’informations sur, consultez [classes de stockage](../c-language/c-storage-classes.md) **`static`** .

L'exemple suivant illustre une instruction composée :

```
if ( i > 0 )
{
    line[i] = x;
    x++;
    i--;
}
```

Dans cet exemple, si `i` est supérieur à 0, toutes les instructions figurant dans l'instruction composée sont exécutées dans l'ordre.

## <a name="see-also"></a>Voir aussi

[Instructions](../c-language/statements-c.md)
