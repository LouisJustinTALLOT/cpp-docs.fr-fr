---
title: _gcvt_s
ms.date: 04/05/2018
api_name:
- _gcvt_s
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _gcvt_s
- gcvt_s
helpviewer_keywords:
- _gcvt_s function
- _CVTBUFSIZE
- floating-point functions, converting number to string
- gcvt_s function
- numbers, converting to strings
- conversions, floating point to strings
- strings [C++], converting from floating point
- CVTBUFSIZE
ms.assetid: 0a8d8a26-5940-4ae3-835e-0aa6ec1b0744
ms.openlocfilehash: da36641f6a3ba8dc1da0894aedbfa390d2e796ae
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/05/2019
ms.locfileid: "73625045"
---
# <a name="_gcvt_s"></a>_gcvt_s

Convertit une valeur à virgule flottante en chaîne. Il s’agit d’une version de [_gcvt](gcvt.md) assortie des améliorations de sécurité décrites dans [Fonctionnalités de sécurité dans le CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Syntaxe

```C
errno_t _gcvt_s(
   char *buffer,
   size_t sizeInBytes,
   double value,
   int digits
);
template <size_t cchStr>
errno_t _gcvt_s(
   char (&buffer)[cchStr],
   double value,
   int digits
); // C++ only
```

### <a name="parameters"></a>Paramètres

*buffer*<br/>
Mémoire tampon pour stocker le résultat de la conversion.

*sizeInBytes*<br/>
Taille de la mémoire tampon.

*valeur*<br/>
Valeur à convertir.

*digits*<br/>
Nombre de chiffres significatifs stockés.

## <a name="return-value"></a>Valeur de retour

Zéro si l’opération aboutit. En cas d’échec en raison d’un paramètre non valide (voir le tableau ci-après pour découvrir les valeurs non valides), le gestionnaire de paramètres non valides est appelé, comme décrit dans [Validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, un code d’erreur est retourné. Les codes d’erreur sont définis dans Errno.h. Pour obtenir la liste de ces erreurs, consultez [errno, _doserrno, _sys_errlist et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

### <a name="error-conditions"></a>Conditions d’erreur

|*buffer*|*sizeInBytes*|*valeur*|*digits*|Return|Valeur dans la *mémoire tampon*|
|--------------|-------------------|-------------|--------------|------------|-----------------------|
|**NULL**|indifférent|indifférent|indifférent|**EINVAL**|Non modifiée.|
|Not **null** (pointe vers une mémoire valide)|zéro|indifférent|indifférent|**EINVAL**|Non modifiée.|
|Not **null** (pointe vers une mémoire valide)|indifférent|indifférent|>= *sizeInBytes*|**EINVAL**|Non modifiée.|

**Problèmes de sécurité**

**_gcvt_s** peut générer une violation d’accès si la *mémoire tampon* ne pointe pas vers une mémoire valide et n’a pas la **valeur null**.

## <a name="remarks"></a>Notes

La fonction **_gcvt_s** convertit une *valeur* à virgule flottante en une chaîne de caractères (qui comprend une virgule décimale et un octet de signe possible) et stocke la chaîne dans la *mémoire tampon*. la *mémoire tampon* doit être suffisamment grande pour accueillir la valeur convertie plus un caractère null de fin, qui est ajouté automatiquement. Une mémoire tampon de longueur **_CVTBUFSIZE** est suffisante pour toute valeur à virgule flottante. Si une taille de mémoire tampon de *chiffres* + 1 est utilisée, la fonction ne remplace pas la fin de la mémoire tampon. Veillez donc à fournir une mémoire tampon suffisante pour cette opération. **_gcvt_s** tente de produire des chiffres de *chiffres* au format décimal. Si ce n’est pas le cas, il génère des chiffres de *chiffres* au format exponentiel. Les zéros de fin peuvent être supprimés pendant la conversion.

En C++, l’utilisation de cette fonction est simplifiée par une surcharge de modèle ; la surcharge peut déduire automatiquement la longueur de la mémoire tampon, ce qui évite d’avoir à spécifier un argument de taille. Pour plus d’informations, consultez [Sécuriser les surcharges de modèle](../../c-runtime-library/secure-template-overloads.md).

La version de débogage de cette fonction remplit d’abord la mémoire tampon avec 0xFE. Pour désactiver ce comportement, utilisez [_CrtSetDebugFillThreshold](crtsetdebugfillthreshold.md).

## <a name="requirements"></a>spécifications

|Routine|En-tête requis|En-tête facultatif|
|-------------|---------------------|---------------------|
|**_gcvt_s**|\<stdlib.h>|\<error.h>|

Pour plus d’informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

```C
// crt_gcvt_s.c
#include <stdio.h>
#include <stdlib.h>
#include <errno.h>

int main()
{
    char buf[_CVTBUFSIZE];
    int decimal;
    int sign;
    int err;

    err = _gcvt_s(buf, _CVTBUFSIZE, 1.2, 5);

    if (err != 0)
    {
        printf("_gcvt_s failed with error code %d\n", err);
        exit(1);
    }

    printf("Converted value: %s\n", buf);
}
```

```Output
Converted value: 1.2
```

## <a name="see-also"></a>Voir aussi

[Conversion de données](../../c-runtime-library/data-conversion.md)<br/>
[Prise en charge de la virgule flottante](../../c-runtime-library/floating-point-support.md)<br/>
[atof, _atof_l, _wtof, _wtof_l](atof-atof-l-wtof-wtof-l.md)<br/>
[_ecvt_s](ecvt-s.md)<br/>
[_fcvt_s](fcvt-s.md)<br/>
[_gcvt](gcvt.md)<br/>
