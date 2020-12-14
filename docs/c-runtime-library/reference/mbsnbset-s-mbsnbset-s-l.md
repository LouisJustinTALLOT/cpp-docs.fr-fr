---
description: 'En savoir plus sur : _mbsnbset_s, _mbsnbset_s_l'
title: _mbsnbset_s, _mbsnbset_s_l
ms.date: 4/2/2020
api_name:
- _mbsnbset_s_l
- _mbsnbset_s
- _o__mbsnbset_s
- _o__mbsnbset_s_l
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
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- mbsnbset_s
- _mbsnbset_s_l
- _mbsnbset_s
- mbsnbset_s_l
helpviewer_keywords:
- tcsnset_s function
- mbsnbset_s function
- mbsnbset_s_l function
- _mbsnbset_s_l function
- _tcsnset_s_l function
- _mbsnbset_s function
- _tcsnset_s function
- tcsnset_s_l function
ms.assetid: 811f92c9-cc31-4bbd-8017-2d1bfc6fb96f
ms.openlocfilehash: e8500de308d564b9e16ba5de29af67ee65b260e6
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97240193"
---
# <a name="_mbsnbset_s-_mbsnbset_s_l"></a>_mbsnbset_s, _mbsnbset_s_l

Définit les **n** premiers octets d’une chaîne de caractères multioctets sur un caractère spécifié. Ces versions de [_mbsnbset, _mbsnbset_l](mbsnbset-mbsnbset-l.md) intègrent des améliorations de sécurité, comme décrit dans [Fonctionnalités de sécurité dans le CRT](../../c-runtime-library/security-features-in-the-crt.md).

> [!IMPORTANT]
> Cette API ne peut pas être utilisée dans les applications qui s'exécutent dans le Windows Runtime. Pour plus d’informations, consultez [Fonctions CRT non prises en charge dans les applications de la plateforme Windows universelle](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntaxe

```C
errno_t _mbsnbset_s(
   unsigned char *str,
   size_t size,
   unsigned int c,
   size_t count
);
errno_t _mbsnbset_s_l(
   unsigned char *str,
   size_t size,
   unsigned int c,
   size_t count,
   _locale_t locale
);
template <size_t size>
errno_t _mbsnbset_s(
   unsigned char (&str)[size],
   unsigned int c,
   size_t count
); // C++ only
template <size_t size>
errno_t _mbsnbset_s_l(
   unsigned char (&str)[size],
   unsigned int c,
   size_t count,
   _locale_t locale
); // C++ only
```

### <a name="parameters"></a>Paramètres

*str*<br/>
Chaîne à modifier.

*size*<br/>
Taille de la mémoire tampon de chaîne.

*c*<br/>
Paramètre de caractère codé sur un octet ou multioctet.

*count*<br/>
Nombre d'octets à définir.

*locale*<br/>
Paramètres régionaux à utiliser.

## <a name="return-value"></a>Valeur renvoyée

Zéro en cas de réussite ; code d'erreur dans un autre cas.

## <a name="remarks"></a>Notes

Les fonctions **_mbsnbset_s** et **_mbsnbset_s_l** définissent, au plus, le premier *nombre* d’octets de *Str* à *c*. Si *Count* est supérieur à la longueur de *Str*, la longueur de *Str* est utilisée à la place de *Count*. Si *c* est un caractère multioctet et ne peut pas être défini entièrement dans le dernier octet spécifié par *Count*, le dernier octet est rempli avec un caractère vide. **_mbsnbset_s** et **_mbsnbset_s_l** ne placent pas de caractère null de fin à la fin de *Str*.

**_mbsnbset_s** et **_mbsnbset_s_l** ressemblent à **_mbsnset**, sauf qu’ils définissent le *nombre* d’octets plutôt que le *nombre* de caractères de *c*.

Si *Str* est **null** ou que *Count* est égal à zéro, cette fonction génère une exception de paramètre non valide, comme décrit dans [validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, **errno** a la valeur **EINVAL** et la fonction retourne la **valeur null**. En outre, si *c* n’est pas un caractère multioctet valide, **errno** a la valeur **EINVAL** et un espace est utilisé à la place.

La valeur de sortie est affectée par la valeur du paramètre de catégorie **LC_CTYPE** des paramètres régionaux. Pour plus d’informations [, consultez setlocale, _wsetlocale](setlocale-wsetlocale.md) . La version **_mbsnbset_s** de cette fonction utilise les paramètres régionaux actuels pour ce comportement dépendant des paramètres régionaux ; la version de **_mbsnbset_s_l** est identique, à ceci près qu’elle utilise à la place les paramètres régionaux qui sont passés. Pour plus d’informations, consultez [Locale](../../c-runtime-library/locale.md).

En C++, l’utilisation de ces fonctions est simplifiée par les surcharges de modèle ; les surcharges peuvent déduire automatiquement la longueur de la mémoire tampon, ce qui évite ainsi d’avoir à spécifier un argument de taille. Pour plus d’informations, consultez [Sécuriser les surcharges de modèle](../../c-runtime-library/secure-template-overloads.md).

Les versions de la bibliothèque de débogage de ces fonctions remplissent d’abord la mémoire tampon avec 0xFE. Pour désactiver ce comportement, utilisez [_CrtSetDebugFillThreshold](crtsetdebugfillthreshold.md).

Par défaut, l’état global de cette fonction est limité à l’application. Pour modifier cette valeur, consultez [état global dans le CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine Tchar.h|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tcsnset_s**|**_strnset_s**|**_mbsnbset_s**|**_wcsnset_s**|
|**_tcsnset_s_l**|`_strnset_s _l`|**_mbsnbset_s_l**|**_wcsnset_s_l**|

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**_mbsnbset_s**|\<mbstring.h>|
|**_mbsnbset_s_l**|\<mbstring.h>|

Pour plus d’informations sur la compatibilité, consultez [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

```C
// crt_mbsnbset_s.c
#include <mbstring.h>
#include <stdio.h>

int main( void )
{
   char string[15] = "This is a test";
   /* Set not more than 4 bytes of string to be *'s */
   printf( "Before: %s\n", string );
   _mbsnbset_s( string, sizeof(string), '*', 4 );
   printf( "After:  %s\n", string );
}
```

## <a name="output"></a>Output

```Output
Before: This is a test
After:  **** is a test
```

## <a name="see-also"></a>Voir aussi

[Manipulation de chaînes](../../c-runtime-library/string-manipulation-crt.md)<br/>
[_mbsnbcat, _mbsnbcat_l](mbsnbcat-mbsnbcat-l.md)<br/>
[_strnset, _strnset_l, _wcsnset, _wcsnset_l, _mbsnset, _mbsnset_l](strnset-strnset-l-wcsnset-wcsnset-l-mbsnset-mbsnset-l.md)<br/>
[_strset, _strset_l, _wcsset, _wcsset_l, _mbsset, _mbsset_l](strset-strset-l-wcsset-wcsset-l-mbsset-mbsset-l.md)<br/>
