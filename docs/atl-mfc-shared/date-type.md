---
title: Type de DATE | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- DATE
dev_langs:
- C++
helpviewer_keywords:
- Date data type, implementing
- Date data type
- DATE type
- Date data type, about Date data type
- MFC, date and time
- hour values representation
ms.assetid: 695853ed-b614-4575-b793-b8c287372038
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5aafed046fa5724442e30014aa5634542de0f4aa
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32358125"
---
# <a name="date-type"></a>Type de DATE
Le **DATE** type est implémenté à l’aide d’un nombre à virgule flottante de 8 octets. Jours d’utilisation sont représentées par incréments de nombres entiers commençant le 30 décembre 1899, minuit heure zéro. Valeurs d’heure sont exprimées en tant que la valeur absolue de la partie fractionnaire du nombre. Le tableau suivant illustre plusieurs dates avec leurs **DATE** équivalent numérique du type :  
  
|Date et heure|Représentation sous forme de|  
|-------------------|--------------------|  
|30 décembre 1899, minuit|0.00|  
|1er janvier 1900, minuit|2.00|  
|4 janvier 1900, minuit|5.00|  
|4 janvier 1900, 6 h 00|5.25|  
|4 janvier 1900, MIDI|5.50|  
|4 janvier 1900, 21.|5.875|  
  
 Le **DATE** date type, ainsi que le `COleDateTime` classe représente dates et heures sous forme de nombre classique. La `COleDateTime` classe contient plusieurs méthodes pour manipuler les valeurs de DATE, notamment la conversion vers et depuis d’autres formats de date courants.  
  
 Notez les points suivants lorsque vous travaillez avec ces formats de date et d’heure dans Automation :  
  
-   Les dates sont spécifiées dans l’heure locale. synchronisation doit être effectuée manuellement lorsque vous travaillez avec des dates dans des fuseaux horaires différents.  
  
-   Les types de date ne correspondent pas à l’heure d’été.  
  
-   La chronologie date devient discontinue pour les valeurs de date inférieure à 0 (avant le 30 décembre 1899). C’est parce que la partie nombre entier de la valeur de date est considérée comme signée, alors que la partie fractionnaire est traitée comme étant non signé. En d’autres termes, la partie de nombre entier de la valeur de date peut être positif ou négatif, tandis que la partie fractionnaire de la valeur de date est toujours ajoutée à la date logique globale. Le tableau suivant décrit quelques exemples :  
  
|Date et heure|Représentation sous forme de|  
|-------------------|--------------------|  
|27 décembre 1899, minuit|-3.00|  
|28 décembre 1899, MIDI|-2.50|  
|28 décembre 1899, minuit|-2.00|  
|29 décembre 1899, minuit|-1.00|  
|30 décembre 1899, 18.|-0.75|  
|30 décembre 1899, MIDI|-0.50|  
|30 décembre 1899, 6 h 00|-0.25|  
|30 décembre 1899, minuit|0.00|  
|30 décembre 1899, 6 h 00|0.25|  
|30 décembre 1899, MIDI|0.50|  
|30 décembre 1899, 18.|0.75|  
|Le 31 décembre 1899, minuit|1.00|  
|1er janvier 1900, minuit|2.00|  
|1er janvier 1900, MIDI|2.50|  
|2 janvier 1900, minuit|3.00|  
  
> [!CAUTION]
>  Notez que puisque 6:00 AM est toujours représentée par une valeur fractionnaire 0,25, quelle que soit l’entier représentant le jour est positif (après le 30 décembre 1899) ou négatif (avant le 30 décembre 1899), une comparaison point flottant simple tort triez n’importe quel **DATE** représentant 6 h 00 un jour antérieures à 30/12/1899 en tant que *ultérieurement* à un **DATE** représentant 7:00 AM sur ce même jour.  
  
 Plus d’informations sur les problèmes liés à la **DATE** et `COleDateTime` types peuvent être trouvées sous [COleDateTime (classe)](../atl-mfc-shared/reference/coledatetime-class.md) et [Date et heure : prise en charge Automation](../atl-mfc-shared/date-and-time-automation-support.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Date et heure](../atl-mfc-shared/date-and-time.md)   
 [COleDateTime, classe](../atl-mfc-shared/reference/coledatetime-class.md)

