---
title: COleChangeIconDialog, classe
ms.date: 11/04/2016
f1_keywords:
- COleChangeIconDialog
- AFXODLGS/COleChangeIconDialog
- AFXODLGS/COleChangeIconDialog::COleChangeIconDialog
- AFXODLGS/COleChangeIconDialog::DoChangeIcon
- AFXODLGS/COleChangeIconDialog::DoModal
- AFXODLGS/COleChangeIconDialog::GetIconicMetafile
- AFXODLGS/COleChangeIconDialog::m_ci
helpviewer_keywords:
- COleChangeIconDialog [MFC], COleChangeIconDialog
- COleChangeIconDialog [MFC], DoChangeIcon
- COleChangeIconDialog [MFC], DoModal
- COleChangeIconDialog [MFC], GetIconicMetafile
- COleChangeIconDialog [MFC], m_ci
ms.assetid: 8d6e131b-ddbb-4dff-a432-f239efda8e3d
ms.openlocfilehash: 6cdc0ed6bfa4765817de8b7628f339db5e7e5bf5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369623"
---
# <a name="colechangeicondialog-class"></a>COleChangeIconDialog, classe

Utilisé pour la boîte de dialogue OLE Changer d'icône.

## <a name="syntax"></a>Syntaxe

```
class COleChangeIconDialog : public COleDialog
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[COleChangeIconDialog::COleChangeIconDialog](#colechangeicondialog)|Construit un objet `COleChangeIconDialog`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[COleChangeIconDialog::DoChangeIcon](#dochangeicon)|Effectue la modification spécifiée dans la boîte de dialogue.|
|[COleChangeIconDialog::DoModal](#domodal)|Affiche la boîte de dialogue OLE 2 Change Icon.|
|[COleChangeIconDialog::GetIconicMetafile](#geticonicmetafile)|Obtient une poignée au metafile associé à la forme iconique de cet article.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[COleChangeIconDialog::m_ci](#m_ci)|Une structure qui contrôle le comportement de la boîte de dialogue.|

## <a name="remarks"></a>Notes

Créez un objet `COleChangeIconDialog` de classe lorsque vous voulez appeler cette boîte de dialogue. Une `COleChangeIconDialog` fois qu’un objet a été construit, vous pouvez utiliser la structure [m_ci](#m_ci) pour initialiser les valeurs ou les états de contrôles dans la boîte de dialogue. La `m_ci` structure est de type OLEUICHANGEICON. Pour plus d’informations sur l’utilisation de cette classe de dialogue, consultez la fonction membre [DoModal.](#domodal)

Pour plus d’informations, consultez la structure [OLECHANGEICON](/windows/win32/api/oledlg/ns-oledlg-oleuichangeiconw) dans le SDK Windows.

Pour plus d’informations sur les boîtes de dialogue spécifiques à l’OLOL, voir l’article [Dialog Boxes in OLE](../../mfc/dialog-boxes-in-ole.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

[COleDialog](../../mfc/reference/coledialog-class.md)

`COleChangeIconDialog`

## <a name="requirements"></a>Spécifications

**En-tête:** afxodlgs.h

## <a name="colechangeicondialogcolechangeicondialog"></a><a name="colechangeicondialog"></a>COleChangeIconDialog::COleChangeIconDialog

Cette fonction ne `COleChangeIconDialog` construit qu’un objet.

```
explicit COleChangeIconDialog(
    COleClientItem* pItem,
    DWORD dwFlags = CIF_SELECTCURRENT,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>Paramètres

*pItem (en)*<br/>
Points à l’élément à convertir.

*dwFlags*<br/>
Indicateur de création, qui contient n’importe quel nombre des valeurs suivantes combinées à l’aide du bitwise-ou de l’opérateur :

- CIF_SELECTCURRENT précise que le bouton radio actuel sera choisi initialement lorsque la boîte de dialogue est appelée. Il s’agit de la valeur par défaut.

- CIF_SELECTDEFAULT précise que le bouton radio par défaut sera choisi initialement lorsque la boîte de dialogue est appelée.

- CIF_SELECTFROMFILE précise que le bouton radio From File sera choisi initialement lorsque la boîte de dialogue est appelée.

- CIF_SHOWHELP précise que le bouton Aide sera affiché lorsque la boîte de dialogue est appelée.

- CIF_USEICONEXE précise que l’icône doit être extraite de l’exécutable spécifié dans le `szIconExe` champ de [m_ci](#m_ci) au lieu d’être extraite du type. Ceci est utile pour l’intégration ou le lien vers des fichiers non-OLE.

*pParentWnd*<br/>
Points à l’objet de fenêtre `CWnd`du parent ou du propriétaire (de type ) auquel appartient l’objet de dialogue. S’il s’agit de NULL, la fenêtre parente de la boîte de dialogue sera réglée sur la fenêtre d’application principale.

### <a name="remarks"></a>Notes

Pour afficher la boîte de dialogue, appelez la fonction [DoModal.](#domodal)

Pour plus d’informations, consultez la structure [OLECHANGEICON](/windows/win32/api/oledlg/ns-oledlg-oleuichangeiconw) dans le SDK Windows.

## <a name="colechangeicondialogdochangeicon"></a><a name="dochangeicon"></a>COleChangeIconDialog::DoChangeIcon

Appelez cette fonction pour changer l’icône représentant l’élément à celle sélectionnée dans la boîte de dialogue après [DoModal](#domodal) retourne IDOK.

```
BOOL DoChangeIcon(COleClientItem* pItem);
```

### <a name="parameters"></a>Paramètres

*pItem (en)*<br/>
Indique l’élément dont l’icône change.

### <a name="return-value"></a>Valeur de retour

Nonzero si le changement est réussi; sinon 0.

## <a name="colechangeicondialogdomodal"></a><a name="domodal"></a>COleChangeIconDialog::DoModal

Appelez cette fonction pour afficher la boîte de dialogue OLE Change Icon.

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>Valeur de retour

État d’achèvement pour la boîte de dialogue. L’une des valeurs suivantes :

- IDOK si la boîte de dialogue a été affichée avec succès.

- IDCANCEL si l’utilisateur a annulé la boîte de dialogue.

- IDABORT en cas d’erreur. Si IDABORT est retourné, appelez la `COleDialog::GetLastError` fonction membre pour obtenir plus d’informations sur le type d’erreur qui s’est produite. Pour une liste d’erreurs possibles, consultez la fonction [OleUIChangeIcon](/windows/win32/api/oledlg/nf-oledlg-oleuichangeiconw) dans le SDK Windows.

### <a name="remarks"></a>Notes

Si vous souhaitez paralyser les différents contrôles de boîte de dialogue en définissant `DoModal`les membres de la structure [m_ci,](#m_ci) vous devriez le faire avant d’appeler, mais après la construction de l’objet de dialogue.

Si `DoModal` vous retournez IDOK, vous pouvez appeler d’autres fonctions de membre pour récupérer les paramètres ou les informations qui ont été saisies par l’utilisateur dans la boîte de dialogue.

## <a name="colechangeicondialoggeticonicmetafile"></a><a name="geticonicmetafile"></a>COleChangeIconDialog::GetIconicMetafile

Appelez cette fonction pour obtenir une poignée au metafile qui contient l’aspect emblématique de l’élément sélectionné.

```
HGLOBAL GetIconicMetafile() const;
```

### <a name="return-value"></a>Valeur de retour

La poignée du metafile contenant l’aspect iconique de la nouvelle icône, si la boîte de dialogue a été rejetée en choisissant **OK**; autrement, l’icône telle qu’elle était avant que le dialogue ne soit affiché.

## <a name="colechangeicondialogm_ci"></a><a name="m_ci"></a>COleChangeIconDialog::m_ci

Structure du type OLEUICHANGEICON utilisé pour contrôler le comportement de la boîte de dialogue Change Icon.

```
OLEUICHANGEICON m_ci;
```

### <a name="remarks"></a>Notes

Les membres de cette structure peuvent être modifiés directement ou par des fonctions de membre.

Pour plus d’informations, consultez la structure [OLECHANGEICON](/windows/win32/api/oledlg/ns-oledlg-oleuichangeiconw) dans le SDK Windows.

## <a name="see-also"></a>Voir aussi

[COleDialog, classe](../../mfc/reference/coledialog-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[COleDialog, classe](../../mfc/reference/coledialog-class.md)
