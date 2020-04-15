---
title: timespec_get, _timespec32_get, _timespec64_get1
ms.date: 4/2/2020
api_name:
- timespec_get
- _timespec32_get
- _timespec64_get
- _o__timespec32_get
- _o__timespec64_get
api_location:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-time-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- timespec_get
- _timespec32_get
- _timespec64_get
- time/timespec_get
- time/_timespec32_get
- time/_timespec64_get
- timespec
- _timespec32
- _timespec64
helpviewer_keywords:
- timespec_get function
- _timespec32_get function
- _timespec64_get function
ms.assetid: ed757258-b4f2-4c1d-a91b-22ea6ffce4ab
ms.openlocfilehash: fc6d91b076f2dd2e25c55d9cf7062e81c3fab11a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81362490"
---
# <a name="timespec_get-_timespec32_get-_timespec64_get"></a>timespec_get, _timespec32_get, _timespec64_get

Affecte à l’intervalle indiqué par le premier argument l’heure de calendrier actuelle, en fonction de la base de temps spécifiée.

## <a name="syntax"></a>Syntaxe

```C
int timespec_get(
    struct timespec* const time_spec,
    int const base
);
int _timespec32_get(
    struct _timespec32* const time_spec,
    int const base
);
int _timespec64_get(
    struct _timespec64* const time_spec,
    int const base
);
```

### <a name="parameters"></a>Paramètres

*time_spec*<br/>
Pointeur vers un struct qui a pour valeur la durée, en secondes et nanosecondes, depuis le début de l’époque.

*base*<br/>
Valeur propre à l’implémentation différente de zéro qui spécifie la base de temps.

## <a name="return-value"></a>Valeur de retour

La valeur de *base* en cas de succès, sinon elle renvoie zéro.

## <a name="remarks"></a>Notes

Les fonctions **timespec_get** fixent l’heure actuelle de la struction soulignée par *l’argument time_spec.* Toutes les versions de cette struct ont deux membres, **tv_sec** et **tv_nsec**. La valeur **tv_sec** est réglée à l’ensemble des secondes et **tv_nsec** au nombre intégral de nanosecondes, arrondi à la résolution de l’horloge du système, depuis le début de l’époque spécifiée par *la base*.

**Microsoft Spécifique**

Ces fonctions ne prennent **en charge** que TIME_UTC comme valeur *de base.* Cela définit la valeur *time_spec* au nombre de secondes et de nanosecondes depuis le début de l’époque, Minuit, 1er janvier 1970, Coordinated Universal Time (UTC). Dans une **_timespec32 struct** **_timespec32**, **tv_sec** est une valeur **__time32_t.** Dans une **_timespec64 struct** **_timespec64**, **tv_sec** est une valeur **__time64_t.** Dans un **timespec struct** **,** **tv_sec** est un type **time_t,** qui est de 32 bits ou 64 bits de longueur selon que le préprocesseur macro _USE_32BIT_TIME_T est défini. La fonction **timespec_get** est une fonction inline qui appelle **_timespec32_get** si _USE_32BIT_TIME_T est définie; sinon il appelle **_timespec64_get**.

**FIN de la section spécifique à Microsoft**

Par défaut, l’état global de cette fonction est étendue à l’application. Pour changer cela, voir [Global State dans le CRT](../global-state.md).

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**timespec_get**, **_timespec32_get**, **_timespec64_get**|C : \<time.h>, C++ : \<ctime> ou \<time.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[Gestion du temps](../../c-runtime-library/time-management.md)<br/>
[asctime, _wasctime](asctime-wasctime.md)<br/>
[asctime_s, _wasctime_s](asctime-s-wasctime-s.md)<br/>
[_ftime, _ftime32, _ftime64](ftime-ftime32-ftime64.md)<br/>
[gmtime, _gmtime32, _gmtime64](gmtime-gmtime32-gmtime64.md)<br/>
[gmtime_s, _gmtime32_s, _gmtime64_s](gmtime-s-gmtime32-s-gmtime64-s.md)<br/>
[localtime, _localtime32, _localtime64](localtime-localtime32-localtime64.md)<br/>
[localtime_s, _localtime32_s, _localtime64_s](localtime-s-localtime32-s-localtime64-s.md)<br/>
[time, _time32, _time64](time-time32-time64.md)<br/>
[_utime, _utime32, _utime64, _wutime, _wutime32, _wutime64](utime-utime32-utime64-wutime-wutime32-wutime64.md)<br/>
