---
title: Prise en charge à virgule flottante pour le Code plus ancien (Visual C++) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: a2a26b96-7bc2-418a-981a-51aa1a0294a2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: cd7cbf955fbf795d06d9cd2448d0736dc435f3b5
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32367158"
---
# <a name="floating-point-support-for-older-code-visual-c"></a>Prise en charge de la virgule flottante pour le code plus ancien (Visual C++)
Les registres MMX et pile à virgule flottante (MM0-MM7/ST0-ST7) sont conservés entre les commutateurs de contexte.  Il n’existe aucune convention d’appel explicite pour ces registres.  L’utilisation de ces registres est strictement interdite dans le code en mode noyau.  
  
## <a name="see-also"></a>Voir aussi  
 [Convention d’appel](../build/calling-convention.md)