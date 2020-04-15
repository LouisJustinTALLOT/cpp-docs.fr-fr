---
title: _ismbslead, _ismbstrail, _ismbslead_l, _ismbstrail_l
ms.date: 4/2/2020
api_name:
- _ismbstrail
- _ismbslead_l
- _ismbslead
- _ismbstrail_l
- _o__ismbslead
- _o__ismbslead_l
- _o__ismbstrail
- _o__ismbstrail_l
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
- _ismbslead
- ismbs
- ismbslead_l
- _ismbs
- ismbstrail_l
- ismbslead
- _ismbstrail
- _ismbstrail_l
- ismbstrail
- _ismbslead_l
helpviewer_keywords:
- ismbstrail function
- _ismbslead function
- ismbslead function
- ismbslead_l function
- _ismbstrail function
- _ismbslead_l function
- ismbstrail_l function
- _ismbstrail_l function
ms.assetid: 86d2cd7a-3cff-443a-b713-14cc17a231e9
ms.openlocfilehash: d4c9bfcec1deab8c00eb490dc044e62a6124aba3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81342918"
---
# <a name="_ismbslead-_ismbstrail-_ismbslead_l-_ismbstrail_l"></a>_ismbslead, _ismbstrail, _ismbslead_l, _ismbstrail_l

Effectue des tests contextuels pour les octets de tête et de fin des chaînes de caractères multioctets et détermine si un pointeur de sous-chaîne pointe vers un octet de tête ou un octet de fin.

> [!IMPORTANT]
> Cette API ne peut pas être utilisée dans les applications qui s'exécutent dans le Windows Runtime. Pour plus d’informations, consultez [Fonctions CRT non prises en charge dans les applications de la plateforme Windows universelle](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntaxe

```C
int _ismbslead(
   const unsigned char *str,
   const unsigned char *current
);
int _ismbstrail(
   const unsigned char *str,
   const unsigned char *current
);
int _ismbslead_l(
   const unsigned char *str,
   const unsigned char *current,
   _locale_t locale
);
int _ismbstrail_l(
   const unsigned char *str,
   const unsigned char *current,
   _locale_t locale
);
```

### <a name="parameters"></a>Paramètres

*Str*<br/>
Pointeur indiquant le début de la chaîne ou l'octet de tête connu précédent.

*Actuelle*<br/>
Pointeur indiquant la position dans la chaîne à tester.

*locale*<br/>
Paramètres régionaux à utiliser.

## <a name="return-value"></a>Valeur de retour

**_ismbslead** revient -1 si le personnage est un byte de plomb et **_ismbstrail** retourne -1 si le personnage est un byte de piste. Si les chaînes d'entrée sont valides mais qu'elles ne correspondent ni à un octet de tête ni à un octet de fin, ces fonctions retournent zéro. Si l’un ou l’autre argument est **NULL**, le gestionnaire de paramètre invalide est invoqué, tel que décrit dans [La validation de paramètres](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, ces fonctions renvoient **NULL** et **placent errno** à **EINVAL**.

## <a name="remarks"></a>Notes

**_ismbslead** et **_ismbstrail** sont plus lents que les versions **_ismbblead** et **_ismbbtrail** parce qu’ils tiennent compte du contexte de la chaîne.

Les versions de ces fonctions qui ont le **suffixe _l** sont identiques, sauf que pour leur comportement local-dépendant, ils utilisent le lieu qui est passé au lieu de la localisation actuelle. Pour plus d’informations, consultez [Locale](../../c-runtime-library/locale.md).

Par défaut, l’état global de cette fonction est étendue à l’application. Pour changer cela, voir [Global State dans le CRT](../global-state.md).

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|En-tête facultatif|
|-------------|---------------------|---------------------|
|**_ismbslead**|\<mbctype.h> ou \<mbstring.h>|\<ctype.h>,* \<limits.h>, \<stdlib.h>|
|**_ismbstrail**|\<mbctype.h> ou \<mbstring.h>|\<ctype.h>,* \<limits.h>, \<stdlib.h>|
|**_ismbslead_l**|\<mbctype.h> ou \<mbstring.h>|\<ctype.h>,* \<limits.h>, \<stdlib.h>|
|**_ismbstrail_l**|\<mbctype.h> ou \<mbstring.h>|\<ctype.h>,* \<limits.h>, \<stdlib.h>|

\* Pour les constantes manifestes des conditions de test.

Pour plus d’informations sur la compatibilité, consultez [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[Classifications des caractères](../../c-runtime-library/character-classification.md)<br/>
[_ismbc, routines](../../c-runtime-library/ismbc-routines.md)<br/>
[is, isw, routines](../../c-runtime-library/is-isw-routines.md)<br/>
[routines _ismbb](../../c-runtime-library/ismbb-routines.md)<br/>
