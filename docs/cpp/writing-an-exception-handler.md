---
title: L’écriture d’un gestionnaire d’exceptions | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- structured exception handling [C++], exception handlers
- exception handling [C++], exception handlers
ms.assetid: 71473fee-f773-4a34-bf12-82a3af79579c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 01d16d95cc246ad7ef0fe9f03c20e2652fe81aad
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32421820"
---
# <a name="writing-an-exception-handler"></a>Écriture d'un gestionnaire d'exceptions
Les gestionnaires d'exceptions sont généralement utilisés pour répondre à des erreurs spécifiques. Vous pouvez utiliser la syntaxe de gestion des exceptions pour filtrer les exceptions autres que celles que vous savez gérer. D'autres exceptions doivent être passées à d'autres gestionnaires (éventuellement dans la bibliothèque Runtime ou dans le système d'exploitation) écrits pour rechercher ces exceptions spécifiques.  
  
 Les gestionnaires d'exceptions utilisent l'instruction try-except.  
  
## <a name="what-do-you-want-to-know-more-about"></a>Sur quels éléments souhaitez-vous obtenir des informations supplémentaires ?  
  
-   [Try-except, instruction](../cpp/try-except-statement.md)  
  
-   [Écriture d’un filtre d’exception](../cpp/writing-an-exception-filter.md)  
  
-   [Le déclenchement d’exceptions logicielles](../cpp/raising-software-exceptions.md)  
  
-   [Exceptions matérielles](../cpp/hardware-exceptions.md)  
  
-   [Restrictions sur les gestionnaires d’exceptions](../cpp/restrictions-on-exception-handlers.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion structurée des exceptions (C/C++)](../cpp/structured-exception-handling-c-cpp.md)