---
title: Commentaires (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- code comments, C++
- comments, documenting code
- comments, C++ code
- white space, C++ comments
ms.assetid: 6fcb906c-c264-4083-84bc-373800b2e514
ms.openlocfilehash: 3326ad7d0b5118182a5d582061fd0c103986f232
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80189752"
---
# <a name="comments-c"></a>Commentaires (C++)

Un commentaire est un texte que le compilateur ignore mais qui est utile pour les programmeurs. Les commentaires sont normalement utilisés pour annoter le code à des fins de référence ultérieure. Le compilateur les traite comme des espaces blancs. Vous pouvez utiliser des commentaires dans les tests pour rendre certaines lignes de code inactives. Toutefois, `#if`/`#endif` directives de préprocesseur fonctionnent mieux pour cela, car vous pouvez entourer du code qui contient des commentaires, mais vous ne pouvez pas imbriquer des commentaires.

Un C++ commentaire est écrit de l’une des manières suivantes :

- Les caractères `/*` (barre oblique, astérisque), suivis d’une séquence de caractères (y compris les nouvelles lignes), suivis des caractères `*/`. Cette syntaxe est identique à celle de C ANSI.

- Le `//` (deux barres obliques), suivi de n’importe quelle séquence de caractères. Une nouvelle ligne qui n’est pas immédiatement précédée d’une barre oblique inverse met fin à cette forme de commentaire. Par conséquent, il est communément appelé « commentaire sur une seule ligne ».

Les caractères de commentaire (`/*`, `*/`et `//`) n’ont aucune signification particulière au sein d’une constante caractère, d’un littéral de chaîne ou d’un commentaire. Les commentaires utilisant la première syntaxe, par conséquent, ne peuvent pas être imbriqués.

## <a name="see-also"></a>Voir aussi

[Conventions lexicales](../cpp/lexical-conventions.md)
