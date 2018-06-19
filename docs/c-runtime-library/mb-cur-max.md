---
title: MB_CUR_MAX | Microsoft Docs
ms.custom: ''
ms.date: 10/18/2017
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- MB_CUR_MAX
dev_langs:
- C++
helpviewer_keywords:
- MB_CUR_MAX constant
ms.assetid: fab22609-c14d-4c19-991c-bd09ff30e604
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8c9b290df51d631251811d1f8a92dff980304b24
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32390379"
---
# <a name="mbcurmax"></a>MB_CUR_MAX

Macro indiquant le nombre maximal d’octets dans un caractère multioctet pour les paramètres régionaux actuels.

## <a name="syntax"></a>Syntaxe

`#include <stdlib.h>`

## <a name="remarks"></a>Notes

Contexte : Fonctions de conversion de caractères multi-octets et larges ANSI

La valeur de `MB_CUR_MAX` correspond au nombre maximal d’octets dans un caractère multi-octets pour les paramètres régionaux actuels.

## <a name="see-also"></a>Voir aussi

[_mbclen, mblen, _mblen_l](../c-runtime-library/reference/mbclen-mblen-mblen-l.md)   
[mbstowcs, _mbstowcs_l](../c-runtime-library/reference/mbstowcs-mbstowcs-l.md)   
[mbtowc, _mbtowc_l](../c-runtime-library/reference/mbtowc-mbtowc-l.md)   
[&#95;&#95;&#95;mb_cur_max_func, &#95;&#95;&#95;mb_cur_max_l_func, &#95;&#95;p&#95;&#95;&#95;mb_cur_max, &#95;&#95;mb_cur_max](../c-runtime-library/mb-cur-max-func-mb-cur-max-l-func-p-mb-cur-max-mb-cur-max.md)   
[Types standard](../c-runtime-library/standard-types.md)   
[wcstombs, _wcstombs_l](../c-runtime-library/reference/wcstombs-wcstombs-l.md)   
[wctomb, _wctomb_l](../c-runtime-library/reference/wctomb-wctomb-l.md)   
[Constantes de types de données](../c-runtime-library/data-type-constants.md)   
[Constantes globales](../c-runtime-library/global-constants.md)