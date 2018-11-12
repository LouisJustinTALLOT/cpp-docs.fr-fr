---
title: ___mb_cur_max_func, ___mb_cur_max_l_func, __p___mb_cur_max, __mb_cur_max
ms.date: 11/04/2016
apiname:
- ___mb_cur_max_l_func
- __p___mb_cur_max
- ___mb_cur_max_func
- __mb_cur_max
apilocation:
- msvcr110_clr0400.dll
- msvcr110.dll
- msvcr80.dll
- msvcr100.dll
- msvcrt.dll
- msvcr90.dll
- msvcr120.dll
apitype: DLLExport
f1_keywords:
- ___mb_cur_max_func
- ___mb_cur_max_l_func
- __p___mb_cur_max
- __mb_cur_max
helpviewer_keywords:
- __mb_cur_max
- ___mb_cur_max_func
- ___mb_cur_max_l_func
- __p___mb_cur_max
ms.assetid: 60d36108-1ca7-45a6-8ce7-68a91f13e3a1
ms.openlocfilehash: cb84c77ebafc7fb53c1544f9ec07db3fba6f02d6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50657039"
---
# <a name="mbcurmaxfunc-mbcurmaxlfunc-pmbcurmax-mbcurmax"></a>___mb_cur_max_func, ___mb_cur_max_l_func, __p___mb_cur_max, __mb_cur_max

Fonction CRT interne. Récupère le nombre maximal d'octets dans un caractère multioctets pour les paramètres régionaux actifs ou spécifiés.

## <a name="syntax"></a>Syntaxe

```cpp
int ___mb_cur_max_func(void);
int ___mb_cur_max_l_func(_locale_t locale);
int * __p___mb_cur_max(void);
#define __mb_cur_max (___mb_cur_max_func())
```

#### <a name="parameters"></a>Paramètres

locale Structure de paramètres régionaux auprès de laquelle le résultat doit être récupéré. Si cette valeur est null, les paramètres régionaux de thread actifs sont utilisés.

## <a name="return-value"></a>Valeur de retour

Nombre maximal d’octets dans un caractère multioctets pour les paramètres régionaux de thread actifs ou les paramètres régionaux spécifiés.

## <a name="remarks"></a>Notes

Il s'agit d'une fonction interne qu'utilise le CRT pour récupérer la valeur actuelle de la macro [MB_CUR_MAX](../c-runtime-library/mb-cur-max.md) auprès du stockage local de threads. Nous vous recommandons d'utiliser la macro `MB_CUR_MAX` dans votre code à des fins de portabilité.

La macro `__mb_cur_max` est un moyen pratique d'appeler la fonction `___mb_cur_max_func()`. La fonction `__p___mb_cur_max` est définie pour assurer une compatibilité avec Visual C++ 5.0 et les versions antérieures.

Les fonctions CRT internes sont spécifiques à l'implémentation et sont susceptibles d'être modifiées à chaque nouvelle version. Nous vous déconseillons de les utiliser dans votre code.

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis|
|-------------|---------------------|
|`___mb_cur_max_func`, `___mb_cur_max_l_func`, `__p___mb_cur_max`|\<ctype.h>, \<stdlib.h>|

## <a name="see-also"></a>Voir aussi

[MB_CUR_MAX](../c-runtime-library/mb-cur-max.md)