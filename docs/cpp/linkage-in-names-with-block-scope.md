---
title: Liaison des noms avec portée de bloc | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- scope [C++], linkage rules
- linkage [C++], scope linkage rules
- names [C++], scope linkage rules
- block scope [C++]
- external linkage, scope linkage rules
ms.assetid: 73efa91a-f761-47f7-bbd9-9f9e3508e218
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ab7758e962c028c4746836e470ee43eaab510f9e
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32418885"
---
# <a name="linkage-in-names-with-block-scope"></a>Liaison des noms avec la portée de bloc
Les règles de liaison suivantes s’appliquent aux noms avec une portée de bloc (noms locaux) :  
  
-   Noms déclarés en tant que `extern` ont une liaison externe, sauf si elles ont été précédemment déclarés comme **statique**.  
  
-   Tous les autres noms avec portée de bloc ne possèdent pas de liaison.  
  
## <a name="see-also"></a>Voir aussi  
 [Programme et liaison](../cpp/program-and-linkage-cpp.md)