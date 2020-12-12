---
description: 'En savoir plus sur : Comparaison de caractères'
title: Comparaison de caractères
ms.date: 11/04/2016
helpviewer_keywords:
- comparing characters
- MBCS [C++], character comparison
- characters [C++], comparing
ms.assetid: 18846e44-3e6e-40c4-9b42-3153fb15db20
ms.openlocfilehash: 0e00e087074a70145f1a73694293edc3c522d69f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97297003"
---
# <a name="character-comparison"></a>Comparaison de caractères

Utilisez les conseils suivants :

- La comparaison d’un octet de tête connu avec un caractère ASCII fonctionne correctement :

    ```cpp
    if( *sz1 == 'A' )
    ```

- La comparaison de deux caractères inconnus requiert l’utilisation de l’une des macros définies dans mbstring. h :

    ```cpp
    if( !_mbccmp( sz1, sz2) )
    ```

   Cela garantit que les deux octets d’un caractère codé sur deux octets sont comparés pour déterminer leur égalité.

## <a name="see-also"></a>Voir aussi

[Conseils de programmation MBCS](../text/mbcs-programming-tips.md)<br/>
[Dépassement de mémoire tampon](../text/buffer-overflow.md)
