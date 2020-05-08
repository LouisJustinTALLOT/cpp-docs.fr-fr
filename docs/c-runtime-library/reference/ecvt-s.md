---
title: _ecvt_s
ms.date: 4/2/2020
api_name:
- _ecvt_s
- _o__ecvt_s
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
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- ecvt_s
- _ecvt_s
helpviewer_keywords:
- _ecvt_s function
- ecvt_s function
- numbers, converting
- converting double numbers
ms.assetid: d52fb0a6-cb91-423f-80b3-952a8955d914
ms.openlocfilehash: 9ac623c6cb80c774184dcb005e6d1d631c498040
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82915143"
---
# <a name="_ecvt_s"></a>_ecvt_s

Convertit un nombre **double** en une chaîne. Il s’agit d’une version de [_ecvt](ecvt.md) assortie des améliorations de sécurité décrites dans [Fonctionnalités de sécurité dans le CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Syntaxe

```C
errno_t _ecvt_s(
   char * _Buffer,
   size_t _SizeInBytes,
   double _Value,
   int _Count,
   int *_Dec,
   int *_Sign
);
template <size_t size>
errno_t _ecvt_s(
   char (&_Buffer)[size],
   double _Value,
   int _Count,
   int *_Dec,
   int *_Sign
); // C++ only
```

### <a name="parameters"></a>Paramètres

*_Buffer*<br/>
Rempli avec le pointeur désignant la chaîne de chiffres, le résultat de la conversion.

*_SizeInBytes*<br/>
Taille, en octets, de la mémoire tampon.

*_Value*<br/>
Nombre à convertir.

*_Count*<br/>
Nombre de chiffres stockés.

*_Dec*<br/>
Position de la virgule décimale stockée.

*_Sign*<br/>
Signe du nombre converti.

## <a name="return-value"></a>Valeur de retour

Zéro si l’opération réussit. En cas d’échec, la valeur de retour est un code d’erreur. Les codes d’erreur sont définis dans Errno.h. Pour plus d’informations, consultez [errno, _doserrno, _sys_errlist et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

En cas de paramètre non valide, comme indiqué dans le tableau suivant, cette fonction appelle le gestionnaire de paramètres non valides, comme décrit dans [Validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, cette fonction affecte à **errno** la valeur **EINVAL** et retourne **EINVAL**.

### <a name="error-conditions"></a>Conditions d'erreur

|*_Buffer*|*_SizeInBytes*|_Value|_Count|_Dec|_Sign|Valeur retournée|Valeur dans la *mémoire tampon*|
|---------------|--------------------|-------------|-------------|-----------|------------|------------------|-----------------------|
|**NUL**|n'importe laquelle|n'importe laquelle|n'importe laquelle|n'importe laquelle|n'importe laquelle|**EINVAL**|Non modifiée.|
|Not **null** (pointe vers une mémoire valide)|<=0|n'importe laquelle|n'importe laquelle|n'importe laquelle|n'importe laquelle|**EINVAL**|Non modifiée.|
|n'importe laquelle|n'importe laquelle|n'importe laquelle|n'importe laquelle|**NUL**|n'importe laquelle|**EINVAL**|Non modifiée.|
|n'importe laquelle|n'importe laquelle|n'importe laquelle|n'importe laquelle|n'importe laquelle|**NUL**|**EINVAL**|Non modifiée.|

## <a name="security-issues"></a>Problèmes de sécurité

**_ecvt_s** peut générer une violation d’accès si la *mémoire tampon* ne pointe pas vers une mémoire valide et n’a pas la **valeur null**.

## <a name="remarks"></a>Notes 

La fonction **_ecvt_s** convertit un nombre à virgule flottante en une chaîne de caractères. Le paramètre *_Value* est le nombre à virgule flottante à convertir. Cette fonction stocke jusqu’à *Count* chiffres de *_Value* sous forme de chaîne et ajoute un caractère null (« \ 0 »). Si le nombre de chiffres dans *_Value* dépasse *_count*, le chiffre de poids faible est arrondi. Si le *nombre* de chiffres est inférieur à, la chaîne est complétée par des zéros.

Seuls des chiffres sont stockés dans la chaîne. La position de la virgule décimale et le signe de *_Value* peuvent être obtenus à partir de *_Dec* et *_Sign* après l’appel. Le paramètre *_Dec* pointe vers une valeur entière indiquant la position de la virgule décimale par rapport au début de la chaîne. Une valeur entière ou 0 indique que la virgule décimale est située à gauche du premier chiffre. Le paramètre *_Sign* pointe vers un entier qui indique le signe du nombre converti. Si la valeur entière est 0, le nombre est positif. Sinon, le nombre est négatif.

Une mémoire tampon de longueur **_CVTBUFSIZE** est suffisante pour toute valeur à virgule flottante.

La différence entre **_ecvt_s** et **_fcvt_s** est l’interprétation du paramètre *_count* . **_ecvt_s** interprète *_count* comme nombre total de chiffres dans la chaîne de sortie, tandis que **_fcvt_s** interprète *_count* comme nombre de chiffres après la virgule décimale.

En C++, l’utilisation de cette fonction est simplifiée par une surcharge de modèle ; la surcharge peut déduire automatiquement la longueur de la mémoire tampon, ce qui évite d’avoir à spécifier un argument de taille. Pour plus d’informations, consultez [Sécuriser les surcharges de modèle](../../c-runtime-library/secure-template-overloads.md).

La version de débogage de cette fonction remplit d’abord la mémoire tampon avec 0xFE. Pour désactiver ce comportement, utilisez [_CrtSetDebugFillThreshold](crtsetdebugfillthreshold.md).

Par défaut, l’état global de cette fonction est limité à l’application. Pour modifier cette valeur, consultez [état global dans le CRT](../global-state.md).

## <a name="requirements"></a>Spécifications

|Function|En-tête requis|En-tête facultatif|
|--------------|---------------------|---------------------|
|**_ecvt_s**|\<stdlib.h>|\<errno.h>|

Pour plus d’informations sur la compatibilité, consultez [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

```C
// ecvt_s.c
#include <stdio.h>
#include <stdlib.h>
#include <errno.h>

int main( )
{
    char * buf = 0;
    int decimal;
    int sign;
    int err;

    buf = (char*) malloc(_CVTBUFSIZE);
    err = _ecvt_s(buf, _CVTBUFSIZE, 1.2, 5, &decimal, &sign);

    if (err != 0)
    {
        printf("_ecvt_s failed with error code %d\n", err);
        exit(1);
    }

    printf("Converted value: %s\n", buf);
}
```

```Output
Converted value: 12000
```

## <a name="see-also"></a>Voir aussi

[Conversion de données](../../c-runtime-library/data-conversion.md)<br/>
[Prise en charge de la virgule flottante](../../c-runtime-library/floating-point-support.md)<br/>
[atof, _atof_l, _wtof, _wtof_l](atof-atof-l-wtof-wtof-l.md)<br/>
[_ecvt](ecvt.md)<br/>
[_fcvt_s](fcvt-s.md)<br/>
[_gcvt_s](gcvt-s.md)<br/>
