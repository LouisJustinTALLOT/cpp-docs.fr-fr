---
description: 'En savoir plus sur : classe Cfolderpickerdialog,'
title: CFolderPickerDialog, classe
ms.date: 03/27/2019
f1_keywords:
- CFolderPickerDialog
- AFXDLGS/CFolderPickerDialog
- AFXDLGS/CFolderPickerDialog::CFolderPickerDialog
helpviewer_keywords:
- CFolderPickerDialog [MFC], CFolderPickerDialog
ms.assetid: 8db01684-dd1d-4e9c-989e-07a2318a8156
ms.openlocfilehash: f4a5bcc3162a5fffcc723d7ec420685b02be10f0
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97184424"
---
# <a name="cfolderpickerdialog-class"></a>CFolderPickerDialog, classe

La classe Cfolderpickerdialog, implémente CFileDialog en mode de sélecteur de dossiers.

## <a name="syntax"></a>Syntaxe

```
class CFolderPickerDialog : public CFileDialog;
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[Cfolderpickerdialog, :: ~ Cfolderpickerdialog,](#_dtorcfolderpickerdialog)|Destructeur.|
|[Cfolderpickerdialog, :: Cfolderpickerdialog,](#cfolderpickerdialog)|Constructeur.|

## <a name="remarks"></a>Notes

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

[CFileDialog](../../mfc/reference/cfiledialog-class.md)

`CFolderPickerDialog`

## <a name="requirements"></a>Spécifications

**En-tête :** afxdlgs. h

## <a name="cfolderpickerdialogcfolderpickerdialog"></a><a name="cfolderpickerdialog"></a> Cfolderpickerdialog, :: Cfolderpickerdialog,

Constructeur.

```
explicit CFolderPickerDialog(
    LPCTSTR lpszFolder = NULL,
    DWORD dwFlags = 0,
    CWnd* pParentWnd = NULL,
    DWORD dwSize = 0);
```

### <a name="parameters"></a>Paramètres

*lpszFolder*<br/>
Dossier initial.

*dwFlags*<br/>
Combinaison d’un ou de plusieurs indicateurs qui vous permettent de personnaliser la boîte de dialogue.

*pParentWnd*<br/>
Pointeur vers la fenêtre parente ou propriétaire de l’objet de boîte de dialogue.

*dwSize nul*<br/>
Taille de la structure OPENFILENAME.

### <a name="remarks"></a>Notes

## <a name="cfolderpickerdialogcfolderpickerdialog"></a><a name="_dtorcfolderpickerdialog"></a> Cfolderpickerdialog, :: ~ Cfolderpickerdialog,

Destructeur.

```
virtual ~CFolderPickerDialog();
```

### <a name="remarks"></a>Notes

## <a name="see-also"></a>Voir aussi

[Classes](../../mfc/reference/mfc-classes.md)
