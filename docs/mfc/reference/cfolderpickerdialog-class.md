---
title: Cfolderpickerdialog, classe | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CFolderPickerDialog
- AFXDLGS/CFolderPickerDialog
- AFXDLGS/CFolderPickerDialog::CFolderPickerDialog
dev_langs:
- C++
helpviewer_keywords:
- CFolderPickerDialog [MFC], CFolderPickerDialog
ms.assetid: 8db01684-dd1d-4e9c-989e-07a2318a8156
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1627d11c5c55c62e39092882177ec893cefb89a9
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33366419"
---
# <a name="cfolderpickerdialog-class"></a>CFolderPickerDialog, classe
Cfolderpickerdialog, classe implémente CFileDialog en mode de sélecteur de dossier.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CFolderPickerDialog : public CFileDialog;  
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CFolderPickerDialog :: ~ CFolderPickerDialog](#cfolderpickerdialog__~cfolderpickerdialog)|Destructeur.|  
|[CFolderPickerDialog::CFolderPickerDialog](#cfolderpickerdialog)|Constructeur.|  
  
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
 **En-tête :** afxdlgs.h  
  
##  <a name="cfolderpickerdialog"></a>  CFolderPickerDialog::CFolderPickerDialog  
 Constructeur.  
  
```  
explicit CFolderPickerDialog(
    LPCTSTR lpszFolder = NULL,  
    DWORD dwFlags = 0,  
    CWnd* pParentWnd = NULL,  
    DWORD dwSize = 0);
```  
  
### <a name="parameters"></a>Paramètres  
 `lpszFolder`  
 Dossier initial.  
  
 `dwFlags`  
 Une combinaison d’un ou plusieurs indicateurs qui vous permettent de personnaliser la boîte de dialogue.  
  
 `pParentWnd`  
 Pointeur vers la fenêtre parente ou propriétaire de l’objet de boîte de dialogue.  
  
 `dwSize`  
 La taille de la structure OPENFILENAME.  
  
### <a name="remarks"></a>Notes  
  
##  <a name="_dtorcfolderpickerdialog"></a>  CFolderPickerDialog :: ~ CFolderPickerDialog  
 Destructeur.  
  
```  
virtual ~CFolderPickerDialog();
```  
  
### <a name="remarks"></a>Notes  
  
## <a name="see-also"></a>Voir aussi  
 [Classes](../../mfc/reference/mfc-classes.md)
