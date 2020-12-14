---
description: En savoir plus sur les conversions de Type-Cast
title: Conversions de type cast
ms.date: 11/04/2016
helpviewer_keywords:
- data type conversion [C++], type-cast conversions
- conversions [C++], type-cast
- type casts
- explicit type conversions
- type casts [C++], about type-cast conversion
- type-cast conversions [C++]
ms.assetid: 57ab5902-f12f-4326-a2f6-6282f1d4025a
ms.openlocfilehash: dfa3e54320c416e4bd69cca06d2677def6244247
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97242910"
---
# <a name="type-cast-conversions"></a>Conversions de type cast

Vous pouvez utiliser des casts de type pour convertir explicitement les types.

**Syntaxe**

*Cast-expression*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*expression unaire*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**(**  *type-name*  **)**  *Cast-expression*

*nom de type*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*specifier-qualifier-list* *abstract-declarator*<sub>opt</sub>

*type-name* est un type et *cast-expression* est une valeur à convertir en ce type. Une expression avec un cast de type n'est pas une l-value. *cast-expression* est converti comme s'il avait été assigné à une variable de type *type-name*. Les règles de conversion pour les assignations (décrites dans [Conversions d'assignation](../c-language/assignment-conversions.md)) s'appliquent également aux casts de type. Le tableau suivant indique les types pouvant être castés en un type donné.

### <a name="legal-type-casts"></a>Casts de type autorisés

|Types de destination|Sources possibles|
|-----------------------|-----------------------|
|Types intégraux|Tout type entier ou type à virgule flottante ou pointeur vers un objet|
|Virgule flottante|Tout type arithmétique|
|Pointeur vers un objet ou ( **`void`** <strong>\*</strong> )|Tout type entier, ( **`void`** <strong>\*</strong> ), pointeur vers un objet ou pointeur fonction|
|Pointeur fonction|Tout type intégral, pointeur vers un objet ou pointeur fonction|
|Structure, union ou tableau|None|
|Type void|Tout type|

Tout identificateur peut être casté en **`void`** type. Toutefois, si le type spécifié dans une expression de cast de type n’est pas **`void`** , l’identificateur converti en ce type ne peut pas être une **`void`** expression. Toute expression peut être convertie en **`void`** , mais une expression de type **`void`** ne peut pas être convertie en un autre type. Par exemple, une fonction avec un **`void`** type de retour ne peut pas avoir son retour converti en un autre type.

Notez qu’une **`void`** <strong>\*</strong> expression a un pointeur de type vers **`void`** , et non type **`void`** . Si un objet est casté en **`void`** type, l’expression obtenue ne peut pas être assignée à un élément. De même, un objet type cast n'est pas une l-value acceptable. Ainsi, aucune assignation ne peut devenir un objet type cast.

**Spécifique à Microsoft**

Un cast de type peut être une expression l-value tant que la taille de l'identificateur ne change pas. Pour plus d'informations sur les expressions l-value, consultez [Expressions L-Value et R-Value](../c-language/l-value-and-r-value-expressions.md).

**FIN spécifique à Microsoft**

Vous pouvez convertir une expression en type **`void`** avec un cast, mais l’expression résultante ne peut être utilisée que si aucune valeur n’est requise. Un pointeur d’objet converti vers **`void`** <strong>\*</strong> le type d’origine et lui revient à sa valeur d’origine.

## <a name="see-also"></a>Voir aussi

[Conversions de type](../c-language/type-conversions-c.md)
