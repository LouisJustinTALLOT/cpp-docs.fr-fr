---
description: 'En savoir plus sur : _mbsnbset, _mbsnbset_l'
title: _mbsnbset, _mbsnbset_l
ms.date: 4/2/2020
api_name:
- _mbsnbset
- _mbsnbset_l
- _o__mbsnbset
- _o__mbsnbset_l
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
- mbsnbset
- mbsnbset_l
- _mbsnbset
- _mbsnbset_l
helpviewer_keywords:
- tcsnset function
- _tcsnset_l function
- _mbsnbset function
- _tcsnset function
- _mbsnbset_l function
- mbsnbset_l function
- tcsnset_l function
- mbsnbset function
ms.assetid: 8e46ef75-9a56-42d2-a522-a08450c67c19
ms.openlocfilehash: a99e92cec8b15c9534cec981652ce7c78fa31923
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97240258"
---
# <a name="_mbsnbset-_mbsnbset_l"></a>_mbsnbset, _mbsnbset_l

Définit les **n** premiers octets d’une chaîne de caractères multioctets sur un caractère spécifié. Des versions plus sécurisées de ces fonctions sont disponibles. Consultez [_mbsnbset_s, _mbsnbset_s_l](mbsnbset-s-mbsnbset-s-l.md).

> [!IMPORTANT]
> Cette API ne peut pas être utilisée dans les applications qui s'exécutent dans le Windows Runtime. Pour plus d’informations, consultez [Fonctions CRT non prises en charge dans les applications de la plateforme Windows universelle](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntaxe

```C
unsigned char *_mbsnbset(
   unsigned char *str,
   unsigned int c,
   size_t count
);
unsigned char *_mbsnbset_l(
   unsigned char *str,
   unsigned int c,
   size_t count,
   _locale_t locale
);
```

### <a name="parameters"></a>Paramètres

*str*<br/>
Chaîne à modifier.

*c*<br/>
Paramètre de caractère codé sur un octet ou multioctet.

*count*<br/>
Nombre d'octets à définir.

*locale*<br/>
Paramètres régionaux à utiliser.

## <a name="return-value"></a>Valeur renvoyée

**_mbsnbset** retourne un pointeur vers la chaîne modifiée.

## <a name="remarks"></a>Notes

Les fonctions **_mbsnbset** et **_mbsnbset_l** définissent, au plus, le premier *nombre* d’octets de *Str* à *c*. Si *Count* est supérieur à la longueur de *Str*, la longueur de *Str* est utilisée à la place de *Count*. Si *c* est un caractère multioctet et ne peut pas être défini entièrement dans le dernier octet spécifié par *Count*, le dernier octet est rempli avec un caractère vide. **_mbsnbset** et **_mbsnbset_l** ne placent pas de caractère null de fin à la fin de *Str*.

**_mbsnbset** et **_mbsnbset_l** est similaire à **_mbsnset**, à ceci près qu’il définit le *nombre* d’octets plutôt que le *nombre* de caractères de *c*.

Si *Str* est **null** ou que *Count* est égal à zéro, cette fonction génère une exception de paramètre non valide, comme décrit dans [validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, **errno** a la valeur **EINVAL** et la fonction retourne la **valeur null**. En outre, si *c* n’est pas un caractère multioctet valide, **errno** a la valeur **EINVAL** et un espace est utilisé à la place.

La valeur de sortie est affectée par la valeur du paramètre de catégorie **LC_CTYPE** des paramètres régionaux. Pour plus d’informations, consultez [setlocale](setlocale-wsetlocale.md). La version **_mbsnbset** de cette fonction utilise les paramètres régionaux actuels pour ce comportement dépendant des paramètres régionaux ; la version de **_mbsnbset_l** est identique, à ceci près qu’elle utilise à la place les paramètres régionaux transmis. Pour plus d’informations, consultez [Locale](../../c-runtime-library/locale.md).

**Remarque relative à la sécurité** Cette API est exposée à une menace potentielle liée à un problème de dépassement de mémoire tampon. Les dépassements de mémoire tampon sont une méthode fréquente d'attaque du système, ce qui provoque une élévation des privilèges injustifiée. Pour plus d’informations, consultez [Solutions contre les dépassements de mémoire tampon](/windows/win32/SecBP/avoiding-buffer-overruns).

Par défaut, l’état global de cette fonction est limité à l’application. Pour modifier cette valeur, consultez [état global dans le CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine Tchar.h|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tcsnset**|**_strnset**|**_mbsnbset**|**_wcsnset**|
|**_tcsnset_l**|**_strnset_l**|**_mbsnbset_l**|**_wcsnset_l**|

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**_mbsnbset**|\<mbstring.h>|
|**_mbsnbset_l**|\<mbstring.h>|

Pour plus d’informations sur la compatibilité, consultez [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

```C
// crt_mbsnbset.c
// compile with: /W3
#include <mbstring.h>
#include <stdio.h>

int main( void )
{
   char string[15] = "This is a test";
   /* Set not more than 4 bytes of string to be *'s */
   printf( "Before: %s\n", string );
   _mbsnbset( string, '*', 4 ); // C4996
   // Note; _mbsnbset is deprecated; consider _mbsnbset_s
   printf( "After:  %s\n", string );
}
```

### <a name="output"></a>Output

```Output
Before: This is a test
After:  **** is a test
```

## <a name="see-also"></a>Voir aussi

[Manipulation de chaînes](../../c-runtime-library/string-manipulation-crt.md)<br/>
[_mbsnbcat, _mbsnbcat_l](mbsnbcat-mbsnbcat-l.md)<br/>
[_strnset, _strnset_l, _wcsnset, _wcsnset_l, _mbsnset, _mbsnset_l](strnset-strnset-l-wcsnset-wcsnset-l-mbsnset-mbsnset-l.md)<br/>
[_strset, _strset_l, _wcsset, _wcsset_l, _mbsset, _mbsset_l](strset-strset-l-wcsset-wcsset-l-mbsset-mbsset-l.md)<br/>
