---
description: 'En savoir plus sur : classe CMFCWindowsManagerDialog'
title: CMFCWindowsManagerDialog, classe
ms.date: 11/04/2016
f1_keywords:
- CMFCWindowsManagerDialog
- AFXWINDOWSMANAGERDIALOG/CMFCWindowsManagerDialog
- AFXWINDOWSMANAGERDIALOG/CMFCWindowsManagerDialog::CMFCWindowsManagerDialog
helpviewer_keywords:
- CMFCWindowsManagerDialog [MFC], CMFCWindowsManagerDialog
ms.assetid: 35b4b0db-33c4-4b22-94d8-5e3396341340
ms.openlocfilehash: 526cf731e049ffd267382b0c3895b5d29792dcb0
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97331622"
---
# <a name="cmfcwindowsmanagerdialog-class"></a>CMFCWindowsManagerDialog, classe

L' `CMFCWindowsManagerDialog` objet permet à un utilisateur de gérer des fenêtres enfants MDI dans une application MDI.

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

`CMFCWindowsManagerDialog`Contient une liste de fenêtres MDI enfants actuellement ouvertes dans l’application. L’utilisateur peut contrôler manuellement l’état des fenêtres MDI enfants à l’aide de cette boîte de dialogue.

`CMFCWindowsManagerDialog` est incorporé à l’intérieur de la [classe CMDIFrameWndEx](../../mfc/reference/cmdiframewndex-class.md). `CMFCWindowsManagerDialog`N’est pas une classe que vous devez créer manuellement. Au lieu de cela, appelez la fonction [CMDIFrameWndEx :: ShowWindowsDialog](../../mfc/reference/cmdiframewndex-class.md#showwindowsdialog), qui créera et affichera un `CMFCWindowsManagerDialog` objet.

## <a name="example"></a>Exemple

L’exemple suivant montre comment construire un `CMFCWindowsManagerDialog` objet en appelant `CMDIFrameWndEx::ShowWindowsDialog` . Cet extrait de code fait partie de l' [exemple de démonstration Visual Studio](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_VisualStudioDemo#18](../../mfc/codesnippet/cpp/cmfcwindowsmanagerdialog-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CMFCWindowsManagerDialog](../../mfc/reference/cmfcwindowsmanagerdialog-class.md)

## <a name="requirements"></a>Spécifications

**En-tête :** afxWindowsManagerDialog. h

## <a name="cmfcwindowsmanagerdialogcmfcwindowsmanagerdialog"></a><a name="cmfcwindowsmanagerdialog"></a> CMFCWindowsManagerDialog::CMFCWindowsManagerDialog

Construit un objet [CMFCWindowsManagerDialog](../../mfc/reference/cmfcwindowsmanagerdialog-class.md) .

```
CMFCWindowsManagerDialog(
    CMDIFrameWndEx* pMDIFrame,
    BOOL bHelpButton = FALSE);
```

### <a name="parameters"></a>Paramètres

*pMDIFrame*<br/>
dans Pointeur vers la fenêtre parente ou propriétaire.

*bHelpButton*<br/>
dans Paramètre booléen qui spécifie si l’infrastructure affiche un bouton **aide** .

### <a name="remarks"></a>Notes

Pour plus d’informations sur les gestionnaires visuels, consultez la page [Gestionnaire de visualisation](../../mfc/visualization-manager.md).

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[CMDIFrameWndEx, classe](../../mfc/reference/cmdiframewndex-class.md)
