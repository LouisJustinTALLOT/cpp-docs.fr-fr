---
title: Classe de CMFCTasksPaneTaskGroup | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCTasksPaneTaskGroup
- AFXTASKSPANE/CMFCTasksPaneTaskGroup
- AFXTASKSPANE/CMFCTasksPaneTaskGroup::CMFCTasksPaneTaskGroup
- AFXTASKSPANE/CMFCTasksPaneTaskGroup::SetACCData
- AFXTASKSPANE/CMFCTasksPaneTaskGroup::m_bIsBottom
- AFXTASKSPANE/CMFCTasksPaneTaskGroup::m_bIsCollapsed
- AFXTASKSPANE/CMFCTasksPaneTaskGroup::m_bIsSpecial
- AFXTASKSPANE/CMFCTasksPaneTaskGroup::m_lstTasks
- AFXTASKSPANE/CMFCTasksPaneTaskGroup::m_rect
- AFXTASKSPANE/CMFCTasksPaneTaskGroup::m_rectGroup
- AFXTASKSPANE/CMFCTasksPaneTaskGroup::m_strName
dev_langs:
- C++
helpviewer_keywords:
- CMFCTasksPaneTaskGroup class
ms.assetid: 2111640b-a46e-4b27-b033-29e88632b86a
caps.latest.revision: 33
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: 405a69a0c7d8c4179b36e1beec09fdfa7acd2d7b
ms.lasthandoff: 02/24/2017

---
# <a name="cmfctaskspanetaskgroup-class"></a>CMFCTasksPaneTaskGroup (classe)
Le `CMFCTasksPaneTaskGroup` classe est une classe d’assistance utilisée par le [CMFCTasksPane](../../mfc/reference/cmfctaskspane-class.md) contrôle. Les objets de type `CMFCTasksPaneTaskGroup` représentent un *groupe de tâches*. Le groupe de tâches est une liste d'éléments affichée par l'infrastructure dans une zone séparée comportant un bouton de réduction. La zone peut avoir une légende facultative (nom de groupe). Si un groupe est réduit, la liste de tâches n’est pas visible.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CMFCTasksPaneTaskGroup : public CObject  
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CMFCTasksPaneTaskGroup::CMFCTasksPaneTaskGroup](#cmfctaskspanetaskgroup)|Construit un objet `CMFCTasksPaneTaskGroup`.|  
|`CMFCTasksPaneTaskGroup::~CMFCTasksPaneTaskGroup`|Destructeur.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[CMFCTasksPaneTaskGroup::SetACCData](#setaccdata)|Détermine les données d’accessibilité pour le groupe de tâches en cours.|  
  
### <a name="data-members"></a>Membres de données  
  
|Nom|Description|  
|----------|-----------------|  
|[CMFCTasksPaneTaskGroup::m_bIsBottom](#m_bisbottom)|Détermine si le groupe de tâches est aligné en bas du contrôle du volet de tâches.|  
|[CMFCTasksPaneTaskGroup::m_bIsCollapsed](#m_biscollapsed)|Détermine si le groupe de tâches est réduit.|  
|[CMFCTasksPaneTaskGroup::m_bIsSpecial](#m_bisspecial)|Détermine si le groupe de tâches est *spécial.* Le framework affiche les légendes spéciaux dans une couleur différente.|  
|[CMFCTasksPaneTaskGroup::m_lstTasks](#m_lsttasks)|Contient la liste des tâches interne.|  
|[CMFCTasksPaneTaskGroup::m_rect](#m_rect)|Spécifie le rectangle englobant de la légende du groupe.|  
|[CMFCTasksPaneTaskGroup::m_rectGroup](#m_rectgroup)|Spécifie le rectangle englobant du groupe.|  
|[CMFCTasksPaneTaskGroup::m_strName](#m_strname)|Spécifie le nom du groupe.|  
  
## <a name="remarks"></a>Remarques  
 L’illustration suivante montre un groupe de tâches développé :  
  
 ![Groupe de tâches, développé](../../mfc/reference/media/nexttaskgrpexpand.png "nexttaskgrpexpand")  
  
 L’illustration suivante montre un groupe de tâches réduit :  
  
 ![Groupe de tâches réduit](../../mfc/reference/media/nexttaskgrpcollapse.png "nexttaskgrpcollapse")  
  
 L’illustration suivante montre un groupe de tâches sans légende :  
  
 ![Groupe de tâches sans légende](../../mfc/reference/media/nexttaskgrpnocapt.png "nexttaskgrpnocapt")  
  
 L’illustration suivante montre deux groupes de tâches. Le premier groupe de tâches est marqué comme étant spéciaux en définissant le `m_bIsSpecial` indicateur `TRUE`, tandis que le second groupe de tâches n’est pas spécial. Notez que la légende du premier groupe de tâches est plus sombre que le deuxième groupe de tâches :  
  
 ![Groupe de tâches spéciales](../../mfc/reference/media/nexttaskgrpspecial.png "nexttaskgrpspecial")  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d’héritage  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCTasksPaneTaskGroup](../../mfc/reference/cmfctaskspanetaskgroup-class.md)  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** afxTasksPane.h  
  
##  <a name="cmfctaskspanetaskgroup"></a>CMFCTasksPaneTaskGroup::CMFCTasksPaneTaskGroup  
 Construit un objet `CMFCTasksPaneTaskGroup`.  
  
```  
CMFCTasksPaneTaskGroup(
    LPCTSTR lpszName,  
    BOOL bIsBottom,  
    BOOL bIsSpecial=FALSE,  
    BOOL bIsCollapsed=FALSE,  
    CMFCTasksPanePropertyPage* pPage=NULL,  
    HICON hIcon=NULL);
```  
  
### <a name="parameters"></a>Paramètres  
 `lpszName`  
 Spécifie le nom du groupe dans la légende du groupe.  
  
 `bIsBottom`  
 Spécifie si le groupe est aligné en bas du contrôle du volet de tâches.  
  
 `bIsSpecial`  
 Spécifie si le groupe est désigné en tant que *spéciale* et par conséquent, si la légende du groupe est remplie avec une couleur différente.  
  
 `bIsCollapsed`  
 Spécifie si le groupe est réduit.  
  
 `pPage`  
 Spécifie la page de propriétés appartenant à ce groupe de tâches.  
  
 `hIcon`  
 Spécifie l’icône qui s’affiche dans la légende du groupe.  
  
### <a name="remarks"></a>Notes  
  
##  <a name="m_bisbottom"></a>CMFCTasksPaneTaskGroup::m_bIsBottom  
 Détermine si le groupe de tâches est aligné en bas du contrôle du volet de tâches.  
  
```  
BOOL m_bIsBottom;  
```  
  
### <a name="remarks"></a>Notes  
 Seul un groupe peut être aligné au bas du contrôle du volet de tâches. Ce groupe de tâches doit être ajouté en dernier. Pour plus d’informations, consultez [CMFCTasksPane::AddGroup](../../mfc/reference/cmfctaskspane-class.md#addgroup).  
  
##  <a name="m_biscollapsed"></a>CMFCTasksPaneTaskGroup::m_bIsCollapsed  
 Détermine si le groupe de tâches est réduit.  
  
```  
BOOL m_bIsCollapsed;  
```  
  
### <a name="remarks"></a>Notes  
 Vous pouvez activer ou désactiver la possibilité de réduire les groupes dans le volet Office en appelant [CMFCTasksPane::EnableGroupCollapse](../../mfc/reference/cmfctaskspane-class.md#enablegroupcollapse).  
  
##  <a name="m_bisspecial"></a>CMFCTasksPaneTaskGroup::m_bIsSpecial  
 Détermine si le groupe de tâches est *spéciale* et indique si la légende d’un groupe de tâches spéciales doit être identifiée par une couleur différente.  
  
```  
BOOL m_bIsSpecial;  
```  
  
### <a name="remarks"></a>Notes  
 Si votre application utilise le thème visuel de Windows XP et `m_bIsSpecial` est `FALSE`, le framework appelle `DrawThemeBackground` avec la `EBP_NORMALGROUPBACKGROUND` indicateur. Si `m_bIsSpecial` est `TRUE`, le framework appelle `DrawThemeBackground` avec la `EBP_SPECIALGROUPBACKGROUND` indicateur.  
  
##  <a name="m_lsttasks"></a>CMFCTasksPaneTaskGroup::m_lstTasks  
 Contient la liste des tâches interne.  
  
```  
CObList m_lstTasks;  
```  
  
### <a name="remarks"></a>Notes  
 Pour remplir cette liste, appelez [CMFCTasksPane::AddTask](../../mfc/reference/cmfctaskspane-class.md#addtask).  
  
##  <a name="m_rect"></a>CMFCTasksPaneTaskGroup::m_rect  
 Spécifie le rectangle englobant de la légende du groupe.  
  
```  
CRect m_rect;  
```  
  
### <a name="remarks"></a>Remarques  
 Cette valeur est calculée automatiquement par l’infrastructure.  
  
##  <a name="m_rectgroup"></a>CMFCTasksPaneTaskGroup::m_rectGroup  
 Spécifie le rectangle englobant du groupe.  
  
```  
CRect m_rectGroup;  
```  
  
### <a name="remarks"></a>Notes  
 Cette valeur est calculée automatiquement par l’infrastructure.  
  
##  <a name="m_strname"></a>CMFCTasksPaneTaskGroup::m_strName  
 Spécifie le nom du groupe.  
  
```  
CString m_strName;  
```  
  
### <a name="remarks"></a>Remarques  
 Si cette valeur est vide, la légende du groupe n’est pas affichée et le groupe ne peut pas être réduit.  
  
##  <a name="setaccdata"></a>CMFCTasksPaneTaskGroup::SetACCData  
 Détermine les données d’accessibilité pour le groupe de tâches en cours.  
  
```  
virtual BOOL SetACCData(
    CWnd* pParent,  
    CAccessibilityData& data);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `pParent`  
 Représente la fenêtre parent du groupe de tâches en cours.  
  
 [out] `data`  
 Un objet de type `CAccessibilityData` qui est rempli avec les données d’accessibilité du groupe de tâches en cours.  
  
### <a name="return-value"></a>Valeur de retour  
 `TRUE`Si le `data` paramètre a été remplie avec les données d’accessibilité du groupe de tâches en cours ; sinon, `FALSE`.  
  
## <a name="see-also"></a>Voir aussi  
 [Graphique de la hiérarchie](../../mfc/hierarchy-chart.md)   
 [Classes](../../mfc/reference/mfc-classes.md)   
 [CMFCTasksPane (classe)](../../mfc/reference/cmfctaskspane-class.md)   
 [CMFCTasksPaneTask (classe)](../../mfc/reference/cmfctaskspanetask-class.md)   
 [CMFCOutlookBar (classe)](../../mfc/reference/cmfcoutlookbar-class.md)   
 [CObject (classe)](../../mfc/reference/cobject-class.md)

