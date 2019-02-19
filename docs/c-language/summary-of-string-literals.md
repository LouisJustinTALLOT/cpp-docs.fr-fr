---
title: Résumé des littéraux de chaîne
ms.date: 11/04/2016
ms.assetid: d2693900-f4e2-4820-b7de-085d51827aee
ms.openlocfilehash: bc235a26849c284d8b46216606d40d07452e2237
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/12/2019
ms.locfileid: "56149685"
---
# <a name="summary-of-string-literals"></a>Résumé des littéraux de chaîne

*string-literal*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**'** *s-char-sequence*<sub>opt</sub> **'**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**L'** *s-char-sequence*sub>opt</sub> **'**

*s-char-sequence*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*s-char*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*s-char-sequence* *s-char*

*s-char* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;tout membre du jeu de caractères de code source sauf le guillemet double (''), la barre oblique inverse (\\) ou la séquence d'échappement du caractère de saut de ligne

## <a name="see-also"></a>Voir aussi

[Grammaire lexicale](../c-language/lexical-grammar.md)
