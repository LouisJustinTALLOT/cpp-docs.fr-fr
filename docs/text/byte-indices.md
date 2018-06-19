---
title: Indices d’octets | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MBCS [C++], byte indices
- byte indices [C++]
ms.assetid: f6e7774a-86c6-41c2-89e3-74fd46432e47
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 509e66c7ea458519eaa9dc4f52c8a6b65c789d0f
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33863798"
---
# <a name="byte-indices"></a>Indices d'octets
Utilisez les conseils suivants :  
  
-   Travail avec des index dans une chaîne présente des problèmes semblables à ceux posés par la manipulation du pointeur. Considérez cet exemple, qui analyse une chaîne d’un caractère de barre oblique inverse :  
  
    ```  
    while ( rgch[ i ] != '\\' )  
        i++;  
    ```  
  
     Cela peut indexer un octet de fin, et non un octet de tête, et par conséquent, elle ne peut pas pointer sur un `character`.  
  
-   Utilisez le [_mbclen](../c-runtime-library/reference/mbclen-mblen-mblen-l.md) afin de résoudre le problème précédent :  
  
    ```  
    while ( rgch[ i ] != '\\' )  
        i += _mbclen ( rgch + i );  
    ```  
  
     Ce code indexe correctement un octet de tête, par conséquent, pour un `character`. Le `_mbclen` fonction détermine la taille d’un caractère (1 ou 2 octets).  
  
## <a name="see-also"></a>Voir aussi  
 [Conseils de programmation MBCS](../text/mbcs-programming-tips.md)   
 [Dernier caractère d’une chaîne](../text/last-character-in-a-string.md)