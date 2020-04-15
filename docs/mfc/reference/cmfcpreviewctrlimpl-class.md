---
title: CMFCPreviewCtrlImpl, classe
ms.date: 11/04/2016
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
ms.openlocfilehash: 060e601901fa5725d7ca62f244f66784af3dc11d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375336"
---
# <a name="cmfcpreviewctrlimpl-class"></a>CMFCPreviewCtrlImpl, classe

Cette classe met en œuvre une fenêtre placée sur une fenêtre d’hôte fournie par la Shell pour Rich Preview.

## <a name="syntax"></a>Syntaxe

```
class CMFCPreviewCtrlImpl : public CWnd;
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CMFCPreviewCtrlImpl::CMFCPreviewCtrlImpl](#dtor)|Destructs un objet de contrôle de prévisualisation.|
|[CMFCPreviewCtrlImpl::CMFCPreviewCtrlImpl](#cmfcpreviewctrlimpl)|Construit un objet de contrôle de prévisualisation.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CMFCPreviewCtrlImpl::Créer](#create)|Surchargé. Appelé par un gestionnaire Rich Preview pour créer la fenêtre Windows.|
|[CMFCPreviewCtrlImpl::Destroy](#destroy)|Appelé par un gestionnaire Rich Preview quand il a besoin de détruire ce contrôle.|
|[CMFCPreviewCtrlImpl::Focus](#focus)|Définit le focus d'entrée sur ce contrôle.|
|[CMFCPreviewCtrlImpl::GetDocument](#getdocument)|Renvoie un document connecté à ce contrôle de prévisualisation.|
|[CMFCPreviewCtrlImpl::Redraw](#redraw)|Ca dit à ce contrôle de redessiner.|
|[CMFCPreviewCtrlImpl::SetDocument](#setdocument)|Appelé par le gestionnaire de prévisualisation pour créer une relation entre la mise en œuvre du document et le contrôle de prévisualisation.|
|[CMFCPreviewCtrlImpl::SetHost](#sethost)|Définit un nouveau parent pour ce contrôle.|
|[CMFCPreviewCtrlImpl::SetPreviewVisuals](#setpreviewvisuals)|Appelé par un gestionnaire De preview riche quand il a besoin de définir des visuels de contenu de prévisualisation riche.|
|[CMFCPreviewCtrlImpl::SetRect](#setrect)|Définit un nouveau rectangle de délimitation pour ce contrôle.|

### <a name="protected-methods"></a>Méthodes protégées

|Nom|Description|
|----------|-----------------|
|[CMFCPreviewCtrlImpl::DoPaint](#dopaint)|Appelé par le cadre pour rendre l’aperçu.|

### <a name="protected-data-members"></a>Membres de données protégés

|Nom|Description|
|----------|-----------------|
|[CMFCPreviewCtrlImpl::m_clrBackColor](#m_clrbackcolor)|Couleur de fond de la fenêtre d’aperçu.|
|[CMFCPreviewCtrlImpl::m_clrTextColor](#m_clrtextcolor)|Couleur de texte de la fenêtre de prévisualisation.|
|[CMFCPreviewCtrlImpl::m_font](#m_font)|Font utilisé pour afficher le texte dans la fenêtre de prévisualisation.|
|[CMFCPreviewCtrlImpl::m_pDocument](#m_pdocument)|Un pointeur d’un document dont le contenu est prévisualisé dans le contrôle.|

## <a name="requirements"></a>Spécifications

**En-tête :** afxwin.h

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CMFCPreviewCtrlImpl](../../mfc/reference/cmfcpreviewctrlimpl-class.md)

## <a name="cmfcpreviewctrlimplcmfcpreviewctrlimpl"></a><a name="cmfcpreviewctrlimpl"></a>CMFCPreviewCtrlImpl::CMFCPreviewCtrlImpl

Construit un objet de contrôle de prévisualisation.

### <a name="syntax"></a>Syntaxe

CMFCPreviewCtrlImpl();

## <a name="cmfcpreviewctrlimplcreate"></a><a name="create"></a>CMFCPreviewCtrlImpl::Créer

Surchargé. Appelé par un gestionnaire Rich Preview pour créer la fenêtre Windows.

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

*hWndParent*<br/>
Une poignée à la fenêtre hôte fournie par la Shell pour Rich Preview.

*Rpc*<br/>
Spécifie la taille et la position initiales de la fenêtre.

*pContext*<br/>
Un pointeur vers un contexte de création.

### <a name="return-value"></a>Valeur de retour

TRUE si la création a abouti ; sinon, FALSE.

## <a name="cmfcpreviewctrlimpldestroy"></a><a name="destroy"></a>CMFCPreviewCtrlImpl::Destroy

Appelé par un gestionnaire Rich Preview quand il a besoin de détruire ce contrôle.

### <a name="syntax"></a>Syntaxe

```
virtual void Destroy();
```

## <a name="cmfcpreviewctrlimpldopaint"></a><a name="dopaint"></a>CMFCPreviewCtrlImpl::DoPaint

Appelé par le cadre pour rendre l’aperçu.

### <a name="syntax"></a>Syntaxe

```
virtual void DoPaint(
   CPaintDC* pDC
);
```

### <a name="parameters"></a>Paramètres

*pDC*<br/>
Un pointeur vers un contexte de dispositif pour la peinture.

## <a name="cmfcpreviewctrlimplfocus"></a><a name="focus"></a>CMFCPreviewCtrlImpl::Focus

Définit le focus d'entrée sur ce contrôle.

### <a name="syntax"></a>Syntaxe

```
virtual void Focus();
```

## <a name="cmfcpreviewctrlimplgetdocument"></a><a name="getdocument"></a>CMFCPreviewCtrlImpl::GetDocument

Renvoie un document connecté à ce contrôle de prévisualisation.

### <a name="syntax"></a>Syntaxe

```
ATL::IDocument* GetDocument();
```

### <a name="return-value"></a>Valeur de retour

Un pointeur à un document, dont le contenu est prévisualisé dans le contrôle.

## <a name="cmfcpreviewctrlimplm_clrbackcolor"></a><a name="m_clrbackcolor"></a>CMFCPreviewCtrlImpl::m_clrBackColor

Couleur de fond de la fenêtre d’aperçu.

### <a name="syntax"></a>Syntaxe

```
COLORREF m_clrBackColor;
```

## <a name="cmfcpreviewctrlimplm_clrtextcolor"></a><a name="m_clrtextcolor"></a>CMFCPreviewCtrlImpl::m_clrTextColor

Couleur de texte de la fenêtre de prévisualisation.

### <a name="syntax"></a>Syntaxe

```
COLORREF m_clrTextColor;
```

## <a name="cmfcpreviewctrlimplm_font--font-used-to-display-text-in-the-preview-window"></a><a name="m_font"></a>CMFCPreviewCtrlImpl::m_font Font utilisé pour afficher du texte dans la fenêtre de prévisualisation.

### <a name="syntax"></a>Syntaxe

```
CFont m_font;
```

## <a name="cmfcpreviewctrlimplm_pdocument"></a><a name="m_pdocument"></a>CMFCPreviewCtrlImpl::m_pDocument

Un pointeur d’un document dont le contenu est prévisualisé dans le contrôle.

### <a name="syntax"></a>Syntaxe

```
ATL::IDocument* m_pDocument;
```

## <a name="cmfcpreviewctrlimplredraw"></a><a name="redraw"></a>CMFCPreviewCtrlImpl::Redraw

Ca dit à ce contrôle de redessiner.

### <a name="syntax"></a>Syntaxe

```
virtual void Redraw();
```

## <a name="cmfcpreviewctrlimplsetdocument"></a><a name="setdocument"></a>CMFCPreviewCtrlImpl::SetDocument

Appelé par le gestionnaire de prévisualisation pour créer une relation entre la mise en œuvre du document et le contrôle de prévisualisation.

### <a name="syntax"></a>Syntaxe

```
void SetDocument(
   IDocument* pDocument
);
```

### <a name="parameters"></a>Paramètres

*pDocument*<br/>
Un pointeur à la mise en œuvre du document.

## <a name="cmfcpreviewctrlimplsethost"></a><a name="sethost"></a>CMFCPreviewCtrlImpl::SetHost

Définit un nouveau parent pour ce contrôle.

### <a name="syntax"></a>Syntaxe

```
virtual void SetHost(
   HWND hWndParent
);
```

### <a name="parameters"></a>Paramètres

*hWndParent*<br/>
Handle vers la nouvelle fenêtre parente.

## <a name="cmfcpreviewctrlimplsetpreviewvisuals"></a><a name="setpreviewvisuals"></a>CMFCPreviewCtrlImpl::SetPreviewVisuals

Appelé par un gestionnaire De preview riche quand il a besoin de définir des visuels de contenu de prévisualisation riche.

### <a name="syntax"></a>Syntaxe

```
virtual void SetPreviewVisuals(
   COLORREF clrBack,
   COLORREF clrText,
   const LOGFONTW *plf
);
```

### <a name="parameters"></a>Paramètres

*clrBack (en)*<br/>
Couleur de fond de la fenêtre d’aperçu.

*clrText*<br/>
Couleur de texte de la fenêtre de prévisualisation.

*plf (plf)*<br/>
Font utilisé pour afficher le texte dans la fenêtre de prévisualisation.

## <a name="cmfcpreviewctrlimplsetrect"></a><a name="setrect"></a>CMFCPreviewCtrlImpl::SetRect

Définit un nouveau rectangle de délimitation pour ce contrôle.

### <a name="syntax"></a>Syntaxe

```
virtual void SetRect(
   const RECT* prc,
   BOOL bRedraw
);
```

### <a name="parameters"></a>Paramètres

*Rpc*<br/>
Spécifie la nouvelle taille et la nouvelle position du contrôle d’aperçu.

*bRedraw (en)*<br/>
Précise si le contrôle doit être redessiné.

### <a name="remarks"></a>Notes

Habituellement, un nouveau rectangle de délimitation est réglé lorsque le contrôle de l’hôte est resized.

## <a name="cmfcpreviewctrlimplcmfcpreviewctrlimpl"></a><a name="dtor"></a>CMFCPreviewCtrlImpl::CMFCPreviewCtrlImpl

Destructs un objet de contrôle de prévisualisation.

### <a name="syntax"></a>Syntaxe

```
virtual ~CMFCPreviewCtrlImpl();
```
