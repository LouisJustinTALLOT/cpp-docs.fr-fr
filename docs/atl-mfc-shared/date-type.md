---
title: DATE Type
ms.date: 11/04/2016
f1_keywords:
- DATE
helpviewer_keywords:
- Date data type, implementing
- Date data type
- DATE type
- Date data type, about Date data type
- MFC, date and time
- hour values representation
ms.assetid: 695853ed-b614-4575-b793-b8c287372038
ms.openlocfilehash: 6fd9fde83474ff4f439c0dd3989d4dc35fe1241a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81317918"
---
# <a name="date-type"></a>DATE Type

Le type DATE est implémenté à l’aide d’un numéro de 8 points flottants. Les jours sont représentés par des augmentations de nombre entières commençant par le 30 décembre 1899, minuit comme heure zéro. Les valeurs d'heure sont exprimées sous la forme de la valeur absolue de la partie fractionnaire du nombre. Le tableau suivant illustre plusieurs dates ainsi que leur équivalent numérique de type DATE :

|Date et heure|Représentation|
|-------------------|--------------------|
|30 décembre 1899, minuit|0,00|
|1er janvier 1900, minuit|2,00|
|4 janvier 1900, minuit|5.00|
|4 janvier 1900, 6 h|5.25|
|4 janvier 1900, midi|5.50|
|4 janvier 1900, 21 h|5.875|

Le type de date DATE, ainsi que la classe, représente les `COleDateTime` dates et les heures comme une ligne de numéro classique. La `COleDateTime` classe contient plusieurs méthodes pour manipuler les valeurs DATE, y compris la conversion à et à partir d’autres formats de date commune.

Les points suivants doivent être notés lors de la collaboration avec ces formats de date et d’heure dans Automation :

- Les dates sont spécifiées dans l’heure locale; la synchronisation doit être effectuée manuellement lorsque vous travaillez avec des dates dans différents fuseaux horaires.

- Les types de dates ne tiennent pas compte de l’heure d’été.

- Le délai de date devient discontinu pour les valeurs de date inférieures à 0 (avant le 30 décembre 1899). C’est parce que la partie numéro entier de la valeur de date est traitée comme signée, tandis que la partie fractionnaire est traitée comme non signée. En d’autres termes, la partie numéro entière de la valeur de la date peut être positive ou négative, tandis que la partie fractionnée de la valeur de la date est toujours ajoutée à la date logique globale. Le tableau suivant illustre quelques exemples :

|Date et heure|Représentation|
|-------------------|--------------------|
|27 décembre 1899, minuit|-3.00|
|28 décembre 1899, midi|-2.50|
|28 décembre 1899, minuit|-2.00|
|29 décembre 1899, minuit|-1.00|
|30 décembre 1899, 18 h|-0.75|
|30 décembre 1899, midi|-0.50|
|30 décembre 1899, 6 h|-0.25|
|30 décembre 1899, minuit|0,00|
|30 décembre 1899, 6 h|0,25|
|30 décembre 1899, midi|0.50|
|30 décembre 1899, 18 h|0.75|
|31 décembre 1899, minuit|1.00|
|1er janvier 1900, minuit|2,00|
|1er janvier 1900, midi|2.50|
|2 janvier 1900, minuit|3.00|

> [!CAUTION]
> Notez que parce que 6:00 AM est toujours représenté par une valeur fractionnée 0,25 indépendamment du fait que l’intégrer représentant la journée est positif (après Le 30 décembre, 1899) ou négative (avant le 30 décembre 1899), une simple comparaison des points flottants trierait à tort toute DATE représentant 6 h un jour plus tôt que le 30/1899, soit plus *tard* qu’une DATE représentant 7 h le même jour.

Plus d’informations sur les `COleDateTime` questions liées à la DATE et les types peuvent être trouvés sous [la classe COleDateTime](../atl-mfc-shared/reference/coledatetime-class.md) et [date et heure: Support automatisation](../atl-mfc-shared/date-and-time-automation-support.md).

## <a name="see-also"></a>Voir aussi

[Date et heure](../atl-mfc-shared/date-and-time.md)<br/>
[Classe COleDateTime](../atl-mfc-shared/reference/coledatetime-class.md)
