---
description: 'En savoir plus sur : classe COleConvertDialog'
title: COleConvertDialog, classe
ms.date: 11/04/2016
f1_keywords:
- COleConvertDialog
- AFXODLGS/COleConvertDialog
- AFXODLGS/COleConvertDialog::COleConvertDialog
- AFXODLGS/COleConvertDialog::DoConvert
- AFXODLGS/COleConvertDialog::DoModal
- AFXODLGS/COleConvertDialog::GetClassID
- AFXODLGS/COleConvertDialog::GetDrawAspect
- AFXODLGS/COleConvertDialog::GetIconicMetafile
- AFXODLGS/COleConvertDialog::GetSelectionType
- AFXODLGS/COleConvertDialog::m_cv
helpviewer_keywords:
- COleConvertDialog [MFC], COleConvertDialog
- COleConvertDialog [MFC], DoConvert
- COleConvertDialog [MFC], DoModal
- COleConvertDialog [MFC], GetClassID
- COleConvertDialog [MFC], GetDrawAspect
- COleConvertDialog [MFC], GetIconicMetafile
- COleConvertDialog [MFC], GetSelectionType
- COleConvertDialog [MFC], m_cv
ms.assetid: a7c57714-31e8-4b78-834d-8ddd1b856a1c
ms.openlocfilehash: be0b1e88868918b623874cd5691c21752e7af47c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97227465"
---
# <a name="coleconvertdialog-class"></a>COleConvertDialog, classe

Pour plus d’informations, consultez la structure [OLEUICONVERT](/windows/win32/api/oledlg/ns-oledlg-oleuiconvertw) dans le SDK Windows.

## <a name="syntax"></a>Syntaxe

```
class COleConvertDialog : public COleDialog
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[COleConvertDialog::COleConvertDialog](#coleconvertdialog)|Construit un objet `COleConvertDialog`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[COleConvertDialog ::D oConvert](#doconvert)|Exécute la conversion spécifiée dans la boîte de dialogue.|
|[COleConvertDialog ::D oModal](#domodal)|Affiche la boîte de dialogue OLE modifier l’élément.|
|[COleConvertDialog :: GetClassID](#getclassid)|Obtient le CLSID associé à l’élément choisi.|
|[COleConvertDialog::GetDrawAspect](#getdrawaspect)|Spécifie si l’élément doit être dessiné sous la forme d’une icône.|
|[COleConvertDialog::GetIconicMetafile](#geticonicmetafile)|Obtient un handle vers le métafichier associé au formulaire sous forme de cet élément.|
|[COleConvertDialog::GetSelectionType](#getselectiontype)|Obtient le type de sélection choisi.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[COleConvertDialog :: m_cv](#m_cv)|Structure qui contrôle le comportement de la boîte de dialogue.|

## <a name="remarks"></a>Notes

> [!NOTE]
> Le code de conteneur généré par l’Assistant application utilise cette classe.

Pour plus d’informations sur les boîtes de dialogue spécifiques à OLE, consultez l’article [boîtes de dialogue dans OLE](../../mfc/dialog-boxes-in-ole.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

[COleDialog](../../mfc/reference/coledialog-class.md)

`COleConvertDialog`

## <a name="requirements"></a>Spécifications

**En-tête :** afxodlgs. h

## <a name="coleconvertdialogcoleconvertdialog"></a><a name="coleconvertdialog"></a> COleConvertDialog::COleConvertDialog

Construit uniquement un `COleConvertDialog` objet.

```
explicit COleConvertDialog (
    COleClientItem* pItem,
    DWORD dwFlags = CF_SELECTCONVERTTO,
    CLSID* pClassID = NULL,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>Paramètres

*pItem*<br/>
Pointe vers l’élément à convertir ou à activer.

*dwFlags*<br/>
Indicateur de création, qui contient un nombre quelconque de valeurs suivantes combinées à l’aide de l’opérateur or au niveau du bit :

- CF_SELECTCONVERTTO spécifie que la case d’option convertir en est sélectionnée initialement lorsque la boîte de dialogue est appelée. Il s’agit de la valeur par défaut.

- CF_SELECTACTIVATEAS spécifie que la case d’option Activer en tant que est sélectionnée initialement lorsque la boîte de dialogue est appelée.

- CF_SETCONVERTDEFAULT spécifie que la classe dont le CLSID est spécifié par le `clsidConvertDefault` membre de la `m_cv` structure sera utilisée comme sélection par défaut dans la zone de liste classe lorsque la case d’option convertir en valeur est sélectionnée.

- CF_SETACTIVATEDEFAULT spécifie que la classe dont le CLSID est spécifié par le `clsidActivateDefault` membre de la `m_cv` structure sera utilisée comme sélection par défaut dans la zone de liste classe lorsque la case d’option Activer en tant que est sélectionnée.

- CF_SHOWHELPBUTTON spécifie que le bouton aide s’affiche lorsque la boîte de dialogue est appelée.

*pClassID*<br/>
Pointe vers le CLSID de l’élément à convertir ou à activer. Si la valeur est NULL, le CLSID associé à *pItem* sera utilisé.

*pParentWnd*<br/>
Pointe vers l’objet de fenêtre parent ou propriétaire (de type `CWnd` ) auquel l’objet de boîte de dialogue appartient. Si la valeur est NULL, la fenêtre parente de la boîte de dialogue est définie sur la fenêtre d’application principale.

### <a name="remarks"></a>Notes

Pour afficher la boîte de dialogue, appelez la fonction [DoModal](#domodal) .

Pour plus d’informations, consultez la rubrique [clé CLSID](/windows/win32/com/clsid-key-hklm) et la structure [OLEUICONVERT](/windows/win32/api/oledlg/ns-oledlg-oleuiconvertw) .

## <a name="coleconvertdialogdoconvert"></a><a name="doconvert"></a> COleConvertDialog ::D oConvert

Appelez cette fonction après avoir retournée correctement à partir de [DoModal](#domodal), soit pour convertir, soit pour activer un objet de type [COleClientItem](../../mfc/reference/coleclientitem-class.md).

```
BOOL DoConvert(COleClientItem* pItem);
```

### <a name="parameters"></a>Paramètres

*pItem*<br/>
Pointe vers l’élément à convertir ou à activer. Ne peut pas avoir la valeur NULL.

### <a name="return-value"></a>Valeur renvoyée

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

L’élément est converti ou activé en fonction des informations sélectionnées par l’utilisateur dans la boîte de dialogue convertir.

## <a name="coleconvertdialogdomodal"></a><a name="domodal"></a> COleConvertDialog ::D oModal

Appelez cette fonction pour afficher la boîte de dialogue OLE Convert.

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>Valeur renvoyée

État d’achèvement de la boîte de dialogue. Une des valeurs suivantes :

- IDOK si la boîte de dialogue a été correctement affichée.

- IDCANCEL si l’utilisateur a annulé la boîte de dialogue.

- IDABORT si une erreur s’est produite. Si IDABORT est retourné, appelez la fonction membre [COleDialog :: GetLastError](../../mfc/reference/coledialog-class.md#getlasterror) pour obtenir plus d’informations sur le type d’erreur qui s’est produit. Pour obtenir la liste des erreurs possibles, consultez la fonction [OleUIConvert](/windows/win32/api/oledlg/nf-oledlg-oleuiconvertw) dans la SDK Windows.

### <a name="remarks"></a>Notes

Si vous souhaitez initialiser les différents contrôles de boîte de dialogue en définissant les membres de la structure [m_cv](#m_cv) , vous devez le faire avant d’appeler `DoModal` , mais après la construction de l’objet de boîte de dialogue.

Si `DoModal` retourne IDOK, vous pouvez appeler d’autres fonctions membres pour récupérer les paramètres ou les informations qui ont été entrés par l’utilisateur dans la boîte de dialogue.

## <a name="coleconvertdialoggetclassid"></a><a name="getclassid"></a> COleConvertDialog :: GetClassID

Appelez cette fonction pour récupérer le CLSID associé à l’élément sélectionné par l’utilisateur dans la boîte de dialogue convertir.

```
REFCLSID GetClassID() const;
```

### <a name="return-value"></a>Valeur renvoyée

CLSID associé à l’élément qui a été sélectionné dans la boîte de dialogue convertir.

### <a name="remarks"></a>Notes

Appelez cette fonction uniquement lorsque [DoModal](#domodal) retourne IDOK.

Pour plus d’informations, consultez [clé CLSID](/windows/win32/com/clsid-key-hklm) dans le SDK Windows.

## <a name="coleconvertdialoggetdrawaspect"></a><a name="getdrawaspect"></a> COleConvertDialog::GetDrawAspect

Appelez cette fonction pour déterminer si l’utilisateur a choisi d’afficher l’élément sélectionné en tant qu’icône.

```
DVASPECT GetDrawAspect() const;
```

### <a name="return-value"></a>Valeur renvoyée

Méthode nécessaire pour restituer l’objet.

- DVASPECT_CONTENT retourné si la case à cocher Afficher comme icône n’a pas été activée.

- DVASPECT_ICON retourné si la case à cocher Afficher comme icône a été activée.

### <a name="remarks"></a>Notes

Appelez cette fonction uniquement lorsque [DoModal](#domodal) retourne IDOK.

Pour plus d’informations sur l’aspect du dessin, consultez la structure de données [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) dans le SDK Windows.

## <a name="coleconvertdialoggeticonicmetafile"></a><a name="geticonicmetafile"></a> COleConvertDialog::GetIconicMetafile

Appelez cette fonction pour obtenir un handle vers le métafichier qui contient l’aspect sous forme de l’élément sélectionné.

```
HGLOBAL GetIconicMetafile() const;
```

### <a name="return-value"></a>Valeur renvoyée

Handle du métafichier contenant l’aspect sous forme de l’élément sélectionné, si la case à cocher Afficher comme icône a été activée lorsque la boîte de dialogue a été fermée, en choisissant OK. Sinon, NULL.

## <a name="coleconvertdialoggetselectiontype"></a><a name="getselectiontype"></a> COleConvertDialog::GetSelectionType

Appelez cette fonction pour déterminer le type de conversion sélectionné dans la boîte de dialogue convertir.

```
UINT GetSelectionType() const;
```

### <a name="return-value"></a>Valeur renvoyée

Type de sélection effectuée.

### <a name="remarks"></a>Notes

Les valeurs de type de retour sont spécifiées par le `Selection` type d’énumération déclaré dans la `COleConvertDialog` classe.

```
enum Selection {
    noConversion,
    convertItem,
    activateAs
    };
```

Des descriptions succinctes de ces valeurs sont les suivantes :

- `COleConvertDialog::noConversion` Retourné si la boîte de dialogue a été annulée ou si l’utilisateur n’a pas sélectionné de conversion. Si `COleConvertDialog::DoModal` a retourné IDOK, il est possible que l’utilisateur ait sélectionné une icône différente de celle précédemment sélectionnée.

- `COleConvertDialog::convertItem` Retourné si la case d’option convertir en a été activée, l’utilisateur a sélectionné un autre élément à convertir et `DoModal` a retourné IDOK.

- `COleConvertDialog::activateAs` Retourné si la case à cocher Activer en tant que est activée, l’utilisateur a sélectionné un autre élément à activer et `DoModal` a retourné IDOK.

## <a name="coleconvertdialogm_cv"></a><a name="m_cv"></a> COleConvertDialog :: m_cv

Structure de type OLEUICONVERT utilisée pour contrôler le comportement de la boîte de dialogue convertir.

```
OLEUICONVERT m_cv;
```

### <a name="remarks"></a>Notes

Les membres de cette structure peuvent être modifiés soit directement, soit par le biais de fonctions membres.

Pour plus d’informations, consultez la structure [OLEUICONVERT](/windows/win32/api/oledlg/ns-oledlg-oleuiconvertw) dans le SDK Windows.

## <a name="see-also"></a>Voir aussi

[COleDialog, classe](../../mfc/reference/coledialog-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[COleDialog, classe](../../mfc/reference/coledialog-class.md)
