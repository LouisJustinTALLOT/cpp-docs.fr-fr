---
description: 'En savoir plus sur : classe COleChangeSourceDialog'
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
ms.openlocfilehash: 2962534b5c1e85e274d134a347821a94d646b66d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97209930"
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
|[COleChangeSourceDialog ::D oModal](#domodal)|Affiche la boîte de dialogue OLE modifier la source.|
|[COleChangeSourceDialog :: GetDisplayName](#getdisplayname)|Obtient le nom complet de la source complète.|
|[COleChangeSourceDialog :: GetFileName](#getfilename)|Obtient le nom du fichier à partir du nom de la source.|
|[COleChangeSourceDialog::GetFromPrefix](#getfromprefix)|Obtient le préfixe de la source précédente.|
|[COleChangeSourceDialog::GetItemName](#getitemname)|Obtient le nom de l’élément à partir du nom de la source.|
|[COleChangeSourceDialog::GetToPrefix](#gettoprefix)|Obtient le préfixe de la nouvelle source|
|[COleChangeSourceDialog::IsValidSource](#isvalidsource)|Indique si la source est valide.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[COleChangeSourceDialog :: m_cs](#m_cs)|Structure qui contrôle le comportement de la boîte de dialogue.|

## <a name="remarks"></a>Notes

Créez un objet de classe `COleChangeSourceDialog` lorsque vous souhaitez appeler cette boîte de dialogue. Une fois qu’un `COleChangeSourceDialog` objet a été construit, vous pouvez utiliser la structure [m_cs](#m_cs) pour initialiser les valeurs ou les États des contrôles dans la boîte de dialogue. La `m_cs` structure est de type [OLEUICHANGESOURCE](/windows/win32/api/oledlg/ns-oledlg-oleuichangesourcew). Pour plus d’informations sur l’utilisation de cette classe de boîte de dialogue, consultez la fonction membre [DoModal](#domodal) .

Pour plus d’informations, consultez la structure [OLEUICHANGESOURCE](/windows/win32/api/oledlg/ns-oledlg-oleuichangesourcew) dans SDK Windows.

Pour plus d’informations sur les boîtes de dialogue spécifiques à OLE, consultez l’article [boîtes de dialogue dans OLE](../../mfc/dialog-boxes-in-ole.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

[COleDialog](../../mfc/reference/coledialog-class.md)

`COleChangeSourceDialog`

## <a name="requirements"></a>Spécifications

**En-tête :** afxodlgs. h

## <a name="colechangesourcedialogcolechangesourcedialog"></a><a name="colechangesourcedialog"></a> COleChangeSourceDialog::COleChangeSourceDialog

Cette fonction construit un `COleChangeSourceDialog` objet.

```
explicit COleChangeSourceDialog(
    COleClientItem* pItem,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>Paramètres

*pItem*<br/>
Pointeur vers le [COleClientItem](../../mfc/reference/coleclientitem-class.md) lié dont la source doit être mise à jour.

*pParentWnd*<br/>
Pointe vers l’objet de fenêtre parent ou propriétaire (de type `CWnd` ) auquel l’objet de boîte de dialogue appartient. Si la valeur est NULL, la fenêtre parente de la boîte de dialogue est définie sur la fenêtre d’application principale.

### <a name="remarks"></a>Notes

Pour afficher la boîte de dialogue, appelez la fonction [DoModal](#domodal) .

Pour plus d’informations, consultez la structure [OLEUICHANGESOURCE](/windows/win32/api/oledlg/ns-oledlg-oleuichangesourcew) et la fonction [OLEUICHANGESOURCE](/windows/win32/api/oledlg/nf-oledlg-oleuichangesourcew) dans SDK Windows.

## <a name="colechangesourcedialogdomodal"></a><a name="domodal"></a> COleChangeSourceDialog ::D oModal

Appelez cette fonction pour afficher la boîte de dialogue OLE change source.

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>Valeur renvoyée

État d’achèvement de la boîte de dialogue. Une des valeurs suivantes :

- IDOK si la boîte de dialogue a été correctement affichée.

- IDCANCEL si l’utilisateur a annulé la boîte de dialogue.

- IDABORT si une erreur s’est produite. Si IDABORT est retourné, appelez la fonction membre [COleDialog :: GetLastError](../../mfc/reference/coledialog-class.md#getlasterror) pour obtenir plus d’informations sur le type d’erreur qui s’est produit. Pour obtenir la liste des erreurs possibles, consultez la fonction [OleUIChangeSource](/windows/win32/api/oledlg/nf-oledlg-oleuichangesourcew) dans SDK Windows.

### <a name="remarks"></a>Notes

Si vous souhaitez initialiser les différents contrôles de boîte de dialogue en définissant les membres de la structure [m_cs](#m_cs) , vous devez le faire avant d’appeler `DoModal` , mais après la construction de l’objet de boîte de dialogue.

Si `DoModal` retourne IDOK, vous pouvez appeler des fonctions membres pour récupérer des informations ou des paramètres entrés par l’utilisateur dans la boîte de dialogue. Les noms de liste suivants sont des fonctions de requête typiques :

- [GetFileName](#getfilename)

- [GetDisplayName,](#getdisplayname)

- [GetItemName](#getitemname)

## <a name="colechangesourcedialoggetdisplayname"></a><a name="getdisplayname"></a> COleChangeSourceDialog :: GetDisplayName

Appelez cette fonction pour récupérer le nom complet complet de l’élément client lié.

```
CString GetDisplayName();
```

### <a name="return-value"></a>Valeur renvoyée

Nom complet de la source complet (moniker) pour le [COleClientItem](../../mfc/reference/coleclientitem-class.md) spécifié dans le constructeur.

## <a name="colechangesourcedialoggetfilename"></a><a name="getfilename"></a> COleChangeSourceDialog :: GetFileName

Appelez cette fonction pour récupérer la partie du moniker de fichier du nom complet de l’élément client lié.

```
CString GetFileName();
```

### <a name="return-value"></a>Valeur renvoyée

Partie du moniker de fichier du nom d’affichage source pour le [COleClientItem](../../mfc/reference/coleclientitem-class.md) spécifié dans le constructeur.

### <a name="remarks"></a>Notes

Le moniker de fichier avec le moniker d’élément donne le nom complet complet.

## <a name="colechangesourcedialoggetfromprefix"></a><a name="getfromprefix"></a> COleChangeSourceDialog::GetFromPrefix

Appelez cette fonction pour obtenir la chaîne de préfixe précédente pour la source.

```
CString GetFromPrefix();
```

### <a name="return-value"></a>Valeur renvoyée

Chaîne de préfixe précédente de la source.

### <a name="remarks"></a>Notes

Appelez cette fonction uniquement lorsque [DoModal](#domodal) retourne IDOK.

Cette valeur provient directement du `lpszFrom` membre de la structure [OLEUICHANGESOURCE](/windows/win32/api/oledlg/ns-oledlg-oleuichangesourcew) .

Pour plus d’informations, consultez la structure [OLEUICHANGESOURCE](/windows/win32/api/oledlg/ns-oledlg-oleuichangesourcew) dans SDK Windows.

## <a name="colechangesourcedialoggetitemname"></a><a name="getitemname"></a> COleChangeSourceDialog::GetItemName

Appelez cette fonction pour récupérer la partie moniker de l’élément du nom complet de l’élément client lié.

```
CString GetItemName();
```

### <a name="return-value"></a>Valeur renvoyée

Partie moniker d’élément du nom d’affichage source pour le [COleClientItem](../../mfc/reference/coleclientitem-class.md) spécifié dans le constructeur.

### <a name="remarks"></a>Notes

Le moniker de fichier avec le moniker d’élément donne le nom complet complet.

## <a name="colechangesourcedialoggettoprefix"></a><a name="gettoprefix"></a> COleChangeSourceDialog::GetToPrefix

Appelez cette fonction pour obtenir la nouvelle chaîne de préfixe pour la source.

```
CString GetToPrefix();
```

### <a name="return-value"></a>Valeur renvoyée

Nouvelle chaîne de préfixe de la source.

### <a name="remarks"></a>Notes

Appelez cette fonction uniquement lorsque [DoModal](#domodal) retourne IDOK.

Cette valeur provient directement du `lpszTo` membre de la structure [OLEUICHANGESOURCE](/windows/win32/api/oledlg/ns-oledlg-oleuichangesourcew) .

Pour plus d’informations, consultez la structure [OLEUICHANGESOURCE](/windows/win32/api/oledlg/ns-oledlg-oleuichangesourcew) dans SDK Windows.

## <a name="colechangesourcedialogm_cs"></a><a name="m_cs"></a> COleChangeSourceDialog :: m_cs

Ce membre de données est une structure de type [OLEUICHANGESOURCE](/windows/win32/api/oledlg/ns-oledlg-oleuichangesourcew).

```
OLEUICHANGESOURCE m_cs;
```

### <a name="remarks"></a>Notes

`OLEUICHANGESOURCE` est utilisé pour contrôler le comportement de la boîte de dialogue de la source de modification OLE. Les membres de cette structure peuvent être modifiés directement.

Pour plus d’informations, consultez la structure [OLEUICHANGESOURCE](/windows/win32/api/oledlg/ns-oledlg-oleuichangesourcew) dans SDK Windows.

## <a name="colechangesourcedialogisvalidsource"></a><a name="isvalidsource"></a> COleChangeSourceDialog::IsValidSource

Appelez cette fonction pour déterminer si la nouvelle source est valide.

```
BOOL IsValidSource();
```

### <a name="return-value"></a>Valeur renvoyée

Différent de zéro si la nouvelle source est valide ; sinon, 0.

### <a name="remarks"></a>Notes

Appelez cette fonction uniquement lorsque [DoModal](#domodal) retourne IDOK.

Pour plus d’informations, consultez la structure [OLEUICHANGESOURCE](/windows/win32/api/oledlg/ns-oledlg-oleuichangesourcew) dans SDK Windows.

## <a name="see-also"></a>Voir aussi

[COleDialog, classe](../../mfc/reference/coledialog-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[COleDialog, classe](../../mfc/reference/coledialog-class.md)
