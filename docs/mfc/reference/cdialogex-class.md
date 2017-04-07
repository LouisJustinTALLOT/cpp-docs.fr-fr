---
title: Classe de CDialogEx | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CDialogEx
- AFXDIALOGEX/CDialogEx
- AFXDIALOGEX/CDialogEx::CDialogEx
- AFXDIALOGEX/CDialogEx::SetBackgroundColor
- AFXDIALOGEX/CDialogEx::SetBackgroundImage
dev_langs:
- C++
helpviewer_keywords:
- CDialogEx class
- CDialogEx::PreTranslateMessage method
ms.assetid: a6ed3b1f-aef8-4b66-ac78-2160faf63c13
caps.latest.revision: 27
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: c12aa0152fdbf83e423b944a0100045962ddb704
ms.lasthandoff: 02/24/2017

---
# <a name="cdialogex-class"></a>CDialogEx (classe)
La classe `CDialogEx` spécifie la couleur d'arrière-plan et l'image d'arrière-plan d'une boîte de dialogue.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CDialogEx : public CDialog  
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CDialogEx::CDialogEx](#cdialogex)|Construit un objet `CDialogEx`.|  
|`CDialogEx::~CDialogEx`|Destructeur.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[CDialogEx::SetBackgroundColor](#setbackgroundcolor)|Définit la couleur d'arrière-plan de la boîte de dialogue.|  
|[CDialogEx::SetBackgroundImage](#setbackgroundimage)|Définit l'image d'arrière-plan de la boîte de dialogue.|  
  
## <a name="remarks"></a>Remarques  
 Pour utiliser la classe `CDialogEx`, dérivez votre classe de boîte de dialogue de la classe `CDialogEx` plutôt que de la classe `CDialog`.  
  
 Les images de boîte de dialogue sont stockées dans un fichier de ressources. Le framework supprime automatiquement toute image qui est chargée à partir du fichier de ressources. Pour supprimer par programme l’image d’arrière-plan en cours, appelez le [CDialogEx::SetBackgroundImage](#setbackgroundimage) méthode ou implémentez un `OnDestroy` Gestionnaire d’événements. Lorsque vous appelez le [CDialogEx::SetBackgroundImage](#setbackgroundimage) méthode, passez un `HBITMAP` paramètre en tant que handle de l’image. L'objet `CDialogEx` prend possession de l'image et la supprime si l'indicateur `m_bAutoDestroyBmp` a pour valeur `TRUE`.  
  
 A `CDialogEx` objet peut être un parent d’un [CMFCPopupMenu classe](../../mfc/reference/cmfcpopupmenu-class.md) objet. Le [CMFCPopupMenu classe](../../mfc/reference/cmfcpopupmenu-class.md) object appelle le `CDialogEx::SetActiveMenu` (méthode) lors de la [CMFCPopupMenu classe](../../mfc/reference/cmfcpopupmenu-class.md) ouvre l’objet. Ensuite, le `CDialogEx` objet gère tout événement de menu jusqu'à ce que la [CMFCPopupMenu classe](../../mfc/reference/cmfcpopupmenu-class.md) objet est fermé.  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d’héritage  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CDialogEx](../../mfc/reference/cdialogex-class.md)  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** afxdialogex.h  
  
##  <a name="cdialogex"></a>CDialogEx::CDialogEx  
 Construit un objet `CDialogEx`.  
  
```  
CDialogEx(
    UINT nIDTemplate,  
    CWnd* pParent=NULL);

 
CDialogEx(
    LPCTSTR lpszTemplateName,  
    CWnd* pParentWnd=NULL);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `nIDTemplate`  
 L’ID de ressource d’un modèle de boîte de dialogue.  
  
 [in] `lpszTemplateName`  
 Le nom de la ressource d’un modèle de boîte de dialogue.  
  
 [in] `pParent`  
 Pointeur vers la fenêtre parente. La valeur par défaut est `NULL`.  
  
 [in] `pParentWnd`  
 Pointeur vers la fenêtre parente. La valeur par défaut est `NULL`.  
  
### <a name="return-value"></a>Valeur de retour  
  
### <a name="remarks"></a>Remarques  
  
##  <a name="setbackgroundcolor"></a>CDialogEx::SetBackgroundColor  
 Définit la couleur d'arrière-plan de la boîte de dialogue.  
  
```  
void SetBackgroundColor(
    COLORREF color,  
    BOOL bRepaint=TRUE);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `color`  
 Une valeur de couleur RVB.  
  
 [in] `bRepaint`  
 `TRUE`Pour mettre immédiatement à jour l’écran ; dans le cas contraire, `FALSE`. La valeur par défaut est `TRUE`.  
  
### <a name="remarks"></a>Notes  
  
##  <a name="setbackgroundimage"></a>CDialogEx::SetBackgroundImage  
 Définit l'image d'arrière-plan de la boîte de dialogue.  
  
```  
void SetBackgroundImage(
    HBITMAP hBitmap,  
    BackgroundLocation location=BACKGR_TILE,  
    BOOL bAutoDestroy=TRUE,  
    BOOL bRepaint=TRUE);

 
BOOL SetBackgroundImage(
    UINT uiBmpResId,  
    BackgroundLocation location=BACKGR_TILE,  
    BOOL bRepaint=TRUE);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `hBitmap`  
 Handle de l’image d’arrière-plan.  
  
 [in] `uiBmpResId`  
 L’ID de ressource de l’image d’arrière-plan.  
  
 [in] `location`  
 Parmi les `CDialogEx::BackgroundLocation` les valeurs qui spécifient l’emplacement de l’image. Les valeurs valides sont BACKGR_TILE, BACKGR_TOPLEFT, BACKGR_TOPRIGHT, BACKGR_BOTTOMLEFT et BACKGR_BOTTOMRIGHT. La valeur par défaut est BACKGR_TILE.  
  
 [in] `bAutoDestroy`  
 `TRUE`Pour détruire automatiquement l’image d’arrière-plan ; dans le cas contraire, `FALSE`.  
  
 [in] `bRepaint`  
 `TRUE`pour redessiner immédiatement la boîte de dialogue dans le cas contraire, `FALSE`.  
  
### <a name="return-value"></a>Valeur de retour  
 Dans la deuxième méthode de surcharge syntaxe, `TRUE` si la méthode réussit ; sinon, `FALSE`.  
  
### <a name="remarks"></a>Notes  
 L’image que vous spécifiez n’est pas étirée pour s’ajuster à la zone cliente de la boîte de dialogue.  
  
## <a name="see-also"></a>Voir aussi  
 [Graphique de la hiérarchie](../../mfc/hierarchy-chart.md)   
 [Classes](../../mfc/reference/mfc-classes.md)   
 [CMFCPopupMenu (classe)](../../mfc/reference/cmfcpopupmenu-class.md)   
 [CContextMenuManager (classe)](../../mfc/reference/ccontextmenumanager-class.md)

