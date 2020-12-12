---
description: 'En savoir plus sur : dernier caractère d’une chaîne'
title: Dernier caractère d'une chaîne
ms.date: 11/04/2016
helpviewer_keywords:
- last character in string
- MBCS [C++], last character in string
ms.assetid: 0a180376-4e55-41e8-9c64-539c7b6d8047
ms.openlocfilehash: 10ab90614509508b9667c29ccf166ddaf784a92e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97207239"
---
# <a name="last-character-in-a-string"></a>Dernier caractère d'une chaîne

Utilisez les conseils suivants :

- Dans de nombreux cas, les plages d’octets de fin chevauchent le jeu de caractères ASCII. Vous pouvez utiliser en toute sécurité des analyses bytewise pour tous les caractères de contrôle (moins de 32).

- Examinez la ligne de code suivante, qui peut vérifier si le dernier caractère d’une chaîne est une barre oblique inverse :

    ```cpp
    if ( sz[ strlen( sz ) - 1 ] == '\\' )    // Is last character a '\'?
        // . . .
    ```

   Étant donné que `strlen` ne prend pas en charge MBCS, il retourne le nombre d’octets, et non le nombre de caractères, dans une chaîne multioctet. Notez également que dans certaines pages de codes (932, par exemple), « \\ » (0x5C) est un octet de fin valide ( `sz` est une chaîne C).

   Une solution possible consiste à réécrire le code de cette façon :

    ```cpp
    char *pLast;
    pLast = _mbsrchr( sz, '\\' );    // find last occurrence of '\' in sz
    if ( pLast && ( *_mbsinc( pLast ) == '\0' ) )
        // . . .
    ```

   Ce code utilise les fonctions MBCS `_mbsrchr` et `_mbsinc` . Étant donné que ces fonctions prennent en charge MBCS, elles peuvent faire la distinction entre un \\ caractère « » et un octet de fin « \\ ». Le code effectue une action si le dernier caractère de la chaîne est une valeur null (' \ 0 ').

## <a name="see-also"></a>Voir aussi

[Conseils de programmation MBCS](../text/mbcs-programming-tips.md)<br/>
[Assignation de caractère](../text/character-assignment.md)
