---
description: 'En savoir plus sur : classe CAnimationGroup,'
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
ms.openlocfilehash: 45fd49b95f73811f52795b87bf3de2dd004fa5ee
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97336796"
---
# <a name="canimationgroup-class"></a>CAnimationGroup, classe

Implémente un groupe d’animation, qui combine un Storyboard d’animation, des objets d’animation et des transitions pour définir une animation.

## <a name="syntax"></a>Syntaxe

```
class CAnimationGroup;
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CAnimationGroup, :: CAnimationGroup,](#canimationgroup)|Construit un groupe d’animation.|
|[CAnimationGroup, :: ~ CAnimationGroup,](#_dtorcanimationgroup)|Destructeur. Appelé lorsqu’un groupe d’animation est en cours de destruction.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CAnimationGroup, :: Animate](#animate)|Anime un groupe.|
|[CAnimationGroup, :: ApplyTransitions](#applytransitions)|Applique des transitions aux objets d’animation.|
|[CAnimationGroup, :: FindAnimationObject](#findanimationobject)|Recherche un objet d’animation qui contient la variable d’animation spécifiée.|
|[CAnimationGroup, :: GetGroupID](#getgroupid)|Retourne GroupID.|
|[CAnimationGroup, :: RemoveKeyframes](#removekeyframes)|Supprime et éventuellement toutes les images clés qui appartiennent à un groupe d’animation.|
|[CAnimationGroup, :: RemoveTransitions](#removetransitions)|Supprime les transitions des objets d’animation qui appartiennent à un groupe d’animation.|
|[CAnimationGroup, :: Schedule](#schedule)|Planifie une animation à l’heure spécifiée.|
|[CAnimationGroup, :: SetAutodestroyTransitions](#setautodestroytransitions)|Dirige tous les objets d’animation qui appartiennent au groupe détruisant automatiquement les transitions.|

### <a name="protected-methods"></a>Méthodes protégées

|Nom|Description|
|----------|-----------------|
|[CAnimationGroup, :: AddKeyframes](#addkeyframes)|Application auxiliaire qui ajoute des images clés à une table de montage séquentiel.|
|[CAnimationGroup, :: AddTransitions](#addtransitions)|Application auxiliaire qui ajoute des transitions à une table de montage séquentiel.|
|[CAnimationGroup, :: CreateTransitions](#createtransitions)|Application auxiliaire qui crée des objets de transition COM.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CAnimationGroup, :: m_bAutoclearTransitions](#m_bautocleartransitions)|Spécifie comment effacer les transitions des objets d’animation qui appartiennent au groupe. Si ce membre a la valeur TRUE, les transitions sont supprimées automatiquement lorsqu’une animation a été planifiée. Dans le cas contraire, vous devez supprimer les transitions manuellement.|
|[CAnimationGroup, :: m_bAutodestroyAnimationObjects](#m_bautodestroyanimationobjects)|Spécifie comment détruire des objets d’animation. Si ce paramètre a la valeur TRUE, les objets d’animation sont détruits automatiquement lorsque le groupe est détruit. Sinon, les objets d’animation doivent être détruits manuellement. La valeur par défaut est FALSE. Définissez cette valeur sur TRUE uniquement si tous les objets d’animation qui appartiennent au groupe sont alloués dynamiquement avec l’opérateur New.|
|[CAnimationGroup, :: m_bAutodestroyKeyframes](#m_bautodestroykeyframes)|Spécifie comment détruire les images clés. Si cette valeur est TRUE, toutes les images clés sont supprimées et détruites ; dans le cas contraire, elles ne sont supprimées que dans la liste. La valeur par défaut est TRUE.|
|[CAnimationGroup, :: m_lstAnimationObjects](#m_lstanimationobjects)|Contient une liste d’objets d’animation.|
|[CAnimationGroup, :: m_lstKeyFrames](#m_lstkeyframes)|Contient une liste d’images clés.|
|[CAnimationGroup, :: m_pStoryboard](#m_pstoryboard)|Pointe vers le Storyboard d’animation. Ce pointeur est valide uniquement après l’appel d’Animate.|

### <a name="protected-data-members"></a>Membres de données protégés

|Nom|Description|
|----------|-----------------|
|[CAnimationGroup, :: m_nGroupID](#m_ngroupid)|Identificateur unique du groupe d’animation.|
|[CAnimationGroup, :: m_pParentController](#m_pparentcontroller)|Pointeur vers le contrôleur d’animation auquel appartient ce groupe.|

## <a name="remarks"></a>Notes

Les groupes d’animations sont créés automatiquement par le contrôleur d’animation (CAnimationController) quand vous ajoutez des objets d’animation à l’aide de CAnimationController :: AddAnimationObject. Un groupe d’animation est identifié par GroupID, qui est généralement utilisé comme paramètre pour manipuler des groupes d’animation. Le GroupID est extrait du premier objet d’animation ajouté à un nouveau groupe d’animation. Une table de montage séquentiel d’animation encapsulée est créée après l’appel de CAnimationController :: AnimateGroup et est accessible via un membre public m_pStoryboard.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`CAnimationGroup`

## <a name="requirements"></a>Spécifications

**En-tête :** afxanimationcontroller.h

## <a name="canimationgroupcanimationgroup"></a><a name="_dtorcanimationgroup"></a> CAnimationGroup, :: ~ CAnimationGroup,

Destructeur. Appelé lorsqu’un groupe d’animation est en cours de destruction.

```
~CAnimationGroup();
```

## <a name="canimationgroupaddkeyframes"></a><a name="addkeyframes"></a> CAnimationGroup, :: AddKeyframes

Application auxiliaire qui ajoute des images clés à une table de montage séquentiel.

```cpp
void AddKeyframes(IUIAnimationStoryboard* pStoryboard, BOOL bAddDeep);
```

### <a name="parameters"></a>Paramètres

*pStoryboard*<br/>
Pointeur vers un objet COM d’une table de montage séquentiel.

*bAddDeep*<br/>
Spécifie si cette méthode doit être ajoutée aux images clés de la table de montage séquentiel qui dépendent d’autres images clés.

## <a name="canimationgroupaddtransitions"></a><a name="addtransitions"></a> CAnimationGroup, :: AddTransitions

Application auxiliaire qui ajoute des transitions à une table de montage séquentiel.

```cpp
void AddTransitions(
    IUIAnimationStoryboard* pStoryboard,
    BOOL bDependOnKeyframes);
```

### <a name="parameters"></a>Paramètres

*pStoryboard*<br/>
Pointeur vers un objet COM d’une table de montage séquentiel.

*bDependOnKeyframes*

## <a name="canimationgroupanimate"></a><a name="animate"></a> CAnimationGroup, :: Animate

Anime un groupe.

```
BOOL Animate(
    IUIAnimationManager* pManager,
    IUIAnimationTimer* pTimer,
    BOOL bScheduleNow);
```

### <a name="parameters"></a>Paramètres

*pManager*<br/>
*ptimer* 
 *bScheduleNow*

### <a name="return-value"></a>Valeur renvoyée

TRUE si la méthode est réussie ; Sinon, FALSe.

### <a name="remarks"></a>Notes

Cette méthode crée un Storyboard interne, crée et applique des transitions et planifie une animation si bScheduleNow a la valeur TRUE. Si bScheduleNow a la valeur FALSe, vous devez appeler Schedule pour démarrer l’animation à l’heure spécifiée.

## <a name="canimationgroupapplytransitions"></a><a name="applytransitions"></a> CAnimationGroup, :: ApplyTransitions

Applique des transitions aux objets d’animation.

```cpp
void ApplyTransitions();
```

### <a name="remarks"></a>Notes

Cette méthode déclare en mode débogage si le Storyboard n’a pas été créé. Il crée tout d’abord toutes les transitions, puis ajoute les images clés « statiques » (images clés qui dépendent des décalages), ajoute des transitions qui ne dépendent pas des images clés, ajoute des images clés en fonction des transitions et des autres images clés, et ajoute des transitions qui dépendent d’images clés.

## <a name="canimationgroupcanimationgroup"></a><a name="canimationgroup"></a> CAnimationGroup, :: CAnimationGroup,

Construit un groupe d’animation.

```
CAnimationGroup(CAnimationController* pParentController, UINT32 nGroupID);
```

### <a name="parameters"></a>Paramètres

*pParentController*<br/>
Pointeur vers le contrôleur d’animation qui crée un groupe.

*nGroupID*<br/>
Spécifie GroupID.

## <a name="canimationgroupcreatetransitions"></a><a name="createtransitions"></a> CAnimationGroup, :: CreateTransitions

Application auxiliaire qui crée des objets de transition COM.

```
BOOL CreateTransitions();
```

### <a name="return-value"></a>Valeur renvoyée

TRUE si la méthode est réussie ; sinon, FALSe.

## <a name="canimationgroupfindanimationobject"></a><a name="findanimationobject"></a> CAnimationGroup, :: FindAnimationObject

Recherche un objet d’animation qui contient la variable d’animation spécifiée.

```
CAnimationBaseObject* FindAnimationObject(IUIAnimationVariable* pVariable);
```

### <a name="parameters"></a>Paramètres

*pVariable*<br/>
Pointeur vers une variable d’animation.

### <a name="return-value"></a>Valeur renvoyée

Pointeur vers un objet d’animation, ou NULL si l’objet d’animation est introuvable.

## <a name="canimationgroupgetgroupid"></a><a name="getgroupid"></a> CAnimationGroup, :: GetGroupID

Retourne GroupID.

```
UINT32 GetGroupID() const;
```

### <a name="return-value"></a>Valeur renvoyée

Identificateur de groupe.

## <a name="canimationgroupm_bautocleartransitions"></a><a name="m_bautocleartransitions"></a> CAnimationGroup, :: m_bAutoclearTransitions

Spécifie comment effacer les transitions des objets d’animation qui appartiennent au groupe. Si ce membre a la valeur TRUE, les transitions sont supprimées automatiquement lorsqu’une animation a été planifiée. Dans le cas contraire, vous devez supprimer les transitions manuellement.

```
BOOL m_bAutoclearTransitions;
```

## <a name="canimationgroupm_bautodestroyanimationobjects"></a><a name="m_bautodestroyanimationobjects"></a> CAnimationGroup, :: m_bAutodestroyAnimationObjects

Spécifie comment détruire des objets d’animation. Si ce paramètre a la valeur TRUE, les objets d’animation sont détruits automatiquement lorsque le groupe est détruit. Sinon, les objets d’animation doivent être détruits manuellement. La valeur par défaut est FALSE. Définissez cette valeur sur TRUE uniquement si tous les objets d’animation qui appartiennent au groupe sont alloués dynamiquement avec l’opérateur New.

```
BOOL m_bAutodestroyAnimationObjects;
```

## <a name="canimationgroupm_bautodestroykeyframes"></a><a name="m_bautodestroykeyframes"></a> CAnimationGroup, :: m_bAutodestroyKeyframes

Spécifie comment détruire les images clés. Si cette valeur est TRUE, toutes les images clés sont supprimées et détruites ; dans le cas contraire, elles ne sont supprimées que dans la liste. La valeur par défaut est TRUE.

```
BOOL m_bAutodestroyKeyframes;
```

## <a name="canimationgroupm_lstanimationobjects"></a><a name="m_lstanimationobjects"></a> CAnimationGroup, :: m_lstAnimationObjects

Contient une liste d’objets d’animation.

```
CObList m_lstAnimationObjects;
```

## <a name="canimationgroupm_lstkeyframes"></a><a name="m_lstkeyframes"></a> CAnimationGroup, :: m_lstKeyFrames

Contient une liste d’images clés.

```
CObList m_lstKeyFrames;
```

## <a name="canimationgroupm_ngroupid"></a><a name="m_ngroupid"></a> CAnimationGroup, :: m_nGroupID

Identificateur unique du groupe d’animation.

```
UINT32 m_nGroupID;
```

## <a name="canimationgroupm_pparentcontroller"></a><a name="m_pparentcontroller"></a> CAnimationGroup, :: m_pParentController

Pointeur vers le contrôleur d’animation auquel appartient ce groupe.

```
CAnimationController* m_pParentController;
```

## <a name="canimationgroupm_pstoryboard"></a><a name="m_pstoryboard"></a> CAnimationGroup, :: m_pStoryboard

Pointe vers le Storyboard d’animation. Ce pointeur est valide uniquement après l’appel d’Animate.

```
ATL::CComPtr<IUIAnimationStoryboard> m_pStoryboard;
```

## <a name="canimationgroupremovekeyframes"></a><a name="removekeyframes"></a> CAnimationGroup, :: RemoveKeyframes

Supprime et éventuellement toutes les images clés qui appartiennent à un groupe d’animation.

```cpp
void RemoveKeyframes();
```

### <a name="remarks"></a>Notes

Si m_bAutodestroyKeyframes membre a la valeur TRUE, les images clés sont supprimées et détruites, sinon les images clés sont simplement supprimées de la liste interne des images clés.

## <a name="canimationgroupremovetransitions"></a><a name="removetransitions"></a> CAnimationGroup, :: RemoveTransitions

Supprime les transitions des objets d’animation qui appartiennent à un groupe d’animation.

```cpp
void RemoveTransitions();
```

### <a name="remarks"></a>Notes

Si m_bAutoclearTransitions indicateur a la valeur TRUE, cette méthode effectue une boucle sur tous les objets d’animation qui appartiennent au groupe et appelle CAnimationObject :: ClearTransitions (FALSe).

## <a name="canimationgroupschedule"></a><a name="schedule"></a> CAnimationGroup, :: Schedule

Planifie une animation à l’heure spécifiée.

```
BOOL Schedule(IUIAnimationTimer* pTimer, UI_ANIMATION_SECONDS time);
```

### <a name="parameters"></a>Paramètres

*pTimer*<br/>
Pointeur vers le minuteur d’animation.

*time*<br/>
Spécifie l’heure de planification de l’animation.

### <a name="return-value"></a>Valeur renvoyée

TRUE si la méthode est réussie ; FALSe si la méthode échoue ou si l’animation n’a pas été appelée avec bScheduleNow défini sur FALSe.

### <a name="remarks"></a>Notes

Appelez cette fonction pour planifier une animation à l’heure spécifiée. Vous devez d’abord appeler Animate avec bScheduleNow avec la valeur FALSe.

## <a name="canimationgroupsetautodestroytransitions"></a><a name="setautodestroytransitions"></a> CAnimationGroup, :: SetAutodestroyTransitions

Dirige tous les objets d’animation qui appartiennent au groupe détruisant automatiquement les transitions.

```cpp
void SetAutodestroyTransitions(BOOL bAutoDestroy = TRUE);
```

### <a name="parameters"></a>Paramètres

*bAutoDestroy*<br/>
Spécifie comment détruire des transitions.

### <a name="remarks"></a>Notes

Affectez la valeur FALSe uniquement si vous allouez des transitions sur la pile. La valeur par défaut est TRUE, c’est pourquoi il est fortement recommandé d’allouer des objets de transition à l’aide de operator new.

## <a name="see-also"></a>Voir aussi

[Classes](../../mfc/reference/mfc-classes.md)
