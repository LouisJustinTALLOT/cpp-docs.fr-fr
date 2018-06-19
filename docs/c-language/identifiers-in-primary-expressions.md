---
title: Identificateurs dans les expressions primaires | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- identifiers, designating objects
ms.assetid: d4602fe6-e7e6-40cc-9823-3b1ebf5d3d38
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7d9f39f7ce609ea06a2d991ac79c2b1151625bc1
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32384757"
---
# <a name="identifiers-in-primary-expressions"></a>Identificateurs dans les expressions primaires
Les identificateurs peuvent avoir un type intégral, **float**, `enum`, `struct`, **union**, tableau, pointeur ou fonction. Un identificateur est une expression primaire à condition d'avoir été déclaré comme désignant un objet (auquel cas il s'agit d'une l-value) ou comme fonction (auquel cas il s'agit d'un indicateur de fonction). Pour obtenir une définition de lvalue, consultez [Expressions lvalue et rvalue](../c-language/l-value-and-r-value-expressions.md).  
  
 La valeur de pointeur représentée par un identificateur de tableau n’étant pas une variable, un identificateur de tableau ne peut pas former l’opérande gauche d’une opération d’assignation et n’est donc pas une l-value modifiable.  
  
 Un identificateur déclaré comme fonction représente un pointeur dont la valeur est l'adresse de la fonction. Le pointeur adresse une fonction qui retourne une valeur d'un type spécifié. Ainsi, les identificateurs de fonction ne peuvent pas non plus être des lvalues dans les opérations d'assignation. Pour plus d’informations, consultez [Identifiers](../c-language/c-identifiers.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Expressions primaires C](../c-language/c-primary-expressions.md)