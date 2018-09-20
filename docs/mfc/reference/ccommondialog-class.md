---
title: Ccommondialog, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CCommonDialog
- AFXDLGS/CCommonDialog
- AFXDLGS/CCommonDialog::CCommonDialog
dev_langs:
- C++
helpviewer_keywords:
- CCommonDialog [MFC], CCommonDialog
ms.assetid: 1f68d65f-a0fd-4778-be22-ebbe51a95f95
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c79c00dd81029a4a3f210178b732d6e9e8f5700f
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46409856"
---
# <a name="ccommondialog-class"></a>Ccommondialog, classe

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

Les classes suivantes encapsulent la fonctionnalité des boîtes de dialogue communes Windows :

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

## <a name="requirements"></a>Configuration requise

**En-tête :** afxdlgs.h

##  <a name="ccommondialog"></a>  CCommonDialog::CCommonDialog

Construit un objet `CCommonDialog`.

```
explicit CCommonDialog(CWnd* pParentWnd);
```

### <a name="parameters"></a>Paramètres

*pParentWnd*<br/>
Pointe vers l’objet de fenêtre parente ou propriétaire (de type [CWnd](../../mfc/reference/cwnd-class.md)) auquel appartient l’objet de la boîte de dialogue. Si sa valeur est NULL, la boîte de dialogue fenêtre l’objet parent est définie dans la fenêtre principale de l’application.

### <a name="remarks"></a>Notes

Consultez [CDialog::CDialog](../../mfc/reference/cdialog-class.md#cdialog) pour obtenir des informations complètes.

## <a name="see-also"></a>Voir aussi

[CDialog, classe](../../mfc/reference/cdialog-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CFileDialog, classe](../../mfc/reference/cfiledialog-class.md)<br/>
[CFontDialog, classe](../../mfc/reference/cfontdialog-class.md)<br/>
[CColorDialog, classe](../../mfc/reference/ccolordialog-class.md)<br/>
[CPageSetupDialog, classe](../../mfc/reference/cpagesetupdialog-class.md)<br/>
[CPrintDialog, classe](../../mfc/reference/cprintdialog-class.md)<br/>
[CFindReplaceDialog, classe](../../mfc/reference/cfindreplacedialog-class.md)<br/>
[COleDialog, classe](../../mfc/reference/coledialog-class.md)
