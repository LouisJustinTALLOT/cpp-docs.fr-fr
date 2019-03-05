---
title: Colechangesourcedialog, classe
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
ms.openlocfilehash: 1d118b132fc110402967e9c7f2b1d74a2164d7c8
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57304611"
---
# <a name="colechangesourcedialog-class"></a>Colechangesourcedialog, classe

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
|[COleChangeSourceDialog::DoModal](#domodal)|Affiche la boîte de dialogue OLE modifier la Source.|
|[COleChangeSourceDialog::GetDisplayName](#getdisplayname)|Obtient le nom d’affichage source complet.|
|[COleChangeSourceDialog::GetFileName](#getfilename)|Obtient le nom de fichier à partir du nom de la source.|
|[COleChangeSourceDialog::GetFromPrefix](#getfromprefix)|Obtient le préfixe de la source précédente.|
|[COleChangeSourceDialog::GetItemName](#getitemname)|Obtient le nom de l’élément à partir du nom de la source.|
|[COleChangeSourceDialog::GetToPrefix](#gettoprefix)|Obtient le préfixe de la nouvelle source|
|[COleChangeSourceDialog::IsValidSource](#isvalidsource)|Indique si la source est valide.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[COleChangeSourceDialog::m_cs](#m_cs)|Structure qui contrôle le comportement de la boîte de dialogue.|

## <a name="remarks"></a>Notes

Créer un objet de classe `COleChangeSourceDialog` lorsque vous souhaitez appeler cette boîte de dialogue. Après un `COleChangeSourceDialog` objet a été construit, vous pouvez utiliser la [m_cs](#m_cs) structure pour initialiser les valeurs ou les États de contrôles dans la boîte de dialogue. Le `m_cs` structure est de type [OLEUICHANGESOURCE](/windows/desktop/api/oledlg/ns-oledlg-tagoleuichangesourcea). Pour plus d’informations sur l’utilisation de cette classe de boîte de dialogue, consultez la [DoModal](#domodal) fonction membre.

Pour plus d’informations, consultez le [OLEUICHANGESOURCE](/windows/desktop/api/oledlg/ns-oledlg-tagoleuichangesourcea) structure dans le Kit de développement logiciel Windows.

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

**En-tête :** afxodlgs.h

##  <a name="colechangesourcedialog"></a>  COleChangeSourceDialog::COleChangeSourceDialog

Cette fonction construit un `COleChangeSourceDialog` objet.

```
explicit COleChangeSourceDialog(
    COleClientItem* pItem,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>Paramètres

*pItem*<br/>
Pointeur vers l’élément lié [COleClientItem](../../mfc/reference/coleclientitem-class.md) dont la source est mise à jour.

*pParentWnd*<br/>
Pointe vers l’objet de fenêtre parente ou propriétaire (de type `CWnd`) auquel appartient l’objet de la boîte de dialogue. Si sa valeur est NULL, la fenêtre parente de la boîte de dialogue est fixée à la fenêtre principale de l’application.

### <a name="remarks"></a>Notes

Pour afficher la boîte de dialogue, appelez le [DoModal](#domodal) (fonction).

Pour plus d’informations, consultez le [OLEUICHANGESOURCE](/windows/desktop/api/oledlg/ns-oledlg-tagoleuichangesourcea) structure et [OleUIChangeSource](/windows/desktop/api/oledlg/nf-oledlg-oleuichangesourcea) fonction dans le Kit de développement logiciel Windows.

##  <a name="domodal"></a>  COleChangeSourceDialog::DoModal

Appelez cette fonction pour afficher la boîte de dialogue OLE modifier la Source.

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>Valeur de retour

État d’achèvement de la boîte de dialogue. Une des valeurs suivantes :

- IDOK si la boîte de dialogue a été correctement affichée.

- IDCANCEL, si l’utilisateur a annulé la boîte de dialogue.

- IDABORT si une erreur s’est produite. Si IDABORT est retournée, appelez le [COleDialog::GetLastError](../../mfc/reference/coledialog-class.md#getlasterror) fonction membre pour obtenir plus d’informations sur le type d’erreur qui s’est produite. Pour obtenir la liste des erreurs possibles, consultez le [OleUIChangeSource](/windows/desktop/api/oledlg/nf-oledlg-oleuichangesourcea) fonction dans le Kit de développement logiciel Windows.

### <a name="remarks"></a>Notes

Si vous souhaitez initialiser les divers contrôles de boîte de dialogue en définissant des membres de la [m_cs](#m_cs) structure, vous devez le faire avant d’appeler `DoModal`, mais une fois que l’objet de la boîte de dialogue est construit.

Si `DoModal` retourne IDOK, vous pouvez appeler des fonctions pour récupérer des paramètres entré par l’utilisateur ou les informations à partir de la boîte de dialogue membres. La liste suivante nomme les fonctions de requête classique :

- [GetFileName](#getfilename)

- [GetDisplayName](#getdisplayname)

- [GetItemName](#getitemname)

##  <a name="getdisplayname"></a>  COleChangeSourceDialog::GetDisplayName

Appelez cette fonction pour récupérer le nom d’affichage complet pour l’élément client lié.

```
CString GetDisplayName();
```

### <a name="return-value"></a>Valeur de retour

Le nom d’affichage source complet (moniker) pour le [COleClientItem](../../mfc/reference/coleclientitem-class.md) spécifié dans le constructeur.

##  <a name="getfilename"></a>  COleChangeSourceDialog::GetFileName

Appelez cette fonction pour récupérer la partie du moniker de fichier du nom complet de l’élément client lié.

```
CString GetFileName();
```

### <a name="return-value"></a>Valeur de retour

La partie du moniker de fichier du nom d’affichage de source pour le [COleClientItem](../../mfc/reference/coleclientitem-class.md) spécifié dans le constructeur.

### <a name="remarks"></a>Notes

Le moniker du fichier avec le moniker de l’élément donne le nom complet.

##  <a name="getfromprefix"></a>  COleChangeSourceDialog::GetFromPrefix

Appelez cette fonction pour obtenir la chaîne de préfixe précédent pour la source.

```
CString GetFromPrefix();
```

### <a name="return-value"></a>Valeur de retour

La chaîne de préfixe précédent de la source.

### <a name="remarks"></a>Notes

Appel de cette fonction uniquement après avoir [DoModal](#domodal) retourne IDOK.

Cette valeur provient directement le `lpszFrom` membre de la [OLEUICHANGESOURCE](/windows/desktop/api/oledlg/ns-oledlg-tagoleuichangesourcea) structure.

Pour plus d’informations, consultez le [OLEUICHANGESOURCE](/windows/desktop/api/oledlg/ns-oledlg-tagoleuichangesourcea) structure dans le Kit de développement logiciel Windows.

##  <a name="getitemname"></a>  COleChangeSourceDialog::GetItemName

Appelez cette fonction pour récupérer la partie de moniker d’élément du nom complet de l’élément client lié.

```
CString GetItemName();
```

### <a name="return-value"></a>Valeur de retour

La partie de moniker d’élément du nom d’affichage de source pour le [COleClientItem](../../mfc/reference/coleclientitem-class.md) spécifié dans le constructeur.

### <a name="remarks"></a>Notes

Le moniker du fichier avec le moniker de l’élément donne le nom complet.

##  <a name="gettoprefix"></a>  COleChangeSourceDialog::GetToPrefix

Appelez cette fonction pour obtenir la nouvelle chaîne de préfixe pour la source.

```
CString GetToPrefix();
```

### <a name="return-value"></a>Valeur de retour

La nouvelle chaîne de préfixe de la source.

### <a name="remarks"></a>Notes

Appel de cette fonction uniquement après avoir [DoModal](#domodal) retourne IDOK.

Cette valeur provient directement le `lpszTo` membre de la [OLEUICHANGESOURCE](/windows/desktop/api/oledlg/ns-oledlg-tagoleuichangesourcea) structure.

Pour plus d’informations, consultez le [OLEUICHANGESOURCE](/windows/desktop/api/oledlg/ns-oledlg-tagoleuichangesourcea) structure dans le Kit de développement logiciel Windows.

##  <a name="m_cs"></a>  COleChangeSourceDialog::m_cs

Ce membre de données est une structure de type [OLEUICHANGESOURCE](/windows/desktop/api/oledlg/ns-oledlg-tagoleuichangesourcea).

```
OLEUICHANGESOURCE m_cs;
```

### <a name="remarks"></a>Notes

`OLEUICHANGESOURCE` est utilisé pour contrôler le comportement de la boîte de dialogue OLE modifier la Source. Membres de cette structure peuvent être modifiés directement.

Pour plus d’informations, consultez le [OLEUICHANGESOURCE](/windows/desktop/api/oledlg/ns-oledlg-tagoleuichangesourcea) structure dans le Kit de développement logiciel Windows.

##  <a name="isvalidsource"></a>  COleChangeSourceDialog::IsValidSource

Appelez cette fonction pour déterminer si la nouvelle source est valide.

```
BOOL IsValidSource();
```

### <a name="return-value"></a>Valeur de retour

Différent de zéro si la nouvelle source n’est valide, sinon 0.

### <a name="remarks"></a>Notes

Appel de cette fonction uniquement après avoir [DoModal](#domodal) retourne IDOK.

Pour plus d’informations, consultez le [OLEUICHANGESOURCE](/windows/desktop/api/oledlg/ns-oledlg-tagoleuichangesourcea) structure dans le Kit de développement logiciel Windows.

## <a name="see-also"></a>Voir aussi

[COleDialog, classe](../../mfc/reference/coledialog-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[COleDialog, classe](../../mfc/reference/coledialog-class.md)
