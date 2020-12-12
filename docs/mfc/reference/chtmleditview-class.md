---
description: 'En savoir plus sur : classe CHtmlEditView'
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
ms.openlocfilehash: 9ab998ca16a26fd4ef7a23e4dc58c6542ec330b3
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97261318"
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
|[CHtmlEditView :: Create](#create)|Crée un nouvel objet Window.|
|[CHtmlEditView::GetDHtmlDocument](#getdhtmldocument)|Retourne l' `IHTMLDocument2` interface sur le document actif.|
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

## <a name="chtmleditviewchtmleditview"></a><a name="chtmleditview"></a> CHtmlEditView::CHtmlEditView

Construit un objet `CHtmlEditView`.

```
CHtmlEditView();
```

## <a name="chtmleditviewcreate"></a><a name="create"></a> CHtmlEditView :: Create

Crée un nouvel objet Window.

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
Pointe vers une chaîne de caractères se terminant par un caractère null qui nomme la classe Windows. Le nom de la classe peut être n’importe quel nom enregistré avec la fonction globale [AfxRegisterWndClass](application-information-and-management.md#afxregisterwndclass) ou la `RegisterClass` fonction Windows. Si la valeur est NULL, utilise les attributs [CFrameWnd](../../mfc/reference/cframewnd-class.md) par défaut prédéfinis.

*lpszWindowName*<br/>
Pointe vers une chaîne de caractères se terminant par un caractère null qui représente le nom de la fenêtre.

*dwStyle*<br/>
Spécifie les attributs de style de fenêtre. Par défaut, les styles Windows WS_VISIBLE et WS_CHILD sont définis.

*rectangulaire*<br/>
Référence à une structure [Rect](/windows/win32/api/windef/ns-windef-rect) spécifiant la taille et la position de la fenêtre. La valeur *rectDefault* permet à Windows de spécifier la taille et la position de la nouvelle fenêtre.

*pParentWnd*<br/>
Pointeur vers la fenêtre parente du contrôle.

*nID*<br/>
Numéro d’identification de la vue. Par défaut, affectez la valeur AFX_IDW_PANE_FIRST.

*pContext*<br/>
Pointeur vers un [CCreateContext](../../mfc/reference/ccreatecontext-structure.md). NULL par défaut.

### <a name="remarks"></a>Notes

Cette méthode appellera également la méthode contenue dans le WebBrowser `Navigate` pour charger un document par défaut (consultez [CHtmlEditView :: GetStartDocument](#getstartdocument)).

## <a name="chtmleditviewgetdhtmldocument"></a><a name="getdhtmldocument"></a> CHtmlEditView::GetDHtmlDocument

Retourne l' `IHTMLDocument2` interface sur le document actif.

```
BOOL GetDHtmlDocument(IHTMLDocument2** ppDocument) const;
```

### <a name="parameters"></a>Paramètres

*ppDocument*<br/>
Interface [IHTMLDocument2](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa752574\(v=vs.85\)) .

## <a name="chtmleditviewgetstartdocument"></a><a name="getstartdocument"></a> CHtmlEditView::GetStartDocument

Récupère le nom du document par défaut pour cette vue.

```
virtual LPCTSTR GetStartDocument();
```

## <a name="see-also"></a>Voir aussi

[HTMLEdit, exemple](../../overview/visual-cpp-samples.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)
