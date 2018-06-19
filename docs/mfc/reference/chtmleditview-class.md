---
title: Classe de CHtmlEditView | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CHtmlEditView
- AFXHTML/CHtmlEditView
- AFXHTML/CHtmlEditView::CHtmlEditView
- AFXHTML/CHtmlEditView::Create
- AFXHTML/CHtmlEditView::GetDHtmlDocument
- AFXHTML/CHtmlEditView::GetStartDocument
dev_langs:
- C++
helpviewer_keywords:
- CHtmlEditView [MFC], CHtmlEditView
- CHtmlEditView [MFC], Create
- CHtmlEditView [MFC], GetDHtmlDocument
- CHtmlEditView [MFC], GetStartDocument
ms.assetid: 166c8ba8-3fb5-4dd7-a9ea-5bca662d00f6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 10f474ce860bf5d9071a93f17654123f4777efa7
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33367342"
---
# <a name="chtmleditview-class"></a>CHtmlEditView Class
Fournit les fonctionnalités de la plateforme d'édition WebBrowser dans le contexte de l'architecture document/vue de MFC.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CHtmlEditView : public CHtmlView, public CHtmlEditCtrlBase<CHtmlEditView>  
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CHtmlEditView::CHtmlEditView](#chtmleditview)|Construit un objet `CHtmlEditView`.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[CHtmlEditView::Create](#create)|Crée un nouvel objet de fenêtre.|  
|[CHtmlEditView::GetDHtmlDocument](#getdhtmldocument)|Retourne le **IHTMLDocument2** interface sur le document actif.|  
|[CHtmlEditView::GetStartDocument](#getstartdocument)|Récupère le nom du document par défaut pour cette vue.|  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CView](../../mfc/reference/cview-class.md)  
  
 [CScrollView](../../mfc/reference/cscrollview-class.md)  
  
 [CFormView](../../mfc/reference/cformview-class.md)  
  
 [CHtmlEditCtrlBase](../../mfc/reference/chtmleditctrlbase-class.md)  
  
 [CHtmlView](../../mfc/reference/chtmlview-class.md)  
  
 `CHtmlEditView`  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** afxhtml.h  
  
##  <a name="chtmleditview"></a>  CHtmlEditView::CHtmlEditView  
 Construit un objet `CHtmlEditView`.  
  
```  
CHtmlEditView();
```  
  
##  <a name="create"></a>  CHtmlEditView::Create  
 Crée un nouvel objet de fenêtre.  
  
```  
virtual BOOL Create(
    LPCTSTR lpszClassName,  
    LPCTSTR lpszWindowName,  
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID,  
    CCreateContext* pContext = NULL);
```  
  
### <a name="parameters"></a>Paramètres  
 `lpszClassName`  
 Pointe vers une chaîne de caractères terminée par null que les noms de la classe Windows. Le nom de classe peut être n’importe quel nom inscrit avec le [AfxRegisterWndClass](application-information-and-management.md#afxregisterwndclass) fonction globale ou **RegisterClass** fonction Windows. Si **NULL**, utilise la valeur par défaut prédéfinie [CFrameWnd](../../mfc/reference/cframewnd-class.md) attributs.  
  
 `lpszWindowName`  
 Pointe vers une chaîne de caractères terminée par null qui représente le nom de la fenêtre.  
  
 `dwStyle`  
 Spécifie les attributs de style de fenêtre. Par défaut, le **WS_VISIBLE** et **WS_CHILD** définissent des styles de Windows.  
  
 `rect`  
 Une référence à un [RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897) structure spécifiant la taille et la position de la fenêtre. Le `rectDefault` valeur permet à Windows pour spécifier la taille et la position de la nouvelle fenêtre.  
  
 `pParentWnd`  
 Pointeur vers la fenêtre parente du contrôle.  
  
 `nID`  
 Le numéro d’ID de la vue. Par défaut, la valeur **AFX_IDW_PANE_FIRST**.  
  
 `pContext`  
 Un pointeur vers un [CCreateContext](../../mfc/reference/ccreatecontext-structure.md). **NULL** par défaut.  
  
### <a name="remarks"></a>Notes  
 Cette méthode appelle également le contrôle WebBrowser contenu **naviguer** méthode pour charger un document par défaut (voir [CHtmlEditView::GetStartDocument](#getstartdocument)).  
  
##  <a name="getdhtmldocument"></a>  CHtmlEditView::GetDHtmlDocument  
 Retourne le **IHTMLDocument2** interface sur le document actif.  
  
```  
BOOL GetDHtmlDocument(IHTMLDocument2** ppDocument) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 `ppDocument`  
 Le [IHTMLDocument2](https://msdn.microsoft.com/library/aa752574.aspx) interface.  
  
##  <a name="getstartdocument"></a>  CHtmlEditView::GetStartDocument  
 Récupère le nom du document par défaut pour cette vue.  
  
```  
virtual LPCTSTR GetStartDocument();
```  
  
## <a name="see-also"></a>Voir aussi  
 [HTMLEdit, exemple](../../visual-cpp-samples.md)   
 [Graphique hiérarchique](../../mfc/hierarchy-chart.md)


