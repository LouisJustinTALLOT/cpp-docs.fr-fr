---
title: CAnimationGroup, classe | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
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
dev_langs:
- C++
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
caps.latest.revision: 17
author: mikeblome
ms.author: mblome
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 4a770b6508067913aec51b8b3878f33e30eed4bb
ms.openlocfilehash: 9c59bd895187d0d9a047c626426736a957a4d6b5
ms.contentlocale: fr-fr
ms.lasthandoff: 10/09/2017

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
|[CAnimationGroup :: ~ CAnimationGroup](#canimationgroup__~canimationgroup)|Destructeur. Appelé lorsqu’un groupe d’animation est détruit.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[Pas CAnimationGroup::Animate](#animate)|Réalise une animation d’un groupe.|  
|[CAnimationGroup::ApplyTransitions](#applytransitions)|Applique des transitions aux objets d’animation.|  
|[CAnimationGroup::FindAnimationObject](#findanimationobject)|Recherche un objet d’animation qui contient la variable d’animation spécifiée.|  
|[CAnimationGroup::GetGroupID](#getgroupid)|Retourne le GroupID.|  
|[CAnimationGroup::RemoveKeyframes](#removekeyframes)|Supprime et, éventuellement détruit, toutes les images clés qui appartiennent à un groupe d’animation.|  
|[CAnimationGroup::RemoveTransitions](#removetransitions)|Supprime les transitions des objets d’animation qui appartiennent à un groupe d’animation.|  
|[CAnimationGroup::Schedule](#schedule)|Planifie une animation à l’heure spécifiée.|  
|[CAnimationGroup::SetAutodestroyTransitions](#setautodestroytransitions)|Indique tous les objets d’animation qui appartient au groupe automatiquement les détruire les transitions.|  
  
### <a name="protected-methods"></a>Méthodes protégées  
  
|Nom|Description|  
|----------|-----------------|  
|[CAnimationGroup::AddKeyframes](#addkeyframes)|Un programme d’assistance qui ajoute des images clés à un plan conceptuel.|  
|[CAnimationGroup::AddTransitions](#addtransitions)|Un programme d’assistance qui ajoute des transitions à un plan conceptuel.|  
|[CAnimationGroup::CreateTransitions](#createtransitions)|Un programme d’assistance qui crée des objets COM transition.|  
  
### <a name="public-data-members"></a>Membres de données publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CAnimationGroup::m_bAutoclearTransitions](#m_bautocleartransitions)|Indique comment effacer les transitions des objets d’animation qui appartiennent au groupe. Si ce membre est TRUE, les transitions sont supprimées automatiquement lorsqu’une animation a été planifiée. Sinon, vous devez supprimer manuellement les transitions.|  
|[CAnimationGroup::m_bAutodestroyAnimationObjects](#m_bautodestroyanimationobjects)|Spécifie comment détruire les objets d’animation. Si ce paramètre est TRUE, les objets d’animation seront détruits automatiquement lorsque le groupe est détruit. Sinon, les objets d’animation doivent être détruits manuellement. La valeur par défaut est FALSE. Définissez cette valeur sur TRUE uniquement si tous les objets d’animation qui appartiennent au groupe sont alloués dynamiquement avec l’opérateur new.|  
|[CAnimationGroup::m_bAutodestroyKeyframes](#m_bautodestroykeyframes)|Spécifie comment détruire les images clés. Si cette valeur est TRUE, toutes les images clés sont supprimées et détruites ; dans le cas contraire, elles sont supprimées de la liste uniquement. La valeur par défaut est TRUE.|  
|[CAnimationGroup::m_lstAnimationObjects](#m_lstanimationobjects)|Contient une liste des objets d’animation.|  
|[CAnimationGroup::m_lstKeyFrames](#m_lstkeyframes)|Contient une liste d’images clés.|  
|[CAnimationGroup::m_pStoryboard](#m_pstoryboard)|Pointe vers le storyboard de l’animation. Ce pointeur est valide uniquement après l’appel d’animer.|  
  
### <a name="protected-data-members"></a>Membres de données protégés  
  
|Nom|Description|  
|----------|-----------------|  
|[CAnimationGroup::m_nGroupID](#m_ngroupid)|Identificateur unique du groupe d’animation.|  
|[CAnimationGroup::m_pParentController](#m_pparentcontroller)|Pointeur vers le contrôleur de l’animation qu'appartient ce groupe.|  
  
## <a name="remarks"></a>Remarques  
 Groupes d’animation sont créés automatiquement par le contrôleur de l’animation (CAnimationController) lorsque vous ajoutez des objets d’animation à l’aide de CAnimationController::AddAnimationObject. Un groupe d’animation est identifié par GroupID qui est généralement considéré comme un paramètre pour manipuler des groupes d’animation. GroupID est pris du premier objet d’animation qui est ajouté à un nouveau groupe d’animation. Un storyboard encapsulé est créé après l’appel de CAnimationController::AnimateGroup et est accessible via m_pStoryboard du membre public.  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 `CAnimationGroup`  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** afxanimationcontroller.h  
  
##  <a name="_dtorcanimationgroup"></a>CAnimationGroup :: ~ CAnimationGroup  
 Destructeur. Appelé lorsqu’un groupe d’animation est détruit.  
  
```  
~CAnimationGroup();
```  
  
##  <a name="addkeyframes"></a>CAnimationGroup::AddKeyframes  
 Un programme d’assistance qui ajoute des images clés à un plan conceptuel.  
  
```  
void AddKeyframes(IUIAnimationStoryboard* pStoryboard, BOOL bAddDeep);
```  
  
### <a name="parameters"></a>Paramètres  
 `pStoryboard`  
 Pointeur vers un objet COM de plan conceptuel.  
  
 `bAddDeep`  
 Spécifie si cette méthode doit ajouter aux table de montage séquentiel des images clés qui dépendent d’autres images clés.  
  
##  <a name="addtransitions"></a>CAnimationGroup::AddTransitions  
 Un programme d’assistance qui ajoute des transitions à un plan conceptuel.  
  
```  
void AddTransitions(
    IUIAnimationStoryboard* pStoryboard,  
    BOOL bDependOnKeyframes);
```  
  
### <a name="parameters"></a>Paramètres  
 `pStoryboard`  
 Pointeur vers un objet COM de plan conceptuel.  
  
 `bDependOnKeyframes`  
  
##  <a name="animate"></a>Pas CAnimationGroup::Animate  
 Réalise une animation d’un groupe.  
  
```  
BOOL Animate(
    IUIAnimationManager* pManager,  
    IUIAnimationTimer* pTimer,  
    BOOL bScheduleNow);
```  
  
### <a name="parameters"></a>Paramètres  
 `pManager`  
 `pTimer`  
 `bScheduleNow`  
  
### <a name="return-value"></a>Valeur de retour  
 TRUE si la méthode réussit ; Sinon, FALSE.  
  
### <a name="remarks"></a>Remarques  
 Cette méthode crée un storyboard interne, crée et applique des transitions et planifie une animation si bScheduleNow a la valeur TRUE. Si bScheduleNow a la valeur FALSE, vous devez appeler la planification pour démarrer l’animation à l’heure spécifiée.  
  
##  <a name="applytransitions"></a>CAnimationGroup::ApplyTransitions  
 Applique des transitions aux objets d’animation.  
  
```  
void ApplyTransitions();
```  
  
### <a name="remarks"></a>Remarques  
 Cette méthode déclare en mode débogage si le storyboard n’a pas été créé. Il crée toutes les transitions tout d’abord, puis ajoute les images clés « statiques » (images clés qui dépendent des offsets), ajoute des transitions qui ne dépendent pas des images clés, ajoute des images clés en fonction des transitions et autres images clés et enfin ajoute des transitions qui dépendent des images clés .  
  
##  <a name="canimationgroup"></a>CAnimationGroup::CAnimationGroup  
 Construit un groupe d’animation.  
  
```  
CAnimationGroup(CAnimationController* pParentController, UINT32 nGroupID);
```  
  
### <a name="parameters"></a>Paramètres  
 `pParentController`  
 Pointeur vers le contrôleur de l’animation qui crée un groupe.  
  
 `nGroupID`  
 Spécifie GroupID.  
  
##  <a name="createtransitions"></a>CAnimationGroup::CreateTransitions  
 Un programme d’assistance qui crée des objets COM transition.  
  
```  
BOOL CreateTransitions();
```  
  
### <a name="return-value"></a>Valeur de retour  
 La valeur TRUE est la méthode réussit, sinon FALSE.  
  
##  <a name="findanimationobject"></a>CAnimationGroup::FindAnimationObject  
 Recherche un objet d’animation qui contient la variable d’animation spécifiée.  
  
```  
CAnimationBaseObject* FindAnimationObject(IUIAnimationVariable* pVariable);
```  
  
### <a name="parameters"></a>Paramètres  
 `pVariable`  
 Pointeur vers la variable de l’animation.  
  
### <a name="return-value"></a>Valeur de retour  
 Pointeur vers l’objet d’animation, ou NULL si l’objet d’animation est introuvable.  
  
##  <a name="getgroupid"></a>CAnimationGroup::GetGroupID  
 Retourne le GroupID.  
  
```  
UINT32 GetGroupID() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Un identificateur de groupe.  
  
##  <a name="m_bautocleartransitions"></a>CAnimationGroup::m_bAutoclearTransitions  
 Indique comment effacer les transitions des objets d’animation qui appartiennent au groupe. Si ce membre est TRUE, les transitions sont supprimées automatiquement lorsqu’une animation a été planifiée. Sinon, vous devez supprimer manuellement les transitions.  
  
```  
BOOL m_bAutoclearTransitions;  
```  
  
##  <a name="m_bautodestroyanimationobjects"></a>CAnimationGroup::m_bAutodestroyAnimationObjects  
 Spécifie comment détruire les objets d’animation. Si ce paramètre est TRUE, les objets d’animation seront détruits automatiquement lorsque le groupe est détruit. Sinon, les objets d’animation doivent être détruits manuellement. La valeur par défaut est FALSE. Définissez cette valeur sur TRUE uniquement si tous les objets d’animation qui appartiennent au groupe sont alloués dynamiquement avec l’opérateur new.  
  
```  
BOOL m_bAutodestroyAnimationObjects;  
```  
  
##  <a name="m_bautodestroykeyframes"></a>CAnimationGroup::m_bAutodestroyKeyframes  
 Spécifie comment détruire les images clés. Si cette valeur est TRUE, toutes les images clés sont supprimées et détruites ; dans le cas contraire, elles sont supprimées de la liste uniquement. La valeur par défaut est TRUE.  
  
```  
BOOL m_bAutodestroyKeyframes;  
```  
  
##  <a name="m_lstanimationobjects"></a>CAnimationGroup::m_lstAnimationObjects  
 Contient une liste des objets d’animation.  
  
```  
CObList m_lstAnimationObjects;  
```  
  
##  <a name="m_lstkeyframes"></a>CAnimationGroup::m_lstKeyFrames  
 Contient une liste d’images clés.  
  
```  
CObList m_lstKeyFrames;  
```  
  
##  <a name="m_ngroupid"></a>CAnimationGroup::m_nGroupID  
 Identificateur unique du groupe d’animation.  
  
```  
UINT32 m_nGroupID;  
```  
  
##  <a name="m_pparentcontroller"></a>CAnimationGroup::m_pParentController  
 Pointeur vers le contrôleur de l’animation qu'appartient ce groupe.  
  
```  
CAnimationController* m_pParentController;  
```  
  
##  <a name="m_pstoryboard"></a>CAnimationGroup::m_pStoryboard  
 Pointe vers le storyboard de l’animation. Ce pointeur est valide uniquement après l’appel d’animer.  
  
```  
ATL::CComPtr<IUIAnimationStoryboard> m_pStoryboard;  
```  
  
##  <a name="removekeyframes"></a>CAnimationGroup::RemoveKeyframes  
 Supprime et, éventuellement détruit, toutes les images clés qui appartiennent à un groupe d’animation.  
  
```  
void RemoveKeyframes();
```  
  
### <a name="remarks"></a>Remarques  
 Si m_bAutodestroyKeyframes du membre est TRUE, puis les images clés sont supprimées et détruites, sinon les images clés sont supprimées uniquement à partir de la liste interne des images clés.  
  
##  <a name="removetransitions"></a>CAnimationGroup::RemoveTransitions  
 Supprime les transitions des objets d’animation qui appartiennent à un groupe d’animation.  
  
```  
void RemoveTransitions();
```  
  
### <a name="remarks"></a>Remarques  
 Si l’indicateur m_bAutoclearTransitions est définie sur TRUE, cette méthode effectue une itération sur tous les objets d’animation qui appartiennent au groupe et appelle CAnimationObject::ClearTransitions (false).  
  
##  <a name="schedule"></a>CAnimationGroup::Schedule  
 Planifie une animation à l’heure spécifiée.  
  
```  
BOOL Schedule(IUIAnimationTimer* pTimer, UI_ANIMATION_SECONDS time);
```  
  
### <a name="parameters"></a>Paramètres  
 `pTimer`  
 Pointeur vers la minuterie de l’animation.  
  
 `time`  
 Spécifie l’heure de planification de l’animation.  
  
### <a name="return-value"></a>Valeur de retour  
 TRUE si la méthode réussit ; FALSE si la méthode échoue ou si l’animation ne possède pas été appelé avec bScheduleNow défini sur FALSE.  
  
### <a name="remarks"></a>Remarques  
 Appelez cette fonction pour planifier une animation à l’heure spécifiée. Vous devez appeler animer avec bScheduleNow tout d’abord la valeur FALSE.  
  
##  <a name="setautodestroytransitions"></a>CAnimationGroup::SetAutodestroyTransitions  
 Indique tous les objets d’animation qui appartient au groupe automatiquement les détruire les transitions.  
  
```  
void SetAutodestroyTransitions(BOOL bAutoDestroy = TRUE);
```  
  
### <a name="parameters"></a>Paramètres  
 `bAutoDestroy`  
 Spécifie comment détruire les transitions.  
  
### <a name="remarks"></a>Remarques  
 Définissez cette valeur sur FALSE uniquement si vous allouez des transitions sur la pile. La valeur par défaut est TRUE, par conséquent, il a fortement recommandé d’allouer des objets de transition à l’aide de nouvel opérateur.  
  
## <a name="see-also"></a>Voir aussi  
 [Classes](../../mfc/reference/mfc-classes.md)

