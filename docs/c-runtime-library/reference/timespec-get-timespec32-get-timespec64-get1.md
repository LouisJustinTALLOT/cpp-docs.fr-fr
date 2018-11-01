---
title: timespec_get, _timespec32_get, _timespec64_get1
ms.date: 11/04/2016
apiname:
- timespec_get
- _timespec32_get
- _timespec64_get
apilocation:
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
apitype: DLLExport
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
ms.openlocfilehash: c1d0cbaf194060d816e31d397a9319ef47f75371
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50638449"
---
# <a name="timespecget-timespec32get-timespec64get"></a>timespec_get, _timespec32_get, _timespec64_get

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

La valeur de *base* cas de réussite, sinon il retourne zéro.

## <a name="remarks"></a>Notes

Le **timespec_get** fonctions définissent l’heure actuelle dans le struct vers lequel pointé le *time_spec* argument. Toutes les versions de ce struct ont deux membres, **tv_sec** et **tv_nsec**. Le **tv_sec** a la valeur au nombre entier de secondes et **tv_nsec** au nombre entier de nanosecondes, arrondi à la résolution de l’horloge système, depuis le début de l’époque spécifiée par *base*.

**Section spécifique à Microsoft**

Ces fonctions prennent uniquement en charge **TIME_UTC** en tant que le *base* valeur. Cela définit le *time_spec* valeur au nombre de secondes et nanosecondes depuis le démarrage de l’époque, minuit, le 1er janvier 1970, temps universel coordonné (UTC). Dans un **struct** **_timespec32**, **tv_sec** est un **__time32_t** valeur. Dans un **struct** **_timespec64**, **tv_sec** est un **__time64_t** valeur. Dans un **struct** **timespec**, **tv_sec** est un **time_t** type, qui est de 32 bits ou 64 bits de longueur selon que le préprocesseur macro _USE_32BIT_TIME_T est défini. Le **timespec_get** fonction est une fonction inline qui appelle **_timespec32_get** si _USE_32BIT_TIME_T est définie ; sinon, elle appelle **_timespec64_get**.

**Fin de la section spécifique à Microsoft**

## <a name="requirements"></a>Configuration requise

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
