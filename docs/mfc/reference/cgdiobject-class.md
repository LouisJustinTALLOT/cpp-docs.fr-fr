---
title: CGdiObject, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CGdiObject
- AFXWIN/CGdiObject
- AFXWIN/CGdiObject::CGdiObject
- AFXWIN/CGdiObject::Attach
- AFXWIN/CGdiObject::CreateStockObject
- AFXWIN/CGdiObject::DeleteObject
- AFXWIN/CGdiObject::DeleteTempMap
- AFXWIN/CGdiObject::Detach
- AFXWIN/CGdiObject::FromHandle
- AFXWIN/CGdiObject::GetObject
- AFXWIN/CGdiObject::GetObjectType
- AFXWIN/CGdiObject::GetSafeHandle
- AFXWIN/CGdiObject::UnrealizeObject
- AFXWIN/CGdiObject::m_hObject
dev_langs:
- C++
helpviewer_keywords:
- CGdiObject [MFC], CGdiObject
- CGdiObject [MFC], Attach
- CGdiObject [MFC], CreateStockObject
- CGdiObject [MFC], DeleteObject
- CGdiObject [MFC], DeleteTempMap
- CGdiObject [MFC], Detach
- CGdiObject [MFC], FromHandle
- CGdiObject [MFC], GetObject
- CGdiObject [MFC], GetObjectType
- CGdiObject [MFC], GetSafeHandle
- CGdiObject [MFC], UnrealizeObject
- CGdiObject [MFC], m_hObject
ms.assetid: 1cba3ba5-3d49-4e43-8293-209299f2f6f4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e72c7ea788085f25dc2a4ec1b2f8682df9e20b25
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/29/2018
ms.locfileid: "43209125"
---
# <a name="cgdiobject-class"></a>CGdiObject, classe
Fournit une classe de base pour différents genres d'objets GDI (Graphics Device Interface) Windows, par exemple des images bitmap, des zones, des pinceaux, des plumes, des palettes et des polices.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CGdiObject : public CObject  
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CGdiObject::CGdiObject](#cgdiobject)|Construit un objet `CGdiObject`.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[CGdiObject::Attach](#attach)|Attache un objet GDI de Windows vers un `CGdiObject` objet.|  
|[CGdiObject::CreateStockObject](#createstockobject)|Récupère un handle vers un des stylets stocks prédéfinis de Windows, des pinceaux ou des polices.|  
|[CGdiObject::DeleteObject](#deleteobject)|Supprime l’objet Windows GDI attaché à la `CGdiObject` objet de la mémoire en libérant tout le stockage système associé à l’objet.|  
|[CGdiObject::DeleteTempMap](#deletetempmap)|Supprime tout temporaire `CGdiObject` objets créés par `FromHandle`.|  
|[CGdiObject::Detach](#detach)|Détache un objet GDI de Windows à partir d’un `CGdiObject` de l’objet et retourne un handle vers l’objet GDI de Windows.|  
|[CGdiObject::FromHandle](#fromhandle)|Retourne un pointeur vers un `CGdiObject` objet en fonction d’un handle à un objet GDI de Windows.|  
|[CGdiObject::GetObject](#getobject)|Remplit une mémoire tampon avec des données qui décrit l’objet Windows GDI attaché à la `CGdiObject` objet.|  
|[CGdiObject::GetObjectType](#getobjecttype)|Récupère le type de l’objet GDI.|  
|[CGdiObject::GetSafeHandle](#getsafehandle)|Retourne `m_hObject` , sauf si **cela** est NULL, auquel cas NULL est retournée.|  
|[CGdiObject::UnrealizeObject](#unrealizeobject)|Réinitialise l’origine d’un pinceau ou réinitialise une palette logique.|  
  
### <a name="public-operators"></a>Op&#233;rateurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CGdiObject::operator ! =](#operator_neq)|Détermine si deux objets GDI sont logiquement pas égaux.|  
|[CGdiObject::operator ==](#operator_eq_eq)|Détermine si deux objets GDI sont logiquement égales.|  
|[CGdiObject::operator HGDIOBJ](#operator_hgdiobj)|Récupère un HANDLE vers l’objet Windows GDI attaché.|  
  
### <a name="public-data-members"></a>Membres de données publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CGdiObject::m_hObject](#m_hobject)|Un HANDLE contenant le HBITMAP, HPALETTE, HRGN, HBRUSH, HPEN ou HFONT attaché à cet objet.|  
  
## <a name="remarks"></a>Notes  
 Vous ne créez jamais un `CGdiObject` directement. Au lieu de cela, vous créez un objet à partir d’une de ses classes dérivées, telles que `CPen` ou `CBrush`.  
  
 Pour plus d’informations sur `CGdiObject`, consultez [objets graphiques](../../mfc/graphic-objects.md).  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CGdiObject`  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** afxwin.h  
  
##  <a name="attach"></a>  CGdiObject::Attach  
 Attache un objet GDI de Windows vers un `CGdiObject` objet.  
  
```  
BOOL Attach(HGDIOBJ hObject);
```  
  
### <a name="parameters"></a>Paramètres  
 *hObject*  
 HANDLE vers un objet Windows GDI (par exemple, HPEN ou HBRUSH).  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si la pièce jointe a réussi ; sinon 0.  
  
##  <a name="cgdiobject"></a>  CGdiObject::CGdiObject  
 Construit un objet `CGdiObject`.  
  
```  
CGdiObject();
```  
  
### <a name="remarks"></a>Notes  
 Vous ne créez jamais un `CGdiObject` directement. Au lieu de cela, vous créez un objet à partir d’une de ses classes dérivées, telles que `CPen` ou `Cbrush`.  
  
##  <a name="createstockobject"></a>  CGdiObject::CreateStockObject  
 Récupère un handle vers un de le prédéfinis stock Windows GDI stylets, pinceaux ou polices et attache l’objet GDI pour le `CGdiObject` objet.  
  
```  
BOOL CreateStockObject(int nIndex);
```  
  
### <a name="parameters"></a>Paramètres  
 *nIndex*  
 Constante spécifiant le type d’objet de stock souhaité. Consultez le paramètre *fnObject* pour [GetStockObject](/windows/desktop/api/wingdi/nf-wingdi-getstockobject) dans le SDK Windows pour une description des valeurs appropriées.  
  
### <a name="return-value"></a>Valeur de retour  
 Une valeur différente de zéro si la fonction réussit ; sinon, 0.  
  
### <a name="remarks"></a>Notes  
 Appel de cette fonction avec l’un des dérivés des classes qui correspond au type d’objet Windows GDI, telles que `CPen` pour un stylet.  
  
##  <a name="deleteobject"></a>  CGdiObject::DeleteObject  
 Supprime l’objet de Windows GDI attaché à partir de la mémoire en libérant tout le stockage système associé à l’objet GDI de Windows.  
  
```  
BOOL DeleteObject();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si l’objet GDI a été supprimé avec succès ; sinon 0.  
  
### <a name="remarks"></a>Notes  
 Le stockage associé le `CGdiObject` objet n’est pas affecté par cet appel. Une application ne doit pas appeler `DeleteObject` sur un `CGdiObject` objet actuellement sélectionné dans un contexte de périphérique.  
  
 Lorsqu’un pinceau de modèle est supprimé, l’image bitmap associée au pinceau n’est pas supprimé. L’image bitmap doit être supprimé de manière indépendante.  
  
##  <a name="deletetempmap"></a>  CGdiObject::DeleteTempMap  
 Appelé automatiquement par le `CWinApp` Gestionnaire de durée d’inactivité, `DeleteTempMap` supprime temporaires `CGdiObject` objets créés par `FromHandle`.  
  
```  
static void PASCAL DeleteTempMap();
```  
  
### <a name="remarks"></a>Notes  
 `DeleteTempMap` Détache l’objet de Windows GDI attaché à une table temporaire `CGdiObject` objet avant de supprimer le `CGdiObject` objet.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFCDocView#175](../../mfc/codesnippet/cpp/cgdiobject-class_1.cpp)]  
  
##  <a name="detach"></a>  CGdiObject::Detach  
 Détache un objet GDI de Windows à partir d’un `CGdiObject` de l’objet et retourne un handle vers l’objet GDI de Windows.  
  
```  
HGDIOBJ Detach();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Un `HANDLE` pour l’interface GDI Windows objet détachée ; sinon, NULL si aucun objet GDI n’est attaché.  
  
##  <a name="fromhandle"></a>  CGdiObject::FromHandle  
 Retourne un pointeur vers un `CGdiObject` objet en fonction d’un handle à un objet GDI de Windows.  
  
```  
static CGdiObject* PASCAL FromHandle(HGDIOBJ hObject);
```  
  
### <a name="parameters"></a>Paramètres  
 *hObject*  
 HANDLE vers un objet GDI de Windows.  
  
### <a name="return-value"></a>Valeur de retour  
 Un pointeur vers un `CGdiObject` qui peut être temporaire ou permanent.  
  
### <a name="remarks"></a>Notes  
 Si un `CGdiObject` objet n’est pas déjà attaché à l’objet GDI de Windows, une table temporaire `CGdiObject` objet est créé et attaché.  
  
 Ce fichier temporaire `CGdiObject` objet est valide uniquement jusqu'à la prochaine fois que l’application a un temps d’inactivité dans sa boucle d’événement, moment auquel tous les objets graphiques temporaires sont supprimés. Une autre façon de dire cela est que l’objet temporaire est valide uniquement pendant le traitement du message d’une fenêtre.  
  
##  <a name="getobject"></a>  CGdiObject::GetObject  
 Remplit une mémoire tampon de données qui définit un objet spécifié.  
  
```  
int GetObject(
    int nCount,  
    LPVOID lpObject) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 *nCount*  
 Spécifie le nombre d’octets à copier dans le *lpObject* mémoire tampon.  
  
 *lpObject*  
 Pointe vers une mémoire tampon fournie par l’utilisateur qui doit recevoir les informations.  
  
### <a name="return-value"></a>Valeur de retour  
 Le nombre d’octets récupérés ; Sinon, 0 si une erreur se produit.  
  
### <a name="remarks"></a>Notes  
 La fonction récupère une structure de données dont le type varie selon le type d’objet de graphique, comme indiqué par la liste suivante :  
  
|Object|Type de tampon|  
|------------|-----------------|  
|`CPen`|[LOGPEN](../../mfc/reference/logpen-structure.md)|  
|`CBrush`|[LOGBRUSH](../../mfc/reference/logbrush-structure.md)|  
|`CFont`|[LOGFONT](/windows/desktop/api/wingdi/ns-wingdi-taglogfonta)|  
|`CBitmap`|[BITMAP](../../mfc/reference/bitmap-structure.md)|  
|`CPalette`|WORD|  
|`CRgn`|Non pris en charge|  
  
 Si l’objet est un `CBitmap` objet, `GetObject` retourne uniquement la largeur, hauteur et des informations de format de couleur de l’image bitmap. Les bits réels peuvent être récupérées à l’aide de [CBitmap::GetBitmapBits](../../mfc/reference/cbitmap-class.md#getbitmapbits).  
  
 Si l’objet est un `CPalette` objet, `GetObject` récupère un mot qui spécifie le nombre d’entrées dans la palette. La fonction ne récupère pas le [LOGPALETTE](/windows/desktop/api/wingdi/ns-wingdi-taglogpalette) structure qui définit la palette. Une application peut obtenir des informations sur les entrées de la palette en appelant [CPalette::GetPaletteEntries](../../mfc/reference/cpalette-class.md#getpaletteentries).  
  
##  <a name="getobjecttype"></a>  CGdiObject::GetObjectType  
 Récupère le type de l’objet GDI.  
  
```  
UINT GetObjectType() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Le type de l’objet, en cas de réussite ; sinon 0. Il peut avoir l’une des valeurs suivantes :  
  
- OBJ_BITMAP Bitmap  
  
- Pinceau OBJ_BRUSH  
  
- OBJ_FONT police  
  
- Palette OBJ_PAL  
  
- OBJ_PEN stylet  
  
- Stylet OBJ_EXTPEN étendu  
  
- Région OBJ_REGION  
  
- Contexte de périphérique de OBJ_DC  
  
- Contexte de périphérique de mémoire de OBJ_MEMDC  
  
- OBJ_METAFILE métafichier  
  
- Contexte de périphérique de métafichier de OBJ_METADC  
  
- OBJ_ENHMETAFILE Enhanced metafile  
  
- Contexte de périphérique de métafichier amélioré OBJ_ENHMETADC  
  
##  <a name="getsafehandle"></a>  CGdiObject::GetSafeHandle  
 Retourne `m_hObject` , sauf si **cela** est NULL, auquel cas NULL est retournée.  
  
```  
HGDIOBJ GetSafeHandle() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Un HANDLE vers l’objet Windows GDI attaché ; Sinon, NULL si aucun objet n’est attaché.  
  
### <a name="remarks"></a>Notes  
 Cela fait partie du paradigme interface handle général et est utile lorsque NULL est une valeur valide ou spéciale pour un handle.  
  
### <a name="example"></a>Exemple  
  Consultez l’exemple de [CWnd::IsWindowEnabled](../../mfc/reference/cwnd-class.md#iswindowenabled).  
  
##  <a name="m_hobject"></a>  CGdiObject::m_hObject  
 Un HANDLE contenant le HBITMAP, HRGN, HBRUSH, HPEN, HPALETTE ou HFONT attaché à cet objet.  
  
```  
HGDIOBJ m_hObject;  
```  
  
##  <a name="operator_neq"></a>  CGdiObject::operator ! =  
 Détermine si deux objets GDI sont logiquement pas égaux.  
  
```  
BOOL operator!=(const CGdiObject& obj) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 *obj*  
 Un pointeur vers un existant `CGdiObject`.  
  
### <a name="remarks"></a>Notes  
 Détermine si un objet GDI sur le côté gauche n’est pas égal à un objet GDI sur le côté droit.  
  
##  <a name="operator_eq_eq"></a>  CGdiObject::operator ==  
 Détermine si deux objets GDI sont logiquement égales.  
  
```  
BOOL operator==(const CGdiObject& obj) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 *obj*  
 Une référence à un existant `CGdiObject`.  
  
### <a name="remarks"></a>Notes  
 Détermine si un objet GDI sur le côté gauche est égal à un objet GDI sur le côté droit.  
  
##  <a name="operator_hgdiobj"></a>  CGdiObject::operator HGDIOBJ  
 Récupère un HANDLE vers l’objet Windows GDI attaché ; Sinon, NULL si aucun objet n’est attaché.  
  
```  
operator HGDIOBJ() const;  
```  
  
##  <a name="unrealizeobject"></a>  CGdiObject::UnrealizeObject  
 Réinitialise l’origine d’un pinceau ou réinitialise une palette logique.  
  
```  
BOOL UnrealizeObject();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur différente de zéro cas de réussite ; sinon, 0.  
  
### <a name="remarks"></a>Notes  
 Bien que `UnrealizeObject` est une fonction membre de la `CGdiObject` (classe), il doit être appelée uniquement sur `CBrush` ou `CPalette` objets.  
  
 Pour `CBrush` objets, `UnrealizeObject` dirige le système à réinitialiser à l’origine du pinceau donné la prochaine fois qu’il est sélectionné dans un contexte de périphérique. Si l’objet est un `CPalette` objet, `UnrealizeObject` force le système à réaliser la palette comme s’il n’avait pas été précédemment réalisé. La prochaine fois que l’application appelle le [CDC::RealizePalette](../../mfc/reference/cdc-class.md#realizepalette) fonction de la palette spécifiée, le système remappe complètement la palette logique à la palette système.  
  
 Le `UnrealizeObject` fonction ne doit pas être utilisée avec des objets de stock. Le `UnrealizeObject` fonction doit être appelée chaque fois qu’un nouveau pinceau d’origine (par le biais de la [CDC::SetBrushOrg](../../mfc/reference/cdc-class.md#setbrushorg) (fonction)). Le `UnrealizeObject` fonction ne doit pas être appelée pour le pinceau actuellement sélectionné ou de la palette actuellement sélectionné de n’importe quel contexte d’affichage.  
  
## <a name="see-also"></a>Voir aussi  
 [Graphique hiérarchique](../../mfc/hierarchy-chart.md)   
 [CBitmap (classe)](../../mfc/reference/cbitmap-class.md)   
 [CBrush (classe)](../../mfc/reference/cbrush-class.md)   
 [CFont (classe)](../../mfc/reference/cfont-class.md)   
 [CPalette (classe)](../../mfc/reference/cpalette-class.md)   
 [CPen (classe)](../../mfc/reference/cpen-class.md)   
 [CRgn, classe](../../mfc/reference/crgn-class.md)
