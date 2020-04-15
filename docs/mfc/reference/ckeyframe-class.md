---
title: CKeyFrame, classe
ms.date: 11/04/2016
f1_keywords:
- CKeyFrame
- AFXANIMATIONCONTROLLER/CKeyFrame
- AFXANIMATIONCONTROLLER/CKeyFrame::CKeyFrame
- AFXANIMATIONCONTROLLER/CKeyFrame::AddToStoryboard
- AFXANIMATIONCONTROLLER/CKeyFrame::AddToStoryboardAfterTransition
- AFXANIMATIONCONTROLLER/CKeyFrame::AddToStoryboardAtOffset
- AFXANIMATIONCONTROLLER/CKeyFrame::GetExistingKeyframe
- AFXANIMATIONCONTROLLER/CKeyFrame::GetOffset
- AFXANIMATIONCONTROLLER/CKeyFrame::GetTransition
- AFXANIMATIONCONTROLLER/CKeyFrame::m_offset
- AFXANIMATIONCONTROLLER/CKeyFrame::m_pExistingKeyFrame
- AFXANIMATIONCONTROLLER/CKeyFrame::m_pTransition
helpviewer_keywords:
- CKeyFrame [MFC], CKeyFrame
- CKeyFrame [MFC], AddToStoryboard
- CKeyFrame [MFC], AddToStoryboardAfterTransition
- CKeyFrame [MFC], AddToStoryboardAtOffset
- CKeyFrame [MFC], GetExistingKeyframe
- CKeyFrame [MFC], GetOffset
- CKeyFrame [MFC], GetTransition
- CKeyFrame [MFC], m_offset
- CKeyFrame [MFC], m_pExistingKeyFrame
- CKeyFrame [MFC], m_pTransition
ms.assetid: d050a562-20f6-4c65-8ce5-ccb3aef1a20e
ms.openlocfilehash: f535503338a82c7cc70455ae6a08cdab0f13c624
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372294"
---
# <a name="ckeyframe-class"></a>CKeyFrame, classe

Représente une image clé de l'animation.

## <a name="syntax"></a>Syntaxe

```
class CKeyFrame : public CBaseKeyFrame;
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CKeyFrame::CKeyFrame](#ckeyframe)|Surchargé. Construit un cadre clé qui dépend d’autres cadres clés.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CKeyFrame::AddToStoryboard](#addtostoryboard)|Ajoute un cadre clé à un storyboard. (Overrides [CBaseKeyFrame::AddToStoryboard](../../mfc/reference/cbasekeyframe-class.md#addtostoryboard).)|
|[CKeyFrame::AddToStoryboardAfterTransition](#addtostoryboardaftertransition)|Ajoute un cadre clé au storyboard après la transition.|
|[CKeyFrame::AddToStoryboardAtOffset](#addtostoryboardatoffset)|Ajoute un cadre clé au storyboard à la compensation.|
|[CKeyFrame::GetExistingKeyframe](#getexistingkeyframe)|Retourne un pointeur à un cadre clé dont dépend ce cadre clé.|
|[CKeyFrame::GetOffset](#getoffset)|Retourne un décalage d’autres cadres clés.|
|[CKeyFrame::GetTransition](#gettransition)|Retourne un pointeur à une transition dont dépend ce cadre clé.|

### <a name="protected-data-members"></a>Membres de données protégés

|Nom|Description|
|----------|-----------------|
|[CKeyFrame::m_offset](#m_offset)|Spécifie le décalage de ce cadre clé à partir d’un cadre clé stocké dans m_pExistingKeyFrame.|
|[CKeyFrame::m_pExistingKeyFrame](#m_pexistingkeyframe)|Stocke un pointeur sur un keframe existant. Ce cadre clé est ajouté au storyboard avec m_offset à la clé existante.|
|[CKeyFrame::m_pTransition](#m_ptransition)|Stocke un pointeur de transtion qui commence à ce cadre clé.|

## <a name="remarks"></a>Notes

Cette classe met en œuvre un cadre d’animation. Un cadre clé représente un moment dans le temps dans un storyboard et peut être utilisé pour spécifier les heures de début et de fin des transitions. Un cadre clé peut être basé sur d’autres cadres clés et avoir un décalage (en quelques secondes) de celui-ci, ou peut être basé sur une transition et représenter un moment dans le temps où cette transition se termine.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CBaseKeyFrame](../../mfc/reference/cbasekeyframe-class.md)

[CKeyFrame](../../mfc/reference/ckeyframe-class.md)

## <a name="requirements"></a>Spécifications

**En-tête :** afxanimationcontroller.h

## <a name="ckeyframeaddtostoryboard"></a><a name="addtostoryboard"></a>CKeyFrame::AddToStoryboard

Ajoute un cadre clé à un storyboard.

```
virtual BOOL AddToStoryboard(
    IUIAnimationStoryboard* pStoryboard,
    BOOL bDeepAdd);
```

### <a name="parameters"></a>Paramètres

*pStoryboard (en)*<br/>
Un pointeur à un storyboard.

*bDeepAdd (en)*<br/>
Précise s’il faut ajouter du cadre clé ou la transition de façon récursive.

### <a name="return-value"></a>Valeur de retour

VRAI, si keyframe a été ajouté avec succès.

### <a name="remarks"></a>Notes

Cette méthode ajoute un cadre clé au storyboard. Si cela dépend d’un autre cadre clé ou de transition et bDeepAdd est VRAI, cette méthode tente de les ajouter de façon récursive.

## <a name="ckeyframeaddtostoryboardaftertransition"></a><a name="addtostoryboardaftertransition"></a>CKeyFrame::AddToStoryboardAfterTransition

Ajoute un cadre clé au storyboard après la transition.

```
BOOL AddToStoryboardAfterTransition(
    IUIAnimationStoryboard* pStoryboard,
    BOOL bDeepAdd);
```

### <a name="parameters"></a>Paramètres

*pStoryboard (en)*<br/>
Un pointeur à un storyboard.

*bDeepAdd (en)*<br/>
Précise s’il faut ajouter une transition de façon récursive.

### <a name="return-value"></a>Valeur de retour

VRAI, si keyframe a été ajouté avec succès.

### <a name="remarks"></a>Notes

Cette fonction est appelée par le cadre pour ajouter un cadre clé à storyboard après la transition.

## <a name="ckeyframeaddtostoryboardatoffset"></a><a name="addtostoryboardatoffset"></a>CKeyFrame::AddToStoryboardAtOffset

Ajoute un cadre clé au storyboard à la compensation.

```
virtual BOOL AddToStoryboardAtOffset(
    IUIAnimationStoryboard* pStoryboard,
    BOOL bDeepAdd);
```

### <a name="parameters"></a>Paramètres

*pStoryboard (en)*<br/>
Un pointeur à un storyboard.

*bDeepAdd (en)*<br/>
Précise s’il faut ajouter un cadre clé dont ce cadre clé dépend de la récursivité.

### <a name="return-value"></a>Valeur de retour

VRAI, si keyframe a été ajouté avec succès.

### <a name="remarks"></a>Notes

Cette fonction est appelée par le cadre pour ajouter un cadre clé à storyboard à compensation.

## <a name="ckeyframeckeyframe"></a><a name="ckeyframe"></a>CKeyFrame::CKeyFrame

Construit un cadre clé qui dépend d’une transition.

```
CKeyFrame(CBaseTransition* pTransition);

CKeyFrame(
    CBaseKeyFrame* pKeyframe,
    UI_ANIMATION_SECONDS offset = 0.0);
```

### <a name="parameters"></a>Paramètres

*pTransition*<br/>
Un pointeur vers une transition.

*pKeyframe (en)*<br/>
Un pointeur à keyframe.

*offset*<br/>
Décalage, en quelques secondes, à partir de keyframe spécifié par pKeyframe.

### <a name="remarks"></a>Notes

Le cadre de clé construit représentera un moment dans le temps dans un storyboard lorsque la transition spécifiée se termine.

## <a name="ckeyframegetexistingkeyframe"></a><a name="getexistingkeyframe"></a>CKeyFrame::GetExistingKeyframe

Retourne un pointeur à un cadre clé dont dépend ce cadre clé.

```
CBaseKeyFrame* GetExistingKeyframe();
```

### <a name="return-value"></a>Valeur de retour

Un pointeur valide pour le cadre de clé, ou NULL si ce cadre clé ne dépend pas d’autres cadres clés.

### <a name="remarks"></a>Notes

Il s’agit d’un accessoir-clé d’un cadre clé dont dépend ce cadre clé.

## <a name="ckeyframegetoffset"></a><a name="getoffset"></a>CKeyFrame::GetOffset

Retourne un décalage d’autres cadres clés.

```
UI_ANIMATION_SECONDS GetOffset();
```

### <a name="return-value"></a>Valeur de retour

Un décalage en quelques secondes à partir d’autres cadres clés.

### <a name="remarks"></a>Notes

Cette méthode devrait être appelée pour déterminer un décalage en quelques secondes à partir d’autres cadres clés.

## <a name="ckeyframegettransition"></a><a name="gettransition"></a>CKeyFrame::GetTransition

Retourne un pointeur à une transition dont dépend ce cadre clé.

```
CBaseTransition* GetTransition();
```

### <a name="return-value"></a>Valeur de retour

Un pointeur valide à la transition, ou NULL si ce cadre clé ne dépend pas de la transition.

### <a name="remarks"></a>Notes

Il s’agit d’un accessoirier à une transition dont dépend ce cadre clé.

## <a name="ckeyframem_offset"></a><a name="m_offset"></a>CKeyFrame::m_offset

Spécifie le décalage de ce cadre clé à partir d’un cadre clé stocké dans m_pExistingKeyFrame.

```
UI_ANIMATION_SECONDS m_offset;
```

## <a name="ckeyframem_pexistingkeyframe"></a><a name="m_pexistingkeyframe"></a>CKeyFrame::m_pExistingKeyFrame

Stocke un pointeur sur un keframe existant. Ce cadre clé est ajouté au storyboard avec m_offset à la clé existante.

```
CBaseKeyFrame* m_pExistingKeyFrame;
```

## <a name="ckeyframem_ptransition"></a><a name="m_ptransition"></a>CKeyFrame::m_pTransition

Stocke un pointeur de transtion qui commence à ce cadre clé.

```
CBaseTransition* m_pTransition;
```

## <a name="see-also"></a>Voir aussi

[Classes](../../mfc/reference/mfc-classes.md)
