---
title: Résumé des littéraux de chaîne | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: d2693900-f4e2-4820-b7de-085d51827aee
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a94d575ee36f38b56f64fb6298eb6f6f6e43567e
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43762741"
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