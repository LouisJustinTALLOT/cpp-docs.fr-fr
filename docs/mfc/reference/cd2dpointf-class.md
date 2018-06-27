---
title: Classe de CD2DPointF | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CD2DPointF
- AFXRENDERTARGET/CD2DPointF
- AFXRENDERTARGET/CD2DPointF::CD2DPointF
dev_langs:
- C++
helpviewer_keywords:
- CD2DPointF [MFC], CD2DPointF
ms.assetid: 30f72083-1c8a-4f50-adb2-72dbbe3522d4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e23dbce668234fecc3162d52e0bbea6fb05a7b06
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/26/2018
ms.locfileid: "36957271"
---
# <a name="cd2dpointf-class"></a>CD2DPointF, classe
Wrapper pour `D2D1_POINT_2F`.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CD2DPointF : public D2D1_POINT_2F;  
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CD2DPointF::CD2DPointF](#cd2dpointf)|Surchargé. Construit un `CD2DPointF` à partir de l’objet `D2D1_POINT_2F` objet.|  
  
### <a name="public-operators"></a>Op&#233;rateurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CD2DPointF::operator CPoint](#operator_cpoint)|Convertit `CD2DPointF` à `CPoint` objet.|  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 `D2D1_POINT_2F`  
  
 `CD2DPointF`  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** afxrendertarget.h  
  
##  <a name="cd2dpointf"></a>  CD2DPointF::CD2DPointF  
 Construit un objet CD2DPointF à partir de l’objet CPoint.  
  
```  
CD2DPointF(const CPoint& pt);    
CD2DPointF(const D2D1_POINT_2F& pt);    
CD2DPointF(const D2D1_POINT_2F* pt); 
CD2DPointF(FLOAT fX = 0., FLOAT fY = 0.);
```  
  
### <a name="parameters"></a>Paramètres  
 *pt*  
 point de code source  
  
 *fX*  
 source X  
  
 *année fiscale*  
 source Y  
  
##  <a name="operator_cpoint"></a>  CD2DPointF::operator CPoint  
 Convertit CD2DPointF en objet CPoint.  
  
```  
operator CPoint();
```   
  
### <a name="return-value"></a>Valeur de retour  
 Valeur actuelle du point de D2D.  
  
## <a name="see-also"></a>Voir aussi  
 [Classes](../../mfc/reference/mfc-classes.md)
