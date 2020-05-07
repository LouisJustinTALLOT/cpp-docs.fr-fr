---
title: Résumé des jetons
ms.date: 11/04/2016
ms.assetid: 2978cbf6-e66e-46fc-9938-caa052f2ccf7
ms.openlocfilehash: 4fdc1cf4c4e5a89cc9ecf029e64b6eb5422cd6a3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62345134"
---
# <a name="summary-of-tokens"></a>Résumé des jetons

*jeton*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*mot*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*identificateur*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*suivantes*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*littéral de chaîne*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*and*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*punctuator*

*preprocessing-token* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*nom-en-tête*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*identificateur*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*pp-numéro*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*caractère-constante*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*littéral de chaîne*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*operator punctuator*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;chaque caractère autre qu'un espace blanc qui ne peut pas être l'un des éléments ci-dessus

*nom-en-tête*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**\<**  *chemin d’accès-spécification*  **>**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**«**  *spécification du chemin*  **»**

*chemin d’accès-spécification*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;Chemin d’accès de fichier conforme

*pp-numéro*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*caractères*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**.** *caractères*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*pp-number* *digit* <br/>
&nbsp;&nbsp;&nbsp;&nbsp;*pp-number* *nondigit*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*pp-number*  **e**  *sign*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*pp-numéro***E***sign*    <br/>
&nbsp;&nbsp;&nbsp;&nbsp;*pp-number*  **.**

## <a name="see-also"></a>Voir aussi

[Grammaire lexicale](../c-language/lexical-grammar.md)
