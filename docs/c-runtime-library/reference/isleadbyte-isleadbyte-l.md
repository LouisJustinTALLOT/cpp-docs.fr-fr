---
title: isleadbyte, _isleadbyte_l
ms.date: 11/04/2016
apiname:
- _isleadbyte_l
- isleadbyte
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
- api-ms-win-crt-string-l1-1-0.dll
apitype: DLLExport
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
ms.openlocfilehash: 1a3f427e49e53bb553020da100b0e713350fab3f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50531887"
---
# <a name="isleadbyte-isleadbytel"></a>isleadbyte, _isleadbyte_l

Détermine si un caractère est l’octet de tête d’un caractère multioctet.

> [!IMPORTANT]
> Cette API ne peut pas être utilisée dans les applications qui s’exécutent dans le Windows Runtime. Pour plus d’informations, consultez [Fonctions CRT non prises en charge dans les applications de la plateforme Windows universelle](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntaxe

```C
int isleadbyte( int c );
int _isleadbyte_l( int c );
```

### <a name="parameters"></a>Paramètres

*c*<br/>
Entier à tester.

## <a name="return-value"></a>Valeur de retour

**isleadbyte** retourne une valeur différente de zéro si l’argument satisfait la condition de test ou 0 si elle n’est pas le cas. Jeu de paramètres régionaux (SBCS), dans les paramètres régionaux « C » et dans un octet caractères **isleadbyte** retourne toujours 0.

## <a name="remarks"></a>Notes

Le **isleadbyte** macro retourne une valeur différente de zéro si son argument est le premier octet d’un caractère multioctet. **isleadbyte** produit un résultat significatif pour n’importe quel argument entier compris entre -1 (**EOF**) à **UCHAR_MAX** (0xFF), inclus.

Type d’argument attendu de **isleadbyte** est **int**; si un caractère signé est passé, le compilateur peut le convertir en un entier par extension de signe, produisant des résultats imprévisibles.

La version de cette fonction avec la **_l** suffixe est identique, sauf qu’elle utilise les paramètres régionaux passé au lieu des paramètres régionaux actuels pour son comportement dépendant des paramètres régionaux.

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine TCHAR.H|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_istleadbyte**|Retourne toujours la valeur false|**_isleadbyte**|Retourne toujours la valeur false|

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis|
|-------------|---------------------|
|**isleadbyte**|\<ctype.h>|
|**_isleadbyte_l**|\<ctype.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[Classification d’octets](../../c-runtime-library/byte-classification.md)<br/>
[Paramètres régionaux](../../c-runtime-library/locale.md)<br/>
[_ismbb, routines](../../c-runtime-library/ismbb-routines.md)<br/>
