---
title: Fonctions globales de Conversion pixel-HIMETRIC
ms.date: 11/04/2016
f1_keywords:
- atlwin/ATL::AtlHiMetricToPixel
- atlwin/ATL::AtlPixelToHiMetric
ms.assetid: ecb1b1b2-7e9d-4fbc-a855-16252d2d794c
ms.openlocfilehash: 43a12985f259603a9b67f22f7a7891bf847c0b0f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62276833"
---
# <a name="pixelhimetric-conversion-global-functions"></a>Fonctions globales de Conversion pixel/HIMETRIC

Ces fonctions prennent en charge la conversion vers et depuis le pixel et unités HIMETRIC.

> [!IMPORTANT]
>  Les fonctions répertoriées dans le tableau suivant ne peut pas être utilisées dans les applications qui s’exécutent dans le Windows Runtime.

|||
|-|-|
|[AtlHiMetricToPixel](#atlhimetrictopixel)|Convertit des unités HIMETRIC (chaque unité représente 0,01 millimètre) en pixels.|
|[AtlPixelToHiMetric](#atlpixeltohimetric)|Convertit des pixels en unités HIMETRIC (chaque unité représente 0,01 millimètre).|

##  <a name="atlhimetrictopixel"></a>  AtlHiMetricToPixel

Convertit la taille d'un objet en unités HIMETRIC (chaque unité représente 0,01 millimètre) vers une taille en pixels sur l'appareil à écran.

```
extern void AtlHiMetricToPixel(
    const SIZEL* lpSizeInHiMetric,
    LPSIZEL lpSizeInPix);
```

### <a name="parameters"></a>Paramètres

*lpSizeInHiMetric*<br/>
[in] Pointeur vers la taille de l’objet en unités HIMETRIC.

*lpSizeInPix*<br/>
[out] Pointeur vers l’emplacement où la taille l’objet en pixels à retourner.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_COM#49](../../atl/codesnippet/cpp/pixel-himetric-conversion-global-functions_1.cpp)]

### <a name="requirements"></a>Configuration requise

**En-tête :** atlwin.h

##  <a name="atlpixeltohimetric"></a>  AtlPixelToHiMetric

Convertit la taille d'un objet en pixels sur l'appareil à écran vers une taille en unités HIMETRIC (chaque unité représente 0,01 millimètre).

```
extern void AtlPixelToHiMetric(
    const SIZEL* lpSizeInPix,
    LPSIZEL lpSizeInHiMetric);
```

### <a name="parameters"></a>Paramètres

*lpSizeInPix*<br/>
[in] Pointeur vers la taille de l’objet en pixels.

*lpSizeInHiMetric*<br/>
[out] Pointeur vers l’emplacement où la taille l’objet en unités HIMETRIC à retourner.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_COM#51](../../atl/codesnippet/cpp/pixel-himetric-conversion-global-functions_2.cpp)]

### <a name="requirements"></a>Configuration requise

**En-tête :** atlwin.h

## <a name="see-also"></a>Voir aussi

[Fonctions](../../atl/reference/atl-functions.md)
