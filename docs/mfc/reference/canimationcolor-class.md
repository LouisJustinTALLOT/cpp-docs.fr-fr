---
title: CAnimationColor, classe
ms.date: 11/04/2016
f1_keywords:
- CAnimationColor
- AFXANIMATIONCONTROLLER/CAnimationColor
- AFXANIMATIONCONTROLLER/CAnimationColor::CAnimationColor
- AFXANIMATIONCONTROLLER/CAnimationColor::AddTransition
- AFXANIMATIONCONTROLLER/CAnimationColor::GetB
- AFXANIMATIONCONTROLLER/CAnimationColor::GetDefaultValue
- AFXANIMATIONCONTROLLER/CAnimationColor::GetG
- AFXANIMATIONCONTROLLER/CAnimationColor::GetR
- AFXANIMATIONCONTROLLER/CAnimationColor::GetValue
- AFXANIMATIONCONTROLLER/CAnimationColor::SetDefaultValue
- AFXANIMATIONCONTROLLER/CAnimationColor::GetAnimationVariableList
- AFXANIMATIONCONTROLLER/CAnimationColor::m_bValue
- AFXANIMATIONCONTROLLER/CAnimationColor::m_gValue
- AFXANIMATIONCONTROLLER/CAnimationColor::m_rValue
helpviewer_keywords:
- CAnimationColor [MFC], CAnimationColor
- CAnimationColor [MFC], AddTransition
- CAnimationColor [MFC], GetB
- CAnimationColor [MFC], GetDefaultValue
- CAnimationColor [MFC], GetG
- CAnimationColor [MFC], GetR
- CAnimationColor [MFC], GetValue
- CAnimationColor [MFC], SetDefaultValue
- CAnimationColor [MFC], GetAnimationVariableList
- CAnimationColor [MFC], m_bValue
- CAnimationColor [MFC], m_gValue
- CAnimationColor [MFC], m_rValue
ms.assetid: 88bfabd4-efeb-4652-87e8-304253d8e48c
ms.openlocfilehash: 5940cce6d55b95d8e1bac103cacc0bc828c213de
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371106"
---
# <a name="canimationcolor-class"></a>CAnimationColor, classe

Implémente les fonctionnalités d'une couleur dont les composants rouge, vert et bleu peuvent être animés.

## <a name="syntax"></a>Syntaxe

```
class CAnimationColor : public CAnimationBaseObject;
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CAnimationColor::CAnimationColor](#canimationcolor)|Surchargé. Construit un objet couleur d’animation.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CAnimationColor::AddTransition](#addtransition)|Ajoute des transitions pour les composants Rouge, Vert et Bleu.|
|[CAnimationColor::GetB](#getb)|Donne accès à CAnimationVariable représentant composant bleu.|
|[CAnimationColor::GetDefaultValue](#getdefaultvalue)|Retourne les valeurs par défaut pour les composants de couleur.|
|[CAnimationColor::GetG](#getg)|Donne accès à CAnimationVariable représentant la composante verte.|
|[CAnimationColor::GetR](#getr)|Donne accès à CAnimationVariable représentant composant rouge.|
|[CAnimationColor::GetValue](#getvalue)|Retourne la valeur actuelle.|
|[CAnimationColor::SetDefaultValue](#setdefaultvalue)|Définit la valeur par défaut.|

### <a name="protected-methods"></a>Méthodes protégées

|Nom|Description|
|----------|-----------------|
|[CAnimationColor::GetAnimationVariableList](#getanimationvariablelist)|Place les variables d’animation encapsulées dans une liste. (Overrides [CAnimationBaseObject::GetAnimationVariableList](../../mfc/reference/canimationbaseobject-class.md#getanimationvariablelist).)|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[CAnimationColor::opérateur COLORREF](#operator_colorref)||
|[CAnimationColor::opérateur](#operator_eq)|Attribue la couleur à CAnimationColor.|

### <a name="protected-data-members"></a>Membres de données protégés

|Nom|Description|
|----------|-----------------|
|[CAnimationColor:m_bValue](#m_bvalue)|La variable d’animation encapsulée qui représente le composant bleu de couleur d’animation.|
|[CAnimationColor::m_gValue](#m_gvalue)|La variable d’animation encapsulée qui représente le composant vert de couleur d’animation.|
|[CAnimationColor:m_rValue](#m_rvalue)|La variable d’animation encapsulée qui représente la composante rouge de la couleur d’animation.|

## <a name="remarks"></a>Notes

La classe CAnimationColor résume trois objets CAnimationVariable et peut représenter dans des applications une couleur. Par exemple, vous pouvez utiliser cette classe pour animer les couleurs de n’importe quel objet à l’écran (comme la couleur du texte, la couleur de fond, etc.). Pour utiliser cette classe en application, il suffit d’instantané d’un objet de cette classe, ajoutez-le au contrôleur d’animation à l’aide de CAnimationController::AddAnimationObject et appelez AddTransition pour chaque transition à appliquer sur les composants Rouges, Verts et Bleus.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CAnimationBaseObject](../../mfc/reference/canimationbaseobject-class.md)

`CAnimationColor`

## <a name="requirements"></a>Spécifications

**En-tête :** afxanimationcontroller.h

## <a name="canimationcoloraddtransition"></a><a name="addtransition"></a>CAnimationColor::AddTransition

Ajoute des transitions pour les composants Rouge, Vert et Bleu.

```
void AddTransition(
    CBaseTransition* pRTransition,
    CBaseTransition* pGTransition,
    CBaseTransition* pBTransition);
```

### <a name="parameters"></a>Paramètres

*pRTransition (en)*<br/>
Transition pour la composante rouge.

*pGTransition (en)*<br/>
Transition pour la composante verte.

*pBTransition (en)*<br/>
Transition pour composant bleu.

### <a name="remarks"></a>Notes

Appelez cette fonction pour ajouter les transitions spécifiées à la liste interne des transitions à appliquer aux variables d’animation représentant les composants de couleur. Lorsque vous ajoutez des transitions, elles ne sont pas appliquées immédiatement et stockées dans une liste interne. Les transitions sont appliquées (ajoutées à un storyboard pour une valeur particulière) lorsque vous appelez CAnimationController::AnimateGroup. Si vous n’avez pas besoin d’appliquer une transition vers l’un des composants de couleur, vous pouvez passer NULL.

## <a name="canimationcolorcanimationcolor"></a><a name="canimationcolor"></a>CAnimationColor::CAnimationColor

Construit un objet CAnimationColor.

```
CAnimationColor();

CAnimationColor(
    COLORREF color,
    UINT32 nGroupID,
    UINT32 nObjectID = (UINT32)-1,
    DWORD dwUserData = 0);
```

### <a name="parameters"></a>Paramètres

*Couleur*<br/>
Spécifie la couleur par défaut.

*nGroupID (en anglais)*<br/>
Spécifie l’ID du groupe.

*nObjectID (nObjectID)*<br/>
Spécifie l’id d’objet.

*dwUserData*<br/>
Spécifie les données définies par l’utilisateur.

### <a name="remarks"></a>Notes

L’objet est construit avec des valeurs par défaut pour le rouge, le vert, le bleu, l’identification d’objet et l’ID de groupe, qui seront réglés à 0. Ils peuvent être modifiés plus tard au moment de l’exécution à l’aide de SetDefaultValue et SetID.

## <a name="canimationcolorgetanimationvariablelist"></a><a name="getanimationvariablelist"></a>CAnimationColor::GetAnimationVariableList

Place les variables d’animation encapsulées dans une liste.

```
virtual void GetAnimationVariableList(CList<CAnimationVariable*>& lst);
```

### <a name="parameters"></a>Paramètres

*Lst*<br/>
Lorsque la fonction revient, il contient des indications sur trois objets CAnimationVariable représentant des composants rouges, verts et bleus.

## <a name="canimationcolorgetb"></a><a name="getb"></a>CAnimationColor::GetB

Donne accès à CAnimationVariable représentant composant bleu.

```
CAnimationVariable& GetB();
```

### <a name="return-value"></a>Valeur de retour

Une référence à CAnimationVariable encapsulé représentant composant bleu.

### <a name="remarks"></a>Notes

Vous pouvez appeler cette méthode pour obtenir un accès direct à CAnimationVariable sous-jacent représentant composant bleu.

## <a name="canimationcolorgetdefaultvalue"></a><a name="getdefaultvalue"></a>CAnimationColor::GetDefaultValue

Retourne les valeurs par défaut pour les composants de couleur.

```
COLORREF GetDefaultValue();
```

### <a name="return-value"></a>Valeur de retour

Une valeur COLORREF contenant des défauts de paiement pour les composants RGB.

### <a name="remarks"></a>Notes

Appelez cette fonction pour récupérer la valeur par défaut, qui a déjà été définie par le constructeur ou SetDefaultValue.

## <a name="canimationcolorgetg"></a><a name="getg"></a>CAnimationColor::GetG

Donne accès à CAnimationVariable représentant la composante verte.

```
CAnimationVariable& GetG();
```

### <a name="return-value"></a>Valeur de retour

Une référence à CAnimationVariable encapsulé représentant la composante verte.

### <a name="remarks"></a>Notes

Vous pouvez appeler cette méthode pour obtenir un accès direct à CAnimationVariable sous-jacent représentant composant vert.

## <a name="canimationcolorgetr"></a><a name="getr"></a>CAnimationColor::GetR

Donne accès à CAnimationVariable représentant composant rouge.

```
CAnimationVariable& GetR();
```

### <a name="return-value"></a>Valeur de retour

Une référence à CAnimationVariable encapsulé représentant la composante rouge.

### <a name="remarks"></a>Notes

Vous pouvez appeler cette méthode pour obtenir un accès direct à CAnimationVariable sous-jacent représentant composant rouge.

## <a name="canimationcolorgetvalue"></a><a name="getvalue"></a>CAnimationColor::GetValue

Retourne la valeur actuelle.

```
BOOL GetValue(COLORREF& color);
```

### <a name="parameters"></a>Paramètres

*Couleur*<br/>
Sortie : Contient la valeur actuelle lorsque cette méthode revient.

### <a name="return-value"></a>Valeur de retour

VRAI, si la valeur actuelle a été récupérée avec succès; autrement FALSE.

### <a name="remarks"></a>Notes

Appelez cette fonction pour récupérer la valeur actuelle de la couleur d’animation. Si cette méthode échoue ou que les objets COM sous-jacents pour les composants de couleur n’ont pas été parasés, la couleur contient une valeur par défaut, qui a déjà été définie dans le constructeur ou par SetDefaultValue.

## <a name="canimationcolorm_bvalue"></a><a name="m_bvalue"></a>CAnimationColor:m_bValue

La variable d’animation encapsulée qui représente le composant bleu de couleur d’animation.

```
CAnimationVariable m_bValue;
```

## <a name="canimationcolorm_gvalue"></a><a name="m_gvalue"></a>CAnimationColor::m_gValue

La variable d’animation encapsulée qui représente le composant vert de couleur d’animation.

```
CAnimationVariable m_gValue;
```

## <a name="canimationcolorm_rvalue"></a><a name="m_rvalue"></a>CAnimationColor:m_rValue

La variable d’animation encapsulée qui représente la composante rouge de la couleur d’animation.

```
CAnimationVariable m_rValue;
```

## <a name="canimationcoloroperator-colorref"></a><a name="operator_colorref"></a>CAnimationColor::opérateur COLORREF

```
operator COLORREF();
```

### <a name="return-value"></a>Valeur de retour

## <a name="canimationcoloroperator"></a><a name="operator_eq"></a>CAnimationColor::opérateur

Attribue la couleur à CAnimationColor.

```
void operator=(COLORREF color);
```

### <a name="parameters"></a>Paramètres

*Couleur*<br/>
Spécifie une nouvelle valeur Animation Color.

### <a name="remarks"></a>Notes

Il est recommandé de le faire avant le début de l’animation, car cet opérateur appelle SetDefaultValue, qui recrée les objets COM sous-jacents pour les composants de couleur s’ils ont été créés. Si vous avez souscrit cet objet d’animation à des événements (ValueChanged ou IntegerValueChanged), vous devez réactiver ces événements.

## <a name="canimationcolorsetdefaultvalue"></a><a name="setdefaultvalue"></a>CAnimationColor::SetDefaultValue

Définit la valeur par défaut.

```
void SetDefaultValue(COLORREF color);
```

### <a name="parameters"></a>Paramètres

*Couleur*<br/>
Spécifie les nouvelles valeurs par défaut pour les composants rouges, verts et bleus.

### <a name="remarks"></a>Notes

Utilisez cette fonction pour définir une valeur par défaut à l’objet d’animation. Ces méthodes attribuent des valeurs par défaut aux composants de couleur de couleur d’animation. Il recrée également des objets COM sous-jacents s’ils ont été créés. Si vous avez souscrit cet objet d’animation à des événements (ValueChanged ou IntegerValueChanged), vous devez réactiver ces événements.

## <a name="see-also"></a>Voir aussi

[Classes](../../mfc/reference/mfc-classes.md)
