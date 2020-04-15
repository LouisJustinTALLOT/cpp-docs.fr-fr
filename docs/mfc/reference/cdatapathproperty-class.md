---
title: Classe CDataPathProperty
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
ms.openlocfilehash: e96106dcd6f496c6cc99c9d72d86052547b6d06b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376463"
---
# <a name="cdatapathproperty-class"></a>Classe CDataPathProperty

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
|[CDataPathProperty::GetControl](#getcontrol)|Récupère le contrôle asynchrone OLE `CDataPathProperty` associé à l’objet.|
|[CDataPathProperty::GetPath](#getpath)|Récupère le nom de la propriété.|
|[CDataPathProperty::Ouvert](#open)|Initie le chargement de la propriété asynchrone pour le contrôle ActifX (OLE) associé.|
|[CDataPathProperty::ResetData](#resetdata)|Appels `CAsyncMonikerFile::OnDataAvailable` pour aviser le conteneur que les propriétés de contrôle ont changé.|
|[CDataPathProperty::SetControl](#setcontrol)|Définit le contrôle asynchrone ActiveX (OLE) associé à la propriété.|
|[CDataPathProperty::SetPath](#setpath)|Définit le nom de la propriété.|

## <a name="remarks"></a>Notes

Les propriétés asynchrones sont chargées après le lancement synchrone.

La `CDataPathProperty` classe est `CAysncMonikerFile`dérivée de . Pour implémenter des propriétés asynchrones `CDataPathProperty`dans vos commandes OLE, tirer une classe de , et remplacer [OnDataAvailable](../../mfc/reference/casyncmonikerfile-class.md#ondataavailable).

Pour plus d’informations sur la façon d’utiliser les surnoms asynchrones et les contrôles ActiveX dans les applications Internet, voir les articles suivants:

- [Les premières étapes d’Internet : contrôles ActiveX](../../mfc/activex-controls-on-the-internet.md)

- [Les premiers pas d’Internet : des monikers asynchrones](../../mfc/asynchronous-monikers-on-the-internet.md)

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CFile](../../mfc/reference/cfile-class.md)

[COleStreamFile](../../mfc/reference/colestreamfile-class.md)

[CMonikerFile](../../mfc/reference/cmonikerfile-class.md)

[CAsyncMonikerFile](../../mfc/reference/casyncmonikerfile-class.md)

`CDataPathProperty`

## <a name="requirements"></a>Spécifications

**En-tête:** afxctl.h

## <a name="cdatapathpropertycdatapathproperty"></a><a name="cdatapathproperty"></a>CDataPathProperty::CDataPathProperty

Construit un objet `CDataPathProperty`.

```
CDataPathProperty(COleControl* pControl = NULL);
CDataPathProperty(LPCTSTR lpszPath, COleControl* pControl = NULL);
```

### <a name="parameters"></a>Paramètres

*pControl*<br/>
Un pointeur à l’objet de `CDataPathProperty` contrôle OLE à associer à cet objet.

*lpszPath*<br/>
Le chemin, qui peut être absolu ou relatif, utilisé pour créer un surnom asynchrone qui fait référence à l’emplacement absolu réel de la propriété. `CDataPathProperty`utilise des URL, pas des noms de fichiers. Si vous `CDataPathProperty` voulez un objet pour `file://` un fichier, prévoyez-vous sur le chemin.

### <a name="remarks"></a>Notes

L’objet `COleControl` pointé par *pControl* est utilisé et `Open` récupéré par des classes dérivées. Si *pControl* est NULL, `Open` le contrôle `SetControl`utilisé avec doit être réglé avec . Si *lpszPath* est NULL, vous pouvez `Open` passer dans `SetPath`le chemin à travers ou le régler avec .

## <a name="cdatapathpropertygetcontrol"></a><a name="getcontrol"></a>CDataPathProperty::GetControl

Appelez cette fonction de `COleControl` membre pour `CDataPathProperty` récupérer l’objet associé à l’objet.

```
COleControl* GetControl();
```

### <a name="return-value"></a>Valeur de retour

Retourne un pointeur au contrôle `CDataPathProperty` OLE associé à l’objet. NULL si ce n’est le contrôle est associé.

## <a name="cdatapathpropertygetpath"></a><a name="getpath"></a>CDataPathProperty::GetPath

Appelez cette fonction de membre pour `CDataPathProperty` récupérer le chemin, `Open`définir lorsque l’objet `SetPath` a été construit, ou spécifié dans , ou spécifié dans un appel précédent à la fonction membre.

```
CString GetPath() const;
```

### <a name="return-value"></a>Valeur de retour

Retourne le nom de chemin à la propriété elle-même. Peut être vide si aucun chemin n’a été spécifié.

## <a name="cdatapathpropertyopen"></a><a name="open"></a>CDataPathProperty::Ouvert

Appelez cette fonction de membre pour initier le chargement de la propriété asynchrone pour le contrôle associé.

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
Un pointeur à l’objet de `CDataPathProperty` contrôle OLE à associer à cet objet.

*Perror*<br/>
Un pointeur à une exception de fichier. En cas d’erreur, sera réglé à la cause.

*lpszPath*<br/>
Le chemin, qui peut être absolu ou relatif, utilisé pour créer un surnom asynchrone qui fait référence à l’emplacement absolu réel de la propriété. `CDataPathProperty`utilise des URL, pas des noms de fichiers. Si vous `CDataPathProperty` voulez un objet pour `file://` un fichier, prévoyez-vous sur le chemin.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

La fonction tente `IBindHost` d’obtenir l’interface du contrôle.

Avant `Open` d’appeler sans chemin, la valeur du chemin de la propriété doit être définie. Cela peut être fait lorsque l’objet `SetPath` est construit, ou en appelant la fonction membre.

Avant `Open` d’appeler sans contrôle, un contrôle ActiveX (anciennement connu sous le nom de contrôle OLE) peut être associé à l’objet. Cela peut être fait lorsque l’objet `SetControl`est construit, ou en appelant .

Toutes les surcharges de [CAsyncMonikerFile::Open](../../mfc/reference/casyncmonikerfile-class.md#open) sont également disponibles à partir de `CDataPathProperty`.

## <a name="cdatapathpropertyresetdata"></a><a name="resetdata"></a>CDataPathProperty::ResetData

Appelez cette fonction `CAsyncMonikerFile::OnDataAvailable` pour obtenir d’aviser le conteneur que les propriétés de contrôle ont changé, et toutes les informations chargées asynchronement n’est plus utile.

```
virtual void ResetData();
```

### <a name="remarks"></a>Notes

L’ouverture doit être redémarrée. Les classes dérivées peuvent remplacer cette fonction pour différents défauts.

## <a name="cdatapathpropertysetcontrol"></a><a name="setcontrol"></a>CDataPathProperty::SetControl

Appelez cette fonction de membre pour associer un contrôle `CDataPathProperty` asynchrone OLE avec l’objet.

```
void SetControl(COleControl* pControl);
```

### <a name="parameters"></a>Paramètres

*pControl*<br/>
Un pointeur au contrôle asynchrone OLE à associer à la propriété.

## <a name="cdatapathpropertysetpath"></a><a name="setpath"></a>CDataPathProperty::SetPath

Appelez cette fonction de membre pour définir le nom de la propriété.

```
void SetPath(LPCTSTR lpszPath);
```

### <a name="parameters"></a>Paramètres

*lpszPath*<br/>
Un chemin, qui peut être absolu ou relatif, à la propriété étant chargée asynchrone. `CDataPathProperty`utilise des URL, pas des noms de fichiers. Si vous `CDataPathProperty` voulez un objet pour `file://` un fichier, prévoyez-vous sur le chemin.

## <a name="see-also"></a>Voir aussi

[Image d’échantillon de MFC](../../overview/visual-cpp-samples.md)<br/>
[Classe CAsyncMonikerFile](../../mfc/reference/casyncmonikerfile-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classe CAsyncMonikerFile](../../mfc/reference/casyncmonikerfile-class.md)
