---
title: Conversions d’assignation | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- conversions, assignment
- assignment conversions
ms.assetid: 4ee01013-de32-4aae-b12e-0051d0cde927
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 928f80375ecdd33902a0586cf31091d5764ee160
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32381832"
---
# <a name="assignment-conversions"></a>Conversions d'assignation
Dans les opérations d'assignation, le type de la valeur assignée est converti en type de la variable qui reçoit l'assignation. C permet des conversions par assignation entre les types intégraux et les types flottants, même si les informations sont perdues lors de la conversion. La méthode de conversion utilisée dépend des types impliqués dans l'assignation, comme décrit dans [Conversions arithmétiques courantes](../c-language/usual-arithmetic-conversions.md) et dans les sections suivantes :  
  
-   [Conversions depuis les types intégraux signés](../c-language/conversions-from-signed-integral-types.md)  
  
-   [Conversions depuis les types intégraux non signés](../c-language/conversions-from-unsigned-integral-types.md)  
  
-   [Conversions depuis les types à virgule flottante](../c-language/conversions-from-floating-point-types.md)  
  
-   [Conversions vers et depuis les types pointeur](../c-language/conversions-to-and-from-pointer-types.md)  
  
-   [Conversions depuis les autres types](../c-language/conversions-from-other-types.md)  
  
 Les qualificateurs de type n'affectent pas l'admissibilité de la conversion bien qu'il ne soit pas possible d'utiliser une l-value **const** à gauche de l'assignation.  
  
## <a name="see-also"></a>Voir aussi  
 [Conversions de type](../c-language/type-conversions-c.md)