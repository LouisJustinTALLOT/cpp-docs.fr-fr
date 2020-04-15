---
title: Classe CCommonDialog
ms.date: 11/04/2016
f1_keywords:
- CCommonDialog
- AFXDLGS/CCommonDialog
- AFXDLGS/CCommonDialog::CCommonDialog
helpviewer_keywords:
- CCommonDialog [MFC], CCommonDialog
ms.assetid: 1f68d65f-a0fd-4778-be22-ebbe51a95f95
ms.openlocfilehash: 853a4756df3b70f4f33deb7159b4d1aee610092c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369444"
---
# <a name="ccommondialog-class"></a>Classe CCommonDialog

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

Les classes suivantes résument la fonctionnalité des dialogues communs Windows :

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

**En-tête:** afxdlgs.h

## <a name="ccommondialogccommondialog"></a><a name="ccommondialog"></a>CCommonDialog::CCommonDialog

Construit un objet `CCommonDialog`.

```
explicit CCommonDialog(CWnd* pParentWnd);
```

### <a name="parameters"></a>Paramètres

*pParentWnd*<br/>
Points à l’objet de fenêtre du parent ou du propriétaire (de type [CWnd](../../mfc/reference/cwnd-class.md)) auquel appartient l’objet de dialogue. S’il s’agit de NULL, la fenêtre parente de l’objet de dialogue est réglée sur la fenêtre d’application principale.

### <a name="remarks"></a>Notes

Voir [CDialog::CDialog](../../mfc/reference/cdialog-class.md#cdialog) pour des informations complètes.

## <a name="see-also"></a>Voir aussi

[Classe CDialog](../../mfc/reference/cdialog-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CFileDialog, classe](../../mfc/reference/cfiledialog-class.md)<br/>
[Classe CFontDialog](../../mfc/reference/cfontdialog-class.md)<br/>
[CColorDialog, classe](../../mfc/reference/ccolordialog-class.md)<br/>
[Classe CPageSetupDialog](../../mfc/reference/cpagesetupdialog-class.md)<br/>
[CPrintDialog, classe](../../mfc/reference/cprintdialog-class.md)<br/>
[Classe CFindReplaceDialog](../../mfc/reference/cfindreplacedialog-class.md)<br/>
[COleDialog, classe](../../mfc/reference/coledialog-class.md)
