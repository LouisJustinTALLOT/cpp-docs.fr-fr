---
title: Littéraux de chaîne C
ms.date: 08/31/2018
helpviewer_keywords:
- string literals, syntax
- strings [C++], string literals
- literal strings, C
ms.assetid: 4b05523e-49a2-4900-b21a-754350af3328
ms.openlocfilehash: 0df7126efe5a5b2caa3a4fee51465d0dbe892e89
ms.sourcegitcommit: 8bb2bea1384b290b7570b01608a86c7488ae7a02
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/26/2019
ms.locfileid: "67400582"
---
# <a name="c-string-literals"></a>Littéraux de chaîne C

Un littéral de chaîne est une séquence de caractères du jeu de caractères source placée entre guillemets ( **" "** ). Les littéraux de chaîne servent à représenter une séquence de caractères qui, une fois combinés, forment une chaîne terminée par le caractère Null. Vous devez toujours faire précéder les littéraux de chaîne étendue de la lettre **L**.

## <a name="syntax"></a>Syntaxe

*string-literal*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **"** *s-char-sequence*<sub>opt</sub> **"**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**L"** *s-char-sequence*<sub>opt</sub> **"**

*s-char-sequence*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*s-char*

&nbsp;&nbsp;&nbsp;&nbsp;*s-char-sequence* *s-char*

*s-char* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;Tout membre du jeu de caractères source, à l'exception du guillemet double ("), de la barre oblique inverse (\\) ou du caractère de saut de ligne

&nbsp;&nbsp;&nbsp;&nbsp;*escape-sequence*

## <a name="remarks"></a>Remarques

L'exemple ci-dessous est un littéral de chaîne simple :

```C
char *amessage = "This is a string literal.";
```

Tous les codes d'échappement répertoriés dans le tableau [Séquences d’échappement](../c-language/escape-sequences.md) sont valides dans les littéraux de chaîne. Pour représenter un guillemet double dans un littéral de chaîne, utilisez la séquence d'échappement **\\"** . Le guillemet simple ( **'** ) peut être représenté sans séquence d'échappement. La barre oblique inverse ( **\\** ) doit être suivie d'une seconde barre oblique inverse ( **\\\\** ) lorsqu'elle apparaît dans une chaîne. Lorsqu'une barre oblique inverse apparaît à la fin d'une ligne, elle est toujours interprétée comme un caractère de continuation de ligne.

## <a name="see-also"></a>Voir aussi

[Éléments de C](../c-language/elements-of-c.md)
