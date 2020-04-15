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
ms.openlocfilehash: 1254a3412846cdebd1d9accb91d27d0afbc4ef8d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81352077"
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
|[CHtmlEditView::Créer](#create)|Crée un nouvel objet de fenêtre.|
|[CHtmlEditView::GetDHtmlDocument](#getdhtmldocument)|Retourne `IHTMLDocument2` l’interface sur le document actuel.|
|[CHtmlEditView::GetStartDocument](#getstartdocument)|Récupère le nom du document par défaut pour cette vue.|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CView](../../mfc/reference/cview-class.md)

[CScrollView](../../mfc/reference/cscrollview-class.md)

[CFormView](../../mfc/reference/cformview-class.md)

[CHtmlEditCtrlBase](../../mfc/reference/chtmleditctrlbase-class.md)

[CHtmlView (en anglais)](../../mfc/reference/chtmlview-class.md)

`CHtmlEditView`

## <a name="requirements"></a>Spécifications

**En-tête :** afxhtml.h

## <a name="chtmleditviewchtmleditview"></a><a name="chtmleditview"></a>CHtmlEditView::CHtmlEditView

Construit un objet `CHtmlEditView`.

```
CHtmlEditView();
```

## <a name="chtmleditviewcreate"></a><a name="create"></a>CHtmlEditView::Créer

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

*lpszClassName (en)*<br/>
Indique une chaîne de caractères à durée nulle qui nomme la classe Windows. Le nom de la classe peut être n’importe quel nom `RegisterClass` enregistré auprès de la fonction globale [AfxRegisterWndClass](application-information-and-management.md#afxregisterwndclass) ou de la fonction Windows. Si NULL, utilise les attributs [CFrameWnd](../../mfc/reference/cframewnd-class.md) par défaut prédéfinis.

*lpszWindowName (en)*<br/>
Indique une chaîne de caractères non terminée qui représente le nom de fenêtre.

*dwStyle (en)*<br/>
Spécifie les attributs de style de fenêtre. Par défaut, les styles Windows WS_VISIBLE et WS_CHILD sont définis.

*Rect*<br/>
Une référence à une structure [RECT](/previous-versions/dd162897\(v=vs.85\)) précisant la taille et la position de la fenêtre. La valeur *rectDefault* permet à Windows de spécifier la taille et la position de la nouvelle fenêtre.

*pParentWnd*<br/>
Un pointeur à la fenêtre parente du contrôle.

*nID*<br/>
Le numéro d’identification de la vue. Par défaut, configuré à AFX_IDW_PANE_FIRST.

*pContext*<br/>
Un pointeur à un [CCreateContext](../../mfc/reference/ccreatecontext-structure.md). NULL par défaut.

### <a name="remarks"></a>Notes

Cette méthode appellera également la `Navigate` méthode webBrowser contenue pour charger un document par défaut (voir [CHtmlEditView::GetStartDocument](#getstartdocument)).

## <a name="chtmleditviewgetdhtmldocument"></a><a name="getdhtmldocument"></a>CHtmlEditView::GetDHtmlDocument

Retourne `IHTMLDocument2` l’interface sur le document actuel.

```
BOOL GetDHtmlDocument(IHTMLDocument2** ppDocument) const;
```

### <a name="parameters"></a>Paramètres

*ppDocument*<br/>
L’interface [IHTMLDocument2.](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa752574\(v=vs.85\))

## <a name="chtmleditviewgetstartdocument"></a><a name="getstartdocument"></a>CHtmlEditView::GetStartDocument

Récupère le nom du document par défaut pour cette vue.

```
virtual LPCTSTR GetStartDocument();
```

## <a name="see-also"></a>Voir aussi

[Échantillon HTMLEdit](../../overview/visual-cpp-samples.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)
