---
title: COleChangeSourceDialog, classe
ms.date: 11/04/2016
f1_keywords:
- COleChangeSourceDialog
- AFXODLGS/COleChangeSourceDialog
- AFXODLGS/COleChangeSourceDialog::COleChangeSourceDialog
- AFXODLGS/COleChangeSourceDialog::DoModal
- AFXODLGS/COleChangeSourceDialog::GetDisplayName
- AFXODLGS/COleChangeSourceDialog::GetFileName
- AFXODLGS/COleChangeSourceDialog::GetFromPrefix
- AFXODLGS/COleChangeSourceDialog::GetItemName
- AFXODLGS/COleChangeSourceDialog::GetToPrefix
- AFXODLGS/COleChangeSourceDialog::IsValidSource
- AFXODLGS/COleChangeSourceDialog::m_cs
helpviewer_keywords:
- COleChangeSourceDialog [MFC], COleChangeSourceDialog
- COleChangeSourceDialog [MFC], DoModal
- COleChangeSourceDialog [MFC], GetDisplayName
- COleChangeSourceDialog [MFC], GetFileName
- COleChangeSourceDialog [MFC], GetFromPrefix
- COleChangeSourceDialog [MFC], GetItemName
- COleChangeSourceDialog [MFC], GetToPrefix
- COleChangeSourceDialog [MFC], IsValidSource
- COleChangeSourceDialog [MFC], m_cs
ms.assetid: d0e08be7-21ef-45e1-97af-fe27d99e3bac
ms.openlocfilehash: 78da0a495de6ea951deab984550756a2d6f3e2bd
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81321871"
---
# <a name="colechangesourcedialog-class"></a>COleChangeSourceDialog, classe

Utilisé pour la boîte de dialogue OLE Changer de source.

## <a name="syntax"></a>Syntaxe

```
class COleChangeSourceDialog : public COleDialog
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[COleChangeSourceDialog::COleChangeSourceDialog](#colechangesourcedialog)|Construit un objet `COleChangeSourceDialog`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[COleChangeSourceDialog::DoModal](#domodal)|Affiche la boîte de dialogue OLE Change Source.|
|[COleChangeSourceDialog::GetDisplayName](#getdisplayname)|Obtient le nom d’affichage source complète.|
|[COleChangeSourceDialog::GetFileName](#getfilename)|Obtient le nom de fichier à partir du nom de source.|
|[COleChangeSourceDialog::GetFromPrefix](#getfromprefix)|Obtient le préfixe de la source précédente.|
|[COleChangeSourceDialog::GetItemName](#getitemname)|Obtient le nom de l’élément à partir du nom de source.|
|[COleChangeSourceDialog::GetToPrefix](#gettoprefix)|Obtient le préfixe de la nouvelle source|
|[COleChangeSourceDialog::IsValidSource](#isvalidsource)|Indique si la source est valide.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[COleChangeSourceDialog::m_cs](#m_cs)|Une structure qui contrôle le comportement de la boîte de dialogue.|

## <a name="remarks"></a>Notes

Créez un objet `COleChangeSourceDialog` de classe lorsque vous voulez appeler cette boîte de dialogue. Une `COleChangeSourceDialog` fois qu’un objet a été construit, vous pouvez utiliser la structure [m_cs](#m_cs) pour initialiser les valeurs ou les états de contrôles dans la boîte de dialogue. La `m_cs` structure est de type [OLEUICHANGESOURCE](/windows/win32/api/oledlg/ns-oledlg-oleuichangesourcew). Pour plus d’informations sur l’utilisation de cette classe de dialogue, consultez la fonction membre [DoModal.](#domodal)

Pour plus d’informations, consultez la structure [OLECHANGESOURCE](/windows/win32/api/oledlg/ns-oledlg-oleuichangesourcew) dans Windows SDK.

Pour plus d’informations sur les boîtes de dialogue spécifiques à l’OLOL, voir l’article [Dialog Boxes in OLE](../../mfc/dialog-boxes-in-ole.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

[COleDialog](../../mfc/reference/coledialog-class.md)

`COleChangeSourceDialog`

## <a name="requirements"></a>Spécifications

**En-tête:** afxodlgs.h

## <a name="colechangesourcedialogcolechangesourcedialog"></a><a name="colechangesourcedialog"></a>COleChangeSourceDialog::COleChangeSourceDialog

Cette fonction construit `COleChangeSourceDialog` un objet.

```
explicit COleChangeSourceDialog(
    COleClientItem* pItem,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>Paramètres

*pItem (en)*<br/>
Pointeur sur le [COleClientItem](../../mfc/reference/coleclientitem-class.md) lié dont la source doit être mise à jour.

*pParentWnd*<br/>
Points à l’objet de fenêtre `CWnd`du parent ou du propriétaire (de type ) auquel appartient l’objet de dialogue. S’il s’agit de NULL, la fenêtre parente de la boîte de dialogue sera réglée sur la fenêtre d’application principale.

### <a name="remarks"></a>Notes

Pour afficher la boîte de dialogue, appelez la fonction [DoModal.](#domodal)

Pour plus d’informations, consultez la structure [OLECHANGESOURCE](/windows/win32/api/oledlg/ns-oledlg-oleuichangesourcew) et la fonction [OleUIChangeSource](/windows/win32/api/oledlg/nf-oledlg-oleuichangesourcew) dans Windows SDK.

## <a name="colechangesourcedialogdomodal"></a><a name="domodal"></a>COleChangeSourceDialog::DoModal

Appelez cette fonction pour afficher la boîte de dialogue OLE Change Source.

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>Valeur de retour

État d’achèvement pour la boîte de dialogue. L’une des valeurs suivantes :

- IDOK si la boîte de dialogue a été affichée avec succès.

- IDCANCEL si l’utilisateur a annulé la boîte de dialogue.

- IDABORT en cas d’erreur. Si IDABORT est retourné, appelez le [COleDialog: :GetLastError](../../mfc/reference/coledialog-class.md#getlasterror) fonction membre pour obtenir plus d’informations sur le type d’erreur qui s’est produite. Pour une liste d’erreurs possibles, consultez la fonction [OleUIChangeSource](/windows/win32/api/oledlg/nf-oledlg-oleuichangesourcew) dans Windows SDK.

### <a name="remarks"></a>Notes

Si vous souhaitez paralyser les différents contrôles de boîte de dialogue en définissant `DoModal`les membres de la structure [m_cs,](#m_cs) vous devriez le faire avant d’appeler, mais après la construction de l’objet de dialogue.

Si `DoModal` vous retournez IDOK, vous pouvez appeler les fonctions des membres pour récupérer les paramètres ou les informations entrés par l’utilisateur à partir de la boîte de dialogue. La liste suivante nomme les fonctions de requête typiques :

- [GetFileName](#getfilename)

- [GetDisplayName (en)](#getdisplayname)

- [GetItemName (en)](#getitemname)

## <a name="colechangesourcedialoggetdisplayname"></a><a name="getdisplayname"></a>COleChangeSourceDialog::GetDisplayName

Appelez cette fonction pour récupérer le nom d’affichage complet de l’élément client lié.

```
CString GetDisplayName();
```

### <a name="return-value"></a>Valeur de retour

Le nom d’affichage source complète (surnom) pour le [COleClientItem](../../mfc/reference/coleclientitem-class.md) spécifié dans le constructeur.

## <a name="colechangesourcedialoggetfilename"></a><a name="getfilename"></a>COleChangeSourceDialog::GetFileName

Appelez cette fonction pour récupérer la partie de nom d’affichage du nom d’affichage pour l’élément client lié.

```
CString GetFileName();
```

### <a name="return-value"></a>Valeur de retour

La partie de nom d’affichage source du nom d’affichage [de la source](../../mfc/reference/coleclientitem-class.md) spécifiée dans le constructeur.

### <a name="remarks"></a>Notes

Le surnom de fichier ainsi que le surnom d’élément donne le nom d’affichage complet.

## <a name="colechangesourcedialoggetfromprefix"></a><a name="getfromprefix"></a>COleChangeSourceDialog::GetFromPrefix

Appelez cette fonction pour obtenir la chaîne préfixe précédente pour la source.

```
CString GetFromPrefix();
```

### <a name="return-value"></a>Valeur de retour

La chaîne préfixe précédente de la source.

### <a name="remarks"></a>Notes

Appelez cette fonction seulement après [que DoModal](#domodal) a revient à IDOK.

Cette valeur provient `lpszFrom` directement du membre de la structure [OLEUICHANGESOURCE.](/windows/win32/api/oledlg/ns-oledlg-oleuichangesourcew)

Pour plus d’informations, consultez la structure [OLECHANGESOURCE](/windows/win32/api/oledlg/ns-oledlg-oleuichangesourcew) dans Windows SDK.

## <a name="colechangesourcedialoggetitemname"></a><a name="getitemname"></a>COleChangeSourceDialog::GetItemName

Appelez cette fonction pour récupérer la partie de surnom d’élément du nom d’affichage pour l’élément client lié.

```
CString GetItemName();
```

### <a name="return-value"></a>Valeur de retour

La partie de surnom d’élément du nom d’affichage source pour le [COleClientItem](../../mfc/reference/coleclientitem-class.md) spécifiée dans le constructeur.

### <a name="remarks"></a>Notes

Le surnom de fichier ainsi que le surnom d’élément donne le nom d’affichage complet.

## <a name="colechangesourcedialoggettoprefix"></a><a name="gettoprefix"></a>COleChangeSourceDialog::GetToPrefix

Appelez cette fonction pour obtenir la nouvelle chaîne de préfixe pour la source.

```
CString GetToPrefix();
```

### <a name="return-value"></a>Valeur de retour

La nouvelle chaîne préfixe de la source.

### <a name="remarks"></a>Notes

Appelez cette fonction seulement après [que DoModal](#domodal) a revient à IDOK.

Cette valeur provient `lpszTo` directement du membre de la structure [OLEUICHANGESOURCE.](/windows/win32/api/oledlg/ns-oledlg-oleuichangesourcew)

Pour plus d’informations, consultez la structure [OLECHANGESOURCE](/windows/win32/api/oledlg/ns-oledlg-oleuichangesourcew) dans Windows SDK.

## <a name="colechangesourcedialogm_cs"></a><a name="m_cs"></a>COleChangeSourceDialog::m_cs

Ce membre de données est une structure de type [OLEUICHANGESOURCE](/windows/win32/api/oledlg/ns-oledlg-oleuichangesourcew).

```
OLEUICHANGESOURCE m_cs;
```

### <a name="remarks"></a>Notes

`OLEUICHANGESOURCE`est utilisé pour contrôler le comportement de la boîte de dialogue OLE Change Source. Les membres de cette structure peuvent être modifiés directement.

Pour plus d’informations, consultez la structure [OLECHANGESOURCE](/windows/win32/api/oledlg/ns-oledlg-oleuichangesourcew) dans Windows SDK.

## <a name="colechangesourcedialogisvalidsource"></a><a name="isvalidsource"></a>COleChangeSourceDialog::IsValidSource

Appelez cette fonction pour déterminer si la nouvelle source est valide.

```
BOOL IsValidSource();
```

### <a name="return-value"></a>Valeur de retour

Nonzero si la nouvelle source est valide, sinon 0.

### <a name="remarks"></a>Notes

Appelez cette fonction seulement après [que DoModal](#domodal) a revient à IDOK.

Pour plus d’informations, consultez la structure [OLECHANGESOURCE](/windows/win32/api/oledlg/ns-oledlg-oleuichangesourcew) dans Windows SDK.

## <a name="see-also"></a>Voir aussi

[COleDialog, classe](../../mfc/reference/coledialog-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[COleDialog, classe](../../mfc/reference/coledialog-class.md)
