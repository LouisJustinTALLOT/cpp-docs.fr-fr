---
title: Instruction composite (C) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- compound statements
- statements, compound
ms.assetid: 32d1bf86-cbbc-42a9-ba3a-1be1c6c7754c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 11197f19047b0058f5401b9419f0f353c44c91d6
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46063619"
---
# <a name="compound-statement-c"></a>Instruction composite (C)

Une instruction composée (également appelée « bloc ») correspond généralement au corps d'une autre instruction, telle que l'instruction **if**. L'article [Déclarations et types](../c-language/declarations-and-types.md) décrit la forme et la signification des déclarations qui peuvent figurer en tête d'une instruction composée.

## <a name="syntax"></a>Syntaxe

*compound-statement*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**{** *declaration-list*<sub>opt</sub> *statement-list*<sub>opt</sub> **}**

*declaration-list* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*declaration*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*declaration-list* *declaration*

*statement-list*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*statement*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*statement-list* *statement*

S'il existe des déclarations, elles doivent précéder toutes les instructions. La portée de chaque identificateur déclaré au début d'une instruction composée s'étend de son point de déclaration jusqu'à la fin du bloc. Elle est visible dans l'ensemble du bloc à moins qu'une déclaration du même identificateur existe dans un bloc interne.

Les identificateurs figurant dans une instruction composée sont supposés **auto** à moins qu'ils soient explicitement déclarés autrement à l'aide de **register**, **static** ou `extern`, à l'exception des fonctions, qui peuvent être `extern` uniquement. Vous pouvez omettre le spécificateur `extern` dans les déclarations de fonction et la fonction sera néanmoins `extern`.

Le stockage n'est pas alloué et l'initialisation n'est pas autorisée si une variable ou une fonction est déclarée dans une instruction composée au moyen de la classe de stockage `extern`. La déclaration fait référence à une variable ou fonction externe définie ailleurs.

Les variables déclarées dans un bloc avec le mot clé **auto** ou **register** sont réaffectées et, si nécessaire, initialisées chaque fois que l'instruction composée est écrite. Ces variables ne sont pas définies une fois que vous quittez l'instruction composée. Si une variable déclarée dans un bloc possède l'attribut **static**, elle est initialisée au début de l'exécution du programme et conserve sa valeur tout au long du programme. Consultez [Classes de stockage](../c-language/c-storage-classes.md) pour plus d'informations sur l'attribut **static**.

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