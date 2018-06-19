---
title: CD2DBrushProperties classe | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CD2DBrushProperties
- AFXRENDERTARGET/CD2DBrushProperties
- AFXRENDERTARGET/CD2DBrushProperties::CD2DBrushProperties
- AFXRENDERTARGET/CD2DBrushProperties::CommonInit
dev_langs:
- C++
helpviewer_keywords:
- CD2DBrushProperties [MFC], CD2DBrushProperties
- CD2DBrushProperties [MFC], CommonInit
ms.assetid: c77d717f-0a16-4d74-b2ce-0ae1766ed6f9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d9b21777ba272819c9921aed90ede185b759ba45
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33349946"
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
|[CD2DBrushProperties::CD2DBrushProperties](#cd2dbrushproperties)|Surchargé. Crée un `CD2D_BRUSH_PROPERTIES` structure|  
  
### <a name="protected-methods"></a>Méthodes protégées  
  
|Nom|Description|  
|----------|-----------------|  
|[CD2DBrushProperties::CommonInit](#commoninit)|Initialise l’objet|  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 `D2D1_BRUSH_PROPERTIES`  
  
 `CD2DBrushProperties`  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** afxrendertarget.h  
  
##  <a name="cd2dbrushproperties"></a>  CD2DBrushProperties::CD2DBrushProperties  
 Crée une structure CD2D_BRUSH_PROPERTIES  
  
```  
CD2DBrushProperties();  
CD2DBrushProperties(FLOAT _opacity);

 
CD2DBrushProperties(
    D2D1_MATRIX_3X2_F _transform,  
    FLOAT _opacity = 1.);
```  
  
### <a name="parameters"></a>Paramètres  
 `_opacity`  
 Opacité de base du pinceau. La valeur par défaut est 1,0.  
  
 `_transform`  
 La transformation à appliquer au pinceau  
  
##  <a name="commoninit"></a>  CD2DBrushProperties::CommonInit  
 Initialise l’objet  
  
```  
void CommonInit();
```  
  
## <a name="see-also"></a>Voir aussi  
 [Classes](../../mfc/reference/mfc-classes.md)
