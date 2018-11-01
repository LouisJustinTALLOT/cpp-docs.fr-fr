---
title: Dernier caractère d'une chaîne
ms.date: 11/04/2016
helpviewer_keywords:
- last character in string
- MBCS [C++], last character in string
ms.assetid: 0a180376-4e55-41e8-9c64-539c7b6d8047
ms.openlocfilehash: 535c2e58edab49e0e2a9dbc3fce9821d5909f1c5
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50456262"
---
# <a name="last-character-in-a-string"></a>Dernier caractère d'une chaîne

Utilisez les conseils suivants :

- Plages d’octets piste chevauchent le jeu dans de nombreux cas de caractères ASCII. Vous pouvez en toute sécurité utiliser des analyses pour les caractères de contrôle (inférieur à 32).

- Prenez en compte la ligne suivante du code, ce qui peut être de vérifier si le dernier caractère dans une chaîne est un caractère de barre oblique inverse :

    ```cpp
    if ( sz[ strlen( sz ) - 1 ] == '\\' )    // Is last character a '\'?
        // . . .
    ```

   Étant donné que `strlen` n’est pas compatible MBCS, elle retourne le nombre d’octets, pas le nombre de caractères, d’une chaîne multioctets. Notez également que dans certaines pages de codes (932, par exemple), «\\» (0x5c) est un octet de fin valide (`sz` est une chaîne C).

   Une solution possible consiste à réécrire le code de cette façon :

    ```cpp
    char *pLast;
    pLast = _mbsrchr( sz, '\\' );    // find last occurrence of '\' in sz
    if ( pLast && ( *_mbsinc( pLast ) == '\0' ) )
        // . . .
    ```

   Ce code utilise les fonctions MBCS `_mbsrchr` et `_mbsinc`. Étant donné que ces fonctions prennent en charge de MBCS, ils peuvent faire la distinction entre un «\\'caractères et un octet de fin'\\'. Le code effectue une action si le dernier caractère dans la chaîne est une valeur null ('\0').

## <a name="see-also"></a>Voir aussi

[Conseils de programmation MBCS](../text/mbcs-programming-tips.md)<br/>
[Assignation de caractère](../text/character-assignment.md)