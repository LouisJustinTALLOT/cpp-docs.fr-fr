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
ms.openlocfilehash: 334f139b81afeb06d57cbd128abe9e413b1fd0e7
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69507145"
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
|[CCtrlView::OnDraw](#ondraw)|Appelé par l’infrastructure pour dessiner à l’aide du contexte de périphérique spécifié.|
|[CCtrlView::PreCreateWindow](#precreatewindow)|Appelé avant la création de la fenêtre Windows attachée à cet objet `CCtrlView`.|

### <a name="protected-data-members"></a>Membres de données protégés

|Nom|Description|
|----------|-----------------|
|[CCtrlView::m_dwDefaultStyle](#m_dwdefaultstyle)|Contient le style par défaut pour la classe d’affichage.|
|[CCtrlView::m_strClass](#m_strclass)|Contient le nom de classe Windows pour la classe d’affichage.|

## <a name="remarks"></a>Notes

La classe `CCtrlView` et ses dérivés, [CEditView](../../mfc/reference/ceditview-class.md), [CListView](../../mfc/reference/clistview-class.md), [CTreeView](../../mfc/reference/ctreeview-class.md)et [CRichEditView](../../mfc/reference/cricheditview-class.md), adaptent l’architecture document-vue aux nouveaux contrôles communs pris en charge par Windows 95/98 et Windows NT versions 3,51 et versions ultérieures. Pour plus d’informations sur l’architecture document-vue, consultez [architecture document/vue](../../mfc/document-view-architecture.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CView](../../mfc/reference/cview-class.md)

`CCtrlView`

## <a name="requirements"></a>Configuration requise

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
Nom de classe Windows de la classe de vue.

*dwStyle*<br/>
Style de la classe de vue.

### <a name="remarks"></a>Notes

L’infrastructure appelle le constructeur lors de la création d’une nouvelle fenêtre frame ou lors du fractionnement d’une fenêtre. Remplacez [CView:: OnInitialUpdate](../../mfc/reference/cview-class.md#oninitialupdate) pour initialiser la vue une fois que le document est attaché. Appelez [CWnd:: Create](../../mfc/reference/cwnd-class.md#create) ou [CWnd:: CreateEx](../../mfc/reference/cwnd-class.md#createex) pour créer l’objet Windows.

##  <a name="m_strclass"></a>  CCtrlView::m_strClass

Contient le nom de classe Windows pour la classe d’affichage.

```
CString m_strClass;
```

##  <a name="m_dwdefaultstyle"></a>  CCtrlView::m_dwDefaultStyle

Contient le style par défaut pour la classe d’affichage.

```
DWORD m_dwDefaultStyle;
```

### <a name="remarks"></a>Notes

Ce style est appliqué lors de la création d’une fenêtre.

##  <a name="ondraw"></a>  CCtrlView::OnDraw

Appelé par l’infrastructure pour dessiner le contenu de l' `CCtrlView` objet à l’aide du contexte de périphérique spécifié.

```
virtual void OnDraw(CDC* pDC);
```

### <a name="parameters"></a>Paramètres

*pDC*<br/>
Pointeur vers le contexte de périphérique dans lequel le dessin se produit.

### <a name="remarks"></a>Notes

`OnDraw`est généralement appelé pour l’affichage à l’écran, passant un contexte de périphérique d’écran spécifié par le *contrôleur de domaine principal*.

##  <a name="precreatewindow"></a>  CCtrlView::PreCreateWindow

Appelé avant la création de la fenêtre Windows attachée à cet objet `CWnd`.

```
virtual BOOL PreCreateWindow(CREATESTRUCT& cs);
```

### <a name="parameters"></a>Paramètres

*cs*<br/>
Structure [CREATESTRUCT](/windows/win32/api/winuser/ns-winuser-createstructw) .

### <a name="return-value"></a>Valeur de retour

Différent de zéro si la création de la fenêtre doit se poursuivre; 0 pour indiquer l’échec de la création.

### <a name="remarks"></a>Notes

N’appelez jamais cette fonction directement.

L’implémentation par défaut de cette fonction recherche un nom de classe de fenêtre NULL et substitue une valeur par défaut appropriée. Substituez cette fonction membre pour modifier la `CREATESTRUCT` structure avant la création de la fenêtre.

Chaque classe dérivée `CCtrlView` de ajoute sa propre fonctionnalité à sa substitution de `PreCreateWindow`. Par défaut, ces dérivations de `PreCreateWindow` ne sont pas documentées. Pour déterminer les styles appropriés à chaque classe et les interdépendances entre les styles, vous pouvez examiner le code source MFC pour la classe de base de votre application. Si vous choisissez de remplacer `PreCreateWindow`, vous pouvez déterminer si les styles utilisés dans la classe de base de votre application fournissent les fonctionnalités dont vous avez besoin en utilisant les informations collectées à partir du code source MFC.

Pour plus d’informations sur la modification des styles de fenêtre, consultez [modification des styles d’une fenêtre créée par MFC](../../mfc/changing-the-styles-of-a-window-created-by-mfc.md).

## <a name="see-also"></a>Voir aussi

[CView, classe](../../mfc/reference/cview-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CTreeView, classe](../../mfc/reference/ctreeview-class.md)<br/>
[CListView, classe](../../mfc/reference/clistview-class.md)<br/>
[CRichEditView, classe](../../mfc/reference/cricheditview-class.md)
