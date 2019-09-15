---
title: strcpy, wcscpy, _mbscpy
ms.date: 11/04/2016
api_name:
- strcpy
- wcscpy
- _mbscpy
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
- api-ms-win-crt-multibyte-l1-1-0.dll
- api-ms-win-crt-string-l1-1-0.dll
- ntoskrnl.exe
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _mbscpy
- _ftcscpy
- wcscpy
- _tcscpy
- strcpy
helpviewer_keywords:
- strcpy function
- tcscpy function
- ftcscpy function
- mbscpy function
- wcscpy function
- copying strings
- strings [C++], copying
- _tcscpy function
- _ftcscpy function
- _mbscpy function
ms.assetid: f97a4f81-e9ee-4f15-888a-0fa5d7094c5a
ms.openlocfilehash: b54bdc2f930b805df036a1fa5d5b1595ea738b88
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70958262"
---
# <a name="strcpy-wcscpy-_mbscpy"></a>strcpy, wcscpy, _mbscpy

Copie une chaîne. Il existe des versions plus sécurisées de ces fonctions. Consultez [strcpy_s, wcscpy_s, _mbscpy_s](strcpy-s-wcscpy-s-mbscpy-s.md).

> [!IMPORTANT]
> **_mbscpy** ne peut pas être utilisé dans les applications qui s’exécutent dans le Windows Runtime. Pour plus d’informations, consultez [Fonctions CRT non prises en charge dans les applications de la plateforme Windows universelle](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntaxe

```C
char *strcpy(
   char *strDestination,
   const char *strSource
);
wchar_t *wcscpy(
   wchar_t *strDestination,
   const wchar_t *strSource
);
unsigned char *_mbscpy(
   unsigned char *strDestination,
   const unsigned char *strSource
);
template <size_t size>
char *strcpy(
   char (&strDestination)[size],
   const char *strSource
); // C++ only
template <size_t size>
wchar_t *wcscpy(
   wchar_t (&strDestination)[size],
   const wchar_t *strSource
); // C++ only
template <size_t size>
unsigned char *_mbscpy(
   unsigned char (&strDestination)[size],
   const unsigned char *strSource
); // C++ only
```

### <a name="parameters"></a>Paramètres

*strDestination*<br/>
Chaîne de destination.

*strSource*<br/>
Chaîne source se terminant par null.

## <a name="return-value"></a>Valeur de retour

Chacune de ces fonctions retourne la chaîne de destination. Aucune valeur de retour n'est réservée pour indiquer une erreur.

## <a name="remarks"></a>Notes

La fonction **strcpy** copie *strSource*, y compris le caractère null de fin, à l’emplacement spécifié par *strDestination*. Le comportement de **strcpy** n’est pas défini si les chaînes source et de destination se chevauchent.

> [!IMPORTANT]
> Étant donné que **strcpy** ne vérifie pas l’espace suffisant dans *strDestination* avant de copier *strSource*, il s’agit d’une cause potentielle de dépassements de mémoire tampon. Par conséquent, nous vous recommandons d’utiliser plutôt [strcpy_s](strcpy-s-wcscpy-s-mbscpy-s.md).

**wcscpy** et **_mbscpy** sont, respectivement, des versions à caractères larges et à caractères multioctets de **strcpy**. Les arguments et la valeur de retour de **wcscpy** sont des chaînes à caractères larges ; ceux de **_mbscpy** sont des chaînes de caractères multioctets. Ces trois fonctions se comportent sinon de façon identique.

En C++, ces fonctions ont des surcharges de modèle qui appellent les équivalents plus récents et sécurisés de ces fonctions. Pour plus d'informations, consultez [Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md).

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine TCHAR.H|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcscpy**|**strcpy**|**_mbscpy**|**wcscpy**|

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis|
|-------------|---------------------|
|**strcpy**|\<string.h>|
|**wcscpy**|\<string.h> ou \<wchar.h>|
|**_mbscpy**|\<mbstring.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

```C
// crt_strcpy.c
// compile with: /W3
// This program uses strcpy
// and strcat to build a phrase.

#include <string.h>
#include <stdio.h>

int main( void )
{
   char string[80];

   // If you change the previous line to
   //   char string[20];
   // strcpy and strcat will happily overrun the string
   // buffer.  See the examples for strncpy and strncat
   // for safer string handling.

   strcpy( string, "Hello world from " ); // C4996
   // Note: strcpy is deprecated; use strcpy_s instead
   strcat( string, "strcpy " );           // C4996
   // Note: strcat is deprecated; use strcat_s instead
   strcat( string, "and " );              // C4996
   strcat( string, "strcat!" );           // C4996
   printf( "String = %s\n", string );
}
```

```Output
String = Hello world from strcpy and strcat!
```

## <a name="see-also"></a>Voir aussi

[Manipulation de chaînes](../../c-runtime-library/string-manipulation-crt.md)<br/>
[strcat, wcscat, _mbscat](strcat-wcscat-mbscat.md)<br/>
[strcmp, wcscmp, _mbscmp](strcmp-wcscmp-mbscmp.md)<br/>
[strncat, _strncat_l, wcsncat, _wcsncat_l, _mbsncat, _mbsncat_l](strncat-strncat-l-wcsncat-wcsncat-l-mbsncat-mbsncat-l.md)<br/>
[strncmp, wcsncmp, _mbsncmp, _mbsncmp_l](strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)<br/>
[strncpy, _strncpy_l, wcsncpy, _wcsncpy_l, _mbsncpy, _mbsncpy_l](strncpy-strncpy-l-wcsncpy-wcsncpy-l-mbsncpy-mbsncpy-l.md)<br/>
[_strnicmp, _wcsnicmp, _mbsnicmp, _strnicmp_l, _wcsnicmp_l, _mbsnicmp_l](strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)<br/>
[strrchr, wcsrchr, _mbsrchr, _mbsrchr_l](strrchr-wcsrchr-mbsrchr-mbsrchr-l.md)<br/>
[strspn, wcsspn, _mbsspn, _mbsspn_l](strspn-wcsspn-mbsspn-mbsspn-l.md)<br/>
