---
title: Classe CCtrlView
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
ms.openlocfilehash: f77f1c265920bd160da790647ef754c55e6dbda3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369356"
---
# <a name="cctrlview-class"></a>Classe CCtrlView

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
|[CCtrlView::OnDraw](#ondraw)|Appelé par le cadre à dessiner en utilisant le contexte de l’appareil spécifié.|
|[CCtrlView::PreCreateWindow](#precreatewindow)|Appelé avant la création de la fenêtre Windows attachée à cet objet `CCtrlView`.|

### <a name="protected-data-members"></a>Membres de données protégés

|Nom|Description|
|----------|-----------------|
|[CCtrlView::m_dwDefaultStyle](#m_dwdefaultstyle)|Contient le style par défaut pour la classe de vue.|
|[CCtrlView::m_strClass](#m_strclass)|Contient le nom de la classe Windows pour la classe de vue.|

## <a name="remarks"></a>Notes

La `CCtrlView` classe et ses dérivés, [CEditView](../../mfc/reference/ceditview-class.md), [CListView](../../mfc/reference/clistview-class.md), [CTreeView](../../mfc/reference/ctreeview-class.md), et [CRichEditView](../../mfc/reference/cricheditview-class.md), adaptent l’architecture de la vue documentaire aux nouveaux contrôles communs pris en charge par Windows 95/98 et Windows NT versions 3.51 et plus tard. Pour plus d’informations sur l’architecture de la vue documentaire, voir [Document/Afficher l’architecture](../../mfc/document-view-architecture.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CView](../../mfc/reference/cview-class.md)

`CCtrlView`

## <a name="requirements"></a>Spécifications

**En-tête :** afxwin.h

## <a name="cctrlviewcctrlview"></a><a name="cctrlview"></a>CCtrlView::CCtrlView

Construit un objet `CCtrlView`.

```
CCtrlView(
    LPCTSTR lpszClass,
    DWORD dwStyle);
```

### <a name="parameters"></a>Paramètres

*Classe lpsz*<br/>
Nom de classe Windows de la classe de vue.

*dwStyle (en)*<br/>
Style de la classe de vue.

### <a name="remarks"></a>Notes

Le cadre appelle le constructeur lorsqu’une nouvelle fenêtre de cadre est créée ou qu’une fenêtre est divisée. Remplacer [CView::OnInitialUpdate](../../mfc/reference/cview-class.md#oninitialupdate) pour initialiser la vue après la jointure du document. Appelez [CWnd::Créer](../../mfc/reference/cwnd-class.md#create) ou [CWnd::CreateEx](../../mfc/reference/cwnd-class.md#createex) pour créer l’objet Windows.

## <a name="cctrlviewm_strclass"></a><a name="m_strclass"></a>CCtrlView::m_strClass

Contient le nom de la classe Windows pour la classe de vue.

```
CString m_strClass;
```

## <a name="cctrlviewm_dwdefaultstyle"></a><a name="m_dwdefaultstyle"></a>CCtrlView::m_dwDefaultStyle

Contient le style par défaut pour la classe de vue.

```
DWORD m_dwDefaultStyle;
```

### <a name="remarks"></a>Notes

Ce style est appliqué lorsqu’une fenêtre est créée.

## <a name="cctrlviewondraw"></a><a name="ondraw"></a>CCtrlView::OnDraw

Appelé par le cadre pour `CCtrlView` dessiner le contenu de l’objet en utilisant le contexte de l’appareil spécifié.

```
virtual void OnDraw(CDC* pDC);
```

### <a name="parameters"></a>Paramètres

*pDC*<br/>
Un pointeur sur le contexte de l’appareil dans lequel le dessin se produit.

### <a name="remarks"></a>Notes

`OnDraw`est généralement appelé pour l’affichage de l’écran, en passant un contexte de périphérique d’écran spécifié par *pDC*.

## <a name="cctrlviewprecreatewindow"></a><a name="precreatewindow"></a>CCtrlView::PreCreateWindow

Appelé avant la création de la fenêtre Windows attachée à cet objet `CWnd`.

```
virtual BOOL PreCreateWindow(CREATESTRUCT& cs);
```

### <a name="parameters"></a>Paramètres

*Cs*<br/>
Une structure [CREATESTRUCT.](/windows/win32/api/winuser/ns-winuser-createstructw)

### <a name="return-value"></a>Valeur de retour

Nonzero si la création de fenêtre doit continuer; 0 pour indiquer l’échec de la création.

### <a name="remarks"></a>Notes

N’appelez jamais cette fonction directement.

La mise en œuvre par défaut de cette fonction vérifie le nom d’une classe de fenêtre NULL et remplace un défaut approprié. Remplacer cette fonction de `CREATESTRUCT` membre pour modifier la structure avant la création de la fenêtre.

Chaque classe `CCtrlView` dérivée ajoute sa propre fonctionnalité `PreCreateWindow`à son remplacement de . Par conception, ces dérivés `PreCreateWindow` de ne sont pas documentés. Pour déterminer les styles appropriés à chaque classe et les interdépendances entre les styles, vous pouvez examiner le code source MFC pour la classe de base de votre application. Si vous choisissez `PreCreateWindow`de remplacer, vous pouvez déterminer si les styles utilisés dans la classe de base de votre application fournissent la fonctionnalité dont vous avez besoin en utilisant les informations recueillies à partir du code source MFC.

Pour plus d’informations sur l’évolution des styles de fenêtre, voir le [changement des styles d’une fenêtre créé par MFC](../../mfc/changing-the-styles-of-a-window-created-by-mfc.md).

## <a name="see-also"></a>Voir aussi

[Classe CView](../../mfc/reference/cview-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classe CTreeView](../../mfc/reference/ctreeview-class.md)<br/>
[Classe CListView](../../mfc/reference/clistview-class.md)<br/>
[Classe CRichEditView](../../mfc/reference/cricheditview-class.md)
