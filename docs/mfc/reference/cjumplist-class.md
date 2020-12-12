---
description: 'En savoir plus sur : classe CJumpList'
title: CJumpList, classe
ms.date: 03/27/2019
f1_keywords:
- CJumpList
- AFXADV/CJumpList
- AFXADV/CJumpList::CJumpList
- AFXADV/CJumpList::AbortList
- AFXADV/CJumpList::AddDestination
- AFXADV/CJumpList::AddKnownCategory
- AFXADV/CJumpList::AddTask
- AFXADV/CJumpList::AddTasks
- AFXADV/CJumpList::AddTaskSeparator
- AFXADV/CJumpList::ClearAll
- AFXADV/CJumpList::ClearAllDestinations
- AFXADV/CJumpList::CommitList
- AFXADV/CJumpList::GetDestinationList
- AFXADV/CJumpList::GetMaxSlots
- AFXADV/CJumpList::GetRemovedItems
- AFXADV/CJumpList::InitializeList
- AFXADV/CJumpList::SetAppID
helpviewer_keywords:
- CJumpList [MFC], CJumpList
- CJumpList [MFC], AbortList
- CJumpList [MFC], AddDestination
- CJumpList [MFC], AddKnownCategory
- CJumpList [MFC], AddTask
- CJumpList [MFC], AddTasks
- CJumpList [MFC], AddTaskSeparator
- CJumpList [MFC], ClearAll
- CJumpList [MFC], ClearAllDestinations
- CJumpList [MFC], CommitList
- CJumpList [MFC], GetDestinationList
- CJumpList [MFC], GetMaxSlots
- CJumpList [MFC], GetRemovedItems
- CJumpList [MFC], InitializeList
- CJumpList [MFC], SetAppID
ms.assetid: d364d27e-f512-4b12-9872-c2a17c78ab1f
ms.openlocfilehash: 07e896c5b3a205a44850d45dcc4876103a48f2fa
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97236904"
---
# <a name="cjumplist-class"></a>CJumpList, classe

Un `CJumpList` est la liste des raccourcis qui s’est révélée lorsque vous cliquez avec le bouton droit sur une icône dans la barre des tâches.

## <a name="syntax"></a>Syntaxe

```
class CJumpList;
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CJumpList::CJumpList](#cjumplist)|Construit un objet `CJumpList`.|
|[CJumpList :: ~ CJumpList](#_dtorcjumplist)|Détruit un objet `CJumpList` .|

|Nom|Description|
|----------|-----------------|
|[CJumpList::AbortList](#abortlist)|Abandonne une transaction de génération de liste sans validation.|
|[CJumpList::AddDestination](#adddestination)|Surchargé. Ajoute la destination à la liste.|
|[CJumpList::AddKnownCategory](#addknowncategory)|Ajoute une catégorie connue à la liste.|
|[CJumpList :: AddTask](#addtask)|Surchargé. Ajoute des éléments à la catégorie de tâches canoniques.|
|[CJumpList::AddTasks](#addtasks)|Ajoute des éléments à la catégorie de tâches canoniques.|
|[CJumpList::AddTaskSeparator](#addtaskseparator)|Ajoute un séparateur entre les tâches.|
|[CJumpList :: ClearAll](#clearall)|Supprime toutes les tâches et destinations qui ont été ajoutées à l’instance actuelle jusqu’à `CJumpList` présent.|
|[CJumpList::ClearAllDestinations](#clearalldestinations)|Supprime toutes les destinations qui ont été ajoutées à l’instance actuelle jusqu’à `CJumpList` présent.|
|[CJumpList::CommitList](#commitlist)|Termine une transaction de génération de liste et valide la liste signalée dans le magasin associé (le registre dans le cas présent).|
|[CJumpList::GetDestinationList](#getdestinationlist)|Récupère un pointeur d’interface vers une liste de destination.|
|[CJumpList::GetMaxSlots](#getmaxslots)|Récupère le nombre maximal d’éléments, y compris les en-têtes de catégorie qui peuvent s’afficher dans le menu de destination de l’application appelante.|
|[CJumpList::GetRemovedItems](#getremoveditems)|Retourne un tableau d’éléments qui représentent les destinations supprimées.|
|[CJumpList::InitializeList](#initializelist)|Commence une transaction de génération de liste.|
|[CJumpList::SetAppID](#setappid)|Définit l’ID du modèle utilisateur de l’application pour la liste qui sera générée.|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CJumpList](../../mfc/reference/cjumplist-class.md)

## <a name="requirements"></a>Spécifications

**En-tête :** afxadv. h

## <a name="cjumplistcjumplist"></a><a name="_dtorcjumplist"></a> CJumpList :: ~ CJumpList

Détruit un objet `CJumpList` .

```
~CJumpList();
```

## <a name="cjumplistabortlist"></a><a name="abortlist"></a> CJumpList::AbortList

Abandonne une transaction de génération de liste sans validation.

```cpp
void AbortList();
```

### <a name="remarks"></a>Notes

L’appel de cette méthode a le même effet que la destruction `CJumpList` sans appeler `CommitList` .

## <a name="cjumplistadddestination"></a><a name="adddestination"></a> CJumpList::AddDestination

Ajoute la destination à la liste.

```
BOOL AddDestination(
    LPCTSTR lpcszCategoryName,
    LPCTSTR strDestinationPath);

BOOL AddDestination(
    LPCTSTR strCategoryName,
    IShellItem* pShellItem);

BOOL AddDestination(
    LPCTSTR strCategoryName,
    IShellLink* pShellLink);
```

### <a name="parameters"></a>Paramètres

*lpcszCategoryName*<br/>
Spécifie un nom de catégorie. Si la catégorie spécifiée n’existe pas, elle est créée.

*strDestinationPath*<br/>
Spécifie un chemin d’accès au fichier de destination.

*strCategoryName*<br/>
Spécifie un nom de catégorie. Si la catégorie spécifiée n’existe pas, elle est créée.

*pShellItem*<br/>
Spécifie un élément de Shell représentant la destination ajoutée.

*pShellLink*<br/>
Spécifie un lien d’interpréteur de commandes représentant la destination ajoutée.

### <a name="return-value"></a>Valeur renvoyée

### <a name="remarks"></a>Notes

L’instance de `CJumpList` accumule en interne les destinations ajoutées, puis les valide dans `CommitList` .

## <a name="cjumplistaddknowncategory"></a><a name="addknowncategory"></a> CJumpList::AddKnownCategory

Ajoute une catégorie connue à la liste.

```
BOOL AddKnownCategory(KNOWNDESTCATEGORY category);
```

### <a name="parameters"></a>Paramètres

*category*<br/>
Spécifie un type de catégorie connu. Il peut s’agir de KDC_RECENT ou KDC_KNOWN.

### <a name="return-value"></a>Valeur renvoyée

### <a name="remarks"></a>Notes

Les catégories connues sont les catégories fréquentes et récentes que nous calculerons automatiquement pour chaque application qui utilise `SHAddToRecentDocs` (ou qui l’utilise indirectement, car l’interpréteur de commandes l’appellera au nom de l’application dans certains scénarios).

## <a name="cjumplistaddtask"></a><a name="addtask"></a> CJumpList :: AddTask

Ajoute des éléments à la catégorie de tâches canoniques.

```
BOOL AddTask(
    LPCTSTR strTargetExecutablePath,
    LPCTSTR strCommandLineArgs,
    LPCTSTR strTitle,
    LPCTSTR strIconLocation,
    int iIconIndex);

BOOL AddTask(IShellLink* pShellLink);
```

### <a name="parameters"></a>Paramètres

*strTargetExecutablePath*<br/>
Spécifie le chemin d’accès de la tâche cible.

*strCommandLineArgs*<br/>
Spécifie les arguments de ligne de commande de l’exécutable spécifié par *strTargetExecutablePath*.

*strTitle*<br/>
Nom de la tâche qui s’affichera dans la liste de destination.

*strIconLocation*<br/>
Emplacement de l’icône qui s’affichera dans la liste de destination avec le titre.

*iIconIndex*<br/>
Index d’icône.

*pShellLink*<br/>
Lien d’interpréteur de commandes qui représente une tâche à ajouter.

### <a name="return-value"></a>Valeur renvoyée

### <a name="remarks"></a>Notes

L’instance de `CJumpList` accumule les tâches spécifiées et les ajoute à la liste de destination pendant `CommitList` . Les éléments de tâche s’affichent dans une catégorie au bas du menu destination de l’application. Cette catégorie est prioritaire sur toutes les autres catégories lorsqu’elle est remplie dans l’interface utilisateur.

## <a name="cjumplistaddtasks"></a><a name="addtasks"></a> CJumpList::AddTasks

Ajoute des éléments à la catégorie de tâches canoniques.

```
BOOL AddTasks(IObjectArray* pObjectCollection);
```

### <a name="parameters"></a>Paramètres

*pObjectCollection*<br/>
Collection de tâches à ajouter.

### <a name="return-value"></a>Valeur renvoyée

### <a name="remarks"></a>Notes

L’instance de CJumpList accumule les tâches spécifiées et les ajoute à la liste de destination pendant `CommitList` . Les éléments de tâche s’affichent dans une catégorie au bas du menu destination de l’application. Cette catégorie est prioritaire sur toutes les autres catégories lorsqu’elle est remplie dans l’interface utilisateur.

## <a name="cjumplistaddtaskseparator"></a><a name="addtaskseparator"></a> CJumpList::AddTaskSeparator

Ajoute un séparateur entre les tâches.

```
BOOL AddTaskSeparator();
```

### <a name="return-value"></a>Valeur renvoyée

Valeur différente de zéro si elle réussit, 0 dans le cas contraire.

## <a name="cjumplistcjumplist"></a><a name="cjumplist"></a> CJumpList::CJumpList

Construit un objet `CJumpList`.

```
CJumpList(BOOL bAutoCommit = TRUE);
```

### <a name="parameters"></a>Paramètres

*bAutoCommit*<br/>
Si ce paramètre a la valeur FALSe, la liste n’est pas validée automatiquement dans le destructeur.

## <a name="cjumplistclearall"></a><a name="clearall"></a> CJumpList :: ClearAll

Supprime toutes les tâches et destinations qui ont été ajoutées à l’instance actuelle jusqu’à `CJumpList` présent.

```cpp
void ClearAll();
```

### <a name="remarks"></a>Notes

Cette méthode efface et libère toutes les données et les interfaces internes.

## <a name="cjumplistclearalldestinations"></a><a name="clearalldestinations"></a> CJumpList::ClearAllDestinations

Supprime jusqu’à présent toutes les destinations qui ont été ajoutées à l’instance actuelle de CJumpList.

```cpp
void ClearAllDestinations();
```

### <a name="remarks"></a>Notes

Appelez cette fonction si vous devez supprimer toutes les destinations qui ont été ajoutées jusqu’à présent dans la liste de la session de destination active et ajouter d’autres destinations. Si le interne `ICustomDestinationList` a été initialisé, son état reste actif.

## <a name="cjumplistcommitlist"></a><a name="commitlist"></a> CJumpList::CommitList

Termine une transaction de génération de liste et valide la liste signalée dans le magasin associé (le registre dans le cas présent).

```
BOOL CommitList();
```

### <a name="return-value"></a>Valeur renvoyée

### <a name="remarks"></a>Notes

La validation est atomique. Une erreur est renvoyée en cas d’échec de la validation.  Lorsque `CommitList` est appelé, la liste actuelle des éléments supprimés est nettoyée. L’appel de cette méthode réinitialise l’objet afin qu’il n’ait pas de transaction de construction de liste active. Pour mettre à jour la liste, `BeginList` doit être appelé à nouveau.

## <a name="cjumplistgetdestinationlist"></a><a name="getdestinationlist"></a> CJumpList::GetDestinationList

Récupère un pointeur d’interface vers une liste de destination.

```
ICustomDestinationList* GetDestinationList();
```

### <a name="return-value"></a>Valeur renvoyée

### <a name="remarks"></a>Notes

Si la liste de raccourcis n’a pas été initialisée ou a été validée ou abandonnée, la valeur retournée est NULL.

## <a name="cjumplistgetmaxslots"></a><a name="getmaxslots"></a> CJumpList::GetMaxSlots

Récupère le nombre maximal d’éléments, y compris les en-têtes de catégorie qui peuvent s’afficher dans le menu de destination de l’application appelante.

```
UINT GetMaxSlots() const;
```

### <a name="return-value"></a>Valeur renvoyée

### <a name="remarks"></a>Notes

Les applications peuvent uniquement signaler un nombre d’éléments et d’en-têtes de catégorie combinés jusqu’à cette valeur. Si les appels à `AppendCategory` , `AppendKnownCategory` ou `AddUserTasks` dépassent ce nombre, ils retournent l’erreur.

## <a name="cjumplistgetremoveditems"></a><a name="getremoveditems"></a> CJumpList::GetRemovedItems

Retourne un tableau d’éléments qui représentent les destinations supprimées.

```
IObjectArray* GetRemovedItems();
```

### <a name="return-value"></a>Valeur renvoyée

### <a name="remarks"></a>Notes

Les destinations supprimées sont récupérées pendant l’initialisation de la liste de raccourcis. Lors de la génération d’une nouvelle liste de destination, les applications sont censées traiter d’abord la liste des destinations supprimées, en effaçant les données de suivi pour tout élément retourné par l’énumérateur de liste supprimé. Si une application tente de fournir un élément qui vient d’être supprimé dans la transaction que l’appel en cours a `BeginList` démarré, l’appel de méthode qui a rajouté cet élément échouera pour s’assurer que les applications respectent la liste supprimée.

## <a name="cjumplistinitializelist"></a><a name="initializelist"></a> CJumpList::InitializeList

Commence une transaction de génération de liste.

```
BOOL InitializeList();
```

### <a name="return-value"></a>Valeur renvoyée

### <a name="remarks"></a>Notes

Vous n’avez pas besoin d’appeler cette méthode explicitement, sauf si vous souhaitez récupérer un pointeur vers à `ICustomDestinationList` l’aide de `GetDestinationList` , le nombre d’emplacements disponibles à l’aide de `GetMaxSlots` ou la liste des éléments supprimés à l’aide de `GetRemovedItems` .

## <a name="cjumplistsetappid"></a><a name="setappid"></a> CJumpList::SetAppID

Définit l’ID du modèle utilisateur de l’application pour la liste qui sera générée.

```cpp
void SetAppID(LPCTSTR strAppID);
```

### <a name="parameters"></a>Paramètres

*strAppID*<br/>
Chaîne qui spécifie l’ID du modèle utilisateur de l’application.

## <a name="see-also"></a>Voir aussi

[Classes](../../mfc/reference/mfc-classes.md)
