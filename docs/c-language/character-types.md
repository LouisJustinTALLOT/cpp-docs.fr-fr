---
title: Types de caractères
ms.date: 11/04/2016
helpviewer_keywords:
- character data types [C]
- types [C], character
ms.assetid: d3ca8cda-c0d7-43af-9472-697e8ef015ce
ms.openlocfilehash: 5b1306c70cdab423c8758bf3e6c9ac4e9d6507da
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87226488"
---
# <a name="character-types"></a>Types de caractères

Une constante de caractère entier non précédée de la lettre **L** est de type **`int`** . La valeur d'une constante caractère entière contenant un seul caractère est la valeur numérique du caractère interprété comme un entier. Par exemple, la valeur numérique du caractère `a` est 97 au format décimal et 61 au format hexadécimal.

Syntaxiquement, une « constante à caractères larges » est une constante caractère préfixée par la lettre **L**. Une constante à caractères larges est de type **`wchar_t`** , un type entier défini dans le STDDEF. Fichier d’en-tête H. Par exemple :

```
char    schar =  'x';   /* A character constant          */
wchar_t wchar = L'x';   /* A wide-character constant for
                            the same character           */
```

Les constantes à caractères larges font 16 bits et spécifient des membres du jeu de caractères d'exécution étendu. Elles vous permettent d’exprimer des caractères dans des alphabets qui sont trop grands pour être représentés par le type **`char`** . Consultez [Caractères multioctets et larges](../c-language/multibyte-and-wide-characters.md) pour plus d'informations sur les caractères larges.

## <a name="see-also"></a>Voir aussi

[Constantes caractère C](../c-language/c-character-constants.md)
