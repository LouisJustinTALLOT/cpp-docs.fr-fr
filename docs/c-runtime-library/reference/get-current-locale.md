---
title: _get_current_locale
ms.date: 11/04/2016
api_name:
- _get_current_locale
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- get_current_locale
- __get_current_locale
- _get_current_locale
helpviewer_keywords:
- get_current_locale function
- _get_current_locale function
- locales, getting information on
- __get_current_locale function
ms.assetid: 572217f2-a37a-4105-a293-a250b4fabd99
ms.openlocfilehash: a17e730b350eaf88cf1c51502fda3df5ae30f611
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70956095"
---
# <a name="_get_current_locale"></a>_get_current_locale

Obtient un objet de paramètres régionaux qui représente les paramètres régionaux actuels.

## <a name="syntax"></a>Syntaxe

```C
_locale_t _get_current_locale(void);
```

## <a name="return-value"></a>Valeur de retour

Objet de paramètres régionaux qui représente les paramètres régionaux actuels.

## <a name="remarks"></a>Notes

La fonction **_get_current_locale** obtient les paramètres régionaux actuellement définis pour le thread et retourne un objet de paramètres régionaux représentant les paramètres régionaux.

Le nom précédent de cette fonction, **__get_current_locale** (avec deux traits de soulignement de début), est déconseillé.

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis|
|-------------|---------------------|
|**_get_current_locale**|\<locale.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[setlocale, _wsetlocale](setlocale-wsetlocale.md)<br/>
[_create_locale, _wcreate_locale](create-locale-wcreate-locale.md)<br/>
[_free_locale](free-locale.md)<br/>
