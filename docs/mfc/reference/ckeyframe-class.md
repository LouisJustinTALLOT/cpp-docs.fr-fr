---
description: 'En savoir plus sur : classe CKeyFrame,'
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
ms.openlocfilehash: ec6aa45484965afbf0c636a1eed26a3d4a63e426
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97236878"
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
|[CKeyFrame, :: CKeyFrame,](#ckeyframe)|Surchargé. Construit une image clé qui dépend d’une autre image clé.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CKeyFrame, :: AddToStoryboard](#addtostoryboard)|Ajoute une image clé à une table de montage séquentiel. (Substitue [CBaseKeyFrame, :: AddToStoryboard](../../mfc/reference/cbasekeyframe-class.md#addtostoryboard).)|
|[CKeyFrame, :: AddToStoryboardAfterTransition](#addtostoryboardaftertransition)|Ajoute une image clé au storyboard après la transition.|
|[CKeyFrame, :: AddToStoryboardAtOffset](#addtostoryboardatoffset)|Ajoute une image clé au Storyboard à l’offset.|
|[CKeyFrame, :: GetExistingKeyframe](#getexistingkeyframe)|Retourne un pointeur vers une image clé dont cette image clé dépend.|
|[CKeyFrame, :: GetOffset,](#getoffset)|Retourne un offset à partir d’une autre image clé.|
|[CKeyFrame, :: GetTransition](#gettransition)|Retourne un pointeur vers une transition dont cette image clé dépend.|

### <a name="protected-data-members"></a>Membres de données protégés

|Nom|Description|
|----------|-----------------|
|[CKeyFrame, :: m_offset](#m_offset)|Spécifie le décalage de cette image clé à partir d’une image clé stockée dans m_pExistingKeyFrame.|
|[CKeyFrame, :: m_pExistingKeyFrame](#m_pexistingkeyframe)|Stocke un pointeur vers un keframe existant. Cette image clé est ajoutée à la table de montage séquentiel avec m_offset à l’image clé existante.|
|[CKeyFrame, :: m_pTransition](#m_ptransition)|Stocke un pointeur vers la transtion qui commence à cette image clé.|

## <a name="remarks"></a>Notes

Cette classe implémente une image clé d’animation. Une image clé représente un moment dans le temps au sein d’une table de montage séquentiel et peut être utilisée pour spécifier les heures de début et de fin des transitions. Une image clé peut être basée sur une autre image clé et avoir un décalage (en secondes) à partir de celle-ci, ou peut être basée sur une transition et représenter un moment où cette transition se termine.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CBaseKeyFrame,](../../mfc/reference/cbasekeyframe-class.md)

[CKeyFrame,](../../mfc/reference/ckeyframe-class.md)

## <a name="requirements"></a>Spécifications

**En-tête :** afxanimationcontroller.h

## <a name="ckeyframeaddtostoryboard"></a><a name="addtostoryboard"></a> CKeyFrame, :: AddToStoryboard

Ajoute une image clé à une table de montage séquentiel.

```
virtual BOOL AddToStoryboard(
    IUIAnimationStoryboard* pStoryboard,
    BOOL bDeepAdd);
```

### <a name="parameters"></a>Paramètres

*pStoryboard*<br/>
Pointeur vers une table de montage séquentiel.

*bDeepAdd*<br/>
Spécifie s’il faut ajouter une image clé ou une transition récursive.

### <a name="return-value"></a>Valeur renvoyée

TRUE si l’image clé a été ajoutée avec succès.

### <a name="remarks"></a>Notes

Cette méthode ajoute une image clé au Storyboard. S’il dépend d’autres images clés ou transition et que bDeepAdd a la valeur TRUE, cette méthode tente de les ajouter de manière récursive.

## <a name="ckeyframeaddtostoryboardaftertransition"></a><a name="addtostoryboardaftertransition"></a> CKeyFrame, :: AddToStoryboardAfterTransition

Ajoute une image clé au storyboard après la transition.

```
BOOL AddToStoryboardAfterTransition(
    IUIAnimationStoryboard* pStoryboard,
    BOOL bDeepAdd);
```

### <a name="parameters"></a>Paramètres

*pStoryboard*<br/>
Pointeur vers une table de montage séquentiel.

*bDeepAdd*<br/>
Spécifie s’il faut ajouter une transition de manière récursive.

### <a name="return-value"></a>Valeur renvoyée

TRUE si l’image clé a été ajoutée avec succès.

### <a name="remarks"></a>Notes

Cette fonction est appelée par l’infrastructure pour ajouter une image clé au storyboard après la transition.

## <a name="ckeyframeaddtostoryboardatoffset"></a><a name="addtostoryboardatoffset"></a> CKeyFrame, :: AddToStoryboardAtOffset

Ajoute une image clé au Storyboard à l’offset.

```
virtual BOOL AddToStoryboardAtOffset(
    IUIAnimationStoryboard* pStoryboard,
    BOOL bDeepAdd);
```

### <a name="parameters"></a>Paramètres

*pStoryboard*<br/>
Pointeur vers une table de montage séquentiel.

*bDeepAdd*<br/>
Spécifie s’il faut ajouter une image clé qui dépend de manière récursive.

### <a name="return-value"></a>Valeur renvoyée

TRUE si l’image clé a été ajoutée avec succès.

### <a name="remarks"></a>Notes

Cette fonction est appelée par l’infrastructure pour ajouter une image clé au Storyboard à l’offset.

## <a name="ckeyframeckeyframe"></a><a name="ckeyframe"></a> CKeyFrame, :: CKeyFrame,

Construit une image clé qui dépend d’une transition.

```
CKeyFrame(CBaseTransition* pTransition);

CKeyFrame(
    CBaseKeyFrame* pKeyframe,
    UI_ANIMATION_SECONDS offset = 0.0);
```

### <a name="parameters"></a>Paramètres

*pTransition*<br/>
Pointeur vers une transition.

*pKeyframe*<br/>
Pointeur vers KeyFrame.

*offset*<br/>
Décalage, en secondes, à partir de l’image clé spécifiée par pKeyframe.

### <a name="remarks"></a>Notes

L’image clé construite représente un moment dans le temps dans un Storyboard lorsque la transition spécifiée se termine.

## <a name="ckeyframegetexistingkeyframe"></a><a name="getexistingkeyframe"></a> CKeyFrame, :: GetExistingKeyframe

Retourne un pointeur vers une image clé dont cette image clé dépend.

```
CBaseKeyFrame* GetExistingKeyframe();
```

### <a name="return-value"></a>Valeur renvoyée

Pointeur valide vers KeyFrame, ou NULL si cette image clé ne dépend pas d’une autre image clé.

### <a name="remarks"></a>Notes

Il s’agit d’un accesseur à une image clé dont cette image clé dépend.

## <a name="ckeyframegetoffset"></a><a name="getoffset"></a> CKeyFrame, :: GetOffset,

Retourne un offset à partir d’une autre image clé.

```
UI_ANIMATION_SECONDS GetOffset();
```

### <a name="return-value"></a>Valeur renvoyée

Décalage en secondes à partir d’une autre image clé.

### <a name="remarks"></a>Notes

Cette méthode doit être appelée pour déterminer un décalage en secondes à partir d’une autre image clé.

## <a name="ckeyframegettransition"></a><a name="gettransition"></a> CKeyFrame, :: GetTransition

Retourne un pointeur vers une transition dont cette image clé dépend.

```
CBaseTransition* GetTransition();
```

### <a name="return-value"></a>Valeur renvoyée

Pointeur valide vers une transition, ou NULL si cette image clé ne dépend pas de la transition.

### <a name="remarks"></a>Notes

Il s’agit d’un accesseur à une transition dont cette image clé dépend.

## <a name="ckeyframem_offset"></a><a name="m_offset"></a> CKeyFrame, :: m_offset

Spécifie le décalage de cette image clé à partir d’une image clé stockée dans m_pExistingKeyFrame.

```
UI_ANIMATION_SECONDS m_offset;
```

## <a name="ckeyframem_pexistingkeyframe"></a><a name="m_pexistingkeyframe"></a> CKeyFrame, :: m_pExistingKeyFrame

Stocke un pointeur vers un keframe existant. Cette image clé est ajoutée à la table de montage séquentiel avec m_offset à l’image clé existante.

```
CBaseKeyFrame* m_pExistingKeyFrame;
```

## <a name="ckeyframem_ptransition"></a><a name="m_ptransition"></a> CKeyFrame, :: m_pTransition

Stocke un pointeur vers la transtion qui commence à cette image clé.

```
CBaseTransition* m_pTransition;
```

## <a name="see-also"></a>Voir aussi

[Classes](../../mfc/reference/mfc-classes.md)
