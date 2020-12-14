---
description: 'En savoir plus sur : classe COlePasteSpecialDialog'
title: COlePasteSpecialDialog, classe
ms.date: 11/04/2016
f1_keywords:
- COlePasteSpecialDialog
- AFXODLGS/COlePasteSpecialDialog
- AFXODLGS/COlePasteSpecialDialog::COlePasteSpecialDialog
- AFXODLGS/COlePasteSpecialDialog::AddFormat
- AFXODLGS/COlePasteSpecialDialog::AddLinkEntry
- AFXODLGS/COlePasteSpecialDialog::AddStandardFormats
- AFXODLGS/COlePasteSpecialDialog::CreateItem
- AFXODLGS/COlePasteSpecialDialog::DoModal
- AFXODLGS/COlePasteSpecialDialog::GetDrawAspect
- AFXODLGS/COlePasteSpecialDialog::GetIconicMetafile
- AFXODLGS/COlePasteSpecialDialog::GetPasteIndex
- AFXODLGS/COlePasteSpecialDialog::GetSelectionType
- AFXODLGS/COlePasteSpecialDialog::m_ps
helpviewer_keywords:
- COlePasteSpecialDialog [MFC], COlePasteSpecialDialog
- COlePasteSpecialDialog [MFC], AddFormat
- COlePasteSpecialDialog [MFC], AddLinkEntry
- COlePasteSpecialDialog [MFC], AddStandardFormats
- COlePasteSpecialDialog [MFC], CreateItem
- COlePasteSpecialDialog [MFC], DoModal
- COlePasteSpecialDialog [MFC], GetDrawAspect
- COlePasteSpecialDialog [MFC], GetIconicMetafile
- COlePasteSpecialDialog [MFC], GetPasteIndex
- COlePasteSpecialDialog [MFC], GetSelectionType
- COlePasteSpecialDialog [MFC], m_ps
ms.assetid: 0e82ef9a-9bbe-457e-8240-42c86a0534f7
ms.openlocfilehash: b2493fbe7f9894a27b6765cbd5e0bc583d9d4a18
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97226855"
---
# <a name="colepastespecialdialog-class"></a>COlePasteSpecialDialog, classe

Utilisée pour la boîte de dialogue OLE Collage spécial.

## <a name="syntax"></a>Syntaxe

```
class COlePasteSpecialDialog : public COleDialog
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[COlePasteSpecialDialog::COlePasteSpecialDialog](#colepastespecialdialog)|Construit un objet `COlePasteSpecialDialog`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[COlePasteSpecialDialog::AddFormat](#addformat)|Ajoute des formats personnalisés à la liste de formats que votre application peut coller.|
|[COlePasteSpecialDialog::AddLinkEntry](#addlinkentry)|Ajoute une nouvelle entrée à la liste des formats de presse-papiers pris en charge.|
|[COlePasteSpecialDialog::AddStandardFormats](#addstandardformats)|Ajoute CF_BITMAP, CF_DIB, CF_METAFILEPICT et éventuellement CF_LINKSOURCE à la liste des formats que votre application peut coller.|
|[COlePasteSpecialDialog :: CreateItem](#createitem)|Crée l’élément dans le document conteneur à l’aide du format spécifié.|
|[COlePasteSpecialDialog ::D oModal](#domodal)|Affiche la boîte de dialogue spécial de collage OLE.|
|[COlePasteSpecialDialog::GetDrawAspect](#getdrawaspect)|Indique si l’élément doit être dessiné sous la forme d’une icône.|
|[COlePasteSpecialDialog::GetIconicMetafile](#geticonicmetafile)|Obtient un handle vers le métafichier associé au formulaire sous forme de cet élément.|
|[COlePasteSpecialDialog::GetPasteIndex](#getpasteindex)|Obtient l’index des options de collage disponibles qui a été choisi par l’utilisateur.|
|[COlePasteSpecialDialog::GetSelectionType](#getselectiontype)|Obtient le type de sélection choisi.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[COlePasteSpecialDialog :: m_ps](#m_ps)|Structure de type OLEUIPASTESPECIAL qui contrôle la fonction de la boîte de dialogue.|

## <a name="remarks"></a>Notes

Créez un objet de classe `COlePasteSpecialDialog` lorsque vous souhaitez appeler cette boîte de dialogue. Une fois qu’un `COlePasteSpecialDialog` objet a été construit, vous pouvez utiliser les fonctions membres [AddFormat](#addformat) et [AddStandardFormats](#addstandardformats) pour ajouter des formats de presse-papiers à la boîte de dialogue. Vous pouvez également utiliser la structure [m_ps](#m_ps) pour initialiser les valeurs ou les États des contrôles dans la boîte de dialogue. La `m_ps` structure est de type OLEUIPASTESPECIAL.

Pour plus d’informations, consultez la structure [OLEUIPASTESPECIAL](/windows/win32/api/oledlg/ns-oledlg-oleuipastespecialw) dans le SDK Windows.

Pour plus d’informations sur les boîtes de dialogue spécifiques à OLE, consultez l’article [boîtes de dialogue dans OLE](../../mfc/dialog-boxes-in-ole.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

[COleDialog](../../mfc/reference/coledialog-class.md)

`COlePasteSpecialDialog`

## <a name="requirements"></a>Spécifications

**En-tête :** afxodlgs. h

## <a name="colepastespecialdialogaddformat"></a><a name="addformat"></a> COlePasteSpecialDialog::AddFormat

Appelez cette fonction pour ajouter de nouveaux formats à la liste de formats que votre application peut prendre en charge dans une opération de Collage spécial.

```cpp
void AddFormat(
    const FORMATETC& formatEtc,
    LPTSTR lpszFormat,
    LPTSTR lpszResult,
    DWORD flags);

void AddFormat(
    UINT cf,
    DWORD tymed,
    UINT nFormatID,
    BOOL bEnableIcon,
    BOOL bLink);
```

### <a name="parameters"></a>Paramètres

*fmt*<br/>
Référence au type de données à ajouter.

*lpszFormat*<br/>
Chaîne qui décrit le format de l’utilisateur.

*lpszResult*<br/>
Chaîne qui décrit le résultat si ce format est choisi dans la boîte de dialogue.

*flags*<br/>
Les différentes options de liaison et d’incorporation disponibles pour ce format. Cet indicateur est une combinaison au niveau du bit d’une ou plusieurs des valeurs différentes dans le type énuméré OLEUIPASTEFLAG.

*Trésor*<br/>
Format du presse-papiers à ajouter.

*TYMED*<br/>
Types de médias disponibles dans ce format. Il s’agit d’une combinaison au niveau du bit d’une ou plusieurs des valeurs du type énuméré TYMED.

*nFormatID*<br/>
ID de la chaîne qui identifie ce format. Le format de cette chaîne est deux chaînes séparées séparées par un caractère « \n ». La première chaîne est la même que celle transmise dans le paramètre *lpstrFormat* , tandis que la seconde est la même que celle du paramètre *lpstrResult* .

*bEnableIcon*<br/>
Indicateur qui détermine si la case à cocher Afficher sous forme d’icône est activée lorsque ce format est choisi dans la zone de liste.

*Clignote*<br/>
Indicateur qui détermine si la case d’option Coller le lien est activée lorsque ce format est choisi dans la zone de liste.

### <a name="remarks"></a>Notes

Cette fonction peut être appelée pour ajouter des formats standard tels que CF_TEXT ou CF_TIFF ou des formats personnalisés que votre application a inscrits auprès du système. Pour plus d’informations sur le collage d’objets de données dans votre application, consultez l’article [objets de données et sources de données : manipulation](../../mfc/data-objects-and-data-sources-manipulation.md).

Pour plus d’informations, consultez le type d’énumération [TYMED](/windows/win32/api/objidl/ne-objidl-tymed) et la structure [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) dans le SDK Windows.

Pour plus d’informations, consultez le type énuméré [OLEUIPASTEFLAG](/windows/win32/api/oledlg/ne-oledlg-oleuipasteflag) dans le SDK Windows.

## <a name="colepastespecialdialogaddlinkentry"></a><a name="addlinkentry"></a> COlePasteSpecialDialog::AddLinkEntry

Ajoute une nouvelle entrée à la liste des formats de presse-papiers pris en charge.

```
OLEUIPASTEFLAG AddLinkEntry(UINT cf);
```

### <a name="parameters"></a>Paramètres

*Trésor*<br/>
Format du presse-papiers à ajouter.

### <a name="return-value"></a>Valeur renvoyée

Structure [OLEUIPASTEFLAG](/windows/win32/api/oledlg/ne-oledlg-oleuipasteflag) contenant les informations relatives à la nouvelle entrée de lien.

## <a name="colepastespecialdialogaddstandardformats"></a><a name="addstandardformats"></a> COlePasteSpecialDialog::AddStandardFormats

Appelez cette fonction pour ajouter les formats de presse-papiers suivants à la liste des formats que votre application peut prendre en charge dans une opération de Collage spécial :

```cpp
void AddStandardFormats(BOOL bEnableLink = TRUE);
```

### <a name="parameters"></a>Paramètres

*bEnableLink*<br/>
Indicateur qui détermine s’il faut ajouter CF_LINKSOURCE à la liste des formats que votre application peut coller.

### <a name="remarks"></a>Notes

- CF_BITMAP

- CF_DIB

- CF_METAFILEPICT

- **« Objet incorporé »**

- éventuellement **« Source de la liaison »**

Ces formats sont utilisés pour prendre en charge l’incorporation et la liaison.

## <a name="colepastespecialdialogcolepastespecialdialog"></a><a name="colepastespecialdialog"></a> COlePasteSpecialDialog::COlePasteSpecialDialog

Construit un objet `COlePasteSpecialDialog`.

```
COlePasteSpecialDialog(
    DWORD dwFlags = PSF_SELECTPASTE,
    COleDataObject* pDataObject = NULL,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>Paramètres

*dwFlags*<br/>
Indicateur de création, contenant un nombre quelconque des indicateurs suivants combinés à l’aide de l’opérateur or au niveau du bit :

- PSF_SELECTPASTE spécifie que la case d’option Coller sera activée initialement lorsque la boîte de dialogue sera appelée. Ne peut pas être utilisé en association avec PSF_SELECTPASTELINK. Il s’agit de la valeur par défaut.

- PSF_SELECTPASTELINK spécifie que la case d’option Coller le lien sera activée initialement lorsque la boîte de dialogue sera appelée. Ne peut pas être utilisé en association avec PSF_SELECTPASTE.

- PSF_CHECKDISPLAYASICON spécifie que la case à cocher Afficher sous forme d’icône est activée initialement lorsque la boîte de dialogue est appelée.

- PSF_SHOWHELP spécifie que le bouton aide s’affiche lorsque la boîte de dialogue est appelée.

*pDataObject*<br/>
Pointe vers le [COleDataObject](../../mfc/reference/coledataobject-class.md) pour le collage. Si cette valeur est NULL, elle obtient le `COleDataObject` à partir du presse-papiers.

*pParentWnd*<br/>
Pointe vers l’objet de fenêtre parent ou propriétaire (de type `CWnd` ) auquel l’objet de boîte de dialogue appartient. Si la valeur est NULL, la fenêtre parente de la boîte de dialogue est définie sur la fenêtre d’application principale.

### <a name="remarks"></a>Notes

Cette fonction construit uniquement un `COlePasteSpecialDialog` objet. Pour afficher la boîte de dialogue, appelez la fonction [DoModal](#domodal) .

Pour plus d’informations, consultez le type énuméré [OLEUIPASTEFLAG](/windows/win32/api/oledlg/ne-oledlg-oleuipasteflag) dans le SDK Windows.

## <a name="colepastespecialdialogcreateitem"></a><a name="createitem"></a> COlePasteSpecialDialog :: CreateItem

Crée le nouvel élément qui a été sélectionné dans la boîte de dialogue Collage spécial.

```
BOOL CreateItem(COleClientItem* pNewItem);
```

### <a name="parameters"></a>Paramètres

*pNewItem*<br/>
Pointe vers une `COleClientItem` instance. Ne peut pas avoir la valeur NULL.

### <a name="return-value"></a>Valeur renvoyée

Différent de zéro si l’élément a été créé avec succès ; Sinon, 0.

### <a name="remarks"></a>Notes

Cette fonction doit uniquement être appelée une fois que [DoModal](#domodal) retourne IDOK.

## <a name="colepastespecialdialogdomodal"></a><a name="domodal"></a> COlePasteSpecialDialog ::D oModal

Affiche la boîte de dialogue spécial de collage OLE.

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>Valeur renvoyée

État d’achèvement de la boîte de dialogue. Une des valeurs suivantes :

- IDOK si la boîte de dialogue a été correctement affichée.

- IDCANCEL si l’utilisateur a annulé la boîte de dialogue.

- IDABORT si une erreur s’est produite. Si IDABORT est retourné, appelez la `COleDialog::GetLastError` fonction membre pour obtenir plus d’informations sur le type d’erreur qui s’est produit. Pour obtenir la liste des erreurs possibles, consultez la fonction [OleUIPasteSpecial](/windows/win32/api/oledlg/nf-oledlg-oleuipastespecialw) dans la SDK Windows.

### <a name="remarks"></a>Notes

Si vous souhaitez initialiser les différents contrôles de boîte de dialogue en définissant les membres de la structure [m_ps](#m_ps) , vous devez le faire avant d’appeler `DoModal` , mais après la construction de l’objet de boîte de dialogue.

Si `DoModal` retourne IDOK, vous pouvez appeler d’autres fonctions membres pour récupérer les paramètres ou les informations entrées par l’utilisateur dans la boîte de dialogue.

## <a name="colepastespecialdialoggetdrawaspect"></a><a name="getdrawaspect"></a> COlePasteSpecialDialog::GetDrawAspect

Détermine si l’utilisateur a choisi d’afficher l’élément sélectionné en tant qu’icône.

```
DVASPECT GetDrawAspect() const;
```

### <a name="return-value"></a>Valeur renvoyée

Méthode nécessaire pour restituer l’objet.

- DVASPECT_CONTENT retourné si la case à cocher Afficher comme icône n’a pas été activée lorsque la boîte de dialogue a été fermée.

- DVASPECT_ICON retourné si la case à cocher Afficher comme icône a été activée lorsque la boîte de dialogue a été fermée.

### <a name="remarks"></a>Notes

Appelez cette fonction uniquement lorsque [DoModal](#domodal) retourne IDOK.

Pour plus d’informations sur l’aspect du dessin, consultez la structure [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) dans le SDK Windows.

## <a name="colepastespecialdialoggeticonicmetafile"></a><a name="geticonicmetafile"></a> COlePasteSpecialDialog::GetIconicMetafile

Obtient le métafichier associé à l’élément sélectionné par l’utilisateur.

```
HGLOBAL GetIconicMetafile() const;
```

### <a name="return-value"></a>Valeur renvoyée

Handle du métafichier contenant l’aspect sous forme de l’élément sélectionné, si la case à cocher Afficher comme icône a été activée lorsque la boîte de dialogue a été fermée, en choisissant **OK**. Sinon, NULL.

## <a name="colepastespecialdialoggetpasteindex"></a><a name="getpasteindex"></a> COlePasteSpecialDialog::GetPasteIndex

Obtient la valeur d’index associée à l’entrée sélectionnée par l’utilisateur.

```
int GetPasteIndex() const;
```

### <a name="return-value"></a>Valeur renvoyée

Index dans le tableau de `OLEUIPASTEENTRY` structures qui a été sélectionné par l’utilisateur. Le format qui correspond à l’index sélectionné doit être utilisé lors de l’opération de collage.

### <a name="remarks"></a>Notes

Pour plus d’informations, consultez la structure [OLEUIPASTEENTRY](/windows/win32/api/oledlg/ns-oledlg-oleuipasteentryw) dans le SDK Windows.

## <a name="colepastespecialdialoggetselectiontype"></a><a name="getselectiontype"></a> COlePasteSpecialDialog::GetSelectionType

Détermine le type de sélection effectué par l’utilisateur.

```
UINT GetSelectionType() const;
```

### <a name="return-value"></a>Valeur renvoyée

Retourne le type de sélection effectuée.

### <a name="remarks"></a>Notes

Les valeurs de type de retour sont spécifiées par le `Selection` type d’énumération déclaré dans la `COlePasteSpecialDialog` classe.

```
enum Selection {
    pasteLink,
    pasteNormal,
    pasteOther,
    pasteStatic
    };
```

Les brèves desccriptions de ces valeurs sont les suivantes :

- `COlePasteSpecialDialog::pasteLink` La case d’option Coller le lien a été cochée et le format choisi est un format OLE standard.

- `COlePasteSpecialDialog::pasteNormal` La case d’option Coller a été cochée et le format choisi est un format OLE standard.

- `COlePasteSpecialDialog::pasteOther` Le format sélectionné n’est pas un format OLE standard.

- `COlePasteSpecialDialog::pasteStatic` Le format choisi était un métafichier.

## <a name="colepastespecialdialogm_ps"></a><a name="m_ps"></a> COlePasteSpecialDialog :: m_ps

Structure de type OLEUIPASTESPECIAL utilisée pour contrôler le comportement de la boîte de dialogue Collage spécial.

```
OLEUIPASTESPECIAL m_ps;
```

### <a name="remarks"></a>Notes

Les membres de cette structure peuvent être modifiés directement ou via des fonctions membres.

Pour plus d’informations, consultez la structure [OLEUIPASTESPECIAL](/windows/win32/api/oledlg/ns-oledlg-oleuipastespecialw) dans le SDK Windows.

## <a name="see-also"></a>Voir aussi

[Exemple MFC OCLIENT](../../overview/visual-cpp-samples.md)<br/>
[COleDialog, classe](../../mfc/reference/coledialog-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[COleDialog, classe](../../mfc/reference/coledialog-class.md)
