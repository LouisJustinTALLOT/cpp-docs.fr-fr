---
description: 'En savoir plus sur les éléments suivants : ___mb_cur_max_func, ___mb_cur_max_l_func, __p___mb_cur_max, __mb_cur_max'
title: ___mb_cur_max_func, ___mb_cur_max_l_func, __p___mb_cur_max, __mb_cur_max
ms.date: 4/2/2020
api_name:
- ___mb_cur_max_l_func
- __p___mb_cur_max
- ___mb_cur_max_func
- __mb_cur_max
- _o____mb_cur_max_func
api_location:
- msvcr110_clr0400.dll
- msvcr110.dll
- msvcr80.dll
- msvcr100.dll
- msvcrt.dll
- msvcr90.dll
- msvcr120.dll
- api-ms-win-crt-locale-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
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
ms.openlocfilehash: 1308dbe969f8b6638835f52ec1e7a2cdcd63bb7f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97321160"
---
# <a name="___mb_cur_max_func-___mb_cur_max_l_func-__p___mb_cur_max-__mb_cur_max"></a>___mb_cur_max_func, ___mb_cur_max_l_func, __p___mb_cur_max, __mb_cur_max

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

## <a name="return-value"></a>Valeur renvoyée

Nombre maximal d’octets dans un caractère multioctets pour les paramètres régionaux de thread actifs ou les paramètres régionaux spécifiés.

## <a name="remarks"></a>Notes

Il s'agit d'une fonction interne qu'utilise le CRT pour récupérer la valeur actuelle de la macro [MB_CUR_MAX](../c-runtime-library/mb-cur-max.md) auprès du stockage local de threads. Nous vous recommandons d'utiliser la macro `MB_CUR_MAX` dans votre code à des fins de portabilité.

La macro `__mb_cur_max` est un moyen pratique d'appeler la fonction `___mb_cur_max_func()`. La fonction `__p___mb_cur_max` est définie pour assurer une compatibilité avec Visual C++ 5.0 et les versions antérieures.

Les fonctions CRT internes sont spécifiques à l'implémentation et sont susceptibles d'être modifiées à chaque nouvelle version. Nous vous déconseillons de les utiliser dans votre code.

Par défaut, l’état global de cette fonction est limité à l’application. Pour modifier cette valeur, consultez [état global dans le CRT](global-state.md).

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|`___mb_cur_max_func`, `___mb_cur_max_l_func`, `__p___mb_cur_max`|\<ctype.h>, \<stdlib.h>|

## <a name="see-also"></a>Voir aussi

[MB_CUR_MAX](../c-runtime-library/mb-cur-max.md)
