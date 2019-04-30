---
title: Assignation de caractère
ms.date: 11/04/2016
helpviewer_keywords:
- characters [C++], assignments
- MBCS [C++], character assignments
ms.assetid: dcc329cd-92df-4e20-817d-364be62ff28f
ms.openlocfilehash: 88c42435d336ba78e87c9acfe3ada5fddbd18fb8
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62410744"
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
