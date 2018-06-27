---
title: Classe de CD2DLayer | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CD2DLayer
- AFXRENDERTARGET/CD2DLayer
- AFXRENDERTARGET/CD2DLayer::CD2DLayer
- AFXRENDERTARGET/CD2DLayer::Attach
- AFXRENDERTARGET/CD2DLayer::Create
- AFXRENDERTARGET/CD2DLayer::Destroy
- AFXRENDERTARGET/CD2DLayer::Detach
- AFXRENDERTARGET/CD2DLayer::Get
- AFXRENDERTARGET/CD2DLayer::GetSize
- AFXRENDERTARGET/CD2DLayer::IsValid
- AFXRENDERTARGET/CD2DLayer::m_pLayer
dev_langs:
- C++
helpviewer_keywords:
- CD2DLayer [MFC], CD2DLayer
- CD2DLayer [MFC], Attach
- CD2DLayer [MFC], Create
- CD2DLayer [MFC], Destroy
- CD2DLayer [MFC], Detach
- CD2DLayer [MFC], Get
- CD2DLayer [MFC], GetSize
- CD2DLayer [MFC], IsValid
- CD2DLayer [MFC], m_pLayer
ms.assetid: 2f96378e-66bb-40d1-9661-6afe324de3c1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d3a89cb258b7208346a76cd2a59eb8da40c38087
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/26/2018
ms.locfileid: "36950691"
---
# <a name="cd2dlayer-class"></a>CD2DLayer, classe
Wrapper pour ID2D1Layer.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CD2DLayer : public CD2DResource;  
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CD2DLayer::CD2DLayer](#cd2dlayer)|Construit un objet CD2DLayer.|  
|[CD2DLayer :: ~ CD2DLayer](#_dtorcd2dlayer)|Destructeur. Appelé lorsqu’un objet de couche D2D est détruit.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[CD2DLayer::Attach](#attach)|Attache existant à l’objet interface de la ressource|  
|[CD2DLayer::Create](#create)|Crée un CD2DLayer. (Substitue [CD2DResource::Create](../../mfc/reference/cd2dresource-class.md#create).)|  
|[CD2DLayer::Destroy](#destroy)|Détruit un objet CD2DLayer. (Substitue [CD2DResource::Destroy](../../mfc/reference/cd2dresource-class.md#destroy).)|  
|[CD2DLayer::Detach](#detach)|Détache l’interface de la ressource à partir de l’objet|  
|[CD2DLayer::Get](#get)|Renvoie l’interface ID2D1Layer|  
|[CD2DLayer::GetSize](#getsize)|Retourne la taille de la cible de rendu en pixels indépendants du périphérique|  
|[CD2DLayer::IsValid](#isvalid)|Vérifie la validité des ressources (remplace [CD2DResource::IsValid](../../mfc/reference/cd2dresource-class.md#isvalid).)|  
  
### <a name="public-operators"></a>Op&#233;rateurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CD2DLayer::operator ID2D1Layer *](#operator_id2d1layer_star)|Renvoie l’interface ID2D1Layer|  
  
### <a name="protected-data-members"></a>Membres de données protégés  
  
|Name|Description|  
|----------|-----------------|  
|[CD2DLayer::m_pLayer](#m_player)|Stocke un pointeur vers un objet ID2D1Layer.|  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CD2DResource](../../mfc/reference/cd2dresource-class.md)  
  
 `CD2DLayer`  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** afxrendertarget.h  
  
##  <a name="_dtorcd2dlayer"></a>  CD2DLayer :: ~ CD2DLayer  
 Destructeur. Appelé lorsqu’un objet de couche D2D est détruit.  
  
```  
virtual ~CD2DLayer();
```  
  
##  <a name="attach"></a>  CD2DLayer::Attach  
 Attache existant à l’objet interface de la ressource  
  
```  
void Attach(ID2D1Layer* pResource);
```  
  
### <a name="parameters"></a>Paramètres  
 *pResource*  
 Interface de la ressource existante. Ne peut pas être NULL  
  
##  <a name="cd2dlayer"></a>  CD2DLayer::CD2DLayer  
 Construit un objet CD2DLayer.  
  
```  
CD2DLayer(
    CRenderTarget* pParentTarget,  
    BOOL bAutoDestroy = TRUE);
```  
  
### <a name="parameters"></a>Paramètres  
 *pParentTarget*  
 Pointeur vers la cible de rendu.  
  
 *bAutoDestroy*  
 Indique que l’objet sera détruit par le propriétaire (pParentTarget).  
  
##  <a name="create"></a>  CD2DLayer::Create  
 Crée un CD2DLayer.  
  
```  
virtual HRESULT Create(CRenderTarget* pRenderTarget);
```  
  
### <a name="parameters"></a>Paramètres  
 *pRenderTarget*  
 Pointeur vers la cible de rendu.  
  
### <a name="return-value"></a>Valeur de retour  
 Si la méthode réussit, elle retourne S_OK. Sinon, elle retourne un code d’erreur HRESULT.  
  
##  <a name="destroy"></a>  CD2DLayer::Destroy  
 Détruit un objet CD2DLayer.  
  
```  
virtual void Destroy();
```  
  
##  <a name="detach"></a>  CD2DLayer::Detach  
 Détache l’interface de la ressource à partir de l’objet  
  
```  
ID2D1Layer* Detach();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Pointeur vers l’interface de la ressource détaché.  
  
##  <a name="get"></a>  CD2DLayer::Get  
 Renvoie l’interface ID2D1Layer  
  
```  
ID2D1Layer* Get();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Pointeur vers une interface de ID2D1Layer ou NULL si l’objet n’est pas encore initialisé.  
  
##  <a name="getsize"></a>  CD2DLayer::GetSize  
 Retourne la taille de la cible de rendu en pixels indépendants du périphérique  
  
```  
CD2DSizeF GetSize() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 La taille actuelle de la cible de rendu en pixels indépendants du périphérique  
  
##  <a name="isvalid"></a>  CD2DLayer::IsValid  
 Vérifications de validité des ressources  
  
```  
virtual BOOL IsValid() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 TRUE si la ressource est valide ; Sinon, FALSE.  
  
##  <a name="m_player"></a>  CD2DLayer::m_pLayer  
 Stocke un pointeur vers un objet ID2D1Layer.  
  
```  
ID2D1Layer* m_pLayer;  
```  
  
##  <a name="operator_id2d1layer_star"></a>  CD2DLayer::operator ID2D1Layer *  
 Renvoie l’interface ID2D1Layer  
  
```  
operator ID2D1Layer* ();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Pointeur vers une interface de ID2D1Layer ou NULL si l’objet n’est pas encore initialisé.  
  
## <a name="see-also"></a>Voir aussi  
 [Classes](../../mfc/reference/mfc-classes.md)
