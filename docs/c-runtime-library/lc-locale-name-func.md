---
title: ___lc_locale_name_func
ms.date: 11/04/2016
apiname:
- ___lc_locale_name_func
apilocation:
- msvcrt.dll
- msvcr110.dll
- msvcr100.dll
- msvcr90.dll
- msvcr120.dll
- msvcr80.dll
- msvcr110_clr0400.dll
apitype: DLLExport
f1_keywords:
- ___lc_locale_name_func
helpviewer_keywords:
- ___lc_locale_name_func
ms.assetid: ef858308-872e-43de-95e0-9b1b4084343e
ms.openlocfilehash: 88ce07ca3fece558c23f4fcd9a12949f184b7532
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/11/2019
ms.locfileid: "57741053"
---
# <a name="lclocalenamefunc"></a>___lc_locale_name_func

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

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|`___lc_locale_name_func`|crt\src\setlocal.h|

## <a name="see-also"></a>Voir aussi

[_get_current_locale](../c-runtime-library/reference/get-current-locale.md)<br/>
[setlocale, _wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)<br/>
[_create_locale, _wcreate_locale](../c-runtime-library/reference/create-locale-wcreate-locale.md)<br/>
[_free_locale](../c-runtime-library/reference/free-locale.md)
