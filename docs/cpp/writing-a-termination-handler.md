---
title: L’écriture d’un gestionnaire de terminaisons | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- structured exception handling [C++], termination handlers
- exceptions [C++], terminating
- termination handlers [C++], writing
- handlers [C++]
- handlers [C++], termination
- termination handlers
- exception handling [C++], termination handlers
- try-catch keyword [C++], termination handlers
ms.assetid: 52aa1f8f-f8dd-44b8-be94-5e2fc88d44fb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d37319e50e7d2429ca9b64c5fc81d8c7c4418ed5
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32423234"
---
# <a name="writing-a-termination-handler"></a>Écriture d'un gestionnaire des terminaisons
Contrairement à un gestionnaire d'exceptions, un gestionnaire de terminaisons est toujours exécuté, que le bloc de code protégé soit terminé normalement ou non. L'objectif unique du gestionnaire de terminaisons doit être de garantir que les ressources, telles que la mémoire, les handles et les fichiers, sont fermées correctement indépendamment de la façon dont se termine l'exécution d'une section de code.  
  
 Les gestionnaires de terminaisons utilisent l'instruction try-finally.  
  
## <a name="what-do-you-want-to-know-more-about"></a>Sur quels éléments souhaitez-vous obtenir des informations supplémentaires ?  
  
-   [L’instruction try-finally](../cpp/try-finally-statement.md)  
  
-   [Nettoyage des ressources](../cpp/cleaning-up-resources.md)  
  
-   [Minutage des actions dans la gestion des exceptions](../cpp/timing-of-exception-handling-a-summary.md)  
  
-   [Restrictions sur les gestionnaires de terminaisons](../cpp/restrictions-on-termination-handlers.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion structurée des exceptions (C/C++)](../cpp/structured-exception-handling-c-cpp.md)