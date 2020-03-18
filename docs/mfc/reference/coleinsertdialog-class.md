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
ms.openlocfilehash: a884f946b60be0567f39477f434db8efe041e393
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/16/2020
ms.locfileid: "79421701"
---
# <a name="coleinsertdialog-class"></a>COleInsertDialog, classe

Utilisée pour la boîte de dialogue OLE Insérer un objet.

## <a name="syntax"></a>Syntaxe

```
class COleInsertDialog : public COleDialog
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Name|Description|
|----------|-----------------|
|[COleInsertDialog::COleInsertDialog](#coleinsertdialog)|Construit un objet `COleInsertDialog`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Name|Description|
|----------|-----------------|
|[COleInsertDialog :: CreateItem](#createitem)|Crée l’élément sélectionné dans la boîte de dialogue.|
|[COleInsertDialog ::D oModal](#domodal)|Affiche la boîte de dialogue OLE Insert Object.|
|[COleInsertDialog :: GetClassID](#getclassid)|Obtient le CLSID associé à l’élément choisi.|
|[COleInsertDialog::GetDrawAspect](#getdrawaspect)|Indique s’il faut dessiner l’élément sous la forme d’une icône.|
|[COleInsertDialog::GetIconicMetafile](#geticonicmetafile)|Obtient un handle vers le métafichier associé au formulaire sous forme de cet élément.|
|[COleInsertDialog::GetPathName](#getpathname)|Obtient le chemin d’accès complet au fichier choisi dans la boîte de dialogue.|
|[COleInsertDialog::GetSelectionType](#getselectiontype)|Obtient le type d’objet sélectionné.|

### <a name="public-data-members"></a>Membres de données publics

|Name|Description|
|----------|-----------------|
|[COleInsertDialog :: m_io](#m_io)|Structure de type OLEUIINSERTOBJECT qui contrôle le comportement de la boîte de dialogue.|

## <a name="remarks"></a>Notes

Créez un objet de la classe `COleInsertDialog` lorsque vous souhaitez appeler cette boîte de dialogue. Une fois qu’un objet `COleInsertDialog` a été construit, vous pouvez utiliser la structure [m_io](#m_io) pour initialiser les valeurs ou les États des contrôles dans la boîte de dialogue. La structure `m_io` est de type OLEUIINSERTOBJECT. Pour plus d’informations sur l’utilisation de cette classe de boîte de dialogue, consultez la fonction membre [DoModal](#domodal) .

> [!NOTE]
>  Le code de conteneur généré par l’Assistant application utilise cette classe.

Pour plus d’informations, consultez la structure [OLEUIINSERTOBJECT](/windows/win32/api/oledlg/ns-oledlg-oleuiinsertobjectw) dans le SDK Windows.

Pour plus d’informations sur les boîtes de dialogue spécifiques à OLE, consultez l’article [boîtes de dialogue dans OLE](../../mfc/dialog-boxes-in-ole.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d’héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

[COleDialog](../../mfc/reference/coledialog-class.md)

`COleInsertDialog`

## <a name="requirements"></a>Spécifications

**En-tête :** afxodlgs. h

##  <a name="coleinsertdialog"></a>COleInsertDialog::COleInsertDialog

Cette fonction construit uniquement un objet `COleInsertDialog`.

```
COleInsertDialog (
    DWORD dwFlags = IOF_SELECTCREATENEW,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>Paramètres

*dwFlags*<br/>
Indicateur de création qui contient un nombre quelconque des valeurs suivantes à associer à l’aide de l’opérateur or au niveau du bit :

- IOF_SHOWHELP spécifie que le bouton aide s’affiche lorsque la boîte de dialogue est appelée.

- IOF_SELECTCREATENEW spécifie que la case d’option créer est sélectionnée initialement lorsque la boîte de dialogue est appelée. Il s’agit de la valeur par défaut et ne peut pas être utilisée avec IOF_SELECTCREATEFROMFILE.

- IOF_SELECTCREATEFROMFILE spécifie que la case d’option créer à partir d’un fichier est sélectionnée initialement lorsque la boîte de dialogue est appelée. Ne peut pas être utilisé avec IOF_SELECTCREATENEW.

- IOF_CHECKLINK spécifie que la case à cocher lien sera activée initialement lorsque la boîte de dialogue sera appelée.

- IOF_DISABLELINK spécifie que la case à cocher Lier est désactivée lorsque la boîte de dialogue est appelée.

- IOF_CHECKDISPLAYASICON spécifie que la case à cocher Afficher sous forme d’icône sera activée initialement, l’icône en cours sera affichée et le bouton changer d’icône sera activé lorsque la boîte de dialogue sera appelée.

- IOF_VERIFYSERVERSEXIST spécifie que la boîte de dialogue doit valider les classes qu’elle ajoute à la zone de liste en veillant à ce que les serveurs spécifiés dans la base de données d’inscription existent avant l’affichage de la boîte de dialogue. La définition de cet indicateur peut nuire considérablement aux performances.

*pParentWnd*<br/>
Pointe vers l’objet de fenêtre parent ou propriétaire (de type `CWnd`) auquel l’objet de boîte de dialogue appartient. Si la valeur est NULL, la fenêtre parente de l’objet Dialog est définie sur la fenêtre d’application principale.

### <a name="remarks"></a>Notes

Pour afficher la boîte de dialogue, appelez la fonction [DoModal](#domodal) .

##  <a name="createitem"></a>COleInsertDialog :: CreateItem

Appelez cette fonction pour créer un objet de type [COleClientItem](../../mfc/reference/coleclientitem-class.md) uniquement si [DoModal](#domodal) retourne IDOK.

```
BOOL CreateItem(COleClientItem* pItem);
```

### <a name="parameters"></a>Paramètres

*pItem*<br/>
Pointe vers l’élément à créer.

### <a name="return-value"></a>Valeur de retour

Différent de zéro si l’élément a été créé ; Sinon, 0.

### <a name="remarks"></a>Notes

Vous devez allouer l’objet `COleClientItem` avant de pouvoir appeler cette fonction.

##  <a name="domodal"></a>COleInsertDialog ::D oModal

Appelez cette fonction pour afficher la boîte de dialogue OLE Insert Object.

```
virtual INT_PTR
    DoModal();

INT_PTR
    DoModal(DWORD  dwFlags);
```

### <a name="parameters"></a>Paramètres

*dwFlags*<br/>
L’une des valeurs suivantes :

`COleInsertDialog::DocObjectsOnly` insère uniquement DocObjects.

`COleInsertDialog::ControlsOnly` insère uniquement des contrôles ActiveX.

Zéro n’insère ni un DocObject, ni un contrôle ActiveX. Cette valeur entraîne la même implémentation que le premier prototype indiqué ci-dessus.

### <a name="return-value"></a>Valeur de retour

État d’achèvement de la boîte de dialogue. L’une des valeurs suivantes :

- IDOK si la boîte de dialogue a été correctement affichée.

- IDCANCEL si l’utilisateur a annulé la boîte de dialogue.

- IDABORT si une erreur s’est produite. Si IDABORT est retourné, appelez la fonction membre [COleDialog :: GetLastError](../../mfc/reference/coledialog-class.md#getlasterror) pour obtenir plus d’informations sur le type d’erreur qui s’est produit. Pour obtenir la liste des erreurs possibles, consultez la fonction [OleUIInsertObject](/windows/win32/api/oledlg/nf-oledlg-oleuiinsertobjectw) dans la SDK Windows.

### <a name="remarks"></a>Notes

Si vous souhaitez initialiser les différents contrôles de boîte de dialogue en définissant les membres de la structure [m_io](#m_io) , vous devez le faire avant d’appeler `DoModal`, mais après la construction de l’objet de boîte de dialogue.

Si `DoModal` retourne IDOK, vous pouvez appeler d’autres fonctions membres pour récupérer les paramètres ou l’entrée d’informations dans la boîte de dialogue par l’utilisateur.

##  <a name="getclassid"></a>COleInsertDialog :: GetClassID

Appelez cette fonction pour que le CLSID soit associé à l’élément sélectionné uniquement si [DoModal](#domodal) retourne IDOK et que le type de sélection est `COleInsertDialog::createNewItem`.

```
REFCLSID GetClassID() const;
```

### <a name="return-value"></a>Valeur de retour

Retourne le CLSID associé à l’élément sélectionné.

### <a name="remarks"></a>Notes

Pour plus d’informations, consultez [clé CLSID](/windows/win32/com/clsid-key-hklm) dans le SDK Windows.

##  <a name="getdrawaspect"></a>COleInsertDialog::GetDrawAspect

Appelez cette fonction pour déterminer si l’utilisateur a choisi d’afficher l’élément sélectionné en tant qu’icône.

```
DVASPECT GetDrawAspect() const;
```

### <a name="return-value"></a>Valeur de retour

Méthode nécessaire pour restituer l’objet.

- DVASPECT_CONTENT retourné si la case à cocher Afficher comme icône n’a pas été activée.

- DVASPECT_ICON retourné si la case à cocher Afficher comme icône a été activée.

### <a name="remarks"></a>Notes

Appelez cette fonction uniquement si [DoModal](#domodal) retourne IDOK.

Pour plus d’informations sur l’aspect du dessin, consultez la rubrique structure de données [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) dans le SDK Windows.

##  <a name="geticonicmetafile"></a>COleInsertDialog::GetIconicMetafile

Appelez cette fonction pour obtenir un handle vers le métafichier qui contient l’aspect sous forme de l’élément sélectionné.

```
HGLOBAL GetIconicMetafile() const;
```

### <a name="return-value"></a>Valeur de retour

Handle du métafichier contenant l’aspect sous forme de l’élément sélectionné, si la case à cocher Afficher comme icône a été activée lorsque la boîte de dialogue a été fermée, en choisissant **OK**. Sinon, NULL.

##  <a name="getpathname"></a>COleInsertDialog::GetPathName

Appelez cette fonction pour obtenir le chemin d’accès complet du fichier sélectionné uniquement si [DoModal](#domodal) retourne IDOK et que le type de sélection n’est pas `COleInsertDialog::createNewItem`.

```
CString GetPathName() const;
```

### <a name="return-value"></a>Valeur de retour

Chemin d’accès complet au fichier sélectionné dans la boîte de dialogue. Si le type de sélection est `createNewItem`, cette fonction retourne un `CString` non significatif en mode mise en sortie ou provoque une assertion en mode débogage.

##  <a name="getselectiontype"></a>COleInsertDialog::GetSelectionType

Appelez cette fonction pour faire en sorte que le type de sélection soit choisi lorsque la boîte de dialogue Insérer un objet a été fermée en choisissant **OK**.

```
UINT GetSelectionType() const;
```

### <a name="return-value"></a>Valeur de retour

Type de sélection effectuée.

### <a name="remarks"></a>Notes

Les valeurs de type de retour sont spécifiées par le type d’énumération `Selection` déclaré dans la classe `COleInsertDialog`.

```
enum Selection {
    createNewItem,
    insertFromFile,
    linkToFile
    };
```

Des descriptions succinctes de ces valeurs sont les suivantes :

- `COleInsertDialog::createNewItem` la case d’option créer un nouveau a été sélectionnée.

- `COleInsertDialog::insertFromFile` la case d’option créer à partir d’un fichier a été sélectionnée et que la case à cocher lien n’a pas été activée.

- `COleInsertDialog::linkToFile` la case d’option créer à partir d’un fichier a été sélectionnée et la case à cocher Lier a été activée.

##  <a name="m_io"></a>COleInsertDialog :: m_io

Structure de type OLEUIINSERTOBJECT utilisée pour contrôler le comportement de la boîte de dialogue Insérer un objet.

```
OLEUIINSERTOBJECT m_io;
```

### <a name="remarks"></a>Notes

Les membres de cette structure peuvent être modifiés soit directement, soit par le biais de fonctions membres.

Pour plus d’informations, consultez la structure [OLEUIINSERTOBJECT](/windows/win32/api/oledlg/ns-oledlg-oleuiinsertobjectw) dans le SDK Windows.

## <a name="see-also"></a>Voir aussi

[Exemple MFC OCLIENT](../../overview/visual-cpp-samples.md)<br/>
[COleDialog, classe](../../mfc/reference/coledialog-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[COleDialog, classe](../../mfc/reference/coledialog-class.md)
