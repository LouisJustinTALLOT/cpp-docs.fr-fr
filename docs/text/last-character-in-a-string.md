---
title: Dernier caractère d’une chaîne | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- last character in string
- MBCS [C++], last character in string
ms.assetid: 0a180376-4e55-41e8-9c64-539c7b6d8047
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 88cde1d2eb30103462f7ae8f8c06274a2977fc36
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33855641"
---
# <a name="last-character-in-a-string"></a>Dernier caractère d'une chaîne
Utilisez les conseils suivants :  
  
-   Plages d’octets piste chevauchent jeu dans de nombreux cas de caractères ASCII. Vous pouvez en toute sécurité utiliser des analyses pour des caractères de contrôle (inférieur à 32).  
  
-   Tenez compte de la ligne suivante du code, qui peut être de vérifier si le dernier caractère dans une chaîne est un caractère de barre oblique inverse :  
  
    ```  
    if ( sz[ strlen( sz ) - 1 ] == '\\' )    // Is last character a '\'?  
        // . . .  
    ```  
  
     Étant donné que `strlen` n’est pas compatible MBCS, il retourne le nombre d’octets, pas le nombre de caractères, d’une chaîne multioctet. Notez également que, dans certaines pages de codes (932, par exemple), «\\» (0x5c) est un octet de fin valide (`sz` est une chaîne C).  
  
     Une solution possible consiste à réécrire le code de cette façon :  
  
    ```  
    char *pLast;  
    pLast = _mbsrchr( sz, '\\' );    // find last occurrence of '\' in sz  
    if ( pLast && ( *_mbsinc( pLast ) == '\0' ) )  
        // . . .  
    ```  
  
     Ce code utilise les fonctions MBCS `_mbsrchr` et `_mbsinc`. Étant donné que ces fonctions prennent en charge de MBCS, elles peuvent faire la distinction entre un '\\'caractère et un octet de fin'\\'. Le code effectue une action si le dernier caractère de la chaîne est une valeur null ('\0').  
  
## <a name="see-also"></a>Voir aussi  
 [Conseils de programmation MBCS](../text/mbcs-programming-tips.md)   
 [Assignation de caractère](../text/character-assignment.md)