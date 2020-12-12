---
description: 'En savoir plus sur : classe CAnimationColor,'
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
ms.openlocfilehash: 430f017bc9d60eed5e2d42b71f0303546deecaca
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97318635"
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
|[CAnimationColor, :: CAnimationColor,](#canimationcolor)|Surchargé. Construit un objet de couleur d’animation.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CAnimationColor, :: AddTransition](#addtransition)|Ajoute des transitions pour les composants rouge, vert et bleu.|
|[CAnimationColor, :: GetB](#getb)|Fournit l’accès à CAnimationVariable représentant le composant bleu.|
|[CAnimationColor, :: GetDefaultValue](#getdefaultvalue)|Retourne les valeurs par défaut des composants de couleur.|
|[CAnimationColor, :: GetG](#getg)|Fournit l’accès à CAnimationVariable représentant le composant vert.|
|[CAnimationColor, :: GetR](#getr)|Fournit l’accès à CAnimationVariable représentant le composant rouge.|
|[CAnimationColor, :: GetValue](#getvalue)|Retourne la valeur actuelle.|
|[CAnimationColor, :: SetDefaultValue](#setdefaultvalue)|Définit la valeur par défaut.|

### <a name="protected-methods"></a>Méthodes protégées

|Nom|Description|
|----------|-----------------|
|[CAnimationColor, :: GetAnimationVariableList](#getanimationvariablelist)|Place les variables d’animation encapsulées dans une liste. (Substitue [CAnimationBaseObject, :: GetAnimationVariableList](../../mfc/reference/canimationbaseobject-class.md#getanimationvariablelist).)|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[CAnimationColor, :: Operator COLORREF](#operator_colorref)||
|[CAnimationColor, :: Operator =](#operator_eq)|Affecte la couleur à CAnimationColor,.|

### <a name="protected-data-members"></a>Membres de données protégés

|Nom|Description|
|----------|-----------------|
|[CAnimationColor, :: m_bValue](#m_bvalue)|Variable d’animation encapsulée qui représente la composante bleue de la couleur d’animation.|
|[CAnimationColor, :: m_gValue](#m_gvalue)|Variable d’animation encapsulée qui représente la composante verte de la couleur de l’animation.|
|[CAnimationColor, :: m_rValue](#m_rvalue)|Variable d’animation encapsulée qui représente la composante rouge de la couleur de l’animation.|

## <a name="remarks"></a>Notes

La classe CAnimationColor, encapsule trois objets CAnimationVariable et peut représenter des couleurs dans les applications. Par exemple, vous pouvez utiliser cette classe pour animer les couleurs de n’importe quel objet sur l’écran (comme la couleur du texte, la couleur d’arrière-plan, etc.). Pour utiliser cette classe dans l’application, il vous suffit d’instancier un objet de cette classe, de l’ajouter au contrôleur d’animation à l’aide de CAnimationController :: AddAnimationObject et d’appeler AddTransition pour chaque transition à appliquer aux composants rouge, vert et bleu.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CAnimationBaseObject,](../../mfc/reference/canimationbaseobject-class.md)

`CAnimationColor`

## <a name="requirements"></a>Spécifications

**En-tête :** afxanimationcontroller.h

## <a name="canimationcoloraddtransition"></a><a name="addtransition"></a> CAnimationColor, :: AddTransition

Ajoute des transitions pour les composants rouge, vert et bleu.

```cpp
void AddTransition(
    CBaseTransition* pRTransition,
    CBaseTransition* pGTransition,
    CBaseTransition* pBTransition);
```

### <a name="parameters"></a>Paramètres

*pRTransition*<br/>
Transition pour le composant rouge.

*pGTransition*<br/>
Transition pour le composant vert.

*pBTransition*<br/>
Transition pour le composant bleu.

### <a name="remarks"></a>Notes

Appelez cette fonction pour ajouter les transitions spécifiées à la liste interne des transitions à appliquer aux variables d’animation représentant les composants de couleur. Lorsque vous ajoutez des transitions, elles ne sont pas appliquées immédiatement et stockées dans une liste interne. Les transitions sont appliquées (ajoutées à une table de montage séquentiel pour une valeur particulière) quand vous appelez CAnimationController :: AnimateGroup. Si vous n’avez pas besoin d’appliquer une transition à l’un des composants de couleur, vous pouvez passer la valeur NULL.

## <a name="canimationcolorcanimationcolor"></a><a name="canimationcolor"></a> CAnimationColor, :: CAnimationColor,

Construit un objet CAnimationColor,.

```
CAnimationColor();

CAnimationColor(
    COLORREF color,
    UINT32 nGroupID,
    UINT32 nObjectID = (UINT32)-1,
    DWORD dwUserData = 0);
```

### <a name="parameters"></a>Paramètres

*color*<br/>
Spécifie la couleur par défaut.

*nGroupID*<br/>
Spécifie l’ID de groupe.

*nObjectID*<br/>
Spécifie l’ID de l’objet.

*dwUserData*<br/>
Spécifie les données définies par l’utilisateur.

### <a name="remarks"></a>Notes

L’objet est construit avec les valeurs par défaut pour les paramètres rouge, vert, bleu, ID d’objet et ID de groupe, qui seront définis sur 0. Vous pouvez les modifier ultérieurement au moment de l’exécution en utilisant SetDefaultValue et SetID.

## <a name="canimationcolorgetanimationvariablelist"></a><a name="getanimationvariablelist"></a> CAnimationColor, :: GetAnimationVariableList

Place les variables d’animation encapsulées dans une liste.

```
virtual void GetAnimationVariableList(CList<CAnimationVariable*>& lst);
```

### <a name="parameters"></a>Paramètres

*LST*<br/>
Quand la fonction retourne, elle contient des pointeurs vers trois objets CAnimationVariable représentant les composants rouge, vert et bleu.

## <a name="canimationcolorgetb"></a><a name="getb"></a> CAnimationColor, :: GetB

Fournit l’accès à CAnimationVariable représentant le composant bleu.

```
CAnimationVariable& GetB();
```

### <a name="return-value"></a>Valeur renvoyée

Référence à CAnimationVariable encapsulé représentant le composant bleu.

### <a name="remarks"></a>Notes

Vous pouvez appeler cette méthode pour bénéficier d’un accès direct à l’CAnimationVariable sous-jacent représentant le composant bleu.

## <a name="canimationcolorgetdefaultvalue"></a><a name="getdefaultvalue"></a> CAnimationColor, :: GetDefaultValue

Retourne les valeurs par défaut des composants de couleur.

```
COLORREF GetDefaultValue();
```

### <a name="return-value"></a>Valeur renvoyée

Valeur COLORREF contenant les valeurs par défaut des composants RGB.

### <a name="remarks"></a>Notes

Appelez cette fonction pour récupérer la valeur par défaut, qui a été précédemment définie par le constructeur ou SetDefaultValue.

## <a name="canimationcolorgetg"></a><a name="getg"></a> CAnimationColor, :: GetG

Fournit l’accès à CAnimationVariable représentant le composant vert.

```
CAnimationVariable& GetG();
```

### <a name="return-value"></a>Valeur renvoyée

Référence à CAnimationVariable encapsulé représentant le composant vert.

### <a name="remarks"></a>Notes

Vous pouvez appeler cette méthode pour bénéficier d’un accès direct à l’CAnimationVariable sous-jacent représentant le composant vert.

## <a name="canimationcolorgetr"></a><a name="getr"></a> CAnimationColor, :: GetR

Fournit l’accès à CAnimationVariable représentant le composant rouge.

```
CAnimationVariable& GetR();
```

### <a name="return-value"></a>Valeur renvoyée

Référence à CAnimationVariable encapsulé représentant le composant rouge.

### <a name="remarks"></a>Notes

Vous pouvez appeler cette méthode pour bénéficier d’un accès direct à l’CAnimationVariable sous-jacent représentant le composant rouge.

## <a name="canimationcolorgetvalue"></a><a name="getvalue"></a> CAnimationColor, :: GetValue

Retourne la valeur actuelle.

```
BOOL GetValue(COLORREF& color);
```

### <a name="parameters"></a>Paramètres

*color*<br/>
Sortie : Contient la valeur actuelle lorsque cette méthode est retournée.

### <a name="return-value"></a>Valeur renvoyée

TRUE si la valeur actuelle a été récupérée avec succès ; Sinon, FALSe.

### <a name="remarks"></a>Notes

Appelez cette fonction pour récupérer la valeur actuelle de la couleur d’animation. Si cette méthode échoue ou si les objets COM sous-jacents pour les composants de couleur n’ont pas été initialisés, Color contient la valeur par défaut, qui a été précédemment définie dans le constructeur ou par SetDefaultValue.

## <a name="canimationcolorm_bvalue"></a><a name="m_bvalue"></a> CAnimationColor, :: m_bValue

Variable d’animation encapsulée qui représente la composante bleue de la couleur d’animation.

```
CAnimationVariable m_bValue;
```

## <a name="canimationcolorm_gvalue"></a><a name="m_gvalue"></a> CAnimationColor, :: m_gValue

Variable d’animation encapsulée qui représente la composante verte de la couleur de l’animation.

```
CAnimationVariable m_gValue;
```

## <a name="canimationcolorm_rvalue"></a><a name="m_rvalue"></a> CAnimationColor, :: m_rValue

Variable d’animation encapsulée qui représente la composante rouge de la couleur de l’animation.

```
CAnimationVariable m_rValue;
```

## <a name="canimationcoloroperator-colorref"></a><a name="operator_colorref"></a> CAnimationColor, :: Operator COLORREF

```
operator COLORREF();
```

### <a name="return-value"></a>Valeur renvoyée

## <a name="canimationcoloroperator"></a><a name="operator_eq"></a> CAnimationColor, :: Operator =

Affecte la couleur à CAnimationColor,.

```cpp
void operator=(COLORREF color);
```

### <a name="parameters"></a>Paramètres

*color*<br/>
Spécifie la nouvelle valeur de la couleur d’animation.

### <a name="remarks"></a>Notes

Il est recommandé de le faire avant le démarrage de l’animation, car cet opérateur appelle SetDefaultValue, qui recrée les objets COM sous-jacents pour les composants de couleur s’ils ont été créés. Si vous avez souscrit cet objet d’animation à des événements (ValueChanged ou IntegerValueChanged), vous devez réactiver ces événements.

## <a name="canimationcolorsetdefaultvalue"></a><a name="setdefaultvalue"></a> CAnimationColor, :: SetDefaultValue

Définit la valeur par défaut.

```cpp
void SetDefaultValue(COLORREF color);
```

### <a name="parameters"></a>Paramètres

*color*<br/>
Spécifie de nouvelles valeurs par défaut pour les composants rouge, vert et bleu.

### <a name="remarks"></a>Notes

Utilisez cette fonction pour définir une valeur par défaut pour l’objet d’animation. Cette méthode affecte des valeurs par défaut aux composants de couleur de la couleur d’animation. Il recrée également les objets COM sous-jacents s’ils ont été créés. Si vous avez souscrit cet objet d’animation à des événements (ValueChanged ou IntegerValueChanged), vous devez réactiver ces événements.

## <a name="see-also"></a>Voir aussi

[Classes](../../mfc/reference/mfc-classes.md)
