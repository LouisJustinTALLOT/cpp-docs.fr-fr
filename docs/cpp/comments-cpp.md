---
description: 'En savoir plus sur : commentaires (C++)'
title: Commentaires (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- code comments, C++
- comments, documenting code
- comments, C++ code
- white space, C++ comments
ms.assetid: 6fcb906c-c264-4083-84bc-373800b2e514
ms.openlocfilehash: b3bbcafe1f18c791fc5935161b6cdbfae0bf03cf
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97239790"
---
# <a name="comments-c"></a>Commentaires (C++)

Un commentaire est un texte que le compilateur ignore mais qui est utile pour les programmeurs. Les commentaires sont normalement utilisés pour annoter le code à des fins de référence ultérieure. Le compilateur les traite comme des espaces blancs. Vous pouvez utiliser des commentaires dans les tests pour rendre certaines lignes de code inactives. Toutefois, `#if` / `#endif` les directives de préprocesseur fonctionnent mieux pour cela, car vous pouvez entourer du code qui contient des commentaires, mais vous ne pouvez pas imbriquer des commentaires.

Un commentaire C++ est écrit de l’une des manières suivantes :

- Les `/*` caractères (barre oblique, astérisque), suivis de toute séquence de caractères (y compris les nouvelles lignes), suivis des `*/` caractères. Cette syntaxe est identique à celle de C ANSI.

- Les `//` caractères (deux barres obliques), suivis de toute séquence de caractères. Une nouvelle ligne qui n’est pas immédiatement précédée d’une barre oblique inverse met fin à cette forme de commentaire. Par conséquent, il est communément appelé « commentaire sur une seule ligne ».

Les caractères de commentaire ( `/*` , `*/` et `//` ) n’ont aucune signification particulière au sein d’une constante caractère, d’un littéral de chaîne ou d’un commentaire. Les commentaires utilisant la première syntaxe, par conséquent, ne peuvent pas être imbriqués.

## <a name="see-also"></a>Voir aussi

[Conventions lexicales](../cpp/lexical-conventions.md)
