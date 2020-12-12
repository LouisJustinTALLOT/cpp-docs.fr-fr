---
description: 'En savoir plus sur : classe Cdialogex,'
title: Cdialogex,, classe
ms.date: 11/04/2016
f1_keywords:
- CDialogEx
- AFXDIALOGEX/CDialogEx
- AFXDIALOGEX/CDialogEx::CDialogEx
- AFXDIALOGEX/CDialogEx::SetBackgroundColor
- AFXDIALOGEX/CDialogEx::SetBackgroundImage
helpviewer_keywords:
- CDialogEx [MFC], CDialogEx
- CDialogEx [MFC], SetBackgroundColor
- CDialogEx [MFC], SetBackgroundImage
ms.assetid: a6ed3b1f-aef8-4b66-ac78-2160faf63c13
ms.openlocfilehash: 27ec0011935871d472734cae6f0d62b402382727
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97185243"
---
# <a name="cdialogex-class"></a>Cdialogex,, classe

La classe `CDialogEx` spécifie la couleur d'arrière-plan et l'image d'arrière-plan d'une boîte de dialogue.

## <a name="syntax"></a>Syntaxe

```
class CDialogEx : public CDialog
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CDialogEx::CDialogEx](#cdialogex)|Construit un objet `CDialogEx`.|
|`CDialogEx::~CDialogEx`|Destructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CDialogEx::SetBackgroundColor](#setbackgroundcolor)|Définit la couleur d'arrière-plan de la boîte de dialogue.|
|[CDialogEx::SetBackgroundImage](#setbackgroundimage)|Définit l'image d'arrière-plan de la boîte de dialogue.|

## <a name="remarks"></a>Notes

Pour utiliser la classe `CDialogEx`, dérivez votre classe de boîte de dialogue de la classe `CDialogEx` plutôt que de la classe `CDialog`.

Les images de boîte de dialogue sont stockées dans un fichier de ressources. Le framework supprime automatiquement toute image qui est chargée à partir du fichier de ressources. Pour supprimer par programmation l’image d’arrière-plan actuelle, appelez la méthode [cdialogex, :: SetBackgroundImage](#setbackgroundimage) ou implémentez un `OnDestroy` Gestionnaire d’événements. Quand vous appelez la méthode [cdialogex, :: SetBackgroundImage](#setbackgroundimage) , transmettez un `HBITMAP` paramètre comme handle d’image. L'objet `CDialogEx` prend possession de l'image et la supprime si l'indicateur `m_bAutoDestroyBmp` a pour valeur `TRUE`.

Un `CDialogEx` objet peut être un parent d’un objet de [classe CMFCPopupMenu](../../mfc/reference/cmfcpopupmenu-class.md) . L’objet de [classe CMFCPopupMenu](../../mfc/reference/cmfcpopupmenu-class.md) appelle la `CDialogEx::SetActiveMenu` méthode lorsque l’objet de [classe CMFCPopupMenu](../../mfc/reference/cmfcpopupmenu-class.md) s’ouvre. Ensuite, l' `CDialogEx` objet gère tout événement de menu jusqu’à la fermeture de l’objet de [classe CMFCPopupMenu](../../mfc/reference/cmfcpopupmenu-class.md) .

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CDialogEx](../../mfc/reference/cdialogex-class.md)

## <a name="requirements"></a>Spécifications

**En-tête :** afxdialogex. h

## <a name="cdialogexcdialogex"></a><a name="cdialogex"></a> Cdialogex, :: Cdialogex,

Construit un objet `CDialogEx`.

```
CDialogEx(
    UINT nIDTemplate,
    CWnd* pParent=NULL);

CDialogEx(
    LPCTSTR lpszTemplateName,
    CWnd* pParentWnd=NULL);
```

### <a name="parameters"></a>Paramètres

*nIDTemplate*<br/>
dans ID de ressource d’un modèle de boîte de dialogue.

*lpszTemplateName*<br/>
dans Nom de ressource d’un modèle de boîte de dialogue.

*pParent*<br/>
dans Pointeur vers la fenêtre parente. La valeur par défaut est NULL.

*pParentWnd*<br/>
dans Pointeur vers la fenêtre parente. La valeur par défaut est NULL.

### <a name="return-value"></a>Valeur renvoyée

### <a name="remarks"></a>Notes

## <a name="cdialogexsetbackgroundcolor"></a><a name="setbackgroundcolor"></a> Cdialogex, :: SetBackgroundColor

Définit la couleur d'arrière-plan de la boîte de dialogue.

```cpp
void SetBackgroundColor(
    COLORREF color,
    BOOL bRepaint=TRUE);
```

### <a name="parameters"></a>Paramètres

*color*<br/>
dans Valeur de couleur RVB.

*bRepaint*<br/>
dans TRUE pour mettre immédiatement à jour l’écran ; Sinon, FALSe. La valeur par défaut est TRUE.

### <a name="remarks"></a>Notes

## <a name="cdialogexsetbackgroundimage"></a><a name="setbackgroundimage"></a> Cdialogex, :: SetBackgroundImage

Définit l'image d'arrière-plan de la boîte de dialogue.

```cpp
void SetBackgroundImage(
    HBITMAP hBitmap,
    BackgroundLocation location=BACKGR_TILE,
    BOOL bAutoDestroy=TRUE,
    BOOL bRepaint=TRUE);

BOOL SetBackgroundImage(
    UINT uiBmpResId,
    BackgroundLocation location=BACKGR_TILE,
    BOOL bRepaint=TRUE);
```

### <a name="parameters"></a>Paramètres

*hBitmap*<br/>
dans Handle vers l’image d’arrière-plan.

*uiBmpResId*<br/>
dans ID de ressource de l’image d’arrière-plan.

*location*<br/>
dans L’une des `CDialogEx::BackgroundLocation` valeurs qui spécifient l’emplacement de l’image. Les valeurs valides sont BACKGR_TILE, BACKGR_TOPLEFT, BACKGR_TOPRIGHT, BACKGR_BOTTOMLEFT et BACKGR_BOTTOMRIGHT. La valeur par défaut est BACKGR_TILE.

*bAutoDestroy*<br/>
dans TRUE pour détruire automatiquement l’image d’arrière-plan ; Sinon, FALSe.

*bRepaint*<br/>
dans TRUE pour redessiner immédiatement la boîte de dialogue ; Sinon, FALSe.

### <a name="return-value"></a>Valeur renvoyée

Dans la deuxième syntaxe de surcharge de méthode, TRUE si la méthode réussit ; Sinon, FALSe.

### <a name="remarks"></a>Notes

L’image que vous spécifiez n’est pas étirée pour s’ajuster à la zone cliente de la boîte de dialogue.

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[CMFCPopupMenu, classe](../../mfc/reference/cmfcpopupmenu-class.md)<br/>
[CContextMenuManager, classe](../../mfc/reference/ccontextmenumanager-class.md)
