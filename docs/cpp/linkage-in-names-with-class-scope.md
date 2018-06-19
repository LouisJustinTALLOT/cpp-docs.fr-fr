---
title: Liaison des noms avec portée de classe | Documents Microsoft
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
- classes [C++], scope
- external linkage, scope linkage rules
- class names [C++], linkage
- classes [C++], names
- scope [C++], class names
- class scope [C++], linkage in names with
ms.assetid: 45275ff3-6e94-4967-82c8-ba540ef4da28
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9eb58f87e998fbe1eeeb9b26eb0da75046a9079d
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32418970"
---
# <a name="linkage-in-names-with-class-scope"></a>Liaison des noms avec la portée de classe
Les règles de liaison suivantes s'appliquent aux noms avec la portée de classe :  
  
-   Les membres de classe statique ont une liaison externe.  
  
-   Les fonctions membres de classe ont une liaison externe.  
  
-   Les noms d'énumérateur et les noms `typedef` n'ont aucune liaison.  
  
 **Section spécifique à Microsoft**  
  
-   Les fonctions déclarées comme fonctions `friend` doivent avoir une liaison externe. La déclaration d'une fonction statique comme `friend` génère une erreur.  
  
 **FIN de la section spécifique à Microsoft**  
  
## <a name="see-also"></a>Voir aussi  
 [Programme et liaison](../cpp/program-and-linkage-cpp.md)