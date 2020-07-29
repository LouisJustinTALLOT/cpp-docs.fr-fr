---
title: Caractères du champ de type scanf
ms.date: 11/04/2016
helpviewer_keywords:
- scanf function, type field characters
ms.assetid: 5d546a84-715b-44ca-b1c5-bbe997f9ff62
ms.openlocfilehash: 8ea5f53f5c6039cf15836ba995df0d63bd6fcb23
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87233897"
---
# <a name="scanf-type-field-characters"></a>Caractères du champ de type scanf

Les informations suivantes s'appliquent à la famille de fonctions `scanf` , y compris les versions sécurisées telles que `scanf_s`.

Le caractère `type` est le seul champ de format obligatoire. Il apparaît après les champs de format facultatifs. Le caractère `type` détermine si l'argument associé est interprété comme un caractère, une chaîne ou un nombre.

### <a name="type-characters-for-scanf-functions"></a>Caractères de type pour les fonctions scanf

|Caractère|Type d'entrée attendu|Type d'argument|Argument de taille dans la version sécurisée ?|
|---------------|----------------------------|----------------------|--------------------------------------|
|`c`|Caractère. Quand il est utilisé avec les fonctions `scanf` , spécifie un caractère codé sur un octet. Quand il est utilisé avec les fonctions `wscanf` , spécifie un caractère large. Les espaces blancs qui sont habituellement ignorés, sont lus quand `c` est spécifié. Pour lire le prochain caractère codé sur un octet qui n’est pas un espace, utilisez `%1s`. Pour lire le prochain caractère large qui n’est pas un espace, utilisez `%1ws`.|Pointeur vers en **`char`** cas d’utilisation avec les `scanf` fonctions, pointeur vers en **`wchar_t`** cas d’utilisation avec les `wscanf` fonctions.|Obligatoire. La taille n'inclut pas d'espace pour un terminateur Null.|
|`C`|Caractère de taille inverse. Quand il est utilisé avec les fonctions `scanf` , spécifie un caractère large. Quand il est utilisé avec les fonctions `wscanf` , spécifie un caractère codé sur un octet. Les espaces blancs qui sont habituellement ignorés, sont lus quand `C` est spécifié. Pour lire le prochain caractère codé sur un octet qui n’est pas un espace, utilisez `%1s`. Pour lire le prochain caractère large qui n’est pas un espace, utilisez `%1ws`.|Pointeur vers en **`wchar_t`** cas d’utilisation avec les `scanf` fonctions, pointeur vers en **`char`** cas d’utilisation avec les `wscanf` fonctions.|Obligatoire. L'argument relatif à la taille n'inclut pas d'espace pour un terminateur Null.|
|`d`|Entier décimal.|Pointeur vers **`int`** .|Non.|
|`i`|Entier. Hexadécimal, si la chaîne d'entrée commence par "0x" ou "0X", octal si la chaîne commence par "0", sinon décimal.|Pointeur vers **`int`** .|Non.|
|`o`|Entier octal.|Pointeur vers **`int`** .|Non.|
|`p`|Adresse du pointeur en notation hexadécimale. Le nombre maximal de chiffres lus dépend de la taille d’un pointeur (32 ou 64 bits), lequel varie selon l’architecture de la machine. "0x" ou "0X" sont acceptés en tant que préfixes.|Pointeur vers **`void*`** .|Non.|
|`u`|Entier décimal non signé.|Pointeur vers **`unsigned int`** .|Non.|
|`x`|Entier hexadécimal.|Pointeur vers **`int`** .|Non.|
|`e`, `E`, `f`, `F`, `g`, `G`|Valeur à virgule flottante composée d’un signe facultatif (+ ou -), d’une série d’un ou de plusieurs chiffres décimaux contenant la virgule décimale et d’un exposant facultatif ("e" ou "E") suivi d’une valeur entière éventuellement signée.|Pointeur vers **`float`** .|Non.|
|`a`, `A`|Valeur à virgule flottante composée d’une série d’un ou plusieurs chiffres hexadécimaux contenant une virgule décimale facultative et un exposant ("p" ou "P"), suivie d’une valeur décimale.|Pointeur vers **`float`** .|Non.|
|`n`|Aucune entrée lue à partir du flux ou de la mémoire tampon.|Pointeur vers **`int`** , dans lequel est stocké le nombre de caractères correctement lus à partir du flux ou de la mémoire tampon jusqu’à ce point dans l’appel actuel aux `scanf` fonctions ou aux `wscanf` fonctions.|Non.|
|`s`|Chaîne, jusqu'au premier espace blanc (espace, tabulation ou nouvelle ligne). Pour lire des chaînes non délimitées par des espaces, utilisez des crochets (`[ ]`), comme indiqué dans [Spécification de largeur scanf](../c-runtime-library/scanf-width-specification.md).|Quand il est utilisé avec les fonctions `scanf` , signifie un tableau de caractères codés sur un octet. Quand il est utilisé avec les fonctions `wscanf` , signifie un tableau de caractères larges. Dans les deux cas, le tableau de caractères doit être suffisamment grand pour le champ d'entrée, ainsi que le caractère Null de fin, qui est automatiquement ajouté.|Obligatoire. La taille inclut un espace pour un terminateur Null.|
|`S`|Chaîne de caractères de taille inverse, jusqu'au premier espace blanc (espace, tabulation ou nouvelle ligne). Pour lire des chaînes non délimitées par des espaces, utilisez des crochets (`[ ]`), comme indiqué dans [Spécification de largeur scanf](../c-runtime-library/scanf-width-specification.md).|Quand il est utilisé avec les fonctions `scanf`, signifie un tableau de caractères codés sur un octet. Quand il est utilisé avec les fonctions `wscanf`, signifie un tableau de caractères larges. Dans les deux cas, le tableau de caractères doit être suffisamment grand pour le champ d'entrée, ainsi que le caractère Null de fin, qui est automatiquement ajouté.|Obligatoire. La taille inclut un espace pour un terminateur Null.|

Les arguments relatifs à la taille, le cas échéant, doivent être passés à la liste de paramètres immédiatement après l'argument auquel ils s'appliquent. Par exemple, le code suivant :

```
char string1[11], string2[9];
scanf_s("%10s %8s", string1, 11, string2, 9);
```

lit une chaîne dont la longueur maximale est 10 dans `string1`, et une chaîne dont la longueur maximale est 8 dans `string2`. Il doit y avoir au moins une taille de mémoire tampon de plus qu'indiqué dans les spécifications de largeur, car l'espace doit être réservé pour le terminateur Null.

La chaîne de format peut gérer l'entrée codée sur un octet ou à caractère large, même si la version du caractère codé sur un octet ou la version des caractères larges de la fonction est utilisée. Ainsi, pour lire des caractères codés sur un octet ou des caractères larges avec les fonctions `scanf` et `wscanf` , utilisez les spécificateurs de format comme suit.

|Pour lire un caractère|Utilisez cette fonction|Avec ces spécificateurs de format|
|--------------------------|-----------------------|----------------------------------|
|octet unique|fonctions`scanf`|`c`, `hc` ou `hC`|
|octet unique|fonctions`wscanf`|`C`, `hc` ou `hC`|
|larges|fonctions`wscanf`|`c`, `lc` ou `lC`|
|larges|fonctions`scanf`|`C`, `lc` ou `lC`|

Pour analyser des chaînes avec les fonctions `scanf` et `wscanf` , utilisez le tableau ci-dessus en vous servant des spécificateurs de type de format `s` et `S` à la place de `c` et `C`.

## <a name="see-also"></a>Voir aussi

[scanf, _scanf_l, wscanf, _wscanf_l](../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md)
