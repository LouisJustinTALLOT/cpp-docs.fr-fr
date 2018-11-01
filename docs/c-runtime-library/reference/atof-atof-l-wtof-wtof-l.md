---
title: atof, _atof_l, _wtof, _wtof_l
ms.date: 04/05/2018
apiname:
- _wtof_l
- atof
- _atof_l
- _wtof
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
- api-ms-win-crt-convert-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _tstof
- _ttof
- atof
- stdlib/atof
- math/atof
- _atof_l
- stdlib/_atof_l
- math/_atof_l
- _wtof
- corecrt_wstdlib/_wtof
- _wtof_l
- corecrt_wstdlib/_wtof_l
helpviewer_keywords:
- tstof function
- atof_l function
- _atof_l function
- atof function
- _tstof function
- _ttof function
- wtof function
- _wtof_l function
- ttof function
- wtof_l function
- _wtof function
- string conversion, to floating point values
ms.assetid: eb513241-c9a9-4f5c-b7e7-a49b14abfb75
ms.openlocfilehash: 6c2ec158ac0b75a861b5b226d33de113d76988cb
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50471173"
---
# <a name="atof-atofl-wtof-wtofl"></a>atof, _atof_l, _wtof, _wtof_l

Convertissent une chaîne en double.

## <a name="syntax"></a>Syntaxe

```C
double atof(
   const char *str
);
double _atof_l(
   const char *str,
   _locale_t locale
);
double _wtof(
   const wchar_t *str
);
double _wtof_l(
   const wchar_t *str,
   _locale_t locale
);
```

## <a name="parameters"></a>Paramètres

*str*<br/>
Chaîne à convertir.

*locale*<br/>
Paramètres régionaux à utiliser.

## <a name="return-value"></a>Valeur de retour

Chaque fonction retourne le **double** valeur produite en interprétant les caractères d’entrée en tant que nombre. La valeur de retour est 0.0 si l’entrée ne peut pas être convertie en valeur de ce type.

Dans tous les cas hors limites, **errno** a la valeur **ERANGE**. Si le paramètre passé est **NULL**, le Gestionnaire de paramètre non valide est appelé, comme décrit dans [Validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, ces fonctions définissent **errno** à **EINVAL** et retournent 0.

## <a name="remarks"></a>Notes

Ces fonctions convertissent une chaîne de caractères en valeur à virgule flottante double précision.

La chaîne d’entrée est une séquence de caractères qui peut être interprétée comme une valeur numérique du type spécifié. La fonction arrête de lire la chaîne d’entrée au premier caractère qu’elle ne peut pas reconnaître comme faisant partie d’un nombre. Ce caractère peut être le caractère Null ('\0' ou L'\0') terminant la chaîne.

Le *str* l’argument de **atof** et **_wtof** a la forme suivante :

[*espace blanc*] [*connexion*] [*chiffres*] [__.__ *chiffres*] [{**e** &#124; **E** } [*connexion*]*chiffres*]

Un *espace blanc* se compose de caractères espace ou tabulation, qui sont ignorés ; *connexion* est soit plus (+) ou moins (-) ; et *chiffres* représente un ou plusieurs chiffres décimaux. Si aucun chiffre n’apparaît avant la virgule décimale, au moins un doit apparaître après celle-ci. Les chiffres décimaux peuvent être suivies d’un exposant, qui se compose d’une lettre d’introduction (**e**, ou **E**) et un entier décimal signé si vous le souhaitez.

Les versions UCRT de ces fonctions ne prennent pas en charge la conversion de style Fortran (**d** ou **D**) lettres d’exposants. Cette extension non standard était prise en charge par les versions antérieures de la bibliothèque CRT et peut être une modification avec rupture pour votre code.

Les versions de ces fonctions avec le **_l** suffixe sont identiques, sauf qu’ils utilisent le *paramètres régionaux* paramètre passés au lieu des paramètres régionaux actuels.

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine TCHAR.H|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tstof**|**atof**|**atof**|**_wtof**|
|**_ttof**|**atof**|**atof**|**_wtof**|

## <a name="requirements"></a>Configuration requise

|Routine(s)|En-tête requis|
|------------------|---------------------|
|**atof**, **_atof_l**|C : \<math.h> ou \<stdlib.h> C++ : \<cstdlib>, \<stdlib.h>, \<cmath> ou \<math.h>|
|**_wtof**, **_wtof_l**|C : \<stdlib.h> ou \<wchar.h> C++ : \<cstdlib>, \<stdlib.h> ou \<wchar.h>|

## <a name="example"></a>Exemple

Ce programme montre comment nombres stockés sous forme de chaînes peuvent être convertis en valeurs numériques à l’aide de la **atof** et **_atof_l** fonctions.

```C
// crt_atof.c
//
// This program shows how numbers stored as
// strings can be converted to numeric
// values using the atof and _atof_l functions.

#include <stdlib.h>
#include <stdio.h>
#include <locale.h>

int main(void)
{
    char    *str = NULL;
    double value = 0;
    _locale_t fr = _create_locale(LC_NUMERIC, "fr-FR");

    // An example of the atof function
    // using leading and training spaces.
    str = "  3336402735171707160320 ";
    value = atof(str);
    printf("Function: atof(\"%s\") = %e\n", str, value);

    // Another example of the atof function
    // using the 'E' exponential formatting keyword.
    str = "3.1412764583E210";
    value = atof(str);
    printf("Function: atof(\"%s\") = %e\n", str, value);

    // An example of the atof and _atof_l functions
    // using the 'e' exponential formatting keyword
    // and showing different decimal point interpretations.
    str = "  -2,309e-25";
    value = atof(str);
    printf("Function: atof(\"%s\") = %e\n", str, value);
    value = _atof_l(str, fr);
    printf("Function: _atof_l(\"%s\", fr)) = %e\n", str, value);
}
```

```Output
Function: atof("  3336402735171707160320 ") = 3.336403e+21
Function: atof("3.1412764583E210") = 3.141276e+210
Function: atof("  -2,309e-25") = -2.000000e+00
Function: _atof_l("  -2,309e-25", fr)) = -2.309000e-25
```

## <a name="see-also"></a>Voir aussi

[Conversion de données](../../c-runtime-library/data-conversion.md)<br/>
[Prise en charge de la virgule flottante](../../c-runtime-library/floating-point-support.md)<br/>
[Paramètres régionaux](../../c-runtime-library/locale.md)<br/>
[_ecvt](ecvt.md)<br/>
[_fcvt](fcvt.md)<br/>
[_gcvt](gcvt.md)<br/>
[setlocale, _wsetlocale](setlocale-wsetlocale.md)<br/>
[_atodbl, _atodbl_l, _atoldbl, _atoldbl_l, _atoflt, _atoflt_l](atodbl-atodbl-l-atoldbl-atoldbl-l-atoflt-atoflt-l.md)<br/>
