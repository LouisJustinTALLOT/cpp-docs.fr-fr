---
title: CHtmlEditView, classe
ms.date: 11/04/2016
f1_keywords:
- CHtmlEditView
- AFXHTML/CHtmlEditView
- AFXHTML/CHtmlEditView::CHtmlEditView
- AFXHTML/CHtmlEditView::Create
- AFXHTML/CHtmlEditView::GetDHtmlDocument
- AFXHTML/CHtmlEditView::GetStartDocument
helpviewer_keywords:
- CHtmlEditView [MFC], CHtmlEditView
- CHtmlEditView [MFC], Create
- CHtmlEditView [MFC], GetDHtmlDocument
- CHtmlEditView [MFC], GetStartDocument
ms.assetid: 166c8ba8-3fb5-4dd7-a9ea-5bca662d00f6
ms.openlocfilehash: 8267a5272d2d542c4679bf30aa9d3ad8b933d81d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62389565"
---
# <a name="chtmleditview-class"></a>CHtmlEditView, classe

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
|[CHtmlEditView::GetDHtmlDocument](#getdhtmldocument)|Retourne le `IHTMLDocument2` interface sur le document actif.|
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

## <a name="requirements"></a>Configuration requise

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

*lpszClassName*<br/>
Pointe vers une chaîne de caractères se terminant par null qui nomme la classe Windows. Le nom de classe peut être n’importe quel nom inscrit avec le [AfxRegisterWndClass](application-information-and-management.md#afxregisterwndclass) fonction globale ou `RegisterClass` (fonction) Windows. Si NULL, utilise la valeur par défaut prédéfinie [CFrameWnd](../../mfc/reference/cframewnd-class.md) attributs.

*lpszWindowName*<br/>
Pointe vers une chaîne de caractères se terminant par null qui représente le nom de la fenêtre.

*dwStyle*<br/>
Spécifie les attributs de style de fenêtre. Par défaut, les styles WS_VISIBLE et WS_CHILD Windows sont définies.

*rect*<br/>
Une référence à un [RECT](/previous-versions/dd162897\(v=vs.85\)) structure qui spécifie la taille et la position de la fenêtre. Le *rectDefault* valeur permet à Windows spécifier la taille et la position de la nouvelle fenêtre.

*pParentWnd*<br/>
Pointeur vers la fenêtre parente du contrôle.

*nID*<br/>
Numéro d’identification de la vue. Par défaut, la valeur AFX_IDW_PANE_FIRST.

*pContext*<br/>
Un pointeur vers un [CCreateContext](../../mfc/reference/ccreatecontext-structure.md). NULL par défaut.

### <a name="remarks"></a>Notes

Cette méthode appelle également le contrôle WebBrowser relation contenant-contenu `Navigate` méthode pour charger un document par défaut (consultez [CHtmlEditView::GetStartDocument](#getstartdocument)).

##  <a name="getdhtmldocument"></a>  CHtmlEditView::GetDHtmlDocument

Retourne le `IHTMLDocument2` interface sur le document actif.

```
BOOL GetDHtmlDocument(IHTMLDocument2** ppDocument) const;
```

### <a name="parameters"></a>Paramètres

*ppDocument*<br/>
Le [IHTMLDocument2](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa752574\(v=vs.85\)) interface.

##  <a name="getstartdocument"></a>  CHtmlEditView::GetStartDocument

Récupère le nom du document par défaut pour cette vue.

```
virtual LPCTSTR GetStartDocument();
```

## <a name="see-also"></a>Voir aussi

[Exemple HTMLEdit](../../overview/visual-cpp-samples.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)
