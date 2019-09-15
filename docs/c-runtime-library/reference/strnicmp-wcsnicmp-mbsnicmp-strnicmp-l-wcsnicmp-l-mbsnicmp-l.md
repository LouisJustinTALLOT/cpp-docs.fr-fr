---
title: _strnicmp, _wcsnicmp, _mbsnicmp, _strnicmp_l, _wcsnicmp_l, _mbsnicmp_l
ms.date: 11/04/2016
api_name:
- _wcsnicmp
- _strnicmp_l
- _wcsnicmp_l
- _strnicmp
- _mbsnicmp
- _mbsnicmp_l
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
- wcsnicmp_l
- _strnicmp
- _ftcsnicmp
- mbsnicmp_l
- _ftcsncicmp
- mbsnicmp
- _tcsncicmp
- _mbsnicmp
- _tcsnicmp
- strnicmp_l
- _wcsnicmp
- _wcsnicmp_l
- CORECRT_WSTRING/_wcsnicmp
- CORECRT_WSTRING/_wcsnicmp_l
- string/_strnicmp
- string/_strnicmp_l
helpviewer_keywords:
- tcsnicmp function
- _tcsncicmp function
- _mbsnicmp_l function
- mbsnicmp_l function
- wcsnicmp_l function
- wcsnicmp function
- string comparison [C++], lowercase
- ftcsnicmp function
- strnicmp_l function
- strncmp function
- _strnicmp function
- strings [C++], comparing characters of
- _wcsnicmp_l function
- tcsncicmp function
- string comparison [C++], strncmp function
- _mbsnicmp function
- ftcsncicmp function
- _tcsnicmp function
- _ftcsncicmp function
- _strnicmp_l function
- _ftcsnicmp function
- characters [C++], comparing
- mbsnicmp function
- _wcsnicmp function
ms.assetid: df6e5037-4039-4c85-a0a6-21d4ef513966
ms.openlocfilehash: 6d1645c33684f5a0fbabc2119592c39a7df97ca3
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70947132"
---
# <a name="_strnicmp-_wcsnicmp-_mbsnicmp-_strnicmp_l-_wcsnicmp_l-_mbsnicmp_l"></a>_strnicmp, _wcsnicmp, _mbsnicmp, _strnicmp_l, _wcsnicmp_l, _mbsnicmp_l

Compare le nombre spécifié de caractères de deux chaînes sans tenir compte de la casse.

> [!IMPORTANT]
> **_mbsnicmp** et **_mbsnicmp_l** ne peuvent pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime. Pour plus d’informations, consultez [Fonctions CRT non prises en charge dans les applications de la plateforme Windows universelle](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntaxe

```C
int _strnicmp(
   const char *string1,
   const char *string2,
   size_t count
);
int _wcsnicmp(
   const wchar_t *string1,
   const wchar_t *string2,
   size_t count
);
int _mbsnicmp(
   const unsigned char *string1,
   const unsigned char *string2,
   size_t count
);
int _strnicmp_l(
   const char *string1,
   const char *string2,
   size_t count,
   _locale_t locale
);
int _wcsnicmp_l(
   const wchar_t *string1,
   const wchar_t *string2,
   size_t count,
   _locale_t locale
);
int _mbsnicmp_l(
   const unsigned char *string1,
   const unsigned char *string2,
   size_t count,
   _locale_t locale
);
```

### <a name="parameters"></a>Paramètres

*string1*, *string2*<br/>
Chaîne terminée par Null à comparer.

*count*<br/>
Nombre de caractères à comparer.

*locale*<br/>
Paramètres régionaux à utiliser.

## <a name="return-value"></a>Valeur de retour

Indique la relation entre les sous-chaînes, comme suit.

|Valeur de retour|Description|
|------------------|-----------------|
|< 0|*Chaîne1* SUBSTRING est inférieure à la sous-chaîne *Chaîne2* .|
|0|*Chaîne1* SUBSTRING est identique à la sous-chaîne *string2* .|
|> 0|la sous-chaîne *Chaîne1* est supérieure à la sous-chaîne *Chaîne2* .|

Dans le cas d’une erreur de validation de paramètre, ces fonctions retournent **_NLSCMPERROR**, qui est \<défini dans \<String. h > et mbstring. h >.

## <a name="remarks"></a>Notes

La fonction **_strnicmp** compare, au plus, les premiers caractères de *nombre* de *string1* et *Chaîne2*. La comparaison est effectuée sans tenir compte de la casse, en convertissant chaque caractère en minuscule. **_strnicmp** est une version de **strncmp**qui ne respecte pas la casse. La comparaison se termine si un caractère null de fin est atteint dans l’une ou l’autre des chaînes avant que les caractères *Count* soient comparés. Si les chaînes sont égales lorsqu’un caractère null de fin est atteint dans l’une ou l’autre des chaînes avant que les caractères *Count* soient comparés, la chaîne la plus courte est inférieure.

Les caractères compris entre 91 et 96 dans la table ASCII (« [ », « \\ », « ] », « ^ », « _ » et « \` ») sont évalués comme étant inférieurs à n’importe quel caractère alphabétique. Ce classement est identique à celui de **stricmp**.

**_wcsnicmp** et **_mbsnicmp** sont des versions à caractères larges et à caractères multioctets de **_strnicmp**. Les arguments de **_wcsnicmp** sont des chaînes à caractères larges ; ceux de **_mbsnicmp** sont des chaînes de caractères multioctets. **_mbsnicmp** reconnaît les séquences de caractères multioctets en fonction de la page de codes multioctets actuelle et retourne **_NLSCMPERROR** sur une erreur. Pour plus d’informations, consultez [Pages de codes](../../c-runtime-library/code-pages.md). Ces trois fonctions se comportent sinon de façon identique. Ces fonctions sont affectées par les paramètres régionaux : les versions qui n’ont pas le suffixe **_L** utilisent les paramètres régionaux actuels pour leur comportement dépendant des paramètres régionaux ; les versions qui ont le suffixe **_L** utilisent à la place les *paramètres régionaux* qui sont passés. Pour plus d’informations, consultez [Locale](../../c-runtime-library/locale.md).

Toutes ces fonctions valident leurs paramètres. Si *Chaîne1* ou *Chaîne2* est un pointeur null, le gestionnaire de paramètres non valides est appelé, comme décrit dans [validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, ces fonctions retournent **_NLSCMPERROR** et attribuent à **errno** la valeur **EINVAL**.

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine TCHAR.H|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcsncicmp**|**_strnicmp**|**_mbsnicmp**|**_wcsnicmp**|
|**_tcsnicmp**|**_strnicmp**|**_mbsnbicmp**|**_wcsnicmp**|
|**_tcsncicmp_l**|**_strnicmp_l**|**_mbsnicmp_l**|**_wcsnicmp_l**|

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis|
|-------------|---------------------|
|**_strnicmp**, **_strnicmp_l**|\<string.h>|
|**_wcsnicmp**, **_wcsnicmp_l**|\<string.h> ou \<wchar.h>|
|**_mbsnicmp**, **_mbsnicmp_l**|\<mbstring.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemples

Consultez l’exemple relatif à [strncmp](strncmp-wcsncmp-mbsncmp-mbsncmp-l.md).

## <a name="see-also"></a>Voir aussi

[Manipulation de chaînes](../../c-runtime-library/string-manipulation-crt.md)<br/>
[strcat, wcscat, _mbscat](strcat-wcscat-mbscat.md)<br/>
[strcmp, wcscmp, _mbscmp](strcmp-wcscmp-mbscmp.md)<br/>
[strcpy, wcscpy, _mbscpy](strcpy-wcscpy-mbscpy.md)<br/>
[strncat, _strncat_l, wcsncat, _wcsncat_l, _mbsncat, _mbsncat_l](strncat-strncat-l-wcsncat-wcsncat-l-mbsncat-mbsncat-l.md)<br/>
[strncmp, wcsncmp, _mbsncmp, _mbsncmp_l](strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)<br/>
[strncpy, _strncpy_l, wcsncpy, _wcsncpy_l, _mbsncpy, _mbsncpy_l](strncpy-strncpy-l-wcsncpy-wcsncpy-l-mbsncpy-mbsncpy-l.md)<br/>
[strrchr, wcsrchr, _mbsrchr, _mbsrchr_l](strrchr-wcsrchr-mbsrchr-mbsrchr-l.md)<br/>
[_strset, _strset_l, _wcsset, _wcsset_l, _mbsset, _mbsset_l](strset-strset-l-wcsset-wcsset-l-mbsset-mbsset-l.md)<br/>
[strspn, wcsspn, _mbsspn, _mbsspn_l](strspn-wcsspn-mbsspn-mbsspn-l.md)<br/>
