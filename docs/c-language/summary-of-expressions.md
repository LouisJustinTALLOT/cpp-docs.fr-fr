---
title: Récapitulatif des expressions
ms.date: 06/14/2018
ms.assetid: ed448953-687a-4b57-a1cb-12967bd770ea
ms.openlocfilehash: 1660690c6d36aa1dbdc025d6afe92e19ff941463
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87220832"
---
# <a name="summary-of-expressions"></a>Récapitulatif des expressions

*primary-expression*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*identificateur*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*suivantes*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*littéral de chaîne*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**(**  *expression*  **)**

*expression*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*assignation-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*expression*  **,**  *assignation-expression*

*expression constante*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*expression conditionnelle*

*expression conditionnelle*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Expression OU logique*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*logique-or-expression*  **?**  *expression*  **:**  *Conditional-expression*

*assignment-expression* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*expression conditionnelle*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*unary-expression* *assignment-operator* *assignment-expression*

*postfix-expression*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*primary-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*postfix-expression*  **[**  *expression*  **]**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*postfix-expression*  **(**  *argument-expression-List*<sub>OPT</sub> **)**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*postfix-expression*  **.**  *identificateur*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*postfix-expression* **->** *identificateur*    <br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Postfix-expression*  **++**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Postfix-expression*  **--**

*argument-expression-list* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*assignation-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*argument-expression-List*  **,**  *assignation-expression*

*unary-expression*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Postfix-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**++**  *unaire-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**--**  *unaire-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*unaire, opérateur*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*cast-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`sizeof`**  *unaire-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**sizeof (**  *type-name*  **)**

*unary-operator* : un des éléments suivants :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**&****&#42;** **+** **-** **~** **!**

*Cast-expression*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*unary-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**(**  *type-name*  **)**  *Cast-expression*

*multiplicatif-expression*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*cast-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*multiplicative-expression*  **&#42;**  *cast-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*multiplicatif-expression* **/** *Cast-expression*    <br/>
&nbsp;&nbsp;&nbsp;&nbsp;*multiplicatif-expression* **%** *Cast-expression*    

*additive-expression*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*multiplicative-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*additive-expression* **+** *multiplicatif-expression*    <br/>
&nbsp;&nbsp;&nbsp;&nbsp;*additive-expression* **-** *multiplicatif-expression*    

*shift-expression* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*additive-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Shift-expression*   * *Shift-expression * additive-expression \<\<**  *additive-expression*<br/> &nbsp; &nbsp; &nbsp; &nbsp; * **>>** *additive-expression*  

*Relational-expression*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Shift-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;Relational *-expression* * * \<**  *shift-expression*<br/> &nbsp; &nbsp; relationnel &nbsp; -expression * Shift-expression relationnelle-expression * * relationnel-expression * Shift-expression &nbsp; * **>** *shift-expression* <br/> &nbsp; &nbsp; &nbsp; &nbsp;   ** \<=**  *shift-expression*<br/> &nbsp; &nbsp; &nbsp; &nbsp; * **>=** *shift-expression*    

*equality-expression* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*relational-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*égalité-expression* **==** *relationnelle-expression*    <br/>
&nbsp;&nbsp;&nbsp;&nbsp;*equality-expression*  **!=**  *relational-expression*

*AND-expression* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*égalité-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*And-expression* **&** *égalité-expression*    

*exclusive-OR-expression* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*AND-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*exclusive-or-expression* **^** *And-expression*    

*inclusif ou expression*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*exclusive-OR-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*inclusive-OR-expression*  **&#124;**  *exclusive-OR-expression*

*expression and logique*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*inclusif ou expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*expression* **&&** and logique *inclusif ou expression*    

*logique-or-expression*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*expression AND logique*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;Logical- *or-expression* **&#124;&#124;** *logique-and-expression*    

## <a name="see-also"></a>Voir aussi

- [Grammaire de la structure des expressions](../c-language/phrase-structure-grammar.md)
