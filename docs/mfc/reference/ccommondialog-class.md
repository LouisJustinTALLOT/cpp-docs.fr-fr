---
description: 'En savoir plus sur : classe CCommonDialog'
title: CCommonDialog, classe
ms.date: 11/04/2016
f1_keywords:
- CCommonDialog
- AFXDLGS/CCommonDialog
- AFXDLGS/CCommonDialog::CCommonDialog
helpviewer_keywords:
- CCommonDialog [MFC], CCommonDialog
ms.assetid: 1f68d65f-a0fd-4778-be22-ebbe51a95f95
ms.openlocfilehash: 927348982529f14eb0ad762019bb4463aaa77c99
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97227895"
---
# <a name="ccommondialog-class"></a>CCommonDialog, classe

Classe de base pour les classes qui encapsulent les fonctionnalités des boîtes de dialogue communes Windows.

## <a name="syntax"></a>Syntaxe

```
class CCommonDialog : public CDialog
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CCommonDialog::CCommonDialog](#ccommondialog)|Construit un objet `CCommonDialog`.|

## <a name="remarks"></a>Notes

Les classes suivantes encapsulent les fonctionnalités des boîtes de dialogue courantes de Windows :

- [CFileDialog](../../mfc/reference/cfiledialog-class.md)

- [CFontDialog](../../mfc/reference/cfontdialog-class.md)

- [CColorDialog](../../mfc/reference/ccolordialog-class.md)

- [CPageSetupDialog](../../mfc/reference/cpagesetupdialog-class.md)

- [CPrintDialog](../../mfc/reference/cprintdialog-class.md)

- [CPrintDialogEx](../../mfc/reference/cprintdialogex-class.md)

- [CFindReplaceDialog](../../mfc/reference/cfindreplacedialog-class.md)

- [COleDialog](../../mfc/reference/coledialog-class.md)

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

`CCommonDialog`

## <a name="requirements"></a>Spécifications

**En-tête :** afxdlgs. h

## <a name="ccommondialogccommondialog"></a><a name="ccommondialog"></a> CCommonDialog::CCommonDialog

Construit un objet `CCommonDialog`.

```
explicit CCommonDialog(CWnd* pParentWnd);
```

### <a name="parameters"></a>Paramètres

*pParentWnd*<br/>
Pointe vers l’objet de fenêtre parent ou propriétaire (de type [CWnd](../../mfc/reference/cwnd-class.md)) auquel l’objet de boîte de dialogue appartient. Si la valeur est NULL, la fenêtre parente de l’objet Dialog est définie sur la fenêtre d’application principale.

### <a name="remarks"></a>Notes

Pour obtenir des informations complètes, consultez [CDialog :: CDialog](../../mfc/reference/cdialog-class.md#cdialog) .

## <a name="see-also"></a>Voir aussi

[CDialog (classe)](../../mfc/reference/cdialog-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CFileDialog (classe)](../../mfc/reference/cfiledialog-class.md)<br/>
[CFontDialog, classe](../../mfc/reference/cfontdialog-class.md)<br/>
[CColorDialog, classe](../../mfc/reference/ccolordialog-class.md)<br/>
[CPageSetupDialog, classe](../../mfc/reference/cpagesetupdialog-class.md)<br/>
[CPrintDialog, classe](../../mfc/reference/cprintdialog-class.md)<br/>
[CFindReplaceDialog, classe](../../mfc/reference/cfindreplacedialog-class.md)<br/>
[COleDialog, classe](../../mfc/reference/coledialog-class.md)
