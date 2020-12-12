---
description: 'En savoir plus sur : type de DATE'
title: Type de DATE
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
ms.openlocfilehash: 6a0fd8f02abe5fd3ecb3695fd2715bfb3a573028
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97167017"
---
# <a name="date-type"></a>Type de DATE

Le type de DATE est implémenté à l’aide d’un nombre à virgule flottante de 8 octets. Les jours sont représentés par des incréments de nombres entiers à partir du 30 décembre 1899, minuit comme heure zéro. Les valeurs d'heure sont exprimées sous la forme de la valeur absolue de la partie fractionnaire du nombre. Le tableau suivant illustre plusieurs dates avec leur type de DATE équivalent numérique :

|Date et heure|Représentation|
|-------------------|--------------------|
|30 décembre 1899, minuit|0,00|
|1er janvier 1900, minuit|2,00|
|4 janvier 1900, minuit|5.00|
|4 janvier 1900, 18:00|5.25|
|4 janvier 1900, midi|5.50|
|4 janvier 1900, 9 h 00|5.875|

Le type date date, ainsi que la `COleDateTime` classe, représentent les dates et les heures sous la forme d’une ligne de nombres classique. La `COleDateTime` classe contient plusieurs méthodes pour manipuler les valeurs de date, y compris la conversion vers et à partir d’autres formats de date courants.

Les points suivants doivent être notés lors de l’utilisation de ces formats de date et d’heure dans Automation :

- Les dates sont spécifiées en heure locale ; la synchronisation doit être effectuée manuellement lors de l’utilisation de dates dans des fuseaux horaires différents.

- Les types de date ne sont pas en compte pour l’heure d’été.

- La chronologie de la date devient discontinue pour les valeurs de date inférieures à 0 (avant le 30 décembre 1899). Cela est dû au fait que la partie entière de la valeur de date est traitée comme étant signée, tandis que la partie fractionnaire est traitée comme non signée. En d’autres termes, la partie entière de la valeur de date peut être positive ou négative, tandis que la partie fractionnaire de la valeur de date est toujours ajoutée à la date logique globale. Le tableau suivant illustre quelques exemples :

|Date et heure|Représentation|
|-------------------|--------------------|
|27 décembre 1899, minuit|-3.00|
|28 décembre 1899, midi|-2.50|
|28 décembre 1899, minuit|-2.00|
|29 décembre 1899, minuit|-1.00|
|30 décembre 1899, 18:00|-0.75|
|30 décembre 1899, midi|-0.50|
|30 décembre 1899, 18:00|-0.25|
|30 décembre 1899, minuit|0,00|
|30 décembre 1899, 18:00|0,25|
|30 décembre 1899, midi|0.50|
|30 décembre 1899, 18:00|0,75|
|31 décembre 1899, minuit|1.00|
|1er janvier 1900, minuit|2,00|
|1er janvier 1900, midi|2,50|
|2 janvier 1900, minuit|3.00|

> [!CAUTION]
> Notez que, étant donné que 6:00 AM est toujours représenté par une valeur fractionnaire 0,25 que l’entier représentant le jour soit positif (après le 30 décembre 1899) ou négatif (avant le 30 décembre 1899), une comparaison simple à virgule flottante trie par erreur toute DATE représentant 6:00 AM sur un jour antérieur à la DATE du jour qui *correspond à 12/30/1899* .

Vous trouverez plus d’informations sur les problèmes liés à la DATE et les `COleDateTime` types sous la [classe COleDateTime](../atl-mfc-shared/reference/coledatetime-class.md) et la [date et l’heure : prise en charge d’Automation](./date-and-time.md).

## <a name="see-also"></a>Voir aussi

[Date et heure](../atl-mfc-shared/date-and-time.md)<br/>
[COleDateTime (classe)](../atl-mfc-shared/reference/coledatetime-class.md)
