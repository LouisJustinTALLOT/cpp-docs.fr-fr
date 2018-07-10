---
title: Spécification de largeur scanf | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
apilocation:
- msvcr100.dll
- msvcr120.dll
- msvcr80.dll
- msvcr110_clr0400.dll
- msvcr110.dll
- msvcr90.dll
apitype: DLLExport
f1_keywords:
- scanf
dev_langs:
- C++
helpviewer_keywords:
- scanf function, width specification
ms.assetid: 94b4e8fe-c4a2-4799-8b6c-a2cf28ffb09c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f0052f4b270366b2f3aa1e1550f790efcb860597
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32418196"
---
# <a name="scanf-width-specification"></a>Spécification de largeur scanf
Ces informations s'appliquent à l'interprétation des chaînes de format dans la famille `scanf` de fonctions, y compris les versions sécurisées telles que `scanf_s`. Ces fonctions partent normalement de l'hypothèse que le flux d'entrée est divisé en une séquence de jetons. Les jetons sont séparés par un espace blanc (un espace, une tabulation ou une nouvelle ligne), ou dans le cas des types numériques, par la fin naturelle d'un type de données numérique, comme indiqué par le premier caractère qui ne peut pas être converti en texte numérique. Toutefois, la spécification de largeur peut servir à provoquer l'arrêt de l'analyse de l'entrée avant la fin naturelle d'un jeton.  
  
 La spécification de *width* se compose de caractères entre le signe `%` et le spécificateur de champ de type, lequel peut inclure un nombre entier positif appelé champ *width*, et un ou plusieurs caractères indiquant la taille du champ, lesquels peuvent également être considérés comme des modificateurs du type du champ, par exemple une indication précisant si l’entier est de type **short** ou **long**. Ces caractères correspondent au préfixe de taille.  
  
## <a name="the-width-field"></a>Champ Width  
 Le champ *width* est un entier décimal positif qui contrôle le nombre maximal de caractères à lire pour ce champ. Jusqu’à n (*width*) caractères sont convertis et stockés dans l’`argument` correspondant. Moins de n (*width*) caractères peuvent être lus si un espace blanc (espace, tabulation ou nouvelle ligne) ou un caractère qui ne peut pas être converti d’après le format donné est présent avant d’atteindre *width*.  
  
 La spécification de largeur est séparée et distincte de l'argument de taille de mémoire tampon imposé par les versions sécurisées de ces fonctions (c'est-à-dire `scanf_s`, `wscanf_s`, etc.). Dans l'exemple suivant, la spécification de largeur correspond à 20, ce qui indique qu'au maximum 20 caractères doivent être lus à partir du flux d'entrée. La longueur de mémoire tampon correspond à 21, ce qui inclut l'espace pour les 20 caractères possibles et le terminateur Null :  
  
```  
char str[21];  
scanf_s("%20s", str, 21);  
```  
  
 Si le champ *width* n’est pas utilisé, `scanf_s` tente de lire le jeton entier dans la chaîne. Si la taille spécifiée n'est pas suffisamment grande pour contenir le jeton entier, aucune valeur n'est écrite dans la chaîne de destination. Si le champ *width* est spécifié, les n (*width*) premiers caractères du jeton sont écrits dans la chaîne de destination avec le terminateur Null.  
  
## <a name="the-size-prefix"></a>Préfixe de taille  
 Les préfixes facultatifs **h**, **l**, **ll**, **I64** et **L** indiquent la taille de l’`argument` (long ou court, caractère codé sur un octet ou caractère large, selon le caractère de type qu’ils modifient). Ces caractères de spécification de format sont utilisés avec les caractères de type dans les fonctions `scanf` ou `wscanf` pour spécifier l'interprétation des arguments, comme indiqué dans le tableau suivant. Le préfixe de type **I64** est une extension Microsoft et n’est pas compatible avec la norme ANSI. Les caractères de type et leurs significations sont décrits dans le tableau « Caractères de type pour les fonctions scanf », dans [Caractères du champ de type scanf](../c-runtime-library/scanf-type-field-characters.md).  
  
> [!NOTE]
>  Les préfixes **h**, **l** et **L** sont des extensions Microsoft quand ils sont utilisés avec des données de type `char`.  
  
### <a name="size-prefixes-for-scanf-and-wscanf-format-type-specifiers"></a>Préfixes de taille pour les spécificateurs de type de format scanf et wscanf  
  
|Pour spécifier|Utilisez le préfixe|Avec le spécificateur de type|  
|----------------|----------------|-------------------------|  
|**double**|**l**|**e**, **E**, **f**, **g** ou **G**|  
|**long double** (identique à double)|**L**|**e**, **E**, **f**, **g** ou **G**|  
|**long int**|**l**|**d**, **i**, **o**, **x** ou **X**|  
|**long unsigned int**|**l**|**u**|  
|**long long**|**ll**|**d**, **i**, **o**, **x** ou **X**|  
|`short int`|**h**|**d**, **i**, **o**, **x** ou **X**|  
|**short unsigned int**|**h**|**u**|  
|__**int64**|**I64**|**d**, **i**, **o**, **u**, **x** ou **X**|  
|Caractère codé sur un octet avec `scanf`|**h**|**c** ou **C**|  
|Caractère codé sur un octet avec `wscanf`|**h**|**c** ou **C**|  
|Caractère large avec `scanf`|**l**|**c** ou **C**|  
|Caractère large avec `wscanf`|**l**|**c** ou **C**|  
|Chaîne de caractères codés sur un octet avec `scanf`|**h**|**s** ou **S**|  
|Chaîne de caractères codés sur un octet avec `wscanf`|**h**|**s** ou **S**|  
|Chaîne de caractères larges avec `scanf`|**l**|**s** ou **S**|  
|Chaîne de caractères larges avec `wscanf`|**l**|**s** ou **S**|  
  
 Les exemples suivants utilisent **h** et **l** avec les fonctions `scanf_s` et les fonctions `wscanf_s` :  
  
```  
scanf_s("%ls", &x, 2);     // Read a wide-character string  
wscanf_s(L"%hC", &x, 2);    // Read a single-byte character  
```  
  
 Si vous utilisez une fonction non sécurisée dans la famille `scanf`, omettez le paramètre de taille indiquant la longueur de la mémoire tampon de l'argument précédent.  
  
## <a name="reading-undelimited-strings"></a>Lecture de chaînes non délimitées  
 Pour la lecture des chaînes non délimitées par des espaces blancs, un jeu de caractères entre crochets (**[ ]**) peut remplacer le caractère de type **s** (string). Le jeu de caractères entre crochets est appelé chaîne de contrôle. Le champ d'entrée correspondant est lu jusqu'au premier caractère non visible dans la chaîne de contrôle. Si le premier caractère du jeu est un accent circonflexe (**^**), l’effet est inversé : le champ d’entrée est lu jusqu’au premier caractère visible dans le reste du jeu de caractères.  
  
 Notez que **%[a-z]** et **%[z-a]** sont interprétés comme étant équivalents à **%[abcde...z]**. Il s'agit d'une extension de fonction `scanf` commune. Toutefois, notez que la norme ANSI ne l'impose pas.  
  
## <a name="reading-unterminated-strings"></a>Lecture de chaînes non terminées  
 Pour stocker une chaîne sans stocker un caractère Null de fin (« \0 »), utilisez la spécification `%`*n***c** où *n* est un entier décimal. Dans ce cas, le caractère de type **c** indique que l’argument est un pointeur vers un tableau de caractères. Les *n* prochains caractères sont lus à partir du flux d’entrée dans l’emplacement spécifié, et aucun caractère Null ('\0') n’est ajouté. Si *n* n’est pas spécifié, sa valeur par défaut est 1.  
  
## <a name="when-scanf-stops-reading-a-field"></a>Quand scanf arrête de lire un champ  
 La fonction `scanf` analyse chaque champ d'entrée, caractère par caractère. Elle peut aussi arrêter de lire un champ d'entrée particulier avant d'atteindre un espace pour diverses raisons :  
  
-   La largeur spécifiée a été atteinte.  
  
-   Impossible de convertir le caractère suivant, tel que cela est spécifié.  
  
-   Le caractère suivant est en conflit avec un caractère de la chaîne de contrôle à laquelle il est censé correspondre.  
  
-   Le caractère suivant n'apparaît pas dans un jeu de caractères donné.  
  
 Pour une raison quelconque, quand la fonction `scanf` arrête de lire un champ d'entrée, le champ d'entrée suivant est censé débuter au premier caractère non lu. Le caractère en conflit, le cas échéant, est considéré comme non lu. Il s'agit du premier caractère du champ d'entrée suivant ou du premier caractère rencontré durant les opérations de lecture suivantes du flux d'entrée.  
  
## <a name="see-also"></a>Voir aussi  
 [scanf, _scanf_l, wscanf, _wscanf_l](../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md)   
 [scanf_s, _scanf_s_l, wscanf_s, _wscanf_s_l](../c-runtime-library/reference/scanf-s-scanf-s-l-wscanf-s-wscanf-s-l.md)   
 [Champs de spécification de format : fonctions scanf et wscanf](../c-runtime-library/format-specification-fields-scanf-and-wscanf-functions.md)   
 [Caractères du champ de type scanf](../c-runtime-library/scanf-type-field-characters.md)