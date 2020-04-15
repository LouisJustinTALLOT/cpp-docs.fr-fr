---
title: Classe CAtlPreviewCtrlImpl
ms.date: 11/04/2016
f1_keywords:
- CAtlPreviewCtrlImpl
- ATLPREVIEWCTRLIMPL/ATL::CAtlPreviewCtrlImpl
- ATLPREVIEWCTRLIMPL/ATL::CAtlPreviewCtrlImpl::CAtlPreviewCtrlImpl
- ATLPREVIEWCTRLIMPL/ATL::CAtlPreviewCtrlImpl::Create
- ATLPREVIEWCTRLIMPL/ATL::CAtlPreviewCtrlImpl::Destroy
- ATLPREVIEWCTRLIMPL/ATL::CAtlPreviewCtrlImpl::Focus
- ATLPREVIEWCTRLIMPL/ATL::CAtlPreviewCtrlImpl::OnPaint
- ATLPREVIEWCTRLIMPL/ATL::CAtlPreviewCtrlImpl::Redraw
- ATLPREVIEWCTRLIMPL/ATL::CAtlPreviewCtrlImpl::SetHost
- ATLPREVIEWCTRLIMPL/ATL::CAtlPreviewCtrlImpl::SetPreviewVisuals
- ATLPREVIEWCTRLIMPL/ATL::CAtlPreviewCtrlImpl::SetRect
- ATLPREVIEWCTRLIMPL/ATL::CAtlPreviewCtrlImpl::DoPaint
- ATLPREVIEWCTRLIMPL/ATL::CAtlPreviewCtrlImpl::m_plf
- ATLPREVIEWCTRLIMPL/ATL::CAtlPreviewCtrlImpl::m_clrBack
- ATLPREVIEWCTRLIMPL/ATL::CAtlPreviewCtrlImpl::m_clrText
helpviewer_keywords:
- CAtlPreviewCtrlImpl class
ms.assetid: 39b3299e-07e4-4abc-9b6e-b54bfa3b0802
ms.openlocfilehash: 1ccd01bc4d48dc088538f4799b595cce3fb910ba
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81321369"
---
# <a name="catlpreviewctrlimpl-class"></a>Classe CAtlPreviewCtrlImpl

Cette classe est une mise en œuvre ATL d’une fenêtre qui est placé sur une fenêtre hôte fournie par la Shell pour Rich Preview.

> [!IMPORTANT]
> Cette classe et ses membres ne peuvent pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
class CAtlPreviewCtrlImpl : public CWindowImpl<CAtlPreviewCtrlImpl>, public IPreviewCtrl;
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CAtlPreviewCtrlImpl::CAtlPreviewCtrlImpl](#dtor)|Destructs un objet de contrôle de prévisualisation.|
|[CAtlPreviewCtrlImpl::CAtlPreviewCtrlImpl](#catlpreviewctrlimpl)|Construit un objet de contrôle de prévisualisation.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CAtlPreviewCtrlImpl::Créer](#create)|Appelé par un gestionnaire Rich Preview pour créer la fenêtre Windows.|
|[CAtlPreviewCtrlImpl::Destroy](#destroy)|Appelé par un gestionnaire Rich Preview quand il a besoin de détruire ce contrôle.|
|[CAtlPreviewCtrlImpl::Focus](#focus)|Définit le focus d'entrée sur ce contrôle.|
|[CAtlPreviewCtrlImpl::OnPaint](#onpaint)|Gère le message WM_PAINT.|
|[CAtlPreviewCtrlImpl::Redraw](#redraw)|Ca dit à ce contrôle de redessiner.|
|[CAtlPreviewCtrlImpl::SetHost](#sethost)|Définit un nouveau parent pour ce contrôle.|
|[CAtlPreviewCtrlImpl::SetPreviewVisuals](#setpreviewvisuals)|Appelé par un gestionnaire De preview riche quand il a besoin de définir des visuels de contenu de prévisualisation riche.|
|[CAtlPreviewCtrlImpl::SetRect](#setrect)|Définit un nouveau rectangle de délimitation pour ce contrôle.|

### <a name="protected-methods"></a>Méthodes protégées

|Nom|Description|
|----------|-----------------|
|[CAtlPreviewCtrlImpl::DoPaint](#dopaint)|Appelé par le cadre pour rendre l’aperçu.|

### <a name="protected-constants"></a>Constants protégés

|Nom|Description|
|----------|-----------------|
|[CAtlPreviewCtrlImpl::m_plf](#m_plf)|Font utilisé pour afficher le texte dans la fenêtre de prévisualisation.|

### <a name="protected-data-members"></a>Membres de données protégés

|Nom|Description|
|----------|-----------------|
|[CAtlPreviewCtrlImpl::m_clrBack](#m_clrback)|Couleur de fond de la fenêtre d’aperçu.|
|[CAtlPreviewCtrlImpl::m_clrText](#m_clrtext)|Couleur de texte de la fenêtre de prévisualisation.|

## <a name="remarks"></a>Notes

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`TBase`

`ATL::CMessageMap`

`ATL::CWindowImplRoot<TBase>`

`ATL::CWindowImplBaseT<TBase,TWinTraits>`

[ATL::CWindowImpl\<CAtlPreviewCtrlImpl>](../../atl/reference/cwindowimpl-class.md)

`IPreviewCtrl`

`ATL::CAtlPreviewCtrlImpl`

## <a name="requirements"></a>Spécifications

**En-tête:** atlpreviewctrlimpl.h

## <a name="catlpreviewctrlimplcatlpreviewctrlimpl"></a><a name="catlpreviewctrlimpl"></a>CAtlPreviewCtrlImpl::CAtlPreviewCtrlImpl

Construit un objet de contrôle de prévisualisation.

```
CAtlPreviewCtrlImpl(void) : m_clrText(0),
   m_clrBack(RGB(255, 255, 255)), m_plf(NULL);
```

### <a name="remarks"></a>Notes

## <a name="catlpreviewctrlimplcatlpreviewctrlimpl"></a><a name="dtor"></a>CAtlPreviewCtrlImpl::CAtlPreviewCtrlImpl

Destructs un objet de contrôle de prévisualisation.

```
virtual ~CAtlPreviewCtrlImpl(void);
```

### <a name="remarks"></a>Notes

## <a name="catlpreviewctrlimplcreate"></a><a name="create"></a>CAtlPreviewCtrlImpl::Créer

Appelé par un gestionnaire Rich Preview pour créer la fenêtre Windows.

```
virtual BOOL Create(HWND hWndParent, const RECT* prc);
```

### <a name="parameters"></a>Paramètres

*hWndParent*<br/>
Une poignée à la fenêtre hôte fournie par la Shell pour Rich Preview.

*Rpc*<br/>
Spécifie la taille et la position initiales de la fenêtre.

### <a name="return-value"></a>Valeur de retour

TRUE en cas de réussite, sinon FALSE.

### <a name="remarks"></a>Notes

## <a name="catlpreviewctrlimpldestroy"></a><a name="destroy"></a>CAtlPreviewCtrlImpl::Destroy

Appelé par un gestionnaire Rich Preview quand il a besoin de détruire ce contrôle.

```
virtual void Destroy();
```

### <a name="remarks"></a>Notes

## <a name="catlpreviewctrlimpldopaint"></a><a name="dopaint"></a>CAtlPreviewCtrlImpl::DoPaint

Appelé par le cadre pour rendre l’aperçu.

```
virtual void DoPaint(HDC hdc);
```

### <a name="parameters"></a>Paramètres

*Hdc*<br/>
Une poignée à un contexte d’appareil pour la peinture.

### <a name="remarks"></a>Notes

## <a name="catlpreviewctrlimplfocus"></a><a name="focus"></a>CAtlPreviewCtrlImpl::Focus

Définit le focus d'entrée sur ce contrôle.

```
virtual void Focus();
```

### <a name="remarks"></a>Notes

## <a name="catlpreviewctrlimplm_clrback"></a><a name="m_clrback"></a>CAtlPreviewCtrlImpl::m_clrBack

Couleur de fond de la fenêtre d’aperçu.

```
COLORREF m_clrBack;
```

### <a name="remarks"></a>Notes

## <a name="catlpreviewctrlimplm_clrtext"></a><a name="m_clrtext"></a>CAtlPreviewCtrlImpl::m_clrText

Couleur de texte de la fenêtre de prévisualisation.

```
COLORREF m_clrText;
```

### <a name="remarks"></a>Notes

## <a name="catlpreviewctrlimplm_plf"></a><a name="m_plf"></a>CAtlPreviewCtrlImpl::m_plf

Font utilisé pour afficher le texte dans la fenêtre de prévisualisation.

```
const LOGFONTW* m_plf;
```

### <a name="remarks"></a>Notes

## <a name="catlpreviewctrlimplonpaint"></a><a name="onpaint"></a>CAtlPreviewCtrlImpl::OnPaint

Gère le message WM_PAINT.

```
LRESULT OnPaint(
    UINT nMsg,
    WPARAM wParam,
    LPARAM lParam,
    BOOL& bHandled);
```

### <a name="parameters"></a>Paramètres

*nMsg*<br/>
Régler pour WM_PAINT.

*wParam*<br/>
Ce paramètre n'est pas utilisé.

*lParam*<br/>
Ce paramètre n'est pas utilisé.

*bHandled*<br/>
Lorsque cette fonction revient, elle contient TRUE.

### <a name="return-value"></a>Valeur de retour

Retourne toujours 0.

### <a name="remarks"></a>Notes

## <a name="catlpreviewctrlimplredraw"></a><a name="redraw"></a>CAtlPreviewCtrlImpl::Redraw

Ca dit à ce contrôle de redessiner.

```
virtual void Redraw();
```

### <a name="remarks"></a>Notes

## <a name="catlpreviewctrlimplsethost"></a><a name="sethost"></a>CAtlPreviewCtrlImpl::SetHost

Définit un nouveau parent pour ce contrôle.

```
virtual void SetHost(HWND hWndParent);
```

### <a name="parameters"></a>Paramètres

*hWndParent*<br/>
Handle vers la nouvelle fenêtre parente.

### <a name="remarks"></a>Notes

## <a name="catlpreviewctrlimplsetpreviewvisuals"></a><a name="setpreviewvisuals"></a>CAtlPreviewCtrlImpl::SetPreviewVisuals

Appelé par un gestionnaire De preview riche quand il a besoin de définir des visuels de contenu de prévisualisation riche.

```
virtual void SetPreviewVisuals(
    COLORREF clrBack,
    COLORREF clrText,
    const LOGFONTW* plf);
```

### <a name="parameters"></a>Paramètres

*clrBack (en)*<br/>
Couleur de fond de la fenêtre d’aperçu.

*clrText*<br/>
Couleur de texte de la fenêtre de prévisualisation.

*plf (plf)*<br/>
Font utilisé pour afficher le texte dans la fenêtre de prévisualisation.

### <a name="remarks"></a>Notes

## <a name="catlpreviewctrlimplsetrect"></a><a name="setrect"></a>CAtlPreviewCtrlImpl::SetRect

Définit un nouveau rectangle de délimitation pour ce contrôle.

```
virtual void SetRect(const RECT* prc, BOOL bRedraw);
```

### <a name="parameters"></a>Paramètres

*Rpc*<br/>
Spécifie la nouvelle taille et la nouvelle position du contrôle d’aperçu.

*bRedraw (en)*<br/>
Précise si le contrôle doit être redessiné.

### <a name="remarks"></a>Notes

## <a name="see-also"></a>Voir aussi

[Composants de bureau COM ATL](../../atl/atl-com-desktop-components.md)
