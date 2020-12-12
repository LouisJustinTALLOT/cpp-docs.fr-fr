---
description: 'En savoir plus sur : classe CBaseKeyFrame,'
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
ms.openlocfilehash: 0bebd91183eab9be71e8df4928dc621565718cb9
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97261254"
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
|[CBaseKeyFrame, :: CBaseKeyFrame,](#cbasekeyframe)|Construit un objet KeyFrame.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CBaseKeyFrame, :: AddToStoryboard](#addtostoryboard)|Ajoute une image clé au Storyboard.|
|[CBaseKeyFrame, :: GetAnimationKeyframe](#getanimationkeyframe)|Retourne la valeur de l’image clé sous-jacente.|
|[CBaseKeyFrame, :: IsAdded](#isadded)|Indique si une image clé a été ajoutée à la table de montage séquentiel.|
|[CBaseKeyFrame, :: IsKeyframeAtOffset](#iskeyframeatoffset)|Spécifie si l’image clé doit être ajoutée au Storyboard au décalage ou après la transition.|

### <a name="protected-data-members"></a>Membres de données protégés

|Nom|Description|
|----------|-----------------|
|[CBaseKeyFrame, :: m_bAdded](#m_badded)|Spécifie si cette image clé a été ajoutée à une table de montage séquentiel.|
|[CBaseKeyFrame, :: m_bIsKeyframeAtOffset](#m_biskeyframeatoffset)|Spécifie si cette image clé doit être ajoutée au Storyboard à un offset à partir d’une autre image clé existante ou à la fin d’une transition.|
|[CBaseKeyFrame, :: m_keyframe](#m_keyframe)|Représente une image clé de l’API d’animation Windows. Quand une image clé n’est pas initialisée, elle est définie sur la valeur prédéfinie UI_ANIMATION_KEYFRAME_STORYBOARD_START.|

## <a name="remarks"></a>Notes

Encapsule UI_ANIMATION_KEYFRAME variable. Sert de classe de base pour n’importe quelle implémentation d’image clé. Une image clé représente un moment dans le temps au sein d’une table de montage séquentiel et peut être utilisée pour spécifier les heures de début et de fin des transitions. Il existe deux types d’images clés : les images clés ajoutées à la table de montage séquentiel à l’offset spécifié (dans le temps), ou les images clés ajoutées après la transition spécifiée. Étant donné que les durées de certaines transitions ne peuvent pas être connues avant le démarrage de l’animation, les valeurs réelles de certaines images clés sont déterminées uniquement au moment de l’exécution. Étant donné que les images clés peuvent dépendre des transitions, qui à leur tour dépendent des images clés, il est important d’éviter les récurrences infinies lors de la création de chaînes d’images clés.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

`CBaseKeyFrame`

## <a name="requirements"></a>Spécifications

**En-tête :** afxanimationcontroller.h

## <a name="cbasekeyframeaddtostoryboard"></a><a name="addtostoryboard"></a> CBaseKeyFrame, :: AddToStoryboard

Ajoute une image clé au Storyboard.

```
virtual BOOL AddToStoryboard(
    IUIAnimationStoryboard* pStoryboard,
    BOOL bDeepAdd);
```

### <a name="parameters"></a>Paramètres

*pStoryboard*<br/>
Pointeur vers une table de montage séquentiel.

*bDeepAdd*<br/>
Si ce paramètre a la valeur TRUE et que l’image clé ajoutée dépend d’une autre image clé ou transition, cette méthode tente d’abord d’ajouter cette image clé ou d’effectuer une transition vers le Storyboard.

### <a name="return-value"></a>Valeur renvoyée

TRUE si l’image clé a été correctement ajoutée au Storyboard ; Sinon, FALSe.

### <a name="remarks"></a>Notes

Cette méthode est appelée pour ajouter une image clé au Storyboard.

## <a name="cbasekeyframecbasekeyframe"></a><a name="cbasekeyframe"></a> CBaseKeyFrame, :: CBaseKeyFrame,

Construit un objet KeyFrame.

```
CBaseKeyFrame();
```

## <a name="cbasekeyframegetanimationkeyframe"></a><a name="getanimationkeyframe"></a> CBaseKeyFrame, :: GetAnimationKeyframe

Retourne la valeur de l’image clé sous-jacente.

```
UI_ANIMATION_KEYFRAME GetAnimationKeyframe() const;
```

### <a name="return-value"></a>Valeur renvoyée

Image clé actuelle. La valeur par défaut est UI_ANIMATION_KEYFRAME_STORYBOARD_START.

### <a name="remarks"></a>Notes

Il s’agit d’un accesseur à la valeur de l’image clé sous-jacente.

## <a name="cbasekeyframeisadded"></a><a name="isadded"></a> CBaseKeyFrame, :: IsAdded

Indique si une image clé a été ajoutée à la table de montage séquentiel.

```
BOOL IsAdded() const;
```

### <a name="return-value"></a>Valeur renvoyée

TRUE si une image clé est ajoutée à un Storyboard ; ; sinon FALSe.

### <a name="remarks"></a>Notes

Dans la classe de base IsAdded retourne toujours la valeur TRUE, mais elle est substituée dans les classes dérivées.

## <a name="cbasekeyframeiskeyframeatoffset"></a><a name="iskeyframeatoffset"></a> CBaseKeyFrame, :: IsKeyframeAtOffset

Spécifie si l’image clé doit être ajoutée au Storyboard au décalage ou après la transition.

```
BOOL IsKeyframeAtOffset() const;
```

### <a name="return-value"></a>Valeur renvoyée

TRUE si l’image clé doit être ajoutée à la table de montage séquentiel à un offset spécifié. FALSe si l’image clé doit être ajoutée au storyboard après une certaine transition.

### <a name="remarks"></a>Notes

Spécifie si l’image clé doit être ajoutée à la table de montage séquentiel à l’offset. Le décalage ou la transition doivent être spécifiés dans une classe dérivée.

## <a name="cbasekeyframem_badded"></a><a name="m_badded"></a> CBaseKeyFrame, :: m_bAdded

Spécifie si cette image clé a été ajoutée à une table de montage séquentiel.

```
BOOL m_bAdded;
```

## <a name="cbasekeyframem_biskeyframeatoffset"></a><a name="m_biskeyframeatoffset"></a> CBaseKeyFrame, :: m_bIsKeyframeAtOffset

Spécifie si cette image clé doit être ajoutée au Storyboard à un offset à partir d’une autre image clé existante ou à la fin d’une transition.

```
BOOL m_bIsKeyframeAtOffset;
```

## <a name="cbasekeyframem_keyframe"></a><a name="m_keyframe"></a> CBaseKeyFrame, :: m_keyframe

Représente une image clé de l’API d’animation Windows. Quand une image clé n’est pas initialisée, elle est définie sur la valeur prédéfinie UI_ANIMATION_KEYFRAME_STORYBOARD_START.

```
UI_ANIMATION_KEYFRAME m_keyframe;
```

## <a name="see-also"></a>Voir aussi

[Classes](../../mfc/reference/mfc-classes.md)
