---
title: double, type | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- mantissas, floating-point variables
- type double
- portability [C++], type double
- double data type
ms.assetid: 17c85b24-1475-4d41-a03c-ddf2d6561d34
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f0eb8fb3952b1825bff730d5d22222b56cdb4ecf
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32387341"
---
# <a name="type-double"></a>double, type
Les valeurs à double précision avec type double possèdent 8 octets. Le format est semblable au format float si ce n'est qu'il a 11 bits d'exposant (excès de 1023) et 52 bits de mantisse, plus le bit 1 d'ordre haut implicite. Ce format fournit une plage d’approximativement 1,7E-308 à 1,7E+308 pour le type double.  
  
 **Section spécifique à Microsoft**  
  
 Le type double contient 64 bits : 1 pour le signe, 11 pour l'exposant et 52 pour la mantisse. Sa plage est +/-1,7E308 avec au moins 15 chiffres de précision.  
  
 **FIN de la section spécifique à Microsoft**  
  
## <a name="see-also"></a>Voir aussi  
 [Stockage de types de base](../c-language/storage-of-basic-types.md)