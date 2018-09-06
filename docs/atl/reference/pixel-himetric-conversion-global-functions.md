---
title: Fonctions globales de Conversion pixel-HIMETRIC | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- atlwin/ATL::AtlHiMetricToPixel
- atlwin/ATL::AtlPixelToHiMetric
dev_langs:
- C++
ms.assetid: ecb1b1b2-7e9d-4fbc-a855-16252d2d794c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 086310efe565e060645320db30526b03d57a68af
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43752408"
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

*lpSizeInHiMetric*  
[in] Pointeur vers la taille de l’objet en unités HIMETRIC.

*lpSizeInPix*  
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

*lpSizeInPix*  
[in] Pointeur vers la taille de l’objet en pixels.

*lpSizeInHiMetric*  
[out] Pointeur vers l’emplacement où la taille l’objet en unités HIMETRIC à retourner.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_COM#51](../../atl/codesnippet/cpp/pixel-himetric-conversion-global-functions_2.cpp)]  

### <a name="requirements"></a>Configuration requise

**En-tête :** atlwin.h  

## <a name="see-also"></a>Voir aussi

[Fonctions](../../atl/reference/atl-functions.md)
