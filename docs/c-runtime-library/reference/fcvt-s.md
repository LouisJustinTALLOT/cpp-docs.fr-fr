---
title: _fcvt_s
ms.date: 4/2/2020
api_name:
- _fcvt_s
- _o__fcvt_s
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
- fcvt_s
- _fcvt_s
helpviewer_keywords:
- fcvt_s function
- converting floating point, to strings
- floating-point functions, converting number to string
- _fcvt_s function
ms.assetid: 48671197-1d29-4c2b-a5d8-d2368f5f68a1
ms.openlocfilehash: 80f02467e160e3196982c10576ad55f5487e5fc1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81347456"
---
# <a name="_fcvt_s"></a>_fcvt_s

Convertir un nombre à virgule flottante en chaîne. Il s’agit d’une version de [_fcvt](fcvt.md) assortie des améliorations de sécurité décrites dans [Fonctionnalités de sécurité dans le CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Syntaxe

```C
errno_t _fcvt_s(
   char* buffer,
   size_t sizeInBytes,
   double value,
   int count,
   int *dec,
   int *sign
);
template <size_t size>
errno_t _fcvt_s(
   char (&buffer)[size],
   double value,
   int count,
   int *dec,
   int *sign
); // C++ only
```

### <a name="parameters"></a>Paramètres

*buffer*<br/>
La mémoire tampon fournie destinée à contenir le résultat de la conversion.

*sizeInBytes*<br/>
Taille de la mémoire tampon en octets.

*value*<br/>
Nombre à convertir.

*count*<br/>
Nombre de chiffres après la virgule décimale.

*dec*<br/>
Pointeur désignant la position de la virgule décimale stockée.

*sign*<br/>
Pointeur désignant l’indicateur de signe stocké.

## <a name="return-value"></a>Valeur de retour

Zéro si l’opération réussit. En cas d’échec, la valeur de retour est un code d’erreur. Les codes d’erreur sont définis dans Errno.h. Pour obtenir la liste de ces erreurs, consultez [errno, _doserrno, _sys_errlist et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

En cas de paramètre non valide, comme indiqué dans le tableau suivant, cette fonction appelle le gestionnaire de paramètres non valides, comme décrit dans [Validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, cette fonction définit **errno** à **EINVAL** et retourne **EINVAL**.

### <a name="error-conditions"></a>Conditions d'erreur

|*buffer*|*sizeInBytes*|value|count|dec|sign|Renvoie|Valeur dans *le tampon*|
|--------------|-------------------|-----------|-----------|---------|----------|------------|-----------------------|
|**Null**|n'importe laquelle|n'importe laquelle|n'importe laquelle|n'importe laquelle|n'importe laquelle|**EINVAL (EN)**|Non modifiée.|
|Non **NULL** (points à la mémoire valide)|<=0|n'importe laquelle|n'importe laquelle|n'importe laquelle|n'importe laquelle|**EINVAL (EN)**|Non modifiée.|
|n'importe laquelle|n'importe laquelle|n'importe laquelle|n'importe laquelle|**Null**|n'importe laquelle|**EINVAL (EN)**|Non modifiée.|
|n'importe laquelle|n'importe laquelle|n'importe laquelle|n'importe laquelle|n'importe laquelle|**Null**|**EINVAL (EN)**|Non modifiée.|

## <a name="security-issues"></a>Problèmes de sécurité

**_fcvt_s** peut générer une violation d’accès si *le tampon* ne pointe pas vers la mémoire valide et n’est pas **NULL**.

## <a name="remarks"></a>Notes

La fonction **_fcvt_s** convertit un numéro de point flottant en une chaîne de caractères à bout de terminaisons nulles. Le paramètre de *valeur* est le nombre de points flottants à convertir. **_fcvt_s** stocke les chiffres de la *valeur* comme une chaîne et appende un caractère nul ('0'). Le *paramètre de comptage* spécifie le nombre de chiffres à stocker après le point décimal. Les chiffres excédentaires sont arrondis pour *compter* les endroits. S’il y a moins de chiffres de *précision,* la corde est rembourrée avec des zéros.

Seuls des chiffres sont stockés dans la chaîne. La position du point décimal et le signe de *valeur* peuvent être obtenus à partir de *déc* et *signe après* l’appel. Le paramètre *déc* indique une valeur integer; cette valeur integer donne la position du point décimal par rapport au début de la chaîne. Une valeur entière ou zéro indique que la virgule décimale est située à gauche du premier chiffre. Le *signe de* paramètre indique un intégrant indiquant le signe de *valeur*. L’intégrateur est réglé à 0 si *la valeur* est positive et est réglé à un nombre non zéro si *la valeur* est négative.

Un tampon de longueur **_CVTBUFSIZE** est suffisant pour toute valeur de point flottant.

La différence entre **_ecvt_s** et **_fcvt_s** réside dans l’interprétation du paramètre de *comptage.* **_ecvt_s** interprète *le* nombre total de chiffres dans la chaîne de sortie, et **_fcvt_s** interprète le *nombre* de chiffres après le point décimal.

En C++, l’utilisation de cette fonction est simplifiée par une surcharge de modèle ; la surcharge peut déduire automatiquement la longueur de la mémoire tampon, ce qui évite d’avoir à spécifier un argument de taille. Pour plus d’informations, consultez [Sécuriser les surcharges de modèle](../../c-runtime-library/secure-template-overloads.md).

La version de débogé de cette fonction remplit d’abord le tampon avec 0xFE. Pour désactiver ce comportement, utilisez [_CrtSetDebugFillThreshold](crtsetdebugfillthreshold.md).

Par défaut, l’état global de cette fonction est étendue à l’application. Pour changer cela, voir [Global State dans le CRT](../global-state.md).

## <a name="requirements"></a>Spécifications

|Fonction|En-tête requis|En-tête facultatif|
|--------------|---------------------|---------------------|
|**_fcvt_s**|\<stdlib.h>|\<errno.h>|

Pour plus d’informations sur la compatibilité, consultez [Compatibility](../../c-runtime-library/compatibility.md).

**Bibliothèques :** toutes les versions des [fonctionnalités de bibliothèque CRT](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Exemple

```C
// fcvt_s.c
#include <stdio.h>
#include <stdlib.h>
#include <errno.h>

int main()
{
    char * buf = 0;
    int decimal;
    int sign;
    int err;

    buf = (char*) malloc(_CVTBUFSIZE);
    err = _fcvt_s(buf, _CVTBUFSIZE, 1.2, 5, &decimal, &sign);

    if (err != 0)
    {
        printf("_fcvt_s failed with error code %d\n", err);
        exit(1);
    }

    printf("Converted value: %s\n", buf);
}
```

```Output
Converted value: 120000
```

## <a name="see-also"></a>Voir aussi

[Conversion de données](../../c-runtime-library/data-conversion.md)<br/>
[Soutien à la pointe flottante](../../c-runtime-library/floating-point-support.md)<br/>
[atof, _atof_l, _wtof, _wtof_l](atof-atof-l-wtof-wtof-l.md)<br/>
[_ecvt_s](ecvt-s.md)<br/>
[_gcvt_s](gcvt-s.md)<br/>
[_fcvt](fcvt.md)<br/>
