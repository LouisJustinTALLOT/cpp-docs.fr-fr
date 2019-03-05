---
title: CCtrlView, classe
ms.date: 11/04/2016
f1_keywords:
- CCtrlView
- AFXWIN/CCtrlView
- AFXWIN/CCtrlView::CCtrlView
- AFXWIN/CCtrlView::OnDraw
- AFXWIN/CCtrlView::PreCreateWindow
- AFXWIN/CCtrlView::m_dwDefaultStyle
- AFXWIN/CCtrlView::m_strClass
helpviewer_keywords:
- CCtrlView [MFC], CCtrlView
- CCtrlView [MFC], OnDraw
- CCtrlView [MFC], PreCreateWindow
- CCtrlView [MFC], m_dwDefaultStyle
- CCtrlView [MFC], m_strClass
ms.assetid: ff488596-1e71-451f-8fec-b0831a7b44e0
ms.openlocfilehash: 5cb68ab46e2cac8b2f1dcc13989077e32480a2c7
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57259566"
---
# <a name="cctrlview-class"></a>CCtrlView, classe

Adapte l'architecture document/vue aux contrôles communs pris en charge par Windows 98 et Windows NT versions 3.51 et ultérieures.

## <a name="syntax"></a>Syntaxe

```
class CCtrlView : public CView
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CCtrlView::CCtrlView](#cctrlview)|Construit un objet `CCtrlView`.|

### <a name="protected-methods"></a>Méthodes protégées

|Nom|Description|
|----------|-----------------|
|[CCtrlView::OnDraw](#ondraw)|Appelé par l’infrastructure pour dessiner en utilisant le contexte de périphérique spécifié.|
|[CCtrlView::PreCreateWindow](#precreatewindow)|Appelé avant la création de la fenêtre Windows attachée à cet objet `CCtrlView`.|

### <a name="protected-data-members"></a>Membres de données protégés

|Name|Description|
|----------|-----------------|
|[CCtrlView::m_dwDefaultStyle](#m_dwdefaultstyle)|Contient le style par défaut pour la classe d’affichage.|
|[CCtrlView::m_strClass](#m_strclass)|Contient le nom de classe de Windows pour la classe d’affichage.|

## <a name="remarks"></a>Notes

La classe `CCtrlView` et ses dérivés, [CEditView](../../mfc/reference/ceditview-class.md), [CListView](../../mfc/reference/clistview-class.md), [CTreeView](../../mfc/reference/ctreeview-class.md), et [CRichEditView](../../mfc/reference/cricheditview-class.md), adapter le l’architecture document / vue pour les nouveaux contrôles communs pris en charge par Windows 95/98 et Windows NT versions 3.51 et ultérieures. Pour plus d’informations sur l’architecture document / vue, consultez [Architecture Document/vue](../../mfc/document-view-architecture.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CView](../../mfc/reference/cview-class.md)

`CCtrlView`

## <a name="requirements"></a>Spécifications

**En-tête :** afxwin.h

##  <a name="cctrlview"></a>  CCtrlView::CCtrlView

Construit un objet `CCtrlView`.

```
CCtrlView(
    LPCTSTR lpszClass,
    DWORD dwStyle);
```

### <a name="parameters"></a>Paramètres

*lpszClass*<br/>
Nom de la classe Windows de la classe d’affichage.

*dwStyle*<br/>
Style de la classe d’affichage.

### <a name="remarks"></a>Notes

Le framework appelle le constructeur lorsqu’une nouvelle fenêtre frame est créée, ou une fenêtre est fractionnée. Substituer [CView::OnInitialUpdate](../../mfc/reference/cview-class.md#oninitialupdate) pour initialiser la vue, une fois que le document est attaché. Appelez [CWnd::Create](../../mfc/reference/cwnd-class.md#create) ou [CWnd::CreateEx](../../mfc/reference/cwnd-class.md#createex) pour créer l’objet de Windows.

##  <a name="m_strclass"></a>  CCtrlView::m_strClass

Contient le nom de classe de Windows pour la classe d’affichage.

```
CString m_strClass;
```

##  <a name="m_dwdefaultstyle"></a>  CCtrlView::m_dwDefaultStyle

Contient le style par défaut pour la classe d’affichage.

```
DWORD m_dwDefaultStyle;
```

### <a name="remarks"></a>Notes

Ce style est appliqué lorsqu’une fenêtre est créée.

##  <a name="ondraw"></a>  CCtrlView::OnDraw

Appelé par l’infrastructure pour dessiner le contenu de la `CCtrlView` de l’objet en utilisant le contexte de périphérique spécifié.

```
virtual void OnDraw(CDC* pDC);
```

### <a name="parameters"></a>Paramètres

*pDC*<br/>
Pointeur vers le contexte de périphérique dans lequel le dessin se produit.

### <a name="remarks"></a>Notes

`OnDraw` est généralement appelée pour afficher l’écran, en passant un contexte de périphérique spécifié par *pDC*.

##  <a name="precreatewindow"></a>  CCtrlView::PreCreateWindow

Appelé avant la création de la fenêtre Windows attachée à cet objet `CWnd`.

```
virtual BOOL PreCreateWindow(CREATESTRUCT& cs);
```

### <a name="parameters"></a>Paramètres

*cs*<br/>
Un [CREATESTRUCT](/windows/desktop/api/winuser/ns-winuser-tagcreatestructa) structure.

### <a name="return-value"></a>Valeur de retour

Différent de zéro si la création de la fenêtre doit être poursuivie ; 0 pour indiquer l’échec de la création.

### <a name="remarks"></a>Notes

Ne jamais appeler directement cette fonction.

L’implémentation par défaut de cette fonction vérifie un nom de classe de fenêtre NULL et la remplace par une valeur par défaut approprié. Remplacez cette fonction membre pour modifier la `CREATESTRUCT` structure avant la création de la fenêtre.

Chaque classe dérivée de `CCtrlView` ajoute ses propres fonctionnalités à sa substitution de `PreCreateWindow`. Par conception, ces dérivations de `PreCreateWindow` ne sont pas documentés. Pour déterminer les styles appropriés à chaque classe et les interdépendances entre les styles, vous pouvez examiner le code source MFC pour la classe de base de votre application. Si vous choisissez de remplacer `PreCreateWindow`, vous pouvez déterminer si les styles utilisés dans la classe de base de votre application fournissent les fonctionnalités que vous avez besoin à l’aide des informations collectées à partir du code source MFC.

Pour plus d’informations sur la modification des styles de fenêtre, consultez la [modification des Styles d’une fenêtre créée par MFC](../../mfc/changing-the-styles-of-a-window-created-by-mfc.md).

## <a name="see-also"></a>Voir aussi

[CView, classe](../../mfc/reference/cview-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CTreeView, classe](../../mfc/reference/ctreeview-class.md)<br/>
[CListView, classe](../../mfc/reference/clistview-class.md)<br/>
[CRichEditView, classe](../../mfc/reference/cricheditview-class.md)
