---
title: _mbctohira, _mbctohira_l, _mbctokata, _mbctokata_l
ms.date: 11/04/2016
apiname:
- _mbctohira
- _mbctohira_l
- _mbctokata
- _mbctokata_l
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
- _mbctokata
- mbctohira
- _mbctohira
- _mbctohira_l
- mbctokata
- mbctokata_l
- mbctohira_l
- _mbctokata_l
helpviewer_keywords:
- _mbctokata function
- _mbctokata_l function
- _mbctohira_l function
- mbctohira_l function
- mbctohira function
- mbctokata_l function
- _mbctohira function
- mbctokata function
ms.assetid: f949afd7-44d4-4f08-ac8f-1fef2c915a1c
ms.openlocfilehash: 11b08449a7d27015c4ffe0ce398c471bbd6069f0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62285611"
---
# <a name="mbctohira-mbctohiral-mbctokata-mbctokatal"></a>_mbctohira, _mbctohira_l, _mbctokata, _mbctokata_l

Convertit des caractères Hiragana en caractères Katakana et inversement

> [!IMPORTANT]
> Cette API ne peut pas être utilisée dans les applications qui s’exécutent dans le Windows Runtime. Pour plus d’informations, consultez [Fonctions CRT non prises en charge dans les applications de la plateforme Windows universelle](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntaxe

```C
unsigned int _mbctohira(
   unsigned int c
);
unsigned int _mbctohira_l(
   unsigned int c,
   _locale_t locale
);
unsigned int _mbctokata(
   unsigned int c
);
unsigned int _mbctokata_l(
   unsigned int c,
   _locale_t locale
);
```

### <a name="parameters"></a>Paramètres

*c*<br/>
Caractère multioctet à convertir.

*locale*<br/>
Paramètres régionaux à utiliser.

## <a name="return-value"></a>Valeur de retour

Chacune de ces fonctions retourne le caractère converti *c*, si possible. Sinon, elle retourne le caractère *c* inchangé.

## <a name="remarks"></a>Notes

Le **_mbctohira** et **_mbctokata** fonctions testent un caractère *c* et, dans la mesure du possible, appliquez une des conversions suivantes.

|Routines|Conversion|
|--------------|--------------|
|**_mbctohira**, **_mbctohira_l**|Katakana multioctet en hiragana multioctet.|
|**_mbctokata**, **_mbctokata_l**|Hiragana multioctet en katakana multioctet.|

La valeur de sortie est affectée par la valeur du paramètre de catégorie **LC_CTYPE** des paramètres régionaux. Pour plus d’informations, consultez [setlocale](setlocale-wsetlocale.md). Les versions de ces fonctions sont identiques, à ceci près que celles qui n’ont le **_l** suffixe utiliser les paramètres régionaux actuels pour ce comportement dépendant des paramètres régionaux et celles qui ont le **_l** suffixe à la place Utilisez les paramètres régionaux qui sont passés. Pour plus d’informations, consultez [Locale](../../c-runtime-library/locale.md).

Dans les versions antérieures, **_mbctohira** s’appelait **jtohira** et **_mbctokata** s’appelait **jtokata**. Pour le nouveau code, utilisez les nouveaux noms.

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis|
|-------------|---------------------|
|**_mbctohira**|\<mbstring.h>|
|**_mbctohira_l**|\<mbstring.h>|
|**_mbctokata**|\<mbstring.h>|
|**_mbctokata_l**|\<mbstring.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[Conversion de données](../../c-runtime-library/data-conversion.md)<br/>
[_mbcjistojms, _mbcjistojms_l, _mbcjmstojis, _mbcjmstojis_l](mbcjistojms-mbcjistojms-l-mbcjmstojis-mbcjmstojis-l.md)<br/>
[_mbctolower, _mbctolower_l, _mbctoupper, _mbctoupper_l](mbctolower-mbctolower-l-mbctoupper-mbctoupper-l.md)<br/>
[_mbctombb, _mbctombb_l](mbctombb-mbctombb-l.md)<br/>
