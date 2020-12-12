---
description: 'En savoir plus sur : _mbsnbcat, _mbsnbcat_l'
title: _mbsnbcat, _mbsnbcat_l
ms.date: 4/2/2020
api_name:
- _mbsnbcat_l
- _mbsnbcat
- _o__mbsnbcat
- _o__mbsnbcat_l
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
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- mbsnbcat
- mbsnbcat_l
- _mbsnbcat
- _mbsnbcat_l
helpviewer_keywords:
- tcsncat_l function
- _tcsncat function
- mbsnbcat_l function
- mbsnbcat function
- _mbsnbcat_l function
- _tcsncat_l function
- _mbsnbcat function
- tcsncat function
ms.assetid: aa0f1d30-0ddd-48d1-88eb-c6884b20fd91
ms.openlocfilehash: 633ee28a1ab90eef286eb27d75e7a5e808c06ef8
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97271042"
---
# <a name="_mbsnbcat-_mbsnbcat_l"></a>_mbsnbcat, _mbsnbcat_l

Ajoute, au plus, les **n** premiers octets d’une chaîne de caractères multioctets à une autre. Des versions plus sécurisées de ces fonctions sont disponibles ; consultez [_mbsnbcat_s, _mbsnbcat_s_l](mbsnbcat-s-mbsnbcat-s-l.md).

> [!IMPORTANT]
> Cette API ne peut pas être utilisée dans les applications qui s'exécutent dans le Windows Runtime. Pour plus d’informations, consultez [Fonctions CRT non prises en charge dans les applications de la plateforme Windows universelle](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntaxe

```C
unsigned char *_mbsnbcat(
   unsigned char *dest,
   const unsigned char *src,
   size_t count
);
unsigned char *_mbsnbcat_l(
   unsigned char *dest,
   const unsigned char *src,
   size_t count,
   _locale_t locale
);
template <size_t size>
unsigned char *_mbsnbcat(
   unsigned char (&dest)[size],
   const unsigned char *src,
   size_t count
); // C++ only
template <size_t size>
unsigned char *_mbsnbcat_l(
   unsigned char (&dest)[size],
   const unsigned char *src,
   size_t count,
   _locale_t locale
); // C++ only
```

### <a name="parameters"></a>Paramètres

*dest*<br/>
Chaîne de destination à caractères multioctets se terminant par un caractère null.

*src*<br/>
Chaîne source à caractères multioctets se terminant par un caractère null.

*count*<br/>
Nombre d’octets de *src* à ajouter à *dest*.

*locale*<br/>
Paramètres régionaux à utiliser.

## <a name="return-value"></a>Valeur renvoyée

**_mbsnbcat** retourne un pointeur vers la chaîne de destination. Aucune valeur de retour n'est réservée pour indiquer une erreur.

## <a name="remarks"></a>Notes

La fonction **_mbsnbcat** ajoute, au plus, le premier *nombre* d’octets de *src* à *dest*. Si l’octet qui précède immédiatement le caractère NULL dans *dest* est un octet de tête, l’octet initial de *src* remplace cet octet de tête. Dans le cas contraire, l’octet initial de *src* remplace le caractère null de fin de *dest*. Si un octet NULL apparaît dans *src* avant que le *nombre* d’octets soit ajouté, **_mbsnbcat** ajoute tous les octets de *src*, jusqu’au caractère null. Si *Count* est supérieur à la longueur de *src*, la longueur de *src* est utilisée à la place de *Count*. La chaîne obtenue se termine par un caractère Null. Si la copie se produit entre des chaînes qui se chevauchent, le comportement est indéfini.

La valeur de sortie est affectée par la valeur du paramètre de catégorie **LC_CTYPE** des paramètres régionaux. Pour plus d’informations, consultez [setlocale](setlocale-wsetlocale.md). La version **_mbsnbcat** de la fonction utilise les paramètres régionaux actuels pour ce comportement dépendant des paramètres régionaux ; la version de **_mbsnbcat_l** est identique, sauf qu’elle utilise à la place les paramètres régionaux transmis. Pour plus d’informations, consultez [Locale](../../c-runtime-library/locale.md).

**Remarque relative à la sécurité** Utilisez une chaîne se terminant par un caractère Null. La chaîne ne doit pas dépasser la taille de la mémoire tampon de destination. Pour plus d’informations, consultez [Solutions contre les dépassements de mémoire tampon](/windows/win32/SecBP/avoiding-buffer-overruns).

Si *dest* ou *src* a la **valeur null**, la fonction génère une erreur de paramètre non valide, comme décrit dans [validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’erreur est gérée, la fonction retourne **EINVAL** et définit **errno** sur **EINVAL**.

En C++, ces fonctions ont des surcharges de modèle qui appellent les équivalents plus récents et sécurisés de ces fonctions. Pour plus d’informations, consultez [Sécuriser les surcharges de modèle](../../c-runtime-library/secure-template-overloads.md).

Par défaut, l’état global de cette fonction est limité à l’application. Pour modifier cette valeur, consultez [état global dans le CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine Tchar.h|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tcsncat**|[strncat](strncat-strncat-l-wcsncat-wcsncat-l-mbsncat-mbsncat-l.md)|**_mbsnbcat**|[wcsncat](strncat-strncat-l-wcsncat-wcsncat-l-mbsncat-mbsncat-l.md)|
|**_tcsncat_l**|**_strncat_l**|**_mbsnbcat_l**|**_wcsncat_l**|

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**_mbsnbcat**|\<mbstring.h>|
|**_mbsnbcat_l**|\<mbstring.h>|

Pour plus d’informations sur la compatibilité, consultez [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[Manipulation de chaînes](../../c-runtime-library/string-manipulation-crt.md)<br/>
[_mbsnbcmp, _mbsnbcmp_l](mbsnbcmp-mbsnbcmp-l.md)<br/>
[_strncnt, _wcsncnt, _mbsnbcnt, _mbsnbcnt_l, _mbsnccnt, _mbsnccnt_l](strncnt-wcsncnt-mbsnbcnt-mbsnbcnt-l-mbsnccnt-mbsnccnt-l.md)<br/>
[_mbsnbcpy, _mbsnbcpy_l](mbsnbcpy-mbsnbcpy-l.md)<br/>
[_mbsnbicmp, _mbsnbicmp_l](mbsnbicmp-mbsnbicmp-l.md)<br/>
[_mbsnbset, _mbsnbset_l](mbsnbset-mbsnbset-l.md)<br/>
[strncat, _strncat_l, wcsncat, _wcsncat_l, _mbsncat, _mbsncat_l](strncat-strncat-l-wcsncat-wcsncat-l-mbsncat-mbsncat-l.md)<br/>
[_mbsnbcat_s, _mbsnbcat_s_l](mbsnbcat-s-mbsnbcat-s-l.md)<br/>
