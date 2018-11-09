---
title: ___lc_collate_cp_func
ms.date: 11/04/2016
apiname:
- ___lc_collate_cp_func
apilocation:
- msvcr120.dll
- msvcrt.dll
- msvcr100.dll
- msvcr80.dll
- msvcr110_clr0400.dll
- msvcr110.dll
- msvcr90.dll
apitype: DLLExport
f1_keywords:
- ___lc_collate_cp_func
helpviewer_keywords:
- ___lc_collate_cp_func
ms.assetid: 46ccc084-7ac9-4e5d-9138-e12cb5845615
ms.openlocfilehash: 37254177ab57212dd57e476716d1dc07d59d7239
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50521240"
---
# <a name="lccollatecpfunc"></a>___lc_collate_cp_func

Fonction CRT interne. Récupère la page de code de classement active du thread.

## <a name="syntax"></a>Syntaxe

```cpp
UINT ___lc_codepage_func(void);
```

## <a name="return-value"></a>Valeur de retour

Page de code de classement active du thread.

## <a name="remarks"></a>Notes

`___lc_collate_cp_func` est une fonction CRT interne utilisée par d'autres fonctions CRT pour obtenir la page de code de classement active à partir du stockage local des threads pour les données CRT. Ces informations sont également disponibles à l'aide de la fonction [_get_current_locale](../c-runtime-library/reference/get-current-locale.md).

Les fonctions CRT internes sont spécifiques à l'implémentation et sont susceptibles d'être modifiées à chaque nouvelle version. Nous vous déconseillons de les utiliser dans votre code.

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis|
|-------------|---------------------|
|`___lc_collate_cp_func`|crt\src\setlocal.h|

## <a name="see-also"></a>Voir aussi

[_get_current_locale](../c-runtime-library/reference/get-current-locale.md)<br/>
[setlocale, _wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)<br/>
[_create_locale, _wcreate_locale](../c-runtime-library/reference/create-locale-wcreate-locale.md)<br/>
[_free_locale](../c-runtime-library/reference/free-locale.md)