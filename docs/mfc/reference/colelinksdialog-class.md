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
ms.openlocfilehash: 911108f9a231b752790abfdf86d1b4042d30b149
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69504120"
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
|[COleLinksDialog::DoModal](#domodal)|Affiche la boîte de dialogue OLE modifier les liens.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[COleLinksDialog::m_el](#m_el)|Structure de type OLEUIEDITLINKS qui contrôle le comportement de la boîte de dialogue.|

## <a name="remarks"></a>Notes

Créez un objet de classe `COleLinksDialog` lorsque vous souhaitez appeler cette boîte de dialogue. Une fois `COleLinksDialog` qu’un objet a été construit, vous pouvez utiliser la structure [m_el](#m_el) pour initialiser les valeurs ou les États des contrôles dans la boîte de dialogue. La `m_el` structure est de type OLEUIEDITLINKS. Pour plus d’informations sur l’utilisation de cette classe de boîte de dialogue, consultez la fonction membre [DoModal](#domodal) .

> [!NOTE]
>  Le code de conteneur généré par l’Assistant application utilise cette classe.

Pour plus d’informations, consultez la structure [OLEUIEDITLINKS](/windows/win32/api/oledlg/ns-oledlg-oleuieditlinksw) dans le SDK Windows.

Pour plus d’informations sur les boîtes de dialogue spécifiques à OLE, consultez l’article [boîtes de dialogue dans OLE](../../mfc/dialog-boxes-in-ole.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

[COleDialog](../../mfc/reference/coledialog-class.md)

`COleLinksDialog`

## <a name="requirements"></a>Configuration requise

**En-tête:** afxodlgs. h

##  <a name="domodal"></a>  COleLinksDialog::DoModal

Affiche la boîte de dialogue OLE modifier les liens.

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>Valeur de retour

État d’achèvement de la boîte de dialogue. L’une des valeurs suivantes :

- IDOK si la boîte de dialogue a été correctement affichée.

- IDCANCEL si l’utilisateur a annulé la boîte de dialogue.

- IDABORT si une erreur s’est produite. Si IDABORT est retourné, appelez la `COleDialog::GetLastError` fonction membre pour obtenir plus d’informations sur le type d’erreur qui s’est produit. Pour obtenir la liste des erreurs possibles, consultez la fonction [OleUIEditLinks](/windows/win32/api/oledlg/nf-oledlg-oleuieditlinksw) dans la SDK Windows.

### <a name="remarks"></a>Notes

Si vous souhaitez initialiser les différents contrôles de boîte de dialogue en définissant les membres de la structure [m_el](#m_el) , vous devez le `DoModal`faire avant d’appeler, mais après la construction de l’objet de boîte de dialogue.

##  <a name="colelinksdialog"></a>  COleLinksDialog::COleLinksDialog

Construit un objet `COleLinksDialog`.

```
COleLinksDialog (
    COleDocument* pDoc,
    CView* pView,
    DWORD dwFlags = 0,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>Paramètres

*pDoc*<br/>
Pointe vers le document OLE qui contient les liens à modifier.

*pView*<br/>
Pointe vers la vue actuelle sur *pdoc*.

*dwFlags*<br/>
Indicateur de création, qui contient 0 ou ELF_SHOWHELP pour spécifier si le bouton aide s’affiche lorsque la boîte de dialogue s’affiche.

*pParentWnd*<br/>
Pointe vers l’objet de fenêtre parent ou propriétaire (de `CWnd`type) auquel l’objet de boîte de dialogue appartient. Si la valeur est NULL, la fenêtre parente de la boîte de dialogue est définie sur la fenêtre d’application principale.

### <a name="remarks"></a>Notes

Cette fonction construit uniquement un `COleLinksDialog` objet. Pour afficher la boîte de dialogue, appelez la fonction [DoModal](#domodal) .

##  <a name="m_el"></a>  COleLinksDialog::m_el

Structure de type OLEUIEDITLINKS utilisée pour contrôler le comportement de la boîte de dialogue Modifier les liens.

```
OLEUIEDITLINKS m_el;
```

### <a name="remarks"></a>Notes

Les membres de cette structure peuvent être modifiés soit directement, soit par le biais de fonctions membres.

Pour plus d’informations, consultez la structure [OLEUIEDITLINKS](/windows/win32/api/oledlg/ns-oledlg-oleuieditlinksw) dans le SDK Windows.

## <a name="see-also"></a>Voir aussi

[COleDialog, classe](../../mfc/reference/coledialog-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[COleDialog, classe](../../mfc/reference/coledialog-class.md)
