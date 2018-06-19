---
title: _strrev, _wcsrev, _mbsrev, _mbsrev_l | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _wcsrev
- _mbsrev
- _strrev
- _mbsrev_l
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
- _strrev
- _ftcsrev
- _tcsrev
- mbsrev
- mbsrev_l
- _wcsrev_fstrrev
- _mbsrev
dev_langs:
- C++
helpviewer_keywords:
- _mbsrev_l function
- characters [C++], switching
- _mbsrev function
- strrev function
- _ftcsrev function
- strings [C++], reversing
- wcsrev function
- _strrev function
- mbsrev_l function
- reversing characters in strings
- ftcsrev function
- characters [C++], reversing order
- _wcsrev function
- mbsrev function
- tcsrev function
- _tcsrev function
ms.assetid: 87863e89-4fa0-421c-af48-25d8516fe72f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 52b99b08fc7761f5fb2d15761bf7726ac0faf64d
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32415424"
---
# <a name="strrev-wcsrev-mbsrev-mbsrevl"></a>_strrev, _wcsrev, _mbsrev, _mbsrev_l

Inverse les caractères d’une chaîne.

> [!IMPORTANT]
> **_mbsrev** et **_mbsrev_l** ne peut pas être utilisée dans les applications qui s’exécutent dans le Windows Runtime. Pour plus d’informations, consultez [Fonctions CRT non prises en charge dans les applications de la plateforme Windows universelle](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntaxe

```C
char *_strrev(
   char *str
);
wchar_t *_wcsrev(
   wchar_t *str
);
unsigned char *_mbsrev(
   unsigned char *str
);
unsigned char *_mbsrev_l(
   unsigned char *str,
   _locale_t locale
);
```

### <a name="parameters"></a>Paramètres

*str*<br/>
Chaîne se terminant par un caractère Null à inverser.

*locale*<br/>
Paramètres régionaux à utiliser.

## <a name="return-value"></a>Valeur de retour

Retourne un pointeur vers la chaîne modifiée. Aucune valeur de retour n'est réservée pour indiquer une erreur.

## <a name="remarks"></a>Notes

Le **_strrev** fonction inverse l’ordre des caractères dans *str*. Le caractère Null de fin reste en place. **_wcsrev** et **_mbsrev** sont des versions à caractères larges et caractères multioctets de **_strrev**. Les arguments et la valeur de retour de **_wcsrev** sont des caractères larges chaînes ; ceux de **_mbsrev** sont des chaînes de caractères multioctets. Pour **_mbsrev**, l’ordre des octets dans chaque caractère multioctet dans *str* n’est pas modifiée. Ces trois fonctions se comportent sinon de façon identique.

**_mbsrev** valide ses paramètres. Si le paramètre *string1* ou *chaîne2* est un pointeur null, le Gestionnaire de paramètre non valide est appelé, comme décrit dans [Validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, **_mbsrev** retourne **NULL** et définit **errno** à **EINVAL**. **_strrev** et **_wcsrev** ne vérifient pas leurs paramètres.

La valeur de sortie est affectée par la définition de la **LC_CTYPE** catégorie des paramètres régionaux ; consultez [setlocale, _wsetlocale](setlocale-wsetlocale.md) pour plus d’informations. Les versions de ces fonctions sont identiques, sauf que ceux qui n’ont le **_l** suffixe utilisent les paramètres régionaux actuels et celles qui ont le **_l** suffixe utilisent à la place les paramètres régionaux de passée. Pour plus d’informations, consultez [Locale](../../c-runtime-library/locale.md).

> [!IMPORTANT]
> Ces fonctions peuvent être vulnérables aux menaces de dépassement de mémoire tampon. Les dépassements de mémoire tampon peuvent être utilisés pour les attaques du système, car ils peuvent provoquer une élévation des privilèges injustifiée. Pour plus d’informations, consultez [Solutions contre les dépassements de mémoire tampon](http://msdn.microsoft.com/library/windows/desktop/ms717795).

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine TCHAR.H|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcsrev**|**_strrev**|**_mbsrev**|**_wcsrev**|
|**n/a**|**n/a**|**_mbsrev_l**|**n/a**|

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**_strrev**|\<string.h>|
|**_wcsrev**|\<string.h> ou \<wchar.h>|
|**_mbsrev**, **_mbsrev_l**|\<mbstring.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

```C
// crt_strrev.c
// This program checks a string to see
// whether it is a palindrome: that is, whether
// it reads the same forward and backward.
//

#include <string.h>
#include <stdio.h>

int main( void )
{
   char* string = "Able was I ere I saw Elba";
   int result;

   // Reverse string and compare (ignore case):
   result = _stricmp( string, _strrev( _strdup( string ) ) );
   if( result == 0 )
      printf( "The string \"%s\" is a palindrome\n", string );
   else
      printf( "The string \"%s\" is not a palindrome\n", string );
}
```

```Output
The string "Able was I ere I saw Elba" is a palindrome
```

## <a name="see-also"></a>Voir aussi

[Manipulation de chaînes](../../c-runtime-library/string-manipulation-crt.md)<br/>
[Paramètres régionaux](../../c-runtime-library/locale.md)<br/>
[Interprétation des séquences de caractères multi-octets](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[strcpy, wcscpy, _mbscpy](strcpy-wcscpy-mbscpy.md)<br/>
[_strset, _strset_l, _wcsset, _wcsset_l, _mbsset, _mbsset_l](strset-strset-l-wcsset-wcsset-l-mbsset-mbsset-l.md)<br/>
