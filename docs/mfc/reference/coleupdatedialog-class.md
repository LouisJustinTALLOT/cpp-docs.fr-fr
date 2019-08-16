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
ms.openlocfilehash: 150e78b7880a61343db21c3c787ffdd1f0b734a5
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69503168"
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
|[COleUpdateDialog::DoModal](#domodal)|Affiche la boîte de dialogue **modifier les liens** dans un mode de mise à jour.|

## <a name="remarks"></a>Notes

Pour plus d’informations sur les boîtes de dialogue spécifiques à OLE, consultez l’article [boîtes de dialogue dans OLE](../../mfc/dialog-boxes-in-ole.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

[COleDialog](../../mfc/reference/coledialog-class.md)

[COleLinksDialog](../../mfc/reference/colelinksdialog-class.md)

`COleUpdateDialog`

## <a name="requirements"></a>Configuration requise

**En-tête:** afxodlgs. h

##  <a name="coleupdatedialog"></a>  COleUpdateDialog::COleUpdateDialog

Construit un objet `COleUpdateDialog`.

```
explicit COleUpdateDialog(
    COleDocument* pDoc,
    BOOL bUpdateLinks = TRUE,
    BOOL bUpdateEmbeddings = FALSE,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>Paramètres

*pDoc*<br/>
Pointe vers le document contenant les liens qui peuvent nécessiter une mise à jour.

*bUpdateLinks*<br/>
Indicateur qui détermine si les objets liés doivent être mis à jour.

*bUpdateEmbeddings*<br/>
Indicateur qui détermine si les objets incorporés doivent être mis à jour.

*pParentWnd*<br/>
Pointe vers l’objet de fenêtre parent ou propriétaire (de `CWnd`type) auquel l’objet de boîte de dialogue appartient. Si la valeur est NULL, la fenêtre parente de la boîte de dialogue est définie sur la fenêtre d’application principale.

### <a name="remarks"></a>Notes

Cette fonction construit uniquement un `COleUpdateDialog` objet. Pour afficher la boîte de dialogue, appelez [DoModal](../../mfc/reference/colelinksdialog-class.md#domodal). Cette classe doit être utilisée au lieu `COleLinksDialog` de lorsque vous souhaitez mettre à jour uniquement les éléments liés ou incorporés existants.

##  <a name="domodal"></a>  COleUpdateDialog::DoModal

Affiche la boîte de dialogue Modifier les liens en mode mise à jour.

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>Valeur de retour

État d’achèvement de la boîte de dialogue. L’une des valeurs suivantes :

- IDOK si la boîte de dialogue a été retournée avec succès.

- IDCANCEL si aucun des éléments liés ou incorporés dans le document actif n’a besoin d’être mis à jour.

- IDABORT si une erreur s’est produite. Si IDABORT est retourné, appelez la fonction membre [COleDialog:: GetLastError](../../mfc/reference/coledialog-class.md#getlasterror) pour obtenir plus d’informations sur le type d’erreur qui s’est produit. Pour obtenir la liste des erreurs possibles, consultez la fonction [OleUIEditLinks](/windows/win32/api/oledlg/nf-oledlg-oleuieditlinksw) dans la SDK Windows.

### <a name="remarks"></a>Notes

Tous les liens et/ou les incorporations sont mis à jour, sauf si l’utilisateur sélectionne le bouton Annuler.

## <a name="see-also"></a>Voir aussi

[Exemple MFC OCLIENT](../../overview/visual-cpp-samples.md)<br/>
[COleLinksDialog, classe](../../mfc/reference/colelinksdialog-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[COleLinksDialog, classe](../../mfc/reference/colelinksdialog-class.md)
