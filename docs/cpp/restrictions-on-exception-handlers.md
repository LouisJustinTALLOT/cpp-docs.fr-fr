---
title: Restrictions sur les gestionnaires d’exceptions | Microsoft Docs
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
ms.openlocfilehash: 8775f752a541d2a250e9c1c5a0c325b684335988
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/02/2018
ms.locfileid: "39464598"
---
# <a name="restrictions-on-exception-handlers"></a>Restrictions sur les gestionnaires d'exceptions
La principale limitation à l’utilisation de gestionnaires d’exceptions dans le code est que vous ne pouvez pas utiliser un **goto** pour sauter dans une **__try** bloc d’instructions. À la place, vous devez entrer dans le bloc d'instruction via le flux de contrôle normal. Vous pouvez sauter hors d’un **__try** instruction bloquer et imbriquer des gestionnaires d’exceptions que vous le souhaitez.  
  
## <a name="see-also"></a>Voir aussi  
 [Écriture d’un gestionnaire d’exceptions](../cpp/writing-an-exception-handler.md)   
 [Gestion structurée des exceptions (C/C++)](../cpp/structured-exception-handling-c-cpp.md)