---
title: isleadbyte, _isleadbyte_l
ms.date: 4/2/2020
api_name:
- _isleadbyte_l
- isleadbyte
- _o__isleadbyte_l
- _o_isleadbyte
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
- api-ms-win-crt-string-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _istleadbyte
- _isleadbyte_l
- isleadbyte
helpviewer_keywords:
- lead bytes
- _isleadbyte_l function
- _istleadbyte function
- istleadbyte function
- isleadbyte function
ms.assetid: 3b2bcf09-d82b-4803-9e80-59d04942802a
ms.openlocfilehash: dddf1d669f77805df8e00f506b6427603ac8fd9f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81343842"
---
# <a name="isleadbyte-_isleadbyte_l"></a>isleadbyte, _isleadbyte_l

Détermine si un caractère est l’octet de tête d’un caractère multioctet.

> [!IMPORTANT]
> Cette API ne peut pas être utilisée dans les applications qui s'exécutent dans le Windows Runtime. Pour plus d’informations, consultez [Fonctions CRT non prises en charge dans les applications de la plateforme Windows universelle](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntaxe

```C
int isleadbyte( int c );
int _isleadbyte_l( int c );
```

### <a name="parameters"></a>Paramètres

*C*<br/>
Entier à tester.

## <a name="return-value"></a>Valeur de retour

**isleadbyte** retourne une valeur non zéro si l’argument satisfait la condition de test ou 0 si elle ne le fait pas. Dans le lieu "C" et dans un seul caractère ensemble (SBCS) lieux, **isleadbyte** retourne toujours 0.

## <a name="remarks"></a>Notes

La macro **isleadbyte** retourne une valeur non zéro si son argument est le premier byte d’un caractère multioctet. **isleadbyte** produit un résultat significatif pour tout argument d’un intégriste de -1 (**EOF**) à **UCHAR_MAX** (0xFF), inclusivement.

Le type d’argument attendu de **l’isleadoctet** est **int**; si un personnage signé est passé, le compilateur peut le convertir en un intégrier par extension de signe, donnant des résultats imprévisibles.

La version de cette fonction avec le **suffixe _l** est identique sauf qu’elle utilise le lieu passé au lieu de la localisation actuelle pour son comportement local-dépendant.

Par défaut, l’état global de cette fonction est étendue à l’application. Pour changer cela, voir [Global State dans le CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine TCHAR.H|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_istleadbyte**|Retourne toujours la valeur false|**_isleadbyte**|Retourne toujours la valeur false|

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**isleadbyte**|\<ctype.h>|
|**_isleadbyte_l**|\<ctype.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[Classification d’octets](../../c-runtime-library/byte-classification.md)<br/>
[Local](../../c-runtime-library/locale.md)<br/>
[routines _ismbb](../../c-runtime-library/ismbb-routines.md)<br/>
