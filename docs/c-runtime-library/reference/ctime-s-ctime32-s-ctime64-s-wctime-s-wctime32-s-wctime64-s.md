---
title: ctime_s, _ctime32_s, _ctime64_s, _wctime_s, _wctime32_s, _wctime64_s | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _ctime64_s
- _wctime32_s
- ctime_s
- _wctime64_s
- _ctime32_s
- _wctime_s
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
- ctime64_s
- _ctime32_s
- _tctime32_s
- _ctime64_s
- _wctime_s
- _tctime_s
- _tctime64_s
- ctime_s
- ctime32_s
dev_langs:
- C++
helpviewer_keywords:
- _wctime32_s function
- ctime64_s function
- _tctime64_s function
- _wctime_s function
- tctime_s function
- _wctime64_s function
- ctime_s function
- ctime32_s function
- _ctime64_s function
- tctime64_s function
- wctime64_s function
- wctime_s function
- _tctime_s function
- tctime32_s function
- wctime32_s function
- time, converting
- _ctime32_s function
- _tctime32_s function
ms.assetid: 36ac419a-8000-4389-9fd8-d78b747a009b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a3f9c5e6d9d6f0d910decae904cbbd75d995a6c4
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32404316"
---
# <a name="ctimes-ctime32s-ctime64s-wctimes-wctime32s-wctime64s"></a>ctime_s, _ctime32_s, _ctime64_s, _wctime_s, _wctime32_s, _wctime64_s

Convertissent une valeur de temps en une chaîne et ajustent les paramètres de fuseau horaire local. Il s’agit des versions de [ctime, _ctime64, _wctime, _wctime64](ctime-ctime32-ctime64-wctime-wctime32-wctime64.md) assortie des améliorations de sécurité décrites dans [Fonctionnalités de sécurité dans le CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Syntaxe

```C
errno_t ctime_s(
   char* buffer,
   size_t numberOfElements,
   const time_t *sourceTime
);
errno_t _ctime32_s(
   char* buffer,
   size_t numberOfElements,
   const __time32_t *sourceTime
);
errno_t _ctime64_s(
   char* buffer,
   size_t numberOfElements,
   const __time64_t *sourceTime )
;
errno_t _wctime_s(
   wchar_t* buffer,
   size_t numberOfElements,
   const time_t *sourceTime
);
errno_t _wctime32_s(
   wchar_t* buffer,
   size_t numberOfElements,
   const __time32_t *sourceTime
);
errno_t _wctime64_s(
   wchar_t* buffer,
   size_t numberOfElements,
   const __time64_t *sourceTime
);
```

```cpp
template <size_t size>
errno_t _ctime32_s(
   char (&buffer)[size],
   const __time32_t *sourceTime
); // C++ only
template <size_t size>
errno_t _ctime64_s(
   char (&buffer)[size],
   const __time64_t *sourceTime
); // C++ only
template <size_t size>
errno_t _wctime32_s(
   wchar_t (&buffer)[size],
   const __time32_t *sourceTime
); // C++ only
template <size_t size>
errno_t _wctime64_s(
   wchar_t (&buffer)[size],
   const __time64_t *sourceTime
); // C++ only
```

### <a name="parameters"></a>Paramètres

*buffer*<br/>
Doit être suffisamment grand pour contenir 26 caractères. Un pointeur vers le résultat de chaîne de caractères, ou **NULL** si :

- *sourceTime* représente une date avant le 1er janvier 1970 à minuit UTC.

- Si vous utilisez **_ctime32_s** ou **_wctime32_s** et *sourceTime* représente une date postérieure à 23:59:59 le 18 janvier 2038, UTC.

- Si vous utilisez **_ctime64_s** ou **_wctime64_s** et *sourceTime* représente une date postérieure à 23:59:59, le 31 décembre 3000 UTC.

- Si vous utilisez **_ctime_s** ou **_wctime_s**, ces fonctions sont des wrappers pour les fonctions précédentes. Consultez la section Notes.

*numberOfElements*<br/>
Taille de la mémoire tampon.

*sourceTime*<br/>
Pointeur désignant la valeur de temps stockée.

## <a name="return-value"></a>Valeur de retour

Zéro si l’opération réussit. En cas d’échec en raison d’un paramètre non valide, le gestionnaire de paramètres non valides est appelé, comme décrit dans [Validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, un code d’erreur est retourné. Les codes d’erreur sont définis dans ERRNO.H ; pour obtenir la liste de ces erreurs, consultez [errno](../../c-runtime-library/errno-constants.md). Les codes d’erreur levés pour chaque condition d’erreur sont répertoriés dans le tableau suivant.

## <a name="error-conditions"></a>Conditions d’erreur

|*buffer*|*numberOfElements*|*sourceTime*|Retourner|Valeur de *tampon*|
|--------------|------------------------|------------|------------|-----------------------|
|**NULL**|any|any|**EINVAL**|Non modifiée|
|Pas **NULL** (pointe vers une mémoire valide)|0|any|**EINVAL**|Non modifiée|
|pas **NULL**|0 < taille < 26|any|**EINVAL**|Chaîne vide|
|pas **NULL**|>= 26|NULL|**EINVAL**|Chaîne vide|
|pas **NULL**|>= 26|< 0|**EINVAL**|Chaîne vide|

## <a name="remarks"></a>Notes

Le **ctime_s** fonction convertit une valeur d’heure stockée en tant qu’un [time_t](../../c-runtime-library/standard-types.md) structure dans une chaîne de caractères. Le *sourceTime* valeur est généralement obtenue à partir d’un appel à [temps](time-time32-time64.md), qui retourne le nombre de secondes écoulé depuis minuit (00 : 00:00), le 1er janvier 1970, temps universel coordonné (UTC). La chaîne de valeur de retour contient exactement 26 caractères et présente la forme suivante :

`Wed Jan 02 02:03:55 1980\n\0`

Une horloge de 24 heures est utilisée. Tous les champs ont une largeur constante. Le caractère de saut de ligne (« \n ») et le caractère null (« \0 ») occupent les deux dernières positions de la chaîne.

La chaîne de caractères convertie est également ajustée en fonction des paramètres de fuseau horaire local. Consultez le [temps](time-time32-time64.md), [_ftime](ftime-ftime32-ftime64.md), et [localtime32_s](localtime-s-localtime32-s-localtime64-s.md) fonctions pour plus d’informations sur la configuration de l’heure locale et la [_tzset](tzset.md) fonction pour plus d’informations sur la définition de l’environnement de fuseau horaire et les variables globales.

**_wctime32_s** et **_wctime64_s** sont la version à caractères larges de **_ctime32_s** et **_ctime64_s**; qui retourne un pointeur vers une chaîne à caractères larges. Dans le cas contraire, **_ctime64_s**, **_wctime32_s**, et **_wctime64_s** se comportent de la même manière que **_ctime32_s**.

**ctime_s** est une fonction inline qui prend la valeur **_ctime64_s** et **time_t** équivaut à **__time64_t**. Si vous avez besoin forcer le compilateur à interpréter **time_t** en tant que l’ancien 32 bits **time_t**, vous pouvez définir **_USE_32BIT_TIME_T**. Cette action provoquerait **ctime_s** à évaluer à **_ctime32_s**. Cela n’est pas recommandé, car votre application peut échouer après le 18 janvier 2038 et cela n’est pas autorisé sur les plateformes 64 bits.

En C++, l’utilisation de ces fonctions est simplifiée par les surcharges de modèle ; celles-ci peuvent déduire automatiquement la longueur de la mémoire tampon, ce qui évite d’avoir à spécifier un argument de taille. Pour plus d'informations, consultez [Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md).

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine TCHAR.H|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tctime_s**|**ctime_s**|**ctime_s**|**_wctime_s**|
|**_tctime32_s**|**_ctime32_s**|**_ctime32_s**|**_wctime32_s**|
|**_tctime64_s**|**_ctime64_s**|**_ctime64_s**|**_wctime64_s**|

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**ctime_s**, **_ctime32_s**, **_ctime64_s**|\<time.h>|
|**_wctime_s**, **_wctime32_s**, **_wctime64_s**|\<time.h> ou \<wchar.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliothèques

Toutes les versions des [bibliothèques Runtime C](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Exemple

```C
// crt_wctime_s.c
// This program gets the current
// time in time_t form and then uses _wctime_s to
// display the time in string form.

#include <time.h>
#include <stdio.h>

#define SIZE 26

int main( void )
{
   time_t ltime;
   wchar_t buf[SIZE];
   errno_t err;

   time( &ltime );

   err = _wctime_s( buf, SIZE, &ltime );
   if (err != 0)
   {
      printf("Invalid Arguments for _wctime_s. Error Code: %d\n", err);
   }
   wprintf_s( L"The time is %s\n", buf );
}
```

```Output
The time is Fri Apr 25 13:03:39 2003
```

## <a name="see-also"></a>Voir aussi

[Gestion du temps](../../c-runtime-library/time-management.md)<br/>
[asctime_s, _wasctime_s](asctime-s-wasctime-s.md)<br/>
[ctime, _ctime32, _ctime64, _wctime, _wctime32, _wctime64](ctime-ctime32-ctime64-wctime-wctime32-wctime64.md)<br/>
[_ftime, _ftime32, _ftime64](ftime-ftime32-ftime64.md)<br/>
[gmtime_s, _gmtime32_s, _gmtime64_s](gmtime-s-gmtime32-s-gmtime64-s.md)<br/>
[localtime_s, _localtime32_s, _localtime64_s](localtime-s-localtime32-s-localtime64-s.md)<br/>
[time, _time32, _time64](time-time32-time64.md)<br/>
