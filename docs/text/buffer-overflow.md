---
title: Dépassement de capacité de mémoire tampon | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- buffers [C++], character sizes
- buffer overflows [C++]
- MBCS [C++], buffer overflow
ms.assetid: f2b7e40a-f02b-46d8-a449-51d26fc0c663
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 9bb362be360986371200c8cde292b3fff5acd7cd
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/09/2018
ms.locfileid: "40020185"
---
# <a name="buffer-overflow"></a>Dépassement de capacité du tampon
Différentes tailles de caractères peut entraîner des problèmes lorsque vous placez des caractères dans une mémoire tampon. Prenons le code suivant, les caractères d’une chaîne, `sz`, dans une mémoire tampon, `rgch`:  
  
```  
cb = 0;  
while( cb < sizeof( rgch ) )  
    rgch[ cb++ ] = *sz++;  
```  
  
 La question est : a été le dernier octet copié un octet de tête ? Les éléments suivants ne résout pas le problème, car il susceptible de déborder la mémoire tampon :  
  
```  
cb = 0;  
while( cb < sizeof( rgch ) )  
{  
    _mbccpy( rgch + cb, sz );  
    cb += _mbclen( sz );  
    sz = _mbsinc( sz );  
}  
```  
  
 Le `_mbccpy` appel tente de faire la chose correcte : copier le caractère, qu’il s’agisse de 1 ou 2 octets. Mais il ne tient pas compte que le dernier caractère copié peut tiennent pas dans la mémoire tampon si le caractère est égale à 2 octets. La solution appropriée est :  
  
```  
cb = 0;  
while( (cb + _mbclen( sz )) <= sizeof( rgch ) )  
{  
    _mbccpy( rgch + cb, sz );  
    cb += _mbclen( sz );  
    sz = _mbsinc( sz );  
}  
```  
  
 Ce code teste le dépassement de capacité de mémoire tampon possible dans la boucle de test, à l’aide de `_mbclen` pour tester la taille du caractère actuel vers lequel pointé `sz`. En effectuant un appel à la `_mbsnbcpy` (fonction), vous pouvez remplacer le code dans le **tandis que** boucle avec une seule ligne de code. Exemple :  
  
```  
_mbsnbcpy( rgch, sz, sizeof( rgch ) );  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Conseils de programmation MBCS](../text/mbcs-programming-tips.md)