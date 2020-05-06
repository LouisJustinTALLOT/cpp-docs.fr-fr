---
title: Récapitulatif des constantes
ms.date: 11/04/2016
helpviewer_keywords:
- constants, C
ms.assetid: 4158234c-e189-4e25-970f-52a04bc6380a
ms.openlocfilehash: f927d977d818bed28c5fd7392f7933cd1a63ced3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62157739"
---
# <a name="summary-of-constants"></a>Récapitulatif des constantes

*constante*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*constante à virgule flottante*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*entier-constante*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*énumération-constante*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*caractère-constante*

*floating-point-constant* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*fractional-constant* *exponent-part*<sub>opt</sub> *floating-suffix*<sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*digit-sequence* *exponent-part* *floating-suffix*<sub>opt</sub>

*fractional-constant* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;option *de séquence numérique*<sub>opt</sub> **.** *digit-sequence*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*chiffre-séquence*  **.**

*exponent-part* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;chiffre d'<sub>annulation</sub> de *signe* **e** *-séquence*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;Chiffre d'<sub>annulation</sub> de *signe* **E** *-séquence*

*sign* : un des éléments suivants<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**+ -**

*chiffre-séquence*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*caractères*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*digit-sequence* *digit*

*floating-suffix* : un des éléments suivants<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**f l F L**

*integer-constant* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*decimal-constant* *integer-suffix*<sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*binary-constant* *integer-suffix*<sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*octal-constant* *integer-suffix*<sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*hexadecimal-constant* *integer-suffix*<sub>opt</sub>

*decimal-constant*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*chiffre différent de zéro*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*decimal-constant* *digit*

*binary-constant* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**0b** *binary-digit*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**0b** *-chiffre binaire*

*octal-constant* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**entre**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*octal-constant* *octal-digit*

*hexadecimal-constant* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**0x**  *-chiffre hexadécimal*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**0X**  *hexadecimal-digit*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*hexadecimal-constant* *hexadecimal-digit*

*nonzero-digit* : un des éléments suivants :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**1 2 3 4 5 6 7 8 9**

*octal-digit* : un des éléments suivants :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**0 1 2 3 4 5 6 7**

*hexadecimal-digit* : un des éléments suivants :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**0 1 2 3 4 5 6 7 8 9**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**a b c d e f**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**A B C D E F**

*unsigned-suffix* : un des éléments suivants :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**u U**

*long-suffix* : un des éléments suivants :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**l L**

*character-constant* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**'** *c-char-Sequence* **'**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**L'** *c-char-Sequence* **'**

*integer-suffix* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*unsigned-suffix* *long-suffix*<sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*long-suffix* *unsigned-suffix*<sub>opt</sub>

*c-char-sequence* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*c-char*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*c-char-sequence* *c-char*

*c-char*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;Tout membre du jeu de caractères source, à l’exception du guillemet simple (**'**),**\\**de la barre oblique inverse () ou du caractère de saut de ligne

*escape-sequence* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*séquence d’échappement simple*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*octal-séquence d’échappement*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*séquence d’échappement hexadécimale*

*simple-escape-sequence* : un des éléments suivants :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**\a \b \f \n \r \t \v**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**\\' \\" \\\ \\?**

*octal-séquence d’échappement*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**\\***octal-chiffre*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**\\**chiffre *octal-chiffre* *octal-digit*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**\\**chiffre *octal-chiffre* *octal-chiffre* *octal-digit*

*hexadecimal-escape-sequence* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**\x** *hexadecimal-digit*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*hexadecimal-escape-sequence* *hexadecimal-digit*

## <a name="see-also"></a>Voir aussi

[Grammaire lexicale](../c-language/lexical-grammar.md)<br/>
