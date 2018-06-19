---
title: Conseils de programmation MBCS | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- _mbcs
dev_langs:
- C++
helpviewer_keywords:
- programming [C++], MBCS
- character sets [C++], multibyte
- MBCS [C++], programming
- multibyte characters [C++]
ms.assetid: d8ad36b8-917f-474e-8adb-69462adecd17
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 7eb6e298961580c959235a97f37793df41d1124f
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33855277"
---
# <a name="mbcs-programming-tips"></a>Conseils de programmation MBCS
Dans tout nouveau développement, vous devez utiliser l’encodage de caractères Unicode pour toutes les chaînes que les utilisateurs finaux peuvent voir éventuellement. MBCS est une technologie héritée qui a été remplacée par le format Unicode. Cette section fournit des conseils pour les développeurs qui doivent conserver les programmes existants qui utilisent MBCS et où il n’est pas pratique de convertir au format Unicode. Les conseils s’appliquent aux applications MFC et les applications écrites sans MFC. Les rubriques traitées ici sont les suivantes :  
  
-   [Conseils généraux sur la programmation MBCS](../text/general-mbcs-programming-advice.md)  
  
-   [Incrémentation et décrémentation de pointeurs](../text/incrementing-and-decrementing-pointers.md)  
  
-   [Indices d’octets](../text/byte-indices.md)  
  
-   [Dernier caractère d’une chaîne](../text/last-character-in-a-string.md)  
  
-   [Assignation de caractère](../text/character-assignment.md)  
  
-   [Comparaison de caractères](../text/character-comparison.md)  
  
-   [Dépassement de mémoire tampon](../text/buffer-overflow.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Prise en charge des jeux de caractères multioctets (MBCS)](../text/support-for-multibyte-character-sets-mbcss.md)