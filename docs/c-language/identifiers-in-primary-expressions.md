---
title: Identificateurs dans les expressions primaires
ms.date: 11/04/2016
helpviewer_keywords:
- identifiers, designating objects
ms.assetid: d4602fe6-e7e6-40cc-9823-3b1ebf5d3d38
ms.openlocfilehash: 053720bcdf635a7e09363712259b558d93a2972c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62233084"
---
# <a name="identifiers-in-primary-expressions"></a>Identificateurs dans les expressions primaires

Les identificateurs peuvent avoir un **float**type intégral `enum`, `struct`flottant,,, **Union**, tableau, pointeur ou fonction. Un identificateur est une expression primaire à condition d'avoir été déclaré comme désignant un objet (auquel cas il s'agit d'une l-value) ou comme fonction (auquel cas il s'agit d'un indicateur de fonction). Pour obtenir une définition de lvalue, consultez [Expressions lvalue et rvalue](../c-language/l-value-and-r-value-expressions.md).

La valeur de pointeur représentée par un identificateur de tableau n’étant pas une variable, un identificateur de tableau ne peut pas former l’opérande gauche d’une opération d’assignation et n’est donc pas une l-value modifiable.

Un identificateur déclaré comme fonction représente un pointeur dont la valeur est l'adresse de la fonction. Le pointeur adresse une fonction qui retourne une valeur d'un type spécifié. Ainsi, les identificateurs de fonction ne peuvent pas non plus être des lvalues dans les opérations d'assignation. Pour plus d’informations, consultez [Identificateurs](../c-language/c-identifiers.md).

## <a name="see-also"></a>Voir aussi

[Expressions primaires C](../c-language/c-primary-expressions.md)
