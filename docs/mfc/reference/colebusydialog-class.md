---
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
ms.openlocfilehash: 5be42463c08cacd83de84900fb4d98771774e897
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364242"
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
|[COleBusyDialog::DoModal](#domodal)|Affiche la boîte de dialogue OLE Server Busy.|
|[COleBusyDialog::GetSelectionType](#getselectiontype)|Détermine le choix fait dans la boîte de dialogue.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[COleBusyDialog::m_bz](#m_bz)|Structure du type OLEUIBUSY qui contrôle le comportement de la boîte de dialogue.|

## <a name="remarks"></a>Notes

Créez un objet `COleBusyDialog` de classe lorsque vous voulez appeler ces boîtes de dialogue. Une `COleBusyDialog` fois qu’un objet a été construit, vous pouvez utiliser la structure [m_bz](#m_bz) pour initialiser les valeurs ou les états de contrôles dans la boîte de dialogue. La `m_bz` structure est de type OLEUIBUSY. Pour plus d’informations sur l’utilisation de cette classe de dialogue, consultez la fonction membre [DoModal.](#domodal)

> [!NOTE]
> Le code de conteneur généré par l’Assistant d’application utilise cette classe.

Pour plus d’informations, voir la structure [OLEUIBUSY](/windows/win32/api/oledlg/ns-oledlg-oleuibusyw) dans le SDK Windows.

Pour plus d’informations sur les boîtes de dialogue spécifiques à l’OLOL, voir l’article [Dialog Boxes in OLE](../../mfc/dialog-boxes-in-ole.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

[COleDialog](../../mfc/reference/coledialog-class.md)

`COleBusyDialog`

## <a name="requirements"></a>Spécifications

**En-tête:** afxodlgs.h

## <a name="colebusydialogcolebusydialog"></a><a name="colebusydialog"></a>COleBusyDialog::COleBusyDialog

Cette fonction ne `COleBusyDialog` construit qu’un objet.

```
explicit COleBusyDialog(
    HTASK htaskBusy,
    BOOL bNotResponding = FALSE,
    DWORD dwFlags = 0,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>Paramètres

*htaskBusy htaskBusy*<br/>
Gérer à la tâche du serveur qui est occupé.

*bNotResponding*<br/>
Si VRAI, appelez la boîte de dialogue Non-Réponse au lieu de la boîte de dialogue Server Busy. Le libellé de la boîte de dialogue Non-Réponse est légèrement différent du libellé de la boîte de dialogue Server Busy, et le bouton Annuler est désactivé.

*dwFlags*<br/>
Drapeau de création. Peut contenir zéro ou plus des valeurs suivantes combinées avec l’opérateur bitwise-OR :

- BZ_DISABLECANCELBUTTON désactiver le bouton Annuler lorsque vous appelez la boîte de dialogue.

- BZ_DISABLESWITCHTOBUTTON désactiver le bouton Switch To lors de l’appel de la boîte de dialogue.

- BZ_DISABLERETRYBUTTON désactiver le bouton Retry lorsque vous appelez la boîte de dialogue.

*pParentWnd*<br/>
Points à l’objet de fenêtre `CWnd`du parent ou du propriétaire (de type ) auquel appartient l’objet de dialogue. S’il s’agit de NULL, la fenêtre parente de l’objet de dialogue est réglée sur la fenêtre d’application principale.

### <a name="remarks"></a>Notes

Pour afficher la boîte de dialogue, appelez [DoModal](#domodal).

Pour plus d’informations, voir la structure [OLEUIBUSY](/windows/win32/api/oledlg/ns-oledlg-oleuibusyw) dans le SDK Windows.

## <a name="colebusydialogdomodal"></a><a name="domodal"></a>COleBusyDialog::DoModal

Appelez cette fonction pour afficher la boîte de dialogue OLE Server Busy ou Server Not Responding.

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>Valeur de retour

État d’achèvement pour la boîte de dialogue. L’une des valeurs suivantes :

- IDOK si la boîte de dialogue a été affichée avec succès.

- IDCANCEL si l’utilisateur a annulé la boîte de dialogue.

- IDABORT en cas d’erreur. Si IDABORT est retourné, appelez la `COleDialog::GetLastError` fonction membre pour obtenir plus d’informations sur le type d’erreur qui s’est produite. Pour une liste d’erreurs possibles, consultez la fonction [OleUIBusy](/windows/win32/api/oledlg/nf-oledlg-oleuibusyw) dans le SDK Windows.

### <a name="remarks"></a>Notes

Si vous souhaitez paralyser les différents contrôles de boîte de dialogue en définissant les membres de la structure [m_bz,](#m_bz) vous devez le faire avant d’appeler, `DoModal`mais après la construction de l’objet de dialogue.

Si `DoModal` vous retournez IDOK, vous pouvez appeler d’autres fonctions de membre pour récupérer les paramètres ou les informations qui ont été saisies par l’utilisateur dans la boîte de dialogue.

## <a name="colebusydialoggetselectiontype"></a><a name="getselectiontype"></a>COleBusyDialog::GetSelectionType

Appelez cette fonction pour obtenir le type de sélection choisi par l’utilisateur dans la boîte de dialogue Server Busy.

```
UINT GetSelectionType() const;
```

### <a name="return-value"></a>Valeur de retour

Type de sélection faite.

### <a name="remarks"></a>Notes

Les valeurs de type `Selection` retour sont spécifiées `COleBusyDialog` par le type d’énumération déclaré dans la classe.

```
enum Selection {
    switchTo,
    retry,
    callUnblocked
    };
```

Voici de brèves descriptions de ces valeurs :

- `COleBusyDialog::switchTo`Le bouton Switch To a été appuyé.

- `COleBusyDialog::retry`Le bouton Retry a été appuyé.

- `COleBusyDialog::callUnblocked`L’appel pour activer le serveur est maintenant débloqué.

## <a name="colebusydialogm_bz"></a><a name="m_bz"></a>COleBusyDialog::m_bz

Structure du type OLEUIBUSY utilisé pour contrôler le comportement de la boîte de dialogue Server Busy.

```
OLEUIBUSY m_bz;
```

### <a name="remarks"></a>Notes

Les membres de cette structure peuvent être modifiés directement ou par des fonctions de membre.

Pour plus d’informations, voir la structure [OLEUIBUSY](/windows/win32/api/oledlg/ns-oledlg-oleuibusyw) dans le SDK Windows.

## <a name="see-also"></a>Voir aussi

[COleDialog, classe](../../mfc/reference/coledialog-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[COleDialog, classe](../../mfc/reference/coledialog-class.md)
