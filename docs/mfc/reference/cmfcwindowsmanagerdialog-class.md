---
title: Classe CMFCWindowsManagerDialog
ms.date: 11/04/2016
f1_keywords:
- CMFCWindowsManagerDialog
- AFXWINDOWSMANAGERDIALOG/CMFCWindowsManagerDialog
- AFXWINDOWSMANAGERDIALOG/CMFCWindowsManagerDialog::CMFCWindowsManagerDialog
helpviewer_keywords:
- CMFCWindowsManagerDialog [MFC], CMFCWindowsManagerDialog
ms.assetid: 35b4b0db-33c4-4b22-94d8-5e3396341340
ms.openlocfilehash: e3928c0d3ae4f607dceb99c0762277e8ea9ddbde
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81319827"
---
# <a name="cmfcwindowsmanagerdialog-class"></a>Classe CMFCWindowsManagerDialog

L’objet `CMFCWindowsManagerDialog` permet à un utilisateur de gérer les fenêtres de mDI dans une application MDI.

## <a name="syntax"></a>Syntaxe

```
class CMFCWindowsManagerDialog : public CDialog
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CMFCWindowsManagerDialog::CMFCWindowsManagerDialog](#cmfcwindowsmanagerdialog)|Construit un objet `CMFCWindowsManagerDialog`.|

## <a name="remarks"></a>Notes

Le `CMFCWindowsManagerDialog` contient une liste de fenêtres pour enfants MDI qui sont actuellement ouvertes dans l’application. L’utilisateur peut contrôler manuellement l’état des fenêtres de l’enfant MDI en utilisant cette boîte de dialogue.

`CMFCWindowsManagerDialog`est intégré à l’intérieur de la [classe CMDIFrameWndEx](../../mfc/reference/cmdiframewndex-class.md). Ce `CMFCWindowsManagerDialog` n’est pas une classe que vous devez créer manuellement. Au lieu de cela, appelez la fonction [CMDIFrameWndEx::ShowWindowsDialog](../../mfc/reference/cmdiframewndex-class.md#showwindowsdialog), et il va créer et afficher un `CMFCWindowsManagerDialog` objet.

## <a name="example"></a>Exemple

L’exemple suivant montre comment `CMFCWindowsManagerDialog` construire `CMDIFrameWndEx::ShowWindowsDialog`un objet en appelant . Cet extrait de code fait partie de [l’échantillon Visual Studio Demo](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_VisualStudioDemo#18](../../mfc/codesnippet/cpp/cmfcwindowsmanagerdialog-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CMFCWindowsManagerDialog](../../mfc/reference/cmfcwindowsmanagerdialog-class.md)

## <a name="requirements"></a>Spécifications

**En-tête:** afxWindowsManagerDialog.h

## <a name="cmfcwindowsmanagerdialogcmfcwindowsmanagerdialog"></a><a name="cmfcwindowsmanagerdialog"></a>CMFCWindowsManagerDialog::CMFCWindowsManagerDialog

Construit un objet [CMFCWindowsManagerDialog.](../../mfc/reference/cmfcwindowsmanagerdialog-class.md)

```
CMFCWindowsManagerDialog(
    CMDIFrameWndEx* pMDIFrame,
    BOOL bHelpButton = FALSE);
```

### <a name="parameters"></a>Paramètres

*pMDIFrame*<br/>
[dans] Un pointeur à la fenêtre du parent ou du propriétaire.

*bHelpButton*<br/>
[dans] Un paramètre Boolean qui précise si le cadre affiche un bouton **Aide.**

### <a name="remarks"></a>Notes

Pour plus d’informations sur les gestionnaires visuels, voir [Visualization Manager](../../mfc/visualization-manager.md).

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[Classe CMDIFrameWndEx](../../mfc/reference/cmdiframewndex-class.md)
