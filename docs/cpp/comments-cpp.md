---
title: Commentaires (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- code comments, C++
- comments, documenting code
- comments, C++ code
- white space, C++ comments
ms.assetid: 6fcb906c-c264-4083-84bc-373800b2e514
ms.openlocfilehash: a90d9d37e69cb2e8be4ab18f77026fdce1221307
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62399172"
---
# <a name="comments-c"></a>Commentaires (C++)

Un commentaire est un texte qui le compilateur ignore, mais qui est utile pour les programmeurs. Commentaires sont normalement utilisés pour annoter le code pour référence ultérieure. Le compilateur les traite comme un espace blanc. Vous pouvez utiliser des commentaires dans le test pour rendre certaines lignes de code inactif ; Toutefois, `#if` / `#endif` directives de préprocesseur mieux fonctionneront pour cela, car vous pouvez entourer le code qui contient des commentaires, mais vous ne pouvez pas imbriquer les commentaires.

Un commentaire de C++ est écrit dans une des manières suivantes :

- Le `/*` (barre oblique, astérisque) caractères, suivi d’une séquence de caractères (y compris les nouvelles lignes), suivie par le `*/` caractères. Cette syntaxe est identique à ANSI C.

- Le `//` caractères (deux barres obliques), suivies de n’importe quelle séquence de caractères. Une nouvelle ligne pas immédiatement précédée d’une barre oblique inverse met fin à cette forme de commentaire. Par conséquent, il est généralement appelé un « commentaire de ligne simple ».

Les caractères de commentaire (`/*`, `*/`, et `//`) n’ont aucune signification particulière dans une constante de caractère littéral de chaîne ou insérer un commentaire. Commentaires à l’aide de la première syntaxe, par conséquent, ne peuvent pas être imbriquées.

## <a name="see-also"></a>Voir aussi

[Conventions lexicales](../cpp/lexical-conventions.md)