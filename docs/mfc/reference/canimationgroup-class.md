---
title: CAnimationGroup, classe
ms.date: 03/27/2019
f1_keywords:
- CAnimationGroup
- AFXANIMATIONCONTROLLER/CAnimationGroup
- AFXANIMATIONCONTROLLER/CAnimationGroup::CAnimationGroup
- AFXANIMATIONCONTROLLER/CAnimationGroup::Animate
- AFXANIMATIONCONTROLLER/CAnimationGroup::ApplyTransitions
- AFXANIMATIONCONTROLLER/CAnimationGroup::FindAnimationObject
- AFXANIMATIONCONTROLLER/CAnimationGroup::GetGroupID
- AFXANIMATIONCONTROLLER/CAnimationGroup::RemoveKeyframes
- AFXANIMATIONCONTROLLER/CAnimationGroup::RemoveTransitions
- AFXANIMATIONCONTROLLER/CAnimationGroup::Schedule
- AFXANIMATIONCONTROLLER/CAnimationGroup::SetAutodestroyTransitions
- AFXANIMATIONCONTROLLER/CAnimationGroup::AddKeyframes
- AFXANIMATIONCONTROLLER/CAnimationGroup::AddTransitions
- AFXANIMATIONCONTROLLER/CAnimationGroup::CreateTransitions
- AFXANIMATIONCONTROLLER/CAnimationGroup::m_bAutoclearTransitions
- AFXANIMATIONCONTROLLER/CAnimationGroup::m_bAutodestroyAnimationObjects
- AFXANIMATIONCONTROLLER/CAnimationGroup::m_bAutodestroyKeyframes
- AFXANIMATIONCONTROLLER/CAnimationGroup::m_lstAnimationObjects
- AFXANIMATIONCONTROLLER/CAnimationGroup::m_lstKeyFrames
- AFXANIMATIONCONTROLLER/CAnimationGroup::m_pStoryboard
- AFXANIMATIONCONTROLLER/CAnimationGroup::m_nGroupID
- AFXANIMATIONCONTROLLER/CAnimationGroup::m_pParentController
helpviewer_keywords:
- CAnimationGroup [MFC], CAnimationGroup
- CAnimationGroup [MFC], Animate
- CAnimationGroup [MFC], ApplyTransitions
- CAnimationGroup [MFC], FindAnimationObject
- CAnimationGroup [MFC], GetGroupID
- CAnimationGroup [MFC], RemoveKeyframes
- CAnimationGroup [MFC], RemoveTransitions
- CAnimationGroup [MFC], Schedule
- CAnimationGroup [MFC], SetAutodestroyTransitions
- CAnimationGroup [MFC], AddKeyframes
- CAnimationGroup [MFC], AddTransitions
- CAnimationGroup [MFC], CreateTransitions
- CAnimationGroup [MFC], m_bAutoclearTransitions
- CAnimationGroup [MFC], m_bAutodestroyAnimationObjects
- CAnimationGroup [MFC], m_bAutodestroyKeyframes
- CAnimationGroup [MFC], m_lstAnimationObjects
- CAnimationGroup [MFC], m_lstKeyFrames
- CAnimationGroup [MFC], m_pStoryboard
- CAnimationGroup [MFC], m_nGroupID
- CAnimationGroup [MFC], m_pParentController
ms.assetid: 8bc18ceb-33a2-41d0-9731-71811adacab7
ms.openlocfilehash: 28d305e2107f7b9a8fd2164eb0ec9678d62ef8fa
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369742"
---
# <a name="canimationgroup-class"></a>CAnimationGroup, classe

Implémente un groupe d’animation, qui combine un storyboard d’animation, des objets d’animation et des transitions pour définir une animation.

## <a name="syntax"></a>Syntaxe

```
class CAnimationGroup;
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CAnimationGroup::CAnimationGroup](#canimationgroup)|Construit un groupe d’animation.|
|[CAnimationGroup::CAnimationGroup](#_dtorcanimationgroup)|Destructeur. Appelé quand un groupe d’animation est détruit.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CAnimationGroup::Animate](#animate)|Anime un groupe.|
|[CAnimationGroup::ApplyTransitions](#applytransitions)|Applique les transitions vers les objets d’animation.|
|[CAnimationGroup::FindAnimationObject](#findanimationobject)|Trouve un objet d’animation qui contient la variable d’animation spécifiée.|
|[CAnimationGroup::GetGroupID](#getgroupid)|Retourne GroupID.|
|[CAnimationGroup::RemoveKeyframes](#removekeyframes)|Supprime et détruit optionnellement tous les cadres clés qui appartiennent à un groupe d’animation.|
|[CAnimationGroup::RemoveTransitions](#removetransitions)|Supprime les transitions des objets d’animation qui appartiennent à un groupe d’animation.|
|[CAnimationGroup::Calendrier](#schedule)|Planifie une animation à l’heure spécifiée.|
|[CAnimationGroup::SetAutodestroyTransitions](#setautodestroytransitions)|Les directives de tous les objets d’animation appartenant au groupe détruisent automatiquement les transitions.|

### <a name="protected-methods"></a>Méthodes protégées

|Nom|Description|
|----------|-----------------|
|[CAnimationGroup::AddKeyframes](#addkeyframes)|Une aide qui ajoute des cadres clés à un storyboard.|
|[CAnimationGroup::AddTransitions](#addtransitions)|Une aide qui ajoute des transitions à un storyboard.|
|[CAnimationGroup::CreateTransitions](#createtransitions)|Une aide qui crée des objets de transition COM.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CAnimationGroup::m_bAutoclearTransitions](#m_bautocleartransitions)|Précise comment effacer les transitions des objets d’animation qui appartiennent au groupe. Si ce membre est VRAI, les transitions sont supprimées automatiquement lorsqu’une animation a été programmée. Sinon, vous devez supprimer les transitions manuellement.|
|[CAnimationGroup::m_bAutodestroyAnimationObjects](#m_bautodestroyanimationobjects)|Précise comment détruire les objets d’animation. Si ce paramètre est VRAI, les objets d’animation seront détruits automatiquement lorsque le groupe sera détruit. Sinon, les objets d’animation doivent être détruits manuellement. La valeur par défaut est FALSE. Définissez cette valeur à TRUE uniquement si tous les objets d’animation appartenant au groupe sont attribués dynamiquement avec l’opérateur nouveau.|
|[CAnimationGroup::m_bAutodestroyKeyframes](#m_bautodestroykeyframes)|Specifie comment détruire les cadres clés. Si cette valeur est VRAI, tous les cadres clés sont enlevés et détruits; sinon ils ne sont retirés de la liste que. La valeur par défaut est TRUE.|
|[CAnimationGroup::m_lstAnimationObjects](#m_lstanimationobjects)|Contient une liste d’objets d’animation.|
|[CAnimationGroup::m_lstKeyFrames](#m_lstkeyframes)|Contient une liste de cadres clés.|
|[CAnimationGroup::m_pStoryboard](#m_pstoryboard)|Points à storyboard d’animation. Ce pointeur n’est valable qu’après l’appel sur Animate.|

### <a name="protected-data-members"></a>Membres de données protégés

|Nom|Description|
|----------|-----------------|
|[CAnimationGroup::m_nGroupID](#m_ngroupid)|Un identifiant unique du groupe d’animation.|
|[CAnimationGroup::m_pParentController](#m_pparentcontroller)|Un pointeur au contrôleur d’animation auquel ce groupe appartient.|

## <a name="remarks"></a>Notes

Les groupes d’animation sont créés automatiquement par le contrôleur d’animation (CAnimationController) lorsque vous ajoutez des objets d’animation à l’aide de CAnimationController::AddAnimationObject. Un groupe d’animation est identifié par GroupID, qui est généralement considéré comme un paramètre pour manipuler les groupes d’animation. Le GroupID est tiré du premier objet d’animation ajouté à un nouveau groupe d’animation. Un storyboard d’animation encapsulé est créé après avoir appelé CAnimationController::AnimateGroup et peut être consulté via des membres du public m_pStoryboard.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`CAnimationGroup`

## <a name="requirements"></a>Spécifications

**En-tête :** afxanimationcontroller.h

## <a name="canimationgroupcanimationgroup"></a><a name="_dtorcanimationgroup"></a>CAnimationGroup::CAnimationGroup

Destructeur. Appelé quand un groupe d’animation est détruit.

```
~CAnimationGroup();
```

## <a name="canimationgroupaddkeyframes"></a><a name="addkeyframes"></a>CAnimationGroup::AddKeyframes

Une aide qui ajoute des cadres clés à un storyboard.

```
void AddKeyframes(IUIAnimationStoryboard* pStoryboard, BOOL bAddDeep);
```

### <a name="parameters"></a>Paramètres

*pStoryboard (en)*<br/>
Un pointeur vers un objet COM storyboard.

*bAddDeep (en)*<br/>
Précise si cette méthode doit ajouter aux cadres clés du tableau de l’histoire qui dépendent d’autres cadres clés.

## <a name="canimationgroupaddtransitions"></a><a name="addtransitions"></a>CAnimationGroup::AddTransitions

Une aide qui ajoute des transitions à un storyboard.

```
void AddTransitions(
    IUIAnimationStoryboard* pStoryboard,
    BOOL bDependOnKeyframes);
```

### <a name="parameters"></a>Paramètres

*pStoryboard (en)*<br/>
Un pointeur vers un objet COM storyboard.

*bDependOnKeyframes*

## <a name="canimationgroupanimate"></a><a name="animate"></a>CAnimationGroup::Animate

Anime un groupe.

```
BOOL Animate(
    IUIAnimationManager* pManager,
    IUIAnimationTimer* pTimer,
    BOOL bScheduleNow);
```

### <a name="parameters"></a>Paramètres

*pManager (en anglais)*<br/>
*pTimer*
*bScheduleNow*

### <a name="return-value"></a>Valeur de retour

VRAI si la méthode réussit; autrement FALSE.

### <a name="remarks"></a>Notes

Cette méthode crée un storyboard interne, crée et applique des transitions et planifie une animation si bScheduleNow est VRAI. Si bScheduleNow est FALSE, vous devez appeler l’annexe pour commencer l’animation à l’heure spécifiée.

## <a name="canimationgroupapplytransitions"></a><a name="applytransitions"></a>CAnimationGroup::ApplyTransitions

Applique les transitions vers les objets d’animation.

```
void ApplyTransitions();
```

### <a name="remarks"></a>Notes

Cette méthode ASSERTS en mode débogé si storyboard n’a pas été créé. Il crée toutes les transitions d’abord, puis ajoute des cadres clés "statiques" (des cadres clés qui dépendent des compensations), ajoute des transitions qui ne dépendent pas des cadres clés, ajoute des cadres clés en fonction des transitions et autres cadres clés, et ajoute enfin des transitions qui dépendent des cadres clés.

## <a name="canimationgroupcanimationgroup"></a><a name="canimationgroup"></a>CAnimationGroup::CAnimationGroup

Construit un groupe d’animation.

```
CAnimationGroup(CAnimationController* pParentController, UINT32 nGroupID);
```

### <a name="parameters"></a>Paramètres

*pParentController*<br/>
Un pointeur au contrôleur d’animation qui crée un groupe.

*nGroupID (en anglais)*<br/>
Spécifie GroupID.

## <a name="canimationgroupcreatetransitions"></a><a name="createtransitions"></a>CAnimationGroup::CreateTransitions

Une aide qui crée des objets de transition COM.

```
BOOL CreateTransitions();
```

### <a name="return-value"></a>Valeur de retour

TRUE est la méthode réussit, sinon FALSE.

## <a name="canimationgroupfindanimationobject"></a><a name="findanimationobject"></a>CAnimationGroup::FindAnimationObject

Trouve un objet d’animation qui contient la variable d’animation spécifiée.

```
CAnimationBaseObject* FindAnimationObject(IUIAnimationVariable* pVariable);
```

### <a name="parameters"></a>Paramètres

*pVariable*<br/>
Un pointeur à la variable d’animation.

### <a name="return-value"></a>Valeur de retour

Un pointeur à l’objet d’animation, ou NULL si l’objet d’animation n’est pas trouvé.

## <a name="canimationgroupgetgroupid"></a><a name="getgroupid"></a>CAnimationGroup::GetGroupID

Retourne GroupID.

```
UINT32 GetGroupID() const;
```

### <a name="return-value"></a>Valeur de retour

Un identifiant de groupe.

## <a name="canimationgroupm_bautocleartransitions"></a><a name="m_bautocleartransitions"></a>CAnimationGroup::m_bAutoclearTransitions

Précise comment effacer les transitions des objets d’animation qui appartiennent au groupe. Si ce membre est VRAI, les transitions sont supprimées automatiquement lorsqu’une animation a été programmée. Sinon, vous devez supprimer les transitions manuellement.

```
BOOL m_bAutoclearTransitions;
```

## <a name="canimationgroupm_bautodestroyanimationobjects"></a><a name="m_bautodestroyanimationobjects"></a>CAnimationGroup::m_bAutodestroyAnimationObjects

Précise comment détruire les objets d’animation. Si ce paramètre est VRAI, les objets d’animation seront détruits automatiquement lorsque le groupe sera détruit. Sinon, les objets d’animation doivent être détruits manuellement. La valeur par défaut est FALSE. Définissez cette valeur à TRUE uniquement si tous les objets d’animation appartenant au groupe sont attribués dynamiquement avec l’opérateur nouveau.

```
BOOL m_bAutodestroyAnimationObjects;
```

## <a name="canimationgroupm_bautodestroykeyframes"></a><a name="m_bautodestroykeyframes"></a>CAnimationGroup::m_bAutodestroyKeyframes

Specifie comment détruire les cadres clés. Si cette valeur est VRAI, tous les cadres clés sont enlevés et détruits; sinon ils ne sont retirés de la liste que. La valeur par défaut est TRUE.

```
BOOL m_bAutodestroyKeyframes;
```

## <a name="canimationgroupm_lstanimationobjects"></a><a name="m_lstanimationobjects"></a>CAnimationGroup::m_lstAnimationObjects

Contient une liste d’objets d’animation.

```
CObList m_lstAnimationObjects;
```

## <a name="canimationgroupm_lstkeyframes"></a><a name="m_lstkeyframes"></a>CAnimationGroup::m_lstKeyFrames

Contient une liste de cadres clés.

```
CObList m_lstKeyFrames;
```

## <a name="canimationgroupm_ngroupid"></a><a name="m_ngroupid"></a>CAnimationGroup::m_nGroupID

Un identifiant unique du groupe d’animation.

```
UINT32 m_nGroupID;
```

## <a name="canimationgroupm_pparentcontroller"></a><a name="m_pparentcontroller"></a>CAnimationGroup::m_pParentController

Un pointeur au contrôleur d’animation auquel ce groupe appartient.

```
CAnimationController* m_pParentController;
```

## <a name="canimationgroupm_pstoryboard"></a><a name="m_pstoryboard"></a>CAnimationGroup::m_pStoryboard

Points à storyboard d’animation. Ce pointeur n’est valable qu’après l’appel sur Animate.

```
ATL::CComPtr<IUIAnimationStoryboard> m_pStoryboard;
```

## <a name="canimationgroupremovekeyframes"></a><a name="removekeyframes"></a>CAnimationGroup::RemoveKeyframes

Supprime et détruit optionnellement tous les cadres clés qui appartiennent à un groupe d’animation.

```
void RemoveKeyframes();
```

### <a name="remarks"></a>Notes

Si m_bAutodestroyKeyframes membre est VRAI, alors les cadres clés sont enlevés et détruits, sinon les cadres clés sont simplement retirés de la liste interne des cadres clés.

## <a name="canimationgroupremovetransitions"></a><a name="removetransitions"></a>CAnimationGroup::RemoveTransitions

Supprime les transitions des objets d’animation qui appartiennent à un groupe d’animation.

```
void RemoveTransitions();
```

### <a name="remarks"></a>Notes

Si m_bAutoclearTransitions drapeau est réglé sur TRUE, cette méthode boucle sur tous les objets d’animation qui appartiennent au groupe et appelle CAnimationObject:ClearTransitions (FALSE).

## <a name="canimationgroupschedule"></a><a name="schedule"></a>CAnimationGroup::Calendrier

Planifie une animation à l’heure spécifiée.

```
BOOL Schedule(IUIAnimationTimer* pTimer, UI_ANIMATION_SECONDS time);
```

### <a name="parameters"></a>Paramètres

*pTimer (en)*<br/>
Un pointeur à la minuterie d’animation.

*Temps*<br/>
Spécifie le temps de programmer l’animation.

### <a name="return-value"></a>Valeur de retour

VRAI si la méthode réussit; FALSE si la méthode échoue ou si Animate n’a pas été appelé avec bScheduleNow réglé à FALSE.

### <a name="remarks"></a>Notes

Appelez cette fonction pour planifier une animation à l’heure spécifiée. Vous devez appeler Animate avec bScheduleNow réglé à FALSE d’abord.

## <a name="canimationgroupsetautodestroytransitions"></a><a name="setautodestroytransitions"></a>CAnimationGroup::SetAutodestroyTransitions

Les directives de tous les objets d’animation appartenant au groupe détruisent automatiquement les transitions.

```
void SetAutodestroyTransitions(BOOL bAutoDestroy = TRUE);
```

### <a name="parameters"></a>Paramètres

*bAutoDestroy*<br/>
Précise comment détruire les transitions.

### <a name="remarks"></a>Notes

Définissez cette valeur à FALSE uniquement si vous allouez des transitions sur la pile. La valeur par défaut est VRAI, il est donc fortement recommandé d’allouer des objets de transition en utilisant l’opérateur nouveau.

## <a name="see-also"></a>Voir aussi

[Classes](../../mfc/reference/mfc-classes.md)
