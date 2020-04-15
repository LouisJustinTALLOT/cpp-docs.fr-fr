---
title: COleLinksDialog, classe
ms.date: 11/04/2016
f1_keywords:
- COleLinksDialog
- AFXODLGS/COleLinksDialog
- AFXODLGS/COleLinksDialog::COleLinksDialog
- AFXODLGS/COleLinksDialog::DoModal
- AFXODLGS/COleLinksDialog::m_el
helpviewer_keywords:
- COleLinksDialog [MFC], COleLinksDialog
- COleLinksDialog [MFC], DoModal
- COleLinksDialog [MFC], m_el
ms.assetid: fb2eb638-2809-46db-ac74-392a732affc7
ms.openlocfilehash: f120678c822749c8f27c3c56c95fcdd54647aca3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374933"
---
# <a name="colelinksdialog-class"></a>COleLinksDialog, classe

Utilisée pour la boîte de dialogue OLE Modifier les liens.

## <a name="syntax"></a>Syntaxe

```
class COleLinksDialog : public COleDialog
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[COleLinksDialog::COleLinksDialog](#colelinksdialog)|Construit un objet `COleLinksDialog`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[COleLinksDialog::DoModal](#domodal)|Affiche la boîte de dialogue OLE Edit Links.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[COleLinksDialog::m_el](#m_el)|Une structure de type OLEUIEDITLINKS qui contrôle le comportement de la boîte de dialogue.|

## <a name="remarks"></a>Notes

Créez un objet `COleLinksDialog` de classe lorsque vous voulez appeler cette boîte de dialogue. Une `COleLinksDialog` fois qu’un objet a été construit, vous pouvez utiliser la structure [m_el](#m_el) pour initialiser les valeurs ou les états de contrôles dans la boîte de dialogue. La `m_el` structure est de type OLEUIEDITLINKS. Pour plus d’informations sur l’utilisation de cette classe de dialogue, consultez la fonction membre [DoModal.](#domodal)

> [!NOTE]
> Le code de conteneur généré par l’Assistant d’application utilise cette classe.

Pour plus d’informations, consultez la structure [OLEUIEDITLINKS](/windows/win32/api/oledlg/ns-oledlg-oleuieditlinksw) dans le SDK Windows.

Pour plus d’informations sur les boîtes de dialogue spécifiques à l’OLOL, voir l’article [Dialog Boxes in OLE](../../mfc/dialog-boxes-in-ole.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

[COleDialog](../../mfc/reference/coledialog-class.md)

`COleLinksDialog`

## <a name="requirements"></a>Spécifications

**En-tête:** afxodlgs.h

## <a name="colelinksdialogdomodal"></a><a name="domodal"></a>COleLinksDialog::DoModal

Affiche la boîte de dialogue OLE Edit Links.

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>Valeur de retour

État d’achèvement pour la boîte de dialogue. L’une des valeurs suivantes :

- IDOK si la boîte de dialogue a été affichée avec succès.

- IDCANCEL si l’utilisateur a annulé la boîte de dialogue.

- IDABORT en cas d’erreur. Si IDABORT est retourné, appelez la `COleDialog::GetLastError` fonction membre pour obtenir plus d’informations sur le type d’erreur qui s’est produite. Pour une liste d’erreurs possibles, consultez la fonction [OleUIEditLinks](/windows/win32/api/oledlg/nf-oledlg-oleuieditlinksw) dans le SDK Windows.

### <a name="remarks"></a>Notes

Si vous souhaitez paralyser les différents contrôles de boîte de dialogue en définissant `DoModal`les membres de la structure [m_el,](#m_el) vous devriez le faire avant d’appeler, mais après la construction de l’objet de dialogue.

## <a name="colelinksdialogcolelinksdialog"></a><a name="colelinksdialog"></a>COleLinksDialog::COleLinksDialog

Construit un objet `COleLinksDialog`.

```
COleLinksDialog (
    COleDocument* pDoc,
    CView* pView,
    DWORD dwFlags = 0,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>Paramètres

*pDoc (en)*<br/>
Points vers le document OLE qui contient les liens à modifier.

*pView (en)*<br/>
Points à la vue actuelle sur *pDoc*.

*dwFlags*<br/>
Indicateur de création, qui contient 0 ou ELF_SHOWHELP pour spécifier si le bouton Aide sera affiché lorsque la boîte de dialogue est affichée.

*pParentWnd*<br/>
Points à l’objet de fenêtre `CWnd`du parent ou du propriétaire (de type ) auquel appartient l’objet de dialogue. S’il s’agit de NULL, la fenêtre parente de la boîte de dialogue est réglée sur la fenêtre d’application principale.

### <a name="remarks"></a>Notes

Cette fonction ne `COleLinksDialog` construit qu’un objet. Pour afficher la boîte de dialogue, appelez la fonction [DoModal.](#domodal)

## <a name="colelinksdialogm_el"></a><a name="m_el"></a>COleLinksDialog::m_el

Structure du type OLEUIEDITLINKS utilisé pour contrôler le comportement de la boîte de dialogue Edit Links.

```
OLEUIEDITLINKS m_el;
```

### <a name="remarks"></a>Notes

Les membres de cette structure peuvent être modifiés directement ou par des fonctions de membre.

Pour plus d’informations, consultez la structure [OLEUIEDITLINKS](/windows/win32/api/oledlg/ns-oledlg-oleuieditlinksw) dans le SDK Windows.

## <a name="see-also"></a>Voir aussi

[COleDialog, classe](../../mfc/reference/coledialog-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[COleDialog, classe](../../mfc/reference/coledialog-class.md)
