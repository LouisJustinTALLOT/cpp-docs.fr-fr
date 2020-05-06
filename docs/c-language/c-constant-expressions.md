---
title: Expressions constantes C
ms.date: 06/14/2018
helpviewer_keywords:
- constant expressions, syntax
- constant expressions
- expressions [C++], constant
ms.assetid: d48a6c47-e44c-4be2-9c8b-7944c7ef8de7
ms.openlocfilehash: f6984c47ef8acde462a8e92e01b72ef26a61eddc
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62325739"
---
# <a name="c-constant-expressions"></a>Expressions constantes C

Une expression constante est évaluée au moment de la compilation, et non au moment de l'exécution, et elle peut être utilisée partout où une constante peut être utilisée. L'expression constante doit être évaluée en une constante qui est comprise dans la plage des valeurs représentables pour ce type. Les opérandes d'une expression constante peuvent être des constantes entières, des constantes caractère, des constantes à virgule flottante, des constantes d'énumération, des casts de type, des expressions **sizeof** et d'autres expressions constantes.

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
&nbsp;&nbsp;&nbsp;&nbsp;**=****&#42;** **/=** **%=** = **+=** **-=** **&#124;** = ** \< \< ** **>>=** **&=** **^=**

Les éléments non terminaux pour les déclarateurs de struct, l’énumérateur, le déclarateur direct, le déclarateur direct-abstract et l’instruction étiquetée contiennent l’élément non terminal *constant-expression*.

Une expression constante intégrale doit être utilisée pour spécifier la taille d’un membre champ de bits d’une structure, la valeur d’une constante d’énumération, la taille d’un tableau ou la valeur d’une constante **case**.

Les expressions constantes utilisées dans les directives de préprocesseur sont soumises à des restrictions supplémentaires. Par conséquent, elles portent le nom d'« expressions constantes restreintes ». Une expression constante restreinte ne peut pas contenir d'expression **sizeof**, de constantes d'énumération, de casts de type en tout type, ni de constantes de type flottant. Elle peut toutefois contenir l’expression constante spéciale **définie (** _identifier_ **)**.

## <a name="see-also"></a>Voir aussi

- [Opérandes et expressions](../c-language/operands-and-expressions.md)
