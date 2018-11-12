---
title: Opérateurs d'assignation C
ms.date: 06/14/2018
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
ms.openlocfilehash: 5080f390d302840e9e7b349cf1c21ab618ae48db
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50657026"
---
# <a name="c-assignment-operators"></a>Opérateurs d'assignation C

Une opération d’assignation assigne la valeur de l’opérande droit à l’emplacement de stockage nommé par l’opérande gauche. Par conséquent, l'opérande gauche d'une opération d'assignation doit être une l-value modifiable. Après l’assignation, une expression d’assignation a la valeur de l’opérande gauche mais n’est pas une l-value.

## <a name="syntax"></a>Syntaxe

*assignment-expression* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*conditional-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*unary-expression* *assignment-operator* *assignment-expression*

*assignment-operator* : un des éléments suivants :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**=** **\*=** **/=** **%=** **+=** **-=** **\<\<=** **>>=** **&=** **^=** **|=**

Les opérateurs d'assignation en langage C peuvent transformer et assigner des valeurs dans une même opération. C propose les opérateurs d'assignation suivants :

|Opérateur|Opération effectuée|
|--------------|-------------------------|
|**=**|Assignation simple|
|**&#42;=**|Assignation de multiplication|
|**/=**|Assignation de division|
|**%=**|Assignation de reste|
|**+=**|Assignation d'addition|
|**-=**|Assignation de soustraction|
|**<\<=**|Assignation de décalage vers la gauche|
|**>>=**|Assignation de décalage vers la droite|
|**&=**|Assignation d'opération AND au niveau du bit|
|**^=**|Assignation d'opération OR exclusive au niveau du bit|
|**&#124;=**|Assignation d'opération OR inclusive au niveau du bit|

Dans l'assignation, le type de la valeur droite est converti pour correspondre au type de la valeur gauche, et la valeur est stockée dans l'opérande gauche après l'assignation. L’opérande gauche ne doit pas être un tableau, une fonction ni une constante. Le chemin d’accès de conversion spécifique, qui dépend des deux types, est décrit en détail dans [Conversions de type](../c-language/type-conversions-c.md).

## <a name="see-also"></a>Voir aussi

- [Opérateurs d’assignation](../cpp/assignment-operators.md)