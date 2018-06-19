---
title: _strtime, _wstrtime | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _wstrtime
- _strtime
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
- _wstrtime
- _strtime
- wstrtime
- strtime
- _tstrtime
dev_langs:
- C++
helpviewer_keywords:
- strtime function
- _strtime function
- _wstrtime function
- copying time to buffers
- wstrtime function
- tstrtime function
- _tstrtime function
- time, copying
ms.assetid: 9e538161-cf49-44ec-bca5-c0ab0b9e4ca3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3b0ca776394b47f5209fbf034cbb10461c220634
ms.sourcegitcommit: 6e3cf8df676d59119ce88bf5321d063cf479108c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/22/2018
ms.locfileid: "34450782"
---
# <a name="strtime-wstrtime"></a>_strtime, _wstrtime

Copient l’heure dans une mémoire tampon. Il existe des versions plus sécurisées de ces fonctions. Consultez [_strtime_s, _wstrtime_s](strtime-s-wstrtime-s.md).

## <a name="syntax"></a>Syntaxe

```C
char *_strtime(
   char *timestr
);
wchar_t *_wstrtime(
   wchar_t *timestr
);
template <size_t size>
char *_strtime(
   char (&timestr)[size]
); // C++ only
template <size_t size>
wchar_t *_wstrtime(
   wchar_t (&timestr)[size]
); // C++ only
```

### <a name="parameters"></a>Paramètres

*timestr*<br/>
Chaîne d’heure.

## <a name="return-value"></a>Valeur de retour

Retourne un pointeur vers la chaîne de caractères *timestr*.

## <a name="remarks"></a>Notes

Le **_strtime** fonction copie l’heure locale actuelle dans la mémoire tampon vers laquelle pointée *timestr*. L’heure sous la forme **hh : mm :** où **hh** comprend deux chiffres représentant l’heure dans la notation de 24 heures, **mm** comprend deux chiffres représentant les minutes après l’heure et **ss** comprend deux chiffres représentant les secondes. Par exemple, la chaîne **18:23:44** représente 23 minutes et 44 secondes après 6 heures La mémoire tampon doit avoir une longueur au moins égale à 9 octets.

**_wstrtime** est une version à caractères larges de **_strtime**; la valeur des arguments et de retour de **_wstrtime** sont des chaînes à caractères larges. Ces fonctions se comportent sinon de façon identique. Si *timestr* est un **NULL** pointeur ou si *timestr* est correctement mise en forme, non valide Gestionnaire de paramètres est appelé, comme décrit dans [paramètre Validation](../../c-runtime-library/parameter-validation.md). Si l’exception est autorisée à se poursuivre, ces fonctions retournent un **NULL** et **errno** à **EINVAL** si *timestr* a été un **NULL** ou **errno** à **ERANGE** si *timestr* est incorrect.

En C++, ces fonctions ont des surcharges de modèle qui appellent les équivalents plus récents et sécurisés de ces fonctions. Pour plus d'informations, consultez [Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md).

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine TCHAR.H|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tstrtime**|**_strtime**|**_strtime**|**_wstrtime**|

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**_strtime**|\<time.h>|
|**_wstrtime**|\<time.h> ou \<wchar.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

```C
// crt_strtime.c
// compile with: /W3

#include <time.h>
#include <stdio.h>

int main( void )
{
   char tbuffer [9];
   _strtime( tbuffer ); // C4996
   // Note: _strtime is deprecated; consider using _strtime_s instead
   printf( "The current time is %s \n", tbuffer );
}
```

```Output
The current time is 14:21:44
```

## <a name="see-also"></a>Voir aussi

[Gestion du temps](../../c-runtime-library/time-management.md)<br/>
[asctime, _wasctime](asctime-wasctime.md)<br/>
[ctime, _ctime32, _ctime64, _wctime, _wctime32, _wctime64](ctime-ctime32-ctime64-wctime-wctime32-wctime64.md)<br/>
[gmtime, _gmtime32, _gmtime64](gmtime-gmtime32-gmtime64.md)<br/>
[localtime, _localtime32, _localtime64](localtime-localtime32-localtime64.md)<br/>
[mktime, _mktime32, _mktime64](mktime-mktime32-mktime64.md)<br/>
[time, _time32, _time64](time-time32-time64.md)<br/>
[_tzset](tzset.md)<br/>
