---
title: CAnimationController, classe | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b91acd3537477e4213ea87dec77a97822b9e3d98
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/26/2018
ms.locfileid: "36955113"
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
|[CAnimationController :: ~ CAnimationController](#canimationcontroller__~canimationcontroller)|Destructeur. Appelé lorsque l’objet contrôleur de l’animation est détruit.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[CAnimationController::AddAnimationObject](#addanimationobject)|Ajoute un objet d’animation à un groupe auquel appartient le contrôleur de l’animation.|  
|[CAnimationController::AddKeyframeToGroup](#addkeyframetogroup)|Ajoute une image clé au groupe.|  
|[CAnimationController::AnimateGroup](#animategroup)|Prépare un groupe pour exécuter l’animation et le planifie si vous le souhaitez.|  
|[CAnimationController::CleanUpGroup](#cleanupgroup)|Surchargé. Appelé par l’infrastructure pour nettoyer le groupe lors de l’animation a été planifiée.|  
|[CAnimationController::CreateKeyframe de préférence](#createkeyframe)|Surchargé. Crée une image clé qui dépend de la transition et l’ajoute au groupe spécifié.|  
|[CAnimationController::EnableAnimationManagerEvent](#enableanimationmanagerevent)|Définit ou libère un gestionnaire à appeler lorsque l’état du Gestionnaire d’animations.|  
|[CAnimationController::EnableAnimationTimerEventHandler](#enableanimationtimereventhandler)|Définit ou libère un gestionnaire pour les événements de minutage et Gestionnaire de synchronisation des mises à jour.|  
|[CAnimationController::EnablePriorityComparisonHandler](#enableprioritycomparisonhandler)|Définit ou libère le Gestionnaire de comparaison de priorité à appeler pour déterminer si un storyboard planifié peut être annulé, conclu, supprimé ou compressé.|  
|[CAnimationController::EnableStoryboardEventHandler](#enablestoryboardeventhandler)|Définit ou libère un gestionnaire d’événements d’état et de mise à jour de plan conceptuel.|  
|[CAnimationController::FindAnimationGroup](#findanimationgroup)|Surchargé. Recherche un groupe d’animation à sa table de montage séquentiel.|  
|[CAnimationController::FindAnimationObject](#findanimationobject)|Recherche l’objet d’animation contenant une variable d’animation spécifiée.|  
|[CAnimationController::GetKeyframeStoryboardStart](#getkeyframestoryboardstart)|Retourne une image clé qui identifie le début de la table de montage séquentiel.|  
|[CAnimationController::GetUIAnimationManager](#getuianimationmanager)|Fournit l’accès à l’objet IUIAnimationManager encapsulé.|  
|[CAnimationController::GetUIAnimationTimer](#getuianimationtimer)|Fournit l’accès à l’objet IUIAnimationTimer encapsulé.|  
|[CAnimationController::GetUITransitionFactory](#getuitransitionfactory)|Pointeur vers l’interface IUIAnimationTransitionFactory ou NULL si l’échec de la création de la bibliothèque de transitions.|  
|[CAnimationController::GetUITransitionLibrary](#getuitransitionlibrary)|Fournit l’accès à l’objet IUIAnimationTransitionLibrary encapsulé.|  
|[CAnimationController::IsAnimationInProgress](#isanimationinprogress)|Indique si au moins un groupe joue l’animation.|  
|[CAnimationController::IsValid](#isvalid)|Indique si le contrôleur de l’animation est valide.|  
|[CAnimationController::OnAnimationIntegerValueChanged](#onanimationintegervaluechanged)|Appelé par l’infrastructure lors de la valeur entière de la variable de l’animation a changé.|  
|[CAnimationController::OnAnimationManagerStatusChanged](#onanimationmanagerstatuschanged)|Appelé par l’infrastructure en réponse à un événement StatusChanged du Gestionnaire d’animations.|  
|[CAnimationController::OnAnimationTimerPostUpdate](#onanimationtimerpostupdate)|Appelé par le framework après qu’une mise à jour de l’animation terminée.|  
|[CAnimationController::OnAnimationTimerPreUpdate](#onanimationtimerpreupdate)|Appelé par l’infrastructure avant le début d’une mise à jour de l’animation.|  
|[CAnimationController::OnAnimationTimerRenderingTooSlow](#onanimationtimerrenderingtooslow)|Appelé par le framework lorsque la fréquence d’images de rendu d’une animation est inférieur à une fréquence minimale souhaitable.|  
|[CAnimationController::OnAnimationValueChanged](#onanimationvaluechanged)|Appelé par l’infrastructure lors de la valeur de la variable de l’animation a changé.|  
|[CAnimationController::OnBeforeAnimationStart](#onbeforeanimationstart)|Appelée par l’infrastructure de droite avant que l’animation est planifiée.|  
|[CAnimationController::OnHasPriorityCancel](#onhasprioritycancel)|Appelé par l'infrastructure pour résoudre les conflits de planification.|  
|[CAnimationController::OnHasPriorityCompress](#onhasprioritycompress)|Appelé par l'infrastructure pour résoudre les conflits de planification.|  
|[CAnimationController::OnHasPriorityConclude](#onhaspriorityconclude)|Appelé par l'infrastructure pour résoudre les conflits de planification.|  
|[CAnimationController::OnHasPriorityTrim](#onhasprioritytrim)|Appelé par l'infrastructure pour résoudre les conflits de planification.|  
|[CAnimationController::OnStoryboardStatusChanged](#onstoryboardstatuschanged)|Appelé par l’infrastructure lors de l’état de la table de montage séquentiel a changé.|  
|[CAnimationController::OnStoryboardUpdated](#onstoryboardupdated)|Appelé par l’infrastructure lors de la table de montage séquentiel a été mis à jour.|  
|[CAnimationController::RemoveAllAnimationGroups](#removeallanimationgroups)|Supprime tous les groupes d’animation à partir du contrôleur de l’animation.|  
|[CAnimationController::RemoveAnimationGroup](#removeanimationgroup)|Supprime un groupe d’animation avec l’ID spécifié à partir du contrôleur de l’animation.|  
|[CAnimationController::RemoveAnimationObject](#removeanimationobject)|Supprimer un objet d’animation à partir du contrôleur de l’animation.|  
|[CAnimationController::RemoveTransitions](#removetransitions)|Supprime les transitions des objets d’animation qui appartiennent au groupe spécifié.|  
|[CAnimationController::ScheduleGroup](#schedulegroup)|Planifie une animation.|  
|[CAnimationController::SetRelatedWnd](#setrelatedwnd)|Établit une relation entre le contrôleur de l’animation et une fenêtre.|  
|[CAnimationController::UpdateAnimationManager](#updateanimationmanager)|Dirige le Gestionnaire d’animation pour mettre à jour les valeurs de toutes les variables de l’animation.|  
  
### <a name="protected-methods"></a>Méthodes protégées  
  
|Nom|Description|  
|----------|-----------------|  
|[CAnimationController::CleanUpGroup](#cleanupgroup)|Surchargé. Un programme d’assistance qui nettoie le groupe.|  
|[CAnimationController::OnAfterSchedule](#onafterschedule)|Appelé par l’infrastructure lorsqu’une animation pour le groupe spécifié vient d’être planifiée.|  
  
### <a name="protected-data-members"></a>Membres de données protégés  
  
|Name|Description|  
|----------|-----------------|  
|[CAnimationController::gkeyframeStoryboardStart](#g_keyframestoryboardstart)|Une image clé qui représente le début de la table de montage séquentiel.|  
|[CAnimationController::m_bIsValid](#m_bisvalid)|Spécifie si un contrôleur de l’animation est valid ou non. Ce membre a la valeur FALSE si le système d’exploitation actuel ne prend pas en charge les API d’Animation Windows.|  
|[CAnimationController::m_lstAnimationGroups](#m_lstanimationgroups)|Une liste des groupes d’animation qui appartiennent à ce contrôleur de l’animation.|  
|[CAnimationController::m_pAnimationManager](#m_panimationmanager)|Stocke un pointeur vers l’objet COM du Gestionnaire d’animations.|  
|[CAnimationController::m_pAnimationTimer](#m_panimationtimer)|Stocke un pointeur vers l’objet COM du minuteur de l’Animation.|  
|[CAnimationController::m_pRelatedWnd](#m_prelatedwnd)|Pointeur vers un objet CWnd connexe qui peut être redessiné automatiquement lorsque l’état du Gestionnaire d’animations a changé ou l’événement de mise à jour de publication s’est produite. Peut être NULL.|  
|[CAnimationController::m_pTransitionFactory](#m_ptransitionfactory)|Stocke un pointeur vers l’objet COM de fabrique de Transition.|  
|[CAnimationController::m_pTransitionLibrary](#m_ptransitionlibrary)|Stocke un pointeur vers l’objet COM de bibliothèque de Transition.|  
  
## <a name="remarks"></a>Notes  
 La classe CAnimationController est la classe clée qui gère les animations. Vous pouvez créer une ou plusieurs instances de contrôleur de l’animation dans une application et, éventuellement, se connecter à une instance de contrôleur de l’animation à un objet CWnd à l’aide de CAnimationController::SetRelatedWnd. Cette connexion est nécessaire pour envoyer automatiquement des messages WM_PAINT à la fenêtre associée lorsque l’état du Gestionnaire d’animations a changé ou l’horloge d’animation a été mis à jour. Si vous n’activez pas cette relation, vous devez redessiner une fenêtre qui affiche une animation manuellement. Pour cela, vous pouvez dériver une classe de CAnimationController et remplacer OnAnimationManagerStatusChanged et/ou OnAnimationTimerPostUpdate et invalider une ou plusieurs fenêtres lorsque cela est nécessaire.  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CAnimationController`  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** afxanimationcontroller.h  
  
##  <a name="_dtorcanimationcontroller"></a>  CAnimationController :: ~ CAnimationController  
 Destructeur. Appelé lorsque l’objet contrôleur de l’animation est détruit.  
  
```  
virtual ~CAnimationController(void);
```   
  
##  <a name="addanimationobject"></a>  CAnimationController::AddAnimationObject  
 Ajoute un objet d’animation à un groupe auquel appartient le contrôleur de l’animation.  
  
```  
CAnimationGroup* AddAnimationObject(CAnimationBaseObject* pObject);
```  
  
### <a name="parameters"></a>Paramètres  
 *pObject*  
 Pointeur vers un objet d’animation.  
  
### <a name="return-value"></a>Valeur de retour  
 Un pointeur vers le groupe d’animation existante ou nouvelle où pObject a été ajouté si la fonction réussit ; NULL si pObject a déjà été ajouté à un groupe qui appartient à un autre contrôleur de l’animation.  
  
### <a name="remarks"></a>Notes  
 Appelez cette méthode pour ajouter un objet d’animation pour le contrôleur de l’animation. Un objet sera être ajouté à un groupe en fonction de GroupID l’objet (voir CAnimationBaseObject::SetID). Le contrôleur de l’animation créera un nouveau groupe s’il s’agit du premier objet ajouté avec le GroupID spécifié. Un objet d’animation peut être ajouté à une animation du contrôleur uniquement. Si vous avez besoin ajouter un objet vers un autre contrôleur, appelez d’abord RemoveAnimationObject. Si vous appelez SetID avec un nouveau GroupID pour un objet qui a déjà été ajouté à un groupe, l’objet est supprimée de l’ancien groupe et ajouté à un autre groupe avec l’ID spécifié.  
  
##  <a name="addkeyframetogroup"></a>  CAnimationController::AddKeyframeToGroup  
 Ajoute une image clé au groupe.  
  
```  
BOOL AddKeyframeToGroup(
    UINT32 nGroupID,  
    CBaseKeyFrame* pKeyframe);
```  
  
### <a name="parameters"></a>Paramètres  
 *nGroupID*  
 Spécifie l’ID de groupe.  
  
 *pKeyframe*  
 Pointeur vers une image clé.  
  
### <a name="return-value"></a>Valeur de retour  
 TRUE si la fonction réussit ; Sinon, FALSE.  
  
### <a name="remarks"></a>Notes  
 En général vous n’avez pas besoin d’appeler cette méthode, utilisez CAnimationController::CreateKeyframe de préférence, qui crée et ajoute l’image clé créée à un groupe automatiquement.  
  
##  <a name="animategroup"></a>  CAnimationController::AnimateGroup  
 Prépare un groupe pour exécuter l’animation et le planifie si vous le souhaitez.  
  
```  
BOOL AnimateGroup(
    UINT32 nGroupID,  
    BOOL bScheduleNow = TRUE);
```  
  
### <a name="parameters"></a>Paramètres  
 *nGroupID*  
 Spécifie GroupID.  
  
 *bScheduleNow*  
 Spécifie s’il faut exécuter immédiatement l’animation.  
  
### <a name="return-value"></a>Valeur de retour  
 TRUE si l’animation a été correctement planifiée et s’exécuter.  
  
### <a name="remarks"></a>Notes  
 Cette méthode effectue le travail Création de plan conceptuel, ajout de variables de l’animation, application de transitions et en définissant des images clés. Il est possible de différer la planification si vous affectez la valeur FALSE à bScheduleNow. Dans ce cas, le groupe spécifié contiendra une animation qui a été configurée pour l’animation. À ce stade, vous pouvez configurer les événements pour les variables de table de montage séquentiel et l’animation. Lorsque vous devez réellement exécuter l’appel de l’animation CAnimationController::ScheduleGroup.  
  
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
 *nGroupID*  
 Spécifie GroupID.  
  
 *pGroup*  
 Pointeur vers le groupe d’animation à nettoyer.  
  
### <a name="remarks"></a>Notes  
 Cette méthode supprime toutes les transitions et les images clés du groupe spécifié, car ils ne sont pas pertinentes après qu’une animation a été planifiée.  
  
##  <a name="createkeyframe"></a>  CAnimationController::CreateKeyframe de préférence  
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
 *nGroupID*  
 Spécifie l’ID de groupe pour lequel l’image clé est créée.  
  
 *pTransition*  
 Pointeur vers la transition. L’image clé sera insérée dans le plan conceptuel après cette transition.  
  
 *pKeyframe*  
 Pointeur vers l’image clé de base pour cette image clé.  
  
 *offset*  
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
 *bActivez*  
 Spécifie s’il faut définir ou de libérer un gestionnaire.  
  
### <a name="return-value"></a>Valeur de retour  
 TRUE si le gestionnaire a été correctement défini ou libéré.  
  
### <a name="remarks"></a>Notes  
 Lorsqu’un gestionnaire est défini (activé) Animation Windows appelle OnAnimationManagerStatusChanged lorsque l’état du Gestionnaire d’animations.  
  
##  <a name="enableanimationtimereventhandler"></a>  CAnimationController::EnableAnimationTimerEventHandler  
 Définit ou libère un gestionnaire pour les événements de minutage et Gestionnaire de synchronisation des mises à jour.  
  
```  
virtual BOOL EnableAnimationTimerEventHandler(
    BOOL bEnable = TRUE,  
    UI_ANIMATION_IDLE_BEHAVIOR idleBehavior = UI_ANIMATION_IDLE_BEHAVIOR_DISABLE);
```  
  
### <a name="parameters"></a>Paramètres  
 *bActivez*  
 Spécifie s’il faut définir ou de libérer les gestionnaires.  
  
 *idleBehavior*  
 Spécifie le comportement inactif pour le Gestionnaire de mise à jour du minuteur.  
  
### <a name="return-value"></a>Valeur de retour  
 TRUE si les gestionnaires ont été correctement définis ou libérés ; FALSE si cette méthode est appelée une deuxième fois sans libérer les gestionnaires d’abord, ou si toute autre erreur se produit.  
  
### <a name="remarks"></a>Notes  
 Lorsque les gestionnaires sont définis (activé) appelle l’API Windows Animation OnAnimationTimerPreUpdate, OnAnimationTimerPostUpdate et OnRenderingTooSlow. Vous devez activer les minuteries de l’animation autoriser les animations de mise à jour de l’API Windows Animation. Dans le cas contraire, vous devez appeler CAnimationController::UpdateAnimationManager afin de diriger l’animation manager pour mettre à jour les valeurs de toutes les variables de l’animation.  
  
##  <a name="enableprioritycomparisonhandler"></a>  CAnimationController::EnablePriorityComparisonHandler  
 Définit ou libère le Gestionnaire de comparaison de priorité à appeler pour déterminer si un storyboard planifié peut être annulé, conclu, supprimé ou compressé.  
  
```  
virtual BOOL EnablePriorityComparisonHandler(DWORD dwHandlerType);
```  
  
### <a name="parameters"></a>Paramètres  
 *dwHandlerType*  
 Une combinaison d’indicateurs UI_ANIMATION_PHT_ (voir Remarques), qui spécifie les gestionnaires à définir ou libérer.  
  
### <a name="return-value"></a>Valeur de retour  
 TRUE si le gestionnaire a été correctement défini ou libéré.  
  
### <a name="remarks"></a>Notes  
 Lorsqu’un gestionnaire est défini (activé) Animation Windows appelle les méthodes virtuelles suivantes dwHandlerType : OnHasPriorityCancel, OnHasPriorityConclude, OnHasPriorityTrim, OnHasPriorityCompress. dwHandler peut être une combinaison des indicateurs suivants : UI_ANIMATION_PHT_NONE - libère tous les gestionnaires UI_ANIMATION_PHT_CANCEL - définir annuler le Gestionnaire de comparaison UI_ANIMATION_PHT_CONCLUDE - définir comparaison Conclude UI_ANIMATION_PHT_COMPRESS - assigner Gestionnaire de comparaison Compress UI_ANIMATION_PHT_TRIM - définir le Gestionnaire de comparaison Trim UI_ANIMATION_PHT_CANCEL_REMOVE défini - supprimer le Gestionnaire de comparaison Cancel UI_ANIMATION_PHT_CONCLUDE_REMOVE - supprimer comparaison Conclude UI_ANIMATION_PHT_COMPRESS_ REMOVE - supprime le Gestionnaire de comparaison Compress UI_ANIMATION_PHT_TRIM_REMOVE - Gestionnaire de comparaison Trim supprimer  
  
##  <a name="enablestoryboardeventhandler"></a>  CAnimationController::EnableStoryboardEventHandler  
 Définit ou libère un gestionnaire d’événements d’état et de mise à jour de plan conceptuel.  
  
```  
virtual BOOL EnableStoryboardEventHandler(
    UINT32 nGroupID,  
    BOOL bEnable = TRUE);
```  
  
### <a name="parameters"></a>Paramètres  
 *nGroupID*  
 Spécifie l’ID de groupe.  
  
 *bActivez*  
 Spécifie s’il faut définir ou de libérer un gestionnaire.  
  
### <a name="return-value"></a>Valeur de retour  
 TRUE si le gestionnaire a été correctement défini ou libéré ; FALSE si le groupe d’animation spécifié se trouve désormais ou animation pour le groupe spécifié n’a pas été initialisée et que son storyboard interne est NULL.  
  
### <a name="remarks"></a>Notes  
 Lorsqu’un gestionnaire est défini (activé) API d’Animation Windows appelle les méthodes virtuelles OnStoryboardStatusChanges et OnStoryboardUpdated. Un gestionnaire doit être défini après que CAnimationController::Animate a été appelé pour le groupe d’animation spécifié, parce qu’il crée l’objet IUIAnimationStoryboard encapsulé.  
  
##  <a name="findanimationgroup"></a>  CAnimationController::FindAnimationGroup  
 Recherche d’un groupe d’animation par son ID de groupe.  
  
```  
CAnimationGroup* FindAnimationGroup(UINT32 nGroupID);  
CAnimationGroup* FindAnimationGroup(IUIAnimationStoryboard* pStoryboard);
```  
  
### <a name="parameters"></a>Paramètres  
 *nGroupID*  
 Spécifie un GroupID.  
  
 *pStoryboard*  
 Pointeur vers un plan conceptuel.  
  
### <a name="return-value"></a>Valeur de retour  
 Pointeur vers le groupe d’animation ou NULL si le groupe avec l’ID spécifié est introuvable.  
  
### <a name="remarks"></a>Notes  
 Utilisez cette méthode pour rechercher un groupe d’animation en cours d’exécution. Un groupe est créé et ajouté à la liste interne des groupes d’animation lorsqu’un premier objet d’animation avec un GroupID particulier est ajouté au contrôleur de l’animation.  
  
##  <a name="findanimationobject"></a>  CAnimationController::FindAnimationObject  
 Recherche l’objet d’animation contenant une variable d’animation spécifiée.  
  
```  
BOOL FindAnimationObject(
    IUIAnimationVariable* pVariable,  
    CAnimationBaseObject** ppObject,  
    CAnimationGroup** ppGroup);
```  
  
### <a name="parameters"></a>Paramètres  
 *pVariable*  
 Pointeur vers la variable de l’animation.  
  
 *ppObject*  
 Sortie. Contient un pointeur vers l’objet d’animation ou NULL.  
  
 *ppGroup*  
 Sortie. Contient un pointeur vers le groupe d’animation qui contient l’objet d’animation, ou NULL.  
  
### <a name="return-value"></a>Valeur de retour  
 TRUE si l’objet a été trouvé ; Sinon, FALSE.  
  
### <a name="remarks"></a>Notes  
 Appelée à partir de gestionnaires d’événements lorsqu’est nécessaire pour trouver un objet d’animation à partir de la variable d’animation entrante.  
  
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
 Pointeur vers l’image clé de base, qui identifie le démarrage de l’animation.  
  
### <a name="remarks"></a>Notes  
 Obtenir cette image clé pour les autres images clés ou les transitions de base sur le moment de l’heure de démarrage d’un plan conceptuel.  
  
##  <a name="getuianimationmanager"></a>  CAnimationController::GetUIAnimationManager  
 Fournit l’accès à l’objet IUIAnimationManager encapsulé.  
  
```  
IUIAnimationManager* GetUIAnimationManager();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Pointeur vers l’interface UIAnimationManager ou NULL si l’échec de la création du Gestionnaire d’animations.  
  
### <a name="remarks"></a>Notes  
 Si le système d’exploitation actuel ne prend pas en charge les API Windows Animation, cette méthode retourne la valeur NULL et après que tous les appels successifs sur CAnimationController::IsValid renvoient la valeur FALSE. Vous devrez peut-être accéder à IUIAnimationManager afin d’appeler ses méthodes d’interface qui ne sont pas encapsulées par le contrôleur de l’animation.  
  
##  <a name="getuianimationtimer"></a>  CAnimationController::GetUIAnimationTimer  
 Fournit l’accès à l’objet IUIAnimationTimer encapsulé.  
  
```  
IUIAnimationTimer* GetUIAnimationTimer();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Pointeur vers l’interface IUIAnimationTimer ou NULL si l’échec de la création du minuteur d’animation.  
  
### <a name="remarks"></a>Notes  
 Si le système d’exploitation actuel ne prend pas en charge les API Windows Animation, cette méthode retourne la valeur NULL et après que tous les appels successifs sur CAnimationController::IsValid renvoient la valeur FALSE.  
  
##  <a name="getuitransitionfactory"></a>  CAnimationController::GetUITransitionFactory  
 Pointeur vers l’interface IUIAnimationTransitionFactory ou NULL si l’échec de la création de la bibliothèque de transitions.  
  
```  
IUIAnimationTransitionFactory* GetUITransitionFactory();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Pointeur vers IUIAnimationTransitionFactory ou NULL, si l’échec de la création de la fabrique de transitions.  
  
### <a name="remarks"></a>Notes  
 Si le système d’exploitation actuel ne prend pas en charge les API Windows Animation, cette méthode retourne la valeur NULL et après que tous les appels successifs sur CAnimationController::IsValid renvoient la valeur FALSE.  
  
##  <a name="getuitransitionlibrary"></a>  CAnimationController::GetUITransitionLibrary  
 Fournit l’accès à l’objet IUIAnimationTransitionLibrary encapsulé.  
  
```  
IUIAnimationTransitionLibrary* GetUITransitionLibrary();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Pointeur vers l’interface IUIAnimationTransitionLibrary ou NULL si l’échec de la création de la bibliothèque de transitions.  
  
### <a name="remarks"></a>Notes  
 Si le système d’exploitation actuel ne prend pas en charge les API Windows Animation, cette méthode retourne la valeur NULL et après que tous les appels successifs sur CAnimationController::IsValid renvoient la valeur FALSE.  
  
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
 Spécifie si un contrôleur de l’animation est valid ou non. Ce membre a la valeur FALSE si le système d’exploitation actuel ne prend pas en charge les API d’Animation Windows.  
  
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
 Stocke un pointeur vers l’objet COM du minuteur de l’Animation.  
  
```  
ATL::CComPtr<IUIAnimationTimer> m_pAnimationTimer;  
```  
  
##  <a name="m_prelatedwnd"></a>  CAnimationController::m_pRelatedWnd  
 Pointeur vers un objet CWnd connexe qui peut être redessiné automatiquement lorsque l’état du Gestionnaire d’animations a changé ou l’événement de mise à jour de publication s’est produite. Peut être NULL.  
  
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
 Appelé par l’infrastructure lorsqu’une animation pour le groupe spécifié vient d’être planifiée.  
  
```  
virtual void OnAfterSchedule(CAnimationGroup* pGroup);
```  
  
### <a name="parameters"></a>Paramètres  
 *pGroup*  
 Pointeur vers un groupe d’animation, qui a été planifié.  
  
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
 *pGroup*  
 Un pointeur vers un groupe d’animation qui contient un objet d’animation dont la valeur a changé.  
  
 *pObject*  
 Pointeur vers un objet d’animation qui contient une variable d’animation dont la valeur a changé.  
  
 *Variable*  
 Pointeur vers une variable de l’animation.  
  
 *nouvelle valeur*  
 Spécifie la nouvelle valeur.  
  
 *prevValue*  
 Spécifie la valeur précédente.  
  
### <a name="remarks"></a>Notes  
 Cette méthode est appelée si vous activez les événements des variables d’animation avec EnableIntegerValueChangedEvent appelé pour une variable de l’animation spécifique ou un objet d’animation. Elle peut être substituée dans une classe dérivée pour prendre des mesures propres à l'application.  
  
##  <a name="onanimationmanagerstatuschanged"></a>  CAnimationController::OnAnimationManagerStatusChanged  
 Appelé par l’infrastructure en réponse à un événement StatusChanged du Gestionnaire d’animations.  
  
```  
virtual void OnAnimationManagerStatusChanged(
    UI_ANIMATION_MANAGER_STATUS newStatus,  
    UI_ANIMATION_MANAGER_STATUS previousStatus);
```  
  
### <a name="parameters"></a>Paramètres  
 *newStatus*  
 Nouvel état de gestionnaire d’animation.  
  
 *previousStatus*  
 État précédent du Gestionnaire de l’animation.  
  
### <a name="remarks"></a>Notes  
 Cette méthode est appelée si vous activez les événements de gestionnaire d’animation avec EnableAnimationManagerEvent. Elle peut être substituée dans une classe dérivée pour prendre des mesures propres à l'application. L’implémentation par défaut des mises à jour une fenêtre associée si elle a été définie avec SetRelatedWnd.  
  
##  <a name="onanimationtimerpostupdate"></a>  CAnimationController::OnAnimationTimerPostUpdate  
 Appelé par le framework après qu’une mise à jour de l’animation terminée.  
  
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
 Appelé par le framework lorsque la fréquence d’images de rendu d’une animation est inférieur à une fréquence minimale souhaitable.  
  
```  
virtual void OnAnimationTimerRenderingTooSlow(UINT32 fps);
```  
  
### <a name="parameters"></a>Paramètres  
 *i/s*  
 La fréquence d’images actuelle en images par seconde.  
  
### <a name="remarks"></a>Notes  
 Cette méthode est appelée si vous activez les gestionnaires d’événements de minuterie avec EnableAnimationTimerEventHandler. Elle peut être substituée dans une classe dérivée pour prendre des mesures propres à l'application. La fréquence d’images souhaitable minimale est spécifiée en appelant IUIAnimationTimer::SetFrameRateThreshold.  
  
##  <a name="onanimationvaluechanged"></a>  CAnimationController::OnAnimationValueChanged  
 Appelé par l’infrastructure lors de la valeur de la variable de l’animation a changé.  
  
```  
virtual void OnAnimationValueChanged(
    CAnimationGroup* pGroup,  
    CAnimationBaseObject* pObject,  
    IUIAnimationVariable* variable,  
    DOUBLE newValue,  
    DOUBLE prevValue);
```  
  
### <a name="parameters"></a>Paramètres  
 *pGroup*  
 Un pointeur vers un groupe d’animation qui contient un objet d’animation dont la valeur a changé.  
  
 *pObject*  
 Pointeur vers un objet d’animation qui contient une variable d’animation dont la valeur a changé.  
  
 *Variable*  
 Pointeur vers une variable de l’animation.  
  
 *nouvelle valeur*  
 Spécifie la nouvelle valeur.  
  
 *prevValue*  
 Spécifie la valeur précédente.  
  
### <a name="remarks"></a>Notes  
 Cette méthode est appelée si vous activez les événements des variables d’animation avec EnableValueChangedEvent appelé pour une variable de l’animation spécifique ou un objet d’animation. Elle peut être substituée dans une classe dérivée pour prendre des mesures propres à l'application.  
  
##  <a name="onbeforeanimationstart"></a>  CAnimationController::OnBeforeAnimationStart  
 Appelée par l’infrastructure de droite avant que l’animation est planifiée.  
  
```  
virtual void OnBeforeAnimationStart(CAnimationGroup* pGroup);
```  
  
### <a name="parameters"></a>Paramètres  
 *pGroup*  
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
 *pGroupScheduled*  
 Groupe propriétaire du plan conceptuel actuellement planifié.  
  
 *pGroupNew*  
 Groupe propriétaire du nouveau plan conceptuel dont la planification est en conflit avec celle du plan conceptuel dont pGroupScheduled est propriétaire.  
  
 *priorityEffect*  
 Effet potentiel sur pGroupNew si pGroupScheduled a une priorité plus élevée.  
  
### <a name="return-value"></a>Valeur de retour  
 Doit retourner TRUE si le plan conceptuel détenu par pGroupNew est prioritaire. Doit retourner FALSE si le plan conceptuel détenu par pGroupScheduled est prioritaire.  
  
### <a name="remarks"></a>Notes  
 Cette méthode est appelée si vous activez les événements de comparaison de priorité à l'aide de CAnimationController::EnablePriorityComparisonHandler et que vous spécifiez UI_ANIMATION_PHT_CANCEL. Elle peut être substituée dans une classe dérivée pour prendre des mesures propres à l'application. Documentation de l’API Windows Animation en lecture pour plus d’informations sur la gestion des conflits (http://msdn.microsoft.com/library/dd371759(VS.85).aspx).  
  
##  <a name="onhasprioritycompress"></a>  CAnimationController::OnHasPriorityCompress  
 Appelé par l'infrastructure pour résoudre les conflits de planification.  
  
```  
virtual BOOL OnHasPriorityCompress(
    CAnimationGroup* pGroupScheduled,  
    CAnimationGroup* pGroupNew,  
    UI_ANIMATION_PRIORITY_EFFECT priorityEffect);
```  
  
### <a name="parameters"></a>Paramètres  
 *pGroupScheduled*  
 Groupe propriétaire du plan conceptuel actuellement planifié.  
  
 *pGroupNew*  
 Groupe propriétaire du nouveau plan conceptuel dont la planification est en conflit avec celle du plan conceptuel dont pGroupScheduled est propriétaire.  
  
 *priorityEffect*  
 Effet potentiel sur pGroupNew si pGroupScheduled a une priorité plus élevée.  
  
### <a name="return-value"></a>Valeur de retour  
 Doit retourner TRUE si le plan conceptuel détenu par pGroupNew est prioritaire. Doit retourner FALSE si le plan conceptuel détenu par pGroupScheduled est prioritaire.  
  
### <a name="remarks"></a>Notes  
 Cette méthode est appelée si vous activez les événements de comparaison de priorité à l'aide de CAnimationController::EnablePriorityComparisonHandler et que vous spécifiez UI_ANIMATION_PHT_COMPRESS. Elle peut être substituée dans une classe dérivée pour prendre des mesures propres à l'application. Documentation de l’API Windows Animation en lecture pour plus d’informations sur la gestion des conflits (http://msdn.microsoft.com/library/dd371759(VS.85).aspx).  
  
##  <a name="onhaspriorityconclude"></a>  CAnimationController::OnHasPriorityConclude  
 Appelé par l'infrastructure pour résoudre les conflits de planification.  
  
```  
virtual BOOL OnHasPriorityConclude(
    CAnimationGroup* pGroupScheduled,  
    CAnimationGroup* pGroupNew,  
    UI_ANIMATION_PRIORITY_EFFECT priorityEffect);
```  
  
### <a name="parameters"></a>Paramètres  
 *pGroupScheduled*  
 Groupe propriétaire du plan conceptuel actuellement planifié.  
  
 *pGroupNew*  
 Groupe propriétaire du nouveau plan conceptuel dont la planification est en conflit avec celle du plan conceptuel dont pGroupScheduled est propriétaire.  
  
 *priorityEffect*  
 Effet potentiel sur pGroupNew si pGroupScheduled a une priorité plus élevée.  
  
### <a name="return-value"></a>Valeur de retour  
 Doit retourner TRUE si le plan conceptuel détenu par pGroupNew est prioritaire. Doit retourner FALSE si le plan conceptuel détenu par pGroupScheduled est prioritaire.  
  
### <a name="remarks"></a>Notes  
 Cette méthode est appelée si vous activez les événements de comparaison de priorité à l'aide de CAnimationController::EnablePriorityComparisonHandler et que vous spécifiez UI_ANIMATION_PHT_CONCLUDE. Elle peut être substituée dans une classe dérivée pour prendre des mesures propres à l'application. Documentation de l’API Windows Animation en lecture pour plus d’informations sur la gestion des conflits (http://msdn.microsoft.com/library/dd371759(VS.85).aspx).  
  
##  <a name="onhasprioritytrim"></a>  CAnimationController::OnHasPriorityTrim  
 Appelé par l'infrastructure pour résoudre les conflits de planification.  
  
```  
virtual BOOL OnHasPriorityTrim(
    CAnimationGroup* pGroupScheduled,  
    CAnimationGroup* pGroupNew,  
    UI_ANIMATION_PRIORITY_EFFECT priorityEffect);
```  
  
### <a name="parameters"></a>Paramètres  
 *pGroupScheduled*  
 Groupe propriétaire du plan conceptuel actuellement planifié.  
  
 *pGroupNew*  
 Groupe propriétaire du nouveau plan conceptuel dont la planification est en conflit avec celle du plan conceptuel dont pGroupScheduled est propriétaire.  
  
 *priorityEffect*  
 Effet potentiel sur pGroupNew si pGroupScheduled a une priorité plus élevée.  
  
### <a name="return-value"></a>Valeur de retour  
 Doit retourner TRUE si le plan conceptuel détenu par pGroupNew est prioritaire. Doit retourner FALSE si le plan conceptuel détenu par pGroupScheduled est prioritaire.  
  
### <a name="remarks"></a>Notes  
 Cette méthode est appelée si vous activez les événements de comparaison de priorité à l'aide de CAnimationController::EnablePriorityComparisonHandler et que vous spécifiez UI_ANIMATION_PHT_TRIM. Elle peut être substituée dans une classe dérivée pour prendre des mesures propres à l'application. Documentation de l’API Windows Animation en lecture pour plus d’informations sur la gestion des conflits (http://msdn.microsoft.com/library/dd371759(VS.85).aspx).  
  
##  <a name="onstoryboardstatuschanged"></a>  CAnimationController::OnStoryboardStatusChanged  
 Appelé par l’infrastructure lors de l’état de la table de montage séquentiel a changé.  
  
```  
virtual void OnStoryboardStatusChanged(
    CAnimationGroup* pGroup,  
    UI_ANIMATION_STORYBOARD_STATUS newStatus,  
    UI_ANIMATION_STORYBOARD_STATUS previousStatus);
```  
  
### <a name="parameters"></a>Paramètres  
 *pGroup*  
 Un pointeur vers un groupe d’animation qui possède le storyboard dont l’état a changé.  
  
 *newStatus*  
 Spécifie le nouvel état.  
  
 *previousStatus*  
 Spécifie l’état précédent.  
  
### <a name="remarks"></a>Notes  
 Cette méthode est appelée si vous activez les événements de table de montage séquentiel à l’aide de CAnimationController::EnableStoryboardEventHandler. Elle peut être substituée dans une classe dérivée pour prendre des mesures propres à l'application.  
  
##  <a name="onstoryboardupdated"></a>  CAnimationController::OnStoryboardUpdated  
 Appelé par l’infrastructure lors de la table de montage séquentiel a été mis à jour.  
  
```  
virtual void OnStoryboardUpdated(CAnimationGroup* pGroup);
```  
  
### <a name="parameters"></a>Paramètres  
 *pGroup*  
 Pointeur vers un groupe qui possède le storyboard.  
  
### <a name="remarks"></a>Notes  
 Cette méthode est appelée si vous activez les événements de table de montage séquentiel à l’aide de CAnimationController::EnableStoryboardEventHandler. Elle peut être substituée dans une classe dérivée pour prendre des mesures propres à l'application.  
  
##  <a name="removeallanimationgroups"></a>  CAnimationController::RemoveAllAnimationGroups  
 Supprime tous les groupes d’animation à partir du contrôleur de l’animation.  
  
```  
void RemoveAllAnimationGroups();
```  
  
### <a name="remarks"></a>Notes  
 Tous les groupes sera supprimé, le pointeur, si stocké au niveau de l’application, doit être invalidé. Si CAnimationGroup::m_bAutodestroyAnimationObjects pour un groupe en cours de suppression est TRUE, tous les objets d’animation qui appartiennent à ce groupe seront supprimés ; Sinon, leurs références au contrôleur de l’animation parent sont la valeur NULL et qu’ils peuvent être ajoutés à un autre contrôleur.  
  
##  <a name="removeanimationgroup"></a>  CAnimationController::RemoveAnimationGroup  
 Supprime un groupe d’animation avec l’ID spécifié à partir du contrôleur de l’animation.  
  
```  
void RemoveAnimationGroup(UINT32 nGroupID);
```  
  
### <a name="parameters"></a>Paramètres  
 *nGroupID*  
 Spécifie l’ID de groupe d’animation.  
  
### <a name="remarks"></a>Notes  
 Cette méthode supprime un groupe d’animation à partir de la liste interne des groupes et le supprime, par conséquent, si vous avez stocké un pointeur vers ce groupe d’animation, elle doit être invalidé. Si CAnimationGroup::m_bAutodestroyAnimationObjects a la valeur TRUE, tous les objets d’animation qui appartiennent à ce groupe seront supprimés ; Sinon, leurs références au contrôleur de l’animation parent sont la valeur NULL et qu’ils peuvent être ajoutés à un autre contrôleur.  
  
##  <a name="removeanimationobject"></a>  CAnimationController::RemoveAnimationObject  
 Supprimer un objet d’animation à partir du contrôleur de l’animation.  
  
```  
void RemoveAnimationObject(
    CAnimationBaseObject* pObject,  
    BOOL bNoDelete = FALSE);
```  
  
### <a name="parameters"></a>Paramètres  
 *pObject*  
 Pointeur vers un objet d’animation.  
  
 *bNoDelete*  
 Si ce paramètre a la valeur TRUE l’objet ne sera pas supprimé à supprimer.  
  
### <a name="remarks"></a>Notes  
 Supprime un objet d’animation de contrôleur de l’animation et de groupe d’animation. Appelez cette fonction si un objet particulier ne doit pas être animé plus ou si vous souhaitez déplacer l’objet vers un autre contrôleur de l’animation. Dans le dernier cas bNoDelete doit être TRUE.  
  
##  <a name="removetransitions"></a>  CAnimationController::RemoveTransitions  
 Supprime les transitions des objets d’animation qui appartiennent au groupe spécifié.  
  
```  
void RemoveTransitions(UINT32 nGroupID);
```  
  
### <a name="parameters"></a>Paramètres  
 *nGroupID*  
 Spécifie l’ID de groupe.  
  
### <a name="remarks"></a>Notes  
 Le groupe effectue une itération sur ses objets d’animation et appelle ClearTransitions (false) pour chaque objet d’animation. Cette méthode est appelée par l’infrastructure une fois l’animation a été planifiée.  
  
##  <a name="schedulegroup"></a>  CAnimationController::ScheduleGroup  
 Planifie une animation.  
  
```  
BOOL ScheduleGroup(
    UINT32 nGroupID,  
    UI_ANIMATION_SECONDS time = 0.0);
```  
  
### <a name="parameters"></a>Paramètres  
 *nGroupID*  
 Spécifie l’ID de groupe de planification de l’animation.  
  
 *time*  
 Spécifie l’heure de planification.  
  
### <a name="return-value"></a>Valeur de retour  
 TRUE si l’animation a été planifiée avec succès. FALSE si la table de montage séquentiel n’a pas été créé, ou autre erreur se produit.  
  
### <a name="remarks"></a>Notes  
 Vous devez appeler AnimateGroup avec bScheduleNow paramètre la valeur FALSE ScheduleGroup préalable. Vous pouvez spécifier l’heure de l’animation souhaitée obtenue à partir de IUIAnimationTimer::GetTime. Si le paramètre d’heure est 0.0, l’animation est planifiée pour l’heure actuelle.  
  
##  <a name="setrelatedwnd"></a>  CAnimationController::SetRelatedWnd  
 Établit une relation entre le contrôleur de l’animation et une fenêtre.  
  
```  
void SetRelatedWnd(CWnd* pWnd);
```  
  
### <a name="parameters"></a>Paramètres  
 *pWnd*  
 Pointeur vers l’objet de fenêtre à définir.  
  
### <a name="remarks"></a>Notes  
 Si un objet CWnd connexe est défini, le contrôleur de l’animation peut automatiquement mettre à jour (envoi un message WM_PAINT) lorsque l’état du Gestionnaire d’animations a changé ou les événements de mise à jour du minuteur post s’est produite.  
  
##  <a name="updateanimationmanager"></a>  CAnimationController::UpdateAnimationManager  
 Dirige le Gestionnaire d’animation pour mettre à jour les valeurs de toutes les variables de l’animation.  
  
```  
virtual void UpdateAnimationManager();
```  
  
### <a name="remarks"></a>Notes  
 Valeurs interpolées à appeler que cette méthode avance le Gestionnaire d’animations à l’heure actuelle, le changement de statut des plans conceptuels que nécessaire et la mise à jour de toutes les variables d’animation appropriés. Cette méthode appelle en interne IUIAnimationTimer::GetTime(timeNow) et IUIAnimationManager::Update (timeNow). Substituez cette méthode dans une classe dérivée pour personnaliser ce comportement.  
  
## <a name="see-also"></a>Voir aussi  
 [Classes](../../mfc/reference/mfc-classes.md)
