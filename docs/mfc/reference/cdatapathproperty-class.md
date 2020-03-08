---
title: CDataPathProperty, classe
ms.date: 11/04/2016
f1_keywords:
- CDataPathProperty
- AFXCTL/CDataPathProperty
- AFXCTL/CDataPathProperty::CDataPathProperty
- AFXCTL/CDataPathProperty::GetControl
- AFXCTL/CDataPathProperty::GetPath
- AFXCTL/CDataPathProperty::Open
- AFXCTL/CDataPathProperty::ResetData
- AFXCTL/CDataPathProperty::SetControl
- AFXCTL/CDataPathProperty::SetPath
helpviewer_keywords:
- CDataPathProperty [MFC], CDataPathProperty
- CDataPathProperty [MFC], GetControl
- CDataPathProperty [MFC], GetPath
- CDataPathProperty [MFC], Open
- CDataPathProperty [MFC], ResetData
- CDataPathProperty [MFC], SetControl
- CDataPathProperty [MFC], SetPath
ms.assetid: 1f96efdb-54e4-460b-862c-eba5d4103488
ms.openlocfilehash: 89cb8ddcdd42643f52f755516e8845109163c57a
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/06/2020
ms.locfileid: "78890822"
---
# <a name="cdatapathproperty-class"></a>CDataPathProperty, classe

Implémente une propriété de contrôle OLE qui peut être chargée de façon asynchrone.

## <a name="syntax"></a>Syntaxe

```
class CDataPathProperty : public CAsyncMonikerFile
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Name|Description|
|----------|-----------------|
|[CDataPathProperty :: CDataPathProperty](#cdatapathproperty)|Construit un objet `CDataPathProperty`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Name|Description|
|----------|-----------------|
|[CDataPathProperty :: GetControl](#getcontrol)|Récupère le contrôle OLE asynchrone associé à l’objet `CDataPathProperty`.|
|[CDataPathProperty :: GetPath](#getpath)|Récupère le nom de chemin d’accès de la propriété.|
|[CDataPathProperty :: Open](#open)|Lance le chargement de la propriété asynchrone pour le contrôle ActiveX (OLE) associé.|
|[CDataPathProperty :: ResetData](#resetdata)|Appelle `CAsyncMonikerFile::OnDataAvailable` pour notifier au conteneur que les propriétés du contrôle ont changé.|
|[CDataPathProperty :: SetControl](#setcontrol)|Définit le contrôle ActiveX (OLE) asynchrone associé à la propriété.|
|[CDataPathProperty :: SetPath](#setpath)|Définit le chemin d’accès de la propriété.|

## <a name="remarks"></a>Notes

Les propriétés asynchrones sont chargées après le lancement synchrone.

La classe `CDataPathProperty` est dérivée de `CAysncMonikerFile`. Pour implémenter des propriétés asynchrones dans vos contrôles OLE, dérivez une classe de `CDataPathProperty`et remplacez [ondataavailable](../../mfc/reference/casyncmonikerfile-class.md#ondataavailable).

Pour plus d’informations sur l’utilisation des monikers asynchrones et des contrôles ActiveX dans les applications Internet, consultez les articles suivants :

- [Premières étapes Internet : contrôles ActiveX](../../mfc/activex-controls-on-the-internet.md)

- [Premières étapes Internet : monikers asynchrones](../../mfc/asynchronous-monikers-on-the-internet.md)

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CFile](../../mfc/reference/cfile-class.md)

[COleStreamFile](../../mfc/reference/colestreamfile-class.md)

[CMonikerFile](../../mfc/reference/cmonikerfile-class.md)

[CAsyncMonikerFile](../../mfc/reference/casyncmonikerfile-class.md)

`CDataPathProperty`

## <a name="requirements"></a>Spécifications

**En-tête :** afxctl. h

##  <a name="cdatapathproperty"></a>CDataPathProperty :: CDataPathProperty

Construit un objet `CDataPathProperty`.

```
CDataPathProperty(COleControl* pControl = NULL);
CDataPathProperty(LPCTSTR lpszPath, COleControl* pControl = NULL);
```

### <a name="parameters"></a>Paramètres

*pControl*<br/>
Pointeur vers l’objet de contrôle OLE à associer à cet objet `CDataPathProperty`.

*lpszPath*<br/>
Chemin d’accès, qui peut être absolu ou relatif, utilisé pour créer un moniker asynchrone qui référence l’emplacement absolu réel de la propriété. `CDataPathProperty` utilise des URL, et non des noms de fichiers. Si vous souhaitez un objet `CDataPathProperty` pour un fichier, ajoutez des `file://` au chemin d’accès.

### <a name="remarks"></a>Notes

L’objet `COleControl` pointé par *pControl* est utilisé par les `Open` et récupérés par les classes dérivées. Si *pControl* a la valeur null, le contrôle utilisé avec `Open` doit être défini avec `SetControl`. Si *lpszPath* a la valeur null, vous pouvez transmettre le chemin d’accès via `Open` ou le définir avec `SetPath`.

##  <a name="getcontrol"></a>CDataPathProperty :: GetControl

Appelez cette fonction membre pour récupérer l’objet `COleControl` associé à l’objet `CDataPathProperty`.

```
COleControl* GetControl();
```

### <a name="return-value"></a>Valeur de retour

Retourne un pointeur vers le contrôle OLE associé à l’objet `CDataPathProperty`. NULL si le contrôle n’est pas associé.

##  <a name="getpath"></a>CDataPathProperty :: GetPath

Appelez cette fonction membre pour récupérer le chemin d’accès, définir quand l’objet `CDataPathProperty` a été construit, ou spécifié dans `Open`, ou spécifié dans un appel précédent à la fonction membre `SetPath`.

```
CString GetPath() const;
```

### <a name="return-value"></a>Valeur de retour

Retourne le nom de chemin d’accès à la propriété proprement dite. Peut être vide si aucun chemin d’accès n’a été spécifié.

##  <a name="open"></a>CDataPathProperty :: Open

Appelez cette fonction membre pour initier le chargement de la propriété asynchrone du contrôle associé.

```
virtual BOOL Open(
    COleControl* pControl,
    CFileException* pError = NULL);

virtual BOOL Open(
    LPCTSTR lpszPath,
    COleControl* pControl,
    CFileException* pError = NULL);

virtual BOOL Open(
    LPCTSTR lpszPath,
    CFileException* pError = NULL);

virtual BOOL Open(CFileException* pError = NULL);
```

### <a name="parameters"></a>Paramètres

*pControl*<br/>
Pointeur vers l’objet de contrôle OLE à associer à cet objet `CDataPathProperty`.

*pError*<br/>
Pointeur vers une exception de fichier. En cas d’erreur, aura pour valeur la cause.

*lpszPath*<br/>
Chemin d’accès, qui peut être absolu ou relatif, utilisé pour créer un moniker asynchrone qui référence l’emplacement absolu réel de la propriété. `CDataPathProperty` utilise des URL, et non des noms de fichiers. Si vous souhaitez un objet `CDataPathProperty` pour un fichier, ajoutez des `file://` au chemin d’accès.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

La fonction tente d’obtenir l’interface `IBindHost` à partir du contrôle.

Avant d’appeler `Open` sans chemin d’accès, la valeur du chemin d’accès de la propriété doit être définie. Cela peut être fait lorsque l’objet est construit, ou en appelant la fonction membre `SetPath`.

Avant d’appeler `Open` sans contrôle, un contrôle ActiveX (anciennement appelé contrôle OLE) peut être associé à l’objet. Cela peut être fait lorsque l’objet est construit, ou en appelant `SetControl`.

Toutes les surcharges de [CAsyncMonikerFile :: Open](../../mfc/reference/casyncmonikerfile-class.md#open) sont également disponibles à partir de `CDataPathProperty`.

##  <a name="resetdata"></a>CDataPathProperty :: ResetData

Appelez cette fonction pour obtenir `CAsyncMonikerFile::OnDataAvailable` pour notifier au conteneur que les propriétés du contrôle ont changé, et que toutes les informations chargées de façon asynchrone ne sont plus utiles.

```
virtual void ResetData();
```

### <a name="remarks"></a>Notes

L’ouverture doit être redémarrée. Les classes dérivées peuvent substituer cette fonction pour des valeurs par défaut différentes.

##  <a name="setcontrol"></a>CDataPathProperty :: SetControl

Appelez cette fonction membre pour associer un contrôle OLE asynchrone à l’objet `CDataPathProperty`.

```
void SetControl(COleControl* pControl);
```

### <a name="parameters"></a>Paramètres

*pControl*<br/>
Pointeur vers le contrôle OLE asynchrone à associer à la propriété.

##  <a name="setpath"></a>CDataPathProperty :: SetPath

Appelez cette fonction membre pour définir le chemin d’accès de la propriété.

```
void SetPath(LPCTSTR lpszPath);
```

### <a name="parameters"></a>Paramètres

*lpszPath*<br/>
Chemin d’accès, qui peut être absolu ou relatif, à la propriété qui est chargée de façon asynchrone. `CDataPathProperty` utilise des URL, et non des noms de fichiers. Si vous souhaitez un objet `CDataPathProperty` pour un fichier, ajoutez des `file://` au chemin d’accès.

## <a name="see-also"></a>Voir aussi

[Exemple d’image MFC](../../overview/visual-cpp-samples.md)<br/>
[CAsyncMonikerFile, classe](../../mfc/reference/casyncmonikerfile-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CAsyncMonikerFile, classe](../../mfc/reference/casyncmonikerfile-class.md)
