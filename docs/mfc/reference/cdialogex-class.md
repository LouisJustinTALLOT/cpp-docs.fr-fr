---
title: CDialogEx, classe
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
ms.openlocfilehash: 717e560035d42957c16168097577d0c8c589e3c7
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753351"
---
# <a name="cdialogex-class"></a>CDialogEx, classe

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

Les images de boîte de dialogue sont stockées dans un fichier de ressources. Le framework supprime automatiquement toute image qui est chargée à partir du fichier de ressources. Pour supprimer de manière programmatique l’image de fond actuelle, appelez la `OnDestroy` méthode [CDialogEx::SetBackgroundImage](#setbackgroundimage) ou implémenter un gestionnaire d’événements. Lorsque vous appelez la méthode [CDialogEx::SetBackgroundImage,](#setbackgroundimage) passez dans un paramètre comme poignée d’image. `HBITMAP` L'objet `CDialogEx` prend possession de l'image et la supprime si l'indicateur `m_bAutoDestroyBmp` a pour valeur `TRUE`.

Un `CDialogEx` objet peut être parent d’un objet [de classe CMFCPopupMenu.](../../mfc/reference/cmfcpopupmenu-class.md) [L’objet cmFCPopupMenu](../../mfc/reference/cmfcpopupmenu-class.md) `CDialogEx::SetActiveMenu` Class appelle la méthode lorsque l’objet [cmFCPopupMenu Class s’ouvre.](../../mfc/reference/cmfcpopupmenu-class.md) Par la `CDialogEx` suite, l’objet gère n’importe quel événement de menu jusqu’à ce que l’objet [cmFCPopupMenu Classe](../../mfc/reference/cmfcpopupmenu-class.md) soit fermé.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CDialogEx](../../mfc/reference/cdialogex-class.md)

## <a name="requirements"></a>Spécifications

**En-tête:** afxdialogex.h

## <a name="cdialogexcdialogex"></a><a name="cdialogex"></a>CDialogEx::CDialogEx

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

*nIDTemplate (en)*<br/>
[dans] L’ID de ressource d’un modèle de boîte de dialogue.

*lpszTemplateName*<br/>
[dans] Le nom de ressource d’un modèle de boîte de dialogue.

*pParent*<br/>
[dans] Un pointeur à la fenêtre parente. La valeur par défaut est NULL.

*pParentWnd*<br/>
[dans] Un pointeur à la fenêtre parente. La valeur par défaut est NULL.

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

## <a name="cdialogexsetbackgroundcolor"></a><a name="setbackgroundcolor"></a>CDialogEx::SetBackgroundColor

Définit la couleur d'arrière-plan de la boîte de dialogue.

```cpp
void SetBackgroundColor(
    COLORREF color,
    BOOL bRepaint=TRUE);
```

### <a name="parameters"></a>Paramètres

*Couleur*<br/>
[dans] Une valeur de couleur RGB.

*bRepaint (en anglais)*<br/>
[dans] VRAI pour mettre immédiatement à jour l’écran; autrement, FALSE. La valeur par défaut est TRUE.

### <a name="remarks"></a>Notes

## <a name="cdialogexsetbackgroundimage"></a><a name="setbackgroundimage"></a>CDialogEx::SetBackgroundImage

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

*hBitmap (en)*<br/>
[dans] Une poignée à l’image de fond.

*uiBmpResId*<br/>
[dans] L’ID de ressource de l’image de fond.

*location*<br/>
[dans] Une des `CDialogEx::BackgroundLocation` valeurs qui spécifient l’emplacement de l’image. Les valeurs valides comprennent les BACKGR_TILE, les BACKGR_TOPLEFT, les BACKGR_TOPRIGHT, les BACKGR_BOTTOMLEFT et les BACKGR_BOTTOMRIGHT. La valeur par défaut est BACKGR_TILE.

*bAutoDestroy*<br/>
[dans] VRAI pour détruire automatiquement l’image de fond; autrement, FALSE.

*bRepaint (en anglais)*<br/>
[dans] VRAI pour redessiner immédiatement la boîte de dialogue; autrement, FALSE.

### <a name="return-value"></a>Valeur de retour

Dans la deuxième méthode surcharge syntaxe, VRAI si la méthode est réussie; autrement, FALSE.

### <a name="remarks"></a>Notes

L’image que vous spécifiez n’est pas étirée pour s’adapter à la zone client de la boîte de dialogue.

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[CMFCPopupMenu, classe](../../mfc/reference/cmfcpopupmenu-class.md)<br/>
[CContextMenuManager, classe](../../mfc/reference/ccontextmenumanager-class.md)
