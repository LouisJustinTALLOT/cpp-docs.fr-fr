---
title: strtold, _strtold_l, wcstold, _wcstold_l
ms.date: 4/2/2020
api_name:
- wcstold
- strtold
- _strtold_l
- _wcstold_l
- _o__strtold_l
- _o__wcstold_l
- _o_strtold
- _o_wcstold
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
- api-ms-win-crt-convert-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _tcstold_l
- _wcstold_l
- _tcstold
- strtold
- _strtold_l
- wcstold
ms.assetid: 928c0c9a-bc49-445b-8822-100eb5954115
ms.openlocfilehash: 9acc98296651f549ceffb1e1deab350a71747ea5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365361"
---
# <a name="strtold-_strtold_l-wcstold-_wcstold_l"></a>strtold, _strtold_l, wcstold, _wcstold_l

Convertit les chaînes en valeur à virgule flottante double précision long.

## <a name="syntax"></a>Syntaxe

```C
long double strtold(
   const char *strSource,
   char **endptr
);
long double _strtold_l(
   const char *strSource,
   char **endptr,
   _locale_t locale
);
long double wcstold(
   const wchar_t *strSource,
   wchar_t **endptr
);
long double wcstold_l(
   const wchar_t *strSource,
   wchar_t **endptr,
   _locale_t locale
);
```

### <a name="parameters"></a>Paramètres

*strSource (en)*<br/>
Chaîne se terminant par un caractère Null à convertir.

*endptr*<br/>
Pointeur désignant le caractère qui arrête l’analyse.

*locale*<br/>
Paramètres régionaux à utiliser.

## <a name="return-value"></a>Valeur de retour

**strtold** renvoie la valeur du nombre de points flottants comme un **long** **double,** sauf lorsque la représentation causerait un débordement — dans ce cas, la fonction renvoie**HUGE_VALL**. Le signe de **HUGE_VALL** correspond au signe de la valeur qui ne peut pas être représentée. **retours strtold** 0 si aucune conversion ne peut être effectuée ou un underflow se produit.

**wcstold** retourne des valeurs de façon analogue à **strtold**. Pour les deux fonctions, **errno** est réglé sur **ERANGE** en cas de débordement ou de sous-flux et si le gestionnaire de paramètres invalide est invoqué, tel que décrit dans [La validation des paramètres](../../c-runtime-library/parameter-validation.md).

Pour plus d’informations sur les codes de retour, consultez [errno, _doserrno, _sys_errlist et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Notes

Chaque fonction convertit la chaîne d’entrée *strSource* en un **long** **double**. La fonction **strtold** cesse de lire la chaîne *strSource* au premier caractère qu’il ne peut pas reconnaître comme faisant partie d’un certain nombre. Il peut s’agir du caractère Null de fin. La version à caractère large de **strtold** est **wcstold;** son argument *strSource* est une chaîne de caractère large. Sinon, ces fonctions se comportent de façon identique.

Par défaut, l’état global de cette fonction est étendue à l’application. Pour changer cela, voir [Global State dans le CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine TCHAR.H|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcstold**|**strtold**|**strtold**|**wcstold**|
|**_tcstold_l**|**_strtold_l**|**_strtold_l**|**_wcstold_l**|

Le **LC_NUMERIC** cadre de catégorie de la localisation actuelle détermine la reconnaissance du caractère radix dans *strSource*. Pour plus d’informations, consultez [setlocale, _wsetlocale](setlocale-wsetlocale.md). Les fonctions sans le **suffixe _l** utilisent le lieu actuel; **_strtold_l** et **_wcstold_l** sont identiques à **_strtold** et **_wcstold** sauf qu’ils utilisent plutôt le lieu qui est passé. Pour plus d’informations, consultez [Locale](../../c-runtime-library/locale.md).

Si *endptr n’est* pas **NULL**, un pointeur pour le personnage qui a arrêté l’analyse est stocké à l’endroit qui est pointé vers par *endptr*. Si aucune conversion ne peut être effectuée (aucun chiffre valide n’a été trouvé ou une base invalide a été spécifiée), la valeur de *strSource* est stockée à l’endroit qui est indiqué par *endptr*.

**strtold** s’attend à ce que *strSource* pointe vers une série de la forme suivante :

[*espace blanc*] [*signe*] [*chiffres*] [. *chiffres*] [**d** &#124; **D** &#124; **e** &#124; **E**[*signe*]*chiffres*]

Un *espace blanc* peut se composer de caractères d’espace et d’onglet, qui sont ignorés ; *signe* est soit**+** plus (**-**) ou moins ( ); et *les chiffres* sont un ou plusieurs chiffres décimaux. Si aucun chiffre n’apparaît avant le caractère de base, il doit en figurer au moins un après le caractère de base. Les chiffres décimaux peuvent être suivis d’un exposant, qui se compose d’une lettre d’introduction (**d**, **D**, **e** ou **E**) et éventuellement d’un entier signé. S’il n’apparaît ni exposant ni caractère de base, il est supposé qu’un caractère de base suit le dernier chiffre dans la chaîne. Le premier caractère qui ne correspond pas à ce format a pour effet d’arrêter l’analyse.

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**strtold**, **_strtold_l**|\<stdlib.h>|
|**wcstold**, **_wcstold_l**|\<stdlib.h> ou \<wchar.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

```C
// crt_strtold.c
// Build with: cl /W4 /Tc crt_strtold.c
// This program uses strtold to convert a
// string to a long double-precision value.

#include <stdlib.h>
#include <stdio.h>

int main( void )
{
   char *string;
   char *stopstring;
   long double x;

   string = "3.1415926535898This stopped it";
   x = strtold(string, &stopstring);
   printf("string = %s\n", string);
   printf("   strtold = %.13Lf\n", x);
   printf("   Stopped scan at: %s\n\n", stopstring);
}
```

```Output
string = 3.1415926535898This stopped it
   strtold = 3.1415926535898
   Stopped scan at: This stopped it
```

## <a name="see-also"></a>Voir aussi

[Conversion de données](../../c-runtime-library/data-conversion.md)<br/>
[Soutien à la pointe flottante](../../c-runtime-library/floating-point-support.md)<br/>
[Interprétation des séquences multioctets-caractères](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[Local](../../c-runtime-library/locale.md)<br/>
[Fonctions de valeur chaîne en valeur numérique](../../c-runtime-library/string-to-numeric-value-functions.md)<br/>
[strtod, _strtod_l, wcstod, _wcstod_l](strtod-strtod-l-wcstod-wcstod-l.md)<br/>
[strtol, wcstol, _strtol_l, _wcstol_l](strtol-wcstol-strtol-l-wcstol-l.md)<br/>
[strtoul, _strtoul_l, wcstoul, _wcstoul_l](strtoul-strtoul-l-wcstoul-wcstoul-l.md)<br/>
[atof, _atof_l, _wtof, _wtof_l](atof-atof-l-wtof-wtof-l.md)<br/>
[localeconv](localeconv.md)<br/>
[_create_locale, _wcreate_locale](create-locale-wcreate-locale.md)<br/>
[_free_locale](free-locale.md)<br/>
