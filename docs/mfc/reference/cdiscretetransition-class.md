---
title: CDiscreteTransition, classe | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CDiscreteTransition
- AFXANIMATIONCONTROLLER/CDiscreteTransition
- AFXANIMATIONCONTROLLER/CDiscreteTransition::CDiscreteTransition
- AFXANIMATIONCONTROLLER/CDiscreteTransition::Create
- AFXANIMATIONCONTROLLER/CDiscreteTransition::m_dblFinalValue
- AFXANIMATIONCONTROLLER/CDiscreteTransition::m_delay
- AFXANIMATIONCONTROLLER/CDiscreteTransition::m_hold
dev_langs:
- C++
helpviewer_keywords:
- CDiscreteTransition [MFC], CDiscreteTransition
- CDiscreteTransition [MFC], Create
- CDiscreteTransition [MFC], m_dblFinalValue
- CDiscreteTransition [MFC], m_delay
- CDiscreteTransition [MFC], m_hold
ms.assetid: b4d84fb3-ccaa-451c-a69b-6b50dcb9b9c8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a0252cc64a1d14a6d096a5c4ad6dd2e0d6c3c7ff
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/26/2018
ms.locfileid: "36957030"
---
# <a name="cdiscretetransition-class"></a>CDiscreteTransition, classe
Encapsule une transition discrète.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CDiscreteTransition : public CBaseTransition;  
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CDiscreteTransition::CDiscreteTransition](#cdiscretetransition)|Construit un objet de transition discret et initialise ses paramètres.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[CDiscreteTransition::Create](#create)|Appelle la bibliothèque de transition pour créer l’objet COM de transition encapsulé. (Substitue [CBaseTransition::Create](../../mfc/reference/cbasetransition-class.md#create).)|  
  
### <a name="public-data-members"></a>Membres de données publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CDiscreteTransition::m_dblFinalValue](#m_dblfinalvalue)|La valeur de la variable à la fin de la transition de l’animation.|  
|[CDiscreteTransition::m_delay](#m_delay)|La quantité de temps en temps le commutateur instantané à la valeur finale.|  
|[CDiscreteTransition::m_hold](#m_hold)|La quantité de temps permettant de contenir la variable à sa valeur finale.|  
  
## <a name="remarks"></a>Notes  
 Pendant une transition discrète, la variable d’animation conserve la valeur initiale pour un délai spécifié, puis passe instantanément à une valeur définitive spécifiée et conserve cette valeur pour une durée donnée. Étant donné que toutes les transitions sont effacées automatiquement, il est recommandé de les allouer à l’aide de nouvel opérateur. L’objet COM IUIAnimationTransition encapsulé est créé par CAnimationController::AnimateGroup, jusqu'à ce que puis sa valeur est NULL. La modification de variables membres après que la création de cet objet COM n’a aucun effet.  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CBaseTransition](../../mfc/reference/cbasetransition-class.md)  
  
 [CDiscreteTransition](../../mfc/reference/cdiscretetransition-class.md)  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** afxanimationcontroller.h  
  
##  <a name="cdiscretetransition"></a>  CDiscreteTransition::CDiscreteTransition  
 Construit un objet de transition discret et initialise ses paramètres.  
  
```  
CDiscreteTransition(
    UI_ANIMATION_SECONDS delay,  
    DOUBLE dblFinalValue,  
    UI_ANIMATION_SECONDS hold);
```  
  
### <a name="parameters"></a>Paramètres  
 *délai*  
 La quantité de temps en temps le commutateur instantané à la valeur finale.  
  
 *dblFinalValue*  
 La valeur de la variable à la fin de la transition de l’animation.  
  
 *Maintenez la touche*  
 La quantité de temps permettant de contenir la variable à sa valeur finale.  
  
##  <a name="create"></a>  CDiscreteTransition::Create  
 Appelle la bibliothèque de transition pour créer l’objet COM de transition encapsulé.  
  
```  
virtual BOOL Create(
    IUIAnimationTransitionLibrary* pLibrary,  
    IUIAnimationTransitionFactory* \*not used*\);
```  
  
*pLibrary*  
 Un pointeur vers un [interface IUIAnimationTransitionLibrary](https://msdn.microsoft.com/library/windows/desktop/dd371897), qui définit une bibliothèque de transitions standards.  

  
### <a name="return-value"></a>Valeur de retour  
 TRUE si la transition est créée avec succès ; Sinon, FALSE.  
  
##  <a name="m_dblfinalvalue"></a>  CDiscreteTransition::m_dblFinalValue  
 La valeur de la variable à la fin de la transition de l’animation.  
  
```  
DOUBLE m_dblFinalValue;  
```  
  
##  <a name="m_delay"></a>  CDiscreteTransition::m_delay  
 La quantité de temps en temps le commutateur instantané à la valeur finale.  
  
```  
UI_ANIMATION_SECONDS m_delay;  
```  
  
##  <a name="m_hold"></a>  CDiscreteTransition::m_hold  
 La quantité de temps permettant de contenir la variable à sa valeur finale.  
  
```  
UI_ANIMATION_SECONDS m_hold;  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Classes](../../mfc/reference/mfc-classes.md)
