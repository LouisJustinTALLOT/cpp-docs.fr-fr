---
title: CAnimationBaseObject, classe
ms.date: 03/27/2019
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
ms.openlocfilehash: 1874ddfdd26b8dd371e32f7e68ea8f668c47d8e1
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "81750221"
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
|[CAnimationBaseObject::CAnimationBaseObject](#_dtorcanimationbaseobject)|Destructeur. Appelé quand un objet d’animation est détruit.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CAnimationBaseObject::ApplyTransitions](#applytransitions)|Ajoute des transitions au storyboard avec variable d’animation encapsulée.|
|[CAnimationBaseObject::ClearTransitions](#cleartransitions)|Supprime toutes les transitions connexes.|
|[CAnimationBaseObject::ContainsVariable](#containsvariable)|Détermine si un objet d’animation contient une variable d’animation particulière.|
|[CAnimationBaseObject::CreateTransitions](#createtransitions)|Crée des transitions associées à un objet d’animation.|
|[CAnimationBaseObject::Dentrétroir](#detachfromcontroller)|Détache un objet d’animation du contrôleur d’animation parent.|
|[CAnimationBaseObject::EnableIntegerValueChangedEvent](#enableintegervaluechangedevent)|Met en place integer Value Changed gestionnaire d’événements.|
|[CAnimationBaseObject::EnableValueChangedEvent](#enablevaluechangedevent)|Définit le gestionnaire d’événements Value Changed.|
|[CAnimationBaseObject::GetAutodestroyTransitions](#getautodestroytransitions)|Indique si la transition connexe est détruite automatiquement.|
|[CAnimationBaseObject::GetGroupID](#getgroupid)|Retourne l’ID de groupe actuel.|
|[CAnimationBaseObject::GetObjectID](#getobjectid)|Retourne l’ID d’objet actuel.|
|[CAnimationBaseObject::GetUserData](#getuserdata)|Retourne les données définies par l’utilisateur.|
|[CAnimationBaseObject::SetAutodestroyTransitions](#setautodestroytransitions)|Définit un drapeau pour détruire automatiquement les transitions.|
|[CAnimationBaseObject::SetID](#setid)|Définit de nouvelles adresses d’adresses d’ensemble.|
|[CAnimationBaseObject::SetUserData](#setuserdata)|Définit les données définies par l’utilisateur.|

### <a name="protected-methods"></a>Méthodes protégées

|Nom|Description|
|----------|-----------------|
|[CAnimationBaseObject::GetAnimationVariableList](#getanimationvariablelist)|Collecte des indications pour contenir les variables d’animation.|
|[CAnimationBaseObject::SetParentAnimationObjects](#setparentanimationobjects)|Établit la relation entre les variables d’animation, contenues dans un objet d’animation, et leur conteneur.|

### <a name="protected-data-members"></a>Membres de données protégés

|Nom|Description|
|----------|-----------------|
|[CAnimationBaseObject::m_bAutodestroyTransitions](#m_bautodestroytransitions)|Précise si les transitions connexes doivent être automatiquement détruites.|
|[CAnimationBaseObject::m_dwUserData](#m_dwuserdata)|Stocke les données définies par les utilisateurs.|
|[CAnimationBaseObject::m_nGroupID](#m_ngroupid)|Spécifie l’ID de groupe de l’objet d’animation.|
|[CAnimationBaseObject::m_nObjectID](#m_nobjectid)|Spécifie l’id d’objet de l’objet d’animation.|
|[CAnimationBaseObject::m_pParentController](#m_pparentcontroller)|Un pointeur pour le contrôleur d’animation parent.|

## <a name="remarks"></a>Notes

Cette classe met en œuvre des méthodes de base pour tous les objets d’animation. Un objet d’animation peut représenter une valeur, un point, une taille, un rectangle ou une couleur dans une application, ainsi que n’importe quelle entité personnalisée. Les objets d’animation sont stockés dans des groupes d’animation (voir CAnimationGroup). Chaque groupe peut être animé séparément et peut être traité comme un analogue de storyboard. Un objet d’animation résume une ou plusieurs variables d’animation (voir CAnimationVariable), en fonction de sa représentation logique. Par exemple, CAnimationRect contient quatre variables d’animation - une variable pour chaque côté du rectangle. Chaque classe d’objets d’animation expose la méthode AddTransition surchargée, qui doit être utilisée pour appliquer des transitions vers des variables d’animation encapsulées. Un objet d’animation peut être identifié par Object ID (optionnellement) et par ID de groupe. Une pièce d’identité de groupe est nécessaire pour placer un objet d’animation pour corriger le groupe, mais si un ID de groupe n’est pas spécifié, un objet est placé dans le groupe par défaut avec ID 0. Si vous appelez SetID avec différents GroupID, un objet d’animation sera déplacé vers un autre groupe (un nouveau groupe est créé si nécessaire).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

`CAnimationBaseObject`

## <a name="requirements"></a>Spécifications

**En-tête :** afxanimationcontroller.h

## <a name="canimationbaseobjectcanimationbaseobject"></a><a name="_dtorcanimationbaseobject"></a>CAnimationBaseObject::CAnimationBaseObject

Destructeur. Appelé quand un objet d’animation est détruit.

```
virtual ~CAnimationBaseObject();
```

## <a name="canimationbaseobjectapplytransitions"></a><a name="applytransitions"></a>CAnimationBaseObject::ApplyTransitions

Ajoute des transitions au storyboard avec variable d’animation encapsulée.

```
virtual BOOL ApplyTransitions(
    IUIAnimationStoryboard* pStoryboard,
    BOOL bDependOnKeyframes);
```

### <a name="parameters"></a>Paramètres

*pStoryboard (en)*<br/>
Un pointeur à un storyboard.

*bDependOnKeyframes*<br/>
Lorsque FALSE, cette méthode ajoute seulement les transitions qui ne dépendent pas des cadres clés.

### <a name="return-value"></a>Valeur de retour

VRAI si les transitions ont été ajoutées avec succès.

### <a name="remarks"></a>Notes

Ajoute des transitions connexes, qui ont été ajoutées avec AddTransition (méthodes surchargées dans les classes dérivées), au storyboard.

## <a name="canimationbaseobjectcanimationbaseobject"></a><a name="canimationbaseobject"></a>CAnimationBaseObject::CAnimationBaseObject

Construit un objet d’animation.

```
CAnimationBaseObject();

CAnimationBaseObject(
    UINT32 nGroupID,
    UINT32 nObjectID = (UINT32)-1,
    DWORD dwUserData = 0);
```

### <a name="parameters"></a>Paramètres

*nGroupID (en anglais)*<br/>
Spécifie l’ID du groupe.

*nObjectID (nObjectID)*<br/>
Spécifie l’id d’objet.

*dwUserData*<br/>
Données définies par l’utilisateur, qui peuvent être associées à l’objet d’animation et récupérées plus tard au moment de l’exécution.

### <a name="remarks"></a>Notes

Construit un objet d’animation et assigne l’id d’objet par défaut (0) et l’ID de groupe (0).

## <a name="canimationbaseobjectcleartransitions"></a><a name="cleartransitions"></a>CAnimationBaseObject::ClearTransitions

Supprime toutes les transitions connexes.

```
virtual void ClearTransitions(BOOL bAutodestroy);
```

### <a name="parameters"></a>Paramètres

*bAutodestroy*<br/>
Précise s’il faut détruire automatiquement des objets de transition, ou simplement les supprimer de la liste connexe.

### <a name="remarks"></a>Notes

Supprime toutes les transitions connexes et les détruit si bAutodestroy ou m_bAutodestroyTransitions drapeau est VRAI. Les transitions ne doivent être détruites automatiquement que si elles ne sont pas réparties sur la pile. Si les drapeaux ci-dessus sont FALSE, les transitions sont simplement supprimées de la liste interne des transitions connexes.

## <a name="canimationbaseobjectcontainsvariable"></a><a name="containsvariable"></a>CAnimationBaseObject::ContainsVariable

Détermine si un objet d’animation contient une variable d’animation particulière.

```
virtual BOOL ContainsVariable(IUIAnimationVariable* pVariable);
```

### <a name="parameters"></a>Paramètres

*pVariable*<br/>
Un pointeur à la variable d’animation.

### <a name="return-value"></a>Valeur de retour

VRAI si la variable d’animation est contenue dans l’objet d’animation; autrement FALSE.

### <a name="remarks"></a>Notes

Cette méthode peut être utilisée pour déterminer si une variable d’animation spécifiée par pVariable est contenue dans un objet d’animation. Un objet d’animation, selon son type, peut contenir plusieurs variables d’animation. Par exemple, CAnimationColor contient trois variables, une pour chaque composant de couleur (rouge, vert et bleu). Lorsqu’une variable d’animation a changé, Windows Animation API envoie des événements ValueChanged ou IntegerValueChanged (si activé), et le paramètre de cet événement est un pointeur pour interfacer IUIAnimationVariable de variable d’animation. Cette méthode permet d’obtenir un pointeur à l’animation à partir d’un pointeur à contenu objet COM.

## <a name="canimationbaseobjectcreatetransitions"></a><a name="createtransitions"></a>CAnimationBaseObject::CreateTransitions

Crée des transitions associées à un objet d’animation.

```
BOOL CreateTransitions();
```

### <a name="return-value"></a>Valeur de retour

VRAI si les transitions ont été créées avec succès; autrement FALSE.

### <a name="remarks"></a>Notes

Boucles sur la liste des variables d’animation encapsulées dans un objet d’animation dérivé et crée des transitions associées à chaque variable d’animation.

## <a name="canimationbaseobjectdetachfromcontroller"></a><a name="detachfromcontroller"></a>CAnimationBaseObject::Dentrétroir

Détache un objet d’animation du contrôleur d’animation parent.

```cpp
void DetachFromController();
```

### <a name="remarks"></a>Notes

Cette méthode est utilisée en interne.

## <a name="canimationbaseobjectenableintegervaluechangedevent"></a><a name="enableintegervaluechangedevent"></a>CAnimationBaseObject::EnableIntegerValueChangedEvent

Met en place integer Value Changed gestionnaire d’événements.

```
virtual void EnableIntegerValueChangedEvent(
    CAnimationController* pController,
    BOOL bEnable);
```

### <a name="parameters"></a>Paramètres

*pController*<br/>
Un pointeur pour un contrôleur parent.

*bEnable*<br/>
Précise s’il faut activer ou désactiver l’événement Integer Value Changed.

### <a name="remarks"></a>Notes

Si le gestionnaire d’événements Integer Value Changed est activé, vous pouvez gérer cet événement dans CAnimationController::OnAnimationIntegerValueLa méthode, qui devrait être remplacée dans une classe dérivée de CAnimationController. Cette méthode est appelée chaque fois que la valeur de l’intégration d’animation a changé.

## <a name="canimationbaseobjectenablevaluechangedevent"></a><a name="enablevaluechangedevent"></a>CAnimationBaseObject::EnableValueChangedEvent

Définit le gestionnaire d’événements Value Changed.

```
virtual void EnableValueChangedEvent(
    CAnimationController* pController,
    BOOL bEnable);
```

### <a name="parameters"></a>Paramètres

*pController*<br/>
Un pointeur pour un contrôleur parent.

*bEnable*<br/>
Précise s’il faut activer ou désactiver l’événement Value Changed.

### <a name="remarks"></a>Notes

Si le gestionnaire d’événements Value Changed est activé, vous pouvez gérer cet événement dans CAnimationController::OnAnimationValueLa méthode, qui doit être remplacée dans une classe dérivée de CAnimationController. Cette méthode est appelée chaque fois que la valeur d’animation a changé.

## <a name="canimationbaseobjectgetanimationvariablelist"></a><a name="getanimationvariablelist"></a>CAnimationBaseObject::GetAnimationVariableList

Collecte des indications pour contenir les variables d’animation.

```
virtual void GetAnimationVariableList(
    CList<CAnimationVariable*,
    CAnimationVariable*>& list) = 0;
```

### <a name="parameters"></a>Paramètres

*list*<br/>
Une liste qui doit être remplie de variables d’animation contenues dans un objet d’animation.

### <a name="remarks"></a>Notes

Cette méthode virtuelle pure doit être remplacée dans une classe dérivée. Un objet d’animation, selon son type, contient une ou plusieurs variables d’animation. Par exemple, CAnimationPoint contient deux variables, pour les coordonnées X et Y respectivement. La classe de base CAnimationBaseObject met en œuvre certaines méthodes génériques, qui agissent sur une liste de variables d’animation: ApplyTransitions, ClearTransitions, EnableValueChangedEvent, EnableIntegerValueChangedEvent. Ces méthodes appellent GetAnimationVariableList, qui est rempli dans une classe dérivée avec des variables d’animation réelles contenues dans un objet d’animation particulier, puis boucle sur la liste et effectuer les actions nécessaires. Si vous créez un objet d’animation personnalisé, vous devez ajouter à *la liste* toutes les variables d’animation contenues dans cet objet.

## <a name="canimationbaseobjectgetautodestroytransitions"></a><a name="getautodestroytransitions"></a>CAnimationBaseObject::GetAutodestroyTransitions

Indique si la transition connexe est détruite automatiquement.

```
BOOL GetAutodestroyTransitions() const;
```

### <a name="return-value"></a>Valeur de retour

Si VRAI, les transitions connexes sont automatiquement détruites; si FALSE, les objets de transition doivent être deallocated par application d’appel.

### <a name="remarks"></a>Notes

Par défaut, ce drapeau est VRAI. Définissez ce drapeau uniquement si vous avez attribué la transition sur la pile et/ou que les transitions doivent être réglées par l’application d’appel.

## <a name="canimationbaseobjectgetgroupid"></a><a name="getgroupid"></a>CAnimationBaseObject::GetGroupID

Retourne l’ID de groupe actuel.

```
UINT32 GetGroupID() const;
```

### <a name="return-value"></a>Valeur de retour

ID de groupe actuel.

### <a name="remarks"></a>Notes

Utilisez cette méthode pour récupérer l’ID du groupe. C’est 0 si l’ID de groupe n’a pas été défini explicitement en constructeur ou avec SetID.

## <a name="canimationbaseobjectgetobjectid"></a><a name="getobjectid"></a>CAnimationBaseObject::GetObjectID

Retourne l’ID d’objet actuel.

```
UINT32 GetObjectID() const;
```

### <a name="return-value"></a>Valeur de retour

ID d’objet actuel.

### <a name="remarks"></a>Notes

Utilisez cette méthode pour récupérer l’identifiant d’objet. C’est 0 si l’ID d’objet n’a pas été défini explicitement dans le constructeur ou avec SetID.

## <a name="canimationbaseobjectgetuserdata"></a><a name="getuserdata"></a>CAnimationBaseObject::GetUserData

Retourne les données définies par l’utilisateur.

```
DWORD GetUserData() const;
```

### <a name="return-value"></a>Valeur de retour

Une valeur de données personnalisées.

### <a name="remarks"></a>Notes

Appelez cette méthode pour récupérer les données personnalisées au moment de l’exécution. La valeur retournée sera de 0 si elle n’a pas été explicitement paraphé dans le constructeur ou avec SetUserData.

## <a name="canimationbaseobjectm_bautodestroytransitions"></a><a name="m_bautodestroytransitions"></a>CAnimationBaseObject::m_bAutodestroyTransitions

Précise si les transitions connexes doivent être automatiquement détruites.

```
BOOL m_bAutodestroyTransitions;
```

## <a name="canimationbaseobjectm_dwuserdata"></a><a name="m_dwuserdata"></a>CAnimationBaseObject::m_dwUserData

Stocke les données définies par les utilisateurs.

```
DWORD m_dwUserData;
```

## <a name="canimationbaseobjectm_ngroupid"></a><a name="m_ngroupid"></a>CAnimationBaseObject::m_nGroupID

Spécifie l’ID de groupe de l’objet d’animation.

```
UINT32 m_nGroupID;
```

## <a name="canimationbaseobjectm_nobjectid"></a><a name="m_nobjectid"></a>CAnimationBaseObject::m_nObjectID

Spécifie l’id d’objet de l’objet d’animation.

```
UINT32 m_nObjectID;
```

## <a name="canimationbaseobjectm_pparentcontroller"></a><a name="m_pparentcontroller"></a>CAnimationBaseObject::m_pParentController

Un pointeur pour le contrôleur d’animation parent.

```
CAnimationController* m_pParentController;
```

## <a name="canimationbaseobjectsetautodestroytransitions"></a><a name="setautodestroytransitions"></a>CAnimationBaseObject::SetAutodestroyTransitions

Définit un drapeau pour détruire automatiquement les transitions.

```cpp
void SetAutodestroyTransitions(BOOL bValue);
```

### <a name="parameters"></a>Paramètres

*bValue (en)*<br/>
Spécifie le drapeau de destruction automatique.

### <a name="remarks"></a>Notes

Réglez ce drapeau uniquement si vous avez attribué des objets de transition à l’aide de l’opérateur nouveau. Si, pour une raison quelconque, des objets de transition sont attribués sur la pile, le drapeau de destruction automatique doit être FALSE. Par défaut, ce drapeau est VRAI.

## <a name="canimationbaseobjectsetid"></a><a name="setid"></a>CAnimationBaseObject::SetID

Définit de nouvelles adresses d’adresses d’ensemble.

```cpp
void SetID(
    UINT32 nObjectID,
    UINT32 nGroupID = 0);
```

### <a name="parameters"></a>Paramètres

*nObjectID (nObjectID)*<br/>
Spécifie la nouvelle pièce d’identité d’objet.

*nGroupID (en anglais)*<br/>
Spécifie la nouvelle pièce d’identité du groupe.

### <a name="remarks"></a>Notes

Vous permet de modifier l’identifiant d’objet et l’ID de groupe. Si le nouvel ID de groupe diffère de l’ID actuel, un objet d’animation est déplacé vers un autre groupe (un nouveau groupe sera créé, si nécessaire).

## <a name="canimationbaseobjectsetparentanimationobjects"></a><a name="setparentanimationobjects"></a>CAnimationBaseObject::SetParentAnimationObjects

Établit la relation entre les variables d’animation, contenues dans un objet d’animation, et leur conteneur.

```
virtual void SetParentAnimationObjects();
```

### <a name="remarks"></a>Notes

Cette aide peut être utilisée pour établir une relation entre les variables d’animation contenues dans un objet d’animation, et leur conteneur. Il boucle sur les variables d’animation et définit un point arrière à un objet d’animation parent à chaque variable d’animation. Dans la mise en œuvre actuelle, la relation réelle est établie dans CAnimationBaseObject::ApplyTransitions, donc les pointeurs arrière ne sont pas fixés jusqu’à ce que vous appelez CAnimationGroup::Animate. Connaître la relation peut être utile lorsque vous traitez des événements et ont besoin d’obtenir un objet d’animation parent de CAnimationVariable. Utilisez CAnimationVariable::GetParentAnimationObject.

## <a name="canimationbaseobjectsetuserdata"></a><a name="setuserdata"></a>CAnimationBaseObject::SetUserData

Définit les données définies par l’utilisateur.

```cpp
void SetUserData (DWORD dwUserData);
```

### <a name="parameters"></a>Paramètres

*dwUserData*<br/>
Spécifie les données personnalisées.

### <a name="remarks"></a>Notes

Utilisez cette méthode pour associer une donnée personnalisée à un objet d’animation. Ces données peuvent être récupérées plus tard à l’heure d’exécution par GetUserData.

## <a name="see-also"></a>Voir aussi

[Classes](../../mfc/reference/mfc-classes.md)
