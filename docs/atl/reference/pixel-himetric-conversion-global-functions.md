---
title: Fonctions globales de conversion Pixel-HIMETRIC
ms.date: 11/04/2016
f1_keywords:
- atlwin/ATL::AtlHiMetricToPixel
- atlwin/ATL::AtlPixelToHiMetric
ms.assetid: ecb1b1b2-7e9d-4fbc-a855-16252d2d794c
ms.openlocfilehash: 08c72c0d8f3d061950d6945d9fb412c0a16355da
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326146"
---
# <a name="pixelhimetric-conversion-global-functions"></a>Fonctions globales de conversion Pixel/HIMETRIC

Ces fonctions fournissent un support pour la conversion aux unités pixel et HIMETRIC.

> [!IMPORTANT]
> Les fonctions énumérées dans le tableau suivant ne peuvent pas être utilisées dans les applications qui s’exécutent dans le Windows Runtime.

|||
|-|-|
|[AtlHiMetricToPixel](#atlhimetrictopixel)|Convertit les unités HIMETRIC (chaque unité est de 0,01 millimètre) en pixels.|
|[AtlPixelToHiMetric](#atlpixeltohimetric)|Convertit les pixels en unités HIMETRIC (chaque unité mesure 0,01 millimètre).|

## <a name="atlhimetrictopixel"></a><a name="atlhimetrictopixel"></a>AtlHiMetricToPixel

Convertit la taille d'un objet en unités HIMETRIC (chaque unité représente 0,01 millimètre) vers une taille en pixels sur l'appareil à écran.

```
extern void AtlHiMetricToPixel(
    const SIZEL* lpSizeInHiMetric,
    LPSIZEL lpSizeInPix);
```

### <a name="parameters"></a>Paramètres

*lpSizeInHiMetric*<br/>
[dans] Pointeur sur la taille de l’objet dans les unités HIMETRIC.

*lpSizeInPix*<br/>
[out] Pointeur à l’endroit où la taille de l’objet en pixels doit être retourné.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_COM#49](../../atl/codesnippet/cpp/pixel-himetric-conversion-global-functions_1.cpp)]

### <a name="requirements"></a>Spécifications

**En-tête:** atlwin.h

## <a name="atlpixeltohimetric"></a><a name="atlpixeltohimetric"></a>AtlPixelToHiMetric

Convertit la taille d'un objet en pixels sur l'appareil à écran vers une taille en unités HIMETRIC (chaque unité représente 0,01 millimètre).

```
extern void AtlPixelToHiMetric(
    const SIZEL* lpSizeInPix,
    LPSIZEL lpSizeInHiMetric);
```

### <a name="parameters"></a>Paramètres

*lpSizeInPix*<br/>
[dans] Pointeur sur la taille de l’objet en pixels.

*lpSizeInHiMetric*<br/>
[out] Pointeur à l’endroit où la taille de l’objet dans les unités HIMETRIC doit être retourné.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_COM#51](../../atl/codesnippet/cpp/pixel-himetric-conversion-global-functions_2.cpp)]

### <a name="requirements"></a>Spécifications

**En-tête:** atlwin.h

## <a name="see-also"></a>Voir aussi

[Fonctions](../../atl/reference/atl-functions.md)
