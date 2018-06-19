---
title: Gestion du temps | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- c.memory
dev_langs:
- C++
helpviewer_keywords:
- dates, run-time library members
- time, time management
- date functions
- time functions
ms.assetid: 93599220-c011-45d5-978f-12182abfdd2f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8c33d22f30275c9d6581d6c1cd97de4ffe68bc08
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32418339"
---
# <a name="time-management"></a>Gestion du temps

Utilisez ces fonctions pour obtenir l’heure actuelle, et la convertir, la régler et la stocker selon vos besoins. L’heure actuelle est l’heure système.

 Les routines **_ftime** et **localtime** utilisent la variable d’environnement **TZ**. Si **TZ** n’est pas défini, la bibliothèque runtime tente d’utiliser les informations de fuseau horaire spécifiées par le système d’exploitation. Si ces informations ne sont pas disponibles, ces fonctions utilisent la valeur par défaut PST8PDT. Pour plus d’informations sur **TZ**, consultez [_tzset](../c-runtime-library/reference/tzset.md) et [_daylight, timezone et _tzname](../c-runtime-library/daylight-dstbias-timezone-and-tzname.md).

### <a name="time-routines"></a>Routines de temps

|Fonction|Utilisez|
|--------------|---------|
|[asctime, _wasctime](../c-runtime-library/reference/asctime-wasctime.md), [asctime_s, _wasctime_s](../c-runtime-library/reference/asctime-s-wasctime-s.md)|Convertit une heure du type **struct tm** en chaîne de caractères. Les versions de ces fonctions qui ont le suffixe **_s** sont plus sécurisées.|
|[horloge](../c-runtime-library/reference/clock.md)|Renvoie le temps horloge écoulé pour le processus.|
|[ctime, _ctime32, _ctime64, _wctime, _wctime32, _wctime64](../c-runtime-library/reference/ctime-ctime32-ctime64-wctime-wctime32-wctime64.md), [_ctime_s, _ctime32_s, _ctime64_s, _wctime_s, _wctime32_s, _wctime64_s](../c-runtime-library/reference/ctime-s-ctime32-s-ctime64-s-wctime-s-wctime32-s-wctime64-s.md)|Convertit une heure de type **time_t**, **__time32_t** ou **__time64_t** en chaîne de caractères. Les versions de ces fonctions qui ont le suffixe **_s** sont plus sécurisées.|
|[difftime, _difftime32, _difftime64](../c-runtime-library/reference/difftime-difftime32-difftime64.md)|Calcule la différence entre deux heures.|[System::DateTime::Subtract](https://msdn.microsoft.com/en-us/library/system.datetime.subtract.aspx)|
|[_ftime, _ftime32, _ftime64](../c-runtime-library/reference/ftime-ftime32-ftime64.md),[_ftime_s, _ftime32_s, _ftime64_s](../c-runtime-library/reference/ftime-s-ftime32-s-ftime64-s.md)|Stocke l’heure système actuelle dans une variable de type **struct _timeb** ou **struct __timeb64**. Les versions de ces fonctions qui ont le suffixe **_s** sont plus sécurisées.|
|[_futime, _futime32, _futime64](../c-runtime-library/reference/futime-futime32-futime64.md)|Définit l’heure de modification du fichier ouvert.|
|[gmtime, _gmtime32, _gmtime64](../c-runtime-library/reference/gmtime-gmtime32-gmtime64.md), [gmtime_s, _gmtime32_s, _gmtime64_s](../c-runtime-library/reference/gmtime-s-gmtime32-s-gmtime64-s.md)|Convertit une heure de type **time_t** en **struct tm**, ou de type **__time64_t** en **struct tm**. Les versions de ces fonctions qui ont le suffixe **_s** sont plus sécurisées.|
|[localtime, _localtime32, _localtime64](../c-runtime-library/reference/localtime-localtime32-localtime64.md), [localtime_s, _localtime32_s, _localtime64_s](../c-runtime-library/reference/localtime-s-localtime32-s-localtime64-s.md)|Convertit une heure de type **time_t** en **struct tm**, ou de type **__time64_t** en **struct tm** avec correction des paramètres régionaux. Les versions de ces fonctions qui ont le suffixe **_s** sont plus sécurisées.|
|[_mkgmtime, _mkgmtime32, _mkgmtime64](../c-runtime-library/reference/mkgmtime-mkgmtime32-mkgmtime64.md)|Convertit une heure en valeur de calendrier au format GMT (heure de Greenwich).|
|[mktime, _mktime32, _mktime64](../c-runtime-library/reference/mktime-mktime32-mktime64.md)|Convertit une heure en valeur de calendrier.|
|[_strdate, _wstrdate](../c-runtime-library/reference/strdate-wstrdate.md), [_strdate_s, _wstrdate_s](../c-runtime-library/reference/strdate-s-wstrdate-s.md)|Renvoie la date système actuelle sous forme de chaîne. Les versions de ces fonctions qui ont le suffixe **_s** sont plus sécurisées.|
|[strftime, wcsftime, _strftime_l, _wcsftime_l](../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md)|Met en forme la chaîne date/heure pour une utilisation internationale.|
|[_strtime, _wstrtime](../c-runtime-library/reference/strtime-wstrtime.md), [_strtime_s, _wstrtime_s](../c-runtime-library/reference/strtime-s-wstrtime-s.md)|Renvoie l’heure système actuelle sous forme de chaîne. Les versions de ces fonctions qui ont le suffixe **_s** sont plus sécurisées.|
|[time, _time32, _time64](../c-runtime-library/reference/time-time32-time64.md)|Obtient l’heure système actuelle en tant que type **time_t**, **__time32_t** ou **__time64_t**.|
|[_tzset](../c-runtime-library/reference/tzset.md)|Définit les variables d’heure externes à partir de la variable d’environnement d’heure **TZ**.|
|[_utime, _utime32, _utime64, _wutime, _wutime32, _wutime64](../c-runtime-library/reference/utime-utime32-utime64-wutime-wutime32-wutime64.md)|Définit l’heure de modification du fichier spécifié en fonction de l’heure actuelle ou de la valeur d’heure stockée dans la structure.|

> [!NOTE]
> Dans toutes les versions de Microsoft C/C++ à l’exception de Microsoft C/C++ version 7.0, et dans toutes les versions de Visual C++, l’heure actuelle renvoyée par la fonction time correspond au nombre de secondes écoulées depuis le 1er janvier 1970 à minuit. Dans Microsoft C/C++ version 7.0, l’heure actuelle retournée par **time** est le nombre de secondes écoulées depuis le 31 décembre 1899 à minuit.

> [!NOTE]
> Dans les versions de Visual C++ et de Microsoft C/C++ antérieures à Visual C++ 2005, **time_t** était une valeur **long** **int** (32 bits) et ne pouvait donc pas être utilisé pour les dates postérieures au 19 janvier 2038 à 3:14:07 (heure UTC). **time_t** est maintenant équivalent à **__time64_t** par défaut. Toutefois, le fait de définir **_USE_32BIT_TIME_T** remplace **time_t** par **__time32_t** et force de nombreuses fonctions time à appeler les versions qui acceptent la valeur **time_t** 32 bits. Pour plus d’informations, consultez [Types standard](../c-runtime-library/standard-types.md) et les commentaires dans la documentation pour les fonctions de temps individuelles.

## <a name="see-also"></a>Voir aussi

[Routines du runtime C universel par catégorie](../c-runtime-library/run-time-routines-by-category.md)<br/>
