---
title: CAtlPreviewCtrlImpl, classe
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
ms.openlocfilehash: fd94d0d6fe43d80b45def3f747c7b7d558de31d4
ms.sourcegitcommit: 2bc15c5b36372ab01fa21e9bcf718fa22705814f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "82167875"
---
# <a name="catlpreviewctrlimpl-class"></a>CAtlPreviewCtrlImpl, classe

Cette classe est une implémentation ATL d’une fenêtre qui est placée dans une fenêtre hôte fournie par le Shell pour l’aperçu riche.

> [!IMPORTANT]
> Cette classe et ses membres ne peuvent pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```cpp
class CAtlPreviewCtrlImpl : public CWindowImpl<CAtlPreviewCtrlImpl>, public IPreviewCtrl;
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CAtlPreviewCtrlImpl :: ~ CAtlPreviewCtrlImpl](#dtor)|Détruit un objet contrôle d’aperçu.|
|[CAtlPreviewCtrlImpl::CAtlPreviewCtrlImpl](#catlpreviewctrlimpl)|Construit un objet contrôle d’aperçu.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CAtlPreviewCtrlImpl :: Create](#create)|Appelée par un gestionnaire d’aperçus enrichis pour créer la fenêtre Windows.|
|[CAtlPreviewCtrlImpl ::D estroy](#destroy)|Appelée par un gestionnaire d’aperçus détaillés lorsqu’il doit détruire ce contrôle.|
|[CAtlPreviewCtrlImpl :: Focus](#focus)|Définit le focus d'entrée sur ce contrôle.|
|[CAtlPreviewCtrlImpl :: OnPaint](#onpaint)|Gère le message de WM_PAINT.|
|[CAtlPreviewCtrlImpl :: redessin](#redraw)|Indique à ce contrôle qu’il doit être redessiné.|
|[CAtlPreviewCtrlImpl::SetHost](#sethost)|Définit un nouveau parent pour ce contrôle.|
|[CAtlPreviewCtrlImpl::SetPreviewVisuals](#setpreviewvisuals)|Appelée par un gestionnaire d’aperçus détaillés lorsqu’il doit définir des éléments visuels d’un contenu riche en préversion.|
|[CAtlPreviewCtrlImpl :: SetRect](#setrect)|Définit un nouveau rectangle englobant pour ce contrôle.|

### <a name="protected-methods"></a>Méthodes protégées

|Nom|Description|
|----------|-----------------|
|[CAtlPreviewCtrlImpl ::D oPaint](#dopaint)|Appelé par l’infrastructure pour restituer l’aperçu.|

### <a name="protected-constants"></a>Constantes protégées

|Nom|Description|
|----------|-----------------|
|[CAtlPreviewCtrlImpl :: m_plf](#m_plf)|Police utilisée pour afficher le texte dans la fenêtre d’aperçu.|

### <a name="protected-data-members"></a>Membres de données protégés

|Nom|Description|
|----------|-----------------|
|[CAtlPreviewCtrlImpl :: m_clrBack](#m_clrback)|Couleur d’arrière-plan de la fenêtre d’aperçu.|
|[CAtlPreviewCtrlImpl :: m_clrText](#m_clrtext)|Couleur du texte de la fenêtre d’aperçu.|

## <a name="remarks"></a>Notes

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`TBase`

`ATL::CMessageMap`

`ATL::CWindowImplRoot<TBase>`

`ATL::CWindowImplBaseT<TBase,TWinTraits>`

[ATL :: CWindowImpl\<CAtlPreviewCtrlImpl>](../../atl/reference/cwindowimpl-class.md)

`IPreviewCtrl`

`ATL::CAtlPreviewCtrlImpl`

## <a name="requirements"></a>Spécifications

**En-tête :** atlpreviewctrlimpl. h

## <a name="catlpreviewctrlimplcatlpreviewctrlimpl"></a><a name="catlpreviewctrlimpl"></a>CAtlPreviewCtrlImpl::CAtlPreviewCtrlImpl

Construit un objet contrôle d’aperçu.

```cpp
CAtlPreviewCtrlImpl(void) : m_clrText(0),
   m_clrBack(RGB(255, 255, 255)), m_plf(NULL);
```

### <a name="remarks"></a>Notes

## <a name="catlpreviewctrlimplcatlpreviewctrlimpl"></a><a name="dtor"></a>CAtlPreviewCtrlImpl :: ~ CAtlPreviewCtrlImpl

Détruit un objet contrôle d’aperçu.

```cpp
virtual ~CAtlPreviewCtrlImpl(void);
```

### <a name="remarks"></a>Notes

## <a name="catlpreviewctrlimplcreate"></a><a name="create"></a>CAtlPreviewCtrlImpl :: Create

Appelée par un gestionnaire d’aperçus enrichis pour créer la fenêtre Windows.

```cpp
virtual BOOL Create(HWND hWndParent, const RECT* prc);
```

### <a name="parameters"></a>Paramètres

*hWndParent*<br/>
Handle de la fenêtre hôte fournie par le Shell pour l’aperçu riche.

*République*<br/>
Spécifie la taille et la position initiales de la fenêtre.

### <a name="return-value"></a>Valeur de retour

TRUE en cas de réussite, sinon FALSE.

### <a name="remarks"></a>Notes

## <a name="catlpreviewctrlimpldestroy"></a><a name="destroy"></a>CAtlPreviewCtrlImpl ::D estroy

Appelée par un gestionnaire d’aperçus détaillés lorsqu’il doit détruire ce contrôle.

```cpp
virtual void Destroy();
```

### <a name="remarks"></a>Notes

## <a name="catlpreviewctrlimpldopaint"></a><a name="dopaint"></a>CAtlPreviewCtrlImpl ::D oPaint

Appelé par l’infrastructure pour restituer l’aperçu.

```cpp
virtual void DoPaint(HDC hdc);
```

### <a name="parameters"></a>Paramètres

*HDC*<br/>
Handle d’un contexte de périphérique pour peindre.

### <a name="remarks"></a>Notes

## <a name="catlpreviewctrlimplfocus"></a><a name="focus"></a>CAtlPreviewCtrlImpl :: Focus

Définit le focus d'entrée sur ce contrôle.

```cpp
virtual void Focus();
```

### <a name="remarks"></a>Notes

## <a name="catlpreviewctrlimplm_clrback"></a><a name="m_clrback"></a>CAtlPreviewCtrlImpl :: m_clrBack

Couleur d’arrière-plan de la fenêtre d’aperçu.

```cpp
COLORREF m_clrBack;
```

### <a name="remarks"></a>Notes

## <a name="catlpreviewctrlimplm_clrtext"></a><a name="m_clrtext"></a>CAtlPreviewCtrlImpl :: m_clrText

Couleur du texte de la fenêtre d’aperçu.

```cpp
COLORREF m_clrText;
```

### <a name="remarks"></a>Notes

## <a name="catlpreviewctrlimplm_plf"></a><a name="m_plf"></a>CAtlPreviewCtrlImpl :: m_plf

Police utilisée pour afficher le texte dans la fenêtre d’aperçu.

```cpp
const LOGFONTW* m_plf;
```

### <a name="remarks"></a>Notes

## <a name="catlpreviewctrlimplonpaint"></a><a name="onpaint"></a>CAtlPreviewCtrlImpl :: OnPaint

Gère le message de WM_PAINT.

```cpp
LRESULT OnPaint(
    UINT nMsg,
    WPARAM wParam,
    LPARAM lParam,
    BOOL& bHandled);
```

### <a name="parameters"></a>Paramètres

*nMsg*<br/>
Définissez sur WM_PAINT.

*wParam*<br/>
Ce paramètre n'est pas utilisé.

*lParam*<br/>
Ce paramètre n'est pas utilisé.

*bHandled*<br/>
Lorsque cette fonction est retournée, elle contient la valeur TRUE.

### <a name="return-value"></a>Valeur de retour

Retourne toujours 0.

### <a name="remarks"></a>Notes

## <a name="catlpreviewctrlimplredraw"></a><a name="redraw"></a>CAtlPreviewCtrlImpl :: redessin

Indique à ce contrôle qu’il doit être redessiné.

```cpp
virtual void Redraw();
```

### <a name="remarks"></a>Notes

## <a name="catlpreviewctrlimplsethost"></a><a name="sethost"></a>CAtlPreviewCtrlImpl::SetHost

Définit un nouveau parent pour ce contrôle.

```cpp
virtual void SetHost(HWND hWndParent);
```

### <a name="parameters"></a>Paramètres

*hWndParent*<br/>
Handle vers la nouvelle fenêtre parente.

### <a name="remarks"></a>Notes

## <a name="catlpreviewctrlimplsetpreviewvisuals"></a><a name="setpreviewvisuals"></a>CAtlPreviewCtrlImpl::SetPreviewVisuals

Appelée par un gestionnaire d’aperçus détaillés lorsqu’il doit définir des éléments visuels d’un contenu riche en préversion.

```cpp
virtual void SetPreviewVisuals(
    COLORREF clrBack,
    COLORREF clrText,
    const LOGFONTW* plf);
```

### <a name="parameters"></a>Paramètres

*clrBack*<br/>
Couleur d’arrière-plan de la fenêtre d’aperçu.

*clrText*<br/>
Couleur du texte de la fenêtre d’aperçu.

*plf*<br/>
Police utilisée pour afficher le texte dans la fenêtre d’aperçu.

### <a name="remarks"></a>Notes

## <a name="catlpreviewctrlimplsetrect"></a><a name="setrect"></a>CAtlPreviewCtrlImpl :: SetRect

Définit un nouveau rectangle englobant pour ce contrôle.

```cpp
virtual void SetRect(const RECT* prc, BOOL bRedraw);
```

### <a name="parameters"></a>Paramètres

*République*<br/>
Spécifie la nouvelle taille et la position du contrôle d’aperçu.

*bRedraw*<br/>
Spécifie si le contrôle doit être redessiné.

### <a name="remarks"></a>Notes

## <a name="see-also"></a>Voir aussi

[Composants de bureau COM ATL](../../atl/atl-com-desktop-components.md)
