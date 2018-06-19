---
title: CSinusoidalTransitionFromRange, classe | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CSinusoidalTransitionFromRange
- AFXANIMATIONCONTROLLER/CSinusoidalTransitionFromRange
- AFXANIMATIONCONTROLLER/CSinusoidalTransitionFromRange::CSinusoidalTransitionFromRange
- AFXANIMATIONCONTROLLER/CSinusoidalTransitionFromRange::Create
- AFXANIMATIONCONTROLLER/CSinusoidalTransitionFromRange::m_dblMaximumValue
- AFXANIMATIONCONTROLLER/CSinusoidalTransitionFromRange::m_dblMinimumValue
- AFXANIMATIONCONTROLLER/CSinusoidalTransitionFromRange::m_duration
- AFXANIMATIONCONTROLLER/CSinusoidalTransitionFromRange::m_period
- AFXANIMATIONCONTROLLER/CSinusoidalTransitionFromRange::m_slope
dev_langs:
- C++
helpviewer_keywords:
- CSinusoidalTransitionFromRange [MFC], CSinusoidalTransitionFromRange
- CSinusoidalTransitionFromRange [MFC], Create
- CSinusoidalTransitionFromRange [MFC], m_dblMaximumValue
- CSinusoidalTransitionFromRange [MFC], m_dblMinimumValue
- CSinusoidalTransitionFromRange [MFC], m_duration
- CSinusoidalTransitionFromRange [MFC], m_period
- CSinusoidalTransitionFromRange [MFC], m_slope
ms.assetid: 8b66a729-5f10-431a-b055-e3600d0065da
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 09c302ec414e26c71d8989bb6d624314c8eb6db4
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33370205"
---
# <a name="csinusoidaltransitionfromrange-class"></a>CSinusoidalTransitionFromRange, classe
Encapsule une transition de plage sinusoïdale comportant une plage d'oscillation donnée.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CSinusoidalTransitionFromRange : public CBaseTransition;  
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CSinusoidalTransitionFromRange::CSinusoidalTransitionFromRange](#csinusoidaltransitionfromrange)|Construit un objet de transition.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[CSinusoidalTransitionFromRange::Create](#create)|Appelle la bibliothèque de transition pour créer l’objet COM de transition encapsulé. (Substitue [CBaseTransition::Create](../../mfc/reference/cbasetransition-class.md#create).)|  
  
### <a name="public-data-members"></a>Membres de données publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CSinusoidalTransitionFromRange::m_dblMaximumValue](#m_dblmaximumvalue)|La valeur de la variable d’animation à une crête de l’onde sinusoïdale.|  
|[CSinusoidalTransitionFromRange::m_dblMinimumValue](#m_dblminimumvalue)|La valeur de la variable d’animation à un bac de l’onde sinusoïdale.|  
|[CSinusoidalTransitionFromRange::m_duration](#m_duration)|La durée de la transition.|  
|[CSinusoidalTransitionFromRange::m_period](#m_period)|La période d’oscillation de l’onde sinusoïdale en secondes.|  
|[CSinusoidalTransitionFromRange::m_slope](#m_slope)|La courbe au début de la transition.|  
  
## <a name="remarks"></a>Notes  
 La valeur de la variable d’animation fluctue entre les valeurs minimales et maximales spécifiées sur toute la durée d’une transition de plage sinusoïdale. Le paramètre de la courbe est utilisé pour lever l’ambiguïté entre les deux ondes possibles spécifiées par les autres paramètres. Étant donné que toutes les transitions sont effacées automatiquement, il est recommandé de les allouer à l’aide de nouvel opérateur. L’objet COM IUIAnimationTransition encapsulé est créé par CAnimationController::AnimateGroup, jusqu'à ce que puis sa valeur est NULL. La modification de variables membres après que la création de cet objet COM n’a aucun effet.  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CBaseTransition](../../mfc/reference/cbasetransition-class.md)  
  
 [CSinusoidalTransitionFromRange](../../mfc/reference/csinusoidaltransitionfromrange-class.md)  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** afxanimationcontroller.h  
  
##  <a name="create"></a>  CSinusoidalTransitionFromRange::Create  
 Appelle la bibliothèque de transition pour créer l’objet COM de transition encapsulé.  
  
```  
virtual BOOL Create(
    IUIAnimationTransitionLibrary* pLibrary,  
    IUIAnimationTransitionFactory* \*not used*\);
```  
  
### <a name="parameters"></a>Paramètres  
 `pLibrary`  
 Pointeur vers la bibliothèque de transitions qui est responsable de la création de transitions standards.  
  
### <a name="return-value"></a>Valeur de retour  
 TRUE si la transition est créée avec succès ; Sinon, FALSE.  
  
##  <a name="csinusoidaltransitionfromrange"></a>  CSinusoidalTransitionFromRange::CSinusoidalTransitionFromRange  
 Construit un objet de transition.  
  
```  
CSinusoidalTransitionFromRange(
    UI_ANIMATION_SECONDS duration,  
    DOUBLE dblMinimumValue,  
    DOUBLE dblMaximumValue,  
    UI_ANIMATION_SECONDS period,  
    UI_ANIMATION_SLOPE slope);
```  
  
### <a name="parameters"></a>Paramètres  
 `duration`  
 La durée de la transition.  
  
 `dblMinimumValue`  
 La valeur de la variable d’animation à un bac de l’onde sinusoïdale.  
  
 `dblMaximumValue`  
 La valeur de la variable d’animation à une crête de l’onde sinusoïdale.  
  
 `period`  
 La période d’oscillation de l’onde sinusoïdale en secondes.  
  
 `slope`  
 La courbe au début de la transition.  
  
##  <a name="m_dblmaximumvalue"></a>  CSinusoidalTransitionFromRange::m_dblMaximumValue  
 La valeur de la variable d’animation à une crête de l’onde sinusoïdale.  
  
```  
DOUBLE m_dblMaximumValue;  
```  
  
##  <a name="m_dblminimumvalue"></a>  CSinusoidalTransitionFromRange::m_dblMinimumValue  
 La valeur de la variable d’animation à un bac de l’onde sinusoïdale.  
  
```  
DOUBLE m_dblMinimumValue;  
```  
  
##  <a name="m_duration"></a>  CSinusoidalTransitionFromRange::m_duration  
 La durée de la transition.  
  
```  
UI_ANIMATION_SECONDS m_duration;  
```  
  
##  <a name="m_period"></a>  CSinusoidalTransitionFromRange::m_period  
 La période d’oscillation de l’onde sinusoïdale en secondes.  
  
```  
UI_ANIMATION_SECONDS m_period;  
```  
  
##  <a name="m_slope"></a>  CSinusoidalTransitionFromRange::m_slope  
 La courbe au début de la transition.  
  
```  
UI_ANIMATION_SLOPE m_slope;  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Classes](../../mfc/reference/mfc-classes.md)
