---
title: CD2DBrushProperties, classe
ms.date: 11/04/2016
f1_keywords:
- CD2DBrushProperties
- AFXRENDERTARGET/CD2DBrushProperties
- AFXRENDERTARGET/CD2DBrushProperties::CD2DBrushProperties
- AFXRENDERTARGET/CD2DBrushProperties::CommonInit
helpviewer_keywords:
- CD2DBrushProperties [MFC], CD2DBrushProperties
- CD2DBrushProperties [MFC], CommonInit
ms.assetid: c77d717f-0a16-4d74-b2ce-0ae1766ed6f9
ms.openlocfilehash: 2db720fd09c62f8b86baecea9229d946f3892333
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754187"
---
# <a name="cd2dbrushproperties-class"></a>CD2DBrushProperties, classe

Wrapper pour `D2D1_BRUSH_PROPERTIES`.

## <a name="syntax"></a>Syntaxe

```
class CD2DBrushProperties : public D2D1_BRUSH_PROPERTIES;
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CD2DBrushProperties::CD2DBrushProperties](#cd2dbrushproperties)|Surchargé. Crée `CD2D_BRUSH_PROPERTIES` une structure|

### <a name="protected-methods"></a>Méthodes protégées

|Nom|Description|
|----------|-----------------|
|[CD2DBrushProperties::CommonInit](#commoninit)|Initialise l’objet|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`D2D1_BRUSH_PROPERTIES`

`CD2DBrushProperties`

## <a name="requirements"></a>Spécifications

**En-tête:** afxrendertarget.h

## <a name="cd2dbrushpropertiescd2dbrushproperties"></a><a name="cd2dbrushproperties"></a>CD2DBrushProperties::CD2DBrushProperties

Crée une structure CD2D_BRUSH_PROPERTIES

```
CD2DBrushProperties();
CD2DBrushProperties(FLOAT _opacity);

CD2DBrushProperties(
    D2D1_MATRIX_3X2_F _transform,
    FLOAT _opacity = 1.);
```

### <a name="parameters"></a>Paramètres

*_opacity*<br/>
L’opacité de base du pinceau. La valeur par défaut est 1,0.

*_transform*<br/>
La transformation à appliquer au pinceau

## <a name="cd2dbrushpropertiescommoninit"></a><a name="commoninit"></a>CD2DBrushProperties::CommonInit

Initialise l’objet

```cpp
void CommonInit();
```

## <a name="see-also"></a>Voir aussi

[Classes](../../mfc/reference/mfc-classes.md)
