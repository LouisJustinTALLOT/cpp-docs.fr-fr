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
ms.openlocfilehash: a319dc0612f68c4d513b7d5ab36ecf67a854bda9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50433642"
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
|[COleChangeIconDialog::DoModal](#domodal)|Affiche la boîte de dialogue OLE 2 changer d’icône.|
|[COleChangeIconDialog::GetIconicMetafile](#geticonicmetafile)|Obtient un handle du métafichier associé au formulaire sous forme d’icône de cet élément.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[COleChangeIconDialog::m_ci](#m_ci)|Structure qui contrôle le comportement de la boîte de dialogue.|

## <a name="remarks"></a>Notes

Créer un objet de classe `COleChangeIconDialog` lorsque vous souhaitez appeler cette boîte de dialogue. Après un `COleChangeIconDialog` objet a été construit, vous pouvez utiliser la [m_ci](#m_ci) structure pour initialiser les valeurs ou les États de contrôles dans la boîte de dialogue. Le `m_ci` structure est de type OLEUICHANGEICON. Pour plus d’informations sur l’utilisation de cette classe de boîte de dialogue, consultez la [DoModal](#domodal) fonction membre.

Pour plus d’informations, consultez le [OLEUICHANGEICON](/windows/desktop/api/oledlg/ns-oledlg-tagoleuichangeicona) structure dans le SDK Windows.

Pour plus d’informations sur les boîtes de dialogue spécifiques à OLE, consultez l’article [boîtes de dialogue dans OLE](../../mfc/dialog-boxes-in-ole.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

[COleDialog](../../mfc/reference/coledialog-class.md)

`COleChangeIconDialog`

## <a name="requirements"></a>Configuration requise

**En-tête :** afxodlgs.h

##  <a name="colechangeicondialog"></a>  COleChangeIconDialog::COleChangeIconDialog

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
Indicateur de création, qui contient un nombre quelconque des valeurs suivantes combinées à l’aide de l’opérateur de bits- ou un opérateur :

- CIF_SELECTCURRENT Spécifie que le bouton radio en cours sera sélectionné initialement lorsque la boîte de dialogue est appelée. Il s'agit de la valeur par défaut.

- CIF_SELECTDEFAULT Spécifie que la case d’option par défaut sera sélectionnée initialement lorsque la boîte de dialogue est appelée.

- CIF_SELECTFROMFILE Spécifie que la case d’option à partir du fichier sera sélectionné initialement lorsque la boîte de dialogue est appelée.

- CIF_SHOWHELP Spécifie que le bouton aide s’affichera lorsque la boîte de dialogue est appelée.

- CIF_USEICONEXE Spécifie que l’icône doit être extraites de l’exécutable spécifié dans le `szIconExe` champ [m_ci](#m_ci) au lieu de récupérer à partir du type. Cela est utile pour l’incorporation ou de liaison aux fichiers non OLE.

*pParentWnd*<br/>
Pointe vers l’objet de fenêtre parente ou propriétaire (de type `CWnd`) auquel appartient l’objet de la boîte de dialogue. Si sa valeur est NULL, la fenêtre parente de la boîte de dialogue est fixée à la fenêtre principale de l’application.

### <a name="remarks"></a>Notes

Pour afficher la boîte de dialogue, appelez le [DoModal](#domodal) (fonction).

Pour plus d’informations, consultez le [OLEUICHANGEICON](/windows/desktop/api/oledlg/ns-oledlg-tagoleuichangeicona) structure dans le SDK Windows.

##  <a name="dochangeicon"></a>  COleChangeIconDialog::DoChangeIcon

Appelez cette fonction pour modifier l’icône représentant l’élément à celui sélectionné dans la boîte de dialogue après [DoModal](#domodal) retourne IDOK.

```
BOOL DoChangeIcon(COleClientItem* pItem);
```

### <a name="parameters"></a>Paramètres

*pItem*<br/>
Pointe vers l’élément dont l’icône change.

### <a name="return-value"></a>Valeur de retour

Différent de zéro si la modification a réussi ; sinon 0.

##  <a name="domodal"></a>  COleChangeIconDialog::DoModal

Appelez cette fonction pour afficher la boîte de dialogue OLE changer d’icône.

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>Valeur de retour

État d’achèvement de la boîte de dialogue. Une des valeurs suivantes :

- IDOK si la boîte de dialogue a été correctement affichée.

- IDCANCEL, si l’utilisateur a annulé la boîte de dialogue.

- IDABORT si une erreur s’est produite. Si IDABORT est retournée, appelez le `COleDialog::GetLastError` fonction membre pour obtenir plus d’informations sur le type d’erreur qui s’est produite. Pour obtenir la liste des erreurs possibles, consultez le [OleUIChangeIcon](/windows/desktop/api/oledlg/nf-oledlg-oleuichangeicona) (fonction) dans le SDK Windows.

### <a name="remarks"></a>Notes

Si vous souhaitez initialiser les divers contrôles de boîte de dialogue en définissant des membres de la [m_ci](#m_ci) structure, vous devez le faire avant d’appeler `DoModal`, mais une fois que l’objet de la boîte de dialogue est construit.

Si `DoModal` retourne IDOK, vous pouvez appeler des fonctions pour récupérer les paramètres ou les informations qui a été entrées par l’utilisateur dans la boîte de dialogue autres membres.

##  <a name="geticonicmetafile"></a>  COleChangeIconDialog::GetIconicMetafile

Appelez cette fonction pour obtenir un handle du métafichier qui contient l’aspect sous forme d’icône de l’élément sélectionné.

```
HGLOBAL GetIconicMetafile() const;
```

### <a name="return-value"></a>Valeur de retour

Le handle du métafichier qui contient l’aspect sous forme d’icône de l’icône Nouveau, si la boîte de dialogue a été fermée en choisissant **OK**; sinon, l’icône tel qu’il était avant l’affichage de la boîte de dialogue.

##  <a name="m_ci"></a>  COleChangeIconDialog::m_ci

Structure de type OLEUICHANGEICON utilisée pour contrôler le comportement de la boîte de dialogue Changer d’icône.

```
OLEUICHANGEICON m_ci;
```

### <a name="remarks"></a>Notes

Membres de cette structure peuvent être modifiés directement ou via les fonctions membres.

Pour plus d’informations, consultez le [OLEUICHANGEICON](/windows/desktop/api/oledlg/ns-oledlg-tagoleuichangeicona) structure dans le SDK Windows.

## <a name="see-also"></a>Voir aussi

[COleDialog, classe](../../mfc/reference/coledialog-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[COleDialog, classe](../../mfc/reference/coledialog-class.md)
