---
title: Classe de CD2DBitmapBrush | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CD2DBitmapBrush
- AFXRENDERTARGET/CD2DBitmapBrush
- AFXRENDERTARGET/CD2DBitmapBrush::CD2DBitmapBrush
- AFXRENDERTARGET/CD2DBitmapBrush::Attach
- AFXRENDERTARGET/CD2DBitmapBrush::Create
- AFXRENDERTARGET/CD2DBitmapBrush::Destroy
- AFXRENDERTARGET/CD2DBitmapBrush::Detach
- AFXRENDERTARGET/CD2DBitmapBrush::Get
- AFXRENDERTARGET/CD2DBitmapBrush::GetBitmap
- AFXRENDERTARGET/CD2DBitmapBrush::GetExtendModeX
- AFXRENDERTARGET/CD2DBitmapBrush::GetExtendModeY
- AFXRENDERTARGET/CD2DBitmapBrush::GetInterpolationMode
- AFXRENDERTARGET/CD2DBitmapBrush::SetBitmap
- AFXRENDERTARGET/CD2DBitmapBrush::SetExtendModeX
- AFXRENDERTARGET/CD2DBitmapBrush::SetExtendModeY
- AFXRENDERTARGET/CD2DBitmapBrush::SetInterpolationMode
- AFXRENDERTARGET/CD2DBitmapBrush::CommonInit
- AFXRENDERTARGET/CD2DBitmapBrush::m_pBitmap
- AFXRENDERTARGET/CD2DBitmapBrush::m_pBitmapBrush
- AFXRENDERTARGET/CD2DBitmapBrush::m_pBitmapBrushProperties
dev_langs:
- C++
helpviewer_keywords:
- CD2DBitmapBrush [MFC], CD2DBitmapBrush
- CD2DBitmapBrush [MFC], Attach
- CD2DBitmapBrush [MFC], Create
- CD2DBitmapBrush [MFC], Destroy
- CD2DBitmapBrush [MFC], Detach
- CD2DBitmapBrush [MFC], Get
- CD2DBitmapBrush [MFC], GetBitmap
- CD2DBitmapBrush [MFC], GetExtendModeX
- CD2DBitmapBrush [MFC], GetExtendModeY
- CD2DBitmapBrush [MFC], GetInterpolationMode
- CD2DBitmapBrush [MFC], SetBitmap
- CD2DBitmapBrush [MFC], SetExtendModeX
- CD2DBitmapBrush [MFC], SetExtendModeY
- CD2DBitmapBrush [MFC], SetInterpolationMode
- CD2DBitmapBrush [MFC], CommonInit
- CD2DBitmapBrush [MFC], m_pBitmap
- CD2DBitmapBrush [MFC], m_pBitmapBrush
- CD2DBitmapBrush [MFC], m_pBitmapBrushProperties
ms.assetid: 46ebbe34-66e0-44c8-af1d-d129e851de5e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d8fb0833fc82895f1f32fb5c93a6e6519bfe119c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33354619"
---
# <a name="cd2dbitmapbrush-class"></a>CD2DBitmapBrush, classe
Wrapper pour ID2D1BitmapBrush.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CD2DBitmapBrush : public CD2DBrush;  
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CD2DBitmapBrush::CD2DBitmapBrush](#cd2dbitmapbrush)|Surchargé. Construit un objet CD2DBitmapBrush à partir du fichier.|  
|[CD2DBitmapBrush :: ~ CD2DBitmapBrush](#dtor)|Destructeur. Appelé lorsqu’un objet de pinceau d’image bitmap D2D est détruit.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[CD2DBitmapBrush::Attach](#attach)|Attache existant à l’objet interface de la ressource|  
|[CD2DBitmapBrush::Create](#create)|Crée un CD2DBitmapBrush. (Substitue [CD2DResource::Create](../../mfc/reference/cd2dresource-class.md#create).)|  
|[CD2DBitmapBrush::Destroy](#destroy)|Détruit un objet CD2DBitmapBrush. (Substitue [CD2DBrush::Destroy](../../mfc/reference/cd2dbrush-class.md#destroy).)|  
|[CD2DBitmapBrush::Detach](#detach)|Détache l’interface de la ressource à partir de l’objet|  
|[CD2DBitmapBrush::Get](#get)|Renvoie l’interface ID2D1BitmapBrush|  
|[CD2DBitmapBrush::GetBitmap](#getbitmap)|Obtient la source de l’image bitmap que ce pinceau utilise pour peindre|  
|[CD2DBitmapBrush::GetExtendModeX](#getextendmodex)|Obtient la méthode par laquelle le pinceau dispose en mosaïque horizontale les zones qui s’étendent au-delà de sa bitmap|  
|[CD2DBitmapBrush::GetExtendModeY](#getextendmodey)|Obtient la méthode par laquelle le pinceau dispose en mosaïque verticale les zones qui s’étendent au-delà de sa bitmap|  
|[CD2DBitmapBrush::GetInterpolationMode](#getinterpolationmode)|Obtient la méthode d’interpolation utilisée lorsque l’image bitmap du pinceau est mis à l’échelle ou pivotée|  
|[CD2DBitmapBrush::SetBitmap](#setbitmap)|Spécifie la source de l’image bitmap que ce pinceau utilise pour peindre|  
|[CD2DBitmapBrush::SetExtendModeX](#setextendmodex)|Spécifie la manière dont le pinceau dispose en mosaïque horizontale les zones qui s’étendent au-delà de sa bitmap|  
|[CD2DBitmapBrush::SetExtendModeY](#setextendmodey)|Spécifie la façon dont le pinceau dispose en mosaïque verticale les zones qui s’étendent au-delà de sa bitmap|  
|[CD2DBitmapBrush::SetInterpolationMode](#setinterpolationmode)|Spécifie le mode d’interpolation utilisé lorsque l’image bitmap du pinceau est mis à l’échelle ou pivotée|  
  
### <a name="protected-methods"></a>Méthodes protégées  
  
|Nom|Description|  
|----------|-----------------|  
|[CD2DBitmapBrush::CommonInit](#commoninit)|Initialise l’objet|  
  
### <a name="public-operators"></a>Op&#233;rateurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CD2DBitmapBrush::operator ID2D1BitmapBrush *](#operator_id2d1bitmapbrush_star)|Renvoie l’interface ID2D1BitmapBrush|  
  
### <a name="protected-data-members"></a>Membres de données protégés  
  
|Name|Description|  
|----------|-----------------|  
|[CD2DBitmapBrush::m_pBitmap](#m_pbitmap)|Stocke un pointeur vers un objet CD2DBitmap.|  
|[CD2DBitmapBrush::m_pBitmapBrush](#m_pbitmapbrush)|Stocke un pointeur vers un objet ID2D1BitmapBrush.|  
|[CD2DBitmapBrush::m_pBitmapBrushProperties](#m_pbitmapbrushproperties)|Propriétés de pinceau de la bitmap.|  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CD2DResource](../../mfc/reference/cd2dresource-class.md)  
  
 [CD2DBrush](../../mfc/reference/cd2dbrush-class.md)  
  
 `CD2DBitmapBrush`  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** afxrendertarget.h  
  
##  <a name="dtor"></a>  CD2DBitmapBrush :: ~ CD2DBitmapBrush  
 Destructeur. Appelé lorsqu’un objet de pinceau d’image bitmap D2D est détruit.  
  
```  
virtual ~CD2DBitmapBrush();
```  
  
##  <a name="attach"></a>  CD2DBitmapBrush::Attach  
 Attache existant à l’objet interface de la ressource  
  
```  
void Attach(ID2D1BitmapBrush* pResource);
```  
  
### <a name="parameters"></a>Paramètres  
 `pResource`  
 Interface de la ressource existante. Ne peut pas être NULL  
  
##  <a name="cd2dbitmapbrush"></a>  CD2DBitmapBrush::CD2DBitmapBrush  
 Construit un objet CD2DBitmapBrush.  
  
```  
CD2DBitmapBrush(
    CRenderTarget* pParentTarget,  
    D2D1_BITMAP_BRUSH_PROPERTIES* pBitmapBrushProperties = NULL,  
    CD2DBrushProperties* pBrushProperties = NULL,  
    BOOL bAutoDestroy = TRUE);

 
CD2DBitmapBrush(
    CRenderTarget* pParentTarget,  
    UINT uiResID,  
    LPCTSTR lpszType = NULL,  
    CD2DSizeU sizeDest = CD2DSizeU(0, 0), 
    D2D1_BITMAP_BRUSH_PROPERTIES* pBitmapBrushProperties = NULL,  
    CD2DBrushProperties* pBrushProperties = NULL,  
    BOOL bAutoDestroy = TRUE);

 
CD2DBitmapBrush(
    CRenderTarget* pParentTarget,  
    LPCTSTR lpszImagePath,  
    CD2DSizeU sizeDest = CD2DSizeU(0, 0), 
    D2D1_BITMAP_BRUSH_PROPERTIES* pBitmapBrushProperties = NULL,  
    CD2DBrushProperties* pBrushProperties = NULL,  
    BOOL bAutoDestroy = TRUE);
```  
  
### <a name="parameters"></a>Paramètres  
 `pParentTarget`  
 Pointeur vers la cible de rendu.  
  
 `pBitmapBrushProperties`  
 Pointeur vers les modes d’extension et le mode d’interpolation d’un pinceau d’image bitmap.  
  
 `pBrushProperties`  
 Pointeur vers l’opacité et de transformation d’un pinceau.  
  
 `bAutoDestroy`  
 Indique que l’objet sera détruit par le propriétaire (pParentTarget).  
  
 `uiResID`  
 Le numéro d’ID de ressource de la ressource.  
  
 `lpszType`  
 Pointeur vers une chaîne terminée par le caractère null qui contient le type de ressource.  
  
 `sizeDest`  
 Taille de la destination de la bitmap.  
  
 `lpszImagePath`  
 Pointeur vers une chaîne se terminant par null qui contient le nom du fichier.  
  
##  <a name="commoninit"></a>  CD2DBitmapBrush::CommonInit  
 Initialise l’objet  
  
```  
void CommonInit(D2D1_BITMAP_BRUSH_PROPERTIES* pBitmapBrushProperties);
```  
  
### <a name="parameters"></a>Paramètres  
 `pBitmapBrushProperties`  
 Pointeur vers les propriétés de pinceau d’image bitmap.  
  
##  <a name="create"></a>  CD2DBitmapBrush::Create  
 Crée un CD2DBitmapBrush.  
  
```  
virtual HRESULT Create(CRenderTarget* pRenderTarget);
```  
  
### <a name="parameters"></a>Paramètres  
 `pRenderTarget`  
 Pointeur vers la cible de rendu.  
  
### <a name="return-value"></a>Valeur de retour  
 Si la méthode réussit, elle retourne S_OK. Sinon, elle retourne un code d’erreur HRESULT.  
  
##  <a name="destroy"></a>  CD2DBitmapBrush::Destroy  
 Détruit un objet CD2DBitmapBrush.  
  
```  
virtual void Destroy();
```  
  
##  <a name="detach"></a>  CD2DBitmapBrush::Detach  
 Détache l’interface de la ressource à partir de l’objet  
  
```  
ID2D1BitmapBrush* Detach();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Pointeur vers l’interface de la ressource détaché.  
  
##  <a name="get"></a>  CD2DBitmapBrush::Get  
 Renvoie l’interface ID2D1BitmapBrush  
  
```  
ID2D1BitmapBrush* Get();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Pointeur vers une interface de ID2D1BitmapBrush ou NULL si l’objet n’est pas encore initialisé.  
  
##  <a name="getbitmap"></a>  CD2DBitmapBrush::GetBitmap  
 Obtient la source de l’image bitmap que ce pinceau utilise pour peindre  
  
```  
CD2DBitmap* GetBitmap();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Pointeur vers un objet de CD2DBitmap ou une valeur NULL si l’objet n’est pas encore initialisé.  
  
##  <a name="getextendmodex"></a>  CD2DBitmapBrush::GetExtendModeX  
 Obtient la méthode par laquelle le pinceau dispose en mosaïque horizontale les zones qui s’étendent au-delà de sa bitmap  
  
```  
D2D1_EXTEND_MODE GetExtendModeX() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Une valeur qui spécifie la manière dont le pinceau dispose en mosaïque horizontale les zones qui s’étendent au-delà de sa bitmap  
  
##  <a name="getextendmodey"></a>  CD2DBitmapBrush::GetExtendModeY  
 Obtient la méthode par laquelle le pinceau dispose en mosaïque verticale les zones qui s’étendent au-delà de sa bitmap  
  
```  
D2D1_EXTEND_MODE GetExtendModeY() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Une valeur qui spécifie la façon dont le pinceau dispose en mosaïque verticale les zones qui s’étendent au-delà de sa bitmap  
  
##  <a name="getinterpolationmode"></a>  CD2DBitmapBrush::GetInterpolationMode  
 Obtient la méthode d’interpolation utilisée lorsque l’image bitmap du pinceau est mis à l’échelle ou pivotée  
  
```  
D2D1_BITMAP_INTERPOLATION_MODE GetInterpolationMode() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 La méthode d’interpolation utilisée lorsque l’image bitmap du pinceau est mis à l’échelle ou pivotée  
  
##  <a name="m_pbitmap"></a>  CD2DBitmapBrush::m_pBitmap  
 Stocke un pointeur vers un objet CD2DBitmap.  
  
```  
CD2DBitmap* m_pBitmap;  
```  
  
##  <a name="m_pbitmapbrush"></a>  CD2DBitmapBrush::m_pBitmapBrush  
 Stocke un pointeur vers un objet ID2D1BitmapBrush.  
  
```  
ID2D1BitmapBrush* m_pBitmapBrush;  
```  
  
##  <a name="m_pbitmapbrushproperties"></a>  CD2DBitmapBrush::m_pBitmapBrushProperties  
 Propriétés de pinceau de la bitmap.  
  
```  
D2D1_BITMAP_BRUSH_PROPERTIES* m_pBitmapBrushProperties;  
```  
  
##  <a name="operator_id2d1bitmapbrush_star"></a>  CD2DBitmapBrush::operator ID2D1BitmapBrush *  
 Renvoie l’interface ID2D1BitmapBrush  
  
```  
operator ID2D1BitmapBrush*();
```   
  
### <a name="return-value"></a>Valeur de retour  
 Pointeur vers une interface de ID2D1BitmapBrush ou NULL si l’objet n’est pas encore initialisé.  
  
##  <a name="setbitmap"></a>  CD2DBitmapBrush::SetBitmap  
 Spécifie la source de l’image bitmap que ce pinceau utilise pour peindre  
  
```  
void SetBitmap(CD2DBitmap* pBitmap);
```  
  
### <a name="parameters"></a>Paramètres  
 `pBitmap`  
 L’image bitmap source utilisée par le pinceau  
  
##  <a name="setextendmodex"></a>  CD2DBitmapBrush::SetExtendModeX  
 Spécifie la manière dont le pinceau dispose en mosaïque horizontale les zones qui s’étendent au-delà de sa bitmap  
  
```  
void SetExtendModeX(D2D1_EXTEND_MODE extendModeX);
```  
  
### <a name="parameters"></a>Paramètres  
 `extendModeX`  
 Une valeur qui spécifie la manière dont le pinceau dispose en mosaïque horizontale les zones qui s’étendent au-delà de sa bitmap  
  
##  <a name="setextendmodey"></a>  CD2DBitmapBrush::SetExtendModeY  
 Spécifie la façon dont le pinceau dispose en mosaïque verticale les zones qui s’étendent au-delà de sa bitmap  
  
```  
void SetExtendModeY(D2D1_EXTEND_MODE extendModeY);
```  
  
### <a name="parameters"></a>Paramètres  
 `extendModeY`  
 Une valeur qui spécifie la façon dont le pinceau dispose en mosaïque verticale les zones qui s’étendent au-delà de sa bitmap  
  
##  <a name="setinterpolationmode"></a>  CD2DBitmapBrush::SetInterpolationMode  
 Spécifie le mode d’interpolation utilisé lorsque l’image bitmap du pinceau est mis à l’échelle ou pivotée  
  
```  
void SetInterpolationMode(D2D1_BITMAP_INTERPOLATION_MODE interpolationMode);
```  
  
### <a name="parameters"></a>Paramètres  
 `interpolationMode`  
 Le mode d’interpolation utilisé lorsque l’image bitmap du pinceau est mis à l’échelle ou pivotée  
  
## <a name="see-also"></a>Voir aussi  
 [Classes](../../mfc/reference/mfc-classes.md)
