---
title: Comparaison de caractères | Documents Microsoft
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
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: b969783a19c0836a8ab81d75820fc688df3ef31e
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33854949"
---
# <a name="character-comparison"></a>Comparaison de caractères
Utilisez les conseils suivants :  
  
-   Comparaison d’un octet de tête connu par un caractère ASCII fonctionne correctement :  
  
    ```  
    if( *sz1 == 'A' )  
    ```  
  
-   Comparaison de deux caractères inconnus nécessite l’utilisation de l’une des macros définies dans Mbstring.h :  
  
    ```  
    if( !_mbccmp( sz1, sz2) )  
    ```  
  
     Cela garantit que les deux octets d’un caractère sur deux octets sont comparés pour l’égalité.  
  
## <a name="see-also"></a>Voir aussi  
 [Conseils de programmation MBCS](../text/mbcs-programming-tips.md)   
 [Dépassement de mémoire tampon](../text/buffer-overflow.md)