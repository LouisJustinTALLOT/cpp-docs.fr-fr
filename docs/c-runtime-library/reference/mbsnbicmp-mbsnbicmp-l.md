---
title: _mbsnbicmp, _mbsnbicmp_l
ms.date: 4/2/2020
api_name:
- _mbsnbicmp_l
- _mbsnbicmp
- _o__mbsnbicmp
- _o__mbsnbicmp_l
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
- api-ms-win-crt-multibyte-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _mbsnbicmp
- mbsnbicmp
- mbsnbicmp_l
- _mbsnbicmp_l
helpviewer_keywords:
- _tcsnicmp_l function
- _strnicmp function
- mbsnbicmp_l function
- _wcsnicmp_l function
- _mbsnbicmp function
- _mbsnbicmp_l function
- _tcsnicmp function
- _strnicmp_l function
- mbsnbicmp function
- _wcsnicmp function
ms.assetid: ddb44974-8b0c-42f0-90d0-56c9350bae0c
ms.openlocfilehash: 80d2708396cdaeb86c25932c3d13129fb318719a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81340575"
---
# <a name="_mbsnbicmp-_mbsnbicmp_l"></a>_mbsnbicmp, _mbsnbicmp_l

Compare **les octets n** de deux cordes multioctets et ignore le cas.

> [!IMPORTANT]
> Cette API ne peut pas être utilisée dans les applications qui s'exécutent dans le Windows Runtime. Pour plus d’informations, consultez [Fonctions CRT non prises en charge dans les applications de la plateforme Windows universelle](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntaxe

```C
int _mbsnbicmp(
   const unsigned char *string1,
   const unsigned char *string2,
   size_t count
);
```

### <a name="parameters"></a>Paramètres

*string1*, *string2*<br/>
Chaîne terminée par Null à comparer.

*count*<br/>
Nombre d'octets à comparer.

## <a name="return-value"></a>Valeur de retour

La valeur de retour indique la relation entre les sous-chaînes.

|Valeur retournée|Description|
|------------------|-----------------|
|< 0|*chaîne1* sous-corde moins que le sous-corde *string2.*|
|0|*sous-corde de chaîne1* identique au sous-corde *string2.*|
|> 0|*sous-corde de chaîne1* plus grande que le sous-corde *string2.*|

Sur une erreur, **_mbsnbicmp** retourne **_NLSCMPERROR**, qui est défini dans String.h et Mbstring.h.

## <a name="remarks"></a>Notes

La fonction **_mbsnbicmp** effectue une comparaison ordinaire des octets de *premier compte* de *string1* et *string2*. La comparaison est effectuée en convertissant chaque personnage en lowercase; [_mbsnbcmp](mbsnbcmp-mbsnbcmp-l.md) est une version sensible aux cas de **_mbsnbicmp**. La comparaison se termine si un caractère nul de fin est atteint dans l’une ou l’autre chaîne avant que les caractères *de comptage* soient comparés. Si les cordes sont égales lorsqu’un caractère nul de fin est atteint dans l’une ou l’autre chaîne avant que les caractères *de comptage* soient comparés, la chaîne plus courte est moindre.

**_mbsnbicmp** est similaire à [_mbsnbcmp](mbsnbcmp-mbsnbcmp-l.md), sauf qu’il compare les cordes jusqu’à *compter* les octets au lieu de par les personnages.

La comparaison de deux chaînes contenant des caractères qui se trouvent entre « Z » et « a » dans la table ASCII (« [ », « \\ », « ] », « ^ », « _ » et « \` ») donne des résultats différents selon leur casse. Par exemple, les deux chaînes "ABCDE" et "ABCD" comparer d’une façon si la comparaison est inférieure ("abcde" > "abcd") et dans l’autre sens ("ABCDE" < "ABCD") si elle est majuscule.

**_mbsnbicmp** reconnaît les séquences multioctets selon la [page de code multioctet](../../c-runtime-library/code-pages.md) actuellement en service. Elle n'est pas affectée par les paramètres régionaux actuels.

Si *la chaîne1* ou *la chaîne2* est un pointeur nul, **_mbsnbicmp** invoque le gestionnaire de paramètres invalide tel que décrit dans [la validation de paramètres](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, la fonction renvoie **_NLSCMPERROR** et définit **errno** à **EINVAL**.

Par défaut, l’état global de cette fonction est étendue à l’application. Pour changer cela, voir [Global State dans le CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine Tchar.h|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tcsnicmp**|**_strnicmp**|**_mbsnbicmp**|**_wcsnicmp**|
|**_tcsnicmp_l**|**_strnicmp_l**|**_mbsnbicmp_l**|**_wcsnicmp_l**|

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**_mbsnbicmp**|\<mbstring.h>|

Pour plus d’informations sur la compatibilité, consultez [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

Consultez l’exemple relatif à [_mbsnbcmp, _mbsnbcmp_l](mbsnbcmp-mbsnbcmp-l.md).

## <a name="see-also"></a>Voir aussi

[Manipulation des cordes](../../c-runtime-library/string-manipulation-crt.md)<br/>
[_mbsnbcat, _mbsnbcat_l](mbsnbcat-mbsnbcat-l.md)<br/>
[_mbsnbcmp, _mbsnbcmp_l](mbsnbcmp-mbsnbcmp-l.md)<br/>
[_stricmp, _wcsicmp, _mbsicmp, _stricmp_l, _wcsicmp_l, _mbsicmp_l](stricmp-wcsicmp-mbsicmp-stricmp-l-wcsicmp-l-mbsicmp-l.md)<br/>
