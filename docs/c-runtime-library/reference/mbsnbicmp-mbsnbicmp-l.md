---
title: _mbsnbicmp, _mbsnbicmp_l | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _mbsnbicmp_l
- _mbsnbicmp
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
- api-ms-win-crt-multibyte-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _strnicmp
- _wcsnicmp_l
- _mbsnbicmp
- mbsnbicmp
- mbsnbicmp_l
- _tcsnicmp
- _strnicmp_l
- _tcsnicmp_l
- _wcsnicmp
- _mbsnbicmp_l
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 15038e42b87a9803312df79eb5d235f1add51669
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32405014"
---
# <a name="mbsnbicmp-mbsnbicmpl"></a>_mbsnbicmp, _mbsnbicmp_l

Compare **n** octets de caractères multioctets deux chaînes et ignore la casse.

> [!IMPORTANT]
> Cette API ne peut pas être utilisée dans les applications qui s’exécutent dans le Windows Runtime. Pour plus d’informations, consultez [Fonctions CRT non prises en charge dans les applications de la plateforme Windows universelle](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntaxe

```C
int _mbsnbicmp(
   const unsigned char *string1,
   const unsigned char *string2,
   size_t count
);
```

### <a name="parameters"></a>Paramètres

*string1*, *chaîne2*<br/>
Chaîne terminée par Null à comparer.

*count*<br/>
Nombre d'octets à comparer.

## <a name="return-value"></a>Valeur de retour

La valeur de retour indique la relation entre les sous-chaînes.

|Valeur de retour|Description|
|------------------|-----------------|
|< 0|*string1* sous-chaîne moins *chaîne2* sous-chaîne.|
|0|*string1* sous-chaîne identique à *chaîne2* sous-chaîne.|
|> 0|*string1* sous-chaîne supérieur *chaîne2* sous-chaîne.|

En cas d’erreur, **_mbsnbicmp** retourne **_NLSCMPERROR**, qui est défini dans String.h et Mbstring.h.

## <a name="remarks"></a>Notes

Le **_mbsnbicmp** fonction effectue une comparaison ordinale du premier au plus *nombre* octets de *string1* et *chaîne2*. La comparaison est effectuée en convertissant chaque caractère en minuscule ; [_mbsnbcmp](mbsnbcmp-mbsnbcmp-l.md) est une version respectant la casse de **_mbsnbicmp**. La comparaison se termine si un caractère null de fin est atteint dans une chaîne avant *nombre* caractères soient comparés. Si les chaînes sont égales quand un caractère null de fin est atteinte dans chaîne avant *nombre* caractères soient comparés, la chaîne courte est moindre.

**_mbsnbicmp** est similaire à [_mbsnbcmp](mbsnbcmp-mbsnbcmp-l.md), à ceci près qu’elle compare des chaînes jusqu'à *nombre* octets au lieu de caractères.

La comparaison de deux chaînes contenant des caractères qui se trouvent entre « Z » et « a » dans la table ASCII (« [ », « \\ », « ] », « ^ », « _ » et « \` ») donne des résultats différents selon leur casse. Par exemple, les deux chaînes « ABCDE » et « ABCD ^ « comparer une façon si la comparaison est en minuscule (« abcde » > « abcd ^ ») et l’autre sens (« ABCDE » < « ABCD ^ ») si elle est en majuscule.

**_mbsnbicmp** reconnaît les séquences de caractères multioctets en fonction de la [page de codes multioctets](../../c-runtime-library/code-pages.md) en cours d’utilisation. Elle n'est pas affectée par les paramètres régionaux actuels.

Si le paramètre *string1* ou *chaîne2* est un pointeur null, **_mbsnbicmp** appelle le Gestionnaire de paramètres non valides, comme décrit dans [Validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, la fonction retourne **_NLSCMPERROR** et définit **errno** à **EINVAL**.

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine Tchar.h|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tcsnicmp**|**_strnicmp**|**_mbsnbicmp**|**_wcsnicmp**|
|**_tcsnicmp_l**|**_strnicmp_l**|**_mbsnbicmp_l**|**_wcsnicmp_l**|

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**_mbsnbicmp**|<mbstring.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

Consultez l’exemple relatif à [_mbsnbcmp, _mbsnbcmp_l](mbsnbcmp-mbsnbcmp-l.md).

## <a name="see-also"></a>Voir aussi

[Manipulation de chaînes](../../c-runtime-library/string-manipulation-crt.md)<br/>
[_mbsnbcat, _mbsnbcat_l](mbsnbcat-mbsnbcat-l.md)<br/>
[_mbsnbcmp, _mbsnbcmp_l](mbsnbcmp-mbsnbcmp-l.md)<br/>
[_stricmp, _wcsicmp, _mbsicmp, _stricmp_l, _wcsicmp_l, _mbsicmp_l](stricmp-wcsicmp-mbsicmp-stricmp-l-wcsicmp-l-mbsicmp-l.md)<br/>
