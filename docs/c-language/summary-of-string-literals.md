---
title: Résumé des littéraux de chaîne
ms.date: 11/04/2016
ms.assetid: d2693900-f4e2-4820-b7de-085d51827aee
ms.openlocfilehash: a51c66f295a04b969d46d961f43517c0d7de5f6c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62346598"
---
# <a name="summary-of-string-literals"></a>Résumé des littéraux de chaîne

*littéral de chaîne*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**«** *s-char-Sequence*<sub>OPT</sub> **»**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**L"** *s-char-sequence*<sub>opt</sub> **"**

*s-char-sequence*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*s-char*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*s-char-sequence* *s-char*

*s-char*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;tout membre du jeu de caractères de code source sauf le guillemet double (''), la barre oblique inverse (\\) ou la séquence d'échappement du caractère de saut de ligne

## <a name="see-also"></a>Voir aussi

[Grammaire lexicale](../c-language/lexical-grammar.md)
