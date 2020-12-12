---
description: 'En savoir plus sur : classe CDockablePaneAdapter'
title: CDockablePaneAdapter, classe
ms.date: 11/04/2016
f1_keywords:
- CDockablePaneAdapter
- AFXDOCKABLEPANEADAPTER/CDockablePaneAdapter
- AFXDOCKABLEPANEADAPTER/CDockablePaneAdapter::GetWrappedWnd
- AFXDOCKABLEPANEADAPTER/CDockablePaneAdapter::LoadState
- AFXDOCKABLEPANEADAPTER/CDockablePaneAdapter::SaveState
- AFXDOCKABLEPANEADAPTER/CDockablePaneAdapter::SetWrappedWnd
helpviewer_keywords:
- CDockablePaneAdapter [MFC], GetWrappedWnd
- CDockablePaneAdapter [MFC], LoadState
- CDockablePaneAdapter [MFC], SaveState
- CDockablePaneAdapter [MFC], SetWrappedWnd
ms.assetid: 6ed6cf82-f39c-4d0c-bf7c-8641495cf8f3
ms.openlocfilehash: 0a46ef15d35194203d6e5c035555de0d80b63c72
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97185035"
---
# <a name="cdockablepaneadapter-class"></a>CDockablePaneAdapter, classe

Fournit la prise en charge de l'ancrage pour les volets dérivés de `CWnd`.

## <a name="syntax"></a>Syntaxe

```
class CDockablePaneAdapter : public CDockablePane
```

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CDockablePaneAdapter :: GetWrappedWnd](#getwrappedwnd)|Retourne la fenêtre incluse dans un wrapper.|
|[CDockablePaneAdapter::LoadState](#loadstate)|(Substitue [CDockablePane :: LoadState](cdockablepane-class.md#loadstate).)|
|[CDockablePaneAdapter::SaveState](#savestate)|(Substitue [CDockablePane :: saveste](cdockablepane-class.md).)|
|[CDockablePaneAdapter::SetWrappedWnd](#setwrappedwnd)||

## <a name="remarks"></a>Notes

En général, le Framework instancie les objets de cette classe lorsque vous utilisez les méthodes [CMFCBaseTabCtrl :: addTab](../../mfc/reference/cmfcbasetabctrl-class.md#addtab) ou [CMFCBaseTabCtrl :: InsertTab](../../mfc/reference/cmfcbasetabctrl-class.md#inserttab) .

Si vous souhaitez personnaliser le `CDockablePaneAdapter` comportement, il vous suffit de dériver une nouvelle classe de celle-ci et de définir les informations de classe Runtime dans une fenêtre à onglets à l’aide de [CMFCBaseTabCtrl :: SetDockingBarWrapperRTC](../../mfc/reference/cmfcbasetabctrl-class.md#setdockingbarwrapperrtc).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)\
└ &nbsp; [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)\
&nbsp;&nbsp;&nbsp;&nbsp;└ &nbsp; [CWnd](../../mfc/reference/cwnd-class.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;└ &nbsp; [CBasePane](../../mfc/reference/cbasepane-class.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;└ &nbsp; [CPane](../../mfc/reference/cpane-class.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;└ &nbsp; [CDockablePane](../../mfc/reference/cdockablepane-class.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;└ &nbsp; [CDockablePaneAdapter](../../mfc/reference/cdockablepaneadapter-class.md)

## <a name="requirements"></a>Spécifications

**En-tête :** afxDockablePaneAdapter. h

## <a name="cdockablepaneadaptergetwrappedwnd"></a><a name="getwrappedwnd"></a> CDockablePaneAdapter :: GetWrappedWnd

Retourne la fenêtre sous-jacente de l’adaptateur de volet Ancrable.

```
virtual CWnd* GetWrappedWnd() const;
```

### <a name="return-value"></a>Valeur renvoyée

Pointeur vers la fenêtre encapsulée.

### <a name="remarks"></a>Notes

Utilisez cette fonction pour accéder à la fenêtre encapsulée.

## <a name="cdockablepaneadapterloadstate"></a><a name="loadstate"></a> CDockablePaneAdapter :: LoadState

Charge l’état du volet à partir du Registre.

```
virtual BOOL LoadState(
    LPCTSTR lpszProfileName = NULL,
    int nIndex = -1,
    UINT uiID = (UINT) -1);
```

### <a name="parameters"></a>Paramètres

*lpszProfileName*<br/>
dans Nom du profil.

*nIndex*<br/>
dans Index du profil.

*uiID*<br/>
dans ID du volet.

### <a name="return-value"></a>Valeur renvoyée

### <a name="remarks"></a>Notes

## <a name="cdockablepaneadaptersavestate"></a><a name="savestate"></a> CDockablePaneAdapter :: saveste

Enregistre l’état du volet dans le registre.

```
virtual BOOL SaveState(
    LPCTSTR lpszProfileName = NULL,
    int nIndex = -1,
    UINT uiID = (UINT) -1);
```

### <a name="parameters"></a>Paramètres

*lpszProfileName*<br/>
dans Nom du profil.

*nIndex*<br/>
dans Index de profil (valeur par défaut : l’ID de contrôle de la fenêtre).

*uiID*<br/>
dans ID du volet.

### <a name="return-value"></a>Valeur renvoyée

### <a name="remarks"></a>Notes

## <a name="cdockablepaneadaptersetwrappedwnd"></a><a name="setwrappedwnd"></a> CDockablePaneAdapter :: SetWrappedWnd

Définit la fenêtre sous-jacente de l’adaptateur de volet Ancrable.

```
virtual BOOL SetWrappedWnd(CWnd* pWnd);
```

### <a name="parameters"></a>Paramètres

*pWnd*<br/>
dans Pointeur vers la fenêtre de l’adaptateur de volet à encapsuler.

### <a name="return-value"></a>Valeur renvoyée

### <a name="remarks"></a>Notes

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[CDockablePane, classe](../../mfc/reference/cdockablepane-class.md)
