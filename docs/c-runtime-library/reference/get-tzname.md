---
title: _get_tzname
ms.date: 4/2/2020
api_name:
- _get_tzname
- _o__get_tzname
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
- api-ms-win-crt-time-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _get_tzname
- get_tzname
helpviewer_keywords:
- _get_tzname function
- time zones
- get_tzname function
ms.assetid: df0065ff-095f-4237-832c-2fe9ab913875
ms.openlocfilehash: 50f1f6e4320e3ef905b4eda67ba1d458a5b1df08
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81344874"
---
# <a name="_get_tzname"></a>_get_tzname

Récupère la représentation sous forme de chaîne de caractères du nom du fuseau horaire standard ou du nom du fuseau horaire d’été (DST).

## <a name="syntax"></a>Syntaxe

```C
errno_t _get_tzname(
    size_t* pReturnValue,
    char* timeZoneName,
    size_t sizeInBytes,
    int index
);
```

### <a name="parameters"></a>Paramètres

*pReturnValue*<br/>
La durée de la *chaîneZoneName* y compris un terminateur nul.

*timeZoneName timeZoneName*<br/>
L’adresse d’une chaîne de caractère pour la représentation du nom du fuseau horaire ou le nom du fuseau horaire standard de jour (DST), selon *l’index*.

*sizeInBytes*<br/>
La taille de la chaîne de caractère *timeZoneName* dans les octets.

*index*<br/>
Index d’un des deux noms de fuseaux horaires à récupérer.

|*index*|Contenu de *timeZoneName*|*timeZoneName* valeur par défaut|
|-|-|-|
|0|Nom du fuseau horaire|« PST »|
|1|Nom du fuseau horaire d’hiver|« PDT »|
|> 1 ou < 0|**errno** réglé à **EINVAL**|non modifié|

À moins que les valeurs soient explicitement modifiées pendant l’exécution, les valeurs par défaut sont respectivement « PST » et « PDT ».

## <a name="return-value"></a>Valeur de retour

Zéro en cas de succès, sinon une valeur de type **errno.**

Si l’un ou l’autre *timeZoneName* est **NULL**, ou *sizeInBytes* est zéro ou moins que zéro (mais pas les deux), un gestionnaire de paramètre invalide est invoqué, comme décrit dans [la validation de paramètres](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, cette fonction définit **errno** à **EINVAL** et retourne **EINVAL**.

### <a name="error-conditions"></a>Conditions d'erreur

|*pReturnValue*|*timeZoneName timeZoneName*|*sizeInBytes*|*index*|Valeur retournée|Contenu de *timeZoneName*|
|--------------------|--------------------|-------------------|-------------|------------------|--------------------------------|
|Taille du nom du fuseau horaire|**Null**|0|0 ou 1|0|non modifié|
|Taille du nom du fuseau horaire|n'importe laquelle|> 0|0 ou 1|0|Nom du fuseau horaire|
|non modifié|**Null**|> 0|n'importe laquelle|**EINVAL (EN)**|non modifié|
|non modifié|n'importe laquelle|zéro|n'importe laquelle|**EINVAL (EN)**|non modifié|
|non modifié|n'importe laquelle|> 0|> 1|**EINVAL (EN)**|non modifié|

## <a name="remarks"></a>Notes

La fonction **_get_tzname** récupère la représentation de la chaîne de caractères du nom actuel du fuseau horaire ou du nom du fuseau horaire standard de la lumière du jour (DST) dans l’adresse de *timeZoneName* en fonction de la valeur de l’indice, ainsi que la taille de la chaîne dans *pReturnValue*. Si *timeZoneName* est **NULL** et *sizeInBytes* est nul, la taille de la chaîne requise pour tenir le fuseau horaire spécifié et une date de non dans les octets est retournée dans *pReturnValue*. Les valeurs de l’indice doivent être soit 0 pour le fuseau horaire standard ou 1 pour le fuseau horaire standard de jour; toutes les autres valeurs de *l’indice* ont des résultats indéterminés.

Par défaut, l’état global de cette fonction est étendue à l’application. Pour changer cela, voir [Global State dans le CRT](../global-state.md).

## <a name="example"></a>Exemple

Cet exemple appelle **_get_tzname** pour obtenir la taille du tampon requis pour afficher le nom actuel du fuseau horaire standard Daylight, alloue un tampon de cette taille, appelle **_get_tzname** à nouveau pour charger le nom dans le tampon, et l’imprime à la console.

```C
// crt_get_tzname.c
// Compile by using: cl /W4 crt_get_tzname.c
#include <stdio.h>
#include <time.h>
#include <malloc.h>

enum TZINDEX {
    STD,
    DST
};

int main()
{
    size_t tznameSize = 0;
    char * tznameBuffer = NULL;

    // Get the size of buffer required to hold DST time zone name
    if (_get_tzname(&tznameSize, NULL, 0, DST))
        return 1;    // Return an error value if it failed

    // Allocate a buffer for the name
    if (NULL == (tznameBuffer = (char *)(malloc(tznameSize))))
        return 2;    // Return an error value if it failed

    // Load the name in the buffer
    if (_get_tzname(&tznameSize, tznameBuffer, tznameSize, DST))
        return 3;    // Return an error value if it failed

    printf_s("The current Daylight standard time zone name is %s.\n", tznameBuffer);
    return 0;
}
```

### <a name="output"></a>Output

```Output
The current Daylight standard time zone name is PDT.
```

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**_get_tzname**|\<time.h>|

Pour plus d’informations, consultez [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[Gestion du temps](../../c-runtime-library/time-management.md)<br/>
[errno, _doserrno, _sys_errlist et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)<br/>
[_get_daylight](get-daylight.md)<br/>
[_get_dstbias](get-dstbias.md)<br/>
[_get_timezone](get-timezone.md)<br/>
