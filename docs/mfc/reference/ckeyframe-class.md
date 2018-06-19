---
title: CKeyFrame, classe | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9a9e9ff3d6e3e4bcccf8e9ebd46f791f60f1cc37
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33367183"
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
|[CKeyFrame::CKeyFrame](#ckeyframe)|Surchargé. Construit une image clé qui dépend d’autres images clés.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[CKeyFrame::AddToStoryboard](#addtostoryboard)|Ajoute une image clé à un plan conceptuel. (Substitue [CBaseKeyFrame::AddToStoryboard](../../mfc/reference/cbasekeyframe-class.md#addtostoryboard).)|  
|[CKeyFrame::AddToStoryboardAfterTransition](#addtostoryboardaftertransition)|Ajoute une image clé au storyboard après la transition.|  
|[CKeyFrame::AddToStoryboardAtOffset](#addtostoryboardatoffset)|Ajoute une image clé au storyboard à l’offset.|  
|[CKeyFrame::GetExistingKeyframe](#getexistingkeyframe)|Retourne un pointeur vers une image clé que dépend de cette image clé.|  
|[CKeyFrame::GetOffset](#getoffset)|Retourne un offset à partir d’autres images clés.|  
|[CKeyFrame::GetTransition](#gettransition)|Retourne un pointeur à une transition dont dépend cette image clé.|  
  
### <a name="protected-data-members"></a>Membres de données protégés  
  
|Name|Description|  
|----------|-----------------|  
|[CKeyFrame::m_offset](#m_offset)|Spécifie le décalage de l’image clé à partir d’une image clé stockée dans m_pExistingKeyFrame.|  
|[CKeyFrame::m_pExistingKeyFrame](#m_pexistingkeyframe)|Stocke un pointeur vers une image clé existante. Cette image clé est ajoutée au storyboard avec m_offset à l’image clé existante.|  
|[CKeyFrame::m_pTransition](#m_ptransition)|Stocke un pointeur vers la transition qui commence à cette image clé.|  
  
## <a name="remarks"></a>Notes  
 Cette classe implémente une image clé de l’animation. Une image clé représente un moment dans une table de montage séquentiel et peut être utilisée pour indiquer les heures de début et de fin des transitions. Une image clé peut être basée sur les autres images clés et avoir un décalage (en secondes) à partir de celui-ci, ou peut être basée sur une transition et représente un moment dans l’heure de fin de cette transition.  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CBaseKeyFrame](../../mfc/reference/cbasekeyframe-class.md)  
  
 [CKeyFrame](../../mfc/reference/ckeyframe-class.md)  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** afxanimationcontroller.h  
  
##  <a name="addtostoryboard"></a>  CKeyFrame::AddToStoryboard  
 Ajoute une image clé à un plan conceptuel.  
  
```  
virtual BOOL AddToStoryboard(
    IUIAnimationStoryboard* pStoryboard,  
    BOOL bDeepAdd);
```  
  
### <a name="parameters"></a>Paramètres  
 `pStoryboard`  
 Pointeur vers un plan conceptuel.  
  
 `bDeepAdd`  
 Spécifie s’il faut ajouter l’image clé ou une transition de manière récursive.  
  
### <a name="return-value"></a>Valeur de retour  
 TRUE si l’image clé a été ajoutée avec succès.  
  
### <a name="remarks"></a>Notes  
 Cette méthode ajoute une image clé d’animation. Si elle dépend d’autres images clés ou de transition et que bDeepAdd a la valeur TRUE, cette méthode essaie d’ajouter de manière récursive.  
  
##  <a name="addtostoryboardaftertransition"></a>  CKeyFrame::AddToStoryboardAfterTransition  
 Ajoute une image clé au storyboard après la transition.  
  
```  
BOOL AddToStoryboardAfterTransition(
    IUIAnimationStoryboard* pStoryboard,  
    BOOL bDeepAdd);
```  
  
### <a name="parameters"></a>Paramètres  
 `pStoryboard`  
 Pointeur vers un plan conceptuel.  
  
 `bDeepAdd`  
 Spécifie s’il faut ajouter une transition de manière récursive.  
  
### <a name="return-value"></a>Valeur de retour  
 TRUE si l’image clé a été ajoutée avec succès.  
  
### <a name="remarks"></a>Notes  
 Cette fonction est appelée par l’infrastructure pour ajouter une image clé au storyboard après la transition.  
  
##  <a name="addtostoryboardatoffset"></a>  CKeyFrame::AddToStoryboardAtOffset  
 Ajoute une image clé au storyboard à l’offset.  
  
```  
virtual BOOL AddToStoryboardAtOffset(
    IUIAnimationStoryboard* pStoryboard,  
    BOOL bDeepAdd);
```  
  
### <a name="parameters"></a>Paramètres  
 `pStoryboard`  
 Pointeur vers un plan conceptuel.  
  
 `bDeepAdd`  
 Spécifie si cette image clé dépendante de façon récursive pour ajouter une image clé.  
  
### <a name="return-value"></a>Valeur de retour  
 TRUE si l’image clé a été ajoutée avec succès.  
  
### <a name="remarks"></a>Notes  
 Cette fonction est appelée par l’infrastructure pour ajouter une image clé au storyboard à l’offset.  
  
##  <a name="ckeyframe"></a>  CKeyFrame::CKeyFrame  
 Construit une image clé qui dépend d’une transition.  
  
```  
CKeyFrame(CBaseTransition* pTransition);

 
CKeyFrame(
    CBaseKeyFrame* pKeyframe,  
    UI_ANIMATION_SECONDS offset = 0.0);
```  
  
### <a name="parameters"></a>Paramètres  
 `pTransition`  
 Pointeur vers une transition.  
  
 `pKeyframe`  
 Pointeur vers l’image clé.  
  
 `offset`  
 Offset, en secondes, à partir de l’image clé spécifiée par pKeyframe.  
  
### <a name="remarks"></a>Notes  
 Les images clés construites représentent un moment dans le temps au sein d’une table de montage séquentiel lorsque la transition spécifiée se termine.  
  
##  <a name="getexistingkeyframe"></a>  CKeyFrame::GetExistingKeyframe  
 Retourne un pointeur vers une image clé que dépend de cette image clé.  
  
```  
CBaseKeyFrame* GetExistingKeyframe();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Pointeur valid vers l’image clé, ou NULL si cette image clé ne dépend pas d’autres images clés.  
  
### <a name="remarks"></a>Notes  
 Il s’agit d’un accesseur à un moment précis que dépend de cette image clé.  
  
##  <a name="getoffset"></a>  CKeyFrame::GetOffset  
 Retourne un offset à partir d’autres images clés.  
  
```  
UI_ANIMATION_SECONDS GetOffset();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Un décalage en secondes à partir d’autres images clés.  
  
### <a name="remarks"></a>Notes  
 Cette méthode doit être appelée pour déterminer un offset en secondes à partir d’autres images clés.  
  
##  <a name="gettransition"></a>  CKeyFrame::GetTransition  
 Retourne un pointeur à une transition dont dépend cette image clé.  
  
```  
CBaseTransition* GetTransition();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Obtenir un pointeur valide vers la transition, ou NULL si cette image clé ne dépendante pas de transition.  
  
### <a name="remarks"></a>Notes  
 Il s’agit d’un accesseur à une transition dont dépend cette image clé.  
  
##  <a name="m_offset"></a>  CKeyFrame::m_offset  
 Spécifie le décalage de l’image clé à partir d’une image clé stockée dans m_pExistingKeyFrame.  
  
```  
UI_ANIMATION_SECONDS m_offset;  
```  
  
##  <a name="m_pexistingkeyframe"></a>  CKeyFrame::m_pExistingKeyFrame  
 Stocke un pointeur vers une image clé existante. Cette image clé est ajoutée au storyboard avec m_offset à l’image clé existante.  
  
```  
CBaseKeyFrame* m_pExistingKeyFrame;  
```  
  
##  <a name="m_ptransition"></a>  CKeyFrame::m_pTransition  
 Stocke un pointeur vers la transition qui commence à cette image clé.  
  
```  
CBaseTransition* m_pTransition;  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Classes](../../mfc/reference/mfc-classes.md)
