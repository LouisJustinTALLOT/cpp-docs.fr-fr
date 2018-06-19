---
title: strcat, wcscat, _mbscat | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _mbscat
- wcscat
- strcat
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
- api-ms-win-crt-multibyte-l1-1-0.dll
- api-ms-win-crt-string-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _mbscat
- _ftcscat
- _tcscat
- strcat
- wcscat
dev_langs:
- C++
helpviewer_keywords:
- concatenating strings
- mbscat function
- _ftcscat function
- _tcscat function
- ftcscat function
- strcat function
- strings [C++], appending
- _mbscat function
- tcscat function
- strings [C++], concatenating
- appending strings
- wcscat function
ms.assetid: c89c4ef1-817a-44ff-a229-fe22d06ba78a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f2daf6621cb2e72c38212227da20f6b847bb08e9
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32413412"
---
# <a name="strcat-wcscat-mbscat"></a>strcat, wcscat, _mbscat

Ajoute une chaîne. Il existe des versions plus sécurisées de ces fonctions. Consultez [strcpy_s, wcscpy_s, _mbscpy_s](strcat-s-wcscat-s-mbscat-s.md).

> [!IMPORTANT]
> **_mbscat_s** ne peut pas être utilisée dans les applications qui s’exécutent dans le Windows Runtime. Pour plus d’informations, consultez [Fonctions CRT non prises en charge dans les applications de la plateforme Windows universelle](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntaxe

```C
char *strcat(
   char *strDestination,
   const char *strSource
);
wchar_t *wcscat(
   wchar_t *strDestination,
   const wchar_t *strSource
);
unsigned char *_mbscat(
   unsigned char *strDestination,
   const unsigned char *strSource
);
template <size_t size>
char *strcat(
   char (&strDestination)[size],
   const char *strSource
); // C++ only
template <size_t size>
wchar_t *wcscat(
   wchar_t (&strDestination)[size],
   const wchar_t *strSource
); // C++ only
template <size_t size>
unsigned char *_mbscat(
   unsigned char (&strDestination)[size],
   const unsigned char *strSource
); // C++ only
```

### <a name="parameters"></a>Paramètres

*strDestination*<br/>
Chaîne de destination se terminant par un caractère Null.

*strSource*<br/>
Chaîne source se terminant par null.

## <a name="return-value"></a>Valeur de retour

Chacune de ces fonctions retourne la chaîne de destination (*strDestination*). Aucune valeur de retour n'est réservée pour indiquer une erreur.

## <a name="remarks"></a>Notes

Le **strcat** fonction ajoute *strSource* à *strDestination* et met fin à la chaîne obtenue par un caractère null. Le caractère initial de *strSource* remplace le caractère null de fin de *strDestination*. Le comportement de **strcat** n’est pas défini si les chaînes source et de destination se chevauchent.

> [!IMPORTANT]
> Étant donné que **strcat** ne vérifie pas suffisamment d’espace *strDestination* avant d’ajouter *strSource*, il s’agit d’une cause potentielle de dépassements de mémoire tampon. Envisagez d’utiliser plutôt [strncat](strncat-strncat-l-wcsncat-wcsncat-l-mbsncat-mbsncat-l.md).

**wcscat** et **_mbscat** sont des versions à caractères larges et caractères multioctets de **strcat**. Les arguments et la valeur de retour de **wcscat** sont des caractères larges chaînes ; ceux de **_mbscat** sont des chaînes de caractères multioctets. Ces trois fonctions se comportent sinon de façon identique.

En C++, ces fonctions ont des surcharges de modèle qui appellent les équivalents plus récents et sécurisés de ces fonctions. Pour plus d'informations, consultez [Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md).

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine TCHAR.H|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcscat**|**strcat**|**_mbscat**|**wcscat**|

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**strcat**|\<string.h>|
|**wcscat**|\<string.h> ou \<wchar.h>|
|**_mbscat**|\<mbstring.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

Consultez l’exemple relatif à [strcpy](strcpy-wcscpy-mbscpy.md).

## <a name="see-also"></a>Voir aussi

[Manipulation de chaînes](../../c-runtime-library/string-manipulation-crt.md)<br/>
[strncat, _strncat_l, wcsncat, _wcsncat_l, _mbsncat, _mbsncat_l](strncat-strncat-l-wcsncat-wcsncat-l-mbsncat-mbsncat-l.md)<br/>
[strncmp, wcsncmp, _mbsncmp, _mbsncmp_l](strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)<br/>
[strncpy, _strncpy_l, wcsncpy, _wcsncpy_l, _mbsncpy, _mbsncpy_l](strncpy-strncpy-l-wcsncpy-wcsncpy-l-mbsncpy-mbsncpy-l.md)<br/>
[_strnicmp, _wcsnicmp, _mbsnicmp, _strnicmp_l, _wcsnicmp_l, _mbsnicmp_l](strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)<br/>
[strrchr, wcsrchr, _mbsrchr, _mbsrchr_l](strrchr-wcsrchr-mbsrchr-mbsrchr-l.md)<br/>
[strspn, wcsspn, _mbsspn, _mbsspn_l](strspn-wcsspn-mbsspn-mbsspn-l.md)<br/>
