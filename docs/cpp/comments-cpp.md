---
title: Commentaires (C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- code comments, C++
- comments, documenting code
- comments, C++ code
- white space, C++ comments
ms.assetid: 6fcb906c-c264-4083-84bc-373800b2e514
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a873ca82fc51c2f08e3788f9ec3c59c199961105
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46111873"
---
# <a name="comments-c"></a>Commentaires (C++)

Un commentaire est un texte qui le compilateur ignore, mais qui est utile pour les programmeurs. Commentaires sont normalement utilisés pour annoter le code pour référence ultérieure. Le compilateur les traite comme un espace blanc. Vous pouvez utiliser des commentaires dans le test pour rendre certaines lignes de code inactif ; Toutefois, `#if` / `#endif` directives de préprocesseur mieux fonctionneront pour cela, car vous pouvez entourer le code qui contient des commentaires, mais vous ne pouvez pas imbriquer les commentaires.

Un commentaire de C++ est écrit dans une des manières suivantes :

- Le `/*` (barre oblique, astérisque) caractères, suivi d’une séquence de caractères (y compris les nouvelles lignes), suivie par le `*/` caractères. Cette syntaxe est identique à ANSI C.

- Le `//` caractères (deux barres obliques), suivies de n’importe quelle séquence de caractères. Une nouvelle ligne pas immédiatement précédée d’une barre oblique inverse met fin à cette forme de commentaire. Par conséquent, il est généralement appelé un « commentaire de ligne simple ».

Les caractères de commentaire (`/*`, `*/`, et `//`) n’ont aucune signification particulière dans une constante de caractère littéral de chaîne ou insérer un commentaire. Commentaires à l’aide de la première syntaxe, par conséquent, ne peuvent pas être imbriquées.

## <a name="see-also"></a>Voir aussi

[Conventions lexicales](../cpp/lexical-conventions.md)