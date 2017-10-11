---
title: CAnimationBaseObject, classe | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CAnimationBaseObject
- AFXANIMATIONCONTROLLER/CAnimationBaseObject
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::CAnimationBaseObject
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::ApplyTransitions
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::ClearTransitions
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::ContainsVariable
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::CreateTransitions
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::DetachFromController
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::EnableIntegerValueChangedEvent
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::EnableValueChangedEvent
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::GetAutodestroyTransitions
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::GetGroupID
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::GetObjectID
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::GetUserData
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::SetAutodestroyTransitions
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::SetID
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::SetUserData
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::GetAnimationVariableList
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::SetParentAnimationObjects
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::m_bAutodestroyTransitions
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::m_dwUserData
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::m_nGroupID
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::m_nObjectID
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::m_pParentController
dev_langs:
- C++
helpviewer_keywords:
- CAnimationBaseObject [MFC], CAnimationBaseObject
- CAnimationBaseObject [MFC], ApplyTransitions
- CAnimationBaseObject [MFC], ClearTransitions
- CAnimationBaseObject [MFC], ContainsVariable
- CAnimationBaseObject [MFC], CreateTransitions
- CAnimationBaseObject [MFC], DetachFromController
- CAnimationBaseObject [MFC], EnableIntegerValueChangedEvent
- CAnimationBaseObject [MFC], EnableValueChangedEvent
- CAnimationBaseObject [MFC], GetAutodestroyTransitions
- CAnimationBaseObject [MFC], GetGroupID
- CAnimationBaseObject [MFC], GetObjectID
- CAnimationBaseObject [MFC], GetUserData
- CAnimationBaseObject [MFC], SetAutodestroyTransitions
- CAnimationBaseObject [MFC], SetID
- CAnimationBaseObject [MFC], SetUserData
- CAnimationBaseObject [MFC], GetAnimationVariableList
- CAnimationBaseObject [MFC], SetParentAnimationObjects
- CAnimationBaseObject [MFC], m_bAutodestroyTransitions
- CAnimationBaseObject [MFC], m_dwUserData
- CAnimationBaseObject [MFC], m_nGroupID
- CAnimationBaseObject [MFC], m_nObjectID
- CAnimationBaseObject [MFC], m_pParentController
ms.assetid: 76b25917-940e-4eba-940f-31d270702603
caps.latest.revision: 17
author: mikeblome
ms.author: mblome
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 4a770b6508067913aec51b8b3878f33e30eed4bb
ms.openlocfilehash: 0e866ec4858ecc32c4608d1fd9cbd9d42d4b1eee
ms.contentlocale: fr-fr
ms.lasthandoff: 10/09/2017

---
# <a name="canimationbaseobject-class"></a>CAnimationBaseObject, classe
Classe de base pour tous les objets d'animation.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CAnimationBaseObject : public CObject;  
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CAnimationBaseObject::CAnimationBaseObject](#canimationbaseobject)|Surchargé. Construit un objet d’animation.|  
|[CAnimationBaseObject :: ~ CAnimationBaseObject](#canimationbaseobject__~canimationbaseobject)|Destructeur. Appelé lorsqu’un objet d’animation est détruit.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[CAnimationBaseObject::ApplyTransitions](#applytransitions)|Ajoute des transitions storyboard avec une variable d’animation encapsulée.|  
|[CAnimationBaseObject::ClearTransitions](#cleartransitions)|Supprime toutes les transitions connexes.|  
|[CAnimationBaseObject::ContainsVariable](#containsvariable)|Détermine si un objet d’animation contient une variable d’animation particulière.|  
|[CAnimationBaseObject::CreateTransitions](#createtransitions)|Crée des transitions associées à un objet d’animation.|  
|[CAnimationBaseObject::DetachFromController](#detachfromcontroller)|Détache un objet d’animation à partir du contrôleur de l’animation parent.|  
|[CAnimationBaseObject::EnableIntegerValueChangedEvent](#enableintegervaluechangedevent)|Définit la valeur de type entier modifié Gestionnaire d’événements.|  
|[CAnimationBaseObject::EnableValueChangedEvent](#enablevaluechangedevent)|Définit la valeur modifiée Gestionnaire d’événements.|  
|[CAnimationBaseObject::GetAutodestroyTransitions](#getautodestroytransitions)|Indique si une transition connexe sont détruits automatiquement.|  
|[CAnimationBaseObject::GetGroupID](#getgroupid)|Retourne l’ID du groupe actuel.|  
|[CAnimationBaseObject::GetObjectID](#getobjectid)|Retourne l’ID d’objet en cours.|  
|[CAnimationBaseObject::GetUserData](#getuserdata)|Retourne les données définies par l’utilisateur.|  
|[CAnimationBaseObject::SetAutodestroyTransitions](#setautodestroytransitions)|Définit un indicateur qui ordonne la destruction automatique des transitions.|  
|[CAnimationBaseObject::SetID](#setid)|Définit les nouveaux ID.|  
|[CAnimationBaseObject::SetUserData](#setuserdata)|Données définies par l’utilisateur de jeux.|  
  
### <a name="protected-methods"></a>Méthodes protégées  
  
|Nom|Description|  
|----------|-----------------|  
|[CAnimationBaseObject::GetAnimationVariableList](#getanimationvariablelist)|Collecte des pointeurs aux variables d’animation de relation contenant-contenu.|  
|[CAnimationBaseObject::SetParentAnimationObjects](#setparentanimationobjects)|Établit la relation entre les variables d’animation, contenues dans un objet d’animation et leur conteneur.|  
  
### <a name="protected-data-members"></a>Membres de données protégés  
  
|Nom|Description|  
|----------|-----------------|  
|[CAnimationBaseObject::m_bAutodestroyTransitions](#m_bautodestroytransitions)|Spécifie si les transitions connexes doivent être détruites automatiquement.|  
|[CAnimationBaseObject::m_dwUserData](#m_dwuserdata)|Stocke les données définies par l’utilisateur.|  
|[CAnimationBaseObject::m_nGroupID](#m_ngroupid)|Spécifie l’ID de groupe de l’objet d’animation.|  
|[CAnimationBaseObject::m_nObjectID](#m_nobjectid)|Spécifie l’ID d’objet de l’objet d’animation.|  
|[CAnimationBaseObject::m_pParentController](#m_pparentcontroller)|Pointeur vers le contrôleur de l’animation parent.|  
  
## <a name="remarks"></a>Remarques  
 Cette classe implémente les méthodes de base pour tous les objets d’animation. Un objet d’animation peut représenter une valeur, le point, la taille, la rectangle ou de couleur dans une application, ainsi que toute entité personnalisée. Objets d’animation sont stockés dans les groupes d’animation (voir CAnimationGroup). Chaque groupe peut être animé séparément et peut être traité comme un équivalent du plan conceptuel. Un objet d’animation encapsule une ou plusieurs variables d’animation (voir CAnimationVariable), en fonction de sa représentation logique. Par exemple, CAnimationRect contient quatre variables d’animation - une variable pour chaque côté du rectangle. Chaque classe d’objet animation expose la méthode AddTransition surchargée, qui doit être utilisé pour appliquer des transitions aux variables d’animation encapsulée. Un objet d’animation peut être identifié par l’ID d’objet (facultatif), par ID de groupe. Un ID de groupe est nécessaire pour placer un objet d’animation pour le groupe approprié, mais si un ID de groupe n’est pas spécifié, un objet est placé dans le groupe par défaut avec l’ID 0. Si vous appelez SetID avec un GroupID différent, un objet d’animation est déplacé vers un autre groupe (un nouveau groupe est créé si nécessaire).  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CAnimationBaseObject`  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** afxanimationcontroller.h  
  
##  <a name="_dtorcanimationbaseobject"></a>CAnimationBaseObject :: ~ CAnimationBaseObject  
 Destructeur. Appelé lorsqu’un objet d’animation est détruit.  
  
```  
virtual ~CAnimationBaseObject();
```  
  
##  <a name="applytransitions"></a>CAnimationBaseObject::ApplyTransitions  
 Ajoute des transitions storyboard avec une variable d’animation encapsulée.  
  
```  
virtual BOOL ApplyTransitions(
    IUIAnimationStoryboard* pStoryboard,  
    BOOL bDependOnKeyframes);
```  
  
### <a name="parameters"></a>Paramètres  
 `pStoryboard`  
 Pointeur vers un plan conceptuel.  
  
 `bDependOnKeyframes`  
 Avec la valeur FALSE, cette méthode ajoute uniquement les transitions qui ne dépendent pas des images clés.  
  
### <a name="return-value"></a>Valeur de retour  
 TRUE si les transitions ont été ajoutées avec succès.  
  
### <a name="remarks"></a>Remarques  
 Ajoute des transitions connexes qui ont été ajoutées avec AddTransition (méthodes surchargées dans les classes dérivées), pour créer un plan conceptuel.  
  
##  <a name="canimationbaseobject"></a>CAnimationBaseObject::CAnimationBaseObject  
 Construit un objet d’animation.  
  
```  
CAnimationBaseObject();

 
CAnimationBaseObject(
    UINT32 nGroupID,  
    UINT32 nObjectID = (UINT32)-1,  
    DWORD dwUserData = 0);
```  
  
### <a name="parameters"></a>Paramètres  
 `nGroupID`  
 Spécifie l’ID de groupe.  
  
 `nObjectID`  
 Spécifie l’ID d’objet.  
  
 `dwUserData`  
 Données utilisateur, qui peuvent être associées à l’objet d’animation et récupérées ultérieurement lors de l’exécution.  
  
### <a name="remarks"></a>Remarques  
 Construit un objet d’animation et assigne des ID d’objet par défaut (0) et l’ID de groupe (0).  
  
##  <a name="cleartransitions"></a>CAnimationBaseObject::ClearTransitions  
 Supprime toutes les transitions connexes.  
  
```  
virtual void ClearTransitions(BOOL bAutodestroy);
```  
  
### <a name="parameters"></a>Paramètres  
 `bAutodestroy`  
 Spécifie s’il faut détruire automatiquement les objets de transition ou juste les supprimer de la liste associée.  
  
### <a name="remarks"></a>Remarques  
 Supprime toutes les transitions et les détruit si l’indicateur bAutodestroy ou m_bAutodestroyTransitions a la valeur TRUE. Transitions doivent être détruites automatiquement uniquement si elles ne sont pas alloués sur la pile. Si les indicateurs ci-dessus ont la valeur FALSE, les transitions sont supprimées uniquement à partir de la liste interne des transitions connexes.  
  
##  <a name="containsvariable"></a>CAnimationBaseObject::ContainsVariable  
 Détermine si un objet d’animation contient une variable d’animation particulière.  
  
```  
virtual BOOL ContainsVariable(IUIAnimationVariable* pVariable);
```  
  
### <a name="parameters"></a>Paramètres  
 `pVariable`  
 Pointeur vers la variable de l’animation.  
  
### <a name="return-value"></a>Valeur de retour  
 TRUE si la variable de l’animation est contenue dans l’objet d’animation. Sinon, FALSE.  
  
### <a name="remarks"></a>Remarques  
 Cette méthode peut être utilisée pour déterminer si une variable d’animation spécifiée par pVariable est contenue dans un objet d’animation. Un objet d’animation, selon son type, peut contenir plusieurs variables d’animation. Par exemple, CAnimationColor contient trois variables, une pour chaque composant de couleur (rouge, vert et bleu). Lorsqu’une valeur de variable de l’animation a changé, l’API Windows Animation envoie des événements ValueChanged ou IntegerValueChanged (si activé) et le paramètre de cet événement est un pointeur vers l’interface IUIAnimationVariable de la variable de l’animation. Cette méthode permet d’obtenir un pointeur vers une animation à partir d’un pointeur vers un objet COM qu’il contient.  
  
##  <a name="createtransitions"></a>CAnimationBaseObject::CreateTransitions  
 Crée des transitions associées à un objet d’animation.  
  
```  
BOOL CreateTransitions();
```  
  
### <a name="return-value"></a>Valeur de retour  
 TRUE si les transitions ont été créées avec succès ; Sinon, FALSE.  
  
### <a name="remarks"></a>Remarques  
 Effectue une itération sur la liste des variables d’animation encapsulées dans un objet d’animation dérivé et crée des transitions associées à chaque variable de l’animation.  
  
##  <a name="detachfromcontroller"></a>CAnimationBaseObject::DetachFromController  
 Détache un objet d’animation à partir du contrôleur de l’animation parent.  
  
```  
void DetachFromController();
```  
  
### <a name="remarks"></a>Remarques  
 Cette méthode est utilisée en interne.  
  
##  <a name="enableintegervaluechangedevent"></a>CAnimationBaseObject::EnableIntegerValueChangedEvent  
 Définit la valeur de type entier modifié Gestionnaire d’événements.  
  
```  
virtual void EnableIntegerValueChangedEvent(
    CAnimationController* pController,  
    BOOL bEnable);
```  
  
### <a name="parameters"></a>Paramètres  
 `pController`  
 Pointeur vers un contrôleur parent.  
  
 `bEnable`  
 Spécifie s’il faut activer ou désactiver l’événement de modification de valeur d’entier.  
  
### <a name="remarks"></a>Remarques  
 Si le Gestionnaire d’événements valeur de type entier modifié est activé, vous pouvez gérer cet événement dans la méthode CAnimationController::OnAnimationIntegerValueChanged, qui doit être substituée dans une classe dérivée de CAnimationController. Cette méthode est appelée chaque fois que la valeur d’entier de l’animation a changé.  
  
##  <a name="enablevaluechangedevent"></a>CAnimationBaseObject::EnableValueChangedEvent  
 Définit la valeur modifiée Gestionnaire d’événements.  
  
```  
virtual void EnableValueChangedEvent(
    CAnimationController* pController,  
    BOOL bEnable);
```  
  
### <a name="parameters"></a>Paramètres  
 `pController`  
 Pointeur vers un contrôleur parent.  
  
 `bEnable`  
 Spécifie s’il faut activer ou désactiver l’événement de modification de valeur.  
  
### <a name="remarks"></a>Remarques  
 Si le Gestionnaire d’événements valeur modifiée est activé, vous pouvez gérer cet événement dans la méthode CAnimationController::OnAnimationValueChanged, qui doit être substituée dans une classe dérivée de CAnimationController. Cette méthode est appelée chaque fois que la valeur de l’animation a changé.  
  
##  <a name="getanimationvariablelist"></a>CAnimationBaseObject::GetAnimationVariableList  
 Collecte des pointeurs aux variables d’animation de relation contenant-contenu.  
  
```  
virtual void GetAnimationVariableList(
    CList<CAnimationVariable*, 
    CAnimationVariable*>& lst) = 0;  
```  
  
### <a name="parameters"></a>Paramètres  
 `lst`  
 Une liste qui doit être remplie avec les variables d’animation contenues dans un objet d’animation.  
  
### <a name="remarks"></a>Remarques  
 Il s’agit d’une méthode virtuelle pure qui doit être substituée dans une classe dérivée. Un objet d’animation, selon son type, contient une ou plusieurs variables d’animation. Par exemple, CAnimationPoint contient deux variables, pour les coordonnées X et Y respectivement. La classe de base CAnimationBaseObject implémente certaines méthodes génériques qui agissent sur une liste de variables d’animation : ApplyTransitions, ClearTransitions, EnableValueChangedEvent, EnableIntegerValueChangedEvent. Ces méthodes appellent GetAnimationVariableList, qui est rempli avec les variables d’animation réelles contenues dans un objet d’animation particulier dans une classe dérivée, puis une boucle sur la liste et effectuer les actions nécessaires. Si vous créez un objet d’animation personnalisée, vous devez ajouter à lst toutes les variables d’animation contenues dans cet objet.  
  
##  <a name="getautodestroytransitions"></a>CAnimationBaseObject::GetAutodestroyTransitions  
 Indique si une transition connexe sont détruits automatiquement.  
  
```  
BOOL GetAutodestroyTransitions() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Si la valeur est TRUE, les transitions connexes sont détruites automatiquement. Si la valeur est FALSE, les objets de transition doivent être libérées en appelant l’application.  
  
### <a name="remarks"></a>Remarques  
 Par défaut, cet indicateur est TRUE. Définissez cet indicateur uniquement si vous avez alloué la transition sur la pile et/ou transitions doivent être libérées par l’application appelante.  
  
##  <a name="getgroupid"></a>CAnimationBaseObject::GetGroupID  
 Retourne l’ID du groupe actuel.  
  
```  
UINT32 GetGroupID() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 ID de groupe actuel.  
  
### <a name="remarks"></a>Remarques  
 Utilisez cette méthode pour récupérer l’ID de groupe. Il s’agit de 0 si l’ID de groupe n'a pas été défini explicitement dans le constructeur ou avec SetID.  
  
##  <a name="getobjectid"></a>CAnimationBaseObject::GetObjectID  
 Retourne l’ID d’objet en cours.  
  
```  
UINT32 GetObjectID() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 ID d’objet en cours.  
  
### <a name="remarks"></a>Remarques  
 Utilisez cette méthode pour récupérer l’ID d’objet. Il s’agit de 0 si l’ID d’objet n'a pas été défini explicitement dans le constructeur ou avec SetID.  
  
##  <a name="getuserdata"></a>CAnimationBaseObject::GetUserData  
 Retourne les données définies par l’utilisateur.  
  
```  
DWORD GetUserData() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Une valeur de données personnalisées.  
  
### <a name="remarks"></a>Remarques  
 Appelez cette méthode pour récupérer les données personnalisées lors de l’exécution. La valeur retournée sera 0 si elle a été pas explicitement dans le constructeur ou avec SetUserData.  
  
##  <a name="m_bautodestroytransitions"></a>CAnimationBaseObject::m_bAutodestroyTransitions  
 Spécifie si les transitions connexes doivent être détruites automatiquement.  
  
```  
BOOL m_bAutodestroyTransitions;  
```  
  
##  <a name="m_dwuserdata"></a>CAnimationBaseObject::m_dwUserData  
 Stocke les données définies par l’utilisateur.  
  
```  
DWORD m_dwUserData;  
```  
  
##  <a name="m_ngroupid"></a>CAnimationBaseObject::m_nGroupID  
 Spécifie l’ID de groupe de l’objet d’animation.  
  
```  
UINT32 m_nGroupID;  
```  
  
##  <a name="m_nobjectid"></a>CAnimationBaseObject::m_nObjectID  
 Spécifie l’ID d’objet de l’objet d’animation.  
  
```  
UINT32 m_nObjectID;  
```  
  
##  <a name="m_pparentcontroller"></a>CAnimationBaseObject::m_pParentController  
 Pointeur vers le contrôleur de l’animation parent.  
  
```  
CAnimationController* m_pParentController;  
```  
  
##  <a name="setautodestroytransitions"></a>CAnimationBaseObject::SetAutodestroyTransitions  
 Définit un indicateur qui ordonne la destruction automatique des transitions.  
  
```  
void SetAutodestroyTransitions(BOOL bValue);
```  
  
### <a name="parameters"></a>Paramètres  
 `bValue`  
 Spécifie l’indicateur de destruction automatique.  
  
### <a name="remarks"></a>Remarques  
 Définissez cet indicateur uniquement si vous avez alloué des objets de transition à l’aide de nouvel opérateur. Si pour une raison quelconque, les objets de transition sont alloués sur la pile, détruire automatique indicateur doit être FALSE. Par défaut, cet indicateur est TRUE.  
  
##  <a name="setid"></a>CAnimationBaseObject::SetID  
 Définit les nouveaux ID.  
  
```  
void SetID(
    UINT32 nObjectID,  
    UINT32 nGroupID = 0);
```  
  
### <a name="parameters"></a>Paramètres  
 `nObjectID`  
 Spécifie le nouvel ID d’objet.  
  
 `nGroupID`  
 Spécifie le nouvel ID de groupe.  
  
### <a name="remarks"></a>Remarques  
 Permet de modifier l’ID d’objet et ID de groupe. Si le nouvel ID de groupe diffère de l’ID actuel, un objet d’animation est déplacé vers un autre groupe (un nouveau groupe sera créé, si nécessaire).  
  
##  <a name="setparentanimationobjects"></a>CAnimationBaseObject::SetParentAnimationObjects  
 Établit la relation entre les variables d’animation, contenues dans un objet d’animation et leur conteneur.  
  
```  
virtual void SetParentAnimationObjects();
```  
  
### <a name="remarks"></a>Remarques  
 Il s’agit d’un programme d’assistance qui peut être utilisé pour établir une relation entre les variables d’animation, contenues dans un objet d’animation et leur conteneur. Il effectue une itération sur les variables d’animation et définit un pointeur arrière vers un objet d’animation parent pour chaque variable de l’animation. Dans l’implémentation actuelle de que la relation réelle est établie dans CAnimationBaseObject::ApplyTransitions, par conséquent, les pointeurs arrière sont sont pas définies tant que vous n’appelez pas CAnimationGroup::Animate. Le fait de connaître la relation peut être utile lorsque vous avez besoin d’une animation parent et les événements de traitement de l’objet à partir de CAnimationVariable (utilisez CAnimationVariable::GetParentAnimationObject).  
  
##  <a name="setuserdata"></a>CAnimationBaseObject::SetUserData  
 Données définies par l’utilisateur de jeux.  
  
```  
void SetUserData (DWORD dwUserData);
```  
  
### <a name="parameters"></a>Paramètres  
 `dwUserData`  
 Spécifie les données personnalisées.  
  
### <a name="remarks"></a>Remarques  
 Cette méthode permet d’associer des données personnalisées à un objet d’animation. Ces données peuvent être récupérées ultérieurement lors de l’exécution par GetUserData.  
  
## <a name="see-also"></a>Voir aussi  
 [Classes](../../mfc/reference/mfc-classes.md)

