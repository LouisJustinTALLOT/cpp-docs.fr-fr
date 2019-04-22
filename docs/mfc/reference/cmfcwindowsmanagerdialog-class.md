---
title: Cmfcwindowsmanagerdialog, classe
ms.date: 11/04/2016
f1_keywords:
- CMFCWindowsManagerDialog
- AFXWINDOWSMANAGERDIALOG/CMFCWindowsManagerDialog
- AFXWINDOWSMANAGERDIALOG/CMFCWindowsManagerDialog::CMFCWindowsManagerDialog
helpviewer_keywords:
- CMFCWindowsManagerDialog [MFC], CMFCWindowsManagerDialog
ms.assetid: 35b4b0db-33c4-4b22-94d8-5e3396341340
ms.openlocfilehash: 5089decc7a118cd867aa14df51f5d7e269221108
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58767403"
---
# <a name="cmfcwindowsmanagerdialog-class"></a>Cmfcwindowsmanagerdialog, classe

Le `CMFCWindowsManagerDialog` objet permet à un utilisateur gérer les fenêtres MDI enfants dans une application MDI.

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

Le `CMFCWindowsManagerDialog` contient une liste des fenêtres enfants MDI qui sont actuellement ouverts dans l’application. L’utilisateur peut contrôler manuellement l’état des fenêtres MDI enfants à l’aide de cette boîte de dialogue.

`CMFCWindowsManagerDialog` est incorporé à l’intérieur de la [CMDIFrameWndEx, classe](../../mfc/reference/cmdiframewndex-class.md). Le `CMFCWindowsManagerDialog` n’est pas une classe que vous devez créer manuellement. Au lieu de cela, appelez la fonction [CMDIFrameWndEx::ShowWindowsDialog](../../mfc/reference/cmdiframewndex-class.md#showwindowsdialog), il crée et affiche un `CMFCWindowsManagerDialog` objet.

## <a name="example"></a>Exemple

L’exemple suivant montre comment construire un `CMFCWindowsManagerDialog` objet en appelant `CMDIFrameWndEx::ShowWindowsDialog`. Cet extrait de code fait partie de la [exemple de démonstration Visual Studio](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_VisualStudioDemo#18](../../mfc/codesnippet/cpp/cmfcwindowsmanagerdialog-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CMFCWindowsManagerDialog](../../mfc/reference/cmfcwindowsmanagerdialog-class.md)

## <a name="requirements"></a>Configuration requise

**En-tête :** afxWindowsManagerDialog.h

##  <a name="cmfcwindowsmanagerdialog"></a>  CMFCWindowsManagerDialog::CMFCWindowsManagerDialog

Construit un [CMFCWindowsManagerDialog](../../mfc/reference/cmfcwindowsmanagerdialog-class.md) objet.

```
CMFCWindowsManagerDialog(
    CMDIFrameWndEx* pMDIFrame,
    BOOL bHelpButton = FALSE);
```

### <a name="parameters"></a>Paramètres

*pMDIFrame*<br/>
[in] Pointeur vers la fenêtre parente ou propriétaire.

*bHelpButton*<br/>
[in] Un paramètre booléen qui spécifie si le framework affiche un **aide** bouton.

### <a name="remarks"></a>Notes

Pour plus d’informations sur les gestionnaires visuels, consultez [Gestionnaire de visualisation](../../mfc/visualization-manager.md).

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[CMDIFrameWndEx, classe](../../mfc/reference/cmdiframewndex-class.md)
