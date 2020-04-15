---
title: strcpy_s, wcscpy_s, _mbscpy_s, _mbscpy_s_l
ms.date: 4/2/2020
api_name:
- wcscpy_s
- _mbscpy_s
- _mbscpy_s_l
- strcpy_s
- _o__mbscpy_s
- _o__mbscpy_s_l
- _o_strcpy_s
- _o_wcscpy_s
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
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- strcpy_s
- _mbscpy_s
- _mbscpy_s_l
- _tcscpy_s
- wcscpy_s
helpviewer_keywords:
- strcpy_s function
- _tcscpy_s function
- _mbscpy_s function
- _mbscpy_s_l function
- copying strings
- strings [C++], copying
- tcscpy_s function
- wcscpy_s function
ms.assetid: 611326f3-7929-4a5d-a465-a4683af3b053
ms.openlocfilehash: ac68d2fb86a43d7114b3b0e7651f5ae4367aa44b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81358706"
---
# <a name="strcpy_s-wcscpy_s-_mbscpy_s-_mbscpy_s_l"></a>strcpy_s, wcscpy_s, _mbscpy_s, _mbscpy_s_l

Copie une chaîne. Ces versions de [strcpy, wcscpy, _mbscpy](strcpy-wcscpy-mbscpy.md) intègrent les améliorations de sécurité décrites dans [Fonctionnalités de sécurité dans le CRT](../../c-runtime-library/security-features-in-the-crt.md).

> [!IMPORTANT]
> **_mbscpy_s** et **_mbscpy_s_l** ne peuvent pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime. Pour plus d’informations, consultez [Fonctions CRT non prises en charge dans les applications de la plateforme Windows universelle](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntaxe

```C
errno_t strcpy_s(
   char *dest,
   rsize_t dest_size,
   const char *src
);
errno_t wcscpy_s(
   wchar_t *dest,
   rsize_t dest_size,
   const wchar_t *src
);
errno_t _mbscpy_s(
   unsigned char *dest,
   rsize_t dest_size,
   const unsigned char *src
);
errno_t _mbscpy_s_l(
   unsigned char *dest,
   rsize_t dest_size,
   const unsigned char *src,
   _locale_t locale
);
```

```cpp
// Template functions are C++ only:
template <size_t size>
errno_t strcpy_s(
   char (&dest)[size],
   const char *src
); // C++ only
template <size_t size>
errno_t wcscpy_s(
   wchar_t (&dest)[size],
   const wchar_t *src
); // C++ only
template <size_t size>
errno_t _mbscpy_s(
   unsigned char (&dest)[size],
   const unsigned char *src
); // C++ only
template <size_t size>
errno_t _mbscpy_s_l(
   unsigned char (&dest)[size],
   const unsigned char *src,
   _locale_t locale
); // C++ only
```

### <a name="parameters"></a>Paramètres

*dest*<br/>
Emplacement de la mémoire tampon de chaîne de destination.

*dest_size*<br/>
Taille du tampon de chaîne de destination dans les unités **d’omble** pour les fonctions étroites et multi-byte, et **wchar_t** unités pour les fonctions larges. Cette valeur doit être supérieure à zéro et ne pas supérieure **à RSIZE_MAX**.

*src*<br/>
Mémoire tampon de chaîne source se terminant par null.

*locale*<br/>
Paramètres régionaux à utiliser.

## <a name="return-value"></a>Valeur de retour

Zéro en cas de réussite ; erreur dans un autre cas.

### <a name="error-conditions"></a>Conditions d'erreur

|*dest*|*dest_size*|*src*|Valeur retournée|Contenu de *dest*|
|----------------------|------------------------|-----------------|------------------|----------------------------------|
|**Null**|n'importe laquelle|n'importe laquelle|**EINVAL (EN)**|non modifié|
|n'importe laquelle|n'importe laquelle|**Null**|**EINVAL (EN)**|*dest*[0] réglé à 0|
|n'importe laquelle|0 ou trop petit|n'importe laquelle|**ERANGE**|*dest*[0] réglé à 0|

## <a name="remarks"></a>Notes

La fonction **strcpy_s** copie le contenu dans *l’adresse*de src , y compris le caractère null de fin, à l’endroit qui est spécifié par *dest*. La chaîne de destination doit être suffisamment grande pour contenir la chaîne source et son caractère null de fin. Le comportement de **strcpy_s** n’est pas défini si les chaînes de la source et de la destination se chevauchent.

**wcscpy_s** est la version grand caractère de **strcpy_s**, et **_mbscpy_s** est la version multioctet-caractère. Les arguments de **wcscpy_s** sont des chaînes de caractère large; ceux de **_mbscpy_s** et **_mbscpy_s_l** sont des cordes multioctets-caractères. Ces fonctions se comportent sinon de façon identique. **_mbscpy_s_l** est identique à **_mbscpy_s** sauf qu’il utilise le paramètre local passé au lieu de la localisation actuelle. Pour plus d’informations, consultez [Locale](../../c-runtime-library/locale.md).

Si *le dest* ou *le cr* est un pointeur nul, ou si la taille de la chaîne de destination *dest_size* est trop petite, le gestionnaire de paramètres invalide est invoqué, tel que décrit dans la validation [de paramètres](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, ces fonctions retournent **EINVAL** et mettent **errno** à **EINVAL** lorsque *dest* ou *src* est un pointeur nul, et ils retournent **ERANGE** et mettent **errno** à **ERANGE** lorsque la chaîne de destination est trop petite.

Si l'exécution aboutit, la chaîne de destination se termine toujours par un caractère null.

En C++, l’utilisation de ces fonctions est simplifiée par les surcharges de modèle qui peuvent déduire la longueur de la mémoire tampon automatiquement, ce qui vous évite ainsi d’avoir à spécifier un argument de taille, et elles peuvent remplacer automatiquement les fonctions plus anciennes et moins sécurisées par leurs équivalents plus récents et sécurisés. Pour plus d’informations, consultez [Sécuriser les surcharges de modèle](../../c-runtime-library/secure-template-overloads.md).

Les versions de bibliothèque de débogé de ces fonctions remplissent d’abord le tampon avec 0xFE. Pour désactiver ce comportement, utilisez [_CrtSetDebugFillThreshold](crtsetdebugfillthreshold.md).

Par défaut, l’état global de cette fonction est étendue à l’application. Pour changer cela, voir [Global State dans le CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine TCHAR.H|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcscpy_s**|**strcpy_s**|**_mbscpy_s**|**wcscpy_s**|

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**strcpy_s**|\<string.h>|
|**wcscpy_s**|\<string.h> ou \<wchar.h>|
|**_mbscpy_s**|\<mbstring.h>|

Ces fonctions sont spécifiques à Microsoft. Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

Contrairement au code de qualité de production, cet échantillon appelle les fonctions de chaîne sécurisées sans vérifier les erreurs :

```C
// crt_strcpy_s.c
// Compile by using: cl /W4 crt_strcpy_s.c
// This program uses strcpy_s and strcat_s
// to build a phrase.

#include <string.h>     // for strcpy_s, strcat_s
#include <stdlib.h>     // for _countof
#include <stdio.h>      // for printf
#include <errno.h>      // for return values

int main(void)
{
    char string[80];

    strcpy_s(string, _countof(string), "Hello world from ");
    strcat_s(string, _countof(string), "strcpy_s ");
    strcat_s(string, _countof(string), "and ");
    strcat_s(string, _countof(string), "strcat_s!");

    printf("String = %s\n", string);
}
```

```Output
String = Hello world from strcpy_s and strcat_s!
```

Lors de la construction du code C, les versions de modèle peuvent être plus faciles à utiliser.

```cpp
// crt_wcscpy_s.cpp
// Compile by using: cl /EHsc /W4 crt_wcscpy_s.cpp
// This program uses wcscpy_s and wcscat_s
// to build a phrase.

#include <cstring>  // for wcscpy_s, wcscat_s
#include <cstdlib>  // for _countof
#include <iostream> // for cout, includes <cstdlib>, <cstring>
#include <errno.h>  // for return values

int main(void)
{
    wchar_t string[80];
    // using template versions of wcscpy_s and wcscat_s:
    wcscpy_s(string, L"Hello world from ");
    wcscat_s(string, L"wcscpy_s ");
    wcscat_s(string, L"and ");
    // of course we can supply the size explicitly if we want to:
    wcscat_s(string, _countof(string), L"wcscat_s!");

    std::wcout << L"String = " << string << std::endl;
}
```

```Output
String = Hello world from wcscpy_s and wcscat_s!
```

## <a name="see-also"></a>Voir aussi

[Manipulation des cordes](../../c-runtime-library/string-manipulation-crt.md) <br/>
[strcat, wcscat, _mbscat, _mbscat_l](strcat-wcscat-mbscat.md) <br/>
[strcmp, wcscmp, _mbscmp, _mbscmp_l](strcmp-wcscmp-mbscmp.md) <br/>
[strncat_s, _strncat_s_l, wcsncat_s, _wcsncat_s_l, _mbsncat_s, _mbsncat_s_l](strncat-s-strncat-s-l-wcsncat-s-wcsncat-s-l-mbsncat-s-mbsncat-s-l.md) <br/>
[strncmp, wcsncmp, _mbsncmp, _mbsncmp_l](strncmp-wcsncmp-mbsncmp-mbsncmp-l.md) <br/>
[strncpy_s, _strncpy_s_l, wcsncpy_s, _wcsncpy_s_l, _mbsncpy_s, _mbsncpy_s_l](strncpy-s-strncpy-s-l-wcsncpy-s-wcsncpy-s-l-mbsncpy-s-mbsncpy-s-l.md) <br/>
[_strnicmp, _wcsnicmp, _mbsnicmp, _strnicmp_l, _wcsnicmp_l, _mbsnicmp_l](strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md) <br/>
[strrchr, wcsrchr, _mbsrchr, _mbsrchr_l](strrchr-wcsrchr-mbsrchr-mbsrchr-l.md) <br/>
[strspn, wcsspn, _mbsspn, _mbsspn_l](strspn-wcsspn-mbsspn-mbsspn-l.md)<br/>
