---
description: 'En savoir plus sur : _fcvt_s'
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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: dd4d58b39d4c18f2fff7da54c5fbd0f2346dfdd4
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97235877"
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

*mémoire tampon*<br/>
La mémoire tampon fournie destinée à contenir le résultat de la conversion.

*sizeInBytes*<br/>
Taille de la mémoire tampon en octets.

*value*<br/>
Nombre à convertir.

*count*<br/>
Nombre de chiffres après la virgule décimale.

*decembre*<br/>
Pointeur désignant la position de la virgule décimale stockée.

*sign*<br/>
Pointeur désignant l’indicateur de signe stocké.

## <a name="return-value"></a>Valeur renvoyée

Zéro si l’opération réussit. En cas d’échec, la valeur de retour est un code d’erreur. Les codes d’erreur sont définis dans Errno.h. Pour obtenir la liste de ces erreurs, consultez [errno, _doserrno, _sys_errlist et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

En cas de paramètre non valide, comme indiqué dans le tableau suivant, cette fonction appelle le gestionnaire de paramètres non valides, comme décrit dans [Validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, cette fonction affecte à **errno** la valeur **EINVAL** et retourne **EINVAL**.

### <a name="error-conditions"></a>Conditions d'erreur

|*mémoire tampon*|*sizeInBytes*|value|count|dec|sign|Renvoie|Valeur dans la *mémoire tampon*|
|--------------|-------------------|-----------|-----------|---------|----------|------------|-----------------------|
|**NULL**|n'importe laquelle|n'importe laquelle|n'importe laquelle|n'importe laquelle|n'importe laquelle|**EINVAL**|Non modifiée.|
|Not **null** (pointe vers une mémoire valide)|<=0|n'importe laquelle|n'importe laquelle|n'importe laquelle|n'importe laquelle|**EINVAL**|Non modifiée.|
|n'importe laquelle|n'importe laquelle|n'importe laquelle|n'importe laquelle|**NULL**|n'importe laquelle|**EINVAL**|Non modifiée.|
|n'importe laquelle|n'importe laquelle|n'importe laquelle|n'importe laquelle|n'importe laquelle|**NULL**|**EINVAL**|Non modifiée.|

## <a name="security-issues"></a>Problèmes de sécurité

**_fcvt_s** peut générer une violation d’accès si la *mémoire tampon* ne pointe pas vers une mémoire valide et n’a pas la **valeur null**.

## <a name="remarks"></a>Notes

La fonction **_fcvt_s** convertit un nombre à virgule flottante en une chaîne de caractères terminée par le caractère null. Le paramètre de *valeur* est le nombre à virgule flottante à convertir. **_fcvt_s** stocke les chiffres de *valeur* sous forme de chaîne et ajoute un caractère null (' \ 0 '). Le paramètre *Count* spécifie le nombre de chiffres à stocker après la virgule décimale. Les chiffres excédentaires sont arrondis à la *valeur nombre* d’emplacements. Si le *nombre* de chiffres de précision est inférieur à, la chaîne est remplie de zéros.

Seuls des chiffres sont stockés dans la chaîne. La position de la virgule décimale et le signe de la *valeur* peuvent être obtenus à partir de *Dec* et du *signe* après l’appel. Le paramètre *Dec* pointe sur une valeur entière ; Cette valeur entière indique la position de la virgule décimale par rapport au début de la chaîne. Une valeur entière ou zéro indique que la virgule décimale est située à gauche du premier chiffre. Le paramètre *signe* pointe sur un entier indiquant le signe de la *valeur*. L’entier est défini sur 0 si la *valeur* est positive et est définie sur un nombre différent de zéro si la *valeur* est négative.

Une mémoire tampon de longueur **_CVTBUFSIZE** est suffisante pour toute valeur à virgule flottante.

La différence entre **_ecvt_s** et **_fcvt_s** est l’interprétation du paramètre *Count* . **_ecvt_s** interprète le *nombre comme le* nombre total de chiffres dans la chaîne de sortie, et **_fcvt_s** interprète le nombre comme le *nombre de* chiffres après la virgule décimale.

En C++, l’utilisation de cette fonction est simplifiée par une surcharge de modèle ; la surcharge peut déduire automatiquement la longueur de la mémoire tampon, ce qui évite d’avoir à spécifier un argument de taille. Pour plus d’informations, consultez [Sécuriser les surcharges de modèle](../../c-runtime-library/secure-template-overloads.md).

La version de débogage de cette fonction remplit d’abord la mémoire tampon avec 0xFE. Pour désactiver ce comportement, utilisez [_CrtSetDebugFillThreshold](crtsetdebugfillthreshold.md).

Par défaut, l’état global de cette fonction est limité à l’application. Pour modifier cette valeur, consultez [état global dans le CRT](../global-state.md).

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
[Prise en charge de la virgule flottante](../../c-runtime-library/floating-point-support.md)<br/>
[atof, _atof_l, _wtof, _wtof_l](atof-atof-l-wtof-wtof-l.md)<br/>
[_ecvt_s](ecvt-s.md)<br/>
[_gcvt_s](gcvt-s.md)<br/>
[_fcvt](fcvt.md)<br/>
