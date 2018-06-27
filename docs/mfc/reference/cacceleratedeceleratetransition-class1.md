---
title: CAccelerateDecelerateTransition Class1 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CAccelerateDecelerateTransition
- afxanimationcontroller/CAccelerateDecelerateTransition
dev_langs:
- C++
helpviewer_keywords:
- CAccelerateDecelerateTransition class [MFC]
ms.assetid: b1f31ee8-bb11-4ccc-b124-365fb02b025c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4342ed03991317bd030d308dbac9945734dcbd9e
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/26/2018
ms.locfileid: "36954706"
---
# <a name="cacceleratedeceleratetransition-class"></a>CAccelerateDecelerateTransition (classe)
Implémente une transition accélérer-ralentir.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CAccelerateDecelerateTransition : public CBaseTransition;  
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CAccelerateDecelerateTransition::CAccelerateDecelerateTransition](#cacceleratedeceleratetransition)|Construit un objet de transition.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[CAccelerateDecelerateTransition::Create](#create)|Appelle la bibliothèque de transition pour créer l’objet COM de transition encapsulé. (Substitue [CBaseTransition::Create](../../mfc/reference/cbasetransition-class.md#create).)|  
  
### <a name="public-data-members"></a>Membres de données publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CAccelerateDecelerateTransition::m_accelerationRatio](#m_accelerationratio)|Le rapport entre le temps consacré à l’accélération de la durée.|  
|[CAccelerateDecelerateTransition::m_decelerationRatio](#m_decelerationratio)|Le rapport entre le temps de décélération à la durée.|  
|[CAccelerateDecelerateTransition::m_duration](#m_duration)|La durée de la transition.|  
|[CAccelerateDecelerateTransition::m_finalValue](#m_finalvalue)|La valeur de la variable à la fin de la transition de l’animation.|  
  
## <a name="remarks"></a>Notes  
 Pendant une accélérer-ralentir la transition, la variable d’animation accélère et ralentit pendant la durée de la transition, se terminant à une valeur spécifiée. Vous pouvez contrôler la rapidité avec laquelle l’accélération et de décélération indépendamment, en spécifiant l’accélération différents et des ratios de décélération. Lorsque la rapidité initiale est nulle, le taux d’accélération est la fraction de la durée pendant laquelle la variable passent à l’accélération ; de même avec le taux de décélération. Si la rapidité initiale est différente de zéro, il est le moins de temps entre la rapidité qui atteint zéro et la fin de la transition. Le taux d’accélération de la décélération doivent correspondre à un maximum de 1.0. Étant donné que toutes les transitions sont effacées automatiquement, il est recommandé de les allouer à l’aide de nouvel opérateur. L’objet COM IUIAnimationTransition encapsulé est créé par CAnimationController::AnimateGroup, jusqu'à ce que puis sa valeur est NULL. La modification de variables membres après que la création de cet objet COM n’a aucun effet.  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CBaseTransition](../../mfc/reference/cbasetransition-class.md)  
  
 `CAccelerateDecelerateTransition`   
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** afxanimationcontroller.h  
  
##  <a name="cacceleratedeceleratetransition"></a>  CAccelerateDecelerateTransition::CAccelerateDecelerateTransition  
 Construit un objet de transition.  
  
```  
CAccelerateDecelerateTransition(
    UI_ANIMATION_SECONDS duration,  
    DOUBLE finalValue,  
    DOUBLE accelerationRatio = 0.3,  
    DOUBLE decelerationRatio = 0.3);
```  
  
### <a name="parameters"></a>Paramètres  
 *Durée*  
 La durée de la transition.  
  
 *finalValue*  
 La valeur de la variable à la fin de la transition de l’animation.  
  
 *accelerationRatio*  
 Le rapport entre le temps consacré à l’accélération de la durée.  
  
 *decelerationRatio*  
 Le rapport entre le temps de décélération à la durée.  
  
##  <a name="create"></a>  CAccelerateDecelerateTransition::Create  
 Appelle la bibliothèque de transition pour créer l’objet COM de transition encapsulé.  
  
```  
virtual BOOL Create(
    IUIAnimationTransitionLibrary* pLibrary,  
    IUIAnimationTransitionFactory* *\not used*\);
```  
  
### <a name="parameters"></a>Paramètres  
*pLibrary*  
 Un pointeur vers un [interface IUIAnimationTransitionLibrary](https://msdn.microsoft.com/library/windows/desktop/dd371897), qui définit une bibliothèque de transitions standards.  
  
### <a name="return-value"></a>Valeur de retour  
 TRUE si la transition est créée avec succès ; Sinon, FALSE.  
  
##  <a name="m_accelerationratio"></a>  CAccelerateDecelerateTransition::m_accelerationRatio  
 Le rapport entre le temps consacré à l’accélération de la durée.  
  
```  
DOUBLE m_accelerationRatio;  
```  
  
##  <a name="m_decelerationratio"></a>  CAccelerateDecelerateTransition::m_decelerationRatio  
 Le rapport entre le temps de décélération à la durée.  
  
```  
DOUBLE m_decelerationRatio;  
```  
  
##  <a name="m_duration"></a>  CAccelerateDecelerateTransition::m_duration  
 La durée de la transition.  
  
```  
UI_ANIMATION_SECONDS m_duration;  
```  
  
##  <a name="m_finalvalue"></a>  CAccelerateDecelerateTransition::m_finalValue  
 La valeur de la variable à la fin de la transition de l’animation.  
  
```  
DOUBLE m_finalValue;  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Classes](../../mfc/reference/mfc-classes.md)
