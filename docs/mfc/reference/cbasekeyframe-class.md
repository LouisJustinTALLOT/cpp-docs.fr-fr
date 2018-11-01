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
ms.openlocfilehash: 850ce46f524d9069609c1e5809c091c18bd58ee4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50618242"
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
|[CBaseKeyFrame::AddToStoryboard](#addtostoryboard)|Ajoute une image clé au storyboard.|
|[CBaseKeyFrame::GetAnimationKeyframe](#getanimationkeyframe)|Retourne la valeur d’image clé sous-jacente.|
|[CBaseKeyFrame::IsAdded](#isadded)|Indique si une image clé a été ajoutée au storyboard.|
|[CBaseKeyFrame::IsKeyframeAtOffset](#iskeyframeatoffset)|Spécifie si l’image clé doit être ajoutée au storyboard à l’offset, ou après la transition.|

### <a name="protected-data-members"></a>Membres de données protégés

|Name|Description|
|----------|-----------------|
|[CBaseKeyFrame::m_bAdded](#m_badded)|Spécifie si cette image clé a été ajoutée à une table de montage séquentiel.|
|[CBaseKeyFrame::m_bIsKeyframeAtOffset](#m_biskeyframeatoffset)|Spécifie si cette image clé doit être ajoutée au storyboard à un offset à partir d’une autre image clé existante, ou à la fin d’une transition.|
|[CBaseKeyFrame::m_keyframe](#m_keyframe)|Représente une image clé API d’Animation de Windows. Lorsqu’une image clé n’est pas initialisée, il est défini à la valeur prédéfinie UI_ANIMATION_KEYFRAME_STORYBOARD_START.|

## <a name="remarks"></a>Notes

Encapsule la variable UI_ANIMATION_KEYFRAME. Sert de classe de base pour n’importe quelle implémentation de l’image clé. Une image clé représente un moment donné dans une table de montage séquentiel et peut être utilisée pour spécifier les heures de début et de fin des transitions. Il existe deux types d’images clés : images clés ajoutées au storyboard à l’offset spécifié (dans le temps) ou images clés ajoutées après la transition spécifiée. Étant donné que les durées de certaines transitions ne peut pas être connues avant le démarrage de l’animation, les valeurs réelles de certaines images clés sont déterminées lors de l’exécution uniquement. Étant donné que les images clés peuvent dépendre des transitions, qui à leur tour dépendent des images clés, il est important éviter les récurrences infinies lors de la création de chaînes d’images clés.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

`CBaseKeyFrame`

## <a name="requirements"></a>Configuration requise

**En-tête :** afxanimationcontroller.h

##  <a name="addtostoryboard"></a>  CBaseKeyFrame::AddToStoryboard

Ajoute une image clé au storyboard.

```
virtual BOOL AddToStoryboard(
    IUIAnimationStoryboard* pStoryboard,
    BOOL bDeepAdd);
```

### <a name="parameters"></a>Paramètres

*pStoryboard*<br/>
Pointeur vers une table de montage séquentiel.

*que bDeepAdd*<br/>
Si ce paramètre a la valeur TRUE et que l’image clé en cours d’ajout dépend d’une autre image clé ou transition, cette méthode essaie d’ajouter cette image clé ou une transition au storyboard tout d’abord.

### <a name="return-value"></a>Valeur de retour

TRUE si l’image clé a été ajouté à la table de montage séquentiel avec succès ; Sinon, FALSE.

### <a name="remarks"></a>Notes

Cette méthode est appelée pour ajouter une image clé au storyboard.

##  <a name="cbasekeyframe"></a>  CBaseKeyFrame::CBaseKeyFrame

Construit un objet keyframe.

```
CBaseKeyFrame();
```

##  <a name="getanimationkeyframe"></a>  CBaseKeyFrame::GetAnimationKeyframe

Retourne la valeur d’image clé sous-jacente.

```
UI_ANIMATION_KEYFRAME GetAnimationKeyframe() const;
```

### <a name="return-value"></a>Valeur de retour

Une image clé actuelle. La valeur par défaut est UI_ANIMATION_KEYFRAME_STORYBOARD_START.

### <a name="remarks"></a>Notes

Il s’agit d’un accesseur à la valeur d’image clé sous-jacente.

##  <a name="isadded"></a>  CBaseKeyFrame::IsAdded

Indique si une image clé a été ajoutée au storyboard.

```
BOOL IsAdded() const;
```

### <a name="return-value"></a>Valeur de retour

TRUE si une image clé est ajoutée à une table de montage séquentiel ; Sinon, FALSE.

### <a name="remarks"></a>Notes

Dans la classe de base IsAdded retourne toujours TRUE, mais elle est substituée dans les classes dérivées.

##  <a name="iskeyframeatoffset"></a>  CBaseKeyFrame::IsKeyframeAtOffset

Spécifie si l’image clé doit être ajoutée au storyboard à l’offset, ou après la transition.

```
BOOL IsKeyframeAtOffset() const;
```

### <a name="return-value"></a>Valeur de retour

TRUE si l’image clé doit être ajoutée au storyboard à un offset spécifié. FALSE si l’image clé doit être ajoutée au storyboard après une transition.

### <a name="remarks"></a>Notes

Spécifie si l’image clé doit être ajoutée au storyboard à l’offset. Le décalage ou transition doit être spécifiée dans une classe dérivée.

##  <a name="m_badded"></a>  CBaseKeyFrame::m_bAdded

Spécifie si cette image clé a été ajoutée à une table de montage séquentiel.

```
BOOL m_bAdded;
```

##  <a name="m_biskeyframeatoffset"></a>  CBaseKeyFrame::m_bIsKeyframeAtOffset

Spécifie si cette image clé doit être ajoutée au storyboard à un offset à partir d’une autre image clé existante, ou à la fin d’une transition.

```
BOOL m_bIsKeyframeAtOffset;
```

##  <a name="m_keyframe"></a>  CBaseKeyFrame::m_keyframe

Représente une image clé API d’Animation de Windows. Lorsqu’une image clé n’est pas initialisée, il est défini à la valeur prédéfinie UI_ANIMATION_KEYFRAME_STORYBOARD_START.

```
UI_ANIMATION_KEYFRAME m_keyframe;
```

## <a name="see-also"></a>Voir aussi

[Classes](../../mfc/reference/mfc-classes.md)
