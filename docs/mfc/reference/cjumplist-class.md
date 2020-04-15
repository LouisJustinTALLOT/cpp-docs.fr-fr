---
title: Classe CJumpList
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
ms.openlocfilehash: 98d6bec3d33c9060ebb741111dff793f64cc7cb0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372332"
---
# <a name="cjumplist-class"></a>Classe CJumpList

R `CJumpList` est la liste des raccourcis révélés lorsque vous cliquez à droite sur une icône dans la barre de tâches.

## <a name="syntax"></a>Syntaxe

```
class CJumpList;
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CJumpList::CJumpList](#cjumplist)|Construit un objet `CJumpList`.|
|[CJumpList::CJumpList](#_dtorcjumplist)|Détruit un objet `CJumpList` .|

|Nom|Description|
|----------|-----------------|
|[CJumpList::AbortList](#abortlist)|Annule une transaction de dressage de liste sans s’engager.|
|[CJumpList::AddDestination](#adddestination)|Surchargé. Ajoute la destination à la liste.|
|[CJumpList::AddKnownCategory](#addknowncategory)|Annexe d’une catégorie connue à la liste.|
|[CJumpList::AddTask](#addtask)|Surchargé. Ajoute des éléments à la catégorie des tâches canoniques.|
|[CJumpList::AddTasks](#addtasks)|Ajoute des éléments à la catégorie des tâches canoniques.|
|[CJumpList::AddTaskSeparator](#addtaskseparator)|Ajoute un séparateur entre les tâches.|
|[CJumpList::ClearAll](#clearall)|Supprime toutes les tâches et destinations qui ont `CJumpList` été ajoutées à l’instance actuelle de jusqu’à présent.|
|[CJumpList::ClearAllDestinations](#clearalldestinations)|Supprime toutes les destinations qui ont été `CJumpList` ajoutées à l’instance actuelle de jusqu’à présent.|
|[CJumpList::CommitList](#commitlist)|Termine une transaction de dresseurs de listes et engage la liste indiquée au magasin associé (le registre dans ce cas.)|
|[CJumpList::GetDestinationList](#getdestinationlist)|Récupère un pointeur d’interface vers la liste de destination.|
|[CJumpList::GetMaxSlots](#getmaxslots)|Récupère le nombre maximum d’éléments, y compris les en-têtes de catégorie qui peuvent s’afficher dans le menu de destination de l’application d’appel.|
|[CJumpList:GetRemovedItems](#getremoveditems)|Retourne la gamme d’articles qui représentent les destinations supprimées.|
|[CJumpList::InitializeList](#initializelist)|Commence une transaction de dresse de liste.|
|[CJumpList::SetAppID](#setappid)|Définit l’ID modèle d’utilisateur d’application pour la liste qui sera construite.|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CJumpList](../../mfc/reference/cjumplist-class.md)

## <a name="requirements"></a>Spécifications

**En-tête:** afxadv.h

## <a name="cjumplistcjumplist"></a><a name="_dtorcjumplist"></a>CJumpList::CJumpList

Détruit un objet `CJumpList` .

```
~CJumpList();
```

## <a name="cjumplistabortlist"></a><a name="abortlist"></a>CJumpList::AbortList

Annule une transaction de dressage de liste sans s’engager.

```
void AbortList();
```

### <a name="remarks"></a>Notes

Appeler cette méthode a le `CJumpList` même `CommitList`effet que de détruire sans appeler .

## <a name="cjumplistadddestination"></a><a name="adddestination"></a>CJumpList::AddDestination

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
Spécifie un nom de catégorie. Si la catégorie spécifiée n’existe pas, elle sera créée.

*strDestinationPath (en)*<br/>
Spécifie un fichier de destination vers le chemin.

*strCategoryName (en)*<br/>
Spécifie un nom de catégorie. Si la catégorie spécifiée n’existe pas, elle sera créée.

*pShellItem*<br/>
Spécifie un élément Shell représentant la destination ajoutée.

*pShellLink (en)*<br/>
Spécifie un lien Shell représentant la destination ajoutée.

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

L’exemple `CJumpList` de l’interne accumule les destinations ajoutées et les engage ensuite dans `CommitList`.

## <a name="cjumplistaddknowncategory"></a><a name="addknowncategory"></a>CJumpList::AddKnownCategory

Annexe d’une catégorie connue à la liste.

```
BOOL AddKnownCategory(KNOWNDESTCATEGORY category);
```

### <a name="parameters"></a>Paramètres

*Catégorie*<br/>
Spécifie un type de catégorie connu. Peut être KDC_RECENT, ou KDC_KNOWN.

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

Les catégories connues sont les catégories fréquentes et récentes `SHAddToRecentDocs` que nous calculerons automatiquement pour chaque application qui l’utilise (ou l’utilise indirectement comme la coquille l’appellera au nom de l’application dans certains scénarios).

## <a name="cjumplistaddtask"></a><a name="addtask"></a>CJumpList::AddTask

Ajoute des éléments à la catégorie des tâches canoniques.

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
Spécifie le chemin de tâche cible.

*strCommandLineArgs (en)*<br/>
Spécifie les arguments de la ligne de commande de l’exécutable spécifié par *strTargetExecutablePath*.

*strTitle (strTitle)*<br/>
Nom de tâche qui sera affiché dans la liste de destination.

*strIconLocation*<br/>
Emplacement de l’icône qui sera affichée dans la liste de destination avec le titre.

*iIconIndex*<br/>
Index d’icône.

*pShellLink (en)*<br/>
Shell Link qui représente une tâche à ajouter.

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

L’exemple `CJumpList` des tâches spécifiées accumule et `CommitList`les ajoute à la liste de destination pendant . Les éléments de tâche apparaîtront dans une catégorie au bas du menu de destination de l’application. Cette catégorie a préséance sur toutes les autres catégories lorsqu’elle est remplie dans l’interface utilisateur.

## <a name="cjumplistaddtasks"></a><a name="addtasks"></a>CJumpList::AddTasks

Ajoute des éléments à la catégorie des tâches canoniques.

```
BOOL AddTasks(IObjectArray* pObjectCollection);
```

### <a name="parameters"></a>Paramètres

*pObjectCollection*<br/>
Une collection de tâches à ajouter.

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

L’exemple de CJumpList accumule les tâches spécifiées `CommitList`et les ajoute à la liste de destination pendant . Les éléments de tâche apparaîtront dans une catégorie au bas du menu de destination de l’application. Cette catégorie a préséance sur toutes les autres catégories lorsqu’elle est remplie dans l’interface utilisateur.

## <a name="cjumplistaddtaskseparator"></a><a name="addtaskseparator"></a>CJumpList::AddTaskSeparator

Ajoute un séparateur entre les tâches.

```
BOOL AddTaskSeparator();
```

### <a name="return-value"></a>Valeur de retour

Nonzero si elle est réussie, 0 si elle n’est pas.

## <a name="cjumplistcjumplist"></a><a name="cjumplist"></a>CJumpList::CJumpList

Construit un objet `CJumpList`.

```
CJumpList(BOOL bAutoCommit = TRUE);
```

### <a name="parameters"></a>Paramètres

*bAutoCommit*<br/>
Si ce paramètre est FALSE, la liste n’est pas automatiquement validée dans le destructor.

## <a name="cjumplistclearall"></a><a name="clearall"></a>CJumpList::ClearAll

Supprime toutes les tâches et destinations qui ont `CJumpList` été ajoutées à l’instance actuelle de jusqu’à présent.

```
void ClearAll();
```

### <a name="remarks"></a>Notes

Cette méthode efface et libère toutes les données et les interfaces internes.

## <a name="cjumplistclearalldestinations"></a><a name="clearalldestinations"></a>CJumpList::ClearAllDestinations

Supprime toutes les destinations qui ont été ajoutées à l’exemple actuel de CJumpList jusqu’à présent.

```
void ClearAllDestinations();
```

### <a name="remarks"></a>Notes

Appelez cette fonction si vous avez besoin de supprimer toutes les destinations qui ont été ajoutées jusqu’à présent dans la session actuelle de la construction de liste de destination et ajouter d’autres destinations à nouveau. Si l’interne `ICustomDestinationList` a été parascé, il est laissé en vie.

## <a name="cjumplistcommitlist"></a><a name="commitlist"></a>CJumpList::CommitList

Termine une transaction de dresseurs de listes et engage la liste indiquée au magasin associé (le registre dans ce cas).

```
BOOL CommitList();
```

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

L’engagement est atomique. Une erreur sera retournée si le commit échoue.  Lorsqu’on `CommitList` appelle, la liste actuelle des articles supprimés sera nettoyée. Appeler cette méthode réinitialise l’objet de sorte qu’il n’a pas une transaction active de construction de liste. Pour mettre à `BeginList` jour la liste, doit être appelé à nouveau.

## <a name="cjumplistgetdestinationlist"></a><a name="getdestinationlist"></a>CJumpList::GetDestinationList

Récupère un pointeur d’interface vers la liste de destination.

```
ICustomDestinationList* GetDestinationList();
```

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

Si la liste de saut n’a pas été parasitée, ou a été commise ou avortée, la valeur retournée sera NULL.

## <a name="cjumplistgetmaxslots"></a><a name="getmaxslots"></a>CJumpList::GetMaxSlots

Récupère le nombre maximum d’éléments, y compris les en-têtes de catégorie qui peuvent s’afficher dans le menu de destination de l’application d’appel.

```
UINT GetMaxSlots() const;
```

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

Les demandes ne peuvent signaler qu’un certain nombre d’éléments et d’en-têtes de catégorie combinés à cette valeur. Si les `AppendCategory` `AppendKnownCategory`appels `AddUserTasks` à , , ou dépasser ce nombre, ils retourneront l’échec.

## <a name="cjumplistgetremoveditems"></a><a name="getremoveditems"></a>CJumpList:GetRemovedItems

Retourne la gamme d’articles qui représentent les destinations supprimées.

```
IObjectArray* GetRemovedItems();
```

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

Les destinations supprimées sont récupérées lors de l’initialisation de la liste de saut. Lors de la génération d’une nouvelle liste de destination, on s’attend à ce que les applications traitent d’abord la liste des destinations supprimées, en effaçant leurs données de suivi pour tout élément retourné par l’enumérateur supprimé de liste. Si une application tente de fournir un élément qui vient d’être supprimé dans la transaction que l’appel actuel a `BeginList` commencé, la méthode d’appel qui a ré-ajouté cet élément échouera, pour s’assurer que les applications respectent la liste supprimée.

## <a name="cjumplistinitializelist"></a><a name="initializelist"></a>CJumpList::InitializeList

Commence une transaction de dresse de liste.

```
BOOL InitializeList();
```

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

Vous n’avez pas besoin d’appeler cette méthode `ICustomDestinationList` explicitement, sauf si vous souhaitez récupérer un pointeur à l’aide `GetDestinationList`, le nombre de fentes disponibles à l’aide `GetMaxSlots`, ou la liste des éléments supprimés en utilisant `GetRemovedItems`.

## <a name="cjumplistsetappid"></a><a name="setappid"></a>CJumpList::SetAppID

Définit l’ID modèle d’utilisateur d’application pour la liste qui sera construite.

```
void SetAppID(LPCTSTR strAppID);
```

### <a name="parameters"></a>Paramètres

*strAppID (en)*<br/>
Une chaîne qui spécifie l’ID modèle d’utilisateur d’application.

## <a name="see-also"></a>Voir aussi

[Classes](../../mfc/reference/mfc-classes.md)
