---
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
ms.openlocfilehash: 4ffd1254efd3283a4c5641092aefec8eec0ac22a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373338"
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
|[CAnimationRect::CAnimationRect](#canimationrect)|Surchargé. Construit un objet rect d’animation.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CAnimationRect::AddTransition](#addtransition)|Ajoute des transitions pour les coordonnées gauche, supérieure, droite et inférieure.|
|[CAnimationRect::GetBottom](#getbottom)|Donne accès à CAnimationVariable représentant la coordination inférieure.|
|[CAnimationRect::GetDefaultValue](#getdefaultvalue)|Retourne les valeurs par défaut pour les limites du rectangle.|
|[CAnimationRect::GetLeft](#getleft)|Donne accès à CAnimationVariable représentant la coordination gauche.|
|[CAnimationRect::GetRight](#getright)|Donne accès à CAnimationVariable représentant la bonne coordination.|
|[CAnimationRect::GetTop](#gettop)|Donne accès à CAnimationVariable représentant la plus haute coordination.|
|[CAnimationRect::GetValue](#getvalue)|Retourne la valeur actuelle.|
|[CAnimationRect::SetDefaultValue](#setdefaultvalue)|Définit la valeur par défaut.|

### <a name="protected-methods"></a>Méthodes protégées

|Nom|Description|
|----------|-----------------|
|[CAnimationRect::GetAnimationVariableList](#getanimationvariablelist)|Place les variables d’animation encapsulées dans une liste. (Overrides [CAnimationBaseObject::GetAnimationVariableList](../../mfc/reference/canimationbaseobject-class.md#getanimationvariablelist).)|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[CAnimationRect::opérateur RECT](#operator_rect)|Convertit un CAnimationRect en RECT.|
|[CAnimationRect::opérateur](#operator_eq)|Assigne rect à CAnimationRect.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CAnimationRect::m_bFixedSize](#m_bfixedsize)|Précise si le rectangle a la taille fixe.|

### <a name="protected-data-members"></a>Membres de données protégés

|Nom|Description|
|----------|-----------------|
|[CAnimationRect::m_bottomValue](#m_bottomvalue)|La variable d’animation encapsulée qui représente bottom lié de rectangle d’animation.|
|[CAnimationRect::m_leftValue](#m_leftvalue)|La variable d’animation encapsulée qui représente à gauche lié de rectangle d’animation.|
|[CAnimationRect::m_rightValue](#m_rightvalue)|La variable d’animation encapsulée qui représente la limite droite du rectangle d’animation.|
|[CAnimationRect::m_szInitial](#m_szinitial)|Spécifie la taille initiale du rectangle d’animation.|
|[CAnimationRect::m_topValue](#m_topvalue)|La variable d’animation encapsulée qui représente Top lié de rectangle d’animation.|

## <a name="remarks"></a>Notes

La classe CAnimationRect résume quatre objets CAnimationVariable et peut représenter dans des applications un rectangle. Pour utiliser cette classe en application, il suffit d’instantané d’un objet de cette classe, ajoutez-le au contrôleur d’animation à l’aide de CAnimationController::AddAnimationObject et appelez AddTransition pour chaque transition à appliquer à gauche, à droite en haut et en bas des coordonnées.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CAnimationBaseObject](../../mfc/reference/canimationbaseobject-class.md)

`CAnimationRect`

## <a name="requirements"></a>Spécifications

**En-tête :** afxanimationcontroller.h

## <a name="canimationrectaddtransition"></a><a name="addtransition"></a>CAnimationRect::AddTransition

Ajoute des transitions pour les coordonnées gauche, supérieure, droite et inférieure.

```
void AddTransition(
    CBaseTransition* pLeftTransition,
    CBaseTransition* pTopTransition,
    CBaseTransition* pRightTransition,
    CBaseTransition* pBottomTransition);
```

### <a name="parameters"></a>Paramètres

*pLeftTransition (en)*<br/>
Spécifie la transition pour le côté gauche.

*pTopTransition (en)*<br/>
Spécifie la transition pour le côté supérieur.

*pRightTransition*<br/>
Spécifie la transition du côté droit.

*pBottomTransition*<br/>
Spécifie la transition pour le côté inférieur.

### <a name="remarks"></a>Notes

Appelez cette fonction pour ajouter les transitions spécifiées à la liste interne des transitions à appliquer aux variables d’animation pour chaque côté rectangle. Lorsque vous ajoutez des transitions, elles ne sont pas appliquées immédiatement et stockées dans une liste interne. Les transitions sont appliquées (ajoutées à un storyboard pour une valeur particulière) lorsque vous appelez CAnimationController::AnimateGroup. Si vous n’avez pas besoin d’appliquer une transition vers l’un des côtés rectangle, vous pouvez passer NULL.

## <a name="canimationrectcanimationrect"></a><a name="canimationrect"></a>CAnimationRect::CAnimationRect

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

*nGroupID (en anglais)*<br/>
Spécifie l’ID du groupe.

*nObjectID (nObjectID)*<br/>
Spécifie l’id d’objet.

*dwUserData*<br/>
Spécifie les données définies par l’utilisateur.

*Pt*<br/>
Coordonner le coin supérieur gauche.

*Sz*<br/>
Taille du rectangle.

*nLeft (en)*<br/>
Specifie la coordonnées de la gauche liée.

*Ntop*<br/>
Specifie la coordonnées du haut de l’état.

*nRight (en)*<br/>
Spécifie la coordination de la droite liée.

*nBottom (en)*<br/>
Spécifie la coordonnées du fond lié.

### <a name="remarks"></a>Notes

L’objet est construit avec des valeurs par défaut pour la gauche, le haut, la droite et le bas, l’identifiant d’objet et l’ID de groupe, qui seront réglés à 0. Ils peuvent être modifiés plus tard au moment de l’exécution à l’aide de SetDefaultValue et SetID.

## <a name="canimationrectgetanimationvariablelist"></a><a name="getanimationvariablelist"></a>CAnimationRect::GetAnimationVariableList

Place les variables d’animation encapsulées dans une liste.

```
virtual void GetAnimationVariableList(
    CList<CAnimationVariable*,
    CAnimationVariable*>& lst);
```

### <a name="parameters"></a>Paramètres

*Lst*<br/>
Lorsque la fonction revient, il contient des indications à quatre objets CAnimationVariable représentant les coordonnées du rectangle.

## <a name="canimationrectgetbottom"></a><a name="getbottom"></a>CAnimationRect::GetBottom

Donne accès à CAnimationVariable représentant la coordination inférieure.

```
CAnimationVariable& GetBottom();
```

### <a name="return-value"></a>Valeur de retour

Une référence à CAnimationVariable encapsulé représentant la coordination inférieure.

### <a name="remarks"></a>Notes

Vous pouvez appeler cette méthode pour obtenir un accès direct à CAnimationVariable sous-jacent représentant la coordonnées inférieures.

## <a name="canimationrectgetdefaultvalue"></a><a name="getdefaultvalue"></a>CAnimationRect::GetDefaultValue

Retourne les valeurs par défaut pour les limites du rectangle.

```
CRect GetDefaultValue();
```

### <a name="return-value"></a>Valeur de retour

Une valeur CRect contenant des défauts pour la gauche, la droite, le haut et le bas.

### <a name="remarks"></a>Notes

Appelez cette fonction pour récupérer la valeur par défaut, qui a déjà été définie par le constructeur ou SetDefaultValue.

## <a name="canimationrectgetleft"></a><a name="getleft"></a>CAnimationRect::GetLeft

Donne accès à CAnimationVariable représentant la coordination gauche.

```
CAnimationVariable& GetLeft();
```

### <a name="return-value"></a>Valeur de retour

Une référence à CAnimationVariable encapsulé représentant la coordination gauche.

### <a name="remarks"></a>Notes

Vous pouvez appeler cette méthode pour obtenir un accès direct à CAnimationVariable sous-jacent représentant la coordonnées gauche.

## <a name="canimationrectgetright"></a><a name="getright"></a>CAnimationRect::GetRight

Donne accès à CAnimationVariable représentant la bonne coordination.

```
CAnimationVariable& GetRight();
```

### <a name="return-value"></a>Valeur de retour

Une référence à CAnimationVariable encapsulé représentant la coordination droite.

### <a name="remarks"></a>Notes

Vous pouvez appeler cette méthode pour obtenir un accès direct à CAnimationVariable sous-jacent représentant la bonne coordonnées.

## <a name="canimationrectgettop"></a><a name="gettop"></a>CAnimationRect::GetTop

Donne accès à CAnimationVariable représentant la plus haute coordination.

```
CAnimationVariable& GetTop();
```

### <a name="return-value"></a>Valeur de retour

Une référence à CAnimationVariable encapsulé représentant la haute coordonnées.

### <a name="remarks"></a>Notes

Vous pouvez appeler cette méthode pour obtenir un accès direct à CAnimationVariable sous-jacent représentant la coordonnées supérieures.

## <a name="canimationrectgetvalue"></a><a name="getvalue"></a>CAnimationRect::GetValue

Retourne la valeur actuelle.

```
BOOL GetValue(CRect& rect);
```

### <a name="parameters"></a>Paramètres

*Rect*<br/>
Sortie : Contient la valeur actuelle lorsque cette méthode revient.

### <a name="return-value"></a>Valeur de retour

VRAI, si la valeur actuelle a été récupérée avec succès; autrement FALSE.

### <a name="remarks"></a>Notes

Appelez cette fonction pour récupérer la valeur actuelle du rectangle d’animation. Si cette méthode échoue ou sous-jacent des objets COM pour la gauche, le haut, la droite et le bas n’ont pas été paralés, rect contient une valeur par défaut, qui a déjà été définie dans le constructeur ou par SetDefaultValue.

## <a name="canimationrectm_bfixedsize"></a><a name="m_bfixedsize"></a>CAnimationRect::m_bFixedSize

Précise si le rectangle a la taille fixe.

```
BOOL m_bFixedSize;
```

### <a name="remarks"></a>Notes

Si ce membre est vrai, alors la taille du rectangle est fixe et à droite et les valeurs inférieures sont recalculées chaque fois que le coin supérieur gauche est déplacé en fonction de la taille fixe. Définissez cette valeur à TRUE pour déplacer facilement le rectangle autour de l’écran. Dans ce cas, les transitions appliquées aux coordonnées droites et inférieures sont ignorées. La taille est stockée à l’intérieur lorsque vous construisez l’objet et/ou appelez SetDefaultValue. Par défaut, ce membre est configuré à FALSE.

## <a name="canimationrectm_bottomvalue"></a><a name="m_bottomvalue"></a>CAnimationRect::m_bottomValue

La variable d’animation encapsulée qui représente bottom lié de rectangle d’animation.

```
CAnimationVariable m_bottomValue;
```

## <a name="canimationrectm_leftvalue"></a><a name="m_leftvalue"></a>CAnimationRect::m_leftValue

La variable d’animation encapsulée qui représente à gauche lié de rectangle d’animation.

```
CAnimationVariable m_leftValue;
```

## <a name="canimationrectm_rightvalue"></a><a name="m_rightvalue"></a>CAnimationRect::m_rightValue

La variable d’animation encapsulée qui représente la limite droite du rectangle d’animation.

```
CAnimationVariable m_rightValue;
```

## <a name="canimationrectm_szinitial"></a><a name="m_szinitial"></a>CAnimationRect::m_szInitial

Spécifie la taille initiale du rectangle d’animation.

```
CSize m_szInitial;
```

## <a name="canimationrectm_topvalue"></a><a name="m_topvalue"></a>CAnimationRect::m_topValue

La variable d’animation encapsulée qui représente Top lié de rectangle d’animation.

```
CAnimationVariable m_topValue;
```

## <a name="canimationrectoperator-rect"></a><a name="operator_rect"></a>CAnimationRect::opérateur RECT

Convertit un CAnimationRect en RECT.

```
operator RECT();
```

### <a name="return-value"></a>Valeur de retour

Valeur actuelle du rectangle d’animation en tant que RECT.

### <a name="remarks"></a>Notes

Cette fonction appelle en interne GetValue. Si GetValue échoue pour une raison quelconque, le RECT retourné contiendra des valeurs par défaut pour toutes les coordonnées de rectangle.

## <a name="canimationrectoperator"></a><a name="operator_eq"></a>CAnimationRect::opérateur

Assigne rect à CAnimationRect.

```
void operator=(const RECT& rect);
```

### <a name="parameters"></a>Paramètres

*Rect*<br/>
La nouvelle valeur du rectangle d’animation.

### <a name="remarks"></a>Notes

Il est recommandé de le faire avant le début de l’animation, car cet opérateur appelle SetDefaultValue, qui recrée les objets COM sous-jacents pour les composants de couleur s’ils ont été créés. Si vous avez souscrit cet objet d’animation à des événements (ValueChanged ou IntegerValueChanged), vous devez réactiver ces événements.

## <a name="canimationrectsetdefaultvalue"></a><a name="setdefaultvalue"></a>CAnimationRect::SetDefaultValue

Définit la valeur par défaut.

```
void SetDefaultValue(const CRect& rect);
```

### <a name="parameters"></a>Paramètres

*Rect*<br/>
Spécifie les nouvelles valeurs par défaut pour la gauche, le haut, la droite et le bas.

### <a name="remarks"></a>Notes

Utilisez cette fonction pour définir une valeur par défaut à l’objet d’animation. Ces méthodes attribuent des valeurs par défaut aux limites du rectangle. Il recrée également des objets COM sous-jacents s’ils ont été créés. Si vous avez souscrit cet objet d’animation à des événements (ValueChanged ou IntegerValueChanged), vous devez réactiver ces événements.

## <a name="see-also"></a>Voir aussi

[Classes](../../mfc/reference/mfc-classes.md)
