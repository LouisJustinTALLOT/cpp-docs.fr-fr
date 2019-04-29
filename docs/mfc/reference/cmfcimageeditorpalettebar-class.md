---
title: Cmfcimageeditorpalettebar, classe
ms.date: 11/04/2016
f1_keywords:
- CMFCImageEditorPaletteBar
- AFXIMAGEEDITORDIALOG/CMFCImageEditorPaletteBar
- AFXIMAGEEDITORDIALOG/CMFCImageEditorPaletteBar::GetRowHeight
- AFXIMAGEEDITORDIALOG/CMFCImageEditorPaletteBar::IsButtonExtraSizeAvailable
helpviewer_keywords:
- CMFCImageEditorPaletteBar [MFC], GetRowHeight
- CMFCImageEditorPaletteBar [MFC], IsButtonExtraSizeAvailable
ms.assetid: 3fb7ba8e-f254-4d56-b913-9941b4ed8138
ms.openlocfilehash: 6812f3f425186484ef892d7f5c626c0dfce0f863
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62378100"
---
# <a name="cmfcimageeditorpalettebar-class"></a>Cmfcimageeditorpalettebar, classe

Fournit des fonctionnalités à une image de boîte de dialogue Éditeur de la barre de palette.

## <a name="syntax"></a>Syntaxe

```
class CMFCImageEditorPaletteBar : public CMFCToolBar
```

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|||
|-|-|
|Nom|Description|
|[CMFCImageEditorPaletteBar::GetRowHeight](#getrowheight)|Retourne la hauteur des boutons de barre d’outils. (Substitue [CMFCToolBar::GetRowHeight](../../mfc/reference/cmfctoolbar-class.md#getrowheight).)|
|[CMFCImageEditorPaletteBar::IsButtonExtraSizeAvailable](#isbuttonextrasizeavailable)|Détermine si la barre d’outils peut afficher des boutons qui ont étendu les bordures. (Substitue [CMFCToolBar::IsButtonExtraSizeAvailable](../../mfc/reference/cmfctoolbar-class.md#isbuttonextrasizeavailable).)|

### <a name="remarks"></a>Notes

Cette classe n’est pas destinée à être utilisée directement à partir de votre code.

Le framework utilise cette classe pour afficher une barre de palette dans une image de boîte de dialogue Éditeur. Pour plus d’informations sur l’image de boîte de dialogue Éditeur, consultez [CMFCImageEditorDialog, classe](../../mfc/reference/cmfcimageeditordialog-class.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CBasePane](../../mfc/reference/cbasepane-class.md)

[CPane](../../mfc/reference/cpane-class.md)

[CMFCBaseToolBa](../../mfc/reference/cmfcbasetoolbar-class.md)

[CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md)

[CMFCImageEditorPaletteBar](../../mfc/reference/cmfcimageeditorpalettebar-class.md)

## <a name="requirements"></a>Configuration requise

**En-tête :** afximageeditordialog.h

##  <a name="getrowheight"></a>  CMFCImageEditorPaletteBar::GetRowHeight

Retourne la hauteur des boutons de barre d’outils.

```
virtual int GetRowHeight() const;
```

### <a name="return-value"></a>Valeur de retour

La hauteur de chaque bouton de la barre d’outils.

##  <a name="isbuttonextrasizeavailable"></a>  CMFCImageEditorPaletteBar::IsButtonExtraSizeAvailable

Détermine si la barre d’outils peut afficher des boutons qui ont étendu les bordures.

```
virtual BOOL IsButtonExtraSizeAvailable() const;
```

### <a name="return-value"></a>Valeur de retour

Cette méthode retourne FALSE.

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[CMFCImageEditorDialog, classe](../../mfc/reference/cmfcimageeditordialog-class.md)
