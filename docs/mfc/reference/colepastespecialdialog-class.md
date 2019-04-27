---
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
ms.openlocfilehash: 9c31ed6f82f4280206bf233999fac74981636db3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62224296"
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
|[COlePasteSpecialDialog::AddFormat](#addformat)|Ajoute des formats personnalisés à la liste des formats de que votre application peut coller.|
|[COlePasteSpecialDialog::AddLinkEntry](#addlinkentry)|Ajoute une nouvelle entrée à la liste des formats de Presse-papiers pris en charge.|
|[COlePasteSpecialDialog::AddStandardFormats](#addstandardformats)|Ajoute les CF_METAFILEPICT CF_BITMAP, CF_DIB, et éventuellement CF_LINKSOURCE à la liste des formats de votre application peut coller.|
|[COlePasteSpecialDialog::CreateItem](#createitem)|Crée l’élément dans le document conteneur à l’aide du format spécifié.|
|[COlePasteSpecialDialog::DoModal](#domodal)|Affiche la boîte de dialogue OLE Collage spécial.|
|[COlePasteSpecialDialog::GetDrawAspect](#getdrawaspect)|Indique s’il faut dessiner des éléments en tant qu’icône ou pas.|
|[COlePasteSpecialDialog::GetIconicMetafile](#geticonicmetafile)|Obtient un handle du métafichier associé au formulaire sous forme d’icône de cet élément.|
|[COlePasteSpecialDialog::GetPasteIndex](#getpasteindex)|Obtient l’index d’options de collage disponible qui a été choisie par l’utilisateur.|
|[COlePasteSpecialDialog::GetSelectionType](#getselectiontype)|Obtient le type de sélection choisi.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[COlePasteSpecialDialog::m_ps](#m_ps)|Une structure de type OLEUIPASTESPECIAL qui contrôle la fonction de la boîte de dialogue.|

## <a name="remarks"></a>Notes

Créer un objet de classe `COlePasteSpecialDialog` lorsque vous souhaitez appeler cette boîte de dialogue. Après un `COlePasteSpecialDialog` objet a été construit, vous pouvez utiliser la [AddFormat](#addformat) et [AddStandardFormats](#addstandardformats) des fonctions membres pour ajouter des formats de Presse-papiers à la boîte de dialogue. Vous pouvez également utiliser le [m_ps](#m_ps) structure pour initialiser les valeurs ou les États de contrôles dans la boîte de dialogue. Le `m_ps` structure est de type OLEUIPASTESPECIAL.

Pour plus d’informations, consultez le [OLEUIPASTESPECIAL](/windows/desktop/api/oledlg/ns-oledlg-tagoleuipastespeciala) structure dans le SDK Windows.

Pour plus d’informations sur les boîtes de dialogue spécifiques à OLE, consultez l’article [boîtes de dialogue dans OLE](../../mfc/dialog-boxes-in-ole.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

[COleDialog](../../mfc/reference/coledialog-class.md)

`COlePasteSpecialDialog`

## <a name="requirements"></a>Configuration requise

**En-tête :** afxodlgs.h

##  <a name="addformat"></a>  COlePasteSpecialDialog::AddFormat

Appelez cette fonction pour ajouter de nouveaux formats à la liste des formats de que votre application peut prendre en charge dans une opération de collage spécial.

```
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
Chaîne qui décrit le format à l’utilisateur.

*lpszResult*<br/>
Chaîne qui décrit le résultat si ce format est choisi dans la boîte de dialogue.

*flags*<br/>
L’autre liaison et incorporation options disponibles pour ce format. Cet indicateur est une combinaison au niveau du bit d’un ou plusieurs des valeurs différentes dans le OLEUIPASTEFLAG type énuméré.

*cf*<br/>
Le format de Presse-papiers à ajouter.

*tymed*<br/>
Les types de média disponibles dans ce format. Il s’agit d’une combinaison au niveau du bit d’un ou plusieurs des valeurs dans le TYMED type énuméré.

*nFormatID*<br/>
L’ID de la chaîne qui identifie ce format. Le format de cette chaîne est de deux chaînes séparées par un caractère « \n ». La première chaîne est identique à celui qui est passée dans le *lpstrFormat* paramètre et le second est le même que le *lpstrResult* paramètre.

*bEnableIcon*<br/>
Indicateur qui détermine si la case à cocher Afficher comme icône est activée quand ce format est sélectionné dans la zone de liste.

*bLink*<br/>
Indicateur qui détermine si la case d’option Coller la liaison est activée quand ce format est sélectionné dans la zone de liste.

### <a name="remarks"></a>Notes

Cette fonction peut être appelée pour ajouter des formats standards tels que CF_TEXT ou CF_TIFF ou des formats personnalisés que votre application a inscrit auprès du système. Pour plus d’informations sur le collage d’objets de données dans votre application, consultez l’article [des objets de données et Sources de données : Manipulation](../../mfc/data-objects-and-data-sources-manipulation.md).

Pour plus d’informations, consultez le [TYMED](/windows/desktop/api/objidl/ne-objidl-tagtymed) type d’énumération et la [FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc) structure dans le SDK Windows.

Pour plus d’informations, consultez le [OLEUIPASTEFLAG](/windows/desktop/api/oledlg/ne-oledlg-tagoleuipasteflag) énumérée de type dans le SDK Windows.

##  <a name="addlinkentry"></a>  COlePasteSpecialDialog::AddLinkEntry

Ajoute une nouvelle entrée à la liste des formats de Presse-papiers pris en charge.

```
OLEUIPASTEFLAG AddLinkEntry(UINT cf);
```

### <a name="parameters"></a>Paramètres

*cf*<br/>
Le format de Presse-papiers à ajouter.

### <a name="return-value"></a>Valeur de retour

Un [OLEUIPASTEFLAG](/windows/desktop/api/oledlg/ne-oledlg-tagoleuipasteflag) structure contenant les informations de la nouvelle entrée de lien.

##  <a name="addstandardformats"></a>  COlePasteSpecialDialog::AddStandardFormats

Appelez cette fonction pour ajouter les formats de Presse-papiers suivants à la liste des formats de que votre application peut prendre en charge dans une opération de collage spécial :

```
void AddStandardFormats(BOOL bEnableLink = TRUE);
```

### <a name="parameters"></a>Paramètres

*bEnableLink*<br/>
Indicateur qui détermine s’il faut ajouter CF_LINKSOURCE à la liste des formats de votre application peut coller.

### <a name="remarks"></a>Notes

- CF_BITMAP

- CF_DIB

- CF_METAFILEPICT

- **« Objet incorporé »**

- (facultatif) **« Lier la Source »**

Ces formats sont utilisés pour prendre en charge l’incorporation et la liaison.

##  <a name="colepastespecialdialog"></a>  COlePasteSpecialDialog::COlePasteSpecialDialog

Construit un objet `COlePasteSpecialDialog`.

```
COlePasteSpecialDialog(
    DWORD dwFlags = PSF_SELECTPASTE,
    COleDataObject* pDataObject = NULL,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>Paramètres

*dwFlags*<br/>
Indicateur de création, contient un ou plusieurs indicateurs suivants combinées à l’aide de l’opérateur OR au niveau du bit :

- PSF_SELECTPASTE Spécifie que la case d’option Coller sera vérifiée initialement lorsque la boîte de dialogue est appelée. Ne peut pas être utilisé en association avec PSF_SELECTPASTELINK. Il s'agit de la valeur par défaut.

- PSF_SELECTPASTELINK Spécifie que la case d’option Coller la liaison sera vérifiée initialement lorsque la boîte de dialogue est appelée. Ne peut pas être utilisé en association avec PSF_SELECTPASTE.

- PSF_CHECKDISPLAYASICON Spécifie que la case à cocher Afficher comme icône sera vérifiée initialement lorsque la boîte de dialogue est appelée.

- PSF_SHOWHELP Spécifie que le bouton aide s’affichera lorsque la boîte de dialogue est appelée.

*pDataObject*<br/>
Pointe vers le [COleDataObject](../../mfc/reference/coledataobject-class.md) de collage. Si cette valeur est NULL, il obtient le `COleDataObject` à partir du Presse-papiers.

*pParentWnd*<br/>
Pointe vers l’objet de fenêtre parente ou propriétaire (de type `CWnd`) auquel appartient l’objet de la boîte de dialogue. Si sa valeur est NULL, la fenêtre parente de la boîte de dialogue est définie dans la fenêtre principale de l’application.

### <a name="remarks"></a>Notes

Cette fonction construit uniquement un `COlePasteSpecialDialog` objet. Pour afficher la boîte de dialogue, appelez le [DoModal](#domodal) (fonction).

Pour plus d’informations, consultez le [OLEUIPASTEFLAG](/windows/desktop/api/oledlg/ne-oledlg-tagoleuipasteflag) énumérée de type dans le SDK Windows.

##  <a name="createitem"></a>  COlePasteSpecialDialog::CreateItem

Crée le nouvel élément a été choisi dans la boîte de dialogue Collage spécial.

```
BOOL CreateItem(COleClientItem* pNewItem);
```

### <a name="parameters"></a>Paramètres

*pNewItem*<br/>
Pointe vers un `COleClientItem` instance. Ne peut pas être Null.

### <a name="return-value"></a>Valeur de retour

Différent de zéro si l’élément a été créé avec succès ; sinon 0.

### <a name="remarks"></a>Notes

Cette fonction doit uniquement être appelée après [DoModal](#domodal) retourne IDOK.

##  <a name="domodal"></a>  COlePasteSpecialDialog::DoModal

Affiche la boîte de dialogue OLE Collage spécial.

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>Valeur de retour

État d’achèvement de la boîte de dialogue. Une des valeurs suivantes :

- IDOK si la boîte de dialogue a été correctement affichée.

- IDCANCEL, si l’utilisateur a annulé la boîte de dialogue.

- IDABORT si une erreur s’est produite. Si IDABORT est retournée, appelez le `COleDialog::GetLastError` fonction membre pour obtenir plus d’informations sur le type d’erreur qui s’est produite. Pour obtenir la liste des erreurs possibles, consultez le [OleUIPasteSpecial](/windows/desktop/api/oledlg/nf-oledlg-oleuipastespeciala) (fonction) dans le SDK Windows.

### <a name="remarks"></a>Notes

Si vous souhaitez initialiser les divers contrôles de boîte de dialogue en définissant des membres de la [m_ps](#m_ps) structure, vous devez le faire avant d’appeler `DoModal`, mais une fois que l’objet de la boîte de dialogue est construit.

Si `DoModal` retourne IDOK, vous pouvez appeler des fonctions pour récupérer les paramètres ou les informations saisies par l’utilisateur dans la boîte de dialogue autres membres.

##  <a name="getdrawaspect"></a>  COlePasteSpecialDialog::GetDrawAspect

Détermine si l’utilisateur a choisi d’afficher l’élément sélectionné en tant qu’icône.

```
DVASPECT GetDrawAspect() const;
```

### <a name="return-value"></a>Valeur de retour

La méthode nécessaire pour restituer l’objet.

- DVASPECT_CONTENT retournée si la case à cocher Afficher comme icône n’a pas été vérifiée lorsque la boîte de dialogue a été fermée.

- DVASPECT_ICON retournée si la case à cocher Afficher comme icône était activée lorsque la boîte de dialogue a été ignorée.

### <a name="remarks"></a>Notes

Uniquement appeler cette fonction après [DoModal](#domodal) retourne IDOK.

Pour plus d’informations sur l’aspect de dessin, consultez le [FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc) structure dans le SDK Windows.

##  <a name="geticonicmetafile"></a>  COlePasteSpecialDialog::GetIconicMetafile

Obtient le métafichier associé à l’élément sélectionné par l’utilisateur.

```
HGLOBAL GetIconicMetafile() const;
```

### <a name="return-value"></a>Valeur de retour

Le handle du métafichier qui contient l’aspect sous forme d’icône de l’élément sélectionné, si la case à cocher Afficher comme icône a été sélectionné lors du rejet de la boîte de dialogue en choisissant **OK**; sinon, NULL.

##  <a name="getpasteindex"></a>  COlePasteSpecialDialog::GetPasteIndex

Obtient la valeur d’index associé à l’entrée sélectionnée par l’utilisateur.

```
int GetPasteIndex() const;
```

### <a name="return-value"></a>Valeur de retour

L’index dans le tableau de `OLEUIPASTEENTRY` structures qui a été sélectionnée par l’utilisateur. Le format qui correspond à l’index sélectionné doit être utilisé lors de l’exécution de l’opération de collage.

### <a name="remarks"></a>Notes

Pour plus d’informations, consultez le [OLEUIPASTEENTRY](/windows/desktop/api/oledlg/ns-oledlg-tagoleuipasteentrya) structure dans le SDK Windows.

##  <a name="getselectiontype"></a>  COlePasteSpecialDialog::GetSelectionType

Détermine le type de sélection de l’utilisateur est effectuée.

```
UINT GetSelectionType() const;
```

### <a name="return-value"></a>Valeur de retour

Retourne le type de la sélection effectuée.

### <a name="remarks"></a>Notes

Les valeurs de type de retour sont spécifiées par le `Selection` type énumération déclarée dans la `COlePasteSpecialDialog` classe.

```
enum Selection {
    pasteLink,
    pasteNormal,
    pasteOther,
    pasteStatic
    };
```

Procédez de la brèves desccriptions des valeurs suivantes :

- `COlePasteSpecialDialog::pasteLink` Le bouton de case d’option Coller la liaison a été activé et le format choisi a été un format OLE standard.

- `COlePasteSpecialDialog::pasteNormal` La case d’option Coller a extrait avec succès et le format choisi a été un format OLE standard.

- `COlePasteSpecialDialog::pasteOther` Le format sélectionné n’est pas un format OLE standard.

- `COlePasteSpecialDialog::pasteStatic` Le format choisi a été un métafichier.

##  <a name="m_ps"></a>  COlePasteSpecialDialog::m_ps

Structure de type OLEUIPASTESPECIAL utilisée pour contrôler le comportement de la boîte de dialogue Collage spécial.

```
OLEUIPASTESPECIAL m_ps;
```

### <a name="remarks"></a>Notes

Membres de cette structure peuvent être modifiés directement ou via les fonctions membres.

Pour plus d’informations, consultez le [OLEUIPASTESPECIAL](/windows/desktop/api/oledlg/ns-oledlg-tagoleuipastespeciala) structure dans le SDK Windows.

## <a name="see-also"></a>Voir aussi

[Exemple MFC OCLIENT](../../overview/visual-cpp-samples.md)<br/>
[COleDialog, classe](../../mfc/reference/coledialog-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[COleDialog, classe](../../mfc/reference/coledialog-class.md)
