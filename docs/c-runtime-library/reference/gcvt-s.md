---
title: _gcvt_s | Microsoft Docs
ms.custom: ''
ms.date: 04/05/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _gcvt_s
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
- _gcvt_s
- gcvt_s
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0a2bd12a63db064bca0c880484f99a2df9d210f8
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32403766"
---
# <a name="gcvts"></a>_gcvt_s

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

Zéro si l’opération réussit. En cas d’échec en raison d’un paramètre non valide (voir le tableau ci-après pour découvrir les valeurs non valides), le gestionnaire de paramètres non valides est appelé, comme décrit dans [Validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, un code d’erreur est retourné. Les codes d’erreur sont définis dans Errno.h. Pour obtenir la liste de ces erreurs, consultez [errno, _doserrno, _sys_errlist et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

### <a name="error-conditions"></a>Conditions d’erreur

|*buffer*|*sizeInBytes*|*valeur*|*digits*|Retourner|Valeur de *tampon*|
|--------------|-------------------|-------------|--------------|------------|-----------------------|
|**NULL**|any|any|any|**EINVAL**|Non modifiée.|
|Pas **NULL** (pointe vers une mémoire valide)|zéro|any|any|**EINVAL**|Non modifiée.|
|Pas **NULL** (pointe vers une mémoire valide)|any|any|>= *sizeInBytes*|**EINVAL**|Non modifiée.|

**Problèmes de sécurité**

**_gcvt_s** peut générer une violation d’accès si *tampon* ne pointe pas vers la mémoire valide et n’est pas **NULL**.

## <a name="remarks"></a>Notes

Le **_gcvt_s** fonction convertit une virgule flottante *valeur* en une chaîne de caractères (qui inclut une virgule décimale et un octet de connexion possibles) et stocke la chaîne dans *tampon* . *mémoire tampon* doit être suffisamment grand pour contenir la valeur convertie plus un caractère null de fin est ajouté automatiquement. Une mémoire tampon de longueur **_CVTBUFSIZE** est suffisant pour n’importe quel flottante valeur du point. Si une taille de mémoire tampon de *chiffres* + 1 est utilisé, la fonction ne remplace pas la fin de la mémoire tampon, par conséquent, veillez à fournir une mémoire tampon suffisante pour cette opération. **_gcvt_s** tente de se produire *chiffres* chiffres au format décimal. Si elle n’est pas le cas, il produit *chiffres* chiffres au format exponentiel. Les zéros de fin peuvent être supprimés pendant la conversion.

En C++, l’utilisation de cette fonction est simplifiée par une surcharge de modèle ; la surcharge peut déduire automatiquement la longueur de la mémoire tampon, ce qui évite d’avoir à spécifier un argument de taille. Pour plus d'informations, consultez [Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md).

La version de débogage de cette fonction remplit d’abord la mémoire tampon avec 0xFD. Pour désactiver ce comportement, utilisez [_CrtSetDebugFillThreshold](crtsetdebugfillthreshold.md).

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|En-tête facultatif|
|-------------|---------------------|---------------------|
|**_gcvt_s**|\<stdlib.h>|\<error.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

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
