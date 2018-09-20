---
title: Assignation de caractère | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- characters [C++], assignments
- MBCS [C++], character assignments
ms.assetid: dcc329cd-92df-4e20-817d-364be62ff28f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8e17ace90abef63ce4af1dd56b5bbe8dfed9510c
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46429550"
---
# <a name="character-assignment"></a>Assignation de caractère

Prenons l’exemple suivant, dans lequel le **tandis que** boucle analyse une chaîne et copie tous les caractères à l’exception de « X » dans une autre chaîne :

```cpp
while( *sz2 )
{
    if( *sz2 != 'X' )
        *sz1++ = *sz2++;
    else
        sz2++;
}
```

Le code copie l’octet au `sz2` à l’emplacement vers lequel pointé `sz1`, puis incrémente `sz1` pour recevoir l’octet suivant. Toutefois, si le caractère suivant dans `sz2` est un caractère sur deux octets, l’assignation à `sz1` copie uniquement le premier octet. Le code suivant utilise une fonction portable pour copier le caractère et une autre pour incrémenter `sz1` et `sz2` correctement :

```cpp
while( *sz2 )
{
    if( *sz2 != 'X' )
    {
        _mbscpy_s( sz1, 1, sz2 );
        sz1 = _mbsinc( sz1 );
        sz2 = _mbsinc( sz2 );
    }
    else
        sz2 = _mbsinc( sz2 );
}
```

## <a name="see-also"></a>Voir aussi

[Conseils de programmation MBCS](../text/mbcs-programming-tips.md)<br/>
[Comparaison de caractères](../text/character-comparison.md)