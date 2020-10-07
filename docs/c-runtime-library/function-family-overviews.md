---
title: Vue d’ensemble des familles de fonctions
description: Vue d’ensemble des fonctions Microsoft C Runtime par famille.
ms.date: 10/05/2020
ms.assetid: b05a2755-9d11-4ea9-ab97-d00a4e872e16
ms.openlocfilehash: de5192cd03c3821afc646241d75a3e8c6c8c12e3
ms.sourcegitcommit: 8caaf5e00aeb727741a273aecafa15de293426cf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/07/2020
ms.locfileid: "91806511"
---
# <a name="function-family-overview"></a>Vue d’ensemble des familles de fonctions

Cette section répertorie les routines de la bibliothèque Runtime C par famille de fonctions.

## <a name="crt-library-routine-families"></a>Familles de routines de la bibliothèque CRT

[_exec, _wexec](exec-wexec-functions.md)\
Fonctions permettant de charger et d’exécuter un nouveau processus.

[Fonctions de recherche de nom de fichier](filename-search-functions.md)\
Fonctions permettant de rechercher des noms de fichiers spécifiés et de fermer des recherches.

[Syntaxe de spécification de format pour `printf` et `wprintf`](format-specification-syntax-printf-and-wprintf-functions.md)\
Décrit la chaîne de format et les arguments pour `printf` et `wprintf` .

[Caractères du champ de spécification `scanf` de format : et `wscanf`](format-specification-fields-scanf-and-wscanf-functions.md)\
Décrit les champs de spécification de format pour l’analyse d’un flux d’entrée pour l’ensemble `scanf` de la famille de fonctions.

[`is`, `isw` fonctions](is-isw-routines.md)\
Fonctions de test de caractères pour des éléments tels que les majuscules, les ASCII, les chiffres, les signes de ponctuation et ainsi de suite.

[`_ismbb` Mission](ismbb-routines.md)\
Fonctions permettant de tester une valeur entière pour déterminer si elle représente un caractère alphabétique, un caractère vierge, un caractère d’impression, etc.

[`_ismbc` Mission](ismbc-routines.md)\
Fonctions permettant de tester un caractère multioctet pour déterminer s’il représente un caractère alphabétique, un caractère vierge, un caractère d’impression, etc.

[`delete`, opérateur (CRT)](delete-operator-crt.md)\
À compter de Visual Studio 2013, le runtime C universel (UCRT) ne prend plus en charge la fonction de suppression d’opérateur propre à C++. Elle fait maintenant partie de la bibliothèque C++ standard.

[`new`, opérateur (CRT)](new-operator-crt.md)\
À compter de Visual Studio 2013, le runtime C universel (UCRT) ne prend plus en charge la fonction operator new propre à C++. Elle fait maintenant partie de la bibliothèque C++ standard.

[`printf` fonctions de paramètres positionnels](printf-p-positional-parameters.md)\
Les paramètres positionnels spécifient par nombre les arguments à remplacer dans un champ d’une chaîne de format.

[`scanf` caractères du champ de type](scanf-type-field-characters.md)\
Le caractère de type détermine si l’argument associé est interprété comme un caractère, une chaîne ou un nombre pour l’une des `scanf` familles de fonctions, y compris les versions sécurisées, telles que `scanf_s` .

[`scanf` spécification de largeur](scanf-width-specification.md)\
Le champ width est un entier décimal positif qui contrôle le nombre maximal de caractères à lire pour ce champ. S’applique à toute `scanf` famille de fonctions, y compris les versions sécurisées, telles que `scanf_s` .

[_spawn, _wspawn fonctions](spawn-wspawn-functions.md)\
Fonctions permettant de créer et d’exécuter un nouveau processus.

[`strcoll` Mission](strcoll-functions.md)\
Les `strcoll` `wcscoll` fonctions et comparent deux chaînes en fonction du `LC_COLLATE` paramètre de catégorie de la page de codes des paramètres régionaux.

[Fonctions de chaîne en valeur numérique](string-to-numeric-value-functions.md)\
La `strtod` famille de fonctions convertit une chaîne terminée par le caractère null en une valeur numérique.

[`vprintf` Mission](vprintf-functions.md)\
Les `vprintf` fonctions prennent un pointeur désignant une liste d’arguments, la formate et écrivent le résultat dans la destination spécifiée. Les fonctions diffèrent dans la validation des paramètres effectuée, qu’il s’agisse de chaînes de caractères larges ou codées sur un octet, de la destination de sortie et de la prise en charge de la spécification de l’ordre dans lequel les paramètres sont utilisés dans la chaîne de format.

## <a name="see-also"></a>Voir aussi

[Référence de la bibliothèque Runtime C](c-run-time-library-reference.md)