---
title: Instructions d’itération (C++) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- iteration statements
- loop structures, iteration statements
ms.assetid: bf6d75f7-ead2-426a-9c47-33847f59b8c7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1973223d6aab44d4c5d8652111d3e6b8251676fb
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32418911"
---
# <a name="iteration-statements-c"></a>Instructions d'itération (C++)
Les instructions d'itération entraînent une exécution des instructions (ou des instructions composées) zéro ou plusieurs fois, compte tenu de certains critères de terminaison des boucles. Lorsque ces instructions sont des instructions composées, elles sont exécutées dans l’ordre, sauf quand soit le [saut](../cpp/break-statement-cpp.md) instruction ou le [continuer](../cpp/continue-statement-cpp.md) est rencontrée.  
  
 C++ fournit quatre instructions d’itération : [pendant](../cpp/while-statement-cpp.md), [faire](../cpp/do-while-statement-cpp.md), [pour](../cpp/for-statement-cpp.md), et [en fonction de plage pour](../cpp/range-based-for-statement-cpp.md). Chacune itère jusqu'à ce que son expression d’arrêt a la valeur zéro (false), ou jusqu'à ce que la boucle d’arrêt soit forcée avec une **saut** instruction. Le tableau suivant résume ces instructions et leurs actions ; chacune est décrit en détail dans les sections suivantes.  
  
### <a name="iteration-statements"></a>Instructions d'itération  
  
|Instruction|Évaluée en|Initialisation|Incrémentation|  
|---------------|------------------|--------------------|---------------|  
|`while`|Début de boucle|Non|Non|  
|**do**|Fin de boucle|Non|Non|  
|**for**|Début de boucle|Oui|Oui|  
|**en fonction de plage pour**|Début de boucle|Oui|Oui|  
  
 La partie instruction d'une instruction d'itération ne peut pas être une déclaration. Toutefois, il peut s'agir d'une instruction composée contenant une déclaration.  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble des instructions C++](../cpp/overview-of-cpp-statements.md)