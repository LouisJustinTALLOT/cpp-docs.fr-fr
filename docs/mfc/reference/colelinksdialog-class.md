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
ms.openlocfilehash: fa32236dfdaef0966dca0e2f131e6adace747f10
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50502961"
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
|[COleLinksDialog::m_el](#m_el)|Une structure de type OLEUIEDITLINKS qui contrôle le comportement de la boîte de dialogue.|

## <a name="remarks"></a>Notes

Créer un objet de classe `COleLinksDialog` lorsque vous souhaitez appeler cette boîte de dialogue. Après un `COleLinksDialog` objet a été construit, vous pouvez utiliser la [m_el](#m_el) structure pour initialiser les valeurs ou les États de contrôles dans la boîte de dialogue. Le `m_el` structure est de type OLEUIEDITLINKS. Pour plus d’informations sur l’utilisation de cette classe de boîte de dialogue, consultez la [DoModal](#domodal) fonction membre.

> [!NOTE]
>  Code généré par l’Assistant de conteneur d’application utilise cette classe.

Pour plus d’informations, consultez le [OLEUIEDITLINKS](/windows/desktop/api/oledlg/ns-oledlg-tagoleuieditlinksa) structure dans le SDK Windows.

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

**En-tête :** afxodlgs.h

##  <a name="domodal"></a>  COleLinksDialog::DoModal

Affiche la boîte de dialogue OLE modifier les liens.

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>Valeur de retour

État d’achèvement de la boîte de dialogue. Une des valeurs suivantes :

- IDOK si la boîte de dialogue a été correctement affichée.

- IDCANCEL, si l’utilisateur a annulé la boîte de dialogue.

- IDABORT si une erreur s’est produite. Si IDABORT est retournée, appelez le `COleDialog::GetLastError` fonction membre pour obtenir plus d’informations sur le type d’erreur qui s’est produite. Pour obtenir la liste des erreurs possibles, consultez le [OleUIEditLinks](/windows/desktop/api/oledlg/nf-oledlg-oleuieditlinksa) (fonction) dans le SDK Windows.

### <a name="remarks"></a>Notes

Si vous souhaitez initialiser les divers contrôles de boîte de dialogue en définissant des membres de la [m_el](#m_el) structure, vous devez le faire avant d’appeler `DoModal`, mais une fois que l’objet de la boîte de dialogue est construit.

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
Pointe vers la vue actuelle sur *pDoc*.

*dwFlags*<br/>
Indicateur de création, qui contient 0 ou ELF_SHOWHELP pour spécifier si le bouton aide s’affichera lorsque la boîte de dialogue s’affiche.

*pParentWnd*<br/>
Pointe vers l’objet de fenêtre parente ou propriétaire (de type `CWnd`) auquel appartient l’objet de la boîte de dialogue. Si sa valeur est NULL, la fenêtre parente de la boîte de dialogue est définie dans la fenêtre principale de l’application.

### <a name="remarks"></a>Notes

Cette fonction construit uniquement un `COleLinksDialog` objet. Pour afficher la boîte de dialogue, appelez le [DoModal](#domodal) (fonction).

##  <a name="m_el"></a>  COleLinksDialog::m_el

Structure de type OLEUIEDITLINKS utilisée pour contrôler le comportement de la boîte de dialogue Modifier les liens.

```
OLEUIEDITLINKS m_el;
```

### <a name="remarks"></a>Notes

Membres de cette structure peuvent être modifiés directement ou via les fonctions membres.

Pour plus d’informations, consultez le [OLEUIEDITLINKS](/windows/desktop/api/oledlg/ns-oledlg-tagoleuieditlinksa) structure dans le SDK Windows.

## <a name="see-also"></a>Voir aussi

[COleDialog, classe](../../mfc/reference/coledialog-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[COleDialog, classe](../../mfc/reference/coledialog-class.md)
