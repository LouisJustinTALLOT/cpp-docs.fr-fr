---
title: COleUpdateDialog, classe
ms.date: 11/04/2016
f1_keywords:
- COleUpdateDialog
- AFXODLGS/COleUpdateDialog
- AFXODLGS/COleUpdateDialog::COleUpdateDialog
- AFXODLGS/COleUpdateDialog::DoModal
helpviewer_keywords:
- COleUpdateDialog [MFC], COleUpdateDialog
- COleUpdateDialog [MFC], DoModal
ms.assetid: 699ca980-52b1-4cf8-9ab1-ac6767ad5b0e
ms.openlocfilehash: 9e2c7a8d79ebf5e6483a06354b280e474d7b8e61
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374836"
---
# <a name="coleupdatedialog-class"></a>COleUpdateDialog, classe

Utilisée pour un cas particulier de la boîte de dialogue OLE Modifier les liens, qui doit être utilisée lorsque vous devez mettre à jour uniquement les objets liés ou incorporés d'un document.

## <a name="syntax"></a>Syntaxe

```
class COleUpdateDialog : public COleLinksDialog
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[COleUpdateDialog::COleUpdateDialog](#coleupdatedialog)|Construit un objet `COleUpdateDialog`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[COleUpdateDialog::DoModal](#domodal)|Affiche la boîte de dialogue **Edit Links** dans un mode de mise à jour.|

## <a name="remarks"></a>Notes

Pour plus d’informations sur les boîtes de dialogue spécifiques à l’OLOL, voir l’article [Dialog Boxes in OLE](../../mfc/dialog-boxes-in-ole.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

[COleDialog](../../mfc/reference/coledialog-class.md)

[COleLinksDialog](../../mfc/reference/colelinksdialog-class.md)

`COleUpdateDialog`

## <a name="requirements"></a>Spécifications

**En-tête:** afxodlgs.h

## <a name="coleupdatedialogcoleupdatedialog"></a><a name="coleupdatedialog"></a>COleUpdateDialog::COleUpdateDialog

Construit un objet `COleUpdateDialog`.

```
explicit COleUpdateDialog(
    COleDocument* pDoc,
    BOOL bUpdateLinks = TRUE,
    BOOL bUpdateEmbeddings = FALSE,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>Paramètres

*pDoc (en)*<br/>
Points au document contenant les liens qui peuvent avoir besoin d’être mis à jour.

*bUpdateLinks (en)*<br/>
Indicateur qui détermine si les objets liés doivent être mis à jour.

*bUpdateEmbeddings*<br/>
Indicateur qui détermine si les objets embarqués doivent être mis à jour.

*pParentWnd*<br/>
Points à l’objet de fenêtre `CWnd`du parent ou du propriétaire (de type ) auquel appartient l’objet de dialogue. S’il s’agit de NULL, la fenêtre parente de la boîte de dialogue sera réglée sur la fenêtre d’application principale.

### <a name="remarks"></a>Notes

Cette fonction ne `COleUpdateDialog` construit qu’un objet. Pour afficher la boîte de dialogue, appelez [DoModal](../../mfc/reference/colelinksdialog-class.md#domodal). Cette classe doit être `COleLinksDialog` utilisée au lieu de savoir lorsque vous souhaitez mettre à jour uniquement les éléments liés ou intégrés existants.

## <a name="coleupdatedialogdomodal"></a><a name="domodal"></a>COleUpdateDialog::DoModal

Affiche la boîte de dialogue Edit Links en mode mise à jour.

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>Valeur de retour

État d’achèvement pour la boîte de dialogue. L’une des valeurs suivantes :

- IDOK si la boîte de dialogue est retournée avec succès.

- IDCANCEL si aucun des éléments liés ou intégrés dans le document actuel n’a besoin d’être mis à jour.

- IDABORT en cas d’erreur. Si IDABORT est retourné, appelez le [COleDialog: :GetLastError](../../mfc/reference/coledialog-class.md#getlasterror) fonction membre pour obtenir plus d’informations sur le type d’erreur qui s’est produite. Pour une liste d’erreurs possibles, consultez la fonction [OleUIEditLinks](/windows/win32/api/oledlg/nf-oledlg-oleuieditlinksw) dans le SDK Windows.

### <a name="remarks"></a>Notes

Tous les liens et/ou embeddings sont mis à jour à moins que l’utilisateur ne sélectionne le bouton Annuler.

## <a name="see-also"></a>Voir aussi

[Échantillon MFC OCLIENT](../../overview/visual-cpp-samples.md)<br/>
[COleLinksDialog, classe](../../mfc/reference/colelinksdialog-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[COleLinksDialog, classe](../../mfc/reference/colelinksdialog-class.md)
