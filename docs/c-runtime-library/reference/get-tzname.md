---
title: _get_tzname | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- _get_tzname function
- time zones
- get_tzname function
ms.assetid: df0065ff-095f-4237-832c-2fe9ab913875
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a4b49aa404dda6234382ae461459dece64e5996d
ms.sourcegitcommit: 6e3cf8df676d59119ce88bf5321d063cf479108c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/22/2018
ms.locfileid: "34451691"
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
La longueur de chaîne *NomFuseauhoraire* , y compris un terminateur null.

*NomFuseauhoraire*<br/>
L’adresse d’une chaîne de caractères pour la représentation sous forme de nom du fuseau horaire ou le nom de zone de l’heure d’hiver l’heure d’été (DST), en fonction de *index*.

*sizeInBytes*<br/>
La taille de la *NomFuseauhoraire* chaîne en octets de caractères.

*index*<br/>
Index d’un des deux noms de fuseaux horaires à récupérer.

## <a name="return-value"></a>Valeur de retour

Zéro en cas de réussite, sinon un **errno** type valeur.

Si le paramètre *NomFuseauhoraire* est **NULL**, ou *sizeInBytes* est égal à zéro ou inférieur à zéro (mais pas les deux), un gestionnaire de paramètre non valide est appelé, comme décrit dans [ Validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, cette fonction affecte **errno** à **EINVAL** et retourne **EINVAL**.

### <a name="error-conditions"></a>Conditions d’erreur

|*pReturnValue*|*NomFuseauhoraire*|*sizeInBytes*|*index*|Valeur de retour|Contenu de *NomFuseauhoraire*|
|--------------------|--------------------|-------------------|-------------|------------------|--------------------------------|
|Taille du nom du fuseau horaire|**NULL**|0|0 ou 1|0|non modifié|
|Taille du nom du fuseau horaire|any|> 0|0 ou 1|0|Nom du fuseau horaire|
|non modifié|**NULL**|> 0|any|**EINVAL**|non modifié|
|non modifié|any|zéro|any|**EINVAL**|non modifié|
|non modifié|any|> 0|> 1|**EINVAL**|non modifié|

## <a name="remarks"></a>Notes

Le **_get_tzname** fonction récupère la représentation de chaîne de caractères du nom fuseau horaire ou le nom de zone de l’heure d’hiver l’heure d’été (DST) dans l’adresse de *NomFuseauhoraire* en fonction de l’index valeur, ainsi que la taille de la chaîne de *pReturnValue*. Si *NomFuseauhoraire* est **NULL** et *sizeInBytes* est égal à zéro, simplement la taille de la chaîne d’heure zone en octets est retourné dans *pReturnValue*. La valeur d’index doit être 0 (fuseau horaire standard) ou 1 (fuseau horaire d’été) ; toute autre valeur d’index engendre des résultats indéterminés.

### <a name="index-values"></a>Valeurs d’index

|*index*|Contenu de *NomFuseauhoraire*|*NomFuseauhoraire* valeur par défaut|
|-------------|--------------------------------|----------------------------------|
|0|Nom du fuseau horaire|« PST »|
|1|Nom du fuseau horaire d’hiver|« PDT »|
|> 1 ou < 0|**errno** la valeur **EINVAL**|non modifié|

À moins que les valeurs soient explicitement modifiées pendant l’exécution, les valeurs par défaut sont respectivement « PST » et « PDT ».  Les tailles de ces tableaux de caractères sont régies par **TZNAME_MAX** valeur.

## <a name="requirements"></a>Spécifications

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
[TZNAME_MAX](../../c-runtime-library/tzname-max.md)<br/>
