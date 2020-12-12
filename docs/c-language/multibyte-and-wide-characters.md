---
description: En savoir plus sur les caractères multioctets et larges
title: Multioctets et caractères larges
ms.date: 11/04/2016
helpviewer_keywords:
- globalization [C++], character sets
- character data types [C]
- Unicode [C++], wide character set
- types [C], character
- characters [C++], wide
- international applications [C++], character display
- multibyte characters [C++]
- wide characters [C++]
- characters [C++], codes
- character codes [C++], wide
- character codes [C++], multibyte
ms.assetid: 1943c469-200d-4724-b18f-781d70520f9e
ms.openlocfilehash: 48063824b66df42d41b51ca491b0eec5f7679274
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97243388"
---
# <a name="multibyte-and-wide-characters"></a>Multioctets et caractères larges

Un caractère multioctet est un caractère composé de séquences d'un ou plusieurs octets. Chaque séquence d'octets représente un caractère unique dans le jeu de caractères étendu. Les caractères multioctets sont utilisés dans les jeux de caractères tels que Kanji.

Les caractères larges sont des codes de caractères multilingues qui ont toujours une largeur de 16 bits. Le type des constantes caractère est **`char`** ; pour les caractères larges, le type est **`wchar_t`** . Comme les caractères larges ont toujours une taille fixe, leur utilisation simplifie la programmation avec les jeux de caractères internationaux.

Le littéral de chaîne à caractères larges `L"hello"` devient un tableau de six entiers de type **`wchar_t`** .

```
{L'h', L'e', L'l', L'l', L'o', 0}
```

La spécification Unicode régit les caractères larges. Les routines de bibliothèque Runtime permettant de traduire des caractères multioctets et larges incluent `mbstowcs`, `mbtowc`, `wcstombs` et `wctomb`.

## <a name="see-also"></a>Voir aussi

[Identificateurs C](../c-language/c-identifiers.md)
