---
title: Récapitulatif des expressions
description: En savoir plus sur la grammaire C standard pour les expressions implémentées par le compilateur Microsoft C/C++.
ms.date: 10/30/2020
ms.assetid: ed448953-687a-4b57-a1cb-12967bd770ea
ms.openlocfilehash: 317f7c26e89e2741a5496c5a091100f0c2d8a21a
ms.sourcegitcommit: 6284bca6549e7b4f199d4560c30df6c1278bd4a0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/25/2020
ms.locfileid: "96035220"
---
# <a name="summary-of-expressions"></a>Récapitulatif des expressions

*`primary-expression`*:\
&emsp;*`identifier`*\
&emsp;*`constant`*\
&emsp;*`string-literal`*\
&emsp;**`(`** *`expression`* **`)`**\
&emsp;*`generic-selection`*

*`generic-selection`*:\
&emsp;**`_Generic`** **`(`** *`assignment-expression`* **`,`** *`generic-assoc-list`* **`)`**

*`generic-assoc-list`*:\
&emsp;*`generic-association`*\
&emsp;*`generic-assoc-list`* **`,`** *`generic-association`*

*`generic-association`*:\
&emsp;*`type-name`* **`:`** *`assignment-expression`*\
&emsp;**`default`** **`:`** *`assignment-expression`*

*`postfix-expression`*:\
&emsp;*`primary-expression`*\
&emsp;*`postfix-expression`* **`[`** *`expression`* **`]`**\
&emsp;*`postfix-expression`***`(`** *`argument-expression-list`* <sub>OPT</sub>**`)`**\
&emsp;*`postfix-expression`* **`.`** *`identifier`*\
&emsp;*`postfix-expression`* **`->`** *`identifier`*\
&emsp;*`postfix-expression`* **`++`**\
&emsp;*`postfix-expression`* **`--`**\
&emsp;**`(`** *`type-name`* **`)`** **`{`** *`initializer-list`* **`}`**\
&emsp;**`(`** *`type-name`* **`)`** **`{`** *`initializer-list`* **`,`** **`}`**

*`argument-expression-list`*:\
&emsp;*`assignment-expression`*\
&emsp;*`argument-expression-list`* **`,`** *`assignment-expression`*

*`unary-expression`*:\
&emsp;*`postfix-expression`*\
&emsp;**`++`** *`unary-expression`*\
&emsp;**`--`** *`unary-expression`*\
&emsp;*`unary-operator`* *`cast-expression`*\
&emsp;**`sizeof`** *`unary-expression`*\
&emsp;**`sizeof`** **`(`** *`type-name`* **`)`** &emsp;**`_Alignof`** **`(`** *`type-name`* **`)`**

*`unary-operator`*: un des \
&emsp;**`&`** **`*`** **`+`** **`-`** **`~`** **`!`**

*`cast-expression`*:\
&emsp;*`unary-expression`*\
&emsp;**`(`** *`type-name`* **`)`** *`cast-expression`*

*`multiplicative-expression`*:\
&emsp;*`cast-expression`*\
&emsp;*`multiplicative-expression`* **`*`** *`cast-expression`*\
&emsp;*`multiplicative-expression`* **`/`** *`cast-expression`*\
&emsp;*`multiplicative-expression`* **`%`** *`cast-expression`*

*`additive-expression`*:\
&emsp;*`multiplicative-expression`*\
&emsp;*`additive-expression`* **`+`** *`multiplicative-expression`*\
&emsp;*`additive-expression`* **`-`** *`multiplicative-expression`*

*`shift-expression`*:\
&emsp;*`additive-expression`*\
&emsp;*`shift-expression`* **`<<`** *`additive-expression`*\
&emsp;*`shift-expression`* **`>>`** *`additive-expression`*

*`relational-expression`*:\
&emsp;*`shift-expression`*\
&emsp;*`relational-expression`* **`<`** *`shift-expression`*\
&emsp;*`relational-expression`* **`>`** *`shift-expression`*\
&emsp;*`relational-expression`* **`<=`** *`shift-expression`*\
&emsp;*`relational-expression`* **`>=`** *`shift-expression`*

*`equality-expression`*:\
&emsp;*`relational-expression`*\
&emsp;*`equality-expression`* **`==`** *`relational-expression`*\
&emsp;*`equality-expression`* **`!=`** *`relational-expression`*

*`AND-expression`*:\
&emsp;*`equality-expression`*\
&emsp;*`AND-expression`* **`&`** *`equality-expression`*

*`exclusive-OR-expression`*:\
&emsp;*`AND-expression`*\
&emsp;*`exclusive-OR-expression`* **`^`** *`AND-expression`*

*`inclusive-OR-expression`*:\
&emsp;*`exclusive-OR-expression`*\
&emsp;*`inclusive-OR-expression`* **`|`** *`exclusive-OR-expression`*

*`logical-AND-expression`*:\
&emsp;*`inclusive-OR-expression`*\
&emsp;*`logical-AND-expression`* **`&&`** *`inclusive-OR-expression`*

*`logical-OR-expression`*:\
&emsp;*`logical-AND-expression`*\
&emsp;*`logical-OR-expression`* **`||`** *`logical-AND-expression`*

*`conditional-expression`*:\
&emsp;*`logical-OR-expression`*\
&emsp;*`logical-OR-expression`* **`?`** *`expression`* **`:`** *`conditional-expression`*

*`assignment-expression`*:\
&emsp;*`conditional-expression`*\
&emsp;*`unary-expression`* *`assignment-operator`* *`assignment-expression`*

*`assignment-operator`*: un des \
&emsp;**`=`** **`*=`** **`/=`** **`%=`** **`+=`** **`-=`** **`<<=`** **`>>=`** **`&=`** **`^=`** **`|=`**

*`expression`*:\
&emsp;*`assignment-expression`*\
&emsp;*`expression`* **`,`** *`assignment-expression`*

*`constant-expression`*:\
&emsp;*`conditional-expression`*

## <a name="see-also"></a>Voir aussi

- [Grammaire de la structure des expressions](../c-language/phrase-structure-grammar.md)
