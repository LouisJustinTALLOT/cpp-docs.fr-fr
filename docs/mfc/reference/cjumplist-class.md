---
title: Classe de CJumpList | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d22fa264f48d3c5b1b6b88db338bc3be45c3f398
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33369048"
---
# <a name="cjumplist-class"></a>Classe de CJumpList
A `CJumpList` est la liste des raccourcis qui s’affiché lorsque vous avec le bouton droit sur une icône dans la barre des tâches.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CJumpList;  
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CJumpList::CJumpList](#cjumplist)|Construit un objet `CJumpList`.|  
|[CJumpList :: ~ CJumpList](#cjumplist__~cjumplist)|Détruit un objet `CJumpList`.|  
  
|Name|Description|  
|----------|-----------------|  
|[CJumpList::AbortList](#abortlist)|Abandonne une transaction de création de liste sans validation.|  
|[CJumpList::AddDestination](#adddestination)|Surchargé. Ajoute la destination à la liste.|  
|[CJumpList::AddKnownCategory](#addknowncategory)|Ajoute une catégorie connus à la liste.|  
|[CJumpList::AddTask](#addtask)|Surchargé. Ajoute des éléments à la catégorie de tâche canonique.|  
|[CJumpList::AddTasks](#addtasks)|Ajoute des éléments à la catégorie de tâche canonique.|  
|[CJumpList::AddTaskSeparator](#addtaskseparator)|Ajoute un séparateur entre les tâches.|  
|[CJumpList::ClearAll](#clearall)|Supprime toutes les tâches et les destinations qui ont été ajoutées à l’instance actuelle de `CJumpList` jusqu'à présent.|  
|[CJumpList::ClearAllDestinations](#clearalldestinations)|Supprime toutes les destinations qui ont été ajoutées à l’instance actuelle de `CJumpList` jusqu'à présent.|  
|[CJumpList::CommitList](#commitlist)|Termine une transaction de création de liste et valide de la liste signalée dans le magasin associé (le Registre dans ce cas).|  
|[CJumpList::GetDestinationList](#getdestinationlist)|Récupère un pointeur d’interface à la liste de destination.|  
|[CJumpList::GetMaxSlots](#getmaxslots)|Récupère le nombre maximal d’éléments, y compris les en-têtes de catégorie qui peuvent afficher dans le menu de destination de l’application appelante.|  
|[CJumpList::GetRemovedItems](#getremoveditems)|Retourne un tableau des éléments qui représentent supprimé des destinations.|  
|[CJumpList::InitializeList](#initializelist)|Commence une transaction de création de la liste.|  
|[CJumpList::SetAppID](#setappid)|Définit l’ID de modèle d’Application utilisateur pour obtenir la liste qui est construite.|  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 [CJumpList](../../mfc/reference/cjumplist-class.md)  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** afxadv.h  
  
##  <a name="_dtorcjumplist"></a>  CJumpList :: ~ CJumpList  
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
 L’appel à cette méthode a le même effet que la destruction `CJumpList` sans appeler `CommitList`.  
  
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
 `lpcszCategoryName`  
 Spécifie un nom de catégorie. Si la catégorie spécifiée n’existe pas, il sera créé.  
  
 `strDestinationPath`  
 Spécifie un chemin d’accès au fichier de destination.  
  
 `strCategoryName`  
 Spécifie un nom de catégorie. Si la catégorie spécifiée n’existe pas, il sera créé.  
  
 `pShellItem`  
 Spécifie un élément de l’interpréteur de commandes qui représente la destination ajoutée.  
  
 `pShellLink`  
 Spécifie un lien de l’interpréteur de commandes qui représente la destination ajoutée.  
  
### <a name="return-value"></a>Valeur de retour  
  
### <a name="remarks"></a>Notes  
 L’instance de `CJumpList` accumule en interne les destinations ajoutées et puis valide les modifications dans `CommitList`.  
  
##  <a name="addknowncategory"></a>  CJumpList::AddKnownCategory  
 Ajoute une catégorie connus à la liste.  
  
```  
BOOL AddKnownCategory(KNOWNDESTCATEGORY category);
```  
  
### <a name="parameters"></a>Paramètres  
 `category`  
 Spécifie un type de catégorie connue. Peut être `KDC_RECENT`, ou `KDC_KNOWN`.  
  
### <a name="return-value"></a>Valeur de retour  
  
### <a name="remarks"></a>Notes  
 Connu les catégories sont les exécutions fréquentes et récents qui nous calculera automatiquement pour chaque application qui utilise `SHAddToRecentDocs` (ou indirectement l’utilise comme l’interpréteur de commandes appellera en nom de l’application dans certains scénarios).  
  
##  <a name="addtask"></a>  CJumpList::AddTask  
 Ajoute des éléments à la catégorie de tâche canonique.  
  
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
 `strTargetExecutablePath`  
 Spécifie le chemin d’accès cible.  
  
 `strCommandLineArgs`  
 Spécifie les arguments de ligne de commande de l’exécutable spécifié par strTargetExecutablePath.  
  
 `strTitle`  
 Nom de la tâche qui s’affichera dans la liste de Destination.  
  
 `strIconLocation`  
 Emplacement de l’icône qui s’affichera dans la liste de Destination, ainsi que le titre.  
  
 `iIconIndex`  
 Index de l’icône.  
  
 `pShellLink`  
 Lien d’interface qui représente une tâche à ajouter.  
  
### <a name="return-value"></a>Valeur de retour  
  
### <a name="remarks"></a>Notes  
 L’instance de `CJumpList` accumule les tâches spécifiées et les ajoute à la liste de Destination pendant `CommitList`. Éléments de tâche seront affiche dans une catégorie en bas du menu de destination de l’application. Cette catégorie est prioritaire sur toutes les autres catégories lorsqu’elle est remplie dans l’interface utilisateur.  
  
##  <a name="addtasks"></a>  CJumpList::AddTasks  
 Ajoute des éléments à la catégorie de tâche canonique.  
  
```  
BOOL AddTasks(IObjectArray* pObjectCollection);
```  
  
### <a name="parameters"></a>Paramètres  
 `pObjectCollection`  
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
 Différent de zéro si l’opération a réussi, 0 si elle n’est pas.  
  
##  <a name="cjumplist"></a>  CJumpList::CJumpList  
 Construit un objet `CJumpList`.  
  
```  
CJumpList(BOOL bAutoCommit = TRUE);
```  
  
### <a name="parameters"></a>Paramètres  
 `bAutoCommit`  
 Si ce paramètre a la valeur FALSE la liste n’est pas automatiquement validée dans le destructeur.  
  
##  <a name="clearall"></a>  CJumpList::ClearAll  
 Supprime toutes les tâches et les destinations qui ont été ajoutées à l’instance actuelle de `CJumpList` jusqu'à présent.  
  
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
 Appelez cette fonction si vous devez supprimer toutes les destinations qui ont été ajoutées jusqu'à présent dans la session en cours de création de liste de destination et ajoutez de nouveau autres destinations. Si le texte interne `ICustomDestinationList` a été initialisé, il reste actif.  
  
##  <a name="commitlist"></a>  CJumpList::CommitList  
 Termine une transaction de création de liste et valide de la liste signalée dans le magasin associé (le Registre dans ce cas).  
  
```  
BOOL CommitList();
```  
  
### <a name="return-value"></a>Valeur de retour  
  
### <a name="remarks"></a>Notes  
 La validation est atomique. Une erreur est renvoyée si la validation échoue.  Lorsque `CommitList` est appelée, en cours est nettoyée liste d’éléments supprimés. Appel de cette méthode de réinitialise l’objet afin qu’il n’a pas une transaction active de la construction de la liste. Pour mettre à jour la liste, `BeginList` doit être appelé à nouveau.  
  
##  <a name="getdestinationlist"></a>  CJumpList::GetDestinationList  
 Récupère un pointeur d’interface à la liste de destination.  
  
```  
ICustomDestinationList* GetDestinationList();
```  
  
### <a name="return-value"></a>Valeur de retour  
  
### <a name="remarks"></a>Notes  
 Si la liste de raccourcis n’a pas été initialisée, ou s’il a été validée ou annulée, la valeur retournée sera `NULL`.  
  
##  <a name="getmaxslots"></a>  CJumpList::GetMaxSlots  
 Récupère le nombre maximal d’éléments, y compris les en-têtes de catégorie qui peuvent afficher dans le menu de destination de l’application appelante.  
  
```  
UINT GetMaxSlots() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
  
### <a name="remarks"></a>Notes  
 Les applications peuvent signaler uniquement un nombre d’éléments et les en-têtes de catégorie combinées jusqu'à cette valeur. Si les appels à `AppendCategory`, `AppendKnownCategory`, ou `AddUserTasks` dépasse ce nombre, ils renvoient une erreur.  
  
##  <a name="getremoveditems"></a>  CJumpList::GetRemovedItems  
 Retourne un tableau des éléments qui représentent supprimé des destinations.  
  
```  
IObjectArray* GetRemovedItems();
```  
  
### <a name="return-value"></a>Valeur de retour  
  
### <a name="remarks"></a>Notes  
 Les destinations supprimées sont récupérées lors de l’initialisation de la liste de raccourcis. Lorsque vous générez une nouvelle liste de destination, les applications sont censées traiter tout d’abord de la liste de destinations supprimé, effacer les données de suivi pour tout élément retourné par l’énumérateur de la liste supprimée. Si une application tente de fournir un élément qui vient d’être supprimé dans la transaction en cours de l’appel à `BeginList` démarré, l’appel de méthode qui rajouté cet élément échouera, pour vous assurer que les applications sont en respectant la liste supprimée.  
  
##  <a name="initializelist"></a>  CJumpList::InitializeList  
 Commence une transaction de création de la liste.  
  
```  
BOOL InitializeList();
```  
  
### <a name="return-value"></a>Valeur de retour  
  
### <a name="remarks"></a>Notes  
 Vous n’avez pas besoin d’appeler cette méthode explicitement, sauf si vous souhaitez récupérer un pointeur vers `ICustomDestinationList` à l’aide de `GetDestinationList`, le nombre d’emplacements disponibles à l’aide de `GetMaxSlots`, ou une liste d’éléments supprimés à l’aide de `GetRemovedItems`.  
  
##  <a name="setappid"></a>  CJumpList::SetAppID  
 Définit l’ID de modèle d’Application utilisateur pour obtenir la liste qui est construite.  
  
```  
void SetAppID(LPCTSTR strAppID);
```  
  
### <a name="parameters"></a>Paramètres  
 `strAppID`  
 Chaîne qui spécifie l’ID de modèle d’Application utilisateur.  
  
## <a name="see-also"></a>Voir aussi  
 [Classes](../../mfc/reference/mfc-classes.md)
