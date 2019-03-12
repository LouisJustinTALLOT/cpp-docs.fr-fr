---
title: Indices d'octets
ms.date: 11/04/2016
helpviewer_keywords:
- MBCS [C++], byte indices
- byte indices [C++]
ms.assetid: f6e7774a-86c6-41c2-89e3-74fd46432e47
ms.openlocfilehash: 5305a977c23d7a978a89c84809cc6fab8c5731eb
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/11/2019
ms.locfileid: "57751594"
---
# <a name="byte-indices"></a>Indices d'octets

Utilisez les conseils suivants :

- Travailler avec des index dans une chaîne présente des problèmes similaires à ceux posés par la manipulation du pointeur. Considérez cet exemple, qui analyse une chaîne pour une barre oblique inverse :

    ```cpp
    while ( rgch[ i ] != '\\' )
        i++;
    ```

   Cela peut indexer un octet de fin, pas un octet de tête, et par conséquent, elle ne peut pas pointer sur un `character`.

- Utilisez le [_mbclen](../c-runtime-library/reference/mbclen-mblen-mblen-l.md) fonction permettant de résoudre le problème précédent :

    ```cpp
    while ( rgch[ i ] != '\\' )
        i += _mbclen ( rgch + i );
    ```

   Ce code indexe correctement un octet de tête, par conséquent, pour un `character`. Le `_mbclen` fonction détermine la taille d’un caractère (1 ou 2 octets).

## <a name="see-also"></a>Voir aussi

[Conseils de programmation MBCS](../text/mbcs-programming-tips.md)<br/>
[Dernier caractère d’une chaîne](../text/last-character-in-a-string.md)
