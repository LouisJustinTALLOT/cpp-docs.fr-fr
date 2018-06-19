---
title: Assignation de caractère | Documents Microsoft
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
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e403a619fc4c900aca51503862ff8f9dc315c2a3
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33856695"
---
# <a name="character-assignment"></a>Assignation de caractère
Prenons l’exemple suivant, dans lequel le `while` boucle analyse une chaîne et copie tous les caractères, à l’exception de « X » dans une autre chaîne :  
  
```  
while( *sz2 )  
{  
    if( *sz2 != 'X' )  
        *sz1++ = *sz2++;  
    else  
        sz2++;  
}  
```  
  
 Le code copie l’octet à `sz2` à l’emplacement vers lequel pointé `sz1`, puis incrémente `sz1` pour recevoir l’octet suivant. Toutefois, si le caractère suivant dans `sz2` est un caractère codés sur deux octets, l’assignation à `sz1` copie uniquement le premier octet. Le code suivant utilise une fonction portable pour copier le caractère et une autre pour incrémenter `sz1` et `sz2` correctement :  
  
```  
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
 [Conseils de programmation MBCS](../text/mbcs-programming-tips.md)   
 [Comparaison de caractères](../text/character-comparison.md)