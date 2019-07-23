---
title: Séquences d'échappement
ms.date: 11/04/2016
helpviewer_keywords:
- "\r escape sequence"
- double backslash
- horizontal-tab 	 escape sequence
- (') single quotation mark
- "bell character \a escape sequence"
- escape sequences
- hexadecimal escape sequence
- carriage returns
- tab 	 escape sequence
- "\f escape sequence"
- quotation marks, single
- "form feed \f escape sequence"
- "\v escape sequence"
- control character escape sequences
- " symbol in escape sequences"
- octal escape sequence
- escape characters
- "newline character \n escape sequence"
- nongraphic control characters
- question mark, literal
- "\n escape sequence"
- "vertical tab \v escape sequence"
- "\a escape sequence"
- '? symbol'
- '? symbol, escape sequence character'
- "	 escape sequence"
- backspace escape sequence
ms.assetid: 5aef377f-a76c-4d5c-aa04-8308758ad6a8
ms.openlocfilehash: 5de0b5f1a73fcfb6ea0325bea3247ebe4c85d411
ms.sourcegitcommit: 878a164fe6d550ca81ab87d8425c8d3cd52fe384
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/22/2019
ms.locfileid: "68375823"
---
# <a name="escape-sequences"></a>Séquences d'échappement

Les combinaisons de caractères composées d'une barre oblique inverse ( **\\** ) suivie d'une lettre ou d'une combinaison de chiffres sont appelées "séquences d'échappement". Pour représenter un caractère de saut de ligne, un guillemet simple ou certains autres caractères dans une constante caractère, vous devez utiliser des séquences d'échappement. Une séquence d'échappement est considérée comme un caractère unique et est donc valide en tant que constante caractère.

Les séquences d'échappement sont généralement utilisées pour spécifier des actions telles que les retours chariot et les tabulations sur les terminaux et les imprimantes. Elles sont également utilisées pour fournir des représentations littérales des caractères non imprimables et des caractères qui ont généralement des significations spéciales, par exemple les guillemets doubles ( **"** ). Le tableau suivant répertorie les séquences d'échappement ANSI et leur représentation.

Notez que le point d'interrogation précédé d'une barre oblique inverse ( **\\\?** ) spécifie un point d'interrogation littéral dans les cas où la séquence de caractères est interprétée à tort comme un trigraphe. Pour plus d'informations, consultez [Trigraphes](../c-language/trigraphs.md).

### <a name="escape-sequences"></a>Séquences d'échappement

|Séquence d'échappement|Représente|
|---------------------|----------------|
|**\a**|Sonnerie (alerte)|
|**\b**|Retour arrière|
|**\f**|Saut de page|
|**\n**|Nouvelle ligne|
|**\r**|Retour chariot|
|**\t**|Tabulation horizontale|
|**\v**|Tabulation verticale|
|**\\'**|Guillemet simple|
|**\\"**|Guillemets doubles|
|**\\\\**|Barre oblique inverse|
|**\\?**|Point d'interrogation littéral|
|**\\** *ooo*|Caractère ASCII en notation octale|
|**\x** *hh*|Caractère ASCII en notation hexadécimale|
|**\x** *hhhh*|Caractère Unicode en notation hexadécimale si cette séquence d'échappement est utilisée dans une constante à caractères larges ou un littéral de chaîne Unicode.<br /><br /> Par exemple, `WCHAR f = L'\x4e00'` ou `WCHAR b[] = L"The Chinese character for one is \x4e00"`.|

**Section spécifique à Microsoft**

Si une barre oblique inverse précède un caractère qui n'apparaît pas dans le tableau, le compilateur traite le caractère non défini comme le caractère lui-même. Par exemple, `\c` est traité comme `c`.

**FIN de la section spécifique à Microsoft**

Les séquences d'échappement vous permettent d'envoyer des caractères de contrôle non graphiques à un périphérique d'affichage. Par exemple, le caractère ESC ( **\033**) est souvent utilisé comme le premier caractère d'une commande de contrôle pour un terminal ou une imprimante. Certaines séquences d'échappement sont spécifiques au périphérique. Par exemple, les séquences d’échappement de tabulation verticale et de saut de page ( **\v** et **\f**) n'affectent pas la sortie sur l’écran, mais elles exécutent des opérations d'imprimante appropriées.

Vous pouvez également utiliser la barre oblique inverse ( **\\** ) comme caractère de continuation. Lorsqu'un caractère de saut de ligne (équivalent à une pression sur la touche RETOUR) suit immédiatement la barre oblique inverse, le compilateur ignore la barre oblique inverse et le caractère de saut de ligne et traite la ligne suivante dans le cadre de la ligne précédente. Cela est surtout utile pour les définitions de préprocesseur plus longues qu'une ligne. Par exemple :

```
#define assert(exp) \
( (exp) ? (void) 0:_assert( #exp, __FILE__, __LINE__ ) )
```

## <a name="see-also"></a>Voir aussi

[Constantes caractère C](../c-language/c-character-constants.md)
