---
title: CMFCTasksPaneTaskGroup, classe
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
ms.openlocfilehash: 4c24eba646bede462a5f3cfb85715278cfa7daee
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366258"
---
# <a name="cmfctaskspanetaskgroup-class"></a>CMFCTasksPaneTaskGroup, classe

La `CMFCTasksPaneTaskGroup` classe est une classe d’aide utilisée par le contrôle [CMFCTasksPane.](../../mfc/reference/cmfctaskspane-class.md) Les objets de type `CMFCTasksPaneTaskGroup` représentent un *groupe de tâches*. Le groupe de tâches est une liste d'éléments affichée par l'infrastructure dans une zone séparée comportant un bouton de réduction. La zone peut avoir une légende facultative (nom de groupe). Si un groupe est réduit, la liste de tâches n’est pas visible.

## <a name="syntax"></a>Syntaxe

```
class CMFCTasksPaneTaskGroup : public CObject
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CMFCTasksPaneTaskGroup:CMFCTasksPaneTaskGroup](#cmfctaskspanetaskgroup)|Construit un objet `CMFCTasksPaneTaskGroup`.|
|`CMFCTasksPaneTaskGroup::~CMFCTasksPaneTaskGroup`|Destructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CMFCTasksPaneTaskGroup::SetACCData](#setaccdata)|Détermine les données d’accessibilité pour le groupe de travail actuel.|

### <a name="data-members"></a>Données membres

|Nom|Description|
|----------|-----------------|
|[CMFCTasksPaneTaskGroup:m_bIsBottom](#m_bisbottom)|Détermine si le groupe de travail est aligné au bas du contrôle de la partie de la tâche.|
|[CMFCTasksPaneTaskGroup:m_bIsCollapsed](#m_biscollapsed)|Détermine si le groupe de travail est effondré.|
|[CMFCTasksPaneTaskGroup:m_bIsSpecial](#m_bisspecial)|Détermine si le groupe de travail est *spécial.* Le cadre affiche des légendes spéciales dans une couleur différente.|
|[CMFCTasksPaneTaskGroup:m_lstTasks](#m_lsttasks)|Contient la liste interne des tâches.|
|[CMFCTasksPaneTaskGroup:m_rect](#m_rect)|Spécifie le rectangle de délimitation de la légende du groupe.|
|[CMFCTasksPaneTaskGroup:m_rectGroup](#m_rectgroup)|Spécifie le rectangle de délimitation du groupe.|
|[CMFCTasksPaneTaskGroup:m_strName](#m_strname)|Spécifie le nom du groupe.|

## <a name="remarks"></a>Notes

L’illustration suivante montre un groupe de tâches élargi :

![Groupe de travail, élargi](../../mfc/reference/media/nexttaskgrpexpand.png "Groupe de tâches, développé")

L’illustration suivante montre un groupe de tâches effondré :

![Groupe de tâches réduit](../../mfc/reference/media/nexttaskgrpcollapse.png "Groupe de tâches réduit")

L’illustration suivante montre un groupe de travail sans légende :

![Groupe de tâches sans légende](../../mfc/reference/media/nexttaskgrpnocapt.png "Groupe de tâches sans légende")

L’illustration suivante montre deux groupes de tâches. Le premier groupe de travail est `m_bIsSpecial` marqué comme spécial en fixant le drapeau à TRUE, tandis que le deuxième groupe de travail n’est pas spécial. Notez comment la légende du premier groupe de travail est plus sombre que le deuxième groupe de travail :

![Groupe de tâches spéciales](../../mfc/reference/media/nexttaskgrpspecial.png "Groupe de tâches spéciales")

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CMFCTasksPaneTaskGroup](../../mfc/reference/cmfctaskspanetaskgroup-class.md)

## <a name="requirements"></a>Spécifications

**En-tête:** afxTasksPane.h

## <a name="cmfctaskspanetaskgroupcmfctaskspanetaskgroup"></a><a name="cmfctaskspanetaskgroup"></a>CMFCTasksPaneTaskGroup:CMFCTasksPaneTaskGroup

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

*lpszName (en)*<br/>
Précise le nom du groupe dans la légende du groupe.

*bIsBottom (en)*<br/>
Précise si le groupe est aligné au bas du contrôle de la partie de la tâche.

*bIsSpecial (en)*<br/>
Précise si le groupe est désigné comme *spécial* et donc, si la légende du groupe est remplie d’une couleur différente.

*bIsCollapsed*<br/>
Précise si le groupe est effondré.

*pPage*<br/>
Spécifie la page de propriété à laquelle ce groupe de travail appartient.

*hIcon (en)*<br/>
Spécifie l’icône qui s’affiche dans la légende du groupe.

### <a name="remarks"></a>Notes

## <a name="cmfctaskspanetaskgroupm_bisbottom"></a><a name="m_bisbottom"></a>CMFCTasksPaneTaskGroup:m_bIsBottom

Détermine si le groupe de travail est aligné au bas du contrôle de la partie de la tâche.

```
BOOL m_bIsBottom;
```

### <a name="remarks"></a>Notes

Un seul groupe peut être aligné au bas du contrôle de la partie de la tâche. Ce groupe de travail doit être ajouté en dernier. Pour plus d’informations, voir [CMFCTasksPane:AddGroup](../../mfc/reference/cmfctaskspane-class.md#addgroup).

## <a name="cmfctaskspanetaskgroupm_biscollapsed"></a><a name="m_biscollapsed"></a>CMFCTasksPaneTaskGroup:m_bIsCollapsed

Détermine si le groupe de travail est effondré.

```
BOOL m_bIsCollapsed;
```

### <a name="remarks"></a>Notes

Vous pouvez activer ou désactiver la possibilité d’effondrer des groupes sur le volet tâche en appelant [CMFCTasksPane::EnableGroupCollapse](../../mfc/reference/cmfctaskspane-class.md#enablegroupcollapse).

## <a name="cmfctaskspanetaskgroupm_bisspecial"></a><a name="m_bisspecial"></a>CMFCTasksPaneTaskGroup:m_bIsSpecial

Détermine si le groupe de travail est *spécial* et si la légende d’un groupe de tâches spécial doit être identifiée par une couleur différente.

```
BOOL m_bIsSpecial;
```

### <a name="remarks"></a>Notes

Si votre application utilise le thème `m_bIsSpecial` visuel Windows XP `DrawThemeBackground` et est FALSE, le cadre passe avec le drapeau EBP_NORMALGROUPBACKGROUND. Si `m_bIsSpecial` c’est VRAI, le cadre passe `DrawThemeBackground` avec le drapeau EBP_SPECIALGROUPBACKGROUND.

## <a name="cmfctaskspanetaskgroupm_lsttasks"></a><a name="m_lsttasks"></a>CMFCTasksPaneTaskGroup:m_lstTasks

Contient la liste interne des tâches.

```
CObList m_lstTasks;
```

### <a name="remarks"></a>Notes

Pour remplir cette liste, appelez [CMFCTasksPane::AddTask](../../mfc/reference/cmfctaskspane-class.md#addtask).

## <a name="cmfctaskspanetaskgroupm_rect"></a><a name="m_rect"></a>CMFCTasksPaneTaskGroup:m_rect

Spécifie le rectangle de délimitation de la légende du groupe.

```
CRect m_rect;
```

### <a name="remarks"></a>Notes

Cette valeur est automatiquement calculée par le cadre.

## <a name="cmfctaskspanetaskgroupm_rectgroup"></a><a name="m_rectgroup"></a>CMFCTasksPaneTaskGroup:m_rectGroup

Spécifie le rectangle de délimitation du groupe.

```
CRect m_rectGroup;
```

### <a name="remarks"></a>Notes

Cette valeur est calculée automatiquement par le cadre.

## <a name="cmfctaskspanetaskgroupm_strname"></a><a name="m_strname"></a>CMFCTasksPaneTaskGroup:m_strName

Spécifie le nom du groupe.

```
CString m_strName;
```

### <a name="remarks"></a>Notes

Si cette valeur est vide, la légende du groupe n’est pas affichée et le groupe ne peut pas être effondré.

## <a name="cmfctaskspanetaskgroupsetaccdata"></a><a name="setaccdata"></a>CMFCTasksPaneTaskGroup::SetACCData

Détermine les données d’accessibilité pour le groupe de travail actuel.

```
virtual BOOL SetACCData(
    CWnd* pParent,
    CAccessibilityData& data);
```

### <a name="parameters"></a>Paramètres

*pParent*<br/>
[dans] Représente la fenêtre parente du groupe de travail actuel.

*data*<br/>
[out] Un objet `CAccessibilityData` de type qui est peuplé des données d’accessibilité du groupe de travail actuel.

### <a name="return-value"></a>Valeur de retour

VRAI si le paramètre *de données* a été peuplé avec succès avec les données d’accessibilité du groupe de travail actuel; autrement, FALSE.

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[Classe CMFCTasksPane](../../mfc/reference/cmfctaskspane-class.md)<br/>
[CMFCTasksPaneTask, classe](../../mfc/reference/cmfctaskspanetask-class.md)<br/>
[Classe CMFCOutlookBar](../../mfc/reference/cmfcoutlookbar-class.md)<br/>
[Classe CObject](../../mfc/reference/cobject-class.md)
