---
title: CAnimationSize, classe
ms.date: 11/04/2016
f1_keywords:
- CAnimationSize
- AFXANIMATIONCONTROLLER/CAnimationSize
- AFXANIMATIONCONTROLLER/CAnimationSize::CAnimationSize
- AFXANIMATIONCONTROLLER/CAnimationSize::AddTransition
- AFXANIMATIONCONTROLLER/CAnimationSize::GetCX
- AFXANIMATIONCONTROLLER/CAnimationSize::GetCY
- AFXANIMATIONCONTROLLER/CAnimationSize::GetDefaultValue
- AFXANIMATIONCONTROLLER/CAnimationSize::GetValue
- AFXANIMATIONCONTROLLER/CAnimationSize::SetDefaultValue
- AFXANIMATIONCONTROLLER/CAnimationSize::GetAnimationVariableList
- AFXANIMATIONCONTROLLER/CAnimationSize::m_cxValue
- AFXANIMATIONCONTROLLER/CAnimationSize::m_cyValue
helpviewer_keywords:
- CAnimationSize [MFC], CAnimationSize
- CAnimationSize [MFC], AddTransition
- CAnimationSize [MFC], GetCX
- CAnimationSize [MFC], GetCY
- CAnimationSize [MFC], GetDefaultValue
- CAnimationSize [MFC], GetValue
- CAnimationSize [MFC], SetDefaultValue
- CAnimationSize [MFC], GetAnimationVariableList
- CAnimationSize [MFC], m_cxValue
- CAnimationSize [MFC], m_cyValue
ms.assetid: ea06d1b5-502c-44a3-82ca-8bd6ba6a9364
ms.openlocfilehash: 1f4a5b8b52d8bd37d1ed83618e7451dd85f84c32
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "81755123"
---
# <a name="canimationsize-class"></a>CAnimationSize, classe

Implémente les fonctionnalités d'un objet taille dont les dimensions peuvent être animées.

## <a name="syntax"></a>Syntaxe

```
class CAnimationSize : public CAnimationBaseObject;
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CAnimationSize::CAnimationSize](#canimationsize)|Surchargé. Construit un objet de taille d’animation.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CAnimationSize::AddTransition](#addtransition)|Ajoute des transitions pour la largeur et la hauteur.|
|[CAnimationSize::GetCX](#getcx)|Donne accès à CAnimationVariable représentant largeur.|
|[CAnimationSize::GetCY](#getcy)|Donne accès à CAnimationVariable représentant la hauteur.|
|[CAnimationSize::GetDefaultValue](#getdefaultvalue)|Retourne les valeurs par défaut pour la largeur et la hauteur.|
|[CAnimationSize::GetValue](#getvalue)|Retourne la valeur actuelle.|
|[CAnimationSize::SetDefaultValue](#setdefaultvalue)|Définit la valeur par défaut.|

### <a name="protected-methods"></a>Méthodes protégées

|Nom|Description|
|----------|-----------------|
|[CAnimationSize::GetAnimationVariableList](#getanimationvariablelist)|Place les variables d’animation encapsulées dans une liste. (Overrides [CAnimationBaseObject::GetAnimationVariableList](../../mfc/reference/canimationbaseobject-class.md#getanimationvariablelist).)|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[CAnimationSize::opérateur CSize](#operator_csize)|Convertit un CAnimationSize en CSize.|
|[CAnimationSize::opérateur](#operator_eq)|Assigne szSrc à CAnimationSize.|

### <a name="protected-data-members"></a>Membres de données protégés

|Nom|Description|
|----------|-----------------|
|[CAnimationSize::m_cxValue](#m_cxvalue)|La variable d’animation encapsulée qui représente la largeur de la taille de l’animation.|
|[CAnimationSize::m_cyValue](#m_cyvalue)|La variable d’animation encapsulée qui représente la hauteur de la taille de l’animation.|

## <a name="remarks"></a>Notes

La classe CAnimationSize résume deux objets CAnimationVariable et peut représenter dans des applications d’une taille. Par exemple, vous pouvez utiliser cette classe pour animer une taille de n’importe quel objet bidimensionnel sur l’écran (comme le rectangle, le contrôle, etc.). Pour utiliser cette classe en application, il suffit d’instantané d’un objet de cette classe, ajoutez-le au contrôleur d’animation à l’aide de CAnimationController::AddAnimationObject et appelez AddTransition pour chaque transition à appliquer à la largeur et/ou à la hauteur.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CAnimationBaseObject](../../mfc/reference/canimationbaseobject-class.md)

`CAnimationSize`

## <a name="requirements"></a>Spécifications

**En-tête :** afxanimationcontroller.h

## <a name="canimationsizeaddtransition"></a><a name="addtransition"></a>CAnimationSize::AddTransition

Ajoute des transitions pour la largeur et la hauteur.

```cpp
void AddTransition(
    CBaseTransition* pCXTransition,
    CBaseTransition* pCYTransition);
```

### <a name="parameters"></a>Paramètres

*pCXTransition (en)*<br/>
Un pointeur à la transition pour la largeur.

*pCYTransition (en)*<br/>
Un pointeur à la transition pour la hauteur.

### <a name="remarks"></a>Notes

Appelez cette fonction pour ajouter les transitions spécifiées à la liste interne des transitions à appliquer aux variables d’animation pour la largeur et la hauteur. Lorsque vous ajoutez des transitions, elles ne sont pas appliquées immédiatement et stockées dans une liste interne. Les transitions sont appliquées (ajoutées à un storyboard pour une valeur particulière) lorsque vous appelez CAnimationController::AnimateGroup. Si vous n’avez pas besoin d’appliquer une transition vers l’une des dimensions, vous pouvez passer NULL.

## <a name="canimationsizecanimationsize"></a><a name="canimationsize"></a>CAnimationSize::CAnimationSize

Construit un objet de taille d’animation.

```
CAnimationSize();

CAnimationSize(
    const CSize& szDefault,
    UINT32 nGroupID,
    UINT32 nObjectID = (UINT32)-1,
    DWORD dwUserData = 0);
```

### <a name="parameters"></a>Paramètres

*szDefault*<br/>
Spécifie la taille par défaut.

*nGroupID (en anglais)*<br/>
Spécifie l’ID du groupe.

*nObjectID (nObjectID)*<br/>
Spécifie l’id d’objet.

*dwUserData*<br/>
Spécifie les données définies par l’utilisateur.

### <a name="remarks"></a>Notes

L’objet est construit avec des valeurs par défaut pour la largeur, la hauteur, l’identification d’objet et l’ID de groupe, qui sera réglé à 0. Ils peuvent être modifiés plus tard au moment de l’exécution à l’aide de SetDefaultValue et SetID.

## <a name="canimationsizegetanimationvariablelist"></a><a name="getanimationvariablelist"></a>CAnimationSize::GetAnimationVariableList

Place les variables d’animation encapsulées dans une liste.

```
virtual void GetAnimationVariableList(
    CList<CAnimationVariable*,
    CAnimationVariable*>& lst);
```

### <a name="parameters"></a>Paramètres

*Lst*<br/>
Lorsque la fonction revient, il contient des indications à deux objets CAnimationVariable représentant la largeur et la hauteur.

## <a name="canimationsizegetcx"></a><a name="getcx"></a>CAnimationSize::GetCX

Donne accès à CAnimationVariable représentant largeur.

```
CAnimationVariable& GetCX();
```

### <a name="return-value"></a>Valeur de retour

Une référence à CAnimationVariable encapsulé représentant largeur.

### <a name="remarks"></a>Notes

Vous pouvez appeler cette méthode pour obtenir un accès direct à CAnimationVariable sous-jacent représentant largeur.

## <a name="canimationsizegetcy"></a><a name="getcy"></a>CAnimationSize::GetCY

Donne accès à CAnimationVariable représentant la hauteur.

```
CAnimationVariable& GetCY();
```

### <a name="return-value"></a>Valeur de retour

Une référence à CAnimationVariable encapsulé représentant la hauteur.

### <a name="remarks"></a>Notes

Vous pouvez appeler cette méthode pour obtenir un accès direct à CAnimationVariable sous-jacent représentant la hauteur.

## <a name="canimationsizegetdefaultvalue"></a><a name="getdefaultvalue"></a>CAnimationSize::GetDefaultValue

Retourne les valeurs par défaut pour la largeur et la hauteur.

```
CSize GetDefaultValue();
```

### <a name="return-value"></a>Valeur de retour

Un objet CSize contenant des valeurs par défaut.

### <a name="remarks"></a>Notes

Appelez cette fonction pour récupérer la valeur par défaut, qui a déjà été définie par le constructeur ou SetDefaultValue.

## <a name="canimationsizegetvalue"></a><a name="getvalue"></a>CAnimationSize::GetValue

Retourne la valeur actuelle.

```
BOOL GetValue(CSize& szValue);
```

### <a name="parameters"></a>Paramètres

*szValue (en)*<br/>
Sortie : Contient la valeur actuelle lorsque cette méthode revient.

### <a name="return-value"></a>Valeur de retour

VRAI, si la valeur actuelle a été récupérée avec succès; autrement FALSE.

### <a name="remarks"></a>Notes

Appelez cette fonction pour récupérer la valeur actuelle de la taille de l’animation. Si cette méthode échoue ou que les objets COM sous-jacents pour la largeur et la taille n’ont pas été paralysés, szValue contient une valeur par défaut, qui a déjà été définie en constructeur ou par SetDefaultValue.

## <a name="canimationsizem_cxvalue"></a><a name="m_cxvalue"></a>CAnimationSize::m_cxValue

La variable d’animation encapsulée qui représente la largeur de la taille de l’animation.

```
CAnimationVariable m_cxValue;
```

## <a name="canimationsizem_cyvalue"></a><a name="m_cyvalue"></a>CAnimationSize::m_cyValue

La variable d’animation encapsulée qui représente la hauteur de la taille de l’animation.

```
CAnimationVariable m_cyValue;
```

## <a name="canimationsizeoperator-csize"></a><a name="operator_csize"></a>CAnimationSize::opérateur CSize

Convertit un CAnimationSize en CSize.

```
operator CSize();
```

### <a name="return-value"></a>Valeur de retour

Valeur actuelle de la taille de l’animation comme CSize.

### <a name="remarks"></a>Notes

Cette fonction appelle en interne GetValue. Si GetValue pour une raison quelconque échoue, la taille retournée contiendra des valeurs par défaut pour la largeur et la hauteur.

## <a name="canimationsizeoperator"></a><a name="operator_eq"></a>CAnimationSize::opérateur

Assigne szSrc à CAnimationSize.

```cpp
void operator=(const CSize& szSrc);
```

### <a name="parameters"></a>Paramètres

*szSrc*<br/>
Se réfère à CSize ou SIZE.

### <a name="remarks"></a>Notes

Assigne szSrc à CAnimationSize. Il est recommandé de le faire avant le début de l’animation, car cet opérateur appelle SetDefaultValue, qui recrée les objets COM sous-jacents pour largeur et hauteur s’ils ont été créés. Si vous avez souscrit cet objet d’animation à des événements (ValueChanged ou IntegerValueChanged), vous devez réactiver ces événements.

## <a name="canimationsizesetdefaultvalue"></a><a name="setdefaultvalue"></a>CAnimationSize::SetDefaultValue

Définit la valeur par défaut.

```cpp
void SetDefaultValue(const CSize& szDefault);
```

### <a name="parameters"></a>Paramètres

*szDefault*<br/>
Spécifie la nouvelle taille par défaut.

### <a name="remarks"></a>Notes

Utilisez cette fonction pour définir une valeur par défaut à l’objet d’animation. Ces méthodes attribuent des valeurs par défaut à la largeur et à la hauteur de la taille de l’animation. Il recrée également des objets COM sous-jacents s’ils ont été créés. Si vous avez souscrit cet objet d’animation à des événements (ValueChanged ou IntegerValueChanged), vous devez réactiver ces événements.

## <a name="see-also"></a>Voir aussi

[Classes](../../mfc/reference/mfc-classes.md)
