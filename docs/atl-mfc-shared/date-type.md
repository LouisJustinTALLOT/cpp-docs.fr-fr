---
title: Type de DATE | Microsoft Docs
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
ms.openlocfilehash: 314b943b171d43f8b1723321ac3a942ed33fd100
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/06/2018
ms.locfileid: "37883464"
---
# <a name="date-type"></a>Type de DATE
Le type DATE est implémenté à l’aide d’un nombre à virgule flottante de 8 octets. Jours sont représentés par incréments de nombres entiers en commençant par le 30 décembre 1899 à minuit heure zéro. Valeurs d’heure sont exprimées en tant que la valeur absolue de la partie fractionnaire du nombre. Le tableau suivant illustre plusieurs dates, ainsi que leurs équivalents numériques de type DATE :  
  
|Date et heure|Représentation sous forme de|  
|-------------------|--------------------|  
|30 décembre 1899, minuit|0.00|  
|1er janvier 1900, minuit|2.00|  
|4 janvier 1900, minuit|5.00|  
|4 janvier 1900, 6 h 00|5.25|  
|4 janvier 1900, MIDI|5.50|  
|4 janvier 1900, 21.|5.875|  
  
 Le type date, ainsi que la `COleDateTime` classe représente dates et heures sous forme de ligne nombre classique. Le `COleDateTime` classe contient plusieurs méthodes pour manipuler les valeurs de DATE, notamment la conversion vers et à partir d’autres formats de date courants.  
  
 Notez les points suivants lorsque vous travaillez avec ces formats de date et d’heure dans Automation :  
  
-   Les dates sont spécifiées en heure locale ; synchronisation doit être effectuée manuellement lorsque vous travaillez avec des dates dans des fuseaux horaires différents.  
  
-   Les types de date ne tiennent pas compte à l’heure.  
  
-   La chronologie de date devient discontinue pour les valeurs de date inférieure à 0 (avant le 30 décembre 1899). Il s’agit, car la partie nombre entier de la valeur de date est considérée comme signée, alors que la partie fractionnaire est considérée comme non signée. En d’autres termes, la partie entière de la valeur de date peut être positif ou négatif, tandis que la partie fractionnaire de la valeur de date est toujours ajoutée à la date logique globale. Le tableau suivant illustre quelques exemples :  
  
|Date et heure|Représentation sous forme de|  
|-------------------|--------------------|  
|27 décembre 1899, minuit|-3.00|  
|28 décembre 1899, MIDI|-2.50|  
|28 décembre 1899, minuit|-2.00|  
|29 décembre 1899, minuit|-1.00|  
|30 décembre 1899, 18 : 00|-0.75|  
|30 décembre 1899, MIDI|-0.50|  
|30 décembre 1899, 6 h 00|-0.25|  
|30 décembre 1899, minuit|0.00|  
|30 décembre 1899, 6 h 00|0.25|  
|30 décembre 1899, MIDI|0.50|  
|30 décembre 1899, 18 : 00|0.75|  
|Le 31 décembre 1899, minuit|1.00|  
|1er janvier 1900, minuit|2.00|  
|1er janvier 1900, MIDI|2.50|  
|2 janvier 1900, minuit|3.00|  
  
> [!CAUTION]
>  Étant donné que 6:00 AM est toujours représentée par une valeur fractionnaire 0,25, quel que soit l’entier représentant le jour est positif (après le 30 décembre 1899) ou négatif (avant le 30 décembre 1899), une comparaison point flottant simple à tort triez n’importe quelle DATE représentant 6 h 00 un jour antérieures à 30/12/1899 comme *ultérieurement* à une DATE représentant les 7 h 00 sur ce même jour.  
  
 Plus d’informations sur les problèmes liés à la DATE et `COleDateTime` types peuvent être trouvées sous [COleDateTime, classe](../atl-mfc-shared/reference/coledatetime-class.md) et [Date et heure : prise en charge Automation](../atl-mfc-shared/date-and-time-automation-support.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Date et heure](../atl-mfc-shared/date-and-time.md)   
 [COleDateTime, classe](../atl-mfc-shared/reference/coledatetime-class.md)

