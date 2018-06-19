---
title: Restrictions sur les gestionnaires d’exceptions | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- restrictions, exception handlers
- exception handling [C++], exception handlers
ms.assetid: 31d63524-0e8c-419f-b87c-061f4c0ea470
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1f739152b502a156dc62dfab279e5ad044cfff99
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32420202"
---
# <a name="restrictions-on-exception-handlers"></a>Restrictions sur les gestionnaires d'exceptions
La limitation principale concernant l'utilisation des gestionnaires d'exceptions dans le code tient au fait que vous ne pouvez pas utiliser une instruction `goto` pour accéder à un bloc d'instruction `__try`. À la place, vous devez entrer dans le bloc d'instruction via le flux de contrôle normal. Vous pouvez effectuer un saut hors d'un bloc d'instruction `__try` et imbriquer des gestionnaires d'exceptions comme vous le souhaitez.  
  
## <a name="see-also"></a>Voir aussi  
 [L’écriture d’un gestionnaire d’exceptions](../cpp/writing-an-exception-handler.md)   
 [Gestion structurée des exceptions (C/C++)](../cpp/structured-exception-handling-c-cpp.md)