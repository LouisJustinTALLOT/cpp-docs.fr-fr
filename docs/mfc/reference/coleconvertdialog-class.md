---
title: Classe COleConvertDialog
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
ms.openlocfilehash: 6d6690b8d06df29ce9fcd323eb8724009ee3cca9
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366164"
---
# <a name="coleconvertdialog-class"></a>Classe COleConvertDialog

Pour plus d’informations, voir la structure [OLECONVERT](/windows/win32/api/oledlg/ns-oledlg-oleuiconvertw) dans le SDK Windows.

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
|[COleConvertDialog::DoConvert](#doconvert)|Effectue la conversion spécifiée dans la boîte de dialogue.|
|[COleConvertDialog::DoModal](#domodal)|Affiche la boîte de dialogue OLE Change Item.|
|[COleConvertDialog::GetClassID](#getclassid)|Obtient le CLSID associé à l’élément choisi.|
|[COleConvertDialog::GetDrawAspect](#getdrawaspect)|Précise s’il faut dessiner l’élément comme une icône.|
|[COleConvertDialog::GetIconicMetafile](#geticonicmetafile)|Obtient une poignée au metafile associé à la forme iconique de cet article.|
|[COleConvertDialog::GetSelectionType](#getselectiontype)|Obtient le type de sélection choisi.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[COleConvertDialog::m_cv](#m_cv)|Une structure qui contrôle le comportement de la boîte de dialogue.|

## <a name="remarks"></a>Notes

> [!NOTE]
> Le code de conteneur généré par l’Assistant d’application utilise cette classe.

Pour plus d’informations sur les boîtes de dialogue spécifiques à l’OLOL, voir l’article [Dialog Boxes in OLE](../../mfc/dialog-boxes-in-ole.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

[COleDialog](../../mfc/reference/coledialog-class.md)

`COleConvertDialog`

## <a name="requirements"></a>Spécifications

**En-tête:** afxodlgs.h

## <a name="coleconvertdialogcoleconvertdialog"></a><a name="coleconvertdialog"></a>COleConvertDialog::COleConvertDialog

Construit seulement `COleConvertDialog` un objet.

```
explicit COleConvertDialog (
    COleClientItem* pItem,
    DWORD dwFlags = CF_SELECTCONVERTTO,
    CLSID* pClassID = NULL,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>Paramètres

*pItem (en)*<br/>
Points à l’élément à convertir ou à activer.

*dwFlags*<br/>
Indicateur de création, qui contient n’importe quel nombre des valeurs suivantes combinées à l’aide du bitwise-ou de l’opérateur :

- CF_SELECTCONVERTTO précise que le bouton Convertir à la radio sera choisi initialement lorsque la boîte de dialogue est appelée. Il s’agit de la valeur par défaut.

- CF_SELECTACTIVATEAS précise que le bouton Active As radio sera choisi initialement lorsque la boîte de dialogue est appelée.

- CF_SETCONVERTDEFAULT précise que la classe dont le CLSID `clsidConvertDefault` est `m_cv` spécifié par le membre de la structure sera utilisée comme sélection par défaut dans la boîte de liste de classe lorsque le bouton Convertir en radio sera sélectionné.

- CF_SETACTIVATEDEFAULT précise que la classe dont le CLSID `clsidActivateDefault` est `m_cv` spécifié par le membre de la structure sera utilisée comme sélection par défaut dans la boîte de liste de classe lorsque le bouton Radio Activate As est sélectionné.

- CF_SHOWHELPBUTTON précise que le bouton Aide sera affiché lorsque la boîte de dialogue est appelée.

*pClassID (en)*<br/>
Points au CLSID de l’élément à convertir ou à activer. Si NULL, le CLSID associé au *pItem* sera utilisé.

*pParentWnd*<br/>
Points à l’objet de fenêtre `CWnd`du parent ou du propriétaire (de type ) auquel appartient l’objet de dialogue. S’il s’agit de NULL, la fenêtre parente de la boîte de dialogue est réglée sur la fenêtre d’application principale.

### <a name="remarks"></a>Notes

Pour afficher la boîte de dialogue, appelez la fonction [DoModal.](#domodal)

Pour plus d’informations, voir [CLÉ CLSID](/windows/win32/com/clsid-key-hklm) et la structure [OLEUICONVERT.](/windows/win32/api/oledlg/ns-oledlg-oleuiconvertw)

## <a name="coleconvertdialogdoconvert"></a><a name="doconvert"></a>COleConvertDialog::DoConvert

Appelez cette fonction, après le retour avec succès de [DoModal](#domodal), soit pour convertir ou pour activer un objet de type [COleClientItem](../../mfc/reference/coleclientitem-class.md).

```
BOOL DoConvert(COleClientItem* pItem);
```

### <a name="parameters"></a>Paramètres

*pItem (en)*<br/>
Points à l’élément à convertir ou à activer. Ne peut pas avoir la valeur NULL.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

L’élément est converti ou activé en fonction des informations sélectionnées par l’utilisateur dans la boîte de dialogue Convert.

## <a name="coleconvertdialogdomodal"></a><a name="domodal"></a>COleConvertDialog::DoModal

Appelez cette fonction pour afficher la boîte de dialogue OLE Convert.

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>Valeur de retour

État d’achèvement pour la boîte de dialogue. L’une des valeurs suivantes :

- IDOK si la boîte de dialogue a été affichée avec succès.

- IDCANCEL si l’utilisateur a annulé la boîte de dialogue.

- IDABORT en cas d’erreur. Si IDABORT est retourné, appelez le [COleDialog: :GetLastError](../../mfc/reference/coledialog-class.md#getlasterror) fonction membre pour obtenir plus d’informations sur le type d’erreur qui s’est produite. Pour une liste d’erreurs possibles, voir la fonction [OleUIConvert](/windows/win32/api/oledlg/nf-oledlg-oleuiconvertw) dans le SDK Windows.

### <a name="remarks"></a>Notes

Si vous souhaitez paralyser les différents contrôles de boîte de dialogue en définissant `DoModal`les membres de la structure [m_cv,](#m_cv) vous devriez le faire avant d’appeler, mais après la construction de l’objet de dialogue.

Si `DoModal` vous retournez IDOK, vous pouvez appeler d’autres fonctions de membre pour récupérer les paramètres ou les informations qui ont été saisies par l’utilisateur dans la boîte de dialogue.

## <a name="coleconvertdialoggetclassid"></a><a name="getclassid"></a>COleConvertDialog::GetClassID

Appelez cette fonction pour obtenir le CLSID associé à l’élément choisi par l’utilisateur dans la boîte de dialogue Convert.

```
REFCLSID GetClassID() const;
```

### <a name="return-value"></a>Valeur de retour

Le CLSID associé à l’élément qui a été sélectionné dans la boîte de dialogue Convert.

### <a name="remarks"></a>Notes

Appelez cette fonction seulement après [que DoModal](#domodal) a revient à IDOK.

Pour plus d’informations, voir [clé CLSID](/windows/win32/com/clsid-key-hklm) dans le SDK Windows.

## <a name="coleconvertdialoggetdrawaspect"></a><a name="getdrawaspect"></a>COleConvertDialog::GetDrawAspect

Appelez cette fonction pour déterminer si l’utilisateur a choisi d’afficher l’élément sélectionné comme une icône.

```
DVASPECT GetDrawAspect() const;
```

### <a name="return-value"></a>Valeur de retour

La méthode nécessaire pour rendre l’objet.

- DVASPECT_CONTENT retourné si la case à cocher Display As Icon n’a pas été cochée.

- DVASPECT_ICON retourné si la case à cocher Display As Icon a été cochée.

### <a name="remarks"></a>Notes

Appelez cette fonction seulement après [que DoModal](#domodal) a revient à IDOK.

Pour plus d’informations sur l’aspect dessin, consultez la structure de données [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) dans le SDK Windows.

## <a name="coleconvertdialoggeticonicmetafile"></a><a name="geticonicmetafile"></a>COleConvertDialog::GetIconicMetafile

Appelez cette fonction pour obtenir une poignée au metafile qui contient l’aspect emblématique de l’élément sélectionné.

```
HGLOBAL GetIconicMetafile() const;
```

### <a name="return-value"></a>Valeur de retour

La poignée du metafile contenant l’aspect emblématique de l’élément sélectionné, si la case à cocher Display As Icon a été cochée lorsque le dialogue a été rejeté en choisissant OK; autrement NULL.

## <a name="coleconvertdialoggetselectiontype"></a><a name="getselectiontype"></a>COleConvertDialog::GetSelectionType

Appelez cette fonction pour déterminer le type de conversion sélectionné dans la boîte de dialogue Convert.

```
UINT GetSelectionType() const;
```

### <a name="return-value"></a>Valeur de retour

Type de sélection faite.

### <a name="remarks"></a>Notes

Les valeurs de type `Selection` retour sont spécifiées `COleConvertDialog` par le type d’énumération déclaré dans la classe.

```
enum Selection {
    noConversion,
    convertItem,
    activateAs
    };
```

Voici de brèves descriptions de ces valeurs :

- `COleConvertDialog::noConversion`Retourné si la boîte de dialogue a été annulée ou si l’utilisateur n’a sélectionné aucune conversion. Si `COleConvertDialog::DoModal` vous avez retourné IDOK, il est possible que l’utilisateur choisi une icône différente de celle précédemment sélectionnée.

- `COleConvertDialog::convertItem`Retourné si le bouton de radio Convert To a été vérifié, l’utilisateur a sélectionné un élément différent à convertir et `DoModal` retourné IDOK.

- `COleConvertDialog::activateAs`Retourné si le bouton Activez comme radio a été vérifié, l’utilisateur a sélectionné un élément différent pour activer, et `DoModal` retourné IDOK.

## <a name="coleconvertdialogm_cv"></a><a name="m_cv"></a>COleConvertDialog::m_cv

Structure de type OLEUICONVERT utilisée pour contrôler le comportement de la boîte de dialogue Convert.

```
OLEUICONVERT m_cv;
```

### <a name="remarks"></a>Notes

Les membres de cette structure peuvent être modifiés directement ou par des fonctions de membre.

Pour plus d’informations, voir la structure [OLECONVERT](/windows/win32/api/oledlg/ns-oledlg-oleuiconvertw) dans le SDK Windows.

## <a name="see-also"></a>Voir aussi

[COleDialog, classe](../../mfc/reference/coledialog-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[COleDialog, classe](../../mfc/reference/coledialog-class.md)
