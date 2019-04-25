---
title: Cdialogex, classe
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
ms.openlocfilehash: f92058d1aa0dabccf6623d20a248fed8eb99ab26
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62168048"
---
# <a name="cdialogex-class"></a>Cdialogex, classe

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

Les images de boîte de dialogue sont stockées dans un fichier de ressources. Le framework supprime automatiquement toute image qui est chargée à partir du fichier de ressources. Pour supprimer par programmation l’image d’arrière-plan actuelle, appelez le [CDialogEx::SetBackgroundImage](#setbackgroundimage) méthode ou implémentez un `OnDestroy` Gestionnaire d’événements. Lorsque vous appelez le [CDialogEx::SetBackgroundImage](#setbackgroundimage) méthode, passez un `HBITMAP` paramètre en tant que handle de l’image. L'objet `CDialogEx` prend possession de l'image et la supprime si l'indicateur `m_bAutoDestroyBmp` a pour valeur `TRUE`.

Un `CDialogEx` objet peut être un parent d’un [cmfcpopupmenu, classe](../../mfc/reference/cmfcpopupmenu-class.md) objet. Le [cmfcpopupmenu, classe](../../mfc/reference/cmfcpopupmenu-class.md) object appelle le `CDialogEx::SetActiveMenu` méthode lorsque le [cmfcpopupmenu, classe](../../mfc/reference/cmfcpopupmenu-class.md) objet s’ouvre. Par la suite, le `CDialogEx` objet gère les événements de menu jusqu'à ce que le [cmfcpopupmenu, classe](../../mfc/reference/cmfcpopupmenu-class.md) objet est fermé.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CDialogEx](../../mfc/reference/cdialogex-class.md)

## <a name="requirements"></a>Configuration requise

**En-tête :** afxdialogex.h

##  <a name="cdialogex"></a>  CDialogEx::CDialogEx

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
[in] L’ID de ressource d’un modèle de boîte de dialogue.

*lpszTemplateName*<br/>
[in] Le nom de la ressource d’un modèle de boîte de dialogue.

*pParent*<br/>
[in] Pointeur vers la fenêtre parente. La valeur par défaut est NULL.

*pParentWnd*<br/>
[in] Pointeur vers la fenêtre parente. La valeur par défaut est NULL.

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

##  <a name="setbackgroundcolor"></a>  CDialogEx::SetBackgroundColor

Définit la couleur d'arrière-plan de la boîte de dialogue.

```
void SetBackgroundColor(
    COLORREF color,
    BOOL bRepaint=TRUE);
```

### <a name="parameters"></a>Paramètres

*color*<br/>
[in] Une valeur de couleur RVB.

*bRepaint*<br/>
[in] TRUE pour mettre immédiatement à jour l’écran ; Sinon, FALSE. La valeur par défaut est TRUE.

### <a name="remarks"></a>Notes

##  <a name="setbackgroundimage"></a>  CDialogEx::SetBackgroundImage

Définit l'image d'arrière-plan de la boîte de dialogue.

```
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
[in] Handle vers l’image d’arrière-plan.

*uiBmpResId*<br/>
[in] L’ID de ressource de l’image d’arrière-plan.

*location*<br/>
[in] Parmi les `CDialogEx::BackgroundLocation` valeurs qui spécifient l’emplacement de l’image. Les valeurs valides incluent BACKGR_TILE, BACKGR_TOPLEFT, BACKGR_TOPRIGHT, BACKGR_BOTTOMLEFT et BACKGR_BOTTOMRIGHT. La valeur par défaut est BACKGR_TILE.

*bAutoDestroy*<br/>
[in] TRUE pour détruire automatiquement l’image d’arrière-plan ; Sinon, FALSE.

*bRepaint*<br/>
[in] Valeur TRUE à se redessiner immédiatement avec la boîte de dialogue ; Sinon, FALSE.

### <a name="return-value"></a>Valeur de retour

Dans la deuxième méthode de surcharge syntaxe, TRUE si la méthode a réussi ; Sinon, FALSE.

### <a name="remarks"></a>Notes

L’image que vous spécifiez n’est pas étiré pour s’ajuster à la zone cliente de la boîte de dialogue.

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[CMFCPopupMenu, classe](../../mfc/reference/cmfcpopupmenu-class.md)<br/>
[CContextMenuManager, classe](../../mfc/reference/ccontextmenumanager-class.md)
