---
description: 'En savoir plus sur : Classe CAnimationSize,'
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
ms.openlocfilehash: 894675c485077291c3fca35acfb9bfa9a3d10286
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97336765"
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
|[CAnimationSize, :: CAnimationSize,](#canimationsize)|Surchargé. Construit un objet de taille d’animation.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CAnimationSize, :: AddTransition](#addtransition)|Ajoute des transitions pour la largeur et la hauteur.|
|[CAnimationSize, :: GetCX](#getcx)|Fournit l’accès à CAnimationVariable représentant la largeur.|
|[CAnimationSize, :: GetCY](#getcy)|Fournit l’accès à CAnimationVariable représentant la hauteur.|
|[CAnimationSize, :: GetDefaultValue](#getdefaultvalue)|Retourne les valeurs par défaut pour la largeur et la hauteur.|
|[CAnimationSize, :: GetValue](#getvalue)|Retourne la valeur actuelle.|
|[CAnimationSize, :: SetDefaultValue](#setdefaultvalue)|Définit la valeur par défaut.|

### <a name="protected-methods"></a>Méthodes protégées

|Nom|Description|
|----------|-----------------|
|[CAnimationSize, :: GetAnimationVariableList](#getanimationvariablelist)|Place les variables d’animation encapsulées dans une liste. (Substitue [CAnimationBaseObject, :: GetAnimationVariableList](../../mfc/reference/canimationbaseobject-class.md#getanimationvariablelist).)|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[CAnimationSize, :: Operator CSize](#operator_csize)|Convertit un CAnimationSize, en CSize.|
|[CAnimationSize, :: Operator =](#operator_eq)|Affecte szSrc à CAnimationSize,.|

### <a name="protected-data-members"></a>Membres de données protégés

|Nom|Description|
|----------|-----------------|
|[CAnimationSize, :: m_cxValue](#m_cxvalue)|Variable d’animation encapsulée qui représente la largeur de la taille de l’animation.|
|[CAnimationSize, :: m_cyValue](#m_cyvalue)|Variable d’animation encapsulée qui représente la hauteur de la taille de l’animation.|

## <a name="remarks"></a>Notes

La classe CAnimationSize, encapsule deux objets CAnimationVariable et peut représenter dans les applications une taille. Par exemple, vous pouvez utiliser cette classe pour animer une taille de n’importe quel objet à deux dimensions sur l’écran (par exemple, Rectangle, contrôle, etc.). Pour utiliser cette classe dans l’application, il vous suffit d’instancier un objet de cette classe, de l’ajouter au contrôleur d’animation à l’aide de CAnimationController :: AddAnimationObject et d’appeler AddTransition pour chaque transition à appliquer à la largeur et/ou à la hauteur.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CAnimationBaseObject,](../../mfc/reference/canimationbaseobject-class.md)

`CAnimationSize`

## <a name="requirements"></a>Spécifications

**En-tête :** afxanimationcontroller.h

## <a name="canimationsizeaddtransition"></a><a name="addtransition"></a> CAnimationSize, :: AddTransition

Ajoute des transitions pour la largeur et la hauteur.

```cpp
void AddTransition(
    CBaseTransition* pCXTransition,
    CBaseTransition* pCYTransition);
```

### <a name="parameters"></a>Paramètres

*pCXTransition*<br/>
Pointeur vers la transition pour la largeur.

*pCYTransition*<br/>
Pointeur vers la transition pour la hauteur.

### <a name="remarks"></a>Notes

Appelez cette fonction pour ajouter les transitions spécifiées à la liste interne des transitions à appliquer aux variables d’animation pour la largeur et la hauteur. Lorsque vous ajoutez des transitions, elles ne sont pas appliquées immédiatement et stockées dans une liste interne. Les transitions sont appliquées (ajoutées à une table de montage séquentiel pour une valeur particulière) quand vous appelez CAnimationController :: AnimateGroup. Si vous n’avez pas besoin d’appliquer une transition à l’une des dimensions, vous pouvez passer la valeur NULL.

## <a name="canimationsizecanimationsize"></a><a name="canimationsize"></a> CAnimationSize, :: CAnimationSize,

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

*nGroupID*<br/>
Spécifie l’ID de groupe.

*nObjectID*<br/>
Spécifie l’ID de l’objet.

*dwUserData*<br/>
Spécifie les données définies par l’utilisateur.

### <a name="remarks"></a>Notes

L’objet est construit avec des valeurs par défaut pour la largeur, la hauteur, l’ID d’objet et l’ID de groupe, qui auront la valeur 0. Vous pouvez les modifier ultérieurement au moment de l’exécution en utilisant SetDefaultValue et SetID.

## <a name="canimationsizegetanimationvariablelist"></a><a name="getanimationvariablelist"></a> CAnimationSize, :: GetAnimationVariableList

Place les variables d’animation encapsulées dans une liste.

```
virtual void GetAnimationVariableList(
    CList<CAnimationVariable*,
    CAnimationVariable*>& lst);
```

### <a name="parameters"></a>Paramètres

*LST*<br/>
Quand la fonction retourne, elle contient des pointeurs vers deux objets CAnimationVariable représentant la largeur et la hauteur.

## <a name="canimationsizegetcx"></a><a name="getcx"></a> CAnimationSize, :: GetCX

Fournit l’accès à CAnimationVariable représentant la largeur.

```
CAnimationVariable& GetCX();
```

### <a name="return-value"></a>Valeur renvoyée

Référence à CAnimationVariable encapsulé représentant la largeur.

### <a name="remarks"></a>Notes

Vous pouvez appeler cette méthode pour accéder directement à l’CAnimationVariable sous-jacent représentant la largeur.

## <a name="canimationsizegetcy"></a><a name="getcy"></a> CAnimationSize, :: GetCY

Fournit l’accès à CAnimationVariable représentant la hauteur.

```
CAnimationVariable& GetCY();
```

### <a name="return-value"></a>Valeur renvoyée

Référence à CAnimationVariable encapsulé représentant la hauteur.

### <a name="remarks"></a>Notes

Vous pouvez appeler cette méthode pour bénéficier d’un accès direct à l’CAnimationVariable sous-jacent représentant la hauteur.

## <a name="canimationsizegetdefaultvalue"></a><a name="getdefaultvalue"></a> CAnimationSize, :: GetDefaultValue

Retourne les valeurs par défaut pour la largeur et la hauteur.

```
CSize GetDefaultValue();
```

### <a name="return-value"></a>Valeur renvoyée

Objet CSize contenant les valeurs par défaut.

### <a name="remarks"></a>Notes

Appelez cette fonction pour récupérer la valeur par défaut, qui a été précédemment définie par le constructeur ou SetDefaultValue.

## <a name="canimationsizegetvalue"></a><a name="getvalue"></a> CAnimationSize, :: GetValue

Retourne la valeur actuelle.

```
BOOL GetValue(CSize& szValue);
```

### <a name="parameters"></a>Paramètres

*szValue*<br/>
Sortie : Contient la valeur actuelle lorsque cette méthode est retournée.

### <a name="return-value"></a>Valeur renvoyée

TRUE si la valeur actuelle a été récupérée avec succès ; Sinon, FALSe.

### <a name="remarks"></a>Notes

Appelez cette fonction pour récupérer la valeur actuelle de la taille de l’animation. Si cette méthode échoue ou si les objets COM sous-jacents pour la largeur et la taille n’ont pas été initialisés, szValue contient la valeur par défaut, qui a été précédemment définie dans le constructeur ou par SetDefaultValue.

## <a name="canimationsizem_cxvalue"></a><a name="m_cxvalue"></a> CAnimationSize, :: m_cxValue

Variable d’animation encapsulée qui représente la largeur de la taille de l’animation.

```
CAnimationVariable m_cxValue;
```

## <a name="canimationsizem_cyvalue"></a><a name="m_cyvalue"></a> CAnimationSize, :: m_cyValue

Variable d’animation encapsulée qui représente la hauteur de la taille de l’animation.

```
CAnimationVariable m_cyValue;
```

## <a name="canimationsizeoperator-csize"></a><a name="operator_csize"></a> CAnimationSize, :: Operator CSize

Convertit un CAnimationSize, en CSize.

```
operator CSize();
```

### <a name="return-value"></a>Valeur renvoyée

Valeur actuelle de la taille de l’animation en tant que CSize.

### <a name="remarks"></a>Notes

Cette fonction appelle GetValue en interne. Si GetValue pour une raison quelconque échoue, la taille retournée contient des valeurs par défaut pour la largeur et la hauteur.

## <a name="canimationsizeoperator"></a><a name="operator_eq"></a> CAnimationSize, :: Operator =

Affecte szSrc à CAnimationSize,.

```cpp
void operator=(const CSize& szSrc);
```

### <a name="parameters"></a>Paramètres

*szSrc*<br/>
Fait référence à CSize ou SIZE.

### <a name="remarks"></a>Notes

Affecte szSrc à CAnimationSize,. Il est recommandé de le faire avant le démarrage de l’animation, car cet opérateur appelle SetDefaultValue, qui recrée les objets COM sous-jacents pour la largeur et la hauteur s’ils ont été créés. Si vous avez souscrit cet objet d’animation à des événements (ValueChanged ou IntegerValueChanged), vous devez réactiver ces événements.

## <a name="canimationsizesetdefaultvalue"></a><a name="setdefaultvalue"></a> CAnimationSize, :: SetDefaultValue

Définit la valeur par défaut.

```cpp
void SetDefaultValue(const CSize& szDefault);
```

### <a name="parameters"></a>Paramètres

*szDefault*<br/>
Spécifie la nouvelle taille par défaut.

### <a name="remarks"></a>Notes

Utilisez cette fonction pour définir une valeur par défaut pour l’objet d’animation. Cette méthode attribue des valeurs par défaut à la largeur et à la hauteur de la taille de l’animation. Il recrée également les objets COM sous-jacents s’ils ont été créés. Si vous avez souscrit cet objet d’animation à des événements (ValueChanged ou IntegerValueChanged), vous devez réactiver ces événements.

## <a name="see-also"></a>Voir aussi

[Classes](../../mfc/reference/mfc-classes.md)
