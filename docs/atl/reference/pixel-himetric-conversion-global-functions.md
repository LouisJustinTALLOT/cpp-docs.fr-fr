---
title: Fonctions globales de conversion pixel-HIMETRIC
ms.date: 11/04/2016
f1_keywords:
- atlwin/ATL::AtlHiMetricToPixel
- atlwin/ATL::AtlPixelToHiMetric
ms.assetid: ecb1b1b2-7e9d-4fbc-a855-16252d2d794c
ms.openlocfilehash: 43a12985f259603a9b67f22f7a7891bf847c0b0f
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/06/2020
ms.locfileid: "78862914"
---
# <a name="pixelhimetric-conversion-global-functions"></a>Fonctions globales de conversion pixel/HIMETRIC

Ces fonctions assurent la prise en charge de la conversion vers et depuis les unités pixel et HIMETRIC.

> [!IMPORTANT]
>  Les fonctions listées dans le tableau suivant ne peuvent pas être utilisées dans les applications qui s’exécutent dans le Windows Runtime.

|||
|-|-|
|[AtlHiMetricToPixel](#atlhimetrictopixel)|Convertit les unités HIMETRIC (chaque unité est 0,01 millimètre) en pixels.|
|[AtlPixelToHiMetric](#atlpixeltohimetric)|Convertit les pixels en unités HIMETRIC (chaque unité est 0,01 millimètre).|

##  <a name="atlhimetrictopixel"></a>AtlHiMetricToPixel

Convertit la taille d'un objet en unités HIMETRIC (chaque unité représente 0,01 millimètre) vers une taille en pixels sur l'appareil à écran.

```
extern void AtlHiMetricToPixel(
    const SIZEL* lpSizeInHiMetric,
    LPSIZEL lpSizeInPix);
```

### <a name="parameters"></a>Paramètres

*lpSizeInHiMetric*<br/>
dans Pointeur vers la taille de l’objet en unités HIMETRIC.

*lpSizeInPix*<br/>
à Pointeur vers l’emplacement où la taille de l’objet, en pixels, doit être retournée.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_COM#49](../../atl/codesnippet/cpp/pixel-himetric-conversion-global-functions_1.cpp)]

### <a name="requirements"></a>Spécifications

**En-tête :** atlwin. h

##  <a name="atlpixeltohimetric"></a>AtlPixelToHiMetric

Convertit la taille d'un objet en pixels sur l'appareil à écran vers une taille en unités HIMETRIC (chaque unité représente 0,01 millimètre).

```
extern void AtlPixelToHiMetric(
    const SIZEL* lpSizeInPix,
    LPSIZEL lpSizeInHiMetric);
```

### <a name="parameters"></a>Paramètres

*lpSizeInPix*<br/>
dans Pointeur vers la taille de l’objet en pixels.

*lpSizeInHiMetric*<br/>
à Pointeur vers l’emplacement où la taille de l’objet en unités HIMETRIC doit être retournée.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_COM#51](../../atl/codesnippet/cpp/pixel-himetric-conversion-global-functions_2.cpp)]

### <a name="requirements"></a>Spécifications

**En-tête :** atlwin. h

## <a name="see-also"></a>Voir aussi

[Fonctions](../../atl/reference/atl-functions.md)
