---
title: Résumé des instructions
ms.date: 11/04/2016
ms.assetid: ce45d2fe-ec0e-459f-afb1-80ab6a7f0239
ms.openlocfilehash: 1a230ca7d998316d2ec96e76b54ac60575acd2ee
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74856993"
---
# <a name="summary-of-statements"></a>Résumé des instructions

*instruction*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*instruction étiquetée*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Compound-Statement*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*expression-statement*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*instruction de sélection*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*itération-instruction*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*instruction Jump*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*try-except-Statement*  / \* , spécifique à Microsoft\*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*try-finally-instruction*  / \* spécifique à Microsoft\*/

*instruction Jump*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**goto***identificateur*Goto **;**    <br/>
&nbsp;&nbsp;&nbsp;&nbsp;**pouvoir**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**break ;**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**return** *expression*<sub>opt</sub> **;**

*Compound-Statement*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**{** *declaration-list*<sub>OPT</sub> *Statement-List*<sub>OPT</sub> **}**

*declaration-list* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*déclaré*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*declaration-list* *declaration*

*statement-list*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*gestion*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*statement-list* *statement*

*instruction d’expression*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*expression*<sub>opt</sub> **;**

*itération-instruction* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*instruction* **while (***expression***)**      <br/>
&nbsp;&nbsp;&nbsp;&nbsp;**do**  *statement*  **while (**  *expression*  **) ;**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**for (***expression*<sub>OPT</sub> **;** *expression opt*<sub>opt</sub> **;** *expression*<sub>OPT</sub> **)** ( *instruction* )  

*instruction de sélection*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*instruction* **if (***expression***)**      <br/>
&nbsp;&nbsp;&nbsp;&nbsp;*instruction* **if (***expression***)***statement***else**          <br/>
&nbsp;&nbsp;&nbsp;&nbsp;*instruction* **switch (***expression***)**      

*instruction étiquetée*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*identificateur*  **:**  *instruction*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**case**  *constant-expression*  **:**  *Statement*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**default :**  *statement*

*try-except-Statement*:/\* spécifique à Microsoft\*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**__try composée**  *-* instruction **__except (**  *expression*  **)**  *Compound-Statement*

*try-finally-Statement*:\* /spécifique à Microsoft\*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**__try**  *compound-statement* **__finally**  *compound-statement*

## <a name="see-also"></a>Voir aussi

[Grammaire de la structure des expressions](../c-language/phrase-structure-grammar.md)
