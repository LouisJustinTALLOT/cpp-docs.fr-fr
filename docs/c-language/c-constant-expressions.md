---
title: Expressions constantes C
ms.date: 06/14/2018
helpviewer_keywords:
- constant expressions, syntax
- constant expressions
- expressions [C++], constant
ms.assetid: d48a6c47-e44c-4be2-9c8b-7944c7ef8de7
ms.openlocfilehash: 38d4eff6cf764a30bf409032ac692189d1300315
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87213734"
---
# <a name="c-constant-expressions"></a>Expressions constantes C

Une expression constante est évaluée au moment de la compilation, et non au moment de l'exécution, et elle peut être utilisée partout où une constante peut être utilisée. L'expression constante doit être évaluée en une constante qui est comprise dans la plage des valeurs représentables pour ce type. Les opérandes d’une expression constante peuvent être des constantes entières, des constantes caractère, des constantes à virgule flottante, des constantes d’énumération, des casts de type, des **`sizeof`** expressions et d’autres expressions constantes.

## <a name="syntax"></a>Syntaxe

*expression constante*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*expression conditionnelle*

*expression conditionnelle*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Expression OU logique*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*logique-or-expression* **?** *expression* **:** *Conditional-expression*

*expression*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*assignation-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*expression* **,** *assignation-expression*

*assignment-expression* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*expression conditionnelle*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*unary-expression* *assignment-operator* *assignment-expression*

*assignment-operator* : un des éléments suivants :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**=****&#42;=** **/=** **%=** **+=** **-=** **\<\<=** **>>=** **&=** **^=** **&#124;=**

Les éléments non terminaux pour les déclarateurs de struct, l’énumérateur, le déclarateur direct, le déclarateur direct-abstract et l’instruction étiquetée contiennent l’élément non terminal *constant-expression*.

Une expression constante intégrale doit être utilisée pour spécifier la taille d’un membre de champ de bits d’une structure, la valeur d’une constante d’énumération, la taille d’un tableau ou la valeur d’une **`case`** constante.

Les expressions constantes utilisées dans les directives de préprocesseur sont soumises à des restrictions supplémentaires. Par conséquent, elles portent le nom d'« expressions constantes restreintes ». Une expression constante restreinte ne peut pas contenir **`sizeof`** d’expressions, de constantes d’énumération, de casts de type vers tout type ou de constantes de type flottant. Elle peut toutefois contenir l’expression constante spéciale **définie (** _identifier_ **)**.

## <a name="see-also"></a>Voir aussi

- [Opérandes et expressions](../c-language/operands-and-expressions.md)
