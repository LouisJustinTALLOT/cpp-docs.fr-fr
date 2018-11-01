---
title: Comparaison de caractères
ms.date: 11/04/2016
helpviewer_keywords:
- comparing characters
- MBCS [C++], character comparison
- characters [C++], comparing
ms.assetid: 18846e44-3e6e-40c4-9b42-3153fb15db20
ms.openlocfilehash: 206910d4b76f93a92ee5230a227d6f0346a85e61
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50615408"
---
# <a name="character-comparison"></a>Comparaison de caractères

Utilisez les conseils suivants :

- Comparaison d’un octet de tête connu avec un caractère ASCII fonctionne correctement :

    ```cpp
    if( *sz1 == 'A' )
    ```

- Comparaison de deux caractères inconnus nécessite l’utilisation de l’une des macros définies dans Mbstring.h :

    ```cpp
    if( !_mbccmp( sz1, sz2) )
    ```

   Cela garantit que les deux octets d’un caractère sur deux octets sont comparés sont égaux.

## <a name="see-also"></a>Voir aussi

[Conseils de programmation MBCS](../text/mbcs-programming-tips.md)<br/>
[Dépassement de mémoire tampon](../text/buffer-overflow.md)