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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: e33840e772de770e0f05ae45d2c2d4bec7e09939
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81348047"
---
# <a name="_ecvt_s"></a>_ecvt_s

Convertit un **double** numéro en une chaîne. Il s’agit d’une version de [_ecvt](ecvt.md) assortie des améliorations de sécurité décrites dans [Fonctionnalités de sécurité dans le CRT](../../c-runtime-library/security-features-in-the-crt.md).

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

En cas de paramètre non valide, comme indiqué dans le tableau suivant, cette fonction appelle le gestionnaire de paramètres non valides, comme décrit dans [Validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, cette fonction définit **errno** à **EINVAL** et retourne **EINVAL**.

### <a name="error-conditions"></a>Conditions d'erreur

|*_Buffer*|*_SizeInBytes*|_Value|_Count|_Dec|_Sign|Valeur retournée|Valeur dans *le tampon*|
|---------------|--------------------|-------------|-------------|-----------|------------|------------------|-----------------------|
|**Null**|n'importe laquelle|n'importe laquelle|n'importe laquelle|n'importe laquelle|n'importe laquelle|**EINVAL (EN)**|Non modifiée.|
|Non **NULL** (points à la mémoire valide)|<=0|n'importe laquelle|n'importe laquelle|n'importe laquelle|n'importe laquelle|**EINVAL (EN)**|Non modifiée.|
|n'importe laquelle|n'importe laquelle|n'importe laquelle|n'importe laquelle|**Null**|n'importe laquelle|**EINVAL (EN)**|Non modifiée.|
|n'importe laquelle|n'importe laquelle|n'importe laquelle|n'importe laquelle|n'importe laquelle|**Null**|**EINVAL (EN)**|Non modifiée.|

## <a name="security-issues"></a>Problèmes de sécurité

**_ecvt_s** peut générer une violation d’accès si *le tampon* ne pointe pas vers la mémoire valide et n’est pas **NULL**.

## <a name="remarks"></a>Notes

La fonction **_ecvt_s** convertit un numéro de point flottant en une chaîne de caractères. Le *_Value* paramètre est le nombre de points flottants à convertir. Cette fonction stocke jusqu’à *compter* les chiffres de *_Value* comme une chaîne et annexe un caractère nul ('0'). Si le nombre de chiffres dans *_Value* dépasse *_Count,* le chiffre de faible ordre est arrondi. S’il y a moins de chiffres de *comptage,* la chaîne est rembourrée avec des zéros.

Seuls des chiffres sont stockés dans la chaîne. La position du point décimal et le signe de *_Value* peuvent être obtenus à partir de *_Dec* et *_Sign* après l’appel. Le *_Dec* paramètre indique une valeur integer donnant la position du point décimal par rapport au début de la chaîne. Une valeur entière ou 0 indique que la virgule décimale est située à gauche du premier chiffre. Le *_Sign* paramètre indique un intégrant qui indique le signe du nombre converti. Si la valeur entière est 0, le nombre est positif. Sinon, le nombre est négatif.

Un tampon de longueur **_CVTBUFSIZE** est suffisant pour toute valeur de point flottant.

La différence entre **_ecvt_s** et **_fcvt_s** réside dans l’interprétation du *_Count* paramètre. **_ecvt_s** interprète *_Count* comme le nombre total de chiffres dans la chaîne de sortie, tandis que **_fcvt_s** interprète *_Count* comme le nombre de chiffres après le point décimal.

En C++, l’utilisation de cette fonction est simplifiée par une surcharge de modèle ; la surcharge peut déduire automatiquement la longueur de la mémoire tampon, ce qui évite d’avoir à spécifier un argument de taille. Pour plus d’informations, consultez [Sécuriser les surcharges de modèle](../../c-runtime-library/secure-template-overloads.md).

La version de débogé de cette fonction remplit d’abord le tampon avec 0xFE. Pour désactiver ce comportement, utilisez [_CrtSetDebugFillThreshold](crtsetdebugfillthreshold.md).

Par défaut, l’état global de cette fonction est étendue à l’application. Pour changer cela, voir [Global State dans le CRT](../global-state.md).

## <a name="requirements"></a>Spécifications

|Fonction|En-tête requis|En-tête facultatif|
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
[Soutien à la pointe flottante](../../c-runtime-library/floating-point-support.md)<br/>
[atof, _atof_l, _wtof, _wtof_l](atof-atof-l-wtof-wtof-l.md)<br/>
[_ecvt](ecvt.md)<br/>
[_fcvt_s](fcvt-s.md)<br/>
[_gcvt_s](gcvt-s.md)<br/>
