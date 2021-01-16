---
description: 'En savoir plus sur : ___lc_locale_name_func'
title: ___lc_locale_name_func
ms.date: 1/14/2021
api_name:
- ___lc_locale_name_func
- _o____lc_locale_name_func
api_location:
- msvcrt.dll
- msvcr110.dll
- msvcr100.dll
- msvcr90.dll
- msvcr120.dll
- msvcr80.dll
- msvcr110_clr0400.dll
- api-ms-win-crt-private-l1-1-0.dll
- api-ms-win-crt-locale-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- ___lc_locale_name_func
helpviewer_keywords:
- ___lc_locale_name_func
ms.assetid: ef858308-872e-43de-95e0-9b1b4084343e
ms.openlocfilehash: 4747b64c0fc61e0f5d77eacb92c04c9f6d2e2759
ms.sourcegitcommit: 1cd8f8a75fd036ffa57bc70f3ca869042d8019d4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/15/2021
ms.locfileid: "98242863"
---
# <a name="___lc_locale_name_func"></a>___lc_locale_name_func

Fonction CRT interne. Récupère le nom de paramètres régionaux actuel du thread.

## <a name="syntax"></a>Syntaxe

```cpp
wchar_t** ___lc_locale_name_func(void);
```

## <a name="return-value"></a>Valeur de retour

Pointeur vers une chaîne qui contient le nom de paramètres régionaux actuel du thread.

## <a name="remarks"></a>Remarques

`___lc_locale_name_func` est une fonction CRT interne qui est utilisée par d'autres fonctions CRT pour obtenir le nom de paramètres régionaux actuel du stockage local des threads pour les données CRT. Ces informations sont également disponibles à l'aide des fonctions [_get_current_locale](../c-runtime-library/reference/get-current-locale.md) ou [setlocale, _wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md).

Les fonctions CRT internes sont spécifiques à l'implémentation et sont susceptibles d'être modifiées à chaque nouvelle version. Nous vous déconseillons de les utiliser dans votre code.

Par défaut, l’état global de cette fonction est limité à l’application. Pour modifier cette valeur, consultez [état global dans le CRT](global-state.md).

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis|
|-------------|---------------------|
|`___lc_locale_name_func`|crt\src\setlocal.h|

## <a name="see-also"></a>Voir aussi

[_get_current_locale](../c-runtime-library/reference/get-current-locale.md)<br/>
[setlocale, _wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)<br/>
[_create_locale, _wcreate_locale](../c-runtime-library/reference/create-locale-wcreate-locale.md)<br/>
[_free_locale](../c-runtime-library/reference/free-locale.md)
