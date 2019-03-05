---
title: COleInsertDialog, classe
ms.date: 11/04/2016
f1_keywords:
- COleInsertDialog
- AFXODLGS/COleInsertDialog
- AFXODLGS/COleInsertDialog::COleInsertDialog
- AFXODLGS/COleInsertDialog::CreateItem
- AFXODLGS/COleInsertDialog::DoModal
- AFXODLGS/COleInsertDialog::GetClassID
- AFXODLGS/COleInsertDialog::GetDrawAspect
- AFXODLGS/COleInsertDialog::GetIconicMetafile
- AFXODLGS/COleInsertDialog::GetPathName
- AFXODLGS/COleInsertDialog::GetSelectionType
- AFXODLGS/COleInsertDialog::m_io
helpviewer_keywords:
- COleInsertDialog [MFC], COleInsertDialog
- COleInsertDialog [MFC], CreateItem
- COleInsertDialog [MFC], DoModal
- COleInsertDialog [MFC], GetClassID
- COleInsertDialog [MFC], GetDrawAspect
- COleInsertDialog [MFC], GetIconicMetafile
- COleInsertDialog [MFC], GetPathName
- COleInsertDialog [MFC], GetSelectionType
- COleInsertDialog [MFC], m_io
ms.assetid: a9ec610b-abde-431e-bd01-c40159a66dbb
ms.openlocfilehash: 750243ddf6494ecc4a6a28c0cb47b05ca7089c33
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57260684"
---
# <a name="coleinsertdialog-class"></a>COleInsertDialog, classe

Utilisée pour la boîte de dialogue OLE Insérer un objet.

## <a name="syntax"></a>Syntaxe

```
class COleInsertDialog : public COleDialog
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[COleInsertDialog::COleInsertDialog](#coleinsertdialog)|Construit un objet `COleInsertDialog`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[COleInsertDialog::CreateItem](#createitem)|Crée l’élément sélectionné dans la boîte de dialogue.|
|[COleInsertDialog::DoModal](#domodal)|Affiche la boîte de dialogue OLE insérer un objet.|
|[COleInsertDialog::GetClassID](#getclassid)|Obtient le CLSID associé à l’élément choisi.|
|[COleInsertDialog::GetDrawAspect](#getdrawaspect)|Indique s’il faut dessiner l’élément en tant qu’icône.|
|[COleInsertDialog::GetIconicMetafile](#geticonicmetafile)|Obtient un handle du métafichier associé au formulaire sous forme d’icône de cet élément.|
|[COleInsertDialog::GetPathName](#getpathname)|Obtient le chemin d’accès complet au fichier choisi dans la boîte de dialogue.|
|[COleInsertDialog::GetSelectionType](#getselectiontype)|Obtient le type d’objet sélectionné.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[COleInsertDialog::m_io](#m_io)|Une structure de type OLEUIINSERTOBJECT qui contrôle le comportement de la boîte de dialogue.|

## <a name="remarks"></a>Notes

Créer un objet de classe `COleInsertDialog` lorsque vous souhaitez appeler cette boîte de dialogue. Après un `COleInsertDialog` objet a été construit, vous pouvez utiliser la [m_io](#m_io) structure pour initialiser les valeurs ou les États de contrôles dans la boîte de dialogue. Le `m_io` structure est de type OLEUIINSERTOBJECT. Pour plus d’informations sur l’utilisation de cette classe de boîte de dialogue, consultez la [DoModal](#domodal) fonction membre.

> [!NOTE]
>  Code généré par l’Assistant de conteneur d’application utilise cette classe.

Pour plus d’informations, consultez le [OLEUIINSERTOBJECT](/windows/desktop/api/oledlg/ns-oledlg-tagoleuiinsertobjecta) structure dans le SDK Windows.

Pour plus d’informations sur les boîtes de dialogue spécifiques à OLE, consultez l’article [boîtes de dialogue dans OLE](../../mfc/dialog-boxes-in-ole.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

[COleDialog](../../mfc/reference/coledialog-class.md)

`COleInsertDialog`

## <a name="requirements"></a>Spécifications

**En-tête :** afxodlgs.h

##  <a name="coleinsertdialog"></a>  COleInsertDialog::COleInsertDialog

Cette fonction construit uniquement un `COleInsertDialog` objet.

```
COleInsertDialog (
    DWORD dwFlags = IOF_SELECTCREATENEW,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>Paramètres

*dwFlags*<br/>
Indicateur de création qui contient un nombre quelconque de valeurs suivantes pour être combinées à l’aide de l’opérateur OR au niveau du bit :

- IOF_SHOWHELP Spécifie que le bouton aide s’affichera lorsque la boîte de dialogue est appelée.

- IOF_SELECTCREATENEW Spécifie que le bouton de case d’option créer un nouveau sera sélectionné initialement lorsque la boîte de dialogue est appelée. Ceci est la valeur par défaut et ne peut pas être utilisé avec IOF_SELECTCREATEFROMFILE.

- IOF_SELECTCREATEFROMFILE Spécifie que la case d’option Créer à partir du fichier sera sélectionné initialement lorsque la boîte de dialogue est appelée. Ne peut pas être utilisé avec IOF_SELECTCREATENEW.

- IOF_CHECKLINK Spécifie que la case à cocher lien sera vérifiée initialement lorsque la boîte de dialogue est appelée.

- IOF_DISABLELINK Spécifie que le lien case à cocher est désactivée lorsque la boîte de dialogue est appelée.

- IOF_CHECKDISPLAYASICON Spécifie que la case à cocher Afficher comme icône sera vérifié au départ, l’icône actuelle s’affiche, et le bouton Changer d’icône est activé lorsque la boîte de dialogue est appelée.

- IOF_VERIFYSERVERSEXIST Spécifie que la boîte de dialogue doit valider les classes qu’il ajoute à la zone de liste en vous assurant que les serveurs spécifiés dans la base de données d’inscription existent avant que la boîte de dialogue s’affiche. Définition de cet indicateur peut nuire considérablement aux performances.

*pParentWnd*<br/>
Pointe vers l’objet de fenêtre parente ou propriétaire (de type `CWnd`) auquel appartient l’objet de la boîte de dialogue. Si sa valeur est NULL, la fenêtre parente de l’objet de la boîte de dialogue est définie dans la fenêtre principale de l’application.

### <a name="remarks"></a>Notes

Pour afficher la boîte de dialogue, appelez le [DoModal](#domodal) (fonction).

##  <a name="createitem"></a>  COleInsertDialog::CreateItem

Appelez cette fonction pour créer un objet de type [COleClientItem](../../mfc/reference/coleclientitem-class.md) uniquement si [DoModal](#domodal) retourne IDOK.

```
BOOL CreateItem(COleClientItem* pItem);
```

### <a name="parameters"></a>Paramètres

*pItem*<br/>
Pointe vers l’élément à créer.

### <a name="return-value"></a>Valeur de retour

Différent de zéro si l’élément a été créé ; sinon 0.

### <a name="remarks"></a>Notes

Vous devez allouer le `COleClientItem` de l’objet avant de pouvoir appeler cette fonction.

##  <a name="domodal"></a>  COleInsertDialog::DoModal

Appelez cette fonction pour afficher la boîte de dialogue OLE insérer un objet.

```
virtual INT_PTR
    DoModal();

INT_PTR
    DoModal(DWORD  dwFlags);
```

### <a name="parameters"></a>Paramètres

*dwFlags*<br/>
Une des valeurs suivantes :

`COleInsertDialog::DocObjectsOnly` insère uniquement DocObjects.

`COleInsertDialog::ControlsOnly` insère uniquement des contrôles ActiveX.

Zéro insère DocObject, ni un contrôle ActiveX. Résultats de cette valeur dans la même implémentation que le premier prototype répertoriés ci-dessus.

### <a name="return-value"></a>Valeur de retour

État d’achèvement de la boîte de dialogue. Une des valeurs suivantes :

- IDOK si la boîte de dialogue a été correctement affichée.

- IDCANCEL, si l’utilisateur a annulé la boîte de dialogue.

- IDABORT si une erreur s’est produite. Si IDABORT est retournée, appelez le [COleDialog::GetLastError](../../mfc/reference/coledialog-class.md#getlasterror) fonction membre pour obtenir plus d’informations sur le type d’erreur qui s’est produite. Pour obtenir la liste des erreurs possibles, consultez le [OleUIInsertObject](/windows/desktop/api/oledlg/nf-oledlg-oleuiinsertobjecta) (fonction) dans le SDK Windows.

### <a name="remarks"></a>Notes

Si vous souhaitez initialiser les divers contrôles de boîte de dialogue en définissant des membres de la [m_io](#m_io) structure, vous devez le faire avant d’appeler `DoModal`, mais une fois que l’objet de la boîte de dialogue est construit.

Si `DoModal` retourne IDOK, vous pouvez appeler des fonctions pour récupérer les paramètres ou les informations saisies dans la boîte de dialogue par l’utilisateur autres membres.

##  <a name="getclassid"></a>  COleInsertDialog::GetClassID

Appelez cette fonction pour obtenir le CLSID associé à l’élément uniquement si sélectionnée [DoModal](#domodal) retourne IDOK et le type de sélection est `COleInsertDialog::createNewItem`.

```
REFCLSID GetClassID() const;
```

### <a name="return-value"></a>Valeur de retour

Retourne le CLSID associé à l’élément sélectionné.

### <a name="remarks"></a>Notes

Pour plus d’informations, consultez [clé CLSID](/windows/desktop/com/clsid-key-hklm) dans le SDK Windows.

##  <a name="getdrawaspect"></a>  COleInsertDialog::GetDrawAspect

Appelez cette fonction pour déterminer si l’utilisateur a choisi d’afficher l’élément sélectionné en tant qu’icône.

```
DVASPECT GetDrawAspect() const;
```

### <a name="return-value"></a>Valeur de retour

La méthode nécessaire pour restituer l’objet.

- DVASPECT_CONTENT retournée si la case à cocher Afficher comme icône n’a pas été activée.

- DVASPECT_ICON retournée si la case à cocher Afficher comme icône a extrait avec succès.

### <a name="remarks"></a>Notes

Appelez cette ne fonctionnent que si [DoModal](#domodal) retourne IDOK.

Pour plus d’informations sur l’aspect de dessin, consultez [FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc) structure de données dans le SDK Windows.

##  <a name="geticonicmetafile"></a>  COleInsertDialog::GetIconicMetafile

Appelez cette fonction pour obtenir un handle du métafichier qui contient l’aspect sous forme d’icône de l’élément sélectionné.

```
HGLOBAL GetIconicMetafile() const;
```

### <a name="return-value"></a>Valeur de retour

Le handle du métafichier qui contient l’aspect sous forme d’icône de l’élément sélectionné, si la case à cocher Afficher comme icône était activée lorsque la boîte de dialogue a été fermée en choisissant **OK**; sinon, NULL.

##  <a name="getpathname"></a>  COleInsertDialog::GetPathName

Appelez cette fonction pour obtenir le chemin complet du fichier sélectionné uniquement si [DoModal](#domodal) retourne IDOK et le type de sélection n’est pas `COleInsertDialog::createNewItem`.

```
CString GetPathName() const;
```

### <a name="return-value"></a>Valeur de retour

Le chemin d’accès complet au fichier sélectionné dans la boîte de dialogue. Si le type de sélection est `createNewItem`, cette fonction retourne un sans signification `CString` en mode version finale ou provoque une assertion en mode débogage.

##  <a name="getselectiontype"></a>  COleInsertDialog::GetSelectionType

Appelez cette fonction pour obtenir le type de sélection choisi lors du rejet de la boîte de dialogue Insérer un objet en choisissant **OK**.

```
UINT GetSelectionType() const;
```

### <a name="return-value"></a>Valeur de retour

Type de la sélection effectuée.

### <a name="remarks"></a>Notes

Les valeurs de type de retour sont spécifiées par le `Selection` type énumération déclarée dans la `COleInsertDialog` classe.

```
enum Selection {
    createNewItem,
    insertFromFile,
    linkToFile
    };
```

Suivent de brèves descriptions des valeurs suivantes :

- `COleInsertDialog::createNewItem` La case Créer un nouveau a été sélectionnée.

- `COleInsertDialog::insertFromFile` La case d’option Créer à partir du fichier a été sélectionnée et que la case à cocher lien n’a pas été activée.

- `COleInsertDialog::linkToFile` La case d’option Créer à partir du fichier a été sélectionnée et que la case à cocher lien a extrait avec succès.

##  <a name="m_io"></a>  COleInsertDialog::m_io

Structure de type OLEUIINSERTOBJECT utilisée pour contrôler le comportement de la boîte de dialogue Insérer un objet.

```
OLEUIINSERTOBJECT m_io;
```

### <a name="remarks"></a>Notes

Membres de cette structure peuvent être modifiés directement ou via les fonctions membres.

Pour plus d’informations, consultez le [OLEUIINSERTOBJECT](/windows/desktop/api/oledlg/ns-oledlg-tagoleuiinsertobjecta) structure dans le SDK Windows.

## <a name="see-also"></a>Voir aussi

[Exemple MFC OCLIENT](../../visual-cpp-samples.md)<br/>
[COleDialog, classe](../../mfc/reference/coledialog-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[COleDialog, classe](../../mfc/reference/coledialog-class.md)
