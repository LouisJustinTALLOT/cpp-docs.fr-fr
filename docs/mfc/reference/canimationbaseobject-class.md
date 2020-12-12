---
description: 'En savoir plus sur : classe CAnimationBaseObject,'
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
ms.openlocfilehash: bc44d0e55b409f66648007eeb27fefd386640d9f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97318661"
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
|[CAnimationBaseObject, :: CAnimationBaseObject,](#canimationbaseobject)|Surchargé. Construit un objet d’animation.|
|[CAnimationBaseObject, :: ~ CAnimationBaseObject,](#_dtorcanimationbaseobject)|Destructeur. Appelé lorsqu’un objet d’animation est détruit.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CAnimationBaseObject, :: ApplyTransitions](#applytransitions)|Ajoute des transitions à la table de montage séquentiel avec une variable d’animation encapsulée.|
|[CAnimationBaseObject, :: ClearTransitions](#cleartransitions)|Supprime toutes les transitions associées.|
|[CAnimationBaseObject, :: ContainsVariable](#containsvariable)|Détermine si un objet d’animation contient une variable d’animation particulière.|
|[CAnimationBaseObject, :: CreateTransitions](#createtransitions)|Crée des transitions associées à un objet d’animation.|
|[CAnimationBaseObject, ::D etachFromController](#detachfromcontroller)|Détache un objet d’animation du contrôleur d’animation parent.|
|[CAnimationBaseObject, :: EnableIntegerValueChangedEvent](#enableintegervaluechangedevent)|Définit le gestionnaire d’événements de modification de valeur entière.|
|[CAnimationBaseObject, :: EnableValueChangedEvent](#enablevaluechangedevent)|Configure un gestionnaire d’événements de modification de valeur.|
|[CAnimationBaseObject, :: GetAutodestroyTransitions](#getautodestroytransitions)|Indique si la transition associée est détruite automatiquement.|
|[CAnimationBaseObject, :: GetGroupID](#getgroupid)|Retourne l’ID de groupe actuel.|
|[CAnimationBaseObject, :: GetObjectID](#getobjectid)|Retourne l’ID de l’objet actuel.|
|[CAnimationBaseObject, :: GetUserData](#getuserdata)|Retourne les données définies par l’utilisateur.|
|[CAnimationBaseObject, :: SetAutodestroyTransitions](#setautodestroytransitions)|Définit un indicateur pour détruire automatiquement des transitions.|
|[CAnimationBaseObject, :: SetID](#setid)|Définit de nouveaux ID.|
|[CAnimationBaseObject, :: SetUserData](#setuserdata)|Définit les données définies par l’utilisateur.|

### <a name="protected-methods"></a>Méthodes protégées

|Nom|Description|
|----------|-----------------|
|[CAnimationBaseObject, :: GetAnimationVariableList](#getanimationvariablelist)|Collecte des pointeurs vers des variables d’animation contenues.|
|[CAnimationBaseObject, :: SetParentAnimationObjects](#setparentanimationobjects)|Établit la relation entre les variables d’animation, contenues dans un objet d’animation et leur conteneur.|

### <a name="protected-data-members"></a>Membres de données protégés

|Nom|Description|
|----------|-----------------|
|[CAnimationBaseObject, :: m_bAutodestroyTransitions](#m_bautodestroytransitions)|Spécifie si les transitions connexes doivent être automatiquement détruites.|
|[CAnimationBaseObject, :: m_dwUserData](#m_dwuserdata)|Stocke les données définies par l’utilisateur.|
|[CAnimationBaseObject, :: m_nGroupID](#m_ngroupid)|Spécifie l’ID de groupe de l’objet d’animation.|
|[CAnimationBaseObject, :: m_nObjectID](#m_nobjectid)|Spécifie l’ID d’objet de l’objet d’animation.|
|[CAnimationBaseObject, :: m_pParentController](#m_pparentcontroller)|Pointeur vers le contrôleur d’animation parent.|

## <a name="remarks"></a>Notes

Cette classe implémente des méthodes de base pour tous les objets d’animation. Un objet d’animation peut représenter une valeur, un point, une taille, un rectangle ou une couleur dans une application, ainsi qu’une entité personnalisée. Les objets d’animation sont stockés dans des groupes d’animations (consultez CAnimationGroup,). Chaque groupe peut être animé séparément et peut être traité comme un analogue du Storyboard. Un objet d’animation encapsule une ou plusieurs variables d’animation (consultez CAnimationVariable), en fonction de sa représentation logique. Par exemple, CAnimationRect, contient quatre variables d’animation, une variable pour chaque côté du rectangle. Chaque classe d’objet d’animation expose une méthode AddTransition surchargée, qui doit être utilisée pour appliquer des transitions aux variables d’animation encapsulées. Un objet d’animation peut être identifié par l’ID d’objet (facultatif) et par l’ID de groupe. Un ID de groupe est nécessaire pour placer un objet d’animation dans le groupe approprié, mais si aucun ID de groupe n’est spécifié, un objet est placé dans le groupe par défaut avec l’ID 0. Si vous appelez SetID avec un GroupID différent, un objet d’animation est déplacé vers un autre groupe (un nouveau groupe est créé si nécessaire).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

`CAnimationBaseObject`

## <a name="requirements"></a>Spécifications

**En-tête :** afxanimationcontroller.h

## <a name="canimationbaseobjectcanimationbaseobject"></a><a name="_dtorcanimationbaseobject"></a> CAnimationBaseObject, :: ~ CAnimationBaseObject,

Destructeur. Appelé lorsqu’un objet d’animation est détruit.

```
virtual ~CAnimationBaseObject();
```

## <a name="canimationbaseobjectapplytransitions"></a><a name="applytransitions"></a> CAnimationBaseObject, :: ApplyTransitions

Ajoute des transitions à la table de montage séquentiel avec une variable d’animation encapsulée.

```
virtual BOOL ApplyTransitions(
    IUIAnimationStoryboard* pStoryboard,
    BOOL bDependOnKeyframes);
```

### <a name="parameters"></a>Paramètres

*pStoryboard*<br/>
Pointeur vers une table de montage séquentiel.

*bDependOnKeyframes*<br/>
Quand la valeur est FALSe, cette méthode ajoute uniquement les transitions qui ne dépendent pas des images clés.

### <a name="return-value"></a>Valeur renvoyée

TRUE si les transitions ont été ajoutées avec succès.

### <a name="remarks"></a>Notes

Ajoute des transitions connexes, qui ont été ajoutées avec AddTransition (méthodes surchargées dans les classes dérivées), à la table de montage séquentiel.

## <a name="canimationbaseobjectcanimationbaseobject"></a><a name="canimationbaseobject"></a> CAnimationBaseObject, :: CAnimationBaseObject,

Construit un objet d’animation.

```
CAnimationBaseObject();

CAnimationBaseObject(
    UINT32 nGroupID,
    UINT32 nObjectID = (UINT32)-1,
    DWORD dwUserData = 0);
```

### <a name="parameters"></a>Paramètres

*nGroupID*<br/>
Spécifie l’ID de groupe.

*nObjectID*<br/>
Spécifie l’ID de l’objet.

*dwUserData*<br/>
Données définies par l’utilisateur, qui peuvent être associées à un objet d’animation et récupérées ultérieurement au moment de l’exécution.

### <a name="remarks"></a>Notes

Construit des objets d’animation et assigne l’ID d’objet par défaut (0) et l’ID de groupe (0).

## <a name="canimationbaseobjectcleartransitions"></a><a name="cleartransitions"></a> CAnimationBaseObject, :: ClearTransitions

Supprime toutes les transitions associées.

```
virtual void ClearTransitions(BOOL bAutodestroy);
```

### <a name="parameters"></a>Paramètres

*bAutodestroy*<br/>
Spécifie s’il faut détruire des objets de transition automatiquement ou simplement les supprimer de la liste associée.

### <a name="remarks"></a>Notes

Supprime toutes les transitions associées et les détruit si bAutodestroy ou m_bAutodestroyTransitions indicateur a la valeur TRUE. Les transitions doivent être détruites automatiquement uniquement si elles ne sont pas allouées sur la pile. Si les indicateurs ci-dessus ont la valeur FALSe, les transitions sont simplement supprimées de la liste interne des transitions associées.

## <a name="canimationbaseobjectcontainsvariable"></a><a name="containsvariable"></a> CAnimationBaseObject, :: ContainsVariable

Détermine si un objet d’animation contient une variable d’animation particulière.

```
virtual BOOL ContainsVariable(IUIAnimationVariable* pVariable);
```

### <a name="parameters"></a>Paramètres

*pVariable*<br/>
Pointeur vers une variable d’animation.

### <a name="return-value"></a>Valeur renvoyée

TRUE si la variable d’animation est contenue dans l’objet d’animation ; Sinon, FALSe.

### <a name="remarks"></a>Notes

Cette méthode peut être utilisée pour déterminer si une variable d’animation spécifiée par pVariable est contenue dans un objet d’animation. Un objet d’animation, en fonction de son type, peut contenir plusieurs variables d’animation. Par exemple, CAnimationColor, contient trois variables, une pour chaque composant de couleur (rouge, vert et bleu). Quand une valeur de variable d’animation a changé, l’API d’animation Windows envoie des événements ValueChanged ou IntegerValueChanged (si elle est activée) et le paramètre de cet événement est un pointeur vers l’interface IUIAnimationVariable de la variable d’animation. Cette méthode permet d’obtenir un pointeur vers l’animation d’un pointeur vers un objet COM contenu.

## <a name="canimationbaseobjectcreatetransitions"></a><a name="createtransitions"></a> CAnimationBaseObject, :: CreateTransitions

Crée des transitions associées à un objet d’animation.

```
BOOL CreateTransitions();
```

### <a name="return-value"></a>Valeur renvoyée

TRUE si les transitions ont été créées avec succès ; Sinon, FALSe.

### <a name="remarks"></a>Notes

Effectue une boucle sur la liste des variables d’animation encapsulées dans un objet d’animation dérivé et crée des transitions associées à chaque variable d’animation.

## <a name="canimationbaseobjectdetachfromcontroller"></a><a name="detachfromcontroller"></a> CAnimationBaseObject, ::D etachFromController

Détache un objet d’animation du contrôleur d’animation parent.

```cpp
void DetachFromController();
```

### <a name="remarks"></a>Notes

Cette méthode est utilisée en interne.

## <a name="canimationbaseobjectenableintegervaluechangedevent"></a><a name="enableintegervaluechangedevent"></a> CAnimationBaseObject, :: EnableIntegerValueChangedEvent

Définit le gestionnaire d’événements de modification de valeur entière.

```
virtual void EnableIntegerValueChangedEvent(
    CAnimationController* pController,
    BOOL bEnable);
```

### <a name="parameters"></a>Paramètres

*pController*<br/>
Pointeur vers un contrôleur parent.

*bEnable*<br/>
Spécifie s’il faut activer ou désactiver l’événement de modification de valeur entière.

### <a name="remarks"></a>Notes

Si le gestionnaire d’événements de la valeur entière modifiée est activé, vous pouvez gérer cet événement dans la méthode CAnimationController :: OnAnimationIntegerValueChanged, qui doit être substituée dans une classe dérivée de CAnimationController. Cette méthode est appelée chaque fois que la valeur entière de l’animation a été modifiée.

## <a name="canimationbaseobjectenablevaluechangedevent"></a><a name="enablevaluechangedevent"></a> CAnimationBaseObject, :: EnableValueChangedEvent

Configure un gestionnaire d’événements de modification de valeur.

```
virtual void EnableValueChangedEvent(
    CAnimationController* pController,
    BOOL bEnable);
```

### <a name="parameters"></a>Paramètres

*pController*<br/>
Pointeur vers un contrôleur parent.

*bEnable*<br/>
Spécifie s’il faut activer ou désactiver l’événement de modification de valeur.

### <a name="remarks"></a>Notes

Si le gestionnaire d’événements de valeur modifiée est activé, vous pouvez gérer cet événement dans la méthode CAnimationController :: OnAnimationValueChanged, qui doit être substituée dans une classe dérivée de CAnimationController. Cette méthode est appelée chaque fois que la valeur de l’animation a changé.

## <a name="canimationbaseobjectgetanimationvariablelist"></a><a name="getanimationvariablelist"></a> CAnimationBaseObject, :: GetAnimationVariableList

Collecte des pointeurs vers des variables d’animation contenues.

```
virtual void GetAnimationVariableList(
    CList<CAnimationVariable*,
    CAnimationVariable*>& list) = 0;
```

### <a name="parameters"></a>Paramètres

*list*<br/>
Liste qui doit être remplie avec les variables d’animation contenues dans un objet d’animation.

### <a name="remarks"></a>Notes

Cette méthode virtuelle pure doit être substituée dans une classe dérivée. Un objet d’animation, en fonction de son type, contient une ou plusieurs variables d’animation. Par exemple, CAnimationPoint, contient deux variables, respectivement pour les coordonnées X et Y. La classe de base CAnimationBaseObject, implémente certaines méthodes génériques, qui agissent sur une liste de variables d’animation : ApplyTransitions, ClearTransitions, EnableValueChangedEvent, EnableIntegerValueChangedEvent. Ces méthodes appellent GetAnimationVariableList, qui est rempli dans une classe dérivée avec les variables d’animation réelles contenues dans un objet d’animation particulier, puis parcourez la liste et effectuez les actions nécessaires. Si vous créez un objet d’animation personnalisé, vous devez ajouter pour *répertorier* toutes les variables d’animation contenues dans cet objet.

## <a name="canimationbaseobjectgetautodestroytransitions"></a><a name="getautodestroytransitions"></a> CAnimationBaseObject, :: GetAutodestroyTransitions

Indique si la transition associée est détruite automatiquement.

```
BOOL GetAutodestroyTransitions() const;
```

### <a name="return-value"></a>Valeur renvoyée

Si la valeur est TRUE, les transitions associées sont détruites automatiquement ; Si la valeur est FALSe, les objets de transition doivent être désalloués en appelant l’application.

### <a name="remarks"></a>Notes

Par défaut, cet indicateur a la valeur TRUE. Définissez cet indicateur uniquement si vous avez alloué une transition sur la pile et/ou si les transitions doivent être libérées par l’application appelante.

## <a name="canimationbaseobjectgetgroupid"></a><a name="getgroupid"></a> CAnimationBaseObject, :: GetGroupID

Retourne l’ID de groupe actuel.

```
UINT32 GetGroupID() const;
```

### <a name="return-value"></a>Valeur renvoyée

ID de groupe actuel.

### <a name="remarks"></a>Notes

Utilisez cette méthode pour récupérer l’ID de groupe. 0 si l’ID de groupe n’a pas été défini explicitement dans le constructeur ou avec SetID.

## <a name="canimationbaseobjectgetobjectid"></a><a name="getobjectid"></a> CAnimationBaseObject, :: GetObjectID

Retourne l’ID de l’objet actuel.

```
UINT32 GetObjectID() const;
```

### <a name="return-value"></a>Valeur renvoyée

ID de l’objet actuel.

### <a name="remarks"></a>Notes

Utilisez cette méthode pour récupérer l’ID de l’objet. 0 si l’ID d’objet n’a pas été défini explicitement dans le constructeur ou avec SetID.

## <a name="canimationbaseobjectgetuserdata"></a><a name="getuserdata"></a> CAnimationBaseObject, :: GetUserData

Retourne les données définies par l’utilisateur.

```
DWORD GetUserData() const;
```

### <a name="return-value"></a>Valeur renvoyée

Valeur de données personnalisées.

### <a name="remarks"></a>Notes

Appelez cette méthode pour récupérer les données personnalisées au moment de l’exécution. La valeur retournée est 0 si elle n’a pas été initialisée explicitement dans le constructeur ou avec SetUserData.

## <a name="canimationbaseobjectm_bautodestroytransitions"></a><a name="m_bautodestroytransitions"></a> CAnimationBaseObject, :: m_bAutodestroyTransitions

Spécifie si les transitions connexes doivent être automatiquement détruites.

```
BOOL m_bAutodestroyTransitions;
```

## <a name="canimationbaseobjectm_dwuserdata"></a><a name="m_dwuserdata"></a> CAnimationBaseObject, :: m_dwUserData

Stocke les données définies par l’utilisateur.

```
DWORD m_dwUserData;
```

## <a name="canimationbaseobjectm_ngroupid"></a><a name="m_ngroupid"></a> CAnimationBaseObject, :: m_nGroupID

Spécifie l’ID de groupe de l’objet d’animation.

```
UINT32 m_nGroupID;
```

## <a name="canimationbaseobjectm_nobjectid"></a><a name="m_nobjectid"></a> CAnimationBaseObject, :: m_nObjectID

Spécifie l’ID d’objet de l’objet d’animation.

```
UINT32 m_nObjectID;
```

## <a name="canimationbaseobjectm_pparentcontroller"></a><a name="m_pparentcontroller"></a> CAnimationBaseObject, :: m_pParentController

Pointeur vers le contrôleur d’animation parent.

```
CAnimationController* m_pParentController;
```

## <a name="canimationbaseobjectsetautodestroytransitions"></a><a name="setautodestroytransitions"></a> CAnimationBaseObject, :: SetAutodestroyTransitions

Définit un indicateur pour détruire automatiquement des transitions.

```cpp
void SetAutodestroyTransitions(BOOL bValue);
```

### <a name="parameters"></a>Paramètres

*bValue*<br/>
Spécifie l’indicateur de destruction automatique.

### <a name="remarks"></a>Notes

Définissez cet indicateur uniquement si vous avez alloué des objets de transition à l’aide de operator new. Si, pour une raison quelconque, les objets de transition sont alloués sur la pile, l’indicateur de destruction automatique doit avoir la valeur FALSe. Par défaut, cet indicateur a la valeur TRUE.

## <a name="canimationbaseobjectsetid"></a><a name="setid"></a> CAnimationBaseObject, :: SetID

Définit de nouveaux ID.

```cpp
void SetID(
    UINT32 nObjectID,
    UINT32 nGroupID = 0);
```

### <a name="parameters"></a>Paramètres

*nObjectID*<br/>
Spécifie un nouvel ID d’objet.

*nGroupID*<br/>
Spécifie un nouvel ID de groupe.

### <a name="remarks"></a>Notes

Vous permet de modifier l’ID d’objet et l’ID de groupe. Si le nouvel ID de groupe diffère de l’ID actuel, un objet d’animation est déplacé vers un autre groupe (un nouveau groupe est créé, si nécessaire).

## <a name="canimationbaseobjectsetparentanimationobjects"></a><a name="setparentanimationobjects"></a> CAnimationBaseObject, :: SetParentAnimationObjects

Établit la relation entre les variables d’animation, contenues dans un objet d’animation et leur conteneur.

```
virtual void SetParentAnimationObjects();
```

### <a name="remarks"></a>Notes

Cette application d’assistance peut être utilisée pour établir une relation entre les variables d’animation contenues dans un objet d’animation et leur conteneur. Il effectue une boucle sur les variables d’animation et définit un pointeur arrière vers un objet d’animation parent pour chaque variable d’animation. Dans l’implémentation actuelle, la relation réelle est établie dans CAnimationBaseObject, :: ApplyTransitions, par conséquent, les pointeurs de retour ne sont pas définis tant que vous n’avez pas appelé CAnimationGroup, :: Animate. La connaissance de la relation peut être utile lorsque vous traitez des événements et que vous devez obtenir un objet d’animation parent à partir de CAnimationVariable. Utilisez CAnimationVariable :: GetParentAnimationObject.

## <a name="canimationbaseobjectsetuserdata"></a><a name="setuserdata"></a> CAnimationBaseObject, :: SetUserData

Définit les données définies par l’utilisateur.

```cpp
void SetUserData (DWORD dwUserData);
```

### <a name="parameters"></a>Paramètres

*dwUserData*<br/>
Spécifie les données personnalisées.

### <a name="remarks"></a>Notes

Utilisez cette méthode pour associer des données personnalisées à un objet d’animation. Ces données peuvent être récupérées ultérieurement lors de l’exécution par GetUserData.

## <a name="see-also"></a>Voir aussi

[Classes](../../mfc/reference/mfc-classes.md)
