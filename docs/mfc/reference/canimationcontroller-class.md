---
description: 'En savoir plus sur : classe CAnimationController'
title: CAnimationController, classe
ms.date: 03/27/2019
f1_keywords:
- CAnimationController
- AFXANIMATIONCONTROLLER/CAnimationController
- AFXANIMATIONCONTROLLER/CAnimationController::CAnimationController
- AFXANIMATIONCONTROLLER/CAnimationController::AddAnimationObject
- AFXANIMATIONCONTROLLER/CAnimationController::AddKeyframeToGroup
- AFXANIMATIONCONTROLLER/CAnimationController::AnimateGroup
- AFXANIMATIONCONTROLLER/CAnimationController::CleanUpGroup
- AFXANIMATIONCONTROLLER/CAnimationController::CreateKeyframe
- AFXANIMATIONCONTROLLER/CAnimationController::EnableAnimationManagerEvent
- AFXANIMATIONCONTROLLER/CAnimationController::EnableAnimationTimerEventHandler
- AFXANIMATIONCONTROLLER/CAnimationController::EnablePriorityComparisonHandler
- AFXANIMATIONCONTROLLER/CAnimationController::EnableStoryboardEventHandler
- AFXANIMATIONCONTROLLER/CAnimationController::FindAnimationGroup
- AFXANIMATIONCONTROLLER/CAnimationController::FindAnimationObject
- AFXANIMATIONCONTROLLER/CAnimationController::GetKeyframeStoryboardStart
- AFXANIMATIONCONTROLLER/CAnimationController::GetUIAnimationManager
- AFXANIMATIONCONTROLLER/CAnimationController::GetUIAnimationTimer
- AFXANIMATIONCONTROLLER/CAnimationController::GetUITransitionFactory
- AFXANIMATIONCONTROLLER/CAnimationController::GetUITransitionLibrary
- AFXANIMATIONCONTROLLER/CAnimationController::IsAnimationInProgress
- AFXANIMATIONCONTROLLER/CAnimationController::IsValid
- AFXANIMATIONCONTROLLER/CAnimationController::OnAnimationIntegerValueChanged
- AFXANIMATIONCONTROLLER/CAnimationController::OnAnimationManagerStatusChanged
- AFXANIMATIONCONTROLLER/CAnimationController::OnAnimationTimerPostUpdate
- AFXANIMATIONCONTROLLER/CAnimationController::OnAnimationTimerPreUpdate
- AFXANIMATIONCONTROLLER/CAnimationController::OnAnimationTimerRenderingTooSlow
- AFXANIMATIONCONTROLLER/CAnimationController::OnAnimationValueChanged
- AFXANIMATIONCONTROLLER/CAnimationController::OnBeforeAnimationStart
- AFXANIMATIONCONTROLLER/CAnimationController::OnHasPriorityCancel
- AFXANIMATIONCONTROLLER/CAnimationController::OnHasPriorityCompress
- AFXANIMATIONCONTROLLER/CAnimationController::OnHasPriorityConclude
- AFXANIMATIONCONTROLLER/CAnimationController::OnHasPriorityTrim
- AFXANIMATIONCONTROLLER/CAnimationController::OnStoryboardStatusChanged
- AFXANIMATIONCONTROLLER/CAnimationController::OnStoryboardUpdated
- AFXANIMATIONCONTROLLER/CAnimationController::RemoveAllAnimationGroups
- AFXANIMATIONCONTROLLER/CAnimationController::RemoveAnimationGroup
- AFXANIMATIONCONTROLLER/CAnimationController::RemoveAnimationObject
- AFXANIMATIONCONTROLLER/CAnimationController::RemoveTransitions
- AFXANIMATIONCONTROLLER/CAnimationController::ScheduleGroup
- AFXANIMATIONCONTROLLER/CAnimationController::SetRelatedWnd
- AFXANIMATIONCONTROLLER/CAnimationController::UpdateAnimationManager
- AFXANIMATIONCONTROLLER/CAnimationController::OnAfterSchedule
- AFXANIMATIONCONTROLLER/CAnimationController::gkeyframeStoryboardStart
- AFXANIMATIONCONTROLLER/CAnimationController::m_bIsValid
- AFXANIMATIONCONTROLLER/CAnimationController::m_lstAnimationGroups
- AFXANIMATIONCONTROLLER/CAnimationController::m_pAnimationManager
- AFXANIMATIONCONTROLLER/CAnimationController::m_pAnimationTimer
- AFXANIMATIONCONTROLLER/CAnimationController::m_pRelatedWnd
- AFXANIMATIONCONTROLLER/CAnimationController::m_pTransitionFactory
- AFXANIMATIONCONTROLLER/CAnimationController::m_pTransitionLibrary
helpviewer_keywords:
- CAnimationController [MFC], CAnimationController
- CAnimationController [MFC], AddAnimationObject
- CAnimationController [MFC], AddKeyframeToGroup
- CAnimationController [MFC], AnimateGroup
- CAnimationController [MFC], CleanUpGroup
- CAnimationController [MFC], CreateKeyframe
- CAnimationController [MFC], EnableAnimationManagerEvent
- CAnimationController [MFC], EnableAnimationTimerEventHandler
- CAnimationController [MFC], EnablePriorityComparisonHandler
- CAnimationController [MFC], EnableStoryboardEventHandler
- CAnimationController [MFC], FindAnimationGroup
- CAnimationController [MFC], FindAnimationObject
- CAnimationController [MFC], GetKeyframeStoryboardStart
- CAnimationController [MFC], GetUIAnimationManager
- CAnimationController [MFC], GetUIAnimationTimer
- CAnimationController [MFC], GetUITransitionFactory
- CAnimationController [MFC], GetUITransitionLibrary
- CAnimationController [MFC], IsAnimationInProgress
- CAnimationController [MFC], IsValid
- CAnimationController [MFC], OnAnimationIntegerValueChanged
- CAnimationController [MFC], OnAnimationManagerStatusChanged
- CAnimationController [MFC], OnAnimationTimerPostUpdate
- CAnimationController [MFC], OnAnimationTimerPreUpdate
- CAnimationController [MFC], OnAnimationTimerRenderingTooSlow
- CAnimationController [MFC], OnAnimationValueChanged
- CAnimationController [MFC], OnBeforeAnimationStart
- CAnimationController [MFC], OnHasPriorityCancel
- CAnimationController [MFC], OnHasPriorityCompress
- CAnimationController [MFC], OnHasPriorityConclude
- CAnimationController [MFC], OnHasPriorityTrim
- CAnimationController [MFC], OnStoryboardStatusChanged
- CAnimationController [MFC], OnStoryboardUpdated
- CAnimationController [MFC], RemoveAllAnimationGroups
- CAnimationController [MFC], RemoveAnimationGroup
- CAnimationController [MFC], RemoveAnimationObject
- CAnimationController [MFC], RemoveTransitions
- CAnimationController [MFC], ScheduleGroup
- CAnimationController [MFC], SetRelatedWnd
- CAnimationController [MFC], UpdateAnimationManager
- CAnimationController [MFC], CleanUpGroup
- CAnimationController [MFC], OnAfterSchedule
- CAnimationController [MFC], gkeyframeStoryboardStart
- CAnimationController [MFC], m_bIsValid
- CAnimationController [MFC], m_lstAnimationGroups
- CAnimationController [MFC], m_pAnimationManager
- CAnimationController [MFC], m_pAnimationTimer
- CAnimationController [MFC], m_pRelatedWnd
- CAnimationController [MFC], m_pTransitionFactory
- CAnimationController [MFC], m_pTransitionLibrary
ms.assetid: ed294c98-695e-40a6-b940-33ef1d40aa6b
ms.openlocfilehash: 30754084ff62a06ef38d16e555ea32a585bb5b52
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97254753"
---
# <a name="canimationcontroller-class"></a>CAnimationController, classe

Implémente le contrôleur de l'animation, qui propose une interface centrale pour créer et gérer des animations.

## <a name="syntax"></a>Syntaxe

```
class CAnimationController : public CObject;
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CAnimationController :: CAnimationController](#canimationcontroller)|Construit un contrôleur d’animation.|
|[CAnimationController :: ~ CAnimationController](#_dtorcanimationcontroller)|Destructeur. Appelé lorsque l’objet contrôleur de l’animation est détruit.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CAnimationController :: AddAnimationObject](#addanimationobject)|Ajoute un objet d’animation à un groupe qui appartient au contrôleur d’animation.|
|[CAnimationController :: AddKeyframeToGroup](#addkeyframetogroup)|Ajoute une image clé au groupe.|
|[CAnimationController :: AnimateGroup](#animategroup)|Prépare un groupe pour exécuter l’animation et le planifie éventuellement.|
|[CAnimationController :: CleanUpGroup](#cleanupgroup)|Surchargé. Appelé par l’infrastructure pour nettoyer le groupe lorsque l’animation a été planifiée.|
|[CAnimationController::CreateKeyframe](#createkeyframe)|Surchargé. Crée une image clé qui dépend de la transition et l’ajoute au groupe spécifié.|
|[CAnimationController :: EnableAnimationManagerEvent](#enableanimationmanagerevent)|Définit ou libère un gestionnaire à appeler lorsque l’état du gestionnaire d’animations change.|
|[CAnimationController :: EnableAnimationTimerEventHandler](#enableanimationtimereventhandler)|Définit ou libère un gestionnaire pour les événements de minutage et le gestionnaire pour les mises à jour de minutage.|
|[CAnimationController :: EnablePriorityComparisonHandler](#enableprioritycomparisonhandler)|Définit ou libère le gestionnaire de comparaison de priorité à appeler pour déterminer si une table de montage séquentiel planifiée peut être annulée, terminée, tronquée ou compressée.|
|[CAnimationController :: EnableStoryboardEventHandler](#enablestoryboardeventhandler)|Définit ou libère un gestionnaire pour l’état de la table de montage séquentiel et les événements de mise à jour.|
|[CAnimationController :: FindAnimationGroup](#findanimationgroup)|Surchargé. Recherche un groupe d’animations par son Storyboard.|
|[CAnimationController :: FindAnimationObject](#findanimationobject)|Recherche un objet d’animation contenant une variable d’animation spécifiée.|
|[CAnimationController :: GetKeyframeStoryboardStart](#getkeyframestoryboardstart)|Retourne une image clé qui identifie le début du Storyboard.|
|[CAnimationController :: GetUIAnimationManager](#getuianimationmanager)|Fournit l’accès à l’objet IUIAnimationManager encapsulé.|
|[CAnimationController :: GetUIAnimationTimer](#getuianimationtimer)|Fournit l’accès à l’objet IUIAnimationTimer encapsulé.|
|[CAnimationController :: GetUITransitionFactory](#getuitransitionfactory)|Pointeur vers l’interface IUIAnimationTransitionFactory ou NULL, en cas d’échec de la création de la bibliothèque de transition.|
|[CAnimationController :: GetUITransitionLibrary](#getuitransitionlibrary)|Fournit l’accès à l’objet IUIAnimationTransitionLibrary encapsulé.|
|[CAnimationController :: IsAnimationInProgress](#isanimationinprogress)|Indique si au moins un groupe lit l’animation.|
|[CAnimationController :: IsValid](#isvalid)|Indique si le contrôleur d’animation est valide.|
|[CAnimationController :: OnAnimationIntegerValueChanged](#onanimationintegervaluechanged)|Appelé par l’infrastructure lorsque la valeur entière de la variable d’animation a changé.|
|[CAnimationController :: OnAnimationManagerStatusChanged](#onanimationmanagerstatuschanged)|Appelée par l’infrastructure en réponse à l’événement StatusChanged à partir du gestionnaire d’animations.|
|[CAnimationController :: OnAnimationTimerPostUpdate](#onanimationtimerpostupdate)|Appelé par l’infrastructure une fois la mise à jour d’une animation terminée.|
|[CAnimationController :: OnAnimationTimerPreUpdate](#onanimationtimerpreupdate)|Appelé par le Framework avant le début d’une mise à jour d’animation.|
|[CAnimationController :: OnAnimationTimerRenderingTooSlow](#onanimationtimerrenderingtooslow)|Appelée par l’infrastructure lorsque la fréquence d’images de rendu d’une animation passe sous une fréquence d’images minimale désirable.|
|[CAnimationController :: OnAnimationValueChanged](#onanimationvaluechanged)|Appelé par le Framework lorsque la valeur de la variable d’animation a changé.|
|[CAnimationController :: OnBeforeAnimationStart](#onbeforeanimationstart)|Appelée par le Framework juste avant que l’animation soit planifiée.|
|[CAnimationController :: OnHasPriorityCancel](#onhasprioritycancel)|Appelé par l'infrastructure pour résoudre les conflits de planification.|
|[CAnimationController :: OnHasPriorityCompress](#onhasprioritycompress)|Appelé par l'infrastructure pour résoudre les conflits de planification.|
|[CAnimationController :: OnHasPriorityConclude](#onhaspriorityconclude)|Appelé par l'infrastructure pour résoudre les conflits de planification.|
|[CAnimationController :: OnHasPriorityTrim](#onhasprioritytrim)|Appelé par l'infrastructure pour résoudre les conflits de planification.|
|[CAnimationController :: OnStoryboardStatusChanged](#onstoryboardstatuschanged)|Appelé par le Framework lorsque l’état de la table de montage séquentiel a changé.|
|[CAnimationController :: OnStoryboardUpdated](#onstoryboardupdated)|Appelé par le Framework lorsque le Storyboard a été mis à jour.|
|[CAnimationController :: RemoveAllAnimationGroups](#removeallanimationgroups)|Supprime tous les groupes d’animations du contrôleur d’animation.|
|[CAnimationController :: RemoveAnimationGroup](#removeanimationgroup)|Supprime un groupe d’animation avec l’ID spécifié du contrôleur d’animation.|
|[CAnimationController :: RemoveAnimationObject](#removeanimationobject)|Supprimer un objet d’animation du contrôleur d’animation.|
|[CAnimationController :: RemoveTransitions](#removetransitions)|Supprime les transitions des objets d’animation qui appartiennent au groupe spécifié.|
|[CAnimationController :: ScheduleGroup](#schedulegroup)|Planifie une animation.|
|[CAnimationController :: SetRelatedWnd](#setrelatedwnd)|Établit une relation entre le contrôleur d’animation et une fenêtre.|
|[CAnimationController :: UpdateAnimationManager](#updateanimationmanager)|Indique au gestionnaire d’animations de mettre à jour les valeurs de toutes les variables d’animation.|

### <a name="protected-methods"></a>Méthodes protégées

|Nom|Description|
|----------|-----------------|
|[CAnimationController :: CleanUpGroup](#cleanupgroup)|Surchargé. Un programme d’assistance qui nettoie le groupe.|
|[CAnimationController :: OnAfterSchedule](#onafterschedule)|Appelé par le Framework lorsqu’une animation pour le groupe spécifié vient d’être planifiée.|

### <a name="protected-data-members"></a>Membres de données protégés

|Nom|Description|
|----------|-----------------|
|[CAnimationController :: gkeyframeStoryboardStart](#g_keyframestoryboardstart)|Image clé qui représente le début du Storyboard.|
|[CAnimationController :: m_bIsValid](#m_bisvalid)|Spécifie si un contrôleur d’animation est valide ou non. Ce membre a la valeur FALSe si le système d’exploitation actuel ne prend pas en charge l’API d’animation Windows.|
|[CAnimationController :: m_lstAnimationGroups](#m_lstanimationgroups)|Liste des groupes d’animations qui appartiennent à ce contrôleur d’animation.|
|[CAnimationController :: m_pAnimationManager](#m_panimationmanager)|Stocke un pointeur vers l’objet COM du gestionnaire d’animations.|
|[CAnimationController :: m_pAnimationTimer](#m_panimationtimer)|Stocke un pointeur vers l’objet COM du minuteur d’animation.|
|[CAnimationController :: m_pRelatedWnd](#m_prelatedwnd)|Pointeur vers un objet CWnd connexe, qui peut être redessiné automatiquement lorsque l’état du gestionnaire d’animations a changé ou lorsque l’événement de publication de mise à jour s’est produit. Sa valeur peut être NULL.|
|[CAnimationController :: m_pTransitionFactory](#m_ptransitionfactory)|Stocke un pointeur vers l’objet COM de la fabrique de transition.|
|[CAnimationController :: m_pTransitionLibrary](#m_ptransitionlibrary)|Stocke un pointeur vers l’objet COM de la bibliothèque de transitions.|

## <a name="remarks"></a>Notes

La classe CAnimationController est la classe de clé qui gère les animations. Vous pouvez créer une ou plusieurs instances du contrôleur d’animation dans une application et, si vous le souhaitez, connecter une instance du contrôleur d’animation à un objet CWnd à l’aide de CAnimationController :: SetRelatedWnd. Cette connexion est requise pour envoyer automatiquement des messages WM_PAINT à la fenêtre associée lorsque l’état du gestionnaire d’animations a changé ou que le minuteur d’animation a été mis à jour. Si vous n’activez pas cette relation, vous devez redessiner une fenêtre qui affiche une animation manuellement. À cet effet, vous pouvez dériver une classe de CAnimationController et remplacer OnAnimationManagerStatusChanged et/ou OnAnimationTimerPostUpdate et invalider une ou plusieurs fenêtres si nécessaire.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

`CAnimationController`

## <a name="requirements"></a>Spécifications

**En-tête :** afxanimationcontroller.h

## <a name="canimationcontrollercanimationcontroller"></a><a name="_dtorcanimationcontroller"></a> CAnimationController :: ~ CAnimationController

Destructeur. Appelé lorsque l’objet contrôleur de l’animation est détruit.

```
virtual ~CAnimationController(void);
```

## <a name="canimationcontrolleraddanimationobject"></a><a name="addanimationobject"></a> CAnimationController :: AddAnimationObject

Ajoute un objet d’animation à un groupe qui appartient au contrôleur d’animation.

```
CAnimationGroup* AddAnimationObject(CAnimationBaseObject* pObject);
```

### <a name="parameters"></a>Paramètres

*pObject*<br/>
Pointeur vers un objet d’animation.

### <a name="return-value"></a>Valeur renvoyée

Pointeur vers un groupe d’animation existant ou nouveau où pObject a été ajouté si la fonction réussit ; NULL si pObject a déjà été ajouté à un groupe qui appartient à un autre contrôleur d’animation.

### <a name="remarks"></a>Notes

Appelez cette méthode pour ajouter un objet d’animation au contrôleur d’animation. Un objet est ajouté à un groupe en fonction du GroupID de l’objet (consultez CAnimationBaseObject, :: SetID). Le contrôleur d’animation crée un nouveau groupe s’il s’agit du premier objet ajouté avec le GroupID spécifié. Un objet d’animation ne peut être ajouté qu’à un seul contrôleur d’animation. Si vous devez ajouter un objet à un autre contrôleur, appelez d’abord RemoveAnimationObject. Si vous appelez SetID avec New GroupID pour un objet qui a déjà été ajouté à un groupe, l’objet est supprimé de l’ancien groupe et ajouté à un autre groupe avec l’ID spécifié.

## <a name="canimationcontrolleraddkeyframetogroup"></a><a name="addkeyframetogroup"></a> CAnimationController :: AddKeyframeToGroup

Ajoute une image clé au groupe.

```
BOOL AddKeyframeToGroup(
    UINT32 nGroupID,
    CBaseKeyFrame* pKeyframe);
```

### <a name="parameters"></a>Paramètres

*nGroupID*<br/>
Spécifie l’ID de groupe.

*pKeyframe*<br/>
Pointeur vers une image clé.

### <a name="return-value"></a>Valeur renvoyée

TRUE si la fonction est réussie ; Sinon, FALSe.

### <a name="remarks"></a>Notes

En règle générale, vous n’avez pas besoin d’appeler cette méthode, utilisez CAnimationController :: CreateKeyframe à la place, qui crée et ajoute automatiquement l’image clé créée à un groupe.

## <a name="canimationcontrolleranimategroup"></a><a name="animategroup"></a> CAnimationController :: AnimateGroup

Prépare un groupe pour exécuter l’animation et le planifie éventuellement.

```
BOOL AnimateGroup(
    UINT32 nGroupID,
    BOOL bScheduleNow = TRUE);
```

### <a name="parameters"></a>Paramètres

*nGroupID*<br/>
Spécifie GroupID.

*bScheduleNow*<br/>
Spécifie si l’animation doit être exécutée immédiatement.

### <a name="return-value"></a>Valeur renvoyée

TRUE si l’animation a été correctement planifiée et exécutée.

### <a name="remarks"></a>Notes

Cette méthode effectue le travail réel qui crée le Storyboard, ajoute des variables d’animation, applique des transitions et définit des images clés. Il est possible de retarder la planification si vous affectez à bScheduleNow la valeur FALSe. Dans ce cas, le groupe spécifié contiendra une table de montage séquentiel qui a été configurée pour l’animation. À ce stade, vous pouvez configurer des événements pour les variables de Storyboard et d’animation. Lorsque vous devez réellement exécuter l’appel d’animation CAnimationController :: ScheduleGroup.

## <a name="canimationcontrollercanimationcontroller"></a><a name="canimationcontroller"></a> CAnimationController :: CAnimationController

Construit un contrôleur d’animation.

```
CAnimationController(void);
```

## <a name="canimationcontrollercleanupgroup"></a><a name="cleanupgroup"></a> CAnimationController :: CleanUpGroup

Appelé par l’infrastructure pour nettoyer le groupe lorsque l’animation a été planifiée.

```cpp
void CleanUpGroup(UINT32 nGroupID);
void CleanUpGroup(CAnimationGroup* pGroup);
```

### <a name="parameters"></a>Paramètres

*nGroupID*<br/>
Spécifie GroupID.

*pGroup*<br/>
Pointeur vers le groupe d’animation à nettoyer.

### <a name="remarks"></a>Notes

Cette méthode supprime toutes les transitions et toutes les images clés du groupe spécifié, car elles ne sont pas pertinentes après la planification d’une animation.

## <a name="canimationcontrollercreatekeyframe"></a><a name="createkeyframe"></a> CAnimationController :: CreateKeyframe

Crée une image clé qui dépend de la transition et l’ajoute au groupe spécifié.

```
CKeyFrame* CreateKeyframe(
    UINT32 nGroupID,
    CBaseTransition* pTransition);

CKeyFrame* CreateKeyframe(
    UINT32 nGroupID,
    CBaseKeyFrame* pKeyframe,
    UI_ANIMATION_SECONDS offset = 0.0);
```

### <a name="parameters"></a>Paramètres

*nGroupID*<br/>
Spécifie l’ID de groupe pour lequel l’image clé est créée.

*pTransition*<br/>
Pointeur vers la transition. L’image clé sera insérée dans le plan conceptuel après cette transition.

*pKeyframe*<br/>
Pointeur vers l’image clé de base pour cette image clé.

*offset*<br/>
Décalage en secondes à partir de l’image clé de base spécifiée par pKeyframe.

### <a name="return-value"></a>Valeur renvoyée

Pointeur vers l’image clé nouvellement créée si la fonction réussit.

### <a name="remarks"></a>Notes

Vous pouvez stocker le pointeur retourné et baser les autres images clés sur l’image clé nouvellement créée (voir la deuxième surcharge). Il est possible de commencer des transitions au niveau des images clés : voir CBaseTransition::SetKeyframes. Vous n’avez pas besoin de supprimer les images clés créées de cette façon, car elles sont automatiquement supprimées par les groupes d’animation. Soyez prudent lors de la création d’images clés basées sur d’autres images clés et d’autres transitions, et évitez les références circulaires.

## <a name="canimationcontrollerenableanimationmanagerevent"></a><a name="enableanimationmanagerevent"></a> CAnimationController :: EnableAnimationManagerEvent

Définit ou libère un gestionnaire à appeler lorsque l’état du gestionnaire d’animations change.

```
virtual BOOL EnableAnimationManagerEvent(BOOL bEnable = TRUE);
```

### <a name="parameters"></a>Paramètres

*bEnable*<br/>
Spécifie s’il faut définir ou libérer un gestionnaire.

### <a name="return-value"></a>Valeur renvoyée

TRUE si le gestionnaire a été correctement défini ou libéré.

### <a name="remarks"></a>Notes

Lorsqu’un gestionnaire est défini (activé), l’animation Windows appelle OnAnimationManagerStatusChanged quand l’état du gestionnaire d’animations change.

## <a name="canimationcontrollerenableanimationtimereventhandler"></a><a name="enableanimationtimereventhandler"></a> CAnimationController :: EnableAnimationTimerEventHandler

Définit ou libère un gestionnaire pour les événements de minutage et le gestionnaire pour les mises à jour de minutage.

```
virtual BOOL EnableAnimationTimerEventHandler(
    BOOL bEnable = TRUE,
    UI_ANIMATION_IDLE_BEHAVIOR idleBehavior = UI_ANIMATION_IDLE_BEHAVIOR_DISABLE);
```

### <a name="parameters"></a>Paramètres

*bEnable*<br/>
Spécifie s’il faut définir ou libérer les gestionnaires.

*idleBehavior*<br/>
Spécifie le comportement inactif du gestionnaire de mise à jour du minuteur.

### <a name="return-value"></a>Valeur renvoyée

TRUE si les gestionnaires ont été correctement définis ou libérés ; FALSe si cette méthode est appelée pour une deuxième fois sans libérer d’abord les gestionnaires, ou si une autre erreur se produit.

### <a name="remarks"></a>Notes

Lorsque les gestionnaires sont définis (activés), l’API d’animation Windows appelle les méthodes OnAnimationTimerPreUpdate, OnAnimationTimerPostUpdate et OnRenderingTooSlow. Vous devez activer les minuteurs d’animation pour autoriser les storyboards de mise à jour de l’API d’animation Windows. Dans le cas contraire, vous devrez appeler CAnimationController :: UpdateAnimationManager pour indiquer au gestionnaire d’animations de mettre à jour les valeurs de toutes les variables d’animation.

## <a name="canimationcontrollerenableprioritycomparisonhandler"></a><a name="enableprioritycomparisonhandler"></a> CAnimationController :: EnablePriorityComparisonHandler

Définit ou libère le gestionnaire de comparaison de priorité à appeler pour déterminer si une table de montage séquentiel planifiée peut être annulée, terminée, tronquée ou compressée.

```
virtual BOOL EnablePriorityComparisonHandler(DWORD dwHandlerType);
```

### <a name="parameters"></a>Paramètres

*dwHandlerType*<br/>
Combinaison d’indicateurs UI_ANIMATION_PHT_ (consultez la section Notes), qui spécifie les gestionnaires à définir ou à libérer.

### <a name="return-value"></a>Valeur renvoyée

TRUE si le gestionnaire a été correctement défini ou libéré.

### <a name="remarks"></a>Notes

Lorsqu’un gestionnaire est défini (activé), l’animation Windows appelle les méthodes virtuelles suivantes en fonction de dwHandlerType : OnHasPriorityCancel, OnHasPriorityConclude, OnHasPriorityTrim, OnHasPriorityCompress. dwHandler peut être une combinaison des indicateurs suivants : UI_ANIMATION_PHT_NONE-libérer tous les gestionnaires UI_ANIMATION_PHT_CANCEL-SET CANCEL Comparison Handler UI_ANIMATION_PHT_CONCLUDE-Set conclut Comparison Handler UI_ANIMATION_PHT_COMPRESS-Set compresser Handler UI_ANIMATION_PHT_TRIM-Set Trim Comparison Handler UI_ANIMATION_PHT_CANCEL_REMOVE-Remove Cancel compare Handler UI_ANIMATION_PHT_CONCLUDE_REMOVE-Remove conclut Comparison Handler UI_ANIMATION_PHT_COMPRESS_REMOVE-Remove compresse Comparison Handler UI_ANIMATION_PHT_TRIM_REMOVE- supprimer le gestionnaire de comparaison de découpage

## <a name="canimationcontrollerenablestoryboardeventhandler"></a><a name="enablestoryboardeventhandler"></a> CAnimationController :: EnableStoryboardEventHandler

Définit ou libère un gestionnaire pour l’état de la table de montage séquentiel et les événements de mise à jour.

```
virtual BOOL EnableStoryboardEventHandler(
    UINT32 nGroupID,
    BOOL bEnable = TRUE);
```

### <a name="parameters"></a>Paramètres

*nGroupID*<br/>
Spécifie l’ID de groupe.

*bEnable*<br/>
Spécifie s’il faut définir ou libérer un gestionnaire.

### <a name="return-value"></a>Valeur renvoyée

TRUE si le gestionnaire a été correctement défini ou libéré ; FALSe si le groupe d’animation spécifié est maintenant trouvé ou si l’animation pour le groupe spécifié n’a pas été lancée et que son storyboard interne a la valeur NULL.

### <a name="remarks"></a>Notes

Lorsqu’un gestionnaire est défini (activé), les méthodes virtuelles OnStoryboardStatusChanges et OnStoryboardUpdated sont appelées par l’API d’animation Windows. Un gestionnaire doit être défini après l’appel de CAnimationController :: Animate pour le groupe d’animations spécifié, car il crée l’objet IUIAnimationStoryboard encapsulé.

## <a name="canimationcontrollerfindanimationgroup"></a><a name="findanimationgroup"></a> CAnimationController :: FindAnimationGroup

Recherche un groupe d’animations par son ID de groupe.

```
CAnimationGroup* FindAnimationGroup(UINT32 nGroupID);
CAnimationGroup* FindAnimationGroup(IUIAnimationStoryboard* pStoryboard);
```

### <a name="parameters"></a>Paramètres

*nGroupID*<br/>
Spécifie un GroupID.

*pStoryboard*<br/>
Pointeur vers une table de montage séquentiel.

### <a name="return-value"></a>Valeur renvoyée

Pointeur vers le groupe d’animation ou NULL si le groupe avec l’ID spécifié est introuvable.

### <a name="remarks"></a>Notes

Utilisez cette méthode pour rechercher un groupe d’animations au moment de l’exécution. Un groupe est créé et ajouté à la liste interne des groupes d’animations lorsqu’un premier objet d’animation avec GroupID particulier est ajouté au contrôleur d’animation.

## <a name="canimationcontrollerfindanimationobject"></a><a name="findanimationobject"></a> CAnimationController :: FindAnimationObject

Recherche un objet d’animation contenant une variable d’animation spécifiée.

```
BOOL FindAnimationObject(
    IUIAnimationVariable* pVariable,
    CAnimationBaseObject** ppObject,
    CAnimationGroup** ppGroup);
```

### <a name="parameters"></a>Paramètres

*pVariable*<br/>
Pointeur vers une variable d’animation.

*ppObject*<br/>
Sortie : Contient un pointeur vers un objet d’animation ou NULL.

*ppGroup*<br/>
Sortie : Contient un pointeur vers un groupe d’animation qui contient l’objet d’animation, ou NULL.

### <a name="return-value"></a>Valeur renvoyée

TRUE si l’objet a été trouvé ; Sinon, FALSe.

### <a name="remarks"></a>Notes

Appelée à partir des gestionnaires d’événements lorsqu’il est nécessaire de trouver un objet d’animation à partir de la variable d’animation entrante.

## <a name="canimationcontrollergkeyframestoryboardstart"></a><a name="g_keyframestoryboardstart"></a> CAnimationController :: gkeyframeStoryboardStart

Image clé qui représente le début du Storyboard.

```
static CBaseKeyFrame gkeyframeStoryboardStart;
```

## <a name="canimationcontrollergetkeyframestoryboardstart"></a><a name="getkeyframestoryboardstart"></a> CAnimationController :: GetKeyframeStoryboardStart

Retourne une image clé qui identifie le début du Storyboard.

```
static CBaseKeyFrame* GetKeyframeStoryboardStart();
```

### <a name="return-value"></a>Valeur renvoyée

Pointeur vers l’image clé de base, qui identifie le début du Storyboard.

### <a name="remarks"></a>Notes

Obtenez cette image clé pour baser les autres images clés ou transitions au moment du démarrage d’une table de montage séquentiel.

## <a name="canimationcontrollergetuianimationmanager"></a><a name="getuianimationmanager"></a> CAnimationController :: GetUIAnimationManager

Fournit l’accès à l’objet IUIAnimationManager encapsulé.

```
IUIAnimationManager* GetUIAnimationManager();
```

### <a name="return-value"></a>Valeur renvoyée

Pointeur vers l’interface IUIAnimationManager ou NULL, si la création du gestionnaire d’animations a échoué.

### <a name="remarks"></a>Notes

Si le système d’exploitation actuel ne prend pas en charge l’API d’animation Windows, cette méthode retourne NULL et après que tous les appels suivants sur CAnimationController :: IsValid retournent la valeur FALSe. Vous devrez peut-être accéder à IUIAnimationManager pour appeler ses méthodes d’interface, qui ne sont pas encapsulées par le contrôleur d’animation.

## <a name="canimationcontrollergetuianimationtimer"></a><a name="getuianimationtimer"></a> CAnimationController :: GetUIAnimationTimer

Fournit l’accès à l’objet IUIAnimationTimer encapsulé.

```
IUIAnimationTimer* GetUIAnimationTimer();
```

### <a name="return-value"></a>Valeur renvoyée

Pointeur vers l’interface IUIAnimationTimer ou NULL, si la création du minuteur d’animation a échoué.

### <a name="remarks"></a>Notes

Si le système d’exploitation actuel ne prend pas en charge l’API d’animation Windows, cette méthode retourne NULL et après que tous les appels suivants sur CAnimationController :: IsValid retournent la valeur FALSe.

## <a name="canimationcontrollergetuitransitionfactory"></a><a name="getuitransitionfactory"></a> CAnimationController :: GetUITransitionFactory

Pointeur vers l’interface IUIAnimationTransitionFactory ou NULL, en cas d’échec de la création de la bibliothèque de transition.

```
IUIAnimationTransitionFactory* GetUITransitionFactory();
```

### <a name="return-value"></a>Valeur renvoyée

Pointeur vers IUIAnimationTransitionFactory ou NULL, en cas d’échec de la création de la fabrique de transition.

### <a name="remarks"></a>Notes

Si le système d’exploitation actuel ne prend pas en charge l’API d’animation Windows, cette méthode retourne NULL et après que tous les appels suivants sur CAnimationController :: IsValid retournent la valeur FALSe.

## <a name="canimationcontrollergetuitransitionlibrary"></a><a name="getuitransitionlibrary"></a> CAnimationController :: GetUITransitionLibrary

Fournit l’accès à l’objet IUIAnimationTransitionLibrary encapsulé.

```
IUIAnimationTransitionLibrary* GetUITransitionLibrary();
```

### <a name="return-value"></a>Valeur renvoyée

Pointeur vers l’interface IUIAnimationTransitionLibrary ou NULL, en cas d’échec de la création de la bibliothèque de transition.

### <a name="remarks"></a>Notes

Si le système d’exploitation actuel ne prend pas en charge l’API d’animation Windows, cette méthode retourne NULL et après que tous les appels suivants sur CAnimationController :: IsValid retournent la valeur FALSe.

## <a name="canimationcontrollerisanimationinprogress"></a><a name="isanimationinprogress"></a> CAnimationController :: IsAnimationInProgress

Indique si au moins un groupe lit l’animation.

```
virtual BOOL IsAnimationInProgress();
```

### <a name="return-value"></a>Valeur renvoyée

TRUE s’il existe une animation en cours pour ce contrôleur d’animation ; Sinon, FALSe.

### <a name="remarks"></a>Notes

Vérifie l’état du gestionnaire d’animations et retourne la valeur TRUE si l’État est UI_ANIMATION_MANAGER_BUSY.

## <a name="canimationcontrollerisvalid"></a><a name="isvalid"></a> CAnimationController :: IsValid

Indique si le contrôleur d’animation est valide.

```
BOOL IsValid() const;
```

### <a name="return-value"></a>Valeur renvoyée

TRUE si le contrôleur d’animation est valide ; Sinon, FALSe.

### <a name="remarks"></a>Notes

Cette méthode retourne la valeur FALSe uniquement si l’API d’animation Windows n’est pas prise en charge sur le système d’exploitation actuel et que la création du gestionnaire d’animations a échoué, car elle n’est pas inscrite. Vous devez appeler GetUIAnimationManager au moins une fois après l’initialisation des bibliothèques COM pour provoquer le paramétrage de cet indicateur.

## <a name="canimationcontrollerm_bisvalid"></a><a name="m_bisvalid"></a> CAnimationController :: m_bIsValid

Spécifie si un contrôleur d’animation est valide ou non. Ce membre a la valeur FALSe si le système d’exploitation actuel ne prend pas en charge l’API d’animation Windows.

```
BOOL m_bIsValid;
```

## <a name="canimationcontrollerm_lstanimationgroups"></a><a name="m_lstanimationgroups"></a> CAnimationController :: m_lstAnimationGroups

Liste des groupes d’animations qui appartiennent à ce contrôleur d’animation.

```
CList<CAnimationGroup*, CAnimationGroup*> m_lstAnimationGroups;
```

## <a name="canimationcontrollerm_panimationmanager"></a><a name="m_panimationmanager"></a> CAnimationController :: m_pAnimationManager

Stocke un pointeur vers l’objet COM du gestionnaire d’animations.

```
ATL::CComPtr<IUIAnimationManager> m_pAnimationManager;
```

## <a name="canimationcontrollerm_panimationtimer"></a><a name="m_panimationtimer"></a> CAnimationController :: m_pAnimationTimer

Stocke un pointeur vers l’objet COM du minuteur d’animation.

```
ATL::CComPtr<IUIAnimationTimer> m_pAnimationTimer;
```

## <a name="canimationcontrollerm_prelatedwnd"></a><a name="m_prelatedwnd"></a> CAnimationController :: m_pRelatedWnd

Pointeur vers un objet CWnd connexe, qui peut être redessiné automatiquement lorsque l’état du gestionnaire d’animations a changé ou lorsque l’événement de publication de mise à jour s’est produit. Sa valeur peut être NULL.

```
CWnd* m_pRelatedWnd;
```

## <a name="canimationcontrollerm_ptransitionfactory"></a><a name="m_ptransitionfactory"></a> CAnimationController :: m_pTransitionFactory

Stocke un pointeur vers l’objet COM de la fabrique de transition.

```
ATL::CComPtr<IUIAnimationTransitionFactory> m_pTransitionFactory;
```

## <a name="canimationcontrollerm_ptransitionlibrary"></a><a name="m_ptransitionlibrary"></a> CAnimationController :: m_pTransitionLibrary

Stocke un pointeur vers l’objet COM de la bibliothèque de transitions.

```
ATL::CComPtr<IUIAnimationTransitionLibrary> m_pTransitionLibrary;
```

## <a name="canimationcontrolleronafterschedule"></a><a name="onafterschedule"></a> CAnimationController :: OnAfterSchedule

Appelé par le Framework lorsqu’une animation pour le groupe spécifié vient d’être planifiée.

```
virtual void OnAfterSchedule(CAnimationGroup* pGroup);
```

### <a name="parameters"></a>Paramètres

*pGroup*<br/>
Pointeur vers un groupe d’animation, qui a été planifié.

### <a name="remarks"></a>Notes

L’implémentation par défaut supprime les images clés du groupe spécifié et les transitions à partir des variables d’animation qui appartiennent au groupe spécifié. Peut être substitué dans une classe dérivée pour prendre des mesures supplémentaires lors de la planification de l’animation.

## <a name="canimationcontrolleronanimationintegervaluechanged"></a><a name="onanimationintegervaluechanged"></a> CAnimationController :: OnAnimationIntegerValueChanged

Appelé par l’infrastructure lorsque la valeur entière de la variable d’animation a changé.

```
virtual void OnAnimationIntegerValueChanged(
    CAnimationGroup* pGroup,
    CAnimationBaseObject* pObject,
    IUIAnimationVariable* variable,
    INT32 newValue,
    INT32 prevValue);
```

### <a name="parameters"></a>Paramètres

*pGroup*<br/>
Pointeur vers un groupe d’animation qui contient un objet d’animation dont la valeur a été modifiée.

*pObject*<br/>
Pointeur vers un objet d’animation qui contient une variable d’animation dont la valeur a été modifiée.

*variable*<br/>
Pointeur vers une variable d’animation.

*newValue*<br/>
Spécifie une nouvelle valeur.

*prevValue*<br/>
Spécifie la valeur précédente.

### <a name="remarks"></a>Notes

Cette méthode est appelée si vous activez les événements de variable d’animation avec EnableIntegerValueChangedEvent appelé pour une variable d’animation ou un objet d’animation spécifique. Elle peut être substituée dans une classe dérivée pour prendre des mesures propres à l'application.

## <a name="canimationcontrolleronanimationmanagerstatuschanged"></a><a name="onanimationmanagerstatuschanged"></a> CAnimationController :: OnAnimationManagerStatusChanged

Appelée par l’infrastructure en réponse à l’événement StatusChanged à partir du gestionnaire d’animations.

```
virtual void OnAnimationManagerStatusChanged(
    UI_ANIMATION_MANAGER_STATUS newStatus,
    UI_ANIMATION_MANAGER_STATUS previousStatus);
```

### <a name="parameters"></a>Paramètres

*newStatus*<br/>
Nouvel État du gestionnaire d’animations.

*previousStatus*<br/>
État du gestionnaire d’animations précédent.

### <a name="remarks"></a>Notes

Cette méthode est appelée si vous activez les événements du gestionnaire d’animations avec EnableAnimationManagerEvent. Elle peut être substituée dans une classe dérivée pour prendre des mesures propres à l'application. L’implémentation par défaut met à jour une fenêtre connexe si elle a été définie avec SetRelatedWnd.

## <a name="canimationcontrolleronanimationtimerpostupdate"></a><a name="onanimationtimerpostupdate"></a> CAnimationController :: OnAnimationTimerPostUpdate

Appelé par l’infrastructure une fois la mise à jour d’une animation terminée.

```
virtual void OnAnimationTimerPostUpdate();
```

### <a name="remarks"></a>Notes

Cette méthode est appelée si vous activez les gestionnaires d’événements de minuteur à l’aide de EnableAnimationTimerEventHandler. Elle peut être substituée dans une classe dérivée pour prendre des mesures propres à l'application.

## <a name="canimationcontrolleronanimationtimerpreupdate"></a><a name="onanimationtimerpreupdate"></a> CAnimationController :: OnAnimationTimerPreUpdate

Appelé par le Framework avant le début d’une mise à jour d’animation.

```
virtual void OnAnimationTimerPreUpdate();
```

### <a name="remarks"></a>Notes

Cette méthode est appelée si vous activez les gestionnaires d’événements de minuteur à l’aide de EnableAnimationTimerEventHandler. Elle peut être substituée dans une classe dérivée pour prendre des mesures propres à l'application.

## <a name="canimationcontrolleronanimationtimerrenderingtooslow"></a><a name="onanimationtimerrenderingtooslow"></a> CAnimationController :: OnAnimationTimerRenderingTooSlow

Appelée par l’infrastructure lorsque la fréquence d’images de rendu d’une animation passe sous une fréquence d’images minimale désirable.

```
virtual void OnAnimationTimerRenderingTooSlow(UINT32 fps);
```

### <a name="parameters"></a>Paramètres

*fps*<br/>
Fréquence d’images actuelle en images par seconde.

### <a name="remarks"></a>Notes

Cette méthode est appelée si vous activez les gestionnaires d’événements de minuteur à l’aide de EnableAnimationTimerEventHandler. Elle peut être substituée dans une classe dérivée pour prendre des mesures propres à l'application. La fréquence d’images minimale recommandée est spécifiée en appelant IUIAnimationTimer :: SetFrameRateThreshold.

## <a name="canimationcontrolleronanimationvaluechanged"></a><a name="onanimationvaluechanged"></a> CAnimationController :: OnAnimationValueChanged

Appelé par le Framework lorsque la valeur de la variable d’animation a changé.

```
virtual void OnAnimationValueChanged(
    CAnimationGroup* pGroup,
    CAnimationBaseObject* pObject,
    IUIAnimationVariable* variable,
    DOUBLE newValue,
    DOUBLE prevValue);
```

### <a name="parameters"></a>Paramètres

*pGroup*<br/>
Pointeur vers un groupe d’animation qui contient un objet d’animation dont la valeur a été modifiée.

*pObject*<br/>
Pointeur vers un objet d’animation qui contient une variable d’animation dont la valeur a été modifiée.

*variable*<br/>
Pointeur vers une variable d’animation.

*newValue*<br/>
Spécifie une nouvelle valeur.

*prevValue*<br/>
Spécifie la valeur précédente.

### <a name="remarks"></a>Notes

Cette méthode est appelée si vous activez les événements de variable d’animation avec EnableValueChangedEvent appelé pour une variable d’animation ou un objet d’animation spécifique. Elle peut être substituée dans une classe dérivée pour prendre des mesures propres à l'application.

## <a name="canimationcontrolleronbeforeanimationstart"></a><a name="onbeforeanimationstart"></a> CAnimationController :: OnBeforeAnimationStart

Appelée par le Framework juste avant que l’animation soit planifiée.

```
virtual void OnBeforeAnimationStart(CAnimationGroup* pGroup);
```

### <a name="parameters"></a>Paramètres

*pGroup*<br/>
Pointeur vers un groupe d’animation dont l’animation est sur le point de démarrer.

### <a name="remarks"></a>Notes

Cet appel est routé à CWnd connexe et peut être substitué dans une classe dérivée pour exécuter des actions supplémentaires avant le démarrage de l’animation pour le groupe spécifié.

## <a name="canimationcontrolleronhasprioritycancel"></a><a name="onhasprioritycancel"></a> CAnimationController :: OnHasPriorityCancel

Appelé par l'infrastructure pour résoudre les conflits de planification.

```
virtual BOOL OnHasPriorityCancel(
    CAnimationGroup* pGroupScheduled,
    CAnimationGroup* pGroupNew,
    UI_ANIMATION_PRIORITY_EFFECT priorityEffect);
```

### <a name="parameters"></a>Paramètres

*pGroupScheduled*<br/>
Groupe propriétaire du plan conceptuel actuellement planifié.

*pGroupNew*<br/>
Groupe propriétaire du nouveau plan conceptuel dont la planification est en conflit avec celle du plan conceptuel dont pGroupScheduled est propriétaire.

*priorityEffect*<br/>
Effet potentiel sur pGroupNew si pGroupScheduled a une priorité plus élevée.

### <a name="return-value"></a>Valeur renvoyée

Doit retourner TRUE si le plan conceptuel détenu par pGroupNew est prioritaire. Doit retourner FALSE si le plan conceptuel détenu par pGroupScheduled est prioritaire.

### <a name="remarks"></a>Notes

Cette méthode est appelée si vous activez les événements de comparaison de priorité à l'aide de CAnimationController::EnablePriorityComparisonHandler et que vous spécifiez UI_ANIMATION_PHT_CANCEL. Elle peut être substituée dans une classe dérivée pour prendre des mesures propres à l'application. Pour plus d’informations sur la [gestion des conflits](/windows/win32/api/uianimation/nf-uianimation-iuianimationprioritycomparison-haspriority), consultez la documentation de l’API d’animation Windows.

## <a name="canimationcontrolleronhasprioritycompress"></a><a name="onhasprioritycompress"></a> CAnimationController :: OnHasPriorityCompress

Appelé par l'infrastructure pour résoudre les conflits de planification.

```
virtual BOOL OnHasPriorityCompress(
    CAnimationGroup* pGroupScheduled,
    CAnimationGroup* pGroupNew,
    UI_ANIMATION_PRIORITY_EFFECT priorityEffect);
```

### <a name="parameters"></a>Paramètres

*pGroupScheduled*<br/>
Groupe propriétaire du plan conceptuel actuellement planifié.

*pGroupNew*<br/>
Groupe propriétaire du nouveau plan conceptuel dont la planification est en conflit avec celle du plan conceptuel dont pGroupScheduled est propriétaire.

*priorityEffect*<br/>
Effet potentiel sur pGroupNew si pGroupScheduled a une priorité plus élevée.

### <a name="return-value"></a>Valeur renvoyée

Doit retourner TRUE si le plan conceptuel détenu par pGroupNew est prioritaire. Doit retourner FALSE si le plan conceptuel détenu par pGroupScheduled est prioritaire.

### <a name="remarks"></a>Notes

Cette méthode est appelée si vous activez les événements de comparaison de priorité à l'aide de CAnimationController::EnablePriorityComparisonHandler et que vous spécifiez UI_ANIMATION_PHT_COMPRESS. Elle peut être substituée dans une classe dérivée pour prendre des mesures propres à l'application. Pour plus d’informations sur la [gestion des conflits](/windows/win32/api/uianimation/nf-uianimation-iuianimationprioritycomparison-haspriority), consultez la documentation de l’API d’animation Windows.

## <a name="canimationcontrolleronhaspriorityconclude"></a><a name="onhaspriorityconclude"></a> CAnimationController :: OnHasPriorityConclude

Appelé par l'infrastructure pour résoudre les conflits de planification.

```
virtual BOOL OnHasPriorityConclude(
    CAnimationGroup* pGroupScheduled,
    CAnimationGroup* pGroupNew,
    UI_ANIMATION_PRIORITY_EFFECT priorityEffect);
```

### <a name="parameters"></a>Paramètres

*pGroupScheduled*<br/>
Groupe propriétaire du plan conceptuel actuellement planifié.

*pGroupNew*<br/>
Groupe propriétaire du nouveau plan conceptuel dont la planification est en conflit avec celle du plan conceptuel dont pGroupScheduled est propriétaire.

*priorityEffect*<br/>
Effet potentiel sur pGroupNew si pGroupScheduled a une priorité plus élevée.

### <a name="return-value"></a>Valeur renvoyée

Doit retourner TRUE si le plan conceptuel détenu par pGroupNew est prioritaire. Doit retourner FALSE si le plan conceptuel détenu par pGroupScheduled est prioritaire.

### <a name="remarks"></a>Notes

Cette méthode est appelée si vous activez les événements de comparaison de priorité à l'aide de CAnimationController::EnablePriorityComparisonHandler et que vous spécifiez UI_ANIMATION_PHT_CONCLUDE. Elle peut être substituée dans une classe dérivée pour prendre des mesures propres à l'application. Pour plus d’informations sur la [gestion des conflits](/windows/win32/api/uianimation/nf-uianimation-iuianimationprioritycomparison-haspriority), consultez la documentation de l’API d’animation Windows.

## <a name="canimationcontrolleronhasprioritytrim"></a><a name="onhasprioritytrim"></a> CAnimationController :: OnHasPriorityTrim

Appelé par l'infrastructure pour résoudre les conflits de planification.

```
virtual BOOL OnHasPriorityTrim(
    CAnimationGroup* pGroupScheduled,
    CAnimationGroup* pGroupNew,
    UI_ANIMATION_PRIORITY_EFFECT priorityEffect);
```

### <a name="parameters"></a>Paramètres

*pGroupScheduled*<br/>
Groupe propriétaire du plan conceptuel actuellement planifié.

*pGroupNew*<br/>
Groupe propriétaire du nouveau plan conceptuel dont la planification est en conflit avec celle du plan conceptuel dont pGroupScheduled est propriétaire.

*priorityEffect*<br/>
Effet potentiel sur pGroupNew si pGroupScheduled a une priorité plus élevée.

### <a name="return-value"></a>Valeur renvoyée

Doit retourner TRUE si le plan conceptuel détenu par pGroupNew est prioritaire. Doit retourner FALSE si le plan conceptuel détenu par pGroupScheduled est prioritaire.

### <a name="remarks"></a>Notes

Cette méthode est appelée si vous activez les événements de comparaison de priorité à l'aide de CAnimationController::EnablePriorityComparisonHandler et que vous spécifiez UI_ANIMATION_PHT_TRIM. Elle peut être substituée dans une classe dérivée pour prendre des mesures propres à l'application. Pour plus d’informations sur la [gestion des conflits](/windows/win32/api/uianimation/nf-uianimation-iuianimationprioritycomparison-haspriority), consultez la documentation de l’API d’animation Windows.

## <a name="canimationcontrolleronstoryboardstatuschanged"></a><a name="onstoryboardstatuschanged"></a> CAnimationController :: OnStoryboardStatusChanged

Appelé par le Framework lorsque l’état de la table de montage séquentiel a changé.

```
virtual void OnStoryboardStatusChanged(
    CAnimationGroup* pGroup,
    UI_ANIMATION_STORYBOARD_STATUS newStatus,
    UI_ANIMATION_STORYBOARD_STATUS previousStatus);
```

### <a name="parameters"></a>Paramètres

*pGroup*<br/>
Pointeur vers un groupe d’animation qui possède le Storyboard dont l’État a changé.

*newStatus*<br/>
Spécifie le nouvel État.

*previousStatus*<br/>
Spécifie l’état précédent.

### <a name="remarks"></a>Notes

Cette méthode est appelée si vous activez les événements de Storyboard à l’aide de CAnimationController :: EnableStoryboardEventHandler. Elle peut être substituée dans une classe dérivée pour prendre des mesures propres à l'application.

## <a name="canimationcontrolleronstoryboardupdated"></a><a name="onstoryboardupdated"></a> CAnimationController :: OnStoryboardUpdated

Appelé par le Framework lorsque le Storyboard a été mis à jour.

```
virtual void OnStoryboardUpdated(CAnimationGroup* pGroup);
```

### <a name="parameters"></a>Paramètres

*pGroup*<br/>
Pointeur vers un groupe qui possède le Storyboard.

### <a name="remarks"></a>Notes

Cette méthode est appelée si vous activez les événements de Storyboard à l’aide de CAnimationController :: EnableStoryboardEventHandler. Elle peut être substituée dans une classe dérivée pour prendre des mesures propres à l'application.

## <a name="canimationcontrollerremoveallanimationgroups"></a><a name="removeallanimationgroups"></a> CAnimationController :: RemoveAllAnimationGroups

Supprime tous les groupes d’animations du contrôleur d’animation.

```cpp
void RemoveAllAnimationGroups();
```

### <a name="remarks"></a>Notes

Tous les groupes seront supprimés, leur pointeur, s’il est stocké au niveau de l’application, doit être invalidé. Si CAnimationGroup, :: m_bAutodestroyAnimationObjects pour un groupe en cours de suppression a la valeur TRUE, tous les objets d’animation qui appartiennent à ce groupe seront supprimés. dans le cas contraire, leurs références au contrôleur d’animation parent auront la valeur NULL et elles pourront être ajoutées à un autre contrôleur.

## <a name="canimationcontrollerremoveanimationgroup"></a><a name="removeanimationgroup"></a> CAnimationController :: RemoveAnimationGroup

Supprime un groupe d’animation avec l’ID spécifié du contrôleur d’animation.

```cpp
void RemoveAnimationGroup(UINT32 nGroupID);
```

### <a name="parameters"></a>Paramètres

*nGroupID*<br/>
Spécifie l’ID du groupe d’animation.

### <a name="remarks"></a>Notes

Cette méthode supprime un groupe d’animation de la liste interne des groupes et le supprime. par conséquent, si vous avez stocké un pointeur vers ce groupe d’animation, il doit être invalidé. Si CAnimationGroup, :: m_bAutodestroyAnimationObjects a la valeur TRUE, tous les objets d’animation qui appartiennent à ce groupe seront supprimés. dans le cas contraire, leurs références au contrôleur d’animation parent auront la valeur NULL et elles pourront être ajoutées à un autre contrôleur.

## <a name="canimationcontrollerremoveanimationobject"></a><a name="removeanimationobject"></a> CAnimationController :: RemoveAnimationObject

Supprimer un objet d’animation du contrôleur d’animation.

```cpp
void RemoveAnimationObject(
    CAnimationBaseObject* pObject,
    BOOL bNoDelete = FALSE);
```

### <a name="parameters"></a>Paramètres

*pObject*<br/>
Pointeur vers un objet d’animation.

*bNoDelete*<br/>
Si ce paramètre a la valeur TRUE, l’objet n’est pas supprimé lors de la suppression.

### <a name="remarks"></a>Notes

Supprime un objet d’animation du contrôleur d’animation et du groupe d’animation. Appelez cette fonction si un objet particulier ne doit plus être animé ou si vous devez déplacer l’objet vers un autre contrôleur d’animation. Dans le dernier cas, bNoDelete doit avoir la valeur TRUE.

## <a name="canimationcontrollerremovetransitions"></a><a name="removetransitions"></a> CAnimationController :: RemoveTransitions

Supprime les transitions des objets d’animation qui appartiennent au groupe spécifié.

```cpp
void RemoveTransitions(UINT32 nGroupID);
```

### <a name="parameters"></a>Paramètres

*nGroupID*<br/>
Spécifie l’ID de groupe.

### <a name="remarks"></a>Notes

Le groupe effectue une boucle sur ses objets d’animation et appelle ClearTransitions (FALSe) pour chaque objet d’animation. Cette méthode est appelée par le Framework après que l’animation a été planifiée.

## <a name="canimationcontrollerschedulegroup"></a><a name="schedulegroup"></a> CAnimationController :: ScheduleGroup

Planifie une animation.

```
BOOL ScheduleGroup(
    UINT32 nGroupID,
    UI_ANIMATION_SECONDS time = 0.0);
```

### <a name="parameters"></a>Paramètres

*nGroupID*<br/>
Spécifie l’ID du groupe d’animations à planifier.

*time*<br/>
Spécifie l’heure à planifier.

### <a name="return-value"></a>Valeur renvoyée

TRUE si l’animation a été planifiée avec succès. FALSe si le Storyboard n’a pas été créé ou si une autre erreur se produit.

### <a name="remarks"></a>Notes

Vous devez appeler AnimateGroup avec le paramètre bScheduleNow défini sur FALSe précédent ScheduleGroup. Vous pouvez spécifier l’heure d’animation souhaitée obtenue à partir de IUIAnimationTimer :: GetTime. Si le paramètre de temps est 0,0, l’animation est planifiée pour l’heure actuelle.

## <a name="canimationcontrollersetrelatedwnd"></a><a name="setrelatedwnd"></a> CAnimationController :: SetRelatedWnd

Établit une relation entre le contrôleur d’animation et une fenêtre.

```cpp
void SetRelatedWnd(CWnd* pWnd);
```

### <a name="parameters"></a>Paramètres

*pWnd*<br/>
Pointeur vers l’objet de fenêtre à définir.

### <a name="remarks"></a>Notes

Si un objet CWnd associé est défini, le contrôleur d’animation peut le mettre à jour automatiquement (envoyer WM_PAINT message) lorsque l’état du gestionnaire d’animations a changé ou lorsque l’événement de publication de mise à jour du minuteur s’est produit.

## <a name="canimationcontrollerupdateanimationmanager"></a><a name="updateanimationmanager"></a> CAnimationController :: UpdateAnimationManager

Indique au gestionnaire d’animations de mettre à jour les valeurs de toutes les variables d’animation.

```
virtual void UpdateAnimationManager();
```

### <a name="remarks"></a>Notes

L’appel de cette méthode fait avancer le gestionnaire d’animations à l’heure actuelle, en modifiant les États des storyboards si nécessaire et en mettant à jour les variables d’animation avec les valeurs interpolées appropriées. En interne, cette méthode appelle IUIAnimationTimer :: GetTime (timeNow) et IUIAnimationManager :: Update (timeNow). Substituez cette méthode dans une classe dérivée pour personnaliser ce comportement.

## <a name="see-also"></a>Voir aussi

[Classes](../../mfc/reference/mfc-classes.md)
