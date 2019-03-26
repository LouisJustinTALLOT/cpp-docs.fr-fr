---
title: Résumé des littéraux de chaîne
ms.date: 11/04/2016
ms.assetid: d2693900-f4e2-4820-b7de-085d51827aee
ms.openlocfilehash: a51c66f295a04b969d46d961f43517c0d7de5f6c
ms.sourcegitcommit: 90817d9d78fbaed8ffacde63f3add334842e596f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/20/2019
ms.locfileid: "58278344"
---
# <a name="summary-of-string-literals"></a>Résumé des littéraux de chaîne

*string-literal*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**"** *s-char-sequence*<sub>opt</sub> **"**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**L"** *s-char-sequence*<sub>opt</sub> **"**

*s-char-sequence*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*s-char*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*s-char-sequence* *s-char*

*s-char* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;tout membre du jeu de caractères de code source sauf le guillemet double (''), la barre oblique inverse (\\) ou la séquence d'échappement du caractère de saut de ligne

## <a name="see-also"></a>Voir aussi

[Grammaire lexicale](../c-language/lexical-grammar.md)
