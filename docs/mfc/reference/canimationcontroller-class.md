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
ms.openlocfilehash: a3a533b876b9ca245c0553c4c24a815ef3cabca1
ms.sourcegitcommit: 309dc532f13242854b47759cef846de59bb807f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/28/2019
ms.locfileid: "58565959"
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
|[CAnimationController::CAnimationController](#canimationcontroller)|Construit un contrôleur de l’animation.|
|[CAnimationController :: ~ CAnimationController](#_dtorcanimationcontroller)|Destructeur. Appelée lorsque l’objet de contrôleur de l’animation est détruit.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CAnimationController::AddAnimationObject](#addanimationobject)|Ajoute un objet d’animation à un groupe auquel appartient le contrôleur de l’animation.|
|[CAnimationController::AddKeyframeToGroup](#addkeyframetogroup)|Ajoute une image clé au groupe.|
|[CAnimationController::AnimateGroup](#animategroup)|Prépare un groupe pour exécuter l’animation et le planifie si vous le souhaitez.|
|[CAnimationController::CleanUpGroup](#cleanupgroup)|Surchargé. Appelé par l’infrastructure pour nettoyer le groupe lors de l’animation a été planifiée.|
|[CAnimationController::CreateKeyframe](#createkeyframe)|Surchargé. Crée une image clé qui dépend de la transition et l’ajoute au groupe spécifié.|
|[CAnimationController::EnableAnimationManagerEvent](#enableanimationmanagerevent)|Définit ou libère un gestionnaire à appeler lorsque l’état du Gestionnaire d’animations.|
|[CAnimationController::EnableAnimationTimerEventHandler](#enableanimationtimereventhandler)|Définit ou libère un gestionnaire d’événements de minutage et Gestionnaire de synchronisation de mises à jour.|
|[CAnimationController::EnablePriorityComparisonHandler](#enableprioritycomparisonhandler)|Définit ou libère le Gestionnaire de comparaison de priorité à appeler pour déterminer si un storyboard planifié peut être annulé, conclu, supprimé ou compressé.|
|[CAnimationController::EnableStoryboardEventHandler](#enablestoryboardeventhandler)|Définit ou libère un gestionnaire d’événements de statut et de mise à jour de table de montage séquentiel.|
|[CAnimationController::FindAnimationGroup](#findanimationgroup)|Surchargé. Recherche un groupe d’animation par son storyboard.|
|[CAnimationController::FindAnimationObject](#findanimationobject)|Recherche l’objet d’animation contenant une variable d’animation spécifiée.|
|[CAnimationController::GetKeyframeStoryboardStart](#getkeyframestoryboardstart)|Retourne une image clé qui identifie le début de la table de montage séquentiel.|
|[CAnimationController::GetUIAnimationManager](#getuianimationmanager)|Fournit l’accès à l’objet IUIAnimationManager encapsulé.|
|[CAnimationController::GetUIAnimationTimer](#getuianimationtimer)|Fournit l’accès à l’objet IUIAnimationTimer encapsulé.|
|[CAnimationController::GetUITransitionFactory](#getuitransitionfactory)|Un pointeur vers l’interface IUIAnimationTransitionFactory ou NULL si l’échec de la création de la bibliothèque de transition.|
|[CAnimationController::GetUITransitionLibrary](#getuitransitionlibrary)|Fournit l’accès à l’objet IUIAnimationTransitionLibrary encapsulé.|
|[CAnimationController::IsAnimationInProgress](#isanimationinprogress)|Indique si au moins un groupe joue l’animation.|
|[CAnimationController::IsValid](#isvalid)|Indique si le contrôleur de l’animation est valide.|
|[CAnimationController::OnAnimationIntegerValueChanged](#onanimationintegervaluechanged)|Appelé par l’infrastructure lors de la valeur entière de la variable de l’animation a changé.|
|[CAnimationController::OnAnimationManagerStatusChanged](#onanimationmanagerstatuschanged)|Appelé par l’infrastructure en réponse à un événement StatusChanged du Gestionnaire d’animations.|
|[CAnimationController::OnAnimationTimerPostUpdate](#onanimationtimerpostupdate)|Appelé par le framework après qu’une mise à jour de l’animation est terminée.|
|[CAnimationController::OnAnimationTimerPreUpdate](#onanimationtimerpreupdate)|Appelé par l’infrastructure avant le début d’une mise à jour de l’animation.|
|[CAnimationController::OnAnimationTimerRenderingTooSlow](#onanimationtimerrenderingtooslow)|Appelé par l’infrastructure lorsque la fréquence d’images de rendu pour une animation tombe en dessous d’une fréquence d’images souhaitable minimale.|
|[CAnimationController::OnAnimationValueChanged](#onanimationvaluechanged)|Appelé par l’infrastructure lors de la valeur de variable de l’animation a changé.|
|[CAnimationController::OnBeforeAnimationStart](#onbeforeanimationstart)|Appelé par l’infrastructure appropriée avant de l’animation est planifiée.|
|[CAnimationController::OnHasPriorityCancel](#onhasprioritycancel)|Appelé par l'infrastructure pour résoudre les conflits de planification.|
|[CAnimationController::OnHasPriorityCompress](#onhasprioritycompress)|Appelé par l'infrastructure pour résoudre les conflits de planification.|
|[CAnimationController::OnHasPriorityConclude](#onhaspriorityconclude)|Appelé par l'infrastructure pour résoudre les conflits de planification.|
|[CAnimationController::OnHasPriorityTrim](#onhasprioritytrim)|Appelé par l'infrastructure pour résoudre les conflits de planification.|
|[CAnimationController::OnStoryboardStatusChanged](#onstoryboardstatuschanged)|Appelé par l’infrastructure lorsque l’état de la table de montage séquentiel a changé.|
|[CAnimationController::OnStoryboardUpdated](#onstoryboardupdated)|Appelé par l’infrastructure lors de la table de montage séquentiel a été mis à jour.|
|[CAnimationController::RemoveAllAnimationGroups](#removeallanimationgroups)|Supprime tous les groupes d’animation de contrôleur de l’animation.|
|[CAnimationController::RemoveAnimationGroup](#removeanimationgroup)|Supprime un groupe d’animation avec l’ID spécifié à partir du contrôleur de l’animation.|
|[CAnimationController::RemoveAnimationObject](#removeanimationobject)|Supprimer un objet d’animation de contrôleur de l’animation.|
|[CAnimationController::RemoveTransitions](#removetransitions)|Supprime les transitions des objets d’animation qui appartiennent au groupe spécifié.|
|[CAnimationController::ScheduleGroup](#schedulegroup)|Planifie une animation.|
|[CAnimationController::SetRelatedWnd](#setrelatedwnd)|Établit une relation entre le contrôleur de l’animation et une fenêtre.|
|[CAnimationController::UpdateAnimationManager](#updateanimationmanager)|Dirige le Gestionnaire d’animations pour mettre à jour les valeurs de toutes les variables de l’animation.|

### <a name="protected-methods"></a>Méthodes protégées

|Nom|Description|
|----------|-----------------|
|[CAnimationController::CleanUpGroup](#cleanupgroup)|Surchargé. Un programme d’assistance qui nettoie le groupe.|
|[CAnimationController::OnAfterSchedule](#onafterschedule)|Appelé par l’infrastructure lorsqu’une animation pour le groupe spécifié a simplement été planifiée.|

### <a name="protected-data-members"></a>Membres de données protégés

|Nom|Description|
|----------|-----------------|
|[CAnimationController::gkeyframeStoryboardStart](#g_keyframestoryboardstart)|Une image clé qui représente le début de la table de montage séquentiel.|
|[CAnimationController::m_bIsValid](#m_bisvalid)|Spécifie si un contrôleur de l’animation est valide ou non. Ce membre est défini sur FALSE si le système d’exploitation actuel ne prend pas en charge les API d’Animation de Windows.|
|[CAnimationController::m_lstAnimationGroups](#m_lstanimationgroups)|Une liste des groupes d’animation qui appartiennent à ce contrôleur de l’animation.|
|[CAnimationController::m_pAnimationManager](#m_panimationmanager)|Stocke un pointeur vers l’objet COM du Gestionnaire d’animations.|
|[CAnimationController::m_pAnimationTimer](#m_panimationtimer)|Stocke un pointeur vers l’objet COM de minuterie d’Animation.|
|[CAnimationController::m_pRelatedWnd](#m_prelatedwnd)|Pointeur vers un objet CWnd connexe, qui peut être redessiné automatiquement lorsque l’état du Gestionnaire d’animations a changé, ou publier un événement mise à jour s’est produite. Peut être NULL.|
|[CAnimationController::m_pTransitionFactory](#m_ptransitionfactory)|Stocke un pointeur vers l’objet COM de fabrique de Transition.|
|[CAnimationController::m_pTransitionLibrary](#m_ptransitionlibrary)|Stocke un pointeur vers l’objet COM de bibliothèque de Transition.|

## <a name="remarks"></a>Notes

La classe CAnimationController est la classe clé qui gère les animations. Vous pouvez créer une ou plusieurs instances de contrôleur de l’animation dans une application et, éventuellement, se connecter à une instance de contrôleur de l’animation à un objet CWnd à l’aide de CAnimationController::SetRelatedWnd. Cette connexion est nécessaire pour envoyer automatiquement des messages WM_PAINT à la fenêtre associée lors de l’état du Gestionnaire d’animations a changé ou la minuterie d’animation a été mis à jour. Si vous n’activez pas cette relation, vous devez redessiner une fenêtre qui affiche une animation manuellement. Pour cela, vous pouvez dériver une classe de CAnimationController et remplacer OnAnimationManagerStatusChanged et/ou OnAnimationTimerPostUpdate et invalider une ou plusieurs fenêtres lorsque cela est nécessaire.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

`CAnimationController`

## <a name="requirements"></a>Configuration requise

**En-tête :** afxanimationcontroller.h

##  <a name="_dtorcanimationcontroller"></a>  CAnimationController::~CAnimationController

Destructeur. Appelée lorsque l’objet de contrôleur de l’animation est détruit.

```
virtual ~CAnimationController(void);
```

##  <a name="addanimationobject"></a>  CAnimationController::AddAnimationObject

Ajoute un objet d’animation à un groupe auquel appartient le contrôleur de l’animation.

```
CAnimationGroup* AddAnimationObject(CAnimationBaseObject* pObject);
```

### <a name="parameters"></a>Paramètres

*pObject*<br/>
Pointeur vers un objet d’animation.

### <a name="return-value"></a>Valeur de retour

Un pointeur vers le groupe d’animation de nouveau ou existant où pObject a été ajouté si la fonction aboutit ; NULL si pObject a déjà été ajouté à un groupe qui appartient à un autre contrôleur de l’animation.

### <a name="remarks"></a>Notes

Appelez cette méthode pour ajouter un objet d’animation au contrôleur de l’animation. Un objet est ajouté à un groupe en fonction de GroupID l’objet (voir CAnimationBaseObject::SetID). Le contrôleur de l’animation crée un nouveau groupe s’il est le premier objet ajouté avec le GroupID spécifié. Un objet d’animation peut être ajouté au contrôleur une animation uniquement. Si vous avez besoin ajouter un objet vers un autre contrôleur, appelez d’abord RemoveAnimationObject. Si vous appelez SetID avec un nouveau GroupID pour un objet qui a déjà été ajouté à un groupe, l’objet est supprimé de l’ancien groupe et ajouté à un autre groupe avec l’ID spécifié.

##  <a name="addkeyframetogroup"></a>  CAnimationController::AddKeyframeToGroup

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

### <a name="return-value"></a>Valeur de retour

TRUE si la fonction aboutit ; Sinon, FALSE.

### <a name="remarks"></a>Notes

Généralement vous n’avez pas besoin d’appeler cette méthode, utilisez CAnimationController::CreateKeyframe de préférence, ce qui crée et ajoute l’image clé créée à un groupe automatiquement.

##  <a name="animategroup"></a>  CAnimationController::AnimateGroup

Prépare un groupe pour exécuter l’animation et le planifie si vous le souhaitez.

```
BOOL AnimateGroup(
    UINT32 nGroupID,
    BOOL bScheduleNow = TRUE);
```

### <a name="parameters"></a>Paramètres

*nGroupID*<br/>
Spécifie un GroupID.

*bScheduleNow*<br/>
Spécifie s’il faut exécuter animation tout de suite.

### <a name="return-value"></a>Valeur de retour

TRUE si l’animation a été correctement planifiée et exécutée.

### <a name="remarks"></a>Notes

Cette méthode effectue le travail Création de table de montage séquentiel, ajout de variables de l’animation, application de transitions et définition d’images clés. Il est possible de différer la planification si vous définissez bScheduleNow sur FALSE. Dans ce cas le groupe spécifié contient un storyboard qui a été configuré pour l’animation. À ce stade, vous pouvez configurer les événements pour les variables de table de montage séquentiel et l’animation. Lorsque vous devez réellement exécuter l’appel de l’animation CAnimationController::ScheduleGroup.

##  <a name="canimationcontroller"></a>  CAnimationController::CAnimationController

Construit un contrôleur de l’animation.

```
CAnimationController(void);
```

##  <a name="cleanupgroup"></a>  CAnimationController::CleanUpGroup

Appelé par l’infrastructure pour nettoyer le groupe lors de l’animation a été planifiée.

```
void CleanUpGroup(UINT32 nGroupID);
void CleanUpGroup(CAnimationGroup* pGroup);
```

### <a name="parameters"></a>Paramètres

*nGroupID*<br/>
Spécifie un GroupID.

*pGroup*<br/>
Pointeur vers le groupe d’animation à nettoyer.

### <a name="remarks"></a>Notes

Cette méthode supprime toutes les transitions et les images clés du groupe spécifié, car ils ne sont pas pertinentes après qu’une animation a été planifiée.

##  <a name="createkeyframe"></a>  CAnimationController::CreateKeyframe

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

### <a name="return-value"></a>Valeur de retour

Pointeur vers l’image clé nouvellement créée si la fonction réussit.

### <a name="remarks"></a>Notes

Vous pouvez stocker le pointeur retourné et baser les autres images clés sur l’image clé nouvellement créée (voir la deuxième surcharge). Il est possible de commencer des transitions au niveau des images clés : voir CBaseTransition::SetKeyframes. Vous n’avez pas besoin de supprimer les images clés créées de cette façon, car elles sont automatiquement supprimées par les groupes d’animation. Soyez prudent lors de la création d’images clés basées sur d’autres images clés et d’autres transitions, et évitez les références circulaires.

##  <a name="enableanimationmanagerevent"></a>  CAnimationController::EnableAnimationManagerEvent

Définit ou libère un gestionnaire à appeler lorsque l’état du Gestionnaire d’animations.

```
virtual BOOL EnableAnimationManagerEvent(BOOL bEnable = TRUE);
```

### <a name="parameters"></a>Paramètres

*bEnable*<br/>
Spécifie s’il faut définir ou de libérer un gestionnaire.

### <a name="return-value"></a>Valeur de retour

TRUE si le gestionnaire a été correctement défini ou publié.

### <a name="remarks"></a>Notes

Lorsqu’un gestionnaire est défini (activé) Windows Animation appelle OnAnimationManagerStatusChanged lorsque l’état du Gestionnaire d’animation change.

##  <a name="enableanimationtimereventhandler"></a>  CAnimationController::EnableAnimationTimerEventHandler

Définit ou libère un gestionnaire d’événements de minutage et Gestionnaire de synchronisation de mises à jour.

```
virtual BOOL EnableAnimationTimerEventHandler(
    BOOL bEnable = TRUE,
    UI_ANIMATION_IDLE_BEHAVIOR idleBehavior = UI_ANIMATION_IDLE_BEHAVIOR_DISABLE);
```

### <a name="parameters"></a>Paramètres

*bEnable*<br/>
Spécifie s’il faut définir ou de libérer les gestionnaires.

*idleBehavior*<br/>
Spécifie le comportement inactif pour le Gestionnaire de mise à jour du minuteur.

### <a name="return-value"></a>Valeur de retour

TRUE si les gestionnaires ont été correctement définis ou libérés ; FALSE si cette méthode est appelée une deuxième fois sans libérer les gestionnaires d’abord, ou si toute autre erreur se produit.

### <a name="remarks"></a>Notes

Lorsque les gestionnaires sont définis (activés) appels d’API d’Animation Windows OnAnimationTimerPreUpdate, OnAnimationTimerPostUpdate et OnRenderingTooSlow. Vous devez activer les minuteries de l’animation autoriser des storyboards de mise à jour de l’API Windows Animation. Sinon, vous devez appeler CAnimationController::UpdateAnimationManager afin de diriger l’animation manager pour mettre à jour les valeurs de toutes les variables de l’animation.

##  <a name="enableprioritycomparisonhandler"></a>  CAnimationController::EnablePriorityComparisonHandler

Définit ou libère le Gestionnaire de comparaison de priorité à appeler pour déterminer si un storyboard planifié peut être annulé, conclu, supprimé ou compressé.

```
virtual BOOL EnablePriorityComparisonHandler(DWORD dwHandlerType);
```

### <a name="parameters"></a>Paramètres

*dwHandlerType*<br/>
Une combinaison d’indicateurs UI_ANIMATION_PHT_ (consultez Remarques), qui spécifie les gestionnaires de définir ou de mise en production.

### <a name="return-value"></a>Valeur de retour

TRUE si le gestionnaire a été correctement défini ou publié.

### <a name="remarks"></a>Notes

Lorsqu’un gestionnaire est ensemble (activé) Windows Animation appelle les méthodes virtuelles suivantes dwHandlerType : OnHasPriorityCancel, OnHasPriorityConclude, OnHasPriorityTrim, OnHasPriorityCompress. dwHandler peut être une combinaison des indicateurs suivants : UI_ANIMATION_PHT_NONE - libère tous les gestionnaires UI_ANIMATION_PHT_CANCEL - définit Annuler Gestionnaire comparaison UI_ANIMATION_PHT_CONCLUDE - définir Conclude Gestionnaire comparaison UI_ANIMATION_PHT_COMPRESS - définir le Gestionnaire de comparaison Compress UI_ANIMATION_PHT_TRIM - définir Supprimer le Gestionnaire de comparaison UI_ANIMATION_PHT_CANCEL_REMOVE défini - supprimer annuler comparaison Gestionnaire UI_ANIMATION_PHT_CONCLUDE_REMOVE - remove comparaison Conclude UI_ANIMATION_PHT_COMPRESS_REMOVE - supprimer le Gestionnaire de comparaison Compress UI_ANIMATION_PHT _TRIM_REMOVE - supprimer le Gestionnaire de comparaison Trim

##  <a name="enablestoryboardeventhandler"></a>  CAnimationController::EnableStoryboardEventHandler

Définit ou libère un gestionnaire d’événements de statut et de mise à jour de table de montage séquentiel.

```
virtual BOOL EnableStoryboardEventHandler(
    UINT32 nGroupID,
    BOOL bEnable = TRUE);
```

### <a name="parameters"></a>Paramètres

*nGroupID*<br/>
Spécifie l’ID de groupe.

*bEnable*<br/>
Spécifie s’il faut définir ou de libérer un gestionnaire.

### <a name="return-value"></a>Valeur de retour

TRUE si le gestionnaire a été correctement défini ou libéré ; FALSE si le groupe d’animation spécifiée se trouve désormais ou animation pour le groupe spécifié n’a pas été initiée et son storyboard interne est NULL.

### <a name="remarks"></a>Notes

Lorsqu’un gestionnaire est défini (activé) API d’Animation Windows appelle les méthodes virtuelles OnStoryboardStatusChanges et OnStoryboardUpdated. Un gestionnaire doit être défini après que CAnimationController::Animate a été appelé pour le groupe d’animation spécifiée, car elle crée l’objet IUIAnimationStoryboard encapsulé.

##  <a name="findanimationgroup"></a>  CAnimationController::FindAnimationGroup

Recherche un groupe d’animation par son ID de groupe.

```
CAnimationGroup* FindAnimationGroup(UINT32 nGroupID);
CAnimationGroup* FindAnimationGroup(IUIAnimationStoryboard* pStoryboard);
```

### <a name="parameters"></a>Paramètres

*nGroupID*<br/>
Spécifie un GroupID.

*pStoryboard*<br/>
Pointeur vers une table de montage séquentiel.

### <a name="return-value"></a>Valeur de retour

Pointeur vers le groupe d’animation ou NULL si le groupe avec l’ID spécifié est introuvable.

### <a name="remarks"></a>Notes

Utilisez cette méthode pour rechercher un groupe d’animation lors de l’exécution. Un groupe est créé et ajouté à la liste interne des groupes d’animation lorsqu’un premier objet d’animation avec un GroupID particulier est ajouté au contrôleur de l’animation.

##  <a name="findanimationobject"></a>  CAnimationController::FindAnimationObject

Recherche l’objet d’animation contenant une variable d’animation spécifiée.

```
BOOL FindAnimationObject(
    IUIAnimationVariable* pVariable,
    CAnimationBaseObject** ppObject,
    CAnimationGroup** ppGroup);
```

### <a name="parameters"></a>Paramètres

*pVariable*<br/>
Pointeur vers la variable de l’animation.

*ppObject*<br/>
Sortie. Contient un pointeur vers l’objet d’animation ou NULL.

*ppGroup*<br/>
Sortie. Contient un pointeur vers le groupe d’animation qui renferme l’objet d’animation, ou NULL.

### <a name="return-value"></a>Valeur de retour

TRUE si l’objet a été trouvé ; Sinon, FALSE.

### <a name="remarks"></a>Notes

Appelée à partir de gestionnaires d’événements lorsqu’il est nécessaire de trouver un objet d’animation à partir de la variable de l’animation entrant.

##  <a name="g_keyframestoryboardstart"></a>  CAnimationController::gkeyframeStoryboardStart

Une image clé qui représente le début de la table de montage séquentiel.

```
static CBaseKeyFrame gkeyframeStoryboardStart;
```

##  <a name="getkeyframestoryboardstart"></a>  CAnimationController::GetKeyframeStoryboardStart

Retourne une image clé qui identifie le début de la table de montage séquentiel.

```
static CBaseKeyFrame* GetKeyframeStoryboardStart();
```

### <a name="return-value"></a>Valeur de retour

Pointeur vers l’image clé de base, qui identifie le début de la table de montage séquentiel.

### <a name="remarks"></a>Notes

Obtenir cette image clé pour d’autres images clés ou les transitions de base sur le moment dans l’heure de début d’une table de montage séquentiel.

##  <a name="getuianimationmanager"></a>  CAnimationController::GetUIAnimationManager

Fournit l’accès à l’objet IUIAnimationManager encapsulé.

```
IUIAnimationManager* GetUIAnimationManager();
```

### <a name="return-value"></a>Valeur de retour

Pointeur vers l’interface UIAnimationManager ou NULL, si l’échec de la création du Gestionnaire d’animations.

### <a name="remarks"></a>Notes

Si le système d’exploitation actuel ne prend pas en charge les API d’Animation de Windows, cette méthode retourne la valeur NULL, et après que tous les appels successifs sur CAnimationController::IsValid renvoient la valeur FALSE. Vous devrez peut-être accéder à IUIAnimationManager pour appeler ses méthodes d’interface, qui ne sont pas encapsulées par le contrôleur de l’animation.

##  <a name="getuianimationtimer"></a>  CAnimationController::GetUIAnimationTimer

Fournit l’accès à l’objet IUIAnimationTimer encapsulé.

```
IUIAnimationTimer* GetUIAnimationTimer();
```

### <a name="return-value"></a>Valeur de retour

Pointeur vers l’interface IUIAnimationTimer ou NULL, si l’échec de la création de minuterie d’animation.

### <a name="remarks"></a>Notes

Si le système d’exploitation actuel ne prend pas en charge les API d’Animation de Windows, cette méthode retourne la valeur NULL, et après que tous les appels successifs sur CAnimationController::IsValid renvoient la valeur FALSE.

##  <a name="getuitransitionfactory"></a>  CAnimationController::GetUITransitionFactory

Un pointeur vers l’interface IUIAnimationTransitionFactory ou NULL si l’échec de la création de la bibliothèque de transition.

```
IUIAnimationTransitionFactory* GetUITransitionFactory();
```

### <a name="return-value"></a>Valeur de retour

Pointeur vers IUIAnimationTransitionFactory ou NULL, si l’échec de la création de fabrique de transition.

### <a name="remarks"></a>Notes

Si le système d’exploitation actuel ne prend pas en charge les API d’Animation de Windows, cette méthode retourne la valeur NULL, et après que tous les appels successifs sur CAnimationController::IsValid renvoient la valeur FALSE.

##  <a name="getuitransitionlibrary"></a>  CAnimationController::GetUITransitionLibrary

Fournit l’accès à l’objet IUIAnimationTransitionLibrary encapsulé.

```
IUIAnimationTransitionLibrary* GetUITransitionLibrary();
```

### <a name="return-value"></a>Valeur de retour

Pointeur vers l’interface IUIAnimationTransitionLibrary ou NULL, si l’échec de la création de la bibliothèque de transition.

### <a name="remarks"></a>Notes

Si le système d’exploitation actuel ne prend pas en charge les API d’Animation de Windows, cette méthode retourne la valeur NULL, et après que tous les appels successifs sur CAnimationController::IsValid renvoient la valeur FALSE.

##  <a name="isanimationinprogress"></a>  CAnimationController::IsAnimationInProgress

Indique si au moins un groupe joue l’animation.

```
virtual BOOL IsAnimationInProgress();
```

### <a name="return-value"></a>Valeur de retour

TRUE s’il existe une animation en cours pour ce contrôleur de l’animation. Sinon, FALSE.

### <a name="remarks"></a>Notes

Vérifie l’état du Gestionnaire d’animations et retourne la valeur TRUE si l’état est UI_ANIMATION_MANAGER_BUSY.

##  <a name="isvalid"></a>  CAnimationController::IsValid

Indique si le contrôleur de l’animation est valide.

```
BOOL IsValid() const;
```

### <a name="return-value"></a>Valeur de retour

TRUE si le contrôleur de l’animation est valide ; Sinon, FALSE.

### <a name="remarks"></a>Notes

Cette méthode renvoie la valeur FALSE uniquement si l’API Windows Animation n’est pas prise en charge du système d’exploitation et de la création du Gestionnaire d’animations a échoué, car il n’est pas inscrit. Vous devez appeler GetUIAnimationManager au moins une fois après l’initialisation des bibliothèques COM pour définir cet indicateur.

##  <a name="m_bisvalid"></a>  CAnimationController::m_bIsValid

Spécifie si un contrôleur de l’animation est valide ou non. Ce membre est défini sur FALSE si le système d’exploitation actuel ne prend pas en charge les API d’Animation de Windows.

```
BOOL m_bIsValid;
```

##  <a name="m_lstanimationgroups"></a>  CAnimationController::m_lstAnimationGroups

Une liste des groupes d’animation qui appartiennent à ce contrôleur de l’animation.

```
CList<CAnimationGroup*, CAnimationGroup*> m_lstAnimationGroups;
```

##  <a name="m_panimationmanager"></a>  CAnimationController::m_pAnimationManager

Stocke un pointeur vers l’objet COM du Gestionnaire d’animations.

```
ATL::CComPtr<IUIAnimationManager> m_pAnimationManager;
```

##  <a name="m_panimationtimer"></a>  CAnimationController::m_pAnimationTimer

Stocke un pointeur vers l’objet COM de minuterie d’Animation.

```
ATL::CComPtr<IUIAnimationTimer> m_pAnimationTimer;
```

##  <a name="m_prelatedwnd"></a>  CAnimationController::m_pRelatedWnd

Pointeur vers un objet CWnd connexe, qui peut être redessiné automatiquement lorsque l’état du Gestionnaire d’animations a changé, ou publier un événement mise à jour s’est produite. Peut être NULL.

```
CWnd* m_pRelatedWnd;
```

##  <a name="m_ptransitionfactory"></a>  CAnimationController::m_pTransitionFactory

Stocke un pointeur vers l’objet COM de fabrique de Transition.

```
ATL::CComPtr<IUIAnimationTransitionFactory> m_pTransitionFactory;
```

##  <a name="m_ptransitionlibrary"></a>  CAnimationController::m_pTransitionLibrary

Stocke un pointeur vers l’objet COM de bibliothèque de Transition.

```
ATL::CComPtr<IUIAnimationTransitionLibrary> m_pTransitionLibrary;
```

##  <a name="onafterschedule"></a>  CAnimationController::OnAfterSchedule

Appelé par l’infrastructure lorsqu’une animation pour le groupe spécifié a simplement été planifiée.

```
virtual void OnAfterSchedule(CAnimationGroup* pGroup);
```

### <a name="parameters"></a>Paramètres

*pGroup*<br/>
Pointeur vers un groupe d’animation qui a été planifié.

### <a name="remarks"></a>Notes

L’implémentation par défaut supprime les images clés du groupe spécifié et passe à partir de variables d’animation qui appartiennent au groupe spécifié. Peut être substituée dans une classe dérivée pour prendre des mesures supplémentaires sur la planification de l’animation.

##  <a name="onanimationintegervaluechanged"></a>  CAnimationController::OnAnimationIntegerValueChanged

Appelé par l’infrastructure lors de la valeur entière de la variable de l’animation a changé.

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
Un pointeur vers un groupe d’animation qui contient un objet d’animation dont la valeur a changé.

*pObject*<br/>
Pointeur vers un objet d’animation qui contient une variable de l’animation dont la valeur a changé.

*variable*<br/>
Pointeur vers une variable de l’animation.

*newValue*<br/>
Spécifie la nouvelle valeur.

*prevValue*<br/>
Spécifie la valeur précédente.

### <a name="remarks"></a>Notes

Cette méthode est appelée si vous activez les événements des variables d’animation avec EnableIntegerValueChangedEvent appelé pour une variable de l’animation spécifique ou d’un objet d’animation. Elle peut être substituée dans une classe dérivée pour prendre des mesures propres à l'application.

##  <a name="onanimationmanagerstatuschanged"></a>  CAnimationController::OnAnimationManagerStatusChanged

Appelé par l’infrastructure en réponse à un événement StatusChanged du Gestionnaire d’animations.

```
virtual void OnAnimationManagerStatusChanged(
    UI_ANIMATION_MANAGER_STATUS newStatus,
    UI_ANIMATION_MANAGER_STATUS previousStatus);
```

### <a name="parameters"></a>Paramètres

*newStatus*<br/>
Nouvel état de gestionnaire d’animation.

*previousStatus*<br/>
État du gestionnaire animation précédente.

### <a name="remarks"></a>Notes

Cette méthode est appelée si vous activez les événements du Gestionnaire de l’animation avec EnableAnimationManagerEvent. Elle peut être substituée dans une classe dérivée pour prendre des mesures propres à l'application. L’implémentation par défaut met à jour une fenêtre associée s’il a été défini avec SetRelatedWnd.

##  <a name="onanimationtimerpostupdate"></a>  CAnimationController::OnAnimationTimerPostUpdate

Appelé par le framework après qu’une mise à jour de l’animation est terminée.

```
virtual void OnAnimationTimerPostUpdate();
```

### <a name="remarks"></a>Notes

Cette méthode est appelée si vous activez les gestionnaires d’événements de minuterie avec EnableAnimationTimerEventHandler. Elle peut être substituée dans une classe dérivée pour prendre des mesures propres à l'application.

##  <a name="onanimationtimerpreupdate"></a>  CAnimationController::OnAnimationTimerPreUpdate

Appelé par l’infrastructure avant le début d’une mise à jour de l’animation.

```
virtual void OnAnimationTimerPreUpdate();
```

### <a name="remarks"></a>Notes

Cette méthode est appelée si vous activez les gestionnaires d’événements de minuterie avec EnableAnimationTimerEventHandler. Elle peut être substituée dans une classe dérivée pour prendre des mesures propres à l'application.

##  <a name="onanimationtimerrenderingtooslow"></a>  CAnimationController::OnAnimationTimerRenderingTooSlow

Appelé par l’infrastructure lorsque la fréquence d’images de rendu pour une animation tombe en dessous d’une fréquence d’images souhaitable minimale.

```
virtual void OnAnimationTimerRenderingTooSlow(UINT32 fps);
```

### <a name="parameters"></a>Paramètres

*fps*<br/>
La fréquence d’images actuelle dans les images par seconde.

### <a name="remarks"></a>Notes

Cette méthode est appelée si vous activez les gestionnaires d’événements de minuterie avec EnableAnimationTimerEventHandler. Elle peut être substituée dans une classe dérivée pour prendre des mesures propres à l'application. La fréquence d’images souhaitable minimale est spécifiée en appelant IUIAnimationTimer::SetFrameRateThreshold.

##  <a name="onanimationvaluechanged"></a>  CAnimationController::OnAnimationValueChanged

Appelé par l’infrastructure lors de la valeur de variable de l’animation a changé.

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
Un pointeur vers un groupe d’animation qui contient un objet d’animation dont la valeur a changé.

*pObject*<br/>
Pointeur vers un objet d’animation qui contient une variable de l’animation dont la valeur a changé.

*variable*<br/>
Pointeur vers une variable de l’animation.

*newValue*<br/>
Spécifie la nouvelle valeur.

*prevValue*<br/>
Spécifie la valeur précédente.

### <a name="remarks"></a>Notes

Cette méthode est appelée si vous activez les événements des variables d’animation avec EnableValueChangedEvent appelé pour une variable de l’animation spécifique ou d’un objet d’animation. Elle peut être substituée dans une classe dérivée pour prendre des mesures propres à l'application.

##  <a name="onbeforeanimationstart"></a>  CAnimationController::OnBeforeAnimationStart

Appelé par l’infrastructure appropriée avant de l’animation est planifiée.

```
virtual void OnBeforeAnimationStart(CAnimationGroup* pGroup);
```

### <a name="parameters"></a>Paramètres

*pGroup*<br/>
Pointeur vers un groupe d’animation dont l’animation est prêt à démarrer.

### <a name="remarks"></a>Notes

Cet appel est routé vers CWnd connexe et peut être substitué dans une classe dérivée pour effectuer des actions supplémentaires avant le démarrage de l’animation pour le groupe spécifié.

##  <a name="onhasprioritycancel"></a>  CAnimationController::OnHasPriorityCancel

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

### <a name="return-value"></a>Valeur de retour

Doit retourner TRUE si le plan conceptuel détenu par pGroupNew est prioritaire. Doit retourner FALSE si le plan conceptuel détenu par pGroupScheduled est prioritaire.

### <a name="remarks"></a>Notes

Cette méthode est appelée si vous activez les événements de comparaison de priorité à l'aide de CAnimationController::EnablePriorityComparisonHandler et que vous spécifiez UI_ANIMATION_PHT_CANCEL. Elle peut être substituée dans une classe dérivée pour prendre des mesures propres à l'application. Documentation des API d’Animation Windows en lecture pour plus d’informations sur [gestion des conflits](/windows/desktop/api/uianimation/nf-uianimation-iuianimationprioritycomparison-haspriority).

##  <a name="onhasprioritycompress"></a>  CAnimationController::OnHasPriorityCompress

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

### <a name="return-value"></a>Valeur de retour

Doit retourner TRUE si le plan conceptuel détenu par pGroupNew est prioritaire. Doit retourner FALSE si le plan conceptuel détenu par pGroupScheduled est prioritaire.

### <a name="remarks"></a>Notes

Cette méthode est appelée si vous activez les événements de comparaison de priorité à l'aide de CAnimationController::EnablePriorityComparisonHandler et que vous spécifiez UI_ANIMATION_PHT_COMPRESS. Elle peut être substituée dans une classe dérivée pour prendre des mesures propres à l'application. Documentation des API d’Animation Windows en lecture pour plus d’informations sur [gestion des conflits](/windows/desktop/api/uianimation/nf-uianimation-iuianimationprioritycomparison-haspriority).

##  <a name="onhaspriorityconclude"></a>  CAnimationController::OnHasPriorityConclude

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

### <a name="return-value"></a>Valeur de retour

Doit retourner TRUE si le plan conceptuel détenu par pGroupNew est prioritaire. Doit retourner FALSE si le plan conceptuel détenu par pGroupScheduled est prioritaire.

### <a name="remarks"></a>Notes

Cette méthode est appelée si vous activez les événements de comparaison de priorité à l'aide de CAnimationController::EnablePriorityComparisonHandler et que vous spécifiez UI_ANIMATION_PHT_CONCLUDE. Elle peut être substituée dans une classe dérivée pour prendre des mesures propres à l'application. Documentation des API d’Animation Windows en lecture pour plus d’informations sur [gestion des conflits](/windows/desktop/api/uianimation/nf-uianimation-iuianimationprioritycomparison-haspriority).

##  <a name="onhasprioritytrim"></a>  CAnimationController::OnHasPriorityTrim

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

### <a name="return-value"></a>Valeur de retour

Doit retourner TRUE si le plan conceptuel détenu par pGroupNew est prioritaire. Doit retourner FALSE si le plan conceptuel détenu par pGroupScheduled est prioritaire.

### <a name="remarks"></a>Notes

Cette méthode est appelée si vous activez les événements de comparaison de priorité à l'aide de CAnimationController::EnablePriorityComparisonHandler et que vous spécifiez UI_ANIMATION_PHT_TRIM. Elle peut être substituée dans une classe dérivée pour prendre des mesures propres à l'application. Documentation des API d’Animation Windows en lecture pour plus d’informations sur [gestion des conflits](/windows/desktop/api/uianimation/nf-uianimation-iuianimationprioritycomparison-haspriority).

##  <a name="onstoryboardstatuschanged"></a>  CAnimationController::OnStoryboardStatusChanged

Appelé par l’infrastructure lorsque l’état de la table de montage séquentiel a changé.

```
virtual void OnStoryboardStatusChanged(
    CAnimationGroup* pGroup,
    UI_ANIMATION_STORYBOARD_STATUS newStatus,
    UI_ANIMATION_STORYBOARD_STATUS previousStatus);
```

### <a name="parameters"></a>Paramètres

*pGroup*<br/>
Un pointeur vers un groupe d’animation qui possède le storyboard dont l’état a changé.

*newStatus*<br/>
Spécifie le nouvel état.

*previousStatus*<br/>
Spécifie l’état précédent.

### <a name="remarks"></a>Notes

Cette méthode est appelée si vous activez les événements de table de montage séquentiel à l’aide de CAnimationController::EnableStoryboardEventHandler. Elle peut être substituée dans une classe dérivée pour prendre des mesures propres à l'application.

##  <a name="onstoryboardupdated"></a>  CAnimationController::OnStoryboardUpdated

Appelé par l’infrastructure lors de la table de montage séquentiel a été mis à jour.

```
virtual void OnStoryboardUpdated(CAnimationGroup* pGroup);
```

### <a name="parameters"></a>Paramètres

*pGroup*<br/>
Pointeur vers un groupe qui possède le storyboard.

### <a name="remarks"></a>Notes

Cette méthode est appelée si vous activez les événements de table de montage séquentiel à l’aide de CAnimationController::EnableStoryboardEventHandler. Elle peut être substituée dans une classe dérivée pour prendre des mesures propres à l'application.

##  <a name="removeallanimationgroups"></a>  CAnimationController::RemoveAllAnimationGroups

Supprime tous les groupes d’animation de contrôleur de l’animation.

```
void RemoveAllAnimationGroups();
```

### <a name="remarks"></a>Notes

Tous les groupes sera supprimé, son pointeur, si stocké au niveau de l’application, doit être invalidé. Si CAnimationGroup::m_bAutodestroyAnimationObjects pour un groupe en cours de suppression est TRUE, tous les objets d’animation qui appartiennent à ce groupe seront supprimés ; Sinon, leurs références au contrôleur de l’animation parent la valeur NULL et ils peuvent être ajoutés à un autre contrôleur.

##  <a name="removeanimationgroup"></a>  CAnimationController::RemoveAnimationGroup

Supprime un groupe d’animation avec l’ID spécifié à partir du contrôleur de l’animation.

```
void RemoveAnimationGroup(UINT32 nGroupID);
```

### <a name="parameters"></a>Paramètres

*nGroupID*<br/>
Spécifie l’ID de groupe d’animation.

### <a name="remarks"></a>Notes

Cette méthode supprime un groupe d’animation de la liste interne des groupes et le supprime, par conséquent, si vous avez stocké un pointeur vers ce groupe d’animation, elle doit être invalidée. Si CAnimationGroup::m_bAutodestroyAnimationObjects a la valeur TRUE, tous les objets d’animation qui appartiennent à ce groupe seront supprimés ; Sinon, leurs références au contrôleur de l’animation parent la valeur NULL et ils peuvent être ajoutés à un autre contrôleur.

##  <a name="removeanimationobject"></a>  CAnimationController::RemoveAnimationObject

Supprimer un objet d’animation de contrôleur de l’animation.

```
void RemoveAnimationObject(
    CAnimationBaseObject* pObject,
    BOOL bNoDelete = FALSE);
```

### <a name="parameters"></a>Paramètres

*pObject*<br/>
Pointeur vers un objet d’animation.

*bNoDelete*<br/>
Si ce paramètre a la valeur TRUE l’objet ne sera pas supprimé à supprimer.

### <a name="remarks"></a>Notes

Supprime un objet d’animation de contrôleur de l’animation et le groupe d’animation. Appelez cette fonction si un objet particulier ne doit pas être animé plus, ou si vous avez besoin de déplacer l’objet vers un autre contrôleur de l’animation. Dans le dernier cas bNoDelete doit être TRUE.

##  <a name="removetransitions"></a>  CAnimationController::RemoveTransitions

Supprime les transitions des objets d’animation qui appartiennent au groupe spécifié.

```
void RemoveTransitions(UINT32 nGroupID);
```

### <a name="parameters"></a>Paramètres

*nGroupID*<br/>
Spécifie l’ID de groupe.

### <a name="remarks"></a>Notes

Le groupe effectue une itération via ses objets d’animation et appelle ClearTransitions (false) pour chaque objet d’animation. Cette méthode est appelée par l’infrastructure une fois l’animation a été planifiée.

##  <a name="schedulegroup"></a>  CAnimationController::ScheduleGroup

Planifie une animation.

```
BOOL ScheduleGroup(
    UINT32 nGroupID,
    UI_ANIMATION_SECONDS time = 0.0);
```

### <a name="parameters"></a>Paramètres

*nGroupID*<br/>
Spécifie l’ID de groupe pour planifier l’animation.

*time*<br/>
Spécifie le calendrier.

### <a name="return-value"></a>Valeur de retour

TRUE si l’animation a été planifiée avec succès. FALSE si la table de montage séquentiel n’a pas été créé, ou autre erreur se produit.

### <a name="remarks"></a>Notes

Vous devez appeler AnimateGroup avec bScheduleNow paramètre défini sur FALSE ScheduleGroup préalable. Vous pouvez spécifier l’heure de l’animation souhaitée obtenue à partir de IUIAnimationTimer::GetTime. Si le paramètre d’heure est 0.0, l’animation est planifiée pour l’heure actuelle.

##  <a name="setrelatedwnd"></a>  CAnimationController::SetRelatedWnd

Établit une relation entre le contrôleur de l’animation et une fenêtre.

```
void SetRelatedWnd(CWnd* pWnd);
```

### <a name="parameters"></a>Paramètres

*pWnd*<br/>
Pointeur vers l’objet de fenêtre à définir.

### <a name="remarks"></a>Notes

Si un objet CWnd connexe est défini, le contrôleur de l’animation peut automatiquement mettre à jour (envoyer le message WM_PAINT) lorsque l’état du Gestionnaire d’animations a changé ou événement de mise à jour post du minuteur s’est produite.

##  <a name="updateanimationmanager"></a>  CAnimationController::UpdateAnimationManager

Dirige le Gestionnaire d’animations pour mettre à jour les valeurs de toutes les variables de l’animation.

```
virtual void UpdateAnimationManager();
```

### <a name="remarks"></a>Notes

Valeurs interpolées à appeler que cette méthode avance le Gestionnaire d’animations à l’heure actuelle, la modification des États des animations en fonction des besoins et la mise à jour des variables d’animation appropriés. Cette méthode appelle en interne IUIAnimationTimer::GetTime(timeNow) et IUIAnimationManager::Update (timeNow). Substituez cette méthode dans une classe dérivée pour personnaliser ce comportement.

## <a name="see-also"></a>Voir aussi

[Classes](../../mfc/reference/mfc-classes.md)
