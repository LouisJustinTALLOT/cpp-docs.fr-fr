---
title: Classe COlePasteSpecialDialog
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
ms.openlocfilehash: 47fb421ef9dedcae7f92d33f55988dbbc2ea452d
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753815"
---
# <a name="colepastespecialdialog-class"></a>Classe COlePasteSpecialDialog

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
|[COlePasteSpecialDialog::AddFormat](#addformat)|Ajoute des formats personnalisés à la liste des formats que votre application peut coller.|
|[COlePasteSpecialDialog::AddLinkEntry](#addlinkentry)|Ajoute une nouvelle entrée à la liste des formats Clipboard pris en charge.|
|[COlePasteSpecialDialog::AddStandardFormats](#addstandardformats)|Ajoute CF_BITMAP, CF_DIB, CF_METAFILEPICT et CF_LINKSOURCE optionnellement à la liste des formats que votre application peut coller.|
|[COlePasteSpecialDialog::CreateItem](#createitem)|Crée l’élément dans le document de conteneur en utilisant le format spécifié.|
|[COlePasteSpecialDialog::DoModal](#domodal)|Affiche la boîte de dialogue spéciale OLE Paste.|
|[COlePasteSpecialDialog::GetDrawAspect](#getdrawaspect)|Indique s’il faut dessiner l’élément comme une icône ou non.|
|[COlePasteSpecialDialog::GetIconicMetafile](#geticonicmetafile)|Obtient une poignée au metafile associé à la forme iconique de cet article.|
|[COlePasteSpecialDialog::GetPasteIndex](#getpasteindex)|Obtient l’index des options de pâte disponibles qui a été choisi par l’utilisateur.|
|[COlePasteSpecialDialog::GetSelectionType](#getselectiontype)|Obtient le type de sélection choisi.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[COlePasteSpecialDialog::m_ps](#m_ps)|Une structure de type OLEUIPASTESPECIAL qui contrôle la fonction de la boîte de dialogue.|

## <a name="remarks"></a>Notes

Créez un objet `COlePasteSpecialDialog` de classe lorsque vous voulez appeler cette boîte de dialogue. Une `COlePasteSpecialDialog` fois qu’un objet a été construit, vous pouvez utiliser les fonctions des membres [AddFormat](#addformat) et [AddStandardFormats](#addstandardformats) pour ajouter des formats Clipboard à la boîte de dialogue. Vous pouvez également utiliser la structure [m_ps](#m_ps) pour initialiser les valeurs ou les états de contrôle dans la boîte de dialogue. La `m_ps` structure est de type OLEUIPASTESPECIAL.

Pour plus d’informations, consultez la structure [OLEPASTESPECIAL](/windows/win32/api/oledlg/ns-oledlg-oleuipastespecialw) dans le SDK Windows.

Pour plus d’informations sur les boîtes de dialogue spécifiques à l’OLOL, voir l’article [Dialog Boxes in OLE](../../mfc/dialog-boxes-in-ole.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

[COleDialog](../../mfc/reference/coledialog-class.md)

`COlePasteSpecialDialog`

## <a name="requirements"></a>Spécifications

**En-tête:** afxodlgs.h

## <a name="colepastespecialdialogaddformat"></a><a name="addformat"></a>COlePasteSpecialDialog::AddFormat

Appelez cette fonction pour ajouter de nouveaux formats à la liste des formats que votre application peut prendre en charge dans une opération Spéciale Pâte.

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

*Fmt*<br/>
Référence au type de données à ajouter.

*lpszFormat (en)*<br/>
Chaîne qui décrit le format à l’utilisateur.

*lpszResult*<br/>
Chaîne qui décrit le résultat si ce format est choisi dans la boîte de dialogue.

*flags*<br/>
Les différentes options de liaison et d’intégration disponibles pour ce format. Ce drapeau est une combinaison un peu sage d’une ou plusieurs des différentes valeurs dans le type énuméré OLEUIPASTEFLAG.

*Cf*<br/>
Le format de presse-papiers à ajouter.

*attaché*<br/>
Les types de médias disponibles dans ce format. Il s’agit d’une combinaison un peu sage d’une ou plusieurs des valeurs dans le type énuméré TYMED.

*nFormatID (en)*<br/>
L’ID de la chaîne qui identifie ce format. Le format de cette chaîne est deux cordes séparées par un caractère 'n'. La première chaîne est la même qui serait passée dans le paramètre *lpstrFormat,* et la seconde est la même que le paramètre *lpstrResult.*

*bEnableIcon*<br/>
Indicateur qui détermine si la case à cocher Display As Icon est activée lorsque ce format est choisi dans la case de liste.

*Clignoter*<br/>
Indicateur qui détermine si le bouton radio Paste Link est activé lorsque ce format est choisi dans la boîte de liste.

### <a name="remarks"></a>Notes

Cette fonction peut être appelée à ajouter des formats standard tels que CF_TEXT ou CF_TIFF ou des formats personnalisés que votre application s’est enregistré auprès du système. Pour plus d’informations sur le coller des objets de données dans votre application, voir l’article [Data Objects and Data Sources: Manipulation](../../mfc/data-objects-and-data-sources-manipulation.md).

Pour plus d’informations, consultez le type d’énumération [TYMED](/windows/win32/api/objidl/ne-objidl-tymed) et la structure [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) dans le SDK Windows.

Pour plus d’informations, consultez le type [énuméré OLEUIPASTEFLAG](/windows/win32/api/oledlg/ne-oledlg-oleuipasteflag) dans le SDK Windows.

## <a name="colepastespecialdialogaddlinkentry"></a><a name="addlinkentry"></a>COlePasteSpecialDialog::AddLinkEntry

Ajoute une nouvelle entrée à la liste des formats Clipboard pris en charge.

```
OLEUIPASTEFLAG AddLinkEntry(UINT cf);
```

### <a name="parameters"></a>Paramètres

*Cf*<br/>
Le format de presse-papiers à ajouter.

### <a name="return-value"></a>Valeur de retour

Une structure [OLEUIPASTEFLAG](/windows/win32/api/oledlg/ne-oledlg-oleuipasteflag) contenant les informations pour la nouvelle entrée de lien.

## <a name="colepastespecialdialogaddstandardformats"></a><a name="addstandardformats"></a>COlePasteSpecialDialog::AddStandardFormats

Appelez cette fonction pour ajouter les formats Clipboard suivants à la liste des formats que votre application peut prendre en charge dans une opération Spéciale Pâte :

```cpp
void AddStandardFormats(BOOL bEnableLink = TRUE);
```

### <a name="parameters"></a>Paramètres

*bEnableLink (en)*<br/>
Indicateur qui détermine s’il faut ajouter CF_LINKSOURCE à la liste des formats que votre application peut coller.

### <a name="remarks"></a>Notes

- CF_BITMAP

- CF_DIB

- CF_METAFILEPICT

- **"Objet intégré"**

- (optionnellement) **"Source de lien"**

Ces formats sont utilisés pour soutenir l’intégration et le lien.

## <a name="colepastespecialdialogcolepastespecialdialog"></a><a name="colepastespecialdialog"></a>COlePasteSpecialDialog::COlePasteSpecialDialog

Construit un objet `COlePasteSpecialDialog`.

```
COlePasteSpecialDialog(
    DWORD dwFlags = PSF_SELECTPASTE,
    COleDataObject* pDataObject = NULL,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>Paramètres

*dwFlags*<br/>
Drapeau de création, contient n’importe quel nombre des drapeaux suivants combinés à l’aide de l’opérateur bitwise-OR:

- PSF_SELECTPASTE précise que le bouton radio Pâte sera coché initialement lorsque la boîte de dialogue est appelée. Impossible d’utiliser en combinaison avec PSF_SELECTPASTELINK. Il s’agit de la valeur par défaut.

- PSF_SELECTPASTELINK précise que le bouton radio Paste Link sera d’abord coché lorsque la boîte de dialogue est appelée. Impossible d’utiliser en combinaison avec PSF_SELECTPASTE.

- PSF_CHECKDISPLAYASICON précise que la case à cocher Display As Icon sera cochée initialement lorsque la case de dialogue est appelée.

- PSF_SHOWHELP précise que le bouton Aide sera affiché lorsque la boîte de dialogue est appelée.

*pDataObject*<br/>
Points à [l’object de COleData](../../mfc/reference/coledataobject-class.md) pour coller. Si cette valeur est NULL, il obtient le `COleDataObject` de la Planche à sous.

*pParentWnd*<br/>
Points à l’objet de fenêtre `CWnd`du parent ou du propriétaire (de type ) auquel appartient l’objet de dialogue. S’il s’agit de NULL, la fenêtre parente de la boîte de dialogue est réglée sur la fenêtre d’application principale.

### <a name="remarks"></a>Notes

Cette fonction ne `COlePasteSpecialDialog` construit qu’un objet. Pour afficher la boîte de dialogue, appelez la fonction [DoModal.](#domodal)

Pour plus d’informations, consultez le type [énuméré OLEUIPASTEFLAG](/windows/win32/api/oledlg/ne-oledlg-oleuipasteflag) dans le SDK Windows.

## <a name="colepastespecialdialogcreateitem"></a><a name="createitem"></a>COlePasteSpecialDialog::CreateItem

Crée le nouvel élément qui a été choisi dans la boîte de dialogue spécial Pâte.

```
BOOL CreateItem(COleClientItem* pNewItem);
```

### <a name="parameters"></a>Paramètres

*pNewItem (en)*<br/>
Points à `COleClientItem` une instance. Ne peut pas avoir la valeur NULL.

### <a name="return-value"></a>Valeur de retour

Nonzero si l’élément a été créé avec succès; sinon 0.

### <a name="remarks"></a>Notes

Cette fonction ne doit être appelée qu’après [le retour de DoModal](#domodal) IDOK.

## <a name="colepastespecialdialogdomodal"></a><a name="domodal"></a>COlePasteSpecialDialog::DoModal

Affiche la boîte de dialogue spéciale OLE Paste.

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>Valeur de retour

État d’achèvement pour la boîte de dialogue. L’une des valeurs suivantes :

- IDOK si la boîte de dialogue a été affichée avec succès.

- IDCANCEL si l’utilisateur a annulé la boîte de dialogue.

- IDABORT en cas d’erreur. Si IDABORT est retourné, appelez la `COleDialog::GetLastError` fonction membre pour obtenir plus d’informations sur le type d’erreur qui s’est produite. Pour une liste d’erreurs possibles, consultez la fonction [OleUIPasteSpecial](/windows/win32/api/oledlg/nf-oledlg-oleuipastespecialw) dans le SDK Windows.

### <a name="remarks"></a>Notes

Si vous souhaitez paralyser les différents contrôles de boîte de dialogue en définissant `DoModal`les membres de la structure [m_ps,](#m_ps) vous devriez le faire avant d’appeler, mais après la construction de l’objet de dialogue.

Si `DoModal` vous retournez IDOK, vous pouvez appeler d’autres fonctions de membre pour récupérer les paramètres ou l’entrée d’informations par l’utilisateur dans la boîte de dialogue.

## <a name="colepastespecialdialoggetdrawaspect"></a><a name="getdrawaspect"></a>COlePasteSpecialDialog::GetDrawAspect

Détermine si l’utilisateur a choisi d’afficher l’élément sélectionné comme une icône.

```
DVASPECT GetDrawAspect() const;
```

### <a name="return-value"></a>Valeur de retour

La méthode nécessaire pour rendre l’objet.

- DVASPECT_CONTENT retourné si la case à cocher Display As Icon n’a pas été cochée lorsque la case de dialogue a été rejetée.

- DVASPECT_ICON retourné si la case à cocher Display As Icon a été cochée lorsque la case de dialogue a été rejetée.

### <a name="remarks"></a>Notes

Appelez cette fonction seulement après [que DoModal](#domodal) retourne IDOK.

Pour plus d’informations sur l’aspect dessin, consultez la structure [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) dans le SDK Windows.

## <a name="colepastespecialdialoggeticonicmetafile"></a><a name="geticonicmetafile"></a>COlePasteSpecialDialog::GetIconicMetafile

Obtient le metafile associé à l’élément sélectionné par l’utilisateur.

```
HGLOBAL GetIconicMetafile() const;
```

### <a name="return-value"></a>Valeur de retour

La poignée du metafile contenant l’aspect emblématique de l’élément sélectionné, si la case à cocher Display As Icon a été sélectionnée lorsque la case de dialogue a été rejetée en choisissant **OK**; autrement NULL.

## <a name="colepastespecialdialoggetpasteindex"></a><a name="getpasteindex"></a>COlePasteSpecialDialog::GetPasteIndex

Obtient la valeur d’index associée à l’entrée de l’utilisateur sélectionné.

```
int GetPasteIndex() const;
```

### <a name="return-value"></a>Valeur de retour

L’index dans `OLEUIPASTEENTRY` la gamme de structures qui a été sélectionnée par l’utilisateur. Le format correspondant à l’index sélectionné doit être utilisé lors de l’exécution de l’opération de pâte.

### <a name="remarks"></a>Notes

Pour plus d’informations, consultez la structure [OLEPASTEENTRY](/windows/win32/api/oledlg/ns-oledlg-oleuipasteentryw) dans le SDK Windows.

## <a name="colepastespecialdialoggetselectiontype"></a><a name="getselectiontype"></a>COlePasteSpecialDialog::GetSelectionType

Détermine le type de sélection de l’utilisateur.

```
UINT GetSelectionType() const;
```

### <a name="return-value"></a>Valeur de retour

Retourne le type de sélection effectué.

### <a name="remarks"></a>Notes

Les valeurs de type `Selection` retour sont spécifiées `COlePasteSpecialDialog` par le type d’énumération déclaré dans la classe.

```
enum Selection {
    pasteLink,
    pasteNormal,
    pasteOther,
    pasteStatic
    };
```

Voici de brèves desccriptions de ces valeurs :

- `COlePasteSpecialDialog::pasteLink`Le bouton radio Paste Link a été vérifié et le format choisi était un format OLE standard.

- `COlePasteSpecialDialog::pasteNormal`Le bouton radio Pâte a été vérifié et le format choisi était un format OLE standard.

- `COlePasteSpecialDialog::pasteOther`Le format sélectionné n’est pas un format OLE standard.

- `COlePasteSpecialDialog::pasteStatic`Le format choisi était un métaafile.

## <a name="colepastespecialdialogm_ps"></a><a name="m_ps"></a>COlePasteSpecialDialog::m_ps

Structure de type OLEUIPASTESPECIAL utilisée pour contrôler le comportement de la boîte de dialogue spécial Pâte.

```
OLEUIPASTESPECIAL m_ps;
```

### <a name="remarks"></a>Notes

Les membres de cette structure peuvent être modifiés directement ou par des fonctions de membre.

Pour plus d’informations, consultez la structure [OLEPASTESPECIAL](/windows/win32/api/oledlg/ns-oledlg-oleuipastespecialw) dans le SDK Windows.

## <a name="see-also"></a>Voir aussi

[Échantillon MFC OCLIENT](../../overview/visual-cpp-samples.md)<br/>
[COleDialog, classe](../../mfc/reference/coledialog-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[COleDialog, classe](../../mfc/reference/coledialog-class.md)
