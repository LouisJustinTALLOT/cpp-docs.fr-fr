---
title: Instructions d'itération (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- iteration statements
- loop structures, iteration statements
ms.assetid: bf6d75f7-ead2-426a-9c47-33847f59b8c7
ms.openlocfilehash: e8f064fd19e69de2819673f48a7f14e26d60b87e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80178253"
---
# <a name="iteration-statements-c"></a>Instructions d'itération (C++)

Les instructions d'itération entraînent une exécution des instructions (ou des instructions composées) zéro ou plusieurs fois, compte tenu de certains critères de terminaison des boucles. Lorsque ces instructions sont des instructions composées, elles sont exécutées dans l’ordre, sauf lorsque l’instruction [break](../cpp/break-statement-cpp.md) ou l’instruction [continue](../cpp/continue-statement-cpp.md) est rencontrée.

C++fournit quatre instructions d’itération, [while](../cpp/while-statement-cpp.md), [do](../cpp/do-while-statement-cpp.md), [for](../cpp/for-statement-cpp.md)et [Range-based for](../cpp/range-based-for-statement-cpp.md). Chacun de ces itérations jusqu’à ce que son expression d’arrêt ait la valeur zéro (false) ou jusqu’à ce que l’arrêt de la boucle soit forcé avec une instruction **break** . Le tableau suivant résume ces instructions et leurs actions ; chacune est décrit en détail dans les sections suivantes.

### <a name="iteration-statements"></a>Instructions d'itération

|.|Évaluée en|Initialisation|Incrément|
|---------------|------------------|--------------------|---------------|
|**while**|Début de boucle|Non|Non|
|**do**|Fin de boucle|Non|Non|
|**for**|Début de boucle|Oui|Oui|
|**basé sur une plage pour**|Début de boucle|Oui|Oui|

La partie instruction d'une instruction d'itération ne peut pas être une déclaration. Toutefois, il peut s'agir d'une instruction composée contenant une déclaration.

## <a name="see-also"></a>Voir aussi

[Vue d’ensemble des instructions C++](../cpp/overview-of-cpp-statements.md)
