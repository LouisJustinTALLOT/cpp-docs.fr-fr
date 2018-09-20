---
title: Comparaison de caractères | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- comparing characters
- MBCS [C++], character comparison
- characters [C++], comparing
ms.assetid: 18846e44-3e6e-40c4-9b42-3153fb15db20
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c3412939bac9dace6f3abaacda75ed73d6e60f21
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46428068"
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