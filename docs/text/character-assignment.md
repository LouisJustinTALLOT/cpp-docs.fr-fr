---
description: 'En savoir plus sur : l’assignation de caractères'
title: Assignation de caractère
ms.date: 11/04/2016
helpviewer_keywords:
- characters [C++], assignments
- MBCS [C++], character assignments
ms.assetid: dcc329cd-92df-4e20-817d-364be62ff28f
ms.openlocfilehash: d0db79acb8732404016f4a20579aff78ff996c17
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97187544"
---
# <a name="character-assignment"></a>Assignation de caractère

Prenons l’exemple suivant, dans lequel la **`while`** boucle analyse une chaîne, en copiant tous les caractères à l’exception de’X’dans une autre chaîne :

```cpp
while( *sz2 )
{
    if( *sz2 != 'X' )
        *sz1++ = *sz2++;
    else
        sz2++;
}
```

Le code copie l’octet à `sz2` l’emplacement désigné par `sz1` , puis incrémente `sz1` pour recevoir l’octet suivant. Toutefois, si le caractère suivant dans `sz2` est un caractère codé sur deux octets, l’assignation à `sz1` copie uniquement le premier octet. Le code suivant utilise une fonction portable pour copier le caractère en toute sécurité et un autre pour l’incrémentation `sz1` et la `sz2` bonne :

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
