---
title: Cmfcpreviewctrlimpl, classe | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCPreviewCtrlImpl
- AFXWIN/CMFCPreviewCtrlImpl
- AFXWIN/CMFCPreviewCtrlImpl::CMFCPreviewCtrlImpl
- AFXWIN/CMFCPreviewCtrlImpl::Create
- AFXWIN/CMFCPreviewCtrlImpl::Destroy
- AFXWIN/CMFCPreviewCtrlImpl::Focus
- AFXWIN/CMFCPreviewCtrlImpl::GetDocument
- AFXWIN/CMFCPreviewCtrlImpl::Redraw
- AFXWIN/CMFCPreviewCtrlImpl::SetDocument
- AFXWIN/CMFCPreviewCtrlImpl::SetHost
- AFXWIN/CMFCPreviewCtrlImpl::SetPreviewVisuals
- AFXWIN/CMFCPreviewCtrlImpl::SetRect
- AFXWIN/CMFCPreviewCtrlImpl::DoPaint
- AFXWIN/CMFCPreviewCtrlImpl::m_clrBackColor
- AFXWIN/CMFCPreviewCtrlImpl::m_clrTextColor
- AFXWIN/CMFCPreviewCtrlImpl::m_font
- AFXWIN/CMFCPreviewCtrlImpl::m_pDocument
dev_langs:
- C++
helpviewer_keywords:
- CMFCPreviewCtrlImpl [MFC], CMFCPreviewCtrlImpl
- CMFCPreviewCtrlImpl [MFC], Create
- CMFCPreviewCtrlImpl [MFC], Destroy
- CMFCPreviewCtrlImpl [MFC], Focus
- CMFCPreviewCtrlImpl [MFC], GetDocument
- CMFCPreviewCtrlImpl [MFC], Redraw
- CMFCPreviewCtrlImpl [MFC], SetDocument
- CMFCPreviewCtrlImpl [MFC], SetHost
- CMFCPreviewCtrlImpl [MFC], SetPreviewVisuals
- CMFCPreviewCtrlImpl [MFC], SetRect
- CMFCPreviewCtrlImpl [MFC], DoPaint
- CMFCPreviewCtrlImpl [MFC], m_clrBackColor
- CMFCPreviewCtrlImpl [MFC], m_clrTextColor
- CMFCPreviewCtrlImpl [MFC], m_font
- CMFCPreviewCtrlImpl [MFC], m_pDocument
ms.assetid: 06257fa0-54c9-478d-9d68-c9698c3f93ed
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: bb1ef84aabed69554ded868bbe9092c3e8b7082f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33370410"
---
# <a name="cmfcpreviewctrlimpl-class"></a>CMFCPreviewCtrlImpl, classe
Cette classe implémente une fenêtre qui est placée dans une fenêtre hôte fournie par l’interpréteur de commandes pour l’aperçu riche.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CMFCPreviewCtrlImpl : public CWnd;  
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CMFCPreviewCtrlImpl :: ~ CMFCPreviewCtrlImpl](#dtor)|Destruction d’un objet de contrôle de version préliminaire.|  
|[CMFCPreviewCtrlImpl::CMFCPreviewCtrlImpl](#cmfcpreviewctrlimpl)|Construit un objet de contrôle de version préliminaire.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[CMFCPreviewCtrlImpl::Create](#create)|Surchargé. Appelée par un gestionnaire d’aperçu riche pour créer la fenêtre Windows.|  
|[CMFCPreviewCtrlImpl::Destroy](#destroy)|Appelée par un gestionnaire d’aperçu riche lorsqu’il a besoin détruire ce contrôle.|  
|[CMFCPreviewCtrlImpl::Focus](#focus)|Définit le focus à ce contrôle.|  
|[CMFCPreviewCtrlImpl::GetDocument](#getdocument)|Retourne un document connecté à ce contrôle d’aperçu.|  
|[CMFCPreviewCtrlImpl::Redraw](#redraw)|Indique à ce contrôle à redessiner.|  
|[CMFCPreviewCtrlImpl::SetDocument](#setdocument)|Appelée par le Gestionnaire d’aperçu pour créer une relation entre l’implémentation de document et le contrôle d’aperçu.|  
|[CMFCPreviewCtrlImpl::SetHost](#sethost)|Définit un nouveau parent pour ce contrôle.|  
|[CMFCPreviewCtrlImpl::SetPreviewVisuals](#setpreviewvisuals)|Appelée par un gestionnaire d’aperçu riche lorsqu’il a besoin définir les éléments visuels de l’aperçu riche contenu.|  
|[CMFCPreviewCtrlImpl::SetRect](#setrect)|Définit un nouveau rectangle englobant pour ce contrôle.|  
  
### <a name="protected-methods"></a>Méthodes protégées  
  
|Nom|Description|  
|----------|-----------------|  
|[CMFCPreviewCtrlImpl::DoPaint](#dopaint)|Appelé par l’infrastructure pour afficher l’aperçu.|  
  
### <a name="protected-data-members"></a>Membres de données protégés  
  
|Name|Description|  
|----------|-----------------|  
|[CMFCPreviewCtrlImpl::m_clrBackColor](#m_clrbackcolor)|Couleur d’arrière-plan de la fenêtre d’aperçu.|  
|[CMFCPreviewCtrlImpl::m_clrTextColor](#m_clrtextcolor)|Couleur du texte de la fenêtre d’aperçu.|  
|[CMFCPreviewCtrlImpl::m_font](#m_font)|Police utilisée pour afficher le texte dans la fenêtre d’aperçu.|  
|[CMFCPreviewCtrlImpl::m_pDocument](#m_pdocument)|Pointeur vers un document dont le contenu est affiché dans le contrôle.|  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** afxwin.h    
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CMFCPreviewCtrlImpl](../../mfc/reference/cmfcpreviewctrlimpl-class.md)

## <a name="cmfcpreviewctrlimpl"></a> CMFCPreviewCtrlImpl::CMFCPreviewCtrlImpl
Construit un objet de contrôle de version préliminaire.

### <a name="syntax"></a>Syntaxe
CMFCPreviewCtrlImpl() ;  

## <a name="create"></a> CMFCPreviewCtrlImpl::Create
Surchargé. Appelée par un gestionnaire d’aperçu riche pour créer la fenêtre Windows.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
virtual BOOL Create(  
   HWND hWndParent,  
   const RECT* prc  
);  
virtual BOOL Create(  
   HWND hWndParent,  
   const RECT* prc,  
   CCreateContext* pContext  
);  
```  
  
### <a name="parameters"></a>Paramètres  
 `hWndParent`  
 Handle vers la fenêtre hôte fournie par l’interpréteur de commandes pour l’aperçu riche.  
  
 `prc`  
 Spécifie la taille initiale et la position de la fenêtre.  
  
 `pContext`  
 Pointeur vers un contexte de la création.  
  
### <a name="return-value"></a>Valeur de retour  
 `TRUE` Si la création a réussi ; dans le cas contraire `FALSE`.  
  
## <a name="destroy"></a> CMFCPreviewCtrlImpl::Destroy
Appelée par un gestionnaire d’aperçu riche lorsqu’il a besoin détruire ce contrôle.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
virtual void Destroy();  
```  
  
## <a name="dopaint"></a> CMFCPreviewCtrlImpl::DoPaint  
Appelé par l’infrastructure pour afficher l’aperçu.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
virtual void DoPaint(  
   CPaintDC* pDC  
);  
```  
  
### <a name="parameters"></a>Paramètres  
 `pDC`  
 Pointeur vers un contexte de périphérique pour la peinture.  


## <a name="focus"></a> CMFCPreviewCtrlImpl::Focus  
Définit le focus à ce contrôle.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
virtual void Focus();  
```  
## <a name="getdocument"></a> CMFCPreviewCtrlImpl::GetDocument
Retourne un document connecté à ce contrôle d’aperçu.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
ATL::IDocument* GetDocument();  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Pointeur vers un document, dont le contenu est affiché dans le contrôle.

## <a name="m_clrbackcolor"></a> CMFCPreviewCtrlImpl::m_clrBackColor  
Couleur d’arrière-plan de la fenêtre d’aperçu.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
COLORREF m_clrBackColor;  
```  

## <a name="m_clrtextcolor"></a> CMFCPreviewCtrlImpl::m_clrTextColor
Couleur du texte de la fenêtre d’aperçu.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
COLORREF m_clrTextColor;  
```  
## <a name="m_font"></a> CMFCPreviewCtrlImpl::m_font police utilisée pour afficher le texte dans la fenêtre d’aperçu.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
CFont m_font;  
```  
## <a name="m_pdocument"></a> CMFCPreviewCtrlImpl::m_pDocument  
Pointeur vers un document dont le contenu est affiché dans le contrôle.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
ATL::IDocument* m_pDocument;  
```  

## <a name="redraw"></a> CMFCPreviewCtrlImpl::Redraw  
Indique à ce contrôle à redessiner.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
virtual void Redraw();  
```  
## <a name="setdocument"></a> CMFCPreviewCtrlImpl::SetDocument 
Appelée par le Gestionnaire d’aperçu pour créer une relation entre l’implémentation de document et le contrôle d’aperçu.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
void SetDocument(  
   IDocument* pDocument  
);  
```  
  
### <a name="parameters"></a>Paramètres  
 `pDocument`  
 Pointeur vers l’implémentation d’un document.  

## <a name="sethost"></a> CMFCPreviewCtrlImpl::SetHost  
Définit un nouveau parent pour ce contrôle.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
virtual void SetHost(  
   HWND hWndParent  
);  
```  
  
### <a name="parameters"></a>Paramètres  
 `hWndParent`  
 Handle vers la nouvelle fenêtre parent.  

## <a name="setpreviewvisuals"></a> CMFCPreviewCtrlImpl::SetPreviewVisuals  
Appelée par un gestionnaire d’aperçu riche lorsqu’il a besoin définir les éléments visuels de l’aperçu riche contenu.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
virtual void SetPreviewVisuals(  
   COLORREF clrBack,  
   COLORREF clrText,  
   const LOGFONTW *plf  
);  
```  
  
### <a name="parameters"></a>Paramètres  
 `clrBack`  
 Couleur d’arrière-plan de la fenêtre d’aperçu.  
  
 `clrText`  
 Couleur du texte de la fenêtre d’aperçu.  
  
 `plf`  
 Police utilisée pour afficher le texte dans la fenêtre d’aperçu. 

##  <a name="setrect"></a> CMFCPreviewCtrlImpl::SetRect  
Définit un nouveau rectangle englobant pour ce contrôle.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
virtual void SetRect(  
   const RECT* prc,  
   BOOL bRedraw  
);  
```  
  
### <a name="parameters"></a>Paramètres  
 `prc`  
 Spécifie la nouvelle taille et la position du contrôle de version préliminaire.  
  
 `bRedraw`  
 Spécifie si le contrôle doit être redessiné.  
  
### <a name="remarks"></a>Notes  
 Généralement, un rectangle englobant est défini lorsque le contrôle hôte est redimensionné.  

## <a name="dtor"></a> CMFCPreviewCtrlImpl :: ~ CMFCPreviewCtrlImpl  
Destruction d’un objet de contrôle de version préliminaire.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
virtual ~CMFCPreviewCtrlImpl();  
```  
  
