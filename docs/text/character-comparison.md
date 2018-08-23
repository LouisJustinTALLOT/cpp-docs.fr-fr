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
ms.openlocfilehash: 246801abcb04cc8d9c2fd1a005183501bde240d1
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "42612324"
---
# <a name="character-comparison"></a>Comparaison de caractères
Utilisez les conseils suivants :  
  
-   Comparaison d’un octet de tête connu avec un caractère ASCII fonctionne correctement :  
  
    ```  
    if( *sz1 == 'A' )  
    ```  
  
-   Comparaison de deux caractères inconnus nécessite l’utilisation de l’une des macros définies dans Mbstring.h :  
  
    ```  
    if( !_mbccmp( sz1, sz2) )  
    ```  
  
     Cela garantit que les deux octets d’un caractère sur deux octets sont comparés sont égaux.  
  
## <a name="see-also"></a>Voir aussi  
 [Conseils de programmation MBCS](../text/mbcs-programming-tips.md)   
 [Dépassement de mémoire tampon](../text/buffer-overflow.md)