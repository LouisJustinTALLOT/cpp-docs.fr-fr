---
title: _mbsnbicmp, _mbsnbicmp_l
ms.date: 11/04/2016
api_name:
- _mbsnbicmp_l
- _mbsnbicmp
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
api_type:
- DLLExport
topic_type:
- apiref
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
ms.openlocfilehash: 19ffa4c47f0144ba136607fe5cef09e9bd65374f
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70952190"
---
# <a name="_mbsnbicmp-_mbsnbicmp_l"></a>_mbsnbicmp, _mbsnbicmp_l

Compare **n** octets de deux chaînes de caractères multioctets et ignore la casse.

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

*string1*, *string2*<br/>
Chaîne terminée par Null à comparer.

*count*<br/>
Nombre d'octets à comparer.

## <a name="return-value"></a>Valeur de retour

La valeur de retour indique la relation entre les sous-chaînes.

|Valeur de retour|Description|
|------------------|-----------------|
|< 0|*Chaîne1* sous-chaîne inférieure à *Chaîne2* sous-chaîne.|
|0|*Chaîne1* sous-chaîne identique à la sous-chaîne *Chaîne2* .|
|> 0|*Chaîne1* SUBSTRING supérieure à la sous-chaîne *Chaîne2* .|

En cas d’erreur, **_mbsnbicmp** retourne **_NLSCMPERROR**, qui est défini dans String. h et mbstring. h.

## <a name="remarks"></a>Notes

La fonction **_mbsnbicmp** effectue une comparaison ordinale d’au plus le premier *nombre* d’octets de *string1* et *Chaîne2*. La comparaison est effectuée en convertissant chaque caractère en minuscules ; [_mbsnbcmp](mbsnbcmp-mbsnbcmp-l.md) est une version de **_mbsnbicmp**qui respecte la casse. La comparaison se termine si un caractère null de fin est atteint dans l’une ou l’autre des chaînes avant que les caractères *Count* soient comparés. Si les chaînes sont égales lorsqu’un caractère null de fin est atteint dans l’une ou l’autre des chaînes avant que les caractères *Count* soient comparés, la chaîne la plus courte est inférieure.

**_mbsnbicmp** est similaire à [_mbsnbcmp](mbsnbcmp-mbsnbcmp-l.md), à ceci près qu’elle compare des chaînes jusqu’au *nombre* d’octets au lieu de caractères.

La comparaison de deux chaînes contenant des caractères qui se trouvent entre « Z » et « a » dans la table ASCII (« [ », « \\ », « ] », « ^ », « _ » et « \` ») donne des résultats différents selon leur casse. Par exemple, les deux chaînes « ABCDe » et « ABCD ^ » sont comparées de façon unidirectionnelle si la comparaison est en minuscules (« ABCDE » > « ABCD ^ ») et l’autre méthode (« ABCDe » < « ABCD ^ ») si elle est en majuscules.

**_mbsnbicmp** reconnaît les séquences de caractères multioctets en fonction de la [page de codes multioctets](../../c-runtime-library/code-pages.md) en cours d’utilisation. Elle n'est pas affectée par les paramètres régionaux actuels.

Si *Chaîne1* ou *Chaîne2* est un pointeur null, **_mbsnbicmp** appelle le gestionnaire de paramètre non valide comme décrit dans [validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, la fonction retourne **_NLSCMPERROR** et définit **errno** sur **EINVAL**.

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine Tchar.h|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tcsnicmp**|**_strnicmp**|**_mbsnbicmp**|**_wcsnicmp**|
|**_tcsnicmp_l**|**_strnicmp_l**|**_mbsnbicmp_l**|**_wcsnicmp_l**|

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis|
|-------------|---------------------|
|**_mbsnbicmp**|\<mbstring.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

Consultez l’exemple relatif à [_mbsnbcmp, _mbsnbcmp_l](mbsnbcmp-mbsnbcmp-l.md).

## <a name="see-also"></a>Voir aussi

[Manipulation de chaînes](../../c-runtime-library/string-manipulation-crt.md)<br/>
[_mbsnbcat, _mbsnbcat_l](mbsnbcat-mbsnbcat-l.md)<br/>
[_mbsnbcmp, _mbsnbcmp_l](mbsnbcmp-mbsnbcmp-l.md)<br/>
[_stricmp, _wcsicmp, _mbsicmp, _stricmp_l, _wcsicmp_l, _mbsicmp_l](stricmp-wcsicmp-mbsicmp-stricmp-l-wcsicmp-l-mbsicmp-l.md)<br/>
