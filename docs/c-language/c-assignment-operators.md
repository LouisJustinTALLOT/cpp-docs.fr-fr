---
title: Opérateurs d'assignation C
description: Les opérateurs d’assignation de langage C standard, leur syntaxe et leur signification.
ms.date: 10/30/2020
helpviewer_keywords:
- remainder assignment operator (%=)
- '&= operator'
- bitwise-AND assignment operator
- operators [C], assignment
- operators [C], shift
- ^= operator, assignment operators
- += operator
- '>>= operator'
- '|= operator'
- division assignment operator
- subtraction operator
- right shift operators
- subtraction operator, C assignment operators
- = operator, assignment operators
- '*= operator'
- '>> operator'
- '%= operator'
- assignment operators, C
- = operator
- assignment operators
- assignment conversions
- -= operator
- multiplication assignment operator (*=)
- shift operators, right
- /= operator
- operator >>=, C assignment operators
- <<= operator
ms.assetid: 11688dcb-c941-44e7-a636-3fc98e7dac40
ms.openlocfilehash: 460e18772689de0d28fcfda3295a49b2f8a3c0d7
ms.sourcegitcommit: 4abc6c4c9694f91685cfd77940987e29a51e3143
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/03/2020
ms.locfileid: "93238510"
---
# <a name="c-assignment-operators"></a>Opérateurs d'assignation C

Une opération d’assignation assigne la valeur de l’opérande droit à l’emplacement de stockage nommé par l’opérande gauche. Par conséquent, l'opérande gauche d'une opération d'assignation doit être une l-value modifiable. Après l’assignation, une expression d’assignation a la valeur de l’opérande gauche mais n’est pas une l-value.

## <a name="syntax"></a>Syntaxe

*`assignment-expression`* :\
&emsp;*`conditional-expression`*\
&emsp;*`unary-expression`* *`assignment-operator`* *`assignment-expression`*

*`assignment-operator`* : un des éléments suivants :<br/>
&emsp;**`=`** **`*=`** **`/=`** **`%=`** **`+=`** **`-=`** **`<<=`** **`>>=`** **`&=`** **`^=`** **`|=`**

Les opérateurs d'assignation en langage C peuvent transformer et assigner des valeurs dans une même opération. C propose les opérateurs d'assignation suivants :

|Opérateur|Opération effectuée|
|--------------|-------------------------|
|**`=`**|Assignation simple|
|**`*=`**|Assignation de multiplication|
|**`/=`**|Assignation de division|
|**`%=`**|Assignation de reste|
|**`+=`**|Assignation d'addition|
|**`-=`**|Assignation de soustraction|
|**`<<=`**|Assignation de décalage vers la gauche|
|**`>>=`**|Assignation de décalage vers la droite|
|**`&=`**|Assignation d'opération AND au niveau du bit|
|**`^=`**|Assignation d'opération OR exclusive au niveau du bit|
|**`|=`**|Assignation d'opération OR inclusive au niveau du bit|

Dans l'assignation, le type de la valeur droite est converti pour correspondre au type de la valeur gauche, et la valeur est stockée dans l'opérande gauche après l'assignation. L’opérande gauche ne doit pas être un tableau, une fonction ni une constante. Le chemin d’accès de conversion spécifique, qui dépend des deux types, est décrit en détail dans [Conversions de type](../c-language/type-conversions-c.md).

## <a name="see-also"></a>Voir aussi

- [Opérateurs d’assignation](../cpp/assignment-operators.md)
