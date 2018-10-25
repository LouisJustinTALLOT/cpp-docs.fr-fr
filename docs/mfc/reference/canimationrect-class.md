---
title: CAnimationRect, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CAnimationRect
- AFXANIMATIONCONTROLLER/CAnimationRect
- AFXANIMATIONCONTROLLER/CAnimationRect::CAnimationRect
- AFXANIMATIONCONTROLLER/CAnimationRect::AddTransition
- AFXANIMATIONCONTROLLER/CAnimationRect::GetBottom
- AFXANIMATIONCONTROLLER/CAnimationRect::GetDefaultValue
- AFXANIMATIONCONTROLLER/CAnimationRect::GetLeft
- AFXANIMATIONCONTROLLER/CAnimationRect::GetRight
- AFXANIMATIONCONTROLLER/CAnimationRect::GetTop
- AFXANIMATIONCONTROLLER/CAnimationRect::GetValue
- AFXANIMATIONCONTROLLER/CAnimationRect::SetDefaultValue
- AFXANIMATIONCONTROLLER/CAnimationRect::GetAnimationVariableList
- AFXANIMATIONCONTROLLER/CAnimationRect::m_bFixedSize
- AFXANIMATIONCONTROLLER/CAnimationRect::m_bottomValue
- AFXANIMATIONCONTROLLER/CAnimationRect::m_leftValue
- AFXANIMATIONCONTROLLER/CAnimationRect::m_rightValue
- AFXANIMATIONCONTROLLER/CAnimationRect::m_szInitial
- AFXANIMATIONCONTROLLER/CAnimationRect::m_topValue
dev_langs:
- C++
helpviewer_keywords:
- CAnimationRect [MFC], CAnimationRect
- CAnimationRect [MFC], AddTransition
- CAnimationRect [MFC], GetBottom
- CAnimationRect [MFC], GetDefaultValue
- CAnimationRect [MFC], GetLeft
- CAnimationRect [MFC], GetRight
- CAnimationRect [MFC], GetTop
- CAnimationRect [MFC], GetValue
- CAnimationRect [MFC], SetDefaultValue
- CAnimationRect [MFC], GetAnimationVariableList
- CAnimationRect [MFC], m_bFixedSize
- CAnimationRect [MFC], m_bottomValue
- CAnimationRect [MFC], m_leftValue
- CAnimationRect [MFC], m_rightValue
- CAnimationRect [MFC], m_szInitial
- CAnimationRect [MFC], m_topValue
ms.assetid: 0294156d-241e-4a57-92b2-31234fe557d6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ec22bfd2805f4af432821c4aaeb350a2cf635cfa
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50083423"
---
# <a name="canimationrect-class"></a>CAnimationRect, classe

Implémente les fonctionnalités d'un rectangle dont les côtés peuvent être animés.

## <a name="syntax"></a>Syntaxe

```
class CAnimationRect : public CAnimationBaseObject;
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CAnimationRect::CAnimationRect](#canimationrect)|Surchargé. Construit un objet d’animation rect.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CAnimationRect::AddTransition](#addtransition)|Ajoute des transitions pour les coordonnées de gauche, haut, droite et bas.|
|[CAnimationRect::GetBottom](#getbottom)|Fournit l’accès à CAnimationVariable qui représente la coordonnée inférieure.|
|[CAnimationRect::GetDefaultValue](#getdefaultvalue)|Retourne les valeurs par défaut pour les limites du rectangle.|
|[CAnimationRect::GetLeft](#getleft)|Fournit l’accès à CAnimationVariable qui représente la coordonnée gauche.|
|[CAnimationRect::GetRight](#getright)|Fournit l’accès à CAnimationVariable qui représente la coordonnée droite.|
|[CAnimationRect::GetTop](#gettop)|Fournit l’accès à CAnimationVariable qui représente la coordonnée supérieure.|
|[CAnimationRect::GetValue](#getvalue)|Retourne la valeur actuelle.|
|[CAnimationRect::SetDefaultValue](#setdefaultvalue)|Définit la valeur par défaut.|

### <a name="protected-methods"></a>Méthodes protégées

|Nom|Description|
|----------|-----------------|
|[CAnimationRect::GetAnimationVariableList](#getanimationvariablelist)|Place les variables de l’animation encapsulée dans une liste. (Substitue [CAnimationBaseObject::GetAnimationVariableList](../../mfc/reference/canimationbaseobject-class.md#getanimationvariablelist).)|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[CAnimationRect::operator RECT](#operator_rect)|Convertit un CAnimationRect Rect.|
|[CAnimationRect::operator =](#operator_eq)|Assigne rect à CAnimationRect.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CAnimationRect::m_bFixedSize](#m_bfixedsize)|Spécifie si le rectangle a une taille fixe.|

### <a name="protected-data-members"></a>Membres de données protégés

|Name|Description|
|----------|-----------------|
|[CAnimationRect::m_bottomValue](#m_bottomvalue)|Liée de la variable d’animation encapsulée qui représente la partie inférieure du rectangle de l’animation.|
|[CAnimationRect::m_leftValue](#m_leftvalue)|Liée de la variable d’animation encapsulée qui représente la gauche du rectangle d’animation.|
|[CAnimationRect::m_rightValue](#m_rightvalue)|La variable d’animation encapsulée qui représente le droit lié du rectangle de l’animation.|
|[CAnimationRect::m_szInitial](#m_szinitial)|Spécifie la taille initiale du rectangle d’animation.|
|[CAnimationRect::m_topValue](#m_topvalue)|La variable d’animation encapsulée qui représente le haut lié du rectangle de l’animation.|

## <a name="remarks"></a>Notes

La classe CAnimationRect encapsule quatre objets CAnimationVariable et peut représenter dans les applications d’un rectangle. Pour utiliser cette classe dans l’application, simplement instancier un objet de cette classe, ajoutez-le au contrôleur de l’animation à l’aide de CAnimationController::AddAnimationObject et appeler AddTransition pour chaque transition à appliquer à gauche, droite coordonnées haut et bas.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CAnimationBaseObject](../../mfc/reference/canimationbaseobject-class.md)

`CAnimationRect`

## <a name="requirements"></a>Configuration requise

**En-tête :** afxanimationcontroller.h

##  <a name="addtransition"></a>  CAnimationRect::AddTransition

Ajoute des transitions pour les coordonnées de gauche, haut, droite et bas.

```
void AddTransition(
    CBaseTransition* pLeftTransition,
    CBaseTransition* pTopTransition,
    CBaseTransition* pRightTransition,
    CBaseTransition* pBottomTransition);
```

### <a name="parameters"></a>Paramètres

*pLeftTransition*<br/>
Spécifie la transition pour le côté gauche.

*pTopTransition*<br/>
Spécifie la transition pour le côté supérieur.

*pRightTransition*<br/>
Spécifie la transition pour le côté droit.

*pBottomTransition*<br/>
Spécifie la transition pour le côté inférieur.

### <a name="remarks"></a>Notes

Appelez cette fonction pour ajouter les transitions spécifiées à la liste interne des transitions à appliquer aux variables d’animation pour chaque côté du rectangle. Lorsque vous ajoutez des transitions, elles ne sont pas appliquées immédiatement et stockées dans une liste interne. Transitions sont appliquées (ajouté à une table de montage séquentiel pour une valeur particulière) lorsque vous appelez CAnimationController::AnimateGroup. Si vous n’avez pas besoin d’appliquer une transition à un des côtés du rectangle, vous pouvez passer NULL.

##  <a name="canimationrect"></a>  CAnimationRect::CAnimationRect

Construit un objet CAnimationRect.

```
CAnimationRect();

CAnimationRect(
    const CRect& rect,
    UINT32 nGroupID,
    UINT32 nObjectID = (UINT32)-1,
    DWORD dwUserData = 0);

CAnimationRect(
    const CPoint& pt,
    const CSize& sz,
    UINT32 nGroupID,
    UINT32 nObjectID = (UINT32)-1,
    DWORD dwUserData = 0);

CAnimationRect(
    int nLeft,
    int nTop,
    int nRight,
    int nBottom,
    UINT32 nGroupID,
    UINT32 nObjectID = (UINT32)-1,
    DWORD dwUserData = 0);
```

### <a name="parameters"></a>Paramètres

*Rect*<br/>
Spécifie le rectangle par défaut.

*nGroupID*<br/>
Spécifie l’ID de groupe.

*nObjectID*<br/>
Spécifie l’ID d’objet.

*dwUserData*<br/>
Spécifie les données définies par l’utilisateur.

*pt*<br/>
Coordonnée de l’angle supérieur gauche.

*sz*<br/>
Taille du rectangle.

*nLeft*<br/>
Spécifie la coordonnée de la limite gauche.

*nTop*<br/>
Spécifie la coordonnée de la limite supérieure.

*nRight*<br/>
Spécifie la coordonnée de la limite droite.

*nBottom*<br/>
Spécifie la coordonnée de la limite inférieure.

### <a name="remarks"></a>Notes

L’objet est construit avec les valeurs par défaut pour la gauche, haut, droit et bas, ID d’objet et l’ID de groupe, qui sera défini sur 0. Ils peuvent être modifiés ultérieurement lors de l’exécution avec SetDefaultValue et SetID.

##  <a name="getanimationvariablelist"></a>  CAnimationRect::GetAnimationVariableList

Place les variables de l’animation encapsulée dans une liste.

```
virtual void GetAnimationVariableList(
    CList<CAnimationVariable*,
    CAnimationVariable*>& lst);
```

### <a name="parameters"></a>Paramètres

*lst*<br/>
La fonction retourne, contient des pointeurs aux quatre objets CAnimationVariable représentant les coordonnées du rectangle.

##  <a name="getbottom"></a>  CAnimationRect::GetBottom

Fournit l’accès à CAnimationVariable qui représente la coordonnée inférieure.

```
CAnimationVariable& GetBottom();
```

### <a name="return-value"></a>Valeur de retour

Référence à CAnimationVariable encapsulée qui représente la coordonnée inférieure.

### <a name="remarks"></a>Notes

Vous pouvez appeler cette méthode pour obtenir un accès direct à CAnimationVariable sous-jacent qui représente la coordonnée inférieure.

##  <a name="getdefaultvalue"></a>  CAnimationRect::GetDefaultValue

Retourne les valeurs par défaut pour les limites du rectangle.

```
CRect GetDefaultValue();
```

### <a name="return-value"></a>Valeur de retour

Valeur CRect contenant les valeurs par défaut pour la gauche, droite, haut et bas.

### <a name="remarks"></a>Notes

Appelez cette fonction pour récupérer la valeur par défaut, ce qui a été définie précédemment par le constructeur ou SetDefaultValue.

##  <a name="getleft"></a>  CAnimationRect::GetLeft

Fournit l’accès à CAnimationVariable qui représente la coordonnée gauche.

```
CAnimationVariable& GetLeft();
```

### <a name="return-value"></a>Valeur de retour

Référence à CAnimationVariable encapsulée qui représente la coordonnée gauche.

### <a name="remarks"></a>Notes

Vous pouvez appeler cette méthode pour obtenir un accès direct à l’objet CAnimationVariable sous-jacent qui représente la coordonnée gauche.

##  <a name="getright"></a>  CAnimationRect::GetRight

Fournit l’accès à CAnimationVariable qui représente la coordonnée droite.

```
CAnimationVariable& GetRight();
```

### <a name="return-value"></a>Valeur de retour

Référence à CAnimationVariable encapsulée qui représente la coordonnée droite.

### <a name="remarks"></a>Notes

Vous pouvez appeler cette méthode pour obtenir un accès direct à CAnimationVariable sous-jacent qui représente la coordonnée droite.

##  <a name="gettop"></a>  CAnimationRect::GetTop

Fournit l’accès à CAnimationVariable qui représente la coordonnée supérieure.

```
CAnimationVariable& GetTop();
```

### <a name="return-value"></a>Valeur de retour

Référence à CAnimationVariable encapsulée qui représente la coordonnée supérieure.

### <a name="remarks"></a>Notes

Vous pouvez appeler cette méthode pour obtenir un accès direct à l’objet CAnimationVariable sous-jacent représentant la coordonnée supérieure.

##  <a name="getvalue"></a>  CAnimationRect::GetValue

Retourne la valeur actuelle.

```
BOOL GetValue(CRect& rect);
```

### <a name="parameters"></a>Paramètres

*Rect*<br/>
Sortie. Contient la valeur actuelle lorsque cette méthode est retournée.

### <a name="return-value"></a>Valeur de retour

Valeur TRUE, si la valeur actuelle a été correctement récupérée ; Sinon, FALSE.

### <a name="remarks"></a>Notes

Appelez cette fonction pour récupérer la valeur actuelle du rectangle d’animation. Si cette méthode échoue ou un COM sous-jacente des objets de gauche, haut, droit et inférieur n’ont pas été initialisés, rect contient la valeur par défaut, ce qui a été définie précédemment dans le constructeur ou SetDefaultValue.

##  <a name="m_bfixedsize"></a>  CAnimationRect::m_bFixedSize

Spécifie si le rectangle a une taille fixe.

```
BOOL m_bFixedSize;
```

### <a name="remarks"></a>Notes

Si ce membre est true, la taille du rectangle est fixe et de droite, puis les valeurs de bas sont recalculées chaque fois que l’angle supérieur gauche est déplacé en fonction de la taille fixe. Définissez cette valeur sur TRUE pour déplacer facilement le rectangle autour de l’écran. Dans ce cas les transitions appliquées aux coordonnées de droite et bas sont ignorées. La taille est stockée en interne lorsque vous construisez l’objet et/ou appelez SetDefaultValue. Par défaut, ce membre est défini sur FALSE.

##  <a name="m_bottomvalue"></a>  CAnimationRect::m_bottomValue

Liée de la variable d’animation encapsulée qui représente la partie inférieure du rectangle de l’animation.

```
CAnimationVariable m_bottomValue;
```

##  <a name="m_leftvalue"></a>  CAnimationRect::m_leftValue

Liée de la variable d’animation encapsulée qui représente la gauche du rectangle d’animation.

```
CAnimationVariable m_leftValue;
```

##  <a name="m_rightvalue"></a>  CAnimationRect::m_rightValue

La variable d’animation encapsulée qui représente le droit lié du rectangle de l’animation.

```
CAnimationVariable m_rightValue;
```

##  <a name="m_szinitial"></a>  CAnimationRect::m_szInitial

Spécifie la taille initiale du rectangle d’animation.

```
CSize m_szInitial;
```

##  <a name="m_topvalue"></a>  CAnimationRect::m_topValue

La variable d’animation encapsulée qui représente le haut lié du rectangle de l’animation.

```
CAnimationVariable m_topValue;
```

##  <a name="operator_rect"></a>  CAnimationRect::operator RECT

Convertit un CAnimationRect Rect.

```
operator RECT();
```

### <a name="return-value"></a>Valeur de retour

Valeur actuelle du rectangle d’animation Rect.

### <a name="remarks"></a>Notes

En interne, cette fonction appelle GetValue. Si GetValue échoue pour une raison quelconque, l’objet RECT retourné contient les valeurs par défaut pour toutes les coordonnées du rectangle.

##  <a name="operator_eq"></a>  CAnimationRect::operator =

Assigne rect à CAnimationRect.

```
void operator=(const RECT& rect);
```

### <a name="parameters"></a>Paramètres

*Rect*<br/>
La nouvelle valeur du rectangle de l’animation.

### <a name="remarks"></a>Notes

Il est recommandé du pour faire avant le démarrage de l’animation, étant donné que cet opérateur appelle SetDefaultValue qui recrée les objets COM sous-jacents pour les composants de couleur s’ils ont été créés. Si vous êtes abonné aux événements (ValueChanged ou IntegerValueChanged), cet objet d’animation, vous devez réactiver ces événements.

##  <a name="setdefaultvalue"></a>  CAnimationRect::SetDefaultValue

Définit la valeur par défaut.

```
void SetDefaultValue(const CRect& rect);
```

### <a name="parameters"></a>Paramètres

*Rect*<br/>
Spécifie les nouvelles valeurs par défaut pour la gauche, haut, droite et bas.

### <a name="remarks"></a>Notes

Utilisez cette fonction pour définir une valeur par défaut pour l’objet d’animation. Cette méthode attribue des valeurs par défaut aux limites du rectangle. Il recrée également les objets COM sous-jacents s’ils ont été créés. Si vous êtes abonné aux événements (ValueChanged ou IntegerValueChanged), cet objet d’animation, vous devez réactiver ces événements.

## <a name="see-also"></a>Voir aussi

[Classes](../../mfc/reference/mfc-classes.md)
