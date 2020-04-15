---
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
ms.openlocfilehash: 34a02567bfeb76666cc38ccf05dcc285a1f658f5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369751"
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
|[CAnimationController::CAnimationController](#canimationcontroller)|Construit un contrôleur d’animation.|
|[CAnimationController::CAnimationController](#_dtorcanimationcontroller)|Destructeur. Appelé lorsque l’objet du contrôleur d’animation est détruit.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CAnimationController::AddAnimationObject](#addanimationobject)|Ajoute un objet d’animation à un groupe qui appartient au contrôleur d’animation.|
|[CAnimationController::AddKeyframeToGroup](#addkeyframetogroup)|Ajoute un cadre clé au groupe.|
|[CAnimationController::AnimateGroup](#animategroup)|Prépare un groupe pour exécuter l’animation et l’horaire optionnellement.|
|[CAnimationController::CleanUpGroup](#cleanupgroup)|Surchargé. Appelé par le cadre pour nettoyer le groupe lorsque l’animation a été programmée.|
|[CAnimationController::CreateKeyframe](#createkeyframe)|Surchargé. Crée une image clé qui dépend de la transition et l’ajoute au groupe spécifié.|
|[CAnimationController::EnableAnimationManagerEvent](#enableanimationmanagerevent)|Définit ou libère un gestionnaire pour appeler lorsque le statut du gestionnaire d’animation change.|
|[CAnimationController::EnableAnimationTimerEventHandler](#enableanimationtimereventhandler)|Définit ou libère un gestionnaire pour les événements de chronométrage et gestionnaire pour les mises à jour de synchronisation.|
|[CAnimationController::EnablePriorityComparisonHandler](#enableprioritycomparisonhandler)|Définit ou libère le gestionnaire de comparaison prioritaire à appeler pour déterminer si un storyboard prévu peut être annulé, conclu, coupé ou comprimé.|
|[CAnimationController::EnableStoryboardEventHandler](#enablestoryboardeventhandler)|Définit ou libère un gestionnaire pour l’état du storyboard et mettre à jour les événements.|
|[CAnimationController::FindAnimationGroup](#findanimationgroup)|Surchargé. Trouve un groupe d’animation par son storyboard.|
|[CAnimationController::FindAnimationObject](#findanimationobject)|Trouve un objet d’animation contenant une variable d’animation spécifiée.|
|[CAnimationController::GetKeyframeStoryboardStart](#getkeyframestoryboardstart)|Retourne un cadre clé qui identifie le début du storyboard.|
|[CAnimationController::GetUIAnimationManager](#getuianimationmanager)|Donne accès à l’objet IUIAnimationManager encapsulé.|
|[CAnimationController::GetUIAnimationTimer](#getuianimationtimer)|Donne accès à l’objet IUIAnimationTimer encapsulé.|
|[CAnimationController::GetUITransitionFactory](#getuitransitionfactory)|Un pointeur à l’interface IUIAnimationTransitionFactory ou NULL, si la création de la bibliothèque de transition a échoué.|
|[CAnimationController::GetUITransitionLibrary](#getuitransitionlibrary)|Donne accès à l’objet IUIAnimationTransitionTransition encapsulé.|
|[CAnimationController::IsAnimationInProgress](#isanimationinprogress)|Indique si au moins un groupe joue de l’animation.|
|[CAnimationController::IsValid](#isvalid)|Indique si le contrôleur d’animation est valide.|
|[CAnimationController::OnAnimationIntegerValueChanged](#onanimationintegervaluechanged)|Appelé par le cadre lorsque la valeur integer de la variable d’animation a changé.|
|[CAnimationController::OnAnimationManagerStatusChanged](#onanimationmanagerstatuschanged)|Appelé par le cadre en réponse à l’événement StatusChanged du directeur de l’animation.|
|[CAnimationController::OnAnimationTimerPostUpdate](#onanimationtimerpostupdate)|Appelé par le cadre après une mise à jour d’animation est terminée.|
|[CAnimationController::OnAnimationTimerPreUpdate](#onanimationtimerpreupdate)|Appelé par le cadre avant une mise à jour d’animation commence.|
|[CAnimationController::OnAnimationTimerenderingTooSlow](#onanimationtimerrenderingtooslow)|Appelé par le cadre lorsque le taux d’image de rendu pour une animation tombe en dessous d’un taux d’image minimum souhaitable.|
|[CAnimationController::OnAnimationValueChanged](#onanimationvaluechanged)|Appelé par le cadre lorsque la valeur de la variable d’animation a changé.|
|[CAnimationController::OnBeforeAnimationStart](#onbeforeanimationstart)|Appelé par le cadre juste avant l’animation est prévue.|
|[CAnimationController::OnHasPriorityCancel](#onhasprioritycancel)|Appelé par l'infrastructure pour résoudre les conflits de planification.|
|[CAnimationController::OnHasPriorityCompress](#onhasprioritycompress)|Appelé par l'infrastructure pour résoudre les conflits de planification.|
|[CAnimationController::OnHasPriorityConclude](#onhaspriorityconclude)|Appelé par l'infrastructure pour résoudre les conflits de planification.|
|[CAnimationController::OnHasPriorityTrim](#onhasprioritytrim)|Appelé par l'infrastructure pour résoudre les conflits de planification.|
|[CAnimationController::OnStoryboardStatusChanged](#onstoryboardstatuschanged)|Appelé par le cadre lorsque le statut storyboard a changé.|
|[CAnimationController::OnStoryboardUpdated](#onstoryboardupdated)|Appelé par le cadre lorsque storyboard a été mis à jour.|
|[CAnimationController::RemoveAllAnimationGroups](#removeallanimationgroups)|Supprime tous les groupes d’animation du contrôleur d’animation.|
|[CAnimationController::RemoveAnimationGroup](#removeanimationgroup)|Supprime un groupe d’animation avec un ID spécifié du contrôleur d’animation.|
|[CAnimationController::Supprimer l’élégationObject](#removeanimationobject)|Retirez un objet d’animation du contrôleur d’animation.|
|[CAnimationController::RemoveTransitions](#removetransitions)|Supprime les transitions des objets d’animation qui appartiennent au groupe spécifié.|
|[CAnimationController::Groupe d’horaires](#schedulegroup)|Planifie une animation.|
|[CAnimationController::SetRelatedWnd](#setrelatedwnd)|Établit une relation entre le contrôleur d’animation et une fenêtre.|
|[CAnimationController::Mise à jourAnimationManager](#updateanimationmanager)|Dirige le responsable de l’animation pour mettre à jour les valeurs de toutes les variables d’animation.|

### <a name="protected-methods"></a>Méthodes protégées

|Nom|Description|
|----------|-----------------|
|[CAnimationController::CleanUpGroup](#cleanupgroup)|Surchargé. Une aide qui nettoie le groupe.|
|[CAnimationController::OnAfterSchedule](#onafterschedule)|Appelé par le cadre quand une animation pour le groupe spécifié vient d’être programmée.|

### <a name="protected-data-members"></a>Membres de données protégés

|Nom|Description|
|----------|-----------------|
|[CAnimationController::gkeyframeStoryboardStart](#g_keyframestoryboardstart)|Un cadre clé qui représente le début du storyboard.|
|[CAnimationController::m_bIsValid](#m_bisvalid)|Précise si un contrôleur d’animation est valide ou non. Ce membre est configuré à FALSE si le système d’exploitation actuel ne prend pas en charge l’API d’animation Windows.|
|[CAnimationController::m_lstAnimationGroups](#m_lstanimationgroups)|Une liste de groupes d’animation qui appartiennent à ce contrôleur d’animation.|
|[CAnimationController::m_pAnimationManager](#m_panimationmanager)|Stocke un pointeur vers l’objet Animation Manager COM.|
|[CAnimationController::m_pAnimationTimer](#m_panimationtimer)|Stocke un pointeur vers l’objet Animation Timer COM.|
|[CAnimationController::m_pRelatedWnd](#m_prelatedwnd)|Un pointeur vers un objet CWnd connexe, qui peut être automatiquement redessiné lorsque l’état du gestionnaire d’animation a changé, ou l’événement de mise à jour post s’est produit. Sa valeur peut être NULL.|
|[CAnimationController::m_pTransitionFactory](#m_ptransitionfactory)|Stocke un pointeur vers l’objet Transition Factory COM.|
|[CAnimationController::m_pTransitionLibrary](#m_ptransitionlibrary)|Stocke un pointeur vers l’objet TRANSITION Library COM.|

## <a name="remarks"></a>Notes

La classe CAnimationController est la classe clé qui gère les animations. Vous pouvez créer un ou plusieurs cas de contrôleur d’animation dans une application et, en option, connecter une instance de contrôleur d’animation à un objet CWnd à l’aide de CAnimationController:SetRelatedWnd. Cette connexion est nécessaire pour envoyer WM_PAINT messages à la fenêtre connexe automatiquement lorsque le statut du gestionnaire d’animation a changé ou que la minuterie d’animation a été mise à jour. Si vous n’activez pas cette relation, vous devez redessiner une fenêtre qui affiche une animation manuellement. À cette fin, vous pouvez tirer une classe de CAnimationController et remplacer OnAnimationManagerStatusChanged et/ou OnAnimationTimerPostUpdate et invalider une ou plusieurs fenêtres si nécessaire.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

`CAnimationController`

## <a name="requirements"></a>Spécifications

**En-tête :** afxanimationcontroller.h

## <a name="canimationcontrollercanimationcontroller"></a><a name="_dtorcanimationcontroller"></a>CAnimationController::CAnimationController

Destructeur. Appelé lorsque l’objet du contrôleur d’animation est détruit.

```
virtual ~CAnimationController(void);
```

## <a name="canimationcontrolleraddanimationobject"></a><a name="addanimationobject"></a>CAnimationController::AddAnimationObject

Ajoute un objet d’animation à un groupe qui appartient au contrôleur d’animation.

```
CAnimationGroup* AddAnimationObject(CAnimationBaseObject* pObject);
```

### <a name="parameters"></a>Paramètres

*pObject*<br/>
Un pointeur à un objet d’animation.

### <a name="return-value"></a>Valeur de retour

Un pointeur vers le groupe d’animation existant ou nouveau où le pObject a été ajouté si la fonction réussit; NULL si pObject a déjà été ajouté à un groupe qui appartient à un autre contrôleur d’animation.

### <a name="remarks"></a>Notes

Appelez cette méthode pour ajouter un objet d’animation au contrôleur d’animation. Un objet sera ajouté à un groupe selon le GroupID de l’objet (voir CAnimationBaseObject:SetID). Le contrôleur d’animation créera un nouveau groupe s’il s’agit du premier objet ajouté avec le GroupID spécifié. Un objet d’animation peut être ajouté à un seul contrôleur d’animation. Si vous avez besoin d’ajouter un objet à un autre contrôleur, appelez d’abord SupprimerAnimationObject. Si vous appelez SetID avec un nouveau GroupID pour un objet qui a déjà été ajouté à un groupe, l’objet sera retiré de l’ancien groupe et ajouté à un autre groupe avec UNE pièce d’identité spécifiée.

## <a name="canimationcontrolleraddkeyframetogroup"></a><a name="addkeyframetogroup"></a>CAnimationController::AddKeyframeToGroup

Ajoute un cadre clé au groupe.

```
BOOL AddKeyframeToGroup(
    UINT32 nGroupID,
    CBaseKeyFrame* pKeyframe);
```

### <a name="parameters"></a>Paramètres

*nGroupID (en anglais)*<br/>
Spécifie l’ID du groupe.

*pKeyframe (en)*<br/>
Un pointeur à un cadre clé.

### <a name="return-value"></a>Valeur de retour

VRAI si la fonction réussit; autrement FALSE.

### <a name="remarks"></a>Notes

Habituellement, vous n’avez pas besoin d’appeler cette méthode, utilisez CAnimationController::CreateKeyframe à la place, qui crée et ajoute le cadre de clé créé à un groupe automatiquement.

## <a name="canimationcontrolleranimategroup"></a><a name="animategroup"></a>CAnimationController::AnimateGroup

Prépare un groupe pour exécuter l’animation et l’horaire optionnellement.

```
BOOL AnimateGroup(
    UINT32 nGroupID,
    BOOL bScheduleNow = TRUE);
```

### <a name="parameters"></a>Paramètres

*nGroupID (en anglais)*<br/>
Spécifie GroupID.

*bScheduleNow*<br/>
Précise s’il faut exécuter l’animation tout de suite.

### <a name="return-value"></a>Valeur de retour

VRAI si l’animation a été planifiée avec succès et exécutée.

### <a name="remarks"></a>Notes

Cette méthode fait le travail réel de création storyboard, l’ajout de variables d’animation, l’application de transitions et la définition des clés. Il est possible de retarder la planification si vous définissez bScheduleNow à FALSE. Dans ce cas, le groupe spécifié tiendra un storyboard qui a été mis en place pour l’animation. À ce stade, vous pouvez configurer des événements pour le storyboard et les variables d’animation. Lorsque vous avez réellement besoin d’exécuter l’appel d’animation CAnimationController:ScheduleGroup.

## <a name="canimationcontrollercanimationcontroller"></a><a name="canimationcontroller"></a>CAnimationController::CAnimationController

Construit un contrôleur d’animation.

```
CAnimationController(void);
```

## <a name="canimationcontrollercleanupgroup"></a><a name="cleanupgroup"></a>CAnimationController::CleanUpGroup

Appelé par le cadre pour nettoyer le groupe lorsque l’animation a été programmée.

```
void CleanUpGroup(UINT32 nGroupID);
void CleanUpGroup(CAnimationGroup* pGroup);
```

### <a name="parameters"></a>Paramètres

*nGroupID (en anglais)*<br/>
Spécifie GroupID.

*pGroup (en anglais)*<br/>
Un pointeur pour le groupe d’animation à nettoyer.

### <a name="remarks"></a>Notes

Cette méthode supprime toutes les transitions et les cadres clés du groupe spécifié, car elles ne sont pas pertinentes après qu’une animation a été programmée.

## <a name="canimationcontrollercreatekeyframe"></a><a name="createkeyframe"></a>CAnimationController::CreateKeyframe

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

*nGroupID (en anglais)*<br/>
Spécifie l’ID de groupe pour lequel l’image clé est créée.

*pTransition*<br/>
Pointeur vers la transition. L’image clé sera insérée dans le plan conceptuel après cette transition.

*pKeyframe (en)*<br/>
Pointeur vers l’image clé de base pour cette image clé.

*offset*<br/>
Décalage en secondes à partir de l’image clé de base spécifiée par pKeyframe.

### <a name="return-value"></a>Valeur de retour

Pointeur vers l’image clé nouvellement créée si la fonction réussit.

### <a name="remarks"></a>Notes

Vous pouvez stocker le pointeur retourné et baser les autres images clés sur l’image clé nouvellement créée (voir la deuxième surcharge). Il est possible de commencer des transitions au niveau des images clés : voir CBaseTransition::SetKeyframes. Vous n’avez pas besoin de supprimer les images clés créées de cette façon, car elles sont automatiquement supprimées par les groupes d’animation. Soyez prudent lors de la création d’images clés basées sur d’autres images clés et d’autres transitions, et évitez les références circulaires.

## <a name="canimationcontrollerenableanimationmanagerevent"></a><a name="enableanimationmanagerevent"></a>CAnimationController::EnableAnimationManagerEvent

Définit ou libère un gestionnaire pour appeler lorsque le statut du gestionnaire d’animation change.

```
virtual BOOL EnableAnimationManagerEvent(BOOL bEnable = TRUE);
```

### <a name="parameters"></a>Paramètres

*bEnable*<br/>
Précise s’il faut régler ou libérer un gestionnaire.

### <a name="return-value"></a>Valeur de retour

VRAI si le gestionnaire a été réglé avec succès ou libéré.

### <a name="remarks"></a>Notes

Lorsqu’un gestionnaire est défini (activé) Windows Animation appelle OnAnimationManagerStatusM lorsque l’état du gestionnaire d’animation change.

## <a name="canimationcontrollerenableanimationtimereventhandler"></a><a name="enableanimationtimereventhandler"></a>CAnimationController::EnableAnimationTimerEventHandler

Définit ou libère un gestionnaire pour les événements de chronométrage et gestionnaire pour les mises à jour de synchronisation.

```
virtual BOOL EnableAnimationTimerEventHandler(
    BOOL bEnable = TRUE,
    UI_ANIMATION_IDLE_BEHAVIOR idleBehavior = UI_ANIMATION_IDLE_BEHAVIOR_DISABLE);
```

### <a name="parameters"></a>Paramètres

*bEnable*<br/>
Précise s’il faut régler ou libérer les gestionnaires.

*idleBehavior*<br/>
Spécifie le comportement inactif pour le gestionnaire de mise à jour de minuterie.

### <a name="return-value"></a>Valeur de retour

VRAI si les gestionnaires ont été réglés ou libérés avec succès; FALSE si cette méthode est appelée pour une deuxième fois sans relâcher les gestionnaires en premier, ou si une autre erreur se produit.

### <a name="remarks"></a>Notes

Lorsque les gestionnaires sont définis (activé) Windows Animation API appelle OnAnimationTimerPreUpdate, OnAnimationTimerPostUpdate, OnRenderingTooSlow méthodes. Vous devez activer les minuteries d’animation pour permettre à Windows Animation API mettre à jour les storyboards. Sinon, vous devrez appeler CAnimationController::UpdateAnimationManager afin de diriger le gestionnaire d’animation pour mettre à jour les valeurs de toutes les variables d’animation.

## <a name="canimationcontrollerenableprioritycomparisonhandler"></a><a name="enableprioritycomparisonhandler"></a>CAnimationController::EnablePriorityComparisonHandler

Définit ou libère le gestionnaire de comparaison prioritaire à appeler pour déterminer si un storyboard prévu peut être annulé, conclu, coupé ou comprimé.

```
virtual BOOL EnablePriorityComparisonHandler(DWORD dwHandlerType);
```

### <a name="parameters"></a>Paramètres

*dwHandlerType dwHandlerType*<br/>
Une combinaison de drapeaux UI_ANIMATION_PHT_ (voir remarques), qui précise les gestionnaires à définir ou à libérer.

### <a name="return-value"></a>Valeur de retour

VRAI si le gestionnaire a été réglé avec succès ou libéré.

### <a name="remarks"></a>Notes

Lorsqu’un gestionnaire est défini (activé) Windows Animation appelle les méthodes virtuelles suivantes en fonction de dwHandlerType: OnHasPriorityCancel, OnHasPriorityConclude, OnHasPriorityTrim, OnHasPriorityCompress. dwHandler peut être une combinaison des drapeaux suivants: UI_ANIMATION_PHT_NONE - libérer tous les gestionnaires UI_ANIMATION_PHT_CANCEL - définir Annuler le gestionnaire de comparaison UI_ANIMATION_PHT_CONCLUDE - définir Le gestionnaire de comparaison De conclusion UI_ANIMATION_PHT_COMPRESS - définir compresse gestionnaire de comparaison UI_ANIMATION_PHT_TRIM - définir Trim gestionnaire de comparaison UI_ANIMATION_PHT_CANCEL_REMOVE - supprimer Cancel gestionnaire de comparaison UI_ANIMATION_PHT_CONCLUDE_REMOVE - supprimer Le gestionnaire de comparaison Conclu UI_ANIMATION_PHT_COMPRESS_REMOVE - supprimer compress comparison gestionnaire UI_ANIMATION_PHT_TRIM_REMOVE - supprimer Trim gestionnaire de comparaison

## <a name="canimationcontrollerenablestoryboardeventhandler"></a><a name="enablestoryboardeventhandler"></a>CAnimationController::EnableStoryboardEventHandler

Définit ou libère un gestionnaire pour l’état du storyboard et mettre à jour les événements.

```
virtual BOOL EnableStoryboardEventHandler(
    UINT32 nGroupID,
    BOOL bEnable = TRUE);
```

### <a name="parameters"></a>Paramètres

*nGroupID (en anglais)*<br/>
Spécifie l’ID du groupe.

*bEnable*<br/>
Précise s’il faut régler ou libérer un gestionnaire.

### <a name="return-value"></a>Valeur de retour

VRAI si le gestionnaire a été réglé ou libéré avec succès; FALSE si le groupe d’animation spécifié est maintenant trouvé ou l’animation pour le groupe spécifié n’a pas été initiée et son storyboard interne est NULL.

### <a name="remarks"></a>Notes

Lorsqu’un gestionnaire est défini (activé) Windows Animation API appelle OnStoryboardStatusChanges et OnStoryboardUpdated méthodes virtuelles. Un gestionnaire doit être placé après CAnimationController::Animate a été appelé pour le groupe d’animation spécifié, car il crée encapsulé IUIAnimationStoryboard objet.

## <a name="canimationcontrollerfindanimationgroup"></a><a name="findanimationgroup"></a>CAnimationController::FindAnimationGroup

Trouve un groupe d’animation par son id de groupe.

```
CAnimationGroup* FindAnimationGroup(UINT32 nGroupID);
CAnimationGroup* FindAnimationGroup(IUIAnimationStoryboard* pStoryboard);
```

### <a name="parameters"></a>Paramètres

*nGroupID (en anglais)*<br/>
Spécifie un GroupID.

*pStoryboard (en)*<br/>
Un pointeur à un storyboard.

### <a name="return-value"></a>Valeur de retour

Un pointeur vers le groupe d’animation ou NULL si le groupe avec ID spécifié n’est pas trouvé.

### <a name="remarks"></a>Notes

Utilisez cette méthode pour trouver un groupe d’animation à l’heure de l’exécution. Un groupe est créé et ajouté à la liste interne des groupes d’animation lorsqu’un premier objet d’animation avec GroupID particulier est ajouté au contrôleur d’animation.

## <a name="canimationcontrollerfindanimationobject"></a><a name="findanimationobject"></a>CAnimationController::FindAnimationObject

Trouve un objet d’animation contenant une variable d’animation spécifiée.

```
BOOL FindAnimationObject(
    IUIAnimationVariable* pVariable,
    CAnimationBaseObject** ppObject,
    CAnimationGroup** ppGroup);
```

### <a name="parameters"></a>Paramètres

*pVariable*<br/>
Un pointeur à la variable d’animation.

*ppObject*<br/>
Sortie : Contient un pointeur à l’objet d’animation ou NULL.

*ppGroup (en anglais)*<br/>
Sortie : Contient un pointeur au groupe d’animation qui détient l’objet d’animation, ou NULL.

### <a name="return-value"></a>Valeur de retour

VRAI si l’objet a été trouvé; autrement FALSE.

### <a name="remarks"></a>Notes

Appelé à partir de gestionnaires d’événements quand il est nécessaire de trouver un objet d’animation à partir de la variable d’animation entrante.

## <a name="canimationcontrollergkeyframestoryboardstart"></a><a name="g_keyframestoryboardstart"></a>CAnimationController::gkeyframeStoryboardStart

Un cadre clé qui représente le début du storyboard.

```
static CBaseKeyFrame gkeyframeStoryboardStart;
```

## <a name="canimationcontrollergetkeyframestoryboardstart"></a><a name="getkeyframestoryboardstart"></a>CAnimationController::GetKeyframeStoryboardStart

Retourne un cadre clé qui identifie le début du storyboard.

```
static CBaseKeyFrame* GetKeyframeStoryboardStart();
```

### <a name="return-value"></a>Valeur de retour

Un pointeur pour base de keyframe, qui identifie le début du storyboard.

### <a name="remarks"></a>Notes

Obtenez ce cadre clé pour baser d’autres cadres clés ou transitions sur le moment où un storyboard commence.

## <a name="canimationcontrollergetuianimationmanager"></a><a name="getuianimationmanager"></a>CAnimationController::GetUIAnimationManager

Donne accès à l’objet IUIAnimationManager encapsulé.

```
IUIAnimationManager* GetUIAnimationManager();
```

### <a name="return-value"></a>Valeur de retour

Un pointeur à l’interface IUIAnimationManager ou NULL, si la création de gestionnaire d’animation a échoué.

### <a name="remarks"></a>Notes

Si le système d’exploitation actuel ne prend pas en charge l’API d’animation Windows, cette méthode renvoie NULL et après cela tous les appels ultérieurs sur CAnimationController::IsValid retour FALSE. Vous devrez peut-être accéder à IUIAnimationManager afin d’appeler ses méthodes d’interface, qui ne sont pas enveloppées par le contrôleur d’animation.

## <a name="canimationcontrollergetuianimationtimer"></a><a name="getuianimationtimer"></a>CAnimationController::GetUIAnimationTimer

Donne accès à l’objet IUIAnimationTimer encapsulé.

```
IUIAnimationTimer* GetUIAnimationTimer();
```

### <a name="return-value"></a>Valeur de retour

Un pointeur à l’interface IUIAnimationTimer ou NULL, si la création d’une minuterie d’animation a échoué.

### <a name="remarks"></a>Notes

Si le système d’exploitation actuel ne prend pas en charge l’API d’animation Windows, cette méthode renvoie NULL et après cela tous les appels ultérieurs sur CAnimationController::IsValid retour FALSE.

## <a name="canimationcontrollergetuitransitionfactory"></a><a name="getuitransitionfactory"></a>CAnimationController::GetUITransitionFactory

Un pointeur à l’interface IUIAnimationTransitionFactory ou NULL, si la création de la bibliothèque de transition a échoué.

```
IUIAnimationTransitionFactory* GetUITransitionFactory();
```

### <a name="return-value"></a>Valeur de retour

Un pointeur à IUIAnimationTransitionFactory ou NULL, si la création de l’usine de transition a échoué.

### <a name="remarks"></a>Notes

Si le système d’exploitation actuel ne prend pas en charge l’API d’animation Windows, cette méthode renvoie NULL et après cela tous les appels ultérieurs sur CAnimationController::IsValid retour FALSE.

## <a name="canimationcontrollergetuitransitionlibrary"></a><a name="getuitransitionlibrary"></a>CAnimationController::GetUITransitionLibrary

Donne accès à l’objet IUIAnimationTransitionTransition encapsulé.

```
IUIAnimationTransitionLibrary* GetUITransitionLibrary();
```

### <a name="return-value"></a>Valeur de retour

Un pointeur à IUIAnimationTransitionTransitionL’interfacelibérale ou NULL, si la création de la bibliothèque de transition a échoué.

### <a name="remarks"></a>Notes

Si le système d’exploitation actuel ne prend pas en charge l’API d’animation Windows, cette méthode renvoie NULL et après cela tous les appels ultérieurs sur CAnimationController::IsValid retour FALSE.

## <a name="canimationcontrollerisanimationinprogress"></a><a name="isanimationinprogress"></a>CAnimationController::IsAnimationInProgress

Indique si au moins un groupe joue de l’animation.

```
virtual BOOL IsAnimationInProgress();
```

### <a name="return-value"></a>Valeur de retour

VRAI s’il y a une animation en cours pour ce contrôleur d’animation ; autrement FALSE.

### <a name="remarks"></a>Notes

Vérifie l’état du gestionnaire d’animation et renvoie TRUE si le statut est UI_ANIMATION_MANAGER_BUSY.

## <a name="canimationcontrollerisvalid"></a><a name="isvalid"></a>CAnimationController::IsValid

Indique si le contrôleur d’animation est valide.

```
BOOL IsValid() const;
```

### <a name="return-value"></a>Valeur de retour

VRAI si le contrôleur d’animation est valide; autrement FALSE.

### <a name="remarks"></a>Notes

Cette méthode ne renvoie FALSE que si Windows Animation API n’est pas pris en charge sur le système d’exploitation actuel et la création du gestionnaire d’animation a échoué parce qu’elle n’est pas enregistrée. Vous devez appeler GetUIAnimationManager au moins une fois après l’initialisation des bibliothèques COM pour provoquer le réglage de ce drapeau.

## <a name="canimationcontrollerm_bisvalid"></a><a name="m_bisvalid"></a>CAnimationController::m_bIsValid

Précise si un contrôleur d’animation est valide ou non. Ce membre est configuré à FALSE si le système d’exploitation actuel ne prend pas en charge l’API d’animation Windows.

```
BOOL m_bIsValid;
```

## <a name="canimationcontrollerm_lstanimationgroups"></a><a name="m_lstanimationgroups"></a>CAnimationController::m_lstAnimationGroups

Une liste de groupes d’animation qui appartiennent à ce contrôleur d’animation.

```
CList<CAnimationGroup*, CAnimationGroup*> m_lstAnimationGroups;
```

## <a name="canimationcontrollerm_panimationmanager"></a><a name="m_panimationmanager"></a>CAnimationController::m_pAnimationManager

Stocke un pointeur vers l’objet Animation Manager COM.

```
ATL::CComPtr<IUIAnimationManager> m_pAnimationManager;
```

## <a name="canimationcontrollerm_panimationtimer"></a><a name="m_panimationtimer"></a>CAnimationController::m_pAnimationTimer

Stocke un pointeur vers l’objet Animation Timer COM.

```
ATL::CComPtr<IUIAnimationTimer> m_pAnimationTimer;
```

## <a name="canimationcontrollerm_prelatedwnd"></a><a name="m_prelatedwnd"></a>CAnimationController::m_pRelatedWnd

Un pointeur vers un objet CWnd connexe, qui peut être automatiquement redessiné lorsque l’état du gestionnaire d’animation a changé, ou l’événement de mise à jour post s’est produit. Sa valeur peut être NULL.

```
CWnd* m_pRelatedWnd;
```

## <a name="canimationcontrollerm_ptransitionfactory"></a><a name="m_ptransitionfactory"></a>CAnimationController::m_pTransitionFactory

Stocke un pointeur vers l’objet Transition Factory COM.

```
ATL::CComPtr<IUIAnimationTransitionFactory> m_pTransitionFactory;
```

## <a name="canimationcontrollerm_ptransitionlibrary"></a><a name="m_ptransitionlibrary"></a>CAnimationController::m_pTransitionLibrary

Stocke un pointeur vers l’objet TRANSITION Library COM.

```
ATL::CComPtr<IUIAnimationTransitionLibrary> m_pTransitionLibrary;
```

## <a name="canimationcontrolleronafterschedule"></a><a name="onafterschedule"></a>CAnimationController::OnAfterSchedule

Appelé par le cadre quand une animation pour le groupe spécifié vient d’être programmée.

```
virtual void OnAfterSchedule(CAnimationGroup* pGroup);
```

### <a name="parameters"></a>Paramètres

*pGroup (en anglais)*<br/>
Un pointeur pour un groupe d’animation, qui a été programmé.

### <a name="remarks"></a>Notes

La mise en œuvre par défaut supprime les cadres clés du groupe spécifié et les transitions des variables d’animation qui appartiennent au groupe spécifié. Peut être remplacé dans une classe dérivée pour prendre toutes les mesures supplémentaires sur le calendrier d’animation.

## <a name="canimationcontrolleronanimationintegervaluechanged"></a><a name="onanimationintegervaluechanged"></a>CAnimationController::OnAnimationIntegerValueChanged

Appelé par le cadre lorsque la valeur integer de la variable d’animation a changé.

```
virtual void OnAnimationIntegerValueChanged(
    CAnimationGroup* pGroup,
    CAnimationBaseObject* pObject,
    IUIAnimationVariable* variable,
    INT32 newValue,
    INT32 prevValue);
```

### <a name="parameters"></a>Paramètres

*pGroup (en anglais)*<br/>
Un pointeur pour un groupe d’animation qui détient un objet d’animation dont la valeur a changé.

*pObject*<br/>
Pointeur d’un objet d’animation qui contient une variable d’animation dont la valeur a changé.

*variable*<br/>
Un pointeur à une variable d’animation.

*Newvalue*<br/>
Spécifie une nouvelle valeur.

*prevValue*<br/>
Spécifie la valeur précédente.

### <a name="remarks"></a>Notes

Cette méthode s’appelle si vous activez des événements variables d’animation avec EnableIntegerValueChangedEvent appelé pour une variable d’animation spécifique ou un objet d’animation. Elle peut être substituée dans une classe dérivée pour prendre des mesures propres à l'application.

## <a name="canimationcontrolleronanimationmanagerstatuschanged"></a><a name="onanimationmanagerstatuschanged"></a>CAnimationController::OnAnimationManagerStatusChanged

Appelé par le cadre en réponse à l’événement StatusChanged du directeur de l’animation.

```
virtual void OnAnimationManagerStatusChanged(
    UI_ANIMATION_MANAGER_STATUS newStatus,
    UI_ANIMATION_MANAGER_STATUS previousStatus);
```

### <a name="parameters"></a>Paramètres

*nouveauStatus*<br/>
Nouveau statut de directeur d’animation.

*précédentStatus*<br/>
Statut de directeur d’animation précédent.

### <a name="remarks"></a>Notes

Cette méthode s’appelle si vous activez des événements de gestionnaire d’animation avec EnableAnimationManagerEvent. Elle peut être substituée dans une classe dérivée pour prendre des mesures propres à l'application. L’implémentation par défaut met à jour une fenêtre connexe si elle a été définie avec SetRelatedWnd.

## <a name="canimationcontrolleronanimationtimerpostupdate"></a><a name="onanimationtimerpostupdate"></a>CAnimationController::OnAnimationTimerPostUpdate

Appelé par le cadre après une mise à jour d’animation est terminée.

```
virtual void OnAnimationTimerPostUpdate();
```

### <a name="remarks"></a>Notes

Cette méthode s’appelle si vous activez les gestionnaires d’événements minuteurs à l’aide de EnableAnimationTimerEventHandler. Elle peut être substituée dans une classe dérivée pour prendre des mesures propres à l'application.

## <a name="canimationcontrolleronanimationtimerpreupdate"></a><a name="onanimationtimerpreupdate"></a>CAnimationController::OnAnimationTimerPreUpdate

Appelé par le cadre avant une mise à jour d’animation commence.

```
virtual void OnAnimationTimerPreUpdate();
```

### <a name="remarks"></a>Notes

Cette méthode s’appelle si vous activez les gestionnaires d’événements minuteurs à l’aide de EnableAnimationTimerEventHandler. Elle peut être substituée dans une classe dérivée pour prendre des mesures propres à l'application.

## <a name="canimationcontrolleronanimationtimerrenderingtooslow"></a><a name="onanimationtimerrenderingtooslow"></a>CAnimationController::OnAnimationTimerenderingTooSlow

Appelé par le cadre lorsque le taux d’image de rendu pour une animation tombe en dessous d’un taux d’image minimum souhaitable.

```
virtual void OnAnimationTimerRenderingTooSlow(UINT32 fps);
```

### <a name="parameters"></a>Paramètres

*Fps*<br/>
Le taux d’image actuel dans les images par seconde.

### <a name="remarks"></a>Notes

Cette méthode s’appelle si vous activez les gestionnaires d’événements minuteurs à l’aide de EnableAnimationTimerEventHandler. Elle peut être substituée dans une classe dérivée pour prendre des mesures propres à l'application. Le taux d’image minimum souhaitable est spécifié en appelant IUIAnimationTimer::SetFrameRateThreshold.

## <a name="canimationcontrolleronanimationvaluechanged"></a><a name="onanimationvaluechanged"></a>CAnimationController::OnAnimationValueChanged

Appelé par le cadre lorsque la valeur de la variable d’animation a changé.

```
virtual void OnAnimationValueChanged(
    CAnimationGroup* pGroup,
    CAnimationBaseObject* pObject,
    IUIAnimationVariable* variable,
    DOUBLE newValue,
    DOUBLE prevValue);
```

### <a name="parameters"></a>Paramètres

*pGroup (en anglais)*<br/>
Un pointeur pour un groupe d’animation qui détient un objet d’animation dont la valeur a changé.

*pObject*<br/>
Pointeur d’un objet d’animation qui contient une variable d’animation dont la valeur a changé.

*variable*<br/>
Un pointeur à une variable d’animation.

*Newvalue*<br/>
Spécifie une nouvelle valeur.

*prevValue*<br/>
Spécifie la valeur précédente.

### <a name="remarks"></a>Notes

Cette méthode s’appelle si vous activez des événements variables d’animation avec EnableValueChangedEvent appelé pour une variable d’animation spécifique ou un objet d’animation. Elle peut être substituée dans une classe dérivée pour prendre des mesures propres à l'application.

## <a name="canimationcontrolleronbeforeanimationstart"></a><a name="onbeforeanimationstart"></a>CAnimationController::OnBeforeAnimationStart

Appelé par le cadre juste avant l’animation est prévue.

```
virtual void OnBeforeAnimationStart(CAnimationGroup* pGroup);
```

### <a name="parameters"></a>Paramètres

*pGroup (en anglais)*<br/>
Un pointeur pour un groupe d’animation dont l’animation est sur le point de commencer.

### <a name="remarks"></a>Notes

Cet appel est acheminé vers CWnd connexe et peut être remplacé dans une classe dérivée pour effectuer toutes les actions supplémentaires avant que l’animation commence pour le groupe spécifié.

## <a name="canimationcontrolleronhasprioritycancel"></a><a name="onhasprioritycancel"></a>CAnimationController::OnHasPriorityCancel

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

*prioritéEffect*<br/>
Effet potentiel sur pGroupNew si pGroupScheduled a une priorité plus élevée.

### <a name="return-value"></a>Valeur de retour

Doit retourner TRUE si le plan conceptuel détenu par pGroupNew est prioritaire. Doit retourner FALSE si le plan conceptuel détenu par pGroupScheduled est prioritaire.

### <a name="remarks"></a>Notes

Cette méthode est appelée si vous activez les événements de comparaison de priorité à l'aide de CAnimationController::EnablePriorityComparisonHandler et que vous spécifiez UI_ANIMATION_PHT_CANCEL. Elle peut être substituée dans une classe dérivée pour prendre des mesures propres à l'application. Lire la documentation de Windows Animation API pour plus d’informations sur [la gestion des conflits](/windows/win32/api/uianimation/nf-uianimation-iuianimationprioritycomparison-haspriority).

## <a name="canimationcontrolleronhasprioritycompress"></a><a name="onhasprioritycompress"></a>CAnimationController::OnHasPriorityCompress

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

*prioritéEffect*<br/>
Effet potentiel sur pGroupNew si pGroupScheduled a une priorité plus élevée.

### <a name="return-value"></a>Valeur de retour

Doit retourner TRUE si le plan conceptuel détenu par pGroupNew est prioritaire. Doit retourner FALSE si le plan conceptuel détenu par pGroupScheduled est prioritaire.

### <a name="remarks"></a>Notes

Cette méthode est appelée si vous activez les événements de comparaison de priorité à l'aide de CAnimationController::EnablePriorityComparisonHandler et que vous spécifiez UI_ANIMATION_PHT_COMPRESS. Elle peut être substituée dans une classe dérivée pour prendre des mesures propres à l'application. Lire la documentation de Windows Animation API pour plus d’informations sur [la gestion des conflits](/windows/win32/api/uianimation/nf-uianimation-iuianimationprioritycomparison-haspriority).

## <a name="canimationcontrolleronhaspriorityconclude"></a><a name="onhaspriorityconclude"></a>CAnimationController::OnHasPriorityConclude

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

*prioritéEffect*<br/>
Effet potentiel sur pGroupNew si pGroupScheduled a une priorité plus élevée.

### <a name="return-value"></a>Valeur de retour

Doit retourner TRUE si le plan conceptuel détenu par pGroupNew est prioritaire. Doit retourner FALSE si le plan conceptuel détenu par pGroupScheduled est prioritaire.

### <a name="remarks"></a>Notes

Cette méthode est appelée si vous activez les événements de comparaison de priorité à l'aide de CAnimationController::EnablePriorityComparisonHandler et que vous spécifiez UI_ANIMATION_PHT_CONCLUDE. Elle peut être substituée dans une classe dérivée pour prendre des mesures propres à l'application. Lire la documentation de Windows Animation API pour plus d’informations sur [la gestion des conflits](/windows/win32/api/uianimation/nf-uianimation-iuianimationprioritycomparison-haspriority).

## <a name="canimationcontrolleronhasprioritytrim"></a><a name="onhasprioritytrim"></a>CAnimationController::OnHasPriorityTrim

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

*prioritéEffect*<br/>
Effet potentiel sur pGroupNew si pGroupScheduled a une priorité plus élevée.

### <a name="return-value"></a>Valeur de retour

Doit retourner TRUE si le plan conceptuel détenu par pGroupNew est prioritaire. Doit retourner FALSE si le plan conceptuel détenu par pGroupScheduled est prioritaire.

### <a name="remarks"></a>Notes

Cette méthode est appelée si vous activez les événements de comparaison de priorité à l'aide de CAnimationController::EnablePriorityComparisonHandler et que vous spécifiez UI_ANIMATION_PHT_TRIM. Elle peut être substituée dans une classe dérivée pour prendre des mesures propres à l'application. Lire la documentation de Windows Animation API pour plus d’informations sur [la gestion des conflits](/windows/win32/api/uianimation/nf-uianimation-iuianimationprioritycomparison-haspriority).

## <a name="canimationcontrolleronstoryboardstatuschanged"></a><a name="onstoryboardstatuschanged"></a>CAnimationController::OnStoryboardStatusChanged

Appelé par le cadre lorsque le statut storyboard a changé.

```
virtual void OnStoryboardStatusChanged(
    CAnimationGroup* pGroup,
    UI_ANIMATION_STORYBOARD_STATUS newStatus,
    UI_ANIMATION_STORYBOARD_STATUS previousStatus);
```

### <a name="parameters"></a>Paramètres

*pGroup (en anglais)*<br/>
Un pointeur pour un groupe d’animation qui possède le storyboard dont le statut a changé.

*nouveauStatus*<br/>
Spécifie le nouveau statut.

*précédentStatus*<br/>
Spécifie le statut précédent.

### <a name="remarks"></a>Notes

Cette méthode s’appelle si vous activez des événements storyboard en utilisant CAnimationController::EnableStoryboardEventHandler. Elle peut être substituée dans une classe dérivée pour prendre des mesures propres à l'application.

## <a name="canimationcontrolleronstoryboardupdated"></a><a name="onstoryboardupdated"></a>CAnimationController::OnStoryboardUpdated

Appelé par le cadre lorsque storyboard a été mis à jour.

```
virtual void OnStoryboardUpdated(CAnimationGroup* pGroup);
```

### <a name="parameters"></a>Paramètres

*pGroup (en anglais)*<br/>
Un pointeur pour un groupe qui possède le storyboard.

### <a name="remarks"></a>Notes

Cette méthode s’appelle si vous activez des événements storyboard en utilisant CAnimationController::EnableStoryboardEventHandler. Elle peut être substituée dans une classe dérivée pour prendre des mesures propres à l'application.

## <a name="canimationcontrollerremoveallanimationgroups"></a><a name="removeallanimationgroups"></a>CAnimationController::RemoveAllAnimationGroups

Supprime tous les groupes d’animation du contrôleur d’animation.

```
void RemoveAllAnimationGroups();
```

### <a name="remarks"></a>Notes

Tous les groupes seront supprimés, leur pointeur, s’il est stocké au niveau de l’application, doit être invalidé. Si CAnimationGroup:m_bAutodestroyAnimationObjects pour un groupe supprimé est VRAI, tous les objets d’animation qui appartiennent à ce groupe seront supprimés; sinon, leurs références au contrôleur d’animation parent seront réglées à NULL et elles peuvent être ajoutées à un autre contrôleur.

## <a name="canimationcontrollerremoveanimationgroup"></a><a name="removeanimationgroup"></a>CAnimationController::RemoveAnimationGroup

Supprime un groupe d’animation avec un ID spécifié du contrôleur d’animation.

```
void RemoveAnimationGroup(UINT32 nGroupID);
```

### <a name="parameters"></a>Paramètres

*nGroupID (en anglais)*<br/>
Spécifie l’ID du groupe d’animation.

### <a name="remarks"></a>Notes

Cette méthode supprime un groupe d’animation de la liste interne des groupes et le supprime, donc si vous avez stocké un pointeur à ce groupe d’animation, il doit être invalidé. Si CAnimationGroup:m_bAutodestroyAnimationObjects est VRAI, tous les objets d’animation qui appartiennent à ce groupe seront supprimés; sinon, leurs références au contrôleur d’animation parent seront réglées à NULL et elles peuvent être ajoutées à un autre contrôleur.

## <a name="canimationcontrollerremoveanimationobject"></a><a name="removeanimationobject"></a>CAnimationController::Supprimer l’élégationObject

Retirez un objet d’animation du contrôleur d’animation.

```
void RemoveAnimationObject(
    CAnimationBaseObject* pObject,
    BOOL bNoDelete = FALSE);
```

### <a name="parameters"></a>Paramètres

*pObject*<br/>
Un pointeur à un objet d’animation.

*bNoDelete*<br/>
Si ce paramètre est VRAI, l’objet ne sera pas supprimé à la suppression.

### <a name="remarks"></a>Notes

Supprime un objet d’animation du contrôleur d’animation et du groupe d’animation. Appelez cette fonction si un objet particulier ne doit plus être animé, ou si vous avez besoin de déplacer l’objet vers un autre contrôleur d’animation. Dans le dernier cas bNoDelete doit être VRAI.

## <a name="canimationcontrollerremovetransitions"></a><a name="removetransitions"></a>CAnimationController::RemoveTransitions

Supprime les transitions des objets d’animation qui appartiennent au groupe spécifié.

```
void RemoveTransitions(UINT32 nGroupID);
```

### <a name="parameters"></a>Paramètres

*nGroupID (en anglais)*<br/>
Spécifie l’ID du groupe.

### <a name="remarks"></a>Notes

Le groupe boucle ses objets d’animation et appelle ClearTransitions (FALSE) pour chaque objet d’animation. Cette méthode est appelée par le cadre après l’animation a été prévue.

## <a name="canimationcontrollerschedulegroup"></a><a name="schedulegroup"></a>CAnimationController::Groupe d’horaires

Planifie une animation.

```
BOOL ScheduleGroup(
    UINT32 nGroupID,
    UI_ANIMATION_SECONDS time = 0.0);
```

### <a name="parameters"></a>Paramètres

*nGroupID (en anglais)*<br/>
Spécifie l’ID du groupe d’animation à l’horaire.

*Temps*<br/>
Spécifie le temps de planifier.

### <a name="return-value"></a>Valeur de retour

VRAI si l’animation était programmée avec succès. FALSE si storyboard n’a pas été créé, ou une autre erreur se produit.

### <a name="remarks"></a>Notes

Vous devez appeler AnimateGroup avec le paramètre bScheduleNow réglé à FALSE Prior ScheduleGroup. Vous pouvez spécifier le temps d’animation souhaité obtenu à partir de IUIAnimationTimer::GetTime. Si le paramètre de temps est de 0,0, l’animation est programmée pour l’heure actuelle.

## <a name="canimationcontrollersetrelatedwnd"></a><a name="setrelatedwnd"></a>CAnimationController::SetRelatedWnd

Établit une relation entre le contrôleur d’animation et une fenêtre.

```
void SetRelatedWnd(CWnd* pWnd);
```

### <a name="parameters"></a>Paramètres

*Pwnd*<br/>
Un pointeur à l’objet de fenêtre à régler.

### <a name="remarks"></a>Notes

Si un objet CWnd connexe est défini, le contrôleur d’animation peut automatiquement le mettre à jour (envoyer WM_PAINT message) lorsque l’état du gestionnaire d’animation a changé ou que l’événement de mise à jour de la minuterie s’est produit.

## <a name="canimationcontrollerupdateanimationmanager"></a><a name="updateanimationmanager"></a>CAnimationController::Mise à jourAnimationManager

Dirige le responsable de l’animation pour mettre à jour les valeurs de toutes les variables d’animation.

```
virtual void UpdateAnimationManager();
```

### <a name="remarks"></a>Notes

Appeler cette méthode avance le gestionnaire d’animation à l’heure actuelle, en changeant les statuts des storyboards au besoin et la mise à jour de toutes les variables d’animation à des valeurs interpolées appropriées. En interne, cette méthode appelle IUIAnimationTimer::GetTime (timeNow) et IUIAnimationManager::Update (timeNow). Remplacer cette méthode dans une classe dérivée pour personnaliser ce comportement.

## <a name="see-also"></a>Voir aussi

[Classes](../../mfc/reference/mfc-classes.md)
