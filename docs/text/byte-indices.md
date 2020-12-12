---
description: En savoir plus sur les index d’octets
title: Indices d'octets
ms.date: 11/04/2016
helpviewer_keywords:
- MBCS [C++], byte indices
- byte indices [C++]
ms.assetid: f6e7774a-86c6-41c2-89e3-74fd46432e47
ms.openlocfilehash: 5ee4b2cb8611893c71f5c6597e619cc73e2848ef
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97187557"
---
# <a name="byte-indices"></a>Indices d'octets

Utilisez les conseils suivants :

- L’utilisation d’un index bytewise dans une chaîne présente des problèmes similaires à ceux posés par la manipulation des pointeurs. Prenons l’exemple suivant, qui analyse une chaîne pour une barre oblique inverse :

    ```cpp
    while ( rgch[ i ] != '\\' )
        i++;
    ```

   Cela peut indexer un octet de fin, et non un octet de tête, et il peut donc ne pas pointer vers un `character` .

- Utilisez la fonction [_mbclen](../c-runtime-library/reference/mbclen-mblen-mblen-l.md) pour résoudre le problème précédent :

    ```cpp
    while ( rgch[ i ] != '\\' )
        i += _mbclen ( rgch + i );
    ```

   Cela permet d’indexer correctement sur un octet de tête, donc un `character` . La `_mbclen` fonction détermine la taille d’un caractère (1 ou 2 octets).

## <a name="see-also"></a>Voir aussi

[Conseils de programmation MBCS](../text/mbcs-programming-tips.md)<br/>
[Dernier caractère d’une chaîne](../text/last-character-in-a-string.md)
