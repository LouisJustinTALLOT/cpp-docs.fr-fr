---
title: Classe de CD2DRectF | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CD2DRectF
- AFXRENDERTARGET/CD2DRectF
- AFXRENDERTARGET/CD2DRectF::CD2DRectF
- AFXRENDERTARGET/CD2DRectF::IsNull
dev_langs:
- C++
helpviewer_keywords:
- CD2DRectF [MFC], CD2DRectF
- CD2DRectF [MFC], IsNull
ms.assetid: 87c12d87-9d18-4a19-ba14-0f51d6b6835a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ec43e6bb14b9c5629bde60faec80d9e31e2e5188
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33350795"
---
# <a name="cd2drectf-class"></a>CD2DRectF, classe
Wrapper pour `D2D1_RECT_F`.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CD2DRectF : public D2D1_RECT_F;  
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CD2DRectF::CD2DRectF](#cd2drectf)|Surchargé. Construit un `CD2DRectF` à partir de l’objet `D2D1_RECT_F` objet.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[CD2DRectF::IsNull](#isnull)|Retourne un `boolean` valeur qui indique si une expression ne contient aucune donnée valide ( `null`).|  
  
### <a name="public-operators"></a>Op&#233;rateurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CD2DRectF::operator CRect](#operator_crect)|Convertit `CD2DRectF` à `CRect` objet.|  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 `D2D1_RECT_F`  
  
 `CD2DRectF`  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** afxrendertarget.h  
  
##  <a name="cd2drectf"></a>  CD2DRectF::CD2DRectF  
 Construit un objet CD2DRectF à partir de l’objet CRect.  
  
```  
CD2DRectF(const CRect& rect);  
CD2DRectF(const D2D1_RECT_F& rect);  
  CD2DRectF(const D2D1_RECT_F* rect);

 
CD2DRectF(
    FLOAT fLeft = 0.,  
    FLOAT fTop = 0.,  
    FLOAT fRight = 0.,  
    FLOAT fBottom = 0.);
```  
  
### <a name="parameters"></a>Paramètres  
 `rect`  
 rectangle source  
  
 `fLeft`  
 Coordonnée gauche source  
  
 `fTop`  
 coordonnée supérieure source  
  
 `fRight`  
 coordonnée droite source  
  
 `fBottom`  
 Coordonnée inférieure source  
  
##  <a name="isnull"></a>  CD2DRectF::IsNull  
 Retourne une valeur booléenne qui indique si une expression ne contient aucune donnée valide (Null).  
  
```  
BOOL IsNull() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 TRUE si le du rectangle haut, gauche, bas et valeurs sont toujours égaux à 0 ; Sinon, FALSE.  
  
##  <a name="operator_crect"></a>  CD2DRectF::operator CRect  
 Convertit CD2DRectF en objet CRect.  
  
```  
operator CRect();
```   
  
### <a name="return-value"></a>Valeur de retour  
 Valeur actuelle du rectangle de D2D.  
  
## <a name="see-also"></a>Voir aussi  
 [Classes](../../mfc/reference/mfc-classes.md)
