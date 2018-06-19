---
title: _get_current_locale | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _get_current_locale
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
- api-ms-win-crt-locale-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- get_current_locale
- __get_current_locale
- _get_current_locale
dev_langs:
- C++
helpviewer_keywords:
- get_current_locale function
- _get_current_locale function
- locales, getting information on
- __get_current_locale function
ms.assetid: 572217f2-a37a-4105-a293-a250b4fabd99
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c658d960953bea2890202bebe280d46dd3407d63
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32396938"
---
# <a name="getcurrentlocale"></a>_get_current_locale

Obtient un objet de paramètres régionaux qui représente les paramètres régionaux actuels.

## <a name="syntax"></a>Syntaxe

```C
_locale_t _get_current_locale(void);
```

## <a name="return-value"></a>Valeur de retour

Objet de paramètres régionaux qui représente les paramètres régionaux actuels.

## <a name="remarks"></a>Notes

Le **_get_current_locale** fonction obtient actuellement défini les paramètres régionaux du thread et retourne un objet de paramètres régionaux qui représente les paramètres régionaux.

Le nom précédent de cette fonction, **__get_current_locale** (avec deux traits de soulignement au début) a été déconseillée.

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**_get_current_locale**|\<locale.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[setlocale, _wsetlocale](setlocale-wsetlocale.md)<br/>
[_create_locale, _wcreate_locale](create-locale-wcreate-locale.md)<br/>
[_free_locale](free-locale.md)<br/>
