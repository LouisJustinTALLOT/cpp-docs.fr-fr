---
title: _ismbclegal, _ismbclegal_l, _ismbcsymbol, _ismbcsymbol_l
ms.date: 11/04/2016
api_name:
- _ismbclegal_l
- _ismbclegal
- _ismbcsymbol
- _ismbcsymbol_l
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
- ismbcsymbol_l
- _ismbcsymbol_l
- _ismbcsymbol
- _ismbclegal_l
- _ismbclegal
- ismbclegal_l
- ismbcsymbol
- ismbclegal
helpviewer_keywords:
- ismbcsymbol function
- ismbclegal_l function
- _istlegal_l function
- istlegal function
- _istlegal function
- _ismbcsymbol function
- _ismbclegal_l function
- ismbclegal function
- ismbcsymbol_l function
- _ismbclegal function
- _ismbcsymbol_l function
- istlegal_l function
ms.assetid: 31bf1ea5-b56f-4e28-b21e-b49a2cf93ffc
ms.openlocfilehash: 4e040db584725322e98d0a82b28912eea100aff7
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70953805"
---
# <a name="_ismbclegal-_ismbclegal_l-_ismbcsymbol-_ismbcsymbol_l"></a>_ismbclegal, _ismbclegal_l, _ismbcsymbol, _ismbcsymbol_l

Vérifie si un caractère multioctet est un caractère autorisé ou un symbole.

> [!IMPORTANT]
> Cette API ne peut pas être utilisée dans les applications qui s’exécutent dans le Windows Runtime. Pour plus d’informations, consultez [Fonctions CRT non prises en charge dans les applications de la plateforme Windows universelle](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntaxe

```C
int _ismbclegal(
   unsigned int c
);
int _ismbclegal_l(
   unsigned int c,
   _locale_t locale
);
int _ismbcsymbol(
   unsigned int c
);
int _ismbcsymbol_l(
   unsigned int c,
   _locale_t locale
);
```

### <a name="parameters"></a>Paramètres

*c*<br/>
Caractère à tester.

*locale*<br/>
Paramètres régionaux à utiliser.

## <a name="return-value"></a>Valeur de retour

Chacune de ces routines retourne une valeur différente de zéro si le caractère satisfait à la condition de test ou 0 dans le cas contraire. Si *c*< = 255 et qu’il existe une routine **_ismbb** correspondante (par exemple, **_ismbcalnum** correspond à **_ismbbalnum**), le résultat est la valeur de retour de la routine **_ismbb** correspondante.

## <a name="remarks"></a>Notes

Chacune de ces fonctions teste un caractère multioctet fourni pour un état donné.

Les versions de ces fonctions avec le suffixe **_L** sont identiques, sauf qu’elles utilisent les paramètres régionaux passés au lieu des paramètres régionaux actuels pour leur comportement dépendant des paramètres régionaux. Pour plus d’informations, consultez [Locale](../../c-runtime-library/locale.md).

|Routine|Condition de test|Exemple de page de codes 932|
|-------------|--------------------|---------------------------|
|**_ismbclegal**|Multioctet valide|Retourne une valeur différente de zéro si et seulement si le premier octet de *c* se trouve dans les plages 0X81-0X9f ou 0XE0-0xFC, tandis que le deuxième octet se trouve dans les plages 0X40-0x7E ou 0X80-FC.|
|**_ismbcsymbol**|Symbole multioctet|Retourne une valeur différente de zéro si et seulement si 0x8141 < =*c*< = 0x81AC.|

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine Tchar.h|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_istlegal**|Retourne toujours la valeur false|**_ismbclegal**|Retourne toujours la valeur false.|
|**_istlegal_l**|Retourne toujours la valeur false|**_ismbclegal_l**|Retourne toujours la valeur false.|

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis|
|-------------|---------------------|
|**_ismbclegal**, **_ismbclegal_l**|\<mbstring.h>|
|**_ismbcsymbol**, **_ismbcsymbol_l**|\<mbstring.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[Classifications des caractères](../../c-runtime-library/character-classification.md)<br/>
[_ismbc, routines](../../c-runtime-library/ismbc-routines.md)<br/>
[is, isw, routines](../../c-runtime-library/is-isw-routines.md)<br/>
[_ismbb, routines](../../c-runtime-library/ismbb-routines.md)<br/>
