---
title: Conversions de type cast | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- data type conversion [C++], type-cast conversions
- conversions [C++], type-cast
- type casts
- explicit type conversions
- type casts [C++], about type-cast conversion
- type-cast conversions [C++]
ms.assetid: 57ab5902-f12f-4326-a2f6-6282f1d4025a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0d040f3ce29f78b614c60d815cac16362374bddb
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/29/2018
ms.locfileid: "43205608"
---
# <a name="type-cast-conversions"></a>Conversions de type cast
Vous pouvez utiliser des casts de type pour convertir explicitement les types.  
  
 **Syntaxe**  
  
 *cast-expression* :  
 *expression unaire*  
  
 **(**  *type-name*  **)**  *cast-expression*  
  
 *type-name* :  
 *specifier-qualifier-list abstract-declarator* opt  
  
 *type-name* est un type et *cast-expression* est une valeur à convertir en ce type. Une expression avec un cast de type n'est pas une l-value. *cast-expression* est converti comme s'il avait été assigné à une variable de type *type-name*. Les règles de conversion pour les assignations (décrites dans [Conversions d'assignation](../c-language/assignment-conversions.md)) s'appliquent également aux casts de type. Le tableau suivant indique les types pouvant être castés en un type donné.  
  
### <a name="legal-type-casts"></a>Casts de type autorisés  
  
|Types de destination|Sources possibles|  
|-----------------------|-----------------------|  
|Types intégraux|Tout type entier ou type à virgule flottante ou pointeur vers un objet|  
|Virgule flottante|Tout type arithmétique|  
|Pointeur vers un objet, ou (**void** <strong>\*</strong>)|Type entier, (**void** <strong>\*</strong>), pointeur vers un objet ou pointeur fonction|  
|Pointeur fonction|Tout type intégral, pointeur vers un objet ou pointeur fonction|  
|Structure, union ou tableau|Aucun.|  
|Type void|Tout type|  
  
 Tout identificateur peut être converti en type `void`. Toutefois, si le type spécifié dans une expression cast-type n'est pas `void`, l'identificateur converti en ce type ne peut pas être une expression `void`. Toute expression peut être convertie en `void`, mais une expression de type `void` ne peut pas être castée en un autre type. Par exemple, une fonction avec un type de retour `void` ne peut pas avoir son retour converti en un autre type.  
  
 Notez qu’une expression **void** <strong>\*</strong> a un pointeur de type vers `void`, mais pas le type `void`. Si un objet est converti en type `void`, l'expression obtenue ne peut pas être assignée à un élément. De même, un objet type cast n'est pas une l-value acceptable. Ainsi, aucune assignation ne peut devenir un objet type cast.  
  
 **Section spécifique à Microsoft**  
  
 Un cast de type peut être une expression l-value tant que la taille de l'identificateur ne change pas. Pour plus d'informations sur les expressions l-value, consultez [Expressions L-Value et R-Value](../c-language/l-value-and-r-value-expressions.md).  
  
 **FIN de la section spécifique à Microsoft**  
  
 Vous pouvez convertir une expression en un type `void` avec un cast, mais l'expression obtenue peut être utilisée uniquement si une valeur n'est pas requise. Un pointeur d’objet converti en **void** <strong>\*</strong> et retourné au type d’origine retourne à sa valeur d’origine.  
  
## <a name="see-also"></a>Voir aussi  
 [Conversions de type](../c-language/type-conversions-c.md)