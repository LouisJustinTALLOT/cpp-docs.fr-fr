---
description: En savoir plus sur la `scanf` spécification de largeur
title: scanf, spécification de largeur
ms.date: 10/22/2019
helpviewer_keywords:
- scanf function, width specification
ms.assetid: 94b4e8fe-c4a2-4799-8b6c-a2cf28ffb09c
ms.openlocfilehash: f4b0e13ef87add74bc802ba11ea6b87d0dfc6b8a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97284432"
---
# <a name="scanf-width-specification"></a>`scanf` spécification de largeur

Ces informations s'appliquent à l'interprétation des chaînes de format dans la famille `scanf` de fonctions, y compris les versions sécurisées telles que `scanf_s`. Ces fonctions partent normalement de l'hypothèse que le flux d'entrée est divisé en une séquence de jetons. Les jetons sont séparés par un espace blanc (espace, tabulation ou saut de ligne), ou pour les types numériques, par la fin naturelle d’un type de données numérique, comme indiqué par le premier caractère qui ne peut pas être converti en texte numérique. Toutefois, la spécification de largeur peut servir à provoquer l'arrêt de l'analyse de l'entrée avant la fin naturelle d'un jeton.

La spécification de *largeur* est composée de caractères entre `%` et le spécificateur de champ de type, qui peut inclure un entier positif appelé champ de *largeur* et un ou plusieurs caractères indiquant la taille du champ, qui peut également être considéré comme des modificateurs du type du champ, par exemple une indication précisant si le type entier est **`short`** ou **`long`** . Ces caractères correspondent au préfixe de taille.

## <a name="the-width-field"></a>Champ Width

Le champ *Width* est un entier décimal positif qui contrôle le nombre maximal de caractères à lire pour ce champ. Les caractères de *largeur* ne sont pas plus ou moins convertis dans le correspondant `argument` . Moins de *largeur* caractères peuvent être lus si un espace blanc ou un caractère qui ne peut pas être converti selon le format donné se produit avant que *Width* soit atteint.

La spécification de largeur est séparée et distincte de l’argument de taille de mémoire tampon requis par les versions sécurisées de ces fonctions (par exemple,,, etc `scanf_s` `wscanf_s` .). Dans l'exemple suivant, la spécification de largeur correspond à 20, ce qui indique qu'au maximum 20 caractères doivent être lus à partir du flux d'entrée. La longueur de mémoire tampon correspond à 21, ce qui inclut l'espace pour les 20 caractères possibles et le terminateur Null :

```C
char str[21];
scanf_s("%20s", str, 21);
```

Si le champ *Width* n’est pas utilisé, `scanf_s` tente de lire le jeton entier dans la chaîne. Si la taille spécifiée n’est pas suffisamment grande pour contenir le jeton entier, rien n’est écrit dans la chaîne de destination. Si le champ *Width* est spécifié, les caractères de la première *largeur* dans le jeton sont écrits dans la chaîne de destination, avec la marque de fin null.

## <a name="the-size-prefix"></a>Préfixe de taille

Les préfixes facultatifs **h**, **hh**, **l**, **ll**, **I64** et **l** indiquent la taille de `argument` (long ou Short, caractère codé sur un octet ou caractère élargi, selon le caractère de type qu’ils modifient). Ces caractères de spécification de format sont utilisés avec les caractères de type dans les fonctions `scanf` ou `wscanf` pour spécifier l'interprétation des arguments, comme indiqué dans le tableau suivant. Le préfixe de type **I64** est une extension Microsoft et n’est pas compatible avec le langage C standard. Les caractères de type et leurs significations sont décrits dans la table « caractères de type pour les fonctions scanf » dans les [ `scanf` caractères de champ de type](../c-runtime-library/scanf-type-field-characters.md).

> [!NOTE]
> Les préfixes **h**, **l** et **l** sont des extensions Microsoft quand ils sont utilisés avec des données de type **`char`** .

### <a name="size-prefixes-for-scanf-and-wscanf-format-type-specifiers"></a>Préfixes de taille pour les `scanf` `wscanf` spécificateurs de type de format et

|Pour spécifier|Utilisez le préfixe|Avec le spécificateur de type|
|----------------|----------------|-------------------------|
|**`double`**|**l**|**e**, **E**, **f**, **g** ou **G**|
|**`long double`** (identique à **`double`** )|**Budget**|**e**, **E**, **f**, **g** ou **G**|
|**`long int`**|**l**|**d**, **i**, **o**, **x** ou **X**|
|**`long unsigned int`**|**l**|**u**|
|**`long long`**|**UT**|**d**, **i**, **o**, **x** ou **X**|
|**`short int`**|**h**|**d**, **i**, **o**, **x** ou **X**|
|**`short unsigned int`**|**h**|**u**|
|**`char`**|**hh**|**d**, **i**, **o**, **x** ou **X**|
|**`unsigned char`**|**hh**|**u**|
|**`int64`**|**I64**|**d**, **i**, **o**, **u**, **x** ou **X**|
|Caractère codé sur un octet avec `scanf`|**h**|**c** ou **c**|
|Caractère codé sur un octet avec `wscanf`|**h**|**c** ou **c**|
|Caractère large avec `scanf`|**l**|**c** ou **c**|
|Caractère large avec `wscanf`|**l**|**c** ou **c**|
|Chaîne de caractères codés sur un octet avec `scanf`|**h**|**s** ou **S**|
|Chaîne de caractères codés sur un octet avec `wscanf`|**h**|**s** ou **S**|
|Chaîne de caractères larges avec `scanf`|**l**|**s** ou **S**|
|Chaîne de caractères larges avec `wscanf`|**l**|**s** ou **S**|

Les exemples suivants utilisent **h** et **l** avec les fonctions `scanf_s` et les fonctions `wscanf_s` :

```C
scanf_s("%ls", &x, 2);     // Read a wide-character string
wscanf_s(L"%hC", &x, 2);    // Read a single-byte character
```

Si vous utilisez une fonction non sécurisée dans la famille `scanf`, omettez le paramètre de taille indiquant la longueur de la mémoire tampon de l'argument précédent.

## <a name="reading-undelimited-strings"></a>Lecture des chaînes délimitées

Pour lire des chaînes non délimitées par des espaces blancs, un jeu de caractères entre crochets ( **`[ ]`** ) peut remplacer le caractère de type **s** (String). Le jeu de caractères entre crochets est appelé *chaîne de contrôle*. Le champ d’entrée correspondant est lu jusqu’au premier caractère qui n’apparaît pas dans la chaîne de contrôle. Si le premier caractère du jeu est un signe insertion ( **`^`** ), l’effet est inversé : le champ d’entrée est lu jusqu’au premier caractère qui apparaît dans le reste du jeu de caractères.

**% [A-z]** et **% [z-a]** sont interprétés comme équivalents à **% [abcde... z]**. Il s’agit d’une `scanf` extension de fonction commune, mais elle n’est pas requise par le C standard.

## <a name="reading-unterminated-strings"></a>Lecture des chaînes non terminées

Pour stocker une chaîne sans stocker un caractère null de fin (' \ 0 '), utilisez la spécification `%Nc` , où *N* est un entier décimal. Dans ce cas, le caractère de type **c** indique que l’argument est un pointeur vers un tableau de caractères. Les *N* prochains caractères sont lus à partir du flux d’entrée dans l’emplacement spécifié, et aucun caractère null (' \ 0 ') n’est ajouté. Si *N* n’est pas spécifié, sa valeur par défaut est 1.

## <a name="when-scanf-stops-reading-a-field"></a>Quand `scanf` arrête la lecture d’un champ

La fonction `scanf` analyse chaque champ d'entrée, caractère par caractère. Il peut arrêter la lecture d’un champ d’entrée particulier avant d’atteindre un espace pour l’une des raisons suivantes :

- La largeur spécifiée a été atteinte.

- Le caractère suivant ne peut pas être converti comme spécifié.

- Le caractère suivant est en conflit avec un caractère dans la chaîne de contrôle à laquelle il est supposé correspondre.

- Le caractère suivant n'apparaît pas dans un jeu de caractères donné.

Pour une raison quelconque, quand la fonction `scanf` arrête de lire un champ d'entrée, le champ d'entrée suivant est censé débuter au premier caractère non lu. Le caractère en conflit, le cas échéant, est considéré comme non lu. Il s’agit du premier caractère du champ d’entrée suivant, ou du premier caractère dans les opérations de lecture suivantes sur le flux d’entrée.

## <a name="see-also"></a>Voir aussi

[`scanf`, `_scanf_l`, `wscanf`, `_wscanf_l`](../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md)<br/>
[`scanf_s`, `_scanf_s_l`, `wscanf_s`, `_wscanf_s_l`](../c-runtime-library/reference/scanf-s-scanf-s-l-wscanf-s-wscanf-s-l.md)<br/>
[Champs de spécification de format : `scanf` `wscanf` fonctions et](../c-runtime-library/format-specification-fields-scanf-and-wscanf-functions.md)<br/>
[`scanf` Caractères du champ de type](../c-runtime-library/scanf-type-field-characters.md)<br/>
