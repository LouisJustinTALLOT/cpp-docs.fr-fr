---
title: ___lc_codepage_func
ms.date: 11/04/2016
apiname:
- ___lc_codepage_func
apilocation:
- msvcr120.dll
- msvcr110_clr0400.dll
- msvcr80.dll
- msvcr100.dll
- msvcr90.dll
- msvcr110.dll
- msvcrt.dll
apitype: DLLExport
f1_keywords:
- lc_codepage_func
- ___lc_codepage_func
helpviewer_keywords:
- ___lc_codepage_func
ms.assetid: 6a663bd0-5a63-4a2f-9507-872ec1582aae
ms.openlocfilehash: aebd978839cc59c94c01e9c24432b69add72c4dc
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/11/2019
ms.locfileid: "57751333"
---
# <a name="lccodepagefunc"></a>___lc_codepage_func

Fonction CRT interne. Récupère la page de code active du thread.

## <a name="syntax"></a>Syntaxe

```cpp
UINT ___lc_codepage_func(void);
```

## <a name="return-value"></a>Valeur de retour

Page de code active du thread.

## <a name="remarks"></a>Remarques

`___lc_codepage_func` est une fonction CRT interne utilisée par d'autres fonctions CRT pour obtenir la page de code active à partir du stockage local des threads pour les données CRT. Ces informations sont également disponibles à l'aide de la fonction [_get_current_locale](../c-runtime-library/reference/get-current-locale.md).

Une *page de code* est le mappage de codes sur un ou deux octets en caractères individuels. Les différentes pages de code incluent des caractères spéciaux différents, généralement personnalisés pour une langue ou un groupe de langues. Pour plus d’informations sur les pages de code, consultez [Code Pages](../c-runtime-library/code-pages.md).

Les fonctions CRT internes sont spécifiques à l’implémentation et soumises à modification à chaque nouvelle mise en production. Nous vous déconseillons de les utiliser dans votre code.

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|`___lc_codepage_func`|crt\src\setlocal.h|

## <a name="see-also"></a>Voir aussi

[_get_current_locale](../c-runtime-library/reference/get-current-locale.md)<br/>
[setlocale, _wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)<br/>
[_create_locale, _wcreate_locale](../c-runtime-library/reference/create-locale-wcreate-locale.md)<br/>
[_free_locale](../c-runtime-library/reference/free-locale.md)
