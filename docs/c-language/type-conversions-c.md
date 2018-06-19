---
title: Conversions de type (C) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- conversions, type
- type conversion
- converting types
- integral promotions
- type casts, when performed
ms.assetid: d130ee7c-03c3-48f4-af7b-1fdba0d3b086
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e06da627d18fa643cb64fda870c986264c573641
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32387237"
---
# <a name="type-conversions-c"></a>Conversions de type (C)
Les conversions de type dépendent de l’opérateur spécifié et du type de l’opérande ou des opérateurs. Les conversions de type sont effectuées dans les cas suivants :  
  
-   Lorsqu'une valeur d'un type est assignée à une variable d'un type différent ou qu'un opérateur convertit le type de son opérande ou de ses opérandes avant d'exécuter une opération  
  
-   Lorsqu'une valeur d'un type est explicitement convertie en un type différent  
  
-   Lorsqu'une valeur est passée comme argument à une fonction ou lorsqu'un type est retourné depuis une fonction  
  
 Un caractère, un entier court ou un champ de bits entier, tous signés ou non signés, ou un objet de type énumération, peuvent être utilisés dans une expression partout où un entier peut être utilisé. Si `int` peut représenter toutes les valeurs du type d'origine, la valeur est convertie en `int` ; sinon, elle est convertie en `unsigned int`. Ce processus porte le nom de « promotion d'un intégral ». Les promotions d'un intégral conservent la valeur. Autrement dit, vous pouvez être sûr que la valeur après la promotion est identique à celle précédant la promotion. Pour plus d'informations, consultez [Conversions arithmétiques ordinaires](../c-language/usual-arithmetic-conversions.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Expressions et assignations](../c-language/expressions-and-assignments.md)