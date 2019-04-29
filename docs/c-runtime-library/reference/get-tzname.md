---
title: _get_tzname
ms.date: 10/22/2018
apiname:
- _get_tzname
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
- api-ms-win-crt-time-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _get_tzname
- get_tzname
helpviewer_keywords:
- _get_tzname function
- time zones
- get_tzname function
ms.assetid: df0065ff-095f-4237-832c-2fe9ab913875
ms.openlocfilehash: c173832efb866eed133a908b5f2b72266fd3798a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62332038"
---
# <a name="gettzname"></a>_get_tzname

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
La longueur de chaîne de *NomFuseauhoraire* , y compris une marque de fin null.

*timeZoneName*<br/>
L’adresse d’une chaîne de caractères pour la représentation du nom du fuseau horaire ou le nom du fuseau horaire d’été (DST), en fonction de *index*.

*sizeInBytes*<br/>
La taille de la *NomFuseauhoraire* chaîne en octets de caractères.

*index*<br/>
Index d’un des deux noms de fuseaux horaires à récupérer.

|*index*|Contenu de *NomFuseauhoraire*|*NomFuseauhoraire* valeur par défaut|
|-|-|-|
|0|Nom du fuseau horaire|« PST »|
|1|Nom du fuseau horaire d’hiver|« PDT »|
|> 1 ou < 0|**errno** la valeur **EINVAL**|non modifié|

À moins que les valeurs soient explicitement modifiées pendant l’exécution, les valeurs par défaut sont respectivement « PST » et « PDT ».

## <a name="return-value"></a>Valeur de retour

Zéro en cas de réussite, sinon une **errno** type valeur.

Si *NomFuseauhoraire* est **NULL**, ou *sizeInBytes* est égal à zéro ou inférieure à zéro (mais pas les deux), un gestionnaire de paramètre non valide est appelé, comme décrit dans [ Validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, cette fonction affecte **errno** à **EINVAL** et retourne **EINVAL**.

### <a name="error-conditions"></a>Conditions d’erreur

|*pReturnValue*|*timeZoneName*|*sizeInBytes*|*index*|Valeur de retour|Contenu de *NomFuseauhoraire*|
|--------------------|--------------------|-------------------|-------------|------------------|--------------------------------|
|Taille du nom du fuseau horaire|**NULL**|0|0 ou 1|0|non modifié|
|Taille du nom du fuseau horaire|any|> 0|0 ou 1|0|Nom du fuseau horaire|
|non modifié|**NULL**|> 0|any|**EINVAL**|non modifié|
|non modifié|any|zéro|any|**EINVAL**|non modifié|
|non modifié|any|> 0|> 1|**EINVAL**|non modifié|

## <a name="remarks"></a>Notes

Le **_get_tzname** fonction récupère la représentation de chaîne de caractères du nom fuseau horaire actuel ou le nom du fuseau horaire d’été (DST) dans l’adresse de *NomFuseauhoraire* en fonction de la index de valeur, ainsi que la taille de la chaîne dans *pReturnValue*. Si *NomFuseauhoraire* est **NULL** et *sizeInBytes* est zéro, la taille de la chaîne nécessaire pour contenir le fuseau horaire spécifié et une caractère null de fin en octets est retournée dans *pReturnValue*. Les valeurs d’index doivent être 0 pour le fuseau horaire standard ou 1 pour le fuseau horaire de l’heure d’été ; toutes les autres valeurs de *index* ont des résultats indéterminés.

## <a name="example"></a>Exemple

Cet exemple appelle **_get_tzname** pour obtenir la taille de mémoire tampon requise pour afficher le nom de zone actuel l’heure d’été heure d’hiver, alloue une mémoire tampon de cette taille, les appels **_get_tzname** à nouveau pour charger le nom dans le mettre en mémoire tampon et l’imprime sur la console.

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

### <a name="output"></a>Sortie

```Output
The current Daylight standard time zone name is PDT.
```

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis|
|-------------|---------------------|
|**_get_tzname**|\<time.h>|

Pour plus d'informations, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[Gestion du temps](../../c-runtime-library/time-management.md)<br/>
[errno, _doserrno, _sys_errlist et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)<br/>
[_get_daylight](get-daylight.md)<br/>
[_get_dstbias](get-dstbias.md)<br/>
[_get_timezone](get-timezone.md)<br/>
