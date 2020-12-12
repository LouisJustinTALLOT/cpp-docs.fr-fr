---
description: 'En savoir plus sur : classe COleChangeIconDialog'
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
ms.openlocfilehash: 5ec6113bbcf63462380f18c4ac52abbb8706c8d5
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97209956"
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
|[COleChangeIconDialog ::D oChangeIcon](#dochangeicon)|Effectue la modification spécifiée dans la boîte de dialogue.|
|[COleChangeIconDialog ::D oModal](#domodal)|Affiche la boîte de dialogue Modifier l’icône OLE 2.|
|[COleChangeIconDialog::GetIconicMetafile](#geticonicmetafile)|Obtient un handle vers le métafichier associé au formulaire sous forme de cet élément.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[COleChangeIconDialog :: m_ci](#m_ci)|Structure qui contrôle le comportement de la boîte de dialogue.|

## <a name="remarks"></a>Notes

Créez un objet de classe `COleChangeIconDialog` lorsque vous souhaitez appeler cette boîte de dialogue. Une fois qu’un `COleChangeIconDialog` objet a été construit, vous pouvez utiliser la structure [m_ci](#m_ci) pour initialiser les valeurs ou les États des contrôles dans la boîte de dialogue. La `m_ci` structure est de type OLEUICHANGEICON. Pour plus d’informations sur l’utilisation de cette classe de boîte de dialogue, consultez la fonction membre [DoModal](#domodal) .

Pour plus d’informations, consultez la structure [OLEUICHANGEICON](/windows/win32/api/oledlg/ns-oledlg-oleuichangeiconw) dans le SDK Windows.

Pour plus d’informations sur les boîtes de dialogue spécifiques à OLE, consultez l’article [boîtes de dialogue dans OLE](../../mfc/dialog-boxes-in-ole.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

[COleDialog](../../mfc/reference/coledialog-class.md)

`COleChangeIconDialog`

## <a name="requirements"></a>Spécifications

**En-tête :** afxodlgs. h

## <a name="colechangeicondialogcolechangeicondialog"></a><a name="colechangeicondialog"></a> COleChangeIconDialog::COleChangeIconDialog

Cette fonction construit uniquement un `COleChangeIconDialog` objet.

```
explicit COleChangeIconDialog(
    COleClientItem* pItem,
    DWORD dwFlags = CIF_SELECTCURRENT,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>Paramètres

*pItem*<br/>
Pointe vers l’élément à convertir.

*dwFlags*<br/>
Indicateur de création, qui contient un nombre quelconque de valeurs suivantes combinées à l’aide de l’opérateur or au niveau du bit :

- CIF_SELECTCURRENT spécifie que la case d’option en cours sera sélectionnée initialement lorsque la boîte de dialogue est appelée. Il s’agit de la valeur par défaut.

- CIF_SELECTDEFAULT spécifie que la case d’option par défaut sera sélectionnée initialement lorsque la boîte de dialogue est appelée.

- CIF_SELECTFROMFILE spécifie que la case d’option à partir du fichier est sélectionnée initialement lorsque la boîte de dialogue est appelée.

- CIF_SHOWHELP spécifie que le bouton aide s’affiche lorsque la boîte de dialogue est appelée.

- CIF_USEICONEXE spécifie que l’icône doit être extraite de l’exécutable spécifié dans le `szIconExe` champ de [m_ci](#m_ci) au lieu de récupéré du type. Cela est utile pour l’incorporation ou la liaison à des fichiers non-OLE.

*pParentWnd*<br/>
Pointe vers l’objet de fenêtre parent ou propriétaire (de type `CWnd` ) auquel l’objet de boîte de dialogue appartient. Si la valeur est NULL, la fenêtre parente de la boîte de dialogue est définie sur la fenêtre d’application principale.

### <a name="remarks"></a>Notes

Pour afficher la boîte de dialogue, appelez la fonction [DoModal](#domodal) .

Pour plus d’informations, consultez la structure [OLEUICHANGEICON](/windows/win32/api/oledlg/ns-oledlg-oleuichangeiconw) dans le SDK Windows.

## <a name="colechangeicondialogdochangeicon"></a><a name="dochangeicon"></a> COleChangeIconDialog ::D oChangeIcon

Appelez cette fonction pour remplacer l’icône représentant l’élément par celle sélectionnée dans la boîte de dialogue une fois que [DoModal](#domodal) a retourné IDOK.

```
BOOL DoChangeIcon(COleClientItem* pItem);
```

### <a name="parameters"></a>Paramètres

*pItem*<br/>
Pointe vers l’élément dont l’icône change.

### <a name="return-value"></a>Valeur renvoyée

Différent de zéro si la modification est réussie ; Sinon, 0.

## <a name="colechangeicondialogdomodal"></a><a name="domodal"></a> COleChangeIconDialog ::D oModal

Appelez cette fonction pour afficher la boîte de dialogue OLE changer d’icône.

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>Valeur renvoyée

État d’achèvement de la boîte de dialogue. Une des valeurs suivantes :

- IDOK si la boîte de dialogue a été correctement affichée.

- IDCANCEL si l’utilisateur a annulé la boîte de dialogue.

- IDABORT si une erreur s’est produite. Si IDABORT est retourné, appelez la `COleDialog::GetLastError` fonction membre pour obtenir plus d’informations sur le type d’erreur qui s’est produit. Pour obtenir la liste des erreurs possibles, consultez la fonction [OleUIChangeIcon](/windows/win32/api/oledlg/nf-oledlg-oleuichangeiconw) dans la SDK Windows.

### <a name="remarks"></a>Notes

Si vous souhaitez initialiser les différents contrôles de boîte de dialogue en définissant les membres de la structure [m_ci](#m_ci) , vous devez le faire avant d’appeler `DoModal` , mais après la construction de l’objet de boîte de dialogue.

Si `DoModal` retourne IDOK, vous pouvez appeler d’autres fonctions membres pour récupérer les paramètres ou les informations qui ont été entrés par l’utilisateur dans la boîte de dialogue.

## <a name="colechangeicondialoggeticonicmetafile"></a><a name="geticonicmetafile"></a> COleChangeIconDialog::GetIconicMetafile

Appelez cette fonction pour obtenir un handle vers le métafichier qui contient l’aspect sous forme de l’élément sélectionné.

```
HGLOBAL GetIconicMetafile() const;
```

### <a name="return-value"></a>Valeur renvoyée

Handle du métafichier contenant l’aspect sous forme de la nouvelle icône, si la boîte de dialogue a été fermée en choisissant **OK**. Sinon, l’icône telle qu’elle était avant l’affichage de la boîte de dialogue.

## <a name="colechangeicondialogm_ci"></a><a name="m_ci"></a> COleChangeIconDialog :: m_ci

Structure de type OLEUICHANGEICON utilisée pour contrôler le comportement de la boîte de dialogue changer d’icône.

```
OLEUICHANGEICON m_ci;
```

### <a name="remarks"></a>Notes

Les membres de cette structure peuvent être modifiés soit directement, soit par le biais de fonctions membres.

Pour plus d’informations, consultez la structure [OLEUICHANGEICON](/windows/win32/api/oledlg/ns-oledlg-oleuichangeiconw) dans le SDK Windows.

## <a name="see-also"></a>Voir aussi

[COleDialog, classe](../../mfc/reference/coledialog-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[COleDialog, classe](../../mfc/reference/coledialog-class.md)
