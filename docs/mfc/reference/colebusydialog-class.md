---
description: 'En savoir plus sur : classe COleBusyDialog'
title: COleBusyDialog, classe
ms.date: 11/04/2016
f1_keywords:
- COleBusyDialog
- AFXODLGS/COleBusyDialog
- AFXODLGS/COleBusyDialog::COleBusyDialog
- AFXODLGS/COleBusyDialog::DoModal
- AFXODLGS/COleBusyDialog::GetSelectionType
- AFXODLGS/COleBusyDialog::m_bz
helpviewer_keywords:
- COleBusyDialog [MFC], COleBusyDialog
- COleBusyDialog [MFC], DoModal
- COleBusyDialog [MFC], GetSelectionType
- COleBusyDialog [MFC], m_bz
ms.assetid: c881a532-9672-4c41-b51b-5ce4a7246a6b
ms.openlocfilehash: 7191cf193fccbe0883c8c888f888df94e1f70a23
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97340929"
---
# <a name="colebusydialog-class"></a>COleBusyDialog, classe

Utilisé pour les boîtes de dialogue OLE Le serveur ne répond pas ou Le serveur est occupé.

## <a name="syntax"></a>Syntaxe

```
class COleBusyDialog : public COleDialog
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[COleBusyDialog::COleBusyDialog](#colebusydialog)|Construit un objet `COleBusyDialog`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[COleBusyDialog ::D oModal](#domodal)|Affiche la boîte de dialogue serveur OLE occupé.|
|[COleBusyDialog::GetSelectionType](#getselectiontype)|Détermine le choix effectué dans la boîte de dialogue.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[COleBusyDialog :: m_bz](#m_bz)|Structure de type OLEUIBUSY qui contrôle le comportement de la boîte de dialogue.|

## <a name="remarks"></a>Notes

Créez un objet de classe `COleBusyDialog` lorsque vous souhaitez appeler ces boîtes de dialogue. Une fois qu’un `COleBusyDialog` objet a été construit, vous pouvez utiliser la structure [m_bz](#m_bz) pour initialiser les valeurs ou les États des contrôles dans la boîte de dialogue. La `m_bz` structure est de type OLEUIBUSY. Pour plus d’informations sur l’utilisation de cette classe de boîte de dialogue, consultez la fonction membre [DoModal](#domodal) .

> [!NOTE]
> Le code de conteneur généré par l’Assistant application utilise cette classe.

Pour plus d’informations, consultez la structure [OLEUIBUSY](/windows/win32/api/oledlg/ns-oledlg-oleuibusyw) dans le SDK Windows.

Pour plus d’informations sur les boîtes de dialogue spécifiques à OLE, consultez l’article [boîtes de dialogue dans OLE](../../mfc/dialog-boxes-in-ole.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

[COleDialog](../../mfc/reference/coledialog-class.md)

`COleBusyDialog`

## <a name="requirements"></a>Spécifications

**En-tête :** afxodlgs. h

## <a name="colebusydialogcolebusydialog"></a><a name="colebusydialog"></a> COleBusyDialog::COleBusyDialog

Cette fonction construit uniquement un `COleBusyDialog` objet.

```
explicit COleBusyDialog(
    HTASK htaskBusy,
    BOOL bNotResponding = FALSE,
    DWORD dwFlags = 0,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>Paramètres

*htaskBusy*<br/>
Handle vers la tâche serveur qui est occupée.

*bNotResponding*<br/>
Si la valeur est TRUE, appelez la boîte de dialogue qui ne répond pas à la place de la boîte de dialogue serveur occupé. La formulation de la boîte de dialogue ne pas répondre est légèrement différente de celle de la boîte de dialogue serveur occupé et le bouton Annuler est désactivé.

*dwFlags*<br/>
Indicateur de création. Peut contenir zéro, une ou plusieurs des valeurs suivantes, combinées avec l’opérateur or au niveau du bit :

- BZ_DISABLECANCELBUTTON désactiver le bouton Annuler lors de l’appel de la boîte de dialogue.

- BZ_DISABLESWITCHTOBUTTON désactiver le bouton Basculer vers lorsque vous appelez la boîte de dialogue.

- BZ_DISABLERETRYBUTTON désactiver le bouton Réessayer lors de l’appel de la boîte de dialogue.

*pParentWnd*<br/>
Pointe vers l’objet de fenêtre parent ou propriétaire (de type `CWnd` ) auquel l’objet de boîte de dialogue appartient. Si la valeur est NULL, la fenêtre parente de l’objet Dialog est définie sur la fenêtre d’application principale.

### <a name="remarks"></a>Notes

Pour afficher la boîte de dialogue, appelez [DoModal](#domodal).

Pour plus d’informations, consultez la structure [OLEUIBUSY](/windows/win32/api/oledlg/ns-oledlg-oleuibusyw) dans le SDK Windows.

## <a name="colebusydialogdomodal"></a><a name="domodal"></a> COleBusyDialog ::D oModal

Appelez cette fonction pour afficher la boîte de dialogue le serveur OLE occupé ou le serveur ne répond pas.

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>Valeur renvoyée

État d’achèvement de la boîte de dialogue. Une des valeurs suivantes :

- IDOK si la boîte de dialogue a été correctement affichée.

- IDCANCEL si l’utilisateur a annulé la boîte de dialogue.

- IDABORT si une erreur s’est produite. Si IDABORT est retourné, appelez la `COleDialog::GetLastError` fonction membre pour obtenir plus d’informations sur le type d’erreur qui s’est produit. Pour obtenir la liste des erreurs possibles, consultez la fonction [OleUIBusy](/windows/win32/api/oledlg/nf-oledlg-oleuibusyw) dans la SDK Windows.

### <a name="remarks"></a>Notes

Si vous souhaitez initialiser les différents contrôles de boîte de dialogue en définissant les membres de la structure [m_bz](#m_bz) , vous devez le faire avant d’appeler `DoModal` , mais après la construction de l’objet de boîte de dialogue.

Si `DoModal` retourne IDOK, vous pouvez appeler d’autres fonctions membres pour récupérer les paramètres ou les informations qui ont été entrés par l’utilisateur dans la boîte de dialogue.

## <a name="colebusydialoggetselectiontype"></a><a name="getselectiontype"></a> COleBusyDialog::GetSelectionType

Appelez cette fonction pour récupérer le type de sélection choisi par l’utilisateur dans la boîte de dialogue serveur occupé.

```
UINT GetSelectionType() const;
```

### <a name="return-value"></a>Valeur renvoyée

Type de sélection effectuée.

### <a name="remarks"></a>Notes

Les valeurs de type de retour sont spécifiées par le `Selection` type d’énumération déclaré dans la `COleBusyDialog` classe.

```
enum Selection {
    switchTo,
    retry,
    callUnblocked
    };
```

Des descriptions succinctes de ces valeurs sont les suivantes :

- `COleBusyDialog::switchTo` L’utilisateur a cliqué sur le bouton bascule.

- `COleBusyDialog::retry` L’utilisateur a cliqué sur le bouton Réessayer.

- `COleBusyDialog::callUnblocked` L’appel pour activer le serveur est maintenant débloqué.

## <a name="colebusydialogm_bz"></a><a name="m_bz"></a> COleBusyDialog :: m_bz

Structure de type OLEUIBUSY utilisée pour contrôler le comportement de la boîte de dialogue serveur occupé.

```
OLEUIBUSY m_bz;
```

### <a name="remarks"></a>Notes

Les membres de cette structure peuvent être modifiés directement ou via des fonctions membres.

Pour plus d’informations, consultez la structure [OLEUIBUSY](/windows/win32/api/oledlg/ns-oledlg-oleuibusyw) dans le SDK Windows.

## <a name="see-also"></a>Voir aussi

[COleDialog, classe](../../mfc/reference/coledialog-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[COleDialog, classe](../../mfc/reference/coledialog-class.md)
