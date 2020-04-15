---
title: _free_locale
ms.date: 4/2/2020
api_name:
- _free_locale
- _o__free_locale
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
- api-ms-win-crt-locale-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- __free_locale
- free_locale
- _free_locale
helpviewer_keywords:
- __free_locale function
- free_locale function
- locales, freeing
- _free_locale function
ms.assetid: 1f08d348-ab32-4028-a145-6cbd51b49af9
ms.openlocfilehash: 568e44d731f384a0503420339d716fdfdc81e13a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81346041"
---
# <a name="_free_locale"></a>_free_locale

Libère un objet de paramètres régionaux.

## <a name="syntax"></a>Syntaxe

```C
void _free_locale(
   _locale_t locale
);
```

### <a name="parameters"></a>Paramètres

*locale*<br/>
Objet de paramètres régionaux à libérer.

## <a name="remarks"></a>Notes

La fonction **_free_locale** est utilisée pour libérer l’objet local obtenu à partir d’un appel à **_get_current_locale** ou **_create_locale**.

Le nom précédent de cette fonction, **__free_locale** (avec deux soulignements de premier plan) a été déprécié.

Par défaut, l’état global de cette fonction est étendue à l’application. Pour changer cela, voir [Global State dans le CRT](../global-state.md).

## <a name="requirements"></a>Spécifications

|**Routine**|En-tête requis|
|---------------|---------------------|
|**_free_locale**|\<locale.h>|

Pour plus d’informations sur la compatibilité, consultez [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[_get_current_locale](get-current-locale.md)<br/>
[_create_locale, _wcreate_locale](create-locale-wcreate-locale.md)<br/>
