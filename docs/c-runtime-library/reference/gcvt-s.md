---
title: _gcvt_s
ms.date: 4/2/2020
api_name:
- _gcvt_s
- _o__gcvt_s
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
ms.openlocfilehash: 10d2b9af45b78a3f5ed673bde3d37894ccb00168
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81345374"
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

*value*<br/>
Valeur à convertir.

*chiffres*<br/>
Nombre de chiffres significatifs stockés.

## <a name="return-value"></a>Valeur de retour

Zéro si l’opération réussit. En cas d’échec en raison d’un paramètre non valide (voir le tableau ci-après pour découvrir les valeurs non valides), le gestionnaire de paramètres non valides est appelé, comme décrit dans [Validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, un code d’erreur est retourné. Les codes d’erreur sont définis dans Errno.h. Pour obtenir la liste de ces erreurs, consultez [errno, _doserrno, _sys_errlist et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

### <a name="error-conditions"></a>Conditions d'erreur

|*buffer*|*sizeInBytes*|*value*|*chiffres*|Renvoie|Valeur dans *le tampon*|
|--------------|-------------------|-------------|--------------|------------|-----------------------|
|**Null**|n'importe laquelle|n'importe laquelle|n'importe laquelle|**EINVAL (EN)**|Non modifiée.|
|Non **NULL** (points à la mémoire valide)|zéro|n'importe laquelle|n'importe laquelle|**EINVAL (EN)**|Non modifiée.|
|Non **NULL** (points à la mémoire valide)|n'importe laquelle|n'importe laquelle|>= *sizeInBytes*|**EINVAL (EN)**|Non modifiée.|

**Problèmes de sécurité**

**_gcvt_s** peut générer une violation d’accès si *le tampon* ne pointe pas vers la mémoire valide et n’est pas **NULL**.

## <a name="remarks"></a>Notes

La fonction **_gcvt_s** convertit une *valeur* de point flottant en une chaîne de caractère (qui comprend un point décimal et un byte de signe possible) et stocke la chaîne dans *le tampon.* *tampon* doit être assez grand pour tenir compte de la valeur convertie plus un caractère nul de fin, qui est annexé automatiquement. Un tampon de longueur **_CVTBUFSIZE** est suffisant pour toute valeur de point flottant. Si une taille tampon de *chiffres* 1 est utilisée, la fonction ne remplacera pas l’extrémité du tampon, alors assurez-vous de fournir un tampon suffisant pour cette opération. **_gcvt_s** tente de produire des *chiffres* de chiffres en format décimal. Si elle ne peut pas, il produit *des chiffres* de chiffres en format exponentiel. Les zéros de fin peuvent être supprimés pendant la conversion.

En C++, l’utilisation de cette fonction est simplifiée par une surcharge de modèle ; la surcharge peut déduire automatiquement la longueur de la mémoire tampon, ce qui évite d’avoir à spécifier un argument de taille. Pour plus d’informations, consultez [Sécuriser les surcharges de modèle](../../c-runtime-library/secure-template-overloads.md).

La version de débogé de cette fonction remplit d’abord le tampon avec 0xFE. Pour désactiver ce comportement, utilisez [_CrtSetDebugFillThreshold](crtsetdebugfillthreshold.md).

Par défaut, l’état global de cette fonction est étendue à l’application. Pour changer cela, voir [Global State dans le CRT](../global-state.md).

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|En-tête facultatif|
|-------------|---------------------|---------------------|
|**_gcvt_s**|\<stdlib.h>|\<error.h>|

Pour plus d’informations sur la compatibilité, consultez [Compatibility](../../c-runtime-library/compatibility.md).

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
[Soutien à la pointe flottante](../../c-runtime-library/floating-point-support.md)<br/>
[atof, _atof_l, _wtof, _wtof_l](atof-atof-l-wtof-wtof-l.md)<br/>
[_ecvt_s](ecvt-s.md)<br/>
[_fcvt_s](fcvt-s.md)<br/>
[_gcvt](gcvt.md)<br/>
