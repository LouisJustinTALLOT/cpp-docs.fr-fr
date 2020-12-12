---
description: 'En savoir plus sur : classe CAnimationRect,'
title: CAnimationRect, classe
ms.date: 11/04/2016
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
ms.openlocfilehash: 590b1382992a32e0eb3d49e0ea562d10193c1990
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97207889"
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
|[CAnimationRect, :: CAnimationRect,](#canimationrect)|Surchargé. Construit un objet Rect d’animation.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CAnimationRect, :: AddTransition](#addtransition)|Ajoute des transitions pour les coordonnées gauche, haut, droite et inférieure.|
|[CAnimationRect, :: GetBottom](#getbottom)|Fournit l’accès à CAnimationVariable représentant la coordonnée inférieure.|
|[CAnimationRect, :: GetDefaultValue](#getdefaultvalue)|Retourne les valeurs par défaut pour les limites du rectangle.|
|[CAnimationRect, :: GetLeft](#getleft)|Fournit l’accès à CAnimationVariable représentant la coordonnée gauche.|
|[CAnimationRect, :: GetRight](#getright)|Fournit l’accès à CAnimationVariable représentant la coordonnée droite.|
|[CAnimationRect, :: GetTop](#gettop)|Fournit l’accès à CAnimationVariable qui représente la coordonnée supérieure.|
|[CAnimationRect, :: GetValue](#getvalue)|Retourne la valeur actuelle.|
|[CAnimationRect, :: SetDefaultValue](#setdefaultvalue)|Définit la valeur par défaut.|

### <a name="protected-methods"></a>Méthodes protégées

|Nom|Description|
|----------|-----------------|
|[CAnimationRect, :: GetAnimationVariableList](#getanimationvariablelist)|Place les variables d’animation encapsulées dans une liste. (Substitue [CAnimationBaseObject, :: GetAnimationVariableList](../../mfc/reference/canimationbaseobject-class.md#getanimationvariablelist).)|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[CAnimationRect, :: Operator RECT](#operator_rect)|Convertit un CAnimationRect, en RECT.|
|[CAnimationRect, :: Operator =](#operator_eq)|Attribue Rect à CAnimationRect,.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CAnimationRect, :: m_bFixedSize](#m_bfixedsize)|Spécifie si le rectangle a une taille fixe.|

### <a name="protected-data-members"></a>Membres de données protégés

|Nom|Description|
|----------|-----------------|
|[CAnimationRect, :: m_bottomValue](#m_bottomvalue)|Variable d’animation encapsulée qui représente la limite inférieure du rectangle d’animation.|
|[CAnimationRect, :: m_leftValue](#m_leftvalue)|Variable d’animation encapsulée qui représente la limite gauche du rectangle d’animation.|
|[CAnimationRect, :: m_rightValue](#m_rightvalue)|Variable d’animation encapsulée qui représente la limite droite du rectangle d’animation.|
|[CAnimationRect, :: m_szInitial](#m_szinitial)|Spécifie la taille initiale du rectangle d’animation.|
|[CAnimationRect, :: m_topValue](#m_topvalue)|Variable d’animation encapsulée qui représente la limite supérieure du rectangle d’animation.|

## <a name="remarks"></a>Notes

La classe CAnimationRect, encapsule quatre objets CAnimationVariable et peut représenter dans les applications un rectangle. Pour utiliser cette classe dans l’application, il vous suffit d’instancier un objet de cette classe, de l’ajouter au contrôleur d’animation à l’aide de CAnimationController :: AddAnimationObject et d’appeler AddTransition pour chaque transition à appliquer aux coordonnées gauche, droite et inférieure.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CAnimationBaseObject,](../../mfc/reference/canimationbaseobject-class.md)

`CAnimationRect`

## <a name="requirements"></a>Spécifications

**En-tête :** afxanimationcontroller.h

## <a name="canimationrectaddtransition"></a><a name="addtransition"></a> CAnimationRect, :: AddTransition

Ajoute des transitions pour les coordonnées gauche, haut, droite et inférieure.

```cpp
void AddTransition(
    CBaseTransition* pLeftTransition,
    CBaseTransition* pTopTransition,
    CBaseTransition* pRightTransition,
    CBaseTransition* pBottomTransition);
```

### <a name="parameters"></a>Paramètres

*pLeftTransition*<br/>
Spécifie la transition du côté gauche.

*pTopTransition*<br/>
Spécifie la transition pour le côté supérieur.

*pRightTransition*<br/>
Spécifie la transition du côté droit.

*pBottomTransition*<br/>
Spécifie la transition pour le côté inférieur.

### <a name="remarks"></a>Notes

Appelez cette fonction pour ajouter les transitions spécifiées à la liste interne des transitions à appliquer aux variables d’animation pour chaque côté du rectangle. Lorsque vous ajoutez des transitions, elles ne sont pas appliquées immédiatement et stockées dans une liste interne. Les transitions sont appliquées (ajoutées à une table de montage séquentiel pour une valeur particulière) quand vous appelez CAnimationController :: AnimateGroup. Si vous n’avez pas besoin d’appliquer une transition à l’un des côtés du rectangle, vous pouvez passer la valeur NULL.

## <a name="canimationrectcanimationrect"></a><a name="canimationrect"></a> CAnimationRect, :: CAnimationRect,

Construit un objet CAnimationRect,.

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

*rectangulaire*<br/>
Spécifie le rectangle par défaut.

*nGroupID*<br/>
Spécifie l’ID de groupe.

*nObjectID*<br/>
Spécifie l’ID de l’objet.

*dwUserData*<br/>
Spécifie les données définies par l’utilisateur.

*pt*<br/>
Coordonnée de l’angle supérieur gauche.

*SZ*<br/>
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

L’objet est construit avec les valeurs par défaut de gauche, haut, droit et bas, ID d’objet et ID de groupe, qui seront définis sur 0. Vous pouvez les modifier ultérieurement au moment de l’exécution en utilisant SetDefaultValue et SetID.

## <a name="canimationrectgetanimationvariablelist"></a><a name="getanimationvariablelist"></a> CAnimationRect, :: GetAnimationVariableList

Place les variables d’animation encapsulées dans une liste.

```
virtual void GetAnimationVariableList(
    CList<CAnimationVariable*,
    CAnimationVariable*>& lst);
```

### <a name="parameters"></a>Paramètres

*LST*<br/>
Quand la fonction retourne, elle contient des pointeurs vers quatre objets CAnimationVariable représentant les coordonnées du rectangle.

## <a name="canimationrectgetbottom"></a><a name="getbottom"></a> CAnimationRect, :: GetBottom

Fournit l’accès à CAnimationVariable représentant la coordonnée inférieure.

```
CAnimationVariable& GetBottom();
```

### <a name="return-value"></a>Valeur renvoyée

Référence à l’CAnimationVariable encapsulé représentant la coordonnée inférieure.

### <a name="remarks"></a>Notes

Vous pouvez appeler cette méthode pour bénéficier d’un accès direct à l’CAnimationVariable sous-jacent représentant la coordonnée inférieure.

## <a name="canimationrectgetdefaultvalue"></a><a name="getdefaultvalue"></a> CAnimationRect, :: GetDefaultValue

Retourne les valeurs par défaut pour les limites du rectangle.

```
CRect GetDefaultValue();
```

### <a name="return-value"></a>Valeur renvoyée

Valeur CRect contenant les valeurs par défaut à gauche, à droite, en haut et en bas.

### <a name="remarks"></a>Notes

Appelez cette fonction pour récupérer la valeur par défaut, qui a été précédemment définie par le constructeur ou SetDefaultValue.

## <a name="canimationrectgetleft"></a><a name="getleft"></a> CAnimationRect, :: GetLeft

Fournit l’accès à CAnimationVariable représentant la coordonnée gauche.

```
CAnimationVariable& GetLeft();
```

### <a name="return-value"></a>Valeur renvoyée

Référence à l’CAnimationVariable encapsulé représentant la coordonnée gauche.

### <a name="remarks"></a>Notes

Vous pouvez appeler cette méthode pour bénéficier d’un accès direct à l’CAnimationVariable sous-jacent représentant la coordonnée gauche.

## <a name="canimationrectgetright"></a><a name="getright"></a> CAnimationRect, :: GetRight

Fournit l’accès à CAnimationVariable représentant la coordonnée droite.

```
CAnimationVariable& GetRight();
```

### <a name="return-value"></a>Valeur renvoyée

Référence à l’CAnimationVariable encapsulé représentant la coordonnée droite.

### <a name="remarks"></a>Notes

Vous pouvez appeler cette méthode pour bénéficier d’un accès direct à l’CAnimationVariable sous-jacent représentant la coordonnée droite.

## <a name="canimationrectgettop"></a><a name="gettop"></a> CAnimationRect, :: GetTop

Fournit l’accès à CAnimationVariable qui représente la coordonnée supérieure.

```
CAnimationVariable& GetTop();
```

### <a name="return-value"></a>Valeur renvoyée

Référence à l’CAnimationVariable encapsulé représentant la coordonnée supérieure.

### <a name="remarks"></a>Notes

Vous pouvez appeler cette méthode pour accéder directement à l’CAnimationVariable sous-jacent qui représente la coordonnée supérieure.

## <a name="canimationrectgetvalue"></a><a name="getvalue"></a> CAnimationRect, :: GetValue

Retourne la valeur actuelle.

```
BOOL GetValue(CRect& rect);
```

### <a name="parameters"></a>Paramètres

*rectangulaire*<br/>
Sortie : Contient la valeur actuelle lorsque cette méthode est retournée.

### <a name="return-value"></a>Valeur renvoyée

TRUE si la valeur actuelle a été récupérée avec succès ; Sinon, FALSe.

### <a name="remarks"></a>Notes

Appelez cette fonction pour récupérer la valeur actuelle du rectangle d’animation. Si cette méthode échoue ou si les objets COM sous-jacents pour gauche, haut, droit et bas n’ont pas été initialisés, Rect contient la valeur par défaut, qui a été précédemment définie dans le constructeur ou par SetDefaultValue.

## <a name="canimationrectm_bfixedsize"></a><a name="m_bfixedsize"></a> CAnimationRect, :: m_bFixedSize

Spécifie si le rectangle a une taille fixe.

```
BOOL m_bFixedSize;
```

### <a name="remarks"></a>Notes

Si ce membre a la valeur true, la taille du rectangle est fixe et les valeurs à droite et en bas sont recalculées chaque fois que l’angle supérieur gauche est déplacé en fonction de la taille fixe. Définissez cette valeur sur TRUE pour déplacer facilement le rectangle autour de l’écran. Dans ce cas, les transitions appliquées aux coordonnées droite et inférieure sont ignorées. La taille est stockée en interne quand vous construisez l’objet et/ou appelez SetDefaultValue. Par défaut, ce membre est défini sur FALSe.

## <a name="canimationrectm_bottomvalue"></a><a name="m_bottomvalue"></a> CAnimationRect, :: m_bottomValue

Variable d’animation encapsulée qui représente la limite inférieure du rectangle d’animation.

```
CAnimationVariable m_bottomValue;
```

## <a name="canimationrectm_leftvalue"></a><a name="m_leftvalue"></a> CAnimationRect, :: m_leftValue

Variable d’animation encapsulée qui représente la limite gauche du rectangle d’animation.

```
CAnimationVariable m_leftValue;
```

## <a name="canimationrectm_rightvalue"></a><a name="m_rightvalue"></a> CAnimationRect, :: m_rightValue

Variable d’animation encapsulée qui représente la limite droite du rectangle d’animation.

```
CAnimationVariable m_rightValue;
```

## <a name="canimationrectm_szinitial"></a><a name="m_szinitial"></a> CAnimationRect, :: m_szInitial

Spécifie la taille initiale du rectangle d’animation.

```
CSize m_szInitial;
```

## <a name="canimationrectm_topvalue"></a><a name="m_topvalue"></a> CAnimationRect, :: m_topValue

Variable d’animation encapsulée qui représente la limite supérieure du rectangle d’animation.

```
CAnimationVariable m_topValue;
```

## <a name="canimationrectoperator-rect"></a><a name="operator_rect"></a> CAnimationRect, :: Operator RECT

Convertit un CAnimationRect, en RECT.

```
operator RECT();
```

### <a name="return-value"></a>Valeur renvoyée

Valeur actuelle du rectangle d’animation comme RECT.

### <a name="remarks"></a>Notes

Cette fonction appelle GetValue en interne. Si GetValue pour une raison quelconque échoue, le RECT retourné contient des valeurs par défaut pour toutes les coordonnées de rectangle.

## <a name="canimationrectoperator"></a><a name="operator_eq"></a> CAnimationRect, :: Operator =

Attribue Rect à CAnimationRect,.

```cpp
void operator=(const RECT& rect);
```

### <a name="parameters"></a>Paramètres

*rectangulaire*<br/>
Nouvelle valeur du rectangle d’animation.

### <a name="remarks"></a>Notes

Il est recommandé de le faire avant le démarrage de l’animation, car cet opérateur appelle SetDefaultValue, qui recrée les objets COM sous-jacents pour les composants de couleur s’ils ont été créés. Si vous avez souscrit cet objet d’animation à des événements (ValueChanged ou IntegerValueChanged), vous devez réactiver ces événements.

## <a name="canimationrectsetdefaultvalue"></a><a name="setdefaultvalue"></a> CAnimationRect, :: SetDefaultValue

Définit la valeur par défaut.

```cpp
void SetDefaultValue(const CRect& rect);
```

### <a name="parameters"></a>Paramètres

*rectangulaire*<br/>
Spécifie de nouvelles valeurs par défaut pour gauche, haut, droit et bas.

### <a name="remarks"></a>Notes

Utilisez cette fonction pour définir une valeur par défaut pour l’objet d’animation. Cette méthode assigne des valeurs par défaut aux limites du rectangle. Il recrée également les objets COM sous-jacents s’ils ont été créés. Si vous avez souscrit cet objet d’animation à des événements (ValueChanged ou IntegerValueChanged), vous devez réactiver ces événements.

## <a name="see-also"></a>Voir aussi

[Classes](../../mfc/reference/mfc-classes.md)
