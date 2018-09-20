---
title: COleConvertDialog, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b1ff8047e6d7291fe55619d8b0a3eabb877b728a
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46436537"
---
# <a name="coleconvertdialog-class"></a>COleConvertDialog, classe

Pour plus d’informations, consultez le [OLEUICONVERT](/windows/desktop/api/oledlg/ns-oledlg-tagoleuiconverta) structure dans le SDK Windows.

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
|[COleConvertDialog::DoModal](#domodal)|Affiche la boîte de dialogue OLE de modification d’élément.|
|[COleConvertDialog::GetClassID](#getclassid)|Obtient le CLSID associé à l’élément choisi.|
|[COleConvertDialog::GetDrawAspect](#getdrawaspect)|Spécifie s’il faut dessiner l’élément en tant qu’icône.|
|[COleConvertDialog::GetIconicMetafile](#geticonicmetafile)|Obtient un handle du métafichier associé au formulaire sous forme d’icône de cet élément.|
|[COleConvertDialog::GetSelectionType](#getselectiontype)|Obtient le type de sélection choisi.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[COleConvertDialog::m_cv](#m_cv)|Structure qui contrôle le comportement de la boîte de dialogue.|

## <a name="remarks"></a>Notes

> [!NOTE]
>  Code généré par l’Assistant de conteneur d’application utilise cette classe.

Pour plus d’informations sur les boîtes de dialogue spécifiques à OLE, consultez l’article [boîtes de dialogue dans OLE](../../mfc/dialog-boxes-in-ole.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

[COleDialog](../../mfc/reference/coledialog-class.md)

`COleConvertDialog`

## <a name="requirements"></a>Configuration requise

**En-tête :** afxodlgs.h

##  <a name="coleconvertdialog"></a>  COleConvertDialog::COleConvertDialog

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
Pointe vers l’élément à être converti ou activé.

*dwFlags*<br/>
Indicateur de création, qui contient un nombre quelconque des valeurs suivantes combinées à l’aide de l’opérateur de bits- ou un opérateur :

- CF_SELECTCONVERTTO Spécifie que la case d’option Convertir en sera sélectionné initialement lorsque la boîte de dialogue est appelée. Il s'agit de la valeur par défaut.

- CF_SELECTACTIVATEAS Spécifie que la case Activer en tant que sera sélectionné initialement lorsque la boîte de dialogue est appelée.

- CF_SETCONVERTDEFAULT Spécifie que la classe dont le CLSID spécifié par le `clsidConvertDefault` membre de la `m_cv` structure servira la sélection par défaut dans la zone de liste de classe lorsque la case d’option Convertir en est sélectionnée.

- CF_SETACTIVATEDEFAULT Spécifie que la classe dont le CLSID spécifié par le `clsidActivateDefault` membre de la `m_cv` structure servira la sélection par défaut dans la zone de liste de classe lorsque la case Activer en tant qu’est sélectionnée.

- CF_SHOWHELPBUTTON Spécifie que le bouton aide s’affichera lorsque la boîte de dialogue est appelée.

*pClassID*<br/>
Pointe vers le CLSID de l’élément à être converti ou activé. Si NULL, le CLSID associé *pItem* sera utilisé.

*pParentWnd*<br/>
Pointe vers l’objet de fenêtre parente ou propriétaire (de type `CWnd`) auquel appartient l’objet de la boîte de dialogue. Si sa valeur est NULL, la fenêtre parente de la boîte de dialogue est définie dans la fenêtre principale de l’application.

### <a name="remarks"></a>Notes

Pour afficher la boîte de dialogue, appelez le [DoModal](#domodal) (fonction).

Pour plus d’informations, consultez [clé CLSID](/windows/desktop/com/clsid-key-hklm) et [OLEUICONVERT](/windows/desktop/api/oledlg/ns-oledlg-tagoleuiconverta) structure.

##  <a name="doconvert"></a>  COleConvertDialog::DoConvert

Appelez cette fonction, après le retour avec succès [DoModal](#domodal), soit pour convertir ou activer un objet de type [COleClientItem](../../mfc/reference/coleclientitem-class.md).

```
BOOL DoConvert(COleClientItem* pItem);
```

### <a name="parameters"></a>Paramètres

*pItem*<br/>
Pointe vers l’élément à être converti ou activé. Ne peut pas être Null.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

L’élément est converti ou activé conformément aux informations sélectionnées par l’utilisateur dans la boîte de dialogue Convertir.

##  <a name="domodal"></a>  COleConvertDialog::DoModal

Appelez cette fonction pour afficher la boîte de dialogue Convertir OLE.

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>Valeur de retour

État d’achèvement de la boîte de dialogue. Une des valeurs suivantes :

- IDOK si la boîte de dialogue a été correctement affichée.

- IDCANCEL, si l’utilisateur a annulé la boîte de dialogue.

- IDABORT si une erreur s’est produite. Si IDABORT est retournée, appelez le [COleDialog::GetLastError](../../mfc/reference/coledialog-class.md#getlasterror) fonction membre pour obtenir plus d’informations sur le type d’erreur qui s’est produite. Pour obtenir la liste des erreurs possibles, consultez le [OleUIConvert](/windows/desktop/api/oledlg/nf-oledlg-oleuiconverta) (fonction) dans le SDK Windows.

### <a name="remarks"></a>Notes

Si vous souhaitez initialiser les divers contrôles de boîte de dialogue en définissant des membres de la [m_cv](#m_cv) structure, vous devez le faire avant d’appeler `DoModal`, mais une fois que l’objet de la boîte de dialogue est construit.

Si `DoModal` retourne IDOK, vous pouvez appeler des fonctions pour récupérer les paramètres ou les informations qui a été entrées par l’utilisateur dans la boîte de dialogue autres membres.

##  <a name="getclassid"></a>  COleConvertDialog::GetClassID

Appel de cette fonction pour obtenir le CLSID associé à l’utilisateur a sélectionné dans la boîte de dialogue Convertir l’élément.

```
REFCLSID GetClassID() const;
```

### <a name="return-value"></a>Valeur de retour

Le CLSID associé à l’élément qui a été sélectionné dans la boîte de dialogue Convertir.

### <a name="remarks"></a>Notes

Appel de cette fonction uniquement après avoir [DoModal](#domodal) retourne IDOK.

Pour plus d’informations, consultez [clé CLSID](/windows/desktop/com/clsid-key-hklm) dans le SDK Windows.

##  <a name="getdrawaspect"></a>  COleConvertDialog::GetDrawAspect

Appelez cette fonction pour déterminer si l’utilisateur a choisi d’afficher l’élément sélectionné en tant qu’icône.

```
DVASPECT GetDrawAspect() const;
```

### <a name="return-value"></a>Valeur de retour

La méthode nécessaire pour restituer l’objet.

- DVASPECT_CONTENT retournée si la case à cocher Afficher comme icône n’a pas été activée.

- DVASPECT_ICON retournée si la case à cocher Afficher comme icône a extrait avec succès.

### <a name="remarks"></a>Notes

Appel de cette fonction uniquement après avoir [DoModal](#domodal) retourne IDOK.

Pour plus d’informations sur l’aspect de dessin, consultez le [FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc) structure de données dans le SDK Windows.

##  <a name="geticonicmetafile"></a>  COleConvertDialog::GetIconicMetafile

Appelez cette fonction pour obtenir un handle du métafichier qui contient l’aspect sous forme d’icône de l’élément sélectionné.

```
HGLOBAL GetIconicMetafile() const;
```

### <a name="return-value"></a>Valeur de retour

Le handle du métafichier qui contient l’aspect sous forme d’icône de l’élément sélectionné, si la case à cocher Afficher comme icône a été activée lors du rejet de la boîte de dialogue en cliquant sur OK ; Sinon, NULL.

##  <a name="getselectiontype"></a>  COleConvertDialog::GetSelectionType

Appelez cette fonction pour déterminer le type de conversion sélectionné dans la boîte de dialogue Convertir.

```
UINT GetSelectionType() const;
```

### <a name="return-value"></a>Valeur de retour

Type de la sélection effectuée.

### <a name="remarks"></a>Notes

Les valeurs de type de retour sont spécifiées par le `Selection` type énumération déclarée dans la `COleConvertDialog` classe.

```
enum Selection {
    noConversion,
    convertItem,
    activateAs
    };
```

Suivent de brèves descriptions des valeurs suivantes :

- `COleConvertDialog::noConversion` Retourné si la boîte de dialogue a été annulée ou que l’utilisateur a sélectionné aucune conversion. Si `COleConvertDialog::DoModal` retourné IDOK, il est possible que l’utilisateur a sélectionné une autre icône que celle précédemment sélectionnée.

- `COleConvertDialog::convertItem` Retourné si la case d’option Convertir en a été activée, l’utilisateur a sélectionné un autre élément à convertir, et `DoModal` retourné IDOK.

- `COleConvertDialog::activateAs` Retourné si la case Activer en tant qu’a été activée, l’utilisateur a sélectionné un élément différent pour l’activation, et `DoModal` retourné IDOK.

##  <a name="m_cv"></a>  COleConvertDialog::m_cv

Structure de type OLEUICONVERT utilisée pour contrôler le comportement de la boîte de dialogue Convertir.

```
OLEUICONVERT m_cv;
```

### <a name="remarks"></a>Notes

Membres de cette structure peuvent être modifiés directement ou via les fonctions membres.

Pour plus d’informations, consultez le [OLEUICONVERT](/windows/desktop/api/oledlg/ns-oledlg-tagoleuiconverta) structure dans le SDK Windows.

## <a name="see-also"></a>Voir aussi

[COleDialog, classe](../../mfc/reference/coledialog-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[COleDialog, classe](../../mfc/reference/coledialog-class.md)
