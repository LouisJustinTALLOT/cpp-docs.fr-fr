---
description: 'En savoir plus sur : constantes caractère C'
title: Constantes caractère C
ms.date: 11/04/2016
helpviewer_keywords:
- characters, constants
- (') single quotation mark
- constants, character
- single quotation mark
ms.assetid: 388ae7d7-2c3a-44d6-a507-63f541ecd2da
ms.openlocfilehash: 2503fc983d79f363f525b22172d2113393b41091
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97211555"
---
# <a name="c-character-constants"></a>Constantes caractère C

Une constante caractère est formée en plaçant un caractère du jeu de caractères représentable entre guillemets simples (**' '**). Les constantes caractère sont utilisées pour représenter des caractères dans le [jeu de caractères d'exécution](../c-language/execution-character-set.md).

## <a name="syntax"></a>Syntaxe

*constante de caractère*: **'** *c-char-Sequence* **'**

**L'** *c-char-Sequence* **'**

*c-char-Sequence*: *c-char*

*c-char-sequence c-char*

*c-char* : tout membre du jeu de caractères source à l’exception du guillemet simple (**'**), de la barre oblique inverse (**\\**) ou du caractère de saut de ligne

*séquence d’échappement*

*escape-sequence*: *simple-escape-sequence*

*octal-escape-sequence*

*séquence d’échappement hexadécimale*

*simple-escape-sequence* : un des éléments suivants : **\a \b \f \n \r \t \v**

**\\' \\" \\\ \\?**

*octal-séquence d’échappement-séquence*: **\\** *chiffre octal*  

**\\**  *chiffre octal-chiffre*

**\\**  *chiffre octal-chiffre octal-chiffre*

*hexadecimal-escape-sequence*: **\x**  *hexadecimal-digit*

*hexadecimal-escape-sequence hexadecimal-digit*

## <a name="see-also"></a>Voir aussi

[Constantes C](../c-language/c-constants.md)
