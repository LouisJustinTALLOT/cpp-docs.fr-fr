---
title: Résumé des instructions C
description: Résumé de la grammaire de l’instruction dans l’implémentation Microsoft C.
ms.date: 08/24/2020
ms.assetid: ce45d2fe-ec0e-459f-afb1-80ab6a7f0239
ms.openlocfilehash: 448aa7ccb8c78e20ef09f47f4a3c77f447c76f60
ms.sourcegitcommit: efc8c32205c9d610f40597556273a64306dec15d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/26/2020
ms.locfileid: "88898392"
---
# <a name="summary-of-c-statements"></a>Résumé des instructions C

*`statement`*:<br/>
&emsp;*`labeled-statement`*<br/>
&emsp;*`compound-statement`*<br/>
&emsp;*`expression-statement`*<br/>
&emsp;*`selection-statement`*<br/>
&emsp;*`iteration-statement`*<br/>
&emsp;*`jump-statement`*<br/>
&emsp;*`try-except-statement`* /\* Spécifique à Microsoft \*/<br/>
&emsp;*`try-finally-statement`* /\* Spécifique à Microsoft \*/

*`jump-statement`*:<br/>
&emsp;**`goto`** *`identifier`* **`;`**<br/>
&emsp;**`continue ;`**<br/>
&emsp;**`break ;`**<br/>
&emsp;**`return`***`expression`* <sub>OPT</sub>**`;`**<br/>
&emsp;**`__leave ;`** /\*Spécifique à Microsoft<sup>1</sup>\*/

*`compound-statement`*:<br/>
&emsp;**`{`***`declaration-list`* <sub>opt</sub> opt opt *`statement-list`* <sub>opt</sub>**`}`**

*`declaration-list`*:<br/>
&emsp;*`declaration`*<br/>
&emsp;*`declaration-list`* *`declaration`*

*`statement-list`*:<br/>
&emsp;*`statement`*<br/>
&emsp;*`statement-list`* *`statement`*

*`expression-statement`*:<br/>
&emsp;*`expression`*<sub>OPT</sub>**`;`**

*`iteration-statement`*:<br/>
&emsp;**`while (`** *`expression`* **`)`** *`statement`*<br/>
&emsp;**`do`** *`statement`* **`while (`** *`expression`* **`) ;`**<br/>
&emsp;**`for (`***`expression`* <sub>opt</sub> **`;`** OPT *`expression`* <sub>OPT</sub> **`;`** *`expression`* <sub>opt</sub> opt **`)`***`statement`*

*`selection-statement`*:<br/>
&emsp;**`if (`** *`expression`* **`)`** *`statement`*<br/>
&emsp;**`if (`** *`expression`* **`)`** *`statement`* **`else`** *`statement`*<br/>
&emsp;**`switch (`** *`expression`* **`)`** *`statement`*

*`labeled-statement`*:<br/>
&emsp;*`identifier`* **`:`** *`statement`*<br/>
&emsp;**`case`** *`constant-expression`* **`:`** *`statement`*<br/>
&emsp;**`default :`** *`statement`*

*`try-except-statement`*:/ \* Spécifique à Microsoft \*/<br/>
&emsp;**`__try`** *`compound-statement`* **`__except (`** *`expression`* **`)`** *`compound-statement`*

*`try-finally-statement`*:/ \* Spécifique à Microsoft \*/<br/>
&emsp;**`__try`** *`compound-statement`* **`__finally`** *`compound-statement`*

1 le **`__leave`** mot clé est valide uniquement dans le **`__try`** bloc d’un *`try-except-statement`* ou d’un *`try-finally-statement`* .

## <a name="see-also"></a>Voir aussi

[Grammaire de la structure des phrases](../c-language/phrase-structure-grammar.md)
