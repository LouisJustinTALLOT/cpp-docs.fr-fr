---
title: Résumé des instructions
ms.date: 11/04/2016
ms.assetid: ce45d2fe-ec0e-459f-afb1-80ab6a7f0239
ms.openlocfilehash: 122c79b53a8af8a384097dec51a14746a090b1cf
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87220793"
---
# <a name="summary-of-statements"></a>Résumé des instructions

*instruction*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*instruction étiquetée*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Compound-Statement*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*expression-statement*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*instruction de sélection*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*itération-instruction*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*instruction Jump*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*try-except-Statement*  / \* Spécifique à Microsoft\*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*try-finally-Statement*  / \* Spécifique à Microsoft\*/

*instruction Jump*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`goto`**  *identificateur*  **;**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**pouvoir**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**break ;**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`return`***expression*<sub>OPT</sub> **;**

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
&nbsp;&nbsp;&nbsp;&nbsp;**`do`**  *instruction*  **while (**  *expression*  **);**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**for (***expression*<sub>OPT</sub> **;** *expression opt*<sub>opt</sub> **;** *expression*<sub>OPT</sub> **)** ( *instruction* )  

*instruction de sélection*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*instruction* **if (***expression***)**      <br/>
&nbsp;&nbsp;&nbsp;&nbsp;instruction **if (***expression***)***Statement* **`else`** *statement*          <br/>
&nbsp;&nbsp;&nbsp;&nbsp;*instruction* **switch (***expression***)**      

*instruction étiquetée*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*identificateur*  **:**  *instruction*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`case`**  *constant-expression*  **:**  *instruction*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**default :**  *statement*

*try-except-Statement*:/ \* spécifique à Microsoft\*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**__try composée**  *-* instruction **__except (**  *expression*  **)**  *Compound-Statement*

*try-finally-Statement*:/ \* spécifique à Microsoft\*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**__try**composée *-* instruction composée **`__finally`** *-* Statement    

## <a name="see-also"></a>Voir aussi

[Grammaire de la structure des expressions](../c-language/phrase-structure-grammar.md)
