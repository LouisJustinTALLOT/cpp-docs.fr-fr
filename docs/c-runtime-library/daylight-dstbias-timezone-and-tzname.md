---
title: _daylight, _dstbias, _timezone, et _tzname
ms.date: 11/04/2016
f1_keywords:
- tzname
- _timezone
- timezone
- _daylight
- _tzname
- daylight
helpviewer_keywords:
- time zones
- time adjustments
- timezone variables
- _tzname function
- _daylight function
- _timezone function
- daylight function
- local time adjustments
- timezone function
- tzname function
- time-zone variables
ms.assetid: d06c7292-6b99-4aba-b284-16a96570c856
ms.openlocfilehash: d8660c7a6677fb8113b91d6d69a21eef9d1d26c1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50460513"
---
# <a name="daylight-dstbias-timezone-and-tzname"></a>_daylight, _dstbias, _timezone, et _tzname

`_daylight`, `_dstbias`, `_timezone` et `_tzname` sont utilisés dans des routines de date et heure pour régler l’heure locale. Ces variables globales ont été dépréciées dans les versions opérationnelles plus sécurisées, qui doivent être utilisées à la place des variables globales.

|Variable globale|Équivalent opérationnel|
|---------------------|---------------------------|
|`_daylight`|[_get_daylight](../c-runtime-library/reference/get-daylight.md)|
|`_dstbias`|[_get_dstbias](../c-runtime-library/reference/get-dstbias.md)|
|`_timezone`|[_get_timezone](../c-runtime-library/reference/get-timezone.md)|
|`_tzname`|[_get_tzname](../c-runtime-library/reference/get-tzname.md)|

Elles sont déclarées comme suit dans Time.h.

## <a name="syntax"></a>Syntaxe

```
extern int _daylight; 
extern int _dstbias; 
extern long _timezone; 
extern char *_tzname[2];
```

## <a name="remarks"></a>Notes

Dans un appel à `_ftime`, `localtime` ou `_tzset`, les valeurs de `_daylight`, `_dstbias`, `_timezone` et `_tzname` sont déterminées à partir de la valeur de la variable d’environnement `TZ`. Si vous ne définissez pas explicitement la valeur de `TZ`, `_tzname[0]` et `_tzname[1]` contiennent les paramètres par défaut de « PST » et « PDT » respectivement.  Les fonctions de manipulation de temps ([_tzset](../c-runtime-library/reference/tzset.md), [_ftime](../c-runtime-library/reference/ftime-ftime32-ftime64.md) et [localtime](../c-runtime-library/reference/localtime-localtime32-localtime64.md)) essaient de définir les valeurs de `_daylight`, `_dstbias` et `_timezone` en interrogeant le système d’exploitation pour obtenir la valeur par défaut de chaque variable. Les valeurs des variables globales de fuseau horaire sont présentées dans le tableau suivant.

|Variable|Value|
|--------------|-----------|
|`_daylight`|Différent de zéro si l’heure d’été est spécifiée dans `TZ` ou déterminée à partir du système d’exploitation ; sinon, 0. La valeur par défaut est 1.|
|`_dstbias`|Décalage pour l’heure d’été.|
|`_timezone`|Différence en secondes entre le temps universel coordonné et l’heure locale. La valeur par défaut est 28 800.|
|`_tzname[0]`|Nom de fuseau horaire dérivé de la variable d’environnement `TZ`. La valeur par défaut est « PST ».|
|`_tzname[1]`|Nom de zone d’heure d’été dérivé de la variable d’environnement `TZ`. La valeur par défaut est « Pacifique (heure d’été) » (PDT).|

## <a name="see-also"></a>Voir aussi

[Variables globales](../c-runtime-library/global-variables.md)<br/>
[_get_daylight](../c-runtime-library/reference/get-daylight.md)<br/>
[_get_dstbias](../c-runtime-library/reference/get-dstbias.md)<br/>
[_get_timezone](../c-runtime-library/reference/get-timezone.md)<br/>
[_get_tzname](../c-runtime-library/reference/get-tzname.md)