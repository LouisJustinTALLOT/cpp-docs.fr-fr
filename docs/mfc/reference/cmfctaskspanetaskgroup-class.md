---
title: Cmfctaskspanetaskgroup, classe
ms.date: 11/19/2018
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
helpviewer_keywords:
- CMFCTasksPaneTaskGroup [MFC], CMFCTasksPaneTaskGroup
- CMFCTasksPaneTaskGroup [MFC], SetACCData
- CMFCTasksPaneTaskGroup [MFC], m_bIsBottom
- CMFCTasksPaneTaskGroup [MFC], m_bIsCollapsed
- CMFCTasksPaneTaskGroup [MFC], m_bIsSpecial
- CMFCTasksPaneTaskGroup [MFC], m_lstTasks
- CMFCTasksPaneTaskGroup [MFC], m_rect
- CMFCTasksPaneTaskGroup [MFC], m_rectGroup
- CMFCTasksPaneTaskGroup [MFC], m_strName
ms.assetid: 2111640b-a46e-4b27-b033-29e88632b86a
ms.openlocfilehash: a28f00fb732727ec1334946a9e752679307cd3a0
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57295225"
---
# <a name="cmfctaskspanetaskgroup-class"></a>Cmfctaskspanetaskgroup, classe

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

|Name|Description|
|----------|-----------------|
|[CMFCTasksPaneTaskGroup::m_bIsBottom](#m_bisbottom)|Détermine si le groupe de tâches est aligné en bas du contrôle de volet de tâches.|
|[CMFCTasksPaneTaskGroup::m_bIsCollapsed](#m_biscollapsed)|Détermine si le groupe de tâches est réduit.|
|[CMFCTasksPaneTaskGroup::m_bIsSpecial](#m_bisspecial)|Détermine si le groupe de tâches est *spécial.* L’infrastructure affiche des légendes spéciales dans une couleur différente.|
|[CMFCTasksPaneTaskGroup::m_lstTasks](#m_lsttasks)|Contient la liste interne des tâches.|
|[CMFCTasksPaneTaskGroup::m_rect](#m_rect)|Spécifie le rectangle englobant de la légende du groupe.|
|[CMFCTasksPaneTaskGroup::m_rectGroup](#m_rectgroup)|Spécifie le rectangle englobant du groupe.|
|[CMFCTasksPaneTaskGroup::m_strName](#m_strname)|Spécifie le nom du groupe.|

## <a name="remarks"></a>Notes

L’illustration suivante montre un groupe de tâches développé :

![Groupe de tâches, développé](../../mfc/reference/media/nexttaskgrpexpand.png "groupe de tâches, développé")

L’illustration suivante montre un groupe de tâches réduit :

![Groupe de tâches réduit](../../mfc/reference/media/nexttaskgrpcollapse.png "groupe de tâches réduit")

L’illustration suivante montre un groupe de tâches sans légende :

![Groupe de tâches sans légende](../../mfc/reference/media/nexttaskgrpnocapt.png "groupe de tâches sans légende")

L’illustration suivante montre deux groupes de tâches. Le premier groupe de tâches est marqué comme étant spéciaux en définissant le `m_bIsSpecial` indicateur sur TRUE, alors que le deuxième groupe de tâches n’est pas spécial. Notez que la légende du premier groupe de tâches plus sombre que le deuxième groupe de tâches :

![Groupe de tâches spéciales](../../mfc/reference/media/nexttaskgrpspecial.png "groupe de tâches spéciales")

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CMFCTasksPaneTaskGroup](../../mfc/reference/cmfctaskspanetaskgroup-class.md)

## <a name="requirements"></a>Spécifications

**En-tête :** afxTasksPane.h

##  <a name="cmfctaskspanetaskgroup"></a>  CMFCTasksPaneTaskGroup::CMFCTasksPaneTaskGroup

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

*lpszName*<br/>
Spécifie le nom du groupe dans la légende du groupe.

*bIsBottom*<br/>
Spécifie si le groupe est aligné en bas du contrôle de volet de tâches.

*bIsSpecial*<br/>
Spécifie si le groupe est désigné comme *spéciale* et par conséquent, si la légende de groupe est remplie avec une couleur différente.

*bIsCollapsed*<br/>
Spécifie si le groupe est réduit.

*pPage*<br/>
Spécifie la page de propriétés auquel appartient ce groupe de tâches.

*hIcon*<br/>
Spécifie l’icône qui s’affiche dans la légende du groupe.

### <a name="remarks"></a>Notes

##  <a name="m_bisbottom"></a>  CMFCTasksPaneTaskGroup::m_bIsBottom

Détermine si le groupe de tâches est aligné en bas du contrôle de volet de tâches.

```
BOOL m_bIsBottom;
```

### <a name="remarks"></a>Notes

Qu’un seul groupe peut être aligné en bas du contrôle de volet de tâches. Ce groupe de tâches doit être ajouté en dernier. Pour plus d’informations, consultez [CMFCTasksPane::AddGroup](../../mfc/reference/cmfctaskspane-class.md#addgroup).

##  <a name="m_biscollapsed"></a>  CMFCTasksPaneTaskGroup::m_bIsCollapsed

Détermine si le groupe de tâches est réduit.

```
BOOL m_bIsCollapsed;
```

### <a name="remarks"></a>Notes

Vous pouvez activer ou désactiver la possibilité de réduire les groupes dans le volet Office en appelant [CMFCTasksPane::EnableGroupCollapse](../../mfc/reference/cmfctaskspane-class.md#enablegroupcollapse).

##  <a name="m_bisspecial"></a>  CMFCTasksPaneTaskGroup::m_bIsSpecial

Détermine si le groupe de tâches est *spéciale* et indique si la légende pour un groupe de tâches spéciales doit être identifiée par une couleur différente.

```
BOOL m_bIsSpecial;
```

### <a name="remarks"></a>Notes

Si votre application utilise le thème visuel de Windows XP et `m_bIsSpecial` est FALSE, le framework appelle `DrawThemeBackground` avec l’indicateur EBP_NORMALGROUPBACKGROUND. Si `m_bIsSpecial` a la valeur TRUE, le framework appelle `DrawThemeBackground` avec l’indicateur EBP_SPECIALGROUPBACKGROUND.

##  <a name="m_lsttasks"></a>  CMFCTasksPaneTaskGroup::m_lstTasks

Contient la liste interne des tâches.

```
CObList m_lstTasks;
```

### <a name="remarks"></a>Notes

Pour remplir cette liste, appelez [CMFCTasksPane::AddTask](../../mfc/reference/cmfctaskspane-class.md#addtask).

##  <a name="m_rect"></a>  CMFCTasksPaneTaskGroup::m_rect

Spécifie le rectangle englobant de la légende du groupe.

```
CRect m_rect;
```

### <a name="remarks"></a>Notes

Cette valeur est calculée automatiquement par l’infrastructure.

##  <a name="m_rectgroup"></a>  CMFCTasksPaneTaskGroup::m_rectGroup

Spécifie le rectangle englobant du groupe.

```
CRect m_rectGroup;
```

### <a name="remarks"></a>Notes

Cette valeur est calculée automatiquement par l’infrastructure.

##  <a name="m_strname"></a>  CMFCTasksPaneTaskGroup::m_strName

Spécifie le nom du groupe.

```
CString m_strName;
```

### <a name="remarks"></a>Notes

Si cette valeur est vide, la légende du groupe n’est pas affichée, et le groupe ne peut pas être réduit.

##  <a name="setaccdata"></a>  CMFCTasksPaneTaskGroup::SetACCData

Détermine les données d’accessibilité pour le groupe de tâches en cours.

```
virtual BOOL SetACCData(
    CWnd* pParent,
    CAccessibilityData& data);
```

### <a name="parameters"></a>Paramètres

*pParent*<br/>
[in] Représente la fenêtre parent du groupe de tâches en cours.

*data*<br/>
[out] Un objet de type `CAccessibilityData` qui est rempli avec les données d’accessibilité du groupe de tâches en cours.

### <a name="return-value"></a>Valeur de retour

TRUE si le *données* paramètre a été correctement remplis avec les données d’accessibilité du groupe de tâches en cours ; sinon, FALSE.

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[CMFCTasksPane, classe](../../mfc/reference/cmfctaskspane-class.md)<br/>
[CMFCTasksPaneTask, classe](../../mfc/reference/cmfctaskspanetask-class.md)<br/>
[CMFCOutlookBar, classe](../../mfc/reference/cmfcoutlookbar-class.md)<br/>
[CObject, classe](../../mfc/reference/cobject-class.md)
