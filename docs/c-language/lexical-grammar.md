---
title: Grammaire lexicale C
description: Décrit la grammaire lexicale du langage C standard implémentée par le compilateur Microsoft C/C++.
ms.date: 10/30/2020
helpviewer_keywords:
- lexical grammar
ms.assetid: cb5847fa-aef3-47f5-8825-97c2bf4a3d87
ms.openlocfilehash: d0ee2c9e93f3be1a06e264b4c60ec9a89410bb79
ms.sourcegitcommit: 4abc6c4c9694f91685cfd77940987e29a51e3143
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/03/2020
ms.locfileid: "93238497"
---
# <a name="c-lexical-grammar"></a>Grammaire lexicale C

## <a name="tokens"></a><a name="tokens"></a> Jetons

*`token`* :\
&emsp;*`keyword`*\
&emsp;*`identifier`*\
&emsp;*`constant`*\
&emsp;*`string-literal`*\
&emsp;*`punctuator`*

*`preprocessing-token`* :\
&emsp;*`header-name`*\
&emsp;*`identifier`*\
&emsp;*`pp-number`*\
&emsp;*`character-constant`*\
&emsp;*`string-literal`*\
&emsp;*`punctuator`*\
&emsp;chaque caractère autre qu’un espace blanc qui ne peut pas être l’un des éléments ci-dessus

## <a name="keywords"></a><a name="keywords"></a> Mot

*`keyword`* : un des \
&emsp;**`auto`** **`break`** **`case`** **`char`** **`const`** **`continue`**\
&emsp;**`default`** **`do`** **`double`** **`else`** **`enum`** **`extern`**\
&emsp;**`float`** **`for`** **`goto`** **`if`** **`inline`** **`int`** **`long`**\
&emsp;**`register`** **`restrict`** **`return`** **`short`** **`signed`**\
&emsp;**`sizeof`** **`static`** **`struct`** **`switch`** **`typedef`** **`union`**\
&emsp;**`unsigned`** **`void`** **`volatile`** **`while`** **`_Alignas`**\
&emsp;**`_Alignof`** **`_Atomic`** **`_Bool`** **`_Complex`** **`_Generic`**\
&emsp;**`_Imaginary`** **`_Noreturn`** **`_Static_assert`**\
&emsp;**`_Thread_local`**

Pour obtenir la liste des mots clés supplémentaires spécifiques à Microsoft, consultez [C Keywords](./c-keywords.md).

## <a name="identifiers"></a><a name="identifiers"></a> Identificateurs

*`identifier`* :\
&emsp;*`identifier-nondigit`*\
&emsp;*`identifier`* *`identifier-nondigit`*\
&emsp;*`identifier`* *`digit`*

*`identifier-nondigit`* :\
&emsp;*`nondigit`*\
&emsp;*`universal-character-name`*\
&emsp;autres caractères définis par l’implémentation

*`nondigit`* : un des \
&emsp;**`_`** **`a`** **`b`** **`c`** **`d`** **`e`** **`f`** **`g`** **`h`** **`i`** **`j`** **`k`** **`l`** **`m`**\
&emsp;**`n`** **`o`** **`p`** **`q`** **`r`** **`s`** **`t`** **`u`** **`v`** **`w`** **`x`** **`y`** **`z`**\
&emsp;**`A`** **`B`** **`C`** **`D`** **`E`** **`F`** **`G`** **`H`** **`I`** **`J`** **`K`** **`L`** **`M`**\
&emsp;**`N`** **`O`** **`P`** **`Q`** **`R`** **`S`** **`T`** **`U`** **`V`** **`W`** **`X`** **`Y`** **`Z`**

*`digit`* : un des \
&emsp;**`0`** **`1`** **`2`** **`3`** **`4`** **`5`** **`6`** **`7`** **`8`** **`9`**

*`universal-character-name`* :\
&emsp;**`\u`** *`hex-quad`*\
&emsp;**`\U`** *`hex-quad`* *`hex-quad`*

*`hex-quad`* :\
&emsp;*`hexadecimal-digit`* *`hexadecimal-digit`* *`hexadecimal-digit`* *`hexadecimal-digit`*

## <a name="constants"></a><a name="constants"></a> Constantes

*`constant`* :\
&emsp;*`integer-constant`*\
&emsp;*`floating-constant`*\
&emsp;*`enumeration-constant`*\
&emsp;*`character-constant`*

*`integer-constant`* :\
&emsp;*`decimal-constant`**`integer-suffix`* <sub>OPT</sub>\
&emsp;*`binary-constant`*<sup>1</sup> *`integer-suffix`* <sub>OPT</sub>\
&emsp;*`octal-constant`**`integer-suffix`* <sub>OPT</sub>\
&emsp;*`hexadecimal-constant`**`integer-suffix`* <sub>OPT</sub>

*`decimal-constant`* :\
&emsp;*`nonzero-digit`*\
&emsp;*`decimal-constant`* *`digit`*

*`binary-constant`* : <sup>1</sup>\
&emsp;*`binary-prefix`* *`binary-digit`*\
&emsp;*`binary-constant`* *`binary-digit`*

*`binary-prefix`*<sup>1</sup>: un de \
&emsp;**`0b`** **`0B`**

*`binary-digit`*<sup>1</sup>: un de \
&emsp;**`0`** **`1`**

*`octal-constant`* :\
&emsp;**`0`**\
&emsp;*`octal-constant`* *`octal-digit`*

*`hexadecimal-constant`* :\
&emsp;*`hexadecimal-prefix`* *`hexadecimal-digit`*\
&emsp;*`hexadecimal-constant`* *`hexadecimal-digit`*

*`hexadecimal-prefix`* : un des \
&emsp;**`0x`** **`0X`**

*`nonzero-digit`* : un des \
&emsp;**`1`** **`2`** **`3`** **`4`** **`5`** **`6`** **`7`** **`8`** **`9`**

*`octal-digit`* : un des \
&emsp;**`0`** **`1`** **`2`** **`3`** **`4`** **`5`** **`6`** **`7`**

*`hexadecimal-digit`* : un des \
&emsp;**`0`** **`1`** **`2`** **`3`** **`4`** **`5`** **`6`** **`7`** **`8`**\
&emsp;**`a`** **`b`** **`c`** **`d`** **`e`** **`f`**\
&emsp;**`A`** **`B`** **`C`** **`D`** **`E`** **`F`**

*`integer-suffix`* :\
&emsp;*`unsigned-suffix`**`long-suffix`* <sub>OPT</sub>\
&emsp;*`unsigned-suffix`**`long-long-suffix`* <sub>OPT</sub>\
&emsp;*`long-suffix`**`unsigned-suffix`* <sub>OPT</sub>\
&emsp;*`long-long-suffix`**`unsigned-suffix`* <sub>OPT</sub>

*`unsigned-suffix`* : un des \
&emsp;**`u`** **`U`**

*`long-suffix`* : un des \
&emsp;**`l`** **`L`**

*`long-long-suffix`* : un des \
&emsp;**`ll`** **`LL`**

*`floating-constant`* :\
&emsp;*`decimal-floating-constant`*\
&emsp;*`hexadecimal-floating-constant`*

*`decimal-floating-constant`* :\
&emsp;*`fractional-constant`**`exponent-part`* <sub>opt</sub> opt opt *`floating-suffix`* <sub>opt</sub>\
&emsp;*`digit-sequence`**`exponent-part`* *`floating-suffix`* <sub>OPT</sub>

*`hexadecimal-floating-constant`* :\
&emsp;*`hexadecimal-prefix`**`hexadecimal-fractional-constant`* OPT opt *`binary-exponent-part`* <sub>opt</sub> *`floating-suffix`* <sub>opt</sub>\
&emsp;*`hexadecimal-prefix`**`hexadecimal-digit-sequence`* *`binary-exponent-part`* *`floating-suffix`* <sub>OPT</sub>

*`fractional-constant`* :\
&emsp;*`digit-sequence`*<sub>OPT</sub> **`.`***`digit-sequence`*\
&emsp;*`digit-sequence`*  **`.`**

*`exponent-part`* :\
&emsp;**`e`***`sign`* <sub>OPT</sub>*`digit-sequence`*\
&emsp;**`E`***`sign`* <sub>OPT</sub>*`digit-sequence`*

*`sign`* : un des \
&emsp;**`+`** **`-`**

*`digit-sequence`* :\
&emsp;*`digit`*\
&emsp;*`digit-sequence`* *`digit`*

*`hexadecimal-fractional-constant`* :\
&emsp;*`hexadecimal-digit-sequence`*<sub>OPT</sub> **`.`***`hexadecimal-digit-sequence`*\
&emsp;*`hexadecimal-digit-sequence`*  **`.`**

*`binary-exponent-part`* :\
&emsp;**`p`***`sign`* <sub>OPT</sub>*`digit-sequence`*\
&emsp;**`P`***`sign`* <sub>OPT</sub>*`digit-sequence`*

*`hexadecimal-digit-sequence`* :\
&emsp;*`hexadecimal-digit`*\
&emsp;*`hexadecimal-digit-sequence`* *`hexadecimal-digit`*

*`floating-suffix`* : un des \
&emsp;**`f`** **`l`** **`F`** **`L`**

*`enumeration-constant`* :\
&emsp;*`identifier`*

*`character-constant`* :\
&emsp;**`'`** *`c-char-sequence`* **`'`**\
&emsp;**`L'`** *`c-char-sequence`* **`'`**

*`c-char-sequence`* :\
&emsp;*`c-char`*\
&emsp;*`c-char-sequence`* *`c-char`*

*`c-char`* :\
&emsp;Tout membre du jeu de caractères source, à l’exception du guillemet simple ( **`'`** ), de la barre oblique inverse ( **`\`** ) ou du caractère de saut de ligne \
&emsp;*`escape-sequence`*

*`escape-sequence`* :\
&emsp;*`simple-escape-sequence`*\
&emsp;*`octal-escape-sequence`*\
&emsp;*`hexadecimal-escape-sequence`*\
&emsp;*`universal-character-name`*

*`simple-escape-sequence`* : un des \
&emsp;**`\a`** **`\b`** **`\f`** **`\n`** **`\r`** **`\t`** **`\v`**\
&emsp;**`\'`** **`\"`** **`\\`** **`\?`**

*`octal-escape-sequence`* :\
&emsp;**`\`** *`octal-digit`*\
&emsp;**`\`** *`octal-digit`* *`octal-digit`*\
&emsp;**`\`** *`octal-digit`* *`octal-digit`* *`octal-digit`*

*`hexadecimal-escape-sequence`* :\
&emsp;**`\x`** *`hexadecimal-digit`*\
&emsp;*`hexadecimal-escape-sequence`* *`hexadecimal-digit`*

## <a name="string-literals"></a><a name="string-literals"></a> Littéraux de chaîne

*`string-literal`* :\
&emsp;*`encoding-prefix`**`s-char-sequence`* <sub>OPT</sub>**`"`**

*`encoding-prefix`* :\
&emsp;**`u8`**\
&emsp;**`u`**\
&emsp;**`U`**\
&emsp;**`L`**

*`s-char-sequence`* :\
&emsp;*`s-char`*\
&emsp;*`s-char-sequence`* *`s-char`*

*`s-char`* :\
&emsp;tout membre du jeu de caractères source à l’exception du guillemet double ( **`"`** ), de la barre oblique inverse ( **`\`** ) ou du caractère de saut de ligne \
&emsp;*`escape-sequence`*

## <a name="punctuators"></a><a name="punctuators"></a> Ponctuation

*`punctuator`* : un des \
&emsp;**`[`** **`]`** **`(`** **`)`** **`{`** **`}`** **`.`** **`->`**\
&emsp;**`++`** **`--`** **`&`** **`*`** **`+`** **`-`** **`~`** **`!`**\
&emsp;**`/`** **`%`** **`<<`** **`>>`** **`<`** **`>`** **`<=`** **`>=`** **`==`**\
&emsp;**`!=`** **`^`** **`|`** **`&&`** **`||`** **`?`** **`:`** **`;`** **`...`**\
&emsp;**`=`** **`*=`** **`/=`** **`%=`** **`+=`** **`-=`** **`<<=`** **`>>=`**\
&emsp;**`&=`** **`^=`** **`|=`** **`,`** **`#`** **`##`**\
&emsp;**`<:`** **`:>`** **`<%`** **`%>`** **`%:`** **`%:%:`**

## <a name="header-names"></a>Noms des en-têtes

*`header-name`* :\
&emsp;**`<`** *`h-char-sequence`* **`>`**\
&emsp;**`"`** *`q-char-sequence`* **`"`**

*`h-char-sequence`* :\
&emsp;*`h-char`*\
&emsp;*`h-char-sequence`* *`h-char`*

*`h-char`* :\
&emsp;tout membre du jeu de caractères source, à l’exception du caractère de nouvelle ligne et **`>`**

*`q-char-sequence`* :\
&emsp;*`q-char`*\
&emsp;*`q-char-sequence`* *`q-char`*

*`q-char`* :\
&emsp;tout membre du jeu de caractères source, à l’exception du caractère de nouvelle ligne et **`"`**

## <a name="preprocessing-numbers"></a>Prétraitement des nombres

*`pp-number`* :\
&emsp;*`digit`*\
&emsp;**`.`** *`digit`*\
&emsp;*`pp-number`* *`digit`* \
&emsp;*`pp-number`* *`identifier-nondigit`*\
&emsp;*`pp-number`* **`e`** *`sign`*\
&emsp;*`pp-number`* **`E`** *`sign`*\
&emsp;*`pp-number`* **`p`** *`sign`*\
&emsp;*`pp-number`* **`P`** *`sign`*\
&emsp;*`pp-number`* **`.`**

<sup>1</sup> *`binary-constant`* , *`binary-prefix`* et *`binary-digit`* sont des extensions spécifiques à Microsoft.

## <a name="see-also"></a>Voir aussi

[Résumé de la syntaxe du langage C](../c-language/c-language-syntax-summary.md)
