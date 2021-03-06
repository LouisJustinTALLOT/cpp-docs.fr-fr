---
description: 'En savoir plus sur : dépassement de mémoire tampon'
title: Dépassement de capacité du tampon
ms.date: 11/04/2016
helpviewer_keywords:
- buffers [C++], character sizes
- buffer overflows [C++]
- MBCS [C++], buffer overflow
ms.assetid: f2b7e40a-f02b-46d8-a449-51d26fc0c663
ms.openlocfilehash: 17da102b9a48a34d9879c08f0470ced3852ed0ae
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97187596"
---
# <a name="buffer-overflow"></a>Dépassement de capacité du tampon

La variation de la taille des caractères peut entraîner des problèmes lorsque vous placez des caractères dans une mémoire tampon. Prenons le code suivant, qui copie les caractères d’une chaîne, `sz` , dans une mémoire tampon `rgch` :

```cpp
cb = 0;
while( cb < sizeof( rgch ) )
    rgch[ cb++ ] = *sz++;
```

La question est : le dernier octet a-t-il copié un octet de tête ? Le problème suivant ne résout pas le problème, car il peut potentiellement dépasser la mémoire tampon :

```cpp
cb = 0;
while( cb < sizeof( rgch ) )
{
    _mbccpy( rgch + cb, sz );
    cb += _mbclen( sz );
    sz = _mbsinc( sz );
}
```

L' `_mbccpy` appel tente d’effectuer l’opération correcte (copiez le caractère entier, qu’il soit de 1 ou 2 octets). Toutefois, il ne tient pas compte du fait que le dernier caractère copié peut ne pas correspondre à la mémoire tampon si la largeur du caractère est de 2 octets. La solution correcte est la suivante :

```cpp
cb = 0;
while( (cb + _mbclen( sz )) <= sizeof( rgch ) )
{
    _mbccpy( rgch + cb, sz );
    cb += _mbclen( sz );
    sz = _mbsinc( sz );
}
```

Ce code teste le risque de dépassement de mémoire tampon dans le test de boucle, en utilisant `_mbclen` pour tester la taille du caractère actuel pointé par `sz` . En effectuant un appel à la `_mbsnbcpy` fonction, vous pouvez remplacer le code dans la **`while`** boucle par une seule ligne de code. Par exemple :

```cpp
_mbsnbcpy( rgch, sz, sizeof( rgch ) );
```

## <a name="see-also"></a>Voir aussi

[Conseils de programmation MBCS](../text/mbcs-programming-tips.md)
