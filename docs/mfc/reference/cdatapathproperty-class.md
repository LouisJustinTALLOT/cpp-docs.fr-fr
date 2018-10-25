---
title: CDataPathProperty, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- CDataPathProperty [MFC], CDataPathProperty
- CDataPathProperty [MFC], GetControl
- CDataPathProperty [MFC], GetPath
- CDataPathProperty [MFC], Open
- CDataPathProperty [MFC], ResetData
- CDataPathProperty [MFC], SetControl
- CDataPathProperty [MFC], SetPath
ms.assetid: 1f96efdb-54e4-460b-862c-eba5d4103488
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e38595c5c3912fe7558b1279bbc68e7fd60df681
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50074330"
---
# <a name="cdatapathproperty-class"></a>CDataPathProperty, classe

Implémente une propriété de contrôle OLE qui peut être chargée de façon asynchrone.

## <a name="syntax"></a>Syntaxe

```
class CDataPathProperty : public CAsyncMonikerFile
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CDataPathProperty::CDataPathProperty](#cdatapathproperty)|Construit un objet `CDataPathProperty`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CDataPathProperty::GetControl](#getcontrol)|Récupère le contrôle OLE asynchrone associé le `CDataPathProperty` objet.|
|[CDataPathProperty::GetPath](#getpath)|Récupère le chemin d’accès de la propriété.|
|[CDataPathProperty::Open](#open)|Démarre le chargement de la propriété asynchrone pour le contrôle ActiveX (OLE) associé.|
|[CDataPathProperty::ResetData](#resetdata)|Appels `CAsyncMonikerFile::OnDataAvailable` pour notifier au conteneur que les propriétés de contrôle ont changé.|
|[CDataPathProperty::SetControl](#setcontrol)|Définit le contrôle ActiveX (OLE) asynchrone associé à la propriété.|
|[CDataPathProperty::SetPath](#setpath)|Définit le chemin d’accès de la propriété.|

## <a name="remarks"></a>Notes

Les propriétés asynchrones sont chargées après le lancement synchrone.

La classe `CDataPathProperty` est dérivée de `CAysncMonikerFile`. Pour implémenter des propriétés asynchrones dans vos contrôles OLE, dérivez une classe de `CDataPathProperty`et remplacer [OnDataAvailable](../../mfc/reference/casyncmonikerfile-class.md#ondataavailable).

Pour plus d’informations sur l’utilisation des monikers asynchrones et des contrôles ActiveX dans les applications Internet, consultez les articles suivants :

- [Internet premières étapes : Les contrôles ActiveX](../../mfc/activex-controls-on-the-internet.md)

- [Internet premières étapes : Monikers asynchrones](../../mfc/asynchronous-monikers-on-the-internet.md)

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CFile](../../mfc/reference/cfile-class.md)

[COleStreamFile](../../mfc/reference/colestreamfile-class.md)

[CMonikerFile](../../mfc/reference/cmonikerfile-class.md)

[CAsyncMonikerFile](../../mfc/reference/casyncmonikerfile-class.md)

`CDataPathProperty`

## <a name="requirements"></a>Configuration requise

**En-tête :** afxctl.h

##  <a name="cdatapathproperty"></a>  CDataPathProperty::CDataPathProperty

Construit un objet `CDataPathProperty`.

```
CDataPathProperty(COleControl* pControl = NULL);
CDataPathProperty(LPCTSTR lpszPath, COleControl* pControl = NULL);
```

### <a name="parameters"></a>Paramètres

*pControl*<br/>
Un pointeur vers l’objet de contrôle OLE à associer à ce `CDataPathProperty` objet.

*lpszPath*<br/>
Le chemin d’accès, qui peut être absolu ou relatif, utilisé pour créer un moniker asynchrone qui fait référence à l’emplacement absolu réel de la propriété. `CDataPathProperty` utilise des URL, pas les noms de fichiers. Si vous souhaitez un `CDataPathProperty` de l’objet d’un fichier, ajouter `file://` pour le chemin d’accès.

### <a name="remarks"></a>Notes

Le `COleControl` objet vers lequel pointe *pControl* est utilisé par `Open` et récupérées par les classes dérivées. Si *pControl* est NULL, le contrôle utilisé avec `Open` doit être défini avec `SetControl`. Si *lpszPath* est NULL, vous pouvez passer dans le chemin d’accès via `Open` ou définissez-la avec `SetPath`.

##  <a name="getcontrol"></a>  CDataPathProperty::GetControl

Appelez cette fonction membre pour récupérer le `COleControl` objet associé à la `CDataPathProperty` objet.

```
COleControl* GetControl();
```

### <a name="return-value"></a>Valeur de retour

Retourne un pointeur vers le contrôle OLE associé le `CDataPathProperty` objet. NULL si n’est pas le contrôle est associé.

##  <a name="getpath"></a>  CDataPathProperty::GetPath

Appelez cette fonction membre pour récupérer le chemin d’accès, définie lorsque le `CDataPathProperty` objet a été construit, ou spécifié dans `Open`, ou spécifiée dans un appel précédent à la `SetPath` fonction membre.

```
CString GetPath() const;
```

### <a name="return-value"></a>Valeur de retour

Retourne le chemin d’accès à la propriété proprement dite. Peut être vide si aucun chemin d’accès n’a été spécifié.

##  <a name="open"></a>  CDataPathProperty::Open

Appelez cette fonction membre pour lancer le chargement de la propriété asynchrone pour le contrôle associé.

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
Un pointeur vers l’objet de contrôle OLE à associer à ce `CDataPathProperty` objet.

*pError*<br/>
Pointeur vers une exception de fichier. En cas d’erreur, est défini à la cause.

*lpszPath*<br/>
Le chemin d’accès, qui peut être absolu ou relatif, utilisé pour créer un moniker asynchrone qui fait référence à l’emplacement absolu réel de la propriété. `CDataPathProperty` utilise des URL, pas les noms de fichiers. Si vous souhaitez un `CDataPathProperty` de l’objet d’un fichier, ajouter `file://` pour le chemin d’accès.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

La fonction tente d’obtenir le `IBindHost` interface à partir du contrôle.

Avant d’appeler `Open` sans un chemin d’accès, la valeur de chemin d’accès de la propriété doit être définie. Cela est possible lorsque l’objet est construit, ou en appelant le `SetPath` fonction membre.

Avant d’appeler `Open` sans un contrôle, un contrôle ActiveX (anciennement appelé un contrôle OLE) peut être associé à l’objet. Cela est possible lorsque l’objet est construit, ou en appelant `SetControl`.

Toutes les surcharges de [CAsyncMonikerFile::Open](../../mfc/reference/casyncmonikerfile-class.md#open) sont également disponibles à partir de `CDataPathProperty`.

##  <a name="resetdata"></a>  CDataPathProperty::ResetData

Appelez cette fonction pour obtenir `CAsyncMonikerFile::OnDataAvailable` pour notifier au conteneur que les propriétés de contrôle ont changé, et toutes les informations chargées de façon asynchrone ne sont plus utiles.

```
virtual void ResetData();
```

### <a name="remarks"></a>Notes

Ouverture doit être redémarré. Classes dérivées peuvent substituer cette fonction pour différentes valeurs par défaut.

##  <a name="setcontrol"></a>  CDataPathProperty::SetControl

Appelez cette fonction membre pour associer un contrôle OLE asynchrone avec le `CDataPathProperty` objet.

```
void SetControl(COleControl* pControl);
```

### <a name="parameters"></a>Paramètres

*pControl*<br/>
Pointeur vers le contrôle OLE asynchrone à associer à la propriété.

##  <a name="setpath"></a>  CDataPathProperty::SetPath

Appelez cette fonction membre pour définir le chemin d’accès de la propriété.

```
void SetPath(LPCTSTR lpszPath);
```

### <a name="parameters"></a>Paramètres

*lpszPath*<br/>
Un chemin d’accès, qui peut être absolu ou relatif à la propriété qui est chargée de façon asynchrone. `CDataPathProperty` utilise des URL, pas les noms de fichiers. Si vous souhaitez un `CDataPathProperty` de l’objet d’un fichier, ajouter `file://` pour le chemin d’accès.

## <a name="see-also"></a>Voir aussi

[Image d’exemple MFC](../../visual-cpp-samples.md)<br/>
[CAsyncMonikerFile, classe](../../mfc/reference/casyncmonikerfile-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CAsyncMonikerFile, classe](../../mfc/reference/casyncmonikerfile-class.md)
