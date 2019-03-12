---
title: Catégories de paramètres régionaux
ms.date: 11/04/2016
f1_keywords:
- LC_MAX
- LC_MIN
- LC_MONETARY
- LC_TIME
- LC_NUMERIC
- LC_COLLATE
- LC_CTYPE
- LC_ALL
helpviewer_keywords:
- LC_MIN constant
- LC_MONETARY constant
- LC_CTYPE constant
- locale constants
- LC_MAX constant
- LC_ALL constant
- LC_TIME constant
- LC_NUMERIC constant
- LC_COLLATE constant
ms.assetid: 868f1493-fe5d-4722-acab-bfcd374a063a
ms.openlocfilehash: 434500dab0c68aa9475f54e930b91da0b1cd2fc9
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/11/2019
ms.locfileid: "57749800"
---
# <a name="locale-categories"></a>Catégories de paramètres régionaux

## <a name="syntax"></a>Syntaxe

```
#include <locale.h>
```

## <a name="remarks"></a>Remarques

Les catégories de paramètres régionaux sont des constantes manifestes utilisées par les routines de localisation pour spécifier dans quelle portion des informations de paramètres régionaux d’un programme les informations seront utilisées. Les paramètres régionaux font référence à la localité (ou au pays/à la région) pour laquelle certains aspects de votre programme peuvent être personnalisés. Les zones dépendant des paramètres régionaux comprennent par exemple la mise en forme des dates et le format d'affichage des valeurs monétaires.

|Catégorie de paramètres régionaux|Parties de programme affectées|
|---------------------|-------------------------------|
|`LC_ALL`|Tous les comportements spécifiques aux paramètres régionaux (toutes les catégories)|
|`LC_COLLATE`|Comportement des fonctions `strcoll` et `strxfrm`|
|`LC_CTYPE`|Les fonctions de gestion de caractères (sauf `isdigit`, `isxdigit`, `mbstowcs` et `mbtowc`, qui ne sont pas affectés)|
|`LC_MAX`|Identique à `LC_TIME`|
|`LC_MIN`|Identique à `LC_ALL`|
|`LC_MONETARY`|Les informations de mise en forme monétaire retournées par la fonction `localeconv`|
|`LC_NUMERIC`|Le caractère de virgule décimale pour les routines de sortie mise en forme (comme `printf`), pour les routines de conversion de données, et pour les informations de mise en forme non monétaire retournées par `localeconv`|
|`LC_TIME`|Comportement de la fonction `strftime`|

Consultez [setlocale, _wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md) pour obtenir un exemple.

## <a name="see-also"></a>Voir aussi

[localeconv](../c-runtime-library/reference/localeconv.md)<br/>
[setlocale, _wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)<br/>
[strcoll, fonctions](../c-runtime-library/strcoll-functions.md)<br/>
[strftime, wcsftime, _strftime_l, _wcsftime_l](../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md)<br/>
[strxfrm, wcsxfrm, _strxfrm_l, _wcsxfrm_l](../c-runtime-library/reference/strxfrm-wcsxfrm-strxfrm-l-wcsxfrm-l.md)<br/>
[Constantes globales](../c-runtime-library/global-constants.md)
