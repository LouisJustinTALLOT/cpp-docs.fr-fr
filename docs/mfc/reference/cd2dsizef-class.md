---
title: Classe de CD2DSizeF | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CD2DSizeF
- AFXRENDERTARGET/CD2DSizeF
- AFXRENDERTARGET/CD2DSizeF::CD2DSizeF
- AFXRENDERTARGET/CD2DSizeF::IsNull
dev_langs:
- C++
helpviewer_keywords:
- CD2DSizeF [MFC], CD2DSizeF
- CD2DSizeF [MFC], IsNull
ms.assetid: f486a1e1-997d-4286-8cb9-26369dc82055
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e939d189d991ef234e940b272291c2da6c931684
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/26/2018
ms.locfileid: "36954476"
---
# <a name="cd2dsizef-class"></a>CD2DSizeF, classe
Wrapper pour D2D1_SIZE_F.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CD2DSizeF : public D2D1_SIZE_F;  
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CD2DSizeF::CD2DSizeF](#cd2dsizef)|Surchargé. Construit un `CD2DSizeF` à partir de l’objet `D2D1_SIZE_F` objet.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[CD2DSizeF::IsNull](#isnull)|Retourne un **booléenne** valeur qui indique si une expression ne contient aucune donnée valide ( **null**).|  
  
### <a name="public-operators"></a>Op&#233;rateurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CD2DSizeF::operator CSize](#operator_csize)|Convertit `CD2DSizeF` à `CSize` objet.|  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 `D2D1_SIZE_F`  
  
 [CD2DSizeF](../../mfc/reference/cd2dsizef-class.md)  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** afxrendertarget.h  
  
##  <a name="cd2dsizef"></a>  CD2DSizeF::CD2DSizeF  
 Construit un objet CD2DSizeF à partir de l’objet CSize.  
  
```  
CD2DSizeF(const CSize& size);  
CD2DSizeF(const D2D1_SIZE_F& size);  
  CD2DSizeF(const D2D1_SIZE_F* size);

 
CD2DSizeF(
    FLOAT cx = 0.,  
    FLOAT cy = 0.);
```  
  
### <a name="parameters"></a>Paramètres  
 *size*  
 taille de la source  
  
 *CX*  
 largeur de la source  
  
 *CY*  
 hauteur de la source  
  
##  <a name="isnull"></a>  CD2DSizeF::IsNull  
 Retourne une valeur booléenne qui indique si une expression ne contient aucune donnée valide (Null).  
  
```  
BOOL IsNull() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 TRUE si la largeur et la hauteur sont vides ; Sinon, FALSE.  
  
##  <a name="operator_csize"></a>  CD2DSizeF::operator CSize  
 Convertit CD2DSizeF en objet CSize.  
  
```  
operator CSize();
```   
  
### <a name="return-value"></a>Valeur de retour  
 Valeur actuelle de la taille de D2D.  
  
## <a name="see-also"></a>Voir aussi  
 [Classes](../../mfc/reference/mfc-classes.md)
