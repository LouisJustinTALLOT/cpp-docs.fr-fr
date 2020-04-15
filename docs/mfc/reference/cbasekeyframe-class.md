---
title: CBaseKeyFrame, classe
ms.date: 11/04/2016
f1_keywords:
- CBaseKeyFrame
- AFXANIMATIONCONTROLLER/CBaseKeyFrame
- AFXANIMATIONCONTROLLER/CBaseKeyFrame::CBaseKeyFrame
- AFXANIMATIONCONTROLLER/CBaseKeyFrame::AddToStoryboard
- AFXANIMATIONCONTROLLER/CBaseKeyFrame::GetAnimationKeyframe
- AFXANIMATIONCONTROLLER/CBaseKeyFrame::IsAdded
- AFXANIMATIONCONTROLLER/CBaseKeyFrame::IsKeyframeAtOffset
- AFXANIMATIONCONTROLLER/CBaseKeyFrame::m_bAdded
- AFXANIMATIONCONTROLLER/CBaseKeyFrame::m_bIsKeyframeAtOffset
- AFXANIMATIONCONTROLLER/CBaseKeyFrame::m_keyframe
helpviewer_keywords:
- CBaseKeyFrame [MFC], CBaseKeyFrame
- CBaseKeyFrame [MFC], AddToStoryboard
- CBaseKeyFrame [MFC], GetAnimationKeyframe
- CBaseKeyFrame [MFC], IsAdded
- CBaseKeyFrame [MFC], IsKeyframeAtOffset
- CBaseKeyFrame [MFC], m_bAdded
- CBaseKeyFrame [MFC], m_bIsKeyframeAtOffset
- CBaseKeyFrame [MFC], m_keyframe
ms.assetid: 285a2eff-e7c4-43be-b5aa-737727e6866d
ms.openlocfilehash: 3fcd55f6a157f4b837090a3608fb509b870aae5d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81352987"
---
# <a name="cbasekeyframe-class"></a>CBaseKeyFrame, classe

Implémente les fonctionnalités de base d'une image clé.

## <a name="syntax"></a>Syntaxe

```
class CBaseKeyFrame : public CObject;
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CBaseKeyFrame::CBaseKeyFrame](#cbasekeyframe)|Construit un objet keyframe.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CBaseKeyFrame::AddToStoryboard](#addtostoryboard)|Ajoute un cadre clé au storyboard.|
|[CBaseKeyFrame::GetAnimationKeyframe](#getanimationkeyframe)|Retourne la valeur keyframe sous-jacente.|
|[CBaseKeyFrame::IsAdded](#isadded)|Indique si un cadre clé a été ajouté au storyboard.|
|[CBaseKeyFrame::IsKeyframeAtOffset](#iskeyframeatoffset)|Précise si le cadre clé doit être ajouté au storyboard à compensation, ou après la transition.|

### <a name="protected-data-members"></a>Membres de données protégés

|Nom|Description|
|----------|-----------------|
|[CBaseKeyFrame::m_bAdded](#m_badded)|Précise si ce cadre clé a été ajouté à un storyboard.|
|[CBaseKeyFrame::m_bIsKeyframeAtOffset](#m_biskeyframeatoffset)|Précise si ce cadre clé devrait être ajouté au storyboard à un décalage d’un autre cadre clé existant, ou à la fin d’une certaine transition.|
|[CBaseKeyFrame::m_keyframe](#m_keyframe)|Représente un cadre d’API d’animation Windows. Lorsqu’un cadre clé n’est pas paralé, il est réglé sur la valeur prédéfinie UI_ANIMATION_KEYFRAME_STORYBOARD_START.|

## <a name="remarks"></a>Notes

Encapsule UI_ANIMATION_KEYFRAME variable. Sert de classe de base pour toute mise en œuvre de keyframe. Un cadre clé représente un moment dans le temps dans un storyboard et peut être utilisé pour spécifier les heures de début et de fin des transitions. Il existe deux types de cadres clés - les cadres clés ajoutés au storyboard à la compensation spécifiée (dans le temps), ou les cadres clés ajoutés après la transition spécifiée. Étant donné que les durées de certaines transitions ne peuvent pas être connues avant le début de l’animation, les valeurs réelles de certains cadres clés sont déterminées au moment de la course seulement. Étant donné que les cadres clés peuvent dépendre des transitions, qui dépendent à leur tour des cadres clés, il est important d’éviter des récursions infinies lors de la construction de chaînes de porte-clés.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

`CBaseKeyFrame`

## <a name="requirements"></a>Spécifications

**En-tête :** afxanimationcontroller.h

## <a name="cbasekeyframeaddtostoryboard"></a><a name="addtostoryboard"></a>CBaseKeyFrame::AddToStoryboard

Ajoute un cadre clé au storyboard.

```
virtual BOOL AddToStoryboard(
    IUIAnimationStoryboard* pStoryboard,
    BOOL bDeepAdd);
```

### <a name="parameters"></a>Paramètres

*pStoryboard (en)*<br/>
Un pointeur à un storyboard.

*bDeepAdd (en)*<br/>
Si ce paramètre est VRAI et que le cadre clé ajouté dépend d’un autre cadre clé ou transition, cette méthode tente d’ajouter ce cadre clé ou de passer au storyboard en premier.

### <a name="return-value"></a>Valeur de retour

VRAI si keyframe a été ajouté à storyboard avec succès; autrement FALSE.

### <a name="remarks"></a>Notes

Cette méthode est appelée à ajouter un cadre clé au storyboard.

## <a name="cbasekeyframecbasekeyframe"></a><a name="cbasekeyframe"></a>CBaseKeyFrame::CBaseKeyFrame

Construit un objet keyframe.

```
CBaseKeyFrame();
```

## <a name="cbasekeyframegetanimationkeyframe"></a><a name="getanimationkeyframe"></a>CBaseKeyFrame::GetAnimationKeyframe

Retourne la valeur keyframe sous-jacente.

```
UI_ANIMATION_KEYFRAME GetAnimationKeyframe() const;
```

### <a name="return-value"></a>Valeur de retour

Un cadre clé actuel. La valeur par défaut est UI_ANIMATION_KEYFRAME_STORYBOARD_START.

### <a name="remarks"></a>Notes

Il s’agit d’un accessoireur de la valeur sous-jacente de la clé.

## <a name="cbasekeyframeisadded"></a><a name="isadded"></a>CBaseKeyFrame::IsAdded

Indique si un cadre clé a été ajouté au storyboard.

```
BOOL IsAdded() const;
```

### <a name="return-value"></a>Valeur de retour

VRAI si un cadre clé est ajouté à un storyboard; FALSE otehrwise.

### <a name="remarks"></a>Notes

Dans la classe de base IsAdded retourne toujours VRAI, mais il est remplacé dans les classes dérivées.

## <a name="cbasekeyframeiskeyframeatoffset"></a><a name="iskeyframeatoffset"></a>CBaseKeyFrame::IsKeyframeAtOffset

Précise si le cadre clé doit être ajouté au storyboard à compensation, ou après la transition.

```
BOOL IsKeyframeAtOffset() const;
```

### <a name="return-value"></a>Valeur de retour

VRAI si le cadre clé doit être ajouté au storyboard à une compensation spécifiée. FALSE si le cadre clé doit être ajouté au storyboard après une certaine transition.

### <a name="remarks"></a>Notes

Précise si le cadre clé doit être ajouté au storyboard à compensation. Le décalage ou la transition doit être spécifié dans une classe dérivée.

## <a name="cbasekeyframem_badded"></a><a name="m_badded"></a>CBaseKeyFrame::m_bAdded

Précise si ce cadre clé a été ajouté à un storyboard.

```
BOOL m_bAdded;
```

## <a name="cbasekeyframem_biskeyframeatoffset"></a><a name="m_biskeyframeatoffset"></a>CBaseKeyFrame::m_bIsKeyframeAtOffset

Précise si ce cadre clé devrait être ajouté au storyboard à un décalage d’un autre cadre clé existant, ou à la fin d’une certaine transition.

```
BOOL m_bIsKeyframeAtOffset;
```

## <a name="cbasekeyframem_keyframe"></a><a name="m_keyframe"></a>CBaseKeyFrame::m_keyframe

Représente un cadre d’API d’animation Windows. Lorsqu’un cadre clé n’est pas paralé, il est réglé sur la valeur prédéfinie UI_ANIMATION_KEYFRAME_STORYBOARD_START.

```
UI_ANIMATION_KEYFRAME m_keyframe;
```

## <a name="see-also"></a>Voir aussi

[Classes](../../mfc/reference/mfc-classes.md)
