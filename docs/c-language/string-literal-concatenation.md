---
description: 'En savoir plus sur : concaténation de littéraux de chaîne'
title: Concaténation de littéraux chaîne
ms.date: 11/04/2016
helpviewer_keywords:
- concatenating strings
- strings [C++], concatenating
ms.assetid: 51486b1f-4b1e-4061-9add-1aa38c6cdb3c
ms.openlocfilehash: 3486857cb0d218ea80c00252de02d9f29d58f2c8
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97137291"
---
# <a name="string-literal-concatenation"></a>Concaténation de littéraux chaîne

Pour former des littéraux de chaîne acceptant plusieurs lignes, vous pouvez concaténer les deux chaînes. Pour cela, tapez une barre oblique inverse, puis appuyez sur la touche RETOUR. La barre oblique fait que le compilateur ignore le saut de ligne suivant. Par exemple, la chaîne littérale

```
"Long strings can be bro\
ken into two or more pieces."
```

est identique à la chaîne

```
"Long strings can be broken into two or more pieces."
```

La concaténation de chaînes peut être utilisée n'importe où vous avez peut-être utilisé précédemment une barre oblique suivie d'un caractère de saut de ligne pour écrire des chaînes de plus d'une ligne.

Pour forcer une nouvelle ligne dans un littéral de chaîne, entrez la séquence d’échappement de saut de ligne (**\n**) au point dans la chaîne où vous voulez un saut de ligne, comme suit :

```
"Enter a number between 1 and 100\nOr press Return"
```

Les chaînes pouvant commencer dans toute colonne du code source et les chaînes longues pouvant être continuées dans toute colonne d'une ligne suivante, vous pouvez positionner les chaînes pour améliorer la lisibilité du code source. Dans les deux cas, leur représentation à l'écran reste inchangée. Par exemple :

```
printf_s ( "This is the first half of the string, "
           "this is the second half ") ;
```

Tant que chaque partie de la chaîne est placée entre guillemets doubles, les parties sont concaténées et sorties sous forme de chaîne unique. Cette concaténation se produit selon la séquence des événements pendant la compilation spécifiée par les [phases de traduction](../preprocessor/phases-of-translation.md).

```
"This is the first half of the string, this is the second half"
```

Un pointeur de chaîne, initialisé sous la forme de deux littéraux de chaîne distincts séparés uniquement par un espace blanc, est stocké sous forme d'une chaîne unique (les pointeurs sont présentés dans [Déclarations de pointeur](../c-language/pointer-declarations.md)). Une fois référencé correctement, comme dans l'exemple suivant, le résultat est identique à l'exemple précédent :

```
char *string = "This is the first half of the string, "
               "this is the second half";

printf_s( "%s" , string ) ;
```

Dans la phase de traduction 6, les séquences de caractères multioctets spécifiées par toute séquence de littéraux de chaîne adjacents ou de littéraux de chaîne étendue adjacents sont concaténés en une séquence de caractères multioctets unique. Par conséquent, ne concevez pas les programmes de manière à autoriser la modification des littéraux de chaîne pendant l'exécution. La norme C ANSI spécifie que le résultat de la modification d'une chaîne est indéfini.

## <a name="see-also"></a>Voir aussi

[Littéraux de chaîne C](../c-language/c-string-literals.md)
