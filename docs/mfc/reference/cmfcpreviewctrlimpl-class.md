---
description: 'En savoir plus sur : classe Cmfcpreviewctrlimpl,'
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
ms.openlocfilehash: 09e4b8e023a55110986aafccfd2646d8e7775c31
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97334735"
---
# <a name="cmfcpreviewctrlimpl-class"></a>CMFCPreviewCtrlImpl, classe

Cette classe implémente une fenêtre qui est placée dans une fenêtre hôte fournie par le Shell pour l’aperçu riche.

## <a name="syntax"></a>Syntaxe

```
class CMFCPreviewCtrlImpl : public CWnd;
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[Cmfcpreviewctrlimpl, :: ~ Cmfcpreviewctrlimpl,](#dtor)|Détruit un objet contrôle d’aperçu.|
|[Cmfcpreviewctrlimpl, :: Cmfcpreviewctrlimpl,](#cmfcpreviewctrlimpl)|Construit un objet contrôle d’aperçu.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[Cmfcpreviewctrlimpl, :: Create](#create)|Surchargé. Appelée par un gestionnaire d’aperçus enrichis pour créer la fenêtre Windows.|
|[Cmfcpreviewctrlimpl, ::D estroy](#destroy)|Appelée par un gestionnaire d’aperçus détaillés lorsqu’il doit détruire ce contrôle.|
|[Cmfcpreviewctrlimpl, :: Focus](#focus)|Définit le focus d'entrée sur ce contrôle.|
|[Cmfcpreviewctrlimpl, :: GetDocument](#getdocument)|Retourne un document connecté à ce contrôle d’aperçu.|
|[Cmfcpreviewctrlimpl, :: redessin](#redraw)|Indique à ce contrôle qu’il doit être redessiné.|
|[Cmfcpreviewctrlimpl, :: SetDocument](#setdocument)|Appelée par le gestionnaire d’aperçus pour créer une relation entre l’implémentation de document et le contrôle d’aperçu.|
|[Cmfcpreviewctrlimpl, :: SetHost](#sethost)|Définit un nouveau parent pour ce contrôle.|
|[Cmfcpreviewctrlimpl, :: SetPreviewVisuals](#setpreviewvisuals)|Appelée par un gestionnaire d’aperçus détaillés lorsqu’il doit définir des éléments visuels d’un contenu riche en préversion.|
|[Cmfcpreviewctrlimpl, :: SetRect](#setrect)|Définit un nouveau rectangle englobant pour ce contrôle.|

### <a name="protected-methods"></a>Méthodes protégées

|Nom|Description|
|----------|-----------------|
|[Cmfcpreviewctrlimpl, ::D oPaint](#dopaint)|Appelé par l’infrastructure pour restituer l’aperçu.|

### <a name="protected-data-members"></a>Membres de données protégés

|Nom|Description|
|----------|-----------------|
|[Cmfcpreviewctrlimpl, :: m_clrBackColor](#m_clrbackcolor)|Couleur d’arrière-plan de la fenêtre d’aperçu.|
|[Cmfcpreviewctrlimpl, :: m_clrTextColor](#m_clrtextcolor)|Couleur du texte de la fenêtre d’aperçu.|
|[Cmfcpreviewctrlimpl, :: m_font](#m_font)|Police utilisée pour afficher le texte dans la fenêtre d’aperçu.|
|[Cmfcpreviewctrlimpl, :: m_pDocument](#m_pdocument)|Pointeur vers un document dont le contenu est affiché en aperçu dans le contrôle.|

## <a name="requirements"></a>Spécifications

**En-tête :** afxwin.h

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[Cmfcpreviewctrlimpl,](../../mfc/reference/cmfcpreviewctrlimpl-class.md)

## <a name="cmfcpreviewctrlimplcmfcpreviewctrlimpl"></a><a name="cmfcpreviewctrlimpl"></a> Cmfcpreviewctrlimpl, :: Cmfcpreviewctrlimpl,

Construit un objet contrôle d’aperçu.

### <a name="syntax"></a>Syntaxe

Cmfcpreviewctrlimpl, ();

## <a name="cmfcpreviewctrlimplcreate"></a><a name="create"></a> Cmfcpreviewctrlimpl, :: Create

Surchargé. Appelée par un gestionnaire d’aperçus enrichis pour créer la fenêtre Windows.

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
Handle de la fenêtre hôte fournie par le Shell pour l’aperçu riche.

*République*<br/>
Spécifie la taille et la position initiales de la fenêtre.

*pContext*<br/>
Pointeur vers un contexte de création.

### <a name="return-value"></a>Valeur renvoyée

TRUE si la création a abouti ; sinon, FALSE.

## <a name="cmfcpreviewctrlimpldestroy"></a><a name="destroy"></a> Cmfcpreviewctrlimpl, ::D estroy

Appelée par un gestionnaire d’aperçus détaillés lorsqu’il doit détruire ce contrôle.

### <a name="syntax"></a>Syntaxe

```
virtual void Destroy();
```

## <a name="cmfcpreviewctrlimpldopaint"></a><a name="dopaint"></a> Cmfcpreviewctrlimpl, ::D oPaint

Appelé par l’infrastructure pour restituer l’aperçu.

### <a name="syntax"></a>Syntaxe

```
virtual void DoPaint(
   CPaintDC* pDC
);
```

### <a name="parameters"></a>Paramètres

*Maîtres*<br/>
Pointeur vers un contexte de périphérique pour peindre.

## <a name="cmfcpreviewctrlimplfocus"></a><a name="focus"></a> Cmfcpreviewctrlimpl, :: Focus

Définit le focus d'entrée sur ce contrôle.

### <a name="syntax"></a>Syntaxe

```
virtual void Focus();
```

## <a name="cmfcpreviewctrlimplgetdocument"></a><a name="getdocument"></a> Cmfcpreviewctrlimpl, :: GetDocument

Retourne un document connecté à ce contrôle d’aperçu.

### <a name="syntax"></a>Syntaxe

```
ATL::IDocument* GetDocument();
```

### <a name="return-value"></a>Valeur de retour

Pointeur vers un document dont le contenu est affiché en aperçu dans le contrôle.

## <a name="cmfcpreviewctrlimplm_clrbackcolor"></a><a name="m_clrbackcolor"></a> Cmfcpreviewctrlimpl, :: m_clrBackColor

Couleur d’arrière-plan de la fenêtre d’aperçu.

### <a name="syntax"></a>Syntaxe

```
COLORREF m_clrBackColor;
```

## <a name="cmfcpreviewctrlimplm_clrtextcolor"></a><a name="m_clrtextcolor"></a> Cmfcpreviewctrlimpl, :: m_clrTextColor

Couleur du texte de la fenêtre d’aperçu.

### <a name="syntax"></a>Syntaxe

```
COLORREF m_clrTextColor;
```

## <a name="cmfcpreviewctrlimplm_font--font-used-to-display-text-in-the-preview-window"></a><a name="m_font"></a> Cmfcpreviewctrlimpl, :: m_font police utilisée pour afficher le texte dans la fenêtre d’aperçu.

### <a name="syntax"></a>Syntaxe

```
CFont m_font;
```

## <a name="cmfcpreviewctrlimplm_pdocument"></a><a name="m_pdocument"></a> Cmfcpreviewctrlimpl, :: m_pDocument

Pointeur vers un document dont le contenu est affiché en aperçu dans le contrôle.

### <a name="syntax"></a>Syntaxe

```
ATL::IDocument* m_pDocument;
```

## <a name="cmfcpreviewctrlimplredraw"></a><a name="redraw"></a> Cmfcpreviewctrlimpl, :: redessin

Indique à ce contrôle qu’il doit être redessiné.

### <a name="syntax"></a>Syntaxe

```
virtual void Redraw();
```

## <a name="cmfcpreviewctrlimplsetdocument"></a><a name="setdocument"></a> Cmfcpreviewctrlimpl, :: SetDocument

Appelée par le gestionnaire d’aperçus pour créer une relation entre l’implémentation de document et le contrôle d’aperçu.

### <a name="syntax"></a>Syntaxe

```cpp
void SetDocument(
   IDocument* pDocument
);
```

### <a name="parameters"></a>Paramètres

*pDocument*<br/>
Pointeur vers l’implémentation du document.

## <a name="cmfcpreviewctrlimplsethost"></a><a name="sethost"></a> Cmfcpreviewctrlimpl, :: SetHost

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

## <a name="cmfcpreviewctrlimplsetpreviewvisuals"></a><a name="setpreviewvisuals"></a> Cmfcpreviewctrlimpl, :: SetPreviewVisuals

Appelée par un gestionnaire d’aperçus détaillés lorsqu’il doit définir des éléments visuels d’un contenu riche en préversion.

### <a name="syntax"></a>Syntaxe

```
virtual void SetPreviewVisuals(
   COLORREF clrBack,
   COLORREF clrText,
   const LOGFONTW *plf
);
```

### <a name="parameters"></a>Paramètres

*clrBack*<br/>
Couleur d’arrière-plan de la fenêtre d’aperçu.

*clrText*<br/>
Couleur du texte de la fenêtre d’aperçu.

*plf*<br/>
Police utilisée pour afficher le texte dans la fenêtre d’aperçu.

## <a name="cmfcpreviewctrlimplsetrect"></a><a name="setrect"></a> Cmfcpreviewctrlimpl, :: SetRect

Définit un nouveau rectangle englobant pour ce contrôle.

### <a name="syntax"></a>Syntaxe

```
virtual void SetRect(
   const RECT* prc,
   BOOL bRedraw
);
```

### <a name="parameters"></a>Paramètres

*République*<br/>
Spécifie la nouvelle taille et la position du contrôle d’aperçu.

*bRedraw*<br/>
Spécifie si le contrôle doit être redessiné.

### <a name="remarks"></a>Notes

En général, un nouveau rectangle englobant est défini lorsque le contrôle hôte est redimensionné.

## <a name="cmfcpreviewctrlimplcmfcpreviewctrlimpl"></a><a name="dtor"></a> Cmfcpreviewctrlimpl, :: ~ Cmfcpreviewctrlimpl,

Détruit un objet contrôle d’aperçu.

### <a name="syntax"></a>Syntaxe

```
virtual ~CMFCPreviewCtrlImpl();
```
