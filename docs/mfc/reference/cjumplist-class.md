---
title: Cjumplist, classe
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
ms.openlocfilehash: 9296912c97b1efb5f7cbd1ed9f769d0222d5f85c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62392568"
---
# <a name="cjumplist-class"></a>Cjumplist, classe

Un `CJumpList` est une liste de raccourcis qui s’affichent lorsque vous cliquez sur une icône dans la barre des tâches.

## <a name="syntax"></a>Syntaxe

```
class CJumpList;
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CJumpList::CJumpList](#cjumplist)|Construit un objet `CJumpList`.|
|[CJumpList::~CJumpList](#_dtorcjumplist)|Détruit un objet `CJumpList`.|

|Nom|Description|
|----------|-----------------|
|[CJumpList::AbortList](#abortlist)|Abandonne une transaction de création de liste sans validation.|
|[CJumpList::AddDestination](#adddestination)|Surchargé. Ajoute la destination à la liste.|
|[CJumpList::AddKnownCategory](#addknowncategory)|Ajoute une catégorie appelée à la liste.|
|[CJumpList::AddTask](#addtask)|Surchargé. Ajoute des éléments à la catégorie de tâches canonique.|
|[CJumpList::AddTasks](#addtasks)|Ajoute des éléments à la catégorie de tâches canonique.|
|[CJumpList::AddTaskSeparator](#addtaskseparator)|Ajoute un séparateur entre les tâches.|
|[CJumpList::ClearAll](#clearall)|Supprime toutes les tâches et destinations qui ont été ajoutées à l’instance actuelle de `CJumpList` jusqu'à présent.|
|[CJumpList::ClearAllDestinations](#clearalldestinations)|Supprime toutes les destinations qui ont été ajoutées à l’instance actuelle de `CJumpList` jusqu'à présent.|
|[CJumpList::CommitList](#commitlist)|Met fin à une transaction de création de la liste et valide de la liste signalée dans le magasin associé (le Registre dans le cas présent).|
|[CJumpList::GetDestinationList](#getdestinationlist)|Récupère un pointeur d’interface à la liste de destination.|
|[CJumpList::GetMaxSlots](#getmaxslots)|Récupère le nombre maximal d’éléments, y compris les en-têtes de catégorie qui peuvent afficher dans le menu de destination de l’application appelante.|
|[CJumpList::GetRemovedItems](#getremoveditems)|Retourne un tableau des éléments qui représentent supprimé des destinations.|
|[CJumpList::InitializeList](#initializelist)|Commence une transaction de création de la liste.|
|[CJumpList::SetAppID](#setappid)|Définit l’ID de modèle d’Application utilisateur pour obtenir la liste qui sera créée.|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CJumpList](../../mfc/reference/cjumplist-class.md)

## <a name="requirements"></a>Configuration requise

**En-tête :** afxadv.h

##  <a name="_dtorcjumplist"></a>  CJumpList::~CJumpList

Détruit un objet `CJumpList`.

```
~CJumpList();
```

##  <a name="abortlist"></a>  CJumpList::AbortList

Abandonne une transaction de création de liste sans validation.

```
void AbortList();
```

### <a name="remarks"></a>Notes

Appel de cette méthode a le même effet que la destruction `CJumpList` sans appeler `CommitList`.

##  <a name="adddestination"></a>  CJumpList::AddDestination

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
Spécifie un nom de catégorie. Si la catégorie spécifiée n’existe pas, il sera créé.

*strDestinationPath*<br/>
Spécifie un chemin d’accès au fichier de destination.

*strCategoryName*<br/>
Spécifie un nom de catégorie. Si la catégorie spécifiée n’existe pas, il sera créé.

*pShellItem*<br/>
Spécifie un élément de l’interpréteur de commandes représentant la destination en cours d’ajout.

*pShellLink*<br/>
Spécifie un lien de l’interpréteur de commandes représentant la destination en cours d’ajout.

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

L’instance de `CJumpList` accumule en interne les destinations ajoutées et puis les valide dans `CommitList`.

##  <a name="addknowncategory"></a>  CJumpList::AddKnownCategory

Ajoute une catégorie appelée à la liste.

```
BOOL AddKnownCategory(KNOWNDESTCATEGORY category);
```

### <a name="parameters"></a>Paramètres

*category*<br/>
Spécifie un type de catégorie connus. Peut être KDC_RECENT ou KDC_KNOWN.

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

Connu les catégories sont les exécutions fréquentes et récents qui nous calculera automatiquement pour chaque application qui utilise `SHAddToRecentDocs` (ou indirectement l’utilise comme l’interpréteur de commandes appellera en nom de l’application dans certains scénarios).

##  <a name="addtask"></a>  CJumpList::AddTask

Ajoute des éléments à la catégorie de tâches canonique.

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
Nom de la tâche qui s’affichera dans la liste de Destination.

*strIconLocation*<br/>
Emplacement de l’icône qui s’affichera dans la liste de Destination ainsi que le titre.

*iIconIndex*<br/>
Index de l’icône.

*pShellLink*<br/>
Lien de shell qui représente une tâche à ajouter.

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

L’instance de `CJumpList` accumule les tâches spécifiées et les ajoute à la liste de Destination pendant `CommitList`. Éléments de tâche seront affiche dans une catégorie en bas du menu de destination de l’application. Cette catégorie est prioritaire sur toutes les autres catégories lorsqu’elle est remplie dans l’interface utilisateur.

##  <a name="addtasks"></a>  CJumpList::AddTasks

Ajoute des éléments à la catégorie de tâches canonique.

```
BOOL AddTasks(IObjectArray* pObjectCollection);
```

### <a name="parameters"></a>Paramètres

*pObjectCollection*<br/>
Une collection de tâches à ajouter.

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

L’instance de CJumpList accumule les tâches spécifiées et les ajoute à la liste de Destination pendant `CommitList`. Éléments de tâche seront affiche dans une catégorie en bas du menu de destination de l’application. Cette catégorie est prioritaire sur toutes les autres catégories lorsqu’elle est remplie dans l’interface utilisateur.

##  <a name="addtaskseparator"></a>  CJumpList::AddTaskSeparator

Ajoute un séparateur entre les tâches.

```
BOOL AddTaskSeparator();
```

### <a name="return-value"></a>Valeur de retour

Différent de zéro si l’opération a réussi, 0 si ce n’est pas.

##  <a name="cjumplist"></a>  CJumpList::CJumpList

Construit un objet `CJumpList`.

```
CJumpList(BOOL bAutoCommit = TRUE);
```

### <a name="parameters"></a>Paramètres

*bAutoCommit*<br/>
Si ce paramètre est FALSE la liste n’est pas automatiquement validée dans le destructeur.

##  <a name="clearall"></a>  CJumpList::ClearAll

Supprime toutes les tâches et destinations qui ont été ajoutées à l’instance actuelle de `CJumpList` jusqu'à présent.

```
void ClearAll();
```

### <a name="remarks"></a>Notes

Cette méthode efface et libère toutes les données et les interfaces internes.

##  <a name="clearalldestinations"></a>  CJumpList::ClearAllDestinations

Supprime toutes les destinations qui ont été ajoutées à l’instance actuelle de CJumpList jusqu'à présent.

```
void ClearAllDestinations();
```

### <a name="remarks"></a>Notes

Appelez cette fonction si vous devez supprimer toutes les destinations qui ont été ajoutées jusqu'à présent dans la session en cours de création de liste de destination et l’ajouter à nouveau les autres destinations. Si le texte interne `ICustomDestinationList` a été initialisé, il reste actif.

##  <a name="commitlist"></a>  CJumpList::CommitList

Met fin à une transaction de création de la liste et valide de la liste signalée dans le magasin associé (le Registre dans le cas présent).

```
BOOL CommitList();
```

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

La validation est atomique. Une erreur est renvoyée si la validation échoue.  Lorsque `CommitList` est appelée, en cours est nettoyée liste d’éléments supprimés. Appel de cette méthode de réinitialise l’objet afin qu’il n’a pas une transaction active de la création de la liste. Pour mettre à jour la liste, `BeginList` doit être appelée à nouveau.

##  <a name="getdestinationlist"></a>  CJumpList::GetDestinationList

Récupère un pointeur d’interface à la liste de destination.

```
ICustomDestinationList* GetDestinationList();
```

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

Si la liste de liens n’a pas été initialisée, ou s’il a été validée ou abandonnée, la valeur retournée sera NULL.

##  <a name="getmaxslots"></a>  CJumpList::GetMaxSlots

Récupère le nombre maximal d’éléments, y compris les en-têtes de catégorie qui peuvent afficher dans le menu de destination de l’application appelante.

```
UINT GetMaxSlots() const;
```

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

Applications peuvent signaler uniquement un nombre d’éléments et les en-têtes de catégorie combinées jusqu'à cette valeur. Si les appels à `AppendCategory`, `AppendKnownCategory`, ou `AddUserTasks` dépasse ce nombre, ils renvoient une erreur.

##  <a name="getremoveditems"></a>  CJumpList::GetRemovedItems

Retourne un tableau des éléments qui représentent supprimé des destinations.

```
IObjectArray* GetRemovedItems();
```

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

Les destinations supprimées sont récupérées lors de l’initialisation de la liste de raccourcis. Lorsque vous générez une nouvelle liste de destination, les applications doivent traiter tout d’abord la liste de destinations supprimé, effacement leurs données de suivi pour tout élément retourné par l’énumérateur de la liste supprimée. Si une application tente de fournir un élément qui vient d’être supprimé dans la transaction en cours l’appel à `BeginList` démarré, l’appel de méthode qui rajouté cet élément échouera, pour vous assurer que les applications sont en respectant la liste supprimée.

##  <a name="initializelist"></a>  CJumpList::InitializeList

Commence une transaction de création de la liste.

```
BOOL InitializeList();
```

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

Vous n’avez pas besoin d’appeler cette méthode explicitement, sauf si vous souhaitez récupérer un pointeur vers `ICustomDestinationList` à l’aide de `GetDestinationList`, le nombre d’emplacements disponibles à l’aide de `GetMaxSlots`, ou une liste d’éléments supprimés à l’aide de `GetRemovedItems`.

##  <a name="setappid"></a>  CJumpList::SetAppID

Définit l’ID de modèle d’Application utilisateur pour obtenir la liste qui sera créée.

```
void SetAppID(LPCTSTR strAppID);
```

### <a name="parameters"></a>Paramètres

*strAppID*<br/>
Chaîne qui spécifie l’ID de modèle d’Application utilisateur.

## <a name="see-also"></a>Voir aussi

[Classes](../../mfc/reference/mfc-classes.md)
