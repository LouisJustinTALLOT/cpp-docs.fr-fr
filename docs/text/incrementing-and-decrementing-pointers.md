---
title: Incrémentation et décrémentation de pointeurs | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- incrementing pointers
- MBCS [C++], pointers
- pointers [C++], multibyte characters
- decrementing pointers
ms.assetid: 0872b4a0-e2bd-4004-8319-070efb76f2fd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f4fff5d7ec20ce052e4d831f1556432186ebc7bb
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "42603358"
---
# <a name="incrementing-and-decrementing-pointers"></a>Incrémentation et décrémentation de pointeurs
Utilisez les conseils suivants :  
  
-   Pointer vers les octets de tête, pas les octets de Queue. Il est généralement déconseillé d’avoir un pointeur vers un octet de fin. Il est plus sûr d’analyser une chaîne vers l’avant, plutôt que dans l’ordre inverse.  
  
-   Il existe des fonctions incrémenter/décrémenter des pointeurs et des macros disponibles pour déplacement d’un caractère entier :  
  
    ```  
    sz1++;  
    ```  
  
     devient :  
  
    ```  
    sz1 = _mbsinc( sz1 );  
    ```  
  
     Le `_mbsinc` et `_mbsdec` fonctions correctement incrémenter et décrémenter dans `character` unités, quelles que soient la taille des caractères.  
  
-   Pour décréments, vous avez besoin d’un pointeur vers le début de la chaîne, comme dans l’exemple suivant :  
  
    ```  
    sz2--;  
    ```  
  
     devient :  
  
    ```  
    sz2 = _mbsdec( sz2Head, sz2 );  
    ```  
  
     Vous pouvez également votre pointeur d’en-tête peut être un caractère valide dans la chaîne, telles que :  
  
    ```  
    sz2Head < sz2  
    ```  
  
     Vous devez disposer d’un pointeur vers un octet de tête valide connu.  
  
-   Vous pouvez souhaiter conserver un pointeur vers le caractère précédent pour des appels plus rapides à `_mbsdec`.  
  
## <a name="see-also"></a>Voir aussi  
 [Conseils de programmation MBCS](../text/mbcs-programming-tips.md)   
 [Indices d’octets](../text/byte-indices.md)