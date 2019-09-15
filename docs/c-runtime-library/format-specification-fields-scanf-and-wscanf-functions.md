---
title: 'Champs de spécification de format : fonctions scanf et wscanf'
ms.date: 11/04/2016
api_location:
- msvcr80.dll
- msvcr110.dll
- msvcr90.dll
- msvcr100.dll
- msvcr110_clr0400.dll
- msvcr120.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- wscanf
- scanf
helpviewer_keywords:
- width, specifications in scanf function
- scanf format specifications
- scanf width specifications
- scanf type field characters
- type fields, scanf function
- format specification fields for scanf function
- type fields
ms.assetid: 7e95de1b-0b71-4de3-9f81-c9560c78e039
ms.openlocfilehash: 78b64ea29aebdfb355525be69dc7a9fdece55367
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70944416"
---
# <a name="format-specification-fields-scanf-and-wscanf-functions"></a>Champs de spécification de format : fonctions scanf et wscanf

Les informations ici s'appliquent à l'ensemble de la famille de fonctions `scanf`, y compris les versions sécurisées, et décrivent les symboles utilisés pour indiquer aux fonctions `scanf` comment analyser le flux d'entrée, tel que le flux d'entrée `stdin` pour `scanf`, en valeurs insérées dans les variables de programme.

Une spécification de format se présente sous la forme suivante :

`%`[`*`] [[largeur](../c-runtime-library/scanf-width-specification.md)] [{[h &#124; l &#124; ll &#124; I64 &#124; L](../c-runtime-library/scanf-width-specification.md)}][type](../c-runtime-library/scanf-type-field-characters.md)

L'argument `format` spécifie l'interprétation de l'entrée et peut contenir un ou plusieurs des éléments suivants :

- Espaces blancs : espace (' '), tabulation ('\t') ou saut de ligne ('\n'). Un espace blanc oblige `scanf` à lire, mais pas à stocker, tous les espaces blancs consécutifs dans l’entrée jusqu’au caractère suivant autre qu’un espace blanc. Un espace blanc au format correspond à tout nombre (y compris 0) et à toute combinaison d'espaces blancs dans l'entrée.

- Caractères autres que des espaces blancs, sauf le symbole de pourcentage (`%`). Un caractère autre qu’un espace blanc oblige `scanf` à lire, mais pas à stocker, un caractère correspondant autre qu’un espace blanc. Si le caractère suivant dans le flux d'entrée ne correspond pas, `scanf` se termine.

- Spécifications de format, introduites par le symbole de pourcentage (`%`). Une spécification de format oblige `scanf` à lire et à convertir les caractères de l'entrée en valeurs d'un type spécifié. La valeur est affectée à un argument dans la liste d'arguments.

Le format est lu de gauche à droite. Les caractères en dehors des spécifications de format doivent correspondre à la séquence de caractères dans le flux d'entrée ; les caractères correspondants dans le flux d'entrée sont analysés mais pas stockés. Si un caractère du flux d'entrée est en conflit avec la spécification de format, `scanf` se termine, et le caractère est conservé dans le flux d'entrée comme s'il n'avait pas été lu.

Lorsque la première spécification de format est détectée, la valeur du premier champ d'entrée est convertie en fonction de cette spécification et stockée dans l'emplacement spécifié par le premier `argument`. La deuxième spécification de format entraîne la conversion et le stockage du deuxième champ d'entrée dans le deuxième `argument`, et ainsi de suite jusqu'à la fin de la chaîne de format.

Un champ d'entrée est défini comme étant tous les caractères jusqu'au premier espace blanc (espace, tabulation ou saut de ligne) ou jusqu'au premier caractère qui ne peut pas être converti en fonction de la spécification de format, ou jusqu'à ce que la largeur du champ (si spécifiée) soit atteinte. S'il y a trop d'arguments pour les spécifications données, les arguments supplémentaires sont évalués mais ignorés. Les résultats sont imprévisibles si le nombre d'arguments est insuffisant pour la spécification de format.

Chaque champ de la spécification de format est un caractère unique ou un nombre indiquant une option de mise en forme spécifique. Le caractère `type`, qui apparaît après le dernier champ de format facultatif, détermine si le champ d'entrée est interprété comme un caractère, une chaîne ou un nombre.

La spécification de format la plus simple contient uniquement le symbole de pourcentage et un caractère `type` (par exemple, `%s`). Si un symbole de pourcentage (`%`) est suivi d'un caractère qui n'a aucune signification en tant que caractère de contrôle de format, ce caractère et les caractères suivants (jusqu'au symbole de pourcentage suivant) sont traités comme une séquence ordinaire de caractères, c'est-à-dire, une séquence de caractères qui doivent correspondre à l'entrée. Par exemple, pour spécifier qu'un symbole de pourcentage doit être inséré, utilisez `%%`.

Un astérisque (`*`) suivant du symbole de pourcentage supprime l'attribution du champ d'entrée suivant, qui est interprété comme un champ du type spécifié. Le champ est analysé mais pas stocké.

Les versions sécurisées (celles avec le suffixe `_s`) de la famille de fonctions `scanf` requièrent qu'un paramètre de taille de mémoire tampon soit passé immédiatement après chaque paramètre de type `c`, `C`, `s`, `S` ou `[`. Pour plus d’informations sur les versions sécurisées de la famille `scanf` de fonctions, consultez [scanf_s, _scanf_s_l, wscanf_s, _wscanf_s_l](../c-runtime-library/reference/scanf-s-scanf-s-l-wscanf-s-wscanf-s-l.md).

## <a name="see-also"></a>Voir aussi

[Spécification de largeur scanf](../c-runtime-library/scanf-width-specification.md)<br/>
[Caractères du champ de type scanf](../c-runtime-library/scanf-type-field-characters.md)<br/>
[scanf, _scanf_l, wscanf, _wscanf_l](../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md)<br/>
[scanf_s, _scanf_s_l, wscanf_s, _wscanf_s_l](../c-runtime-library/reference/scanf-s-scanf-s-l-wscanf-s-wscanf-s-l.md)
