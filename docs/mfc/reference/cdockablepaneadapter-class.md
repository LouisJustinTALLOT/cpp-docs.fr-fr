---
title: Cdockablepaneadapter, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CDockablePaneAdapter
- AFXDOCKABLEPANEADAPTER/CDockablePaneAdapter
- AFXDOCKABLEPANEADAPTER/CDockablePaneAdapter::GetWrappedWnd
- AFXDOCKABLEPANEADAPTER/CDockablePaneAdapter::LoadState
- AFXDOCKABLEPANEADAPTER/CDockablePaneAdapter::SaveState
- AFXDOCKABLEPANEADAPTER/CDockablePaneAdapter::SetWrappedWnd
dev_langs:
- C++
helpviewer_keywords:
- CDockablePaneAdapter [MFC], GetWrappedWnd
- CDockablePaneAdapter [MFC], LoadState
- CDockablePaneAdapter [MFC], SaveState
- CDockablePaneAdapter [MFC], SetWrappedWnd
ms.assetid: 6ed6cf82-f39c-4d0c-bf7c-8641495cf8f3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1cec0a5c40d7937e8df20b5437b6dcc83b1b9ec1
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46441173"
---
# <a name="cdockablepaneadapter-class"></a>Cdockablepaneadapter, classe

Fournit la prise en charge de l'ancrage pour les volets dérivés de `CWnd`.

## <a name="syntax"></a>Syntaxe

```
class CDockablePaneAdapter : public CDockablePane
```

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CDockablePaneAdapter::GetWrappedWnd](#getwrappedwnd)|Retourne la fenêtre incluse dans un wrapper.|
|[CDockablePaneAdapter::LoadState](#loadstate)|(Substitue [CDockablePane::LoadState](cdockablepane-class.md#loadstate).)|
|[CDockablePaneAdapter::SaveState](#savestate)|(Substitue [CDockablePane::SaveState](cdockablepane-class.md).)|
|[CDockablePaneAdapter::SetWrappedWnd](#setwrappedwnd)||

## <a name="remarks"></a>Notes

En règle générale, l’infrastructure instancie les objets de cette classe lorsque vous utilisez le [CMFCBaseTabCtrl::AddTab](../../mfc/reference/cmfcbasetabctrl-class.md#addtab) ou [CMFCBaseTabCtrl::InsertTab](../../mfc/reference/cmfcbasetabctrl-class.md#inserttab) méthodes.

Si vous souhaitez personnaliser le `CDockablePaneAdapter` comportement, simplement dériver une nouvelle classe à partir de celui-ci et définir les informations de classe runtime pour une fenêtre à onglets à l’aide de [CMFCBaseTabCtrl::SetDockingBarWrapperRTC](../../mfc/reference/cmfcbasetabctrl-class.md#setdockingbarwrapperrtc).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md) [CCmdTarget](../../mfc/reference/ccmdtarget-class.md) [CWnd](../../mfc/reference/cwnd-class.md)

[CBasePane](../../mfc/reference/cbasepane-class.md) [CPane](../../mfc/reference/cpane-class.md) [CDockablePane](../../mfc/reference/cdockablepane-class.md)

[CDockablePaneAdapter](../../mfc/reference/cdockablepaneadapter-class.md)

## <a name="requirements"></a>Configuration requise

**En-tête :** afxDockablePaneAdapter.h

##  <a name="getwrappedwnd"></a>  CDockablePaneAdapter::GetWrappedWnd

Retourne la fenêtre sous-jacente pour l’adaptateur de volet Ancrable.

```
virtual CWnd* GetWrappedWnd() const;
```

### <a name="return-value"></a>Valeur de retour

Pointeur vers la fenêtre encapsulée.

### <a name="remarks"></a>Notes

Cette fonction permet d’accéder à la fenêtre encapsulée.

##  <a name="loadstate"></a>  CDockablePaneAdapter::LoadState

Charge l’état du volet à partir du Registre.

```
virtual BOOL LoadState(
    LPCTSTR lpszProfileName = NULL,
    int nIndex = -1,
    UINT uiID = (UINT) -1);
```

### <a name="parameters"></a>Paramètres

*lpszProfileName*<br/>
[in] Le nom du profil.

*nIndex*<br/>
[in] L’index de profil.

*uiID*<br/>
[in] L’ID du volet.

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

##  <a name="savestate"></a>  CDockablePaneAdapter::SaveState

Enregistre l’état du volet dans le Registre.

```
virtual BOOL SaveState(
    LPCTSTR lpszProfileName = NULL,
    int nIndex = -1,
    UINT uiID = (UINT) -1);
```

### <a name="parameters"></a>Paramètres

*lpszProfileName*<br/>
[in] Le nom du profil.

*nIndex*<br/>
[in] L’index de profil (par défaut, l’ID de contrôle de la fenêtre).

*uiID*<br/>
[in] L’ID du volet.

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

##  <a name="setwrappedwnd"></a>  CDockablePaneAdapter::SetWrappedWnd

Définit la fenêtre sous-jacente pour l’adaptateur de volet Ancrable.

```
virtual BOOL SetWrappedWnd(CWnd* pWnd);
```

### <a name="parameters"></a>Paramètres

*pWnd*<br/>
[in] Pointeur vers la fenêtre de l’adaptateur de volet à encapsuler.

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[CDockablePane, classe](../../mfc/reference/cdockablepane-class.md)
